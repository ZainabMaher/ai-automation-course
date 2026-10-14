# Unit 01 — Process & Data Thinking

> **Think First. Build Later.**

## 1. نظرة عامة

في **AI Automation**، التحدي ليس أن نجعل الأداة تنفذ مهمة.

التحدي الحقيقي هو أن نفهم أولًا:

- ما العمل الذي نحاول تحسينه؟
- ما المشكلة الحقيقية؟
- كيف يحدث العمل حاليًا؟
- ما البيانات التي تدخل إلى النظام؟
- كيف يجب أن يتم اتخاذ القرار؟
- ماذا يحدث عندما تكون الحالة غير واضحة؟
- وما الذي يجب أتمتته فعلًا؟

لذلك تبدأ هذه الوحدة قبل اختيار أي **Tool**.

في **Unit 01** سننتقل من فهم الـ**Work** والـ**Problem** إلى تحليل الـ**Process** والـ**Data**، ثم تصميم الـ**Decision** والـ**Automation**، وأخيرًا تنفيذ التصميم باستخدام **Zapier**.

> **Understand the work before automating the work.**

---

# 2. Learning Outcomes

بنهاية هذه الوحدة، ستكون قادرًا على:

- تحليل الـ**Work** وتحديد الـ**Problem** و**Pain Points**.
- فهم الـ**Current State** وتحديد الـ**Desired Outcome**.
- تحديد **Success Criteria** لمعرفة ما إذا كان الحل يحقق النتيجة المطلوبة.
- تفكيك العمل إلى **Process, Workflow, Task, Subtask**.
- تحليل **Sequence** و**Dependencies**.
- تحديد **Trigger** و**Input** وفهم طبيعة الـ**Data**.
- التمييز بين **Unstructured Data** و**Structured Data**.
- تحديد **Missing Information** وتطبيق **Validation**.
- التمييز بين استخدام **AI** واستخدام **Rule** أو **Human**.
- تصميم **AI Task** ينتج **Structured Output** مناسبًا للخطوات التالية.
- تحديد **Exceptions** ونقاط **Human-in-the-Loop**.
- تصميم الـ**Automation** قبل تنفيذها.
- تحويل التصميم إلى **Working Automation** باستخدام Zapier.
- اختبار الـAutomation والتأكد من أن التنفيذ يطابق التصميم.

---

# 3. The Core Mental Model

تعتمد الوحدة على سبع **Layers** تساعدك على الانتقال من فهم المشكلة إلى بناء الحل.

## Layer 01 — Understand the Work

**Work → Problem → Pain Point → Current State → Desired Outcome → Success Criteria**

**السؤال:**  
ما العمل الذي نحاول تحسينه؟

**English:**  
> **What are we trying to improve?**

في هذه المرحلة نفهم العمل، المشكلة، الصعوبات الموجودة، طريقة العمل الحالية، النتيجة المطلوبة، وكيف سنعرف أن التحسين نجح.

---

## Layer 02 — Decompose the Work

**Process → Workflow → Task → Subtask → Sequence → Dependency**

**السؤال:**  
كيف يحدث العمل؟

**English:**  
> **How does the work happen?**

ننتقل من الصورة الكبيرة إلى التفاصيل التي تساعدنا على فهم الـ**Process**، والـ**Workflow**، والمهام، وترتيبها، وما يعتمد على ماذا.

---

## Layer 03 — Understand the Input & Data

**Trigger → Input → Unstructured Data → Structured Data → Missing Information → Validation**

**السؤال:**  
ما البيانات التي تدخل إلى الـWorkflow، وهل يمكن الاعتماد عليها؟

**English:**  
> **What data enters the workflow, and can it be used reliably?**

نهتم بمصدر البيانات، شكلها، المعلومات الموجودة، المعلومات الناقصة، وكيف نتحقق من صلاحيتها.

---

## Layer 04 — Design the Decision

**AI-Powered Automation → AI vs Rule → Deterministic Logic → AI Task → Structured Output**

**السؤال:**  
كيف يجب أن يتخذ النظام القرار؟

**English:**  
> **How should the system make decisions?**

ليس كل **Task** يحتاج إلى AI.

نحدد متى نستخدم **AI**، ومتى تكون **Rule** أكثر ملاءمة، ومتى نحتاج إلى **Human Judgment**.

> **Use the simplest reliable mechanism for the task.**

---

## Layer 05 — Handle Exceptions Safely

**Exception → Human-in-the-Loop → Safe Automation**

**السؤال:**  
ماذا يحدث عندما لا تسير الحالة بالطريقة المعتادة؟

**English:**  
> **What happens when the normal path is not enough?**

لا نحاول جعل كل شيء آليًا.

نحدد ما يمكن أتمتته بأمان، وما يحتاج إلى تدخل أو قرار بشري.

> **Automate what is clear. Escalate what is not.**

---

## Layer 06 — Design the Automation

بعد فهم الـ**Work** والـ**Process** والـ**Data** والـ**Decision** والـ**Exceptions**، ننتقل إلى تصميم الـ**Automation**.

**السؤال:**  
ماذا يجب أن يحدث تلقائيًا؟

**English:**  
> **What should happen automatically?**

في هذه المرحلة نحول التفكير الهندسي إلى تصميم واضح يمكن تنفيذه.

---

## Layer 07 — Implement the Design

الآن ننتقل من:

> **What should happen?**

إلى:

> **How will we build it?**

في هذه الوحدة نستخدم **Zapier** لتنفيذ التصميم.

> **Tools implement the design. Tools do not replace the design.**

---

# 4. Engineering Flow

الرحلة في هذه الوحدة:

```text
Understand the Work
        ↓
Decompose the Work
        ↓
Understand the Input & Data
        ↓
Design the Decision
        ↓
Handle Exceptions Safely
        ↓
Design the Automation
        ↓
Implement the Design
        ↓
Test
        ↓
Refine
```

هذا الـ**Flow** ليس مجرد خطوات لتنفيذ مشروع واحد.

إنه طريقة تفكير سنبني عليها في الوحدات القادمة.

---

# 5. Learning Journey

خلال الوحدة، سننتقل من **Discovery** إلى **Application** ثم إلى **Independent Thinking**.

### Opening Challenge

نبدأ بمشكلة عملية قبل تقديم الـFramework، حتى تكتشف بنفسك ما الذي نحتاج إلى فهمه قبل بناء Automation.

### Concept Debrief

نعود إلى الـChallenge ونحوّل ما اكتشفناه إلى **Engineering Framework** واضح.

### Guided Practice

نطبق الـFramework عمليًا ونرى كيف يتحول التفكير إلى تصميم ثم إلى **Working Automation**.

### Independent Application

تستخدم نفس طريقة التفكير على مشكلة مختلفة وتبني الحل بنفسك.

### Research Pair

تتوسع في موضوع مرتبط بـ**AI Automation** خارج المفاهيم التي تم شرحها مباشرة.

> **Research = Expansion, not Repetition.**

### Research Pitch

تشارك ما تعلمته مع المجموعة من خلال **Short Research Pitch**.

### NOVA

تبدأ أول مرحلة من **NOVA**، المشروع التراكمي الذي سيتطور معك عبر الوحدات الثماني.

---

# 6. The Engineering Mindset

في هذه الوحدة نريد أن نغيّر نقطة البداية.

لا تبدأ بـ:

> **Which Tool should I use?**

ابدأ بـ:

> **What problem am I solving?**

ثم اسأل:

> **How does the work happen?**  
> كيف يحدث العمل؟

> **What data do I have?**  
> ما البيانات التي أملكها؟

> **How should the decision be made?**  
> كيف يجب أن يتم اتخاذ القرار؟

> **What happens when something goes wrong?**  
> ماذا يحدث عندما لا تسير الحالة بشكل طبيعي؟

> **What should be automated?**  
> ماذا يجب أن تتم أتمتته؟

ثم فقط:

> **How will I build it?**  
> كيف سأبنيه؟

---

# 7. U1 Core Principle

> ## Think First. Build Later.

الهدف من هذه الوحدة ليس أن تصبح خبيرًا في **Zapier**.

الهدف أن تبدأ في التفكير كـ**AI Automation Solution Engineer**:

**يفهم المشكلة → يحلل العمل → يفهم البيانات → يصمم القرار → يتعامل مع الاستثناءات → يصمم الـAutomation → ينفذها → يختبرها.**

> **A good Automation does not begin with a Tool.  
> It begins with understanding.**

