# Arch3D-vision-ai
<footer>
  <p>© 2025 Your Name or Company. All rights reserved.</p>
  <p>Unauthorized use, reproduction, or distribution of this application is strictly prohibited.</p>
</footer>

<script>
  let isFreePeriod = true; // للتحكم بفترة الاستخدام المجاني

  async function generate3DModel() {
    const fileInput = document.getElementById('uploadInput');
    const outputDiv = document.getElementById('output');
    const subscriptionDiv = document.getElementById('subscription');
    outputDiv.innerHTML = ''; // مسح المخرجات السابقة

    // التحقق من بقاء فترة الاستخدام المجاني
    if (!isFreePeriod) {
      subscriptionDiv.innerHTML = '<p style="color: red;">The free trial has ended. Please subscribe to continue using the service.</p>';
      return;
    }

    if (!fileInput.files.length) {
      alert('Please upload a 2D architectural drawing.');
      return;
    }

    const file = fileInput.files[0];

    // التحقق من نوع الملف
    if (!file.type.startsWith('image/')) {
      alert('Please upload a valid image file.');
      return;
    }

    const formData = new FormData();
    formData.append('file', file);

    try {
      outputDiv.innerHTML = '<p>Processing your 2D drawing...</p>';

      // إرسال الملف إلى خدمة الذكاء الاصطناعي لإنتاج النموذج ثلاثي الأبعاد
      const response = await fetch('https://your-backend-api.com/generate-3d-model', {
        method: 'POST',
        body: formData
      });

      if (!response.ok) {
        // تم تعديل هذه الجملة لتكون بصياغة صحيحة
        throw new Error("Server error: " + response.status);
      }

      const result = await response.json();

      // عرض النتيجة بطريقة مرتبة (يمكن تخصيص العرض بحسب صيغة البيانات المرجعة)
      outputDiv.innerHTML = '<p>3D Model generated successfully!</p><pre>' + JSON.stringify(result, null, 2) + '</pre>';
    } catch (error) {
      console.error('Error generating 3D model:', error);
      outputDiv.innerHTML = '<p style="color: red;">An error occurred while generating the 3D model. Please try again later.</p>';
    }
  }
</script>
