# Arch3D-vision-ai
Initial commit - added HTML file and related resources 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="author" content="Your Name or Company">
    <meta name="copyright" content="© 2025 Your Name or Company. All rights reserved.">
    <title>AI Architectural 3D Model Generator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            background-color: #f4f4f9;
        }
        h1 {
            margin-top: 20px;
            color: #333;
        }
        #app {
            width: 80%;
            max-width: 600px;
            text-align: center;
            margin-top: 20px;
        }
        input[type="file"] {
            margin-bottom: 20px;
        }
        button {
            padding: 10px 20px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        #output {
            margin-top: 20px;
            text-align: left;
        }
        .model-link {
            display: block;
            margin-top: 10px;
            color: #007bff;
            text-decoration: none;
        }
        .model-link:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <h1>AI Architectural 3D Model Generator</h1>
    <div id="app">
        <input type="file" id="uploadInput" accept="image/*">
        <button onclick="generate3DModel()">Generate 3D Model</button>
        <div id="output"></div>
        <div id="subscription"></div>
    </div>

    <footer>
        <p>© 2025 Your Name or Company. All rights reserved.</p>
        <p>Unauthorized use, reproduction, or distribution of this application is strictly prohibited.</p>
    </footer>

    <script>
        let isFreePeriod = true; // Control the free period

        async function generate3DModel() {
            const fileInput = document.getElementById('uploadInput');
            const outputDiv = document.getElementById('output');
            const subscriptionDiv = document.getElementById('subscription');
            outputDiv.innerHTML = ''; // Clear previous output

            // Check if free period is still active
            if (!isFreePeriod) {
                subscriptionDiv.innerHTML = '<p style="color: red;">The free trial has ended. Please subscribe to continue using the service.</p>';
                return;
            }

            if (!fileInput.files.length) {
                alert('Please upload a 2D architectural drawing.');
                return;
            }

            const file = fileInput.files[0];

            // Check file type
            if (!file.type.startsWith('image/')) {
                alert('Please upload a valid image file.');
                return;
            }

            const formData = new FormData();
            formData.append('file', file);

            try {
                outputDiv.innerHTML = '<p>Processing your 2D drawing...</p>';
                
                // Simulate sending the file to a backend AI service
                const response = await fetch('https://your-backend-api.com/generate-3d-model', {
                    method: 'POST',
                    body: formData
                });

                if (!response.ok) {
                    throw new Error(Server error: ${response.status});
                }

                const result = await response.json();

// Display download links for generated 3D models
                outputDiv.innerHTML = '<p>Generated 3D Models:</p>';
                result.models.forEach(model => {
                    const link = document.createElement('a');
                    link.href = model.url;
                    link.className = 'model-link';
                    link.textContent = model.format + ' File';
                    link.download = model.${model.format.toLowerCase()};
                    outputDiv.appendChild(link);
                });
            } catch (error) {
                outputDiv.innerHTML = <p style="color: red;">Error: ${error.message}</p>;
            }
        }

        // Simulate ending the free period after a certain time
        setTimeout(() => {
            isFreePeriod = false;
        }, 604800000); // 7 days in milliseconds
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="تحسينات لموقع Arch3D Vision AI">
    <title>Arch3D Vision AI</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            line-height: 1.6;
            scroll-behavior: smooth;
        }

        header {
            background-color: #34495e;
            color: white;
            padding: 1rem 2rem;
            text-align: center;
        }

        nav {
            display: flex;
            justify-content: center;
            background: #2ecc71;
            padding: 1rem;
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        nav a {
            margin: 0 1rem;
            text-decoration: none;
            color: white;
            font-weight: bold;
        }

        nav a:hover {
            text-decoration: underline;
        }

        section {
            padding: 2rem;
            text-align: center;
        }

        footer {
            background-color: #34495e;
            color: white;
            text-align: center;
            padding: 1rem;
            position: fixed;
            width: 100%;
            bottom: 0;
        }

        #back-to-top {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            display: none;
            background-color: #2ecc71;
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* تحسين التصميم للأجهزة المختلفة */
        @media (max-width: 768px) {
            nav {
                flex-direction: column;
            }

            nav a {
                margin: 0.5rem 0;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>مرحبًا في Arch3D Vision AI</h1>
        <p>استمتع بمساحة تصميم متكاملة</p>
    </header>
    
    <nav>
        <a href="#about">من نحن</a>
        <a href="#services">خدماتنا</a>
        <a href="#contact">اتصل بنا</a>
    </nav>
    
    <section id="about">
        <h2>من نحن</h2>
        <p>Arch3D Vision AI متخصص في تصميم المساحات لتحسين رؤيتك المستقبلية.</p>
    </section>
    
    <section id="services">
        <h2>خدماتنا</h2>
        <p>تصميم ثلاثي الأبعاد، تخطيط المساحات، والتحليل الذكي.</p>
    </section>
    
    <section id="contact">
        <h2>اتصل بنا</h2>
        <p>تواصل معنا للحصول على أفضل تصميم لمساحتك.</p>
    </section>
    
    <button id="back-to-top" title="الرجوع للأعلى">↑</button>

    <footer>
        &copy; 2025 Arch3D Vision AI - جميع الحقوق محفوظة
    </footer>
    
    <script>
        // زر الرجوع للأعلى
        const backToTopButton = document.getElementById('back-to-top');

        window.addEventListener('scroll', () => {
            if (window.scrollY > 300) {
                backToTopButton.style.display = 'block';
            } else {
                backToTopButton.style.display = 'none';
            }
        });

        backToTopButton.addEventListener('click', () => {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });

        // تأثيرات الروابط للتنقل السلس
        const navLinks = document.querySelectorAll('nav a');
        navLinks.forEach(link => {
            link.addEventListener('click', event => {
                event.preventDefault();
                const targetId = link.getAttribute('href').substring(1);
                const targetElement = document.getElementById(targetId);
                targetElement.scrollIntoView({ behavior: 'smooth' });
            });
        });
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="تحسينات لموقع Arch3D Vision AI">
    <title>Arch3D Vision AI</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            line-height: 1.6;
            scroll-behavior: smooth;
        }

        header {
            background-color: #34495e;
            color: white;
            padding: 1rem 2rem;
            text-align: center;
        }

        nav {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            background: #2ecc71;
            padding: 1rem;
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        nav a {
            margin: 0.5rem;
            text-decoration: none;
            color: white;
            font-weight: bold;
            padding: 0.5rem 1rem;
            border-radius: 5px;
        }

        nav a:hover {
            background-color: #27ae60;
        }

        section {
            padding: 2rem;
            text-align: center;
        }

        footer {
            background-color: #34495e;
            color: white;
            text-align: center;
            padding: 1rem;
            position: fixed;
            width: 100%;
            bottom: 0;
        }

        #back-to-top {
            position: fixed;
            bottom: 2rem;
            right: 2rem;
            display: none;
            background-color: #2ecc71;
            color: white;
            border: none;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* تحسين التصميم للأجهزة المحمولة */
        @media (max-width: 768px) {
            nav a {
                font-size: 0.9rem;
                padding: 0.3rem 0.8rem;
            }

            section {
                padding: 1rem;
            }

            footer {
                font-size: 0.9rem;
            }
        }

        @media (max-width: 480px) {
            nav {
                flex-direction: column;
                align-items: center;
            }

            nav a {
                font-size: 0.8rem;
                padding: 0.2rem 0.6rem;
            }

            header h1 {
                font-size: 1.5rem;
            }

            section {
                padding: 0.8rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>مرحبًا في Arch3D Vision AI</h1>
        <p>استمتع بمساحة تصميم متكاملة</p>
    </header>
    
    <nav>
        <a href="#about">من نحن</a>
        <a href="#services">خدماتنا</a>
        <a href="#contact">اتصل بنا</a>
    </nav>
    
    <section id="about">
        <h2>من نحن</h2>
        <p>Arch3D Vision AI متخصص في تصميم المساحات لتحسين رؤيتك المستقبلية.</p>
    </section>
    
    <section id="services">
        <h2>خدماتنا</h2>
        <p>تصميم ثلاثي الأبعاد، تخطيط المساحات، والتحليل الذكي.</p>
    </section>
    
    <section id="contact">
        <h2>اتصل بنا</h2>
        <p>تواصل معنا للحصول على أفضل تصميم لمساحتك.</p>
    </section>
    
    <button id="back-to-top" title="الرجوع للأعلى">↑</button>

    <footer>
        &copy; 2025 Arch3D Vision AI - جميع الحقوق محفوظة
    </footer>
    
    <script>
        // زر الرجوع للأعلى
        const backToTopButton = document.getElementById('back-to-top');

        window.addEventListener('scroll', () => {
            if (window.scrollY > 300) {
                backToTopButton.style.display = 'block';
            } else {
                backToTopButton.style.display = 'none';
            }
        });

        backToTopButton.addEventListener('click', () => {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });

        // التأكد من أن القائمة تعمل على الأجهزة المحمولة
        const navLinks = document.querySelectorAll('nav a');
        navLinks.forEach(link => {
            link.addEventListener('click', event => {
                event.preventDefault();
                const targetId = link.getAttribute('href').substring(1);
                const targetElement = document.getElementById(targetId);
                targetElement.scrollIntoView({ behavior: 'smooth' });
            });
        });
    </script>
</body>
</html>

          لتحسين أداء الموقع وجعله متوافقًا مع الهواتف المحمولة، يجب إضافة بعض التعديلات على الكود لضمان استجابة الموقع (Responsive Design). هذا يعني أن الموقع سيتكيف تلقائيًا مع أحجام الشاشات المختلفة، بما في ذلك الهواتف المحمولة والأجهزة اللوحية.

html
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="موقع Arch3D Vision AI للتصميم ثلاثي الأبعاد باستخدام الذكاء الاصطناعي">
    <meta name="keywords" content="تصميم ثلاثي الأبعاد, ذكاء اصطناعي, Arch3D, Vision AI">
    <meta name="author" content="Saly78793">
    <title>Arch3D Vision AI</title>
    <style>
        /* التصميم العام */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            line-height: 1.6;
            background-color: #f4f4f4;
            color: #333;
            direction: rtl;
        }

        header {
            background: #333;
            color: #fff;
            padding: 1rem 0;
            text-align: center;
        }

        header h1 {
            margin: 0;
            font-size: 2rem;
        }

        nav {
            background: #444;
            color: #fff;
            display: flex;
            justify-content: center;
            padding: 0.5rem 0;
        }

        nav a {
            color: #fff;
            text-decoration: none;
            margin: 0 1rem;
            font-size: 1rem;
        }

        nav a:hover {
            text-decoration: underline;
        }

        main {
            padding: 1rem;
        }

        footer {
            background: #333;
            color: #fff;
            text-align: center;
            padding: 1rem 0;
            position: relative;
            bottom: 0;
            width: 100%;
        }

        /* استعلامات الوسائط لتحسين الاستجابة */
        @media (max-width: 768px) {
            header h1 {
                font-size: 1.5rem;
            }

            nav {
                flex-direction: column;
                align-items: center;
            }

            nav a {
                margin: 0.5rem 0;
            }

            main {
                padding: 0.5rem;
            }
        }

        @media (max-width: 480px) {
            header h1 {
                font-size: 1.2rem;
            }

            nav a {
                font-size: 0.9rem;
            }

            main {
                font-size: 0.9rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>Arch3D Vision AI</h1>
    </header>
    <nav>
        <a href="#home">الرئيسية</a>
        <a href="#services">الخدمات</a>
        <a href="#about">عن الموقع</a>
        <a href="#contact">تواصل معنا</a>
    </nav>
    <main>
        <section id="home">
            <h2>مرحبًا بك في Arch3D Vision AI</h2>
            <p>نحن نقدم خدمات التصميم ثلاثي الأبعاد باستخدام تقنيات الذكاء الاصطناعي.</p>
        </section>
        <section id="services">
            <h2>خدماتنا</h2>
            <ul>
                <li>تصميم المباني ثلاثية الأبعاد</li>
                <li>تحليل البيانات باستخدام الذكاء الاصطناعي</li>
                <li>حلول الهندسة المعمارية</li>
            </ul>
        </section>
        <section id="about">
            <h2>عن الموقع</h2>
            <p>موقع Arch3D Vision AI هو منصة متخصصة في تقديم حلول التصميم المعماري باستخدام تقنيات الذكاء الاصطناعي.</p>
        </section>
        <section id="contact">
            <h2>تواصل معنا</h2>
            <p>للتواصل معنا، يرجى مراسلتنا عبر البريد الإلكتروني: <a href="mailto:info@arch3dvisionai.com">info@arch3dvisionai.com</a></p>
        </section>
    </main>
    <footer>
        <p>&copy; 2023 Arch3D Vision AI. جميع الحقوق محفوظة.</p>
    </footer>
</body>
</html>
