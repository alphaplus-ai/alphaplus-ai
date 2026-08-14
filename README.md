<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aryan | Software Engineer</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    <style>
        :root {
            --red: #b74b4b;
            --red-glow: rgba(183,75,75,0.35);
            --red-dim: rgba(183,75,75,0.12);
            --bg: #080808;
            --bg2: #0f0f0f;
            --bg3: #141414;
            --text: #f0ece8;
            --muted: #7a7068;
            --border: rgba(183,75,75,0.18);
        }

        *, *::before, *::after {
            margin: 0; padding: 0;
            box-sizing: border-box;
        }

        html { scroll-behavior: smooth; }

        body {
            background: var(--bg);
            color: var(--text);
            font-family: 'DM Sans', sans-serif;
            overflow-x: hidden;
            cursor: none;
        }

        /* CUSTOM CURSOR */
        #cursor {
            width: 12px; height: 12px;
            background: var(--red);
            border-radius: 50%;
            position: fixed;
            top: 0; left: 0;
            pointer-events: none;
            z-index: 9999;
            transition: transform 0.1s;
        }
        #cursor-ring {
            width: 36px; height: 36px;
            border: 1.5px solid var(--red);
            border-radius: 50%;
            position: fixed;
            top: 0; left: 0;
            pointer-events: none;
            z-index: 9998;
            transition: all 0.18s ease;
            opacity: 0.6;
        }
        body:hover #cursor, body:hover #cursor-ring { opacity: 1; }

        /* SCROLLBAR */
        ::-webkit-scrollbar { width: 4px; }
        ::-webkit-scrollbar-track { background: var(--bg); }
        ::-webkit-scrollbar-thumb { background: var(--red); border-radius: 2px; }

        /* NAV */
        header {
            position: fixed; top: 0; left: 0;
            width: 100%; z-index: 500;
            padding: 1.6rem 6%;
            display: flex; align-items: center; justify-content: space-between;
            background: rgba(8,8,8,0.7);
            backdrop-filter: blur(18px);
            border-bottom: 1px solid var(--border);
            transition: all 0.3s;
        }

        .logo {
            font-family: 'Syne', sans-serif;
            font-size: 2.2rem;
            font-weight: 800;
            color: var(--red);
            letter-spacing: -0.03em;
            text-decoration: none;
        }

        nav { display: flex; gap: 2.8rem; align-items: center; }

        nav a {
            font-size: 0.92rem;
            font-weight: 500;
            color: var(--muted);
            text-decoration: none;
            letter-spacing: 0.06em;
            text-transform: uppercase;
            transition: color 0.25s;
            position: relative;
        }
        nav a::after {
            content: '';
            position: absolute; bottom: -3px; left: 0;
            width: 0; height: 1.5px;
            background: var(--red);
            transition: width 0.3s;
        }
        nav a:hover, nav a.active { color: var(--text); }
        nav a:hover::after, nav a.active::after { width: 100%; }

        .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; }
        .hamburger span { display: block; width: 26px; height: 2px; background: var(--text); transition: 0.3s; }

        /* HERO */
        .hero {
            min-height: 100vh;
            display: flex; align-items: center; justify-content: center;
            padding: 8rem 6% 4rem;
            position: relative;
            overflow: hidden;
        }

        .hero-bg {
            position: absolute; inset: 0;
            background:
                radial-gradient(ellipse 60% 50% at 80% 50%, rgba(183,75,75,0.13) 0%, transparent 70%),
                radial-gradient(ellipse 40% 60% at 20% 80%, rgba(183,75,75,0.07) 0%, transparent 60%);
        }

        .noise {
            position: absolute; inset: 0;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
            opacity: 0.4;
            pointer-events: none;
        }

        .hero-inner {
            display: flex; align-items: center; justify-content: space-between;
            gap: 4rem; width: 100%; max-width: 1200px;
            position: relative; z-index: 1;
        }

        .hero-text { flex: 1; }

        .hero-badge {
            display: inline-flex; align-items: center; gap: 8px;
            background: var(--red-dim);
            border: 1px solid var(--border);
            border-radius: 100px;
            padding: 0.4rem 1.1rem;
            font-size: 0.8rem;
            color: var(--red);
            letter-spacing: 0.08em;
            text-transform: uppercase;
            margin-bottom: 2rem;
            animation: fadeUp 0.7s 0.1s both;
        }

        .hero-badge .dot {
            width: 6px; height: 6px;
            border-radius: 50%;
            background: var(--red);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.5; transform: scale(0.8); }
        }

        .hero-text h1 {
            font-family: 'Syne', sans-serif;
            font-size: clamp(3.5rem, 7vw, 7rem);
            font-weight: 800;
            line-height: 1.0;
            letter-spacing: -0.04em;
            animation: fadeUp 0.7s 0.2s both;
        }

        .hero-text h1 .name {
            color: var(--red);
            position: relative;
            display: inline-block;
        }

        .hero-text h1 .name::after {
            content: '';
            position: absolute; left: 0; bottom: 4px;
            width: 100%; height: 3px;
            background: var(--red);
            transform: scaleX(0); transform-origin: left;
            animation: lineExpand 0.8s 1s both;
        }

        @keyframes lineExpand { to { transform: scaleX(1); } }

        .typewriter-wrap {
            font-family: 'Syne', sans-serif;
            font-size: clamp(1.4rem, 2.5vw, 2.2rem);
            font-weight: 600;
            margin: 1.2rem 0;
            color: var(--muted);
            min-height: 2.6rem;
            animation: fadeUp 0.7s 0.3s both;
        }

        .typewriter-wrap .typed { color: var(--red); }

        .cursor-blink {
            display: inline-block;
            width: 2px; height: 1.1em;
            background: var(--red);
            margin-left: 2px;
            vertical-align: middle;
            animation: blink 0.7s infinite;
        }

        @keyframes blink { 0%,100% { opacity: 1; } 50% { opacity: 0; } }

        .hero-desc {
            font-size: 1.02rem;
            color: var(--muted);
            line-height: 1.75;
            max-width: 520px;
            margin: 1.4rem 0 2.2rem;
            animation: fadeUp 0.7s 0.4s both;
        }

        .hero-actions {
            display: flex; gap: 1.2rem; flex-wrap: wrap;
            animation: fadeUp 0.7s 0.5s both;
        }

        .btn-primary {
            display: inline-flex; align-items: center; gap: 8px;
            padding: 0.85rem 2.2rem;
            background: var(--red);
            color: #fff;
            border-radius: 100px;
            font-size: 0.92rem;
            font-weight: 500;
            letter-spacing: 0.03em;
            text-decoration: none;
            border: 2px solid var(--red);
            transition: all 0.3s;
            cursor: none;
        }
        .btn-primary:hover {
            background: transparent;
            color: var(--red);
            box-shadow: 0 0 28px var(--red-glow);
        }

        .btn-outline {
            display: inline-flex; align-items: center; gap: 8px;
            padding: 0.85rem 2.2rem;
            background: transparent;
            color: var(--text);
            border-radius: 100px;
            font-size: 0.92rem;
            font-weight: 500;
            letter-spacing: 0.03em;
            text-decoration: none;
            border: 1.5px solid rgba(255,255,255,0.15);
            transition: all 0.3s;
            cursor: none;
        }
        .btn-outline:hover {
            border-color: var(--red);
            color: var(--red);
        }

        /* HERO SOCIALS */
        .hero-socials {
            display: flex; gap: 1rem; margin-top: 2.8rem;
            animation: fadeUp 0.7s 0.6s both;
        }
        .hero-socials a {
            display: flex; align-items: center; justify-content: center;
            width: 42px; height: 42px;
            border: 1.5px solid var(--border);
            border-radius: 50%;
            color: var(--muted);
            font-size: 1.05rem;
            text-decoration: none;
            transition: all 0.3s;
            cursor: none;
        }
        .hero-socials a:hover {
            transform: translateY(-4px);
            box-shadow: 0 8px 24px var(--social-glow, var(--red-glow));
        }

        /* Branded social colors */
        .social-linkedin { --social-color: #0A66C2; --social-glow: rgba(10,102,194,0.4); --social-bg: rgba(10,102,194,0.12); }
        .social-github   { --social-color: #e6edf3; --social-glow: rgba(230,237,243,0.25); --social-bg: rgba(230,237,243,0.08); }
        .social-twitter  { --social-color: #e7e7e7; --social-glow: rgba(231,231,231,0.25); --social-bg: rgba(231,231,231,0.08); }
        .social-instagram{ --social-color: #E1306C; --social-glow: rgba(225,48,108,0.4); --social-bg: rgba(225,48,108,0.12); }
        .social-email    { --social-color: #EA4335; --social-glow: rgba(234,67,53,0.4); --social-bg: rgba(234,67,53,0.12); }
        .social-phone    { --social-color: #25D366; --social-glow: rgba(37,211,102,0.4); --social-bg: rgba(37,211,102,0.12); }

        .hero-socials a.social-linkedin,
        .hero-socials a.social-github,
        .hero-socials a.social-twitter,
        .hero-socials a.social-instagram,
        .hero-socials a.social-email {
            color: var(--social-color);
            border-color: color-mix(in srgb, var(--social-color) 30%, transparent);
        }
        .hero-socials a.social-linkedin:hover { border-color: var(--social-color); background: var(--social-bg); }
        .hero-socials a.social-github:hover   { border-color: var(--social-color); background: var(--social-bg); }
        .hero-socials a.social-twitter:hover  { border-color: var(--social-color); background: var(--social-bg); }
        .hero-socials a.social-instagram:hover{ border-color: #E1306C; background: var(--social-bg); color: #E1306C; }
        .hero-socials a.social-email:hover    { border-color: var(--social-color); background: var(--social-bg); }

        /* HERO IMAGE */
        .hero-image-wrap {
            flex: 0 0 auto;
            position: relative;
            animation: fadeUp 0.8s 0.3s both;
        }

        .hero-image-frame {
            width: min(320px, 38vw);
            height: min(320px, 38vw);
            border-radius: 50%;
            position: relative;
        }

        .hero-image-frame::before {
            content: '';
            position: absolute; inset: -3px;
            border-radius: 50%;
            background: conic-gradient(var(--red), transparent 60%, var(--red));
            animation: spin 8s linear infinite;
            z-index: 0;
        }

        @keyframes spin { to { transform: rotate(360deg); } }

        .hero-image-frame::after {
            content: '';
            position: absolute; inset: 3px;
            border-radius: 50%;
            background: var(--bg);
            z-index: 1;
        }

        .hero-image-frame img {
            position: absolute; inset: 8px;
            width: calc(100% - 16px);
            height: calc(100% - 16px);
            border-radius: 50%;
            object-fit: cover;
            z-index: 2;
            background: var(--bg3);
            font-size: 0; /* hide alt text */
        }

        /* fallback avatar */
        .avatar-fallback {
            position: absolute; inset: 8px;
            width: calc(100% - 16px);
            height: calc(100% - 16px);
            border-radius: 50%;
            background: linear-gradient(135deg, var(--bg3) 0%, #1a1010 100%);
            display: flex; align-items: center; justify-content: center;
            z-index: 2;
            font-family: 'Syne', sans-serif;
            font-size: clamp(3rem, 8vw, 5rem);
            font-weight: 800;
            color: var(--red);
        }

        .hero-float-card {
            position: absolute;
            background: rgba(15,15,15,0.9);
            border: 1px solid var(--border);
            border-radius: 14px;
            padding: 0.8rem 1.2rem;
            backdrop-filter: blur(12px);
            font-size: 0.82rem;
            animation: float 4s ease-in-out infinite;
            z-index: 5;
        }
        .hero-float-card .fc-label { color: var(--muted); font-size: 0.72rem; }
        .hero-float-card .fc-val { font-family: 'Syne', sans-serif; font-weight: 700; color: var(--red); font-size: 1.2rem; }
        .card-exp { bottom: -20px; right: -30px; }
        .card-proj { top: 20px; left: -50px; animation-delay: -2s; }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        /* SECTIONS */
        section {
            padding: 7rem 6%;
            max-width: 1300px;
            margin: 0 auto;
        }

        .sec-label {
            font-size: 0.78rem;
            letter-spacing: 0.18em;
            text-transform: uppercase;
            color: var(--red);
            margin-bottom: 0.7rem;
            font-weight: 500;
        }

        .sec-title {
            font-family: 'Syne', sans-serif;
            font-size: clamp(2rem, 4vw, 3.2rem);
            font-weight: 800;
            letter-spacing: -0.03em;
            line-height: 1.1;
            margin-bottom: 1rem;
        }

        .sec-divider {
            width: 48px; height: 3px;
            background: var(--red);
            margin-bottom: 3rem;
            border-radius: 2px;
        }

        /* ABOUT */
        #about {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 5rem;
            align-items: center;
        }

        .about-img-wrap {
            position: relative;
        }

        .about-img-box {
            width: 100%;
            aspect-ratio: 3/4;
            max-height: 480px;
            border-radius: 24px;
            background: var(--bg3);
            overflow: hidden;
            border: 1px solid var(--border);
            display: flex; align-items: center; justify-content: center;
            font-family: 'Syne', sans-serif;
            font-size: 6rem;
            font-weight: 800;
            color: var(--red);
        }

        .about-img-box img {
            width: 100%; height: 100%;
            object-fit: cover;
            display: none;
        }

        .about-deco {
            position: absolute;
            bottom: -20px; right: -20px;
            width: 120px; height: 120px;
            border: 2px solid var(--border);
            border-radius: 16px;
            background: var(--bg2);
            display: flex; flex-direction: column;
            align-items: center; justify-content: center;
            gap: 2px;
        }

        .about-deco .big { font-family: 'Syne', sans-serif; font-size: 2.4rem; font-weight: 800; color: var(--red); }
        .about-deco .small { font-size: 0.72rem; color: var(--muted); text-align: center; }

        .about-text p {
            color: var(--muted);
            line-height: 1.8;
            margin-bottom: 1.2rem;
            font-size: 1rem;
        }

        .info-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1rem;
            margin: 2rem 0;
        }

        .info-item label { font-size: 0.75rem; letter-spacing: 0.1em; text-transform: uppercase; color: var(--red); }
        .info-item p { font-size: 0.92rem; color: var(--text); margin-top: 2px; }

        /* SERVICES */
        #services { max-width: 1300px; }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
            margin-top: 3rem;
        }

        .service-card {
            background: var(--bg2);
            border: 1px solid var(--border);
            border-radius: 20px;
            padding: 2.2rem;
            transition: all 0.35s;
            position: relative;
            overflow: hidden;
        }

        .service-card::before {
            content: '';
            position: absolute; top: 0; left: 0;
            width: 100%; height: 2px;
            background: var(--red);
            transform: scaleX(0); transform-origin: left;
            transition: transform 0.35s;
        }
        .service-card:hover::before { transform: scaleX(1); }
        .service-card:hover {
            border-color: var(--red);
            background: rgba(183,75,75,0.04);
            transform: translateY(-4px);
            box-shadow: 0 20px 50px rgba(183,75,75,0.12);
        }

        .service-icon {
            width: 56px; height: 56px;
            background: var(--red-dim);
            border-radius: 14px;
            display: flex; align-items: center; justify-content: center;
            font-size: 1.6rem;
            color: var(--red);
            margin-bottom: 1.5rem;
        }

        .service-card h3 {
            font-family: 'Syne', sans-serif;
            font-size: 1.3rem;
            font-weight: 700;
            margin-bottom: 0.7rem;
        }
        .service-card p { color: var(--muted); font-size: 0.9rem; line-height: 1.7; }

        /* SKILLS */
        #skills { max-width: 1300px; }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
            gap: 1rem;
            margin-top: 3rem;
        }

        .skill-chip {
            background: var(--bg2);
            border: 1px solid var(--border);
            border-radius: 12px;
            padding: 1rem;
            text-align: center;
            transition: all 0.3s;
        }

        .skill-chip:hover {
            border-color: var(--red);
            background: var(--red-dim);
            transform: translateY(-3px);
        }

        .skill-chip i { font-size: 1.8rem; color: var(--red); margin-bottom: 0.5rem; }
        .skill-chip span { display: block; font-size: 0.8rem; color: var(--muted); font-weight: 500; }

        /* EDUCATION */
        #education { max-width: 1300px; }

        .timeline {
            position: relative;
            padding-left: 2rem;
            margin-top: 3rem;
        }
        .timeline::before {
            content: '';
            position: absolute; left: 0; top: 8px;
            width: 2px; height: calc(100% - 16px);
            background: var(--border);
        }

        .timeline-item {
            position: relative;
            padding-bottom: 3rem;
        }
        .timeline-item::before {
            content: '';
            position: absolute;
            left: -2.5rem; top: 6px;
            width: 12px; height: 12px;
            border-radius: 50%;
            background: var(--red);
            box-shadow: 0 0 12px var(--red-glow);
        }

        .tl-year {
            font-size: 0.78rem; letter-spacing: 0.1em;
            text-transform: uppercase; color: var(--red);
            margin-bottom: 0.4rem;
        }

        .tl-card {
            background: var(--bg2);
            border: 1px solid var(--border);
            border-radius: 16px;
            padding: 1.6rem 2rem;
        }

        .tl-card h3 {
            font-family: 'Syne', sans-serif;
            font-size: 1.2rem; font-weight: 700;
        }

        .tl-card .inst { color: var(--red); font-size: 0.9rem; margin-top: 3px; }
        .tl-card p { color: var(--muted); font-size: 0.9rem; line-height: 1.7; margin-top: 0.8rem; }

        /* EXPERIENCE */
        #experience { max-width: 1300px; }

        /* CONTACT */
        #contact {
            max-width: 1300px;
            display: grid;
            grid-template-columns: 1fr 1.4fr;
            gap: 5rem;
            align-items: start;
        }

        .contact-info h2 { margin-bottom: 0.5rem; }

        .contact-cards { display: flex; flex-direction: column; gap: 1rem; margin-top: 2rem; }

        .contact-card {
            display: flex; align-items: center; gap: 1.2rem;
            background: var(--bg2);
            border: 1px solid var(--border);
            border-radius: 14px;
            padding: 1.2rem 1.4rem;
            text-decoration: none;
            transition: all 0.3s;
            color: var(--text);
            cursor: none;
        }
        .contact-card:hover {
            border-color: var(--social-color, var(--red));
            background: var(--social-bg, var(--red-dim));
            transform: translateX(4px);
        }

        .contact-card .cc-icon {
            width: 48px; height: 48px;
            border-radius: 12px;
            display: flex; align-items: center; justify-content: center;
            font-size: 1.3rem;
            flex-shrink: 0;
            transition: all 0.3s;
        }

        /* Branded contact card icons */
        .contact-card.social-linkedin .cc-icon { background: rgba(10,102,194,0.15); color: #0A66C2; }
        .contact-card.social-github .cc-icon   { background: rgba(230,237,243,0.1); color: #e6edf3; }
        .contact-card.social-twitter .cc-icon  { background: rgba(231,231,231,0.1); color: #e7e7e7; }
        .contact-card.social-instagram .cc-icon{ background: rgba(225,48,108,0.12); color: #E1306C; }
        .contact-card.social-email .cc-icon    { background: rgba(234,67,53,0.12); color: #EA4335; }
        .contact-card.social-phone .cc-icon    { background: rgba(37,211,102,0.12); color: #25D366; }

        .contact-card.social-linkedin { --social-color: #0A66C2; --social-bg: rgba(10,102,194,0.08); }
        .contact-card.social-github   { --social-color: #e6edf3; --social-bg: rgba(230,237,243,0.06); }
        .contact-card.social-twitter  { --social-color: #e7e7e7; --social-bg: rgba(231,231,231,0.06); }
        .contact-card.social-instagram{ --social-color: #E1306C; --social-bg: rgba(225,48,108,0.08); }
        .contact-card.social-email    { --social-color: #EA4335; --social-bg: rgba(234,67,53,0.08); }
        .contact-card.social-phone    { --social-color: #25D366; --social-bg: rgba(37,211,102,0.08); }
        .contact-card .cc-label { font-size: 0.75rem; color: var(--muted); text-transform: uppercase; letter-spacing: 0.08em; }
        .contact-card .cc-val { font-size: 0.92rem; font-weight: 500; margin-top: 2px; }

        /* CONTACT FORM */
        .contact-form-wrap {
            background: var(--bg2);
            border: 1px solid var(--border);
            border-radius: 24px;
            padding: 2.5rem;
        }

        .contact-form-wrap h3 {
            font-family: 'Syne', sans-serif;
            font-size: 1.5rem; font-weight: 700;
            margin-bottom: 1.8rem;
        }

        .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
        .form-group { margin-bottom: 1.2rem; }
        .form-group label { display: block; font-size: 0.8rem; color: var(--muted); text-transform: uppercase; letter-spacing: 0.08em; margin-bottom: 0.5rem; }
        .form-group input,
        .form-group textarea {
            width: 100%;
            background: var(--bg3);
            border: 1.5px solid var(--border);
            border-radius: 12px;
            padding: 0.9rem 1.2rem;
            color: var(--text);
            font-family: 'DM Sans', sans-serif;
            font-size: 0.95rem;
            transition: border-color 0.3s;
            outline: none;
            cursor: none;
        }
        .form-group input:focus,
        .form-group textarea:focus { border-color: var(--red); }
        .form-group textarea { resize: vertical; min-height: 110px; }

        .btn-send {
            width: 100%;
            padding: 1rem;
            background: var(--red);
            color: #fff;
            border: none;
            border-radius: 12px;
            font-family: 'Syne', sans-serif;
            font-size: 1rem;
            font-weight: 700;
            letter-spacing: 0.04em;
            cursor: none;
            transition: all 0.3s;
        }
        .btn-send:hover {
            background: transparent;
            color: var(--red);
            box-shadow: 0 0 0 2px var(--red);
        }

        /* FOOTER */
        footer {
            border-top: 1px solid var(--border);
            padding: 2.5rem 6%;
            display: flex; align-items: center; justify-content: space-between;
            flex-wrap: wrap; gap: 1rem;
        }

        footer .logo { text-decoration: none; font-family: 'Syne', sans-serif; font-size: 1.8rem; font-weight: 800; color: var(--red); }
        footer p { color: var(--muted); font-size: 0.85rem; }

        .footer-socials { display: flex; gap: 0.8rem; }
        .footer-socials a {
            width: 36px; height: 36px;
            border: 1px solid var(--border);
            border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            color: var(--muted);
            font-size: 0.9rem;
            text-decoration: none;
            transition: all 0.3s;
            cursor: none;
        }
        .footer-socials a:hover { border-color: var(--social-color, var(--red)); color: var(--social-color, var(--red)); }
        .footer-socials a.social-linkedin { color: #0A66C2; border-color: rgba(10,102,194,0.3); }
        .footer-socials a.social-github   { color: #e6edf3; border-color: rgba(230,237,243,0.2); }
        .footer-socials a.social-twitter  { color: #e7e7e7; border-color: rgba(231,231,231,0.2); }
        .footer-socials a.social-instagram{ color: #E1306C; border-color: rgba(225,48,108,0.3); }
        .footer-socials a.social-email    { color: #EA4335; border-color: rgba(234,67,53,0.3); }
        .footer-socials a.social-linkedin:hover { background: rgba(10,102,194,0.12); }
        .footer-socials a.social-github:hover   { background: rgba(230,237,243,0.08); }
        .footer-socials a.social-twitter:hover  { background: rgba(231,231,231,0.08); }
        .footer-socials a.social-instagram:hover{ background: rgba(225,48,108,0.12); }
        .footer-socials a.social-email:hover    { background: rgba(234,67,53,0.12); }

        /* ANIMATIONS */
        @keyframes fadeUp {
            from { opacity: 0; transform: translateY(28px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .reveal {
            opacity: 0; transform: translateY(30px);
            transition: opacity 0.7s, transform 0.7s;
        }
        .reveal.visible { opacity: 1; transform: none; }

        /* MOBILE NAV */
        .mobile-nav {
            display: none;
            position: fixed;
            top: 0; right: -100%;
            width: 70%; max-width: 300px;
            height: 100vh;
            background: var(--bg2);
            border-left: 1px solid var(--border);
            z-index: 600;
            padding: 5rem 2rem 2rem;
            flex-direction: column;
            gap: 1.5rem;
            transition: right 0.35s cubic-bezier(0.4,0,0.2,1);
        }
        .mobile-nav.open { right: 0; }
        .mobile-nav a {
            font-family: 'Syne', sans-serif;
            font-size: 1.4rem; font-weight: 700;
            color: var(--muted); text-decoration: none;
            transition: color 0.2s;
        }
        .mobile-nav a:hover { color: var(--red); }
        .mobile-overlay {
            display: none;
            position: fixed; inset: 0;
            background: rgba(0,0,0,0.5);
            z-index: 590;
            backdrop-filter: blur(4px);
        }
        .mobile-overlay.open { display: block; }

        .menu-close {
            position: absolute; top: 1.5rem; right: 1.5rem;
            background: none; border: none; color: var(--text);
            font-size: 1.6rem; cursor: pointer;
        }

        /* RESPONSIVE */
        @media (max-width: 900px) {
            nav { display: none; }
            .hamburger { display: flex; }
            .mobile-nav { display: flex; }

            .hero-inner { flex-direction: column-reverse; text-align: center; }
            .hero-image-frame { width: 240px; height: 240px; }
            .hero-actions { justify-content: center; }
            .hero-socials { justify-content: center; }
            .hero-desc { margin: 1.4rem auto 2.2rem; }
            .card-proj { display: none; }
            .card-exp { display: none; }

            #about { grid-template-columns: 1fr; }
            .about-img-wrap { max-width: 300px; }
            #contact { grid-template-columns: 1fr; }
            .form-row { grid-template-columns: 1fr; }
        }

        @media (max-width: 600px) {
            .info-grid { grid-template-columns: 1fr; }
        }

        /* PROJECTS */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
            margin-top: 3rem;
        }

        .project-card {
            background: var(--bg2);
            border: 1px solid var(--border);
            border-radius: 20px;
            overflow: hidden;
            transition: all 0.35s;
            display: flex;
            flex-direction: column;
        }

        .project-card:hover {
            border-color: var(--red);
            transform: translateY(-6px);
            box-shadow: 0 24px 60px rgba(183,75,75,0.15);
        }

        .project-banner {
            width: 100%;
            height: 160px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3.5rem;
            position: relative;
            overflow: hidden;
        }

        .project-banner::after {
            content: '';
            position: absolute; inset: 0;
            background: linear-gradient(to bottom, transparent 50%, var(--bg2));
        }

        .banner-jarvis   { background: linear-gradient(135deg, #0a0a1a, #1a0a2e, #0d1117); }
        .banner-medicos  { background: linear-gradient(135deg, #0a1a0a, #0d2818, #0d1117); }
        .banner-crypto   { background: linear-gradient(135deg, #1a1200, #2a1f00, #0d1117); }
        .banner-flappy   { background: linear-gradient(135deg, #001a2e, #0a1428, #0d1117); }
        .banner-eventora { background: linear-gradient(135deg, #1a0a12, #2a0d1f, #0d1117); }

        .project-body { padding: 1.5rem; flex: 1; display: flex; flex-direction: column; }

        .project-tags { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-bottom: 1rem; }
        .project-tag {
            font-size: 0.72rem;
            letter-spacing: 0.06em;
            text-transform: uppercase;
            padding: 0.25rem 0.75rem;
            border-radius: 100px;
            background: var(--red-dim);
            color: var(--red);
            border: 1px solid var(--border);
            font-weight: 500;
        }

        .project-body h3 {
            font-family: 'Syne', sans-serif;
            font-size: 1.25rem;
            font-weight: 700;
            margin-bottom: 0.6rem;
        }

        .project-body p {
            color: var(--muted);
            font-size: 0.88rem;
            line-height: 1.7;
            flex: 1;
        }

        .project-footer {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-top: 1.4rem;
            padding-top: 1rem;
            border-top: 1px solid var(--border);
        }

        .project-link {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            font-size: 0.85rem;
            font-weight: 600;
            color: var(--red);
            text-decoration: none;
            transition: gap 0.2s;
        }
        .project-link:hover { gap: 10px; }

        /* CERTIFICATIONS */
        .cert-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 1.4rem;
            margin-top: 3rem;
        }

        .cert-card {
            background: var(--bg2);
            border: 1px solid var(--border);
            border-radius: 20px;
            padding: 1.8rem;
            display: flex;
            flex-direction: column;
            gap: 1.2rem;
            transition: all 0.35s;
            text-decoration: none;
            color: var(--text);
            cursor: none;
            position: relative;
            overflow: hidden;
        }

        .cert-card::before {
            content: '';
            position: absolute; top: 0; left: 0;
            width: 100%; height: 2px;
            transform: scaleX(0); transform-origin: left;
            transition: transform 0.35s;
        }

        .cert-card.cert-ibm::before      { background: #0f62fe; }
        .cert-card.cert-forage::before   { background: #6c63ff; }
        .cert-card.cert-oracle::before   { background: #f80000; }
        .cert-card.cert-hackerrank::before { background: #00ea64; }

        .cert-card:hover::before { transform: scaleX(1); }

        .cert-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 50px rgba(0,0,0,0.4);
        }

        .cert-card.cert-ibm:hover      { border-color: #0f62fe; }
        .cert-card.cert-forage:hover   { border-color: #6c63ff; }
        .cert-card.cert-oracle:hover   { border-color: #f80000; }
        .cert-card.cert-hackerrank:hover { border-color: #00ea64; }

        .cert-logo {
            width: 52px; height: 52px;
            border-radius: 12px;
            display: flex; align-items: center; justify-content: center;
            font-size: 1.6rem;
            font-weight: 900;
            font-family: 'Syne', sans-serif;
            flex-shrink: 0;
        }

        .cert-ibm .cert-logo      { background: rgba(15,98,254,0.15); color: #0f62fe; }
        .cert-forage .cert-logo   { background: rgba(108,99,255,0.15); color: #6c63ff; }
        .cert-oracle .cert-logo   { background: rgba(248,0,0,0.12); color: #f80000; }
        .cert-hackerrank .cert-logo { background: rgba(0,234,100,0.12); color: #00ea64; }

        .cert-header { display: flex; align-items: center; gap: 1rem; }

        .cert-issuer {
            font-size: 0.72rem;
            letter-spacing: 0.1em;
            text-transform: uppercase;
            font-weight: 600;
        }
        .cert-ibm .cert-issuer      { color: #0f62fe; }
        .cert-forage .cert-issuer   { color: #6c63ff; }
        .cert-oracle .cert-issuer   { color: #f80000; }
        .cert-hackerrank .cert-issuer { color: #00ea64; }

        .cert-card h3 {
            font-family: 'Syne', sans-serif;
            font-size: 1.05rem;
            font-weight: 700;
            line-height: 1.3;
        }

        .cert-card p {
            color: var(--muted);
            font-size: 0.85rem;
            line-height: 1.65;
            flex: 1;
        }

        .cert-footer {
            display: flex; align-items: center; justify-content: space-between;
            padding-top: 1rem;
            border-top: 1px solid var(--border);
            font-size: 0.8rem;
            color: var(--muted);
        }

        .cert-view {
            display: inline-flex; align-items: center; gap: 5px;
            font-size: 0.82rem; font-weight: 600;
            transition: gap 0.2s;
        }
        .cert-ibm .cert-view      { color: #0f62fe; }
        .cert-forage .cert-view   { color: #6c63ff; }
        .cert-oracle .cert-view   { color: #f80000; }
        .cert-hackerrank .cert-view { color: #00ea64; }
        .cert-view:hover { gap: 9px; }

        /* TOAST */
        .toast {
            position: fixed; bottom: 2rem; left: 50%;
            transform: translateX(-50%) translateY(20px);
            background: var(--bg2);
            border: 1px solid var(--border);
            border-radius: 100px;
            padding: 0.8rem 1.8rem;
            font-size: 0.9rem;
            color: var(--text);
            opacity: 0;
            transition: all 0.4s;
            z-index: 9000;
            pointer-events: none;
        }
        .toast.show { opacity: 1; transform: translateX(-50%) translateY(0); }
        .toast.success { border-color: #4ade80; color: #4ade80; }
    </style>
</head>
<body>

<!-- CURSOR -->
<div id="cursor"></div>
<div id="cursor-ring"></div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<!-- MOBILE NAV -->
<div class="mobile-overlay" id="overlay" onclick="closeMobileNav()"></div>
<nav class="mobile-nav" id="mobileNav">
    <button class="menu-close" onclick="closeMobileNav()"><i class="fa fa-times"></i></button>
    <a href="#home" onclick="closeMobileNav()">Home</a>
    <a href="#about" onclick="closeMobileNav()">About</a>
    <a href="#services" onclick="closeMobileNav()">Services</a>
    <a href="#skills" onclick="closeMobileNav()">Skills</a>
    <a href="#education" onclick="closeMobileNav()">Education</a>
    <a href="#experience" onclick="closeMobileNav()">Experience</a>
    <a href="#projects" onclick="closeMobileNav()">Projects</a>
    <a href="#certifications" onclick="closeMobileNav()">Certifications</a>
    <a href="#contact" onclick="closeMobileNav()">Contact</a>
</nav>

<!-- HEADER -->
<header id="header">
    <a href="#home" class="logo">Aryan</a>
    <nav>
        <a href="#home" class="active">Home</a>
        <a href="#about">About</a>
        <a href="#services">Services</a>
        <a href="#skills">Skills</a>
        <a href="#education">Education</a>
        <a href="#experience">Experience</a>
        <a href="#projects">Projects</a>
        <a href="#certifications">Certifications</a>
        <a href="#contact">Contact</a>
    </nav>
    <div class="hamburger" onclick="openMobileNav()">
        <span></span><span></span><span></span>
    </div>
</header>

<!-- HERO -->
<section class="hero" id="home">
    <div class="hero-bg"></div>
    <div class="noise"></div>

    <div class="hero-inner">
        <div class="hero-text">
            <div class="hero-badge">
                <span class="dot"></span>
                Available for opportunities
            </div>
            <h1>Hi, I'm<br><span class="name">Aryan</span></h1>
            <div class="typewriter-wrap">
                I'm a <span class="typed" id="typed"></span><span class="cursor-blink"></span>
            </div>
            <p class="hero-desc">
                A student at SRM Institute of Science and Technology, Delhi NCR Campus, driven by a passion for innovation. I aim to become an impactful software engineer who uses technology to shape the future.
            </p>
            <div class="hero-actions">
                <a href="#contact" class="btn-primary"><i class="fa fa-envelope"></i> Contact Me</a>
                <a href="#about" class="btn-outline"><i class="fa fa-user"></i> About Me</a>
            </div>
            <div class="hero-socials">
                <a href="https://www.linkedin.com/in/aryan4web3/" target="_blank" title="LinkedIn" class="social-linkedin"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg></i></a>
                <a href="https://github.com/alphaplus-ai" target="_blank" title="GitHub" class="social-github"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg></i></a>
                <a href="https://x.com/Aryan98380207" target="_blank" title="X / Twitter" class="social-twitter"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M18.901 1.153h3.68l-8.04 9.19L24 22.846h-7.406l-5.8-7.584-6.638 7.584H.474l8.6-9.83L0 1.154h7.594l5.243 6.932ZM17.61 20.644h2.039L6.486 3.24H4.298Z"/></svg></i></a>
                <a href="https://www.instagram.com/im.aryan.18/" target="_blank" title="Instagram" class="social-instagram"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 0C8.74 0 8.333.014 7.053.072 5.775.132 4.905.333 4.14.63c-.789.306-1.459.717-2.126 1.384S.935 3.35.63 4.14C.333 4.905.131 5.775.072 7.053.014 8.333 0 8.74 0 12s.014 3.667.072 4.947c.06 1.277.261 2.148.558 2.913.306.788.717 1.459 1.384 2.126.667.666 1.336 1.079 2.126 1.384.766.296 1.636.499 2.913.558C8.333 23.986 8.74 24 12 24s3.667-.014 4.947-.072c1.277-.06 2.148-.262 2.913-.558.788-.306 1.459-.718 2.126-1.384.666-.667 1.079-1.335 1.384-2.126.296-.765.499-1.636.558-2.913.06-1.28.072-1.687.072-4.947s-.014-3.667-.072-4.947c-.06-1.278-.262-2.149-.558-2.913-.306-.789-.718-1.459-1.384-2.126C21.319 1.347 20.651.935 19.86.63c-.765-.297-1.636-.499-2.913-.558C15.667.014 15.26 0 12 0zm0 2.16c3.203 0 3.585.016 4.85.071 1.17.055 1.805.249 2.227.415.562.217.96.477 1.382.896.419.42.679.819.896 1.381.164.422.36 1.057.413 2.227.057 1.266.07 1.646.07 4.85s-.015 3.585-.074 4.85c-.061 1.17-.256 1.805-.421 2.227-.224.562-.479.96-.899 1.382-.419.419-.824.679-1.38.896-.42.164-1.065.36-2.235.413-1.274.057-1.649.07-4.859.07-3.211 0-3.586-.015-4.859-.074-1.171-.061-1.816-.256-2.236-.421-.569-.224-.96-.479-1.379-.899-.421-.419-.69-.824-.9-1.38-.165-.42-.359-1.065-.42-2.235-.045-1.26-.061-1.649-.061-4.844 0-3.196.016-3.586.061-4.861.061-1.17.255-1.814.42-2.234.21-.57.479-.96.9-1.381.419-.419.81-.689 1.379-.898.42-.166 1.051-.361 2.221-.421 1.275-.045 1.65-.06 4.859-.06zm0 3.678a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zM12 16a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm6.406-11.845a1.44 1.44 0 1 0 0 2.881 1.44 1.44 0 0 0 0-2.881z"/></svg></i></a>
                <a href="mailto:aryangupta5818@gmail.com" title="Email" class="social-email"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg></i></a>
            </div>
        </div>

        <div class="hero-image-wrap">
            <div class="hero-image-frame">
                <!-- Replace src with your actual photo path -->
                <img src="main.jpg" alt="Aryan" onerror="this.style.display='none';document.getElementById('avatar').style.display='flex'">
                <div class="avatar-fallback" id="avatar" style="display:none;">A</div>
            </div>
            <div class="hero-float-card card-proj">
                <div class="fc-label">Projects</div>
                <div class="fc-val">4+</div>
            </div>
            <div class="hero-float-card card-exp">
                <div class="fc-label">Experience</div>
                <div class="fc-val">2+ yrs</div>
            </div>
        </div>
    </div>
</section>

<!-- ABOUT -->
<section id="about" style="max-width:1300px;margin:0 auto;">
    <div class="about-img-wrap reveal">
        <div class="about-img-box">
            <img src="main.jpg" alt="Aryan" onerror="this.style.display='none'">
            A
        </div>
        <div class="about-deco">
            <div class="big">2+</div>
            <div class="small">Years<br>Coding</div>
        </div>
    </div>
    <div class="about-text reveal">
        <div class="sec-label">About Me</div>
        <h2 class="sec-title">Passionate about<br>building the future</h2>
        <div class="sec-divider"></div>
        <p>I'm a Computer Science student at SRM Institute of Science and Technology, Delhi NCR Campus. My journey in technology is fueled by an insatiable curiosity and a drive to create software that makes a real difference.</p>
        <p>To me, software engineering goes far beyond writing code — it's about problem-solving, innovation, and crafting experiences that empower people. I'm constantly learning, building, and pushing my limits.</p>
        <div class="info-grid">
            <div class="info-item">
                <label>Name</label>
                <p>Aryan Gupta</p>
            </div>
            <div class="info-item">
                <label>Email</label>
                <p><a href="mailto:aryangupta5818@gmail.com" style="color:var(--red);text-decoration:none;">aryangupta5818@gmail.com</a></p>
            </div>
            <div class="info-item">
                <label>Phone</label>
                <p><a href="tel:+917827511004" style="color:var(--text);text-decoration:none;">+91 7827511004</a></p>
            </div>
            <div class="info-item">
                <label>Location</label>
                <p>Delhi NCR, India</p>
            </div>
            <div class="info-item">
                <label>University</label>
                <p>SRM IST Delhi NCR</p>
            </div>
            <div class="info-item">
                <label>Status</label>
                <p style="color:var(--red);">Open to Work</p>
            </div>
        </div>
        <a href="mailto:aryangupta5818@gmail.com" class="btn-primary" style="width:fit-content;"><i class="fa fa-download"></i> Get In Touch</a>
    </div>
</section>

<!-- SERVICES -->
<section id="services" style="max-width:1300px;margin:0 auto;">
    <div class="reveal">
        <div class="sec-label">What I Do</div>
        <h2 class="sec-title">Services</h2>
        <div class="sec-divider"></div>
    </div>
    <div class="services-grid">
        <div class="service-card reveal">
            <div class="service-icon"><i class="fa fa-code"></i></div>
            <h3>Web Development</h3>
            <p>Building responsive, performant, and visually stunning websites using modern HTML, CSS, and JavaScript.</p>
        </div>
        <div class="service-card reveal">
            <div class="service-icon"><i class="fa fa-layer-group"></i></div>
            <h3>Full Stack Development</h3>
            <p>Building complete web applications with front-end interfaces, database integration, and server-side logic.</p>
        </div>
        <div class="service-card reveal">
            <div class="service-icon"><i class="fa fa-robot"></i></div>
            <h3>AI & Automation</h3>
            <p>Building intelligent tools and automation scripts using Python, exploring AI APIs and sentiment analysis.</p>
        </div>
        <div class="service-card reveal">
            <div class="service-icon"><i class="fa fa-pen-nib"></i></div>
            <h3>Content Writing</h3>
            <p>Crafting engaging technical content, documentation, and articles that communicate complex ideas clearly.</p>
        </div>
        <div class="service-card reveal">
            <div class="service-icon"><i class="fa fa-mobile-screen"></i></div>
            <h3>UI/UX Design</h3>
            <p>Designing intuitive, user-centered interfaces that balance aesthetic appeal with functional excellence.</p>
        </div>
        <div class="service-card reveal">
            <div class="service-icon"><i class="fa fa-gamepad"></i></div>
            <h3>Game Development</h3>
            <p>Creating fun interactive browser-based games using JavaScript and HTML5 Canvas.</p>
        </div>
    </div>
</section>

<!-- SKILLS -->
<section id="skills" style="max-width:1300px;margin:0 auto;">
    <div class="reveal">
        <div class="sec-label">My Arsenal</div>
        <h2 class="sec-title">Skills & Technologies</h2>
        <div class="sec-divider"></div>
    </div>
    <div class="skills-grid">
        <div class="skill-chip reveal"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M1.5 0h21l-1.91 21.563L11.977 24l-8.564-2.438L1.5 0zm7.031 9.75l-.232-2.718 10.059.003.23-2.622L5.412 4.41l.698 8.01h9.126l-.326 3.426-2.91.804-2.955-.81-.188-2.11H6.248l.33 4.171L12 19.351l5.379-1.443.744-8.157H8.531z"/></svg></i><span>HTML5</span></div>
        <div class="skill-chip reveal"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M1.5 0h21l-1.91 21.563L11.977 24l-8.565-2.437L1.5 0zm17.09 4.413L5.41 4.41l.213 2.622 10.125.002-.255 2.716h-6.64l.24 2.573h6.182l-.366 3.523-2.91.804-2.956-.81-.188-2.11h-2.61l.29 3.855L12 19.288l5.373-1.53L18.59 4.413z"/></svg></i><span>CSS3</span></div>
        <div class="skill-chip reveal"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M0 0h24v24H0V0zm22.034 18.276c-.175-1.095-.888-2.015-3.003-2.873-.736-.345-1.554-.585-1.797-1.14-.091-.33-.105-.51-.046-.705.15-.646.915-.84 1.516-.66.39.12.75.42.976.9 1.034-.676 1.034-.676 1.755-1.125-.27-.42-.404-.601-.586-.78-.63-.705-1.469-1.065-2.834-1.034l-.705.089c-.676.165-1.32.525-1.71 1.005-1.14 1.291-.811 3.541.569 4.471 1.365 1.02 3.361 1.244 3.616 2.205.24 1.17-.87 1.545-1.966 1.41-.811-.176-1.26-.585-1.755-1.336l-1.83 1.051c.21.48.45.689.81 1.109 1.74 1.756 6.09 1.666 6.871-1.004.029-.09.24-.705.074-1.65l.046.067zm-8.983-7.245h-2.248c0 1.938-.009 3.864-.009 5.805 0 1.232.063 2.363-.138 2.711-.33.689-1.18.601-1.566.48-.396-.196-.597-.466-.83-.855-.063-.105-.11-.196-.127-.196l-1.825 1.125c.305.63.75 1.176 1.324 1.53.855.51 2.004.675 3.207.405.783-.226 1.458-.691 1.811-1.411.51-.93.402-2.07.397-3.346.012-2.054 0-4.109 0-6.179l.004-.069z"/></svg></i><span>JavaScript</span></div>
        <div class="skill-chip reveal"><i><svg viewBox="-11.5 -10.23174 23 20.46348" width="1em" height="1em" style="display:inline-block;vertical-align:-0.125em;"><circle r="2.05" fill="currentColor"/><g stroke="currentColor" stroke-width="1" fill="none"><ellipse rx="11" ry="4.2"/><ellipse rx="11" ry="4.2" transform="rotate(60)"/><ellipse rx="11" ry="4.2" transform="rotate(120)"/></g></svg></i><span>React</span></div>
        <div class="skill-chip reveal"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M22.394 6c-.167-.29-.398-.543-.652-.69L12.926.22c-.203-.116-.42-.174-.641-.174-.221 0-.437.058-.64.174L2.83 5.31c-.524.302-.848.87-.848 1.48v10.42c0 .61.324 1.178.848 1.48l1.906 1.1c.926.446 1.246.457 1.634.457 1.084 0 1.716-.618 1.716-1.685v-10.29c0-.148-.135-.144-.283-.144H6.756c-.148 0-.144-.004-.144.144v10.29c0 .488-.512.985-1.335.573L3.35 17.51a.19.19 0 0 1-.101-.174V6.916a.192.192 0 0 1 .1-.174L11.65 1.66a.2.2 0 0 1 .2 0l8.303 5.083a.19.19 0 0 1 .09.174v10.42a.19.19 0 0 1-.09.174l-8.301 4.87a.198.198 0 0 1-.2 0l-2.117-1.253c-.06-.036-.15-.049-.212-.014-.588.335-.696.379-1.243.567-.135.047-.336.128.075.35l2.76 1.633c.203.121.435.183.671.183.238 0 .47-.062.673-.183l8.303-4.87c.524-.31.848-.87.848-1.48V6.916c0-.478-.204-.938-.564-1.246Zm-6.788 8.878c-2.163 0-2.647-.657-2.803-1.812-.02-.146-.144-.145-.294-.145H11.32c-.166 0-.165.144-.165.31 0 1.582 1.28 3.043 4.323 3.043 3.14 0 4.66-1.216 4.66-3.4 0-2.166-1.465-2.741-4.557-3.15-3.13-.412-3.446-.62-3.446-1.35 0-.6.267-1.4 2.582-1.4 2.066 0 2.828.446 3.14 1.844.026.13.145.226.278.226h1.325c.083 0 .162-.033.22-.093.058-.06.088-.142.088-.226-.2-2.37-1.788-3.475-4.05-3.475-2.315 0-3.696 1.024-3.696 2.741 0 1.856 1.436 2.372 3.767 2.605 3.276.33 3.66.622 3.66 1.343 0 1.242-.996 1.775-2.912 1.775Z"/></svg></i><span>Node.js</span></div>
        <div class="skill-chip reveal">
            <svg width="34" height="21" viewBox="0 0 200 50" style="margin-bottom:0.5rem;">
                <text x="0" y="35" font-family="Syne, sans-serif" font-weight="800" font-size="34" fill="var(--red)">express</text>
            </svg>
            <span>Express.js</span>
        </div>
        <div class="skill-chip reveal">
            <svg width="20" height="29" viewBox="0 0 6.096 12.7" style="margin-bottom:0.5rem;">
                <path fill="var(--red)" d="M3.373 12.671s-.055-.688-.055-1.402c-.024-.075.16-.096.16-.096.146-.02.29-.108.42-.238a1.24 1.24 0 0 0 .296-.482c.192-.53.132-1.17-.155-1.643C3.523 8.02 3.048 7.05 3.048 7.05s-.475.972-.99 1.76c-.288.473-.348 1.114-.156 1.643.086.19.183.354.297.482.13.13.273.218.42.238 0 0 .183.021.16.096 0-.714-.056-1.402-.056-1.402S2.723 7.03 2.723 4.65c0-2.383.325-4.45.325-4.45s.325 2.067.325 4.45c0 2.38-.325 5.867-.325 5.867"/>
                <path fill="var(--red)" opacity="0.55" d="M3.048 0S1.06 2.62 1.06 6.61c0 2.61 1.02 4.4 1.66 5.238.13.166.293.288.44.38l.056.03s-.055-.688-.055-1.402c-.612-.86-1.113-2.114-1.113-3.79 0-1.973.512-3.626 1-4.79z"/>
            </svg>
            <span>MongoDB</span>
        </div>
        <div class="skill-chip reveal"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M14.25.18l.9.2.73.26.59.3.45.32.34.34.25.34.16.33.1.3.04.26.02.2-.01.13V8.5l-.05.63-.13.55-.21.46-.26.38-.3.31-.33.25-.35.19-.35.14-.33.1-.3.07-.26.04-.21.02H8.77l-.69.05-.59.14-.5.22-.41.27-.33.32-.27.35-.2.36-.15.37-.1.35-.07.32-.04.27-.02.21v3.06H3.17l-.21-.03-.28-.07-.32-.12-.35-.18-.36-.26-.36-.36-.35-.46-.32-.59-.28-.73-.21-.88-.14-1.05-.05-1.23.06-1.22.16-1.04.24-.87.32-.71.36-.57.4-.44.42-.33.42-.24.4-.16.36-.1.32-.05.24-.01h.16l.06.01h8.16v-.83H6.18l-.01-2.75-.02-.37.05-.34.11-.31.17-.28.25-.26.31-.23.38-.2.44-.18.51-.15.58-.12.64-.1.71-.06.77-.04.84-.02 1.27.05zm-6.3 1.98l-.23.33-.08.41.08.41.23.34.33.22.41.09.41-.09.33-.22.23-.34.08-.41-.08-.41-.23-.33-.33-.22-.41-.09-.41.09zm13.09 3.95l.28.06.32.12.35.18.36.27.36.35.35.47.32.59.28.73.21.88.14 1.04.05 1.23-.06 1.23-.16 1.04-.24.86-.32.71-.36.57-.4.45-.42.33-.42.24-.4.16-.36.09-.32.05-.24.02-.16-.01h-8.22v.82h5.84l.02 2.76.02.37-.05.34-.11.31-.17.29-.25.25-.31.24-.38.2-.44.17-.51.15-.58.13-.64.09-.71.07-.77.04-.84.01-1.27-.04-1.07-.14-.9-.2-.73-.25-.59-.3-.45-.33-.34-.34-.25-.34-.16-.33-.1-.3-.04-.25-.02-.2.01-.13v-5.34l.05-.64.13-.54.21-.46.26-.38.3-.32.33-.24.35-.2.35-.14.33-.1.3-.06.26-.04.21-.02.13-.01h5.84l.69-.05.59-.14.5-.21.41-.28.33-.32.27-.35.2-.36.15-.36.1-.35.07-.32.04-.28.02-.21V6.07h2.09l.14.01zm-6.47 14.25l-.23.33-.08.41.08.41.23.33.33.23.41.08.41-.08.33-.23.23-.33.08-.41-.08-.41-.23-.33-.33-.23-.41-.08-.41.08z"/></svg></i><span>Python</span></div>
        <div class="skill-chip reveal"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 3C7.58 3 4 4.79 4 7s3.58 4 8 4 8-1.79 8-4-3.58-4-8-4zM4 9v3c0 2.21 3.58 4 8 4s8-1.79 8-4V9c0 2.21-3.58 4-8 4s-8-1.79-8-4zm0 5v3c0 2.21 3.58 4 8 4s8-1.79 8-4v-3c0 2.21-3.58 4-8 4s-8-1.79-8-4z"/></svg></i><span>SQL</span></div>
        <div class="skill-chip reveal"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg></i><span>GitHub</span></div>
        <div class="skill-chip reveal"><i><svg viewBox="0 0 90 34" width="2.2em" height="1em" style="display:inline-block;vertical-align:-0.125em;"><text x="0" y="27" font-family="Syne, sans-serif" font-weight="800" font-size="28" fill="currentColor">C++</text></svg></i><span>C/C++</span></div>
    </div>
</section>

<!-- EDUCATION -->
<section id="education" style="max-width:1300px;margin:0 auto;">
    <div class="reveal">
        <div class="sec-label">My Journey</div>
        <h2 class="sec-title">Education</h2>
        <div class="sec-divider"></div>
    </div>
    <div class="timeline">
        <div class="timeline-item reveal">
            <div class="tl-year">2024 — Present</div>
            <div class="tl-card">
                <h3>B.Tech in Computer Science & Engineering</h3>
                <div class="inst">SRM Institute of Science and Technology, Delhi NCR Campus</div>
                <p>Pursuing a comprehensive degree in Computer Science with focus on software engineering, data structures, algorithms, and modern web technologies. Actively participating in coding clubs and hackathons.</p>
            </div>
        </div>
        <div class="timeline-item reveal">
            <div class="tl-year">2010 — 2024</div>
            <div class="tl-card">
                <h3>Class XII — Science (PCM)</h3>
                <div class="inst">KSK Academy</div>
                <p>Completed higher secondary with Physics, Chemistry, and Mathematics. Built a strong analytical and problem-solving foundation that drives my passion for engineering.</p>
            </div>
        </div>
    </div>
</section>

<!-- EXPERIENCE -->
<section id="experience" style="max-width:1300px;margin:0 auto;">
    <div class="reveal">
        <div class="sec-label">Work History</div>
        <h2 class="sec-title">Experience</h2>
        <div class="sec-divider"></div>
    </div>
    <div class="timeline">
        <div class="timeline-item reveal">
            <div class="tl-year">June 2026 — July 2026</div>
            <div class="tl-card">
                <h3>Full Stack Developer Intern</h3>
                <div class="inst">CDAC-Patna</div>
                <p>Worked as a Full Stack Developer Intern at CDAC-Patna, building and maintaining web applications using the MERN stack (MongoDB, Express.js, React, Node.js). Contributed to designing REST APIs, integrating databases, and developing responsive front-end interfaces, while collaborating with the team on real-world project requirements and gaining hands-on experience with industry-standard development practices.</p>
            </div>
        </div>
        <div class="timeline-item reveal">
            <div class="tl-year">2024 — Present</div>
            <div class="tl-card">
                <h3>Web Developer & Content Writer</h3>
                <div class="inst">Freelance / Independent Projects</div>
                <p>Building personal and open-source projects including AI tools, web apps, data analysis scripts, and games. Continuously learning through hands-on development and real-world problem solving.</p>
            </div>
        </div>

    </div>
</section>

<!-- PROJECTS -->
<section id="projects" style="max-width:1300px;margin:0 auto;">
    <div class="reveal">
        <div class="sec-label">What I've Built</div>
        <h2 class="sec-title">Projects</h2>
        <div class="sec-divider"></div>
    </div>
    <div class="projects-grid">

        <!-- Eventora -->
        <div class="project-card reveal">
            <div class="project-banner banner-eventora">🎟️</div>
            <div class="project-body">
                <div class="project-tags">
                    <span class="project-tag">React</span>
                    <span class="project-tag">Node.js</span>
                    <span class="project-tag">Express.js</span>
                    <span class="project-tag">MongoDB</span>
                </div>
                <h3>Eventora</h3>
                <p>A full-stack event ticketing platform built with React + Vite on the frontend and Express.js + MongoDB on the backend. Features a complete booking flow — event browsing, zone-based seat selection, secure checkout with payment integration, and automated confirmation emails.</p>
                <div class="project-footer">
                    <a href="https://github.com/alphaplus-ai/Eventora" target="_blank" class="project-link">
                        <i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg></i> View on GitHub <i class="fa fa-arrow-right" style="font-size:0.75rem;"></i>
                    </a>
                </div>
            </div>
        </div>

        <!-- JARVIS AI -->
        <div class="project-card reveal">
            <div class="project-banner banner-jarvis">🤖</div>
            <div class="project-body">
                <div class="project-tags">
                    <span class="project-tag">Python</span>
                    <span class="project-tag">AI</span>
                    <span class="project-tag">Automation</span>
                </div>
                <h3>J.A.R.V.I.S. AI</h3>
                <p>A personal AI assistant inspired by Iron Man's JARVIS. Built with Python, it handles voice commands, automation tasks, and intelligent responses — a real-world AI companion project.</p>
                <div class="project-footer">
                    <a href="https://github.com/alphaplus-ai/J.A.R.V.I.S.-AI" target="_blank" class="project-link">
                        <i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg></i> View on GitHub <i class="fa fa-arrow-right" style="font-size:0.75rem;"></i>
                    </a>
                </div>
            </div>
        </div>

        <!-- Fortis Medicos -->
        <div class="project-card reveal">
            <div class="project-banner banner-medicos">🏥</div>
            <div class="project-body">
                <div class="project-tags">
                    <span class="project-tag">MySQL</span>
                    <span class="project-tag">Web App</span>
                    <span class="project-tag">Database</span>
                </div>
                <h3>Fortis Medicos</h3>
                <p>An online medical store powered by a MySQL database. Features product listings, inventory management, and a clean interface for browsing and ordering medical supplies.</p>
                <div class="project-footer">
                    <a href="https://github.com/alphaplus-ai/Online-Medical-Store-using-MySQL-Database" target="_blank" class="project-link">
                        <i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg></i> View on GitHub <i class="fa fa-arrow-right" style="font-size:0.75rem;"></i>
                    </a>
                </div>
            </div>
        </div>

        <!-- Crypto Sentiment -->
        <div class="project-card reveal">
            <div class="project-banner banner-crypto">📈</div>
            <div class="project-body">
                <div class="project-tags">
                    <span class="project-tag">Python</span>
                    <span class="project-tag">Data Analysis</span>
                    <span class="project-tag">Crypto</span>
                </div>
                <h3>Crypto Sentiment Trading Analysis</h3>
                <p>A data-driven project that analyzes market sentiment around cryptocurrencies to provide trading insights. Combines web scraping, sentiment analysis, and data visualization.</p>
                <div class="project-footer">
                    <a href="https://github.com/alphaplus-ai/crypto-sentiment-trading-analysis" target="_blank" class="project-link">
                        <i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg></i> View on GitHub <i class="fa fa-arrow-right" style="font-size:0.75rem;"></i>
                    </a>
                </div>
            </div>
        </div>

        <!-- Flappy Bird -->
        <div class="project-card reveal">
            <div class="project-banner banner-flappy">🐦</div>
            <div class="project-body">
                <div class="project-tags">
                    <span class="project-tag">JavaScript</span>
                    <span class="project-tag">HTML5</span>
                    <span class="project-tag">Game</span>
                </div>
                <h3>Flappy Bird</h3>
                <p>A faithful browser-based recreation of the iconic Flappy Bird game built with pure JavaScript and HTML5 Canvas. Smooth physics, score tracking, and addictive gameplay.</p>
                <div class="project-footer">
                    <a href="https://github.com/alphaplus-ai/FLAPPYBIRD" target="_blank" class="project-link">
                        <i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg></i> View on GitHub <i class="fa fa-arrow-right" style="font-size:0.75rem;"></i>
                    </a>
                </div>
            </div>
        </div>

    </div>
</section>

<!-- CERTIFICATIONS -->
<section id="certifications" style="max-width:1300px;margin:0 auto;">
    <div class="reveal">
        <div class="sec-label">Credentials</div>
        <h2 class="sec-title">Certifications</h2>
        <div class="sec-divider"></div>
    </div>
    <div class="cert-grid">

        <!-- IBM -->
        <a href="https://www.credly.com/badges/0781fa5f-c651-4c28-80a4-e27029d170d0/linked_in_profile" target="_blank" class="cert-card cert-ibm reveal">
            <div class="cert-header">
                <div class="cert-logo">
                    <svg width="28" height="28" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <rect width="32" height="4" rx="1" fill="#0f62fe"/>
                        <rect y="7" width="32" height="4" rx="1" fill="#0f62fe"/>
                        <rect x="6" y="14" width="20" height="4" rx="1" fill="#0f62fe"/>
                        <rect x="6" y="21" width="20" height="4" rx="1" fill="#0f62fe"/>
                        <rect y="28" width="32" height="4" rx="1" fill="#0f62fe"/>
                    </svg>
                </div>
                <div>
                    <div class="cert-issuer">IBM</div>
                    <div style="font-size:0.72rem;color:var(--muted);">via Credly</div>
                </div>
            </div>
            <h3>IBM Certified Badge</h3>
            <p>Issued by IBM, verified through Credly. Demonstrates knowledge and competency in IBM technologies and professional skills.</p>
            <div class="cert-footer">
                <span>🏅 Verified Badge</span>
                <span class="cert-view">View Certificate <i class="fa fa-arrow-right" style="font-size:0.7rem;"></i></span>
            </div>
        </a>

        <!-- Forage -->
        <a href="https://www.theforage.com/completion-certificates/pmnMSL4QiQ9JCgE3W/kkE9HyeNcw6rwCRGw_pmnMSL4QiQ9JCgE3W_694ab4621b66a8065726b205_1766504346746_completion_certificate.pdf" target="_blank" class="cert-card cert-forage reveal">
            <div class="cert-header">
                <div class="cert-logo">
                    <svg width="28" height="28" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <circle cx="16" cy="16" r="14" stroke="#6c63ff" stroke-width="3"/>
                        <path d="M10 16 L14 20 L22 12" stroke="#6c63ff" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                </div>
                <div>
                    <div class="cert-issuer">Forage</div>
                    <div style="font-size:0.72rem;color:var(--muted);">Virtual Experience</div>
                </div>
            </div>
            <h3>Forage Virtual Experience Program</h3>
            <p>Completed a virtual job simulation on Forage, gaining hands-on industry experience and practical skills valued by top employers.</p>
            <div class="cert-footer">
                <span>📄 Completion Certificate</span>
                <span class="cert-view">View Certificate <i class="fa fa-arrow-right" style="font-size:0.7rem;"></i></span>
            </div>
        </a>

        <!-- Oracle -->
        <a href="https://catalog-education.oracle.com/ords/certview/sharebadge?id=5B6D1E567C85FDEDA7666682269A0E6148094682B871E354C30E157BE588B3F8" target="_blank" class="cert-card cert-oracle reveal">
            <div class="cert-header">
                <div class="cert-logo">
                    <svg width="30" height="18" viewBox="0 0 60 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <ellipse cx="12" cy="12" rx="12" ry="12" fill="#f80000"/>
                        <ellipse cx="48" cy="12" rx="12" ry="12" fill="#f80000"/>
                        <rect x="12" y="0" width="36" height="24" fill="#f80000"/>
                        <ellipse cx="12" cy="12" rx="7" ry="12" fill="#f80000"/>
                        <ellipse cx="48" cy="12" rx="7" ry="12" fill="#f80000"/>
                    </svg>
                </div>
                <div>
                    <div class="cert-issuer">Oracle</div>
                    <div style="font-size:0.72rem;color:var(--muted);">Oracle Education</div>
                </div>
            </div>
            <h3>Oracle Certified Badge</h3>
            <p>Earned an Oracle certification badge, validating expertise in Oracle technologies and database fundamentals through the Oracle Education catalog.</p>
            <div class="cert-footer">
                <span>🏅 Verified Badge</span>
                <span class="cert-view">View Certificate <i class="fa fa-arrow-right" style="font-size:0.7rem;"></i></span>
            </div>
        </a>

        <!-- HackerRank -->
        <a href="https://www.hackerrank.com/certificates/iframe/7c56c0087b24" target="_blank" class="cert-card cert-hackerrank reveal">
            <div class="cert-header">
                <div class="cert-logo">
                    <svg width="28" height="28" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M16 2 C8.268 2 2 8.268 2 16 C2 23.732 8.268 30 16 30 C23.732 30 30 23.732 30 16 C30 8.268 23.732 2 16 2Z" fill="#00ea64"/>
                        <path d="M11 10 L11 22 M11 16 L21 16 M21 10 L21 22" stroke="#1a1a1a" stroke-width="2.5" stroke-linecap="round"/>
                    </svg>
                </div>
                <div>
                    <div class="cert-issuer">HackerRank</div>
                    <div style="font-size:0.72rem;color:var(--muted);">Skill Certificate</div>
                </div>
            </div>
            <h3>HackerRank Skill Certificate</h3>
            <p>Earned a verified HackerRank skill certificate, demonstrating coding proficiency and problem-solving ability assessed through timed challenges.</p>
            <div class="cert-footer">
                <span>✅ Verified Certificate</span>
                <span class="cert-view">View Certificate <i class="fa fa-arrow-right" style="font-size:0.7rem;"></i></span>
            </div>
        </a>

    </div>
</section>

<!-- CONTACT -->
<section id="contact" style="max-width:1300px;margin:0 auto;display:grid;grid-template-columns:1fr 1.4fr;gap:5rem;align-items:start;">
    <div class="contact-info reveal">
        <div class="sec-label">Let's Talk</div>
        <h2 class="sec-title">Get In<br>Touch</h2>
        <div class="sec-divider"></div>
        <p style="color:var(--muted);line-height:1.8;margin-bottom:2rem;">Have a project in mind, a collaboration idea, or just want to say hello? My inbox is always open.</p>
        <div class="contact-cards">
            <a href="mailto:aryangupta5818@gmail.com" class="contact-card social-email">
                <div class="cc-icon"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg></i></div>
                <div>
                    <div class="cc-label">Email</div>
                    <div class="cc-val">aryangupta5818@gmail.com</div>
                </div>
            </a>
            <a href="tel:+917827511004" class="contact-card social-phone">
                <div class="cc-icon"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z"/></svg></i></div>
                <div>
                    <div class="cc-label">Phone</div>
                    <div class="cc-val">+91 7827511004</div>
                </div>
            </a>
            <a href="https://www.linkedin.com/in/aryan4web3/" target="_blank" class="contact-card social-linkedin">
                <div class="cc-icon"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg></i></div>
                <div>
                    <div class="cc-label">LinkedIn</div>
                    <div class="cc-val">aryan4web3</div>
                </div>
            </a>
            <a href="https://github.com/alphaplus-ai" target="_blank" class="contact-card social-github">
                <div class="cc-icon"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg></i></div>
                <div>
                    <div class="cc-label">GitHub</div>
                    <div class="cc-val">alphaplus-ai</div>
                </div>
            </a>
            <a href="https://www.instagram.com/im.aryan.18/" target="_blank" class="contact-card social-instagram">
                <div class="cc-icon"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 0C8.74 0 8.333.014 7.053.072 5.775.132 4.905.333 4.14.63c-.789.306-1.459.717-2.126 1.384S.935 3.35.63 4.14C.333 4.905.131 5.775.072 7.053.014 8.333 0 8.74 0 12s.014 3.667.072 4.947c.06 1.277.261 2.148.558 2.913.306.788.717 1.459 1.384 2.126.667.666 1.336 1.079 2.126 1.384.766.296 1.636.499 2.913.558C8.333 23.986 8.74 24 12 24s3.667-.014 4.947-.072c1.277-.06 2.148-.262 2.913-.558.788-.306 1.459-.718 2.126-1.384.666-.667 1.079-1.335 1.384-2.126.296-.765.499-1.636.558-2.913.06-1.28.072-1.687.072-4.947s-.014-3.667-.072-4.947c-.06-1.278-.262-2.149-.558-2.913-.306-.789-.718-1.459-1.384-2.126C21.319 1.347 20.651.935 19.86.63c-.765-.297-1.636-.499-2.913-.558C15.667.014 15.26 0 12 0zm0 2.16c3.203 0 3.585.016 4.85.071 1.17.055 1.805.249 2.227.415.562.217.96.477 1.382.896.419.42.679.819.896 1.381.164.422.36 1.057.413 2.227.057 1.266.07 1.646.07 4.85s-.015 3.585-.074 4.85c-.061 1.17-.256 1.805-.421 2.227-.224.562-.479.96-.899 1.382-.419.419-.824.679-1.38.896-.42.164-1.065.36-2.235.413-1.274.057-1.649.07-4.859.07-3.211 0-3.586-.015-4.859-.074-1.171-.061-1.816-.256-2.236-.421-.569-.224-.96-.479-1.379-.899-.421-.419-.69-.824-.9-1.38-.165-.42-.359-1.065-.42-2.235-.045-1.26-.061-1.649-.061-4.844 0-3.196.016-3.586.061-4.861.061-1.17.255-1.814.42-2.234.21-.57.479-.96.9-1.381.419-.419.81-.689 1.379-.898.42-.166 1.051-.361 2.221-.421 1.275-.045 1.65-.06 4.859-.06zm0 3.678a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zM12 16a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm6.406-11.845a1.44 1.44 0 1 0 0 2.881 1.44 1.44 0 0 0 0-2.881z"/></svg></i></div>
                <div>
                    <div class="cc-label">Instagram</div>
                    <div class="cc-val">im.aryan.18</div>
                </div>
            </a>
            <a href="https://x.com/Aryan98380207" target="_blank" class="contact-card social-twitter">
                <div class="cc-icon"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M18.901 1.153h3.68l-8.04 9.19L24 22.846h-7.406l-5.8-7.584-6.638 7.584H.474l8.6-9.83L0 1.154h7.594l5.243 6.932ZM17.61 20.644h2.039L6.486 3.24H4.298Z"/></svg></i></div>
                <div>
                    <div class="cc-label">X (Twitter)</div>
                    <div class="cc-val">@Aryan98380207</div>
                </div>
            </a>
        </div>
    </div>

    <div class="contact-form-wrap reveal">
        <h3>Send a Message</h3>
        <div class="form-row">
            <div class="form-group">
                <label>First Name</label>
                <input type="text" id="fname" placeholder="John">
            </div>
            <div class="form-group">
                <label>Last Name</label>
                <input type="text" id="lname" placeholder="Doe">
            </div>
        </div>
        <div class="form-group">
            <label>Email</label>
            <input type="email" id="femail" placeholder="john@example.com">
        </div>
        <div class="form-group">
            <label>Subject</label>
            <input type="text" id="fsubject" placeholder="Project Discussion">
        </div>
        <div class="form-group">
            <label>Message</label>
            <textarea id="fmessage" placeholder="Tell me about your project..."></textarea>
        </div>
        <button class="btn-send" onclick="sendMessage()">
            <i class="fa fa-paper-plane"></i> &nbsp;Send Message
        </button>
    </div>
</section>

<!-- FOOTER -->
<footer>
    <a href="#home" class="logo">Aryan</a>
    <p>© 2025 Aryan Gupta. Crafted with ❤️ in Delhi, India.</p>
    <div class="footer-socials">
        <a href="https://www.linkedin.com/in/aryan4web3/" target="_blank" class="social-linkedin"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg></i></a>
        <a href="https://github.com/alphaplus-ai" target="_blank" class="social-github"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg></i></a>
        <a href="https://x.com/Aryan98380207" target="_blank" class="social-twitter"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M18.901 1.153h3.68l-8.04 9.19L24 22.846h-7.406l-5.8-7.584-6.638 7.584H.474l8.6-9.83L0 1.154h7.594l5.243 6.932ZM17.61 20.644h2.039L6.486 3.24H4.298Z"/></svg></i></a>
        <a href="https://www.instagram.com/im.aryan.18/" target="_blank" class="social-instagram"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M12 0C8.74 0 8.333.014 7.053.072 5.775.132 4.905.333 4.14.63c-.789.306-1.459.717-2.126 1.384S.935 3.35.63 4.14C.333 4.905.131 5.775.072 7.053.014 8.333 0 8.74 0 12s.014 3.667.072 4.947c.06 1.277.261 2.148.558 2.913.306.788.717 1.459 1.384 2.126.667.666 1.336 1.079 2.126 1.384.766.296 1.636.499 2.913.558C8.333 23.986 8.74 24 12 24s3.667-.014 4.947-.072c1.277-.06 2.148-.262 2.913-.558.788-.306 1.459-.718 2.126-1.384.666-.667 1.079-1.335 1.384-2.126.296-.765.499-1.636.558-2.913.06-1.28.072-1.687.072-4.947s-.014-3.667-.072-4.947c-.06-1.278-.262-2.149-.558-2.913-.306-.789-.718-1.459-1.384-2.126C21.319 1.347 20.651.935 19.86.63c-.765-.297-1.636-.499-2.913-.558C15.667.014 15.26 0 12 0zm0 2.16c3.203 0 3.585.016 4.85.071 1.17.055 1.805.249 2.227.415.562.217.96.477 1.382.896.419.42.679.819.896 1.381.164.422.36 1.057.413 2.227.057 1.266.07 1.646.07 4.85s-.015 3.585-.074 4.85c-.061 1.17-.256 1.805-.421 2.227-.224.562-.479.96-.899 1.382-.419.419-.824.679-1.38.896-.42.164-1.065.36-2.235.413-1.274.057-1.649.07-4.859.07-3.211 0-3.586-.015-4.859-.074-1.171-.061-1.816-.256-2.236-.421-.569-.224-.96-.479-1.379-.899-.421-.419-.69-.824-.9-1.38-.165-.42-.359-1.065-.42-2.235-.045-1.26-.061-1.649-.061-4.844 0-3.196.016-3.586.061-4.861.061-1.17.255-1.814.42-2.234.21-.57.479-.96.9-1.381.419-.419.81-.689 1.379-.898.42-.166 1.051-.361 2.221-.421 1.275-.045 1.65-.06 4.859-.06zm0 3.678a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zM12 16a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm6.406-11.845a1.44 1.44 0 1 0 0 2.881 1.44 1.44 0 0 0 0-2.881z"/></svg></i></a>
        <a href="mailto:aryangupta5818@gmail.com" target="_blank" class="social-email"><i><svg viewBox="0 0 24 24" width="1em" height="1em" fill="currentColor" style="display:inline-block;vertical-align:-0.125em;"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg></i></a>
    </div>
</footer>

<script>
    /* CURSOR */
    const cursor = document.getElementById('cursor');
    const ring = document.getElementById('cursor-ring');
    let mx = 0, my = 0, rx = 0, ry = 0;
    document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
    function animCursor() {
        cursor.style.left = mx - 6 + 'px';
        cursor.style.top = my - 6 + 'px';
        rx += (mx - rx - 18) * 0.15;
        ry += (my - ry - 18) * 0.15;
        ring.style.left = rx + 'px';
        ring.style.top = ry + 'px';
        requestAnimationFrame(animCursor);
    }
    animCursor();
    document.querySelectorAll('a, button, input, textarea').forEach(el => {
        el.addEventListener('mouseenter', () => { ring.style.transform = 'scale(1.6)'; ring.style.opacity = '0.3'; });
        el.addEventListener('mouseleave', () => { ring.style.transform = 'scale(1)'; ring.style.opacity = '0.6'; });
    });

    /* TYPEWRITER */
    const words = ['Web Developer', 'Full Stack Dev', 'Software Engineer', 'Content Writer', 'Problem Solver', 'Coder'];
    let wi = 0, ci = 0, del = false;
    const el = document.getElementById('typed');
    function type() {
        const word = words[wi];
        if (!del) {
            el.textContent = word.slice(0, ci + 1);
            ci++;
            if (ci === word.length) { del = true; setTimeout(type, 1800); return; }
        } else {
            el.textContent = word.slice(0, ci - 1);
            ci--;
            if (ci === 0) { del = false; wi = (wi + 1) % words.length; }
        }
        setTimeout(type, del ? 60 : 90);
    }
    type();

    /* SCROLL REVEAL */
    const reveals = document.querySelectorAll('.reveal');
    const io = new IntersectionObserver(entries => {
        entries.forEach((e, i) => {
            if (e.isIntersecting) {
                setTimeout(() => e.target.classList.add('visible'), i * 80);
                io.unobserve(e.target);
            }
        });
    }, { threshold: 0.12 });
    reveals.forEach(r => io.observe(r));

    /* ACTIVE NAV */
    const sections = document.querySelectorAll('section, .hero');
    const navLinks = document.querySelectorAll('header nav a');
    window.addEventListener('scroll', () => {
        let cur = '';
        sections.forEach(s => { if (window.scrollY >= s.offsetTop - 200) cur = s.id; });
        navLinks.forEach(a => {
            a.classList.remove('active');
            if (a.getAttribute('href') === '#' + cur) a.classList.add('active');
        });
        const h = document.getElementById('header');
        h.style.background = window.scrollY > 60 ? 'rgba(8,8,8,0.95)' : 'rgba(8,8,8,0.7)';
    });

    /* MOBILE NAV */
    function openMobileNav() {
        document.getElementById('mobileNav').classList.add('open');
        document.getElementById('overlay').classList.add('open');
    }
    function closeMobileNav() {
        document.getElementById('mobileNav').classList.remove('open');
        document.getElementById('overlay').classList.remove('open');
    }

    /* TOAST */
    function showToast(msg, type) {
        const t = document.getElementById('toast');
        t.textContent = msg;
        t.className = 'toast show ' + (type || '');
        setTimeout(() => { t.className = 'toast'; }, 3200);
    }

    /* CONTACT FORM → mailto */
    function sendMessage() {
        const fname = document.getElementById('fname').value.trim();
        const lname = document.getElementById('lname').value.trim();
        const email = document.getElementById('femail').value.trim();
        const subject = document.getElementById('fsubject').value.trim();
        const msg = document.getElementById('fmessage').value.trim();

        if (!fname || !email || !msg) {
            showToast('⚠️ Please fill in all required fields.');
            return;
        }
        const body = `Hi Aryan,%0A%0AMy name is ${fname} ${lname}.%0A%0A${msg}%0A%0AReply to: ${email}`;
        window.location.href = `mailto:aryangupta5818@gmail.com?subject=${encodeURIComponent(subject || 'Portfolio Enquiry')}&body=${body}`;
        showToast('✅ Opening your email client…', 'success');
    }
</script>
</body>
</html>
