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
