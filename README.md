#Arch3D-vision AI
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
