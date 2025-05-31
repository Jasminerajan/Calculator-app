<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Calculator</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="calculator">
    <input type="text" id="display" readonly />
    <div class="buttons">
      <button onclick="clearDisplay()" class="btn-clear">C</button>
      <button onclick="deleteLast()" class="btn-del">DEL</button>
      <button onclick="appendValue('/')" class="btn-op">/</button>
      <button onclick="appendValue('*')" class="btn-op">*</button>

      <button onclick="appendValue('7')" class="btn-num">7</button>
      <button onclick="appendValue('8')" class="btn-num">8</button>
      <button onclick="appendValue('9')" class="btn-num">9</button>
      <button onclick="appendValue('-')" class="btn-op">-</button>

      <button onclick="appendValue('4')" class="btn-num">4</button>
      <button onclick="appendValue('5')" class="btn-num">5</button>
      <button onclick="appendValue('6')" class="btn-num">6</button>
      <button onclick="appendValue('+')" class="btn-op">+</button>

      <button onclick="appendValue('1')" class="btn-num">1</button>
      <button onclick="appendValue('2')" class="btn-num">2</button>
      <button onclick="appendValue('3')" class="btn-num">3</button>
      <button onclick="calculate()" class="btn-equal">=</button>

      <button onclick="appendValue('0')" class="btn-num zero">0</button>
      <button onclick="appendValue('.')" class="btn-num">.</button>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>
#css
body {
  background-color: #000000; /* dark blue background */
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.calculator {
  background-color: #000000; /* darker grey-blue */
  padding: 20px;
  border-radius: 25px;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.7);
  width: 320px;
}

#display {
  width: 100%;
  padding: 15px;
  font-size: 2rem;
  margin-bottom: 25px;
  border: none;
  border-radius: 25px;
  background-color: #323035; /* teal */
  color: white;
  text-align: right;
  box-sizing: border-box;
  user-select: none;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 12px;
}

button {
  padding: 18px 0;
  font-size: 1.3rem;
  border: none;
  border-radius: 15px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  color: white;
  user-select: none;
}

button:active {
  transform: scale(0.95);
}

/* Number buttons */
.btn-num {
  background-color: #323035; /* greenish teal */
}

.btn-num:hover {
  background-color: #323035;
}

/* Operator buttons */
.btn-op {
  background-color: #494458; /* orange */
}

.btn-op:hover {
  background-color: #494458;
}

/* Clear button */
.btn-clear {
  background-color: #494458; /* red */
}

.btn-clear:hover {
  background-color: #494458;
}

/* Delete button */
.btn-del {
  background-color: #494458; /* purple */
}

.btn-del:hover {
  background-color: #494458;
}

/* Equal button */
.btn-equal {
  background-color: #D0BDFD; /* blue */
  grid-row: span 2;
}

.btn-equal:hover {
  background-color: #D0BDFD;
}

/* Zero button spans 2 columns */
.zero {
  grid-column: span 2;
}

button {
  color: #FFFFFF;  /* pale purple text color */
}
 .btn-op, .btn-clear, .btn-del {
  color: #D0BDFD;
}

.btn-equal {
  color: #FFFFFF; /* dark text for contrast */
}
#js
const display = document.getElementById('display');

function appendValue(val) {
  display.value += val;
}

function clearDisplay() {
  display.value = '';
}

function deleteLast() {
  display.value = display.value.slice(0, -1);
}

function calculate() {
  try {
    // Evaluate expression safely
    display.value = eval(display.value) ?? '';
  } catch {
    display.value = 'Error';
  }
}
