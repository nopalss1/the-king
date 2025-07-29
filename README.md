<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Kalkulator Ilmiah Lengkap</title>
  <style>
    body {
      background: #f0f0f0;
      font-family: sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .calculator {
      background: #fff;
      padding: 25px;
      border-radius: 15px;
      box-shadow: 0 0 15px rgba(0,0,0,0.2);
      width: 320px;
    }

    #display {
      width: 100%;
      padding: 15px;
      font-size: 20px;
      text-align: right;
      margin-bottom: 10px;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
    }

    button {
      padding: 15px;
      font-size: 16px;
      border: none;
      border-radius: 8px;
      background: #eee;
      cursor: pointer;
      transition: 0.2s;
    }

    button:hover {
      background: #ddd;
    }

    .operator {
      background: #4CAF50;
      color: white;
    }

    .clear {
      background: #e74c3c;
      color: white;
    }
  </style>
</head>
<body>

  <div class="calculator">
    <input type="text" id="display" disabled>

    <div class="buttons">
      <button onclick="clearDisplay()" class="clear">C</button>
      <button onclick="append('π')">π</button>
      <button onclick="append('^')">^</button>
      <button onclick="append('/')">÷</button>

      <button onclick="append('7')">7</button>
      <button onclick="append('8')">8</button>
      <button onclick="append('9')">9</button>
      <button onclick="append('*')">×</button>

      <button onclick="append('4')">4</button>
      <button onclick="append('5')">5</button>
      <button onclick="append('6')">6</button>
      <button onclick="append('-')">−</button>

      <button onclick="append('1')">1</button>
      <button onclick="append('2')">2</button>
      <button onclick="append('3')">3</button>
      <button onclick="append('+')">+</button>

      <button onclick="append('0')">0</button>
      <button onclick="append('.')">.</button>
      <button onclick="calculate()">=</button>
      <button onclick="append('%')">%</button>

      <button onclick="append('Math.sin(')">sin</button>
      <button onclick="append('Math.cos(')">cos</button>
      <button onclick="append('Math.tan(')">tan</button>
      <button onclick="append('Math.sqrt(')">√</button>

      <button onclick="append('Math.log10(')">log</button>
      <button onclick="append('Math.log(')">ln</button>
      <button onclick="append(')')">)</button>
      <button onclick="append('(')">(</button>
    </div>
  </div>

  <script>
    const display = document.getElementById('display');

    function append(value) {
      if (value === 'π') {
        display.value += Math.PI.toFixed(8);
      } else {
        display.value += value;
      }
    }

    function clearDisplay() {
      display.value = '';
    }

    function calculate() {
      try {
        let expression = display.value
          .replace(/\^/g, '**')
          .replace(/%/g, '/100');
        display.value = eval(expression);
      } catch (err) {
        display.value = 'Error';
      }
    }
  </script>

</body>
</html>
