🧮 Advanced Web Calculator
​An advanced, interactive web calculator application that combines modern design with fast performance. Built using JavaScript for precise calculation logic, alongside a sleek, user-friendly interface created with HTML5 and CSS3.

​Features
​Comprehensive Calculations: Supports both basic and advanced arithmetic operations with high accuracy and speed.
​Modern & Responsive UI: Clean design tailored to fit seamlessly across various screen sizes and devices.
​Smooth User Experience: Intuitive input handling via click or keyboard, featuring clear result displays.
​Lightweight & Fast: Instant processing with zero latency, powered by clean and efficient JavaScript.

​Built With
​HTML5: Structures the layout, buttons, and display screen.
​CSS3: Styles the visual presentation, color schemes, and responsive grid.
​JavaScript (JS): Handles mathematical logic, input state management, and real-time evaluation.



<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <title>ApexViperCode - Calculator Viewer</title>
  <!-- مكتبة Highlight.js لتنسيق وتلوين الأكواد -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.7.0/styles/atom-one-dark.min.css">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.7.0/highlight.min.js"></script>

  <style>
    body {
      background-color: #0d1117;
      color: #c9d1d9;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      padding: 20px;
      margin: 0;
    }

    .section-title {
      color: #a855f7;
      border-bottom: 2px solid #3b0764;
      padding-bottom: 8px;
      margin-top: 35px;
      font-size: 20px;
    }

    pre {
      border-radius: 8px;
      overflow: hidden;
      border: 1px solid #30363d;
      direction: ltr;
      text-align: left;
      background: #161b22;
      box-shadow: 0 4px 12px rgba(0,0,0,0.3);
    }

    code {
      font-family: 'Consolas', 'Courier New', monospace !important;
      font-size: 14px;
      line-height: 1.5;
    }

    /* تنسيق المعاينة المباشرة للحاسبة */
    .preview-box {
      background-color: #1a1625;
      border: 1px solid #30363d;
      border-radius: 8px;
      padding: 30px;
      margin-top: 15px;
      display: flex;
      justify-content: center;
      align-items: center;
      direction: ltr;
    }

    /* تنسيقات الآلة الحاسبة داخل المعاينة */
    #claculator {
      font-family: Arial, sans-serif;
      background-color: hsl(0, 0%, 15%);
      border-radius: 15px;
      max-width: 350px;
      overflow: hidden;
      box-shadow: 0 8px 24px rgba(0,0,0,0.5);
    }

    #display {
      width: 100%;
      padding: 15px;
      font-size: 2.5rem;
      color: white;
      border: none;
      background-color: hsl(0, 0%, 30%);
      text-align: right;
      box-sizing: border-box;
    }

    #keys {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
      padding: 15px;
    }

    .calc-btn {
      width: 60px;
      height: 60px;
      border-radius: 30px;
      border: none;
      background-color: hsl(0, 0%, 30%);
      color: white;
      font-size: 1.5rem;
      font-weight: bold;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: auto;
    }

    .calc-btn:hover {
      background-color: hsl(0, 0%, 40%);
    }

    .calc-btn:active {
      background-color: hsl(0, 0%, 50%);
    }

    .operato-btn {
      background-color: hsl(35, 100%, 55%);
    }

    .operato-btn:hover {
      background-color: hsl(35, 100%, 65%);
    }

    .operato-btn:active {
      background-color: hsl(35, 100%, 75%);
    }
  </style>
</head>
<body>

  <!-- 1. عرض كود HTML -->
  <h2 class="section-title">🌐 1. HTML Code (index.html)</h2>
  <pre><code class="language-xml" id="html-code"></code></pre>

  <!-- 2. عرض كود CSS -->
  <h2 class="section-title">🎨 2. CSS Code (Claculator_in_css.css)</h2>
  <pre><code class="language-css" id="css-code"></code></pre>

  <!-- 3. عرض كود JavaScript -->
  <h2 class="section-title">⚡ 3. JavaScript Code (Claculator_in_js.js)</h2>
  <pre><code class="language-javascript" id="js-code"></code></pre>

  <!-- 4. المعاينة المباشرة وتجربة الحاسبة -->
  <h2 class="section-title">🚀 4. Live Preview (تجربة الحاسبة المباشرة)</h2>
  <div class="preview-box">
    <div id="claculator">
      <input readonly id="display">
      <div id="keys">
        <button onclick="appendToDisplay('+')" class="calc-btn operato-btn">+</button>
        <button onclick="appendToDisplay('7')" class="calc-btn">7</button>
        <button onclick="appendToDisplay('8')" class="calc-btn">8</button>
        <button onclick="appendToDisplay('9')" class="calc-btn">9</button>
       
        <button onclick="appendToDisplay('-')" class="calc-btn operato-btn">-</button>
        <button onclick="appendToDisplay('4')" class="calc-btn">4</button>
        <button onclick="appendToDisplay('5')" class="calc-btn">5</button>
        <button onclick="appendToDisplay('6')" class="calc-btn">6</button>
     
        <button onclick="appendToDisplay('*')" class="calc-btn operato-btn">*</button>
        <button onclick="appendToDisplay('1')" class="calc-btn">1</button>
        <button onclick="appendToDisplay('2')" class="calc-btn">2</button>
        <button onclick="appendToDisplay('3')" class="calc-btn">3</button>
            
        <button onclick="appendToDisplay('/')" class="calc-btn operato-btn">/</button>
        <button onclick="appendToDisplay('0')" class="calc-btn">0</button>
        <button onclick="appendToDisplay('.')" class="calc-btn">.</button>
        <button onclick="calculate()" class="calc-btn">=</button>
              
        <button onclick="clearDisplay()" class="calc-btn operato-btn">C</button>
      </div>
    </div>
  </div>

  <script>
    // 1. كود HTML للعرض المنسق
    const rawHTML = `<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <meta name="description" content="AVC"/>
    <title>Claculator</title>
    <link rel="stylesheet" href="Claculator_in_css.css">
</head>
<body> 
    <div id="claculator">
      <input readonly id="display">
      <div id="keys">
        <button onclick="appendToDisplay('+')" class="operato-btn">+</button>
        <button onclick="appendToDisplay('7')">7</button>
        <button onclick="appendToDisplay('8')">8</button>
        <button onclick="appendToDisplay('9')">9</button>
       
        <button onclick="appendToDisplay('-')" class="operato-btn">-</button>
        <button onclick="appendToDisplay('4')">4</button>
        <button onclick="appendToDisplay('5')">5</button>
        <button onclick="appendToDisplay('6')">6</button>
     
        <button onclick="appendToDisplay('*')" class="operato-btn">*</button>
        <button onclick="appendToDisplay('1')">1</button>
        <button onclick="appendToDisplay('2')">2</button>
        <button onclick="appendToDisplay('3')">3</button>
            
        <button onclick="appendToDisplay('/')" class="operato-btn">/</button>
        <button onclick="appendToDisplay('0')">0</button>
        <button onclick="appendToDisplay('.')">.</button>
        <button onclick="calculate()">=</button>
              
        <button onclick="clearDisplay()" class="operato-btn">C</button>
      </div>
    </div>

    <script src="Claculator_in_js.js"><\/script>
</body>
</html>`;

    // 2. كود CSS للعرض المنسق
    const rawCSS = `body {
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: hsl(0, 0%, 95%);
}

#claculator {
  font-family: Arial, sans-serif;
  background-color: hsl(0, 0%, 15%);
  border-radius: 15px;
  max-width: 500px;
  overflow: hidden;
}

#keys {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
  padding: 25px;
}

#display {
  width: 100%;
  padding: 20px;
  font-size: 5rem;
  color: white;
  border: none;
  background-color: hsl(0, 0%, 30%);
  text-align: left;
}

button {
  width: 100px;
  height: 100px;
  border-radius: 50px;
  border: none;
  background-color: hsl(0, 0%, 30%);
  color: white;
  font-size: 3rem;
  font-weight: bold;
  cursor: pointer;
}

button:hover {
  background-color: hsl(0, 0%, 40%);
}

button:active {
  background-color: hsl(0, 0%, 50%);
}

.operato-btn {
  background-color: hsl(35, 100%, 55%);
}

.operato-btn:hover {
  background-color: hsl(35, 100%, 65%);
}

.operato-btn:active {
  background-color: hsl(35, 100%, 75%);
}`;

    // 3. كود JS للعرض المنسق
    const rawJS = `const display = document.getElementById('display');

function appendToDisplay(input) {
    display.value += input;
}

function clearDisplay() {
    display.value = '';
}

function calculate() {
    try {
        display.value = eval(display.value);
    } catch (error) {
        display.value = 'error';
    }
}`;

    // طباعة الأكواد في خيارات العرض النصي
    document.getElementById("html-code").textContent = rawHTML;
    document.getElementById("css-code").textContent = rawCSS;
    document.getElementById("js-code").textContent = rawJS;

    // تفعيل التظليل البرمجي
    hljs.highlightAll();
  </script>

  <!-- كود تشغيل الحاسبة المباشر في المعاينة -->
  <script>
    const displayCalc = document.getElementById('display');

    function appendToDisplay(input) {
        displayCalc.value += input;
    }

    function clearDisplay() {
        displayCalc.value = '';
    }

    function calculate() {
        try {
            displayCalc.value = eval(displayCalc.value);
        } catch (error) {
            displayCalc.value = 'error';
        }
    }
  </script>
</body>
</html>





​How to Run
​Start entering numbers and mathematical operations directly to use the calculator!
