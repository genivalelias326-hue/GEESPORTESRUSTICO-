<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">

  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <meta name="theme-color" content="#155eef">

  <title>GEESPORTESRUSTICO</title>

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: Arial, Helvetica, sans-serif;
      background: #f4f7fc;
      color: #1f2937;
    }

    header {
      background: #155eef;
      color: white;
      padding: 22px 16px;
      text-align: center;
      position: sticky;
      top: 0;
      z-index: 10;
    }

    header h1 {
      margin: 0;
      font-size: 24px;
    }

    header p {
      margin: 6px 0 0;
      font-size: 13px;
    }

    .container {
      max-width: 1000px;
      margin: auto;
      padding: 16px;
    }

    .search-box {
      margin: 15px 0 25px;
    }

    .search-box input {
      width: 100%;
      padding: 15px;
      border-radius: 12px;
      border: 1px solid #ddd;
      font-size: 16px;
    }

    h2 {
      font-size: 20px;
      margin-top: 25px;
    }

    .categories {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 10px;
    }

    .category {
      background: white;
      border: none;
      padding: 18px 10px;
      border-radius: 14px;
      font-size: 15px;
      font-weight: bold;
      cursor: pointer;
      box-shadow: 0 3px 10px rgba(0,0,0,0.08);
    }

    .category:hover {
      background: #eaf0ff;
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      gap: 16px;
      margin-top: 15px;
    }

    .product {
      background: white;
      border-radius: 16px;
      overflow: hidden;
      box-shadow: 0 3px 12px rgba(0,0,0,0.10);
    }

    .product img {
      width: 100%;
      height: 180px;
      object-fit: cover;
      background: #eee;
    }

    .product-info {
      padding: 14px;
    }

    .product h3 {
      margin: 0 0 8px;
      font-size: 16px;
    }

    .price {
      color: #155eef;
      font-size: 18px;
      font-weight: bold;
      margin-bottom: 8px;
    }

    .platform {
      font-size: 13px;
      margin-bottom: 12px;
      color: #666;
    }

    .buy-button {
      display: block;
      text-align: center;
      background: #16a34a;
      color: white;
      padding: 13px;
      border-radius: 10px;
      text-decoration: none;
      font-weight: bold;
    }

    .admin {
      background: white;
      margin-top: 35px;
      padding: 20px;
      border-radius: 16px;
      box-shadow: 0 3px 12px rgba(0,0,0,0.08);
    }

    .admin h2 {
      margin-top: 0;
    }

    .admin input,
    .admin select {
      width: 100%;
      padding: 13px;
      margin: 7px 0;
      border-radius: 10px;
      border: 1px solid #ddd;
      font-size: 15px;
    }

    .add-button {
      width: 100%;
      background: #155eef;
      color: white;
      border: none;
      padding: 15px;
      border-radius: 10px;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
      margin-top: 8px;
    }

    .empty {
      text-align: center;
      color: #777;
      padding: 30px;
    }

    footer {
      text-align: center;
      padding: 30px 15px;
      color: #777;
      font-size: 13px;
    }
  </style>
</head>

<body>

<header>
  <h1>🛒 GEESPORTESRUSTICO</h1>
  <p>Ofertas e produtos selecionados para você</p>
</header>

<div class="container">

  <div class="search-box">
    <input
      type="text"
      id="searchInput"
      placeholder="🔎 Pesquisar produtos..."
      onkeyup="searchProducts()"
    >
  </div>

  <h2>📂 Categorias</h2>

  <div class="categories">

    <button class="category" onclick="filterCategory('Cozinha')">
      🍳 Cozinha
    </button>

    <button class="category" onclick="filterCategory('Banheiro')">
      🚿 Artigos Banheiro
    </button>

    <button class="category" onclick="filterCategory('Brinquedos')">
      🧸 Brinquedos
    </button>

    <button class="category" onclick="filterCategory('Carro')">
      🚗 Acessórios de Carro
    </button>

    <button class="category" onclick="filterCategory('Roupa de Time')">
      ⚽ Roupa de Time
    </button>

    <button class="category" onclick="filterCategory('Celular')">
      📱 Celular
    </button>

    <button class="category" onclick="filterCategory('Fones')">
      🎧 Fones de Ouvido
    </button>

    <button class="category" onclick="filterCategory('Pet')">
      🐶 Pet
    </button>

    <button class="category" onclick="filterCategory('Moda')">
      👕 Moda
    </button>

    <button class="category" onclick="filterCategory('Tênis')">
      👟 Tênis
    </button>

  </div>

  <h2 id="productsTitle">🔥 Produtos e Ofertas</h2>

  <div class="products" id="products"></div>


  <!-- ÁREA DE CADASTRO -->

  <div class="admin">

    <h2>➕ Cadastrar Produto</h2>

    <input
      type="text"
      id="productName"
      placeholder="Nome do produto"
    >

    <input
      type="text"
      id="productPrice"
      placeholder="Preço (Ex: R$ 99,90)"
    >

    <input
      type="url"
      id="productImage"
      placeholder="Link da imagem do produto"
    >

    <select id="productCategory">

      <option value="">Escolha a categoria</option>

      <option>Cozinha</option>
      <option>Banheiro</option>
      <option>Brinquedos</option>
      <option>Carro</option>
      <option>Roupa de Time</option>
      <option>Celular</option>
      <option>Fones</option>
      <option>Pet</option>
      <option>Moda</option>
      <option>Tênis</option>

    </select>

    <select id="productPlatform">

      <option value="">Plataforma</option>
      <option>Shopee</option>
      <option>Mercado Livre</option>

    </select>

    <input
      type="url"
      id="productLink"
      placeholder="Cole aqui seu link de afiliado"
    >

    <button class="add-button" onclick="addProduct()">
      🚀 PUBLICAR PRODUTO
    </button>

  </div>

</div>

<footer>
  © 2026 GEESPORTESRUSTICO • Ofertas selecionadas
</footer>


<script>

let products = JSON.parse(localStorage.getItem("geProdutos")) || [];


function saveProducts() {
  localStorage.setItem("geProdutos", JSON.stringify(products));
}


function renderProducts(list = products) {

  const container = document.getElementById("products");

  container.innerHTML = "";

  if (list.length === 0) {

    container.innerHTML = `
      <div class="empty">
        Nenhum produto encontrado.<br>
        Cadastre seu primeiro produto abaixo! 🛒
      </div>
    `;

    return;
  }


  list.forEach(product => {

    container.innerHTML += `

      <div class="product">

        <img
          src="${product.image}"
          alt="${product.name}"
          onerror="this.src='https://via.placeholder.com/400x300?text=Produto'"
        >

        <div class="product-info">

          <h3>${product.name}</h3>

          <div class="price">${product.price}</div>

          <div class="platform">
            🛍️ ${product.platform}
          </div>

          <a
            class="buy-button"
            href="${product.link}"
            target="_blank"
          >
            🛒 COMPRAR AGORA
          </a>

        </div>

      </div>

    `;

  });

}


function addProduct() {

  const name = document.getElementById("productName").value.trim();

  const price = document.getElementById("productPrice").value.trim();

  const image = document.getElementById("productImage").value.trim();

  const category = document.getElementById("productCategory").value;

  const platform = document.getElementById("productPlatform").value;

  const link = document.getElementById("productLink").value.trim();


  if (
    !name ||
    !price ||
    !image ||
    !category ||
    !platform ||
    !link
  ) {

    alert("⚠️ Preencha todos os campos!");

    return;

  }


  products.push({

    name,
    price,
    image,
    category,
    platform,
    link

  });


  saveProducts();

  renderProducts();


  document.getElementById("productName").value = "";

  document.getElementById("productPrice").value = "";

  document.getElementById("productImage").value = "";

  document.getElementById("productCategory").value = "";

  document.getElementById("productPlatform").value = "";

  document.getElementById("productLink").value = "";


  alert("✅ Produto publicado com sucesso!");

}


function filterCategory(category) {

  const filtered = products.filter(
    product => product.category === category
  );

  document.getElementById("productsTitle").innerText =
    "📂 " + category;

  renderProducts(filtered);

}


function searchProducts() {

  const search = document
    .getElementById("searchInput")
    .value
    .toLowerCase();


  const filtered = products.filter(product =>
    product.name.toLowerCase().includes(search)
  );


  document.getElementById("productsTitle").innerText =
    "🔎 Resultado da pesquisa";


  renderProducts(filtered);

}


renderProducts();

</script>

</body>
</html>