<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TechStore - Интернет-магазин техники</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        header {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 20px 0;
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 28px;
            font-weight: bold;
            color: white;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            cursor: pointer;
        }

        .nav-links {
            display: flex;
            gap: 30px;
            list-style: none;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s;
            padding: 8px 16px;
            border-radius: 20px;
        }

        .nav-links a:hover,
        .nav-links a.active {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        .hero {
            text-align: center;
            padding: 100px 0 80px;
            color: white;
        }

        .hero h1 {
            font-size: 72px;
            margin-bottom: 20px;
            text-shadow: 4px 4px 8px rgba(0,0,0,0.3);
            animation: fadeInUp 1s ease;
        }

        .hero-icon {
            font-size: 120px;
            margin-bottom: 30px;
            animation: float 3s ease-in-out infinite;
        }

        .hero p {
            font-size: 24px;
            opacity: 0.95;
            margin-bottom: 50px;
            animation: fadeInUp 1s ease 0.2s backwards;
        }

        .cta-buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap;
            animation: fadeInUp 1s ease 0.4s backwards;
        }

        .cta-btn {
            padding: 18px 40px;
            font-size: 18px;
            font-weight: bold;
            border-radius: 50px;
            text-decoration: none;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }

        .cta-btn.primary {
            background: white;
            color: #667eea;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .cta-btn.primary:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 15px 40px rgba(0,0,0,0.3);
        }

        .cta-btn.secondary {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: 2px solid white;
            backdrop-filter: blur(10px);
        }

        .cta-btn.secondary:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-5px);
        }

        .features {
            padding: 80px 0;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 40px;
        }

        .feature-card {
            background: white;
            border-radius: 25px;
            padding: 40px;
            text-align: center;
            box-shadow: 0 15px 40px rgba(0,0,0,0.2);
            transition: all 0.4s;
            animation: fadeInUp 0.8s ease forwards;
            opacity: 0;
        }

        .feature-card:nth-child(1) { animation-delay: 0.1s; }
        .feature-card:nth-child(2) { animation-delay: 0.3s; }
        .feature-card:nth-child(3) { animation-delay: 0.5s; }

        .feature-card:hover {
            transform: translateY(-15px) scale(1.02);
            box-shadow: 0 25px 60px rgba(0,0,0,0.3);
        }

        .feature-icon {
            font-size: 80px;
            margin-bottom: 25px;
            display: block;
        }

        .feature-card h3 {
            font-size: 28px;
            color: #333;
            margin-bottom: 15px;
        }

        .feature-card p {
            color: #666;
            font-size: 16px;
            line-height: 1.8;
        }

        .stats-section {
            padding: 80px 0;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            margin: 60px 0;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 40px;
            text-align: center;
        }

        .stat-item {
            color: white;
        }

        .stat-number {
            font-size: 56px;
            font-weight: bold;
            text-shadow: 2px 2px 6px rgba(0,0,0,0.3);
            margin-bottom: 10px;
        }

        .stat-label {
            font-size: 18px;
            opacity: 0.9;
        }

        .products-preview {
            padding: 80px 0;
        }

        .section-title {
            text-align: center;
            color: white;
            font-size: 48px;
            margin-bottom: 60px;
            text-shadow: 3px 3px 6px rgba(0,0,0,0.3);
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 30px;
            margin-bottom: 50px;
        }

        .product-card {
            background: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            transition: all 0.3s;
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 50px rgba(0,0,0,0.3);
        }

        .product-image {
            width: 100%;
            height: 200px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 80px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }

        .product-info {
            padding: 25px;
        }

        .product-name {
            font-size: 20px;
            font-weight: bold;
            color: #333;
            margin-bottom: 10px;
        }

        .product-price {
            font-size: 24px;
            color: #667eea;
            font-weight: bold;
        }

        .view-all-btn {
            display: block;
            width: fit-content;
            margin: 0 auto;
            padding: 16px 50px;
            background: white;
            color: #667eea;
            text-decoration: none;
            border-radius: 50px;
            font-size: 18px;
            font-weight: bold;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            transition: all 0.3s;
        }

        .view-all-btn:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 15px 40px rgba(0,0,0,0.3);
        }

        footer {
            background: rgba(0, 0, 0, 0.3);
            color: white;
            text-align: center;
            padding: 40px 0;
            margin-top: 80px;
        }

        footer p {
            margin: 10px 0;
        }

        .footer-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 20px;
            flex-wrap: wrap;
        }

        .footer-links a {
            color: white;
            text-decoration: none;
            transition: all 0.3s;
        }

        .footer-links a:hover {
            text-decoration: underline;
            transform: translateY(-2px);
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0px);
            }
            50% {
                transform: translateY(-20px);
            }
        }

        @media (max-width: 768px) {
            .hero h1 {
                font-size: 48px;
            }

            .hero p {
                font-size: 18px;
            }

            .cta-buttons {
                flex-direction: column;
                align-items: center;
            }

            .section-title {
                font-size: 36px;
            }

            .stat-number {
                font-size: 42px;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <nav>
                <div class="logo">⚡ TechStore</div>
                <ul class="nav-links">
                    <li><a href="#" class="active">Главная</a></li>
                    <li><a href="ecommerce_projects.html">Проекты</a></li>
                    <li><a href="ecommerce_contacts.html">Контакты</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <section class="hero">
        <div class="container">
            <div class="hero-icon">⚡</div>
            <h1>TechStore</h1>
            <p>Ваш надёжный партнёр в мире современных технологий</p>
            <div class="cta-buttons">
                <a href="ecommerce_projects.html" class="cta-btn primary">
                    <span>🚀</span>
                    Наши проекты
                </a>
                <a href="ecommerce_contacts.html" class="cta-btn secondary">
                    <span>📞</span>
                    Связаться с нами
                </a>
            </div>
        </div>
    </section>

    <section class="features">
        <div class="container">
            <div class="features-grid">
                <div class="feature-card">
                    <span class="feature-icon">🎯</span>
                    <h3>Инновации</h3>
                    <p>Мы создаём передовые технологические решения, которые меняют способ взаимодействия людей с современной техникой</p>
                </div>
                <div class="feature-card">
                    <span class="feature-icon">🌟</span>
                    <h3>Качество</h3>
                    <p>Каждый наш продукт проходит строгий контроль качества. Мы гарантируем надёжность и долговечность</p>
                </div>
                <div class="feature-card">
                    <span class="feature-icon">🤝</span>
                    <h3>Поддержка</h3>
                    <p>Наша команда экспертов всегда готова помочь вам с выбором и настройкой оборудования 24/7</p>
                </div>
            </div>
        </div>
    </section>

    <section class="stats-section">
        <div class="container">
            <div class="stats-grid">
                <div class="stat-item">
                    <div class="stat-number">50+</div>
                    <div class="stat-label">Проектов</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number">1M+</div>
                    <div class="stat-label">Пользователей</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number">30+</div>
                    <div class="stat-label">Стран</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number">15+</div>
                    <div class="stat-label">Наград</div>
                </div>
            </div>
        </div>
    </section>

    <section class="products-preview">
        <div class="container">
            <h2 class="section-title">Популярные категории</h2>
            <div class="products-grid">
                <div class="product-card">
                    <div class="product-image" style="background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);">📱</div>
                    <div class="product-info">
                        <div class="product-name">Мобильные устройства</div>
                        <div class="product-price">от 15 000 ₽</div>
                    </div>
                </div>
                <div class="product-card">
                    <div class="product-image" style="background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);">💻</div>
                    <div class="product-info">
                        <div class="product-name">Ноутбуки</div>
                        <div class="product-price">от 35 000 ₽</div>
                    </div>
                </div>
                <div class="product-card">
                    <div class="product-image" style="background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);">🎧</div>
                    <div class="product-info">
                        <div class="product-name">Аудио техника</div>
                        <div class="product-price">от 5 000 ₽</div>
                    </div>
                </div>
                <div class="product-card">
                    <div class="product-image" style="background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);">⌚</div>
                    <div class="product-info">
                        <div class="product-name">Умные часы</div>
                        <div class="product-price">от 12 000 ₽</div>
                    </div>
                </div>
            </div>
            <a href="ecommerce_projects.html" class="view-all-btn">Смотреть все проекты →</a>
        </div>
    </section>

    <footer>
        <div class="container">
            <p style="font-size: 24px; margin-bottom: 20px;">⚡ TechStore</p>
            <p>&copy; 2025 TechStore. Все права защищены.</p>
            <p>Инновации, которые меняют мир технологий</p>
            <div class="footer-links">
                <a href="#">О компании</a>
                <a href="ecommerce_projects.html">Проекты</a>
                <a href="ecommerce_contacts.html">Контакты</a>
                <a href="#">Политика конфиденциальности</a>
                <a href="#">Условия использования</a>
            </div>
        </div>
    </footer>

    <script>
        // Плавная прокрутка
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth'
                    });
                }
            });
        });

        // Анимация при прокрутке
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        document.querySelectorAll('.feature-card, .product-card').forEach(el => {
            observer.observe(el);
        });
    </script>
</body>
</html>
