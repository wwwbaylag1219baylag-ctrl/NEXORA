
<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#101827">
<title>NEXORA - Монголын нэгдсэн цахим зах зээл</title>

<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:Arial,sans-serif;background:#f3f5f9;color:#172033}
header{background:#101827;color:white;padding:14px 16px;position:sticky;top:0;z-index:10}
.topbar{max-width:1200px;margin:auto;display:flex;align-items:center;justify-content:space-between;gap:12px;flex-wrap:wrap}
.logo{font-size:27px;font-weight:bold;color:#38bdf8}
.logo small{display:block;font-size:10px;letter-spacing:2px;color:white}
.cart{background:#26364c;padding:11px 15px;border-radius:9px;cursor:pointer}
.hero{background:linear-gradient(135deg,#101827,#075985);color:white;text-align:center;padding:42px 15px}
.hero h1{font-size:27px;margin-bottom:12px}
.hero p{line-height:1.7;color:#dbeafe}
.container{max-width:1200px;margin:auto;padding:18px}
.section-title{font-size:21px;margin:25px 0 15px}
.search-box{display:flex;gap:8px;margin:15px 0}
input,select,textarea{font:inherit}
.search-box input,.field{width:100%;padding:13px;border:1px solid #cbd5e1;border-radius:8px;background:white}
button{border:0;border-radius:8px;padding:12px 16px;font-weight:bold;cursor:pointer}
.primary-btn{background:#0284c7;color:white}
.dark-btn{background:#172033;color:white}
.categories{display:grid;grid-template-columns:repeat(auto-fit,minmax(105px,1fr));gap:10px}
.category{background:white;padding:16px 7px;text-align:center;border-radius:10px;font-size:13px;font-weight:bold;box-shadow:0 2px 8px #0000000b;cursor:pointer}
.category span{display:block;font-size:27px;margin-bottom:7px}
.category.active{outline:2px solid #0284c7;color:#0284c7}
.products,.ad-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(155px,1fr));gap:13px}
.product,.ad-card{background:white;padding:12px;border-radius:11px;box-shadow:0 2px 9px #0000000b}
.product-image{height:135px;background:#e2e8f0;border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:48px;margin-bottom:10px}
.product h3,.ad-card h3{font-size:15px;margin:7px 0}
.price{color:#0284c7;font-weight:bold;margin:9px 0}
.product button{width:100%}
.tabs{display:grid;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));gap:9px;margin:20px 0}
.tab{background:white;padding:15px 8px;text-align:center;border-radius:9px;font-weight:bold;cursor:pointer;border:1px solid #e2e8f0}
.tab.active{background:#e0f2fe;border-color:#0284c7;color:#0369a1}
.panel{background:white;padding:17px;border-radius:11px;margin:15px 0}
.field{display:block;margin:10px 0}
textarea.field{min-height:100px;resize:vertical}
.hidden{display:none!important}
footer{background:#101827;color:white;text-align:center;padding:28px 15px;margin-top:35px;line-height:2}
footer strong{color:#38bdf8;font-size:25px}
@media(max-width:480px){
.hero h1{font-size:22px}
.search-box{flex-wrap:wrap}
.search-box button{width:100%}
.container{padding:13px}
}
</style>
</head>

<body>

<header>
<div class="topbar">
  <div class="logo">
    NEXORA
    <small>NEXT GENERATION MARKETPLACE</small>
  </div>
  <div class="cart" onclick="showCart()">
    🛒 Сагс (<span id="cartCount">0</span>)
  </div>
</div>
</header>

<section class="hero">
<h1>МОНГОЛЫН НЭГДСЭН ЦАХИМ ЗАХ ЗЭЭЛ</h1>
<p>Худалдааны шинэ эрин.</p>
<p>Бараа • Зар • Мэдээлэл • Үйлчилгээ</p>
</section>

<main class="container">

<div class="search-box">
<input type="search" id="searchInput" placeholder="Бараа, зар, үйлчилгээ хайх...">
<button class="primary-btn" onclick="searchAll()">Хайх</button>
</div>

<h2 class="section-title">📂 Худалдааны ангилал</h2>

<div class="categories" id="categories">
<div class="category active" data-category="Бүгд"><span>🌐</span>Бүгд</div>
<div class="category" data-category="Электрон бараа"><span>📱</span>Электрон бараа</div>
<div class="category" data-category="Хувцас"><span>👕</span>Хувцас</div>
<div class="category" data-category="Гутал"><span>👟</span>Гутал</div>
<div class="category" data-category="Гэр ахуй"><span>🏠</span>Гэр ахуй</div>
<div class="category" data-category="Автомашин"><span>🚗</span>Автомашин</div>
<div class="category" data-category="Хүүхдийн бараа"><span>🧸</span>Хүүхдийн бараа</div>
<div class="category" data-category="Гоо сайхан"><span>💄</span>Гоо сайхан</div>
<div class="category" data-category="Багаж"><span>🛠️</span>Багаж</div>
<div class="category" data-category="Хүнс"><span>🌾</span>Хүнс</div>
<div class="category" data-category="Бусад"><span>📦</span>Бусад</div>
</div>

<h2 class="section-title">🔥 Шинэ бараанууд</h2>

<div class="products" id="productList">
<div class="product" data-category="Электрон бараа">
<div class="product-image">📱</div>
<h3>Жишээ ухаалаг утас</h3>
<div class="price">450,000₮</div>
<button class="primary-btn" onclick="addToCart(this)">Сагслах</button>
</div>

<div class="product" data-category="Гутал">
<div class="product-image">👟</div>
<h3>Спорт гутал</h3>
<div class="price">85,000₮</div>
<button class="primary-btn" onclick="addToCart(this)">Сагслах</button>
</div>
</div>
</main>

<section class="container">

<div class="tabs">
  <div class="tab active" onclick="switchTab('market',this)">🛍️ Бараа</div>
  <div class="tab" onclick="switchTab('ads',this)">📢 Зар</div>
  <div class="tab" onclick="switchTab('news',this)">📰 Мэдээ</div>
  <div class="tab" onclick="switchTab('services',this)">🛠️ Үйлчилгээ</div>
  <div class="tab" onclick="switchTab('account',this)">👤 Миний булан</div>
</div>

<div id="market" class="tab-content">
  <h2 class="section-title">🛍️ Барааны зах зээл</h2>
  <p>Монголын бүх төрлийн барааг нэг дороос.</p>
</div>

<div id="ads" class="tab-content hidden">
  <h2 class="section-title">📢 Зар мэдээлэл</h2>
  <div class="categories">
    <div class="category">🏠 Үл хөдлөх</div>
    <div class="category">🚗 Автомашин</div>
    <div class="category">💼 Ажлын зар</div>
    <div class="category">🔑 Түрээс</div>
    <div class="category">📦 Бараа зарна</div>
    <div class="category">🤝 Үйлчилгээ</div>
    <div class="category">🔎 Ажил хайна</div>
    <div class="category">📋 Бусад зар</div>
  </div>
  <div class="panel">
    <button class="primary-btn" onclick="showSection('adFormArea')">＋ Зар нийтлэх</button>
  </div>
  <div id="adFormArea" class="panel hidden">
    <h3>Шинэ зар нийтлэх</h3>
    <input class="field" id="adTitle" placeholder="Зарын гарчиг">
    <select class="field" id="adCategory">
      <option value="">Зарын төрөл сонгох</option>
      <option>Үл хөдлөх</option>
      <option>Автомашин</option>
      <option>Ажлын зар</option>
      <option>Түрээс</option>
      <option>Бараа зарна</option>
      <option>Үйлчилгээ</option>
      <option>Бусад</option>
    </select>
    <textarea class="field" id="adDescription" placeholder="Зарын дэлгэрэнгүй"></textarea>
    <input class="field" id="adPrice" placeholder="Үнэ (₮)">
    <input class="field" id="adPhone" placeholder="Холбоо барих утас">
    <button class="primary-btn" onclick="publishAd()">Нийтлэх</button>
    <button class="dark-btn" onclick="showSection('')">Болих</button>
  </div>
  <div id="adList" class="ad-grid"></div>
</div>

<div id="news" class="tab-content hidden">
  <h2 class="section-title">📰 Мэдээ, мэдээлэл</h2>
  <div class="categories">
    <div class="category">🇲🇳 Монгол мэдээ</div>
    <div class="category">💼 Эдийн засаг</div>
    <div class="category">🏢 Байгууллага</div>
    <div class="category">🎉 Үйл явдал</div>
    <div class="category">📣 Зарлал</div>
    <div class="category">🌍 Дэлхий</div>
  </div>
  <div class="panel">
    <p>Мэдээ, мэдээллийн нийтлэлүүд энэ хэсэгт харагдана.</p>
    <p>Мэдээ нийтлэх эрхийг админ болон зөвшөөрөгдсөн байгууллагад олгоно.</p>
  </div>
</div>

<div id="services" class="tab-content hidden">
  <h2 class="section-title">🛠️ Үйлчилгээ</h2>
  <div class="categories">
    <div class="category">🔧 Засвар</div>
    <div class="category">🏗️ Барилга</div>
    <div class="category">🚚 Тээвэр</div>
    <div class="category">📦 Хүргэлт</div>
    <div class="category">💻 IT үйлчилгээ</div>
    <div class="category">🧹 Цэвэрлэгээ</div>
    <div class="category">🎨 Дизайн</div>
    <div class="category">📋 Бусад</div>
  </div>
</div>

<div id="account" class="tab-content hidden">
  <h2 class="section-title">👤 Миний булан</h2>
  <div class="panel">
    <p>Хэрэглэгчийн бүртгэл, нэвтрэх хэсэг</p>
    <input class="field" id="loginPhone" placeholder="Утасны дугаар">
    <input class="field" id="loginPassword" type="password" placeholder="Нууц үг">
    <button class="primary-btn" onclick="loginDemo()">Нэвтрэх</button>
    <button class="dark-btn" onclick="registerDemo()">Бүртгүүлэх</button>
  </div>
  <div class="panel">
    <p>📌 Миний зар</p>
    <p>❤️ Хадгалсан бараа</p>
    <p>🛒 Миний захиалга</p>
    <p>🔔 Мэдэгдэл</p>
  </div>
</div>

</section>

<section class="container hidden" id="cartArea">
<h2 class="section-title">🛒 Миний сагс</h2>
<div id="cartItems"></div>
<button class="dark-btn" onclick="closeCart()">Буцах</button>
</section>

<nav class="mobile-nav">
  <button onclick="switchTab('market')">🏠<small>Нүүр</small></button>
  <button onclick="switchTab('ads')">📢<small>Зар</small></button>
  <button onclick="switchTab('news')">📰<small>Мэдээ</small></button>
  <button onclick="switchTab('services')">🛠️<small>Үйлчилгээ</small></button>
  <button onclick="switchTab('account')">👤<small>Минийх</small></button>
</nav>

<style>
.tab-content{min-height:180px}
.mobile-nav{
  display:none;
  position:fixed;
  bottom:0;
  left:0;
  right:0;
  background:white;
  border-top:1px solid #e2e8f0;
  padding:7px 2px;
  z-index:20;
  justify-content:space-around;
}
.mobile-nav button{
  background:transparent;
  color:#334155;
  padding:5px;
  font-size:19px;
  display:flex;
  flex-direction:column;
  align-items:center;
  gap:3px;
}
.mobile-nav small{font-size:10px}
.ad-card{font-size:13px}
.ad-card p{margin:6px 0;line-height:1.5}
@media(max-width:600px){
  .mobile-nav{display:flex}
  body{padding-bottom:65px}
  .tabs{grid-template-columns:repeat(3,1fr)}
  .tab{font-size:12px;padding:11px 4px}
  .products,.ad-grid{
    grid-template-columns:repeat(2,minmax(0,1fr));
    gap:8px;
  }
  .product,.ad-card{padding:9px}
  .product-image{height:105px;font-size:35px}
  .product h3{font-size:13px}
  .price{font-size:13px}
  .category{padding:11px 4px;font-size:11px}
}
</style>

<script>
/* NEXORA ҮНДСЭН ҮЙЛДЛҮҮД */

let cart = [];
let selectedCategory = "Бүгд";

/* БАРАА САГСЛАХ */
function addToCart(button) {
  const product = button.closest(".product");
  if (!product) return;

  const name = product.querySelector("h3").textContent;
  const price = product.querySelector(".price").textContent;

  cart.push({name, price});

  document.getElementById("cartCount").textContent = cart.length;
  alert(name + " сагсанд нэмэгдлээ!");
}

/* САГС ХАРАХ */
function showCart() {
  document.querySelector("main").classList.add("hidden");
  document.querySelector(".tabs").parentElement.classList.add("hidden");
  document.getElementById("cartArea").classList.remove("hidden");

  renderCart();
}

function closeCart() {
  document.querySelector("main").classList.remove("hidden");
  document.querySelector(".tabs").parentElement.classList.remove("hidden");
  document.getElementById("cartArea").classList.add("hidden");
}

function renderCart() {
  const area = document.getElementById("cartItems");
  area.innerHTML = "";

  if (cart.length === 0) {
    area.textContent = "Таны сагс хоосон байна.";
    return;
  }

  cart.forEach((item, index) => {
    const row = document.createElement("div");
    row.className = "panel";

    const name = document.createElement("strong");
    name.textContent = item.name;

    const price = document.createElement("p");
    price.textContent = item.price;

    const remove = document.createElement("button");
    remove.className = "dark-btn";
    remove.textContent = "Устгах";
    remove.onclick = function() {
      cart.splice(index, 1);
      document.getElementById("cartCount").textContent = cart.length;
      renderCart();
    };

    row.append(name, price, remove);
    area.appendChild(row);
  });
}

/* БАРАА, ЗАР ХАЙХ */
function searchAll() {
  const query = document.getElementById("searchInput")
    .value.trim().toLowerCase();

  let count = 0;

  document.querySelectorAll(".product").forEach(item => {
    const match = item.textContent.toLowerCase().includes(query);
    item.style.display = match ? "" : "none";
    if (match) count++;
  });

  document.querySelectorAll(".ad-card").forEach(item => {
    const match = item.textContent.toLowerCase().includes(query);
    item.style.display = match ? "" : "none";
    if (match) count++;
  });

  switchTab("market");

  if (count === 0) {
    alert("Тохирох бараа, зар олдсонгүй.");
  }
}

/* АНГИЛАЛ ШҮҮХ */
document.querySelectorAll("#categories .category").forEach(category => {
  category.addEventListener("click", function() {
    selectedCategory = this.dataset.category || "Бүгд";

    document.querySelectorAll("#categories .category")
      .forEach(item => item.classList.remove("active"));

    this.classList.add("active");

    document.querySelectorAll(".product").forEach(product => {
      const match = selectedCategory === "Бүгд" ||
        product.dataset.category === selectedCategory;

      product.style.display = match ? "" : "none";
    });
  });
});

/* ЦЭС СОЛИХ */
function switchTab(name, element) {
  document.querySelectorAll(".tab-content").forEach(section => {
    section.classList.add("hidden");
  });

  const target = document.getElementById(name);
  if (target) target.classList.remove("hidden");

  document.querySelectorAll(".tabs .tab").forEach(tab => {
    tab.classList.remove("active");
  });

  if (element && element.classList.contains("tab")) {
    element.classList.add("active");
  } else {
    document.querySelectorAll(".tabs .tab").forEach(tab => {
      if (tab.getAttribute("onclick")?.includes("'" + name + "'")) {
        tab.classList.add("active");
      }
    });
  }

  document.getElementById("cartArea").classList.add("hidden");
  document.querySelector("main").classList.remove("hidden");
  document.querySelector(".tabs").parentElement.classList.remove("hidden");
}

/* ФОРМ НЭЭХ */
function showSection(id) {
  document.getElementById("adFormArea").classList.add("hidden");

  if (id) {
    document.getElementById(id).classList.remove("hidden");
  }
}

/* ЗАР НИЙТЛЭХ */
function publishAd() {
  const title = document.getElementById("adTitle").value.trim();
  const category = document.getElementById("adCategory").value;
  const description = document.getElementById("adDescription").value.trim();
  const price = document.getElementById("adPrice").value.trim();
  const phone = document.getElementById("adPhone").value.trim();

  if (!title || !category || !description || !phone) {
    alert("Гарчиг, төрөл, тайлбар, утсаа бүрэн бөглөнө үү.");
    return;
  }

  const card = document.createElement("div");
  card.className = "ad-card";

  const heading = document.createElement("h3");
  heading.textContent = title;

  const type = document.createElement("p");
  type.textContent = "Ангилал: " + category;

  const detail = document.createElement("p");
  detail.textContent = description;

  const cost = document.createElement("p");
  cost.textContent = price ? "Үнэ: " + price + "₮" : "Үнэ тохирно";

  const contact = document.createElement("p");
  contact.textContent = "Утас: " + phone;

  card.append(heading, type, detail, cost, contact);

  document.getElementById("adList").prepend(card);

  document.getElementById("adTitle").value = "";
  document.getElementById("adCategory").value = "";
  document.getElementById("adDescription").value = "";
  document.getElementById("adPrice").value = "";
  document.getElementById("adPhone").value = "";

  document.getElementById("adFormArea").classList.add("hidden");

  alert("Зар энэ төхөөрөмж дээр түр нийтлэгдлээ.");
}

/* НЭВТРЭХ, БҮРТГҮҮЛЭХ ДЕМО */
function loginDemo() {
  const phone = document.getElementById("loginPhone").value.trim();
  const password = document.getElementById("loginPassword").value;

  if (!phone || !password) {
    alert("Утас болон нууц үгээ оруулна уу.");
    return;
  }

  alert("Бодит хэрэглэгчийн бүртгэл, нэвтрэх сервер хараахан холбогдоогүй байна.");
}

function registerDemo() {
  alert("Хэрэглэгчийн бодит бүртгэлийн систем дараагийн хөгжүүлэлтээр холбогдоно.");
}

/* АНХНЫ ТӨЛӨВ */
switchTab("market");
</script>

</body>
</html>
