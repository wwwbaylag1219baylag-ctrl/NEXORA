# NEXORA
Монголын онлайн худалдааны платформ

<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#101827">
<title>NEXORA | Монголын нэгдсэн цахим зах зээл</title>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, sans-serif;
  background: #f3f5f9;
  color: #172033;
}

header {
  background: #101827;
  color: white;
  padding: 15px;
}

.topbar {
  max-width: 1200px;
  margin: auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 12px;
}

.logo {
  font-size: 27px;
  font-weight: bold;
  color: #38bdf8;
}

.logo span {
  display: block;
  font-size: 10px;
  letter-spacing: 2px;
  color: white;
}

.cart {
  background: #1e293b;
  padding: 10px 14px;
  border-radius: 8px;
}

.hero {
  background: linear-gradient(135deg,#101827,#164e80);
  color: white;
  text-align: center;
  padding: 45px 15px;
}

.hero h1 {
  font-size: 28px;
  margin-bottom: 12px;
}

.hero p {
  font-size: 15px;
  line-height: 1.6;
}

.container {
  max-width: 1200px;
  margin: auto;
  padding: 18px;
}

.search-box {
  display: flex;
  gap: 8px;
  margin: 15px 0;
}

.search-box input {
  flex: 1;
  min-width: 0;
  padding: 13px;
  border: 1px solid #d1d5db;
  border-radius: 8px;
  font-size: 15px;
}

button {
  cursor: pointer;
  border: none;
  border-radius: 8px;
  padding: 12px 16px;
  font-weight: bold;
}

.primary-btn {
  background: #0284c7;
  color: white;
}

.section-title {
  font-size: 21px;
  margin: 24px 0 15px;
}

.categories {
  display: grid;
  grid-template-columns: repeat(auto-fit,minmax(105px,1fr));
  gap: 10px;
}

.category {
  background: white;
  padding: 17px 8px;
  border-radius: 10px;
  text-align: center;
  box-shadow: 0 2px 8px #0000000d;
  font-size: 14px;
  font-weight: bold;
}

.category span {
  display: block;
  font-size: 27px;
  margin-bottom: 7px;
}

.products {
  display: grid;
  grid-template-columns: repeat(auto-fit,minmax(145px,1fr));
  gap: 12px;
}

.product {
  background: white;
  border-radius: 10px;
  padding: 12px;
  box-shadow: 0 2px 8px #0000000d;
}

.product-image {
  background: #e2e8f0;
  height: 130px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 45px;
  margin-bottom: 10px;
}

.product h3 {
  font-size: 15px;
  margin-bottom: 8px;
}

.price {
  color: #0284c7;
  font-weight: bold;
  margin: 8px 0;
}

@media(max-width:480px) {
  .hero h1 {
    font-size: 23px;
  }

  .search-box {
    flex-wrap: wrap;
  }

  .search-box button {
    width: 100%;
  }
}
</style>
</head>

<body>

<header>
  <div class="topbar">
    <div class="logo">
      NEXORA
      <span>NEXT GENERATION MARKETPLACE</span>
    </div>
    <div class="cart">🛒 Сагс (<span id="cartCount">0</span>)</div>
  </div>
</header>

<section class="hero">
  <h1>МОНГОЛЫН НЭГДСЭН ЦАХИМ ЗАХ ЗЭЭЛ</h1>
  <p>Худалдааны шинэ эрин.<br>
  Монголын бүх төрлийн бараа, нэг нэгдсэн зах зээл.</p>
</section>

<main class="container">

<div class="search-box">
  <input type="search" id="searchInput" placeholder="Бараа хайх...">
  <button class="primary-btn" onclick="searchProducts()">Хайх</button>
</div>

<h2 class="section-title">📂 Ангиллууд</h2>

<div class="categories">
  <div class="category"><span>📱</span>Электрон бараа</div>
  <div class="category"><span>👕</span>Хувцас</div>
  <div class="category"><span>👟</span>Гутал</div>
  <div class="category"><span>🏠</span>Гэр ахуй</div>
  <div class="category"><span>🚗</span>Автомашин</div>
  <div class="category"><span>🧸</span>Хүүхдийн бараа</div>
  <div class="category"><span>💄</span>Гоо сайхан</div>
  <div class="category"><span>🛠️</span>Багаж хэрэгсэл</div>
  <div class="category"><span>🌾</span>Хүнс</div>
  <div class="category"><span>📦</span>Бусад</div>
</div>

<h2 class="section-title">🔥 Шинэ бараанууд</h2>

<div class="products" id="productList">
  <div class="product">
    <div class="product-image">📱</div>
    <h3>Жишээ ухаалаг утас</h3>
    <div class="price">450,000₮</div>
    <button class="primary-btn" onclick="addToCart()">Сагслах</button>
  </div>

  <div class="product">
    <div class="product-image">👟</div>
    <h3>Спорт гутал</h3>
    <div class="price">85,000₮</div>
    <button class="primary-btn" onclick="addToCart()">Сагслах</button>
  </div>
</div>
</main>

<script>
let cart = [];

function addToCart() {
  const product = event.target.closest(".product");
  if (!product) return;

  const name = product.querySelector("h3").textContent;
  const price = product.querySelector(".price").textContent;

  cart.push({ name, price });

  document.getElementById("cartCount").textContent =
    cart.length;

  alert(name + " сагсанд нэмэгдлээ!");
}

function searchProducts() {
  const input = document
    .getElementById("searchInput")
    .value.toLowerCase()
    .trim();

  const products = document.querySelectorAll(".product");
  let found = 0;

  products.forEach(product => {
    const name = product.textContent.toLowerCase();

    if (name.includes(input)) {
      product.style.display = "";
      found++;
    } else {
      product.style.display = "none";
    }
  });

  if (found === 0) {
    alert("Хайлтад тохирох бараа олдсонгүй.");
  }
}

document.querySelectorAll(".category").forEach(category => {
  category.style.cursor = "pointer";

  category.addEventListener("click", () => {
    alert(
      category.textContent.trim() +
      " ангиллыг сонголоо."
    );
  });
});
</script>

item.append(heading, detail, cost);

  document.getElementById("adList").appendChild(item);

  document.getElementById("adTitle").value = "";
  document.getElementById("adDescription").value = "";
  document.getElementById("adPrice").value = "";

  document.getElementById("adForm").style.display = "none";

  alert("Зар амжилттай нийтлэгдлээ! (Демо хувилбар)");
}
</script>

</body>
</html>
