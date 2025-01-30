<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Envelope with Fireworks</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: #222;
            flex-direction: column;
            font-family: Arial, sans-serif;
            position: relative;
            overflow: hidden;
            color: white;
        }

        .envelope-container {
            position: relative;
            width: 200px;
            height: 150px;
            cursor: pointer;
        }

        .envelope {
            width: 100%;
            height: 100%;
            background: #e0a96d;
            position: relative;
            border-radius: 10px;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .flap {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 50%;
            background: #d18f5b;
            border-top-left-radius: 10px;
            border-top-right-radius: 10px;
            transform-origin: top;
            transition: transform 0.5s ease-in-out;
        }

        .note {
            position: absolute;
            width: 80%;
            height: 60%;
            background: #fff;
            top: 100%;
            left: 10%;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            font-size: 14px;
            text-align: center;
            padding: 10px;
            transition: top 0.5s ease-in-out;
            color: black;
        }

        .buttons {
            margin-top: 10px;
            display: flex;
            gap: 10px;
        }

        button {
            padding: 5px 10px;
            font-size: 14px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            transition: transform 0.2s ease-in-out;
        }

        .yes-btn {
            background: #4CAF50;
            color: white;
        }

        .no-btn {
            background: #f44336;
            color: white;
        }

        .yes-btn:hover, .no-btn:hover {
            transform: scale(1.1);
        }

        .opened .flap {
            transform: rotateX(180deg);
        }

        .opened .note {
            top: 20%;
        }

        /* Fireworks */
        .firework {
            position: absolute;
            width: 5px;
            height: 5px;
            background: radial-gradient(circle, yellow, red, transparent);
            border-radius: 50%;
            opacity: 0;
            animation: explode 1s ease-out forwards;
        }

        @keyframes explode {
            0% {
                transform: scale(1);
                opacity: 1;
            }
            100% {
                transform: scale(5);
                opacity: 0;
            }
        }
    </style>
</head>
<body>

    <h1>💌 Open the Envelope! 💌</h1>
    <div class="envelope-container" onclick="openEnvelope()">
        <div class="envelope">
            <div class="flap"></div>
            <div class="note">
                <p id="messageText">ZINNIA CHANDA WILL YOU BE MY VALENTINE?</p>
                <div class="buttons">
                    <button class="yes-btn" onclick="handleResponse('yes'); event.stopPropagation();">Yes</button>
                    <button class="no-btn" onclick="handleResponse('no'); event.stopPropagation();">No</button>
                </div>
            </div>
        </div>
    </div>

    <script>
        function openEnvelope() {
            document.querySelector('.envelope-container').classList.toggle('opened');
        }

        function handleResponse(answer) {
            let message = document.getElementById("messageText");

            if (answer === "yes") {
                message.innerText = "🎉 Yay! Fireworks for you! 🎆";
                triggerFireworks();
            } else {
                message.innerText = "Oh no! 😢 Maybe next time! 💌";
            }
        }

        function triggerFireworks() {
            for (let i = 0; i < 20; i++) {
                let firework = document.createElement("div");
                firework.classList.add("firework");

                let x = Math.random() * window.innerWidth;
                let y = Math.random() * window.innerHeight * 0.7; // Appear mostly at the top

                firework.style.left = `${x}px`;
                firework.style.top = `${y}px`;

                document.body.appendChild(firework);

                setTimeout(() => {
                    firework.remove();
                }, 1000);
            }
        }
    </script>

</body>
</html>
