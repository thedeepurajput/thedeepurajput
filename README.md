<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Deepanshu Singh - Flutter Developer</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #6366f1;
            --secondary: #8b5cf6;
            --accent: #06b6d4;
            --success: #10b981;
            --warning: #f59e0b;
            --danger: #ef4444;
            --dark: #0f172a;
            --light: #f8fafc;
            --glass: rgba(255, 255, 255, 0.1);
            --glass-border: rgba(255, 255, 255, 0.2);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
            min-height: 100vh;
            color: #1e293b;
            overflow-x: hidden;
            position: relative;
        }

        /* Animated Background */
        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
            background: linear-gradient(-45deg, #667eea, #764ba2, #f093fb, #48cae4);
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
        }

        .floating-elements {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .floating-circle {
            position: absolute;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.05);
            animation: floatUp 6s infinite ease-in-out;
        }

        .floating-circle:nth-child(1) {
            width: 80px;
            height: 80px;
            left: 10%;
            animation-delay: 0s;
        }

        .floating-circle:nth-child(2) {
            width: 60px;
            height: 60px;
            left: 70%;
            animation-delay: 2s;
        }

        .floating-circle:nth-child(3) {
            width: 100px;
            height: 100px;
            left: 50%;
            animation-delay: 4s;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Navigation */
        .nav {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 1000;
            background: var(--glass);
            backdrop-filter: blur(20px);
            border: 1px solid var(--glass-border);
            border-radius: 50px;
            padding: 15px 30px;
            animation: slideDown 1s ease-out;
        }

        .nav-links {
            display: flex;
            gap: 30px;
            list-style: none;
        }

        .nav-link {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s ease;
            position: relative;
        }

        .nav-link:hover {
            color: var(--accent);
            transform: translateY(-2px);
        }

        .nav-link::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: width 0.3s ease;
        }

        .nav-link:hover::after {
            width: 100%;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
        }

        .hero-content {
            background: var(--glass);
            backdrop-filter: blur(20px);
            border: 1px solid var(--glass-border);
            border-radius: 30px;
            padding: 60px 40px;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.15);
            animation: heroEntrance 1.2s ease-out;
        }

        .hero-avatar {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 40px;
            font-size: 80px;
            position: relative;
            animation: avatarFloat 3s ease-in-out infinite;
        }

        .hero-avatar::before {
            content: '';
            position: absolute;
            top: -10px;
            left: -10px;
            right: -10px;
            bottom: -10px;
            border-radius: 50%;
            background: linear-gradient(45deg, var(--accent), var(--primary), var(--secondary));
            z-index: -1;
            animation: avatarGlow 2s ease-in-out infinite alternate;
        }

        .hero-title {
            font-size: 4rem;
            font-weight: 900;
            background: linear-gradient(135deg, #ffffff, #e2e8f0);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 20px;
            animation: titleSlide 1s ease-out 0.3s both;
        }

        .hero-subtitle {
            font-size: 1.5rem;
            color: rgba(255, 255, 255, 0.9);
            font-weight: 400;
            margin-bottom: 40px;
            animation: subtitleSlide 1s ease-out 0.6s both;
        }

        .hero-cta {
            display: flex;
            gap: 20px;
            justify-content: center;
            animation: ctaSlide 1s ease-out 0.9s both;
        }

        .btn {
            padding: 15px 30px;
            border: none;
            border-radius: 50px;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
        }

        .btn-outline {
            background: transparent;
            color: white;
            border: 2px solid rgba(255, 255, 255, 0.3);
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.5s;
        }

        .btn:hover::before {
            left: 100%;
        }

        /* Section Styling */
        .section {
            padding: 100px 0;
            position: relative;
        }

        .section-header {
            text-align: center;
            margin-bottom: 80px;
        }

        .section-title {
            font-size: 3rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--dark), var(--primary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 20px;
        }

        .section-subtitle {
            font-size: 1.2rem;
            color: #64748b;
            max-width: 600px;
            margin: 0 auto;
            line-height: 1.6;
        }

        /* Skills Section */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-top: 60px;
        }

        .skill-card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 25px;
            padding: 40px 30px;
            text-align: center;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
            cursor: pointer;
        }

        .skill-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transition: left 0.6s;
        }

        .skill-card:hover::before {
            left: 100%;
        }

        .skill-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.15);
        }

        .skill-icon {
            width: 80px;
            height: 80px;
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.5rem;
            margin: 0 auto 25px;
            position: relative;
            animation: iconPulse 2s ease-in-out infinite;
        }

        .skill-icon.flutter {
            background: linear-gradient(135deg, #02569B, #0277BD);
        }

        .skill-icon.firebase {
            background: linear-gradient(135deg, #FFCA28, #FF8F00);
        }

        .skill-icon.java {
            background: linear-gradient(135deg, #ED8B00, #F57C00);
        }

        .skill-icon.mysql {
            background: linear-gradient(135deg, #4479A1, #1976D2);
        }

        .skill-icon.c {
            background: linear-gradient(135deg, #A8B9CC, #607D8B);
        }

        .skill-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--dark);
            margin-bottom: 15px;
        }

        .skill-description {
            color: #64748b;
            line-height: 1.6;
            font-size: 1rem;
        }

        .skill-progress {
            margin-top: 20px;
            background: #e2e8f0;
            height: 8px;
            border-radius: 4px;
            overflow: hidden;
        }

        .skill-progress-bar {
            height: 100%;
            border-radius: 4px;
            transition: width 2s ease-in-out;
        }

        /* Projects Section */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 40px;
            margin-top: 60px;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border-radius: 25px;
            overflow: hidden;
            transition: all 0.4s ease;
            position: relative;
            cursor: pointer;
        }

        .project-card:hover {
            transform: translateY(-15px);
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.2);
        }

        .project-image {
            height: 200px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: white;
        }

        .project-content {
            padding: 30px;
        }

        .project-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--dark);
            margin-bottom: 15px;
        }

        .project-description {
            color: #64748b;
            line-height: 1.6;
            margin-bottom: 20px;
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
        }

        .project-tag {
            padding: 5px 15px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 500;
        }

        /* Contact Section */
        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 60px;
        }

        .contact-card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            border-radius: 25px;
            padding: 40px 30px;
            text-align: center;
            text-decoration: none;
            color: inherit;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
        }

        .contact-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.15);
        }

        .contact-icon {
            width: 80px;
            height: 80px;
            border-radius: 20px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            color: white;
            margin: 0 auto 25px;
        }

        .contact-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--dark);
            margin-bottom: 10px;
        }

        .contact-description {
            color: #64748b;
            font-size: 1rem;
        }

        /* Fun Fact */
        .fun-fact {
            background: linear-gradient(135deg, var(--warning), #f97316);
            color: white;
            padding: 40px;
            border-radius: 25px;
            text-align: center;
            margin-top: 60px;
            position: relative;
            overflow: hidden;
        }

        .fun-fact::before {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(45deg, var(--primary), var(--secondary), var(--accent), var(--warning));
            border-radius: 25px;
            z-index: -1;
            animation: borderRotate 3s linear infinite;
        }

        .fun-fact-content {
            position: relative;
            z-index: 1;
        }

        /* Animations */
        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes floatUp {
            0%, 100% { transform: translateY(100vh) rotate(0deg); opacity: 0; }
            10%, 90% { opacity: 1; }
            50% { transform: translateY(-100px) rotate(180deg); }
        }

        @keyframes slideDown {
            from { transform: translateX(-50%) translateY(-100px); opacity: 0; }
            to { transform: translateX(-50%) translateY(0); opacity: 1; }
        }

        @keyframes heroEntrance {
            from { transform: scale(0.8) translateY(50px); opacity: 0; }
            to { transform: scale(1) translateY(0); opacity: 1; }
        }

        @keyframes avatarFloat {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-15px); }
        }

        @keyframes avatarGlow {
            0% { opacity: 0.5; transform: scale(1); }
            100% { opacity: 0.8; transform: scale(1.05); }
        }

        @keyframes titleSlide {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes subtitleSlide {
            from { transform: translateY(30px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes ctaSlide {
            from { transform: translateY(20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes iconPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        @keyframes borderRotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .nav {
                padding: 10px 20px;
            }
            
            .nav-links {
                gap: 15px;
            }
            
            .hero-title {
                font-size: 2.5rem;
            }
            
            .hero-subtitle {
                font-size: 1.2rem;
            }
            
            .hero-cta {
                flex-direction: column;
                align-items: center;
            }
            
            .section-title {
                font-size: 2rem;
            }
            
            .skills-grid,
            .projects-grid,
            .contact-grid {
                grid-template-columns: 1fr;
            }
            
            .section {
                padding: 60px 0;
            }
        }

        /* Scroll Reveal Animation */
        .reveal {
            opacity: 0;
            transform: translateY(50px);
            transition: all 0.8s ease;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <div class="bg-animation"></div>
    
    <div class="floating-elements">
        <div class="floating-circle"></div>
        <div class="floating-circle"></div>
        <div class="floating-circle"></div>
    </div>

    <!-- Navigation -->
    <nav class="nav">
        <ul class="nav-links">
            <li><a href="#hero" class="nav-link">Home</a></li>
            <li><a href="#skills" class="nav-link">Skills</a></li>
            <li><a href="#projects" class="nav-link">Projects</a></li>
            <li><a href="#contact" class="nav-link">Contact</a></li>
        </ul>
    </nav>

    <!-- Hero Section -->
    <section id="hero" class="hero">
        <div class="hero-content">
            <div class="hero-avatar">👨‍💻</div>
            <h1 class="hero-title">Hi 👋, I'm Deepanshu Singh</h1>
            <p class="hero-subtitle">Flutter Developer | Firebase Enthusiast | Java Backend Learner</p>
            <div class="hero-cta">
                <a href="#projects" class="btn btn-primary">View My Work</a>
                <a href="#contact" class="btn btn-outline">Get In Touch</a>
            </div>
        </div>
    </section>

    <div class="container">
        <!-- Skills Section -->
        <section id="skills" class="section reveal">
            <div class="section-header">
                <h2 class="section-title">🌱 Skills & Expertise</h2>
                <p class="section-subtitle">Passionate about creating beautiful, functional applications with modern technologies</p>
            </div>
            
            <div class="skills-grid">
                <div class="skill-card">
                    <div class="skill-icon flutter">💙</div>
                    <h3 class="skill-title">Dart & Flutter</h3>
                    <p class="skill-description">Cross-platform mobile development with beautiful, native-performance apps for iOS and Android</p>
                    <div class="skill-progress">
                        <div class="skill-progress-bar" style="width: 85%; background: linear-gradient(135deg, #02569B, #0277BD);"></div>
                    </div>
                </div>
                
                <div class="skill-card">
                    <div class="skill-icon firebase">🔥</div>
                    <h3 class="skill-title">Firebase</h3>
                    <p class="skill-description">Authentication, Firestore, Cloud Functions, and real-time database for scalable backend solutions</p>
                    <div class="skill-progress">
                        <div class="skill-progress-bar" style="width: 80%; background: linear-gradient(135deg, #FFCA28, #FF8F00);"></div>
                    </div>
                </div>
                
                <div class="skill-card">
                    <div class="skill-icon java">☕</div>
                    <h3 class="skill-title">Java</h3>
                    <p class="skill-description">Core Java fundamentals and Spring Boot framework for robust backend development</p>
                    <div class="skill-progress">
                        <div class="skill-progress-bar" style="width: 70%; background: linear-gradient(135deg, #ED8B00, #F57C00);"></div>
                    </div>
                </div>
                
                <div class="skill-card">
                    <div class="skill-icon mysql">🐚</div>
                    <h3 class="skill-title">MySQL</h3>
                    <p class="skill-description">Relational database design, optimization, and complex query management</p>
                    <div class="skill-progress">
                        <div class="skill-progress-bar" style="width: 75%; background: linear-gradient(135deg, #4479A1, #1976D2);"></div>
                    </div>
                </div>
                
                <div class="skill-card">
                    <div class="skill-icon c">💻</div>
                    <h3 class="skill-title">C Programming</h3>
                    <p class="skill-description">Strong foundation in programming fundamentals and algorithmic problem-solving</p>
                    <div class="skill-progress">
                        <div class="skill-progress-bar" style="width: 65%; background: linear-gradient(135deg, #A8B9CC, #607D8B);"></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Projects Section -->
        <section id="projects" class="section reveal">
            <div class="section-header">
                <h2 class="section-title">🚀 Current Focus</h2>
                <p class="section-subtitle">What I'm working on and learning right now</p>
            </div>
            
            <div class="projects-grid">
                <div class="project-card">
                    <div class="project-image">🔭</div>
                    <div class="project-content">
                        <h3 class="project-title">Flutter + Firebase Projects</h3>
                        <p class="project-description">Building modern mobile applications with Flutter frontend and Firebase backend integration for real-time data synchronization.</p>
                        <div class="project-tags">
                            <span class="project-tag">Flutter</span>
                            <span class="project-tag">Firebase</span>
                            <span class="project-tag">Dart</span>
                        </div>
                    </div>
                </div>
                
                <div class="project-card">
                    <div class="project-image">🎯</div>
                    <div class="project-content">
                        <h3 class="project-title">State Management & APIs</h3>
                        <p class="project-description">Exploring advanced state management solutions like Provider and Riverpod, along with RESTful API integration patterns.</p>
                        <div class="project-tags">
                            <span class="project-tag">Provider</span>
                            <span class="project-tag">Riverpod</span>
                            <span class="project-tag">REST API</span>
                        </div>
                    </div>
                </div>
                
                <div class="project-card">
                    <div class="project-image">🏗️</div>
                    <div class="project-content">
                        <h3 class="project-title">Clean Architecture</h3>
                        <p class="project-description">Learning and implementing clean architecture principles in Flutter applications for maintainable and scalable codebases.</p>
                        <div class="project-tags">
                            <span class="project-tag">Clean Architecture</span>
                            <span class="project-tag">SOLID</span>
                            <span class="project-tag">Design Patterns</span>
                        </div>
                    </div>
                </div>
                
                <div class="project-card">
                    <div class="project-image">🌐</div>
                    <div class="project-content">
                        <h3 class="project-title">Java + Spring Boot</h3>
                        <p class="project-description">Diving deeper into Java ecosystem and Spring Boot framework for enterprise-level backend development.</p>
                        <div class="project-tags">
                            <span class="project-tag">Spring Boot</span>
                            <span class="project-tag">Java</span>
                            <span class="project-tag">Backend</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="section reveal">
            <div class="section-header">
                <h2 class="section-title">📫 Let's Connect</h2>
                <p class="section-subtitle">Ready to collaborate or discuss opportunities? Let's get in touch!</p>
            </div>
            
            <div class="contact-grid">
                <a href="https://www.linkedin.com/in/thedeepanshurajput" class="contact-card" target="_blank">
                    <div class="contact-icon">💼</div>
                    <h3 class="contact-title">LinkedIn</h3>
                    <p class="contact-description">Connect with me professionally and see my career journey</p>
                </a>
                
                <a href="mailto:thedeepanshurajput@gmail.com" class="contact-card">
                    <div class="contact-icon">📧</div>
                    <h3 class="contact-title">Email</h3>
                    <p class="contact-description">thedeepanshurajput@gmail.com</p>
                </a>
                
                <div class="contact-card">
                    <div class="contact-icon">🌍</div>
                    <h3 class="contact-title">Location</h3>
                    <p class="contact-description">Available for remote opportunities worldwide</p>
                </div>
            </div>
            
            <div class="fun-fact">
                <div class="fun-fact-content">
                    <h3>⚡ Fun Fact</h3>
                    <p>I love building beautiful UIs with Flutter & debugging weird Firebase errors! There's something satisfying about solving complex problems and creating smooth user experiences. 😄</p>
                </div>
            </div>
        </section>
    </div>

    <script>
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

        // Scroll reveal animation
        function reveal() {
            const reveals = document.querySelectorAll('.reveal');
            
            for (let i = 0; i < reveals.length; i++) {
                const windowHeight = window.innerHeight;
                const elementTop = reveals[i].getBoundingClientRect().top;
                const elementVisible = 150;
                
                if (elementTop < windowHeight - elementVisible) {
                    reveals[i].classList.add('active');
                }
            }
        }

        window.addEventListener('scroll', reveal);
        reveal(); // Check on page load

        // Skill progress bars animation
        function animateSkillBars() {
            const skillBars = document.querySelectorAll('.skill-progress-bar');
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        const bar = entry.target;
                        const width = bar.style.width;
                        bar.style.width = '0';
                        setTimeout(() => {
                            bar.style.width = width;
                        }, 500);
                    }
                });
            }, { threshold: 0.5 });

            skillBars.forEach(bar => observer.observe(bar));
        }

        animateSkillBars();

        // Interactive card effects
        document.querySelectorAll('.skill-card, .project-card, .contact-card').forEach(card => {
            card.addEventListener('mouseenter',
