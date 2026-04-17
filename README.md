<!DOCTYPE html>
<html lang="cs">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ismobile servis – Profeionální a spolehlivé služby </title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --blue-deep: #0a1628;
    --blue-mid: #0f2850;
    --blue-bright: #1e5fd4;
    --blue-glow: #3b82f6;
    --blue-light: #93c5fd;
    --accent: #00d4ff;
    --accent2: #f59e0b;
    --white: #f8faff;
    --gray: #94a3b8;
    --card-bg: rgba(255,255,255,0.04);
    --border: rgba(59,130,246,0.2);
  }
  * { margin:0; padding:0; box-sizing:border-box; }
  html { scroll-behavior: smooth; }
  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--blue-deep);
    color: var(--white);
    overflow-x: hidden;
  }

  /* ── NAVBAR ── */
  nav {
    position: fixed; top:0; width:100%; z-index:100;
    background: rgba(10,22,40,0.85);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
    padding: 0 5%;
    display: flex; align-items:center; justify-content:space-between;
    height: 68px;
  }
  .logo { font-family:'Syne',sans-serif; font-weight:800; font-size:1.4rem; }
  .logo span { color: var(--accent); }
  .nav-links { display:flex; gap:2rem; list-style:none; }
  .nav-links a {
    color: var(--gray); text-decoration:none; font-size:.9rem; font-weight:500;
    transition: color .2s;
  }
  .nav-links a:hover { color: var(--accent); }
  .nav-cta {
    background: var(--blue-bright); color:#fff;
    border:none; padding:.55rem 1.3rem; border-radius:8px;
    font-family:'DM Sans',sans-serif; font-weight:500; font-size:.9rem;
    cursor:pointer; transition: background .2s, transform .1s;
  }
  .nav-cta:hover { background: var(--blue-glow); transform:translateY(-1px); }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction:column; align-items:center; justify-content:center;
    text-align:center;
    padding: 100px 5% 60px;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content:'';
    position:absolute; inset:0;
    background: radial-gradient(ellipse 80% 60% at 50% 30%, rgba(30,95,212,0.35) 0%, transparent 70%);
    pointer-events:none;
  }
  .hero-badge {
    display:inline-flex; align-items:center; gap:.5rem;
    background: rgba(0,212,255,0.1); border:1px solid rgba(0,212,255,0.3);
    border-radius:100px; padding:.35rem 1rem; font-size:.8rem;
    color: var(--accent); margin-bottom:1.5rem;
    animation: fadeUp .6s ease both;
  }
  .hero h1 {
    font-family:'Syne',sans-serif; font-weight:800;
    font-size: clamp(2.4rem, 6vw, 4.5rem);
    line-height:1.1; margin-bottom:1.2rem;
    animation: fadeUp .7s .1s ease both;
  }
  .hero h1 em { color: var(--accent); font-style:normal; }
  .hero p {
    font-size:1.1rem; color:var(--gray); max-width:540px;
    line-height:1.7; margin-bottom:2.5rem;
    animation: fadeUp .7s .2s ease both;
  }
  .hero-btns {
    display:flex; gap:1rem; flex-wrap:wrap; justify-content:center;
    animation: fadeUp .7s .3s ease both;
  }
  .btn-primary {
    background: linear-gradient(135deg, var(--blue-bright), var(--blue-glow));
    color:#fff; border:none; padding:.85rem 2rem;
    border-radius:10px; font-size:1rem; font-weight:600;
    cursor:pointer; transition: transform .15s, box-shadow .2s;
    box-shadow: 0 4px 24px rgba(59,130,246,.35);
  }
  .btn-primary:hover { transform:translateY(-2px); box-shadow:0 8px 32px rgba(59,130,246,.5); }
  .btn-outline {
    background:transparent; color:var(--white);
    border:1.5px solid var(--border); padding:.85rem 2rem;
    border-radius:10px; font-size:1rem; font-weight:500;
    cursor:pointer; transition: border-color .2s, background .2s;
  }
  .btn-outline:hover { border-color: var(--blue-glow); background:rgba(59,130,246,.08); }

  .hero-stats {
    display:flex; gap:3rem; margin-top:4rem; flex-wrap:wrap; justify-content:center;
    animation: fadeUp .7s .4s ease both;
  }
  .stat { text-align:center; }
  .stat-num { font-family:'Syne',sans-serif; font-weight:800; font-size:2rem; color:var(--accent); }
  .stat-label { font-size:.8rem; color:var(--gray); margin-top:.2rem; }

  /* floating phone illustration */
  .phone-float {
    position:absolute; right:6%; top:50%; transform:translateY(-50%);
    width:220px; opacity:.15;
    animation: float 4s ease-in-out infinite;
    display:none;
  }
  @media(min-width:900px){ .phone-float { display:block; } }

  /* ── SERVICES ── */
  section { padding:80px 5%; }
  .section-label {
    font-size:.8rem; font-weight:600; letter-spacing:.12em;
    color:var(--accent); text-transform:uppercase; margin-bottom:.8rem;
  }
  .section-title {
    font-family:'Syne',sans-serif; font-weight:800;
    font-size: clamp(1.8rem,4vw,2.8rem); margin-bottom:1rem;
  }
  .section-sub { color:var(--gray); max-width:480px; line-height:1.7; margin-bottom:3rem; }
  .services-grid {
    display:grid; grid-template-columns: repeat(auto-fit, minmax(240px,1fr)); gap:1.5rem;
  }
  .service-card {
    background: var(--card-bg);
    border:1px solid var(--border);
    border-radius:16px; padding:1.8rem;
    transition: transform .2s, border-color .2s, box-shadow .2s;
    position:relative; overflow:hidden;
  }
  .service-card::before {
    content:''; position:absolute; inset:0;
    background: linear-gradient(135deg, rgba(59,130,246,.08), transparent);
    opacity:0; transition: opacity .3s;
  }
  .service-card:hover { transform:translateY(-4px); border-color: var(--blue-glow); box-shadow:0 12px 40px rgba(59,130,246,.15); }
  .service-card:hover::before { opacity:1; }
  .service-icon { font-size:2.2rem; margin-bottom:1rem; }
  .service-card h3 { font-family:'Syne',sans-serif; font-weight:700; font-size:1.1rem; margin-bottom:.5rem; }
  .service-card p { color:var(--gray); font-size:.88rem; line-height:1.6; }
  .service-price {
    display:inline-block; margin-top:1rem;
    background: rgba(0,212,255,.1); border:1px solid rgba(0,212,255,.25);
    border-radius:6px; padding:.25rem .75rem;
    font-size:.82rem; color:var(--accent); font-weight:600;
  }

  /* ── SHOP ── */
  .shop-bg { background: var(--blue-mid); }
  .products-grid {
    display:grid; grid-template-columns: repeat(auto-fit,minmax(200px,1fr)); gap:1.5rem;
  }
  .product-card {
    background: rgba(255,255,255,.05); border:1px solid var(--border);
    border-radius:14px; overflow:hidden;
    transition: transform .2s, box-shadow .2s;
  }
  .product-card:hover { transform:translateY(-4px); box-shadow:0 12px 40px rgba(0,0,0,.3); }
  .product-img {
    width:100%; height:160px;
    display:flex; align-items:center; justify-content:center;
    font-size:4rem;
    background: linear-gradient(135deg, rgba(30,95,212,.3), rgba(0,212,255,.1));
  }
  .product-info { padding:1.2rem; }
  .product-info h4 { font-family:'Syne',sans-serif; font-weight:700; font-size:.95rem; margin-bottom:.3rem; }
  .product-info .price { color:var(--accent2); font-weight:700; font-size:1.1rem; }
  .product-info .old-price { color:var(--gray); text-decoration:line-through; font-size:.8rem; margin-left:.4rem; }
  .add-cart {
    width:100%; margin-top:.8rem; padding:.6rem;
    background: var(--blue-bright); color:#fff; border:none;
    border-radius:8px; font-weight:600; font-size:.85rem;
    cursor:pointer; transition: background .2s;
  }
  .add-cart:hover { background: var(--blue-glow); }

  /* cart badge */
  .cart-btn {
    position:fixed; bottom:2rem; right:2rem; z-index:200;
    background: var(--blue-bright); color:#fff;
    width:56px; height:56px; border-radius:50%; border:none;
    font-size:1.5rem; cursor:pointer;
    box-shadow:0 4px 20px rgba(30,95,212,.5);
    display:flex; align-items:center; justify-content:center;
    transition: transform .2s;
  }
  .cart-btn:hover { transform:scale(1.1); }
  .cart-count {
    position:absolute; top:-4px; right:-4px;
    background:var(--accent2); color:#000;
    width:20px; height:20px; border-radius:50%;
    font-size:.7rem; font-weight:800;
    display:flex; align-items:center; justify-content:center;
  }

  /* ── BOOKING ── */
  .booking-wrap {
    display:grid; grid-template-columns:1fr 1fr; gap:4rem; align-items:start;
  }
  @media(max-width:768px){ .booking-wrap { grid-template-columns:1fr; gap:2rem; } }
  .booking-form {
    background: var(--card-bg); border:1px solid var(--border);
    border-radius:20px; padding:2rem;
  }
  .form-row { display:grid; grid-template-columns:1fr 1fr; gap:1rem; margin-bottom:1rem; }
  @media(max-width:500px){ .form-row { grid-template-columns:1fr; } }
  .form-group { margin-bottom:1rem; }
  .form-group label { display:block; font-size:.82rem; color:var(--gray); margin-bottom:.4rem; font-weight:500; }
  .form-group input, .form-group select, .form-group textarea {
    width:100%; background:rgba(255,255,255,.06);
    border:1px solid var(--border); border-radius:8px;
    color:var(--white); padding:.7rem 1rem; font-size:.9rem;
    font-family:'DM Sans',sans-serif;
    transition: border-color .2s;
  }
  .form-group input:focus, .form-group select:focus, .form-group textarea:focus {
    outline:none; border-color: var(--blue-glow);
    background:rgba(59,130,246,.06);
  }
  .form-group select option { background: var(--blue-deep); }
  .form-group textarea { resize:vertical; min-height:80px; }
  .submit-btn {
    width:100%; padding:.9rem; background:linear-gradient(135deg,var(--blue-bright),var(--blue-glow));
    color:#fff; border:none; border-radius:10px;
    font-size:1rem; font-weight:700; cursor:pointer;
    transition: transform .15s, box-shadow .2s;
    box-shadow:0 4px 20px rgba(59,130,246,.3);
  }
  .submit-btn:hover { transform:translateY(-2px); box-shadow:0 8px 28px rgba(59,130,246,.5); }
  .booking-info h3 { font-family:'Syne',sans-serif; font-weight:700; font-size:1.4rem; margin-bottom:1.5rem; }
  .info-item { display:flex; gap:1rem; align-items:flex-start; margin-bottom:1.5rem; }
  .info-icon { font-size:1.4rem; flex-shrink:0; margin-top:.1rem; }
  .info-item h4 { font-weight:600; font-size:.95rem; margin-bottom:.2rem; }
  .info-item p { color:var(--gray); font-size:.85rem; line-height:1.5; }
  .time-slots { display:flex; flex-wrap:wrap; gap:.5rem; margin-top:.8rem; }
  .slot {
    background:rgba(59,130,246,.1); border:1px solid var(--border);
    border-radius:6px; padding:.3rem .75rem; font-size:.8rem; cursor:pointer;
    transition: all .15s;
  }
  .slot:hover, .slot.active { background:var(--blue-bright); border-color:var(--blue-bright); }

  /* ── REVIEWS ── */
  .reviews-bg { background: var(--blue-mid); }
  .reviews-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(260px,1fr)); gap:1.5rem; }
  .review-card {
    background:var(--card-bg); border:1px solid var(--border);
    border-radius:16px; padding:1.5rem;
  }
  .stars { color:#f59e0b; font-size:1rem; margin-bottom:.8rem; }
  .review-text { color:var(--gray); font-size:.88rem; line-height:1.65; margin-bottom:1rem; font-style:italic; }
  .reviewer { display:flex; align-items:center; gap:.8rem; }
  .avatar {
    width:36px; height:36px; border-radius:50%;
    background:linear-gradient(135deg,var(--blue-bright),var(--accent));
    display:flex; align-items:center; justify-content:center;
    font-weight:700; font-size:.85rem;
  }
  .reviewer-name { font-weight:600; font-size:.88rem; }
  .reviewer-date { font-size:.75rem; color:var(--gray); }

  /* ── CONTACT ── */
  .contact-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(220px,1fr)); gap:1.5rem; }
  .contact-card {
    background:var(--card-bg); border:1px solid var(--border);
    border-radius:16px; padding:1.8rem; text-align:center;
  }
  .contact-card .c-icon { font-size:2rem; margin-bottom:.8rem; }
  .contact-card h4 { font-family:'Syne',sans-serif; font-weight:700; margin-bottom:.4rem; }
  .contact-card p { color:var(--gray); font-size:.88rem; }
  .contact-card a { color:var(--accent); text-decoration:none; }

  /* ── FOOTER ── */
  footer {
    background: rgba(5,12,25,1); border-top:1px solid var(--border);
    padding:2rem 5%; text-align:center;
    color:var(--gray); font-size:.85rem;
  }
  footer strong { color:var(--accent); }

  /* ── CART MODAL ── */
  .modal-overlay {
    position:fixed; inset:0; background:rgba(0,0,0,.6);
    z-index:300; display:none; align-items:center; justify-content:center;
  }
  .modal-overlay.open { display:flex; }
  .modal {
    background:var(--blue-mid); border:1px solid var(--border);
    border-radius:20px; padding:2rem; width:90%; max-width:440px;
    max-height:80vh; overflow-y:auto;
  }
  .modal h3 { font-family:'Syne',sans-serif; font-weight:800; margin-bottom:1.5rem; }
  .cart-item { display:flex; justify-content:space-between; align-items:center; padding:.8rem 0; border-bottom:1px solid var(--border); }
  .cart-item-name { font-size:.9rem; }
  .cart-item-price { color:var(--accent2); font-weight:700; }
  .remove-item { background:none; border:none; color:var(--gray); cursor:pointer; font-size:1rem; }
  .cart-total { margin-top:1rem; text-align:right; font-family:'Syne',sans-serif; font-size:1.1rem; font-weight:700; }
  .checkout-btn {
    width:100%; margin-top:1rem; padding:.8rem;
    background:var(--accent2); color:#000;
    border:none; border-radius:10px; font-weight:700; font-size:1rem; cursor:pointer;
  }
  .close-modal { float:right; background:none; border:none; color:var(--gray); font-size:1.3rem; cursor:pointer; }

  /* ── TOAST ── */
  .toast {
    position:fixed; bottom:6rem; right:2rem; z-index:400;
    background:var(--blue-bright); color:#fff; border-radius:10px;
    padding:.7rem 1.2rem; font-size:.88rem; font-weight:600;
    transform:translateY(20px); opacity:0; pointer-events:none;
    transition: all .3s;
  }
  .toast.show { transform:translateY(0); opacity:1; }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity:0; transform:translateY(24px); }
    to   { opacity:1; transform:translateY(0); }
  }
  @keyframes float {
    0%,100% { transform:translateY(-50%) translateX(0) rotate(-5deg); }
    50%      { transform:translateY(-53%) translateX(6px) rotate(2deg); }
  }

  /* Confirm message */
  .confirm-msg {
    display:none; background:rgba(0,212,255,.1);
    border:1px solid rgba(0,212,255,.3); border-radius:10px;
    padding:1rem; text-align:center; color:var(--accent);
    font-weight:600; margin-top:1rem;
  }
</style>
</head>
<body>

<!-- NAVBAR -->
<nav>
  <div class="logo">TechFix<span>Pro</span></div>
  <ul class="nav-links">
    <li><a href="#services">Služba</a></li>
    <li><a href="#shop</a></li>
    <li><a href="#booking">Đặt lịch</a></li>
    <li><a href="#contact">Liên hệ</a></li>
  </ul>
  <button class="nav-cta" onclick="document.getElementById('booking').scrollIntoView({behavior:'smooth'})">Đặt lịch ngay</button>
</nav>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-badge">⚡ Sửa chữa trong 30–60 phút</div>
  <h1>Thay màn hình<br><em>chuyên nghiệp</em><br>nhanh & uy tín</h1>
  <p>Dịch vụ thay màn hình điện thoại, máy tính bảng chất lượng cao. Linh kiện chính hãng, bảo hành 6 tháng, giá cả minh bạch.</p>
  <div class="hero-btns">
    <button class="btn-primary" onclick="document.getElementById('booking').scrollIntoView({behavior:'smooth'})">📅 Đặt lịch ngay</button>
    <button class="btn-outline" onclick="document.getElementById('services').scrollIntoView({behavior:'smooth'})">Xem dịch vụ →</button>
  </div>
  <div class="hero-stats">
    <div class="stat"><div class="stat-num">2000+</div><div class="stat-label">Khách hài lòng</div></div>
    <div class="stat"><div class="stat-num">6 tháng</div><div class="stat-label">Bảo hành</div></div>
    <div class="stat"><div class="stat-num">60'</div><div class="stat-label">Thời gian sửa</div></div>
    <div class="stat"><div class="stat-num">5★</div><div class="stat-label">Đánh giá trung bình</div></div>
  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <div class="section-label">Dịch vụ của chúng tôi</div>
  <h2 class="section-title">Chúng tôi sửa tất cả các loại thiết bị</h2>
  <p class="section-sub">Đội ngũ kỹ thuật viên giàu kinh nghiệm, trang thiết bị hiện đại, linh kiện chính hãng.</p>
  <div class="services-grid">
    <div class="service-card">
      <div class="service-icon">📱</div>
      <h3>Thay màn hình iPhone</h3>
      <p>Tất cả đời từ iPhone 7 đến iPhone 16 Pro Max. Màn hình OLED/LCD chính hãng.</p>
      <span class="service-price">Từ 500.000đ</span>
    </div>
    <div class="service-card">
      <div class="service-icon">🤖</div>
      <h3>Thay màn hình Android</h3>
      <p>Samsung, Xiaomi, OPPO, Vivo, Realme và nhiều thương hiệu khác.</p>
      <span class="service-price">Từ 400.000đ</span>
    </div>
    <div class="service-card">
      <div class="service-icon">📟</div>
      <h3>Thay màn hình máy tính bảng</h3>
      <p>iPad, Samsung Tab, Xiaomi Pad... sửa nhanh trong ngày.</p>
      <span class="service-price">Từ 800.000đ</span>
    </div>
    <div class="service-card">
      <div class="service-icon">🔋</div>
      <h3>Thay pin điện thoại</h3>
      <p>Pin dung lượng cao, giữ sạc lâu. Bảo hành 3 tháng cho pin.</p>
      <span class="service-price">Từ 200.000đ</span>
    </div>
    <div class="service-card">
      <div class="service-icon">💧</div>
      <h3>Sửa điện thoại vào nước</h3>
      <p>Xử lý nhanh, tăng tỷ lệ phục hồi thiết bị. Kiểm tra miễn phí.</p>
      <span class="service-price">Từ 300.000đ</span>
    </div>
    <div class="service-card">
      <div class="service-icon">🔧</div>
      <h3>Sửa lỗi phần mềm</h3>
      <p>Khôi phục cài đặt, xóa virus, nâng cấp hệ điều hành.</p>
      <span class="service-price">Từ 150.000đ</span>
    </div>
  </div>
</section>

<!-- SHOP -->
<section id="shop" class="shop-bg">
  <div class="section-label">Cửa hàng online</div>
  <h2 class="section-title">Phụ kiện & Sản phẩm</h2>
  <p class="section-sub">Mua ngay phụ kiện chính hãng, giao hàng tận nơi trong 2–4 giờ.</p>
  <div class="products-grid">
    <div class="product-card">
      <div class="product-img">🛡️</div>
      <div class="product-info">
        <h4>Kính cường lực iPhone 15</h4>
        <div><span class="price">120.000đ</span><span class="old-price">180.000đ</span></div>
        <button class="add-cart" onclick="addToCart('Kính cường lực iPhone 15', 120000)">🛒 Thêm vào giỏ</button>
      </div>
    </div>
    <div class="product-card">
      <div class="product-img">📦</div>
      <div class="product-info">
        <h4>Ốp lưng chống sốc Samsung S24</h4>
        <div><span class="price">95.000đ</span><span class="old-price">150.000đ</span></div>
        <button class="add-cart" onclick="addToCart('Ốp lưng Samsung S24', 95000)">🛒 Thêm vào giỏ</button>
      </div>
    </div>
    <div class="product-card">
      <div class="product-img">🔌</div>
      <div class="product-info">
        <h4>Cáp sạc Type-C 100W</h4>
        <div><span class="price">85.000đ</span><span class="old-price">120.000đ</span></div>
        <button class="add-cart" onclick="addToCart('Cáp sạc Type-C 100W', 85000)">🛒 Thêm vào giỏ</button>
      </div>
    </div>
    <div class="product-card">
      <div class="product-img">🎧</div>
      <div class="product-info">
        <h4>Tai nghe Bluetooth TWS</h4>
        <div><span class="price">350.000đ</span><span class="old-price">500.000đ</span></div>
        <button class="add-cart" onclick="addToCart('Tai nghe Bluetooth TWS', 350000)">🛒 Thêm vào giỏ</button>
      </div>
    </div>
    <div class="product-card">
      <div class="product-img">🔋</div>
      <div class="product-info">
        <h4>Pin dự phòng 20.000mAh</h4>
        <div><span class="price">280.000đ</span><span class="old-price">420.000đ</span></div>
        <button class="add-cart" onclick="addToCart('Pin dự phòng 20.000mAh', 280000)">🛒 Thêm vào giỏ</button>
      </div>
    </div>
    <div class="product-card">
      <div class="product-img">💡</div>
      <div class="product-info">
        <h4>Đế sạc không dây 15W</h4>
        <div><span class="price">195.000đ</span><span class="old-price">280.000đ</span></div>
        <button class="add-cart" onclick="addToCart('Đế sạc không dây 15W', 195000)">🛒 Thêm vào giỏ</button>
      </div>
    </div>
  </div>
</section>

<!-- BOOKING -->
<section id="booking">
  <div class="section-label">Đặt lịch sửa chữa</div>
  <h2 class="section-title">Đặt lịch ngay – nhận ưu đãi</h2>
  <p class="section-sub">Đặt lịch trước để được phục vụ nhanh nhất và nhận ngay voucher giảm 50.000đ.</p>
  <div class="booking-wrap">
    <div class="booking-form">
      <h3 style="font-family:'Syne',sans-serif;font-weight:700;margin-bottom:1.5rem;">📅 Thông tin đặt lịch</h3>
      <div class="form-row">
        <div class="form-group">
          <label>Họ và tên *</label>
          <input type="text" id="b-name" placeholder="Nguyễn Văn A">
        </div>
        <div class="form-group">
          <label>Số điện thoại *</label>
          <input type="tel" id="b-phone" placeholder="0901 234 567">
        </div>
      </div>
      <div class="form-group">
        <label>Loại thiết bị *</label>
        <select id="b-device">
          <option value="">-- Chọn thiết bị --</option>
          <option>iPhone 16 / 16 Pro / 16 Pro Max</option>
          <option>iPhone 15 series</option>
          <option>iPhone 14 series</option>
          <option>iPhone 13 series</option>
          <option>Samsung Galaxy S24 series</option>
          <option>Samsung Galaxy A series</option>
          <option>Xiaomi / Redmi</option>
          <option>OPPO / Realme</option>
          <option>iPad / Samsung Tab</option>
          <option>Khác</option>
        </select>
      </div>
      <div class="form-group">
        <label>Dịch vụ cần *</label>
        <select id="b-service">
          <option value="">-- Chọn dịch vụ --</option>
          <option>Thay màn hình</option>
          <option>Thay pin</option>
          <option>Sửa vào nước</option>
          <option>Sửa lỗi phần mềm</option>
          <option>Khác</option>
        </select>
      </div>
      <div class="form-row">
        <div class="form-group">
          <label>Ngày hẹn *</label>
          <input type="date" id="b-date">
        </div>
        <div class="form-group">
          <label>Giờ hẹn *</label>
          <select id="b-time">
            <option>08:00</option><option>09:00</option><option>10:00</option>
            <option>11:00</option><option>13:00</option><option>14:00</option>
            <option>15:00</option><option>16:00</option><option>17:00</option>
          </select>
        </div>
      </div>
      <div class="form-group">
        <label>Mô tả thêm</label>
        <textarea id="b-note" placeholder="Màn hình vỡ góc, mất cảm ứng..."></textarea>
      </div>
      <button class="submit-btn" onclick="submitBooking()">✅ Xác nhận đặt lịch – Nhận voucher 50K</button>
      <div class="confirm-msg" id="confirm-msg">🎉 Đặt lịch thành công! Chúng tôi sẽ liên hệ xác nhận trong 15 phút.</div>
    </div>
    <div class="booking-info">
      <h3>Tại sao chọn TechFix Pro?</h3>
      <div class="info-item"><div class="info-icon">⚡</div><div><h4>Sửa nhanh trong 60 phút</h4><p>Không cần chờ lâu, nhận máy ngay tại chỗ với hầu hết các lỗi thông thường.</p></div></div>
      <div class="info-item"><div class="info-icon">🔒</div><div><h4>Bảo hành 6 tháng</h4><p>Cam kết bảo hành toàn bộ dịch vụ, hoàn tiền nếu không hài lòng.</p></div></div>
      <div class="info-item"><div class="info-icon">💎</div><div><h4>Linh kiện chính hãng</h4><p>Chỉ sử dụng màn hình và linh kiện từ nhà cung cấp được chứng nhận.</p></div></div>
      <div class="info-item"><div class="info-icon">🕐</div><div><h4>Giờ mở cửa</h4><p>Thứ 2 – Thứ 7: 8:00 – 19:00<br>Chủ nhật: 9:00 – 17:00</p></div></div>
    </div>
  </div>
</section>

<!-- REVIEWS -->
<section id="reviews" class="reviews-bg">
  <div class="section-label">Khách hàng nói gì</div>
  <h2 class="section-title">Đánh giá thực tế</h2>
  <p class="section-sub" style="margin-bottom:2.5rem;">Hơn 2000 khách hàng đã tin tưởng chúng tôi.</p>
  <div class="reviews-grid">
    <div class="review-card">
      <div class="stars">★★★★★</div>
      <p class="review-text">"Thay màn hình iPhone 14 Pro Max cực nhanh, chỉ 45 phút là xong. Màn hình mới đẹp như mới mua, giá cả rất hợp lý!"</p>
      <div class="reviewer"><div class="avatar">MH</div><div><div class="reviewer-name">Minh Hoàng</div><div class="reviewer-date">2 tuần trước</div></div></div>
    </div>
    <div class="review-card">
      <div class="stars">★★★★★</div>
      <p class="review-text">"Điện thoại bị ngã vỡ màn, mang đến đây sửa. Nhân viên tư vấn rõ ràng, bảo hành 6 tháng, rất uy tín!"</p>
      <div class="reviewer"><div class="avatar">TL</div><div><div class="reviewer-name">Thu Lan</div><div class="reviewer-date">1 tháng trước</div></div></div>
    </div>
    <div class="review-card">
      <div class="stars">★★★★★</div>
      <p class="review-text">"Mua ốp lưng và kính cường lực online, giao hàng siêu nhanh, chỉ 2 tiếng là có. Chất lượng tốt hơn mong đợi!"</p>
      <div class="reviewer"><div class="avatar">QD</div><div><div class="reviewer-name">Quang Đức</div><div class="reviewer-date">3 tuần trước</div></div></div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="section-label">Liên hệ</div>
  <h2 class="section-title">Tìm chúng tôi</h2>
  <p class="section-sub">Ghé trực tiếp hoặc liên hệ qua các kênh bên dưới.</p>
  <div class="contact-grid">
    <div class="contact-card"><div class="c-icon">📍</div><h4>Địa chỉ</h4><p>123 Nguyễn Trãi, Quận 1<br>TP. Hồ Chí Minh</p></div>
    <div class="contact-card"><div class="c-icon">📞</div><h4>Điện thoại</h4><p><a href="tel:0901234567">0901 234 567</a><br>Hotline 7 ngày/tuần</p></div>
    <div class="contact-card"><div class="c-icon">💬</div><h4>Zalo / FB</h4><p><a href="#">Zalo: 0901 234 567</a><br><a href="#">FB: TechFix Pro</a></p></div>
    <div class="contact-card"><div class="c-icon">✉️</div><h4>Email</h4><p><a href="mailto:hello@techfixpro.vn">hello@techfixpro.vn</a></p></div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <p>© 2025 <strong>TechFix Pro</strong> – Dịch vụ thay màn hình điện thoại chuyên nghiệp.<br>
  Thiết kế website bởi Claude AI 🤖</p>
</footer>

<!-- CART BUTTON -->
<button class="cart-btn" onclick="openCart()">
  🛒
  <span class="cart-count" id="cart-count">0</span>
</button>

<!-- CART MODAL -->
<div class="modal-overlay" id="cart-modal">
  <div class="modal">
    <button class="close-modal" onclick="closeCart()">✕</button>
    <h3>🛒 Giỏ hàng</h3>
    <div id="cart-items"></div>
    <div class="cart-total" id="cart-total"></div>
    <button class="checkout-btn" onclick="checkout()">💳 Thanh toán ngay</button>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
  let cart = [];
  let cartCount = 0;

  function addToCart(name, price) {
    cart.push({ name, price });
    cartCount++;
    document.getElementById('cart-count').textContent = cartCount;
    showToast('✅ Đã thêm: ' + name);
  }

  function openCart() {
    const modal = document.getElementById('cart-modal');
    modal.classList.add('open');
    renderCart();
  }

  function closeCart() {
    document.getElementById('cart-modal').classList.remove('open');
  }

  function renderCart() {
    const el = document.getElementById('cart-items');
    const totalEl = document.getElementById('cart-total');
    if (cart.length === 0) {
      el.innerHTML = '<p style="color:var(--gray);text-align:center;padding:2rem 0;">Giỏ hàng trống</p>';
      totalEl.textContent = '';
      return;
    }
    el.innerHTML = cart.map((item, i) =>
      `<div class="cart-item">
        <span class="cart-item-name">${item.name}</span>
        <span class="cart-item-price">${item.price.toLocaleString('vi-VN')}đ</span>
        <button class="remove-item" onclick="removeItem(${i})">✕</button>
      </div>`
    ).join('');
    const total = cart.reduce((s, i) => s + i.price, 0);
    totalEl.innerHTML = Tổng cộng: <span style="color:var(--accent2)">${total.toLocaleString('vi-VN')}đ</span>;
  }

  function removeItem(i) {
    cart.splice(i, 1);
    cartCount--;
    document.getElementById('cart-count').textContent = cartCount;
    renderCart();
  }

  function checkout() {
    if (cart.length === 0) return;
    cart = []; cartCount = 0;
    document.getElementById('cart-count').textContent = 0;
    closeCart();
    showToast('🎉 Đặt hàng thành công! Chúng tôi sẽ liên hệ ngay!');
  }

  function showToast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg;
    t.classList.add('show');
    setTimeout(() => t.classList.remove('show'), 2800);
  }

  function submitBooking() {
    const name = document.getElementById('b-name').value;
    const phone = document.getElementById('b-phone').value;
    const device = document.getElementById('b-device').value;
    const service = document.getElementById('b-service').value;
    const date = document.getElementById('b-date').value;
    if (!name || !phone || !device || !service || !date) {
      showToast('⚠️ Vui lòng điền đầy đủ thông tin!');
      return;
    }
    document.getElementById('confirm-msg').style.display = 'block';
    showToast('🎉 Đặt lịch thành công!');
  }

  // set min date for booking
  const today = new Date().toISOString().split('T')[0];
  document.getElementById('b-date').min = today;
  document.getElementById('b-date').value = today;
</script>
</body>
</html>
