# valentine---yes---no<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Valentine's Question ❤️</title>
    <style>
        body {
            background: linear-gradient(45deg, #ff85a2, #ff6b6b);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Arial Rounded MT Bold', cursive;
            margin: 0;
            overflow: hidden;
        }

        .container {
            text-align: center;
            padding: 30px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            box-shadow: 0 0 30px rgba(0, 0, 0, 0.2);
            position: relative;
            max-width: 90%;
        }

        h1 {
            color: #ff4757;
            font-size: 2.5em;
            margin-bottom: 20px;
        }

        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            position: relative;
        }

        button {
            padding: 15px 40px;
            font-size: 1.5em;
            border: none;
            border-radius: 15px;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        #btnYes {
            background: #2ed573;
            color: white;
        }

        #btnNo {
            background: #ff4757;
            color: white;
            position: relative;
        }

        button:hover {
            transform: scale(1.1);
        }

        .hearts {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .heart {
            position: absolute;
            font-size: 24px;
            animation: float 3s infinite;
            opacity: 0;
        }

        @keyframes float {
            0% { transform: translateY(0); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateY(-100px); opacity: 0; }
        }

        #message {
            display: none;
            font-size: 2em;
            color: #ff4757;
            margin-top: 20px;
            animation: fadeIn 1s;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @media (max-width: 600px) {
            h1 {
                font-size: 1.8em;
            }
            button {
                padding: 12px 30px;
                font-size: 1.2em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="hearts" id="heartsContainer"></div>
        <h1>💖 Will You Be My Valentine? 💖</h1>
        <div class="buttons">
            <button id="btnYes" onclick="showResponse(true)">YES!</button>
            <button id="btnNo" onmouseover="moveButton()" onclick="moveButton()">NO</button>
        </div>
        <div id="message">YAY! 😍 You've made me the happiest! 💝</div>
    </div>

    <script>
        function createHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + '%';
            heart.style.animationDelay = Math.random() * 2 + 's';
            document.getElementById('heartsContainer').appendChild(heart);
            
            setTimeout(() => heart.remove(), 3000);
        }

        function showResponse(response) {
            const message = document.getElementById('message');
            const buttons = document.querySelector('.buttons');
            
            if(response) {
                message.style.display = 'block';
                buttons.style.display = 'none';
                setInterval(createHeart, 300);
            }
        }

        function moveButton() {
            const btnNo = document.getElementById('btnNo');
            const container = document.querySelector('.container');
            const containerRect = container.getBoundingClientRect();
            
            const maxX = containerRect.width - btnNo.offsetWidth - 20;
            const maxY = containerRect.height - btnNo.offsetHeight - 20;
            
            const randomX = Math.random() * maxX;
            const randomY = Math.random() * maxY;
            
            btnNo.style.position = 'absolute';
            btnNo.style.left = randomX + 'px';
            btnNo.style.top = randomY + 'px';
        }

        // Initial hearts animation
        for(let i = 0; i < 10; i++) {
            setTimeout(createHeart, i * 300);
        }
    </script>
</body>
</html>
