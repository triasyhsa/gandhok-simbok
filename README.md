<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Gandhok Simbok - Warung Makan</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');

  body {
    font-family: 'Poppins', sans-serif;
    background: #fff;
    color: #7f1d1d;
    margin: 0;
    padding: 20px;
  }
  header {
    text-align: center;
    background-color: #c62828;
    color: #fff;
    padding: 20px 0;
    font-size: 2.5em;
    font-weight: 600;
    letter-spacing: 2px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(198, 40, 40, 0.5);
    user-select: none;
  }
  #slogan {
    text-align: center;
    font-size: 1.4em;
    margin-top: 15px;
    color: #b71c1c;
    font-weight: 600;
    letter-spacing: 1px;
  }
  #slogan span {
    color: #c62828;
    font-weight: 700;
    font-style: italic;
  }
  .menu {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
    margin: 30px 0;
  }
  .menu-item {
    background: #fff0f0;
    border-radius: 12px;
    width: 260px;
    padding: 20px;
    box-shadow: 0 6px 12px rgba(198, 40, 40, 0.2);
    text-align: center;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    cursor: pointer;
  }
  .menu-item:hover {
    transform: translateY(-5px);
    box-shadow: 0 12px 24px rgba(198, 40, 40, 0.35);
  }
  .menu-item h3 {
    margin: 0 0 12px;
    font-weight: 600;
    font-size: 1.5em;
    color: #a91a1a;
  }
  .menu-item p {
    font-weight: 600;
    font-size: 1.15em;
    margin: 0 0 12px;
    color: #7f1d1d;
  }
  select, button, textarea {
    width: 100%;
    padding: 12px;
    border-radius: 8px;
    border: 2px solid #c62828;
    font-size: 1em;
    font-weight: 600;
    transition: background-color 0.3s ease, color 0.3s ease;
  }
  select {
    margin-bottom: 12px;
    cursor: pointer;
    background: #fff0f0;
    color: #7f1d1d;
  }
  select:hover, select:focus,
  textarea:hover, textarea:focus {
    background: #fceaea;
    outline: none;
  }
  button {
    background-color: #c62828;
    color: white;
    border: none;
    cursor: pointer;
  }
  button:hover {
    background-color: #8e1b1b;
  }
  #cart {
    background: #fff0f0;
    border-radius: 14px;
    padding: 25px;
    max-width: 520px;
    margin: 0 auto 50px auto;
    box-shadow: 0 6px 15px rgba(198, 40, 40, 0.3);
  }
  #cart h2 {
    margin-top: 0;
    text-align: center;
    font-weight: 700;
    color: #a91a1a;
    letter-spacing: 1.5px;
  }
  #cart-list {
    list-style: none;
    padding: 0;
    margin: 20px 0 15px 0;
    max-height: 240px;
    overflow-y: auto;
  }
  #cart-list li {
    display: flex;
    justify-content: space-between;
    padding: 10px 5px;
    border-bottom: 1px solid #e6b8b8;
    align-items: center;
    font-weight: 600;
    color: #6b0f0f;
  }
  #cart-list li span {
    flex-grow: 1;
    padding-left: 10px;
    text-align: left;
  }
  #cart-total {
    font-weight: 700;
    text-align: right;
    font-size: 1.2em;
    color: #7f1d1d;
  }
  #payment-method {
    margin-top: 20px;
    text-align: center;
    font-weight: 600;
    color: #7f1d1d;
  }
  #payment-method label {
    margin: 0 20px;
    cursor: pointer;
  }
  #order-buttons {
    display: flex;
    justify-content: space-around;
    margin-top: 30px;
  }
  #order-buttons a, #order-buttons button {
    background: #c62828;
    color: white;
    text-decoration: none;
    padding: 14px 28px;
    border-radius: 10px;
    font-weight: 700;
    font-size: 1.1em;
    cursor: pointer;
    box-shadow: 0 6px 12px rgba(198, 40, 40, 0.5);
    transition: background-color 0.3s ease, box-shadow 0.3s ease;
  }
  #order-buttons a:hover, #order-buttons button:hover {
    background-color: #8e1b1b;
    box-shadow: 0 8px 16px rgba(142, 27, 27, 0.7);
  }
  button.remove-btn {
    background: none;
    border: none;
    color: #c62828;
    font-size: 22px;
    cursor: pointer;
    transition: color 0.3s ease;
  }
  button.remove-btn:hover {
    color: #8e1b1b;
  }
  /* Scrollbar untuk keranjang */
  #cart-list::-webkit-scrollbar {
    width: 8px;
  }
  #cart-list::-webkit-scrollbar-thumb {
    background-color: #c62828;
    border-radius: 10px;
  }
  /* Catatan */
  #note-section {
    max-width: 520px;
    margin: 0 auto 40px auto;
    background: #fff0f0;
    padding: 20px;
    border-radius: 14px;
    box-shadow: 0 6px 15px rgba(198, 40, 40, 0.3);
  }
  #note-section label {
    font-weight: 600;
    color: #7f1d1d;
    display: block;
    margin-bottom: 10px;
  }
  #note-section textarea {
    font-weight: 400;
    resize: vertical;
    min-height: 80px;
  }
</style>
</head>
<body>

<header>Gandhok Simbok</header>
<div id="slogan">
  <p>Rasanya Nampol, <span>Pedesnya Nagih!</span></p>
</div>

<section class="menu" id="menu">
  <!-- Menu items akan dimasukkan JS -->
</section>

<section id="note-section">
  <label for="order-note">Catatan untuk Pesanan (misal: level pedas, tambahan, dll):</label>
  <textarea id="order-note" placeholder="Tulis catatan di sini..."></textarea>
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
    <a href="#" id="whatsapp-order" target="_blank" rel="noopener noreferrer">Pesan via WhatsApp</a>
    <a href="https://gofood.link/a/PQXft4o" target="_blank" rel="noopener noreferrer">Order via GoFood</a>
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
      price: 13000,
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

  const waNumber = "+62857-2575-0069";

  const menuContainer = document.getElementById("menu");
  const cartList = document.getElementById("cart-list");
  const cartTotal = document.getElementById("cart-total");
  const orderButtons = document.getElementById("order-buttons");
  const whatsappOrderLink = document.getElementById("whatsapp-order");
  const paymentMethodDiv = document.getElementById("payment-method");
  const orderNote = document.getElementById("order-note");

  let cart = [];

  function renderMenu() {
    menuContainer.innerHTML = "";
    menuData.forEach(item => {
      const div = document.createElement("div");
      div.classList.add("menu-item");

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
    const variantSelect = document.getElementById(`variant-${id}`);
    const variant = variantSelect.value;

    // Check if item with same variant already in cart
    const cartItemIndex = cart.findIndex(c => c.id === id && c.variant === variant);
    if (cartItemIndex > -1) {
      cart[cartItemIndex].qty += 1;
    } else {
      cart.push({ id: id, name: item.name, variant: variant, price: item.price, qty: 1 });
    }
    renderCart();
  }

  function removeFromCart(index) {
    cart.splice(index, 1);
    renderCart();
  }

  function renderCart() {
    if (cart.length === 0) {
      cartList.innerHTML = "<li>Keranjang kosong</li>";
      cartTotal.textContent = "";
      orderButtons.style.display = "none";
      paymentMethodDiv.style.display = "none";
      return;
    }

    cartList.innerHTML = "";
    let total = 0;
    cart.forEach((item, i) => {
      total += item.price * item.qty;
      const li = document.createElement("li");
      li.innerHTML = `
        <button class="remove-btn" title="Hapus item" onclick="removeFromCart(${i})">&times;</button>
        <span>${item.name} (${item.variant}) x ${item.qty}</span>
        <strong>Rp${(item.price * item.qty).toLocaleString()}</strong>
      `;
      cartList.appendChild(li);
    });
    cartTotal.textContent = "Total: Rp" + total.toLocaleString();

    orderButtons.style.display = "flex";
    paymentMethodDiv.style.display = "block";

    updateWhatsappLink();
  }

  function updateWhatsappLink() {
    if (cart.length === 0) return;

    const paymentRadio = document.querySelector('input[name="payment"]:checked');
    const paymentMethod = paymentRadio ? paymentRadio.value : "Cash";

    let message = `Halo Gandhok Simbok,%0ASaya ingin pesan:%0A`;
    cart.forEach(item => {
      message += `- ${item.name} (${item.variant}) x ${item.qty} = Rp${(item.price * item.qty).toLocaleString()}%0A`;
    });
    message += `Total: Rp${cart.reduce((a, c) => a + c.price * c.qty, 0).toLocaleString()}%0A`;
    if(orderNote.value.trim() !== ""){
      message += `Catatan: ${encodeURIComponent(orderNote.value.trim())}%0A`;
    }
    message += `Metode Pembayaran: ${paymentMethod}%0A%0ATerima kasih!`;

    whatsappOrderLink.href = `https://wa.me/${waNumber}?text=${message}`;
  }

  // Update link tiap kali note atau pembayaran diubah
  orderNote.addEventListener("input", updateWhatsappLink);
  paymentMethodDiv.addEventListener("change", updateWhatsappLink);

  renderMenu();
  renderCart();

  // Buat fungsi removeFromCart accessible di global scope
  window.removeFromCart = removeFromCart;
  window.addToCart = addToCart;
</script>

</body>
</html>
