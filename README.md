# shopify-alibaba-theme
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{{ shop.name }} - {{ page_title }}</title>
  {{ content_for_header }}
  {{ 'theme.css' | asset_url | stylesheet_tag }}
</head>
<body>
  {% section 'header' %}
  <main>
    {{ content_for_layout }}
  </main>
  {% section 'footer' %}
  {{ 'theme.js' | asset_url | script_tag }}
</body>
</html>
<header class="header">
  <div class="header-top">
    <div class="logo">
      <a href="/">{{ shop.name }}</a>
    </div>
    <div class="search-bar">
      {% render 'search-form' %}
    </div>
    <div class="user-actions">
      <a href="/cart">Cart ({{ cart.item_count }})</a>
    </div>
  </div>
  <nav class="navbar">
    <ul>
      <li><a href="/">Home</a></li>
      <li><a href="/collections">Products</a></li>
      <li><a href="/pages/suppliers">Suppliers</a></li>
      <li><a href="/pages/contact">Contact</a></li>
    </ul>
  </nav>
</header>
<form action="/search" method="get" role="search">
  <input
    type="search"
    name="q"
    placeholder="Search products, suppliers..."
    aria-label="Search"
  >
  <button type="submit">Search</button>
</form>
<div class="product-grid">
  {% for product in collection.products %}
    <div class="product-item">
      <a href="{{ product.url }}">
        <img
          src="{{ product.featured_image | img_url: 'medium' }}"
          alt="{{ product.title }}"
        >
        <h3>{{ product.title }}</h3>
        <p>{{ product.price | money }}</p>
      </a>
    </div>
  {% endfor %}
</div>
/* Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* Header */
.header-top {
  display: flex;
  justify-content: space-between;
  padding: 1rem;
  background: #f8f9fa;
}

.logo a {
  font-size: 24px;
  font-weight: bold;
  text-decoration: none;
  color: #333;
}

.search-bar input {
  padding: 8px;
  width: 400px;
  border: 1px solid #ddd;
}

.navbar {
  background: #232f3e;
  padding: 1rem;
}

.navbar ul {
  list-style: none;
  display: flex;
  gap: 2rem;
}

.navbar a {
  color: white;
  text-decoration: none;
}

/* Product Grid */
.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 1rem;
  padding: 1rem;
}

.product-item {
  border: 1px solid #ddd;
  padding: 1rem;
  text-align: center;
}

.product-item img {
  max-width: 100%;
  height: auto;
}
// Toggle mobile menu (add later)
document.addEventListener('DOMContentLoaded', function() {
  console.log('Theme loaded!');
});
npm install -g @shopify/cli
