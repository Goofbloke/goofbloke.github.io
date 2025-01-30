<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Envelope</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: #f4f4f4;
            flex-direction: column;
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
            font-family: Arial, sans-serif;
            font-size: 14px;
            text-align: center;
            padding: 10px;
            transition: top 0.5s ease-in-out;
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
        }

        .yes-btn {
            background: #4CAF50;
            color: white;
        }

        .no-btn {
            background: #f44336;
            color: white;
        }

        .opened .flap {
            transform: rotateX(180deg);
        }

        .opened .note {
            top: 20%;
        }
    </style>
</head>
<body>

    <div class="envelope-container" onclick="openEnvelope()">
        <div class="envelope">
            <div class="flap"></div>
            <div class="note">
                <p id="messageText">HELLO MISS ZINNIA CHANDA, WILL YOU BE MY VALENTINE??</p>
                <div class="buttons">
                    <button class="yes-btn" onclick="handleResponse('yes')">Yes</button>
                    <button class="no-btn" onclick="handleResponse('no')">No</button>
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
                message.innerText = "Yay! 🎉 I love you so much! 🤗";
            } else {
                message.innerText = "Oh no! 😢 Maybe next time! 💌";
            }
        }
    </script>

</body>
</html>
