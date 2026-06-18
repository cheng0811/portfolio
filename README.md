[index.html](https://github.com/user-attachments/files/29077689/index.html)
# portfolio<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Andy Tai | 戴安呈</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg:        #090e1c;
      --bg2:       #0e1428;
      --surface:   #131a30;
      --border:    #1e2a45;
      --cyan:      #00d4ff;
      --cyan-dim:  #0099bb;
      --text:      #d4dff5;
      --muted:     #5a6a8a;
      --accent:    #7c6af7;
      --green:     #00e5a0;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'Inter', sans-serif;
      font-size: 16px;
      line-height: 1.7;
      overflow-x: hidden;
    }

    /* ── NOISE OVERLAY ─────────────────────────────────── */
    body::before {
      content: '';
      position: fixed; inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");
      opacity: 0.025;
      pointer-events: none;
      z-index: 0;
    }

    /* ── NAV ──────────────────────────────────────────── */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 1.1rem 4vw;
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      background: rgba(9,14,28,0.75);
      border-bottom: 1px solid var(--border);
    }
    .nav-logo {
      font-family: 'JetBrains Mono', monospace;
      font-weight: 700;
      font-size: 1rem;
      color: var(--cyan);
      text-decoration: none;
      letter-spacing: 0.05em;
    }
    .nav-logo span { color: var(--muted); }
    .nav-links { display: flex; gap: 2rem; list-style: none; }
    .nav-links a {
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.78rem;
      color: var(--muted);
      text-decoration: none;
      letter-spacing: 0.08em;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--cyan); }

    /* ── HERO ─────────────────────────────────────────── */
    #hero {
      min-height: 100vh;
      display: flex; flex-direction: column; justify-content: center;
      padding: 8rem 4vw 4rem;
      position: relative;
    }

    .hero-grid-bg {
      position: absolute; inset: 0;
      background-image:
        linear-gradient(rgba(0,212,255,0.04) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0,212,255,0.04) 1px, transparent 1px);
      background-size: 60px 60px;
      mask-image: radial-gradient(ellipse 80% 70% at 50% 40%, black 0%, transparent 100%);
    }

    .hero-eyebrow {
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.78rem;
      color: var(--cyan);
      letter-spacing: 0.2em;
      margin-bottom: 1.5rem;
      display: flex; align-items: center; gap: 0.75rem;
    }
    .hero-eyebrow::before {
      content: '';
      display: block; width: 2rem; height: 1px;
      background: var(--cyan);
    }

    .hero-name {
      font-family: 'JetBrains Mono', monospace;
      font-size: clamp(2.8rem, 8vw, 6rem);
      font-weight: 700;
      line-height: 1.05;
      color: #fff;
      margin-bottom: 0.5rem;
    }
    .hero-name .accent { color: var(--cyan); }

    .hero-role {
      font-family: 'JetBrains Mono', monospace;
      font-size: clamp(1rem, 2.5vw, 1.4rem);
      color: var(--muted);
      margin-bottom: 2rem;
      min-height: 2em;
    }
    .cursor {
      display: inline-block;
      width: 2px; height: 1.1em;
      background: var(--cyan);
      margin-left: 2px;
      vertical-align: text-bottom;
      animation: blink 1s step-end infinite;
    }
    @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

    .hero-desc {
      max-width: 540px;
      color: var(--muted);
      font-size: 1.05rem;
      margin-bottom: 3rem;
      line-height: 1.8;
    }

    .hero-cta {
      display: flex; gap: 1rem; flex-wrap: wrap;
    }
    .btn {
      display: inline-flex; align-items: center; gap: 0.5rem;
      padding: 0.75rem 1.6rem;
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.82rem;
      letter-spacing: 0.05em;
      border-radius: 4px;
      text-decoration: none;
      transition: all 0.2s;
      cursor: pointer;
    }
    .btn-primary {
      background: var(--cyan);
      color: var(--bg);
      border: none;
      font-weight: 700;
    }
    .btn-primary:hover { background: #33ddff; transform: translateY(-2px); box-shadow: 0 6px 24px rgba(0,212,255,0.25); }
    .btn-ghost {
      background: transparent;
      color: var(--text);
      border: 1px solid var(--border);
    }
    .btn-ghost:hover { border-color: var(--cyan); color: var(--cyan); transform: translateY(-2px); }

    .hero-stats {
      position: absolute; right: 6vw; bottom: 8vh;
      display: flex; gap: 3rem;
    }
    .stat { text-align: right; }
    .stat-num {
      font-family: 'JetBrains Mono', monospace;
      font-size: 2rem; font-weight: 700;
      color: #fff;
    }
    .stat-num .unit { font-size: 1rem; color: var(--cyan); }
    .stat-label {
      font-size: 0.75rem; color: var(--muted);
      letter-spacing: 0.1em;
    }

    /* ── SECTIONS ─────────────────────────────────────── */
    section {
      padding: 6rem 4vw;
      max-width: 1100px;
      margin: 0 auto;
    }

    .section-label {
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.72rem;
      letter-spacing: 0.25em;
      color: var(--cyan);
      margin-bottom: 0.75rem;
    }
    .section-title {
      font-family: 'JetBrains Mono', monospace;
      font-size: clamp(1.6rem, 4vw, 2.4rem);
      font-weight: 700;
      color: #fff;
      margin-bottom: 3rem;
    }
    .section-title .dim { color: var(--muted); }

    /* ── ABOUT ────────────────────────────────────────── */
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 4rem;
      align-items: start;
    }
    .about-text p { color: var(--muted); margin-bottom: 1.2rem; line-height: 1.85; }
    .about-text p strong { color: var(--text); }

    .about-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 1.8rem;
    }
    .about-card-title {
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.75rem;
      letter-spacing: 0.15em;
      color: var(--cyan);
      margin-bottom: 1.2rem;
    }
    .info-row {
      display: flex; justify-content: space-between; align-items: center;
      padding: 0.6rem 0;
      border-bottom: 1px solid var(--border);
      font-size: 0.9rem;
    }
    .info-row:last-child { border-bottom: none; }
    .info-key { color: var(--muted); font-size: 0.82rem; }
    .info-val { color: var(--text); font-weight: 500; }

    /* ── SKILLS ───────────────────────────────────────── */
    #skills { background: var(--bg2); max-width: 100%; padding: 6rem 0; }
    #skills > .inner { max-width: 1100px; margin: 0 auto; padding: 0 4vw; }

    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.5rem;
    }
    .skill-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 1.6rem;
      transition: border-color 0.25s, transform 0.25s;
    }
    .skill-card:hover { border-color: var(--cyan); transform: translateY(-4px); }
    .skill-icon { font-size: 1.8rem; margin-bottom: 0.75rem; }
    .skill-cat {
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.72rem;
      letter-spacing: 0.18em;
      color: var(--cyan);
      margin-bottom: 0.4rem;
    }
    .skill-name {
      font-size: 1rem; font-weight: 600;
      color: #fff; margin-bottom: 0.9rem;
    }
    .tags { display: flex; flex-wrap: wrap; gap: 0.4rem; }
    .tag {
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.72rem;
      padding: 0.2rem 0.55rem;
      border-radius: 3px;
      background: rgba(0,212,255,0.08);
      color: var(--cyan);
      border: 1px solid rgba(0,212,255,0.2);
    }

    /* ── PROJECTS ─────────────────────────────────────── */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
      gap: 1.5rem;
    }
    .project-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 2rem;
      position: relative; overflow: hidden;
      transition: border-color 0.25s, transform 0.25s;
    }
    .project-card::before {
      content: '';
      position: absolute; top: 0; left: 0; right: 0; height: 2px;
      background: linear-gradient(90deg, var(--cyan), var(--accent));
      transform: scaleX(0); transform-origin: left;
      transition: transform 0.35s ease;
    }
    .project-card:hover { border-color: rgba(0,212,255,0.4); transform: translateY(-4px); }
    .project-card:hover::before { transform: scaleX(1); }

    .project-num {
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.72rem;
      color: var(--muted);
      margin-bottom: 1rem;
    }
    .project-title {
      font-size: 1.1rem; font-weight: 600;
      color: #fff; margin-bottom: 0.6rem;
    }
    .project-desc { font-size: 0.9rem; color: var(--muted); margin-bottom: 1.2rem; line-height: 1.7; }
    .project-tags { display: flex; flex-wrap: wrap; gap: 0.35rem; }
    .project-tag {
      font-size: 0.72rem;
      padding: 0.15rem 0.5rem;
      border-radius: 3px;
      background: rgba(124,106,247,0.12);
      color: var(--accent);
      border: 1px solid rgba(124,106,247,0.25);
    }

    /* ── TERMINAL ─────────────────────────────────────── */
    .terminal {
      background: #070b15;
      border: 1px solid var(--border);
      border-radius: 8px;
      overflow: hidden;
      margin-top: 2rem;
    }
    .terminal-bar {
      display: flex; align-items: center; gap: 0.4rem;
      padding: 0.7rem 1rem;
      background: var(--surface);
      border-bottom: 1px solid var(--border);
    }
    .dot { width: 10px; height: 10px; border-radius: 50%; }
    .dot-red { background: #ff5f56; }
    .dot-yellow { background: #ffbd2e; }
    .dot-green { background: #27c93f; }
    .terminal-title {
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.72rem; color: var(--muted);
      margin-left: auto; margin-right: auto;
    }
    .terminal-body {
      padding: 1.4rem 1.5rem;
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.82rem;
      line-height: 1.9;
    }
    .t-prompt { color: var(--green); }
    .t-cmd { color: var(--text); }
    .t-out { color: var(--muted); }
    .t-key { color: var(--cyan); }
    .t-val { color: var(--accent); }

    /* ── CONTACT ──────────────────────────────────────── */
    #contact { text-align: center; }
    .contact-email {
      display: inline-block;
      font-family: 'JetBrains Mono', monospace;
      font-size: clamp(1.2rem, 3vw, 1.8rem);
      color: var(--cyan);
      text-decoration: none;
      border-bottom: 2px solid transparent;
      transition: border-color 0.2s;
      margin: 1.5rem 0 2.5rem;
    }
    .contact-email:hover { border-color: var(--cyan); }
    .social-links { display: flex; justify-content: center; gap: 1.2rem; flex-wrap: wrap; }
    .social-link {
      display: inline-flex; align-items: center; gap: 0.4rem;
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.78rem;
      color: var(--muted);
      text-decoration: none;
      padding: 0.5rem 1rem;
      border: 1px solid var(--border);
      border-radius: 4px;
      transition: all 0.2s;
    }
    .social-link:hover { color: var(--cyan); border-color: var(--cyan); }

    /* ── FOOTER ───────────────────────────────────────── */
    footer {
      border-top: 1px solid var(--border);
      padding: 2rem 4vw;
      display: flex; justify-content: space-between; align-items: center;
      flex-wrap: wrap; gap: 1rem;
    }
    .footer-copy {
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.72rem; color: var(--muted);
    }
    .footer-badge {
      font-family: 'JetBrains Mono', monospace;
      font-size: 0.72rem; color: var(--muted);
    }
    .footer-badge span { color: var(--cyan); }

    /* ── REVEAL ANIMATION ─────────────────────────────── */
    .reveal {
      opacity: 0;
      transform: translateY(28px);
      transition: opacity 0.65s ease, transform 0.65s ease;
    }
    .reveal.visible { opacity: 1; transform: none; }

    /* ── MOBILE ───────────────────────────────────────── */
    @media (max-width: 768px) {
      .about-grid { grid-template-columns: 1fr; gap: 2rem; }
      .hero-stats { position: static; margin-top: 3rem; justify-content: flex-start; gap: 2rem; }
      .nav-links { display: none; }
    }

    @media (prefers-reduced-motion: reduce) {
      .reveal { opacity: 1; transform: none; transition: none; }
      .cursor { animation: none; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <a class="nav-logo" href="#hero">andy<span>.dev</span></a>
    <ul class="nav-links">
      <li><a href="#about">about</a></li>
      <li><a href="#skills">skills</a></li>
      <li><a href="#projects">projects</a></li>
      <li><a href="#contact">contact</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <section id="hero">
    <div class="hero-grid-bg"></div>
    <div class="hero-eyebrow">PORTFOLIO · 2025</div>
    <h1 class="hero-name">
      Andy <span class="accent">Tai</span><br>戴安呈
    </h1>
    <p class="hero-role" id="typewriter"><span class="cursor"></span></p>
    <p class="hero-desc">
      亞洲大學 資訊工程系大二生，專注於 Web 開發與密碼學研究，
      同時對長期投資與金融市場保持濃厚興趣。
    </p>
    <div class="hero-cta">
      <a class="btn btn-primary" href="#projects">查看專案</a>
      <a class="btn btn-ghost" href="#contact">聯絡我</a>
    </div>
    <div class="hero-stats">
      <div class="stat">
        <div class="stat-num">2<span class="unit">nd</span></div>
        <div class="stat-label">YEAR · AU</div>
      </div>
      <div class="stat">
        <div class="stat-num">4<span class="unit">+</span></div>
        <div class="stat-label">PROJECTS</div>
      </div>
      <div class="stat">
        <div class="stat-num">∞</div>
        <div class="stat-label">CURIOSITY</div>
      </div>
    </div>
  </section>

  <!-- ABOUT -->
  <section id="about">
    <div class="reveal">
      <div class="section-label">// ABOUT ME</div>
      <h2 class="section-title">關於我 <span class="dim">·</span> About</h2>
    </div>
    <div class="about-grid">
      <div class="about-text reveal">
        <p>
          我是 <strong>戴安呈（Andy）</strong>，就讀於亞洲大學資訊工程系，
          學號 113021155。目前主修 Web 開發、演算法、資料結構與密碼學。
        </p>
        <p>
          對 <strong>前後端開發</strong> 充滿熱情，喜歡將複雜問題化繁為簡。
          在密碼學領域特別研究橢圓曲線密碼學（ECC）與 ECDH 金鑰交換協議。
        </p>
        <p>
          課餘同時是一位 <strong>長期投資者</strong>，
          關注台灣上市股票與 ETF，以定期定額方式累積資產。
          也在餐飲業兼職，磨練溝通與服務能力。
        </p>

        <!-- Terminal Easter Egg -->
        <div class="terminal" style="margin-top:2rem;">
          <div class="terminal-bar">
            <span class="dot dot-red"></span>
            <span class="dot dot-yellow"></span>
            <span class="dot dot-green"></span>
            <span class="terminal-title">andy@au ~ bash</span>
          </div>
          <div class="terminal-body" id="terminal-out">
            <div><span class="t-prompt">andy@au:~$</span> <span class="t-cmd">cat about.json</span></div>
          </div>
        </div>
      </div>

      <div class="about-card reveal">
        <div class="about-card-title">// PROFILE</div>
        <div class="info-row"><span class="info-key">姓名</span><span class="info-val">戴安呈 Andy</span></div>
        <div class="info-row"><span class="info-key">學號</span><span class="info-val">113021155</span></div>
        <div class="info-row"><span class="info-key">就讀</span><span class="info-val">亞洲大學 CSE</span></div>
        <div class="info-row"><span class="info-key">年級</span><span class="info-val">大二（2nd Year）</span></div>
        <div class="info-row"><span class="info-key">所在地</span><span class="info-val">台灣 台中</span></div>
        <div class="info-row"><span class="info-key">研究</span><span class="info-val">ECC · 密碼學</span></div>
        <div class="info-row"><span class="info-key">興趣</span><span class="info-val">投資 · Web Dev</span></div>
        <div class="info-row"><span class="info-key">狀態</span><span class="info-val" style="color:var(--green)">● 求職中</span></div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills" style="max-width:100%; padding: 6rem 0;">
    <div class="inner">
      <div class="reveal">
        <div class="section-label">// TECH STACK</div>
        <h2 class="section-title">技能 <span class="dim">·</span> Skills</h2>
      </div>
      <div class="skills-grid">
        <div class="skill-card reveal">
          <div class="skill-icon">🌐</div>
          <div class="skill-cat">FRONTEND</div>
          <div class="skill-name">Web 開發</div>
          <div class="tags">
            <span class="tag">HTML5</span><span class="tag">CSS3</span>
            <span class="tag">JavaScript</span><span class="tag">DOM</span>
            <span class="tag">LocalStorage</span><span class="tag">IndexedDB</span>
          </div>
        </div>
        <div class="skill-card reveal">
          <div class="skill-icon">🔐</div>
          <div class="skill-cat">CRYPTOGRAPHY</div>
          <div class="skill-name">密碼學</div>
          <div class="tags">
            <span class="tag">ECC</span><span class="tag">ECDH</span>
            <span class="tag">ECDSA</span><span class="tag">D-H</span>
            <span class="tag">Python</span><span class="tag">OpenSSL</span>
          </div>
        </div>
        <div class="skill-card reveal">
          <div class="skill-icon">⚡</div>
          <div class="skill-cat">ELECTRONICS</div>
          <div class="skill-name">電子電路</div>
          <div class="tags">
            <span class="tag">MOSFET</span><span class="tag">JFET</span>
            <span class="tag">Amplifier</span><span class="tag">DC Bias</span>
            <span class="tag">小信號分析</span>
          </div>
        </div>
        <div class="skill-card reveal">
          <div class="skill-icon">🧮</div>
          <div class="skill-cat">ALGORITHMS</div>
          <div class="skill-name">演算法與資料結構</div>
          <div class="tags">
            <span class="tag">Sorting</span><span class="tag">Dijkstra</span>
            <span class="tag">Floyd</span><span class="tag">Knapsack</span>
            <span class="tag">Binary Search</span>
          </div>
        </div>
        <div class="skill-card reveal">
          <div class="skill-icon">📈</div>
          <div class="skill-cat">FINANCE</div>
          <div class="skill-name">台股投資</div>
          <div class="tags">
            <span class="tag">ETF</span><span class="tag">定期定額</span>
            <span class="tag">零股交易</span><span class="tag">基本面分析</span>
          </div>
        </div>
        <div class="skill-card reveal">
          <div class="skill-icon">🛠️</div>
          <div class="skill-cat">TOOLS</div>
          <div class="skill-name">開發工具</div>
          <div class="tags">
            <span class="tag">Git</span><span class="tag">GitHub</span>
            <span class="tag">VS Code</span><span class="tag">Colab</span>
            <span class="tag">Linux</span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects">
    <div class="reveal">
      <div class="section-label">// SELECTED WORK</div>
      <h2 class="section-title">專案 <span class="dim">·</span> Projects</h2>
    </div>
    <div class="projects-grid">
      <div class="project-card reveal">
        <div class="project-num">01 · CRYPTOGRAPHY</div>
        <div class="project-title">ECDH 互動教學工具</div>
        <div class="project-desc">以 D3.js 視覺化橢圓曲線 Diffie-Hellman 金鑰交換流程，搭配逐步動畫呈現點乘運算，輔助密碼學課程教學。</div>
        <div class="project-tags">
          <span class="project-tag">JavaScript</span>
          <span class="project-tag">ECC</span>
          <span class="project-tag">D3.js</span>
          <span class="project-tag">密碼學</span>
        </div>
      </div>
      <div class="project-card reveal">
        <div class="project-num">02 · WEB DEV</div>
        <div class="project-title">Todo List with IndexedDB</div>
        <div class="project-desc">使用原生 JavaScript 建立的 Todo 應用，整合 IndexedDB 持久儲存、LocalStorage 偏好設定，支援離線使用。</div>
        <div class="project-tags">
          <span class="project-tag">JavaScript</span>
          <span class="project-tag">IndexedDB</span>
          <span class="project-tag">DOM API</span>
          <span class="project-tag">PWA</span>
        </div>
      </div>
      <div class="project-card reveal">
        <div class="project-num">03 · AI / FINANCE</div>
        <div class="project-title">台股預測工具（開發中）</div>
        <div class="project-desc">以 React 搭配 Anthropic API 分析台灣上市公司基本面資料，透過多輪對話架構取得 AI 分析建議。</div>
        <div class="project-tags">
          <span class="project-tag">React</span>
          <span class="project-tag">Anthropic API</span>
          <span class="project-tag">台股</span>
          <span class="project-tag">AI</span>
        </div>
      </div>
      <div class="project-card reveal">
        <div class="project-num">04 · CRYPTOGRAPHY</div>
        <div class="project-title">ECC / ECDSA Colab Notebook</div>
        <div class="project-desc">Google Colab 教學筆記本，比較 Python hashlib/ECDSA 函式庫與 OpenSSL 指令列工具的簽章與驗證流程。</div>
        <div class="project-tags">
          <span class="project-tag">Python</span>
          <span class="project-tag">ECDSA</span>
          <span class="project-tag">OpenSSL</span>
          <span class="project-tag">Google Colab</span>
        </div>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <div class="reveal">
      <div class="section-label">// GET IN TOUCH</div>
      <h2 class="section-title">聯絡 <span class="dim">·</span> Contact</h2>
      <p style="color:var(--muted); max-width:480px; margin: 0 auto 1.5rem;">
        歡迎有關實習、合作或任何技術討論的聯繫 🙌
      </p>
      <a class="contact-email" href="mailto:113021155@live.asia.edu.tw">
        113021155@live.asia.edu.tw
      </a>
      <div class="social-links">
        <a class="social-link" href="https://github.com/" target="_blank" rel="noopener">
          ⌨ GitHub
        </a>
        <a class="social-link" href="https://www.linkedin.com/" target="_blank" rel="noopener">
          💼 LinkedIn
        </a>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-copy">© 2025 Andy Tai 戴安呈 · 113021155</div>
    <div class="footer-badge">Built with <span>♥</span> + vanilla JS · Asia University CSE</div>
  </footer>

  <!-- ── JAVASCRIPT ──────────────────────────────────── -->
  <script>
    /* 1. Typewriter effect */
    const roles = [
      'CS & Engineering Student',
      '資訊工程系大二生',
      'Web Developer',
      'Cryptography Enthusiast',
      '長期投資者',
      'Problem Solver'
    ];
    let ri = 0, ci = 0, deleting = false;
    const el = document.getElementById('typewriter');

    function type() {
      const word = roles[ri];
      if (!deleting) {
        ci++;
        el.innerHTML = word.slice(0, ci) + '<span class="cursor"></span>';
        if (ci === word.length) {
          deleting = true;
          setTimeout(type, 1800);
          return;
        }
      } else {
        ci--;
        el.innerHTML = word.slice(0, ci) + '<span class="cursor"></span>';
        if (ci === 0) {
          deleting = false;
          ri = (ri + 1) % roles.length;
        }
      }
      setTimeout(type, deleting ? 55 : 95);
    }
    type();

    /* 2. Terminal print-out animation */
    const termOut = document.getElementById('terminal-out');
    const termLines = [
      '',
      '<span class="t-out">{</span>',
      '  <span class="t-key">"name"</span>: <span class="t-val">"戴安呈 Andy Tai"</span>,',
      '  <span class="t-key">"id"</span>: <span class="t-val">"113021155"</span>,',
      '  <span class="t-key">"school"</span>: <span class="t-val">"Asia University"</span>,',
      '  <span class="t-key">"major"</span>: <span class="t-val">"Computer Science & Engineering"</span>,',
      '  <span class="t-key">"year"</span>: <span class="t-val">2</span>,',
      '  <span class="t-key">"interests"</span>: [<span class="t-val">"Web Dev"</span>, <span class="t-val">"Cryptography"</span>, <span class="t-val">"Investing"</span>],',
      '  <span class="t-key">"status"</span>: <span class="t-val">"open to opportunities"</span>',
      '<span class="t-out">}</span>',
    ];
    let tl = 1;
    function printTermLine() {
      if (tl >= termLines.length) return;
      const div = document.createElement('div');
      div.innerHTML = '<span class="t-out">' + termLines[tl] + '</span>';
      termOut.appendChild(div);
      tl++;
      setTimeout(printTermLine, 110);
    }
    setTimeout(printTermLine, 800);

    /* 3. Scroll reveal */
    const revealEls = document.querySelectorAll('.reveal');
    const obs = new IntersectionObserver((entries) => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.classList.add('visible');
          obs.unobserve(e.target);
        }
      });
    }, { threshold: 0.12 });
    revealEls.forEach(el => obs.observe(el));

    /* 4. Stagger delays for grid children */
    document.querySelectorAll('.skills-grid .skill-card, .projects-grid .project-card').forEach((el, i) => {
      el.style.transitionDelay = `${(i % 3) * 0.1}s`;
    });

    /* 5. Active nav highlight */
    const sections = document.querySelectorAll('section[id]');
    const navLinks = document.querySelectorAll('.nav-links a');
    window.addEventListener('scroll', () => {
      let cur = '';
      sections.forEach(s => {
        if (window.scrollY >= s.offsetTop - 120) cur = s.id;
      });
      navLinks.forEach(a => {
        a.style.color = a.getAttribute('href') === '#' + cur
          ? 'var(--cyan)' : '';
      });
    }, { passive: true });
  </script>
</body>
</html>
