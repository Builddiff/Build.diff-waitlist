<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Build.diff — Waitlist</title>
  <meta name="description" content="We build what others can't diff. Join the waitlist for Build.diff — a design studio rewriting the rules."/>

  <!-- ══════════════════════════════════════════
       FONTS — change here to update typography
  ══════════════════════════════════════════ -->
  <link rel="preconnect" href="https://fonts.googleapis.com"/>
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
  <link href="https://fonts.googleapis.com/css2?family=DM+Mono:ital,wght@0,300;0,400;0,500;1,300&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet"/>

  <style>
    /* ══════════════════════════════════════════
       DESIGN TOKENS — edit these to retheme the
       entire page in one place
    ══════════════════════════════════════════ */
    :root {
      --bg:          #0A0A08;        /* page background */
      --surface:     #111110;        /* card / nav surface */
      --surface-2:   #1A1A18;        /* elevated surface */
      --border:      #2A2A28;        /* default border */
      --border-hi:   #3D3D3A;        /* hover border */
      --accent:      #C8F04A;        /* PRIMARY accent — lime green */
      --accent-dim:  #8FAB2E;        /* muted accent */
      --text-1:      #F0EFE6;        /* headings */
      --text-2:      #8E8D84;        /* body / secondary */
      --text-3:      #54534D;        /* placeholders */
      --font-display: 'Syne', sans-serif;
      --font-mono:    'DM Mono', monospace;
      --radius-sm:   6px;
      --radius-md:   12px;
      --radius-lg:   20px;
      --radius-pill: 999px;
      --transition:  0.22s cubic-bezier(0.4, 0, 0.2, 1);
    }

    /* ─── Reset ──────────────────────────────── */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      background: var(--bg);
      color: var(--text-1);
      font-family: var(--font-mono);
      font-size: 15px;
      line-height: 1.65;
      min-height: 100vh;
      overflow-x: hidden;
      -webkit-font-smoothing: antialiased;
    }

    /* ─── Noise texture overlay ──────────────── */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 0;
    }

    /* ─── Radial glow behind hero ────────────── */
    .glow {
      position: fixed;
      top: -200px;
      left: 50%;
      transform: translateX(-50%);
      width: 900px;
      height: 600px;
      background: radial-gradient(ellipse at center, rgba(200,240,74,0.08) 0%, transparent 70%);
      pointer-events: none;
      z-index: 0;
    }

    /* ─── Layout ─────────────────────────────── */
    .wrapper {
      max-width: 1120px;
      margin: 0 auto;
      padding: 0 32px;
      position: relative;
      z-index: 1;
    }

    /* ─── NAV ────────────────────────────────── */
    nav {
      position: sticky;
      top: 0;
      z-index: 100;
      border-bottom: 1px solid var(--border);
      background: rgba(10,10,8,0.82);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
    }
    .nav-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 18px 32px;
      max-width: 1120px;
      margin: 0 auto;
    }
    .logo {
      font-family: var(--font-display);
      font-size: 20px;
      font-weight: 800;
      letter-spacing: -0.5px;
      color: var(--text-1);
      text-decoration: none;
      display: flex;
      align-items: center;
      gap: 6px;
    }
    .logo-dot {
      display: inline-block;
      width: 8px;
      height: 8px;
      background: var(--accent);
      border-radius: 50%;
      animation: pulse 2.4s ease-in-out infinite;
    }
    @keyframes pulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50%       { opacity: 0.5; transform: scale(0.75); }
    }
    .nav-tag {
      font-family: var(--font-mono);
      font-size: 11px;
      letter-spacing: 0.08em;
      color: var(--text-2);
      border: 1px solid var(--border);
      border-radius: var(--radius-pill);
      padding: 4px 12px;
    }

    /* ─── HERO ───────────────────────────────── */
    .hero {
      padding: 120px 0 80px;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 60px;
      align-items: center;
    }
    @media (max-width: 768px) {
      .hero { grid-template-columns: 1fr; padding: 80px 0 60px; }
      .hero-meta { order: -1; }
    }

    .hero-eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-size: 11px;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 24px;
    }
    .hero-eyebrow::before {
      content: '';
      display: block;
      width: 24px;
      height: 1px;
      background: var(--accent);
    }

    h1 {
      font-family: var(--font-display);
      font-size: clamp(48px, 7vw, 80px);
      font-weight: 800;
      line-height: 0.95;
      letter-spacing: -0.03em;
      color: var(--text-1);
      margin-bottom: 28px;
    }
    h1 .diff {
      color: var(--accent);
      display: inline-block;
    }
    h1 .line-break { display: block; }

    .hero-body {
      font-family: var(--font-mono);
      font-size: 15px;
      color: var(--text-2);
      line-height: 1.8;
      max-width: 420px;
      margin-bottom: 40px;
    }

    /* ─── WAITLIST FORM ──────────────────────── */
    .form-wrap {
      display: flex;
      flex-direction: column;
      gap: 12px;
      max-width: 440px;
    }
    .input-row {
      display: flex;
      gap: 10px;
    }
    @media (max-width: 480px) {
      .input-row { flex-direction: column; }
    }
    .field {
      position: relative;
      flex: 1;
    }
    .field input {
      width: 100%;
      background: var(--surface-2);
      border: 1px solid var(--border);
      border-radius: var(--radius-md);
      color: var(--text-1);
      font-family: var(--font-mono);
      font-size: 14px;
      padding: 14px 16px;
      outline: none;
      transition: border-color var(--transition), box-shadow var(--transition);
    }
    .field input::placeholder { color: var(--text-3); }
    .field input:focus {
      border-color: var(--accent);
      box-shadow: 0 0 0 3px rgba(200,240,74,0.12);
    }
    .btn-join {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      background: var(--accent);
      color: #0A0A08;
      font-family: var(--font-display);
      font-weight: 700;
      font-size: 14px;
      letter-spacing: 0.02em;
      border: none;
      border-radius: var(--radius-md);
      padding: 14px 28px;
      cursor: pointer;
      white-space: nowrap;
      transition: background var(--transition), transform var(--transition), box-shadow var(--transition);
    }
    .btn-join:hover {
      background: #d8ff55;
      box-shadow: 0 0 24px rgba(200,240,74,0.3);
      transform: translateY(-1px);
    }
    .btn-join:active { transform: translateY(0); }
    .btn-join svg { flex-shrink: 0; }

    /* select dropdown */
    .select-wrap {
      position: relative;
    }
    .select-wrap select {
      width: 100%;
      appearance: none;
      background: var(--surface-2);
      border: 1px solid var(--border);
      border-radius: var(--radius-md);
      color: var(--text-2);
      font-family: var(--font-mono);
      font-size: 13px;
      padding: 12px 40px 12px 16px;
      outline: none;
      cursor: pointer;
      transition: border-color var(--transition);
    }
    .select-wrap select:focus { border-color: var(--accent); }
    .select-arrow {
      position: absolute;
      right: 14px;
      top: 50%;
      transform: translateY(-50%);
      pointer-events: none;
      color: var(--text-3);
    }

    .form-note {
      font-size: 12px;
      color: var(--text-3);
      letter-spacing: 0.02em;
    }

    /* success state */
    .success-msg {
      display: none;
      align-items: center;
      gap: 10px;
      background: rgba(200,240,74,0.08);
      border: 1px solid rgba(200,240,74,0.25);
      border-radius: var(--radius-md);
      padding: 16px 20px;
      color: var(--accent);
      font-size: 14px;
    }
    .success-msg.show { display: flex; }

    /* ─── HERO META / STATS ──────────────────── */
    .hero-meta {
      display: flex;
      flex-direction: column;
      gap: 24px;
    }
    .stat-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
    }
    .stat-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius-lg);
      padding: 24px;
      position: relative;
      overflow: hidden;
      transition: border-color var(--transition);
    }
    .stat-card:hover { border-color: var(--border-hi); }
    .stat-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: var(--accent);
      opacity: 0;
      transition: opacity var(--transition);
    }
    .stat-card:hover::before { opacity: 1; }
    .stat-num {
      font-family: var(--font-display);
      font-size: 36px;
      font-weight: 800;
      color: var(--text-1);
      line-height: 1;
      margin-bottom: 6px;
    }
    .stat-num span { color: var(--accent); }
    .stat-label {
      font-size: 12px;
      color: var(--text-3);
      letter-spacing: 0.06em;
      text-transform: uppercase;
    }

    /* code block teaser */
    .code-block {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius-lg);
      overflow: hidden;
    }
    .code-header {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 12px 16px;
      border-bottom: 1px solid var(--border);
    }
    .code-dot { width: 10px; height: 10px; border-radius: 50%; }
    .code-dot.red    { background: #FF5F56; }
    .code-dot.yellow { background: #FFBD2E; }
    .code-dot.green  { background: #27C93F; }
    .code-filename {
      font-size: 11px;
      color: var(--text-3);
      margin-left: auto;
      letter-spacing: 0.04em;
    }
    pre {
      padding: 20px;
      font-family: var(--font-mono);
      font-size: 13px;
      line-height: 1.7;
      overflow-x: auto;
    }
    .t-add    { color: #C8F04A; }
    .t-rem    { color: #FF6B6B; }
    .t-mute   { color: var(--text-3); }
    .t-key    { color: #79B8FF; }
    .t-str    { color: #F0A878; }
    .t-num    { color: #D2A8FF; }

    /* ─── SECTION: WHAT WE DO ────────────────── */
    section { padding: 80px 0; }
    .section-tag {
      font-size: 11px;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 16px;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .section-tag::before {
      content: '';
      display: block;
      width: 16px;
      height: 1px;
      background: var(--accent);
    }
    h2 {
      font-family: var(--font-display);
      font-size: clamp(32px, 4vw, 48px);
      font-weight: 800;
      letter-spacing: -0.025em;
      color: var(--text-1);
      line-height: 1.1;
      margin-bottom: 20px;
    }
    .section-sub {
      font-size: 15px;
      color: var(--text-2);
      max-width: 480px;
      line-height: 1.8;
      margin-bottom: 56px;
    }

    /* Service cards */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 20px;
    }
    .service-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius-lg);
      padding: 32px;
      position: relative;
      overflow: hidden;
      transition: border-color var(--transition), transform var(--transition);
    }
    .service-card:hover {
      border-color: var(--border-hi);
      transform: translateY(-3px);
    }
    .service-icon {
      width: 44px;
      height: 44px;
      border-radius: var(--radius-md);
      background: rgba(200,240,74,0.1);
      border: 1px solid rgba(200,240,74,0.2);
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: 20px;
      color: var(--accent);
    }
    .service-icon svg { width: 22px; height: 22px; }
    h3 {
      font-family: var(--font-display);
      font-size: 18px;
      font-weight: 700;
      color: var(--text-1);
      margin-bottom: 10px;
    }
    .service-desc {
      font-size: 13px;
      color: var(--text-2);
      line-height: 1.75;
    }
    .service-num {
      position: absolute;
      top: 24px; right: 24px;
      font-family: var(--font-display);
      font-size: 56px;
      font-weight: 800;
      color: var(--border);
      line-height: 1;
      user-select: none;
    }

    /* ─── DIVIDER ────────────────────────────── */
    .divider {
      border: none;
      border-top: 1px solid var(--border);
    }

    /* ─── PROCESS ────────────────────────────── */
    .process-list {
      display: flex;
      flex-direction: column;
      gap: 0;
    }
    .process-item {
      display: grid;
      grid-template-columns: 64px 1fr;
      gap: 24px;
      padding: 32px 0;
      border-bottom: 1px solid var(--border);
      align-items: start;
      transition: background var(--transition);
    }
    .process-item:last-child { border-bottom: none; }
    .process-num {
      font-family: var(--font-display);
      font-size: 13px;
      font-weight: 700;
      color: var(--text-3);
      padding-top: 4px;
    }
    .process-content h3 {
      font-size: 20px;
      margin-bottom: 8px;
    }
    .process-content p {
      font-size: 14px;
      color: var(--text-2);
      line-height: 1.8;
      max-width: 560px;
    }

    /* ─── TEAM ───────────────────────────────── */
    .team-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 20px;
    }
    .team-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius-lg);
      padding: 28px;
      text-align: center;
      transition: border-color var(--transition);
    }
    .team-card:hover { border-color: var(--border-hi); }
    .avatar {
      width: 64px;
      height: 64px;
      border-radius: 50%;
      background: var(--surface-2);
      border: 2px solid var(--border);
      margin: 0 auto 16px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: var(--font-display);
      font-weight: 800;
      font-size: 20px;
      color: var(--accent);
    }
    .team-name {
      font-family: var(--font-display);
      font-size: 16px;
      font-weight: 700;
      color: var(--text-1);
      margin-bottom: 4px;
    }
    .team-role {
      font-size: 12px;
      color: var(--text-3);
      letter-spacing: 0.04em;
    }

    /* ─── BOTTOM CTA ─────────────────────────── */
    .cta-section {
      padding: 100px 0;
      text-align: center;
    }
    .cta-box {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 28px;
      padding: 72px 48px;
      position: relative;
      overflow: hidden;
    }
    .cta-box::before {
      content: '';
      position: absolute;
      top: 0; left: 50%; transform: translateX(-50%);
      width: 400px; height: 1px;
      background: linear-gradient(90deg, transparent, var(--accent), transparent);
    }
    .cta-box h2 { margin: 0 auto 16px; max-width: 600px; }
    .cta-box p { color: var(--text-2); max-width: 440px; margin: 0 auto 40px; }
    .cta-form {
      display: flex;
      gap: 10px;
      justify-content: center;
      flex-wrap: wrap;
      max-width: 480px;
      margin: 0 auto;
    }
    .cta-form input {
      flex: 1;
      min-width: 220px;
      background: var(--bg);
      border: 1px solid var(--border);
      border-radius: var(--radius-md);
      color: var(--text-1);
      font-family: var(--font-mono);
      font-size: 14px;
      padding: 14px 18px;
      outline: none;
      transition: border-color var(--transition), box-shadow var(--transition);
    }
    .cta-form input::placeholder { color: var(--text-3); }
    .cta-form input:focus {
      border-color: var(--accent);
      box-shadow: 0 0 0 3px rgba(200,240,74,0.12);
    }

    /* ─── FOOTER ─────────────────────────────── */
    footer {
      border-top: 1px solid var(--border);
      padding: 40px 0;
    }
    .footer-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 16px;
    }
    .footer-copy {
      font-size: 12px;
      color: var(--text-3);
    }
    .footer-links {
      display: flex;
      gap: 24px;
    }
    .footer-links a {
      font-size: 12px;
      color: var(--text-3);
      text-decoration: none;
      transition: color var(--transition);
    }
    .footer-links a:hover { color: var(--text-2); }

    /* ─── SCROLL ANIMATIONS ──────────────────── */
    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.6s ease, transform 0.6s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* ─── TICKER ─────────────────────────────── */
    .ticker-wrap {
      overflow: hidden;
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      padding: 14px 0;
      margin: 0 -32px;
    }
    .ticker-track {
      display: flex;
      gap: 0;
      animation: ticker 28s linear infinite;
      width: max-content;
    }
    .ticker-item {
      display: flex;
      align-items: center;
      gap: 16px;
      padding: 0 40px;
      font-size: 12px;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--text-3);
      white-space: nowrap;
    }
    .ticker-item .dot {
      width: 4px; height: 4px;
      background: var(--accent);
      border-radius: 50%;
      flex-shrink: 0;
    }
    @keyframes ticker {
      from { transform: translateX(0); }
      to   { transform: translateX(-50%); }
    }
  </style>
</head>
<body>

  <div class="glow"></div>

  <!-- ══════════════════ NAV ══════════════════ -->
  <nav>
    <div class="nav-inner">
      <a href="#" class="logo">
        Build<span style="color:var(--accent)">.</span>diff
        <span class="logo-dot"></span>
      </a>
      <!-- ✏️ Edit nav badge text here -->
      <span class="nav-tag">Early Access 2025</span>
    </div>
  </nav>

  <!-- ══════════════════ HERO ══════════════════ -->
  <div class="wrapper">
    <div class="hero">
      <!-- Left: Headline + Form -->
      <div>
        <div class="hero-eyebrow">New design studio · Mumbai</div>

        <!-- ✏️ Edit hero headline here -->
        <h1>
          <span class="line-break">We build</span>
          <span class="line-break">what others</span>
          <span class="diff">can't diff.</span>
        </h1>

        <!-- ✏️ Edit hero body copy here -->
        <p class="hero-body">
          Build.diff is a design studio crafting interfaces, brand systems, and digital products that actually move people. We're opening our doors soon — get in first.
        </p>

        <!-- ✏️ FORM — hook up to your backend / Mailchimp / Airtable below -->
        <div class="form-wrap" id="hero-form-wrap">
          <div class="input-row">
            <div class="field">
              <input type="text" id="hero-name" placeholder="Your name" autocomplete="given-name"/>
            </div>
            <div class="field">
              <input type="email" id="hero-email" placeholder="Email address" autocomplete="email"/>
            </div>
          </div>
          <div class="select-wrap">
            <select id="hero-interest">
              <option value="" disabled selected>What are you looking for?</option>
              <option value="product-design">Product Design</option>
              <option value="brand-identity">Brand & Identity</option>
              <option value="web-development">Web Development</option>
              <option value="motion">Motion & Animation</option>
              <option value="other">Something else</option>
            </select>
            <span class="select-arrow">
              <svg width="12" height="12" viewBox="0 0 12 12" fill="none" stroke="currentColor" stroke-width="1.5">
                <path d="M2 4l4 4 4-4"/>
              </svg>
            </span>
          </div>
          <div>
            <button class="btn-join" onclick="handleJoin('hero')">
              Join the Waitlist
              <svg width="16" height="16" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round">
                <path d="M3 8h10M9 4l4 4-4 4"/>
              </svg>
            </button>
          </div>
          <p class="form-note">No spam, ever. We'll only reach out when we're ready for you.</p>
        </div>
        <div class="success-msg" id="hero-success">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none" stroke="currentColor" stroke-width="2">
            <circle cx="9" cy="9" r="8"/><path d="M5.5 9l2.5 2.5 4.5-4.5"/>
          </svg>
          You're on the list. We'll be in touch soon.
        </div>
      </div>

      <!-- Right: Stats + Code preview -->
      <div class="hero-meta">
        <div class="stat-grid">
          <!-- ✏️ Edit stats here -->
          <div class="stat-card">
            <div class="stat-num">3<span>+</span></div>
            <div class="stat-label">Founders</div>
          </div>
          <div class="stat-card">
            <div class="stat-num">∞</div>
            <div class="stat-label">Ambition</div>
          </div>
          <div class="stat-card">
            <div class="stat-num">0<span>%</span></div>
            <div class="stat-label">Mediocrity</div>
          </div>
          <div class="stat-card">
            <div class="stat-num">1<span>st</span></div>
            <div class="stat-label">Cohort Open</div>
          </div>
        </div>

        <!-- Decorative diff code block -->
        <div class="code-block">
          <div class="code-header">
            <span class="code-dot red"></span>
            <span class="code-dot yellow"></span>
            <span class="code-dot green"></span>
            <span class="code-filename">studio.config.ts</span>
          </div>
          <pre><span class="t-mute">// what we changed about design</span>
<span class="t-rem">- mediocre: true,</span>
<span class="t-add">+ crafted:  true,</span>

<span class="t-rem">- shipped_fast: "maybe",</span>
<span class="t-add">+ shipped_right: "always",</span>

<span class="t-key">const</span> studio = {
  <span class="t-key">name</span>: <span class="t-str">"Build.diff"</span>,
  <span class="t-key">founded</span>: <span class="t-num">2025</span>,
<span class="t-add">+ open_for_clients: <span class="t-str">"soon"</span>,</span>
}</pre>
        </div>
      </div>
    </div>

    <!-- Ticker -->
    <div class="ticker-wrap">
      <div class="ticker-track">
        <!-- ✏️ Edit ticker items (duplicate the set twice for seamless loop) -->
        <div class="ticker-item"><span class="dot"></span>Product Design</div>
        <div class="ticker-item"><span class="dot"></span>Brand Identity</div>
        <div class="ticker-item"><span class="dot"></span>Web Development</div>
        <div class="ticker-item"><span class="dot"></span>Motion Design</div>
        <div class="ticker-item"><span class="dot"></span>Design Systems</div>
        <div class="ticker-item"><span class="dot"></span>UX Strategy</div>
        <div class="ticker-item"><span class="dot"></span>Interaction Design</div>
        <!-- duplicate for seamless -->
        <div class="ticker-item"><span class="dot"></span>Product Design</div>
        <div class="ticker-item"><span class="dot"></span>Brand Identity</div>
        <div class="ticker-item"><span class="dot"></span>Web Development</div>
        <div class="ticker-item"><span class="dot"></span>Motion Design</div>
        <div class="ticker-item"><span class="dot"></span>Design Systems</div>
        <div class="ticker-item"><span class="dot"></span>UX Strategy</div>
        <div class="ticker-item"><span class="dot"></span>Interaction Design</div>
      </div>
    </div>

    <!-- ══════════════════ WHAT WE DO ══════════════════ -->
    <section class="reveal">
      <div class="section-tag">What we do</div>
      <!-- ✏️ Edit section headline -->
      <h2>Design that diffs<br/>from the rest.</h2>
      <p class="section-sub">
        We partner with founders, startups, and brands to craft digital experiences that are precise, intentional, and unforgettable.
      </p>

      <div class="services-grid">
        <!-- ✏️ Edit service cards here — icon SVGs can be swapped from heroicons.com or similar -->
        <div class="service-card">
          <span class="service-num">01</span>
          <div class="service-icon">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8">
              <rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/>
              <rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/>
            </svg>
          </div>
          <h3>Product Design</h3>
          <p class="service-desc">End-to-end product experiences — from early wireframes to pixel-perfect, shipped UI systems your team can scale.</p>
        </div>
        <div class="service-card">
          <span class="service-num">02</span>
          <div class="service-icon">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8">
              <circle cx="12" cy="12" r="3"/><path d="M12 2v2m0 16v2M2 12h2m16 0h2"/>
              <path d="M4.93 4.93l1.41 1.41m11.32 11.32 1.41 1.41M4.93 19.07l1.41-1.41m11.32-11.32 1.41-1.41"/>
            </svg>
          </div>
          <h3>Brand & Identity</h3>
          <p class="service-desc">Visual systems that hold up — logos, typography, color, motion, and a brand language that actually communicates.</p>
        </div>
        <div class="service-card">
          <span class="service-num">03</span>
          <div class="service-icon">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8">
              <polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/>
            </svg>
          </div>
          <h3>Web Development</h3>
          <p class="service-desc">Design implemented faithfully — performant, accessible, and crafted with the same intent as the original designs.</p>
        </div>
        <div class="service-card">
          <span class="service-num">04</span>
          <div class="service-icon">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8">
              <path d="M5 3l14 9-14 9V3z"/>
            </svg>
          </div>
          <h3>Motion & Animation</h3>
          <p class="service-desc">From UI micro-interactions to full brand motion systems — movement that adds meaning, not just noise.</p>
        </div>
      </div>
    </section>

    <hr class="divider"/>

    <!-- ══════════════════ PROCESS ══════════════════ -->
    <section class="reveal">
      <div class="section-tag">How we work</div>
      <h2>Clear process.<br/>No guessing.</h2>
      <p class="section-sub">Every engagement follows a proven structure — so there are no surprises, only results.</p>

      <div class="process-list">
        <!-- ✏️ Edit process steps here -->
        <div class="process-item">
          <div class="process-num">01</div>
          <div class="process-content">
            <h3>Discovery</h3>
            <p>We start by understanding your users, your goals, and the gaps in your current experience. No assumptions — just sharp questions and careful listening.</p>
          </div>
        </div>
        <div class="process-item">
          <div class="process-num">02</div>
          <div class="process-content">
            <h3>Define & Design</h3>
            <p>We synthesize findings into a clear direction, then design it — systematically. Every decision has a reason you'll be able to explain to stakeholders.</p>
          </div>
        </div>
        <div class="process-item">
          <div class="process-num">03</div>
          <div class="process-content">
            <h3>Build & Implement</h3>
            <p>Handoffs are where design dies. We build alongside your team or own it entirely — ensuring designs survive contact with real code.</p>
          </div>
        </div>
        <div class="process-item">
          <div class="process-num">04</div>
          <div class="process-content">
            <h3>Iterate & Ship</h3>
            <p>We ship, learn, and improve. Our relationships don't end at launch — we stay in the loop to make sure things actually work in the wild.</p>
          </div>
        </div>
      </div>
    </section>

    <hr class="divider"/>

    <!-- ══════════════════ TEAM ══════════════════ -->
    <section class="reveal">
      <div class="section-tag">The team</div>
      <h2>Built by designers<br/>who code.</h2>
      <p class="section-sub">We're a small team with strong opinions and the skill to back them up.</p>

      <div class="team-grid">
        <!-- ✏️ Edit team members here — replace initials, names, and roles -->
        <div class="team-card">
          <div class="avatar">A</div>
          <div class="team-name">Founder Name</div>
          <div class="team-role">Design Lead</div>
        </div>
        <div class="team-card">
          <div class="avatar">B</div>
          <div class="team-name">Founder Name</div>
          <div class="team-role">Engineering Lead</div>
        </div>
        <div class="team-card">
          <div class="avatar">C</div>
          <div class="team-name">Founder Name</div>
          <div class="team-role">Strategy & Brand</div>
        </div>
      </div>
    </section>

    <!-- ══════════════════ BOTTOM CTA ══════════════════ -->
    <div class="cta-section reveal">
      <div class="cta-box">
        <!-- ✏️ Edit CTA copy here -->
        <h2>Ready to build<br/>something different?</h2>
        <p>We're taking on our first cohort of clients. Spots are limited. Get in early.</p>
        <div class="cta-form" id="cta-form-wrap">
          <input type="email" id="cta-email" placeholder="your@email.com"/>
          <button class="btn-join" onclick="handleJoin('cta')">
            Get Early Access
            <svg width="14" height="14" viewBox="0 0 16 16" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round">
              <path d="M3 8h10M9 4l4 4-4 4"/>
            </svg>
          </button>
        </div>
        <div class="success-msg" id="cta-success" style="justify-content:center; margin-top:16px;">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none" stroke="currentColor" stroke-width="2">
            <circle cx="9" cy="9" r="8"/><path d="M5.5 9l2.5 2.5 4.5-4.5"/>
          </svg>
          You're in! We'll reach out when we're ready.
        </div>
      </div>
    </div>
  </div>

  <!-- ══════════════════ FOOTER ══════════════════ -->
  <footer>
    <div class="wrapper">
      <div class="footer-inner">
        <!-- ✏️ Edit footer copy & links -->
        <span class="footer-copy">© 2025 Build.diff. All rights reserved.</span>
        <div class="footer-links">
          <a href="mailto:hello@builddiff.com">hello@builddiff.com</a>
          <a href="#">Twitter</a>
          <a href="#">LinkedIn</a>
          <a href="#">Dribbble</a>
        </div>
      </div>
    </div>
  </footer>

  <script>
    /* ══════════════════════════════════════════
       FORM HANDLER
       ✏️ Replace the TODO comment with your
       actual API call (Mailchimp, Airtable, etc.)
    ══════════════════════════════════════════ */
    function handleJoin(source) {
      if (source === 'hero') {
        const name  = document.getElementById('hero-name').value.trim();
        const email = document.getElementById('hero-email').value.trim();
        if (!email) { alert('Please enter your email address.'); return; }

        // TODO: POST to your backend / Mailchimp / Airtable / ConvertKit
        // fetch('/api/waitlist', { method: 'POST', body: JSON.stringify({ name, email }) });

        document.getElementById('hero-form-wrap').style.display = 'none';
        document.getElementById('hero-success').classList.add('show');
      }

      if (source === 'cta') {
        const email = document.getElementById('cta-email').value.trim();
        if (!email) { alert('Please enter your email address.'); return; }

        // TODO: POST to your backend
        document.getElementById('cta-form-wrap').style.display = 'none';
        document.getElementById('cta-success').classList.add('show');
      }
    }

    /* ══════════════════════════════════════════
       SCROLL REVEAL
    ══════════════════════════════════════════ */
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.classList.add('visible');
          observer.unobserve(e.target);
        }
      });
    }, { threshold: 0.08 });

    document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
  </script>
</body>
</html>
