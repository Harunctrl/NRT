# NRT
NRT
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nurten Öğet Hakkında</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            background: white;
            padding: 30px 20px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            text-align: center;
            max-width: 500px;
            width: 100%;
            margin: 0 auto;
        }
        
        h1 {
            color: #333;
            margin-bottom: 25px;
            font-size: clamp(18px, 4vw, 24px);
            line-height: 1.4;
            padding: 0 10px;
        }
        
        .buttons {
            display: flex;
            gap: 15px;
            justify-content: center;
            margin-top: 25px;
            position: relative;
            flex-wrap: wrap;
            min-height: 120px;
        }
        
        .btn {
            padding: clamp(12px, 3vw, 15px) clamp(20px, 4vw, 30px);
            font-size: clamp(16px, 3vw, 18px);
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
            min-width: 100px;
        }
        
        .yes-btn {
            background: #4CAF50;
            color: white;
            position: relative;
        }
        
        .no-btn {
            background: #f44336;
            color: white;
            z-index: 10;
            position: relative;
        }
        
        .yes-btn:hover {
            background: #45a049;
        }
        
        .no-btn:hover {
            background: #da190b;
        }
        
        .zaa-text {
            font-size: clamp(32px, 8vw, 60px);
            font-weight: bold;
            color: #ff0000;
            margin-top: 20px;
            display: none;
            animation: zaaAnimation 1s ease;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            letter-spacing: 3px;
        }
        
        .photo-container {
            margin-top: 20px;
            display: none;
            animation: photoAppear 1s ease 0.5s both;
        }
        
        .surprise-photo {
            width: 100%;
            max-width: 300px;
            height: auto;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            border: 5px solid #ff6b6b;
        }
        
        @keyframes zaaAnimation {
            0% { 
                transform: scale(0.1) rotate(-10deg);
                opacity: 0;
            }
            50% { 
                transform: scale(1.2) rotate(5deg);
                opacity: 1;
            }
            100% { 
                transform: scale(1) rotate(0deg);
                opacity: 1;
            }
        }
        
        @keyframes photoAppear {
            0% {
                transform: scale(0.8);
                opacity: 0;
            }
            100% {
                transform: scale(1);
                opacity: 1;
            }
        }
        
        .move {
            animation: shake 0.5s ease;
        }
        
        @keyframes shake {
            0% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            50% { transform: translateX(10px); }
            75% { transform: translateX(-10px); }
            100% { transform: translateX(0); }
        }

        /* Mobil için medya sorguları */
        @media (max-width: 480px) {
            .container {
                padding: 25px 15px;
                margin: 10px;
            }
            
            .buttons {
                gap: 10px;
                min-height: 100px;
            }
            
            .btn {
                min-width: 80px;
                padding: 12px 20px;
            }
            
            h1 {
                margin-bottom: 20px;
            }
            
            .surprise-photo {
                max-width: 250px;
            }
        }

        @media (max-width: 360px) {
            .buttons {
                flex-direction: column;
                align-items: center;
            }
            
            .btn {
                width: 150px;
            }
            
            .container {
                padding: 20px 10px;
            }
            
            .surprise-photo {
                max-width: 200px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Nurten Öğet iyi bir insan mı?</h1>
        
        <div class="buttons">
            <button class="btn yes-btn" id="yesBtn">EVET</button>
            <button class="btn no-btn" id="noBtn">HAYIR</button>
        </div>
        
        <div class="zaa-text" id="zaaText">ZAAAAAAA</div>
        <div class="photo-container" id="photoContainer">
            <img src="https://media.licdn.com/dms/image/v2/D4E03AQFKYXWwbcO-5g/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1711041563005?e=2147483647&v=beta&t=NkBgh8M_tuPNlOZf19mXynWISIQoVFKH3lvgc2QinTk" alt="Sürpriz Fotoğraf" class="surprise-photo" id="surprisePhoto">
        </div>
    </div>

    <script>
        function moveYesButton() {
            const yesBtn = document.getElementById('yesBtn');
            const buttons = document.querySelector('.buttons');
            const container = document.querySelector('.container');
            
            const isMobile = window.innerWidth <= 480;
            const maxX = isMobile ? (container.offsetWidth - yesBtn.offsetWidth - 30) : (container.offsetWidth - yesBtn.offsetWidth - 20);
            const maxY = isMobile ? (buttons.offsetHeight - yesBtn.offsetHeight - 10) : (container.offsetHeight - yesBtn.offsetHeight - 20);
            
            const randomX = Math.floor(Math.random() * maxX);
            const randomY = Math.floor(Math.random() * maxY);
            
            yesBtn.style.position = isMobile ? 'relative' : 'absolute';
            yesBtn.style.left = randomX + 'px';
            yesBtn.style.top = randomY + 'px';
            
            yesBtn.classList.add('move');
            setTimeout(() => {
                yesBtn.classList.remove('move');
            }, 500);
        }
        
        function showZaaAndPhoto() {
            const zaaText = document.getElementById('zaaText');
            const photoContainer = document.getElementById('photoContainer');
            
            // Önce ZAAAAAAA yazısını göster
            zaaText.style.display = 'block';
            
            // 1 saniye sonra fotoğrafı göster
            setTimeout(() => {
                photoContainer.style.display = 'block';
            }, 1000);
            
            // 5 saniye sonra her şeyi gizle
            setTimeout(() => {
                zaaText.style.display = 'none';
                photoContainer.style.display = 'none';
            }, 5000);
        }
        
        document.addEventListener('DOMContentLoaded', function() {
            const yesBtn = document.getElementById('yesBtn');
            const noBtn = document.getElementById('noBtn');
            
            if ('ontouchstart' in window) {
                yesBtn.addEventListener('touchstart', function(e) {
                    e.preventDefault();
                    moveYesButton();
                });
                
                yesBtn.addEventListener('touchmove', function(e) {
                    e.preventDefault();
                });
                
                noBtn.addEventListener('touchstart', function(e) {
                    e.preventDefault();
                    showZaaAndPhoto();
                });
            } else {
                yesBtn.addEventListener('mouseover', moveYesButton);
                yesBtn.addEventListener('click', function(e) {
                    e.preventDefault();
                    moveYesButton();
                });
            }
            
            noBtn.addEventListener('click', showZaaAndPhoto);
        });

        window.addEventListener('resize', function() {
            const yesBtn = document.getElementById('yesBtn');
            yesBtn.style.position = 'relative';
            yesBtn.style.left = '0';
            yesBtn.style.top = '0';
        });
    </script>
</body>
</html>
