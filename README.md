<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bhuwan Singh - 3D GitHub Profile</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, #0c0c0c 0%, #1a1a2e 50%, #16213e 100%);
            color: white;
            overflow-x: hidden;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
        }
        
        .floating-particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }
        
        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: #64ffda;
            border-radius: 50%;
            animation: float 6s infinite ease-in-out;
            opacity: 0.6;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
        }
        
        .hero-section {
            text-align: center;
            padding: 80px 0;
            position: relative;
            z-index: 2;
        }
        
        .hero-title {
            font-size: 4rem;
            font-weight: 700;
            background: linear-gradient(45deg, #64ffda, #ff6b6b, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 20px;
            animation: glow 2s ease-in-out infinite alternate;
            transform-style: preserve-3d;
        }
        
        @keyframes glow {
            from { text-shadow: 0 0 20px rgba(100, 255, 218, 0.5); }
            to { text-shadow: 0 0 30px rgba(100, 255, 218, 0.8), 0 0 40px rgba(100, 255, 218, 0.6); }
        }
        
        .hero-subtitle {
            font-size: 1.5rem;
            opacity: 0.8;
            margin-bottom: 40px;
            animation: slideInUp 1s ease-out 0.5s both;
        }
        
        .wave-emoji {
            display: inline-block;
            animation: wave 2s infinite;
            transform-origin: 70% 70%;
        }
        
        @keyframes wave {
            0% { transform: rotate(0deg); }
            10% { transform: rotate(14deg); }
            20% { transform: rotate(-8deg); }
            30% { transform: rotate(14deg); }
            40% { transform: rotate(-4deg); }
            50% { transform: rotate(10deg); }
            60% { transform: rotate(0deg); }
            100% { transform: rotate(0deg); }
        }
        
        .card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 40px;
            margin: 30px 0;
            position: relative;
            overflow: hidden;
            transform-style: preserve-3d;
            transition: all 0.4s ease;
        }
        
        .card:hover {
            transform: translateY(-10px) rotateX(5deg);
            box-shadow: 0 25px 50px rgba(100, 255, 218, 0.2);
        }
        
        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(100, 255, 218, 0.1), transparent);
            transition: 0.5s;
        }
        
        .card:hover::before {
            left: 100%;
        }
        
        .section-title {
            font-size: 2.5rem;
            font-weight: 600;
            margin-bottom: 30px;
            position: relative;
            display: inline-block;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(45deg, #64ffda, #ff6b6b);
            border-radius: 2px;
            animation: expand 2s ease-in-out infinite alternate;
        }
        
        @keyframes expand {
            from { width: 50%; }
            to { width: 100%; }
        }
        
        .about-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .about-item {
            padding: 20px;
            background: rgba(100, 255, 218, 0.05);
            border-radius: 15px;
            border-left: 4px solid #64ffda;
            transform: perspective(1000px) rotateY(0deg);
            transition: all 0.3s ease;
        }
        
        .about-item:hover {
            transform: perspective(1000px) rotateY(5deg) translateZ(20px);
            background: rgba(100, 255, 218, 0.1);
        }
        
        .tech-stack {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .tech-item {
            text-align: center;
            padding: 20px;
            background: rgba(255, 255, 255, 0.03);
            border-radius: 15px;
            border: 1px solid rgba(100, 255, 218, 0.2);
            transition: all 0.3s ease;
            transform-style: preserve-3d;
        }
        
        .tech-item:hover {
            transform: translateY(-10px) rotateX(10deg);
            background: rgba(100, 255, 218, 0.1);
            box-shadow: 0 20px 40px rgba(100, 255, 218, 0.2);
        }
        
        .tech-icon {
            width: 60px;
            height: 60px;
            margin: 0 auto 15px;
            background: linear-gradient(45deg, #64ffda, #4ecdc4);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            animation: spin 10s linear infinite;
        }
        
        @keyframes spin {
            from { transform: rotateY(0deg); }
            to { transform: rotateY(360deg); }
        }
        
        .connect-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .connect-item {
            padding: 25px;
            background: linear-gradient(135deg, rgba(100, 255, 218, 0.1), rgba(255, 107, 107, 0.1));
            border-radius: 15px;
            text-align: center;
            text-decoration: none;
            color: white;
            transition: all 0.3s ease;
            transform-style: preserve-3d;
            position: relative;
            overflow: hidden;
        }
        
        .connect-item:hover {
            transform: translateY(-10px) scale(1.05);
            box-shadow: 0 20px 40px rgba(100, 255, 218, 0.3);
        }
        
        .connect-item::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: radial-gradient(circle, rgba(100, 255, 218, 0.3) 0%, transparent 70%);
            transition: all 0.3s ease;
            transform: translate(-50%, -50%);
        }
        
        .connect-item:hover::before {
            width: 300px;
            height: 300px;
        }
        
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }
        
        .project-card {
            background: linear-gradient(135deg, rgba(100, 255, 218, 0.05), rgba(255, 107, 107, 0.05));
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(100, 255, 218, 0.2);
            transition: all 0.4s ease;
            transform-style: preserve-3d;
            position: relative;
        }
        
        .project-card:hover {
            transform: translateY(-15px) rotateX(5deg);
            box-shadow: 0 30px 60px rgba(100, 255, 218, 0.2);
        }
        
        .project-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(45deg, #64ffda, #ff6b6b);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            margin-bottom: 20px;
            animation: bounce 2s infinite;
        }
        
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-10px); }
            60% { transform: translateY(-5px); }
        }
        
        .cta-section {
            text-align: center;
            padding: 60px 0;
            background: linear-gradient(135deg, rgba(100, 255, 218, 0.1), rgba(255, 107, 107, 0.1));
            margin-top: 50px;
            border-radius: 30px;
            position: relative;
            overflow: hidden;
        }
        
        .cta-section::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(100, 255, 218, 0.1) 0%, transparent 70%);
            animation: rotate 20s linear infinite;
        }
        
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        .cta-text {
            font-size: 2rem;
            font-weight: 600;
            position: relative;
            z-index: 2;
            background: linear-gradient(45deg, #64ffda, #ff6b6b, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .animated {
            animation: slideInUp 0.8s ease-out both;
        }
        
        .delay-1 { animation-delay: 0.1s; }
        .delay-2 { animation-delay: 0.2s; }
        .delay-3 { animation-delay: 0.3s; }
        .delay-4 { animation-delay: 0.4s; }
        
        @media (max-width: 768px) {
            .hero-title {
                font-size: 2.5rem;
            }
            
            .hero-subtitle {
                font-size: 1.2rem;
            }
            
            .section-title {
                font-size: 2rem;
            }
            
            .card {
                padding: 20px;
            }
            
            .tech-stack {
                grid-template-columns: repeat(auto-fit, minmax(80px, 1fr));
            }
        }
    </style>
</head>
<body>
    <div class="floating-particles" id="particles"></div>
    
    <div class="container">
        <div class="hero-section animated">
            <h1 class="hero-title">Hey <span class="wave-emoji">👋</span> What's up?</h1>
            <p class="hero-subtitle">I'm Bhuwan, a Computer Science student at BCU passionate about leveraging technology to build smart, impactful digital experiences.</p>
        </div>
        
        <div class="card animated delay-1">
            <h2 class="section-title">About Me</h2>
            <div class="about-grid">
                <div class="about-item">
                    <h3>✨ Innovation</h3>
                    <p>Building cutting-edge software solutions</p>
                </div>
                <div class="about-item">
                    <h3>📚 Learning</h3>
                    <p>Exploring AI and building seamless frontends with Streamlit</p>
                </div>
                <div class="about-item">
                    <h3>🎯 Goals</h3>
                    <p>Harness AI to solve real-world problems</p>
                </div>
                <div class="about-item">
                    <h3>🎲 Philosophy</h3>
                    <p>I believe technology should not only be smart but also meaningful</p>
                </div>
            </div>
        </div>
        
        <div class="card animated delay-2">
            <h2 class="section-title">I code with</h2>
            <div class="tech-stack">
                <div class="tech-item">
                    <div class="tech-icon">🐍</div>
                    <p>Python</p>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">⚡</div>
                    <p>JavaScript</p>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">🌐</div>
                    <p>HTML5</p>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">🎨</div>
                    <p>CSS3</p>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">⚛️</div>
                    <p>React</p>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">🟢</div>
                    <p>Node.js</p>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">🗃️</div>
                    <p>SQLite</p>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">🍃</div>
                    <p>MongoDB</p>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">📦</div>
                    <p>Git</p>
                </div>
                <div class="tech-item">
                    <div class="tech-icon">🐙</div>
                    <p>GitHub</p>
                </div>
            </div>
        </div>
        
        <div class="card animated delay-3">
            <h2 class="section-title">Connect With Me</h2>
            <div class="connect-grid">
                <a href="https://github.com/BHUWON12" class="connect-item">
                    <h3>🐙 GitHub</h3>
                    <p>BHUWON12</p>
                </a>
                <a href="https://www.linkedin.com/in/bhuwansingh02/" class="connect-item">
                    <h3>💼 LinkedIn</h3>
                    <p>bhuwansingh02</p>
                </a>
                <a href="https://x.com/bhuwansinghh" class="connect-item">
                    <h3>🐦 Twitter</h3>
                    <p>bhuwansinghh</p>
                </a>
                <a href="https://digitalbhuwan.vercel.app/" class="connect-item">
                    <h3>🌐 Portfolio</h3>
                    <p>My Portfolio</p>
                </a>
            </div>
        </div>
        
        <div class="card animated delay-4">
            <h2 class="section-title">🚀 Projects Showcase</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <div class="project-icon">🌿</div>
                    <h3>AgriDoctor</h3>
                    <p>Identify plant diseases using AI - A revolutionary tool for farmers and agricultural experts.</p>
                    <a href="https://agridoctor.streamlit.app/" style="color: #64ffda; text-decoration: none;">Live Project →</a>
                </div>
                <div class="project-card">
                    <div class="project-icon">💡</div>
                    <h3>Business Solutions</h3>
                    <p>Innovative software solutions for modern businesses - Creating impactful digital experiences.</p>
                    <p style="color: #64ffda;">Website in Progress...</p>
                </div>
            </div>
        </div>
        
        <div class="cta-section animated">
            <p class="cta-text">🌟 Let's innovate, collaborate, and create something extraordinary! 🌟</p>
        </div>
    </div>
    
    <script>
        // Create floating particles
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 50;
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.classList.add('particle');
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 6 + 's';
                particle.style.animationDuration = (Math.random() * 3 + 3) + 's';
                particlesContainer.appendChild(particle);
            }
        }
        
        // Add scroll animations
        function addScrollAnimations() {
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.opacity = '1';
                        entry.target.style.transform = 'translateY(0)';
                    }
                });
            });
            
            document.querySelectorAll('.card').forEach(card => {
                card.style.opacity = '0';
                card.style.transform = 'translateY(50px)';
                card.style.transition = 'all 0.8s ease';
                observer.observe(card);
            });
        }
        
        // Add mouse movement parallax effect
        function addParallaxEffect() {
            document.addEventListener('mousemove', (e) => {
                const mouseX = e.clientX / window.innerWidth;
                const mouseY = e.clientY / window.innerHeight;
                
                document.querySelectorAll('.card').forEach((card, index) => {
                    const speed = (index + 1) * 0.5;
                    card.style.transform = `translate(${mouseX * speed}px, ${mouseY * speed}px)`;
                });
            });
        }
        
        // Initialize all effects
        document.addEventListener('DOMContentLoaded', () => {
            createParticles();
            addScrollAnimations();
            addParallaxEffect();
        });
        
        // Add dynamic color changes
        setInterval(() => {
            const particles = document.querySelectorAll('.particle');
            particles.forEach(particle => {
                const colors = ['#64ffda', '#ff6b6b', '#4ecdc4', '#45b7d1', '#96ceb4'];
                particle.style.background = colors[Math.floor(Math.random() * colors.length)];
            });
        }, 3000);
    </script>
</body>
</html>
