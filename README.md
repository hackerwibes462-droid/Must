<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hacker X | Digital Ghost</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=VT323&amp;display=swap');
        
        :root {
            --neon-green: #00ff9f;
            --neon-pink: #ff00ff;
            --dark-bg: #0a0a0a;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: var(--dark-bg);
            color: var(--neon-green);
            font-family: 'VT323', monospace;
            overflow-x: hidden;
            line-height: 1.4;
            cursor: url('data:image/svg+xml;utf8,<svg xmlns=%27http://www.w3.org/2000/svg%27 width=%2716%27 height=%2716%27 viewBox=%270 0 16 16%27><text y=%2712%27 font-size=%2712%27>⚡</text></svg>') 8 8, auto;
        }
        
        /* Animated Background */
        .scanlines {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                to bottom,
                transparent 0px,
                transparent 2px,
                rgba(0, 255, 159, 0.03) 2px,
                rgba(0, 255, 159, 0.03) 4px
            );
            pointer-events: none;
            z-index: 1;
            animation: scan 4s linear infinite;
        }
        
        @keyframes scan {
            0% { transform: translateY(-100%); }
            100% { transform: translateY(100%); }
        }
        
        .grid-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(var(--neon-green) 0.5px, transparent 0.5px),
                linear-gradient(90deg, var(--neon-green) 0.5px, transparent 0.5px);
            background-size: 40px 40px;
            opacity: 0.08;
            z-index: 0;
            pointer-events: none;
        }
        
        header {
            position: fixed;
            top: 0;
            width: 100%;
            z-index: 1000;
            padding: 15px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid rgba(0, 255, 159, 0.2);
            background: rgba(10, 10, 10, 0.95);
            backdrop-filter: blur(8px);
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            text-shadow: 0 0 10px var(--neon-green);
            letter-spacing: 4px;
        }
        
        nav a {
            color: var(--neon-green);
            text-decoration: none;
            margin-left: 30px;
            transition: all 0.3s;
            position: relative;
        }
        
        nav a:hover {
            color: white;
            text-shadow: 0 0 15px var(--neon-green);
        }
        
        /* Hero */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            z-index: 2;
            text-align: center;
        }
        
        .hero-content {
            max-width: 800px;
            padding: 0 20px;
        }
        
        .glitch {
            font-size: 6.5rem;
            font-weight: bold;
            text-transform: uppercase;
            position: relative;
            display: inline-block;
            color: var(--neon-green);
            text-shadow: 
                0.05em 0 0 #ff00ff,
                -0.025em -0.05em 0 #00ffff,
                0.025em 0.05em 0 #ffff00;
            animation: glitch 1.5s infinite;
        }
        
        @keyframes glitch {
            0% { transform: translate(0); }
            20% { transform: translate(-3px, 3px); }
            40% { transform: translate(-3px, -3px); }
            60% { transform: translate(3px, 3px); }
            80% { transform: translate(3px, -3px); }
            100% { transform: translate(0); }
        }
        
        .glitch::before,
        .glitch::after {
            content: attr(data-text);
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }
        
        .glitch::before {
            left: 2px;
            text-shadow: -2px 0 #ff00ff;
            clip: rect(24px, 9999px, 56px, 0);
            animation: glitch-anim 2s infinite linear alternate-reverse;
        }
        
        .glitch::after {
            left: -2px;
            text-shadow: -2px 0 #00ffff;
            clip: rect(85px, 9999px, 120px, 0);
            animation: glitch-anim2 3s infinite linear alternate-reverse;
        }
        
        @keyframes glitch-anim {
            0% { clip: rect(10px, 9999px, 40px, 0); }
            5% { clip: rect(50px, 9999px, 80px, 0); }
            10% { clip: rect(20px, 9999px, 60px, 0); }
        }
        
        .subtitle {
            font-size: 1.8rem;
            margin: 20px 0;
            opacity: 0.9;
            letter-spacing: 6px;
        }
        
        .typewriter {
            font-size: 1.4rem;
            margin-top: 30px;
            color: #00cc7a;
            overflow: hidden;
            border-right: 3px solid var(--neon-green);
            white-space: nowrap;
            animation: typing 3.5s steps(30, end) forwards,
                       blink-caret .75s step-end infinite;
        }
        
        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }
        
        @keyframes blink-caret {
            from, to { border-color: transparent }
            50% { border-color: var(--neon-green) }
        }
        
        /* Sections */
        section {
            padding: 100px 8%;
            position: relative;
            z-index: 2;
        }
        
        .section-title {
            font-size: 3rem;
            margin-bottom: 60px;
            text-align: center;
            position: relative;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 120px;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--neon-green), transparent);
        }
        
        /* About */
        .about-card {
            max-width: 700px;
            margin: 0 auto;
            background: rgba(20, 20, 30, 0.8);
            border: 2px solid var(--neon-green);
            padding: 40px;
            box-shadow: 0 0 40px rgba(0, 255, 159, 0.3);
            transition: all 0.4s;
        }
        
        .about-card:hover {
            box-shadow: 0 0 60px rgba(0, 255, 159, 0.6);
            transform: translateY(-10px);
        }
        
        /* Skills */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 25px;
            max-width: 1100px;
            margin: 0 auto;
        }
        
        .skill-card {
            background: rgba(15, 15, 25, 0.9);
            border: 1px solid var(--neon-green);
            padding: 30px 20px;
            text-align: center;
            transition: all 0.4s;
            position: relative;
            overflow: hidden;
        }
        
        .skill-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 40%;
            height: 40%;
            background: radial-gradient(circle, rgba(0,255,159,0.4) 0%, transparent 70%);
            opacity: 0;
            transition: all 0.6s;
        }
        
        .skill-card:hover {
            transform: scale(1.08) rotate(2deg);
            box-shadow: 0 0 40px var(--neon-green);
        }
        
        .skill-card:hover::before {
            opacity: 1;
            top: -20%;
            left: -20%;
        }
        
        .skill-card h3 {
            font-size: 1.8rem;
            margin-bottom: 15px;
        }
        
        /* Contact */
        .contact-container {
            text-align: center;
            max-width: 600px;
            margin: 0 auto;
        }
        
        .terminal {
            background: #000;
            border: 3px solid #00ff9f;
            padding: 30px;
            font-size: 1.3rem;
            box-shadow: 0 0 30px rgba(0, 255, 159, 0.5);
            margin-bottom: 40px;
        }
        
        .neon-button {
            display: inline-block;
            padding: 18px 50px;
            font-size: 1.6rem;
            color: #000;
            background: var(--neon-green);
            text-decoration: none;
            border: 3px solid var(--neon-green);
            transition: all 0.4s;
            box-shadow: 0 0 20px var(--neon-green);
            position: relative;
            overflow: hidden;
        }
        
        .neon-button:hover {
            background: transparent;
            color: var(--neon-green);
            box-shadow: 0 0 40px var(--neon-green);
            transform: scale(1.05);
        }
        
        /* Footer */
        footer {
            text-align: center;
            padding: 40px;
            border-top: 1px dashed rgba(0, 255, 159, 0.3);
            font-size: 1.1rem;
            opacity: 0.7;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .glitch {
                font-size: 4rem;
            }
            .hero {
                padding-top: 80px;
            }
        }
    </style>
</head>
<body>
    <!-- Background Elements -->
    <div class="grid-bg"></div>
    <div class="scanlines"></div>
    
    <!-- Navigation -->
    <header>
        <div class="logo">HACKER_X</div>
        <nav>
            <a href="#about">ABOUT</a>
            <a href="#skills">SKILLS</a>
            <a href="#contact">CONNECT</a>
        </nav>
    </header>
    
    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-content">
            <h1 class="glitch" data-text="HACKER X">HACKER X</h1>
            <p class="subtitle">HACKER • DEVELOPER • DIGITAL GHOST</p>
            <p class="typewriter" id="typewriter">Accessing the mainframe since 20XX...</p>
            
            <div style="margin-top: 80px;">
                <a href="#about" style="color: var(--neon-green); font-size: 1.5rem; text-decoration: none; border: 2px solid var(--neon-green); padding: 12px 40px; display: inline-block; transition: 0.3s;">
                    ENTER SYSTEM
                </a>
            </div>
        </div>
    </section>
    
    <!-- About Section -->
    <section id="about">
        <h2 class="section-title">SYSTEM PROFILE</h2>
        <div class="about-card">
            <p style="font-size: 1.5rem; margin-bottom: 25px;">
                I am Hacker X — a shadow in the wires. 
                I breach firewalls, craft exploits, and build digital fortresses.
            </p>
            <p style="font-size: 1.4rem; opacity: 0.9;">
                By day, I develop clean, efficient systems. 
                By night, I hunt vulnerabilities and secure the unsecured. 
                The matrix is my domain.
            </p>
            <div style="margin-top: 40px; text-align: center; font-size: 1.3rem; color: #ff00ff;">
                STATUS: <span style="color: var(--neon-green);">ONLINE • UNTRACEABLE</span>
            </div>
        </div>
    </section>
    
    <!-- Skills Section -->
    <section id="skills" style="background: rgba(10, 10, 20, 0.6);">
        <h2 class="section-title">CAPABILITIES</h2>
        <div class="skills-grid">
            <div class="skill-card">
                <h3>WEB DEVELOPMENT</h3>
                <p>Full-stack systems. React, Node, and everything in between. I make the web bleed neon.</p>
            </div>
            <div class="skill-card">
                <h3>ETHICAL HACKING</h3>
                <p>Penetration testing, vulnerability assessment, social engineering countermeasures.</p>
            </div>
            <div class="skill-card">
                <h3>AUTOMATION</h3>
                <p>Scripts that never sleep. Python, Bash, Selenium — I make machines obey.</p>
            </div>
            <div class="skill-card">
                <h3>REVERSE ENGINEERING</h3>
                <p>Binary analysis, malware dissection, and cracking the unbreakable.</p>
            </div>
        </div>
    </section>
    
    <!-- Contact Section -->
    <section id="contact">
        <div class="contact-container">
            <h2 class="section-title">ESTABLISH CONNECTION</h2>
            
            <div class="terminal">
                &gt; INITIALIZING SECURE TUNNEL...<br>
                &gt; ENCRYPTION: AES-256 + QUANTUM<br>
                &gt; TARGET: TELEGRAM RELAY<br><br>
                <span style="color: #ff00ff;">CONNECTION STABLE</span>
            </div>
            
            <a href="https://t.me/Hackerwibes" target="_blank" class="neon-button">
                TRANSMIT MESSAGE →
            </a>
            
            <p style="margin-top: 60px; font-size: 1.3rem; opacity: 0.8;">
                No logs. No traces. Only signals in the dark.
            </p>
        </div>
    </section>
    
    <!-- Footer -->
    <footer>
        © 2026 HACKER X • ALL RIGHTS RESERVED • 
        <span style="color: #ff00ff;">NOTHING IS REAL</span>
    </footer>
    
    <script>
        // Typewriter already handled with CSS, but we can enhance
        function enhanceTypewriter() {
            const texts = [
                "Accessing the mainframe since 20XX...",
                "Breaching firewalls...",
                "Ghost protocol active..."
            ];
            let index = 0;
            const typewriter = document.getElementById('typewriter');
            
            setInterval(() => {
                typewriter.style.animation = 'none';
                typewriter.offsetHeight; // trigger reflow
                typewriter.textContent = texts[index];
                typewriter.style.animation = 'typing 3.5s steps(30, end) forwards, blink-caret .75s step-end infinite';
                index = (index + 1) % texts.length;
            }, 5000);
        }
        
        // Glitch on click
        document.addEventListener('click', (e) => {
            if (Math.random() > 0.7) {
                const glitch = document.querySelector('.glitch');
                if (glitch) {
                    glitch.style.animation = 'none';
                    setTimeout(() => {
                        glitch.style.animation = 'glitch 1.5s infinite';
                    }, 10);
                }
            }
        });
        
        // Keyboard hacker feel
        document.addEventListener('keydown', (e) => {
            if (e.key === '/' && document.activeElement.tagName !== "INPUT" && document.activeElement.tagName !== "TEXTAREA") {
                const contact = document.getElementById('contact');
                contact.scrollIntoView({ behavior: "smooth" });
            }
        });
        
        // Smooth scroll for nav links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                if (this.getAttribute('href') !== '#') {
                    e.preventDefault();
                    const target = document.querySelector(this.getAttribute('href'));
                    if (target) {
                        target.scrollIntoView({
                            behavior: 'smooth'
                        });
                    }
                }
            });
        });
        
        // Initialize everything
        window.onload = function() {
            enhanceTypewriter();
            
            // Random subtle glitch on hero every 8 seconds
            setInterval(() => {
                const glitch = document.querySelector('.glitch');
                if (glitch && Math.random() > 0.6) {
                    glitch.style.animationDuration = '0.4s';
                    setTimeout(() => {
                        glitch.style.animationDuration = '1.5s';
                    }, 800);
                }
            }, 8000);
            
            console.log('%cHACKER X SYSTEM ONLINE', 'color: #00ff9f; font-family: monospace; font-size: 14px;');
        };
    </script>
</body>
</html>
