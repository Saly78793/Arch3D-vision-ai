# Arch3D-vision-ai
<footer>
    <p>© 2025 Your Name or Company. All rights reserved.</p>
    <p>Unauthorized use, reproduction, or distribution of this application is strictly prohibited.</p>
</footer>

<!-- Add external libraries -->
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/lodash/lodash.min.js"></script>

<script>
    let isFreePeriod = true; // Control the free period

    async function generate3DModel() {
        const fileInput = document.getElementById('uploadInput');
        const outputDiv = document.getElementById('output');
        const subscriptionDiv = document.getElementById('subscription');
        const loadingDiv = document.getElementById('loading');
        outputDiv.innerHTML = ''; // Clear previous output
        loadingDiv.style.display = 'block'; // Show loading indicator

        // Check if free period is still active
        if (!isFreePeriod) {
            loadingDiv.style.display = 'none'; // Hide loading indicator
            subscriptionDiv.innerHTML = '<p style="color: red;">The free trial has ended. Please subscribe to continue using the service.</p>';
            return;
        }

        if (!fileInput.files.length) {
            loadingDiv.style.display = 'none'; // Hide loading indicator
            alert('Please upload a 2D architectural drawing.');
            return;
        }

        const file = fileInput.files[0];

        // Check file type
        if (!file.type.startsWith('image/')) {
            loadingDiv.style.display = 'none'; // Hide loading indicator
            alert('Please upload a valid image file.');
            return;
        }

        const formData = new FormData();
        formData.append('file', file);

        try {
            // Simulate sending the file to a backend AI service
            const response = await axios.post('https://your-backend-api.com/generate-3d-model', formData, {
                headers: {
                    'Content-Type': 'multipart/form-data'
                }
            });

            const result = response.data;

            if (_.has(result, 'modelUrl')) {
                outputDiv.innerHTML = `
                    <p>Your 3D model has been successfully generated.</p>
                    <iframe src="${result.modelUrl}" width="600" height="400" style="border:none;"></iframe>
                `;
            } else {
                outputDiv.innerHTML = `<p>Error: Unable to generate the 3D model. Please try again.</p>`;
            }
        } catch (error) {
            console.error('Error:', error);
            if (error.code === 'ERR_NETWORK') {
                outputDiv.innerHTML = `<p style="color: red;">Network Error: Unable to connect to the server. Please check your internet connection and try again.</p>`;
            } else if (error.response) {
                // Server responded with a status code outside the 2xx range
                outputDiv.innerHTML = `<p style="color: red;">Server Error: ${error.response.status} - ${error.response.statusText}</p>`;
            } else {
                outputDiv.innerHTML = `<p style="color: red;">An unexpected error occurred: ${error.message}</p>`;
            }
        } finally {
            loadingDiv.style.display = 'none'; // Hide loading indicator
        }
    }

    // Function to toggle free period for demonstration purposes
    function toggleFreePeriod() {
        isFreePeriod = !isFreePeriod;
        const subscriptionDiv = document.getElementById('subscription');
        if (!isFreePeriod) {
            subscriptionDiv.innerHTML = '<p style="color: red;">The free trial has ended. Please subscribe to continue using the service.</p>';
        } else {
            subscriptionDiv.innerHTML = '<p style="color: green;">You are in the free trial period. Enjoy!</p>';
        }
    }
</script>

<!-- HTML structure -->
<div id="app">
    <h1>2D to 3D Model Generator</h1>
    <input type="file" id="uploadInput" accept="image/*">
    <button onclick="generate3DModel()">Generate 3D Model</button>
    <div id="loading" style="display: none;">
        <p>Processing your 2D drawing... <img src="https://i.imgur.com/kOn7HJt.gif" alt="Loading" width="20"></p>
    </div>
    <div id="output"></div>
    <div id="subscription">
        <p style="color: green;">You are in the free trial period. Enjoy!</p>
    </div>
    <!-- Button to toggle free period (for demo purposes) -->
    <button onclick="toggleFreePeriod()">Toggle Free Period</button>
</div>
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Pages Build Error</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 800px;
            margin: 2rem auto;
            padding: 0 20px;
            line-height: 1.6;
            color: #333;
        }
        .container {
            background: #f9f9f9;
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 20px;
        }
        h1 {
            color: #d9534f;
            border-bottom: 2px solid #d9534f;
            padding-bottom: 10px;
        }
        .workflow-steps {
            margin: 20px 0;
        }
        .step {
            background: #fff;
            border: 1px solid #eee;
            border-radius: 6px;
            padding: 15px;
            margin: 10px 0;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }
        code {
            display: block;
            background: #2d2d2d;
            color: #fff;
            padding: 15px;
            border-radius: 6px;
            margin: 10px 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>فشل في بناء GitHub Pages</h1>
        <div class="workflow-steps">
            <div class="step">
                <h3>1. تحقق من سجلات البناء</h3>
                <p>قم بزيارة <a href="https://github.com/Saly78793/Arch3D-vision-ai/actions" target="_blank">صفحة Actions</a> في المستودع</p>
            </div>
            <div class="step">
                <h3>2. تحقق من ملف الـ workflow</h3>
                <code>
name: Build and Deploy
on:
  push:
    branches: [main]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm install
      - run: npm run build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: ./dist
  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/download-pages-artifact@v3
      - uses: actions/upload-pages@v3
                </code>
            </div>
            <div class="step">
                <h3>3. خطوات الإصلاح</h3>
                <ul>
                    <li>تأكد من وجود ملف <code>dist</code> بعد التنفيذ</li>
                    <li>تحقق من صحة ملفات البناء باستخدام <code>npm run build</code> محليًا</li>
                    <li>تأكد من صحة الإصدار المحدد في <code>node-version</code></li>
                </ul>
            </div>
        </div>
    </div>
</body>
</html> 
