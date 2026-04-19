<!DOCTYPE html>
<html lang="en" data-theme="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Priyanshu Kashyap | Portfolio</title>
    <style>
        /* === CSS VARIABLES & THEMING === */
        :root {
            /* Dark/Hacker Theme (Default) */
            --bg-base: #050505;
            --bg-grid: #0f1710;
            --text-main: #e2e8f0;
            --text-muted: #94a3b8;
            --accent: #00ff66;
            --accent-glow: rgba(0, 255, 102, 0.2);
            --glass-bg: rgba(20, 25, 20, 0.6);
            --glass-border: rgba(0, 255, 102, 0.15);
            --card-bg: rgba(10, 15, 10, 0.8);
            --modal-bg: rgba(0, 0, 0, 0.95);
        }

        [data-theme="light"] {
            /* Light/Modern Theme */
            --bg-base: #f0fdf4;
            --bg-grid: #e2e8f0;
            --text-main: #0f172a;
            --text-muted: #475569;
            --accent: #16a34a;
            --accent-glow: rgba(22, 163, 74, 0.2);
            --glass-bg: rgba(255, 255, 255, 0.7);
            --glass-border: rgba(22, 163, 74, 0.2);
            --card-bg: rgba(255, 255, 255, 0.9);
            --modal-bg: rgba(255, 255, 255, 0.95);
        }

        /* === RESET & BASE === */
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Segoe UI', system-ui, -apple-system, sans-serif; scroll-behavior: smooth; }
        
        body {
            background-color: var(--bg-base);
            color: var(--text-main);
            overflow-x: hidden;
            transition: background-color 0.4s ease, color 0.4s ease;
            background-image: linear-gradient(var(--glass-border) 1px, transparent 1px), linear-gradient(90deg, var(--glass-border) 1px, transparent 1px);
            background-size: 30px 30px;
            background-attachment: fixed;
        }

        body.locked { overflow: hidden; }
        a { text-decoration: none; color: inherit; }
        ul { list-style: none; }
        
        .container { max-width: 1200px; margin: 0 auto; padding: 0 20px; }
        section { padding: 100px 0; }
        
        .section-title {
            font-size: 2.5rem; text-align: center; margin-bottom: 60px;
            color: var(--accent); text-shadow: 0 0 10px var(--accent-glow);
            text-transform: uppercase; letter-spacing: 2px; font-weight: 800;
        }
        .section-title::after { content: '_'; animation: blink 1s step-end infinite; }

        /* === GLASSMORPHISM === */
        .glass {
            background: var(--glass-bg);
            backdrop-filter: blur(12px); -webkit-backdrop-filter: blur(12px);
            border: 1px solid var(--glass-border); border-radius: 16px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
        }

        /* === BUTTONS === */
        .btn {
            display: inline-flex; align-items: center; justify-content: center;
            gap: 10px; padding: 14px 28px; border-radius: 10px;
            font-weight: 600; cursor: pointer; transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid var(--accent); position: relative; overflow: hidden; z-index: 1; letter-spacing: 0.5px;
        }
        .btn-primary { background: var(--accent); color: var(--bg-base); box-shadow: 0 0 15px var(--accent-glow); }
        .btn-primary:hover { background: var(--bg-base); color: var(--accent); box-shadow: 0 0 30px var(--accent), inset 0 0 10px var(--accent); transform: translateY(-3px) scale(1.02); }
        .btn-outline { background: transparent; color: var(--accent); }
        .btn-outline:hover { background: var(--accent-glow); box-shadow: 0 0 20px var(--accent-glow); transform: translateY(-3px) scale(1.02); }
        .btn:active { transform: translateY(1px) scale(0.98); }

        /* === ANIMATIONS === */
        @keyframes blink { 50% { opacity: 0; } }
        @keyframes fadeTransition { 0% { opacity: 0; transform: translateY(-5px); } 100% { opacity: 1; transform: translateY(0); } }
        @keyframes float { 0% { transform: translateY(0px); } 50% { transform: translateY(-15px); } 100% { transform: translateY(0px); } }
        @keyframes spinPulse { 0% { transform: rotate(0deg) scale(1); box-shadow: 0 0 15px var(--accent-glow); } 50% { transform: rotate(180deg) scale(1.05); box-shadow: 0 0 35px var(--accent); } 100% { transform: rotate(360deg) scale(1); box-shadow: 0 0 15px var(--accent-glow); } }
        @keyframes counterSpin { 100% { transform: rotate(-360deg); } }
        @keyframes shake { 10%, 90% { transform: translate3d(-1px, 0, 0); } 20%, 80% { transform: translate3d(2px, 0, 0); } 30%, 50%, 70% { transform: translate3d(-4px, 0, 0); } 40%, 60% { transform: translate3d(4px, 0, 0); } }

        .animate-on-scroll { opacity: 0; transform: translateY(40px); transition: opacity 0.8s ease-out, transform 0.8s ease-out; }
        .animate-on-scroll.visible { opacity: 1; transform: translateY(0); }
        .fade-text { animation: fadeTransition 0.4s ease-out forwards; }
        .i18n { display: inline-block; }

        /* === NAVBAR === */
        nav { position: fixed; top: 0; left: 0; width: 100%; padding: 20px 0; z-index: 1000; transition: all 0.4s ease; }
        nav.scrolled { padding: 12px 0; background: var(--glass-bg); backdrop-filter: blur(20px); border-bottom: 1px solid var(--glass-border); box-shadow: 0 4px 30px rgba(0,0,0,0.1); }
        .nav-content { display: flex; justify-content: space-between; align-items: center; }
        .logo { font-size: 1.6rem; font-weight: 800; color: var(--text-main); letter-spacing: 1px; }
        .logo span { color: var(--accent); }
        .nav-links { display: flex; gap: 30px; align-items: center; }
        .nav-links a { font-weight: 500; transition: color 0.3s ease; position: relative; }
        .nav-links a::after { content: ''; position: absolute; width: 0; height: 2px; bottom: -4px; left: 0; background: var(--accent); transition: width 0.3s; }
        .nav-links a:hover::after { width: 100%; }
        .nav-links a:hover { color: var(--accent); }
        .nav-controls { display: flex; gap: 15px; align-items: center; }
        .nav-btn { background: transparent; border: 1px solid var(--glass-border); color: var(--text-main); cursor: pointer; padding: 6px 12px; border-radius: 6px; font-weight: 600; transition: all 0.3s; display: flex; align-items: center; gap: 5px; }
        .nav-btn:hover { background: var(--accent-glow); border-color: var(--accent); color: var(--accent); }

        /* === HERO SECTION === */
        #home { min-height: 100vh; display: flex; align-items: center; justify-content: center; text-align: center; padding-top: 80px; flex-direction: column;}
        .hero-img-wrapper { position: relative; width: 220px; height: 220px; margin: 0 auto 35px; border-radius: 50%; padding: 6px; background: conic-gradient(from 0deg, transparent, var(--accent), transparent, var(--accent)); animation: spinPulse 6s linear infinite; }
        .hero-img-inner { width: 100%; height: 100%; border-radius: 50%; overflow: hidden; background: var(--bg-base); animation: counterSpin 6s linear infinite; display: flex; align-items: center; justify-content: center; }
        .hero-img-inner img { width: 100%; height: 100%; object-fit: cover; object-position: center 20%; }
        .hero-name { font-size: 3.8rem; font-weight: 800; margin-bottom: 10px; letter-spacing: -1px; }
        .hero-tagline { font-size: 1.5rem; color: var(--text-muted); margin-bottom: 20px; }
        .typing-container { font-family: monospace; font-size: 1.3rem; color: var(--accent); min-height: 35px; margin-bottom: 40px; }
        .hero-buttons { display: flex; gap: 20px; justify-content: center; flex-wrap: wrap; }

        /* === ABOUT SECTION === */
        .about-grid { display: grid; grid-template-columns: 1fr 2fr; gap: 50px; align-items: center; }
        .about-img { width: 100%; max-width: 320px; border-radius: 20px; border: 2px solid var(--glass-border); box-shadow: 0 10px 40px rgba(0,0,0,0.4); animation: float 6s ease-in-out infinite; object-fit: cover; }
        .about-text { line-height: 1.8; color: var(--text-muted); font-size: 1.15rem; }
        .about-text p { margin-bottom: 18px; }
        .highlight { color: var(--accent); font-weight: 600; }
        .mission-box { margin-top: 30px; padding: 25px; border-left: 4px solid var(--accent); transition: transform 0.3s; }
        .mission-box:hover { transform: translateX(10px); background: var(--accent-glow); }

        /* === FEATURED PROJECT === */
        .featured-card { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; padding: 50px; align-items: center; }
        .featured-content h3 { font-size: 2.8rem; color: var(--accent); margin-bottom: 15px; }
        .featured-features { margin: 25px 0; display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        .featured-features li { display: flex; align-items: center; gap: 10px; color: var(--text-main); font-weight: 500; }
        .featured-features li::before { content: '✓'; color: var(--accent); font-weight: bold; background: var(--accent-glow); width: 24px; height: 24px; display: flex; align-items: center; justify-content: center; border-radius: 50%; }

        /* === PROJECTS GRID === */
        .projects-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); gap: 35px; }
        .project-card { padding: 30px; transition: all 0.4s ease; display: flex; flex-direction: column; height: 100%; }
        .project-card:hover { transform: translateY(-12px); border-color: var(--accent); box-shadow: 0 15px 35px var(--accent-glow); }
        .project-icon { font-size: 2.5rem; color: var(--accent); margin-bottom: 25px; transition: transform 0.3s; }
        .project-card:hover .project-icon { transform: scale(1.1); }
        .project-title { font-size: 1.4rem; margin-bottom: 15px; color: var(--text-main); }

        /* === SKILLS & SERVICES === */
        .skills-container { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 40px; }
        .skill-category { padding: 35px; transition: transform 0.3s; }
        .skill-category:hover { transform: translateY(-5px); border-color: var(--accent); }
        .skill-category h3 { margin-bottom: 25px; color: var(--accent); display: flex; align-items: center; gap: 10px; }
        .skill-item { margin-bottom: 20px; }
        .skill-info { display: flex; justify-content: space-between; margin-bottom: 8px; font-size: 0.95rem; font-weight: 500; }
        .progress-bar { width: 100%; height: 10px; background: rgba(255,255,255,0.05); border-radius: 5px; overflow: hidden; border: 1px solid var(--glass-border); }
        .progress-fill { height: 100%; background: var(--accent); width: 0; transition: width 1.5s cubic-bezier(0.1, 0.5, 0.1, 1); box-shadow: 0 0 15px var(--accent); }
        
        .services-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 35px; }
        .service-card { padding: 40px 30px; text-align: center; transition: all 0.4s; }
        .service-card:hover { transform: translateY(-10px); border-color: var(--accent); background: var(--accent-glow); }
        .service-icon { width: 70px; height: 70px; background: rgba(0,255,102,0.1); border: 1px solid var(--accent); border-radius: 50%; display: flex; align-items: center; justify-content: center; margin: 0 auto 25px; color: var(--accent); transition: transform 0.3s; }
        .service-card:hover .service-icon { transform: rotateY(180deg); }

        /* === SOCIAL MEDIA SECTION === */
        .social-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(100px, 1fr)); gap: 20px; max-width: 900px; margin: 0 auto; }
        .social-item { display: flex; flex-direction: column; align-items: center; gap: 12px; padding: 25px 15px; border-radius: 16px; transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1); text-align: center; cursor: pointer; }
        .social-item:hover { transform: translateY(-8px); background: var(--glass-bg); border-color: var(--accent); box-shadow: 0 10px 25px var(--accent-glow); }
        .social-item svg { width: 36px; height: 36px; stroke: var(--text-main); stroke-width: 1.5; transition: stroke 0.3s, transform 0.3s; fill: none; }
        .social-item:hover svg { stroke: var(--accent); transform: scale(1.15); }
        .social-item span { font-size: 0.9rem; font-weight: 600; color: var(--text-muted); transition: color 0.3s; }
        .social-item:hover span { color: var(--text-main); }

        /* === MINI GAME === */
        .runner-container { max-width: 800px; margin: 0 auto; border: 1px solid var(--glass-border); border-radius: 16px; overflow: hidden; position: relative; background: rgba(0, 0, 0, 0.4); transition: box-shadow 0.4s ease; }
        .runner-container:hover { box-shadow: 0 10px 40px var(--accent-glow); border-color: var(--accent); }
        .runner-ui-top { display: flex; justify-content: space-between; padding: 15px 25px; background: rgba(0,0,0,0.6); border-bottom: 1px solid var(--glass-border); font-family: monospace; font-size: 1.2rem; color: var(--accent); letter-spacing: 1px; }
        .canvas-wrapper { position: relative; width: 100%; height: 0; padding-bottom: 37.5%; background-image: linear-gradient(rgba(0, 255, 102, 0.05) 1px, transparent 1px), linear-gradient(90deg, rgba(0, 255, 102, 0.05) 1px, transparent 1px); background-size: 20px 20px; }
        #runner-canvas { position: absolute; top: 0; left: 0; width: 100%; height: 100%; display: block; touch-action: none; }
        .runner-overlay { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.85); backdrop-filter: blur(5px); display: flex; flex-direction: column; align-items: center; justify-content: center; text-align: center; z-index: 10; transition: opacity 0.3s ease; padding: 20px; }
        .runner-overlay h3 { font-size: 2rem; color: var(--accent); margin-bottom: 10px; font-family: monospace; }
        .runner-cta-box { margin-top: 20px; padding: 15px; border: 1px dashed var(--accent); border-radius: 10px; background: var(--accent-glow); animation: fadeTransition 0.5s ease-out; }

        /* === TIMELINE === */
        .timeline { position: relative; max-width: 800px; margin: 0 auto; }
        .timeline::before { content: ''; position: absolute; width: 2px; background: var(--glass-border); top: 0; bottom: 0; left: 50%; transform: translateX(-50%); }
        .timeline-item { padding: 40px 0; position: relative; width: 50%; }
        .timeline-item:nth-child(odd) { left: 0; padding-right: 50px; text-align: right; }
        .timeline-item:nth-child(even) { left: 50%; padding-left: 50px; }
        .timeline-dot { position: absolute; width: 24px; height: 24px; background: var(--accent); border-radius: 50%; top: 50%; transform: translateY(-50%); box-shadow: 0 0 20px var(--accent); border: 4px solid var(--bg-base); z-index: 2; }
        .timeline-item:nth-child(odd) .timeline-dot { right: -12px; }
        .timeline-item:nth-child(even) .timeline-dot { left: -12px; }

        /* === CONTACT & FOOTER === */
        .contact-box { padding: 60px; text-align: center; max-width: 800px; margin: 0 auto; transition: border-color 0.4s; }
        .contact-box:hover { border-color: var(--accent); }
        .contact-buttons { display: flex; gap: 20px; flex-wrap: wrap; justify-content: center; margin-top: 30px; }
        .contact-email { font-family: monospace; font-size: 1.2rem; color: var(--accent); margin: 20px 0; padding: 15px; background: rgba(0,255,102,0.05); border-radius: 8px; display: inline-block; border: 1px dashed var(--glass-border); }
        footer { text-align: center; padding: 40px; border-top: 1px solid var(--glass-border); color: var(--text-muted); margin-top: 50px; background: rgba(0,0,0,0.3); }

        /* MODAL */
        #unlock-modal { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: var(--modal-bg); z-index: 9999; display: flex; align-items: center; justify-content: center; backdrop-filter: blur(25px); transition: opacity 0.5s ease; }
        #code-container input { width: 50px; height: 60px; font-size: 28px; text-align: center; background: rgba(0,0,0,0.5); border: 2px solid var(--glass-border); color: var(--accent); border-radius: 10px; outline: none; transition: all 0.3s; font-family: monospace; }
        #code-container input:focus { border-color: var(--accent); box-shadow: 0 0 20px var(--accent-glow); transform: translateY(-2px); }

        .floating-group { position: fixed; bottom: 30px; right: 30px; display: flex; flex-direction: column; gap: 15px; z-index: 100; }
        .floating-btn { width: 55px; height: 55px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 1.5rem; cursor: pointer; transition: all 0.3s; opacity: 0; visibility: hidden; box-shadow: 0 5px 20px rgba(0,0,0,0.5); }
        .floating-btn.visible { opacity: 1; visibility: visible; }
        .floating-btn:hover { transform: translateY(-5px) scale(1.05); }
        .fab-up { background: var(--card-bg); color: var(--text-main); border: 1px solid var(--glass-border); }
        .fab-wa { background: #25D366; color: #fff; opacity: 1; visibility: visible; box-shadow: 0 5px 20px rgba(37, 211, 102, 0.4); animation: float 4s ease-in-out infinite; }

        @media (max-width: 900px) {
            .about-grid, .featured-card { grid-template-columns: 1fr; text-align: center; padding: 30px; }
            .about-img { margin: 0 auto; }
            .timeline::before { left: 30px; }
            .timeline-item { width: 100%; padding-left: 70px !important; text-align: left !important; }
            .timeline-item:nth-child(odd), .timeline-item:nth-child(even) { left: 0; }
            .timeline-dot { left: 18px !important; right: auto !important; }
            .hero-name { font-size: 2.8rem; }
            .hero-img-wrapper { width: 180px; height: 180px; }
        }
        @media (max-width: 600px) {
            .nav-links { display: none; }
            .hero-buttons { flex-direction: column; width: 100%; padding: 0 20px; }
            .hero-buttons .btn { width: 100%; }
            .featured-features { grid-template-columns: 1fr; }
            .code-inputs input { width: 40px; height: 50px; font-size: 22px; }
            .contact-box { padding: 30px 15px; }
        }
    </style>
</head>
<body class="locked">

    <!-- 6-DIGIT UNLOCK MODAL -->
    <div id="unlock-modal">
        <div class="unlock-box glass" style="padding: 50px; text-align: center; max-width: 450px; width: 90%;">
            <svg fill="none" height="48" stroke="var(--accent)" stroke-width="2" style="margin-bottom: 20px; filter: drop-shadow(0 0 10px var(--accent-glow));" viewBox="0 0 24 24" width="48">
                <rect height="11" rx="2" ry="2" width="18" x="3" y="11"/>
                <path d="M7 11V7a5 5 0 0 1 10 0v4"/>
            </svg>
            <h2 style="color: var(--accent); margin-bottom: 10px; font-family: monospace; letter-spacing: 2px;">SYSTEM_LOCKED</h2>
            <p class="i18n" data-en="ENTER 6-DIGIT ACCESS CODE" data-hi="6-अंकीय एक्सेस कोड दर्ज करें" style="color: var(--text-muted); margin-bottom: 30px; font-size: 0.95rem; font-weight: 500;">ENTER 6-DIGIT ACCESS CODE</p>
            <div class="code-inputs" id="code-container" style="display: flex; gap: 12px; justify-content: center; margin-bottom: 30px;">
                <input autofocus="autofocus" maxlength="1" pattern="[0-9]" type="text"/>
                <input maxlength="1" pattern="[0-9]" type="text"/>
                <input maxlength="1" pattern="[0-9]" type="text"/>
                <input maxlength="1" pattern="[0-9]" type="text"/>
                <input maxlength="1" pattern="[0-9]" type="text"/>
                <input maxlength="1" pattern="[0-9]" type="text"/>
            </div>
            <button class="btn btn-primary" onclick="verifyCode()" style="width: 100%;">
                <span class="i18n" data-en="UNLOCK PORTFOLIO" data-hi="पोर्टफोलियो अनलॉक करें">UNLOCK PORTFOLIO</span>
            </button>
            <p class="i18n" data-en="Hint: Any 6 digits will work for demo" data-hi="संकेत: डेमो के लिए कोई भी 6 अंक काम करेंगे" style="margin-top: 20px; font-size: 0.85rem; color: var(--text-muted);">Hint: Any 6 digits will work for demo</p>
        </div>
    </div>

    <!-- NAVBAR -->
    <nav id="navbar">
        <div class="container nav-content">
            <a class="logo" href="#home">PK<span>.</span>dev</a>
            <ul class="nav-links">
                <li><a class="i18n" data-en="About" data-hi="मेरे बारे में" href="#about">About</a></li>
                <li><a class="i18n" data-en="Projects" data-hi="प्रोजेक्ट्स" href="#projects">Projects</a></li>
                <li><a class="i18n" data-en="Skills" data-hi="कौशल" href="#skills">Skills</a></li>
                <li><a class="i18n" data-en="Services" data-hi="सेवाएं" href="#services">Services</a></li>
                <li><a class="i18n" data-en="Socials" data-hi="सोशल मीडिया" href="#socials">Socials</a></li>
                <li><a class="i18n" data-en="Game" data-hi="गेम" href="#minigame">Game</a></li>
                <li><a class="i18n" data-en="Contact" data-hi="संपर्क" href="#contact">Contact</a></li>
            </ul>
            <div class="nav-controls">
                <button class="nav-btn" onclick="toggleLanguage()" title="Toggle Language">
                    <svg fill="none" height="18" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="18"><circle cx="12" cy="12" r="10"/><line x1="2" x2="22" y1="12" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>
                    <span id="lang-text">हिंदी</span>
                </button>
                <button class="nav-btn" id="theme-btn" title="Toggle Theme (D)">
                    <svg fill="none" height="18" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="18"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>
                </button>
            </div>
        </div>
    </nav>

    <!-- MAIN PORTFOLIO SECTIONS -->
    
    <!-- 1. HERO SECTION -->
    <section id="home">
        <div class="container animate-on-scroll">
            <div class="hero-img-wrapper">
                <div class="hero-img-inner">
                    <img alt="Priyanshu Kashyap" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTXO38b3_QYI0zI__CI1t3YdI3lLXRlN5W6sw&s"/>
                </div>
            </div>
            
            <h1 class="hero-name">Priyanshu Kashyap</h1>
            <p class="hero-tagline">Self-Taught Developer | App &amp; System Builder</p>

            <div class="typing-container" id="typing-text"></div>
            
            <div class="hero-buttons">
                <a class="btn btn-primary" href="#projects">
                    <svg fill="none" height="20" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="20"><path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"/><path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"/></svg>
                    <span class="i18n" data-en="View Projects" data-hi="प्रोजेक्ट्स देखें">View Projects</span>
                </a>
                <a class="btn btn-outline" href="#contact">
                    <svg fill="none" height="20" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="20"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
                    <span class="i18n" data-en="Contact Me" data-hi="संपर्क करें">Contact Me</span>
                </a>
            </div>
            
        </div>
    </section>

    <!-- 2. ABOUT SECTION -->
    <section id="about" style="background: rgba(0,0,0,0.15);">
        <div class="container">
            <h2 class="section-title animate-on-scroll i18n" data-en="Initializing... _About" data-hi="आरंभ हो रहा है... _मेरे बारे में">Initializing... _About</h2>
            <div class="about-grid">
                <div class="animate-on-scroll">
                    <img alt="Priyanshu" class="about-img" src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTXO38b3_QYI0zI__CI1t3YdI3lLXRlN5W6sw&s"/>
                </div>
                <div class="about-text animate-on-scroll" style="transition-delay: 0.2s;">
                    <p class="i18n" data-en='Hello! I am <span class="highlight">Priyanshu Kashyap</span>, hailing from a middle-class family in Lakhimpur Kheri, Uttar Pradesh.' data-hi='नमस्ते! मैं <span class="highlight">प्रियांशु कश्यप</span> हूँ, जो लखीमपुर खीरी, उत्तर प्रदेश के एक मध्यमवर्गीय परिवार से हूँ।'>Hello! I am <span class="highlight">Priyanshu Kashyap</span>, hailing from a middle-class family in Lakhimpur Kheri, Uttar Pradesh.</p>
                    <p class="i18n" data-en="Due to financial constraints, I could only pursue my formal education up to class 12. However, my passion for technology led me to a computer shop where I spent 8 years (2016–2024) practically mastering computer systems and coding." data-hi="आर्थिक तंगी के कारण, मैं केवल 12वीं कक्षा तक ही औपचारिक शिक्षा प्राप्त कर सका। हालाँकि, तकनीक के प्रति मेरे जुनून ने मुझे एक कंप्यूटर की दुकान तक पहुँचाया जहाँ मैंने 8 साल (2016–2024) कंप्यूटर सिस्टम और कोडिंग को व्यावहारिक रूप से सीखने में बिताए।">Due to financial constraints, I could only pursue my formal education up to class 12. However, my passion for technology led me to a computer shop where I spent 8 years (2016–2024) practically mastering computer systems and coding.</p>
                    <p class="i18n" data-en="Life wasn't a straight path. I balanced my time working night shifts in a factory and day shifts at the shop. It was during these intense struggles that I began building real-world projects, turning adversity into opportunity." data-hi="जीवन का रास्ता सीधा नहीं था। मैंने एक कारखाने में रात की पाली और दुकान पर दिन की पाली में काम करते हुए अपना समय संतुलित किया। इन्हीं कड़े संघर्षों के दौरान मैंने वास्तविक दुनिया के प्रोजेक्ट बनाना शुरू किया और विपरीत परिस्थितियों को अवसर में बदल दिया।">Life wasn't a straight path. I balanced my time working night shifts in a factory and day shifts at the shop. It was during these intense struggles that I began building real-world projects, turning adversity into opportunity.</p>
                    <div class="mission-box glass">
                        <strong>🎯 <span class="i18n" data-en="My Mission:" data-hi="मेरा मिशन:">My Mission:</span></strong><br/>
                        <span class="i18n" data-en="To build simple, accessible, and highly useful tools that solve everyday problems for everyone." data-hi="सरल, सुलभ और अत्यधिक उपयोगी उपकरण बनाना जो सभी के लिए रोजमर्रा की समस्याओं को हल करें।">To build simple, accessible, and highly useful tools that solve everyday problems for everyone.</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 3. FEATURED PROJECT SECTION -->
    <section id="featured">
        <div class="container">
            <h2 class="section-title animate-on-scroll i18n" data-en="Featured_System" data-hi="प्रमुख_सिस्टम">Featured_System</h2>
            <div class="featured-card glass animate-on-scroll">
                <div class="featured-content">
                    <h3>KP Flux Share</h3>
                    <p class="i18n" data-en="A seamless, secure, and fast file-sharing ecosystem designed for simplicity and speed. No accounts needed." data-hi="सरलता और गति के लिए डिज़ाइन किया गया एक सहज, सुरक्षित और तेज़ फ़ाइल-शेयरिंग इकोसिस्टम। कोई अकाउंट आवश्यक नहीं।" style="color: var(--text-muted); margin-bottom: 25px; font-size: 1.1rem; line-height: 1.6;">A seamless, secure, and fast file-sharing ecosystem designed for simplicity and speed. No accounts needed.</p>
                    <ul class="featured-features">
                        <li class="i18n" data-en="6-digit code system" data-hi="6-अंकीय कोड प्रणाली">6-digit code system</li>
                        <li class="i18n" data-en="No login required" data-hi="लॉगिन की आवश्यकता नहीं">No login required</li>
                        <li class="i18n" data-en="QR code sharing" data-hi="क्यूआर कोड शेयरिंग">QR code sharing</li>
                        <li class="i18n" data-en="Shareable links" data-hi="शेयर करने योग्य लिंक">Shareable links</li>
                        <li class="i18n" data-en="Expiry system" data-hi="समाप्ति प्रणाली">Expiry system</li>
                    </ul>
                    <div style="margin-top: 40px; display: flex; gap: 15px; flex-wrap: wrap;">
                        <a class="btn btn-primary" href="https://kpflux.blogspot.com" target="_blank">
                            <svg fill="none" height="20" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="20"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" x2="21" y1="14" y2="3"/></svg>
                            <span class="i18n" data-en="Open KP Flux Share" data-hi="केपी फ्लक्स शेयर खोलें">Open KP Flux Share</span>
                        </a>
                        <a class="btn btn-outline" href="#livedemo">
                            <svg fill="none" height="20" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="20"><circle cx="12" cy="12" r="10"/><polygon points="10 8 16 12 10 16 10 8"/></svg>
                            <span class="i18n" data-en="Live Demo" data-hi="लाइव डेमो">Live Demo</span>
                        </a>
                    </div>
                </div>
                <div class="featured-image" style="text-align: center;">
                    <svg fill="none" height="250" stroke="var(--accent)" stroke-linecap="round" stroke-linejoin="round" stroke-width="1" style="filter: drop-shadow(0 0 30px var(--accent-glow)); animation: float 5s ease-in-out infinite;" viewBox="0 0 24 24" width="250">
                        <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
                        <polyline points="17 8 12 3 7 8"/>
                        <line x1="12" x2="12" y1="3" y2="15"/>
                    </svg>
                </div>
            </div>
        </div>
    </section>

    <!-- 4. ALL PROJECTS SECTION -->
    <section id="projects" style="background: rgba(0,0,0,0.15);">
        <div class="container">
            <h2 class="section-title animate-on-scroll i18n" data-en="Deployed_Modules" data-hi="तैनात_मॉड्यूल">Deployed_Modules</h2>
            <div class="projects-grid" id="projects-container"></div>
        </div>
    </section>

    <!-- 5. SKILLS SECTION -->
    <section id="skills">
        <div class="container">
            <h2 class="section-title animate-on-scroll i18n" data-en="System_Capabilities" data-hi="सिस्टम_क्षमताएं">System_Capabilities</h2>
            <div class="skills-container">
                <div class="skill-category glass animate-on-scroll">
                    <h3><svg fill="none" height="24" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="24"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg> <span class="i18n" data-en="Core Engine" data-hi="कोर इंजन">Core Engine</span></h3>
                    <div class="skill-item">
                        <div class="skill-info"><span>HTML5</span><span>95%</span></div>
                        <div class="progress-bar"><div class="progress-fill" data-width="95%"></div></div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-info"><span>CSS3 / UI Design</span><span>90%</span></div>
                        <div class="progress-bar"><div class="progress-fill" data-width="90%"></div></div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-info"><span>JavaScript (ES6+)</span><span>85%</span></div>
                        <div class="progress-bar"><div class="progress-fill" data-width="85%"></div></div>
                    </div>
                </div>
                <div class="skill-category glass animate-on-scroll" style="transition-delay: 0.1s">
                    <h3><svg fill="none" height="24" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="24"><ellipse cx="12" cy="5" rx="9" ry="3"/><path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/></svg> <span class="i18n" data-en="Backend &amp; Database" data-hi="बैकएंड और डेटाबेस">Backend &amp; Database</span></h3>
                    <div class="skill-item">
                        <div class="skill-info"><span>Firebase</span><span>90%</span></div>
                        <div class="progress-bar"><div class="progress-fill" data-width="90%"></div></div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-info"><span>Supabase</span><span>85%</span></div>
                        <div class="progress-bar"><div class="progress-fill" data-width="85%"></div></div>
                    </div>
                </div>
                <div class="skill-category glass animate-on-scroll" style="transition-delay: 0.2s">
                    <h3><svg fill="none" height="24" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="24"><path d="M2 16.1A5 5 0 0 1 5.9 20M2 12.05A9 9 0 0 1 9.95 20M2 8V6a2 2 0 0 1 2-2h16a2 2 0 0 1 2 2v12a2 2 0 0 1-2 2h-6"/><line x1="2" x2="2.01" y1="20" y2="20"/></svg> <span class="i18n" data-en="Integrations &amp; Other" data-hi="एकीकरण और अन्य">Integrations &amp; Other</span></h3>
                    <div class="skill-item">
                        <div class="skill-info"><span>Cloudinary</span><span>80%</span></div>
                        <div class="progress-bar"><div class="progress-fill" data-width="80%"></div></div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-info"><span>API Integration</span><span>85%</span></div>
                        <div class="progress-bar"><div class="progress-fill" data-width="85%"></div></div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-info"><span>UI/UX Principles</span><span>88%</span></div>
                        <div class="progress-bar"><div class="progress-fill" data-width="88%"></div></div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 6. SERVICES SECTION -->
    <section id="services" style="background: rgba(0,0,0,0.15);">
        <div class="container">
            <h2 class="section-title animate-on-scroll i18n" data-en="Execute_Services" data-hi="निष्पादन_सेवाएं">Execute_Services</h2>
            <div class="services-grid">
                <div class="service-card glass animate-on-scroll">
                    <div class="service-icon"><svg fill="none" height="30" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="30"><rect height="14" rx="2" ry="2" width="20" x="2" y="3"/><line x1="8" x2="16" y1="21" y2="21"/><line x1="12" x2="12" y1="17" y2="21"/></svg></div>
                    <h3 class="i18n" data-en="Web App Dev" data-hi="वेब ऐप विकास">Web App Dev</h3>
                    <p class="i18n" data-en="Custom, responsive web applications built for speed and usability." data-hi="गति और उपयोगिता के लिए बनाए गए कस्टम, उत्तरदायी वेब एप्लिकेशन।" style="color: var(--text-muted); margin-top: 15px; font-size: 0.95rem; line-height: 1.5;">Custom, responsive web applications built for speed and usability.</p>
                </div>
                <div class="service-card glass animate-on-scroll" style="transition-delay: 0.1s">
                    <div class="service-icon"><svg fill="none" height="30" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="30"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" x2="12" y1="3" y2="15"/></svg></div>
                    <h3 class="i18n" data-en="File Sharing Systems" data-hi="फ़ाइल शेयरिंग सिस्टम">File Sharing Systems</h3>
                    <p class="i18n" data-en="Secure, fast, and anonymous file transfer architecture." data-hi="सुरक्षित, तेज़ और अनाम फ़ाइल स्थानांतरण वास्तुकला।" style="color: var(--text-muted); margin-top: 15px; font-size: 0.95rem; line-height: 1.5;">Secure, fast, and anonymous file transfer architecture.</p>
                </div>
                <div class="service-card glass animate-on-scroll" style="transition-delay: 0.2s">
                    <div class="service-icon"><svg fill="none" height="30" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="30"><path d="M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 0 1-7.6 4.7 8.38 8.38 0 0 1-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 0 1-.9-3.8 8.5 8.5 0 0 1 4.7-7.6 8.38 8.38 0 0 1 3.8-.9h.5a8.48 8.48 0 0 1 8 8v.5z"/></svg></div>
                    <h3 class="i18n" data-en="Chat Applications" data-hi="चैट एप्लिकेशन">Chat Applications</h3>
                    <p class="i18n" data-en="Real-time communication platforms using WebSocket/Firebase." data-hi="वेबसोकेट/फायरबेस का उपयोग करके रीयल-टाइम संचार प्लेटफॉर्म।" style="color: var(--text-muted); margin-top: 15px; font-size: 0.95rem; line-height: 1.5;">Real-time communication platforms using WebSocket/Firebase.</p>
                </div>
                <div class="service-card glass animate-on-scroll" style="transition-delay: 0.3s">
                    <div class="service-icon"><svg fill="none" height="30" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="30"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg></div>
                    <h3 class="i18n" data-en="UI/UX Design" data-hi="यूआई/यूएक्स डिजाइन">UI/UX Design</h3>
                    <p class="i18n" data-en="Clean, modern, and user-centric interface design." data-hi="स्वच्छ, आधुनिक और उपयोगकर्ता-केंद्रित इंटरफ़ेस डिज़ाइन।" style="color: var(--text-muted); margin-top: 15px; font-size: 0.95rem; line-height: 1.5;">Clean, modern, and user-centric interface design.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- 7. SOCIAL MEDIA SECTION -->
    <section id="socials">
        <div class="container">
            <h2 class="section-title animate-on-scroll i18n" data-en="Connect_Network" data-hi="कनेक्ट_नेटवर्क">Connect_Network</h2>
            <div class="social-grid">
                <a class="social-item glass animate-on-scroll" data-name="youtube" href="https://www.youtube.com/@pomsd" target="_blank">
                    <svg class="social-svg-placeholder" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/></svg>
                    <span>YouTube</span>
                </a>
                <a class="social-item glass animate-on-scroll" data-name="instagram" href="https://www.instagram.com/princek_97" target="_blank">
                    <svg class="social-svg-placeholder" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/></svg>
                    <span>Instagram</span>
                </a>
                <a class="social-item glass animate-on-scroll" data-name="snapchat" href="https://www.snapchat.com/add/its_prince9014" target="_blank">
                    <svg class="social-svg-placeholder" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/></svg>
                    <span>Snapchat</span>
                </a>
                <a class="social-item glass animate-on-scroll" data-name="facebook" href="https://www.facebook.com/officialPOMSD/" target="_blank">
                    <svg class="social-svg-placeholder" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/></svg>
                    <span>Facebook Page</span>
                </a>
                <a class="social-item glass animate-on-scroll" data-name="twitter" href="https://x.com/princek9889" target="_blank">
                    <svg class="social-svg-placeholder" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/></svg>
                    <span>Twitter/X</span>
                </a>
                <a class="social-item glass animate-on-scroll" data-name="github" href="https://github.com/pomsd" target="_blank">
                    <svg class="social-svg-placeholder" viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/></svg>
                    <span>GitHub</span>
                </a>
            </div>
        </div>
    </section>

    <!-- 8. RUNNER GAME SECTION -->
    <section id="minigame" style="background: rgba(0,0,0,0.15);">
        <div class="container">
            <h2 class="section-title animate-on-scroll i18n" data-en="Mini Game - Runner Challenge" data-hi="मिनी गेम - रनर चैलेंज">Mini Game - Runner Challenge</h2>
            <div class="runner-container glass animate-on-scroll">
                <div class="runner-ui-top">
                    <div><span class="i18n" data-en="Score: " data-hi="स्कोर: ">Score: </span><span id="runner-score">0</span></div>
                    <div><span class="i18n" data-en="Best: " data-hi="सर्वश्रेष्ठ: ">Best: </span><span id="runner-hi-score">0</span></div>
                </div>
                <div class="canvas-wrapper">
                    <canvas height="300" id="runner-canvas" width="800"></canvas>
                    <div class="runner-overlay" id="runner-start-overlay">
                        <h3 class="i18n" data-en="Runner Challenge" data-hi="रनर चैलेंज">Runner Challenge</h3>
                        <p class="i18n" data-en="Press Space or Tap to Jump" data-hi="कूदने के लिए स्पेस दबाएं या टैप करें">Press Space or Tap to Jump</p>
                        <button class="btn btn-primary" onclick="startRunnerGame()">
                            <svg fill="none" height="20" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="20"><polygon points="5 3 19 12 5 21 5 3"/></svg>
                            <span class="i18n" data-en="Start Game" data-hi="गेम शुरू करें">Start Game</span>
                        </button>
                    </div>
                    <div class="runner-overlay" id="runner-gameover-overlay" style="display: none;">
                        <h3 class="i18n" data-en="GAME OVER" data-hi="खेल खत्म" style="color: #ef4444;">GAME OVER</h3>
                        <p id="runner-final-score" style="font-family: monospace; font-size: 1.5rem; color: var(--text-main); margin-bottom: 15px;">Score: 0</p>
                        <button class="btn btn-primary" onclick="startRunnerGame()" style="margin-bottom: 25px;">
                            <svg fill="none" height="18" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="18"><polyline points="1 4 1 10 7 10"/><path d="M3.51 15a9 9 0 1 0 2.13-9.36L1 10"/></svg>
                            <span class="i18n" data-en="Play Again" data-hi="फिर से खेलें">Play Again</span>
                        </button>
                        <div class="runner-cta-box">
                            <p class="i18n" data-en="Liked the game? Check my projects or contact me!" data-hi="क्या आपको गेम पसंद आया? मेरे प्रोजेक्ट्स देखें या संपर्क करें!">Liked the game? Check my projects or contact me!</p>
                            <div class="runner-cta-btns">
                                <a class="btn btn-outline" href="#projects" style="padding: 8px 16px; font-size: 0.85rem;"><span class="i18n" data-en="Projects" data-hi="प्रोजेक्ट्स">Projects</span></a>
                                <a class="btn btn-outline" href="#contact" style="padding: 8px 16px; font-size: 0.85rem;"><span class="i18n" data-en="Contact" data-hi="संपर्क">Contact</span></a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- TIMELINE / JOURNEY -->
    <section id="journey">
        <div class="container">
            <h2 class="section-title animate-on-scroll i18n" data-en="Execution_Log" data-hi="निष्पादन_लॉग">Execution_Log</h2>
            <div class="timeline">
                <div class="timeline-item animate-on-scroll">
                    <div class="timeline-dot"></div>
                    <div class="glass" style="padding: 30px;">
                        <div class="timeline-date" style="font-weight: 800; color: var(--accent); margin-bottom: 10px; font-size: 1.1rem;">2016 – 2024</div>
                        <h4 class="i18n" data-en="The Learning Phase" data-hi="सीखने का चरण" style="margin-bottom: 15px; font-size: 1.3rem;">The Learning Phase</h4>
                        <p class="i18n" data-en="Spent 8 years practically learning computers, software, and fixing systems at a local computer shop." data-hi="स्थानीय कंप्यूटर की दुकान पर व्यावहारिक रूप से कंप्यूटर, सॉफ्टवेयर सीखने और सिस्टम को ठीक करने में 8 साल बिताए।" style="color: var(--text-muted); font-size: 0.95rem; line-height: 1.5;">Spent 8 years practically learning computers, software, and fixing systems at a local computer shop.</p>
                    </div>
                </div>
                <div class="timeline-item animate-on-scroll">
                    <div class="timeline-dot"></div>
                    <div class="glass" style="padding: 30px;">
                        <div class="timeline-date" style="font-weight: 800; color: var(--accent); margin-bottom: 10px; font-size: 1.1rem;">2020 – 2021</div>
                        <h4 class="i18n" data-en="First Major Project" data-hi="पहला प्रमुख प्रोजेक्ट" style="margin-bottom: 15px; font-size: 1.3rem;">First Major Project</h4>
                        <p class="i18n" data-en="Built '69 Send Files', marking my entry into creating real utility applications." data-hi="'69 Send Files' बनाया, जो वास्तविक उपयोगिता एप्लिकेशन बनाने में मेरे प्रवेश को चिह्नित करता है।" style="color: var(--text-muted); font-size: 0.95rem; line-height: 1.5;">Built '69 Send Files', marking my entry into creating real utility applications.</p>
                    </div>
                </div>
                <div class="timeline-item animate-on-scroll">
                    <div class="timeline-dot"></div>
                    <div class="glass" style="padding: 30px;">
                        <div class="timeline-date" style="font-weight: 800; color: var(--accent); margin-bottom: 10px; font-size: 1.1rem;">2024</div>
                        <h4 class="i18n" data-en="The Struggle &amp; Grind" data-hi="संघर्ष और मेहनत" style="margin-bottom: 15px; font-size: 1.3rem;">The Struggle &amp; Grind</h4>
                        <p class="i18n" data-en="Moved to Delhi. Worked day shifts at a shop and night shifts in a factory, but kept building projects." data-hi="दिल्ली चला गया। एक दुकान पर दिन की पाली और एक कारखाने में रात की पाली में काम किया, लेकिन प्रोजेक्ट बनाना जारी रखा।" style="color: var(--text-muted); font-size: 0.95rem; line-height: 1.5;">Moved to Delhi. Worked day shifts at a shop and night shifts in a factory, but kept building projects.</p>
                    </div>
                </div>
                <div class="timeline-item animate-on-scroll">
                    <div class="timeline-dot"></div>
                    <div class="glass" style="padding: 30px;">
                        <div class="timeline-date" style="font-weight: 800; color: var(--accent); margin-bottom: 10px; font-size: 1.1rem;">2026</div>
                        <h4 class="i18n" data-en="Current Era" data-hi="वर्तमान युग" style="margin-bottom: 15px; font-size: 1.3rem;">Current Era</h4>
                        <p class="i18n" data-en="Launched KP Flux Share and developed a suite of 14+ functional applications." data-hi="केपी फ्लक्स शेयर लॉन्च किया और 14+ कार्यात्मक एप्लिकेशन का एक सूट विकसित किया।" style="color: var(--text-muted); font-size: 0.95rem; line-height: 1.5;">Launched KP Flux Share and developed a suite of 14+ functional applications.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 9. CONTACT SECTION -->
    <section id="contact" style="background: rgba(0,0,0,0.15);">
        <div class="container">
            <h2 class="section-title animate-on-scroll i18n" data-en="Establish_Connection" data-hi="संपर्क_स्थापित_करें">Establish_Connection</h2>
            <div class="contact-box glass animate-on-scroll">
                <svg fill="none" height="60" stroke="var(--accent)" stroke-width="1.5" style="margin-bottom: 25px; filter: drop-shadow(0 0 10px var(--accent-glow));" viewBox="0 0 24 24" width="60">
                    <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/>
                    <polyline points="22,6 12,13 2,6"/>
                </svg>
                <h3 class="i18n" data-en="Ready to collaborate?" data-hi="सहयोग करने के लिए तैयार हैं?" style="font-size: 2.5rem; margin-bottom: 15px;">Ready to collaborate?</h3>
                <p class="i18n" data-en="Whether it's building a system, creating a website, or professional typing work, I am just a message away." data-hi="चाहे सिस्टम बनाना हो, वेबसाइट बनानी हो, या पेशेवर टाइपिंग का काम हो, मैं बस एक संदेश दूर हूँ।" style="color: var(--text-muted); font-size: 1.1rem;">Whether it's building a system, creating a website, or professional typing work, I am just a message away.</p>
                <div class="contact-email">Priyanshukumarkumarpk98@gmail.com</div>
                <div class="contact-buttons">
                    <a class="btn btn-primary" href="mailto:Priyanshukumarkumarpk98@gmail.com">
                        <svg fill="none" height="20" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="20"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
                        <span class="i18n" data-en="Email Me" data-hi="मुझे ईमेल करें">Email Me</span>
                    </a>
                    <a class="btn btn-outline" href="https://priyanshuomsd.blogspot.com" target="_blank">
                        <svg fill="none" height="20" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="20"><circle cx="12" cy="12" r="10"/><line x1="2" x2="22" y1="12" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>
                        <span class="i18n" data-en="Visit Official Website" data-hi="आधिकारिक वेबसाइट पर जाएं">Visit Official Website</span>
                    </a>
                </div>
            </div>
        </div>
    </section>

    <!-- 10. FOOTER SECTION -->
    <footer>
        <div class="container">
            <p>© 2026 Priyanshu Kashyap. All Systems Operational.</p>
            <p style="font-size: 0.85rem; margin-top: 10px; opacity: 0.6; font-family: monospace;">Crafted during the grind. Built for the future.</p>
        </div>
    </footer>

    <!-- FLOATING BUTTONS -->
    <div class="floating-group">
        <a class="floating-btn fab-wa" href="#contact" id="fab-wa" title="WhatsApp UI">
            <svg fill="currentColor" height="28" viewBox="0 0 24 24" width="28"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51a12.8 12.8 0 0 0-.57-.01c-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413Z"/></svg>
        </a>
        <a class="floating-btn fab-up" href="#home" id="fab">
            <svg fill="none" height="24" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="24"><polyline points="18 15 12 9 6 15"/></svg>
        </a>
    </div>

    <!-- === JAVASCRIPT === -->
    <script>
        /* -----------------------------------------------------
           1. LANGUAGE TRANSLATION LOGIC
        ----------------------------------------------------- */
        let currentLang = 'en';
        
        function toggleLanguage() {
            currentLang = currentLang === 'en' ? 'hi' : 'en';
            document.getElementById('lang-text').innerText = currentLang === 'en' ? 'हिंदी' : 'ENG';
            
            document.querySelectorAll('.i18n').forEach(el => {
                el.classList.remove('fade-text');
                void el.offsetWidth;
                el.classList.add('fade-text');
                el.innerHTML = el.getAttribute(`data-${currentLang}`);
            });

            texts = currentLang === 'en' ? textsEn : textsHi;
            charIndex = 0; textIndex = 0; isDeleting = false; 
            renderProjects();
        }

        /* -----------------------------------------------------
           2. TYPING EFFECT WITH I18N
        ----------------------------------------------------- */
        const textsEn = [
            "Building robust systems...",
            "Designing clean UIs...",
            "Solving real-world problems...",
            "Turning ideas into code."
        ];
        const textsHi = [
            "मजबूत सिस्टम बना रहा हूँ...",
            "स्वच्छ यूआई डिजाइन कर रहा हूँ...",
            "वास्तविक दुनिया की समस्याओं को हल करना...",
            "विचारों को कोड में बदलना।"
        ];
        let texts = textsEn;
        let textIndex = 0; let charIndex = 0; let isDeleting = false;
        const typingElement = document.getElementById('typing-text');

        function triggerTypingEffect() {
            if(!typingElement) return;
            const currentText = texts[textIndex];
            
            if (isDeleting) {
                typingElement.innerHTML = "> " + currentText.substring(0, charIndex - 1) + "<span style='animation: blink 1s infinite'>_</span>";
                charIndex--;
            } else {
                typingElement.innerHTML = "> " + currentText.substring(0, charIndex + 1) + "<span style='animation: blink 1s infinite'>_</span>";
                charIndex++;
            }

            let speed = isDeleting ? 40 : 80;

            if (!isDeleting && charIndex === currentText.length) {
                speed = 2000; isDeleting = true;
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false; textIndex = (textIndex + 1) % texts.length; speed = 500;
            }

            setTimeout(triggerTypingEffect, speed);
        }

        /* -----------------------------------------------------
           3. PROJECTS RENDERING
        ----------------------------------------------------- */
        const projectsList = [
            { nameEn: "KP Flux Share", nameHi: "केपी फ्लक्स शेयर", descEn: "Advanced file sharing system.", descHi: "उन्नत फ़ाइल शेयरिंग सिस्टम।", icon: "M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4 M17 8l-5-5-5 5 M12 3v12" },
            { nameEn: "Bharat Chat", nameHi: "भारत चैट", descEn: "Coming Soon - Secure messaging app.", descHi: "जल्द आ रहा है - सुरक्षित मैसेजिंग ऐप।", icon: "M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 0 1-7.6 4.7 8.38 8.38 0 0 1-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 0 1-.9-3.8 8.5 8.5 0 0 1 4.7-7.6 8.38 8.38 0 0 1 3.8-.9h.5a8.48 8.48 0 0 1 8 8v.5z" },
            { nameEn: "CroChat", nameHi: "क्रोचैट", descEn: "Real-time communication platform.", descHi: "रीयल-टाइम संचार प्लेटफॉर्म।", icon: "M17 6.1H3 M21 12.1H3 M15.1 18H3" },
            { nameEn: "QR Code Gen Pro", nameHi: "क्यूआर कोड जेन प्रो", descEn: "Customizable QR code creator.", descHi: "अनुकूलन योग्य क्यूआर कोड निर्माता।", icon: "M3 3h6v6H3z M15 3h6v6h-6z M3 15h6v6H3z M15 15h6v6h-6z" },
            { nameEn: "KP AI Assistant", nameHi: "केपी एआई सहायक", descEn: "Smart AI helper integration.", descHi: "स्मार्ट एआई सहायक एकीकरण।", icon: "M12 2a2 2 0 0 1 2 2v2a2 2 0 0 1-2 2 M12 14a2 2 0 0 1 2 2v2a2 2 0 0 1-2 2 M4 10a2 2 0 0 1 2-2h2a2 2 0 0 1 2 2 M20 10a2 2 0 0 0-2-2h-2a2 2 0 0 0-2 2" },
            { nameEn: "KP Code Editor", nameHi: "केपी कोड एडिटर", descEn: "In-browser lightweight IDE.", descHi: "इन-ब्राउज़र हल्का आईडीई।", icon: "M16 18l6-6-6-6 M8 6l-6 6 6 6" },
            { nameEn: "KP Calc Pro", nameHi: "केपी कैल्क प्रो", descEn: "Advanced mathematical tool.", descHi: "उन्नत गणितीय उपकरण।", icon: "M19 3H5a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V5a2 2 0 0 0-2-2z M8 7h8 M8 11h.01 M12 11h.01 M16 11h.01 M8 15h.01 M12 15h.01 M16 15h.01 M8 19h.01 M12 19h.01 M16 19h.01" },
            { nameEn: "KP Shake Flash", nameHi: "केपी शेक फ्लैश", descEn: "Motion-activated utility.", descHi: "मोशन-सक्रिय उपयोगिता।", icon: "M11 2h2v7h-2z M11 22h2v-7h-2z M2 11h7v2H2z M22 11h-7v2h7z" },
            { nameEn: "KP Runner Game", nameHi: "केपी रनर गेम", descEn: "Endless 2D runner challenge.", descHi: "अंतहीन 2डी रनर चुनौती।", icon: "M13 5a2 2 0 1 1-4 0 2 2 0 0 1 4 0z M5 22v-5l4-4v-4l-4-4 M19 22v-5l-4-4v-4l4-4" },
            { nameEn: "Duggu Buggu Name", nameHi: "डुग्गु बुग्गु नाम", descEn: "Fun name generator utility.", descHi: "मज़ेदार नाम जनरेटर उपयोगिता।", icon: "M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2 M9 3a4 4 0 1 0 0 8 4 4 0 0 0 0-8z M23 21v-2a4 4 0 0 0-3-3.87 M16 3.13a4 4 0 0 1 0 7.75" }
        ];

        function renderProjects() {
            const container = document.getElementById('projects-container');
            if(!container) return;
            container.innerHTML = projectsList.map((p, i) => `
                <div class="project-card glass animate-on-scroll" style="transition-delay: ${(i%3)*0.1}s">
                    <svg class="project-icon" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path d="${p.icon}"></path>
                    </svg>
                    <h3 class="project-title">${currentLang === 'en' ? p.nameEn : p.nameHi}</h3>
                    <p style="color: var(--text-muted); margin-bottom: 25px; font-size: 0.95rem;">${currentLang === 'en' ? p.descEn : p.descHi}</p>
                    <a href="#" class="btn btn-outline" style="padding: 10px 20px; font-size: 0.95rem;">
                        <span class="i18n" data-en="View Project" data-hi="प्रोजेक्ट देखें">${currentLang === 'en' ? 'View Project' : 'प्रोजेक्ट देखें'}</span>
                    </a>
                </div>
            `).join('');
            document.querySelectorAll('#projects-container .animate-on-scroll').forEach(el => observer.observe(el));
        }

        /* -----------------------------------------------------
           4. MODAL LOGIC & SOCIAL SVG INJECTOR
        ----------------------------------------------------- */
        const modalInputs = document.querySelectorAll('#code-container input');
        const modal = document.getElementById('unlock-modal');
        
        if (modalInputs.length > 0 && modal) {
            modalInputs.forEach((input, index) => {
                input.addEventListener('input', (e) => {
                    if (e.target.value.length > 0) {
                        if (index < modalInputs.length - 1) modalInputs[index + 1].focus();
                    }
                    checkModalAutoSubmit();
                });
                input.addEventListener('keydown', (e) => {
                    if (e.key === 'Backspace' && e.target.value === '' && index > 0) {
                        modalInputs[index - 1].focus();
                    }
                });
            });
        }

        function checkModalAutoSubmit() {
            const allFilled = Array.from(modalInputs).every(input => input.value.length === 1);
            if (allFilled) verifyCode();
        }

        function verifyCode() {
            const code = Array.from(modalInputs).map(i => i.value).join('');
            if (code.length === 6) {
                modalInputs.forEach(i => i.style.borderColor = 'var(--accent)');
                setTimeout(() => {
                    modal.style.opacity = '0';
                    setTimeout(() => {
                        modal.style.display = 'none';
                        document.body.classList.remove('locked');
                        triggerTypingEffect();
                        fillProgressBars();
                    }, 500);
                }, 500);
            } else {
                document.getElementById('code-container').style.animation = 'shake 0.4s both';
                setTimeout(() => { document.getElementById('code-container').style.animation = ''; }, 400);
            }
        }

        const socialIcons = {
            'youtube': '<svg viewBox="0 0 24 24"><path d="M22.54 6.42a2.78 2.78 0 0 0-1.94-2C18.88 4 12 4 12 4s-6.88 0-8.6.46a2.78 2.78 0 0 0-1.94 2A29 29 0 0 0 1 11.75a29 29 0 0 0 .46 5.33 2.78 2.78 0 0 0 1.94 2c1.72.46 8.6.46 8.6.46s6.88 0 8.6-.46a2.78 2.78 0 0 0 1.94-2 29 29 0 0 0 .46-5.33 29 29 0 0 0-.46-5.33z"></path><polygon points="9.75 15.02 15.5 11.75 9.75 8.48 9.75 15.02"></polygon></svg>',
            'instagram': '<svg viewBox="0 0 24 24"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line></svg>',
            'snapchat': '<svg viewBox="0 0 24 24"><path d="M22.48 16.59c-1.42-1.32-3.8-1.78-4.57-1.87-.22-.03-.45-.1-.49-.33-.03-.18.06-.41.25-.62.59-.65 1.55-2.3 1.83-3.41.07-.3.04-.61-.09-.89a1.6 1.6 0 0 0-.9-.81c-.2-.07-.42-.1-.64-.09-.37.02-.75.13-1.07.31-.05.03-.1.01-.13-.03-.31-.4-.61-.83-.87-1.28-1.03-1.83-2.5-3.8-3.8-3.8h-.02c-1.3 0-2.77 1.97-3.8 3.8-.26.45-.56.88-.87 1.28-.03.04-.08.06-.13.03-.32-.18-.7-.29-1.07-.31-.22-.01-.44.02-.64.09a1.6 1.6 0 0 0-.9.81c-.13.28-.16.59-.09.89.28 1.11 1.24 2.76 1.83 3.41.19.21.28.44.25.62-.04.23-.27.3-.49.33-.77.09-3.15.55-4.57 1.87-.33.31-.43.79-.24 1.19.17.37.54.61.94.62.91.03 2.15.43 3.12.98.54.31.78.96.55 1.54-.15.39-.52.64-.93.66a21.4 21.4 0 0 1-2.92-.2c-.39-.06-.71.21-.77.6a.6.6 0 0 0 .58.67h.03c.51.05 1.02.08 1.53.11 2.37.1 3.51.98 3.86 1.27.34.28.79.43 1.25.43.46 0 .91-.15 1.25-.43.35-.29 1.49-1.17 3.86-1.27.51-.03 1.02-.06 1.53-.11h.03a.6.6 0 0 0 .58-.67c-.06-.39-.38-.66-.77-.6a21.4 21.4 0 0 1-2.92.2c-.41-.02-.78-.27-.93-.66-.23-.58.01-1.23.55-1.54.97-.55 2.21-.95 3.12-.98.4-.01.77-.25.94-.62.19-.4.09-.88-.24-1.19z"></path></svg>',
            'facebook': '<svg viewBox="0 0 24 24"><path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"></path></svg>',
            'twitter': '<svg viewBox="0 0 24 24"><path d="M4 4l11.73 16h5l-11.73-16z"></path><path d="M4 20l6.76-6.76"></path><path d="M20 4l-6.76 6.76"></path></svg>',
            'reddit': '<svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"></circle><path d="M16 11.5c0-1.11-.89-2-2-2s-2 .89-2 2 .89 2 2 2 2-.89 2-2zm-8 0c0-1.11-.89-2-2-2s-2 .89-2 2 .89 2 2 2 2-.89 2-2z"></path><path d="M12 16.5c-1.66 0-3-1.34-3-3h6c0 1.66-1.34 3-3 3z"></path><path d="M12 4c.66 0 1.2.54 1.2 1.2s-.54 1.2-1.2 1.2-1.2-.54-1.2-1.2.54-1.2 1.2-1.2m0-2c-1.76 0-3.2 1.44-3.2 3.2 0 1.48 1 2.73 2.38 3.1l-.14 1.7h1.92l-.14-1.7c1.38-.37 2.38-1.62 2.38-3.1 0-1.76-1.44-3.2-3.2-3.2z"></path></svg>',
            'github': '<svg viewBox="0 0 24 24"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path></svg>',
            'codepen': '<svg viewBox="0 0 24 24"><polygon points="12 2 22 8.5 22 15.5 12 22 2 15.5 2 8.5 12 2"></polygon><line x1="12" y1="22" x2="12" y2="15.5"></line><polyline points="22 8.5 12 15.5 2 8.5"></polyline><polyline points="2 15.5 12 8.5 22 15.5"></polyline><line x1="12" y1="2" x2="12" y2="8.5"></line></svg>',
            'default': '<svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"></circle><path d="M12 16v-4"></path><path d="M12 8h.01"></path></svg>'
        };

        document.querySelectorAll('.social-item').forEach(item => {
            let name = (item.getAttribute('data-name') || '').toLowerCase();
            let iconHtml = socialIcons['default'];
            for (let key in socialIcons) {
                if(name.includes(key) || (name.includes('x') && key==='twitter')) iconHtml = socialIcons[key];
            }
            let svgHolder = item.querySelector('.social-svg-placeholder');
            if(svgHolder) svgHolder.outerHTML = iconHtml;
        });

        /* -----------------------------------------------------
           5. SCROLL ANIMATIONS
        ----------------------------------------------------- */
        const observerOptions = { threshold: 0.1, rootMargin: "0px 0px -50px 0px" };
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                    if (entry.target.closest('#skills')) fillProgressBars();
                }
            });
        }, observerOptions);

        document.querySelectorAll('.animate-on-scroll').forEach(el => observer.observe(el));

        function fillProgressBars() {
            document.querySelectorAll('.progress-fill').forEach(bar => {
                bar.style.width = bar.getAttribute('data-width');
            });
        }

        /* -----------------------------------------------------
           6. NAVBAR, FAB & THEME
        ----------------------------------------------------- */
        const navbar = document.getElementById('navbar');
        const fab = document.getElementById('fab');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
                fab.classList.add('visible');
            } else {
                navbar.classList.remove('scrolled');
                fab.classList.remove('visible');
            }
        });

        const themeBtn = document.getElementById('theme-btn');
        const htmlEl = document.documentElement;
        themeBtn.addEventListener('click', () => {
            if (htmlEl.getAttribute('data-theme') === 'dark') {
                htmlEl.setAttribute('data-theme', 'light');
                themeBtn.innerHTML = '<svg fill="none" height="18" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="18"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path></svg>';
            } else {
                htmlEl.setAttribute('data-theme', 'dark');
                themeBtn.innerHTML = '<svg fill="none" height="18" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" width="18"><circle cx="12" cy="12" r="5"></circle><line x1="12" y1="1" x2="12" y2="3"></line><line x1="12" y1="21" x2="12" y2="23"></line><line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line><line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line><line x1="1" y1="12" x2="3" y2="12"></line><line x1="21" y1="12" x2="23" y2="12"></line><line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line><line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line></svg>';
            }
        });

        renderProjects();

        /* -----------------------------------------------------
           7. MINI GAME LOGIC
        ----------------------------------------------------- */
        const canvas = document.getElementById('runner-canvas');
        if (canvas) {
            const ctx = canvas.getContext('2d');
            const scoreEl = document.getElementById('runner-score');
            const hiScoreEl = document.getElementById('runner-hi-score');
            const finalScoreEl = document.getElementById('runner-final-score');
            const startOverlay = document.getElementById('runner-start-overlay');
            const gameOverOverlay = document.getElementById('runner-gameover-overlay');
            
            let gameScore = 0;
            let gameHiScore = localStorage.getItem('kp_runner_hi') || 0;
            hiScoreEl.innerText = gameHiScore;

            let gameActive = false;
            let gameSpeed = 5;
            let gameFrame = 0;
            let animationId;
            let obstacles = [];
            let groundY = canvas.height - 30;
            
            const AudioContext = window.AudioContext || window.webkitAudioContext;
            let audioCtx;
            function playSfx(type) {
                try {
                    if (!audioCtx) audioCtx = new AudioContext();
                    if (audioCtx.state === 'suspended') audioCtx.resume();
                    const osc = audioCtx.createOscillator();
                    const gain = audioCtx.createGain();
                    osc.connect(gain);
                    gain.connect(audioCtx.destination);
                    
                    if (type === 'jump') {
                        osc.type = 'sine';
                        osc.frequency.setValueAtTime(300, audioCtx.currentTime);
                        osc.frequency.exponentialRampToValueAtTime(600, audioCtx.currentTime + 0.1);
                        gain.gain.setValueAtTime(0.1, audioCtx.currentTime);
                        gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.1);
                        osc.start(); osc.stop(audioCtx.currentTime + 0.1);
                    } else if (type === 'crash') {
                        osc.type = 'sawtooth';
                        osc.frequency.setValueAtTime(100, audioCtx.currentTime);
                        osc.frequency.exponentialRampToValueAtTime(10, audioCtx.currentTime + 0.3);
                        gain.gain.setValueAtTime(0.2, audioCtx.currentTime);
                        gain.gain.linearRampToValueAtTime(0, audioCtx.currentTime + 0.3);
                        osc.start(); osc.stop(audioCtx.currentTime + 0.3);
                    }
                } catch (e) { }
            }

            const player = { x: 80, y: groundY - 40, w: 35, h: 40, dy: 0, jumpPower: -14, gravity: 0.8, grounded: true, color: '#00ff66' };

            function drawPlayer() {
                ctx.shadowBlur = 15; ctx.shadowColor = player.color; ctx.fillStyle = player.color;
                ctx.fillRect(player.x, player.y, player.w, player.h);
                ctx.fillStyle = '#050505'; ctx.shadowBlur = 0;
                ctx.fillRect(player.x + 20, player.y + 10, 8, 8);
            }

            function handlePlayer() {
                if (!player.grounded) { player.dy += player.gravity; player.y += player.dy; }
                if (player.y + player.h >= groundY) { player.y = groundY - player.h; player.dy = 0; player.grounded = true; }
                drawPlayer();
            }

            function playerJump() {
                if (player.grounded && gameActive) { player.dy = player.jumpPower; player.grounded = false; playSfx('jump'); }
            }

            class Obstacle {
                constructor() { this.h = 40 + Math.random() * 40; this.w = 30 + Math.random() * 20; this.x = canvas.width; this.y = groundY - this.h; this.color = '#ef4444'; }
                update() { this.x -= gameSpeed; }
                draw() { ctx.shadowBlur = 10; ctx.shadowColor = this.color; ctx.fillStyle = this.color; ctx.fillRect(this.x, this.y, this.w, this.h); ctx.shadowBlur = 0; }
            }

            function handleObstacles() {
                if (gameFrame % Math.floor(Math.random() * 60 + 80) === 0 && gameFrame > 0) { obstacles.push(new Obstacle()); }
                for (let i = 0; i < obstacles.length; i++) {
                    obstacles[i].update(); obstacles[i].draw();
                    if (player.x < obstacles[i].x + obstacles[i].w && player.x + player.w > obstacles[i].x && player.y < obstacles[i].y + obstacles[i].h && player.y + player.h > obstacles[i].y) { gameOver(); }
                    if (obstacles[i].x + obstacles[i].w < 0) { obstacles.splice(i, 1); i--; }
                }
            }

            function drawGround() {
                ctx.strokeStyle = '#00ff66'; ctx.shadowBlur = 5; ctx.shadowColor = '#00ff66'; ctx.lineWidth = 3;
                ctx.beginPath(); ctx.moveTo(0, groundY); ctx.lineTo(canvas.width, groundY); ctx.stroke(); ctx.shadowBlur = 0;
                ctx.fillStyle = '#00ff66';
                for(let i = 0; i < canvas.width; i+= 50) {
                    let offset = (i - (gameFrame * gameSpeed)) % canvas.width;
                    if(offset < 0) offset += canvas.width;
                    ctx.fillRect(offset, groundY, 15, 5);
                }
            }

            function updateGame() {
                if (!gameActive) return;
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                drawGround(); handlePlayer(); handleObstacles();
                if (gameFrame % 5 === 0) {
                    gameScore++; scoreEl.innerText = gameScore;
                    if (gameSpeed < 15) gameSpeed += 0.005;
                }
                gameFrame++; animationId = requestAnimationFrame(updateGame);
            }

            window.startRunnerGame = function() {
                gameActive = true; gameScore = 0; gameSpeed = 6; gameFrame = 0; obstacles = [];
                player.y = groundY - player.h; player.dy = 0; player.grounded = true;
                scoreEl.innerText = gameScore;
                startOverlay.style.display = 'none'; gameOverOverlay.style.display = 'none';
                cancelAnimationFrame(animationId); updateGame();
            }

            function gameOver() {
                gameActive = false; cancelAnimationFrame(animationId); playSfx('crash');
                if (gameScore > gameHiScore) {
                    gameHiScore = gameScore; localStorage.setItem('kp_runner_hi', gameHiScore); hiScoreEl.innerText = gameHiScore;
                }
                finalScoreEl.innerText = (currentLang === 'en' ? 'Score: ' : 'स्कोर: ') + gameScore;
                gameOverOverlay.style.display = 'flex';
            }

            window.addEventListener('keydown', (e) => { if (e.code === 'Space' || e.code === 'ArrowUp') { if(gameActive) { e.preventDefault(); playerJump(); } } });
            canvas.addEventListener('touchstart', (e) => { e.preventDefault(); if(gameActive) playerJump(); }, {passive: false});
            canvas.addEventListener('mousedown', (e) => { if(gameActive) playerJump(); });

            ctx.clearRect(0, 0, canvas.width, canvas.height); drawGround(); drawPlayer();
        }
    </script>
</body>
</html>
