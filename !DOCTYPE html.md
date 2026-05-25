<!DOCTYPE html>  
<html dir="rtl" lang="ar">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">  
    <title>سراب - متجر الأزياء</title>  
    <style>  
        * {  
            margin: 0;  
            padding: 0;  
            box-sizing: border-box;  
        }  
  
        body {  
            font-family: 'Tajawal', 'Segoe UI', system-ui, sans-serif;  
            background: linear-gradient(135deg, #f5f0e8 0%, #e8e0d5 100%);  
            color: #2c2c2c;  
        }  
  
        /* ========== شريط علوي شفاف مائي ========== */  
        .navbar {  
            position: fixed;  
            top: 0;  
            left: 0;  
            right: 0;  
            background: rgba(255, 255, 255, 0.6);  
            backdrop-filter: blur(15px);  
            -webkit-backdrop-filter: blur(15px);  
            z-index: 1000;  
            padding: 12px 20px;  
            border-bottom: 1px solid rgba(77, 40, 11, 0.1);  
        }  
  
        .navbar-container {  
            max-width: 1200px;  
            margin: 0 auto;  
            display: flex;  
            align-items: center;  
            justify-content: space-between;  
        }  
  
        .menu-icon {  
            font-size: 1.5rem;  
            cursor: pointer;  
            background: rgba(77, 40, 11, 0.1);  
            width: 42px;  
            height: 42px;  
            display: flex;  
            align-items: center;  
            justify-content: center;  
            border-radius: 50%;  
            transition: 0.2s;  
        }  
  
        .menu-icon:hover {  
            background: rgba(77, 40, 11, 0.2);  
        }  
  
        .navbar-logo {  
            font-size: 1.6rem;  
            font-weight: 800;  
            letter-spacing: 2px;  
            background: linear-gradient(135deg, #4D280B, #8B5A2B);  
            -webkit-background-clip: text;  
            background-clip: text;  
            color: transparent;  
        }  
  
        .navbar-icons {  
            display: flex;  
            gap: 12px;  
            align-items: center;  
        }  
  
        .nav-icon {  
            background: rgba(77, 40, 11, 0.1);  
            width: 42px;  
            height: 42px;  
            display: flex;  
            align-items: center;  
            justify-content: center;  
            border-radius: 50%;  
            cursor: pointer;  
            transition: 0.2s;  
            font-size: 1.2rem;  
            position: relative;  
        }  
  
        .nav-icon:hover {  
            background: rgba(77, 40, 11, 0.2);  
            transform: scale(1.05);  
        }  
  
        .cart-count {  
            position: absolute;  
            top: -3px;  
            right: -3px;  
            background: #b33;  
            color: white;  
            font-size: 0.65rem;  
            font-weight: bold;  
            border-radius: 50%;  
            width: 18px;  
            height: 18px;  
            display: flex;  
            align-items: center;  
            justify-content: center;  
        }  
  
        /* ========== المحتوى الرئيسي ========== */  
        .page {  
            padding: 20px;  
            max-width: 1200px;  
            margin: 80px auto 0;  
        }  
  
        /* بطاقات المنتجات الشفافة */  
        .products-grid {  
            display: grid;  
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));  
            gap: 25px;  
            margin-bottom: 60px;  
        }  
  
        .product-card {  
            background: rgba(255, 255, 255, 0.7);  
            backdrop-filter: blur(10px);  
            border-radius: 24px;  
            overflow: hidden;  
            box-shadow: 0 8px 20px rgba(0,0,0,0.05);  
            transition: all 0.3s ease;  
            position: relative;  
            border: 1px solid rgba(255,255,255,0.3);  
        }  
  
        .product-card:hover {  
            transform: translateY(-8px);  
            background: rgba(255, 255, 255, 0.85);  
            box-shadow: 0 15px 30px rgba(0,0,0,0.1);  
        }  
  
        .plus-btn {  
            position: absolute;  
            bottom: 15px;  
            left: 15px;  
            width: 45px;  
            height: 45px;  
            background: #4D280B;  
            border-radius: 50%;  
            display: flex;  
            align-items: center;  
            justify-content: center;  
            color: white;  
            font-size: 1.8rem;  
            cursor: pointer;  
            transition: 0.2s;  
            z-index: 10;  
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);  
        }  
  
        .plus-btn:hover {  
            transform: scale(1.1);  
            background: #2e1806;  
        }  
  
        .product-img {  
            width: 100%;  
            height: 260px;  
            object-fit: cover;  
            background: rgba(240, 237, 232, 0.5);  
            display: flex;  
            align-items: center;  
            justify-content: center;  
            font-size: 4rem;  
        }  
  
        .product-info {  
            padding: 15px;  
            text-align: center;  
        }  
  
        .product-title {  
            font-size: 1.1rem;  
            font-weight: 600;  
            color: #4D280B;  
        }  
  
        .product-price {  
            font-size: 1.2rem;  
            font-weight: bold;  
            color: #2c6e2c;  
            margin: 5px 0;  
        }  
  
        .stock-badge {  
            position: absolute;  
            top: 10px;  
            right: 10px;  
            background: rgba(0,0,0,0.6);  
            color: white;  
            padding: 3px 8px;  
            border-radius: 20px;  
            font-size: 0.65rem;  
        }  
  
        .stock-badge.low { background: #b33; }  
        .stock-badge.medium { background: #e6a017; }  
        .stock-badge.high { background: #2c6e2c; }  
  
        /* ========== آراء العملاء ========== */  
        .reviews-section {  
            background: rgba(255, 255, 255, 0.5);  
            backdrop-filter: blur(10px);  
            border-radius: 30px;  
            padding: 40px 20px;  
            margin: 40px 0;  
            border: 1px solid rgba(255,255,255,0.3);  
        }  
  
        .section-title {  
            text-align: center;  
            font-size: 1.8rem;  
            color: #4D280B;  
            margin-bottom: 30px;  
            position: relative;  
        }  
  
        .section-title::after {  
            content: '';  
            display: block;  
            width: 80px;  
            height: 3px;  
            background: #4D280B;  
            margin: 10px auto;  
            border-radius: 3px;  
        }  
  
        .reviews-container {  
            display: flex;  
            flex-wrap: wrap;  
            gap: 20px;  
            justify-content: center;  
        }  
  
        .review-card {  
            background: rgba(255, 255, 255, 0.8);  
            backdrop-filter: blur(5px);  
            border-radius: 20px;  
            padding: 20px;  
            width: 280px;  
            transition: 0.2s;  
        }  
  
        .review-card:hover {  
            transform: translateY(-5px);  
            background: white;  
        }  
  
        .review-stars {  
            color: #FFD700;  
            font-size: 1.2rem;  
            margin-bottom: 10px;  
        }  
  
        .review-text {  
            font-size: 0.9rem;  
            color: #555;  
            margin-bottom: 15px;  
            line-height: 1.5;  
        }  
  
        .review-author {  
            font-weight: bold;  
            color: #4D280B;  
        }  
  
        .add-review-btn {  
            background: #4D280B;  
            color: white;  
            border: none;  
            padding: 10px 24px;  
            border-radius: 40px;  
            cursor: pointer;  
            display: block;  
            margin: 30px auto 0;  
            font-size: 1rem;  
            transition: 0.2s;  
        }  
  
        .add-review-btn:hover {  
            background: #2e1806;  
            transform: scale(1.02);  
        }  
  
        /* ========== الفوتر (تواصل اجتماعي + خدمة العملاء) ========== */  
        footer {  
            background: #4D280B;  
            color: white;  
            padding: 50px 20px 30px;  
            margin-top: 60px;  
            border-radius: 30px 30px 0 0;  
        }  
  
        .footer-container {  
            max-width: 1200px;  
            margin: 0 auto;  
            display: grid;  
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));  
            gap: 40px;  
        }  
  
        .footer-section h3 {  
            font-size: 1.3rem;  
            margin-bottom: 20px;  
            border-right: 3px solid #e6a017;  
            padding-right: 12px;  
        }  
  
        .footer-section p, .footer-section a {  
            color: #ddd;  
            text-decoration: none;  
            display: block;  
            margin-bottom: 12px;  
            font-size: 0.95rem;  
            transition: 0.2s;  
        }  
  
        .footer-section a:hover {  
            color: #e6a017;  
            transform: translateX(-5px);  
            display: inline-block;  
        }  
  
        .social-icons {  
            display: flex;  
            gap: 15px;  
            margin-top: 20px;  
            flex-wrap: wrap;  
        }  
  
        .social-icon {  
            background: rgba(255,255,255,0.1);  
            width: 45px;  
            height: 45px;  
            border-radius: 50%;  
            display: flex;  
            align-items: center;  
            justify-content: center;  
            font-size: 1.4rem;  
            cursor: pointer;  
            transition: 0.2s;  
        }  
  
        .social-icon:hover {  
            background: #e6a017;  
            transform: translateY(-3px);  
        }  
  
        .contact-item {  
            display: flex;  
            align-items: center;  
            gap: 12px;  
            margin-bottom: 15px;  
        }  
  
        .contact-item span:first-child {  
            font-size: 1.3rem;  
        }  
  
        .copyright {  
            text-align: center;  
            padding-top: 40px;  
            margin-top: 40px;  
            border-top: 1px solid rgba(255,255,255,0.1);  
            font-size: 0.8rem;  
            color: #bbb;  
        }  
  
        /* ========== مودال اختيار اللون والمقاس ========== */  
        .option-modal {  
            display: none;  
            position: fixed;  
            top: 0;  
            left: 0;  
            width: 100%;  
            height: 100%;  
            background: rgba(0,0,0,0.5);  
            backdrop-filter: blur(5px);  
            justify-content: center;  
            align-items: center;  
            z-index: 2000;  
        }  
  
        .option-modal-content {  
            background: rgba(255, 255, 255, 0.95);  
            backdrop-filter: blur(15px);  
            border-radius: 28px;  
            width: 90%;  
            max-width: 380px;  
            padding: 25px;  
            text-align: center;  
            animation: fadeInUp 0.3s;  
            position: relative;  
        }  
  
        @keyframes fadeInUp {  
            from { opacity: 0; transform: translateY(30px); }  
            to { opacity: 1; transform: translateY(0); }  
        }  
  
        .close-modal-btn {  
            position: absolute;  
            top: 15px;  
            left: 20px;  
            font-size: 1.5rem;  
            cursor: pointer;  
            color: #4D280B;  
        }  
  
        .option-group {  
            margin-bottom: 20px;  
            text-align: right;  
        }  
  
        .option-group label {  
            display: block;  
            font-weight: bold;  
            margin-bottom: 8px;  
            color: #4D280B;  
        }  
  
        .color-options, .size-options {  
            display: flex;  
            flex-wrap: wrap;  
            gap: 10px;  
            justify-content: center;  
        }  
  
        .color-circle {  
            width: 40px;  
            height: 40px;  
            border-radius: 50%;  
            cursor: pointer;  
            border: 2px solid #ddd;  
            transition: 0.1s;  
        }  
  
        .color-circle.selected {  
            border: 3px solid #4D280B;  
            transform: scale(1.1);  
        }  
  
        .size-option {  
            background: #f0ede8;  
            padding: 8px 16px;  
            border-radius: 30px;  
            cursor: pointer;  
            transition: 0.1s;  
        }  
  
        .size-option.selected {  
            background: #4D280B;  
            color: white;  
        }  
  
        .quantity-selector {  
            display: flex;  
            align-items: center;  
            justify-content: center;  
            gap: 15px;  
            margin: 15px 0;  
        }  
  
        .qty-btn {  
            width: 35px;  
            height: 35px;  
            background: #e0d6cc;  
            border: none;  
            border-radius: 50%;  
            font-size: 1.2rem;  
            cursor: pointer;  
        }  
  
        .confirm-btn {  
            background: #4D280B;  
            color: white;  
            border: none;  
            padding: 12px;  
            border-radius: 40px;  
            width: 100%;  
            font-size: 1rem;  
            cursor: pointer;  
            margin-top: 15px;  
        }  
  
        /* مودال السلة */  
        .cart-modal {  
            display: none;  
            position: fixed;  
            top: 0;  
            left: 0;  
            width: 100%;  
            height: 100%;  
            background: rgba(0,0,0,0.5);  
            justify-content: center;  
            align-items: center;  
            z-index: 1500;  
        }  
  
        .cart-modal-content {  
            background: white;  
            border-radius: 24px;  
            width: 90%;  
            max-width: 500px;  
            padding: 20px;  
            max-height: 85vh;  
            overflow-y: auto;  
        }  
  
        .close-cart {  
            float: left;  
            font-size: 28px;  
            cursor: pointer;  
        }  
  
        .cart-item {  
            display: flex;  
            justify-content: space-between;  
            padding: 12px 0;  
            border-bottom: 1px solid #eee;  
            flex-wrap: wrap;  
        }  
  
        .cart-total {  
            font-weight: bold;  
            margin: 15px 0;  
            font-size: 1.1rem;  
        }  
  
        .customer-info input, .customer-info textarea {  
            width: 100%;  
            padding: 10px;  
            margin: 8px 0;  
            border: 1px solid #ddd;  
            border-radius: 12px;  
        }  
  
        .toast {  
            position: fixed;  
            bottom: 30px;  
            left: 50%;  
            transform: translateX(-50%);  
            background: #4D280B;  
            color: white;  
            padding: 10px 20px;  
            border-radius: 50px;  
            z-index: 2000;  
            animation: fadeIn 0.3s;  
        }  
  
        @keyframes fadeIn {  
            from { opacity: 0; bottom: 10px; }  
            to { opacity: 1; bottom: 30px; }  
        }  
  
        @media (max-width: 600px) {  
            .page { margin-top: 70px; }  
            .products-grid { gap: 15px; }  
            .footer-container { grid-template-columns: 1fr; text-align: center; }  
            .footer-section h3 { border-right: none; border-bottom: 2px solid #e6a017; padding-bottom: 8px; display: inline-block; }  
            .social-icons { justify-content: center; }  
            .contact-item { justify-content: center; }  
        }  
    </style>  
</head>  
<body>  
  
<!-- شريط علوي شفاف -->  
<div class="navbar">  
    <div class="navbar-container">  
        <div class="menu-icon" onclick="toggleSideMenu()">☰</div>  
        <div class="navbar-logo">SARAB</div>  
        <div class="navbar-icons">  
            <div class="nav-icon" onclick="openCart()">🛒<span class="cart-count" id="cartCount">0</span></div>  
        </div>  
    </div>  
</div>  
  
<!-- القائمة الجانبية -->  
<div id="sideMenu" class="side-menu" style="position:fixed; top:0; right:-300px; width:280px; height:100%; background:rgba(255,255,255,0.95); backdrop-filter:blur(15px); z-index:1100; transition:0.3s; padding:80px 20px 20px;">  
    <div class="close-menu" onclick="toggleSideMenu()" style="position:absolute; top:20px; left:20px; font-size:1.8rem; cursor:pointer;">✕</div>  
    <a href="#" onclick="scrollToSection('products')">🏠 الرئيسية</a>  
    <a href="#" onclick="scrollToSection('products')">👕 المنتجات</a>  
    <a href="#" onclick="scrollToSection('reviews')">⭐ آراء العملاء</a>  
    <a href="#" onclick="scrollToSection('contact')">📞 اتصل بنا</a>  
    <a href="#" onclick="openCart()">🛒 سلة التسوق</a>  
</div>  
<div id="overlay" onclick="toggleSideMenu()" style="position:fixed; top:0; left:0; right:0; bottom:0; background:rgba(0,0,0,0.3); z-index:1050; display:none;"></div>  
  
<!-- المحتوى الرئيسي -->  
<div class="page">  
    <!-- شبكة المنتجات -->  
    <div class="products-grid" id="productsGrid"></div>  
  
    <!-- آراء العملاء -->  
    <div class="reviews-section" id="reviews">  
        <h2 class="section-title">📝 آراء عملائنا</h2>  
        <div class="reviews-container" id="reviewsContainer"></div>  
        <button class="add-review-btn" onclick="showAddReview()">➕ أضف رأيك</button>  
    </div>  
</div>  
  
<!-- الفوتر: تواصل اجتماعي + خدمة العملاء -->  
<footer id="contact">  
    <div class="footer-container">  
        <div class="footer-section">  
            <h3>🌐 تابعنا</h3>  
            <div class="social-icons">  
                <div class="social-icon" onclick="window.open('https://instagram.com', '_blank')">📷</div>  
                <div class="social-icon" onclick="window.open('https://tiktok.com', '_blank')">🎵</div>  
                <div class="social-icon" onclick="window.open('https://twitter.com', '_blank')">🐦</div>  
                <div class="social-icon" onclick="window.open('https://facebook.com', '_blank')">📘</div>  
                <div class="social-icon" onclick="window.open('https://wa.me/218912345678', '_blank')">💬</div>  
                <div class="social-icon" onclick="window.open('https://snapchat.com', '_blank')">👻</div>  
            </div>  
        </div>  
        <div class="footer-section">  
            <h3>📞 خدمة العملاء</h3>  
            <div class="contact-item">  
                <span>💬</span>  
                <span><a href="https://wa.me/218912345678" target="_blank">واتساب: +218 912 345 678</a></span>  
            </div>  
            <div class="contact-item">  
                <span>📧</span>  
                <span><a href="mailto:sarab@shop.com">البريد: sarab@shop.com</a></span>  
            </div>  
            <div class="contact-item">  
                <span>📞</span>  
                <span><a href="tel:+218912345678">اتصال: +218 912 345 678</a></span>  
            </div>  
        </div>  
        <div class="footer-section">  
            <h3>🔗 روابط مهمة</h3>  
            <a href="#">سياسة الاستبدال والإسترجاع</a>  
            <a href="#">الشحن والتوصيل</a>  
            <a href="#">الأسئلة الشائعة</a>  
            <a href="#">معلومات عنا</a>  
        </div>  
        <div class="footer-section">  
            <h3>📦 شرح سريع</h3>  
            <p>🚀 استلم طلبك في وقت قياسي</p>  
            <p>💎 منتجات أصلية 100%</p>  
            <p>🔄 سياسة استبدال مرنة</p>  
            <p>⭐ خدمة عملاء على مدار الساعة</p>  
        </div>  
    </div>  
    <div class="copyright">  
        <p>© 2024 سراب - جميع الحقوق محفوظة</p>  
        <p style="font-size: 0.7rem; margin-top: 5px;">وثيقة العمل الحر | FL-412623614</p>  
    </div>  
</footer>  
  
<!-- مودال اختيار اللون والمقاس -->  
<div id="optionModal" class="option-modal">  
    <div class="option-modal-content">  
        <span class="close-modal-btn" onclick="closeOptionModal()">&times;</span>  
        <h3 id="modalProductName">اختر التفاصيل</h3>  
        <div class="option-group">  
            <label>🎨 اللون</label>  
            <div class="color-options" id="colorOptions"></div>  
        </div>  
        <div class="option-group">  
            <label>📏 المقاس</label>  
            <div class="size-options" id="sizeOptions"></div>  
        </div>  
        <div class="option-group">  
            <label>🔢 الكمية</label>  
            <div class="quantity-selector">  
                <button class="qty-btn" onclick="changeModalQty(-1)">-</button>  
                <span class="qty-value" id="modalQty">1</span>  
                <button class="qty-btn" onclick="changeModalQty(1)">+</button>  
            </div>  
        </div>  
        <button class="confirm-btn" onclick="confirmAddToCart()">➕ إضافة إلى السلة</button>  
    </div>  
</div>  
  
<!-- مودال السلة -->  
<div id="cartModal" class="cart-modal">  
    <div class="cart-modal-content">  
        <span class="close-cart" onclick="closeCart()">&times;</span>  
        <h2>🛍️ سلة التسوق</h2>  
        <div id="cartItems"></div>  
        <div class="cart-total" id="cartTotal"></div>  
        <div class="customer-info">  
            <input type="text" id="customerName" placeholder="الاسم الكامل">  
            <input type="tel" id="customerPhone" placeholder="رقم الهاتف (واتساب)">  
            <textarea id="customerAddress" rows="2" placeholder="العنوان"></textarea>  
        </div>  
        <button class="confirm-btn" onclick="processPayment()">💬 إتمام الطلب عبر واتساب</button>  
    </div>  
</div>  
  
<!-- مودال إضافة رأي -->  
<div id="reviewModal" class="cart-modal">  
    <div class="cart-modal-content" style="max-width:400px;">  
        <span class="close-cart" onclick="closeReviewModal()">&times;</span>  
        <h2 style="text-align:center;">⭐ أضف رأيك</h2>  
        <div style="margin: 15px 0; text-align:center;">  
            <div style="display: flex; gap: 8px; font-size: 2rem; justify-content: center; cursor: pointer;" id="ratingStars">★★★★★</div>  
            <input type="hidden" id="reviewRating" value="5">  
        </div>  
        <textarea id="reviewText" rows="3" placeholder="رأيك..." style="width:100%; padding:10px; border-radius:12px; margin:10px 0;"></textarea>  
        <input type="text" id="reviewAuthor" placeholder="اسمك" style="width:100%; padding:10px; border-radius:12px; margin:10px 0;">  
        <button class="confirm-btn" onclick="addReview()">إرسال الرأي</button>  
    </div>  
</div>  
  
<script>  
    // ========== القائمة الجانبية ==========  
    function toggleSideMenu() {  
        const menu = document.getElementById('sideMenu');  
        const overlay = document.getElementById('overlay');  
        if (menu.style.right === '0px') {  
            menu.style.right = '-300px';  
            overlay.style.display = 'none';  
        } else {  
            menu.style.right = '0px';  
            overlay.style.display = 'block';  
        }  
    }  
  
    function scrollToSection(section) {  
        toggleSideMenu();  
        if (section === 'products') {  
            document.querySelector('.products-grid').scrollIntoView({ behavior: 'smooth' });  
        } else if (section === 'reviews') {  
            document.getElementById('reviews').scrollIntoView({ behavior: 'smooth' });  
        } else if (section === 'contact') {  
            document.getElementById('contact').scrollIntoView({ behavior: 'smooth' });  
        }  
    }  
  
    // ========== آراء العملاء ==========  
    let reviews = [];  
    let ratingValue = 5;  
  
    function loadReviews() {  
        const stored = localStorage.getItem('sarab_reviews');  
        if (stored) {  
            reviews = JSON.parse(stored);  
        } else {  
            reviews = [  
                { id: 1, author: "أحمد محمد", rating: 5, text: "منتج رائع جداً، جودة عالية وأنصح به", date: "2024-01-15" },  
                { id: 2, author: "فاطمة علي", rating: 4, text: "المنتج جميل وسعر مناسب، شكراً سراب", date: "2024-01-20" },  
                { id: 3, author: "عبدالله سعيد", rating: 5, text: "خدمة ممتازة وسريعة، المنتج وصل بحالة جيدة", date: "2024-01-25" }  
            ];  
            saveReviews();  
        }  
        renderReviews();  
    }  
  
    function saveReviews() {  
        localStorage.setItem('sarab_reviews', JSON.stringify(reviews));  
    }  
  
    function renderReviews() {  
        const container = document.getElementById('reviewsContainer');  
        if (!container) return;  
        container.innerHTML = reviews.slice(-6).reverse().map(r => `  
            <div class="review-card">  
                <div class="review-stars">${'★'.repeat(r.rating)}${'☆'.repeat(5-r.rating)}</div>  
                <div class="review-text">"${r.text.substring(0, 100)}"</div>  
                <div class="review-author">- ${r.author}</div>  
            </div>  
        `).join('');  
    }  
  
    function showAddReview() {  
        document.getElementById('reviewModal').style.display = 'flex';  
        document.getElementById('reviewText').value = '';  
        document.getElementById('reviewAuthor').value = '';  
        ratingValue = 5;  
        updateStarDisplay();  
    }  
  
    function closeReviewModal() {  
        document.getElementById('reviewModal').style.display = 'none';  
    }  
  
    function updateStarDisplay() {  
        const stars = document.getElementById('ratingStars');  
        if (stars) {  
            stars.innerHTML = '';  
            for (let i = 1; i <= 5; i++) {  
                stars.innerHTML += i <= ratingValue ? '★' : '☆';  
            }  
        }  
    }  
  
    document.getElementById('ratingStars')?.addEventListener('click', function(e) {  
        const target = e.target;  
        if (target.textContent === '★' || target.textContent === '☆') {  
            const index = [...target.parentElement.children].indexOf(target);  
            if (index !== -1) ratingValue = index + 1;  
            updateStarDisplay();  
            document.getElementById('reviewRating').value = ratingValue;  
        }  
    });  
  
    function addReview() {  
        const text = document.getElementById('reviewText').value;  
        const author = document.getElementById('reviewAuthor').value;  
        if (!text || !author) {  
            showToast('الرجاء إدخال رأيك واسمك');  
            return;  
        }  
        reviews.push({  
            id: Date.now(),  
            author: author,  
            rating: ratingValue,  
            text: text,  
            date: new Date().toISOString().split('T')[0]  
        });  
        saveReviews();  
        renderReviews();  
        closeReviewModal();  
        showToast('✅ شكراً لمشاركتك رأيك');  
    }  
  
    // ========== بيانات المنتجات ==========  
    let products = [];  
    let cart = [];  
    let selectedProductId = null;  
    let selectedColor = null;  
    let selectedSize = null;  
    let modalQuantity = 1;  
    let productStock = 0;  
  
    const availableColors = [  
        { name: "أسود", code: "#111111" }, { name: "أبيض", code: "#F5F5F5" },  
        { name: "رمادي", code: "#888888" }, { name: "أحمر", code: "#CC3333" },  
        { name: "أزرق", code: "#2266CC" }, { name: "أخضر", code: "#2C6E2C" },  
        { name: "بيج", code: "#F5E6D3" }, { name: "كحلي", code: "#1A2A4F" }  
    ];  
    const availableSizes = ["XS", "S", "M", "L", "XL", "XXL"];  
  
    function loadProducts() {  
        const stored = localStorage.getItem('sarab_products');  
        if (stored) {  
            products = JSON.parse(stored);  
        } else {  
            products = [  
                { id: 1, name: "KARKADEH", price: 35, stock: 0, imageData: null, colors: ["أسود"], sizes: ["M","L"], soldOut: true },  
                { id: 2, name: "ASWAD COMFORT BOTTOMS", price: 60, stock: 8, imageData: null, colors: ["أسود", "رمادي"], sizes: ["S","M","L","XL"], soldOut: false },  
                { id: 3, name: "THE PERFECT TEE", price: 45, stock: 3, imageData: null, colors: ["أبيض", "أسود"], sizes: ["M","L"], soldOut: false },  
                { id: 4, name: "QUBBA'A", price: 25, stock: 15, imageData: null, colors: ["بيج", "كحلي"], sizes: ["M","L"], soldOut: false }  
            ];  
            saveProducts();  
        }  
        renderProducts();  
    }  
  
    function saveProducts() {  
        localStorage.setItem('sarab_products', JSON.stringify(products));  
    }  
  
    function getColorCode(name) {  
        const c = availableColors.find(c => c.name === name);  
        return c ? c.code : '#ccc';  
    }  
  
    function getStockClass(stock) {  
        if (stock === 0) return 'low';  
        if (stock <= 3) return 'low';  
        if (stock <= 8) return 'medium';  
        return 'high';  
    }  
  
    function getStockText(stock) {  
        if (stock === 0) return 'غير متوفر';  
        if (stock <= 3) return `⚠️ متبقي ${stock}`;  
        if (stock <= 8) return `📦 متبقي ${stock}`;  
        return `✅ متوفر ${stock}`;  
    }  
  
    function renderProducts() {  
        const grid = document.getElementById('productsGrid');  
        if (!grid) return;  
        grid.innerHTML = products.map(p => {  
            const img = p.imageData ? `<img src="${p.imageData}" class="product-img">` : `<div class="product-img">👕</div>`;  
            return `  
                <div class="product-card">  
                    <div class="stock-badge ${getStockClass(p.stock)}">${getStockText(p.stock)}</div>  
                    ${img}  
                    <div class="product-info">  
                        <div class="product-title">${p.name}</div>  
                        <div class="product-price">${p.price} د.ل</div>  
                    </div>  
                    <div class="plus-btn" onclick="openOptionModal(${p.id})">+</div>  
                </div>  
            `;  
        }).join('');  
    }  
  
    // ========== نافذة اختيار اللون والمقاس ==========  
    function openOptionModal(productId) {  
        const product = products.find(p => p.id === productId);  
        if (!product || product.stock === 0) {  
            showToast('هذا المنتج غير متوفر حالياً');  
            return;  
        }  
        selectedProductId = productId;  
        productStock = product.stock;  
        selectedColor = product.colors[0] || null;  
        selectedSize = product.sizes[0] || null;  
        modalQuantity = 1;  
        document.getElementById('modalProductName').innerText = product.name;  
        document.getElementById('modalQty').innerText = modalQuantity;  
          
        const colorContainer = document.getElementById('colorOptions');  
        colorContainer.innerHTML = product.colors.map(c => `  
            <div class="color-circle" style="background:${getColorCode(c)}" data-color="${c}" onclick="selectModalColor('${c}')"></div>  
        `).join('');  
          
        const sizeContainer = document.getElementById('sizeOptions');  
        sizeContainer.innerHTML = product.sizes.map(s => `  
            <div class="size-option" data-size="${s}" onclick="selectModalSize('${s}')">${s}</div>  
        `).join('');  
          
        document.querySelectorAll('.color-circle').forEach(el => {  
            if (el.getAttribute('data-color') === selectedColor) el.classList.add('selected');  
        });  
        document.querySelectorAll('.size-option').forEach(el => {  
            if (el.getAttribute('data-size') === selectedSize) el.classList.add('selected');  
        });  
          
        document.getElementById('optionModal').style.display = 'flex';  
    }  
  
    function selectModalColor(color) {  
        selectedColor = color;  
        document.querySelectorAll('.color-circle').forEach(el => el.classList.remove('selected'));  
        document.querySelector(`.color-circle[data-color="${color}"]`).classList.add('selected');  
    }  
  
    function selectModalSize(size) {  
        selectedSize = size;  
        document.querySelectorAll('.size-option').forEach(el => el.classList.remove('selected'));  
        document.querySelector(`.size-option[data-size="${size}"]`).classList.add('selected');  
    }  
  
    function changeModalQty(delta) {  
        let newQty = modalQuantity + delta;  
        if (newQty < 1) newQty = 1;  
        if (newQty > productStock) newQty = productStock;  
        modalQuantity = newQty;  
        document.getElementById('modalQty').innerText = modalQuantity;  
    }  
  
    function closeOptionModal() {  
        document.getElementById('optionModal').style.display = 'none';  
        selectedProductId = null;  
    }  
  
    function confirmAddToCart() {  
        if (!selectedColor || !selectedSize) {  
            showToast('الرجاء اختيار اللون والمقاس');  
            return;  
        }  
        const product = products.find(p => p.id === selectedProductId);  
        if (!product) return;  
          
        if (modalQuantity > product.stock) {  
            showToast(`الكمية المطلوبة (${modalQuantity}) أكبر من المتوفر (${product.stock})`);  
            return;  
        }  
          
        const existing = cart.find(i => i.id === selectedProductId && i.color === selectedColor && i.size === selectedSize);  
        if (existing) {  
            if (existing.qty + modalQuantity > product.stock) {  
                showToast(`لا يمكن إضافة ${modalQuantity} قطع، المتوفر فقط ${product.stock - existing.qty}`);  
                return;  
            }  
            existing.qty += modalQuantity;  
        } else {  
            cart.push({  
                id: selectedProductId,  
                name: product.name,  
                price: product.price,  
                color: selectedColor,  
                size: selectedSize,  
                qty: modalQuantity  
            });  
        }  
          
        product.stock -= modalQuantity;  
        if (product.stock === 0) product.soldOut = true;  
        saveProducts();  
        saveCart();  
        renderProducts();  
        closeOptionModal();  
        showToast(`✅ تمت إضافة ${modalQuantity} × ${product.name} إلى السلة`);  
    }  
  
    // ========== السلة ==========  
    function loadCart() {  
        const stored = localStorage.getItem('sarab_cart');  
        if (stored) cart = JSON.parse(stored);  
        updateCartUI();  
    }  
  
    function saveCart() {  
        localStorage.setItem('sarab_cart', JSON.stringify(cart));  
        updateCartUI();  
    }  
  
    function updateCartUI() {  
        const count = cart.reduce((s, i) => s + i.qty, 0);  
        document.getElementById('cartCount').innerText = count;  
        renderCartModal();  
    }  
  
    function renderCartModal() {  
        const container = document.getElementById('cartItems');  
        if (!container) return;  
        if (cart.length === 0) {  
            container.innerHTML = '<p>السلة فارغة</p>';  
            document.getElementById('cartTotal').innerHTML = 'المجموع: 0 د.ل';  
            return;  
        }  
        let total = 0;  
        let html = '';  
        cart.forEach((item, idx) => {  
            total += item.price * item.qty;  
            html += `<div class="cart-item">  
                        <div><b>${item.name}</b><br>${item.color} | ${item.size}<br>${item.price} د.ل × ${item.qty} = ${(item.price*item.qty).toFixed(2)}</div>  
                        <button onclick="removeFromCart(${idx})" style="background:#b33; color:white; border:none; padding:5px 12px; border-radius:20px;">حذف</button>  
                     </div>`;  
        });  
        container.innerHTML = html;  
        document.getElementById('cartTotal').innerHTML = `المجموع الكلي: ${total.toFixed(2)} د.ل`;  
    }  
  
    function removeFromCart(idx) {  
        const item = cart[idx];  
        const product = products.find(p => p.id === item.id);  
        if (product) {  
            product.stock += item.qty;  
            if (product.stock > 0) product.soldOut = false;  
            saveProducts();  
            renderProducts();  
        }  
        cart.splice(idx, 1);  
        saveCart();  
    }  
  
    function openCart() {  
        renderCartModal();  
        document.getElementById('customerName').value = '';  
        document.getElementById('customerPhone').value = '';  
        document.getElementById('customerAddress').value = '';  
        document.getElementById('cartModal').style.display = 'flex';  
    }  
  
    function closeCart() {  
        document.getElementById('cartModal').style.display = 'none';  
    }  
  
    function processPayment() {  
        const name = document.getElementById('customerName').value;  
        const phone = document.getElementById('customerPhone').value;  
        if (!name || !phone) {  
            alert('الرجاء إدخال الاسم ورقم الهاتف');  
            return;  
        }  
        if (cart.length === 0) {  
            alert('السلة فارغة');  
            return;  
        }  
        let total = 0;  
        let items = cart.map((item, i) => `${i+1}️⃣ ${item.name}\n   ▫️ ${item.color} | ${item.size}\n   ▫️ ${item.price} د.ل × ${item.qty} = ${(item.price*item.qty).toFixed(2)}`).join('\n\n');  
        cart.forEach(i => total += i.price * i.qty);  
        const msg = encodeURIComponent(`🛍️ طلب جديد من متجر سراب\n\n👤 الاسم: ${name}\n📞 الهاتف: ${phone}\n📍 العنوان: ${document.getElementById('customerAddress').value}\n\nالمنتجات:\n${items}\n\n💰 المجموع الكلي: ${total.toFixed(2)} د.ل`);  
        window.open(`https://wa.me/218912345678?text=${msg}`, '_blank');  
        cart = [];  
        saveCart();  
        closeCart();  
        showToast('✅ تم إرسال الطلب بنجاح');  
    }  
  
    function showToast(msg) {  
        const toast = document.createElement('div');  
        toast.className = 'toast';  
        toast.innerText = msg;  
        document.body.appendChild(toast);  
        setTimeout(() => toast.remove(), 2500);  
    }  
  
    // ربط الدوال  
    window.toggleSideMenu = toggleSideMenu;  
    window.scrollToSection = scrollToSection;  
    window.openOptionModal = openOptionModal;  
    window.selectModalColor = selectModalColor;  
    window.selectModalSize = selectModalSize;  
    window.changeModalQty = changeModalQty;  
    window.closeOptionModal = closeOptionModal;  
    window.confirmAddToCart = confirmAddToCart;  
    window.removeFromCart = removeFromCart;  
    window.openCart = openCart;  
    window.closeCart = closeCart;  
    window.processPayment = processPayment;  
    window.showAddReview = showAddReview;  
    window.closeReviewModal = closeReviewModal;  
    window.addReview = addReview;  
  
    loadProducts();  
    loadCart();  
    loadReviews();  
</script>  
</body>  
</html>  
