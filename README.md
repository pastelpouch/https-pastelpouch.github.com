# https-pastelpouch.github.com
"Charming finds to brighten your space and moments"
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Simple Shop</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 20px; }
    .products { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; }
    .product { border: 1px solid #ddd; padding: 15px; border-radius: 8px; text-align: center; }
    .cart { margin-top: 30px; border-top: 2px solid #333; padding-top: 20px; }
    button { padding: 8px 12px; background: #333; color: white; border: none; border-radius: 5px; cursor: pointer; }
    button:hover { background: #555; }
  </style>
</head>
<body>
  <h1>🛍️ My Shop</h1>

  <div class="products" id="products"></div>

  <div class="cart">
    <h2>Cart</h2>
    <ul id="cart-items"></ul>
    <p><strong>Total:</strong> $<span id="total">0</span></p>
    <button onclick="checkout()">Checkout</button>
  </div>

  <script>
    const products = [
      { id: 1, name: "T-Shirt", price: 20 },
      { id: 2, name: "Jeans", price: 40 },
      { id: 3, name: "Sneakers", price: 60 }
    ];
    const cart = [];

    function renderProducts() {
      const container = document.getElementById("products");
      container.innerHTML = products.map(p => `
        <div class="product">
          <h3>${p.name}</h3>
          <p>$${p.price}</p>
          <button onclick="addToCart(${p.id})">Add to Cart</button>
        </div>
      `).join("");
    }

    function addToCart(id) {
      const product = products.find(p => p.id === id);
      cart.push(product);
      renderCart();
    }

    function renderCart() {
      const items = document.getElementById("cart-items");
      items.innerHTML = cart.map(item => `<li>${item.name} - $${item.price}</li>`).join("");
      const total = cart.reduce((sum, item) => sum + item.price, 0);
      document.getElementById("total").textContent = total;
    }

    function checkout() {
      alert("Checkout not implemented yet!");
    }

    renderProducts();
  </script>
</body>
</html>

