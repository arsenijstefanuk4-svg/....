
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>MM2 Shop</title>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
}

body {
    background: #f5f6f8;
    color: #111;
}

.page {
    max-width: 1250px;
    margin: 30px auto;
    padding: 0 15px;
}

/* ================= ТОВАР ================= */

.product {
    background: white;
    border-radius: 12px;
    padding: 6px;
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: 35px;
}

.product-img {
    width: 100%;
    height: 745px;
    object-fit: cover;
    border-radius: 8px;
}

.info {
    padding: 10px 15px 30px 5px;
}

.price-row {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 10px;
}

.price {
    color: #ff174d;
    font-size: 28px;
    font-weight: bold;
}

.discount {
    background: #ff174d;
    color: white;
    padding: 4px 9px;
    border-radius: 15px;
    font-weight: bold;
}

.old-price {
    color: #999;
    text-decoration: line-through;
}

.title {
    font-size: 18px;
    line-height: 1.5;
    margin-bottom: 12px;
}

.rating {
    color: #1764ff;
    margin-bottom: 28px;
}

.delivery {
    background: #f1f3f6;
    border-radius: 10px;
    padding: 20px;
    margin-bottom: 16px;
}

.delivery-title {
    font-size: 17px;
    font-weight: bold;
    margin-bottom: 12px;
}

.delivery-small {
    color: #888;
    margin-top: 7px;
    font-size: 14px;
}

.buy {
    width: 100%;
    height: 53px;
    background: #ff174d;
    color: white;
    border: none;
    border-radius: 8px;
    font-size: 18px;
    font-weight: bold;
    cursor: pointer;
}

.buy:hover {
    background: #e90042;
}

.guarantee {
    margin-top: 18px;
}

/* ================= ОПЛАТА ================= */

.payment {
    display: none;
    max-width: 500px;
    margin: 40px auto;
    background: white;
    padding: 30px;
    border-radius: 16px;
}

.payment h1 {
    margin-bottom: 20px;
}

.order {
    display: flex;
    gap: 14px;
    align-items: center;
    background: #f1f3f6;
    border-radius: 10px;
    padding: 12px;
    margin-bottom: 25px;
}

.order img {
    width: 80px;
    height: 65px;
    object-fit: cover;
    border-radius: 8px;
}

.order-price {
    color: #ff174d;
    font-weight: bold;
    margin-top: 5px;
}

label {
    display: block;
    font-weight: bold;
    margin: 15px 0 7px;
}

input {
    width: 100%;
    padding: 13px;
    border: 1px solid #d5d7db;
    border-radius: 9px;
    font-size: 16px;
    outline: none;
}

input:focus {
    border-color: #ff174d;
}

.row {
    display: flex;
    gap: 10px;
}

.row div {
    width: 50%;
}

.pay {
    width: 100%;
    height: 52px;
    margin-top: 25px;
    background: #ff174d;
    color: white;
    border: none;
    border-radius: 9px;
    font-size: 17px;
    font-weight: bold;
    cursor: pointer;
}

.back {
    width: 100%;
    height: 45px;
    margin-top: 10px;
    border: none;
    border-radius: 9px;
    background: #e9ebee;
    cursor: pointer;
}

.demo {
    text-align: center;
    color: #888;
    font-size: 12px;
    margin-top: 12px;
}

/* ================= ПРОВЕРКА ================= */

.processing {
    display: none;
    max-width: 500px;
    margin: 60px auto;
    background: white;
    border-radius: 16px;
    padding: 45px 30px;
    text-align: center;
}

.loader {
    width: 65px;
    height: 65px;
    border: 6px solid #eeeeee;
    border-top: 6px solid #ff174d;
    border-radius: 50%;
    margin: 0 auto 25px;
    animation: spin 1s linear infinite;
}

.processing h2 {
    margin-bottom: 10px;
}

.processing p {
    color: #777;
}

.status {
    margin-top: 25px;
    font-size: 14px;
    color: #555;
}

@keyframes spin {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}

/* ================= УСПЕШНО ================= */

.success {
    display: none;
    max-width: 500px;
    margin: 60px auto;
    background: white;
    border-radius: 16px;
    padding: 40px 30px;
    text-align: center;
}

.success-icon {
    width: 75px;
    height: 75px;
    border-radius: 50%;
    background: #22c55e;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 40px;
    margin: 0 auto 20px;
}

.success h1 {
    margin-bottom: 10px;
}

.success p {
    color: #555;
    line-height: 1.6;
}

.username {
    background: #f1f3f6;
    border-radius: 10px;
    padding: 13px;
    margin: 20px 0;
    font-weight: bold;
}

.done {
    width: 100%;
    height: 50px;
    margin-top: 25px;
    border: none;
    border-radius: 9px;
    background: #111827;
    color: white;
    font-size: 16px;
    cursor: pointer;
}

/* ================= МОБИЛЬНАЯ ВЕРСИЯ ================= */

@media(max-width: 850px) {

    .product {
        grid-template-columns: 1fr;
    }

    .product-img {
        height: auto;
        max-height: 600px;
    }

    .info {
        padding: 10px;
    }
}
</style>
</head>

<body>

<div class="page">

    <!-- ================= ТОВАР ================= -->

    <div class="product" id="productPage">

        <div>
            <img
                src="product.png"
                class="product-img"
                alt="Murder Mystery 2"
            >
        </div>

        <div class="info">

            <div class="price-row">
                <span class="price">210 ₽</span>

                <span class="discount">
                    -58%
                </span>

                <span class="old-price">
                    499
                </span>
            </div>

            <div class="title">
                🎁 АКЦИЯ 4 НОЖЕЙ + ПОДАРОК |
                Murder Mystery 2 🎁
            </div>

            <div class="rating">
                ★★★★★ &nbsp; 2226 отзывов
            </div>

            <div class="delivery">

                <div class="delivery-title">
                    📦 Способ получения
                </div>

                <div>
                    Трейд
                </div>

                <div class="delivery-small">
                    Передача предметов трейдом
                </div>

            </div>

            <button
                class="buy"
                onclick="openPayment()"
            >
                Купить
            </button>

            <div class="guarantee">
                🛡️ Гарантия Playerok ›
            </div>

        </div>

    </div>


    <!-- ================= ОПЛАТА ================= -->

    <div class="payment" id="paymentPage">

        <h1>
            Оплата заказа
        </h1>

        <div class="order">

            <img src="product.png">

            <div>
                <b>
                    4 ножей + подарок
                </b>

                <div class="order-price">
                    210 ₽
                </div>
            </div>

        </div>


        <label>
            Username
        </label>

        <input
            id="username"
            type="text"
            placeholder="@username"
        >


        <label>
            Номер карты
        </label>

        <input
            id="card"
            type="text"
            placeholder="0000 0000 0000 0000"
            maxlength="19"
        >


        <div class="row">

            <div>

                <label>
                    Срок
                </label>

                <input
                    id="date"
                    type="text"
                    placeholder="MM/YY"
                    maxlength="5"
                >

            </div>


            <div>

                <label>
                    CVV
                </label>

                <input
                    id="cvv"
                    type="text"
                    placeholder="000"
                    maxlength="3"
                >

            </div>

        </div>


        <button
            class="pay"
            onclick="startPayment()"
        >
            Оплатить 210 ₽
        </button>


        <div class="demo">
            🔒 Демо-режим — реальные деньги не списываются
        </div>


        <button
            class="back"
            onclick="backToProduct()"
        >
            ← Назад
        </button>

    </div>


    <!-- ================= ПРОВЕРКА ================= -->

    <div
        class="processing"
        id="processingPage"
    >

        <div class="loader"></div>

        <h2 id="processingTitle">
            Проверяем данные...
        </h2>

        <p id="processingText">
            Подождите несколько секунд
        </p>

        <div
            class="status"
            id="status"
        >
            Подключение к платёжной системе...
        </div>

    </div>


    <!-- ================= УСПЕШНАЯ ОПЛАТА ================= -->

    <div
        class="success"
        id="successPage"
    >

        <div class="success-icon">
            ✓
        </div>

        <h1>
            Оплачено!
        </h1>

        <p>
            Оплата успешно завершена.
        </p>

        <div class="username">
            Username:
            <span id="resultUsername"></span>
        </div>

        <p>
            📦 Продукт придёт в течение
            <b>1–14 дней</b>.
        </p>

        <p style="margin-top:15px;">
            Спасибо за покупку ❤️
        </p>

        <button
            class="done"
            onclick="location.reload()"
        >
            Вернуться в магазин
        </button>

    </div>

</div>


<script>

/* =========================================
   ОТКРЫТЬ ОПЛАТУ
========================================= */

function openPayment() {

    document.getElementById("productPage").style.display = "none";

    document.getElementById("paymentPage").style.display = "block";

    window.scrollTo(0, 0);
}


/* =========================================
   НАЗАД
========================================= */

function backToProduct() {

    document.getElementById("paymentPage").style.display = "none";

    document.getElementById("productPage").style.display = "grid";
}


/* =========================================
   НОМЕР КАРТЫ
========================================= */

document.getElementById("card").addEventListener(
    "input",
    function() {

        let value = this.value
            .replace(/\D/g, "")
            .substring(0, 16);

        let parts = value.match(/.{1,4}/g);

        this.value = parts
            ? parts.join(" ")
            : "";
    }
);


/* =========================================
   СРОК КАРТЫ
========================================= */

document.getElementById("date").addEventListener(
    "input",
    function() {

        let value = this.value
            .replace(/\D/g, "")
            .substring(0, 4);

        if (value.length >= 3) {

            value =
                value.substring(0, 2)
                + "/"
                + value.substring(2);
        }

        this.value = value;
    }
);


/* =========================================
   CVV
========================================= */

document.getElementById("cvv").addEventListener(
    "input",
    function() {

        this.value =
            this.value
            .replace(/\D/g, "")
            .substring(0, 3);
    }
);


/* =========================================
   НАЧАЛО ДЕМО-ОПЛАТЫ
========================================= */

function startPayment() {

    const username =
        document
        .getElementById("username")
        .value
        .trim();

    const card =
        document
        .getElementById("card")
        .value
        .replace(/\s/g, "");

    const date =
        document
        .getElementById("date")
        .value;

    const cvv =
        document
        .getElementById("cvv")
        .value;


    /* Проверяем поля */

    if (!username) {

        alert("Введите username");

        return;
    }


    if (card.length !== 16) {

        alert(
            "Введите 16 цифр тестовой карты"
        );

        return;
    }


    if (date.length !== 5) {

        alert(
            "Введите срок действия в формате MM/YY"
        );

        return;
    }


    if (cvv.length !== 3) {

        alert(
            "Введите 3 цифры тестового CVV"
        );

        return;
    }


    /* Скрываем оплату */

    document.getElementById(
        "paymentPage"
    ).style.display = "none";


    /* Показываем проверку */

    document.getElementById(
        "processingPage"
    ).style.display = "block";


    window.scrollTo(0, 0);


    /*
       ЭТАП 1
       Проверка
    */

    setTimeout(function() {

        document.getElementById(
            "processingTitle"
        ).textContent =
            "Проверяем данные...";

        document.getElementById(
            "status"
        ).textContent =
            "Данные карты проверяются...";

    }, 1000);


    /*
       ЭТАП 2
       Подтверждение
    */

    setTimeout(function() {

        document.getElementById(
            "processingTitle"
        ).textContent =
            "Подтверждаем оплату...";

        document.getElementById(
            "status"
        ).textContent =
            "Платёж подтверждён системой...";

    }, 2200);


    /*
       ЭТАП 3
       Симуляция списания
    */

    setTimeout(function() {

        document.getElementById(
            "processingTitle"
        ).textContent =
            "Списываем 210 ₽...";

        document.getElementById(
            "status"
        ).textContent =
            "Проводим операцию...";

    }, 3400);


    /*
       ЭТАП 4
       Успешно
    */

    setTimeout(function() {

        document.getElementById(
            "processingPage"
        ).style.display = "none";


        document.getElementById(
            "successPage"
        ).style.display = "block";


        document.getElementById(
            "resultUsername"
        ).textContent = username;


        window.scrollTo(0, 0);

    }, 5000);

}

</script>

</body>
</html>
