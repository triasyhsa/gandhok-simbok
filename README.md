<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Gandhok Simbok - Warung Makan</title>
<style>
  body {
    font-family: Arial, sans-serif;
    background: #fff6f6;
    color: #8b0000;
    margin: 0;
    padding: 20px;
  }
  header {
    text-align: center;
    background-color: #d32f2f;
    color: white;
    padding: 15px 0;
    font-size: 2em;
    font-weight: bold;
  }
  .menu {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 15px;
    margin: 20px 0;
  }
  .menu-item {
    background: white;
    border: 2px solid #d32f2f;
    border-radius: 8px;
    width: 240px;
    padding: 10px;
    text-align: center;
  }
  .menu-item h3 {
    margin: 0 0 10px;
  }
  .menu-item select, .menu-item button {
    margin-top: 8px;
    width: 100%;
    padding: 8px;
    border-radius: 4px;
    border: 1px solid #d32f2f;
    font-size: 1em;
  }
  .menu-item button {
    background: #d32f2f;
    color: white;
    border: none;
    cursor: pointer;
  }
  .menu-item button:hover {
    background: #b71c1c;
  }
  #cart {
    background: white;
    border: 2px solid #d32f2f;
    border-radius: 8px;
    padding: 15px;
    max-width: 500px;
    margin: 0 auto 40px auto;
  }
  #cart h2 {
    margin-top: 0;
    text-align: center;
  }
  #cart-list {
    list-style: none;
    padding: 0;
    margin: 10px 0;
  }
  #cart-list li {
    display: flex;
    justify-content: space-between;
    padding: 5px 0;
    border-bottom: 1px solid #ddd;
    align-items: center;
  }
  #cart-list li span {
    flex-grow: 1;
    padding-left: 10px;
    text-align: left;
  }
  #cart-total {
    font-weight: bold;
    text-align: right;
    margin-top: 10px;
  }
  #payment-method {
    margin-top: 15px;
    text-align: center;
  }
  #payment-method label {
    margin: 0 15px;
    cursor: pointer;
  }
  #order-buttons {
    display: flex;
    justify-content: space-around;
    margin-top: 20px;
  }
  #order-buttons a, #order-buttons button {
    background: #d32f2f;
    color: white;
    text-decoration: none;
    padding: 12px 20px;
    border-radius: 6px;
    font-weight: bold;
    cursor: pointer;
  }
  #order-buttons a:hover, #order-buttons button:hover {
    background: #b71c1c;
  }
  button.remove-btn {
    background: none;
    border: none;
    color: #d32f2f;
    font-size: 20px;
    cursor: pointer;
  }
</style>
</head>
<body>

<header>Gandhok Simbok</header>

<section class="menu" id="menu">
  <!-- Menu items akan dimasukkan JS -->
</section>

<section id="cart">
  <h2>Keranjang Belanja</h2>
  <ul id="cart-list">
    <li>Keranjang kosong</li>
  </ul>
  <div id="cart-total"></div>

  <div id="payment-method" style="display:none;">
    <p><strong>Pilih Metode Pembayaran:</strong></p>
    <label><input type="radio" name="payment" value="Cash" checked /> Cash</label>
    <label><input type="radio" name="payment" value="Transfer" /> Transfer</label>
  </div>

  <div id="order-buttons" style="display:none;">
    <a href="#" id="whatsapp-order" target="_blank">Pesan via WhatsApp</a>
    <a href="https://gofood.link/a/PQXft4o" target="_blank">Order via GoFood</a>
  </div>
</section>

<script>
  const menuData = [
    {
      id: 1,
      name: "Kremesan",
      price: 8000,
      variants: [
        "Sambal Original",
        "Sambal Terasi",
        "Sambal Bawang",
        "Sambal Campur",
        "Sambal Kacang",
        "Sambal Tomat"
      ]
    },
    {
      id: 2,
      name: "Krispi Celup",
      price: 12000,
      variants: [
        "Saos Judes",
        "Saus Keju",
        "Saus Kari",
        "Saus Lada Hitam",
        "Saus Original"
      ]
    },
    {
      id: 3,
      name: "Mie Jebew",
      price: 15000,
      variants: [
        "Mie Original",
        "Mie Ayam Bawang",
        "Mie Lada Hitam",
        "Mie Rendang",
        "Mie Kari"
      ]
    }
  ];

  const waNumber = "085712028101";

  const menuContainer = document.getElementById("menu");
  const cartList = document.getElementById("cart-list");
  const cartTotal = document.getElementById("cart-total");
  const orderButtons = document.getElementById("order-buttons");
  const whatsappOrderLink = document.getElementById("whatsapp-order");
  const paymentMethodDiv = document.getElementById("payment-method");

  let cart = [];

  function renderMenu() {
    menuContainer.innerHTML = "";
    menuData.forEach(item => {
      const div = document.createElement("div");
      div.classList.add("menu-item");

      // buat option variant
      let variantOptions = item.variants.map(v => `<option value="${v}">${v}</option>`).join("");

      div.innerHTML = `
        <h3>${item.name}</h3>
        <p>Rp${item.price.toLocaleString()}</p>
        <select id="variant-${item.id}">
          ${variantOptions}
        </select>
        <button onclick="addToCart(${item.id})">Tambah ke Keranjang</button>
      `;
      menuContainer.appendChild(div);
    });
  }

  function addToCart(id) {
    const item = menuData.find(m => m.id === id);
    const selectVariant = document.getElementById(`variant-${id}`);
    const selectedVariant = selectVariant.value;

    // cari item di cart berdasarkan id + variant
    const cartItem = cart.find(c => c.id === id && c.variant === selectedVariant);
    if (cartItem) {
      cartItem.qty++;
    } else {
      cart.push({ ...item, qty: 1, variant: selectedVariant });
    }
    renderCart();
  }

  function removeFromCart(index) {
    cart.splice(index, 1);
    renderCart();
  }

  function getSelectedPayment() {
    const radios = document.getElementsByName('payment');
    for (const radio of radios) {
      if (radio.checked) return radio.value;
    }
    return "Cash"; // default
  }

  function renderCart() {
    cartList.innerHTML = "";
    if (cart.length === 0) {
      cartList.innerHTML = "<li>Keranjang kosong</li>";
      cartTotal.textContent = "";
      orderButtons.style.display = "none";
      paymentMethodDiv.style.display = "none";
      return;
    }

    let total = 0;
    cart.forEach((item, index) => {
      const li = document.createElement("li");
      li.innerHTML = `
        <button class="remove-btn" title="Hapus item" onclick="removeFromCart(${index})">&times;</button>
        <span>${item.name} (${item.variant}) x ${item.qty}</span>
        <span>Rp${(item.price * item.qty).toLocaleString()}</span>
      `;
      cartList.appendChild(li);
      total += item.price * item.qty;
    });

    cartTotal.textContent = `Total: Rp${total.toLocaleString()}`;
    orderButtons.style.display = "flex";
    paymentMethodDiv.style.display = "block";

    updateWhatsappLink();
  }

  function updateWhatsappLink() {
    let message = `Halo Gandhok Simbok! Saya mau pesan:\n`;
    cart.forEach(item => {
      message += `- ${item.name} (${item.variant}) x${item.qty}\n`;
    });

    const total = cart.reduce((sum, item) => sum + item.price * item.qty, 0);
    message += `Total: Rp${total.toLocaleString()}\n`;

    const payment = getSelectedPayment();
    message += `Metode Pembayaran: ${payment}\nTerima kasih!`;

    whatsappOrderLink.href = `https://wa.me/62${waNumber.slice(1)}?text=${encodeURIComponent(message)}`;
  }

  // Update link WA saat user ganti metode pembayaran
  document.getElementsByName('payment').forEach(radio => {
    radio.addEventListener('change', updateWhatsappLink);
  });

  renderMenu();
  renderCart();

  window.addToCart = addToCart;
  window.removeFromCart = removeFromCart;
</script>

</body>
</html>
