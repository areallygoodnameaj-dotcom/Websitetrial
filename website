<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Hidden Horizons — Travel Planned By Humans, Not Algorithms</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400;1,500&family=Jost:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --cream: #F5F0E8;
    --warm-white: #FAF7F2;
    --deep-earth: #2C2416;
    --forest: #3A4A3A;
    --gold: #B5975A;
    --gold-light: #D4B483;
    --muted: #7A6E5F;
    --border: rgba(181,151,90,0.25);
    --serif: 'Cormorant Garamond', Georgia, serif;
    --sans: 'Jost', sans-serif;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body { font-family: var(--sans); background: var(--warm-white); color: var(--deep-earth); overflow-x: hidden; }

  /* ─── NAV ─── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 22px 48px;
    transition: all 0.4s ease;
  }
  nav.scrolled {
    background: rgba(250,247,242,0.97);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid var(--border);
    padding: 14px 48px;
  }
  .nav-logo {
    font-family: var(--serif); font-size: 1.5rem; font-weight: 500;
    letter-spacing: 0.04em; color: #fff; text-decoration: none; transition: color 0.4s;
  }
  nav.scrolled .nav-logo { color: var(--deep-earth); }
  .nav-links { display: flex; align-items: center; gap: 36px; list-style: none; }
  .nav-links a {
    font-family: var(--sans); font-size: 0.78rem; font-weight: 400;
    letter-spacing: 0.14em; text-transform: uppercase;
    color: rgba(255,255,255,0.9); text-decoration: none; transition: color 0.3s;
  }
  nav.scrolled .nav-links a { color: var(--muted); }
  .nav-links a:hover { color: var(--gold); }
  .nav-cta {
    font-family: var(--sans); font-size: 0.75rem; font-weight: 500;
    letter-spacing: 0.16em; text-transform: uppercase;
    color: var(--deep-earth) !important; background: var(--gold);
    padding: 10px 22px; text-decoration: none; transition: background 0.3s;
  }
  .nav-cta:hover { background: var(--gold-light); }

  /* ─── HERO SLIDESHOW ─── */
  .hero {
    position: relative; height: 100vh;
    min-height: 620px; max-height: 900px;
    overflow: hidden; display: flex; align-items: flex-end;
  }

  /* Individual slides */
  .hero-slides { position: absolute; inset: 0; }
  .hero-slide {
    position: absolute; inset: 0;
    background-size: cover;
    background-position: center;
    opacity: 0;
    transition: opacity 1.6s cubic-bezier(0.4,0,0.2,1);
    transform: scale(1.06);
    transition: opacity 1.6s cubic-bezier(0.4,0,0.2,1), transform 8s ease-out;
  }
  .hero-slide.active {
    opacity: 1;
    transform: scale(1.0);
  }
  /* Gradient overlay on each slide */
  .hero-slide::after {
    content: '';
    position: absolute; inset: 0;
    background: linear-gradient(
      to top,
      rgba(15,10,5,0.80) 0%,
      rgba(15,10,5,0.35) 45%,
      rgba(15,10,5,0.10) 100%
    );
  }

  /* Hero content */
  .hero-content {
    position: relative; z-index: 3;
    padding: 0 56px 80px;
    max-width: 760px;
  }
  .hero-eyebrow {
    font-family: var(--sans); font-size: 0.7rem; font-weight: 400;
    letter-spacing: 0.26em; text-transform: uppercase;
    color: var(--gold-light); margin-bottom: 16px;
    opacity: 0; transform: translateY(16px);
    animation: fadeUp 1s ease 0.4s forwards;
  }
  .hero h1 {
    font-family: var(--serif); font-size: clamp(3rem, 6vw, 5.4rem);
    font-weight: 300; line-height: 1.08; color: #fff; margin-bottom: 20px;
    opacity: 0; transform: translateY(20px);
    animation: fadeUp 1s ease 0.6s forwards;
  }
  .hero h1 em { font-style: italic; font-weight: 400; color: var(--gold-light); }
  .hero-sub {
    font-family: var(--sans); font-size: 0.88rem; font-weight: 300;
    letter-spacing: 0.05em; color: rgba(255,255,255,0.75);
    margin-bottom: 36px; line-height: 1.75; max-width: 480px;
    opacity: 0; transform: translateY(16px);
    animation: fadeUp 1s ease 0.85s forwards;
  }
  .hero-btns {
    display: flex; gap: 16px; flex-wrap: wrap;
    opacity: 0; transform: translateY(16px);
    animation: fadeUp 1s ease 1.05s forwards;
  }
  @keyframes fadeUp {
    to { opacity: 1; transform: translateY(0); }
  }

  /* Destination name that changes per slide */
  .hero-dest-name {
    position: absolute; z-index: 3;
    right: 56px; bottom: 120px;
    text-align: right;
  }
  .hero-dest-name-current {
    font-family: var(--serif); font-size: 4.5rem; font-weight: 300;
    font-style: italic; color: rgba(255,255,255,0.08);
    letter-spacing: 0.02em; line-height: 1;
    transition: opacity 0.8s ease;
    user-select: none;
  }

  /* Slide indicators bottom-right */
  .hero-indicators {
    position: absolute; z-index: 3;
    right: 56px; bottom: 52px;
    display: flex; align-items: center; gap: 10px;
  }
  .hero-ind {
    position: relative; height: 2px; width: 40px;
    background: rgba(255,255,255,0.2);
    cursor: pointer; overflow: hidden;
    transition: width 0.3s;
  }
  .hero-ind.active { width: 64px; }
  .hero-ind-fill {
    position: absolute; top: 0; left: 0; height: 100%;
    background: var(--gold-light); width: 0%;
  }
  .hero-ind.active .hero-ind-fill {
    animation: fillBar var(--slide-duration, 6s) linear forwards;
  }
  @keyframes fillBar { from { width: 0%; } to { width: 100%; } }

  /* Slide counter */
  .hero-counter {
    position: absolute; z-index: 3;
    left: 56px; bottom: 52px;
    font-family: var(--sans); font-size: 0.68rem;
    letter-spacing: 0.2em; color: rgba(255,255,255,0.45);
  }
  .hero-counter span { color: var(--gold-light); font-size: 0.8rem; }

  /* Destination tab labels on right */
  .hero-dest-tabs {
    position: absolute; z-index: 3;
    right: 56px; top: 50%;
    transform: translateY(-50%);
    display: flex; flex-direction: column; gap: 10px;
    opacity: 0; animation: fadeUp 1s ease 1.2s forwards;
  }
  .hero-dest-tab {
    font-family: var(--sans); font-size: 0.66rem;
    letter-spacing: 0.2em; text-transform: uppercase;
    color: rgba(255,255,255,0.4); cursor: pointer;
    padding: 4px 0; border-right: 2px solid transparent;
    transition: all 0.3s; text-align: right; padding-right: 12px;
  }
  .hero-dest-tab:hover { color: rgba(255,255,255,0.75); }
  .hero-dest-tab.active { color: var(--gold-light); border-right-color: var(--gold-light); }

  /* ─── BUTTONS ─── */
  .btn-primary {
    display: inline-block; font-family: var(--sans); font-size: 0.75rem;
    font-weight: 500; letter-spacing: 0.18em; text-transform: uppercase;
    color: var(--deep-earth); background: var(--gold);
    padding: 14px 32px; text-decoration: none; transition: background 0.3s;
  }
  .btn-primary:hover { background: var(--gold-light); }
  .btn-secondary {
    display: inline-block; font-family: var(--sans); font-size: 0.75rem;
    font-weight: 400; letter-spacing: 0.18em; text-transform: uppercase;
    color: rgba(255,255,255,0.85); border: 1px solid rgba(181,151,90,0.6);
    padding: 14px 32px; text-decoration: none; transition: all 0.3s;
  }
  .btn-secondary:hover { background: var(--gold); color: var(--deep-earth); border-color: var(--gold); }
  .btn-outline-dark {
    display: inline-block; font-family: var(--sans); font-size: 0.75rem;
    font-weight: 400; letter-spacing: 0.18em; text-transform: uppercase;
    color: var(--deep-earth); border: 1px solid var(--gold);
    padding: 14px 32px; text-decoration: none; transition: all 0.3s;
  }
  .btn-outline-dark:hover { background: var(--gold); }

  /* ─── SECTION SHARED ─── */
  section { padding: 96px 48px; }
  .section-eyebrow {
    font-family: var(--sans); font-size: 0.7rem; letter-spacing: 0.22em;
    text-transform: uppercase; color: var(--gold); margin-bottom: 18px;
  }
  .section-title {
    font-family: var(--serif); font-size: clamp(2rem, 3.5vw, 3rem);
    font-weight: 300; line-height: 1.2; color: var(--deep-earth); margin-bottom: 24px;
  }
  .section-title em { font-style: italic; color: var(--forest); }
  .section-body { font-family: var(--sans); font-size: 0.9rem; line-height: 1.82; color: var(--muted); max-width: 580px; }
  .divider { width: 48px; height: 1px; background: var(--gold); margin-bottom: 28px; }
  .see-all-link {
    font-family: var(--sans); font-size: 0.72rem; letter-spacing: 0.18em;
    text-transform: uppercase; color: var(--gold); text-decoration: none;
    border-bottom: 1px solid var(--gold); padding-bottom: 2px; transition: all 0.3s;
  }
  .see-all-link:hover { color: var(--muted); border-color: var(--muted); }

  /* ─── WHY SECTION ─── */
  .why-section {
    background: var(--cream);
    display: grid; grid-template-columns: 1fr 1fr; gap: 0; padding: 0;
  }
  .why-text {
    padding: 96px 64px 96px 48px;
    display: flex; flex-direction: column; justify-content: center;
  }
  .why-text .section-body { margin-bottom: 28px; }
  .why-images { display: grid; grid-template-rows: 1fr 1fr; height: 580px; }
  .why-img { overflow: hidden; position: relative; }
  .why-img img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.8s ease; }
  .why-img:hover img { transform: scale(1.04); }
  .why-img-caption {
    position: absolute; bottom: 16px; left: 16px;
    background: rgba(20,16,10,0.72); color: rgba(255,255,255,0.88);
    font-family: var(--sans); font-size: 0.66rem; letter-spacing: 0.18em;
    text-transform: uppercase; padding: 6px 12px;
  }

  /* ─── DESTINATIONS GRID ─── */
  .destinations-section { background: var(--warm-white); }
  .destinations-header { display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 52px; }
  .destinations-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 2px; }
  .dest-card { position: relative; overflow: hidden; aspect-ratio: 3/4; cursor: pointer; text-decoration: none; }
  .dest-card img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.7s ease; }
  .dest-card:hover img { transform: scale(1.06); }
  .dest-overlay {
    position: absolute; inset: 0;
    background: linear-gradient(to top, rgba(20,16,10,0.75) 0%, transparent 55%);
    transition: background 0.4s;
  }
  .dest-card:hover .dest-overlay { background: linear-gradient(to top, rgba(20,16,10,0.85) 0%, rgba(20,16,10,0.2) 55%); }
  .dest-info { position: absolute; bottom: 24px; left: 24px; right: 24px; }
  .dest-label { font-family: var(--sans); font-size: 0.65rem; letter-spacing: 0.2em; text-transform: uppercase; color: var(--gold-light); margin-bottom: 6px; }
  .dest-name { font-family: var(--serif); font-size: 1.4rem; font-weight: 400; color: #fff; line-height: 1.2; }
  .dest-tours { font-family: var(--sans); font-size: 0.7rem; color: rgba(255,255,255,0.6); margin-top: 4px; letter-spacing: 0.08em; }

  /* ─── TESTIMONIAL ─── */
  .testimonial-section {
    background: var(--forest); color: var(--cream); padding: 80px 48px;
    display: grid; grid-template-columns: 1fr auto; align-items: center; gap: 64px;
  }
  .testimonial-quote {
    font-family: var(--serif); font-size: clamp(1.4rem, 2.5vw, 2rem);
    font-weight: 300; font-style: italic; line-height: 1.55; color: var(--cream); max-width: 700px;
  }
  .testimonial-quote::before { content: '\201C'; }
  .testimonial-quote::after  { content: '\201D'; }
  .testimonial-meta { text-align: right; min-width: 200px; }
  .testimonial-name { font-family: var(--sans); font-size: 0.82rem; letter-spacing: 0.12em; font-weight: 500; color: var(--gold-light); margin-bottom: 4px; }
  .testimonial-role { font-family: var(--sans); font-size: 0.7rem; color: rgba(245,240,232,0.55); letter-spacing: 0.06em; }

  /* ─── PROCESS ─── */
  .process-section { background: var(--cream); }
  .process-header { margin-bottom: 64px; }
  .process-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 48px; }
  .step-number { font-family: var(--serif); font-size: 3rem; font-weight: 300; color: var(--gold); opacity: 0.5; line-height: 1; margin-bottom: 20px; }
  .step-title { font-family: var(--serif); font-size: 1.25rem; font-weight: 500; color: var(--deep-earth); margin-bottom: 12px; }
  .step-body { font-family: var(--sans); font-size: 0.86rem; line-height: 1.8; color: var(--muted); }
  .process-img-row { display: grid; grid-template-columns: 1fr 1fr; gap: 2px; margin-top: 64px; height: 420px; }
  .process-img { overflow: hidden; position: relative; }
  .process-img img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.7s ease; }
  .process-img:hover img { transform: scale(1.04); }
  .process-img-label {
    position: absolute; bottom: 16px; left: 16px;
    background: rgba(20,16,10,0.68); color: rgba(255,255,255,0.85);
    font-family: var(--sans); font-size: 0.66rem; letter-spacing: 0.18em;
    text-transform: uppercase; padding: 6px 12px;
  }

  /* ─── ITINERARIES ─── */
  .itineraries-section { background: var(--warm-white); }
  .itin-header { display: flex; justify-content: space-between; align-items: flex-end; margin-bottom: 52px; }
  .itin-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 2px; }
  .itin-card { position: relative; overflow: hidden; text-decoration: none; display: block; }
  .itin-img { aspect-ratio: 4/3; overflow: hidden; }
  .itin-img img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.7s ease; }
  .itin-card:hover .itin-img img { transform: scale(1.05); }
  .itin-body { background: var(--cream); padding: 24px 20px 20px; }
  .itin-tag { font-family: var(--sans); font-size: 0.62rem; letter-spacing: 0.2em; text-transform: uppercase; color: var(--gold); margin-bottom: 8px; }
  .itin-title { font-family: var(--serif); font-size: 1.15rem; font-weight: 400; color: var(--deep-earth); line-height: 1.3; margin-bottom: 14px; }
  .itin-meta { display: flex; gap: 20px; font-family: var(--sans); font-size: 0.72rem; color: var(--muted); letter-spacing: 0.06em; }
  .itin-meta span { display: flex; align-items: center; gap: 5px; }
  .itin-meta span::before { content: '—'; color: var(--gold); font-size: 0.6rem; }

  /* ─── WHY CHOOSE US ─── */
  .why-choose { background: var(--cream); display: grid; grid-template-columns: 1fr 1fr; gap: 0; padding: 0; }
  .why-choose-text { padding: 96px 64px 96px 48px; display: flex; flex-direction: column; justify-content: center; }
  .why-choose-images { display: grid; grid-template-columns: 1fr 1fr; grid-template-rows: 1fr 1fr; height: 580px; }
  .wc-img { overflow: hidden; position: relative; }
  .wc-img img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.7s ease; }
  .wc-img:hover img { transform: scale(1.05); }
  .wc-img-label {
    position: absolute; bottom: 12px; left: 12px;
    font-family: var(--sans); font-size: 0.62rem; letter-spacing: 0.18em;
    text-transform: uppercase; color: rgba(255,255,255,0.75);
    background: rgba(20,16,10,0.6); padding: 5px 10px;
  }
  .why-pillars { display: flex; flex-direction: column; gap: 24px; margin: 32px 0 40px; }
  .pillar { display: flex; align-items: flex-start; gap: 16px; }
  .pillar-dot { width: 6px; height: 6px; background: var(--gold); border-radius: 50%; margin-top: 6px; flex-shrink: 0; }
  .pillar-text { font-family: var(--sans); font-size: 0.85rem; line-height: 1.65; color: var(--muted); }
  .pillar-text strong { font-weight: 500; color: var(--deep-earth); display: block; font-size: 0.82rem; letter-spacing: 0.04em; }

  /* ─── APPROACH ─── */
  .approach-section { background: var(--deep-earth); display: grid; grid-template-columns: 1fr 1fr; gap: 0; padding: 0; min-height: 520px; }
  .approach-text { padding: 96px 64px 96px 48px; display: flex; flex-direction: column; justify-content: center; }
  .approach-text .section-eyebrow { color: var(--gold-light); }
  .approach-text .section-title { color: var(--cream); }
  .approach-text .section-title em { color: var(--gold-light); }
  .approach-text .section-body { color: rgba(245,240,232,0.65); margin-bottom: 20px; }
  .approach-text .divider { background: var(--gold-light); }
  .approach-btns { display: flex; gap: 16px; flex-wrap: wrap; margin-top: 16px; }
  .approach-right { position: relative; overflow: hidden; }
  .approach-right img { width: 100%; height: 100%; object-fit: cover; }
  .approach-badge {
    position: absolute; bottom: 48px; left: 48px;
    background: rgba(20,16,10,0.8); border: 1px solid rgba(181,151,90,0.3);
    padding: 20px 24px; max-width: 220px;
  }
  .approach-badge-title { font-family: var(--serif); font-size: 1rem; font-style: italic; color: var(--gold-light); line-height: 1.3; margin-bottom: 4px; }
  .approach-badge-sub { font-family: var(--sans); font-size: 0.66rem; letter-spacing: 0.16em; text-transform: uppercase; color: rgba(245,240,232,0.45); }

  /* ─── NEWSLETTER ─── */
  .newsletter-section { background: var(--cream); padding: 72px 48px; text-align: center; }
  .newsletter-section h3 { font-family: var(--serif); font-size: 1.8rem; font-weight: 300; color: var(--deep-earth); margin-bottom: 10px; }
  .newsletter-section p { font-family: var(--sans); font-size: 0.86rem; color: var(--muted); margin-bottom: 36px; }
  .newsletter-form { display: flex; max-width: 480px; margin: 0 auto; }
  .newsletter-form input { flex: 1; font-family: var(--sans); font-size: 0.82rem; padding: 14px 20px; border: 1px solid var(--border); background: var(--warm-white); color: var(--deep-earth); outline: none; }
  .newsletter-form input::placeholder { color: var(--muted); }
  .newsletter-form button { font-family: var(--sans); font-size: 0.72rem; letter-spacing: 0.16em; text-transform: uppercase; font-weight: 500; background: var(--gold); color: var(--deep-earth); border: none; padding: 14px 28px; cursor: pointer; transition: background 0.3s; }
  .newsletter-form button:hover { background: var(--gold-light); }

  /* ─── FOOTER ─── */
  footer { background: var(--deep-earth); color: var(--cream); padding: 72px 48px 32px; }
  .footer-top { display: grid; grid-template-columns: 2fr 1fr 1fr 1fr; gap: 48px; padding-bottom: 56px; border-bottom: 1px solid rgba(181,151,90,0.15); margin-bottom: 32px; }
  .footer-brand { font-family: var(--serif); font-size: 1.3rem; font-weight: 400; color: var(--cream); margin-bottom: 16px; }
  .footer-brand span { color: var(--gold); }
  .footer-tagline { font-family: var(--sans); font-size: 0.78rem; line-height: 1.75; color: rgba(245,240,232,0.45); margin-bottom: 24px; max-width: 260px; }
  .footer-contact a { display: block; font-family: var(--sans); font-size: 0.8rem; color: rgba(245,240,232,0.7); text-decoration: none; margin-bottom: 6px; transition: color 0.3s; }
  .footer-contact a:hover { color: var(--gold-light); }
  .footer-col h5 { font-family: var(--sans); font-size: 0.68rem; letter-spacing: 0.2em; text-transform: uppercase; color: var(--gold); margin-bottom: 20px; }
  .footer-col ul { list-style: none; }
  .footer-col ul li { margin-bottom: 10px; }
  .footer-col ul li a { font-family: var(--sans); font-size: 0.8rem; color: rgba(245,240,232,0.55); text-decoration: none; transition: color 0.3s; }
  .footer-col ul li a:hover { color: var(--gold-light); }
  .footer-bottom { display: flex; justify-content: space-between; align-items: center; }
  .footer-copy { font-family: var(--sans); font-size: 0.72rem; color: rgba(245,240,232,0.3); letter-spacing: 0.06em; }
  .footer-legal { display: flex; gap: 24px; list-style: none; }
  .footer-legal a { font-family: var(--sans); font-size: 0.72rem; color: rgba(245,240,232,0.3); text-decoration: none; transition: color 0.3s; }
  .footer-legal a:hover { color: var(--gold-light); }

  /* ─── WHATSAPP ─── */
  .wa-float {
    position: fixed; bottom: 28px; right: 28px; z-index: 99;
    width: 52px; height: 52px; background: #25D366; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    text-decoration: none; box-shadow: 0 4px 20px rgba(37,211,102,0.4);
    transition: transform 0.3s, box-shadow 0.3s;
  }
  .wa-float:hover { transform: scale(1.1); box-shadow: 0 6px 28px rgba(37,211,102,0.5); }
  .wa-float svg { width: 26px; height: 26px; fill: #fff; }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 900px) {
    nav { padding: 18px 24px; }
    nav.scrolled { padding: 12px 24px; }
    .nav-links { display: none; }
    section { padding: 64px 24px; }
    .hero-content { padding: 0 24px 100px; }
    .hero-dest-tabs { display: none; }
    .hero-indicators { right: 24px; }
    .hero-counter { left: 24px; }
    .why-section, .why-choose, .approach-section { grid-template-columns: 1fr; }
    .why-images, .why-choose-images { height: 300px; grid-template-columns: 1fr 1fr; }
    .destinations-grid { grid-template-columns: 1fr 1fr; }
    .itin-grid { grid-template-columns: 1fr; }
    .process-grid { grid-template-columns: 1fr; gap: 36px; }
    .footer-top { grid-template-columns: 1fr 1fr; }
    .testimonial-section { grid-template-columns: 1fr; gap: 32px; }
    .testimonial-meta { text-align: left; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav id="mainNav">
  <a href="#" class="nav-logo">Hidden Horizons</a>
  <ul class="nav-links">
    <li><a href="#">Destinations</a></li>
    <li><a href="#">Packages</a></li>
    <li><a href="#">Our Process</a></li>
    <li><a href="#">About Us</a></li>
    <li><a href="#enquiry" class="nav-cta">Plan Your Journey</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero" id="hero">

  <!-- Slides -->
  <div class="hero-slides" id="heroSlides">
    <div class="hero-slide active" style="background-image: url('https://images.unsplash.com/photo-1602216056096-3b40cc0c9944?w=1920&q=90');"></div>
    <div class="hero-slide" style="background-image: url('https://images.unsplash.com/photo-1586348943529-beaae6c28db9?w=1920&q=90');"></div>
    <div class="hero-slide" style="background-image: url('https://images.unsplash.com/photo-1626621341517-bbf3d9990a23?w=1920&q=90');"></div>
    <div class="hero-slide" style="background-image: url('https://images.unsplash.com/photo-1564507592333-c60657eea523?w=1920&q=90');"></div>
    <div class="hero-slide" style="background-image: url('https://images.unsplash.com/photo-1477587458883-47145ed6979e?w=1920&q=90');"></div>
    <div class="hero-slide" style="background-image: url('https://images.unsplash.com/photo-1510797215324-95aa89f43c33?w=1920&q=90');"></div>
  </div>

  <!-- Hero Text -->
  <div class="hero-content">
    <p class="hero-eyebrow">Welcome to Hidden Horizons</p>
    <h1>Journeys Crafted by <em>Real Humans</em></h1>
    <p class="hero-sub">Travel planned by people, not algorithms. Every itinerary is handcrafted by experts who've actually been there.</p>
    <div class="hero-btns">
      <a href="#enquiry" class="btn-primary">Plan Your Journey</a>
      <a href="#destinations" class="btn-secondary">Explore Destinations</a>
    </div>
  </div>

  <!-- Big ghost destination name -->
  <div class="hero-dest-name">
    <div class="hero-dest-name-current" id="heroDestNameBig">Kerala</div>
  </div>

  <!-- Side destination tabs -->
  <div class="hero-dest-tabs" id="heroDestTabs">
    <div class="hero-dest-tab active" data-index="0">Kerala</div>
    <div class="hero-dest-tab" data-index="1">Kashmir</div>
    <div class="hero-dest-tab" data-index="2">Himachal</div>
    <div class="hero-dest-tab" data-index="3">Golden Triangle</div>
    <div class="hero-dest-tab" data-index="4">Rajasthan</div>
    <div class="hero-dest-tab" data-index="5">Ladakh</div>
  </div>

  <!-- Progress indicators -->
  <div class="hero-indicators" id="heroIndicators">
    <div class="hero-ind active"><div class="hero-ind-fill"></div></div>
    <div class="hero-ind"><div class="hero-ind-fill"></div></div>
    <div class="hero-ind"><div class="hero-ind-fill"></div></div>
    <div class="hero-ind"><div class="hero-ind-fill"></div></div>
    <div class="hero-ind"><div class="hero-ind-fill"></div></div>
    <div class="hero-ind"><div class="hero-ind-fill"></div></div>
  </div>

  <!-- Slide counter -->
  <div class="hero-counter" id="heroCounter"><span>01</span> / 06</div>

</section>

<!-- WHY HIDDEN HORIZONS -->
<div class="why-section">
  <div class="why-text">
    <p class="section-eyebrow">Why Choose Hidden Horizons</p>
    <div class="divider"></div>
    <h2 class="section-title">Handcrafted Journeys Through <em>India's Soul</em></h2>
    <p class="section-body">We specialise in giving curious travellers genuine access to India's most extraordinary destinations — from Kerala's secret backwaters to the high passes of Ladakh. No AI. No middlemen. Just real people, real places, and meaningful travel.</p>
    <p class="section-body" style="margin-top:16px;">Every journey is designed around you, personally, by someone who has walked those paths.</p>
    <br>
    <a href="#enquiry" class="btn-outline-dark">Contact Us</a>
  </div>
  <div class="why-images">
    <div class="why-img">
      <img src="https://images.unsplash.com/photo-1602216056096-3b40cc0c9944?w=900&q=88" alt="Kerala backwaters">
      <div class="why-img-caption">Private Journeys · Tailor Made</div>
    </div>
    <div class="why-img">
      <img src="https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=900&q=88" alt="Himalayan landscape">
      <div class="why-img-caption">Experts Who've Actually Been There</div>
    </div>
  </div>
</div>

<!-- DESTINATIONS -->
<section class="destinations-section" id="destinations">
  <div class="destinations-header">
    <div>
      <p class="section-eyebrow">Where We Operate</p>
      <h2 class="section-title" style="margin-bottom:0">Discover <em>India's Finest</em></h2>
    </div>
    <a href="#" class="see-all-link">See All Destinations</a>
  </div>
  <div class="destinations-grid">
    <a href="#" class="dest-card">
      <img src="https://images.unsplash.com/photo-1602216056096-3b40cc0c9944?w=700&q=85" alt="Kerala">
      <div class="dest-overlay"></div>
      <div class="dest-info">
        <div class="dest-label">Destination</div>
        <div class="dest-name">Kerala</div>
        <div class="dest-tours">13+ Journeys</div>
      </div>
    </a>
    <a href="#" class="dest-card">
      <img src="https://images.unsplash.com/photo-1586348943529-beaae6c28db9?w=700&q=85" alt="Kashmir">
      <div class="dest-overlay"></div>
      <div class="dest-info">
        <div class="dest-label">Destination</div>
        <div class="dest-name">Kashmir</div>
        <div class="dest-tours">8+ Journeys</div>
      </div>
    </a>
    <a href="#" class="dest-card">
      <img src="https://images.unsplash.com/photo-1626621341517-bbf3d9990a23?w=700&q=85" alt="Himachal Pradesh">
      <div class="dest-overlay"></div>
      <div class="dest-info">
        <div class="dest-label">Destination</div>
        <div class="dest-name">Himachal</div>
        <div class="dest-tours">6+ Journeys</div>
      </div>
    </a>
    <a href="#" class="dest-card">
      <img src="https://images.unsplash.com/photo-1510797215324-95aa89f43c33?w=700&q=85" alt="Ladakh">
      <div class="dest-overlay"></div>
      <div class="dest-info">
        <div class="dest-label">Destination</div>
        <div class="dest-name">Ladakh</div>
        <div class="dest-tours">5+ Journeys</div>
      </div>
    </a>
  </div>
</section>

<!-- TESTIMONIAL -->
<div class="testimonial-section">
  <blockquote class="testimonial-quote">
    Hidden Horizons understood exactly what we were looking for — they found corners of Kerala we never would have discovered on our own. Every detail felt personal, warm, and completely unhurried.
  </blockquote>
  <div class="testimonial-meta">
    <div class="testimonial-name">Priya & Rohan Mehta</div>
    <div class="testimonial-role">Honeymooners from Mumbai</div>
  </div>
</div>

<!-- HOW IT WORKS -->
<section class="process-section">
  <div class="process-header">
    <p class="section-eyebrow">How it Works</p>
    <div class="divider"></div>
    <h2 class="section-title">Meaningful Travel Begins with a <em>Real Conversation</em></h2>
    <p class="section-body">We believe the best journeys start with a genuine dialogue. We take the time to understand your interests, pace, and vision — then our destination experts craft every detail around you. Not automated. Thoughtfully curated.</p>
  </div>
  <div class="process-grid">
    <div class="process-step">
      <div class="step-number">01</div>
      <h3 class="step-title">Initial Consultation</h3>
      <p class="step-body">Our approach begins with a direct conversation — by phone or in person. We explore your travel goals, interests, dates, and what truly matters to you, so we can understand your vision on a deeper level.</p>
    </div>
    <div class="process-step">
      <div class="step-number">02</div>
      <h3 class="step-title">Your Journey, Designed</h3>
      <p class="step-body">Our experts — who've personally visited every destination — craft a handpicked itinerary around you. Every accommodation, experience, and route is chosen with care. No templates. No AI. Just expert human judgment.</p>
    </div>
    <div class="process-step">
      <div class="step-number">03</div>
      <h3 class="step-title">While You Travel</h3>
      <p class="step-body">Once your journey begins, we remain available at all times. Our trusted local contacts welcome you at every step. Should anything require attention, a real person — not a chatbot — is there to help.</p>
    </div>
  </div>
  <div class="process-img-row">
    <div class="process-img">
      <img src="https://images.unsplash.com/photo-1477587458883-47145ed6979e?w=900&q=85" alt="Rajasthan">
      <div class="process-img-label">Bespoke · To You · By Design</div>
    </div>
    <div class="process-img">
      <img src="https://images.unsplash.com/photo-1564507592333-c60657eea523?w=900&q=85" alt="Taj Mahal">
      <div class="process-img-label">Human-Led · From Start to Finish</div>
    </div>
  </div>
</section>

<!-- ITINERARIES -->
<section class="itineraries-section">
  <div class="itin-header">
    <div>
      <p class="section-eyebrow">Looking for Inspiration</p>
      <h2 class="section-title" style="margin-bottom:0">Journeys We've <em>Crafted</em></h2>
    </div>
    <a href="#" class="see-all-link">See All Packages</a>
  </div>
  <div class="itin-grid">
    <a href="#" class="itin-card">
      <div class="itin-img">
        <img src="https://images.unsplash.com/photo-1602216056096-3b40cc0c9944?w=800&q=85" alt="Kerala backwaters">
      </div>
      <div class="itin-body">
        <div class="itin-tag">Kerala · Private</div>
        <div class="itin-title">Kochi – Munnar – Alleppey Houseboat Experience</div>
        <div class="itin-meta">
          <span>From ₹42,000</span>
          <span>2 Guests</span>
          <span>7 Days</span>
        </div>
      </div>
    </a>
    <a href="#" class="itin-card">
      <div class="itin-img">
        <img src="https://images.unsplash.com/photo-1586348943529-beaae6c28db9?w=800&q=85" alt="Kashmir">
      </div>
      <div class="itin-body">
        <div class="itin-tag">Kashmir · Private</div>
        <div class="itin-title">Paradise of Kashmir: Dal Lake & Gulmarg in Winter</div>
        <div class="itin-meta">
          <span>From ₹55,000</span>
          <span>2 Guests</span>
          <span>6 Days</span>
        </div>
      </div>
    </a>
    <a href="#" class="itin-card">
      <div class="itin-img">
        <img src="https://images.unsplash.com/photo-1564507592333-c60657eea523?w=800&q=85" alt="Taj Mahal">
      </div>
      <div class="itin-body">
        <div class="itin-tag">Golden Triangle · Private</div>
        <div class="itin-title">Delhi – Agra – Jaipur: India's Royal Heart</div>
        <div class="itin-meta">
          <span>From ₹38,000</span>
          <span>2 Guests</span>
          <span>6 Days</span>
        </div>
      </div>
    </a>
  </div>
</section>

<!-- WHY CHOOSE US -->
<div class="why-choose">
  <div class="why-choose-images">
    <div class="wc-img">
      <img src="https://images.unsplash.com/photo-1602216056096-3b40cc0c9944?w=700&q=85" alt="Kerala">
      <div class="wc-img-label">Kerala</div>
    </div>
    <div class="wc-img">
      <img src="https://images.unsplash.com/photo-1510797215324-95aa89f43c33?w=700&q=85" alt="Ladakh">
      <div class="wc-img-label">Ladakh</div>
    </div>
    <div class="wc-img">
      <img src="https://images.unsplash.com/photo-1477587458883-47145ed6979e?w=700&q=85" alt="Rajasthan">
      <div class="wc-img-label">Rajasthan</div>
    </div>
    <div class="wc-img">
      <img src="https://images.unsplash.com/photo-1626621341517-bbf3d9990a23?w=700&q=85" alt="Himachal">
      <div class="wc-img-label">Himachal Pradesh</div>
    </div>
  </div>
  <div class="why-choose-text">
    <p class="section-eyebrow">Why Choose Us</p>
    <div class="divider"></div>
    <h2 class="section-title">Not Automated. <em>Thoughtfully Curated.</em></h2>
    <p class="section-body">Our independence means we remain fully dedicated to you — free from algorithms, corporate templates, and auto-generated itineraries. We've spent years building deep relationships with local experts across India, so every journey we design carries real knowledge and genuine care.</p>
    <div class="why-pillars">
      <div class="pillar">
        <div class="pillar-dot"></div>
        <div class="pillar-text"><strong>Real human travel experts</strong>Every itinerary crafted by someone who's personally experienced the destination.</div>
      </div>
      <div class="pillar">
        <div class="pillar-dot"></div>
        <div class="pillar-text"><strong>No AI. No middlemen.</strong>You speak directly with the people designing your trip — always.</div>
      </div>
      <div class="pillar">
        <div class="pillar-dot"></div>
        <div class="pillar-text"><strong>Slow, intentional, meaningful travel</strong>We build journeys around depth, not just destinations.</div>
      </div>
    </div>
    <a href="#" class="btn-outline-dark">About Us</a>
  </div>
</div>

<!-- OUR APPROACH -->
<div class="approach-section">
  <div class="approach-text">
    <p class="section-eyebrow">Our Approach</p>
    <div class="divider"></div>
    <h2 class="section-title">Human, <em>Personal,</em> Seamless</h2>
    <p class="section-body">At Hidden Horizons, we believe travel should feel personal again. We favour genuine conversations over digital forms, ensuring your vision is truly understood from the very first call.</p>
    <p class="section-body">Beyond bookings — human-first travel planning. Reach out to begin shaping your journey with us.</p>
    <div class="approach-btns">
      <a href="tel:9871625009" class="btn-primary">Call Us</a>
      <a href="#enquiry" class="btn-secondary" style="color:rgba(255,255,255,0.85);">Contact Us</a>
    </div>
  </div>
  <div class="approach-right">
    <img src="https://images.unsplash.com/photo-1571003123894-1f0594d2b5d9?w=1000&q=88" alt="Travel planning">
    <div class="approach-badge">
      <div class="approach-badge-title">Bespoke<br>To You, By Design</div>
      <div class="approach-badge-sub">Human-first since day one</div>
    </div>
  </div>
</div>

<!-- NEWSLETTER -->
<section class="newsletter-section" id="enquiry">
  <p class="section-eyebrow" style="text-align:center;">Stay Inspired</p>
  <h3>Receive Inspiration in Your Inbox</h3>
  <p>Handpicked stories, seasonal itineraries, and quiet corners of India — curated by our experts.</p>
  <div class="newsletter-form">
    <input type="email" placeholder="Your email address">
    <button type="submit">Subscribe</button>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-top">
    <div>
      <div class="footer-brand">Hidden <span>Horizons</span></div>
      <p class="footer-tagline">Travel planned by real humans, not algorithms. Handcrafted journeys designed around you, with care.</p>
      <div class="footer-contact">
        <a href="tel:9871625009">+91 98716 25009</a>
        <a href="tel:9650224833">+91 96502 24833</a>
        <a href="mailto:contact@hiddenhorizons.in">contact@hiddenhorizons.in</a>
        <a href="#">Delhi · Alleppey</a>
      </div>
    </div>
    <div class="footer-col">
      <h5>Destinations</h5>
      <ul>
        <li><a href="#">Kerala</a></li>
        <li><a href="#">Kashmir</a></li>
        <li><a href="#">Himachal</a></li>
        <li><a href="#">Golden Triangle</a></li>
        <li><a href="#">Rajasthan</a></li>
        <li><a href="#">Ladakh</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h5>Packages</h5>
      <ul>
        <li><a href="#">Family Tours</a></li>
        <li><a href="#">Honeymoon</a></li>
        <li><a href="#">North India</a></li>
        <li><a href="#">South India</a></li>
        <li><a href="#">All Packages</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h5>Company</h5>
      <ul>
        <li><a href="#">About Us</a></li>
        <li><a href="#">Our Process</a></li>
        <li><a href="#">Blog</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <span class="footer-copy">© 2026 Hidden Horizons. All rights reserved.</span>
    <ul class="footer-legal">
      <li><a href="#">Privacy Policy</a></li>
      <li><a href="#">Terms & Conditions</a></li>
      <li><a href="#">Cancellation Policy</a></li>
    </ul>
  </div>
</footer>

<a href="https://wa.me/919650224833?text=Hello+Hidden+Horizons%2C+I+have+an+enquiry." class="wa-float" target="_blank" rel="noopener">
  <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
    <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413Z"/>
  </svg>
</a>

<script>
  // ─── NAV SCROLL ───
  const nav = document.getElementById('mainNav');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 60);
  });

  // ─── HERO SLIDESHOW ───
  const SLIDE_DURATION = 6000; // ms per slide
  const destinations = ['Kerala', 'Kashmir', 'Himachal', 'Golden Triangle', 'Rajasthan', 'Ladakh'];
  const slides = document.querySelectorAll('.hero-slide');
  const indicators = document.querySelectorAll('.hero-ind');
  const tabs = document.querySelectorAll('.hero-dest-tab');
  const counter = document.getElementById('heroCounter');
  const destNameBig = document.getElementById('heroDestNameBig');
  let current = 0;
  let timer = null;

  function pad(n) { return n < 10 ? '0' + n : '' + n; }

  function goTo(index) {
    // Deactivate current
    slides[current].classList.remove('active');
    indicators[current].classList.remove('active');
    tabs[current].classList.remove('active');

    current = (index + slides.length) % slides.length;

    // Activate new
    slides[current].classList.add('active');
    indicators[current].classList.add('active');
    tabs[current].classList.add('active');

    // Update counter
    counter.innerHTML = `<span>${pad(current + 1)}</span> / ${pad(slides.length)}`;

    // Update big ghost name
    destNameBig.style.opacity = '0';
    setTimeout(() => {
      destNameBig.textContent = destinations[current];
      destNameBig.style.opacity = '1';
    }, 300);

    // Reset fill animations by cloning indicator fills
    indicators.forEach((ind, i) => {
      const fill = ind.querySelector('.hero-ind-fill');
      const newFill = fill.cloneNode(true);
      fill.replaceWith(newFill);
    });

    // Set CSS variable for fill animation duration
    const activeFill = indicators[current].querySelector('.hero-ind-fill');
    indicators[current].style.setProperty('--slide-duration', (SLIDE_DURATION / 1000) + 's');
  }

  function startAuto() {
    clearInterval(timer);
    timer = setInterval(() => {
      goTo(current + 1);
    }, SLIDE_DURATION);
  }

  // Tab click
  tabs.forEach(tab => {
    tab.addEventListener('click', () => {
      const idx = parseInt(tab.dataset.index);
      clearInterval(timer);
      goTo(idx);
      startAuto();
    });
  });

  // Indicator click
  indicators.forEach((ind, i) => {
    ind.addEventListener('click', () => {
      clearInterval(timer);
      goTo(i);
      startAuto();
    });
  });

  // Init
  destNameBig.style.transition = 'opacity 0.6s ease';
  goTo(0);
  startAuto();
</script>
</body>
</html>
