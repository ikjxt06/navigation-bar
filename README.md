<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Techify - Digital Learning Platform</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-bg: #ffffff;
            --secondary-bg: #f8fafc;
            --text-color: #1e293b;
            --accent-color: #4f46e5;
            --accent-hover: #4338ca;
            --nav-bg: rgba(255, 255, 255, 0.95);
            --nav-text: #1e293b;
            --nav-scrolled-bg: rgba(15, 23, 42, 0.98);
            --nav-scrolled-text: #e2e8f0;
            --hero-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            --logo-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            --underline-gradient: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
            --card-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
            --transition-all: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
        }

        .dark-mode {
            --primary-bg: #0f172a;
            --secondary-bg: #1e293b;
            --text-color: #f8fafc;
            --accent-color: #818cf8;
            --accent-hover: #a5b4fc;
            --nav-bg: rgba(15, 23, 42, 0.98);
            --nav-text: #e2e8f0;
            --nav-scrolled-bg: rgba(30, 41, 59, 0.98);
            --nav-scrolled-text: #f8fafc;
            --hero-gradient: linear-gradient(135deg, #4338ca 0%, #5b21b6 100%);
            --logo-gradient: linear-gradient(135deg, #f6d365 0%, #fda085 100%);
            --underline-gradient: linear-gradient(90deg, #f6d365 0%, #fda085 100%);
            --card-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.25), 0 2px 4px -1px rgba(0, 0, 0, 0.15);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            transition: var(--transition-all);
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background-color: var(--primary-bg);
            color: var(--text-color);
            line-height: 1.6;
        }

        /* Advanced Navigation Bar */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 18px 5%;
            background-color: var(--nav-bg);
            box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
            z-index: 1000;
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
        }

        .navbar.scrolled {
            padding: 12px 5%;
            background-color: var(--nav-scrolled-bg);
            box-shadow: 0 4px 30px rgba(0, 0, 0, 0.2);
        }

        .logo-container {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-img {
            width: 40px;
            height: 40px;
            background: var(--logo-gradient);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 20px;
        }

        .logo-text {
            font-size: 26px;
            font-weight: 800;
            background: var(--logo-gradient);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: -0.5px;
        }

        .nav-actions {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 30px;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--nav-text);
            font-weight: 600;
            font-size: 16px;
            position: relative;
            padding: 8px 0;
            letter-spacing: -0.3px;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 3px;
            background: var(--underline-gradient);
            border-radius: 3px;
            transition: width 0.3s ease, opacity 0.3s ease;
            opacity: 0;
        }

        .nav-links a:hover::after {
            width: 100%;
            opacity: 1;
        }

        .nav-links a:hover {
            color: var(--accent-color);
        }

        /* Theme Toggle */
        .theme-toggle {
            background: none;
            border: none;
            color: var(--nav-text);
            font-size: 20px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            transition: var(--transition-all);
        }

        .theme-toggle:hover {
            background-color: rgba(79, 70, 229, 0.1);
            color: var(--accent-color);
        }

        .dark-mode .theme-toggle:hover {
            background-color: rgba(129, 140, 248, 0.1);
        }

        /* Mobile Menu */
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            color: var(--nav-text);
            font-size: 24px;
            cursor: pointer;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            transition: var(--transition-all);
        }

        .mobile-menu-btn:hover {
            background-color: rgba(79, 70, 229, 0.1);
            color: var(--accent-color);
        }

        /* Hero Section - Fixed overlap issue */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 100px 20px 20px; /* Added top padding for navbar */
            background: var(--hero-gradient);
            color: white;
        }

        .hero-content {
            max-width: 800px;
            margin-top: 60px; /* Additional margin to ensure visibility */
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 20px;
            font-weight: 800;
            line-height: 1.2;
        }

        .hero p {
            font-size: 1.2rem;
            opacity: 0.9;
            margin-bottom: 30px;
        }

        .btn {
            display: inline-block;
            padding: 12px 28px;
            background-color: white;
            color: #4f46e5;
            border-radius: 8px;
            font-weight: 600;
            text-decoration: none;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: var(--transition-all);
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }

        /* Content Sections */
        .section {
            padding: 100px 10%;
            background-color: var(--primary-bg);
        }

        .section-title {
            font-size: 2.5rem;
            margin-bottom: 50px;
            text-align: center;
            font-weight: 700;
            background: var(--logo-gradient);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            display: inline-block;
            width: 100%;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .service-card {
            background-color: var(--secondary-bg);
            border-radius: 12px;
            padding: 30px;
            box-shadow: var(--card-shadow);
        }

        .service-card h3 {
            font-size: 1.5rem;
            margin-bottom: 15px;
            color: var(--accent-color);
        }

        .contact-info {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-top: 40px;
        }

        .contact-card {
            background-color: var(--secondary-bg);
            border-radius: 12px;
            padding: 25px;
            box-shadow: var(--card-shadow);
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
        }

        .contact-icon {
            width: 60px;
            height: 60px;
            background: var(--logo-gradient);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 24px;
            margin-bottom: 20px;
        }

        /* Responsive Styles */
        @media (max-width: 1024px) {
            .nav-links {
                gap: 20px;
            }
        }

        @media (max-width: 768px) {
            .navbar {
                padding: 15px 5%;
            }

            .nav-links {
                position: fixed;
                top: 80px;
                left: -100%;
                width: 100%;
                height: calc(100vh - 80px);
                background-color: var(--nav-scrolled-bg);
                flex-direction: column;
                align-items: center;
                justify-content: center;
                gap: 30px;
                transition: left 0.4s ease;
            }

            .nav-links.active {
                left: 0;
            }

            .nav-links a {
                font-size: 20px;
            }

            .mobile-menu-btn {
                display: block;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .section-title {
                font-size: 2rem;
            }
        }

        @media (max-width: 480px) {
            .hero h1 {
                font-size: 2rem;
            }

            .hero p {
                font-size: 1rem;
            }

            .section {
                padding: 80px 5%;
            }
        }
    </style>
</head>
<body>
    <nav class="navbar">
        <div class="logo-container">
            <div class="logo-img">
                <i class="fas fa-laptop-code"></i>
            </div>
            <span class="logo-text">Techify</span>
        </div>
        
        <ul class="nav-links" id="navLinks">
            <li><a href="#home">Home</a></li>
            <li><a href="#solutions">Solutions</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
        
        <div class="nav-actions">
            <button class="theme-toggle" id="themeToggle">
                <i class="fas fa-moon"></i>
            </button>
            <button class="mobile-menu-btn" id="mobileMenuBtn">
                <i class="fas fa-bars"></i>
            </button>
        </div>
    </nav>
    
    <section class="hero" id="home">
        <div class="hero-content">
            <h1>Empowering Your Digital Learning Journey</h1>
            <p>Access world-class tech education and build your future with our innovative platform</p>
            <a href="#services" class="btn">Explore Services</a>
        </div>
    </section>
    
    <section class="section" id="solutions">
        <h2 class="section-title">Our Solutions</h2>
        <div class="services-grid">
            <div class="service-card">
                <h3>Interactive Learning</h3>
                <p>Engage with hands-on coding exercises and real-world projects that enhance your understanding and retention.</p>
            </div>
            <div class="service-card">
                <h3>Skill Assessment</h3>
                <p>Our advanced evaluation system tracks your progress and identifies areas for improvement.</p>
            </div>
            <div class="service-card">
                <h3>Career Pathways</h3>
                <p>Structured learning tracks designed to take you from beginner to job-ready professional.</p>
            </div>
        </div>
    </section>
    
    <section class="section" id="services">
        <h2 class="section-title">Our Services</h2>
        <div class="services-grid">
            <div class="service-card">
                <h3>Free Course Access</h3>
                <p>We provide complimentary access to our foundational courses, enabling students to learn essential skills without financial barriers. Our curriculum is designed by industry experts to deliver maximum value.</p>
            </div>
            <div class="service-card">
                <h3>Practical Challenges</h3>
                <p>Upon course completion, students receive real-world tasks and problem sets that reinforce learning. These challenges simulate actual workplace scenarios to bridge the gap between theory and practice.</p>
            </div>
            <div class="service-card">
                <h3>Reward System</h3>
                <p>Successful completion of challenges earns you Techify Tokens, our platform currency. These tokens can be redeemed for advanced courses, certifications, and premium learning resources.</p>
            </div>
        </div>
    </section>

    <section class="section" id="about">
        <h2 class="section-title">About Techify</h2>
        <div class="services-grid">
            <div class="service-card">
                <h3>Our Mission</h3>
                <p>To democratize technology education by removing financial and geographical barriers, making quality learning accessible to everyone regardless of their background or circumstances.</p>
            </div>
            <div class="service-card">
                <h3>Our Approach</h3>
                <p>We combine project-based learning with gamification elements to create an engaging, effective educational experience that prepares students for real-world challenges.</p>
            </div>
            <div class="service-card">
                <h3>Our Impact</h3>
                <p>Since our founding, we've helped over 50,000 students acquire valuable tech skills, with many securing positions at leading tech companies worldwide.</p>
            </div>
        </div>
    </section>
    
    <section class="section" id="contact">
        <h2 class="section-title">Contact Us</h2>
        <div class="contact-info">
            <div class="contact-card">
                <div class="contact-icon">
                    <i class="fas fa-map-marker-alt"></i>
                </div>
                <h3>Headquarters</h3>
                <p>Techify Education Center<br>123 Innovation Drive<br>San Francisco, CA 94107</p>
            </div>
            <div class="contact-card">
                <div class="contact-icon">
                    <i class="fas fa-phone-alt"></i>
                </div>
                <h3>Phone</h3>
                <p>+1 (415) 555-0192<br>+1 (415) 555-0193 (Support)</p>
                <p>Mon-Fri: 9AM-6PM PST</p>
            </div>
            <div class="contact-card">
                <div class="contact-icon">
                    <i class="fas fa-envelope"></i>
                </div>
                <h3>Email</h3>
                <p>info@techify.com<br>support@techify.com<br>partners@techify.com</p>
            </div>
            <div class="contact-card">
                <div class="contact-icon">
                    <i class="fas fa-comment-dots"></i>
                </div>
                <h3>Social Media</h3>
                <p>Twitter: @TechifyEdu<br>LinkedIn: Techify Education<br>Instagram: @TechifyOfficial</p>
            </div>
        </div>
    </section>

    <script>
        // Theme Toggle Functionality
        const themeToggle = document.getElementById('themeToggle');
        const prefersDarkScheme = window.matchMedia('(prefers-color-scheme: dark)');
        
        // Check for saved theme preference or use system preference
        const currentTheme = localStorage.getItem('theme');
        if (currentTheme === 'dark' || (!currentTheme && prefersDarkScheme.matches)) {
            document.body.classList.add('dark-mode');
            themeToggle.innerHTML = '<i class="fas fa-sun"></i>';
        }
        
        themeToggle.addEventListener('click', function() {
            document.body.classList.toggle('dark-mode');
            const theme = document.body.classList.contains('dark-mode') ? 'dark' : 'light';
            localStorage.setItem('theme', theme);
            
            if (theme === 'dark') {
                themeToggle.innerHTML = '<i class="fas fa-sun"></i>';
            } else {
                themeToggle.innerHTML = '<i class="fas fa-moon"></i>';
            }
        });
        
        // Navigation Scroll Effect
        window.addEventListener('scroll', function() {
            const navbar = document.querySelector('.navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });
        
        // Mobile Menu Toggle
        const mobileMenuBtn = document.getElementById('mobileMenuBtn');
        const navLinks = document.getElementById('navLinks');
        
        mobileMenuBtn.addEventListener('click', function() {
            navLinks.classList.toggle('active');
            this.innerHTML = navLinks.classList.contains('active') 
                ? '<i class="fas fa-times"></i>' 
                : '<i class="fas fa-bars"></i>';
        });
        
        // Close mobile menu when clicking a link
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', function() {
                if (window.innerWidth <= 768) {
                    navLinks.classList.remove('active');
                    mobileMenuBtn.innerHTML = '<i class="fas fa-bars"></i>';
                }
            });
        });
        
        // Smooth scrolling for all links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                
                window.scrollTo({
                    top: targetElement.offsetTop - 80,
                    behavior: 'smooth'
                });
            });
        });
    </script>
</body>
</html>
