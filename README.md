
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Demo Shop</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
    }

    body {
      min-height: 100vh;
      background: #f3f4f6;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
    }

    .container {
      width: 100%;
      max-width: 430px;
      background: white;
      border-radius: 20px;
      padding: 30px;
      box-shadow: 0 10px 40px rgba(0,0,0,0.1);
    }

    h1 {
      text-align: center;
      margin-bottom: 25px;
      font-size: 28px;
    }

    .product {
      background: #f8f8f8;
      border-radius: 15px;
      padding: 20px;
      margin-bottom: 25px;
    }

    .product h2 {
      margin-bottom: 10px;
    }

    .price {
      font-size: 25px;
      font-weight: bold;
    }

    label {
      display: block;
      margin-top: 15px;
      margin-bottom: 7px;
      font-weight: bold;
    }

    input {
      width: 100%;
      padding: 13px;
      border: 1px solid #d1d5db;
      border-radius: 10px;
      font-size: 16px;
      outline: none;
    }

    input:focus {
      border-color: #111827;
    }

    .card-row {
      display: flex;
      gap: 10px;
    }

    .card-row div {
      flex: 1;
    }

    button {
      width: 100%;
      margin-top: 25px;
      padding: 15px;
      border: none;
      border-radius: 12px;
      background: #111827;
      color: white;
      font-size: 17px;
      font-weight: bold;
      cursor: pointer;
    }

    button:hover {
      background: #000;
    }

    .demo {
      text-align: center;
      margin-top: 15px;
      color: #777;
      font-size: 13px;
    }

    .success {
      display: none;
      text-align: center;
      padding: 20px 0;
    }

    .success-icon {
      width: 70px;
      height: 70px;
      background: #22c55e;
      color: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 38px;
      margin: 0 auto 20px;
    }

    .success h2 {
      margin-bottom: 12px;
    }

    .success p {
      color: #555;
      line-height: 1.5;
    }

    .username-result {
      margin-top: 15px;
      padding: 12px;
      background: #f3f4f6;
      border-radius: 10px;
      font-weight: bold;
    }

    .back-button {
      background: #e5e7eb;
      color: #111827;
    }
  </style>
</head>

<body>

  <div class="container">

    <!-- ФОРМА ОПЛАТЫ -->
    <div id="paymentPage">

      <h1>Оплата</h1>

      <div class="product">
        <h2>Цифровой продукт</h2>
        <p>Доступ к продукту после оплаты</p>
        <br>
        <div class="price">249 ₽</div>
      </div>

      <label for="username">Ваш username</label>
      <input
        type="text"
        id="username"
        placeholder="@username"
      >

      <label for="card">Номер карты</label>
      <input
        type="text"
        id="card"
        placeholder="0000 0000 0000 0000"
        maxlength="19"
      >

      <div class="card-row">

        <div>
          <label for="date">Срок</label>
          <input
            type="text"
            id="date"
            placeholder="MM/YY"
            maxlength="5"
          >
        </div>

        <div>
          <label for="cvv">CVV</label>
          <input
            type="text"
            id="cvv"
            placeholder="000"
            maxlength="3"
          >
        </div>

      </div>

      <button onclick="pay()">
        Оплатить 249 ₽
      </button>

      <div class="demo">
        🔒 Демо-оплата — реальные деньги не списываются
      </div>

    </div>


    <!-- СТРАНИЦА УСПЕШНОЙ ОПЛАТЫ -->
    <div id="successPage" class="success">

      <div class="success-icon">
        ✓
      </div>

      <h2>Оплачено!</h2>

      <p>
        Спасибо за покупку.
      </p>

      <div class="username-result">
        Username: <span id="resultUsername"></span>
      </div>

      <p style="margin-top: 20px;">
        📦 Продукт придёт в течение <b>1–14 дней</b>.
      </p>

      <button class="back-button" onclick="location.reload()">
        Вернуться
      </button>

    </div>

  </div>


  <script>

    // Формат номера карты
    document.getElementById("card").addEventListener("input", function(e) {

      let value = e.target.value.replace(/\D/g, "");

      value = value.substring(0, 16);

      let formatted = value.match(/.{1,4}/g);

      e.target.value = formatted
        ? formatted.join(" ")
        : "";

    });


    // Формат даты
    document.getElementById("date").addEventListener("input", function(e) {

      let value = e.target.value.replace(/\D/g, "");

      value = value.substring(0, 4);

      if (value.length >= 3) {
        value = value.substring(0, 2) + "/" + value.substring(2);
      }

      e.target.value = value;

    });


    // Только цифры для CVV
    document.getElementById("cvv").addEventListener("input", function(e) {

      e.target.value = e.target.value
        .replace(/\D/g, "")
        .substring(0, 3);

    });


    // Оплата
    function pay() {

      const username = document
        .getElementById("username")
        .value
        .trim();

      const card = document
        .getElementById("card")
        .value
        .replace(/\s/g, "");

      const date = document
        .getElementById("date")
        .value;

      const cvv = document
        .getElementById("cvv")
        .value;


      // Проверка username
      if (username === "") {
        alert("Введите username");
        return;
      }


      // Проверка тестовой карты
      if (card.length !== 16) {
        alert("Введите 16 цифр тестовой карты");
        return;
      }


      if (date.length !== 5) {
        alert("Введите срок действия карты в формате MM/YY");
        return;
      }


      if (cvv.length !== 3) {
        alert("Введите 3 цифры CVV");
        return;
      }


      // Показываем успешную оплату
      document.getElementById("paymentPage").style.display = "none";

      document.getElementById("successPage").style.display = "block";

      document.getElementById("resultUsername").textContent = username;

    }

  </script>

</body>
</html># ....
