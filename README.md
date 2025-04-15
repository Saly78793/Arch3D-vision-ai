# Arch3D-vision-ai
// تغيير لون الأثاث
        function changeFurnitureColor() {
            const color = document.getElementById('furnitureColor').value;
            ctx.fillStyle = color;
            ctx.fillRect(100, 100, 50, 50); // تحديث لون الأثاث
        }

        // استيراد الملفات
        function uploadFiles() {
            const dwgFile = document.getElementById('dwgFile').files[0];
            const bdfFile = document.getElementById('bdfFile').files[0];

            if (dwgFile) {
                alert(تم رفع ملف DWG: ${dwgFile.name});
                // هنا يمكنك إضافة منطق لتحويل ملف DWG إلى نموذج ثلاثي الأبعاد باستخدام مكتبة مثل Three.js
            }

            if (bdfFile) {
                alert(تم رفع ملف BDF: ${bdfFile.name});
                // هنا يمكنك إضافة منطق لمعالجة ملف BDF
            }
        }

        // تشغيل إنشاء الصورة عند التحميل
        window.onload = generateImage;
    </script>
</body>
</html>
`
