<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SOLITEI Fencing Supplies</title>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #fff;
  color: #333;
}

header {
  background: #1b5e20;
  color: white;
  padding: 60px 20px;
  text-align: center;
}

header h1 {
  font-size: 2.4rem;
}

.btn {
  background: #f57c00;
  color: white;
  padding: 12px 25px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
}

section {
  padding: 40px 20px;
  max-width: 1100px;
  margin: auto;
}

.products {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

.card {
  border: 1px solid #eee;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
}

.card h3 {
  color: #1b5e20;
}

input[type="number"] {
  width: 70px;
  padding: 5px;
}

.order-box {
  background: #f5f5f5;
  padding: 20px;
  border-radius: 8px;
}

footer {
  background: #1b5e20;
  color: white;
  text-align: center;
  padding: 15px;
}
</style>
</head>

<body>

<header>
  <h1>SOLITEI Fencing Supplies</h1>
  <p>Quality Fencing Posts & Wires | Emali Town, Kenya</p>
  <a href="#products"><button class="btn">View Products</button></a>
</header>

<section id="products">
  <h2>Fencing Posts</h2>
  <div class="products">
    <div class="card">
      <h3>Concrete Posts</h3>
      <p>KES 1,500 per post</p>
      Qty: <input type="number" min="0" value="0" data-name="Concrete Post" data-price="1500">
    </div>

    <div class="card">
      <h3>Steel W-Posts</h3>
      <p>KES 450 per post</p>
      Qty: <input type="number" min="0" value="0" data-name="Steel W-Post" data-price="350">
    </div>

    <div class="card">
      <h3>Wooden Posts</h3>
      <p>KES 700 per post</p>
      Qty: <input type="number" min="0" value="0" data-name="Wooden Post" data-price="600">
    </div>
  </div>
</section>

<section>
  <h2>Fencing Wires</h2>
  <div class="products">
    <div class="card">
      <h3>Barbed Wire (Roll)</h3>
      <p>KES 6,500 per roll</p>
      Qty: <input type="number" min="0" value="0" data-name="Barbed Wire Roll" data-price="6500">
    </div>

    <div class="card">
      <h3>Chain Link Wire (Per Meter)</h3>
      <p>KES 350 per meter</p>
      Qty: <input type="number" min="0" value="0" data-name="Chain Link Wire" data-price="350">
    </div>

    <div class="card">
      <h3>Electric Fence HT Wire</h3>
      <p>KES 7,000 per roll</p>
      Qty: <input type="number" min="0" value="0" data-name="Electric Fence Wire" data-price="7000">
    </div>
  </div>
</section>

<section>
  <h2>Order Summary</h2>
  <div class="order-box">
    <p id="summary">No items selected.</p>
    <button class="btn" onclick="sendOrder()">Order via WhatsApp</button>
  </div>
</section>

<section>
  <h2>Contact & Location</h2>
  <p>📍 Emali Town, Kenya</p>
  <p>📞 0743505529</p>
</section>

<footer>
  <p>© 2026 SOLITEI Fencing Supplies</p>
</footer>

<script>
function sendOrder() {
  let inputs = document.querySelectorAll('input[type="number"]');
  let message = "Hello, I would like to order:%0A";
  let total = 0;
  let hasItems = false;

  inputs.forEach(input => {
    let qty = parseInt(input.value);
    let price = parseInt(input.dataset.price);
    let name = input.dataset.name;

    if (qty > 0) {
      hasItems = true;
      total += qty * price;
      message += `- ${name}: ${qty} pcs%0A`;
    }
  });

  if (!hasItems) {
    alert("Please select at least one item.");
    return;
  }

  message += `%0ATotal Estimate: KES ${total}`;
  let phone = "254743505529"; // replace with your WhatsApp number
  window.open(`https://wa.me/${phone}?text=${message}`, "_blank");
}
</script>

</body>
</html>
