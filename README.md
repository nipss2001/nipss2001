<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Valentine's Day Proposal</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: 'Arial', sans-serif;
            background-color: #fce4ec;
        }

        #container {
            text-align: center;
        }

        #question {
            font-size: 24px;
            margin-bottom: 20px;
        }

        .button {
            display: inline-block;
            padding: 10px 20px;
            font-size: 18px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            margin: 0 10px;
        }

        #yes {
            background-color: #4caf50;
            color: #fff;
        }

        #no {
            background-color: #e53935;
            color: #fff;
        }

        .emoji {
            font-size: 30px;
            margin: 0 5px;
        }

        #emojis {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div id="container">
        <div id="question">Will you be my Valentine?</div>
        <button class="button" id="yes" onclick="celebrate()">Yes</button>
        <button class="button" id="no" onclick="handleNo()">No</button>
        <div id="emojis"></div>
    </div>

    <script>
        var noClickCount = 0;
        var sadEmojis = ['😢', '😔', '😞', '😟', '😕'];

        function handleNo() {
            noClickCount++;

            if (noClickCount % 5 === 0) {
                document.getElementById('emojis').innerHTML = '';
                for (var i = 0; i < 5; i++) {
                    document.getElementById('emojis').innerHTML += '<div class="emoji">' + sadEmojis[i] + '</div>';
                }
            } else {
                document.getElementById('emojis').innerHTML += '<div class="emoji">' + sadEmojis[noClickCount % 5] + '</div>';
            }

            enlargeNo();
        }

        function enlargeNo() {
            document.getElementById('no').style.transform = 'scale(1.2)';
            setTimeout(() => {
                document.getElementById('no').style.transform = 'scale(1)';
                enlargeNo();
            }, 500);
        }

        function celebrate() {
            document.getElementById('emojis').innerHTML = '<div class="emoji">❤️😊</div>';
            document.getElementById('yes').disabled = true; // Disable the button to prevent multiple clicks
            setTimeout(() => {
                alert("Yay!!! You said yes! Tell me when you are free so we can go out!");
                document.getElementById('container').style.display = 'none';
            }, 1000); // Delay the alert for 1 second
        }
    </script>
</body>
</html>
