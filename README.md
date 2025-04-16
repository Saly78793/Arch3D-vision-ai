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
            outputDiv.innerHTML = `<p style="color: red;">An error occurred: ${error.message}</p>`;
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
