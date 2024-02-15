# Shineway.in
Here interns can Push their project source code<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Basic Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
    }
    .calculator {
      width: 300px;
      margin: 50px auto;
      border: 1px solid #ccc;
      border-radius: 5px;
      padding: 20px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    .display {
      width: 100%;
      height: 40px;
      margin-bottom: 10px;
      font-size: 20px;
      text-align: right;
      padding: 5px;
    }
    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 5px;
    }
    button {
      padding: 10px;
      font-size: 18px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
    button:hover {
      background-color: #eee;
    }
    button.operator {
      background-color: orange;
      color: #fff;
    }
    button.clear {
      background-color: red;
      color: #fff;
    }
  </style>
</head>
<body>

<div class="calculator">
  <div class="display" id="display">0</div>
  <div class="buttons">
    <button onclick="appendToDisplay('7')">7</button>
    <button onclick="appendToDisplay('8')">8</button>
    <button onclick="appendToDisplay('9')">9</button>
    <button class="operator" onclick="setOperator('+')">+</button>
    <button onclick="appendToDisplay('4')">4</button>
    <button onclick="appendToDisplay('5')">5</button>
    <button onclick="appendToDisplay('6')">6</button>
    <button class="operator" onclick="setOperator('-')">-</button>
    <button onclick="appendToDisplay('1')">1</button>
    <button onclick="appendToDisplay('2')">2</button>
    <button onclick="appendToDisplay('3')">3</button>
    <button class="operator" onclick="setOperator('*')">*</button>
    <button onclick="appendToDisplay('0')">0</button>
    <button onclick="appendToDisplay('.')">.</button>
    <button class="clear" onclick="clearDisplay()">C</button>
    <button class="operator" onclick="calculate()">=</button>
    <button class="operator" onclick="setOperator('/')">/</button>
  </div>
</div>

<script>
  let currentInput = '';
  let operator = '';
  let previousInput = '';

  function appendToDisplay(value) {
    currentInput += value;
    updateDisplay();
  }

  function setOperator(op) {
    if (currentInput !== '') {
      operator = op;
      previousInput = currentInput;
      currentInput = '';
    }
  }

  function clearDisplay() {
    currentInput = '';
    previousInput = '';
    operator = '';
    updateDisplay();
  }

  function calculate() {
    let result;
    const num1 = parseFloat(previousInput);
    const num2 = parseFloat(currentInput);
    switch (operator) {
      case '+':
        result = num1 + num2;
        break;
      case '-':
        result = num1 - num2;
        break;
      case '*':
        result = num1 * num2;
        break;
      case '/':
        result = num1 / num2;
        break;
      default:
        return;
    }
    currentInput = result.toString();
    previousInput = '';
    operator = '';
    updateDisplay();
  }

  function updateDisplay() {
    document.getElementById('display').innerText = currentInput || '0';
  }
</script>

</body>
</html>
.
