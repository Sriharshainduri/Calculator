# Calculator.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Elegant Calculator</title>
    <!-- Link to external CSS file -->
    <link rel="stylesheet" href="styles.css">
</head>
<body>

    <div class="calculator">
        <!-- Display screen -->
        <div id="display" class="display">0</div>

        <!-- Buttons -->
        <div class="buttons">
            <button class="button clear" onclick="clearDisplay()">C</button>
            <button class="button backspace" onclick="backspace()">⌫</button>
            <button class="button operator" onclick="appendToDisplay('/')">÷</button>
            <button class="button operator" onclick="appendToDisplay('*')">×</button>

            <button class="button" onclick="appendToDisplay('7')">7</button>
            <button class="button" onclick="appendToDisplay('8')">8</button>
            <button class="button" onclick="appendToDisplay('9')">9</button>
            <button class="button operator" onclick="appendToDisplay('-')">−</button>

            <button class="button" onclick="appendToDisplay('4')">4</button>
            <button class="button" onclick="appendToDisplay('5')">5</button>
            <button class="button" onclick="appendToDisplay('6')">6</button>
            <button class="button operator" onclick="appendToDisplay('+')">+</button>

            <button class="button" onclick="appendToDisplay('1')">1</button>
            <button class="button" onclick="appendToDisplay('2')">2</button>
            <button class="button" onclick="appendToDisplay('3')">3</button>
            <button class="button equals" onclick="calculateResult()">=</button>

            <button class="button" onclick="appendToDisplay('0')" style="grid-column: span 2">0</button>
            <button class="button" onclick="appendToDisplay('.')">.</button>
        </div>
    </div>

    <!-- JavaScript for calculator functionality -->
    <script>
        function clearDisplay() {
            document.getElementById("display").innerText = "0";
        }

        function backspace() {
            const display = document.getElementById("display");
            display.innerText = display.innerText.slice(0, -1) || "0";
        }

        function appendToDisplay(value) {
            const display = document.getElementById("display");
            if (display.innerText === "0") display.innerText = value;
            else display.innerText += value;
        }

        function calculateResult() {
            const display = document.getElementById("display");
            try {
                display.innerText = eval(display.innerText);
            } catch (e) {
                display.innerText = "Error";
            }
        }
    </script>

</body>
</html>


#Calculator.css

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: 'Arial', sans-serif;
}

body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background: linear-gradient(135deg, #8EC5FC, #E0C3FC);
    color: #333;
}

.calculator {
    width: 320px;
    background: #fff;
    border-radius: 12px;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
    overflow: hidden;
}

.display {
    background: #222;
    color: #fff;
    padding: 20px;
    font-size: 2em;
    text-align: right;
    border-top-left-radius: 12px;
    border-top-right-radius: 12px;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    padding: 20px;
    background-color: #f4f4f4;
}

.button {
    padding: 20px;
    font-size: 1.2em;
    border-radius: 8px;
    border: none;
    cursor: pointer;
    transition: background 0.3s, transform 0.2s;
}

.button:active {
    transform: scale(0.95);
}

.button.operator {
    background: #FD7272;
    color: white;
}

.button.clear {
    background: #FC427B;
    color: white;
}

.button.backspace {
    background: #FC427B;
    color: white;
}

.button.equal {
    background: #58B19F;
    color: white;
    grid-column: span 2;
}

.button:hover {
    background: #dfe6e9;
}
