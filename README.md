<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Budong Cravings - Premium Meals, Affordable Prices</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        /* CSS Variables for Colors */
        :root {
            --primary-green: #1DB954;
            --secondary-yellow: #FFC107;
            --background: #FEFEFE;
            --accent-dark-green: #0D7F3F;
            --hover-light-green: #E8F5E8;
            --text-dark: #333;
            --shadow: rgba(0, 0, 0, 0.1);
        }

        /* Dark Mode Variables */
        [data-theme="dark"] {
            --background: #121212;
            --text-dark: #E0E0E0;
            --shadow: rgba(255, 255, 255, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background-color: var(--background);
            color: var(--text-dark);
            transition: background-color 0.3s, color 0.3s;
        }

        /* Header */
        header {
            position: sticky;
            top: 0;
            background: var(--background);
            box-shadow: 0 2px 10px var(--shadow);
            z-index: 1000;
            padding: 10px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary-green);
        }

        .search-bar {
            flex: 1;
            max-width: 400px;
            margin: 0 20px;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 20px;
            outline: none;
        }

        .cart-icon {
            position: relative;
            font-size: 24px;
            cursor: pointer;
        }

        .cart-badge {
            position: absolute;
            top: -5px;
            right: -10px;
            background: var(--secondary-yellow);
            color: var(--text-dark);
            border-radius: 50%;
            padding: 2px 6px;
            font-size: 12px;
        }

        .login-btn {
            background: var(--accent-dark-green);
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 20px;
            cursor: pointer;
            margin-left: 10px;
        }

        /* Hero */
        .hero {
            background: url('https://source.unsplash.com/featured/?food,filipino') center/cover;
            height: 50vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            color: white;
            position: relative;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.5);
        }

        .hero h1, .hero p {
            position: relative;
            z-index: 1;
        }

        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }

        .hero p {
            font-size: 1.2rem;
            margin-bottom: 20px;
        }

        .cta-btn {
            background: var(--primary-green);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 20px;
            font-size: 1.1rem;
            cursor: pointer;
            box-shadow: 0 4px 15px var(--shadow);
            transition: all 0.3s;
        }

        .cta-btn:hover {
            background: var(--accent-dark-green);
            box-shadow: 0 6px 20px var(--shadow);
        }

        /* Categories */
        .categories {
            display: flex;
            overflow-x: auto;
            padding: 20px;
            gap: 10px;
            background: var(--background);
            border-bottom: 1px solid #eee;
        }

        .category-tab {
            background: white;
            border: 1px solid #ddd;
            padding: 10px 20px;
            border-radius: 20px;
            cursor: pointer;
            white-space: nowrap;
            transition: all 0.3s;
        }

        .category-tab.active {
            background: var(--primary-green);
            color: white;
        }

        /* Menu */
        .menu {
            padding: 20px;
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
        }

        .menu-item {
            background: white;
            border-radius: 20px;
            box-shadow: 0 4px 10px var(--shadow);
            overflow: hidden;
            transition: transform 0.3s;
        }

        .menu-item:hover {
            transform: translateY(-5px);
        }

        .menu-item img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .menu-details {
            padding: 15px;
        }

        .menu-name {
            font-weight: 600;
            font-size: 1.2rem;
            margin-bottom: 5px;
        }

        .menu-desc {
            color: #666;
            margin-bottom: 10px;
        }

        .price-badge {
            background: var(--secondary-yellow);
            color: var(--text-dark);
            padding: 5px 10px;
            border-radius: 20px;
            font-weight: 600;
            display: inline-block;
            margin-bottom: 10px;
        }

        .quantity-selector {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 10px;
        }

        .qty-btn {
            background: #eee;
            border: none;
            padding: 5px 10px;
            border-radius: 50%;
            cursor: pointer;
        }

        .add-to-cart {
            background: var(--primary-green);
            color: white;
            border: none;
            padding: 10px;
            border-radius: 20px;
            width: 100%;
            cursor: pointer;
            transition: background 0.3s;
        }

        .add-to-cart:hover {
            background: var(--accent-dark-green);
        }

        .best-seller {
            position: absolute;
            top: 10px;
            left: 10px;
            background: var(--secondary-yellow);
            color: var(--text-dark);
            padding: 5px 10px;
            border-radius: 10px;
            font-size: 0.8rem;
        }

        /* Cart */
        .cart-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: var(--primary-green);
            color: white;
            border: none;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            font-size: 24px;
            cursor: pointer;
            box-shadow: 0 4px 15px var(--shadow);
            z-index: 1000;
        }

        .cart-drawer {
            position: fixed;
            top: 0;
            right: -400px;
            width: 400px;
            height: 100%;
            background: white;
            box-shadow: -2px 0 10px var(--shadow);
            transition: right 0.3s;
            z-index: 1001;
            padding: 20px;
            overflow-y: auto;
        }

        .cart-drawer.open {
            right: 0;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            padding: 10px;
            border-bottom: 1px solid #eee;
        }

        .cart-total {
            font-weight: 600;
            margin-top: 20px;
        }

        .checkout-btn {
            background: var(--primary-green);
            color: white;
            border: none;
            padding: 15px;
            width: 100%;
            border-radius: 20px;
            cursor: pointer;
            margin-top: 20px;
        }

        .delivery-form {
            margin-top: 20px;
        }

        .delivery-form input {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ddd;
            border-radius: 10px;
        }

        .payment-options {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }

        .payment-option {
            flex: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 10px;
            text-align: center;
            cursor: pointer;
        }

        .payment-option.selected {
            border-color: var(--primary-green);
            background: var(--hover-light-green);
        }

        /* Dark Mode Toggle */
        .dark-mode-toggle {
            position: fixed;
            top: 20px;
            right: 20px;
            background: var(--secondary-yellow);
            border: none;
            padding: 10px;
            border-radius: 50%;
            cursor: pointer;
        }

        /* Toast */
        .toast {
            position: fixed;
            bottom: 100px;
            left: 50%;
            transform: translateX(-50%);
            background: var(--primary-green);
            color: white;
            padding: 10px 20px;
            border-radius: 20px;
            opacity: 0;
            transition: opacity 0.3s;
        }

        .toast.show {
            opacity: 1;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .menu {
                grid-template-columns: 1fr;
            }
            .cart-drawer {
                width: 100%;
                right: -100%;
            }
        }
    </style>
</head>
<body>
    <button class="dark-mode-toggle" onclick="toggleDarkMode()">🌙</button>
    <header>
        <div class="logo">Budong Cravings</div>
        <input type="text" class="search-bar" placeholder="Search silog, sisig, chicken…" oninput="filterMenu()">
        <div class="cart-icon" onclick="toggleCart()">
            🛒
            <span class="cart-badge" id="cart-count">0</span>
        </div>
        <button class="login-btn">Login</button>
    </header>

    <section class="hero">
        <h1>Masarap. Sulit. Araw-araw — Budong Cravings</h1>
        <p>Premium meals, affordable presyo.</p>
        <button class="cta-btn" onclick="scrollToMenu()">Order Now</button>
    </section>

    <div class="categories">
        <div class="category-tab active" onclick="filterCategory('all')">All</div>
        <div class="category-tab" onclick="filterCategory('silog')">Silog Meals</div>
        <div class="category-tab" onclick="filterCategory('ala-carte')">Ala Carte</div>
        <div class="category-tab" onclick="filterCategory('best-sellers')">Best Sellers</div>
        <div class="category-tab" onclick="filterCategory('snacks')">Snacks</div>
        <div class="category-tab" onclick="filterCategory('drinks')">Drinks</div>
    </div>

    <div class="menu" id="menu-container">
        <!-- Menu items will be populated by JS -->
    </div>

    <button class="cart-btn" onclick="toggleCart()">🛒</button>

    <div class="cart-drawer" id="cart-drawer">
        <h2>Your Cart</h2>
        <div id="cart-items"></div>
        <div class="cart-total">Subtotal: ₱0</div>
        <div>Delivery Fee: ₱50</div>
        <div>Service Fee: ₱20</div>
        <div>Total: ₱70</div>
        <button class="checkout-btn" onclick="checkout()">Checkout</button>
        <div class="delivery-form">
            <input type="text" placeholder="Name">
            <input type="tel" placeholder="Phone">
            <input type="text" placeholder="Address">
        </div>
        <div class="payment-options">
            <div class="payment-option selected" onclick="selectPayment(this)">COD</div>
            <div class="payment-option" onclick="selectPayment(this)">GCash</div>
            <div class="payment-option" onclick="selectPayment(this)">Maya</div>
        </div>
    </div>

    <div class="toast" id="toast">Added to cart!</div>

    <script>
        let cart = JSON.parse(localStorage.getItem('cart')) || [];
        let menuData = [
            // Silog Meals
            { id: 1, name: 'Sisigsilog', price: 149, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?sisig', category: 'silog', bestSeller: true },
            { id: 2, name: 'Chicksilog', price: 149, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?chicken', category: 'silog' },
            { id: 3, name: 'Tapsilog', price: 149, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?beef', category: 'silog' },
            { id: 4, name: 'Liemposilog', price: 149, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?pork', category: 'silog' },
            { id: 5, name: 'Porksilog', price: 149, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?pork', category: 'silog' },
            { id: 6, name: 'Bangsilog', price: 149, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?fish', category: 'silog' },
            { id: 7, name: 'Tosilog', price: 120, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?tocino', category: 'silog' },
            { id: 8, name: 'Longsilog', price: 120, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?longanisa', category: 'silog' },
            { id: 9, name: 'Hotsilog', price: 120, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?hotdog', category: 'silog' },
            { id: 10, name: 'Hamsilog', price: 120, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?ham', category: 'silog' },
            { id: 11, name: 'Cornsilog', price: 120, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?corn', category: 'silog' },
            { id: 12, name: 'Spamsilog', price: 120, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?spam', category: 'silog' },
            { id: 13, name: 'Lumpiasilog', price: 120, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?lumpia', category: 'silog' },
            { id: 14, name: 'Siomaisilog', price: 120, desc: 'Served with garlic rice & egg', img: 'https://source.unsplash.com/featured/?siomai', category: 'silog' },
            // Ala Carte
            { id: 15, name: 'Sizzling Sisig', price: 170, desc: 'Hot and sizzling', img: 'https://source.unsplash.com/featured/?sisig', category: 'ala-carte', bestSeller: true },
            { id: 16, name: 'Sizzling Hotdog', price: 149, desc: 'Hot and sizzling', img: 'https://source.unsplash.com/featured/?hotdog', category: 'ala-carte' },
            { id: 17, name: 'Sizzling Isaw', price: 149, desc: 'Hot and sizzling', img: 'https://source.unsplash.com/featured/?isaw', category: 'ala-carte' },
            { id: 18, name: 'Sizzling Corn', price: 139, desc: 'Hot and sizzling', img: 'https://source.unsplash.com/featured/?corn', category: 'ala-carte' },
            { id: 19, name: 'Sizzling Tofu', price: 149, desc: 'Hot and sizzling', img: 'https://source.unsplash.com/featured/?tofu', category: 'ala-carte' },
            { id: 20, name: 'Fried Liempo w/ Fries', price: 149, desc: 'Crispy and delicious', img: 'https://source.unsplash.com/featured/?liempo', category: 'ala-carte' },
            { id: 21, name: 'Fried Chicken w/ Fries', price: 149, desc: 'Crispy and delicious', img: 'https://source.unsplash.com/featured/?chicken', category: 'ala-carte' },
            { id: 22, name: 'Fried Porkchop w/ Fries', price: 149, desc: 'Crispy and delicious', img: 'https://source.unsplash.com/featured/?porkchop', category: 'ala-carte'
