### دعم .clineignore

لتوفير المزيد من التحكم في الملفات التي يمكن لـ Cline الوصول إليها، قمنا بتنفيذ وظيفة `.clineignore`، مشابهة لـ `.gitignore`. هذا يتيح لك تحديد الملفات والدلائل التي يجب ألا يتمكن Cline من الوصول إليها أو معالجتها. هذا مفيد لـ:

*   **الخصوصية:** منع Cline من الوصول إلى الملفات الحساسة أو الخاصة في مساحة العمل الخاصة بك.
*   **الأداء:** استبعاد الدلائل أو الملفات الكبيرة التي لا تتعلق بمهامك، مما قد يحسن كفاءة Cline.
*   **إدارة السياق:** تركيز انتباه Cline على الأجزاء ذات الصلة من مشروعك.

**كيفية استخدام `.clineignore`**

1.  **إنشاء ملف `.clineignore`:** في الدليل الجذر لمساحة العمل الخاصة بك (نفس مستوى مجلد `.vscode`، أو الدليل العلوي الذي فتحته في VS Code)، قم بإنشاء ملف جديد باسم `.clineignore`.

2.  **تحديد أنماط التجاهل:** افتح ملف `.clineignore` وحدد الأنماط للملفات والدلائل التي تريد أن يتجاهلها Cline. النحو مشابه لـ `.gitignore`:

    *   كل سطر في الملف يمثل نمطًا.
    *   **تُدعم أنماط glob القياسية:**
        *   `*` تطابق صفر أو أكثر من الأحرف
        *   `?` تطابق حرفًا واحدًا
        *   `[]` تطابق نطاقًا من الأحرف
        *   `**` تطابق أي عدد من الدلائل والدلائل الفرعية.

    *   **أنماط الدلائل:** أضف `/` في نهاية النمط لتحديد دليل.
    *   **أنماط النفي:** ابدأ النمط بـ `!` لإلغاء تجاهل نمط تم تجاهله سابقًا.
    *   **التعليقات:** ابدأ السطر بـ `#` لإضافة تعليقات.

    **مثال على ملف `.clineignore`:**

    ```
    # تجاهل ملفات السجل
    *.log

    # تجاهل الدليل 'node_modules' بالكامل
    node_modules/

    # تجاهل جميع الملفات في الدليل 'temp' ودلائله الفرعية
    temp/**

    # لكن لا تجاهل 'important.log' حتى لو كان في الجذر
    !important.log

    # تجاهل أي ملف يسمى 'secret.txt' في أي دليل فرعي
    **/secret.txt
    ```

3.  **Cline يحترم `.clineignore` الخاص بك:** بمجرد حفظ ملف `.clineignore`، سيتعرف Cline تلقائيًا ويطبق هذه القواعد.

    *   **التحكم في الوصول إلى الملفات:** لن يتمكن Cline من قراءة محتوى الملفات المتجاهلة باستخدام أدوات مثل `read_file`. إذا حاولت استخدام أداة على ملف متجاهل، سيخبرك Cline بأن الوصول محجوب بسبب إعدادات `.clineignore`.
    *   **سرد الملفات:** عندما تطلب من Cline سرد الملفات في دليل (مثل استخدام `list_files`)، ستظل الملفات والدلائل المتجاهلة مدرجة، لكنها ستكون معلمة برمز **🔒** بجانب اسمها للإشارة إلى أنها متجاهلة. هذا يساعدك على فهم الملفات التي يمكن ولا يمكن لـ Cline التفاعل معها.

4.  **التحديثات الديناميكية:** يراقب Cline ملف `.clineignore` الخاص بك للتغييرات. إذا قمت بتعديل أو إنشاء أو حذف ملف `.clineignore` الخاص بك، سيقوم Cline تلقائيًا بتحديث قواعد التجاهل دون الحاجة إلى إعادة تشغيل VS Code أو الإضافة.

**خلاصة**

يوفر ملف `.clineignore` طريقة قوية ومرنة للتحكم في وصول Cline إلى ملفات مساحة العمل الخاصة بك، مما يعزز الخصوصية والأداء وإدارة السياق. من خلال الاستفادة من نحو `.gitignore` المألوف، يمكنك بسهولة تخصيص تركيز Cline على الأجزاء الأكثر أهمية من مشاريعك.