<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Магазин — Murder Mystery 2</title>

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

.product-page {
    background: white;
    border-radius: 12px;
    padding: 6px;
    display: grid;
    grid-template-columns: minmax(500px, 2fr) minmax(350px, 1fr);
    gap: 35px;
}

.product-image {
    width: 100%;
    height: 745px;
    object-fit: cover;
    border-radius: 8px;
    display: block;
}

.info {
    padding: 10px 15px 30px 5px;
}

.price-line {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 8px;
}

.price {
    color: #ff174d;
    font-size: 27px;
    font-weight: 700;
}

.discount {
    background: #ff174d;
    color: white;
    border-radius: 15px;
    padding: 4px 9px;
    font-weight: bold;
}

.old-price {
    color: #999;
    text-decoration: line-through;
    font-size: 16px;
}

.title {
    font-size: 18px;
    line-height: 1.45;
    margin: 5px 0 12px;
}

.rating {
    color: #1764ff;
    font-size: 16px;
    margin-bottom: 28px;
}

.delivery {
    background: #f1f3f6;
    border-radius: 10px;
    padding: 20px;
    margin-bottom: 16px;
}

.delivery-title {
    font-weight: bold;
    font-size: 17px;
    margin-bottom: 10px;
}

.delivery-main {
    font-size: 16px;
    margin-bottom: 7px;
}

.delivery-small {
    color: #8b8f96;
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
    transition: 0.2s;
}

.buy:hover {
    background: #e6003f;
}

.guarantee {
    margin-top: 18px;
    font-size: 16px;
}

/* ОПЛАТА */

.payment {
    display: none;
    max-width: 500px;
    margin: 40px auto;
    background: white;
    border-radius: 16px;
    padding: 30px;
}

.payment h1 {
    margin-bottom: 25px;
}

.product-mini {
    display: flex;
    gap: 15px;
    align-items: center;
    background: #f3f4f6;
    padding: 12px;
    border-radius: 12px;
    margin-bottom: 25px;
}

.product-mini img {
    width: 80px;
    height: 65px;
    object-fit: cover;
    border-radius: 8px;
}

.product-mini b {
    display: block;
    margin-bottom: 5px;
}

label {
    display: block;
    font-weight: bold;
    margin-bottom: 7px;
    margin-top: 16px;
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

.pay-button {
    width: 100%;
    margin-top: 25px;
    height: 52px;
    border: none;
    border-radius: 9px;
    background: #ff174d;
    color: white;
    font-size: 17px;
    font-weight: bold;
    cursor: pointer;
}

.demo {
    text-align: center;
    color: #888;
    font-size: 12px;
    margin-top: 12px;
}

.back {
    width: 100%;
    margin-top: 10px;
    height: 45px;
    border: none;
    border-radius: 9px;
    background: #e9ebee;
    cursor: pointer;
}

/* УСПЕШНАЯ ОПЛАТА */

.success {
    display: none;
    max-width: 500px;
    margin: 70px auto;
    background: white;
    border-radius: 16px;
    padding: 40px 30px;
    text-align: center;
}

.success-icon {
    width: 75px;
    height: 75px;
    background: #22c55e;
    color: white;
    border-radius: 50%;
    margin: 0 auto 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 40px;
}

.success h1 {
    margin-bottom: 12px;
}

.success p {
    color: #555;
    line-height: 1.6;
}

.user-result {
    background: #f1f3f6;
    border-radius: 10px;
    padding: 13px;
    margin: 20px 0;
    font-weight: bold;
}

@media(max-width: 850px) {
    .product-page {
        grid-template-columns: 1fr;
    }

    .product-image {
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

    <!-- СТРАНИЦА ТОВАРА -->
    <div class="product-page" id="productPage">

        <div>
            <img
                src="product.png"
                class="product-image"
                alt="Murder Mystery 2"
            >
        </div>

        <div class="info">

            <div class="price-line">
                <span class="price">210 ₽</span>
                <span class="discount">-58%</span>
                <span class="old-price">499</span>
            </div>

            <div class="title">
                🎁 АКЦИЯ 4 НОЖЕЙ + ПОДАРОК | Murder Mystery 2 🎁
            </div>

            <div class="rating">
                ★★★★★ &nbsp; 2226 отзывов
            </div>

            <div class="delivery">

                <div class="delivery-title">
                    📦 Способ получения
                </div>

                <div class="delivery-main">
                    Трейд
                </div>

                <div class="delivery-small">
                    Передача предметов трейдом
                </div>

            </div>

            <button class="buy" onclick="openPayment()">
                Купить
            </button>

            <div class="guarantee">
                🛡️ Гарантия Playerok &nbsp;›
            </div>

        </div>

    </div>


    <!-- СТРАНИЦА ОПЛАТЫ -->
    <div class="payment" id="paymentPage">

        <h1>Оплата заказа</h1>

        <div class="product-mini">

            <img src="product.png">

            <div>
                <b>4 ножей + подарок</b>
                <span>Стоимость: <b>210 ₽</b></span>
            </div>

        </div>

        <label>Username</label>
        <input
            id="username"
            type="text"
            placeholder="@username"
        >

        <label>Номер карты</label>
        <input
            id="card"
            type="text"
            placeholder="0000 0000 0000 0000"
            maxlength="19"
        >

        <div class="row">

            <div>
                <label>Срок действия</label>
                <input
                    id="date"
                    type="text"
                    placeholder="MM/YY"
                    maxlength="5"
                >
            </div>

            <div>
                <label>CVV</label>
                <input
                    id="cvv"
                    type="text"
                    placeholder="000"
                    maxlength="3"
                >
            </div>

        </div>

        <button class="pay-button" onclick="pay()">
            Оплатить 210 ₽
        </button>

        <div class="demo">
            🔒 Демо-оплата. Реальные деньги не списываются.
        </div>

        <button class="back" onclick="backToProduct()">
            ← Вернуться к товару
        </button>

    </div>


    <!-- УСПЕШНАЯ ОПЛАТА -->
    <div class="success" id="successPage">

        <div class="success-icon">
            ✓
        </div>

        <h1>Оплачено!</h1>

        <p>
            Заказ успешно оформлен.
        </p>

        <div class="user-result">
            Username: <span id="resultUsername"></span>
        </div>

        <p>
            📦 Продукт придёт в течение
            <b>1–14 дней</b>.
        </p>

        <button class="pay-button" onclick="location.reload()">
            Вернуться в магазин
        </button>

    </div>

</div>


<script>

/* Открыть оплату */

function openPayment() {

    document.getElementById("productPage").style.display = "none";

    document.getElementById("paymentPage").style.display = "block";

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });
}


/* Вернуться к товару */

function backToProduct() {

    document.getElementById("paymentPage").style.display = "none";

    document.getElementById("productPage").style.display = "grid";
}


/* Формат номера карты */

document.getElementById("card").addEventListener("input", function() {

    let value = this.value
        .replace(/\D/g, "")
        .substring(0, 16);

    let parts = value.match(/.{1,4}/g);

    this.value = parts ? parts.join(" ") : "";
});


/* Формат срока */

document.getElementById("date").addEventListener("input", function() {

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
});


/* Только цифры CVV */

document.getElementById("cvv").addEventListener("input", function() {

    this.value = this.value
        .replace(/\D/g, "")
        .substring(0, 3);
});


/* Демо-оплата */

function pay() {

    const username =
        document.getElementById("username").value.trim();

    const card =
        document.getElementById("card").value
        .replace(/\s/g, "");

    const date =
        document.getElementById("date").value;

    const cvv =
        document.getElementById("cvv").value;


    if (!username) {
        alert("Введите username");
        return;
    }

    if (card.length !== 16) {
        alert("Введите 16 цифр тестовой карты");
        return;
    }

    if (date.length !== 5) {
        alert("Введите срок в формате MM/YY");
        return;
    }

    if (cvv.length !== 3) {
        alert("Введите 3 цифры CVV");
        return;
    }


    document.getElementById("paymentPage").style.display = "none";

    document.getElementById("successPage").style.display = "block";

    document.getElementById("resultUsername").textContent =
        username;

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });
}

</script>

</body>
</html>
