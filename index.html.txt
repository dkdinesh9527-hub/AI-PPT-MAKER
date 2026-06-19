<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PresentAI — Create Stunning Presentations in Seconds</title>
<meta name="description" content="Turn ideas, documents, PDFs, websites, and notes into beautifully designed presentations instantly. No design skills required.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --bg: #050508;
    --bg2: #0a0a12;
    --bg3: #0f0f1a;
    --surface: rgba(255,255,255,0.04);
    --surface2: rgba(255,255,255,0.07);
    --border: rgba(255,255,255,0.08);
    --border2: rgba(255,255,255,0.14);
    --text: #f0f0f8;
    --text2: #9090a8;
    --text3: #5a5a70;
    --accent: #6c5ce7;
    --accent2: #a29bfe;
    --accent3: #fd79a8;
    --green: #00cec9;
    --grad: linear-gradient(135deg, #6c5ce7 0%, #a29bfe 50%, #fd79a8 100%);
  }
  html { scroll-behavior: smooth; }
  body {
    font-family: 'Inter', sans-serif;
    background: var(--bg);
    color: var(--text);
    overflow-x: hidden;
    line-height: 1.6;
  }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 48px; height: 64px;
    background: rgba(5,5,8,0.85);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
  }
  .nav-logo {
    display: flex; align-items: center; gap: 10px;
    font-size: 18px; font-weight: 700; letter-spacing: -0.5px;
    text-decoration: none; color: var(--text);
  }
  .logo-icon {
    width: 30px; height: 30px; border-radius: 8px;
    background: var(--grad);
    display: flex; align-items: center; justify-content: center; font-size: 15px;
  }
  .nav-links { display: flex; gap: 32px; list-style: none; }
  .nav-links a {
    color: var(--text2); text-decoration: none;
    font-size: 14px; font-weight: 500; transition: color .2s;
  }
  .nav-links a:hover { color: var(--text); }
  .nav-cta { display: flex; gap: 12px; align-items: center; }
  .btn-ghost {
    background: none; border: 1px solid var(--border2); color: var(--text2);
    padding: 8px 20px; border-radius: 8px; font-size: 14px; font-weight: 500;
    cursor: pointer; transition: all .2s; font-family: inherit;
  }
  .btn-ghost:hover { border-color: var(--accent2); color: var(--text); }
  .btn-primary {
    background: var(--grad); border: none; color: #fff;
    padding: 9px 22px; border-radius: 8px; font-size: 14px; font-weight: 600;
    cursor: pointer; transition: opacity .2s; font-family: inherit;
  }
  .btn-primary:hover { opacity: 0.88; }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    padding: 120px 48px 80px; text-align: center; position: relative; overflow: hidden;
  }
  .hero-glow {
    position: absolute; top: 10%; left: 50%; transform: translateX(-50%);
    width: 800px; height: 500px; border-radius: 50%;
    background: radial-gradient(ellipse, rgba(108,92,231,0.18) 0%, transparent 70%);
    pointer-events: none;
  }
  .hero-glow2 {
    position: absolute; top: 30%; left: 20%;
    width: 400px; height: 300px;
    background: radial-gradient(ellipse, rgba(253,121,168,0.1) 0%, transparent 70%);
    pointer-events: none;
  }
  .badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(108,92,231,0.15); border: 1px solid rgba(108,92,231,0.35);
    padding: 6px 16px; border-radius: 100px; font-size: 13px; font-weight: 500;
    color: var(--accent2); margin-bottom: 28px;
  }
  .badge-dot {
    width: 6px; height: 6px; border-radius: 50%;
    background: var(--accent2); animation: pulse 2s infinite;
  }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:.4} }
  h1 {
    font-size: clamp(40px, 5vw, 72px); font-weight: 800;
    letter-spacing: -2.5px; line-height: 1.08;
    max-width: 820px; margin-bottom: 24px;
    background: linear-gradient(135deg, #ffffff 0%, #c8c8e8 60%, #a29bfe 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
  }
  .subhead {
    font-size: 18px; color: var(--text2); max-width: 560px;
    line-height: 1.7; margin-bottom: 40px;
  }
  .hero-btns {
    display: flex; gap: 14px; justify-content: center;
    flex-wrap: wrap; margin-bottom: 60px;
  }
  .btn-hero {
    padding: 14px 32px; border-radius: 10px;
    font-size: 15px; font-weight: 600; cursor: pointer;
    border: none; font-family: inherit;
  }
  .btn-hero-primary {
    background: var(--grad); color: #fff;
    box-shadow: 0 0 40px rgba(108,92,231,0.4); transition: all .2s;
  }
  .btn-hero-primary:hover { transform: translateY(-1px); box-shadow: 0 0 60px rgba(108,92,231,0.55); }
  .btn-hero-secondary {
    background: rgba(255,255,255,0.06);
    border: 1px solid rgba(255,255,255,0.12) !important;
    color: var(--text);
    display: flex; align-items: center; gap: 10px; transition: all .2s;
  }
  .btn-hero-secondary:hover { background: rgba(255,255,255,0.1); }
  .play-icon {
    width: 28px; height: 28px; border-radius: 50%;
    background: rgba(255,255,255,0.15);
    display: flex; align-items: center; justify-content: center;
  }
  .play-icon::after {
    content: '';
    border-left: 8px solid white;
    border-top: 5px solid transparent;
    border-bottom: 5px solid transparent;
    margin-left: 2px;
  }

  /* ── HERO DASHBOARD ── */
  .hero-dashboard {
    width: 100%; max-width: 900px;
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--border2); border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 40px 120px rgba(0,0,0,0.6), 0 0 0 1px rgba(255,255,255,0.05);
  }
  .dash-topbar {
    background: rgba(255,255,255,0.04); border-bottom: 1px solid var(--border);
    padding: 14px 20px; display: flex; align-items: center; gap: 12px;
  }
  .dot-row { display: flex; gap: 7px; }
  .dot { width: 11px; height: 11px; border-radius: 50%; }
  .dot-r { background: #ff5f57; }
  .dot-y { background: #ffbd2e; }
  .dot-g { background: #28c840; }
  .dash-title { font-size: 13px; color: var(--text3); margin-left: 8px; }
  .dash-body { display: grid; grid-template-columns: 260px 1fr; min-height: 380px; }
  .dash-sidebar { border-right: 1px solid var(--border); padding: 20px 16px; }
  .dash-sidebar-title {
    font-size: 11px; text-transform: uppercase; letter-spacing: 1px;
    color: var(--text3); margin-bottom: 14px; font-weight: 600;
  }
  .ai-prompt-box {
    background: rgba(108,92,231,0.1); border: 1px solid rgba(108,92,231,0.3);
    border-radius: 10px; padding: 14px; margin-bottom: 14px;
  }
  .ai-prompt-label { font-size: 11px; color: var(--accent2); font-weight: 600; margin-bottom: 8px; }
  .ai-prompt-text { font-size: 13px; color: var(--text2); line-height: 1.5; }
  .ai-step { display: flex; align-items: center; gap: 10px; padding: 8px 10px; border-radius: 8px; margin-bottom: 6px; }
  .ai-step-active { background: rgba(108,92,231,0.12); }
  .step-icon {
    width: 22px; height: 22px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 11px; font-weight: 700; flex-shrink: 0;
  }
  .step-done-icon { background: rgba(0,206,201,0.2); color: var(--green); }
  .step-active-icon { background: var(--accent); color: white; animation: pulse 1.5s infinite; }
  .step-pending-icon { background: var(--surface2); color: var(--text3); }
  .step-label { font-size: 13px; color: var(--text2); }
  .step-label-active { color: var(--text); font-weight: 500; }
  .dash-main { padding: 24px; }
  .dash-main-header {
    display: flex; align-items: center; justify-content: space-between; margin-bottom: 20px;
  }
  .dash-main-title { font-size: 15px; font-weight: 600; }
  .gen-badge {
    background: rgba(0,206,201,0.1); border: 1px solid rgba(0,206,201,0.25);
    color: var(--green); font-size: 12px; padding: 3px 10px; border-radius: 20px;
  }
  .slides-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; margin-bottom: 18px; }
  .slide-thumb {
    aspect-ratio: 16/9; border-radius: 8px; border: 1.5px solid var(--border);
    padding: 10px; position: relative; overflow: hidden;
    cursor: pointer; transition: border-color .2s;
  }
  .slide-thumb:hover { border-color: var(--accent2); }
  .slide-thumb.active { border-color: var(--accent); box-shadow: 0 0 0 2px rgba(108,92,231,0.3); }
  .slide-bg-1 { background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%); }
  .slide-bg-2 { background: linear-gradient(135deg, #0f3460 0%, #533483 100%); }
  .slide-bg-3 { background: linear-gradient(135deg, #12002b 0%, #1a0033 100%); }
  .slide-bg-4 { background: linear-gradient(135deg, #1b1b2f 0%, #162447 100%); }
  .slide-bg-5 { background: linear-gradient(135deg, #2d132c 0%, #1a0033 100%); }
  .slide-bg-6 { background: linear-gradient(135deg, #101522 0%, #1f4068 100%); }
  .slide-line { height: 3px; border-radius: 2px; margin-bottom: 5px; opacity: 0.8; }
  .slide-line-accent { background: var(--grad); }
  .slide-line-sm { background: rgba(255,255,255,0.2); }
  .w30{width:30%} .w40{width:40%} .w50{width:50%} .w60{width:60%} .w70{width:70%}
  .progress-row { display: flex; align-items: center; gap: 10px; }
  .progress-bar-wrap { flex: 1; height: 4px; background: var(--surface2); border-radius: 2px; overflow: hidden; }
  .progress-bar-fill {
    height: 100%; border-radius: 2px; background: var(--grad);
    width: 42%; transition: width 1s ease;
  }
  .progress-label { font-size: 12px; color: var(--text3); white-space: nowrap; }

  /* ── TRUST ── */
  .trust-section {
    padding: 60px 48px; text-align: center;
    border-top: 1px solid var(--border);
  }
  .trust-label {
    font-size: 13px; color: var(--text3);
    text-transform: uppercase; letter-spacing: 1.2px; margin-bottom: 32px; font-weight: 600;
  }
  .logo-strip {
    display: flex; justify-content: center; align-items: center;
    gap: 48px; flex-wrap: wrap;
  }
  .logo-item {
    font-size: 18px; font-weight: 700; color: rgba(255,255,255,0.18);
    letter-spacing: -0.5px; transition: color .2s; cursor: default;
  }
  .logo-item:hover { color: rgba(255,255,255,0.45); }

  /* ── SHARED SECTION STYLES ── */
  .section-inner { max-width: 1200px; margin: 0 auto; padding: 100px 48px; }
  .section-tag {
    display: inline-block; font-size: 12px; text-transform: uppercase;
    letter-spacing: 1.5px; font-weight: 700; color: var(--accent2); margin-bottom: 16px;
  }
  .section-h2 {
    font-size: clamp(28px, 3.5vw, 48px); font-weight: 700;
    letter-spacing: -1.5px; margin-bottom: 16px; line-height: 1.1;
  }
  .section-sub { font-size: 17px; color: var(--text2); max-width: 520px; line-height: 1.7; }

  /* ── STATS ── */
  .stats-row {
    display: grid; grid-template-columns: repeat(4, 1fr);
    gap: 1px; background: var(--border);
    border: 1px solid var(--border); border-radius: 16px; overflow: hidden; margin-top: 60px;
  }
  .stat-card { background: var(--bg); padding: 36px; text-align: center; }
  .stat-num {
    font-size: 48px; font-weight: 800; letter-spacing: -2px;
    background: var(--grad); -webkit-background-clip: text;
    -webkit-text-fill-color: transparent; background-clip: text;
  }
  .stat-label { font-size: 14px; color: var(--text2); margin-top: 8px; }

  /* ── FEATURES ── */
  .features-grid {
    display: grid; grid-template-columns: repeat(3, 1fr);
    gap: 1px; background: var(--border);
    border: 1px solid var(--border); border-radius: 16px; overflow: hidden; margin-top: 60px;
  }
  .feature-card { background: var(--bg); padding: 36px 28px; transition: background .25s; }
  .feature-card:hover { background: var(--bg3); }
  .feat-icon {
    width: 44px; height: 44px; border-radius: 12px; margin-bottom: 18px;
    display: flex; align-items: center; justify-content: center; font-size: 20px;
  }
  .fi-purple { background: rgba(108,92,231,0.15); }
  .fi-pink   { background: rgba(253,121,168,0.12); }
  .fi-teal   { background: rgba(0,206,201,0.12); }
  .fi-blue   { background: rgba(116,185,255,0.12); }
  .fi-amber  { background: rgba(253,203,110,0.12); }
  .fi-green  { background: rgba(0,184,148,0.12); }
  .feature-card h3 { font-size: 16px; font-weight: 600; margin-bottom: 10px; }
  .feature-card p  { font-size: 14px; color: var(--text2); line-height: 1.65; }

  /* ── HOW IT WORKS ── */
  .how-bg { background: var(--bg2); }
  .steps-row {
    display: grid; grid-template-columns: repeat(4, 1fr);
    gap: 0; margin-top: 60px; position: relative;
  }
  .steps-row::before {
    content: ''; position: absolute; top: 27px; left: 12%; right: 12%; height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent), var(--accent3), transparent);
  }
  .step-card { padding: 0 20px; text-align: center; position: relative; }
  .step-num {
    width: 56px; height: 56px; border-radius: 50%;
    margin: 0 auto 20px;
    display: flex; align-items: center; justify-content: center;
    font-size: 20px; font-weight: 700; border: 2px solid;
    position: relative; z-index: 1; background: var(--bg2);
  }
  .sn-1 { border-color: var(--accent);  color: var(--accent); }
  .sn-2 { border-color: #a29bfe;        color: #a29bfe; }
  .sn-3 { border-color: var(--accent3); color: var(--accent3); }
  .sn-4 { border-color: var(--green);   color: var(--green); }
  .step-card h4 { font-size: 15px; font-weight: 600; margin-bottom: 10px; }
  .step-card p  { font-size: 14px; color: var(--text2); line-height: 1.6; }

  /* ── BENEFITS ── */
  .benefits-layout {
    display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: center;
  }
  .benefits-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; }
  .benefit-item { display: flex; gap: 14px; align-items: flex-start; }
  .check-icon {
    width: 22px; height: 22px; border-radius: 50%;
    background: rgba(0,206,201,0.15); flex-shrink: 0; margin-top: 2px;
    display: flex; align-items: center; justify-content: center;
  }
  .check-icon::after { content: '✓'; font-size: 12px; color: var(--green); font-weight: 700; }
  .benefit-item strong { font-size: 15px; display: block; margin-bottom: 4px; }
  .benefit-item span { font-size: 14px; color: var(--text2); }

  /* ── TESTIMONIALS ── */
  .testi-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; margin-top: 60px; }
  .testi-card {
    background: var(--surface); border: 1px solid var(--border2);
    border-radius: 16px; padding: 28px; transition: border-color .2s;
  }
  .testi-card:hover { border-color: rgba(162,155,254,0.3); }
  .stars { color: #ffd700; font-size: 14px; margin-bottom: 16px; letter-spacing: 2px; }
  .testi-quote { font-size: 15px; line-height: 1.7; color: var(--text); margin-bottom: 22px; }
  .testi-author { display: flex; align-items: center; gap: 12px; }
  .avatar {
    width: 40px; height: 40px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-weight: 700; font-size: 14px;
    background: var(--grad); color: white; flex-shrink: 0;
  }
  .author-name { font-size: 14px; font-weight: 600; }
  .author-role { font-size: 13px; color: var(--text3); margin-top: 2px; }

  /* ── PRICING ── */
  .pricing-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; margin-top: 60px; }
  .price-card {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 20px; padding: 36px 28px; position: relative; transition: border-color .25s;
  }
  .price-card:hover { border-color: var(--border2); }
  .price-card.featured { border-color: rgba(108,92,231,0.5); background: rgba(108,92,231,0.07); }
  .popular-badge {
    position: absolute; top: -14px; left: 50%; transform: translateX(-50%);
    background: var(--grad); color: white;
    font-size: 12px; font-weight: 700; padding: 4px 18px; border-radius: 100px; white-space: nowrap;
  }
  .plan-name {
    font-size: 13px; text-transform: uppercase; letter-spacing: 1.5px;
    color: var(--text3); font-weight: 700; margin-bottom: 16px;
  }
  .plan-price { font-size: 48px; font-weight: 800; letter-spacing: -2px; margin-bottom: 4px; }
  .plan-price span { font-size: 18px; font-weight: 500; color: var(--text2); }
  .plan-period { font-size: 14px; color: var(--text3); margin-bottom: 28px; }
  .plan-features { list-style: none; margin-bottom: 28px; }
  .plan-features li {
    font-size: 14px; color: var(--text2); padding: 9px 0;
    border-bottom: 1px solid var(--border);
    display: flex; align-items: center; gap: 8px;
  }
  .plan-features li::before { content: '✓'; color: var(--green); font-weight: 700; flex-shrink: 0; }
  .plan-features li.no::before { content: '—'; color: var(--text3); }
  .plan-features li.no { color: var(--text3); }
  .btn-plan {
    width: 100%; padding: 13px; border-radius: 10px;
    font-size: 15px; font-weight: 600; cursor: pointer;
    transition: all .2s; border: none; font-family: inherit;
  }
  .btn-plan-outline { background: transparent; border: 1px solid var(--border2) !important; color: var(--text); }
  .btn-plan-outline:hover { background: var(--surface2); }
  .btn-plan-grad { background: var(--grad); color: white; box-shadow: 0 4px 24px rgba(108,92,231,0.35); }
  .btn-plan-grad:hover { opacity: 0.88; transform: translateY(-1px); }

  /* ── FAQ ── */
  .faq-list { margin-top: 60px; max-width: 720px; }
  .faq-item { border-bottom: 1px solid var(--border); padding: 24px 0; cursor: pointer; }
  .faq-q {
    font-size: 16px; font-weight: 600;
    display: flex; justify-content: space-between; align-items: center; gap: 16px;
  }
  .faq-q::after {
    content: '+'; font-size: 22px; color: var(--accent2);
    font-weight: 300; transition: transform .25s; flex-shrink: 0;
  }
  .faq-item.open .faq-q::after { transform: rotate(45deg); }
  .faq-a {
    font-size: 15px; color: var(--text2); line-height: 1.7;
    max-height: 0; overflow: hidden; transition: max-height .35s ease, padding .2s;
  }
  .faq-item.open .faq-a { max-height: 200px; padding-top: 14px; }

  /* ── FINAL CTA ── */
  .cta-section {
    padding: 120px 48px; text-align: center;
    background: radial-gradient(ellipse at 50% 0%, rgba(108,92,231,0.15) 0%, transparent 60%);
    border-top: 1px solid var(--border);
  }
  .cta-section h2 {
    font-size: clamp(32px, 4vw, 56px); font-weight: 800;
    letter-spacing: -2px; margin-bottom: 16px;
  }
  .cta-section > p { font-size: 17px; color: var(--text2); margin-bottom: 40px; }
  .cta-btns { display: flex; gap: 14px; justify-content: center; flex-wrap: wrap; }
  .cta-note { margin-top: 20px; font-size: 13px; color: var(--text3); }

  /* ── FOOTER ── */
  footer { border-top: 1px solid var(--border); padding: 60px 48px; }
  .footer-inner { max-width: 1200px; margin: 0 auto; }
  .footer-top {
    display: grid; grid-template-columns: 2fr 1fr 1fr 1fr 1fr;
    gap: 40px; margin-bottom: 48px;
  }
  .footer-brand p {
    font-size: 14px; color: var(--text3); line-height: 1.7;
    margin-top: 12px; max-width: 240px;
  }
  .footer-col h5 {
    font-size: 13px; font-weight: 700; text-transform: uppercase;
    letter-spacing: 1px; color: var(--text3); margin-bottom: 16px;
  }
  .footer-col a {
    display: block; font-size: 14px; color: var(--text2);
    text-decoration: none; margin-bottom: 10px; transition: color .2s;
  }
  .footer-col a:hover { color: var(--text); }
  .footer-bottom {
    border-top: 1px solid var(--border); padding-top: 28px;
    display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 16px;
  }
  .footer-bottom p { font-size: 13px; color: var(--text3); }
  .footer-links { display: flex; gap: 24px; }
  .footer-links a { font-size: 13px; color: var(--text3); text-decoration: none; }
  .footer-links a:hover { color: var(--text2); }

  /* ── SCROLL ANIMATIONS ── */
  .fade-up { opacity: 0; transform: translateY(30px); transition: opacity .65s ease, transform .65s ease; }
  .fade-up.visible { opacity: 1; transform: translateY(0); }
  .delay-1 { transition-delay: .12s; }
  .delay-2 { transition-delay: .24s; }
  .delay-3 { transition-delay: .36s; }

  /* ── RESPONSIVE ── */
  @media (max-width: 960px) {
    nav { padding: 0 24px; }
    .nav-links { display: none; }
    .hero { padding: 100px 24px 60px; }
    h1 { font-size: 36px; }
    .dash-body { grid-template-columns: 1fr; }
    .dash-sidebar { border-right: none; border-bottom: 1px solid var(--border); }
    .stats-row { grid-template-columns: repeat(2, 1fr); }
    .features-grid { grid-template-columns: 1fr 1fr; }
    .steps-row { grid-template-columns: repeat(2, 1fr); gap: 32px; }
    .steps-row::before { display: none; }
    .benefits-layout { grid-template-columns: 1fr; gap: 40px; }
    .benefits-grid { grid-template-columns: 1fr; }
    .testi-grid { grid-template-columns: 1fr; }
    .pricing-grid { grid-template-columns: 1fr; max-width: 440px; margin-left: auto; margin-right: auto; }
    .section-inner { padding: 60px 24px; }
    .cta-section { padding: 80px 24px; }
    footer { padding: 40px 24px; }
    .footer-top { grid-template-columns: 1fr 1fr; }
    .trust-section { padding: 48px 24px; }
    .logo-strip { gap: 28px; }
  }
  @media (max-width: 560px) {
    .features-grid { grid-template-columns: 1fr; }
    .stats-row { grid-template-columns: 1fr 1fr; }
    .steps-row { grid-template-columns: 1fr; }
    .footer-top { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- ═══════════════ NAV ═══════════════ -->
<nav>
  <a href="#" class="nav-logo">
    <div class="logo-icon">✦</div>
    PresentAI
  </a>
  <ul class="nav-links">
    <li><a href="#features">Features</a></li>
    <li><a href="#how">How it works</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#faq">FAQ</a></li>
  </ul>
  <div class="nav-cta">
    <button class="btn-ghost">Log in</button>
    <button class="btn-primary">Start Free</button>
  </div>
</nav>

<!-- ═══════════════ HERO ═══════════════ -->
<section class="hero">
  <div class="hero-glow"></div>
  <div class="hero-glow2"></div>

  <div class="badge">
    <span class="badge-dot"></span>
    AI-Powered Presentation Builder
  </div>

  <h1>Create Stunning Presentations in Seconds with AI</h1>

  <p class="subhead">Turn ideas, documents, PDFs, websites, and notes into beautifully designed presentations instantly. No design skills required.</p>

  <div class="hero-btns">
    <button class="btn-hero btn-hero-primary">Start Free — No credit card</button>
    <button class="btn-hero btn-hero-secondary">
      <span class="play-icon"></span>
      Watch Demo
    </button>
  </div>

  <!-- Interactive dashboard preview -->
  <div class="hero-dashboard fade-up">
    <div class="dash-topbar">
      <div class="dot-row">
        <div class="dot dot-r"></div>
        <div class="dot dot-y"></div>
        <div class="dot dot-g"></div>
      </div>
      <div class="dash-title">PresentAI — Q4 Investor Deck</div>
    </div>
    <div class="dash-body">
      <div class="dash-sidebar">
        <div class="dash-sidebar-title">AI Generation</div>
        <div class="ai-prompt-box">
          <div class="ai-prompt-label">✦ Your Prompt</div>
          <div class="ai-prompt-text">"Create a Q4 investor deck for our SaaS startup with market data and growth metrics"</div>
        </div>
        <div class="ai-step" style="opacity:0.6">
          <div class="step-icon step-done-icon">✓</div>
          <div class="step-label">Analyzing prompt</div>
        </div>
        <div class="ai-step" style="opacity:0.6">
          <div class="step-icon step-done-icon">✓</div>
          <div class="step-label">Structuring content</div>
        </div>
        <div class="ai-step ai-step-active">
          <div class="step-icon step-active-icon">●</div>
          <div class="step-label step-label-active">Designing slides</div>
        </div>
        <div class="ai-step">
          <div class="step-icon step-pending-icon">4</div>
          <div class="step-label">Finalizing export</div>
        </div>
      </div>
      <div class="dash-main">
        <div class="dash-main-header">
          <div class="dash-main-title">Slide Preview</div>
          <div class="gen-badge">● Generating…</div>
        </div>
        <div class="slides-grid">
          <div class="slide-thumb slide-bg-1 active">
            <div class="slide-line slide-line-accent w60"></div>
            <div class="slide-line slide-line-sm w70"></div>
            <div class="slide-line slide-line-sm w50"></div>
          </div>
          <div class="slide-thumb slide-bg-2">
            <div class="slide-line slide-line-sm w40"></div>
            <div class="slide-line slide-line-sm w70"></div>
            <div class="slide-line slide-line-sm w30"></div>
          </div>
          <div class="slide-thumb slide-bg-3">
            <div class="slide-line slide-line-accent w50"></div>
            <div class="slide-line slide-line-sm w70"></div>
            <div class="slide-line slide-line-sm w40"></div>
          </div>
          <div class="slide-thumb slide-bg-4">
            <div class="slide-line slide-line-sm w60"></div>
            <div class="slide-line slide-line-sm w40"></div>
            <div class="slide-line slide-line-sm w70"></div>
          </div>
          <div class="slide-thumb slide-bg-5">
            <div class="slide-line slide-line-accent w70"></div>
            <div class="slide-line slide-line-sm w50"></div>
            <div class="slide-line slide-line-sm w40"></div>
          </div>
          <div class="slide-thumb slide-bg-6" style="opacity:0.35;display:flex;align-items:center;justify-content:center;">
            <span style="font-size:24px;color:rgba(255,255,255,0.25)">✦</span>
          </div>
        </div>
        <div class="progress-row">
          <div style="font-size:13px;color:var(--text3)">Generating slide 5 of 12</div>
          <div class="progress-bar-wrap">
            <div class="progress-bar-fill" id="prog-fill"></div>
          </div>
          <div class="progress-label" id="prog-label">42%</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ═══════════════ TRUST ═══════════════ -->
<div class="trust-section">
  <div class="trust-label">Trusted by teams at world-class companies</div>
  <div class="logo-strip">
    <div class="logo-item">Notion</div>
    <div class="logo-item">Linear</div>
    <div class="logo-item">Stripe</div>
    <div class="logo-item">Vercel</div>
    <div class="logo-item">Figma</div>
    <div class="logo-item">OpenAI</div>
    <div class="logo-item">Airbnb</div>
  </div>
</div>

<!-- ═══════════════ STATS ═══════════════ -->
<div class="section-inner" style="padding-bottom:0">
  <div style="text-align:center">
    <div class="section-tag fade-up">By the numbers</div>
    <h2 class="section-h2 fade-up delay-1" style="text-align:center;max-width:100%">The results speak for themselves</h2>
  </div>
  <div class="stats-row fade-up delay-2">
    <div class="stat-card">
      <div class="stat-num">95%</div>
      <div class="stat-label">Faster than traditional methods</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">2M+</div>
      <div class="stat-label">Presentations created</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">50K+</div>
      <div class="stat-label">Happy users worldwide</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">4.9★</div>
      <div class="stat-label">Average user rating</div>
    </div>
  </div>
</div>

<!-- ═══════════════ FEATURES ═══════════════ -->
<div class="section-inner" id="features">
  <div class="section-tag fade-up">Features</div>
  <h2 class="section-h2 fade-up delay-1">Everything you need to present brilliantly</h2>
  <p class="section-sub fade-up delay-2">Six powerful capabilities that transform how you create and deliver presentations.</p>
  <div class="features-grid fade-up delay-3">
    <div class="feature-card">
      <div class="feat-icon fi-purple">✦</div>
      <h3>AI-Powered Generation</h3>
      <p>Generate complete, professional slide decks from a simple text prompt in seconds. Our AI understands context, structure, and storytelling.</p>
    </div>
    <div class="feature-card">
      <div class="feat-icon fi-pink">◈</div>
      <h3>Smart Design Engine</h3>
      <p>Automatically creates layouts, selects visuals, animations, and typography that perfectly match your content and brand identity.</p>
    </div>
    <div class="feature-card">
      <div class="feat-icon fi-teal">⟐</div>
      <h3>Document to Deck</h3>
      <p>Upload PDFs, Word docs, websites, or raw notes. PresentAI extracts key information and transforms it into a polished presentation.</p>
    </div>
    <div class="feature-card">
      <div class="feat-icon fi-blue">⌨</div>
      <h3>Real-Time AI Editing</h3>
      <p>Edit content using plain language commands. Say "make this slide more concise" or "add a growth chart" — AI handles the rest.</p>
    </div>
    <div class="feature-card">
      <div class="feat-icon fi-amber">◎</div>
      <h3>Team Collaboration</h3>
      <p>Share presentations with your team for real-time editing, commenting, and version control — just like Google Docs, but for slides.</p>
    </div>
    <div class="feature-card">
      <div class="feat-icon fi-green">⊞</div>
      <h3>Multi-Format Export</h3>
      <p>Export to PowerPoint (.pptx), PDF, interactive web pages, or mobile-optimized formats — ready for any stage or screen.</p>
    </div>
  </div>
</div>

<!-- ═══════════════ HOW IT WORKS ═══════════════ -->
<div class="how-bg" id="how">
  <div class="section-inner">
    <div class="section-tag fade-up">How it works</div>
    <h2 class="section-h2 fade-up delay-1">From idea to deck in four steps</h2>
    <p class="section-sub fade-up delay-2">The most intuitive presentation workflow ever built.</p>
    <div class="steps-row fade-up delay-3">
      <div class="step-card">
        <div class="step-num sn-1">1</div>
        <h4>Enter a prompt or upload</h4>
        <p>Type your idea or drop in a document, PDF, or URL. PresentAI handles the rest from there.</p>
      </div>
      <div class="step-card">
        <div class="step-num sn-2">2</div>
        <h4>AI analyzes &amp; structures</h4>
        <p>Our AI breaks down your content, identifies key points, and creates a compelling narrative flow.</p>
      </div>
      <div class="step-card">
        <div class="step-num sn-3">3</div>
        <h4>Generate your deck</h4>
        <p>Watch as a beautifully designed, professional presentation is built right before your eyes.</p>
      </div>
      <div class="step-card">
        <div class="step-num sn-4">4</div>
        <h4>Customize &amp; export</h4>
        <p>Refine with AI commands, collaborate with your team, then export in any format you need.</p>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════ BENEFITS ═══════════════ -->
<div class="section-inner">
  <div class="benefits-layout">
    <div>
      <div class="section-tag fade-up">Benefits</div>
      <h2 class="section-h2 fade-up delay-1">Why teams choose PresentAI</h2>
      <p class="section-sub fade-up delay-2">Join thousands of professionals saving hours every week while delivering better presentations than ever before.</p>
    </div>
    <div class="benefits-grid fade-up delay-2">
      <div class="benefit-item">
        <div class="check-icon"></div>
        <div>
          <strong>Save 95% of the time</strong>
          <span>What took days now takes minutes. Focus on ideas, not formatting.</span>
        </div>
      </div>
      <div class="benefit-item">
        <div class="check-icon"></div>
        <div>
          <strong>Professional quality, instantly</strong>
          <span>Every slide designed by AI trained on thousands of beautiful decks.</span>
        </div>
      </div>
      <div class="benefit-item">
        <div class="check-icon"></div>
        <div>
          <strong>No design skills needed</strong>
          <span>Anyone on your team can create stunning slides in minutes.</span>
        </div>
      </div>
      <div class="benefit-item">
        <div class="check-icon"></div>
        <div>
          <strong>Built for teams &amp; individuals</strong>
          <span>Scales from solo freelancers to enterprise teams of hundreds.</span>
        </div>
      </div>
      <div class="benefit-item">
        <div class="check-icon"></div>
        <div>
          <strong>AI-generated visuals</strong>
          <span>Charts, diagrams, and layouts created automatically from your data.</span>
        </div>
      </div>
      <div class="benefit-item">
        <div class="check-icon"></div>
        <div>
          <strong>Constantly improving</strong>
          <span>Our AI learns and improves with every presentation created globally.</span>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════ TESTIMONIALS ═══════════════ -->
<div class="section-inner" style="padding-top:0" id="testimonials">
  <div style="text-align:center">
    <div class="section-tag fade-up">Testimonials</div>
    <h2 class="section-h2 fade-up delay-1" style="max-width:100%;text-align:center">Loved by thousands of professionals</h2>
  </div>
  <div class="testi-grid">
    <div class="testi-card fade-up">
      <div class="stars">★★★★★</div>
      <p class="testi-quote">"PresentAI cut my deck creation time from 6 hours to under 20 minutes. The quality is genuinely better than what I was producing manually. It's become essential for our sales team."</p>
      <div class="testi-author">
        <div class="avatar">SR</div>
        <div>
          <div class="author-name">Sarah Ramirez</div>
          <div class="author-role">Head of Sales, CloudScale Inc.</div>
        </div>
      </div>
    </div>
    <div class="testi-card fade-up delay-1">
      <div class="stars">★★★★★</div>
      <p class="testi-quote">"I uploaded a 40-page research report and got a beautiful 12-slide deck in 30 seconds. The AI understood exactly what was important. I was genuinely stunned by the output quality."</p>
      <div class="testi-author">
        <div class="avatar">MK</div>
        <div>
          <div class="author-name">Marcus Kim</div>
          <div class="author-role">Senior Analyst, Deloitte Digital</div>
        </div>
      </div>
    </div>
    <div class="testi-card fade-up delay-2">
      <div class="stars">★★★★★</div>
      <p class="testi-quote">"As a startup founder, I'm constantly pitching. PresentAI lets me iterate on investor decks in real-time. We raised our Series A in record time — this tool played a huge part in that."</p>
      <div class="testi-author">
        <div class="avatar">AP</div>
        <div>
          <div class="author-name">Anika Patel</div>
          <div class="author-role">Co-Founder &amp; CEO, Nexus Labs</div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════ PRICING ═══════════════ -->
<div class="section-inner" style="padding-top:40px" id="pricing">
  <div style="text-align:center">
    <div class="section-tag fade-up">Pricing</div>
    <h2 class="section-h2 fade-up delay-1" style="max-width:100%;text-align:center">Simple, transparent pricing</h2>
    <p class="section-sub fade-up delay-2" style="margin:0 auto">Start free, upgrade when you're ready. No hidden fees, no surprises ever.</p>
  </div>
  <div class="pricing-grid fade-up delay-2">
    <div class="price-card">
      <div class="plan-name">Starter</div>
      <div class="plan-price">$0</div>
      <div class="plan-period">Free forever</div>
      <ul class="plan-features">
        <li>5 AI presentations / month</li>
        <li>10 slides per deck</li>
        <li>PDF export</li>
        <li>Basic templates</li>
        <li class="no">Custom branding</li>
        <li class="no">Team collaboration</li>
        <li class="no">PPTX export</li>
      </ul>
      <button class="btn-plan btn-plan-outline">Get started free</button>
    </div>
    <div class="price-card featured">
      <div class="popular-badge">Most Popular</div>
      <div class="plan-name">Pro</div>
      <div class="plan-price">$19<span>/mo</span></div>
      <div class="plan-period">Billed monthly · $15/mo billed annually</div>
      <ul class="plan-features">
        <li>Unlimited presentations</li>
        <li>Unlimited slides</li>
        <li>PPTX, PDF &amp; Web export</li>
        <li>All premium templates</li>
        <li>Custom branding</li>
        <li>Document upload (PDF, DOCX)</li>
        <li class="no">Team collaboration</li>
      </ul>
      <button class="btn-plan btn-plan-grad">Start Pro free trial</button>
    </div>
    <div class="price-card">
      <div class="plan-name">Business</div>
      <div class="plan-price">$49<span>/mo</span></div>
      <div class="plan-period">Per user · Billed annually</div>
      <ul class="plan-features">
        <li>Everything in Pro</li>
        <li>Team collaboration</li>
        <li>Shared brand kit</li>
        <li>Analytics &amp; insights</li>
        <li>Priority AI generation</li>
        <li>Dedicated support</li>
        <li>SSO &amp; admin controls</li>
      </ul>
      <button class="btn-plan btn-plan-outline">Start Business trial</button>
    </div>
  </div>
</div>

<!-- ═══════════════ FAQ ═══════════════ -->
<div class="section-inner" style="padding-top:40px;padding-bottom:60px" id="faq">
  <div class="section-tag fade-up">FAQ</div>
  <h2 class="section-h2 fade-up delay-1">Frequently asked questions</h2>
  <div class="faq-list fade-up delay-2">
    <div class="faq-item">
      <div class="faq-q">How does the AI work?</div>
      <div class="faq-a">PresentAI uses large language models trained on millions of professional presentations, design principles, and storytelling frameworks. When you enter a prompt or upload a document, our AI analyzes the content, creates a narrative structure, selects appropriate layouts, and generates copy — all in seconds.</div>
    </div>
    <div class="faq-item">
      <div class="faq-q">Can I export to PowerPoint?</div>
      <div class="faq-a">Yes! Pro and Business plans include full PPTX export. Your slides export with editable text, vector graphics, and native PowerPoint formatting — fully compatible with Microsoft Office, Google Slides, and Keynote.</div>
    </div>
    <div class="faq-item">
      <div class="faq-q">Is there a free plan?</div>
      <div class="faq-a">Absolutely. Our Starter plan is free forever and includes 5 AI-generated presentations per month with up to 10 slides each. No credit card required to get started. Upgrade anytime to unlock unlimited presentations and advanced features.</div>
    </div>
    <div class="faq-item">
      <div class="faq-q">Can teams collaborate in real time?</div>
      <div class="faq-a">Team collaboration is available on our Business plan. Multiple team members can edit, comment, and provide feedback simultaneously — with full version history, permissions management, and shared brand kits across the organization.</div>
    </div>
    <div class="faq-item">
      <div class="faq-q">What file types can I upload?</div>
      <div class="faq-a">Pro and Business users can upload PDF files, Microsoft Word documents (.docx), plain text files, and paste in any URL. Our AI extracts key content and structures it into a presentation automatically within seconds.</div>
    </div>
  </div>
</div>

<!-- ═══════════════ FINAL CTA ═══════════════ -->
<div class="cta-section">
  <div class="section-tag fade-up">Get started today</div>
  <h2 class="fade-up delay-1">Ready to build your next presentation in minutes?</h2>
  <p class="fade-up delay-2">Join 50,000+ professionals who've already transformed how they present to the world.</p>
  <div class="cta-btns fade-up delay-3">
    <button class="btn-hero btn-hero-primary" style="font-size:17px;padding:16px 48px">Start Free Today</button>
    <button class="btn-hero btn-hero-secondary" style="font-size:15px;padding:14px 32px">See all features</button>
  </div>
  <p class="cta-note fade-up delay-3">No credit card required · Free forever plan available · Cancel anytime</p>
</div>

<!-- ═══════════════ FOOTER ═══════════════ -->
<footer>
  <div class="footer-inner">
    <div class="footer-top">
      <div class="footer-brand">
        <a href="#" class="nav-logo" style="font-size:16px;text-decoration:none;color:var(--text)">
          <div class="logo-icon" style="width:26px;height:26px;font-size:13px">✦</div>
          PresentAI
        </a>
        <p>The AI-powered presentation platform trusted by professionals and teams worldwide.</p>
      </div>
      <div class="footer-col">
        <h5>Product</h5>
        <a href="#">Features</a>
        <a href="#">Pricing</a>
        <a href="#">Templates</a>
        <a href="#">Changelog</a>
      </div>
      <div class="footer-col">
        <h5>Resources</h5>
        <a href="#">Blog</a>
        <a href="#">Documentation</a>
        <a href="#">Tutorials</a>
        <a href="#">API</a>
      </div>
      <div class="footer-col">
        <h5>Company</h5>
        <a href="#">About</a>
        <a href="#">Careers</a>
        <a href="#">Press</a>
        <a href="#">Contact</a>
      </div>
      <div class="footer-col">
        <h5>Legal</h5>
        <a href="#">Privacy Policy</a>
        <a href="#">Terms of Service</a>
        <a href="#">Security</a>
        <a href="#">Cookies</a>
      </div>
    </div>
    <div class="footer-bottom">
      <p>© 2026 PresentAI, Inc. All rights reserved.</p>
      <div class="footer-links">
        <a href="#">Privacy</a>
        <a href="#">Terms</a>
        <a href="#">Status</a>
      </div>
    </div>
  </div>
</footer>

<script>
  /* Scroll animations */
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.1 });
  document.querySelectorAll('.fade-up').forEach(el => observer.observe(el));

  /* FAQ accordion */
  document.querySelectorAll('.faq-item').forEach(item => {
    item.addEventListener('click', () => {
      const wasOpen = item.classList.contains('open');
      document.querySelectorAll('.faq-item').forEach(i => i.classList.remove('open'));
      if (!wasOpen) item.classList.add('open');
    });
  });

  /* Hero progress bar animation */
  let pct = 42;
  const fill  = document.getElementById('prog-fill');
  const label = document.getElementById('prog-label');
  const timer = setInterval(() => {
    pct = Math.min(pct + Math.floor(Math.random() * 4) + 1, 85);
    if (fill)  fill.style.width  = pct + '%';
    if (label) label.textContent = pct + '%';
    if (pct >= 85) clearInterval(timer);
  }, 1800);

  /* Slide thumb click interaction */
  document.querySelectorAll('.slide-thumb').forEach(thumb => {
    thumb.addEventListener('click', () => {
      document.querySelectorAll('.slide-thumb').forEach(t => t.classList.remove('active'));
      thumb.classList.add('active');
    });
  });
</script>
</body>
</html>