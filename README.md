
<head>
    <title>Калькулятор</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: #0f172a;
            color: #f8fafc;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 24px;
        }
        
        .page {
            width: min(100%, 1000px);
            background: linear-gradient(180deg, #1e293b 0%, #0f172a 100%);
            border: 1px solid rgba(148, 163, 184, 0.18);
            border-radius: 28px;
            overflow: hidden;
            box-shadow: 0 40px 120px rgba(15, 23, 42, 0.65);
        }
        
        .header {
            padding: 28px 32px 20px;
            background: #111827;
            text-align: left;
            border-bottom: 1px solid rgba(148, 163, 184, 0.12);
        }
        
        .header h1 {
            font-size: 36px;
            letter-spacing: 0.08em;
            text-transform: uppercase;
            color: #e2e8f0;
        }
        
        .header p {
            margin-top: 10px;
            color: #cbd5e1;
            max-width: 720px;
            line-height: 1.6;
            font-size: 16px;
        }
        
        .calculator {
            display: grid;
            grid-template-columns: 1.1fr 0.9fr;
        }
        
        .panel {
            padding: 32px;
            display: flex;
            flex-direction: column;
            gap: 18px;
        }
        
        .left-panel {
            border-right: 1px solid rgba(148, 163, 184, 0.12);
            background: #0f172a;
        }
        
        .right-panel {
            background: #111827;
        }
        
        label {
            display: block;
            font-size: 14px;
            color: #94a3b8;
            margin-bottom: 8px;
        }
        
        input {
            width: 100%;
            padding: 16px 18px;
            font-size: 16px;
            border-radius: 14px;
            border: 1px solid rgba(148, 163, 184, 0.18);
            background: #0f172a;
            color: #f8fafc;
        }
        
        input::placeholder {
            color: #64748b;
        }
        
        button {
            width: 100%;
            padding: 16px 18px;
            border-radius: 14px;
            border: none;
            background: #2563eb;
            color: #f8fafc;
            font-size: 16px;
            font-weight: 700;
            cursor: pointer;
            text-transform: uppercase;
            letter-spacing: 0.04em;
        }
        
        button:active {
            transform: translateY(1px);
        }
        
        .results-card {
            padding: 24px;
            border-radius: 20px;
            background: linear-gradient(180deg, rgba(15, 23, 42, 0.95), rgba(15, 23, 42, 0.8));
            border: 1px solid rgba(148, 163, 184, 0.1);
            display: flex;
            flex-direction: column;
            gap: 16px;
            min-height: 280px;
        }
        
        #results {
            min-height: 200px;
            display: flex;
            flex-direction: column;
            gap: 16px;
            justify-content: center;
        }
        
        .result-title {
            font-size: 18px;
            color: #e2e8f0;
            letter-spacing: 0.08em;
            text-transform: uppercase;
        }
        
        .result-item {
            display: flex;
            justify-content: space-between;
            background: rgba(148, 163, 184, 0.08);
            padding: 14px 16px;
            border-radius: 14px;
            color: #e2e8f0;
        }
        
        .result-item span:first-child {
            color: #94a3b8;
        }
        
        .result-item span:last-child {
            font-weight: 700;
            color: #f8fafc;
        }
        
        .empty-state {
            color: #94a3b8;
            line-height: 1.7;
        }
        
        @media (max-width: 840px) {
            .calculator {
                grid-template-columns: 1fr;
            }
            .left-panel {
                border-right: none;
                border-bottom: 1px solid rgba(148, 163, 184, 0.12);
            }
        }
        
        @media (max-width: 560px) {
            .header {
                padding: 24px 20px 16px;
            }
            .page {
                border-radius: 20px;
            }
            .panel {
                padding: 24px 18px;
            }
            button {
                padding: 14px 16px;
            }
        }
    </style>
</head>
<body>
    <div class="page">
        <div class="header">
            <h1>Калькулятор</h1>
            <p>Введите два числа слева, нажмите «Вычислить» и посмотрите результаты справа. Страница готова для GitHub Pages как статичная веб-страница.</p>
        </div>

        <div class="calculator">
            <div class="panel left-panel">
                <label for="num1">Первое число</label>
                <input type="number" id="num1" placeholder="Введите первое число">

                <label for="num2">Второе число</label>
                <input type="number" id="num2" placeholder="Введите второе число">

                <button onclick="calculate()">Вычислить</button>
            </div>

            <div class="panel right-panel">
                <div class="results-card">
                    <div class="result-title">Результаты</div>
                    <div id="results">
                        <div class="empty-state">Результаты появятся здесь после нажатия кнопки.</div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        function calculate() {
            const num1 = parseFloat(document.getElementById('num1').value);
            const num2 = parseFloat(document.getElementById('num2').value);
            
            if (isNaN(num1) || isNaN(num2)) {
                alert('Введите оба числа!');
                return;
            }
            
            const summa = num1 + num2;
            const sub = num1 - num2;
            const mult = num1 * num2;
            const div = num2 !== 0 ? (num1 / num2).toFixed(2) : 'Ошибка: деление на 0';
            
            document.getElementById('results').innerHTML = `
                <div class="result-item"><span>Сумма</span><span>${summa}</span></div>
                <div class="result-item"><span>Разность</span><span>${sub}</span></div>
                <div class="result-item"><span>Умножение</span><span>${mult}</span></div>
                <div class="result-item"><span>Деление</span><span>${div}</span></div>
            `;
        }
    </script>
</body>
</html>
