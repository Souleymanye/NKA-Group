<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NKA Group | Excellence Immobilière & Automobile</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700;800&family=Playfair+Display:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --gold: #D4AF37;
            --dark-gold: #B8860B;
            --charcoal: #0a0a0a;
            --dark-gray: #1a1a1a;
            --light-gray: #f8f8f8;
            --white: #ffffff;
            --transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
            --shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
            --gradient: linear-gradient(135deg, #0a0a0a 0%, #1a1a1a 100%);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            color: var(--white);
            background: var(--charcoal);
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* Header immersif */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            background: rgba(10, 10, 10, 0.9);
            backdrop-filter: blur(20px);
            padding: 20px 0;
            transition: var(--transition);
            border-bottom: 1px solid rgba(212, 175, 55, 0.1);
        }

        header.scrolled {
            padding: 15px 0;
            background: rgba(10, 10, 10, 0.98);
            box-shadow: var(--shadow);
        }

        .nav-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 40px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        /* Logo personnalisé */
        .logo-container {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo-badge {
            width: 50px;
            height: 50px;
            background: var(--gold);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Montserrat', sans-serif;
            font-weight: 800;
            font-size: 1.4rem;
            color: var(--charcoal);
            position: relative;
            overflow: hidden;
        }

        .logo-badge:after {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, transparent, rgba(255,255,255,0.2), transparent);
            transform: translateX(-100%);
        }

        .logo-container:hover .logo-badge:after {
            animation: shine 1s ease;
        }

        .logo-text {
            font-family: 'Montserrat', sans-serif;
            font-weight: 700;
            font-size: 1.8rem;
            letter-spacing: 2px;
            background: linear-gradient(45deg, var(--gold), #fff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .logo-subtitle {
            font-size: 0.7rem;
            color: rgba(255,255,255,0.7);
            letter-spacing: 3px;
            margin-top: -5px;
        }

        /* Navigation immersive */
        .nav-links {
            display: flex;
            gap: 40px;
            align-items: center;
        }

        .nav-link {
            color: rgba(255,255,255,0.8);
            text-decoration: none;
            font-weight: 500;
            font-size: 0.9rem;
            letter-spacing: 1px;
            text-transform: uppercase;
            position: relative;
            padding: 10px 0;
            transition: var(--transition);
        }

        .nav-link:before {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--gold);
            transition: var(--transition);
        }

        .nav-link:hover {
            color: var(--white);
        }

        .nav-link:hover:before {
            width: 100%;
        }

        .nav-link.active {
            color: var(--gold);
        }

        .nav-link.active:before {
            width: 100%;
        }

        .nav-cta {
            background: linear-gradient(135deg, var(--gold), var(--dark-gold));
            color: var(--charcoal);
            padding: 12px 30px;
            border-radius: 30px;
            font-weight: 600;
            text-decoration: none;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .nav-cta:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(212, 175, 55, 0.3);
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: var(--white);
            font-size: 1.5rem;
            cursor: pointer;
            z-index: 1001;
        }

        /* Hero section immersive */
        .hero {
            height: 100vh;
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: center;
            padding-top: 100px;
        }

        .hero-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(rgba(10,10,10,0.9), rgba(10,10,10,0.7)),
                        url('https://images.unsplash.com/photo-1613490493576-7fde63acd811?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            transform: scale(1.1);
            animation: zoomIn 20s infinite alternate;
        }

        .hero-content {
            position: relative;
            z-index: 2;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 40px;
        }

        .hero-title {
            font-family: 'Playfair Display', serif;
            font-size: 4.5rem;
            font-weight: 700;
            line-height: 1.1;
            margin-bottom: 30px;
            opacity: 0;
            transform: translateY(50px);
            animation: fadeUp 1s ease 0.3s forwards;
        }

        .hero-subtitle {
            font-size: 1.3rem;
            color: rgba(255,255,255,0.9);
            max-width: 600px;
            margin-bottom: 50px;
            opacity: 0;
            transform: translateY(50px);
            animation: fadeUp 1s ease 0.6s forwards;
        }

        .hero-buttons {
            display: flex;
            gap: 20px;
            opacity: 0;
            transform: translateY(50px);
            animation: fadeUp 1s ease 0.9s forwards;
        }

        .hero-btn {
            padding: 18px 40px;
            font-size: 1rem;
            font-weight: 600;
            text-decoration: none;
            border-radius: 5px;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .btn-gold {
            background: linear-gradient(135deg, var(--gold), var(--dark-gold));
            color: var(--charcoal);
        }

        .btn-gold:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(212, 175, 55, 0.4);
        }

        .btn-outline {
            background: transparent;
            color: var(--white);
            border: 2px solid rgba(255,255,255,0.3);
        }

        .btn-outline:hover {
            border-color: var(--gold);
            color: var(--gold);
            transform: translateY(-5px);
        }

        /* Section Services immersive */
        .services {
            padding: 150px 0;
            position: relative;
            background: var(--gradient);
        }

        .section-title {
            text-align: center;
            margin-bottom: 80px;
            position: relative;
        }

        .section-title h2 {
            font-family: 'Playfair Display', serif;
            font-size: 3.5rem;
            margin-bottom: 20px;
            position: relative;
            display: inline-block;
        }

        .section-title h2:after {
            content: '';
            position: absolute;
            width: 100px;
            height: 3px;
            background: var(--gold);
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
        }

        .section-title p {
            font-size: 1.2rem;
            color: rgba(255,255,255,0.7);
            max-width: 600px;
            margin: 0 auto;
        }

        /* Grille de services immersive */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 40px;
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 40px;
        }

        .service-card {
            background: rgba(30, 30, 30, 0.6);
            border-radius: 20px;
            padding: 50px 40px;
            transition: var(--transition);
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(212, 175, 55, 0.1);
            backdrop-filter: blur(10px);
        }

        .service-card:before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(212,175,55,0.1), transparent);
            opacity: 0;
            transition: var(--transition);
        }

        .service-card:hover {
            transform: translateY(-20px);
            border-color: rgba(212, 175, 55, 0.3);
            box-shadow: var(--shadow);
        }

        .service-card:hover:before {
            opacity: 1;
        }

        .service-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, var(--gold), var(--dark-gold));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            margin-bottom: 30px;
            position: relative;
            z-index: 1;
        }

        .service-card h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            margin-bottom: 20px;
            position: relative;
            z-index: 1;
        }

        .service-card p {
            color: rgba(255,255,255,0.8);
            margin-bottom: 30px;
            position: relative;
            z-index: 1;
        }

        .service-features {
            list-style: none;
            position: relative;
            z-index: 1;
        }

        .service-features li {
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
            color: rgba(255,255,255,0.9);
        }

        .service-features i {
            color: var(--gold);
            font-size: 0.9rem;
        }

        /* Section Immobilier détaillée */
        .real-estate {
            padding: 150px 0;
            background: linear-gradient(rgba(10,10,10,0.95), rgba(10,10,10,0.95)),
                        url('https://images.unsplash.com/photo-1567496898669-ee935f003f30?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');
            background-size: cover;
            background-attachment: fixed;
            position: relative;
        }

        .real-estate-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 40px;
            text-align: center;
        }

        .real-estate h2 {
            font-family: 'Playfair Display', serif;
            font-size: 3.5rem;
            margin-bottom: 20px;
            color: var(--gold);
        }

        .real-estate p {
            font-size: 1.2rem;
            color: rgba(255,255,255,0.9);
            max-width: 800px;
            margin: 0 auto 50px;
        }

        .properties-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 60px;
        }

        .property-card {
            background: rgba(30, 30, 30, 0.8);
            border-radius: 15px;
            overflow: hidden;
            transition: var(--transition);
            border: 1px solid rgba(212, 175, 55, 0.1);
        }

        .property-card:hover {
            transform: translateY(-10px);
            border-color: var(--gold);
            box-shadow: 0 20px 40px rgba(0,0,0,0.4);
        }

        .property-image {
            height: 250px;
            background: linear-gradient(45deg, #222, #333);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: var(--gold);
        }

        .property-content {
            padding: 30px;
        }

        .property-content h4 {
            font-size: 1.3rem;
            margin-bottom: 15px;
            color: var(--white);
        }

        .property-content p {
            color: rgba(255,255,255,0.7);
            font-size: 0.9rem;
            margin-bottom: 20px;
        }

        /* Section Contact immersive */
        .contact {
            padding: 150px 0;
            background: var(--gradient);
        }

        .contact-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 40px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 80px;
        }

        .contact-info {
            display: flex;
            flex-direction: column;
            gap: 40px;
        }

        .contact-item {
            display: flex;
            align-items: flex-start;
            gap: 25px;
            transition: var(--transition);
            padding: 20px;
            border-radius: 15px;
            background: rgba(30, 30, 30, 0.6);
        }

        .contact-item:hover {
            background: rgba(212, 175, 55, 0.1);
            transform: translateX(10px);
        }

        .contact-icon {
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, var(--gold), var(--dark-gold));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            flex-shrink: 0;
        }

        .contact-details h3 {
            font-size: 1.3rem;
            margin-bottom: 10px;
            color: var(--gold);
        }

        .contact-details p {
            color: rgba(255,255,255,0.9);
            line-height: 1.8;
        }

        .contact-form {
            background: rgba(30, 30, 30, 0.6);
            padding: 50px;
            border-radius: 20px;
            border: 1px solid rgba(212, 175, 55, 0.1);
            backdrop-filter: blur(10px);
        }

        .form-group {
            margin-bottom: 30px;
        }

        .form-group label {
            display: block;
            margin-bottom: 10px;
            color: var(--gold);
            font-weight: 500;
            letter-spacing: 1px;
        }

        .form-control {
            width: 100%;
            padding: 18px 20px;
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 10px;
            color: var(--white);
            font-size: 1rem;
            transition: var(--transition);
        }

        .form-control:focus {
            outline: none;
            border-color: var(--gold);
            background: rgba(255,255,255,0.08);
        }

        textarea.form-control {
            min-height: 150px;
            resize: vertical;
        }

        /* Footer immersif */
        footer {
            background: #000;
            padding: 100px 0 30px;
            border-top: 1px solid rgba(212, 175, 55, 0.1);
        }

        .footer-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 40px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 60px;
            margin-bottom: 60px;
        }

        .footer-logo {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .footer-logo .logo-text {
            font-size: 2rem;
        }

        .footer-logo p {
            color: rgba(255,255,255,0.7);
            margin-top: 20px;
        }

        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 30px;
        }

        .social-link {
            width: 50px;
            height: 50px;
            background: rgba(255,255,255,0.05);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--white);
            text-decoration: none;
            transition: var(--transition);
        }

        .social-link:hover {
            background: var(--gold);
            color: var(--charcoal);
            transform: translateY(-5px);
        }

        .footer-heading {
            color: var(--gold);
            font-size: 1.2rem;
            margin-bottom: 30px;
            font-family: 'Playfair Display', serif;
        }

        .footer-links ul {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 15px;
        }

        .footer-links a {
            color: rgba(255,255,255,0.7);
            text-decoration: none;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .footer-links a:hover {
            color: var(--gold);
            transform: translateX(5px);
        }

        .copyright {
            text-align: center;
            padding-top: 30px;
            border-top: 1px solid rgba(255,255,255,0.1);
            color: rgba(255,255,255,0.5);
            font-size: 0.9rem;
        }

        /* Animations */
        @keyframes fadeUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes zoomIn {
            to {
                transform: scale(1);
            }
        }

        @keyframes shine {
            to {
                transform: translateX(100%);
            }
        }

        /* Responsive Design */
        @media (max-width: 992px) {
            .hero-title {
                font-size: 3.5rem;
            }
            
            .section-title h2 {
                font-size: 2.8rem;
            }
            
            .services-grid {
                grid-template-columns: 1fr;
                padding: 0 20px;
            }
        }

        @media (max-width: 768px) {
            .mobile-menu-btn {
                display: block;
            }
            
            .nav-links {
                position: fixed;
                top: 0;
                right: -100%;
                width: 100%;
                height: 100vh;
                background: rgba(10,10,10,0.98);
                flex-direction: column;
                justify-content: center;
                gap: 40px;
                transition: var(--transition);
                backdrop-filter: blur(20px);
            }
            
            .nav-links.active {
                right: 0;
            }
            
            .hero-title {
                font-size: 2.8rem;
            }
            
            .hero-subtitle {
                font-size: 1.1rem;
            }
            
            .hero-buttons {
                flex-direction: column;
            }
            
            .nav-container,
            .hero-content,
            .contact-container {
                padding: 0 20px;
            }
            
            .contact-form {
                padding: 30px;
            }
            
            .service-card {
                padding: 40px 30px;
            }
        }

        @media (max-width: 480px) {
            .hero-title {
                font-size: 2.2rem;
            }
            
            .section-title h2 {
                font-size: 2.2rem;
            }
            
            .real-estate h2 {
                font-size: 2.5rem;
            }
            
            .contact-item {
                padding: 15px;
            }
        }

        /* Scroll reveal animations */
        .reveal {
            opacity: 0;
            transform: translateY(50px);
            transition: all 1s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <!-- Header avec logo -->
    <header id="header">
        <div class="nav-container">
            <div class="logo-container">
                <div class="logo-badge">NKA</div>
                <div>
                    <div class="logo-text">GROUP</div>
                    <div class="logo-subtitle">EXCELLENCE & PRESTIGE</div>
                </div>
            </div>
            
            <button class="mobile-menu-btn" id="mobileMenuBtn">
                <i class="fas fa-bars"></i>
            </button>
            
            <nav class="nav-links" id="navLinks">
                <a href="#accueil" class="nav-link active">Accueil</a>
                <a href="#services" class="nav-link">Services</a>
                <a href="#immobilier" class="nav-link">Immobilier</a>
                <a href="#contact" class="nav-link">Contact</a>
                <a href="tel:+2250707400144" class="nav-cta">
                    <i class="fas fa-phone"></i> 07 07 40 01 44
                </a>
            </nav>
        </div>
    </header>

    <!-- Hero Section Immersive -->
    <section class="hero" id="accueil">
        <div class="hero-bg"></div>
        <div class="hero-content">
            <h1 class="hero-title">L'Excellence Réinventée</h1>
            <p class="hero-subtitle">
                NKA Group réunit l'élégance immobilière et l'excellence automobile dans une expérience unique. 
                Location-vente de propriétés d'exception et sélection de véhicules premium à Abidjan.
            </p>
            <div class="hero-buttons">
                <a href="#contact" class="hero-btn btn-gold">
                    <i class="fas fa-calendar-check"></i> Rendez-vous Privé
                </a>
                <a href="#services" class="hero-btn btn-outline">
                    <i class="fas fa-gem"></i> Découvrir Nos Prestations
                </a>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section class="services" id="services">
        <div class="section-title reveal">
            <h2>Services Prestige</h2>
            <p>Une gamme complète de services pour une clientèle exigeante</p>
        </div>
        
        <div class="services-grid">
            <div class="service-card reveal">
                <div class="service-icon">
                    <i class="fas fa-gem"></i>
                </div>
                <h3>Immobilier d'Exception</h3>
                <p>Location-vente de propriétés prestigieuses dans les quartiers les plus exclusifs d'Abidjan.</p>
                <ul class="service-features">
                    <li><i class="fas fa-check"></i> Villas & Résidences de luxe</li>
                    <li><i class="fas fa-check"></i> Appartements haut de gamme</li>
                    <li><i class="fas fa-check"></i> Terrains viabilisés premium</li>
                    <li><i class="fas fa-check"></i> Accompagnement personnalisé</li>
                </ul>
            </div>
            
            <div class="service-card reveal">
                <div class="service-icon">
                    <i class="fas fa-car"></i>
                </div>
                <h3>Automobile Premium</h3>
                <p>Véhicules d'occasion sélectionnés avec rigueur, garantissant qualité et performance.</p>
                <ul class="service-features">
                    <li><i class="fas fa-check"></i> Voitures de luxe toutes marques</li>
                    <li><i class="fas fa-check"></i> SUV & 4x4 premium</li>
                    <li><i class="fas fa-check"></i> Véhicules utilitaires haut de gamme</li>
                    <li><i class="fas fa-check"></i> Inspection technique complète</li>
                </ul>
            </div>
            
            <div class="service-card reveal">
                <div class="service-icon">
                    <i class="fas fa-crown"></i>
                </div>
                <h3>Accessoires Élégance</h3>
                <p>Accessoires automobiles et pièces d'exception pour véhicules de prestige.</p>
                <ul class="service-features">
                    <li><i class="fas fa-check"></i> Pièces certifiées d'origine</li>
                    <li><i class="fas fa-check"></i> Équipements intérieurs luxueux</li>
                    <li><i class="fas fa-check"></i> Accessoires extérieurs premium</li>
                    <li><i class="fas fa-check"></i> Service après-vente exclusif</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Section Immobilier détaillée -->
    <section class="real-estate" id="immobilier">
        <div class="real-estate-content">
            <h2 class="reveal">Services Immobiliers NKA</h2>
            <p class="reveal">
                Notre expertise immobilière vous offre des solutions sur mesure pour acquérir 
                la propriété de vos rêves à Abidjan. Location-vente flexible et adaptée à vos besoins.
            </p>
            
            <div class="properties-grid">
                <div class="property-card reveal">
                    <div class="property-image">
                        <i class="fas fa-home"></i>
                    </div>
                    <div class="property-content">
                        <h4>Location-Vente Flexible</h4>
                        <p>Solution innovante pour devenir propriétaire progressivement selon vos capacités.</p>
                    </div>
                </div>
                
                <div class="property-card reveal">
                    <div class="property-image">
                        <i class="fas fa-building"></i>
                    </div>
                    <div class="property-content">
                        <h4>Portefeuille Premium</h4>
                        <p>Propriétés sélectionnées dans les quartiers les plus recherchés d'Abidjan.</p>
                    </div>
                </div>
                
                <div class="property-card reveal">
                    <div class="property-image">
                        <i class="fas fa-handshake"></i>
                    </div>
                    <div class="property-content">
                        <h4>Accompagnement Expert</h4>
                        <p>Conseil personnalisé à chaque étape de votre projet immobilier.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="contact" id="contact">
        <div class="section-title reveal">
            <h2>Contact Privé</h2>
            <p>Accédez à un service personnalisé et discret</p>
        </div>
        
        <div class="contact-container">
            <div class="contact-info">
                <div class="contact-item reveal">
                    <div class="contact-icon">
                        <i class="fas fa-map-marker-alt"></i>
                    </div>
                    <div class="contact-details">
                        <h3>Siège Prestige</h3>
                        <p>Cocody 7ème tranche<br>Non loin du carrefour Arafat<br>Abidjan, Côte d'Ivoire</p>
                    </div>
                </div>
                
                <div class="contact-item reveal">
                    <div class="contact-icon">
                        <i class="fas fa-phone"></i>
                    </div>
                    <div class="contact-details">
                        <h3>Lignes Directes</h3>
                        <p>+225 07 07 40 01 44<br>+225 05 66 12 74 73<br>+225 05 00 43 01 34</p>
                    </div>
                </div>
                
                <div class="contact-item reveal">
                    <div class="contact-icon">
                        <i class="fas fa-envelope"></i>
                    </div>
                    <div class="contact-details">
                        <h3>Email Exclusif</h3>
                        <p>Ralpheamanvy316@gmail.com</p>
                    </div>
                </div>
                
                <div class="contact-item reveal">
                    <div class="contact-icon">
                        <i class="fas fa-clock"></i>
                    </div>
                    <div class="contact-details">
                        <h3>Horaires Prestige</h3>
                        <p>Lundi - Vendredi: 8h30 - 18h30<br>Samedi: 10h00 - 16h00<br>Sur rendez-vous exclusif</p>
                    </div>
                </div>
            </div>
            
            <div class="contact-form reveal">
                <form id="contactForm">
                    <div class="form-group">
                        <label for="name">Nom Complet *</label>
                        <input type="text" id="name" class="form-control" required placeholder="Votre nom">
                    </div>
                    
                    <div class="form-group">
                        <label for="phone">Téléphone *</label>
                        <input type="tel" id="phone" class="form-control" required placeholder="Votre numéro">
                    </div>
                    
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input type="email" id="email" class="form-control" placeholder="Votre email">
                    </div>
                    
                    <div class="form-group">
                        <label for="service">Service Sollicité *</label>
                        <select id="service" class="form-control" required>
                            <option value="">Sélectionnez un service</option>
                            <option value="immobilier">Immobilier d'Exception</option>
                            <option value="vehicules">Automobile Premium</option>
                            <option value="accessoires">Accessoires Élégance</option>
                            <option value="rendezvous">Rendez-vous Privé</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="message">Message *</label>
                        <textarea id="message" class="form-control" required placeholder="Votre message..."></textarea>
                    </div>
                    
                    <button type="submit" class="hero-btn btn-gold" style="width: 100%;">
                        <i class="fas fa-paper-plane"></i> Envoyer la Demande
                    </button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-container">
            <div class="footer-logo">
                <div class="logo-container">
                    <div class="logo-badge">NKA</div>
                    <div>
                        <div class="logo-text">GROUP</div>
                        <div class="logo-subtitle">EXCELLENCE & PRESTIGE</div>
                    </div>
                </div>
                <p>Leader en immobilier premium et véhicules d'exception à Abidjan depuis 2008.</p>
                <div class="social-links">
                    <a href="#" class="social-link"><i class="fab fa-facebook-f"></i></a>
                    <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
                    <a href="#" class="social-link"><i class="fab fa-whatsapp"></i></a>
                    <a href="#" class="social-link"><i class="fab fa-linkedin-in"></i></a>
                </div>
            </div>
            
            <div class="footer-links">
                <h3 class="footer-heading">Navigation</h3>
                <ul>
                    <li><a href="#accueil"><i class="fas fa-chevron-right"></i> Accueil</a></li>
                    <li><a href="#services"><i class="fas fa-chevron-right"></i> Services</a></li>
                    <li><a href="#immobilier"><i class="fas fa-chevron-right"></i> Immobilier</a></li>
                    <li><a href="#contact"><i class="fas fa-chevron-right"></i> Contact</a></li>
                </ul>
            </div>
            
            <div class="footer-links">
                <h3 class="footer-heading">Services</h3>
                <ul>
                    <li><a href="#immobilier"><i class="fas fa-gem"></i> Immobilier d'Exception</a></li>
                    <li><a href="#services"><i class="fas fa-car"></i> Automobile Premium</a></li>
                    <li><a href="#services"><i class="fas fa-crown"></i> Accessoires Élégance</a></li>
                </ul>
            </div>
        </div>
        
        <div class="copyright">
            <p>&copy; 2023 NKA Group. Tous droits réservés. | Cocody 7ème tranche, Abidjan</p>
            <p style="margin-top: 10px; color: var(--gold);">
                <a href="tel:+2250707400144" style="color: var(--gold); text-decoration: none;">07 07 40 01 44</a> | 
                <a href="mailto:Ralpheamanvy316@gmail.com" style="color: var(--gold); text-decoration: none;">Email</a>
            </p>
        </div>
    </footer>

    <script>
        // Menu mobile
        const mobileMenuBtn = document.getElementById('mobileMenuBtn');
        const navLinks = document.getElementById('navLinks');

        mobileMenuBtn.addEventListener('click', () => {
            navLinks.classList.toggle('active');
            mobileMenuBtn.innerHTML = navLinks.classList.contains('active') 
                ? '<i class="fas fa-times"></i>' 
                : '<i class="fas fa-bars"></i>';
        });

        // Fermer le menu au clic sur les liens
        document.querySelectorAll('.nav-link').forEach(link => {
            link.addEventListener('click', () => {
                navLinks.classList.remove('active');
                mobileMenuBtn.innerHTML = '<i class="fas fa-bars"></i>';
                
                // Mettre à jour les liens actifs
                document.querySelectorAll('.nav-link').forEach(l => l.classList.remove('active'));
                link.classList.add('active');
            });
        });

        // Header scroll effect
        window.addEventListener('scroll', () => {
            const header = document.getElementById('header');
            if (window.scrollY > 100) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }

            // Scroll reveal
            const reveals = document.querySelectorAll('.reveal');
            const windowHeight = window.innerHeight;
            const revealPoint = 150;

            reveals.forEach(element => {
                const revealTop = element.getBoundingClientRect().top;
                
                if (revealTop < windowHeight - revealPoint) {
                    element.classList.add('active');
                }
            });
        });

        // Gestion du formulaire
        const contactForm = document.getElementById('contactForm');
        
        contactForm.addEventListener('submit', (e) => {
            e.preventDefault();
            
            const name = document.getElementById('name').value;
            const phone = document.getElementById('phone').value;
            const service = document.getElementById('service').value;
            
            // Créer notification
            const notification = document.createElement('div');
            notification.style.cssText = `
                position: fixed;
                top: 100px;
                right: 30px;
                background: linear-gradient(135deg, #D4AF37, #B8860B);
                color: #0a0a0a;
                padding: 20px 30px;
                border-radius: 10px;
                box-shadow: 0 10px 30px rgba(0,0,0,0.3);
                z-index: 10000;
                font-weight: 600;
                max-width: 350px;
                animation: slideIn 0.5s ease;
            `;
            
            notification.innerHTML = `
                <div style="margin-bottom: 10px; font-size: 1.1rem;">
                    <i class="fas fa-check-circle"></i> Demande envoyée !
                </div>
                <div style="font-size: 0.9rem; font-weight: 400;">
                    Merci ${name}. Nous vous contacterons au ${phone} très rapidement.
                </div>
            `;
            
            document.body.appendChild(notification);
            
            // Supprimer après 5 secondes
            setTimeout(() => {
                notification.style.animation = 'slideOut 0.5s ease';
                setTimeout(() => {
                    document.body.removeChild(notification);
                }, 500);
            }, 5000);
            
            // Réinitialiser
            contactForm.reset();
        });

        // Ajouter styles d'animation
        const style = document.createElement('style');
        style.textContent = `
            @keyframes slideIn {
                from { transform: translateX(100%); opacity: 0; }
                to { transform: translateX(0); opacity: 1; }
            }
            @keyframes slideOut {
                from { transform: translateX(0); opacity: 1; }
                to { transform: translateX(100%); opacity: 0; }
            }
        `;
        document.head.appendChild(style);

        // Navigation fluide
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if(targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if(targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 100,
                        behavior: 'smooth'
                    });
                }
            });
        });

        // Initialiser animations
        window.dispatchEvent(new Event('scroll'));
    </script>
</body>
</html>
