# Arch3D-vision-ai

  ```html
  <div id="loader" style="display: none;">جاري الإنشاء...</div>
  ```

  ```css
  #loader {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 20px;
      color: #333;
  }
  ```

  ```javascript
  document.getElementById('createButton').addEventListener('click', function () {
      // إظهار المؤشر
      document.getElementById('loader').style.display = 'block';

      // تنفيذ العملية (مثل إرسال البيانات إلى الخادم)
      performCreation().then(() => {
          // إخفاء المؤشر عند الانتهاء
          document.getElementById('loader').style.display = 'none';
      }).catch((error) => {
          console.error('حدث خطأ:', error);
          document.getElementById('loader').style.display = 'none';
      });
  });
  ```

---

  ```html
  <div id="result"></div>
  ```

  ```javascript
  function displayResult(data) {
      const resultElement = document.getElementById('result');
      resultElement.innerHTML = `<p>${data.message}</p>`;
  }
  ```


  ```javascript
  function performCreation() {
      return new Promise((resolve, reject) => {
          // محاكاة عملية طويلة الأمد
          setTimeout(() => {
              resolve({ message: 'تم الإنشاء بنجاح!' });
          }, 2000); // انتظر ثانيتين
      });
  }

  performCreation().then((data) => {
      displayResult(data);
  }).catch((error) => {
      console.error('حدث خطأ:', error);
  });
  ```
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
