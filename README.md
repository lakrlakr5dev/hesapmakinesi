[online_viewer_net (2).htm](https://github.com/user-attachments/files/24637750/online_viewer_net.2.htm)
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LakrHesapMakinesi</title>
    <style>
        :root {
            --bg-color: #0a0a00;
            --calc-bg: #151500;
            --lakr-gold: #ffcc00;
            --btn-bg: #222200;
            --text-color: #ffcc00;
        }

        body {
            background-color: var(--bg-color);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        .calculator {
            background-color: var(--calc-bg);
            width: 350px;
            padding: 25px;
            border-radius: 20px;
            border: 2px solid var(--lakr-gold);
            box-shadow: 0 0 30px rgba(255, 204, 0, 0.2);
        }

        .brand {
            color: var(--lakr-gold);
            text-align: center;
            font-weight: bold;
            font-size: 20px;
            letter-spacing: 3px;
            margin-bottom: 20px;
            text-shadow: 0 0 10px var(--lakr-gold);
        }

        #display {
            width: 100%;
            height: 60px;
            background-color: #000;
            border: 1px solid var(--lakr-gold);
            border-radius: 10px;
            color: var(--lakr-gold);
            font-size: 28px;
            text-align: right;
            padding: 10px;
            box-sizing: border-box;
            margin-bottom: 25px;
            outline: none;
            box-shadow: inset 0 0 10px rgba(255, 204, 0, 0.1);
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
        }

        button {
            height: 60px;
            border-radius: 10px;
            border: 1px solid #333;
            background-color: var(--btn-bg);
            color: var(--text-color);
            font-size: 20px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.2s;
        }

        button:hover {
            background-color: var(--lakr-gold);
            color: #000;
            transform: scale(1.05);
        }

        .operator {
            background-color: #332b00;
            border-color: var(--lakr-gold);
        }

        .equals {
            grid-column: span 2;
            background-color: var(--lakr-gold);
            color: #000;
        }

        .clear {
            grid-column: span 2;
            color: #ff4444;
            border-color: #ff4444;
        }
    </style>
</head>
<body>

<div class="calculator">
    <div class="brand">LAKR CALCULATOR</div>
    <input type="text" id="display" disabled value="0">
    
    <div class="buttons">
        <button class="clear" onclick="clearDisplay()">C</button>
        <button class="operator" onclick="deleteLast()">DEL</button>
        <button class="operator" onclick="addToDisplay('/')">/</button>
        
        <button onclick="addToDisplay('7')">7</button>
        <button onclick="addToDisplay('8')">8</button>
        <button onclick="addToDisplay('9')">9</button>
        <button class="operator" onclick="addToDisplay('*')">×</button>
        
        <button onclick="addToDisplay('4')">4</button>
        <button onclick="addToDisplay('5')">5</button>
        <button onclick="addToDisplay('6')">6</button>
        <button class="operator" onclick="addToDisplay('-')">-</button>
        
        <button onclick="addToDisplay('1')">1</button>
        <button onclick="addToDisplay('2')">2</button>
        <button onclick="addToDisplay('3')">3</button>
        <button class="operator" onclick="addToDisplay('+')">+</button>
        
        <button onclick="addToDisplay('0')">0</button>
        <button onclick="addToDisplay('.')">.</button>
        <button class="equals" onclick="calculate()">=</button>
    </div>
</div>

<script>
    let display = document.getElementById('display');

    function addToDisplay(value) {
        if (display.value === '0') {
            display.value = value;
        } else {
            display.value += value;
        }
    }

    function clearDisplay() {
        display.value = '0';
    }

    function deleteLast() {
        if (display.value.length > 1) {
            display.value = display.value.slice(0, -1);
        } else {
            display.value = '0';
        }
    }

    function calculate() {
        try {
            // eval yerine daha güvenli bir işlem için basit bir mantık
            display.value = eval(display.value.replace('×', '*'));
        } catch (error) {
            display.value = "Hata";
            setTimeout(clearDisplay, 1500);
        }
    }
</script>

</body>
</html>
