<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Johan's Lego Marketplace | Jual Beli Lego Premium</title>
  <!-- Google Fonts & Font Awesome Icons untuk tampilan menarik -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,600;14..32,700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(145deg, #f7f3e9 0%, #fff4e4 100%);
      color: #2d2a24;
      padding: 2rem 1.5rem;
    }

    /* container utama */
    .container {
      max-width: 1300px;
      margin: 0 auto;
    }

    /* header dengan sentuhan nama Johan */
    .hero {
      text-align: center;
      margin-bottom: 3rem;
      background: rgba(255, 248, 225, 0.7);
      backdrop-filter: blur(4px);
      border-radius: 3rem;
      padding: 1.8rem 2rem;
      box-shadow: 0 10px 25px rgba(0,0,0,0.05);
      border: 1px solid rgba(255,215,130,0.6);
    }

    .hero h1 {
      font-size: 2.7rem;
      font-weight: 800;
      background: linear-gradient(135deg, #c23b22, #e67e22, #f1c40f);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      letter-spacing: -0.5px;
      display: inline-flex;
      align-items: center;
      gap: 12px;
    }

    .hero h1 i {
      background: none;
      color: #e67e22;
      font-size: 2.4rem;
    }

    .hero .badge {
      margin-top: 12px;
      font-size: 1.1rem;
      background: #2d2a24;
      display: inline-block;
      padding: 0.4rem 1.2rem;
      border-radius: 40px;
      color: #ffdd99;
      font-weight: 500;
    }

    .badge i {
      margin-right: 8px;
    }

    /* filter dan tombol aksi */
    .toolbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 1rem;
      margin-bottom: 2.5rem;
      background: white;
      padding: 0.9rem 1.6rem;
      border-radius: 60px;
      box-shadow: 0 5px 12px rgba(0,0,0,0.05);
    }

    .filter-group {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
    }

    .filter-btn {
      background: #f0ede8;
      border: none;
      padding: 8px 20px;
      border-radius: 40px;
      font-weight: 600;
      font-family: 'Inter', sans-serif;
      cursor: pointer;
      transition: 0.2s;
      color: #4a3f32;
    }

    .filter-btn.active, .filter-btn:hover {
      background: #e67e22;
      color: white;
      box-shadow: 0 4px 10px rgba(230,126,34,0.3);
    }

    .cart-info {
      background: #fff2e0;
      padding: 6px 18px;
      border-radius: 40px;
      display: flex;
      align-items: center;
      gap: 12px;
      font-weight: 600;
    }

    .cart-info i {
      font-size: 1.3rem;
      color: #c23b22;
    }

    #cart-count {
      background: #e67e22;
      color: white;
      border-radius: 30px;
      padding: 0px 8px;
      font-size: 0.9rem;
      min-width: 26px;
      display: inline-block;
      text-align: center;
    }

    /* produk grid - semua bisa dipencet (klik card untuk melihat detail / tambah) */
    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 2rem;
      margin-bottom: 3rem;
    }

    /* kartu produk yang interaktif dan bisa diklik */
    .product-card {
      background: white;
      border-radius: 2rem;
      overflow: hidden;
      box-shadow: 0 15px 30px rgba(0,0,0,0.08);
      transition: all 0.25s ease;
      cursor: pointer;
      border: 1px solid rgba(0,0,0,0.05);
      position: relative;
    }

    .product-card:hover {
      transform: translateY(-8px);
      box-shadow: 0 25px 35px rgba(0,0,0,0.12);
      border-color: #f3c26b;
    }

    /* efek klik */
    .product-card:active {
      transform: scale(0.98);
    }

    .product-img {
      background: #fcf6e8;
      text-align: center;
      padding: 2rem 1rem;
      font-size: 4.5rem;
      border-bottom: 2px solid #ffebcd;
    }

    .product-info {
      padding: 1.3rem 1.2rem 1.2rem;
    }

    .product-title {
      font-size: 1.35rem;
      font-weight: 700;
      margin-bottom: 0.4rem;
      display: flex;
      justify-content: space-between;
    }

    .product-category {
      font-size: 0.75rem;
      text-transform: uppercase;
      background: #f0e5d5;
      display: inline-block;
      padding: 0.2rem 0.7rem;
      border-radius: 20px;
      font-weight: 600;
      color: #a86020;
      margin: 8px 0 6px;
    }

    .price {
      font-size: 1.6rem;
      font-weight: 800;
      color: #d35400;
      margin: 12px 0 8px;
    }

    .price small {
      font-size: 0.75rem;
      font-weight: 400;
      color: #7f6b5a;
    }

    .btn-add {
      width: 100%;
      background: #f5b041;
      border: none;
      padding: 12px 0;
      border-radius: 40px;
      font-weight: 700;
      font-size: 1rem;
      font-family: 'Inter', sans-serif;
      color: #2d2a24;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      cursor: pointer;
      transition: 0.2s;
      margin-top: 12px;
    }

    .btn-add:hover {
      background: #e67e22;
      color: white;
      transform: scale(1.02);
    }

    /* tombol beli spesial Johan (tampil keranjang + checkout) */
    .checkout-section {
      display: flex;
      justify-content: flex-end;
      margin-top: 1rem;
      margin-bottom: 2rem;
    }

    .btn-johan-beli {
      background: linear-gradient(95deg, #e67e22, #f39c12);
      border: none;
      padding: 14px 28px;
      font-size: 1.25rem;
      font-weight: bold;
      border-radius: 60px;
      color: white;
      font-family: 'Inter', sans-serif;
      display: inline-flex;
      align-items: center;
      gap: 14px;
      cursor: pointer;
      box-shadow: 0 8px 18px rgba(230,126,34,0.3);
      transition: all 0.2s;
    }

    .btn-johan-beli:hover {
      background: linear-gradient(95deg, #cf711f, #e67e22);
      transform: scale(1.02);
      box-shadow: 0 12px 22px rgba(230,126,34,0.4);
    }

    /* keranjang side panel style (modal sederhana) */
    .cart-modal {
      position: fixed;
      top: 0;
      right: -420px;
      width: 400px;
      max-width: 90vw;
      height: 100%;
      background: white;
      z-index: 1000;
      box-shadow: -5px 0 25px rgba(0,0,0,0.2);
      transition: right 0.3s ease;
      display: flex;
      flex-direction: column;
      border-radius: 24px 0 0 24px;
      font-family: 'Inter', sans-serif;
    }

    .cart-modal.open {
      right: 0;
    }

    .cart-header {
      padding: 1.5rem;
      border-bottom: 2px solid #f7e5cf;
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: #fef6e8;
      border-radius: 24px 0 0 0;
    }

    .cart-header h3 {
      font-size: 1.6rem;
      display: flex;
      gap: 8px;
    }

    .close-cart {
      background: none;
      border: none;
      font-size: 1.8rem;
      cursor: pointer;
    }

    .cart-items {
      flex: 1;
      overflow-y: auto;
      padding: 1rem;
    }

    .cart-item {
      display: flex;
      justify-content: space-between;
      background: #fefaf5;
      margin-bottom: 12px;
      padding: 12px;
      border-radius: 20px;
      align-items: center;
    }

    .cart-item-details h4 {
      font-size: 1rem;
    }

    .cart-item-price {
      font-weight: bold;
      color: #e67e22;
    }

    .cart-item-remove {
      color: #bc6f2c;
      background: none;
      border: none;
      font-size: 1.2rem;
      cursor: pointer;
    }

    .cart-total {
      padding: 1rem;
      border-top: 2px solid #f0e0ce;
      font-weight: bold;
      font-size: 1.3rem;
      display: flex;
      justify-content: space-between;
      background: white;
    }

    .cart-checkout {
      background: #e67e22;
      border: none;
      padding: 15px;
      width: calc(100% - 2rem);
      margin: 0 1rem 1.5rem;
      border-radius: 40px;
      font-weight: bold;
      font-size: 1.1rem;
      color: white;
      cursor: pointer;
    }

    .overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.4);
      z-index: 999;
      visibility: hidden;
      opacity: 0;
      transition: 0.2s;
    }

    .overlay.active {
      visibility: visible;
      opacity: 1;
    }

    footer {
      text-align: center;
      margin-top: 3rem;
      padding: 1.2rem;
      color: #7b6b58;
      border-top: 1px solid rgba(0,0,0,0.05);
    }

    @media (max-width: 680px) {
      .hero h1 { font-size: 1.8rem; }
      .toolbar { flex-direction: column; align-items: stretch; border-radius: 1.5rem; }
      .filter-group { justify-content: center; }
    }
  </style>
</head>
<body>

<div class="container">
  <div class="hero">
    <h1>
      <i class="fas fa-brick"></i> 
      Johan's Lego Bazaar
      <i class="fas fa-store"></i>
    </h1>
    <div class="badge">
      <i class="fas fa-crown"></i> Dikelola oleh Johan — Koleksi LEGO Original & Limited
    </div>
    <p style="margin-top: 14px; color: #5a4a38;">✨ Klik pada kartu produk atau tombol "➕ Tambah" untuk memasukkan ke keranjang ✨</p>
  </div>

  <div class="toolbar">
    <div class="filter-group">
      <button class="filter-btn active" data-filter="all">Semua Lego</button>
      <button class="filter-btn" data-filter="city">City</button>
      <button class="filter-btn" data-filter="starwars">Star Wars™</button>
      <button class="filter-btn" data-filter="technic">Technic</button>
      <button class="filter-btn" data-filter="classic">Classic</button>
    </div>
    <div class="cart-info">
      <i class="fas fa-shopping-cart"></i>
      <span>Keranjang Johan : </span>
      <span id="cart-count">0</span>
      <button id="openCartBtn" style="background:#e67e22; border:none; color:white; border-radius: 30px; padding:6px 14px; cursor:pointer; font-weight:bold;"><i class="fas fa-eye"></i> Lihat</button>
    </div>
  </div>

  <div class="products-grid" id="productsGrid"></div>

  <div class="checkout-section">
    <button class="btn-johan-beli" id="johanSpecialBeliBtn">
      <i class="fas fa-hand-holding-heart"></i> BELI SEKARANG (JOHAN'S PICK)
      <i class="fas fa-arrow-right"></i>
    </button>
  </div>
</div>

<!-- Overlay & Side Cart -->
<div class="overlay" id="overlay"></div>
<div class="cart-modal" id="cartModal">
  <div class="cart-header">
    <h3><i class="fas fa-brick"></i> Keranjang Johan</h3>
    <button class="close-cart" id="closeCartBtn">&times;</button>
  </div>
  <div class="cart-items" id="cartItemsList">
    <div style="text-align:center; padding:2rem; color:#aaa;">Keranjang masih kosong</div>
  </div>
  <div class="cart-total">
    <span>Total Belanja</span>
    <span id="cartTotalPrice">Rp 0</span>
  </div>
  <button class="cart-checkout" id="checkoutBtn">✅ Konfirmasi Beli (Johan)</button>
</div>

<footer>
  <i class="fas fa-heart" style="color:#e67e22;"></i> Johan's Lego – Setiap klik membawa kebahagiaan membangun
</footer>

<script>
  // Data produk LEGO (nama, kategori, harga, icon)
  const productsData = [
    { id: 1, name: "LEGO City Stasiun Pemadam", category: "city", price: 550000, icon: "🚒", desc: "Truk pemadam + helikopter" },
    { id: 2, name: "LEGO City Kereta Ekspres", category: "city", price: 890000, icon: "🚂", desc: "Set rel lengkap" },
    { id: 3, name: "Millennium Falcon", category: "starwars", price: 1499000, icon: "🛸", desc: "Starship ikonik" },
    { id: 4, name: "X-Wing Starfighter", category: "starwars", price: 699000, icon: "✈️", desc: "Pesawat tempur rebel" },
    { id: 5, name: "LEGO Technic Bugatti", category: "technic", price: 1850000, icon: "🏎️", desc: "Model mobil sport" },
    { id: 6, name: "Technic Crawler Crane", category: "technic", price: 1120000, icon: "🏗️", desc: "Crane remote" },
    { id: 7, name: "LEGO Classic Kotak Kreator", category: "classic", price: 350000, icon: "🧩", desc: "1100 pcs warna" },
    { id: 8, name: "LEGO Classic Bantal Jeruk", category: "classic", price: 285000, icon: "🍊", desc: "Set bangunan unik" },
    { id: 9, name: "LEGO City Pelabuhan", category: "city", price: 1275000, icon: "🚢", desc: "Kapal & dermaga" },
    { id: 10, name: "Darth Vader's Castle", category: "starwars", price: 990000, icon: "🏰", desc: "Set eksklusif" }
  ];

  let cart = []; // array { id, name, price, quantity, icon }

  // DOM elements
  const productsGrid = document.getElementById('productsGrid');
  const filterBtns = document.querySelectorAll('.filter-btn');
  const cartCountSpan = document.getElementById('cart-count');
  const cartModal = document.getElementById('cartModal');
  const overlay = document.getElementById('overlay');
  const openCartBtn = document.getElementById('openCartBtn');
  const closeCartBtn = document.getElementById('closeCartBtn');
  const cartItemsList = document.getElementById('cartItemsList');
  const cartTotalPriceSpan = document.getElementById('cartTotalPrice');
  const johanSpecialBeliBtn = document.getElementById('johanSpecialBeliBtn');
  const checkoutBtn = document.getElementById('checkoutBtn');

  let currentFilter = 'all';

  // fungsi render produk berdasarkan filter
  function renderProducts() {
    let filtered = productsData;
    if (currentFilter !== 'all') {
      filtered = productsData.filter(p => p.category === currentFilter);
    }
    if (productsGrid) {
      productsGrid.innerHTML = '';
      filtered.forEach(product => {
        const card = document.createElement('div');
        card.className = 'product-card';
        // seluruh card bisa di klik untuk menambah ke keranjang (memudahkan user)
        card.addEventListener('click', (e) => {
          // jangan trigger jika yang diklik adalah tombol add (agar tidak double)
          if (e.target.classList && e.target.classList.contains('btn-add')) {
            // sudah ditangani tombol sendiri, prevent card click?
            e.stopPropagation();
            addToCart(product);
          } else {
            addToCart(product);
          }
        });

        card.innerHTML = `
          <div class="product-img">
            <i class="fas fa-cube" style="font-size: 3rem; color:#e67e22;"></i> 
            <span style="font-size:2.5rem; margin-left:8px;">${product.icon}</span>
          </div>
          <div class="product-info">
            <div class="product-title">
              ${product.name}
            </div>
            <div class="product-category">${product.category.toUpperCase()}</div>
            <div class="price">Rp ${product.price.toLocaleString('id-ID')} <small></small></div>
            <button class="btn-add" data-id="${product.id}">
              <i class="fas fa-cart-plus"></i> Tambah ke Keranjang
            </button>
          </div>
        `;
        const addBtn = card.querySelector('.btn-add');
        addBtn.addEventListener('click', (e) => {
          e.stopPropagation();
          addToCart(product);
        });
        productsGrid.appendChild(card);
      });
    }
  }

  // add to cart
  function addToCart(product) {
    const existing = cart.find(item => item.id === product.id);
    if (existing) {
      existing.quantity += 1;
    } else {
      cart.push({
        id: product.id,
        name: product.name,
        price: product.price,
        quantity: 1,
        icon: product.icon
      });
    }
    updateCartUI();
    // animasi feedback (opsional)
    showToast(`👍 ${product.name} ditambahkan ke keranjang Johan!`);
  }

  function updateCartUI() {
    const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
    cartCountSpan.innerText = totalItems;
    // render cart list di modal
    if (cartItemsList) {
      if (cart.length === 0) {
        cartItemsList.innerHTML = '<div style="text-align:center; padding:2rem; color:#aaa;"><i class="fas fa-brick"></i> Keranjang kosong, ayo pilih lego favoritmu!</div>';
      } else {
        cartItemsList.innerHTML = '';
        cart.forEach(item => {
          const itemDiv = document.createElement('div');
          itemDiv.className = 'cart-item';
          itemDiv.innerHTML = `
            <div style="display:flex; gap:10px; align-items:center;">
              <span style="font-size:1.8rem;">${item.icon || '🧱'}</span>
              <div class="cart-item-details">
                <h4>${item.name}</h4>
                <small>Rp ${item.price.toLocaleString('id-ID')} x ${item.quantity}</small>
              </div>
            </div>
            <div style="display:flex; align-items:center; gap:12px;">
              <span class="cart-item-price">Rp ${(item.price * item.quantity).toLocaleString('id-ID')}</span>
              <button class="cart-item-remove" data-id="${item.id}"><i class="fas fa-trash-alt"></i></button>
            </div>
          `;
          const removeBtn = itemDiv.querySelector('.cart-item-remove');
          removeBtn.addEventListener('click', (e) => {
            e.stopPropagation();
            removeFromCart(item.id);
          });
          cartItemsList.appendChild(itemDiv);
        });
      }
      const totalPrice = cart.reduce((sum, i) => sum + (i.price * i.quantity), 0);
      cartTotalPriceSpan.innerText = `Rp ${totalPrice.toLocaleString('id-ID')}`;
    }
  }

  function removeFromCart(id) {
    const index = cart.findIndex(i => i.id === id);
    if (index !== -1) {
      if (cart[index].quantity > 1) {
        cart[index].quantity -= 1;
      } else {
        cart.splice(index, 1);
      }
      updateCartUI();
      showToast(`🗑️ Item dihapus dari keranjang`);
    }
  }

  function showToast(msg) {
    // simple toast notif 
    let toast = document.createElement('div');
    toast.innerText = msg;
    toast.style.position = 'fixed';
    toast.style.bottom = '20px';
    toast.style.left = '50%';
    toast.style.transform = 'translateX(-50%)';
    toast.style.backgroundColor = '#2d2a24';
    toast.style.color = '#ffdd99';
    toast.style.padding = '12px 24px';
    toast.style.borderRadius = '40px';
    toast.style.fontWeight = 'bold';
    toast.style.zIndex = '2000';
    toast.style.fontSize = '0.9rem';
    toast.style.boxShadow = '0 5px 15px rgba(0,0,0,0.2)';
    document.body.appendChild(toast);
    setTimeout(() => {
      toast.remove();
    }, 2000);
  }

  // filter logic
  filterBtns.forEach(btn => {
    btn.addEventListener('click', () => {
      filterBtns.forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      currentFilter = btn.getAttribute('data-filter');
      renderProducts();
    });
  });

  // cart modal controls
  function openCart() {
    cartModal.classList.add('open');
    overlay.classList.add('active');
    updateCartUI();
  }
  function closeCartModal() {
    cartModal.classList.remove('open');
    overlay.classList.remove('active');
  }
  openCartBtn.addEventListener('click', openCart);
  closeCartBtn.addEventListener('click', closeCartModal);
  overlay.addEventListener('click', closeCartModal);

  // TOMBOL BELI SPESIAL JOHAN (Menampilkan ringkasan keranjang & konfirmasi)
  johanSpecialBeliBtn.addEventListener('click', () => {
    if (cart.length === 0) {
      showToast("😢 Keranjang Johan masih kosong! Silakan pilih lego dulu ya.");
      return;
    }
    const totalItem = cart.reduce((sum,i)=> sum + i.quantity,0);
    const totalPrice = cart.reduce((sum,i)=> sum + (i.price * i.quantity),0);
    // menampilkan modal interaktif langsung checkout sambil menampilkan keranjang
    openCart(); // buka side cart supaya user lihat
    // tambahan sweet alert konfirmasi pakai confirm native karena ringan
    setTimeout(() => {
      const userConfirm = confirm(`✨ Halo Johan! ✨\nTotal ${totalItem} item lego siap dibeli dengan total Rp ${totalPrice.toLocaleString('id-ID')}\nKlik OK untuk menyelesaikan pembelian (simulasi sukses).`);
      if (userConfirm) {
        // proses checkout
        cart = [];
        updateCartUI();
        closeCartModal();
        showToast("🎉 Yeay! Pembelian berhasil. Terima kasih Johan telah berbelanja Lego 🧱❤️");
        renderProducts(); // refresh produk (tidak ada perubahan tapi rapi)
      }
    }, 80);
  });

  // tombol checkout di dalam cart
  checkoutBtn.addEventListener('click', () => {
    if (cart.length === 0) {
      showToast("Keranjang kosong, tidak bisa checkout.");
      return;
    }
    const totalPrice = cart.reduce((sum,i)=> sum + (i.price * i.quantity),0);
    const confirmCheck = confirm(`🧾 Checkout sebagai Johan\nTotal belanja: Rp ${totalPrice.toLocaleString('id-ID')}\nLanjutkan pembelian?`);
    if (confirmCheck) {
      cart = [];
      updateCartUI();
      closeCartModal();
      showToast("✅ Transaksi sukses! LEGO akan segera dikirim. Selamat membangun, Johan!");
      renderProducts();
    }
  });

  // initial render
  renderProducts();
  updateCartUI();

  // tambahan efek klik pada semua produk sudah di handle card click
  // membuat website fully interactive + semua tombol berfungsi + Nama Johan terlihat prominent
</script>
</body>
</html>
