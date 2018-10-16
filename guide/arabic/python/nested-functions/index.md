---
title: Nested Functions in Python
localeTitle: وظائف متداخلة في بيثون
---
### مساحات

تمثل معلمات الدالة ، بالإضافة إلى أي متغيرات مرتبطة (بواسطة تخصيص أو بواسطة عبارات ملزمة أخرى ، مثل def) في نص الدالة ، مساحة الاسم المحلية للوظيفة ، والتي تعرف أيضًا باسم النطاق المحلي. ويعرف كل من هذه المتغيرات كمتغير محلي للدالة.

تعرف المتغيرات غير المحلية بالمتغيرات العامة (في غياب تعريفات الدالة المتداخلة ، والتي سنناقشها بعد قليل). المتغيرات العمومية هي سمات كائن الوحدة النمطية ، كما تم تغطيتها في "سمات كائنات الوحدة النمطية" في الصفحة 140. عندما يكون للمتغير المحلي الخاص بالوظيفة نفس الاسم كمتغير عمومي ، يشير هذا الاسم ، داخل نص الدالة ، إلى المتغير المحلي ، ليس العالم. نحن نعبر عن هذا بالقول أن المتغير المحلي يخفي المتغير الشامل الذي يحمل نفس الاسم في جسم الوظيفة.

### البيان العالمي

بشكل افتراضي ، أي متغير مرتبط داخل جسم دالة هو متغير محلي للدالة. إذا احتاجت إحدى الوظائف إلى إعادة بث بعض المتغيرات العامة ، فيجب أولاً يجب أن يكون بيان الوظيفة كما يلي:

معرفات عالمية

حيث المعرفات هي واحد أو أكثر من المعرفات مفصولة بفواصل (،). تشير المعرّفات المدرجة في بيان عالمي إلى المتغيرات العامة (أي سمات كائن الوحدة النمطية) التي تحتاج الدالة إلى إعادة بثها. على سبيل المثال ، يمكن تنفيذ عداد الدالة الذي رأيناه في "سمات أخرى لكائنات الدالة" في صفحة 73 باستخدام المتغير العام والمتغير العام ، بدلاً من سمة كائن الدالة:

\_count = 0 def counter (): عالمي \_ عدد \_count + = 1 عودة \_count

بدون العبارة العمومية ، سترفع الدالة العداد استثناء UnboundLocal- خطأ لأن \_count سيكون متغير محلي غير مهيأ (غير منضم). في حين أن البيان العالمي يمكّن هذا النوع من البرمجة ، فإن هذا النمط غالباً ما يكون غير متناسق وغير مرغوب فيه. كما ذكرت سابقًا ، عندما تريد تجميع بعض الحالات وبعض السلوكيات ، تكون الآليات الموجهة للكائنات في الفصل 5 عادةً أفضل.

لا تستخدم العمومية إذا كان جسم الدالة يستخدم فقط متغيرًا عامًا (بما في ذلك تحوير الكائن المرتبط بهذا المتغير إذا كان الكائن قابلاً للتغيير). استخدم عبارة عامة فقط في حالة قيام جسم الدالة بتكرار متغير عام (بشكل عام عن طريق تعيين اسم المتغير). كمسألة أسلوب ، لا تستخدم عالميًا إلا إذا كان ذلك ضروريًا تمامًا ، نظرًا لأن وجودها سيؤدي إلى أن يقرِّر برنامجك أن البيان موجود لغرض مفيد. على وجه الخصوص ، لا تستخدم عالميًا باستثناء العبارة الأولى في نص وظيفة.

{عنوان mospagebreak = وظائف متداخلة ونطاقات متداخلة}

تعرف عبارة def (def def) في جسم دالة دالة متداخلة ، وتعرف الدالة التي يتضمن جسمها def كوظيفة خارجية إلى الدالة المتداخلة. قد يدخل الرمز الموجود في جسم الدالة المتداخلة (ولكن ليس التكرار) المتغيرات المحلية لدالة خارجية ، والتي تعرف أيضًا باسم المتغيرات المجانية للدالة المتداخلة.

إن أبسط طريقة للسماح لدالة متداخلة بالوصول إلى قيمة لا تعتمد في الغالب على نطاقات متداخلة ، ولكن بدلاً من تمرير هذه القيمة بشكل صريح كواحدة من وسائط الدالة. إذا لزم الأمر ، يمكن ربط قيمة الوسيطة عندما يتم تعريف الدالة المتداخلة باستخدام القيمة على أنها القيمة الافتراضية لوسيطة اختيارية. فمثلا:

def percent1 (a، b، c): def pc (x، total = a + b + c): return (x \* 100.0) / total الطباعة "النسب المئوية هي:" ، أجهزة الكمبيوتر (أ) ، وأجهزة الكمبيوتر (ب) ، وأجهزة الكمبيوتر (ج)

إليك الوظيفة نفسها باستخدام النطاقات المتداخلة:

def percent2 (a، b، c): def pc (x): return (x \* 100.0) / (a ​​+ b + c) الطباعة "النسب المئوية هي:" ، أجهزة الكمبيوتر (أ) ، وأجهزة الكمبيوتر (ب) ، وأجهزة الكمبيوتر (ج)

في هذه الحالة المحددة ، يكون لدى النسبة المئوية 1 ميزة صغيرة: يحدث حساب a + b + c مرة واحدة فقط ، بينما يكرر الكمبيوتر الداخلي ذو الوظائف المئوية في الحصة ثلاث مرات. ومع ذلك ، إذا كانت الدالة الخارجية تقوم بتجريد المتغيرات المحلية الخاصة بها بين الاستدعاءات إلى الدالة المتداخلة ، فيمكن أن يكون تكرار الحساب ضروريًا. لذلك من المستحسن أن تكون على دراية بكلا النهجين ، واختيار الحالة الأكثر ملاءمة لكل حالة على حدة.

تعرف أيضًا الدالة المتداخلة التي تصل إلى القيم من المتغيرات المحلية الخارجية باسم الإغلاق. يوضح المثال التالي كيفية إنشاء إغلاق:

def\_adder def (augend): def add (addend): إضافة الإضافة + أوجند العودة إضافة

عمليات الإغلاق هي استثناء للقاعدة العامة بأن الآليات الموجهة للكائنات التي يغطيها الفصل الخامس هي أفضل طريقة لتجميع البيانات والشفرات معاً. عندما تحتاج على وجه التحديد إلى إنشاء كائنات قابلة للاستدعاء ، مع بعض المعلمات التي تم إصلاحها في وقت بناء الكائن ، يمكن أن تكون عمليات الإغلاق أكثر بساطة وفعالية من الفئات. على سبيل المثال ، تكون نتيجة make\_adder (7) دالة تقبل وسيطة واحدة وتضيف 7 إلى هذه الوسيطة. تعتبر الدالة الخارجية التي تعيد الإغلاق "مصنعًا" لأعضاء مجموعة من الوظائف المتميزة ببعض المعلمات ، مثل قيمة الوسيط المعجزة في المثال السابق ، وقد تساعدك في الغالب على تجنب تكرار الكود.

### تعبيرات لامدا

إذا كان نص الدالة عبارة تعبير واحد ، فيمكنك اختيار استبدال الوظيفة بنموذج التعبير lambda الخاص:

معلمات lambda: التعبير

تعبير lambda هو المعادل المجهول للدالة العادية التي يكون جسدها عبارة إرجاع واحدة. لاحظ أن بناء الجملة lambda لا يستخدم الكلمة الأساسية المرجعة. يمكنك استخدام تعبير lambda حيثما يمكنك استخدام مرجع لوظيفة. يمكن أن تكون lambda مفيدة في بعض الأحيان عندما تريد استخدام وظيفة بسيطة كحجة أو قيمة إرجاع. في ما يلي مثال يستخدم تعبير lambda كوسيطة لوظيفة التصفية المضمنة (المغطاة في الفلتر في الصفحة 161):

aList = \[1 ، 2 ، 3 ، 4 ، 5 ، 6 ، 7 ، 8 ، 9\] منخفض = 3 عالية = 7 عامل التصفية (lambda x، l = low، h = high: h> x> l، aList) # returns: \[4، 5، 6\]

وكبديل ، يمكنك دائمًا استخدام عبارة def محلية تعطي اسم الدالة كائنًا. يمكنك بعد ذلك استخدام هذا الاسم كوسيطة أو قيمة إرجاع. في ما يلي مثال الفلتر نفسه باستخدام عبارة def def:

aList = \[1 ، 2 ، 3 ، 4 ، 5 ، 6 ، 7 ، 8 ، 9\] منخفض = 3 عالية = 7 def ضمن _الحدود (القيمة ، l = low ، h = high): return h> value> l عامل التصفية (ضمن_ الحدود ، القائمة) # يرجع: \[4 ، 5 ، 6\]

في حين أن lambda يمكن أن تكون مفيدة في بعض الأحيان ، يفضل العديد من مستخدمي Python def ، وهو أكثر عمومية ، وقد يجعل كودك أكثر قابلية للقراءة إذا اخترت اسمًا معقولًا للدالة.

{mospagebreak title = Generators}

عندما يحتوي جسم الدالة على واحد أو أكثر من مرات حدوث ناتج الكلمة الرئيسية ، تُعرف الدالة باسم المولد. عند استدعاء مولد ، لا يتم تنفيذ نص الدالة. وبدلاً من ذلك ، يقوم استدعاء المولد بإرجاع كائن مكوّن خاص يلف جسم الوظيفة ، والمتغيرات المحلية (بما في ذلك المعلمات) ، ونقطة التنفيذ الحالية ، وهي بداية تشغيل الدالة.

عندما يتم استدعاء الأسلوب التالي لكائن التكرار هذا ، ينفذ جسم الدالة حتى بيان العائد التالي ، والذي يأخذ النموذج:

التعبير العائد

عند تنفيذ بيان العائد ، يتم "تنفيذ التعليمة" ، مع نقطة التنفيذ الحالية والمتغيرات المحلية سليمة ، ويتم إرجاع التعبير بعد العائد كنتيجة للطريقة التالية. عندما يتم استدعاء التالي مرة أخرى ، يستأنف تنفيذ جسم الوظيفة حيث توقفت ، مرة أخرى حتى بيان العائد التالي. في حالة انتهاء نص الدالة أو تنفيذ عبارة return ، يقوم المكافئ بإصدار استثناء StopIteration للإشارة إلى انتهاء التكرار. لا يمكن أن تحتوي عبارات الإرجاع في مولد على تعبيرات.

مولد هو وسيلة سهلة جدا لبناء مكرر. نظرًا لأن الطريقة الأكثر شيوعًا لاستخدام مكرر البيانات هي التكرار باستخدام عبارة for ، فإنك عادةً ما تتصل بمولد مثل هذا:

للمتغير في somegenerator (الحجج):

على سبيل المثال ، قل أنك تريد تسلسلًا من الأرقام من 1 إلى N ثم إلى 1 مرة أخرى. يمكن أن يساعد المولد في:

def updown (N): لـ x في xrange (1، N): yield x لـ x في xrange (N، 0، -1): الإنتاجية x لأني في updown (3): print i # printts: 1 2 3 2 1

هنا مولد يعمل إلى حد ما مثل وظيفة xrange المضمنة ، لكنه يعيد سلسلة من قيم الفاصلة العائمة بدلاً من تسلسل من الأعداد الصحيحة:

defange frange (start، stop، step = 1.0): بينما تبدأ <stop: بداية العائد start + = step

هذا المثال frange فقط يشبه إلى حد ما xrange لأنه ، من أجل البساطة ، فإنه يجعل الحجج تبدأ وتوقف إلزامي ، ويفترض بصمت الخطوة إيجابية.

تكون المولدات أكثر مرونة من الوظائف التي تعيد القوائم. قد يقوم المولد ببناء مكرر غير محدود ، بمعنى واحد يعيد سلسلة لا نهائية من النتائج (لاستخدامها فقط في الحلقات التي تنتهي بوسائل أخرى ، على سبيل المثال ، عبر بيان استراحة). علاوة على ذلك ، يعمل المكرر المبني بالمولدات على إجراء تقييم كسول: يحسب التكرار كل عنصر متتالي فقط عند وعند الحاجة ، في الوقت المناسب ، بينما تقوم الوظيفة المكافئة بإجراء جميع الحسابات مسبقًا وقد تتطلب كميات كبيرة من الذاكرة لاحتواء قائمة النتائج. لذلك ، إذا كان كل ما تحتاج إليه هو القدرة على التكرار على تتابع محسوب ، فمن الأفضل حساب التسلسل في المولد بدلاً من وظيفة تقوم بإرجاع قائمة. إذا احتاج المتصل إلى قائمة بجميع العناصر التي تم إنتاجها من قبل بعض المولدات المحدودة G (الوسائط) ، فيمكن للمتصل ببساطة استخدام التعليمة البرمجية التالية:

result\_list = list (G (الحجج))

### تعبيرات المولدات

تقدم Python 2.4 طريقة أكثر بساطة لترميز المولدات البسيطة بشكل خاص: تعبيرات المولدات ، والمعروفة باسم genexps. إن صيغة صيغة genEx تشبه إلى حدٍ ما الفهم المدرج بالقائمة (كما هو مشار إليه في "قائمة الفهم" في الصفحة 67) فيما عدا أنه يتم وضع genexp بين الأقواس (()) بدلاً من الأقواس (\[\])؛ تكون دلالات اللفافة نفسها مماثلة لتلك الخاصة بفهم القائمة المقابلة ، باستثناء أن جينسبيرت ينتج عنه مكرر ينتج عنصرًا واحدًا في كل مرة ، في حين أن فهم القائمة ينتج قائمة بجميع النتائج في الذاكرة (وبالتالي ، باستخدام genEx ، عندما المناسب ، يحفظ الذاكرة). على سبيل المثال ، لإلزام مربعات جميع الأعداد الصحيحة المكونة من رقم واحد ، في أي بايثون حديثة ، يمكنك التوليف sum (\[x _x for x in xrange (10)\])؛ في Python 2.4 ، يمكنك التعبير عن هذه الوظيفة بشكل أفضل ، وترميزها كمجموع (x_ x لـ x في xrange (10)) (فقط نفس ، ولكن حذف الأقواس) ، والحصول على نفس النتيجة بالضبط أثناء استهلاك ذاكرة أقل. لاحظ أن الأقواس التي تشير إلى استدعاء الدالة أيضا "القيام بواجب مضاعف" وأرفق genexp (لا حاجة لأقواس إضافية).

{عنوان mospagebreak = مولدات في Python 2.5}

في بيثون 2.5 ، يتم تعزيز المولدات بشكل أكبر ، مع إمكانية الحصول على قيمة (أو استثناء) من المتصل حيث يتم تنفيذ كل العائد. تسمح هذه الميزات المتقدمة للمولدات في 2.5 بتطبيق إجراءات مشاركة كاملة ، كما هو موضح في http://www.python.org/peps/pep-0342.html. التغيير الرئيسي هو ، في 2.5 ، العائد ليس عبارة ، بل تعبير ، لذلك له قيمة. عندما يستأنف المولد عن طريق استدعاء الأسلوب التالي ، فإن قيمة العائد المقابل هي بلا. لتمرير قيمة x إلى بعض المولدات g (بحيث يتلقى g قيمة العائد الذي يتم تعليقه) ، بدلاً من استدعاء g.next () ، يستدعي المتصل g.send (x) (استدعاء g.send (لا شيء) هو مجرد مثل استدعاء g.next ()). أيضا ، العائد المجرد بدون حجج ، في Python 2.5 ، يصبح قانوني ، ويعادل أن ينتج لا شيء.

هناك تحسينات أخرى في Python 2.5 للمولدات تتعلق بالاستثناءات ، وهي مشمولة في "تحسينات المولد" في الصفحة 126.

### العودية

وتدعم بايثون العودية (أي أن وظيفة بايثون يمكن أن تطلق على نفسها) ، لكن هناك حدًا لمدى عمق التكرار. افتراضياً ، يقطع Python العودية ويرفع استثناء RecursionLimitExceeded (المغطاة في "فئات الاستثناء القياسي" في الصفحة 130) عندما يكتشف أن مكدس الاستدعاءات العودية قد ذهب عبر عمق 1000. يمكنك تغيير حد العودية مع الدالة setrecursionlimit من sys الوحدة النمطية ، تغطيتها في setrecursionlimit على الصفحة 171.

ومع ذلك ، تغيير حد العودية لا يعطيك العودية غير محدود؛ يعتمد الحد الأقصى المطلق على النظام الأساسي الذي يعمل عليه البرنامج ، خاصةً على نظام التشغيل الأساسي ومكتبة وقت التشغيل C ، ولكنه عادةً بضعة آلاف من المستويات. في حالة تعطل مكالمات العودية ، تعطل برنامجك. مثل هذه العفوية الجامحة ، بعد استدعاء ل setrecursionlimit الذي يتجاوز قدرات المنصة ، هي واحدة من الطرق القليلة جدا التي يمكن أن يتعطل فيها برنامج بايثون - حقا ، من الصعب ، بدون شبكة الأمان المعتادة من آليات الاستثناء في Python. لذلك ، كن حذراً من محاولة إصلاح برنامج الذي يتم الحصول على استثناءات RecursionLimitExceeded عن طريق رفع حد العودية مرتفع للغاية مع setrecursionlimit. في أغلب الأحيان ، من الأفضل أن تبحث عن طرق لإزالة التكرار ، أو بشكل أكثر تحديدًا ، الحد من عمق العودية التي يحتاجها برنامجك.

يجب على القراء الذين يعرفون لغة Lisp ، أو Scheme ، أو لغات البرمجة الوظيفية أن يدركوا على وجه الخصوص أن Python لا يطبق أمثلية "إزالة الاستبعاد" ، وهو أمر مهم للغاية في هذه اللغات. في بايثون ، أي اتصال ، متكرر أم لا ، له نفس التكلفة من حيث الوقت ومساحة الذاكرة ، معتمدين فقط على عدد الوسيطات: التكلفة لا تتغير ، سواء كانت المكالمة "مكالمة خلفية" (بمعنى أن المكالمة هي آخر عملية ينفذها المتصل) أو أي مكالمة أخرى.