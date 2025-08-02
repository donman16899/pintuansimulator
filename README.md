# pintuansimulator
from IPython.display import HTML

html_code = """
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>拼團收益試算器</title>
  <style>
    * { box-sizing: border-box; }
    body {
      font-family: 'Arial', sans-serif;
      background: #f8f9fa;
      color: #333;
      padding: 1rem;
      margin: 0;
    }
    h1 {
      color: #2c3e50;
      font-size: 1.5rem;
      text-align: center;
    }
    label {
      display: block;
      margin-top: 1.2rem;
      font-size: 1rem;
    }
    input {
      width: 100%;
      padding: 0.5rem;
      font-size: 1rem;
      border-radius: 4px;
      border: 1px solid #ccc;
      margin-top: 0.3rem;
    }
    .result {
      margin-top: 2rem;
      background: white;
      padding: 1rem;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.05);
    }
    .highlight {
      color: #e74c3c;
      font-weight: bold;
    }
    @media (min-width: 768px) {
      body {
        max-width: 600px;
        margin: auto;
      }
    }
  </style>
</head>
<body>

  <h1>📈 拼團收益試算器</h1>

  <label>
    ✅ 輸入推薦人數（每人獎金 $500）：
    <input type="number" id="referrals" value="2" min="0" oninput="updateCalculation()" onchange="updateCalculation()">
  </label>

  <label>
    💎 輸入拼團分紅次數（每次實領 $200）：
    <input type="number" id="bonuses" value="1" min="0" oninput="updateCalculation()" onchange="updateCalculation()">
  </label>

  <label>
    🔁 輸入推薦會員復購次數（每次 $200）：
    <input type="number" id="repeats" value="3" min="0" oninput="updateCalculation()" onchange="updateCalculation()">
  </label>

  <div class="result">
    <p>🧾 固定投入：<span class="highlight">-1000 元</span></p>
    <p>🎯 推薦收益：<span id="referral_income">0</span> 元</p>
    <p>🎯 分紅收益（實領）：<span id="bonus_income">0</span> 元</p>
    <p>🎯 復購收益：<span id="repeat_income">0</span> 元</p>
    <hr>
    <p>💰 <strong>累積淨收益：</strong><span id="net_income" class="highlight">0</span> 元</p>
  </div>

  <script>
    function updateCalculation() {
      const referrals = parseInt(document.getElementById('referrals').value) || 0;
      const bonuses = parseInt(document.getElementById('bonuses').value) || 0;
      const repeats = parseInt(document.getElementById('repeats').value) || 0;

      const referralIncome = referrals * 500;
      const bonusIncome = bonuses * 200;
      const repeatIncome = repeats * 200;
      const netIncome = -1000 + referralIncome + bonusIncome + repeatIncome;

      document.getElementById('referral_income').innerText = referralIncome;
      document.getElementById('bonus_income').innerText = bonusIncome;
      document.getElementById('repeat_income').innerText = repeatIncome;
      document.getElementById('net_income').innerText = netIncome;
    }

    window.onload = updateCalculation;
  </script>

</body>
</html>
"""

HTML(html_code)
