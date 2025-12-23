[index.html](https://github.com/user-attachments/files/24301840/index.html)
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>자동차세 연납 할인 계산기</title>
  <style>
    body {
      font-family: sans-serif;
      max-width: 480px;
      margin: 40px auto;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 10px;
      background-color: #fdfdfd;
    }
    label, select, input {
      display: block;
      margin-top: 15px;
      width: 100%;
      font-size: 16px;
    }
    button {
      margin-top: 20px;
      padding: 10px;
      width: 100%;
      font-size: 16px;
      background-color: #0078ff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    #result {
      margin-top: 20px;
      font-weight: bold;
      font-size: 18px;
      background: #f0f8ff;
      padding: 15px;
      border-radius: 6px;
    }
    .footer {
      margin-top: 40px;
      text-align: center;
      font-size: 14px;
      color: #777;
    }
  </style>
</head>
<body>
  <h2>자동차세 연납 할인 계산기</h2>

  <label for="amount">자동차세 총액 (원):</label>
  <input type="number" id="amount" placeholder="예: 300000" />

  <label for="month">연납 시기 선택:</label>
  <select id="month">
    <option value="1">1월 (약 4.58% 할인)</option>
    <option value="3">3월 (약 3.76% 할인)</option>
    <option value="6">6월 (약 2.51% 할인)</option>
    <option value="9">9월 (약 1.25% 할인)</option>
  </select>

  <button onclick="calculateDiscount()">계산하기</button>

  <div id="result"></div>

  <div class="footer">
    본 계산기는 참고용이며 실제 고지서와 다를 수 있습니다
  </div>

  <script>
    function calculateDiscount() {
      const amount = parseFloat(document.getElementById('amount').value);
      const month = document.getElementById('month').value;
      let rate = 0;

      switch (month) {
        case "1":
          rate = 0.0458; // 1월 연납 약 4.58%
          break;
        case "3":
          rate = 0.0376; // 3월 연납 약 3.76%
          break;
        case "6":
          rate = 0.0251; // 6월 연납 약 2.51%
          break;
        case "9":
          rate = 0.0125; // 9월 연납 약 1.25%
          break;
      }

      if (isNaN(amount) || amount <= 0) {
        document.getElementById('result').innerText = '올바른 금액을 입력해 주세요';
        return;
      }

      const discount = Math.round(amount * rate);
      const total = amount - discount;

      document.getElementById('result').innerHTML =
        `할인액: ${discount.toLocaleString()}원<br>연납 시 납부할 금액: ${total.toLocaleString()}원`;
    }
  </script>
</body>
</html>
