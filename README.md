<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>حساب نقاط تركس</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            direction: rtl;
        }
        .container {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            margin-top: 20px;
        }
        .column {
            width: 150px;
            margin: 10px;
            text-align: center;
        }
        .name-box {
            background-color: lightgray;
            padding: 10px;
            font-weight: bold;
            border: 1px solid black;
        }
        .blue-box {
            background-color: lightblue;
            padding: 10px;
            font-weight: bold;
            border: 1px solid black;
            margin-top: 5px;
        }
        .toggle-box {
            display: inline-block;
            width: 50px;
            height: 30px;
            background-color: white;
            border: 1px solid black;
            text-align: center;
            line-height: 30px;
            cursor: pointer;
            margin: 2px;
        }
        .active {
            background-color: red;
            color: white;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1>حساب نقاط تركس</h1>
    <div class="container">
        <!-- إنشاء 6 لاعبين -->
        <script>
            for (let i = 1; i <= 6; i++) {
                document.write(`
                    <div class="column">
                        <input type="text" id="name${i}" placeholder="اسم اللاعب">
                        <div>
                            <div class="toggle-box" id="tricks${i}" onclick="toggleBox('tricks${i}')">تركس</div>
                            <div class="toggle-box" id="complex${i}" onclick="toggleBox('complex${i}')"></div>
                        </div>
                        <div class="blue-box" id="score${i}">0</div>
                        <input type="number" id="input${i}" placeholder="أدخل رقم">
                        <button onclick="updateScore(${i})">إدخال</button>
                    </div>
                `);
            }
        </script>
    </div>

    <script>
        function updateScore(player) {
            let inputId = "input" + player;
            let scoreId = "score" + player;
            let inputValue = parseInt(document.getElementById(inputId).value) || 0;
            let currentScore = parseInt(document.getElementById(scoreId).innerText);
            
            document.getElementById(scoreId).innerText = currentScore + inputValue;
            document.getElementById(inputId).value = "";
        }

        function toggleBox(id) {
            let box = document.getElementById(id);
            if (box.classList.contains("active")) {
                box.classList.remove("active");
                box.innerHTML = "";
            } else {
                box.classList.add("active");
                box.innerHTML = "✔";
            }
        }
    </script>
</body>
</html>
