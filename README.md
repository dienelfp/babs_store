# babs_store
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Babs-Store - Votre Boutique en Ligne</title>
    <style>
        :root {
            --primary-color: #3a86ff;
            --secondary-color: #ff006e;
            --background-color: #f9f2f9d6;
            --text-color: #333;
            --light-gray: #e9ecef;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: var(--background-color);
            color: var(--text-color);
            line-height: 1.6;
        }
        
        header {
            background-color: white;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 5%;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--primary-color);
        }
        
        .logo span {
            color: var(--secondary-color);
        }
        
        .nav-links {
            display: flex;
            list-style: none;
        }
        
        .nav-links li {
            margin-left: 2rem;
        }
        
        .nav-links a {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 500;
            transition: color 0.3s;
        }
        
        .nav-links a:hover {
            color: var(--primary-color);
        }
        
        .cart-icon {
            font-size: 1.2rem;
            position: relative;
            cursor: pointer;
            padding: 0.5rem;
            border-radius: 5px;
            transition: background-color 0.3s;
        }
        
        .cart-icon:hover {
            background-color: var(--light-gray);
        }
        
        .cart-count {
            position: absolute;
            top: -5px;
            right: -5px;
            background-color: var(--secondary-color);
            color: white;
            font-size: 0.7rem;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .hero {
            background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), 
            color: white;
            text-align: center;
            padding: 5rem 1rem;
        }
        
        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }
        
        .hero p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .btn {
            display: inline-block;
            background-color: var(--primary-color);
            color: white;
            padding: 0.8rem 1.5rem;
            border-radius: 5px;
            text-decoration: none;
            font-weight: 500;
            transition: background-color 0.3s;
            border: none;
            cursor: pointer;
        }
        
        .btn:hover {
            background-color: #2a75e6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem 1rem;
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 2rem;
            font-size: 2rem;
            color: var(--primary-color);
        }
        
        .products {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 2rem;
        }
        
        .product-card {
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s;
        }
        
        .product-card:hover {
            transform: translateY(-10px);
        }
        
        .product-img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            background-color: var(--light-gray);
        }
        
        .product-info {
            padding: 1.5rem;
        }
        
        .product-title {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
        }
        
        .product-price {
            font-size: 1.3rem;
            color: var(--secondary-color);
            font-weight: 700;
            margin-bottom: 1rem;
        }
        
        .product-desc {
            color: #666;
            margin-bottom: 1rem;
            font-size: 0.9rem;
        }
        
        .add-to-cart {
            width: 100%;
            padding: 0.8rem;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 500;
            transition: background-color 0.3s;
        }
        
        .add-to-cart:hover {
            background-color: #2a75e6;
        }
        
        .categories {
            display: flex;
            justify-content: center;
            gap: 1rem;
            flex-wrap: wrap;
            margin-bottom: 2rem;
        }
        
        .category {
            background-color: var(--light-gray);
            padding: 0.5rem 1.5rem;
            border-radius: 50px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .category:hover, .category.active {
            background-color: var(--primary-color);
            color: white;
        }
        
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }
        
        .feature {
            text-align: center;
            padding: 2rem 1rem;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
        }
        
        .feature-icon {
            font-size: 2.5rem;
            color: var(--primary-color);
            margin-bottom: 1rem;
        }
        
        .feature h3 {
            margin-bottom: 0.5rem;
        }
        
        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            z-index: 1000;
        }
        
        .modal-content {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: white;
            border-radius: 15px;
            padding: 2rem;
            max-width: 500px;
            width: 90%;
            max-height: 80vh;
            overflow-y: auto;
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }
        
        .close-btn {
            background: none;
            border: none;
            font-size: 2rem;
            cursor: pointer;
            color: #999;
        }
        
        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
            border-bottom: 1px solid #eee;
        }
        
        .cart-total {
            font-size: 1.5rem;
            font-weight: bold;
            text-align: center;
            margin: 1.5rem 0;
            color: var(--primary-color);
        }
        
        .checkout-btn {
            width: 100%;
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: 500;
            cursor: pointer;
            margin-bottom: 1rem;
        }
        
        .payment-methods {
            display: grid;
            gap: 1rem;
            margin: 1.5rem 0;
        }
        
        .payment-option {
            display: flex;
            align-items: center;
            padding: 1rem;
            border: 2px solid #eee;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .payment-option:hover {
            border-color: var(--primary-color);
            background-color: #f8f9ff;
        }
        
        .payment-option.selected {
            border-color: var(--primary-color);
            background-color: #f8f9ff;
        }
        
        .payment-logo {
            width: 50px;
            height: 50px;
            border-radius: 8px;
            margin-right: 1rem;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: white;
            font-size: 1.2rem;
        }
        
        .wave-logo {
            background: linear-gradient(45deg, #FF6B6B, #FF8E8E);
        }
        
        .orange-logo {
            background: linear-gradient(45deg, #FF8C00, #FFA500);
        }
        
        .payment-details {
            display: none;
            margin-top: 1rem;
            padding: 1.5rem;
            background-color: #f8f9ff;
            border-radius: 10px;
            border: 1px solid #e0e7ff;
        }
        
        .payment-details.active {
            display: block;
        }
        
        .phone-display {
            text-align: center;
            font-size: 1.3rem;
            font-weight: bold;
            color: var(--primary-color);
            margin: 1rem 0;
            padding: 0.8rem;
            background-color: white;
            border-radius: 8px;
            border: 2px solid var(--primary-color);
        }
        
        .payment-instructions {
            background-color: #e8f4fd;
            padding: 1.5rem;
            border-radius: 10px;
            margin: 1rem 0;
            border-left: 4px solid var(--primary-color);
        }
        
        .payment-instructions h4 {
            margin-bottom: 1rem;
            color: var(--primary-color);
        }
        
        .payment-instructions ol {
            margin-left: 1rem;
        }
        
        .payment-instructions li {
            margin-bottom: 0.5rem;
        }
        
        .confirm-payment-btn {
            width: 100%;
            background: linear-gradient(45deg, #00d4aa, #00b894);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 10px;
            font-size: 1.1rem;
            font-weight: 500;
            cursor: pointer;
            margin-top: 1rem;
        }
        
        .success-message {
            display: none;
            text-align: center;
            color: #00b894;
            margin: 1rem 0;
        }
        
        .invoice-section {
            margin-top: 2rem;
            padding: 1.5rem;
            background-color: #f8f9fa;
            border-radius: 10px;
            border: 1px solid #dee2e6;
        }
        
        .invoice-header {
            text-align: center;
            margin-bottom: 1.5rem;
            color: var(--primary-color);
        }
        
        .invoice-details {
            display: grid;
            gap: 0.5rem;
            margin-bottom: 1rem;
        }
        
        .invoice-item {
            display: flex;
            justify-content: space-between;
            padding: 0.5rem 0;
            border-bottom: 1px solid #eee;
        }
        
        .invoice-total {
            display: flex;
            justify-content: space-between;
            font-weight: bold;
            font-size: 1.2rem;
            padding: 1rem 0;
            border-top: 2px solid var(--primary-color);
            color: var(--primary-color);
        }
        
        .download-invoice-btn {
            width: 100%;
            background-color: var(--secondary-color);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 8px;
            font-weight: 500;
            cursor: pointer;
            margin-top: 1rem;
        }
        
        footer {
            background-color: rgb(194, 160, 160);
            color: white;
            padding: 3rem 0;
        }
        
        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 1rem;
        }
        
        .footer-title {
            font-size: 1.2rem;
            margin-bottom: 1rem;
            color: var(--primary-color);
        }
        
        .footer-links {
            list-style: none;
        }
        
        .footer-links li {
            margin-bottom: 0.5rem;
        }
        
        .footer-links a {
            color: rgb(201, 25, 25);
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-links a:hover {
            color: rgba(231, 14, 14, 0.301);
        }
        
        .social-icons {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }
        
        .social-icons div {
            width: 40px;
            height: 40px;
            background-color: #444;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .social-icons div:hover {
            background-color: var(--primary-color);
        }
        
        .copyright {
            text-align: center;
            margin-top: 2rem;
            color: #aaa;
        }
        
        @media (max-width: 768px) {
            .navbar {
                flex-direction: column;
                padding: 1rem;
            }
            
            .nav-links {
                margin-top: 1rem;
                width: 100%;
                justify-content: space-between;
            }
            
            .nav-links li {
                margin-left: 0;
            }
            
            .hero h1 {
                font-size: 2rem;
            }
            
            .hero p {
                font-size: 1rem;
            }
            
            .modal-content {
                width: 95%;
                padding: 1rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <nav class="navbar">
            <div class="logo">Babs<span>-Store</span></div>
            <ul class="nav-links">
                <li><a href="#accueil">Accueil</a></li>
                <li><a href="#produits">Produits</a></li>
                <li><a href="#apropos">À propos</a></li>
                <li><a href="#contact">Contact</a></li>
                <li class="cart-icon" onclick="openCart()">
                    🛒 <span class="cart-count" id="cartCount">0</span>
                </li>
            </ul>
        </nav>
    </header>

    <section class="hero" id="accueil">
        <h1>Bienvenue chez Babs-Store</h1>
        <p>Découvrez notre collection exceptionnelle de produits de qualité à des prix imbattables.</p>
        <a href="#produits" class="btn">Voir nos produits</a>
    </section>

    <div class="container" id="produits">
        <h2 class="section-title">Nos Produits</h2>
        
        <div class="categories">
            <div class="category active">Tous</div>
            <div class="category">Vêtements</div>
            <div class="category">Accessoires</div>
            <div class="category">Chaussures</div>
        </div>
        
        <div class="products">
            <div class="product-card" data-category="chaussures">
                <img src="https://images.unsplash.com/photo-1549298916-b41d501d3772?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=400&q=80" alt="Air Force One" class="product-img">
                <div class="product-info">
                    <h3 class="product-title">Chaussure Air Force One</h3>
                    <p class="product-price">10.000 FCFA</p>
                    <p class="product-desc">Originale, confortable et élégant.</p>
                    <button class="add-to-cart" onclick="addToCart(1, 'Chaussure Air Force One', 10000)">Ajouter au panier</button>
                </div>
            </div>
            
            <div class="product-card" data-category="accessoires">
                <img src="https://images.unsplash.com/photo-1553062407-98eeb64c6a62?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=400&q=80" alt="Sac à dos urbain" class="product-img">
                <div class="product-info">
                    <h3 class="product-title">Sac à dos urbain</h3>
                    <p class="product-price">10.000 FCFA</p>
                    <p class="product-desc">Sac à dos élégant et spacieux, parfait pour la ville et les courts voyages.</p>
                    <button class="add-to-cart" onclick="addToCart(2, 'Sac à dos urbain', 10000)">Ajouter au panier</button>
                </div>
            </div>
            
            <div class="product-card" data-category="vetements">
                <img src="https://www.intersport.fr/maillot_de_football_homme_real_madrid_third_24_25-adidas-p-IY1763~7DO/" alt="Maillot Real Madrid" class="product-img">
                <div class="product-info">
                    <h3 class="product-title">Maillot Real Madrid</h3>
                    <p class="product-price">8.000 FCFA</p>
                    <p class="product-desc">Maillot original taille M, L, XL, XXL</p>
                    <button class="add-to-cart" onclick="addToCart(3, 'Maillot Real Madrid', 8000)">Ajouter au panier</button>
                </div>
            </div>
            
            <div class="product-card" data-category="chaussures">
                <img src="https://images.unsplash.com/photo-1560769629-975ec94e6a86?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=400&q=80" alt="Adidas Campus" class="product-img">
                <div class="product-info">
                    <h3 class="product-title">Adidas Campus</h3>
                    <p class="product-price">13.000 FCFA</p>
                    <p class="product-desc">Pointures 37, 40, 41, 42, 43, 44, 45.</p>
                    <button class="add-to-cart" onclick="addToCart(4, 'Adidas Campus', 13000)">Ajouter au panier</button>
                </div>
            </div>
            
            <div class="product-card" data-category="accessoires">
                <img src="https://images.unsplash.com/photo-1523275335684-37898b6baf30?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=400&q=80" alt="Montre élégante" class="product-img">
                <div class="product-info">
                    <h3 class="product-title">Montre élégante</h3>
                    <p class="product-price">10.000 FCFA</p>
                    <p class="product-desc">Montre analogique au design intemporel, bracelet en cuir véritable.</p>
                    <button class="add-to-cart" onclick="addToCart(5, 'Montre élégante', 10000)">Ajouter au panier</button>
                </div>
            </div>
            
            <div class="product-card" data-category="vetements">
                <img src="https://images.unsplash.com/photo-1542272604-787c3835535d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=400&q=80" alt="Jeans premium" class="product-img">
                <div class="product-info">
                    <h3 class="product-title">Jeans premium</h3>
                    <p class="product-price">6.000 FCFA</p>
                    <p class="product-desc">Jeans de qualité supérieure, coupe moderne et confortable.</p>
                    <button class="add-to-cart" onclick="addToCart(6, 'Jeans premium', 6000)">Ajouter au panier</button>
                </div>
            </div>
        </div>
    </div>

    <div class="container" id="apropos">
        <h2 class="section-title">Pourquoi nous choisir</h2>
        <div class="features">
            <div class="feature">
                <div class="feature-icon">🚚</div>
                <h3>Livraison rapide</h3>
                <p>Livraison  gratuit en moins de 48h jours ouvrables partout au Sénégal avec la poste.</p>
            </div>
            
            <div class="feature">
                <div class="feature-icon">🛡️</div>
                <h3>Garantie qualité</h3>
                <p>Tous nos produits sont garantis .</p>
            </div>
            
            <div class="feature">
                <div class="feature-icon">💰</div>
                <h3>Prix imbattables</h3>
                <p>Nous vous offrons les meilleurs produits aux meilleurs prix.</p>
            </div>
            
            <div class="feature">
                <div class="feature-icon">📱</div>
                <h3>Paiement mobile</h3>
                <p>Payez facilement avec Wave ou Orange Money.</p>
            </div>
        </div>
    </div>

    <!-- Cart Modal -->
    <div class="modal" id="cartModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Votre Panier</h2>
                <button class="close-btn" onclick="closeCart()">&times;</button>
            </div>
            <div id="cartItems"></div>
            <div class="cart-total" id="cartTotal">Total: 0 FCFA</div>
            <button class="checkout-btn btn" onclick="openPayment()">Procéder au paiement</button>
        </div>
    </div>

    <!-- Payment Modal -->
    <div class="modal" id="paymentModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Paiement Sécurisé</h2>
                <button class="close-btn" onclick="closePayment()">&times;</button>
            </div>
            
            <div class="payment-methods">
                <div class="payment-option" onclick="selectPayment('wave')">
                    <div class="payment-logo wave-logo">WAVE</div>
                    <div>
                        <h3>Wave</h3>
                        <p>Paiement mobile sécurisé et rapide</p>
                    </div>
                </div>
                
                <div class="payment-option" onclick="selectPayment('orange')">
                    <div class="payment-logo orange-logo">OM</div>
                    <div>
                        <h3>Orange Money</h3>
                        <p>Paiement mobile Orange</p>
                    </div>
                </div>
            </div>

            <div class="payment-details" id="waveDetails">
                <h3>🌊 Paiement Wave</h3>
                <div class="phone-display">📱 77-850-13-15</div>
                <div class="payment-instructions">
                    <h4>Instructions de paiement:</h4>
                    <ol>
                        <li>Ouvrez votre application <strong>Wave</strong></li>
                        <li>Sélectionnez <strong>"Envoyer de l'argent"</strong></li>
                        <li>Entrez le numéro: <strong>778501315</strong></li>
                        <li>Montant à envoyer: <span id="waveAmount">0 FCFA</span></li>
                        <li>Confirmez le paiement dans l'application</li>
                        <li>Cliquez sur "J'ai payé" ci-dessous</li>
                    </ol>
                </div>
                <button class="confirm-payment-btn" onclick="confirmPayment('wave')">
                    ✅ J'ai effectué le paiement Wave
                </button>
            </div>

            <div class="payment-details" id="orangeDetails">
                <h3>🍊 Paiement Orange Money</h3>
                <div class="phone-display">📱 77-850-13-15</div>
                <div class="payment-instructions">
                    <h4>Instructions de paiement:</h4>
                    <ol>
                        <li>Composez <strong>#144#</strong> sur votre téléphone</li>
                        <li>Sélectionnez <strong>"Transfert d'argent"</strong></li>
                        <li>Entrez le numéro: <strong>778501315</strong></li>
                        <li>Montant à envoyer: <span id="orangeAmount">0 FCFA</span></li>
                        <li>Confirmez avec votre <strong>code PIN Orange Money</strong></li>
                        <li>Cliquez sur "J'ai payé" ci-dessous</li>
                    </ol>
                </div>
                <button class="confirm-payment-btn" onclick="confirmPayment('orange')">
                    ✅ J'ai effectué le paiement Orange Money
                </button>
            </div>

            <div class="success-message" id="successMessage">
                <h3>
