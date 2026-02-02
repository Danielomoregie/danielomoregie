<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Daniel Omoregie</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --bg: #0a0a0a;
            --text: #e8e8e8;
            --accent: #00ff9d;
            --muted: #6b6b6b;
            --border: #1a1a1a;
        }

        body {
            font-family: 'Syne', sans-serif;
            background: var(--bg);
            color: var(--text);
            line-height: 1.6;
            overflow-x: hidden;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 4rem 2rem;
            min-height: 100vh;
        }

        .header {
            margin-bottom: 8rem;
            position: relative;
            padding-right: 200px;
        }

        @media (max-width: 768px) {
            .header {
                padding-right: 0;
                margin-bottom: 10rem;
            }
        }

        .name {
            font-size: clamp(3rem, 10vw, 5.5rem);
            font-weight: 700;
            letter-spacing: -0.03em;
            line-height: 0.9;
            margin-bottom: 1.5rem;
            opacity: 0;
            animation: fadeInUp 0.8s ease forwards;
        }

        .tagline {
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.95rem;
            color: var(--muted);
            letter-spacing: 0.02em;
            opacity: 0;
            animation: fadeInUp 0.8s ease 0.2s forwards;
            min-height: 1.5rem;
        }

        .tagline::after {
            content: '|';
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 50% { opacity: 1; }
            51%, 100% { opacity: 0; }
        }

        .status {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            margin-top: 2rem;
            padding: 0.5rem 1rem;
            border: 1px solid var(--border);
            border-radius: 100px;
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.8rem;
            opacity: 0;
            animation: fadeInUp 0.8s ease 0.4s forwards;
        }

        .status-dot {
            width: 6px;
            height: 6px;
            background: var(--accent);
            border-radius: 50%;
            animation: pulse 2s ease infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.4; }
        }

        .section {
            margin-bottom: 6rem;
            opacity: 0;
            animation: fadeInUp 0.8s ease 0.6s forwards;
        }

        .section-title {
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 0.15em;
            color: var(--muted);
            margin-bottom: 2rem;
            font-weight: 600;
        }

        .item {
            margin-bottom: 3rem;
            padding-bottom: 3rem;
            border-bottom: 1px solid var(--border);
            transition: all 0.3s ease;
        }

        .item:last-child {
            border-bottom: none;
            margin-bottom: 0;
            padding-bottom: 0;
        }

        .item:hover {
            transform: translateX(8px);
        }

        .item-header {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            margin-bottom: 0.5rem;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .experience-item {
            cursor: pointer;
            position: relative;
        }

        .experience-item .item-header {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .experience-item .item-header > div {
            flex: 1;
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .experience-item .item-title::after {
            content: '+';
            margin-left: 0.75rem;
            color: var(--accent);
            font-weight: 400;
            transition: transform 0.3s ease;
            display: inline-block;
        }

        .experience-item.active .item-title::after {
            transform: rotate(45deg);
        }

        .experience-details {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.4s ease, opacity 0.4s ease;
            opacity: 0;
        }

        .experience-item.active .experience-details {
            max-height: 500px;
            opacity: 1;
            margin-top: 1rem;
        }

        .experience-detail {
            padding-left: 1rem;
            margin-bottom: 0.75rem;
            border-left: 2px solid var(--border);
            color: var(--muted);
            font-size: 0.9rem;
            line-height: 1.7;
        }

        .item-title {
            font-size: 1.4rem;
            font-weight: 600;
            letter-spacing: -0.01em;
        }

        .item-meta {
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.75rem;
            color: var(--muted);
        }

        .item-desc {
            color: var(--muted);
            font-size: 0.95rem;
            line-height: 1.7;
        }

        .item-tag {
            display: inline-block;
            padding: 0.25rem 0.75rem;
            background: var(--border);
            border-radius: 4px;
            font-size: 0.75rem;
            margin-right: 0.5rem;
            margin-top: 0.75rem;
            font-family: 'JetBrains Mono', monospace;
            color: var(--accent);
        }

        .links {
            display: flex;
            gap: 2rem;
            flex-wrap: wrap;
        }

        .link {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            color: var(--text);
            text-decoration: none;
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            padding: 0.5rem 0;
            position: relative;
        }

        .link::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 1px;
            background: var(--accent);
            transition: width 0.3s ease;
        }

        .link:hover::after {
            width: 100%;
        }

        .link:hover {
            color: var(--accent);
        }

        .footer {
            margin-top: 8rem;
            padding-top: 2rem;
            border-top: 1px solid var(--border);
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.75rem;
            color: var(--muted);
            text-align: center;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @media (max-width: 768px) {
            .container {
                padding: 3rem 1.5rem;
            }

            .header {
                margin-bottom: 5rem;
            }

            .section {
                margin-bottom: 4rem;
            }

            .item-header {
                flex-direction: column;
                align-items: flex-start;
            }

            .links {
                gap: 1.5rem;
            }
        }

        /* Matrix rain background */
        #matrix-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
            opacity: 0.03;
        }

        /* Scan lines effect */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                0deg,
                rgba(0, 255, 157, 0.03) 0px,
                transparent 1px,
                transparent 2px,
                rgba(0, 255, 157, 0.03) 3px
            );
            z-index: -1;
            pointer-events: none;
            animation: scan 8s linear infinite;
        }

        @keyframes scan {
            0% { transform: translateY(0); }
            100% { transform: translateY(10px); }
        }

        /* Glitch effect on hover for name */
        .name {
            position: relative;
            display: inline-block;
        }

        .name:hover {
            animation: glitch 0.3s ease-in-out;
        }

        @keyframes glitch {
            0%, 100% {
                transform: translate(0);
            }
            20% {
                transform: translate(-2px, 2px);
            }
            40% {
                transform: translate(-2px, -2px);
            }
            60% {
                transform: translate(2px, 2px);
            }
            80% {
                transform: translate(2px, -2px);
            }
        }

        /* Terminal cursor effect */
        .terminal-cursor {
            display: inline-block;
            width: 10px;
            height: 20px;
            background: var(--accent);
            margin-left: 5px;
            animation: blink 1s infinite;
        }

        /* Grid accent lines */
        body::after {
            content: '';
            position: fixed;
            top: 0;
            left: 50%;
            width: 1px;
            height: 100%;
            background: linear-gradient(180deg,
                transparent 0%,
                var(--border) 10%,
                var(--border) 90%,
                transparent 100%
            );
            z-index: -1;
            opacity: 0.3;
        }

        /* Accent glow on interactive elements */
        .item:hover,
        .link:hover {
            text-shadow: 0 0 8px rgba(0, 255, 157, 0.3);
        }

        .status {
            position: relative;
            overflow: hidden;
        }

        .status::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                90deg,
                transparent,
                rgba(0, 255, 157, 0.1),
                transparent
            );
            animation: shimmer 3s infinite;
        }

        @keyframes shimmer {
            0% { left: -100%; }
            100% { left: 100%; }
        }

        /* Profile photo in top right */
        .profile-photo {
            position: fixed;
            top: 2rem;
            right: 2rem;
            width: 180px;
            height: auto;
            z-index: 100;
            opacity: 0;
            animation: fadeInUp 0.8s ease 0.8s forwards;
            filter: drop-shadow(0 0 20px rgba(0, 255, 157, 0.3));
            transition: all 0.3s ease;
        }

        .profile-photo:hover {
            transform: scale(1.05);
            filter: drop-shadow(0 0 30px rgba(0, 255, 157, 0.5));
        }

        /* Company logos */
        .company-logo {
            width: 50px;
            height: 50px;
            margin-right: 1rem;
            flex-shrink: 0;
            opacity: 0.8;
            transition: all 0.3s ease;
        }

        .experience-item:hover .company-logo {
            opacity: 1;
            transform: scale(1.1);
            filter: drop-shadow(0 0 10px rgba(0, 255, 157, 0.5));
        }

        .experience-item .item-header {
            display: flex;
            align-items: center;
        }

        @media (max-width: 768px) {
            .profile-photo {
                width: 120px;
                top: 1rem;
                right: 1rem;
            }

            .company-logo {
                width: 40px;
                height: 40px;
            }
        }
    </style>
</head>
<body>
    <canvas id="matrix-canvas"></canvas>
    <div class="container">
        <header class="header">
            <h1 class="name">Daniel<br>Omoregie</h1>
            <p class="tagline"><span id="typing-text"></span></p>
            <div class="status">
                <span class="status-dot"></span>
                <span>Incoming SWE Intern @ JP Morgan Chase</span>
            </div>
        </header>

        <section class="section">
            <h2 class="section-title">Experience</h2>

            <div class="item experience-item" onclick="toggleExperience(this)">
                <div class="item-header">
                    <svg class="company-logo" viewBox="0 0 60 60" xmlns="http://www.w3.org/2000/svg">
                        <!-- Outer circle -->
                        <circle cx="30" cy="30" r="27" fill="none" stroke="#00ff9d" stroke-width="1.5"/>

                        <!-- NASA text -->
                        <path d="M 12 35 L 12 20 M 12 20 L 19 33 M 19 20 L 19 35" fill="none" stroke="#00ff9d" stroke-width="1.3" stroke-linecap="round" stroke-linejoin="round"/>

                        <path d="M 22 22 L 27 22 M 24.5 22 L 24.5 35" fill="none" stroke="#00ff9d" stroke-width="1.3" stroke-linecap="round"/>

                        <path d="M 30 28 C 30 32 32.5 35 36 35 C 32 35 30 32 30 28 C 30 24 32 20 36 20 C 32.5 20 30 24 30 28" fill="none" stroke="#00ff9d" stroke-width="1.3"/>

                        <path d="M 39 22 L 44 22 M 41.5 22 L 41.5 35 M 39 28.5 L 44 28.5" fill="none" stroke="#00ff9d" stroke-width="1.3" stroke-linecap="round"/>

                        <!-- Orbital path -->
                        <ellipse cx="30" cy="30" rx="24" ry="9" fill="none" stroke="#00ff9d" stroke-width="1.2" transform="rotate(-18 30 30)"/>

                        <!-- Small star/planet -->
                        <circle cx="46" cy="20" r="1.8" fill="#00ff9d"/>

                        <!-- Chevron wing -->
                        <path d="M 12 42 L 30 38 L 48 42" fill="none" stroke="#00ff9d" stroke-width="1.2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                    <div style="flex: 1;">
                        <h3 class="item-title">NASA</h3>
                        <span class="item-meta">Jan - Aug 2025</span>
                    </div>
                </div>
                <div class="experience-details">
                    <div class="experience-detail">
                        Contributed production-level code to the ISS Fire Port application, completing a successful UI update independently and merging it into software now running on the International Space Station.
                    </div>
                    <div class="experience-detail">
                        Boosted usability by implementing an auto-scaling fix that reduced manual screen resolution adjustments by over 90%.
                    </div>
                    <div class="experience-detail">
                        Streamlined software deployment by troubleshooting security-related file transfer issues and securing workstation admin access to facilitate development.
                    </div>
                    <span class="item-tag">C++</span>
                    <span class="item-tag">SVN</span>
                    <span class="item-tag">ISS Operations</span>
                </div>
            </div>

            <div class="item experience-item" onclick="toggleExperience(this)">
                <div class="item-header">
                    <svg class="company-logo" viewBox="0 0 60 60" xmlns="http://www.w3.org/2000/svg">
                        <!-- Star -->
                        <path d="M 30 8 L 32.5 16 L 41 16 L 34 21 L 37 29 L 30 24 L 23 29 L 26 21 L 19 16 L 27.5 16 Z" fill="none" stroke="#00ff9d" stroke-width="1.3" stroke-linejoin="miter"/>

                        <!-- Torch flames -->
                        <path d="M 28 10 Q 28 6 30 4 Q 32 6 32 10" fill="none" stroke="#ff4444" stroke-width="1.2" stroke-linecap="round"/>
                        <path d="M 29 9 Q 29 7 30 6 Q 31 7 31 9" fill="none" stroke="#ff6666" stroke-width="1" stroke-linecap="round"/>

                        <!-- M -->
                        <path d="M 8 32 L 8 52 M 8 32 L 15 42 L 22 32 M 22 32 L 22 52" fill="none" stroke="#00ff9d" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"/>

                        <!-- I -->
                        <path d="M 26 32 L 26 52 M 24 32 L 28 32 M 24 52 L 28 52" fill="none" stroke="#00ff9d" stroke-width="2.2" stroke-linecap="round"/>

                        <!-- S -->
                        <path d="M 38 34 C 36 32 32 32 31 34 C 30 36 32 37 34 38 C 36 39 38 40 38 42 C 38 44 36 45 34 45 C 32 45 30 44 29 42" fill="none" stroke="#00ff9d" stroke-width="2.2" stroke-linecap="round"/>

                        <!-- D -->
                        <path d="M 42 32 L 42 52 M 42 32 C 48 32 52 36 52 42 C 52 48 48 52 42 52" fill="none" stroke="#00ff9d" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                    <div style="flex: 1;">
                        <h3 class="item-title">Mansfield ISD Technology</h3>
                        <span class="item-meta">Sept 2023 - Aug 2024</span>
                    </div>
                </div>
                <div class="experience-details">
                    <div class="experience-detail">
                        Engaged in backend development and debugging, enhancing application functionality and resolving critical issues.
                    </div>
                    <div class="experience-detail">
                        Assisted IT technicians with troubleshooting, maintenance, and system operations, contributing to a 15% reduction in tech support response time.
                    </div>
                    <div class="experience-detail">
                        Produced and edited a promotional video shown to over 10,000 K-12 students across the school district, resulting in a 25% increase in applications to the practicum program.
                    </div>
                    <span class="item-tag">Backend Development</span>
                    <span class="item-tag">IT Operations</span>
                    <span class="item-tag">Video Production</span>
                </div>
            </div>
        </section>

        <section class="section">
            <h2 class="section-title">Select Work</h2>

            <div class="item">
                <div class="item-header">
                    <h3 class="item-title">CreatorHub AI</h3>
                    <span class="item-meta">2024</span>
                </div>
                <p class="item-desc">
                    Personal productivity tool that automates video planning using AI. Cuts planning time by 50%, integrates with Notion and YouTube analytics.
                </p>
                <span class="item-tag">Python</span>
                <span class="item-tag">React</span>
                <span class="item-tag">OpenAI</span>
            </div>

            <div class="item">
                <div class="item-header">
                    <h3 class="item-title">Analytics Dashboard</h3>
                    <span class="item-meta">2023-24</span>
                </div>
                <p class="item-desc">
                    Built real-time data visualization dashboard for 50+ users at Mansfield ISD. Connected to ticketing software for streamlined reporting.
                </p>
                <span class="item-tag">Flask</span>
                <span class="item-tag">Python</span>
            </div>
        </section>

        <section class="section">
            <h2 class="section-title">Other</h2>

            <div class="item">
                <div class="item-header">
                    <h3 class="item-title">Excel with Dell</h3>
                    <span class="item-meta">2026</span>
                </div>
                <p class="item-desc">
                    Selected for Dell's mentorship program. Professional development, networking with Dell team members, and career guidance.
                </p>
            </div>

            <div class="item">
                <div class="item-header">
                    <h3 class="item-title">YouTube</h3>
                    <span class="item-meta">700k+ views • 12k+ subs</span>
                </div>
                <p class="item-desc">
                    Tech, internships, college life. @filmedbydaniel
                </p>
            </div>

            <div class="item">
                <div class="item-header">
                    <h3 class="item-title">NSBE Marketing Lead</h3>
                    <span class="item-meta">2024-Present</span>
                </div>
                <p class="item-desc">
                    Leading 6-person media team. Videos hit 10k+ views each, drove 1M+ Instagram visits.
                </p>
            </div>

            <div class="item">
                <div class="item-header">
                    <h3 class="item-title">Yahoo Industry Breakers</h3>
                    <span class="item-meta">2025</span>
                </div>
                <p class="item-desc">
                    Selected 1 of 25 nationwide for leadership program.
                </p>
            </div>
        </section>

        <section class="section">
            <h2 class="section-title">Links</h2>
            <div class="links">
                <a href="https://github.com/Danielomoregie" class="link" target="_blank">
                    <span>→</span>
                    <span>github</span>
                </a>
                <a href="https://linkedin.com/in/omoregiedaniel" class="link" target="_blank">
                    <span>→</span>
                    <span>linkedin</span>
                </a>
                <a href="https://youtube.com/@filmedbydaniel" class="link" target="_blank">
                    <span>→</span>
                    <span>youtube</span>
                </a>
                <a href="mailto:omoregiebusiness@gmail.com" class="link">
                    <span>→</span>
                    <span>email</span>
                </a>
            </div>
        </section>

        <footer class="footer">
            <p>© 2026 Daniel Omoregie</p>
        </footer>
    </div>

    <script>
        // Matrix rain effect
        const canvas = document.getElementById('matrix-canvas');
        const ctx = canvas.getContext('2d');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const letters = '01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン';
        const fontSize = 14;
        const columns = canvas.width / fontSize;

        const drops = [];
        for (let i = 0; i < columns; i++) {
            drops[i] = Math.random() * -100;
        }

        function drawMatrix() {
            ctx.fillStyle = 'rgba(10, 10, 10, 0.05)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            ctx.fillStyle = '#00ff9d';
            ctx.font = fontSize + 'px monospace';

            for (let i = 0; i < drops.length; i++) {
                const text = letters[Math.floor(Math.random() * letters.length)];
                ctx.fillText(text, i * fontSize, drops[i] * fontSize);

                if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
                    drops[i] = 0;
                }
                drops[i]++;
            }
        }

        setInterval(drawMatrix, 50);

        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });

        // Typing animation
        const phrases = ['software engineer', 'creator', 'problem solver'];
        let phraseIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        let typingSpeed = 100;
        const typingElement = document.getElementById('typing-text');

        function type() {
            const currentPhrase = phrases[phraseIndex];

            if (isDeleting) {
                typingElement.textContent = currentPhrase.substring(0, charIndex - 1);
                charIndex--;
                typingSpeed = 50;
            } else {
                typingElement.textContent = currentPhrase.substring(0, charIndex + 1);
                charIndex++;
                typingSpeed = 100;
            }

            if (!isDeleting && charIndex === currentPhrase.length) {
                // Pause at end of phrase
                typingSpeed = 2000;
                isDeleting = true;
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                phraseIndex = (phraseIndex + 1) % phrases.length;
                typingSpeed = 500;
            }

            setTimeout(type, typingSpeed);
        }

        // Start typing animation after page loads
        setTimeout(() => {
            type();
        }, 1000);

        // Toggle experience details
        function toggleExperience(element) {
            element.classList.toggle('active');
        }
    </script>
</body>
</html>
