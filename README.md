# PRODIGY_WD_01
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aurora Digital Studio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            line-height: 1.6;
            background: #0a0a0a;
            color: #ffffff;
            overflow-x: hidden;
        }

        /* Animated gradient background */
        .gradient-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, #667eea, #764ba2, #f093fb, #f5576c, #4facfe, #00f2fe);
            background-size: 400% 400%;
            animation: gradientFlow 15s ease infinite;
            z-index: -2;
        }

        @keyframes gradientFlow {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* Glassmorphism overlay */
        .glass-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(100px);
            z-index: -1;
        }

        /* Floating orbs */
        .orb {
            position: fixed;
            border-radius: 50%;
            background: linear-gradient(45deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.05));
            backdrop-filter: blur(20px);
            pointer-events: none;
            animation: float 8s ease-in-out infinite;
        }

        .orb:nth-child(1) {
            width: 200px;
            height: 200px;
            top: 10%;
            left: 10%;
            animation-delay: 0s;
        }

        .orb:nth-child(2) {
            width: 150px;
            height: 150px;
            top: 60%;
            right: 10%;
            animation-delay: 2s;
        }

        .orb:nth-child(3) {
            width: 100px;
            height: 100px;
            bottom: 20%;
            left: 20%;
            animation-delay: 4s;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            33% { transform: translateY(-30px) rotate(120deg); }
            66% { transform: translateY(30px) rotate(240deg); }
        }

        /* Header */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(10, 10, 10, 0.8);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            z-index: 1000;
            transition: all 0.3s ease;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 5%;
            max-width: 1400px;
            margin: 0 auto;
        }

        .logo {
            font-size: 2rem;
            font-weight: 700;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: -0.02em;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2.5rem;
        }

        .nav-links a {
            color: rgba(255, 255, 255, 0.8);
            text-decoration: none;
            transition: all 0.3s ease;
            font-weight: 500;
            position: relative;
        }

        .nav-links a:hover {
            color: #667eea;
            transform: translateY(-2px);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Mobile menu button */
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
            z-index: 2;
        }

        .hero-content {
            max-width: 1000px;
            padding: 2rem;
            animation: fadeInUp 1s ease-out;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(80px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero h1 {
            font-size: 5rem;
            margin-bottom: 1.5rem;
            font-weight: 800;
            line-height: 1.1;
            background: linear-gradient(45deg, #667eea, #764ba2, #f093fb);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: gradientShift 4s ease-in-out infinite;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .hero p {
            font-size: 1.4rem;
            margin-bottom: 3rem;
            opacity: 0.9;
            line-height: 1.6;
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
        }

        .cta-primary, .cta-secondary {
            padding: 16px 32px;
            border-radius: 50px;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .cta-primary {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
        }

        .cta-secondary {
            background: rgba(255, 255, 255, 0.1);
            color: white;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .cta-primary:hover, .cta-secondary:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 40px rgba(102, 126, 234, 0.4);
        }

        /* Services Section */
        .services {
            padding: 120px 5%;
            position: relative;
            z-index: 2;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
        }

        .section-title {
            text-align: center;
            font-size: 3.5rem;
            margin-bottom: 4rem;
            font-weight: 700;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 120px;
            height: 4px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            border-radius: 2px;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .service-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            padding: 3rem 2rem;
            border-radius: 24px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .service-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, rgba(102, 126, 234, 0.1), rgba(118, 75, 162, 0.1));
            opacity: 0;
            transition: opacity 0.4s ease;
        }

        .service-card:hover::before {
            opacity: 1;
        }

        .service-card:hover {
            transform: translateY(-15px);
            box-shadow: 0 25px 60px rgba(102, 126, 234, 0.2);
            border-color: rgba(102, 126, 234, 0.3);
        }

        .service-icon {
            width: 100px;
            height: 100px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 1.5rem;
            font-size: 2.5rem;
            position: relative;
            z-index: 1;
        }

        .service-card h3 {
            font-size: 1.8rem;
            margin-bottom: 1rem;
            font-weight: 600;
            position: relative;
            z-index: 1;
        }

        .service-card p {
            color: rgba(255, 255, 255, 0.8);
            line-height: 1.6;
            position: relative;
            z-index: 1;
        }

        /* Portfolio Section */
        .portfolio {
            padding: 120px 5%;
            position: relative;
            z-index: 2;
        }

        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 4rem;
        }

        .portfolio-item {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            overflow: hidden;
            transition: all 0.4s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .portfolio-item:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 50px rgba(102, 126, 234, 0.2);
        }

        .portfolio-image {
            height: 200px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
        }

        .portfolio-content {
            padding: 1.5rem;
        }

        .portfolio-content h3 {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }

        .portfolio-content p {
            color: rgba(255, 255, 255, 0.7);
            font-size: 0.9rem;
        }

        /* About Section */
        .about {
            padding: 120px 5%;
            position: relative;
            z-index: 2;
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 6rem;
            align-items: center;
        }

        .about-text h2 {
            font-size: 3rem;
            margin-bottom: 2rem;
            font-weight: 700;
        }

        .about-text p {
            font-size: 1.2rem;
            color: rgba(255, 255, 255, 0.8);
            margin-bottom: 2rem;
            line-height: 1.7;
        }

        .stats {
            display: flex;
            gap: 2rem;
            margin-top: 3rem;
        }

        .stat {
            text-align: center;
        }

        .stat h3 {
            font-size: 2.5rem;
            font-weight: 700;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .stat p {
            color: rgba(255, 255, 255, 0.6);
            font-size: 0.9rem;
        }

        .about-visual {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            height: 500px;
            border-radius: 24px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            position: relative;
            overflow: hidden;
        }

        .about-visual::before {
            content: '✨';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 6rem;
            animation: pulse 3s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: translate(-50%, -50%) scale(1); }
            50% { transform: translate(-50%, -50%) scale(1.1); }
        }

        /* Footer */
        footer {
            background: rgba(10, 10, 10, 0.9);
            backdrop-filter: blur(20px);
            padding: 80px 5% 30px;
            position: relative;
            z-index: 2;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        .footer-content {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 3rem;
        }

        .footer-section h3 {
            margin-bottom: 1.5rem;
            color: #667eea;
            font-weight: 600;
        }

        .footer-section p, .footer-section a {
            color: rgba(255, 255, 255, 0.7);
            text-decoration: none;
            line-height: 1.8;
            transition: color 0.3s ease;
        }

        .footer-section a:hover {
            color: #667eea;
        }

        .footer-bottom {
            text-align: center;
            margin-top: 3rem;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: rgba(255, 255, 255, 0.5);
        }

        /* Dark mode toggle */
        .theme-toggle {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            border: none;
            border-radius: 50%;
            width: 60px;
            height: 60px;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
            z-index: 1000;
        }

        .theme-toggle:hover {
            transform: scale(1.1);
            box-shadow: 0 15px 40px rgba(102, 126, 234, 0.4);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .mobile-menu-btn {
                display: block;
            }

            .hero h1 {
                font-size: 3rem;
            }

            .hero p {
                font-size: 1.2rem;
            }

            .cta-buttons {
                flex-direction: column;
                align-items: center;
            }

            .about-content {
                grid-template-columns: 1fr;
                gap: 3rem;
            }

            .section-title {
                font-size: 2.5rem;
            }

            .stats {
                justify-content: center;
            }

            .orb {
                display: none;
            }
        }

        /* Smooth scrolling */
        html {
            scroll-behavior: smooth;
        }

        /* Loading animation */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .fade-in {
            animation: fadeIn 1s ease-out;
        }
    </style>
</head>
<body>
    <!-- Background Elements -->
    <div class="gradient-bg"></div>
    <div class="glass-overlay"></div>
    <div class="orb"></div>
    <div class="orb"></div>
    <div class="orb"></div>

    <!-- Header -->
    <header>
        <nav>
            <div class="logo">Aurora</div>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#services">Services</a></li>
                <li><a href="#portfolio">Portfolio</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
            <button class="mobile-menu-btn">☰</button>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-content">
            <h1>Digital Dreams. Realized.</h1>
            <p>We craft extraordinary digital experiences that blur the line between imagination and reality. Your vision, our expertise, infinite possibilities.</p>
            <div class="cta-buttons">
                <a href="#portfolio" class="cta-primary">View Our Work</a>
                <a href="#contact" class="cta-secondary">Start Your Project</a>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section class="services" id="services">
        <div class="container">
            <h2 class="section-title">What We Create</h2>
            <div class="services-grid">
                <div class="service-card">
                    <div class="service-icon">🎨</div>
                    <h3>UI/UX Design</h3>
                    <p>Crafting intuitive interfaces that captivate users and drive engagement through thoughtful design and seamless user experiences.</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">💻</div>
                    <h3>Web Development</h3>
                    <p>Building lightning-fast, responsive websites using modern technologies and frameworks that scale with your business.</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">📱</div>
                    <h3>Mobile Apps</h3>
                    <p>Developing native and cross-platform mobile applications that deliver exceptional performance and user satisfaction.</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">🚀</div>
                    <h3>Brand Identity</h3>
                    <p>Creating memorable brand identities that tell your story and resonate with your audience across all touchpoints.</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">⚡</div>
                    <h3>Digital Strategy</h3>
                    <p>Developing comprehensive digital strategies that align with your business goals and maximize your online presence.</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">🎯</div>
                    <h3>Performance Optimization</h3>
                    <p>Optimizing websites and applications for maximum speed, SEO, and conversion rates to boost your business growth.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Portfolio Section -->
    <section class="portfolio" id="portfolio">
        <div class="container">
            <h2 class="section-title">Our Showcase</h2>
            <div class="portfolio-grid">
                <div class="portfolio-item">
                    <div class="portfolio-image">🌟</div>
                    <div class="portfolio-content">
                        <h3>E-commerce Platform</h3>
                        <p>Modern shopping experience with seamless checkout</p>
                    </div>
                </div>
                <div class="portfolio-item">
                    <div class="portfolio-image">🎵</div>
                    <div class="portfolio-content">
                        <h3>Music Streaming App</h3>
                        <p>Immersive audio experience with social features</p>
                    </div>
                </div>
                <div class="portfolio-item">
                    <div class="portfolio-image">🏢</div>
                    <div class="portfolio-content">
                        <h3>Corporate Website</h3>
                        <p>Professional presence with interactive elements</p>
                    </div>
                </div>
                <div class="portfolio-item">
                    <div class="portfolio-image">🎮</div>
                    <div class="portfolio-content">
                        <h3>Gaming Platform</h3>
                        <p>Interactive gaming hub with real-time features</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section class="about" id="about">
        <div class="container">
            <div class="about-content">
                <div class="about-text">
                    <h2>About Aurora Studio</h2>
                    <p>We're a forward-thinking digital agency that believes in the power of exceptional design and cutting-edge technology. Our team of passionate creators and innovators work together to bring your wildest digital dreams to life.</p>
                    <p>From concept to launch, we're your partners in creating digital experiences that not only look stunning but deliver real results for your business.</p>
                    <div class="stats">
                        <div class="stat">
                            <h3>150+</h3>
                            <p>Projects Completed</p>
                        </div>
                        <div class="stat">
                            <h3>98%</h3>
                            <p>Client Satisfaction</p>
                        </div>
                        <div class="stat">
                            <h3>5+</h3>
                            <p>Years Experience</p>
                        </div>
                    </div>
                </div>
                <div class="about-visual"></div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer id="contact">
        <div class="footer-content">
            <div class="footer-section">
                <h3>Get In Touch</h3>
            
            </div>
            <div class="footer-section">
                <h3>Services</h3>
                <p><a href="#services">UI/UX Design</a></p>
                <p><a href="#services">Web Development</a></p>
                <p><a href="#services">Mobile Apps</a></p>
                <p><a href="#services">Brand Identity</a></p>
            </div>
            <div class="footer-section">
                <h3>Connect</h3>
                <p><a href="#">Instagram</a></p>
                <p><a href="#">LinkedIn</a></p>
                <p><a href="#">Twitter</a></p>
                <p><a href="#">Dribbble</a></p>
            </div>
            <div class="footer-section">
                <h3>Resources</h3>
                <p><a href="#">Blog</a></p>
                <p><a href="#">Case Studies</a></p>
                <p><a href="#">Process</a></p>
                <p><a href="#">Careers</a></p>
            </div>
        </div>
        <div class="footer-bottom">
            <p>&copy; 2025 Aurora Digital Studio. All rights reserved.</p>
        </div>
    </footer>

    <!-- Theme Toggle Button -->
    <button class="theme-toggle" id="themeToggle">🌙</button>

    <script>
        // Header scroll effect
        window.addEventListener('scroll', () => {
            const header = document.querySelector('header');
            if (window.scrollY > 100) {
                header.style.background = 'rgba(10, 10, 10, 0.95)';
            } else {
                header.style.background = 'rgba(10, 10, 10, 0.8)';
            }
        });

        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Intersection Observer for animations
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

        // Theme toggle functionality
        const themeToggle = document.getElementById('themeToggle');
        let isLightMode = false;

        themeToggle.addEventListener('click', () => {
            isLightMode = !isLightMode;
            
            if (isLightMode) {
                document.body.style.background = '#ffffff';
                document.body.style.color = '#333333';
                document.querySelector('.gradient-bg').style.opacity = '0.1';
                document.querySelector('.glass-overlay').style.background = 'rgba(255, 255, 255, 0.8)';
                themeToggle.textContent = '☀';
            } else {
                document.body.style.background = '#0a0a0a';
                document.body.style.color = '#ffffff';
                document.querySelector('.gradient-bg').style.opacity = '1';
                document.querySelector('.glass-overlay').style.background = 'rgba(0, 0, 0, 0.3)';
                themeToggle.textContent = '🌙';
            }
        });

        // Mobile menu toggle
        const mobileMenuBtn = document.querySelector('.mobile-menu-btn');
        const navLinks = document.querySelector('.nav-links');

        mobileMenuBtn.addEventListener('click', () => {
            navLinks.style.display = navLinks.style.display === 'flex' ? 'none' : 'flex';
        });

        // Animate elements on scroll
        document.addEventListener('DOMContentLoaded', () => {
            const animatedElements = document.querySelectorAll('.service-card, .portfolio-item');
            
            animatedElements.forEach((element, index) => {
                element.style.opacity = '0';
                element.style.transform = 'translateY(50px)';
                element.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
                element.style.transitionDelay = (index * 0.1) + 's';
                observer.observe(element);
            });
        });

        // Parallax effect for orbs
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const orbs = document.querySelectorAll('.orb');
            
            orbs.forEach((orb, index) => {
                const speed = 0.5 + (index * 0.1);
                orb.style.transform = translateY(${scrolled * speed}px);
            });
        });

        // Add loading animation
        window.addEventListener('load', () => {
            document.body.classList.add('fade-in');
        });
    </script>
</body>
</html>
