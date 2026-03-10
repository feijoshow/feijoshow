<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Feijo · GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet" />
<style>
  :root {
    --bg: #0d1117;
    --surface: #161b22;
    --surface2: #1c2333;
    --border: #21262d;
    --accent: #2A6592;
    --accent2: #58a6ff;
    --accent3: #3fb950;
    --text: #e6edf3;
    --muted: #7d8590;
    --red: #f85149;
    --orange: #d29922;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    padding: 40px 20px;
    overflow-x: hidden;
  }

  /* Animated grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(42,101,146,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(42,101,146,0.04) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .wrapper {
    max-width: 860px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
  }

  /* ── HERO ── */
  .hero {
    text-align: center;
    padding: 60px 20px 48px;
    animation: fadeUp 0.7s ease both;
  }

  .hero-eyebrow {
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent2);
    margin-bottom: 16px;
    opacity: 0;
    animation: fadeUp 0.6s 0.1s ease forwards;
  }

  .hero h1 {
    font-size: clamp(36px, 6vw, 64px);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -1px;
    margin-bottom: 12px;
    opacity: 0;
    animation: fadeUp 0.6s 0.2s ease forwards;
  }

  .hero h1 span { color: var(--accent2); }

  .hero-sub {
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    color: var(--muted);
    margin-bottom: 28px;
    opacity: 0;
    animation: fadeUp 0.6s 0.3s ease forwards;
  }

  .hero-sub b { color: var(--accent3); }

  .badges {
    display: flex;
    gap: 10px;
    justify-content: center;
    flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.6s 0.4s ease forwards;
  }

  .badge {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    padding: 6px 14px;
    border-radius: 4px;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--muted);
    text-decoration: none;
    transition: all 0.2s;
    cursor: pointer;
  }

  .badge:hover { border-color: var(--accent2); color: var(--accent2); }
  .badge.loc { border-color: var(--accent); color: var(--accent2); }
  .badge.open { border-color: var(--accent3); color: var(--accent3); }

  /* ── DIVIDER ── */
  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
    margin: 8px 0 40px;
  }

  /* ── SECTION ── */
  .section {
    margin-bottom: 48px;
    opacity: 0;
    transform: translateY(20px);
    animation: fadeUp 0.6s ease forwards;
  }

  .section:nth-child(2) { animation-delay: 0.5s; }
  .section:nth-child(3) { animation-delay: 0.6s; }
  .section:nth-child(4) { animation-delay: 0.7s; }
  .section:nth-child(5) { animation-delay: 0.8s; }
  .section:nth-child(6) { animation-delay: 0.9s; }
  .section:nth-child(7) { animation-delay: 1.0s; }
  .section:nth-child(8) { animation-delay: 1.1s; }

  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--accent2);
    margin-bottom: 18px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ── ABOUT ── */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .about-item {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 14px 18px;
    font-size: 14px;
    color: var(--text);
    display: flex;
    align-items: flex-start;
    gap: 10px;
    transition: border-color 0.2s;
  }

  .about-item:hover { border-color: var(--accent); }
  .about-item .icon { font-size: 18px; flex-shrink: 0; margin-top: 1px; }
  .about-item .label { color: var(--muted); font-size: 11px; font-family: 'Space Mono', monospace; margin-bottom: 2px; }

  .quote-block {
    margin-top: 16px;
    padding: 16px 20px;
    border-left: 3px solid var(--accent);
    background: var(--surface);
    border-radius: 0 8px 8px 0;
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    color: var(--muted);
    font-style: italic;
  }

  /* ── STACK ── */
  .stack-groups {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .stack-row {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 16px 20px;
  }

  .stack-row-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 12px;
  }

  .tech-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .pill {
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    padding: 5px 12px;
    border-radius: 4px;
    background: var(--surface2);
    border: 1px solid var(--border);
    color: var(--text);
    transition: all 0.2s;
  }

  .pill:hover { border-color: var(--accent2); color: var(--accent2); transform: translateY(-1px); }
  .pill.fe { border-color: rgba(88,166,255,0.3); }
  .pill.be { border-color: rgba(63,185,80,0.3); }
  .pill.tool { border-color: rgba(210,153,34,0.3); }

  /* ── PROJECTS TABLE ── */
  .projects {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 18px 22px;
    display: grid;
    grid-template-columns: 1fr auto;
    align-items: center;
    gap: 16px;
    transition: border-color 0.2s, transform 0.2s;
  }

  .project-card:hover { border-color: var(--accent2); transform: translateX(4px); }
  .project-name { font-size: 16px; font-weight: 600; margin-bottom: 4px; }
  .project-stack { font-family: 'Space Mono', monospace; font-size: 11px; color: var(--muted); }
  .status-badge {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    padding: 4px 10px;
    border-radius: 20px;
    white-space: nowrap;
  }
  .status-active { background: rgba(63,185,80,0.15); color: var(--accent3); border: 1px solid rgba(63,185,80,0.3); }
  .status-plan { background: rgba(210,153,34,0.15); color: var(--orange); border: 1px solid rgba(210,153,34,0.3); }

  /* ── GOALS ── */
  .goals-list { display: flex; flex-direction: column; gap: 10px; }

  .goal-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 12px 16px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    font-size: 14px;
    transition: border-color 0.2s;
  }

  .goal-item:hover { border-color: var(--accent); }

  .goal-check {
    width: 18px;
    height: 18px;
    border: 2px solid var(--border);
    border-radius: 4px;
    flex-shrink: 0;
  }

  /* ── STATS ── */
  .stats-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 20px;
    text-align: center;
    transition: border-color 0.2s;
  }

  .stat-card:hover { border-color: var(--accent2); }
  .stat-number { font-size: 32px; font-weight: 800; color: var(--accent2); }
  .stat-label { font-family: 'Space Mono', monospace; font-size: 11px; color: var(--muted); margin-top: 4px; text-transform: uppercase; letter-spacing: 1px; }

  .github-img-row {
    display: flex;
    flex-direction: column;
    gap: 12px;
    align-items: center;
  }

  .github-img-row img { border-radius: 8px; max-width: 100%; border: 1px solid var(--border); }

  /* ── ANIME ── */
  .anime-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .anime-pill {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    padding: 6px 14px;
    border-radius: 4px;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--muted);
    transition: all 0.2s;
  }

  .anime-pill:hover { transform: translateY(-2px); }
  .ap-blue:hover { border-color: #0069b4; color: #58a6ff; }
  .ap-red:hover { border-color: #CC0000; color: #f85149; }
  .ap-dark:hover { border-color: #555; color: var(--text); }
  .ap-brown:hover { border-color: #8B5E3C; color: #d4a76a; }
  .ap-purple:hover { border-color: #6B21A8; color: #c084fc; }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    padding: 48px 20px 20px;
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    color: var(--muted);
    line-height: 1.8;
  }

  .footer-tagline {
    font-size: 14px;
    font-style: italic;
    color: var(--text);
    margin-bottom: 10px;
    font-family: 'Syne', sans-serif;
  }

  .footer-fuel { letter-spacing: 1px; margin-top: 6px; }
  .footer-fuel span { color: var(--accent2); }

  .footer img {
    margin-top: 24px;
    border-radius: 8px;
    opacity: 0.85;
  }

  /* ── ANIMATION ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @media (max-width: 600px) {
    .about-grid { grid-template-columns: 1fr; }
    .stats-grid { grid-template-columns: 1fr; }
    .project-card { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>
<div class="wrapper">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-eyebrow">feijoshow · github profile</div>
    <h1>Feijo <span>·</span><br>Fullstack Engineer</h1>
    <div class="hero-sub">Frontend Alchemist 🧪 · API Architect 🔧 · <b>Anime-Powered Builder</b> 🎌</div>
    <div class="badges">
      <span class="badge loc">📍 Namibia</span>
      <span class="badge open">● Open to Collabs</span>
      <a class="badge" href="mailto:cristianofeijo@gmail.com">✉ cristianofeijo@gmail.com</a>
    </div>
  </div>

  <div class="divider"></div>

  <!-- ABOUT -->
  <div class="section">
    <div class="section-label">About Me</div>
    <div class="about-grid">
      <div class="about-item">
        <span class="icon">🖥️</span>
        <div>
          <div class="label">Frontend</div>
          React, clean responsive interfaces, smooth UX
        </div>
      </div>
      <div class="about-item">
        <span class="icon">⚙️</span>
        <div>
          <div class="label">Backend</div>
          Node.js, Express, REST APIs, GraphQL
        </div>
      </div>
      <div class="about-item">
        <span class="icon">🗄️</span>
        <div>
          <div class="label">Database</div>
          PostgreSQL, MySQL
        </div>
      </div>
      <div class="about-item">
        <span class="icon">🔐</span>
        <div>
          <div class="label">Principles</div>
          Auth, security, and systems that scale
        </div>
      </div>
    </div>
    <div class="quote-block">"Code is like chakra — invisible, but it fuels everything you see." ✨</div>
  </div>

  <!-- STACK -->
  <div class="section">
    <div class="section-label">Tech Stack</div>
    <div class="stack-groups">
      <div class="stack-row">
        <div class="stack-row-label">Frontend</div>
        <div class="tech-pills">
          <span class="pill fe">HTML5</span>
          <span class="pill fe">CSS3</span>
          <span class="pill fe">JavaScript</span>
          <span class="pill fe">TypeScript</span>
          <span class="pill fe">React</span>
        </div>
      </div>
      <div class="stack-row">
        <div class="stack-row-label">Backend & Database</div>
        <div class="tech-pills">
          <span class="pill be">Node.js</span>
          <span class="pill be">Express</span>
          <span class="pill be">PostgreSQL</span>
          <span class="pill be">MySQL</span>
          <span class="pill be">GraphQL</span>
          <span class="pill be">REST APIs</span>
        </div>
      </div>
      <div class="stack-row">
        <div class="stack-row-label">Tools & Deployment</div>
        <div class="tech-pills">
          <span class="pill tool">Git</span>
          <span class="pill tool">GitHub</span>
          <span class="pill tool">VS Code</span>
          <span class="pill tool">Vercel</span>
          <span class="pill tool">Railway</span>
          <span class="pill tool">Figma</span>
        </div>
      </div>
    </div>
  </div>

  <!-- PROJECTS -->
  <div class="section">
    <div class="section-label">Currently Building</div>
    <div class="projects">
      <div class="project-card">
        <div>
          <div class="project-name">🌾 AGRILINK</div>
          <div class="project-stack">React · Node.js · PostgreSQL · REST API</div>
        </div>
        <span class="status-badge status-active">🚧 Active</span>
      </div>
      <div class="project-card">
        <div>
          <div class="project-name">🎨 Agritech UI Kit</div>
          <div class="project-stack">React · TypeScript · Open Source</div>
        </div>
        <span class="status-badge status-plan">📐 Planning</span>
      </div>
    </div>
  </div>

  <!-- GOALS -->
  <div class="section">
    <div class="section-label">2026 Goals</div>
    <div class="goals-list">
      <div class="goal-item"><div class="goal-check"></div> Ship the next major AGRILINK milestone</div>
      <div class="goal-item"><div class="goal-check"></div> Go deeper on auth, security & backend architecture</div>
      <div class="goal-item"><div class="goal-check"></div> Open-source a UI component kit</div>
      <div class="goal-item"><div class="goal-check"></div> Connect with more African developer communities</div>
    </div>
  </div>

  <!-- STATS -->
  <div class="section">
    <div class="section-label">GitHub Stats</div>
    <div class="github-img-row">
      <img src="https://streak-stats.demolab.com?user=feijoshow&theme=tokyonight&hide_border=true" alt="GitHub streak" />
      <img src="https://github-readme-stats.vercel.app/api?username=feijoshow&show_icons=true&theme=tokyonight&hide_border=true&rank_icon=github" alt="GitHub stats" />
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=feijoshow&layout=compact&theme=tokyonight&hide_border=true" alt="Top languages" />
    </div>
    <div style="text-align:center;margin-top:14px;">
      <img src="https://komarev.com/ghpvc/?username=feijoshow&style=flat-square&color=2A6592" alt="Profile views" />
    </div>
  </div>

  <!-- ANIME -->
  <div class="section">
    <div class="section-label">Anime Corner 🎌</div>
    <div class="anime-pills">
      <span class="anime-pill ap-blue">🍥 Naruto · Rasengan Dev</span>
      <span class="anime-pill ap-red">🔥 Dragon Ball · Over 9000 Commits</span>
      <span class="anime-pill ap-dark">🏴‍☠️ One Piece · Pirate Coder</span>
      <span class="anime-pill ap-brown">💥 Attack on Titan · Colossal Builder</span>
      <span class="anime-pill ap-purple">⚔️ Demon Slayer · Breathing in Code</span>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="divider"></div>
  <div class="footer">
    <div class="footer-tagline">May your builds stay green, your APIs stay fast,<br>and your animations flow like Studio Ghibli skies. 🌸</div>
    <div class="footer-fuel">Fueled by coffee ☕ · <span>Powered by anime ⚔️</span> · Shipped with code 💻</div>
    <div><br><img src="https://media.giphy.com/media/13HgwGsXF0aiGY/giphy.gif" width="240" alt="Anime coding" /></div>
  </div>

</div>
</body>
</html>
