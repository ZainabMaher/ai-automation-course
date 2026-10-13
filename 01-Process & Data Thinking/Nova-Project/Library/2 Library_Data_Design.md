# 03 — Data Design

**Project:** Library Borrowing & Reservation Tracker

## 1. Trigger

يبدأ الـZap عند إرسال عضو المكتبة طلبًا عبر Google Forms، فيُضاف صف جديد إلى تبويب `Requests` في Google Sheets.

| Property | Value |
|---|---|
| Application | Google Sheets |
| Event | New Spreadsheet Row |
| Worksheet | `Requests` |
| Trigger | صف جديد لطلب عضو |
| Reference | `Row ID` لتحديث الصف الأصلي دون تكراره |

## 2. Inputs

| Field | Purpose | Required |
|---|---|---|
| `member_name` | اسم العضو | Yes |
| `member_id` | رقم العضوية | Yes |
| `email` | بريد العضو | Yes |
| `book_title_input` | عنوان الكتاب كما كتبه العضو | No |
| `request_text` | تفاصيل الطلب بلغة طبيعية | Yes |
| `Row ID` | معرّف صف الطلب الناتج عن الـTrigger | Automatic |

**مدخل إضافي ديناميكي:** تقرأ خطوة `Get Data Range` عناوين الكتب من `Books!B2:B500` (وقد أظهرت التجربة 308 عناوين)، ثم تحولها خطوة `Formatter` إلى نص مفصول بعلامة `|` في `Output Text`. يُمرَّر هذا النص إلى `AI by Zapier` بدل قائمة الكتب الثمانية المكتوبة يدويًا.

## 3. Unstructured Data

الحقل `request_text` نص حر، وقد يتضمن صياغات عربية أو إنجليزية أو طلبًا غير مكتمل.

**أمثلة:**
- «بدي أستعير كتاب العادات الذرية».
- «خلصت الرواية ورجعتها اليوم».
- «I want to borrow Atomic Habits».

يستخلص AI العملية والعنوان من النص، مع الحفاظ على المطابقة لعنوان الكتالوج الفعلي.

## 4. Structured Data

| Field | Description |
|---|---|
| `request_type` | نوع العملية |
| `book_title` | عنوان مطابق للكتالوج كما هو في الشيت |
| `request_summary` | ملخص بجملة واحدة بلغة الطلب |
| `missing_information` | المعلومات الناقصة، أو `None` |

### Allowed `request_type` Values

- `borrow`: استعارة
- `reserve`: حجز
- `return`: إرجاع
- `other`: طلب مفهوم لكنه خارج نطاق العمليات
- `unknown`: تعذّر تحديد العملية

### Book Title Rules

- يجب أن يكون العنوان مطابقًا لأحد العناوين المسترجعة ديناميكيًا من `Books`.
- إذا كتب العضو العنوان بالإنجليزية وكان مسجلاً بالعربية، يعيد AI الصيغة العربية المطابقة للشيت.
- `Not provided`: لم يُذكر عنوان.
- `NOT_IN_CATALOG`: لم يُعثر على الكتاب في القائمة.
- `MULTIPLE`: طلب يتضمن أكثر من كتاب.
- لا يخترع AI عنوانًا أو بيانات غير موجودة.

## 5. Data Schema

### A. `Requests` — سجل الطلبات

| Field | Source | Purpose |
|---|---|---|
| `member_name` | Google Forms | اسم العضو |
| `member_id` | Google Forms | رقم العضوية |
| `email` | Google Forms | البريد الإلكتروني |
| `book_title_input` | Google Forms | العنوان المدخل |
| `request_text` | Google Forms | النص الحر |
| `request_type` | AI by Zapier | العملية المستخرجة |
| `book_title` | AI by Zapier | العنوان المطابق |
| `request_summary` | AI by Zapier | الملخص |
| `missing_information` | AI by Zapier | المعلومات الناقصة |
| `validation_status` | Decision Engine | نتيجة التحقق |
| `requires_human` | Decision Engine | الحاجة إلى تدخل بشري |
| `decision` | Decision Engine | القرار النهائي |
| `routing` | Decision Engine | المسار المحدد |
| `review_reason` | Decision Engine | سبب الإحالة |
| `processed_at` | Zapier | وقت المعالجة |

يحتفظ الشيت أيضًا بوقت تقديم النموذج ومعرّف الصف؛ يُحدّث النظام الصف الأصلي باستخدام `Row ID` بدل إنشاء صف جديد.

### B. `Books` — سجل الكتب

| Field | Purpose |
|---|---|
| `title` | عنوان الكتاب؛ مصدر الكتالوج |
| `status` | حالة الكتاب: `available`, `borrowed`, `on_hold` |
| `borrowed_by` | المستعير الحالي |
| `borrow_date` | تاريخ الاستعارة |
| `due_date` | موعد الإرجاع |
| `reserved_by` | صاحب الحجز |
| `reserved_email` | بريد صاحب الحجز |

تحتوي ورقة `Books` بحسب الوثيقة المرجعية على 10 أعمدة؛ يعرض الجدول الحقول ذات الصلة بالمعالجة، ولا يفترض أسماء بقية الأعمدة غير المحددة في المصدر.

## 6. Missing Information

| Value | Meaning |
|---|---|
| `Not provided` | عنوان الكتاب غير مذكور |
| `NOT_IN_CATALOG` | العنوان غير موجود في الكتالوج |
| `MULTIPLE` | أكثر من كتاب في طلب واحد |
| `unknown` | نوع الطلب غير قابل للتحديد |
| `other` | طلب خارج نطاق الأتمتة |
| `None` | لا توجد معلومات ناقصة بحسب الاستخراج |

لا تُعامل هذه القيم بوصفها مترادفات. تُحال الحالات غير الواضحة أو المتعارضة إلى المراجعة البشرية.

## 7. Validation

يتحقق `Code by Zapier` من مخرجات AI وبيانات العضو وحالة الكتاب وفق قواعد مرتبة؛ أول قاعدة تنطبق تحدد قرارًا واحدًا.

1. التحقق من وجود مخرجات AI وصحتها.
2. التأكد من اسم العضو ورقم العضوية والبريد.
3. رفض `unknown` و`other` للتنفيذ التلقائي.
4. التحقق من وجود عنوان واحد واضح.
5. التحقق من وجود الكتاب في `Books`.
6. منع إعارة كتاب لنفس المستعير مرة أخرى.
7. الموافقة على الاستعارة إذا كان الكتاب متاحًا أو محجوزًا للعضو نفسه.
8. تسجيل حجز إذا كان الكتاب مُعارًا ولم يُحجز لغيره.
9. إحالة الحجز المتعارض للمراجعة.
10. قبول الإرجاع فقط من المستعير المسجل.
11. إحالة أي إرجاع غير مطابق للمراجعة.

### Processing Results

| Field | Allowed values / description |
|---|---|
| `validation_status` | `VALID`, `NEEDS_REVIEW` |
| `requires_human` | `true`, `false` |
| `decision` | `BORROW_APPROVED`, `RESERVED`, `RETURN_RECORDED`, `NEEDS_REVIEW` |
| `routing` | `auto_borrow`, `auto_reserve`, `auto_return`, `librarian_review` |
| `review_reason` | سبب المراجعة أو `None` |
| `processed_at` | Timestamp |

**ملاحظة تنفيذية:** نجاح اختبار `RESERVED` في الخطوات الخاصة بالاستخراج والبحث واتخاذ القرار لا يثبت وحده نجاح تحديث الحجز أو إرسال البريد في الخطوات اللاحقة.

## Expected Outcome

تحديد مصدر البيانات وشكلها وكيفية تحويل النص الحر إلى بيانات منظمة، ثم التحقق منها وتسجيل القرار في صف الطلب الأصلي، مع إبقاء `Books` مصدر الحقيقة لحالة الكتب وعناوينها.

> **AI يفهم — Rules تقرر — Human يراجع الاستثناءات.**

**حدّ النطاق:** تتعرف خطوة قراءة الكتالوج تلقائيًا على العناوين داخل `B2:B500`، ولا تشمل العناوين خارج هذا النطاق دون تعديل الإعدادات.
