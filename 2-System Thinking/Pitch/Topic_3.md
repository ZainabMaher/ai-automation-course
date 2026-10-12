# MVP — Minimum Viable Product

## How Do We Decide What to Build First?
### كيف نحدد ما الذي يجب أن نبنيه أولًا؟

**Research Topic:** MVP Feature Prioritization  
**Project Example:** StudyFlow — Student Task Manager  
**Team:** Zainab Alsersawi & Deema Redwan

---

# 01 — Research Notes

## 1.1 What Is MVP?

**MVP — Minimum Viable Product** هو أبسط نسخة من المنتج تحتوي على الوظائف الضرورية لتقديم قيمة حقيقية للمستخدم، وتسمح باختبار الفكرة وجمع الملاحظات قبل التوسع في التطوير.

يتكون المفهوم من ثلاثة أجزاء:

| Term | Meaning |
|---|---|
| Minimum | أقل عدد من الميزات الضرورية |
| Viable | منتج مفيد وقابل للاستخدام |
| Product | حل يستطيع المستخدم تجربته |

> **MVP ≠ Low Quality**
>
> تقليل عدد الميزات لا يعني تقليل جودة المنتج، بل التركيز على تنفيذ الوظائف الأساسية بشكل صحيح.

## 1.2 Why Do We Need MVP?

نستخدم MVP للأسباب التالية:

- **Reduce Development Cost:** تقليل تكلفة التطوير.
- **Save Time:** تقليل الوقت اللازم لإطلاق النسخة الأولى.
- **Validate the Idea:** اختبار الفكرة قبل التوسع.
- **Collect Feedback:** جمع ملاحظات المستخدمين الحقيقيين.
- **Continuous Improvement:** تحسين المنتج بناءً على نتائج الاستخدام.

## 1.3 How Do We Prioritize Features?

نقسم الميزات إلى نوعين:

### Must Have — Essential Features

- ضرورية لحل المشكلة الأساسية.
- يجب تنفيذها في النسخة الأولى.
- غيابها يمنع المستخدم من تحقيق الهدف الأساسي.

### Later — Additional Features

- تحسن تجربة المستخدم.
- ليست ضرورية لتحقيق القيمة الأساسية.
- يمكن إضافتها بعد اختبار النسخة الأولى.

**Key Question:**

> If we remove this feature, can users still achieve their main goal?

إذا كانت الإجابة **No**، فغالبًا الميزة Must Have.

أما إذا كانت الإجابة **Yes**، فيمكن التفكير بتأجيلها إلى Later.

## 1.4 Why Can Feature-Rich Applications Fail?

قد يفشل التطبيق رغم احتوائه على ميزات كثيرة للأسباب التالية:

1. **User Distraction:** تشتيت المستخدم عن هدفه الأساسي.
2. **High Complexity:** زيادة تعقيد التطبيق.
3. **Higher Cost:** ارتفاع تكلفة التطوير والصيانة.
4. **Delayed Launch:** تأخير إطلاق المنتج.
5. **Lack of Focus:** التركيز على الميزات بدل حل المشكلة الأساسية.

**Key Insight:**

> More Features ≠ More Value

نجاح التطبيق لا يعتمد على عدد الميزات، بل على قدرته على حل مشكلة حقيقية للمستخدم.

---

# 02 — One Practical Artifact

## MVP Feature Prioritization — StudyFlow

### 2.1 Application Overview

**Application Name:** StudyFlow  
**Application Type:** Student Task Manager

**Problem Statement:**

يواجه طلاب الجامعات صعوبة في تنظيم الواجبات والمشاريع الدراسية ومتابعة مواعيد التسليم، مما قد يؤدي إلى نسيان المهام أو التأخر في إنجازها.

**Target Users:**

طلاب الجامعات.

**Core Value Proposition:**

مساعدة الطالب على تنظيم مهامه الدراسية، ومعرفة مواعيد تسليمها، ومتابعة حالة إنجازها بطريقة بسيطة وواضحة.

### 2.2 Proposed Features

اقترحنا ست ميزات للتطبيق، وصنفناها حسب أهميتها للنسخة الأولى.

| # | Feature | Description | Priority |
|---|---|---|---|
| 01 | Add Tasks | إضافة الواجبات والمهام الدراسية | Must Have |
| 02 | Set Deadlines | تحديد مواعيد تسليم المهام | Must Have |
| 03 | Track Task Status | متابعة حالة المهام | Must Have |
| 04 | Smart Notifications | إرسال تذكيرات بالمواعيد | Later |
| 05 | AI Study Planner | إنشاء خطة دراسية باستخدام AI | Later |
| 06 | Team Collaboration | مشاركة المهام مع الزملاء | Later |

### 2.3 Selected MVP Features

اخترنا **3 Features فقط** للنسخة الأولى:

#### Feature 01 — Add Tasks

تمكين الطالب من إضافة الواجبات والمشاريع الدراسية.

**Why Must Have?**

لأن التطبيق لا يستطيع تنظيم المهام دون وجود إمكانية لإضافتها.

#### Feature 02 — Set Deadlines

تمكين الطالب من تحديد موعد تسليم كل مهمة.

**Why Must Have?**

لأن معرفة مواعيد التسليم ضرورية لتنظيم الوقت وتحديد المهام القادمة.

#### Feature 03 — Track Task Status

تمكين الطالب من متابعة حالة كل مهمة:

- To Do
- In Progress
- Done

**Why Must Have?**

لأن الطالب يحتاج إلى معرفة المهام التي أنجزها والمهام التي ما زالت بحاجة إلى متابعة.

### 2.4 MVP Workflow

**The Core User Journey**

Add Task → Set Deadline → Track Progress

**Step 1:** يضيف الطالب المهمة الدراسية.

**Step 2:** يحدد موعد تسليمها.

**Step 3:** يتابع حالة المهمة ويحدثها عند التقدم في إنجازها.

### 2.5 Example Output

| Task | Deadline | Status |
|---|---|---|
| Database Assignment | October 15 | To Do |
| AI Presentation | October 17 | In Progress |
| Programming Quiz | October 12 | Done |

### 2.6 Why Did We Choose These Features?

اخترنا هذه الميزات الثلاث لأنها تحقق القيمة الأساسية للتطبيق وتكوّن رحلة استخدام متكاملة.

- بدون **Add Tasks** لا توجد مهام لتنظيمها.
- بدون **Set Deadlines** لا يستطيع الطالب متابعة مواعيد التسليم.
- بدون **Track Task Status** يصعب معرفة ما أُنجز وما تبقى.

أما الميزات الأخرى مثل AI Study Planner وSmart Notifications وTeam Collaboration، فهي مفيدة لكنها ليست ضرورية للنسخة الأولى.

### 2.7 Expected MVP Result

يمكن للطالب استخدام النسخة الأولى من StudyFlow لإضافة مهامه الدراسية، وتحديد مواعيدها، ومتابعة إنجازها دون الحاجة إلى ميزات متقدمة.

بعد بناء النسخة الأولى، يمكن اختبارها مع مجموعة من الطلاب، وجمع ملاحظاتهم لتحسين التطبيق وتحديد الميزات التي يجب تطويرها لاحقًا.

**Final MVP Scope:**

3 Essential Features — One Core Problem — Real User Value

---

# 03 — Sources

المصادر المعتمدة للبحث:

### 1. Lean Startup — What Is an MVP?

**Topic:** تعريف MVP وأهمية اختبار الأفكار والتعلم من المستخدمين.

https://leanstartup.co/resources/articles/what-is-an-mvp/

### 2. Atlassian — Prioritization Frameworks

**Topic:** طرق ترتيب أولويات الميزات، بما فيها MoSCoW Prioritization.

https://www.atlassian.com/agile/product-management/prioritization-framework

### 3. Nielsen Norman Group — Feature Richness and User Engagement

**Topic:** العلاقة بين كثرة الميزات وتجربة المستخدم وسهولة الاستخدام.

https://www.nngroup.com/articles/feature-richness-and-user-engagement/

---
uilding more features, but about delivering real value with the minimum essential features.**
