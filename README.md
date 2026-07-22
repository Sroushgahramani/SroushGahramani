<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>sroush@gahramani: ~</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700;800&display=swap');

    :root {
      --bg: #0a0a0f;
      --panel: #0d0d1a;
      --border: #1a1a3e;
      --key: #8fa8cf;
      --val: #d7dce6;
      --accent: #e0a458;
      --accent2: #5fb894;
      --muted: #4c5468;
      --heading: #eef1f7;
      
      /* Cyber colors */
      --cyber-green: #00ff41;
      --cyber-red: #ff0040;
      --cyber-purple: #b400ff;
      --cyber-blue: #00d4ff;
      --cyber-yellow: #ffea00;
      --cyber-orange: #ff6a00;
      --cyber-pink: #ff0088;
      --cyber-cyan: #00ffcc;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html,
    body {
      min-height: 100%;
      background: radial-gradient(1200px 700px at 50% -10%, #1a0a2e 0%, var(--bg) 55%);
      font-family: 'JetBrains Mono', monospace;
      color: var(--val);
      display: flex;
      align-items: center;
      justify-content: center;
      padding: clamp(16px, 5vw, 40px) clamp(12px, 3vw, 16px);
    }

    .window {
      width: 100%;
      max-width: 860px;
      background: var(--panel);
      border: 2px solid var(--cyber-green);
      border-radius: 10px;
      box-shadow: 0 0 30px rgba(0, 255, 65, 0.15), 0 0 60px rgba(0, 255, 65, 0.05), 0 0 0 1px rgba(0, 255, 65, 0.1);
      overflow: hidden;
      opacity: 0;
      transform: translateY(14px);
      animation: rise .5s ease forwards;
    }

    @keyframes rise {
      to {
        opacity: 1;
        transform: none;
      }
    }

    .titlebar {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 10px 14px;
      background: linear-gradient(180deg, #12101f, #0d0d1a);
      border-bottom: 1px solid var(--cyber-red);
      flex-wrap: wrap;
    }

    .dot {
      width: 11px;
      height: 11px;
      border-radius: 50%;
      flex-shrink: 0;
    }
    .dot.r { background: var(--cyber-red); box-shadow: 0 0 10px var(--cyber-red); }
    .dot.y { background: var(--cyber-yellow); box-shadow: 0 0 10px var(--cyber-yellow); }
    .dot.g { background: var(--cyber-green); box-shadow: 0 0 10px var(--cyber-green); }

    .titlebar .path {
      margin-left: 10px;
      font-size: clamp(10px, 1.6vw, 12.5px);
      color: var(--muted);
      letter-spacing: .3px;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }
    .titlebar .path b {
      color: var(--cyber-green);
      font-weight: 600;
      text-shadow: 0 0 10px rgba(0, 255, 65, 0.3);
    }

    .body {
      display: grid;
      grid-template-columns: minmax(160px, 280px) 1fr;
      gap: clamp(16px, 3vw, 28px);
      padding: clamp(20px, 4vw, 30px) clamp(16px, 3vw, 28px) clamp(24px, 4vw, 34px);
    }

    .profile-image {
      width: 100%;
      max-width: 280px;
      border-radius: 10px;
      border: 2px solid var(--cyber-green);
      filter: grayscale(100%);
      box-shadow: 0 0 30px rgba(0, 255, 65, 0.15);
      transition: filter 0.3s ease;
      align-self: start;
    }
    .profile-image:hover {
      filter: grayscale(0%);
    }

    .info {
      min-width: 0;
      overflow: hidden;
    }

    .whoami {
      font-size: clamp(14px, 2.2vw, 18px);
      font-weight: 800;
      color: var(--cyber-green);
      margin: 2px 0 10px;
      letter-spacing: .2px;
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      text-shadow: 0 0 20px rgba(0, 255, 65, 0.3);
    }
    .whoami .caret {
      display: inline-block;
      width: 8px;
      height: 1.1em;
      background: var(--cyber-green);
      margin-left: 4px;
      animation: blink 1.1s steps(1) infinite;
      flex-shrink: 0;
      box-shadow: 0 0 15px var(--cyber-green);
    }
    @keyframes blink {
      50% { opacity: 0; }
    }

    hr.rule {
      border: none;
      border-top: 1px solid var(--cyber-red);
      margin: 10px 0 14px;
      box-shadow: 0 0 20px rgba(255, 0, 64, 0.2);
    }

    .section-title {
      font-size: clamp(10px, 1.4vw, 11px);
      letter-spacing: 1.5px;
      text-transform: uppercase;
      color: var(--cyber-red);
      margin: 18px 0 8px;
      font-weight: 700;
      text-shadow: 0 0 15px rgba(255, 0, 64, 0.3);
    }
    .section-title:first-child {
      margin-top: 0;
    }

    .row {
      display: grid;
      grid-template-columns: 148px 1fr;
      gap: 8px 12px;
      font-size: clamp(12px, 1.6vw, 14px);
      line-height: 1.85;
      padding: 2px 0;
    }
    .row .k {
      color: var(--key);
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }
    .row .k .dim {
      color: var(--muted);
    }
    .row .v {
      color: var(--val);
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
    }
    .row .v a {
      color: var(--val);
      text-decoration: none;
      border-bottom: 1px dashed var(--muted);
    }
    .row .v a:hover {
      color: var(--cyber-green);
      border-color: var(--cyber-green);
    }

    /* Language color tags */
    .lang-tag {
      display: inline-block;
      padding: 0 8px;
      border-radius: 3px;
      font-weight: 600;
      font-size: 0.85em;
      margin: 1px 2px;
    }
    .lang-tag.html { color: #e34f26; }
    .lang-tag.css { color: #1572b6; }
    .lang-tag.js { color: #f7df1e; }
    .lang-tag.php { color: #777bb3; }
    .lang-tag.sql { color: #00758f; }
    .lang-tag.tailwind { color: #06b6d4; }
    .lang-tag.react { color: #61dafb; }
    .lang-tag.nodejs { color: #68a063; }
    .lang-tag.nextjs { color: #ffffff; }
    .lang-tag.wordpress { color: #21759b; }
    .lang-tag.elementor { color: #92003b; }

    .lang-percent {
      font-size: 0.75em;
      color: var(--muted);
      margin-left: 2px;
    }

    /* Progress bar for skills */
    .skill-bar-wrap {
      display: flex;
      align-items: center;
      gap: 8px;
      width: 100%;
    }
    .skill-bar-bg {
      flex: 1;
      height: 6px;
      background: #1a1a2e;
      border-radius: 3px;
      overflow: hidden;
      border: 1px solid #2a2a4e;
    }
    .skill-bar-fill {
      height: 100%;
      border-radius: 3px;
      transition: width 1s ease;
      box-shadow: 0 0 10px currentColor;
    }
    .skill-bar-fill.html-fill { background: #e34f26; width: 100%; }
    .skill-bar-fill.css-fill { background: #1572b6; width: 100%; }
    .skill-bar-fill.js-fill { background: #f7df1e; width: 70%; }
    .skill-bar-fill.php-fill { background: #777bb3; width: 72%; }
    .skill-bar-fill.sql-fill { background: #00758f; width: 65%; }
    .skill-bar-fill.tailwind-fill { background: #06b6d4; width: 85%; }
    .skill-bar-fill.react-fill { background: #61dafb; width: 68%; }
    .skill-bar-fill.nodejs-fill { background: #68a063; width: 55%; }
    .skill-bar-fill.nextjs-fill { background: #ffffff; width: 64%; }
    .skill-bar-fill.wordpress-fill { background: #21759b; width: 100%; }
    .skill-bar-fill.elementor-fill { background: #92003b; width: 100%; }

    .skill-percent {
      font-size: 0.8em;
      min-width: 36px;
      text-align: right;
      color: var(--muted);
      font-weight: 600;
    }

    /* ===== Slider Styles ===== */
    .slider-section {
      padding: 0 clamp(16px, 3vw, 28px) clamp(20px, 3vw, 28px);
      border-top: 1px solid var(--cyber-red);
    }

    .slider-title {
      font-size: clamp(10px, 1.4vw, 11px);
      letter-spacing: 1.5px;
      text-transform: uppercase;
      color: var(--cyber-red);
      margin: 16px 0 12px;
      font-weight: 700;
      text-shadow: 0 0 15px rgba(255, 0, 64, 0.3);
    }

    .slider-container {
      position: relative;
      overflow: hidden;
      border-radius: 8px;
      border: 1px solid var(--cyber-green);
      background: var(--bg);
      box-shadow: 0 0 20px rgba(0, 255, 65, 0.05);
    }

    .slider-track {
      display: flex;
      transition: transform 0.5s ease-in-out;
    }

    .slider-slide {
      min-width: 100%;
      padding: 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 10px;
    }

    .slider-slide img {
      width: 100%;
      max-width: 400px;
      height: 200px;
      object-fit: cover;
      border-radius: 6px;
      border: 1px solid var(--border);
    }

    .slider-slide .project-name {
      font-size: clamp(14px, 2vw, 18px);
      font-weight: 700;
      color: var(--cyber-green);
      text-shadow: 0 0 20px rgba(0, 255, 65, 0.2);
    }

    .slider-slide .project-desc {
      font-size: clamp(11px, 1.3vw, 13px);
      color: var(--muted);
      text-align: center;
      max-width: 80%;
    }

    .slider-slide .project-link {
      color: var(--cyber-red);
      text-decoration: none;
      font-size: clamp(11px, 1.2vw, 13px);
      border-bottom: 1px dashed var(--cyber-red);
      padding-bottom: 2px;
    }
    .slider-slide .project-link:hover {
      color: var(--cyber-green);
      border-color: var(--cyber-green);
    }

    .slider-btn {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      background: rgba(13, 13, 26, 0.9);
      border: 1px solid var(--cyber-green);
      color: var(--cyber-green);
      width: 32px;
      height: 32px;
      border-radius: 50%;
      cursor: pointer;
      font-size: 18px;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.3s;
      z-index: 2;
      box-shadow: 0 0 15px rgba(0, 255, 65, 0.1);
    }
    .slider-btn:hover {
      background: var(--cyber-green);
      color: var(--bg);
      box-shadow: 0 0 30px rgba(0, 255, 65, 0.3);
    }
    .slider-btn.prev { left: 8px; }
    .slider-btn.next { right: 8px; }

    .slider-dots {
      display: flex;
      justify-content: center;
      gap: 8px;
      padding: 12px 0 4px;
    }
    .slider-dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: var(--muted);
      border: none;
      cursor: pointer;
      transition: background 0.3s;
    }
    .slider-dot.active {
      background: var(--cyber-green);
      box-shadow: 0 0 15px var(--cyber-green);
    }

    /* ===== Skills Section ===== */
    .skills-section {
      padding: 0 clamp(16px, 3vw, 28px) clamp(20px, 3vw, 28px);
      border-top: 1px solid var(--cyber-red);
    }

    .skills-title {
      font-size: clamp(10px, 1.4vw, 11px);
      letter-spacing: 1.5px;
      text-transform: uppercase;
      color: var(--cyber-red);
      margin: 16px 0 10px;
      font-weight: 700;
      text-shadow: 0 0 15px rgba(255, 0, 64, 0.3);
    }

    .skill-row {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 3px 0;
      font-size: clamp(11px, 1.3vw, 13px);
    }
    .skill-row .skill-label {
      min-width: 100px;
      color: var(--key);
    }
    .skill-row .skill-label .lang-tag {
      font-size: 0.9em;
    }
    .skill-row .skill-bar-wrap {
      flex: 1;
    }
    .skill-row .skill-percent {
      min-width: 36px;
      text-align: right;
      color: var(--muted);
      font-weight: 600;
    }

    .footer {
      padding: 12px clamp(16px, 3vw, 28px) 20px;
      border-top: 1px solid var(--cyber-green);
      font-size: clamp(10px, 1.3vw, 11.5px);
      color: var(--muted);
      letter-spacing: .4px;
    }
    .footer b {
      color: var(--cyber-green);
      text-shadow: 0 0 10px rgba(0, 255, 65, 0.2);
    }

    /* ===== Responsive ===== */

    @media (max-width: 768px) {
      .body {
        grid-template-columns: 1fr;
        gap: 16px;
      }
      .profile-image {
        max-width: 200px;
        margin: 0 auto;
      }
      .row {
        grid-template-columns: 1fr;
        gap: 0 4px;
        white-space: normal;
      }
      .row .k {
        white-space: normal;
        font-weight: 500;
        font-size: 0.9em;
        color: var(--muted);
      }
      .row .k .dim {
        display: none;
      }
      .row .v {
        white-space: normal;
        word-break: break-word;
        padding-left: 4px;
        font-size: 0.95em;
      }
      .row .v a {
        word-break: break-all;
      }
      .section-title {
        margin-top: 14px;
      }
      .slider-slide img {
        height: 150px;
        max-width: 300px;
      }
      .slider-btn {
        width: 26px;
        height: 26px;
        font-size: 14px;
      }
      .skill-row {
        flex-wrap: wrap;
        gap: 4px;
      }
      .skill-row .skill-label {
        min-width: 80px;
        font-size: 0.9em;
      }
    }

    @media (max-width: 480px) {
      html, body {
        padding: 8px;
      }
      .titlebar {
        padding: 6px 10px;
        gap: 5px;
      }
      .titlebar .path {
        margin-left: 4px;
        font-size: 9px;
      }
      .dot {
        width: 9px;
        height: 9px;
      }
      .body {
        padding: 14px 12px 18px;
        gap: 12px;
      }
      .profile-image {
        max-width: 150px;
      }
      .whoami {
        font-size: 14px;
      }
      .row {
        font-size: 11px;
        line-height: 1.6;
        padding: 1px 0;
      }
      .row .k {
        font-size: 0.85em;
      }
      .row .v {
        font-size: 0.9em;
        padding-left: 2px;
      }
      .slider-slide {
        padding: 12px;
      }
      .slider-slide img {
        height: 120px;
        max-width: 250px;
      }
      .slider-slide .project-name {
        font-size: 13px;
      }
      .slider-slide .project-desc {
        font-size: 10px;
      }
      .slider-btn {
        width: 22px;
        height: 22px;
        font-size: 12px;
      }
      .skill-row {
        font-size: 10px;
      }
      .skill-row .skill-label {
        min-width: 70px;
      }
      .footer {
        font-size: 9px;
        padding: 10px 12px 16px;
      }
      .section-title {
        font-size: 9px;
        margin: 12px 0 4px;
      }
      .section-title:first-child {
        margin-top: 0;
      }
    }

    @media (max-width: 360px) {
      .profile-image {
        max-width: 120px;
      }
      .row {
        font-size: 10px;
      }
      .whoami {
        font-size: 12px;
      }
    }
  </style>
</head>
<body>

  <div class="window">
    <div class="titlebar">
      <span class="dot r"></span>
      <span class="dot y"></span>
      <span class="dot g"></span>
      <span class="path"><b>sroushgahramani</b> / README.md</span>
    </div>

    <div class="body">
      <img src="https://xprocoo.com/admin/uploads/1784725956_file_000000001ce871f5a88d131216165285.png" alt="Profile" class="profile-image">

      <div class="info">
        <div class="whoami">sroush@gahramani<span class="caret"></span></div>
        <hr class="rule">
        <div id="rows"></div>
      </div>
    </div>

    <!-- Skills Section -->
    <div class="skills-section">
      <div class="skills-title">── Skills & Expertise</div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag html">HTML</span></span>
        <div class="skill-bar-wrap">
          <div class="skill-bar-bg"><div class="skill-bar-fill html-fill"></div></div>
        </div>
        <span class="skill-percent">100%</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag css">CSS</span></span>
        <div class="skill-bar-wrap">
          <div class="skill-bar-bg"><div class="skill-bar-fill css-fill"></div></div>
        </div>
        <span class="skill-percent">100%</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag js">JavaScript</span></span>
        <div class="skill-bar-wrap">
          <div class="skill-bar-bg"><div class="skill-bar-fill js-fill"></div></div>
        </div>
        <span class="skill-percent">70%</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag php">PHP</span></span>
        <div class="skill-bar-wrap">
          <div class="skill-bar-bg"><div class="skill-bar-fill php-fill"></div></div>
        </div>
        <span class="skill-percent">72%</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag sql">SQL</span></span>
        <div class="skill-bar-wrap">
          <div class="skill-bar-bg"><div class="skill-bar-fill sql-fill"></div></div>
        </div>
        <span class="skill-percent">65%</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag tailwind">Tailwind CSS</span></span>
        <div class="skill-bar-wrap">
          <div class="skill-bar-bg"><div class="skill-bar-fill tailwind-fill"></div></div>
        </div>
        <span class="skill-percent">85%</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag react">React</span></span>
        <div class="skill-bar-wrap">
          <div class="skill-bar-bg"><div class="skill-bar-fill react-fill"></div></div>
        </div>
        <span class="skill-percent">68%</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag nodejs">Node.js</span></span>
        <div class="skill-bar-wrap">
          <div class="skill-bar-bg"><div class="skill-bar-fill nodejs-fill"></div></div>
        </div>
        <span class="skill-percent">55%</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag nextjs">Next.js</span></span>
        <div class="skill-bar-wrap">
          <div class="skill-bar-bg"><div class="skill-bar-fill nextjs-fill"></div></div>
        </div>
        <span class="skill-percent">64%</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag wordpress">WordPress</span></span>
        <div class="skill-bar-wrap">
          <div class="skill-bar-bg"><div class="skill-bar-fill wordpress-fill"></div></div>
        </div>
        <span class="skill-percent">100%</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag elementor">Elementor</span></span>
        <div class="skill-bar-wrap">
          <div class="skill-bar-bg"><div class="skill-bar-fill elementor-fill"></div></div>
        </div>
        <span class="skill-percent">100%</span>
      </div>
      
      <div class="skill-row" style="margin-top: 8px; border-top: 1px solid var(--border); padding-top: 8px;">
        <span class="skill-label"><span class="lang-tag" style="color:var(--cyber-green);">⚡ API</span></span>
        <span style="color:var(--muted); font-size:0.9em;">REST, WebSocket</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag" style="color:var(--cyber-purple);">🤖 AI</span></span>
        <span style="color:var(--muted); font-size:0.9em;">OpenAI, Gemini, Claude</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag" style="color:var(--cyber-cyan);">💬 Chatbots</span></span>
        <span style="color:var(--muted); font-size:0.9em;">Web</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag" style="color:var(--cyber-orange);">📊 Data</span></span>
        <span style="color:var(--muted); font-size:0.9em;">Web Scraping, Automation</span>
      </div>
      
      <div class="skill-row">
        <span class="skill-label"><span class="lang-tag" style="color:var(--cyber-pink);">🧠 LLM</span></span>
        <span style="color:var(--muted); font-size:0.9em;">Prompt Engineering, RAG</span>
      </div>
    </div>

    <!-- Slider Section -->
    <div class="slider-section">
      <div class="slider-title">── Portfolio</div>
      <div class="slider-container">
        <div class="slider-track" id="sliderTrack">
          <div class="slider-slide">
            <img src="https://xprocoo.com/admin/uploads/1784726462_Untitled-1.png" alt="XproCoo Project">
            <div class="project-name">🚀 XproCoo</div>
            <div class="project-desc">Personal website &amp; portfolio</div>
            <a href="https://xprocoo.com" target="_blank" class="project-link">xprocoo.com →</a>
          </div>
          <div class="slider-slide">
            <img src="https://xprocoo.com/admin/uploads/1784726186_IMG_20260531_210712.png" alt="CoinsPlays Project">
            <div class="project-name">🪙 CoinsPlays</div>
            <div class="project-desc">Gaming &amp; crypto platform with real-time analytics</div>
            <a href="https://coinsplays.com" target="_blank" class="project-link">coinsplays.com →</a>
          </div>
        </div>
        <button class="slider-btn prev" id="prevBtn">‹</button>
        <button class="slider-btn next" id="nextBtn">›</button>
        <div class="slider-dots" id="sliderDots"></div>
      </div>
    </div>

    <div class="footer">
      <b>tip:</b> click a stat to copy &middot; last synced just now
    </div>
  </div>

  <script>
    const rows = [
      { section: 'sroush@gahramani' },
      { k: 'Age', v: '21 years' },
      { k: 'Education', v: 'BSc in Computer Engineering - Islamic Azad University' },

      { sep: true },
      { k: 'Languages.Spoken', v: 'Kurdish, Persian, English' },

      { section: 'Website' },
      { k: 'Personal Website', v: 'xprocoo.com', link: 'https://xprocoo.com' },

      { section: 'Contact' },
      { k: 'Email.Personal', v: 'sroushgahramani@gmail.com', link: 'mailto:sroushgahramani@gmail.com' },
      { k: 'WhatsApp', v: '09381358518', link: 'https://wa.me/989381358518' },
      { k: 'Telegram', v: '@Sroushi', link: 'https://t.me/Sroushi' },
    ];

    const container = document.getElementById('rows');
    rows.forEach(r => {
      if (r.section) {
        const el = document.createElement('div');
        el.className = 'section-title';
        el.textContent = '── ' + r.section;
        container.appendChild(el);
        return;
      }
      if (r.sep) {
        const el = document.createElement('div');
        el.style.height = '6px';
        container.appendChild(el);
        return;
      }
      const row = document.createElement('div');
      row.className = 'row';

      let valueHtml;
      if (r.link) {
        valueHtml = `<a href="${r.link}" target="_blank">${r.v}</a>`;
      } else {
        valueHtml = r.v;
      }

      row.innerHTML = `<span class="k">${r.k}<span class="dim">:</span></span><span class="v">${valueHtml}</span>`;
      container.appendChild(row);
    });

    // ===== Slider Logic =====
    let currentSlide = 0;
    const track = document.getElementById('sliderTrack');
    const slides = track.querySelectorAll('.slider-slide');
    const totalSlides = slides.length;
    const dotsContainer = document.getElementById('sliderDots');

    // Create dots
    for (let i = 0; i < totalSlides; i++) {
      const dot = document.createElement('button');
      dot.className = 'slider-dot' + (i === 0 ? ' active' : '');
      dot.setAttribute('data-index', i);
      dot.addEventListener('click', () => goToSlide(i));
      dotsContainer.appendChild(dot);
    }

    function goToSlide(index) {
      currentSlide = index;
      track.style.transform = `translateX(-${currentSlide * 100}%)`;
      document.querySelectorAll('.slider-dot').forEach((dot, i) => {
        dot.classList.toggle('active', i === currentSlide);
      });
    }

    document.getElementById('prevBtn').addEventListener('click', () => {
      goToSlide((currentSlide - 1 + totalSlides) % totalSlides);
    });

    document.getElementById('nextBtn').addEventListener('click', () => {
      goToSlide((currentSlide + 1) % totalSlides);
    });

    // Auto-play slider every 5 seconds
    let autoPlay = setInterval(() => {
      goToSlide((currentSlide + 1) % totalSlides);
    }, 5000);

    // Pause auto-play on hover
    const sliderContainer = document.querySelector('.slider-container');
    sliderContainer.addEventListener('mouseenter', () => clearInterval(autoPlay));
    sliderContainer.addEventListener('mouseleave', () => {
      autoPlay = setInterval(() => {
        goToSlide((currentSlide + 1) % totalSlides);
      }, 5000);
    });
  </script>

</body>
</html>