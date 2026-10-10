<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة مدرسة WE للتكنولوجيا التطبيقية</title>
    <style>
        :root {
            --we-purple: #3f0071;
            --we-cyan: #00e1ff;
            --we-dark: #090a0f;
            --card-bg: rgba(255, 255, 255, 0.96);
            --text-color: #222;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--we-dark);
            color: var(--text-color);
            position: relative;
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* خلفية تفصيلية متقدمة */
        .tech-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
            background: 
                radial-gradient(circle at 15% 20%, rgba(0, 225, 255, 0.12) 0%, transparent 40%),
                radial-gradient(circle at 85% 80%, rgba(79, 0, 153, 0.2) 0%, transparent 45%),
                linear-gradient(135deg, #090a0f 0%, #1a0033 50%, #001a2c 100%);
        }

        .tech-background::before {
            content: "WE  CONNECT  TECH  DATA  FUTURE  NETWORK  AI  CYBER  WE";
            position: absolute;
            top: -10%;
            left: -10%;
            width: 120%;
            height: 120%;
            font-size: 110px;
            font-weight: 900;
            color: rgba(255, 255, 255, 0.015);
            line-height: 1.8;
            word-spacing: 50px;
            transform: rotate(-15deg);
            white-space: pre-wrap;
        }

        .tech-background::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(0, 225, 255, 0.04) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 225, 255, 0.04) 1px, transparent 1px);
            background-size: 40px 40px;
        }

        /* شاشة تسجيل الدخول */
        #login-screen {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            position: relative;
            z-index: 2;
        }

        .login-card {
            background: var(--card-bg);
            padding: 40px;
            border-radius: 16px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.6), 0 0 20px rgba(0, 225, 255, 0.2);
            width: 100%;
            max-width: 420px;
            text-align: center;
            border-top: 6px solid var(--we-cyan);
        }

        .login-card .logo-badge {
            background: linear-gradient(135deg, var(--we-purple), #0055ff);
            color: white;
            display: inline-block;
            padding: 8px 20px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 18px;
            margin-bottom: 15px;
            letter-spacing: 2px;
        }

        .login-card h2 {
            margin-bottom: 5px;
            color: #1a0033;
        }

        .login-card p {
            color: #666;
            margin-bottom: 25px;
            font-size: 14px;
        }

        .form-group {
            margin-bottom: 20px;
            text-align: right;
        }

        .form-group label {
            display: block;
            margin-bottom: 6px;
            font-weight: bold;
            color: #444;
            font-size: 14px;
        }

        .form-group input {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            transition: border-color 0.3s;
        }

        .form-group input:focus {
            border-color: var(--we-cyan);
            outline: none;
        }

        .btn {
            background: linear-gradient(135deg, #0055ff, var(--we-cyan));
            color: white;
            border: none;
            padding: 12px;
            width: 100%;
            border-radius: 8px;
            font-size: 16px;
            cursor: pointer;
            font-weight: bold;
            box-shadow: 0 5px 15px rgba(0, 225, 255, 0.3);
            transition: transform 0.2s, opacity 0.3s;
        }

        .btn:hover {
            opacity: 0.95;
            transform: translateY(-2px);
        }

        .error-msg {
            color: #ff3333;
            margin-top: 15px;
            font-size: 14px;
            font-weight: bold;
        }

        /* التطبيق الرئيسي */
        #app-screen {
            display: none;
            min-height: 100vh;
            flex-direction: column;
            position: relative;
            z-index: 2;
        }

        header {
            background: rgba(15, 12, 41, 0.9);
            backdrop-filter: blur(10px);
            color: white;
            padding: 15px 35px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 3px solid var(--we-cyan);
            box-shadow: 0 4px 20px rgba(0,0,0,0.5);
        }

        header .header-title {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        header h1 {
            font-size: 20px;
            color: var(--we-cyan);
            letter-spacing: 1px;
        }

        header .we-mini-logo {
            background: var(--we-cyan);
            color: #000;
            font-weight: 900;
            padding: 4px 10px;
            border-radius: 6px;
            font-size: 14px;
        }

        nav button {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 14px;
            margin-left: 10px;
            cursor: pointer;
            padding: 8px 15px;
            border-radius: 6px;
            transition: all 0.3s;
        }

        nav button:hover, nav button.active {
            background: var(--we-cyan);
            color: #000;
            border-color: var(--we-cyan);
            font-weight: bold;
        }

        .main-content {
            flex: 1;
            padding: 30px;
            max-width: 1100px;
            margin: 0 auto;
            width: 100%;
        }

        .tab-content {
            display: none;
            background: rgba(255, 255, 255, 0.95);
            padding: 30px;
            border-radius: 14px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.4);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .tab-content.active {
            display: block;
        }

        h3 {
            margin-bottom: 20px;
            color: var(--we-purple);
            border-right: 5px solid var(--we-cyan);
            padding-right: 12px;
            font-size: 22px;
        }

        /* المناهج التعليمية وتنسيق اللينكات */
        .lesson-card {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 15px;
            border: 1px solid #e0e0e0;
            border-left: 6px solid var(--we-purple);
        }

        .lesson-card h4 { color: var(--we-purple); margin-bottom: 6px; font-size: 18px; }
        .lesson-card p { color: #555; line-height: 1.6; margin-bottom: 12px; }
        
        .yt-link {
            display: inline-block;
            background-color: #ff0000;
            color: white;
            padding: 6px 14px;
            border-radius: 6px;
            text-decoration: none;
            font-size: 13px;
            font-weight: bold;
            transition: opacity 0.2s;
        }
        .yt-link:hover {
            opacity: 0.85;
        }

        /* شاشة الألعاب الـ 10 */
        .games-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(210px, 1fr));
            gap: 15px;
            margin-bottom: 25px;
        }

        .game-btn {
            background: #f1f3f5;
            border: 2px solid #d1d8e0;
            padding: 15px;
            border-radius: 10px;
            font-size: 14px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
            color: #333;
        }

        .game-btn:hover {
            background: var(--we-cyan);
            color: #000;
            border-color: #0099bb;
            transform: translateY(-3px);
        }

        .game-container {
            background: #fdfdfd;
            border: 2px dashed #0099bb;
            padding: 25px;
            border-radius: 12px;
            margin-top: 15px;
            display: none;
        }

        .game-container.active {
            display: block;
        }

        .game-box input {
            padding: 10px;
            border-radius: 6px;
            border: 1px solid #ccc;
            margin: 8px 0;
            width: 200px;
        }

        /* منظم اليوم */
        .todo-input-group {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        .todo-input-group input {
            flex: 1;
            padding: 12px 15px;
            border: 1px solid #ccc;
            border-radius: 8px;
            font-size: 15px;
        }

        ul { list-style: none; }

        ul li {
            background: #f8f9fa;
            padding: 14px 18px;
            border-radius: 8px;
            margin-bottom: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid #e5e5e5;
            font-weight: 500;
        }

        ul li button {
            background: #ff4757;
            color: white;
            border: none;
            padding: 6px 14px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <!-- الخلفية التقنية التفصيلية -->
    <div class="tech-background"></div>

    <!-- شاشة تسجيل الدخول -->
    <div id="login-screen">
        <div class="login-card">
            <div class="logo-badge">WE SCHOOL</div>
            <h2>بوابة دخول الطلاب</h2>
            <p>منصة مدرسة WE للتكنولوجيا التطبيقية</p>
            <div class="form-group">
                <label for="username">اسم المستخدم (Username)</label>
                <input type="text" id="username" placeholder="أدخل اسم المستخدم">
            </div>
            <div class="form-group">
                <label for="password">كلمة المرور (Password)</label>
                <input type="password" id="password" placeholder="أدخل كلمة المرور">
            </div>
            <button class="btn" type="button" onclick="login()">تسجيل الدخول</button>
            <div id="error" class="error-msg"></div>
        </div>
    </div>

    <!-- التطبيق الرئيسي -->
    <div id="app-screen">
        <header>
            <div class="header-title">
                <span class="we-mini-logo">WE</span>
                <h1>منصة تكنولوجيا المستقبل</h1>
            </div>
            <nav>
                <button class="active" onclick="switchTab('courses', this)">المناهج واليوتيوب</button>
                <button onclick="switchTab('break', this)">استراحة البريك (10 ألعاب)</button>
                <button onclick="switchTab('planner', this)">منظم اليوم</button>
                <button onclick="logout()" style="color: #ff8a80;">خروج</button>
            </nav>
        </header>

        <div class="main-content">
            <!-- تبويب المناهج والشروحات -->
            <div id="courses" class="tab-content active">
                <h3>المناهج الدراسية مع روابط الشرح الحقيقية</h3>
                
                <div class="lesson-card">
                    <h4>شرح math مبسط</h4>
                    <p>شرح مبسط لتمارين النسبة والتناسب (Ratio and Proportion) وخصائصها لطلاب مدارس التكنولوجيا التطبيقية.</p>
                    <a href="https://youtu.be/yJy9M7PIc3k?si=pYCeQTMyiFD0eTt-" target="_blank" class="yt-link">▶ مشاهدة شرح الـ Math على يوتيوب</a>
                </div>

                <div class="lesson-card">
                    <h4>شرح مبسط لـ Motherboard (اللوحة الأم ومكونات الكمبيوتر)</h4>
                    <p>استعراض مبسط ومختصر لأهم مكونات الكمبيوتر الداخلية ووظيفة اللوحة الأم (Motherboard) وباقي الوحدات.</p>
                    <a href="https://youtu.be/ppuxNaDz-Gc?si=KUUZ-VxrAzvcwtxu" target="_blank" class="yt-link">▶ مشاهدة شرح المذر بورد على يوتيوب</a>
                </div>
            </div>

            <!-- تبويب استراحة البريك (10 ألعاب ذكاء) -->
            <div id="break" class="tab-content">
                <h3>اختر لعبة لتجديد نشاط عقلك وقت البريك:</h3>
                
                <div class="games-grid">
                    <button class="game-btn" onclick="openGame(1)">1. تخمين الرقم السري</button>
                    <button class="game-btn" onclick="openGame(2)">2. حجر النرد السريع</button>
                    <button class="game-btn" onclick="openGame(3)">3. اختبار سرعة التفاعل</button>
                    <button class="game-btn" onclick="openGame(4)">4. تحدي الجمع الذهني</button>
                    <button class="game-btn" onclick="openGame(5)">5. تخمين لون الحظ</button>
                    <button class="game-btn" onclick="openGame(6)">6. عداد إبداعك اليومي</button>
                    <button class="game-btn" onclick="openGame(7)">7. اختبار الذاكرة الرقمية</button>
                    <button class="game-btn" onclick="openGame(8)">8. حجر - ورقة - مقص</button>
                    <button class="game-btn" onclick="openGame(9)">9. حاسبة عمرك بالدقائق</button>
                    <button class="game-btn" onclick="openGame(10)">10. رسالة التحفيز التقني</button>
                </div>

                <!-- حاويات الألعاب -->
                <div id="game-1" class="game-container">
                    <h4>1. لعبة تخمين الرقم</h4>
                    <p>اختر رقماً من 1 إلى 10:</p>
                    <input type="number" id="g1-input" placeholder="اكتب رقم">
                    <button class="btn" style="width:auto; padding: 6px 15px;" onclick="playG1()">تأكيد</button>
                    <p id="g1-res" style="margin-top:10px; font-weight:bold;"></p>
                </div>

                <div id="game-2" class="game-container">
                    <h4>2. حجر النرد السريع</h4>
                    <p>اضغط للرمي والحصول على رقم عشوائي (1 إلى 6):</p>
                    <button class="btn" style="width:auto; padding: 6px 15px;" onclick="playG2()">ارْمِ النرد</button>
                    <p id="g2-res" style="margin-top:10px; font-weight:bold;"></p>
                </div>

                <div id="game-3" class="game-container">
                    <h4>3. اختبار سرعة التفاعل</h4>
                    <p>اضغط بأسرع ما يمكن لتسجيل سرعة رد فعلك!</p>
                    <button class="btn" style="width:auto; padding: 6px 15px; background: #2ed573;" onclick="playG3()">اضغط هنا الآن</button>
                    <p id="g3-res" style="margin-top:10px; font-weight:bold;"></p>
                </div>

                <div id="game-4" class="game-container">
                    <h4>4. تحدي الجمع الذهني</h4>
                    <p>ما ناتج جمع: <span id="math-q" style="color:var(--we-purple); font-weight:bold;"></span> ؟</p>
                    <input type="number" id="g4-input" placeholder="الناتج">
                    <button class="btn" style="width:auto; padding: 6px 15px;" onclick="playG4()">تحقق</button>
                    <p id="g4-res" style="margin-top:10px; font-weight:bold;"></p>
                </div>

                <div id="game-5" class="game-container">
                    <h4>5. تخمين لون الحظ</h4>
                    <p>اختر اللون (أحمر أم أزرق):</p>
                    <button class="btn" style="width:auto; background:#ff4757;" onclick="playG5('أحمر')">أحمر</button>
                    <button class="btn" style="width:auto; background:#1e90ff;" onclick="playG5('أزرق')">أزرق</button>
                    <p id="g5-res" style="margin-top:10px; font-weight:bold;"></p>
                </div>

                <div id="game-6" class="game-container">
                    <h4>6. عداد إبداعك اليومي</h4>
                    <p>اكتشف نسبة نشاطك البرمجي اليوم:</p>
                    <button class="btn" style="width:auto; padding: 6px 15px;" onclick="playG6()">اكشف النسبة</button>
                    <p id="g6-res" style="margin-top:10px; font-weight:bold;"></p>
                </div>

                <div id="game-7" class="game-container">
                    <h4>7. اختبار الذاكرة الرقمية</h4>
                    <p>احفظ الكود التالي: <span style="color:var(--we-purple); font-weight:bold;">8492</span></p>
                    <input type="text" id="g7-input" placeholder="اكتب الكود المذكور">
                    <button class="btn" style="width:auto; padding: 6px 15px;" onclick="playG7()">فحص</button>
                    <p id="g7-res" style="margin-top:10px; font-weight:bold;"></p>
                </div>

                <div id="game-8" class="game-container">
                    <h4>8. لعبة حجر، ورقة، مقص</h4>
                    <p>اختر حركتك ضد النظام:</p>
                    <button class="btn" style="width:auto;" onclick="playG8('حجر')">حجر</button>
                    <button class="btn" style="width:auto;" onclick="playG8('ورقة')">ورقة</button>
                    <button class="btn" style="width:auto;" onclick="playG8('مقص')">مقص</button>
                    <p id="g8-res" style="margin-top:10px; font-weight:bold;"></p>
                </div>

                <div id="game-9" class="game-container">
                    <h4>9. حاسبة عمرك بالدقائق</h4>
                    <p>اكتب عمرك الحالي بالسنوات:</p>
                    <input type="number" id="g9-input" placeholder="عمرك بالسنوات">
                    <button class="btn" style="width:auto; padding: 6px 15px;" onclick="playG9()">احسب</button>
                    <p id="g9-res" style="margin-top:10px; font-weight:bold;"></p>
                </div>

                <div id="game-10" class="game-container">
                    <h4>10. رسالة التحفيز التقني</h4>
                    <p>احصل على عبارة تحفيزية لمهندس المستقبل:</p>
                    <button class="btn" style="width:auto; padding: 6px 15px;" onclick="playG10()">الحصول على رسالة</button>
                    <p id="g10-res" style="margin-top:10px; font-weight:bold; color:var(--we-purple);"></p>
                </div>

            </div>

            <!-- تبويب منظم اليوم -->
            <div id="planner" class="tab-content">
                <h3>جدول تنظيم مهام الطالب اليومية</h3>
                <div class="todo-input-group">
                    <input type="text" id="taskInput" placeholder="أضف مهمة جديدة (مثلاً: مشاهدة درس Math وحل الواجب)">
                    <button class="btn" style="width: auto; padding: 12px 25px;" onclick="addTask()">إضافة للمنظم</button>
                </div>
                <ul id="taskList">
                    <!-- المهام تظهر هنا -->
                </ul>
            </div>
        </div>
    </div>

    <script>
        // بيانات الدخول الرسمية للمشروع
        const correctUser = "A-1";
        const correctPass = "o90po90p";

        function login() {
            const uInput = document.getElementById("username");
            const pInput = document.getElementById("password");
            const err = document.getElementById("error");

            if (!uInput || !pInput || !err) return;

            let u = uInput.value.trim();
            let p = pInput.value.trim();

            if (u === correctUser && p === correctPass) {
                err.innerText = "";
                document.getElementById("login-screen").style.display = "none";
                document.getElementById("app-screen").style.display = "flex";
            } else {
                err.innerText = "خطأ في اسم المستخدم أو كلمة المرور!";
            }
        }

        function logout() {
            document.getElementById("login-screen").style.display = "flex";
            document.getElementById("app-screen").style.display = "none";
            document.getElementById("username").value = "";
            document.getElementById("password").value = "";
            document.getElementById("error").innerText = "";
        }

        function switchTab(tabId, btn) {
            let tabs = document.querySelectorAll('.tab-content');
            tabs.forEach(t => t.classList.remove('active'));

            let buttons = document.querySelectorAll('nav button');
            buttons.forEach(b => b.classList.remove('active'));

            let targetTab = document.getElementById(tabId);
            if (targetTab) targetTab.classList.add('active');
            if (btn) btn.classList.add('active');
        }

        function openGame(gameNum) {
            let containers = document.querySelectorAll('.game-container');
            containers.forEach(c => c.classList.remove('active'));

            let target = document.getElementById('game-' + gameNum);
            if(target) target.classList.add('active');

            if(gameNum === 4) initMathGame();
        }

        // الألعاب
        let secret1 = Math.floor(Math.random() * 10) + 1;
        function playG1() {
            let val = parseInt(document.getElementById("g1-input").value);
            let res = document.getElementById("g1-res");
            if(val === secret1) {
                res.style.color = "green";
                res.innerText = "🎉 برافو! خمنت الرقم الصحيح.";
                secret1 = Math.floor(Math.random() * 10) + 1;
            } else if(val < secret1) {
                res.style.color = "orange";
                res.innerText = "📈 الرقم أعلى من كده!";
            } else {
                res.style.color = "orange";
                res.innerText = "📉 الرقم أقل من كده!";
            }
        }

        function playG2() {
            let dice = Math.floor(Math.random() * 6) + 1;
            document.getElementById("g2-res").innerText = "🎲 نتيجة رمي النرد: " + dice;
        }

        let startTime;
        function playG3() {
            startTime = new Date().getTime();
            setTimeout(() => {
                document.getElementById("g3-res").innerText = "⏱️ تم تسجيل سرعة رد فعلك بنجاح!";
            }, 200);
        }

        let numA, numB;
        function initMathGame() {
            numA = Math.floor(Math.random() * 20) + 1;
            numB = Math.floor(Math.random() * 20) + 1;
            let mathQ = document.getElementById("math-q");
            if (mathQ) mathQ.innerText = `${numA} + ${numB}`;
        }
        function playG4() {
            let ans = parseInt(document.getElementById("g4-input").value);
            let res = document.getElementById("g4-res");
            if(ans === (numA + numB)) {
                res.style.color = "green";
                res.innerText = "✨ إجابة صحيحة وعبقرية!";
                initMathGame();
            } else {
                res.style.color = "red";
                res.innerText = "❌ حاول مرة أخرى.";
            }
        }

        function playG5(choice) {
            let colors = ['أحمر', 'أزرق'];
            let luck = colors[Math.floor(Math.random() * colors.length)];
            let res = document.getElementById("g5-res");
            if(choice === luck) {
                res.style.color = "green";
                res.innerText = `🎯 مبروك! اخترت اللون الصحيح (${luck}).`;
            } else {
                res.style.color = "orange";
                res.innerText = `❌ لون الحظ كان (${luck}).`;
            }
        }

        function playG6() {
            let luckNum = Math.floor(Math.random() * 101);
            document.getElementById("g6-res").innerText = `⚡ نسبة كفاءتك البرمجية اليوم: ${luckNum}%`;
        }

        function playG7() {
            let val = document.getElementById("g7-input").value;
            let res = document.getElementById("g7-res");
            if(val === "8492") {
                res.style.color = "green";
                res.innerText = "🧠 ذاكرتك ممتازة!";
            } else {
                res.style.color = "red";
                res.innerText = "❌ الكود الصحيح هو 8492.";
            }
        }

        function playG8(playerChoice) {
            let options = ['حجر', 'ورقة', 'مقص'];
            let compChoice = options[Math.floor(Math.random() * options.length)];
            let res = document.getElementById("g8-res");
            if(playerChoice === compChoice) {
                res.style.color = "orange";
                res.innerText = `🤝 تعادل! الكمبيوتر اختار (${compChoice})`;
            } else if(
                (playerChoice === 'حجر' && compChoice === 'مقص') ||
                (playerChoice === 'ورقة' && compChoice === 'حجر') ||
                (playerChoice === 'مقص' && compChoice === 'ورقة')
            ) {
                res.style.color = "green";
                res.innerText = `🎉 فزت! الكمبيوتر اختار (${compChoice})`;
            } else {
                res.style.color = "red";
                res.innerText = `😢 خسرت! الكمبيوتر اختار (${compChoice})`;
            }
        }

        function playG9() {
            let age = parseFloat(document.getElementById("g9-input").value);
            let res = document.getElementById("g9-res");
            if(isNaN(age) || age <= 0) {
                res.innerText = "الرجاء إدخال عمر صحيح.";
            } else {
                let mins = age * 365 * 24 * 60;
                res.style.color = "blue";
                res.innerText = `⏳ عمرك يعادل تقريباً: ${mins.toLocaleString()} دقيقة من المعرفة!`;
            }
        }

        function playG10() {
            let msgs = [
                "🚀 مبرمج الغد يبدأ اليوم، استمر في التعلم!",
                "💡 كل سطر برمجي يفتح لك باباً جديداً من الإمكانيات.",
                "⭐ مدرسة WE تفتح لك أبواب التكنولوجيا التطبيقية، فكن على قدر المسؤولية.",
                "🔥 العقول العظيمة تصنع البرمجيات التي تغير العالم!"
            ];
            document.getElementById("g10-res").innerText = msgs[Math.floor(Math.random() * msgs.length)];
        }

        // منظم اليوم
        function addTask() {
            let taskInput = document.getElementById("taskInput");
            let text = taskInput.value.trim();
            if(text === "") return;

            let ul = document.getElementById("taskList");
            let li = document.createElement("li");
            li.innerHTML = `<span>${text}</span> <button onclick="this.parentElement.remove()">إنجاز / حذف</button>`;
            ul.appendChild(li);

            taskInput.value = "";
        }
    </script>
</body>
</html>
