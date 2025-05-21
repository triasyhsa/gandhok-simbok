<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Gandhok Simbok</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0; padding: 0;
      background-color: #fff0f0;
      color: #330000;
    }
    header {
      background-color: #cc0000;
      color: white;
      padding: 1em;
      text-align: center;
    }
    nav {
      background-color: #990000;
      padding: 0.5em;
      text-align: center;
    }
    nav a {
      color: white;
      margin: 0 1em;
      text-decoration: none;
      font-weight: bold;
    }
    .produk {
      display: grid;
      grid-template-columns: repeat(auto-fit,minmax(250px,1fr));
      gap: 1em;
      padding: 1em;
    }
    .card {
      border: 1px solid #ddd;
      border-radius: 10px;
      padding: 1em;
      background-color: #fff8f8;
      box-shadow: 1px 1px 5px #ccc;
    }
    .card h3 {
      margin-top: 0;
    }
    .btn {
      background-color: #cc0000;
      color: white;
      border: none;
      padding: 0.5em 1em;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 0.5em;
    }
    .keranjang {
      position: fixed;
      top: 70px;
      right: 10px;
      width: 320px;
      max-height: 80vh;
      overflow-y: auto;
      background: #ffefef;
      border: 2px solid #cc0000;
      border-radius: 10px;
      padding: 1em;
      box-shadow: 2px 2px 10px #aa0000;
      z-index: 100;
    }
    .keranjang h2 {
      margin-top: 0;
      text-align: center;
      color: #cc0000;
    }
    .item-keranjang {
      display: flex;
      justify-content: space-between;
      padding: 0.3em 0;
      border-bottom: 1px solid #cc0000;
    }
    .item-keranjang:last-child {
      border-bottom: none;
    }
    .hapus-btn {
      background-color: #990000;
      border: none;
      color: white;
      border-radius: 3px;
      cursor: pointer;
      padding: 0 0.4em;
    }
    .footer {
      text-align: center;
      background-color: #330000;
      color: white;
      padding: 1em;
      margin-top: 2em;
    }
    .pembayaran {
      margin-top: 1em;
      text-align: center;
    }
  </style>
</head>
<body>
  <header>
    <h1>Gandhok Simbok</h1>
    <p>Rasanya Nampol, Pedasnya Nagih!!</p>
  </header>

  <nav>
    <a href="#kremesan">Kremesan</a>
    <a href="#krispi">Krispi Celup</a>
    <a href="#mie">Mie Jebew</a>
    <a href="https://gofood.link/a/PQXft4o" target="_blank">Pesan via GoFood</a>
    <a href="https://wa.me/628371253839" target="_blank">Chat via WhatsApp</a>
  </nav>

  <section class="produk" id="kremesan">
    <h2>Kremesan</h2>
    <div class="card">
      <h3>Sambal Original</h3>
      <button class="btn" onclick="tambahKeranjang('Kremesan Sambal Original')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Sambal Terasi</h3>
      <button class="btn" onclick="tambahKeranjang('Kremesan Sambal Terasi')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Sambal Bawang</h3>
      <button class="btn" onclick="tambahKeranjang('Kremesan Sambal Bawang')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Sambal Campur</h3>
      <button class="btn" onclick="tambahKeranjang('Kremesan Sambal Campur')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Sambal Kacang</h3>
      <button class="btn" onclick="tambahKeranjang('Kremesan Sambal Kacang')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Sambal Tomat</h3>
      <button class="btn" onclick="tambahKeranjang('Kremesan Sambal Tomat')">Tambah ke Keranjang</button>
    </div>
  </section>

  <section class="produk" id="krispi">
    <h2>Krispi Celup</h2>
    <div class="card">
      <h3>Saos Judes</h3>
      <button class="btn" onclick="tambahKeranjang('Krispi Celup Saos Judes')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Saus Keju</h3>
      <button class="btn" onclick="tambahKeranjang('Krispi Celup Saus Keju')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Saus Kari</h3>
      <button class="btn" onclick="tambahKeranjang('Krispi Celup Saus Kari')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Saus Lada Hitam</h3>
      <button class="btn" onclick="tambahKeranjang('Krispi Celup Saus Lada Hitam')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Saus Original</h3>
      <button class="btn" onclick="tambahKeranjang('Krispi Celup Saus Original')">Tambah ke Keranjang</button>
    </div>
  </section>

  <section class="produk" id="mie">
    <h2>Mie Jebew</h2>
    <div class="card">
      <h3>Mie Original</h3>
      <button class="btn" onclick="tambahKeranjang('Mie Jebew Mie Original')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Mie Ayam Bawang</h3>
      <button class="btn" onclick="tambahKeranjang('Mie Jebew Mie Ayam Bawang')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Mie Lada Hitam</h3>
      <button class="btn" onclick="tambahKeranjang('Mie Jebew Mie Lada Hitam')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Mie Rendang</h3>
      <button class="btn" onclick="tambahKeranjang('Mie Jebew Mie Rendang')">Tambah ke Keranjang</button>
    </div>
    <div class="card">
      <h3>Mie Kari</h3>
      <button class="btn" onclick="tambahKeranjang('Mie Jebew Mie Kari')">Tambah ke Keranjang</button>
    </div>
  </section>

  <aside class="keranjang" id="keranjang">
    <h2>Keranjang Pesanan</h2>
    <div id="list-keranjang"></div>

    <div class="pembayaran">
      <label><input type="radio" name="pembayaran" value="cash" checked> Bayar Cash</label><br />
      <label><input type="radio" name="pembayaran" value="transfer"> Transfer</label>
    </div>

    <button class="btn" onclick="checkout()">Checkout</button>
  </aside>

  <footer class="footer">
    <p>&copy; 2025 Gandhok Simbok. Semua hak dilindungi.</p>
  </footer>

  <script>
    const keranjang = [];

    function tambahKeranjang(item) {
      keranjang.push(item);
      updateKeranjang();
    }

    function hapusDariKeranjang(index) {
      keranjang.splice(index, 1);
      updateKeranjang();
    }

    function updateKeranjang() {
      const list = document.getElementById('list-keranjang');
      list.innerHTML = '';
      if (keranjang.length === 0) {
        list.innerHTML = '<p>Keranjang kosong.</p>';
        return;
      }
      keranjang.forEach((item, i) => {
        const div = document.createElement('div');
        div.className = 'item-keranjang';
        div.innerHTML = `
          <span>${item}</span>
          <button class="hapus-btn" onclick="hapusDariKeranjang(${i})">X</button>
        `;
        list.appendChild(div);
      });
    }

    function checkout() {
      if (keranjang.length === 0) {
        alert('Keranjang masih kosong!');
        return;
      }
      const metodePembayaran = document.querySelector('input[name="pembayaran"]:checked').value;
      let pesan = 'Pesanan:\n';
      keranjang.forEach((item, i) => {
        pesan += `- ${item}\n`;
      });
      pesan += `Metode pembayaran: ${metodePembayaran === 'cash' ? 'Cash' : 'Transfer'}`;
      alert(pesan);
      // Di sini bisa ditambahkan kode untuk submit ke server / integrasi WhatsApp / GoFood
      // Setelah checkout, keranjang dikosongkan
      keranjang.length = 0;
      updateKeranjang();
    }

    updateKeranjang();
  </script>
</body>
</html>
