```mermaid
graph TD
    %% =================================================================
    %% المخطط الرئيسي: دورة حياة وكيل ذكاء اصطناعي واعي هرمي
    %% التصميم: مبني على أفكار المستخدم حول الوعي والاستكشاف والتخطيط
    %% =================================================================

    %% -----------------------------------------------------------------
    %% المرحلة صفر: التهيئة والبنية الأساسية للنظام
    %% -----------------------------------------------------------------
    subgraph المرحلة 0: تهيئة النظام والبنى العصبية
        INIT_START("
        <div style='font-weight:bold; font-size:16px; margin-bottom:5px;'>1. بدء التشغيل</div>
        <div style='text-align:left; font-size:12px;'>
        - تهيئة جميع الشبكات العصبية بأوزان عشوائية.<br/>
        - تهيئة ذاكرة الخبرة (Replay Buffers) فارغة.<br/>
        - لا يوجد أي معرفة مسبقة عن الذات أو البيئة.
        </div>
        ")

        INIT_MODELS("
        <div style='font-weight:bold; font-size:14px; margin-bottom:5px;'>2. تعريف المكونات العصبية</div>
        <div style='text-align:left; font-size:12px;'>
        <b>أ. النموذج الذاتي (World Model / Dynamics Model):</b><br/>
        &nbsp;&nbsp;&nbsp;&nbsp;- شبكة تتنبأ بالحالة التالية (s') بناءً على الحالة الحالية (s) والفعل (a).<br/>
        <b>ب. النموذج البيئي (Environmental Model):</b><br/>
        &nbsp;&nbsp;&nbsp;&nbsp;- شبكة تتنبأ بمدخلات الحساسات (قراءات الأشعة) بناءً على الموقع والاتجاه.<br/>
        <b>ج. السياسة الهرمية (Hierarchical Policy):</b><br/>
        &nbsp;&nbsp;&nbsp;&nbsp;<b>- المدير (Manager / High-Level Policy):</b> يختار الأهداف الفرعية (Sub-goals).<br/>
        &nbsp;&nbsp;&nbsp;&nbsp;<b>- الخبراء (Experts / Low-Level Policies):</b> شبكات متخصصة لتنفيذ الأهداف الفرعية (مثل الانجراف، التسارع).
        </div>
        ")

        INIT_MEMORY("
        <div style='font-weight:bold; font-size:14px; margin-bottom:5px;'>3. تعريف ذاكرة الخبرة</div>
        <div style='text-align:left; font-size:12px;'>
        - <b>ذاكرة الفيزياء (Physics Buffer):</b> لتخزين تجارب (s, a, r, s') لتدريب النموذج الذاتي.<br/>
        - <b>ذاكرة الخريطة (Mapping Buffer):</b> لتخزين (موقع، قراءات الحساسات) لتدريب النموذج البيئي.<br/>
        - <b>ذاكرة المهمة (Task Buffer):</b> لتخزين تجارب كاملة لتدريب المدير والخبراء.
        </div>
        ")
        INIT_START --> INIT_MODELS --> INIT_MEMORY
    end

    %% -----------------------------------------------------------------
    %% المرحلة الأولى: اكتشاف الذات (فهم فيزياء الحركة)
    %% تتم في بيئة فارغة لتركيز التعلم على الذات فقط
    %% -----------------------------------------------------------------
    subgraph المرحلة 1: اكتشاف الذات (مدفوع بالفضول)
        style المرحلة 1 fill:#f9f,stroke:#333,stroke-width:2px

        SELF_START("
        <div style='font-weight:bold; font-size:14px; margin-bottom:5px;'>4. بدء مرحلة اكتشاف الذات</div>
        <div style='text-align:left; font-size:12px;'>
        - البيئة: مساحة مفتوحة لا نهائية.<br/>
        - الدافع: مكافأة الفضول فقط (لا يوجد هدف خارجي).
        </div>
        ")
        
        SELF_LOOP_START("
        <div style='font-weight:bold; font-size:12px;'>5. حلقة الاستكشاف الذاتي</div>
        ")

        SELF_ACTION(إصدار فعل عشوائي أو موجه بالفضول)
        SELF_EXECUTE(تنفيذ الفعل في البيئة الافتراضية)
        SELF_OBSERVE(ملاحظة الحالة الجديدة s' والمكافأة r)
        SELF_STORE(تخزين التجربة (s, a, r, s') في ذاكرة الفيزياء)
        SELF_TRAIN_PREPARE(سحب عينة عشوائية من ذاكرة الفيزياء)
        SELF_TRAIN_MODEL("
        <div style='font-weight:bold; font-size:12px;'>تدريب النموذج الذاتي</div>
        <div style='text-align:left; font-size:11px;'>
        - التنبؤ بـ s' باستخدام النموذج.<br/>
        - حساب الخطأ بين التنبؤ والواقع.<br/>
        - تحديث أوزان الشبكة (Backpropagation).
        </div>
        ")
        
        SELF_CURIOSITY("
        <div style='font-weight:bold; font-size:12px;'>6. حساب مكافأة الفضول</div>
        <div style='text-align:left; font-size:11px;'>
        - المكافأة = مقدار خطأ التنبؤ.<br/>
        - كلما كانت النتيجة مفاجئة، زادت المكافأة.<br/>
        - هذه المكافأة تُستخدم لتوجيه الاستكشاف نحو الأفعال غير المفهومة.
        </div>
        ")

        SELF_CHECK_CONVERGENCE{"
        <div style='font-weight:bold; font-size:12px;'>7. هل النموذج الذاتي دقيق؟</div>
        <div style='text-align:left; font-size:11px;'>
        (هل معدل خطأ التنبؤ منخفض؟)
        </div>
        "}

        SELF_MODEL_COMPLETE(("
        <div style='font-weight:bold; font-size:14px;'>8. اكتمال النموذج الذاتي</div>
        <div style='text-align:left; font-size:12px;'>
        الذكاء الاصطناعي الآن 'يفهم' كيف يتحرك.
        </div>
        "))

        SELF_LOOP_START --> SELF_ACTION --> SELF_EXECUTE --> SELF_OBSERVE --> SELF_STORE --> SELF_TRAIN_PREPARE --> SELF_TRAIN_MODEL --> SELF_CURIOSITY --> SELF_CHECK_CONVERGENCE
        SELF_CHECK_CONVERGENCE -- لا، استمر في الاستكشاف --> SELF_LOOP_START
        SELF_CHECK_CONVERGENCE -- نعم، النموذج مستقر --> SELF_MODEL_COMPLETE
    end

    %% -----------------------------------------------------------------
    %% المرحلة الثانية: اكتشاف البيئة (بناء الخريطة)
    %% -----------------------------------------------------------------
    subgraph المرحلة 2: استكشاف البيئة ورسم الخرائط
        style المرحلة 2 fill:#9cf,stroke:#333,stroke-width:2px

        MAP_START("
        <div style='font-weight:bold; font-size:14px; margin-bottom:5px;'>9. بدء استكشاف المسار</div>
        <div style='text-align:left; font-size:12px;'>
        - البيئة: مسار السباق الفعلي.<br/>
        - تفعيل 'أشعة الاستشعار' (حاسة الخفاش).
        </div>
        ")
        
        MAP_LOOP_START("
        <div style='font-weight:bold; font-size:12px;'>10. حلقة بناء الخريطة</div>
        ")
        
        MAP_MOVE(التحرك في المسار باستخدام النموذج الذاتي)
        MAP_SENSE(إطلاق أشعة الاستشعار في كل الاتجاهات)
        MAP_COLLECT(جمع البيانات: الموقع الحالي + قراءات الأشعة)
        MAP_STORE(تخزين البيانات في ذاكرة الخريطة)
        MAP_TRAIN_PREPARE(سحب عينة من ذاكرة الخريطة)
        MAP_TRAIN_MODEL("
        <div style='font-weight:bold; font-size:12px;'>تدريب النموذج البيئي</div>
        <div style='text-align:left; font-size:11px;'>
        - يتعلم النموذج ربط كل موقع في الخريطة بشكل الجدران والحدود من حوله.
        </div>
        ")

        MAP_CHECK_COVERAGE{"
        <div style='font-weight:bold; font-size:12px;'>11. هل تم استكشاف كافٍ؟</div>
        "}
        
        MAP_MODEL_COMPLETE(("
        <div style='font-weight:bold; font-size:14px;'>12. اكتمال النموذج البيئي</div>
        <div style='text-align:left; font-size:12px;'>
        الذكاء الاصطناعي الآن لديه 'خريطة ذهنية' للمسار.
        </div>
        "))

        MAP_LOOP_START --> MAP_MOVE --> MAP_SENSE --> MAP_COLLECT --> MAP_STORE --> MAP_TRAIN_PREPARE --> MAP_TRAIN_MODEL --> MAP_CHECK_COVERAGE
        MAP_CHECK_COVERAGE -- لا، استمر في الاستكشاف --> MAP_LOOP_START
        MAP_CHECK_COVERAGE -- نعم، الخريطة مفصلة --> MAP_MODEL_COMPLETE
    end

    %% -----------------------------------------------------------------
    %% المرحلة الثالثة: التخطيط الواعي والتنفيذ (السباق الحقيقي)
    %% -----------------------------------------------------------------
    subgraph "المرحلة 3: دورة العمل الواعي (Perceive-Plan-Act-Learn)"
        style "المرحلة 3" fill:#9f9,stroke:#333,stroke-width:2px

        MAIN_LOOP("
        <div style='font-weight:bold; font-size:16px;'>13. بدء حلقة السباق الواعي</div>
        ")

        PERCEIVE("
        <div style='font-weight:bold; font-size:14px;'>أ. الإدراك (Perception)</div>
        <div style='text-align:left; font-size:12px;'>
        - تلقي الحالة الحالية (s) من اللعبة.<br/>
        - استخدام النموذج البيئي لفهم السياق (أنا على وشك دخول منعطف).
        </div>
        ")
        
        PLAN_MANAGER("
        <div style='font-weight:bold; font-size:14px;'>ب. التخطيط عالي المستوى (المدير)</div>
        <div style='text-align:left; font-size:12px;'>
        - المدير يحلل الموقف ويختار هدفًا فرعيًا (sub-goal).<br/>
        - مثال: 'الهدف الآن هو اجتياز المنعطف القادم بأسرع طريقة ممكنة'.<br/>
        - يسلم التحكم إلى الخبير المناسب (خبير الانجراف).
        </div>
        ")

        PLAN_EXPERT("
        <div style='font-weight:bold; font-size:14px;'>ج. التخطيط منخفض المستوى (الخبير)</div>
        <div style='text-align:left; font-size:12px;'>
        - الخبير المتخصص يقوم بـ 'المحاكاة الذهنية'.<br/>
        - يستخدم النموذج الذاتي لتجربة مئات سلاسل الأفعال بسرعة في 'خياله'.<br/>
        - يختار أفضل سلسلة حركات لتحقيق الهدف الفرعي الذي أعطاه المدير.
        </div>
        ")

        ACT("
        <div style='font-weight:bold; font-size:14px;'>د. التنفيذ (Action)</div>
        <div style='text-align:left; font-size:12px;'>
        - تنفيذ الفعل الأول فقط من الخطة التي تم تخيلها في اللعبة الحقيقية.
        </div>
        ")

        LEARN_FEEDBACK("
        <div style='font-weight:bold; font-size:14px;'>هـ. التعلم (Learning & Feedback)</div>
        <div style='text-align:left; font-size:12px;'>
        - ملاحظة النتيجة الحقيقية (s') والمكافأة (r).<br/>
        - تخزين التجربة الكاملة (s, goal, a, r, s') في ذاكرة المهمة.<br/>
        - <b>تحديث النموذج الذاتي:</b> مقارنة s' الحقيقية مع s' المتوقعة لتصحيح فهمه للفيزياء.<br/>
        - <b>تحديث الخبير:</b> استخدام المكافأة r لتحسين قدرته على تحقيق الأهداف الفرعية.<br/>
        - <b>تحديث المدير:</b> استخدام المكافأة r لتقييم ما إذا كان اختيار هذا الهدف الفرعي قرارًا جيدًا.
        </div>
        ")
        
        MAIN_LOOP --> PERCEIVE --> PLAN_MANAGER --> PLAN_EXPERT --> ACT --> LEARN_FEEDBACK --> MAIN_LOOP
    end

    %% -----------------------------------------------------------------
    %% ربط المراحل ببعضها البعض
    %% -----------------------------------------------------------------
    INIT_MEMORY --> SELF_START
    SELF_MODEL_COMPLETE --> MAP_START
    MAP_MODEL_COMPLETE --> MAIN_LOOP
```
