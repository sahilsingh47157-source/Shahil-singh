<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Shakti | Creative Portfolio & Journey</title>

  <!-- Google Fonts: Space Grotesk & Outfit -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&family=Space+Grotesk:wght@600;700;800&display=swap" rel="stylesheet">

  <style>
    /* ==========================================================================
       1. THEME COLORS & VARIABLES (Colors yahan se change kar sakte hain)
       ========================================================================== */
    :root {
      --accent: #38bdf8;
      --pink: #ff007f;
      --purple: #7928ca;
      --neon-cyan: #00f2fe;
      --card-bg: rgba(15, 23, 42, 0.65);
      --card-border: rgba(255, 255, 255, 0.12);
      --text: #f8fafc;
      --muted: #94a3b8;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      cursor: default;
    }

    body {
      font-family: 'Outfit', sans-serif;
      color: var(--text);
      line-height: 1.6;
      background-color: #030712;
      min-height: 100vh;
      overflow-x: hidden;
      position: relative;
    }

    /* Custom Glowing Cursor */
    .cursor-dot {
      width: 8px;
      height: 8px;
      background: var(--neon-cyan);
      border-radius: 50%;
      position: fixed;
      pointer-events: none;
      z-index: 9999;
      box-shadow: 0 0 10px var(--neon-cyan);
      transform: translate(-50%, -50%);
    }

    .cursor-outline {
      width: 32px;
      height: 32px;
      border: 1.5px solid rgba(56, 189, 248, 0.6);
      border-radius: 50%;
      position: fixed;
      pointer-events: none;
      z-index: 9998;
      transform: translate(-50%, -50%);
      transition: width 0.2s, height 0.2s, transform 0.15s ease-out;
    }

    /* Background Particle Canvas & Glow Lights */
    #particles-canvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      z-index: -2;
      pointer-events: none;
    }

    .glow-sphere {
      position: fixed;
      width: 500px;
      height: 500px;
      border-radius: 50%;
      filter: blur(140px);
      opacity: 0.35;
      z-index: -1;
      pointer-events: none;
      animation: floatGlow 15s infinite alternate ease-in-out;
    }

    .glow-1 {
      top: -150px;
      left: -150px;
      background: radial-gradient(circle, var(--purple), transparent 70%);
    }

    .glow-2 {
      bottom: -150px;
      right: -150px;
      background: radial-gradient(circle, var(--pink), transparent 70%);
      animation-delay: -7s;
    }

    @keyframes floatGlow {
      0% { transform: translate(0, 0) scale(1); }
      100% { transform: translate(70px, 80px) scale(1.15); }
    }

    /* Frontend Flying Butterflies Layer */
    #butterfly-container {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      pointer-events: none;
      z-index: 99;
      overflow: hidden;
    }

    .floating-butterfly {
      position: absolute;
      font-size: 2rem;
      user-select: none;
      pointer-events: none;
      will-change: transform, left, top;
    }

    .wing-flapping {
      display: inline-block;
      animation: wingBeat 0.22s infinite alternate ease-in-out;
    }

    @keyframes wingBeat {
      0% { transform: scaleX(0.4) rotate(12deg); }
      100% { transform: scaleX(1.35) rotate(-12deg); }
    }

    .container {
      max-width: 860px;
      margin: 0 auto;
      padding: 4rem 1.4rem 6rem;
      position: relative;
      z-index: 2;
    }

    /* Hero Profile Section */
    .hero {
      text-align: center;
      margin-bottom: 4rem;
      position: relative;
    }

    .avatar-wrapper {
      position: relative;
      width: 150px;
      height: 150px;
      margin: 0 auto 1.8rem;
    }

    /* Avatar Orbiting Butterfly */
    .butterfly-orbit {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      border-radius: 50%;
      animation: orbitFly 5.5s linear infinite;
      pointer-events: none;
      z-index: 10;
    }

    .orbit-butterfly-icon {
      position: absolute;
      top: -16px;
      left: 50%;
      font-size: 2rem;
      transform: translateX(-50%);
      filter: drop-shadow(0 0 12px var(--pink)) drop-shadow(0 0 20px var(--neon-cyan));
      animation: wingBeat 0.2s infinite alternate ease-in-out;
    }

    @keyframes orbitFly {
      from { transform: rotate(0deg); }
      to { transform: rotate(360deg); }
    }

    /* Cyber RGB Ring Glow */
    @keyframes cyberGlow {
      0% { box-shadow: 0 0 30px var(--pink), inset 0 0 12px var(--pink); border-color: var(--pink); }
      33% { box-shadow: 0 0 30px var(--neon-cyan), inset 0 0 12px var(--neon-cyan); border-color: var(--neon-cyan); }
      66% { box-shadow: 0 0 30px var(--purple), inset 0 0 12px var(--purple); border-color: var(--purple); }
      100% { box-shadow: 0 0 30px var(--pink), inset 0 0 12px var(--pink); border-color: var(--pink); }
    }

    .profile-ring {
      width: 138px;
      height: 138px;
      border-radius: 50%;
      background: #0f172a;
      display: flex;
      align-items: center;
      justify-content: center;
      border: 3.5px solid var(--pink);
      animation: cyberGlow 5s linear infinite;
      overflow: hidden;
      margin: 6px auto;
      position: relative;
    }

    .profile-img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.4s ease;
    }

    .profile-ring:hover .profile-img {
      transform: scale(1.1);
    }

    /* Name Typography & Color Shift */
    @keyframes textShift {
      0% { filter: hue-rotate(0deg); }
      50% { filter: hue-rotate(180deg); }
      100% { filter: hue-rotate(360deg); }
    }

    .name-glow {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 3.5rem;
      font-weight: 800;
      letter-spacing: -0.5px;
      margin-bottom: 0.3rem;
      background: linear-gradient(90deg, #ff007f, #a855f7, #00f2fe, #38bdf8, #ff007f);
      background-size: 300% 300%;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      animation: textShift 6s ease infinite alternate;
    }

    .tagline {
      color: var(--accent);
      font-weight: 600;
      font-size: 1.25rem;
      margin-bottom: 0.8rem;
    }

    .bio {
      color: var(--muted);
      max-width: 600px;
      margin: 0 auto 1.8rem;
      font-size: 1.05rem;
    }

    /* Social Media Links */
    .social-links {
      display: flex;
      justify-content: center;
      gap: 0.9rem;
      flex-wrap: wrap;
    }

    .social-btn {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.65rem 1.4rem;
      background: rgba(255, 255, 255, 0.04);
      backdrop-filter: blur(12px);
      color: #fff;
      border: 1px solid var(--card-border);
      border-radius: 30px;
      text-decoration: none;
      font-size: 0.95rem;
      font-weight: 600;
      transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
      cursor: pointer;
    }

    .social-btn:hover {
      background: rgba(56, 189, 248, 0.18);
      border-color: var(--accent);
      transform: translateY(-4px);
      box-shadow: 0 8px 25px rgba(56, 189, 248, 0.35);
    }

    /* Stats Counter Bar */
    .stats-bar {
      display: flex;
      justify-content: center;
      gap: 2rem;
      margin: 2.5rem 0 4.5rem;
      flex-wrap: wrap;
    }

    .stat-item {
      text-align: center;
      background: var(--card-bg);
      backdrop-filter: blur(10px);
      padding: 1rem 1.8rem;
      border-radius: 14px;
      border: 1px solid var(--card-border);
    }

    .stat-num {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 1.8rem;
      font-weight: 800;
      color: var(--neon-cyan);
    }

    .stat-label {
      font-size: 0.8rem;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 0.05em;
    }

    /* Section Styling */
    .section-title {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 1.8rem;
      margin-bottom: 2rem;
      display: flex;
      align-items: center;
      gap: 0.8rem;
    }

    .section-title::after {
      content: '';
      flex: 1;
      height: 1px;
      background: linear-gradient(90deg, rgba(255,255,255,0.15), transparent);
      margin-left: 1rem;
    }

    /* Timeline Section */
    .timeline {
      position: relative;
      border-left: 2px solid rgba(255, 255, 255, 0.1);
      margin-left: 1rem;
      padding-left: 2rem;
      margin-bottom: 5rem;
    }

    .timeline-item {
      position: relative;
      margin-bottom: 2.4rem;
    }

    .timeline-item::before {
      content: '';
      position: absolute;
      left: -2.6rem;
      top: 1.3rem;
      width: 14px;
      height: 14px;
      border-radius: 50%;
      background: var(--accent);
      box-shadow: 0 0 15px var(--accent);
      border: 3px solid #030712;
      transition: transform 0.3s ease;
    }

    .timeline-item:hover::before {
      transform: scale(1.4);
      background: var(--pink);
      box-shadow: 0 0 15px var(--pink);
    }

    .timeline-card {
      background: var(--card-bg);
      backdrop-filter: blur(14px);
      border: 1px solid var(--card-border);
      padding: 1.6rem;
      border-radius: 18px;
      transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .timeline-card:hover {
      transform: translateX(8px);
      border-color: rgba(56, 189, 248, 0.4);
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
    }

    .timeline-year {
      font-size: 0.85rem;
      color: var(--accent);
      font-weight: 700;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      margin-bottom: 0.3rem;
    }

    .timeline-title {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 1.3rem;
      font-weight: 700;
      margin-bottom: 0.4rem;
    }

    .timeline-desc {
      color: var(--muted);
      font-size: 0.98rem;
    }

    /* Projects Grid */
    .grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1.6rem;
      margin-bottom: 5rem;
    }

    .card {
      background: var(--card-bg);
      backdrop-filter: blur(14px);
      border: 1px solid var(--card-border);
      padding: 1.8rem;
      border-radius: 20px;
      transition: transform 0.25s ease, border-color 0.25s ease, box-shadow 0.25s ease;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    .card:hover {
      border-color: rgba(56, 189, 248, 0.5);
      box-shadow: 0 15px 35px rgba(56, 189, 248, 0.2);
    }

    .card-title {
      font-family: 'Space Grotesk', sans-serif;
      font-size: 1.3rem;
      font-weight: 700;
      margin-bottom: 0.6rem;
    }

    .card-desc {
      color: var(--muted);
      font-size: 0.94rem;
      margin-bottom: 1.4rem;
    }

    .tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.5rem;
    }

    .tag {
      font-size: 0.78rem;
      background: rgba(56, 189, 248, 0.12);
      color: var(--accent);
      padding: 0.3rem 0.75rem;
      border-radius: 8px;
      font-weight: 600;
    }

    footer {
      text-align: center;
      color: var(--muted);
      font-size: 0.88rem;
      border-top: 1px solid var(--card-border);
      padding-top: 3rem;
    }

    @media (max-width: 650px) {
      .grid { grid-template-columns: 1fr; }
      .name-glow { font-size: 2.6rem; }
      .timeline { padding-left: 1.4rem; }
      .timeline-item::before { left: -2.1rem; }
      .stats-bar { gap: 1rem; }
    }
  </style>
</head>
<body>

  <!-- Floating Butterflies Container -->
  <div id="butterfly-container"></div>

  <!-- Custom Glowing Cursor -->
  <div class="cursor-dot"></div>
  <div class="cursor-outline"></div>

  <!-- Animated Particle Canvas & Deep Lights -->
  <canvas id="particles-canvas"></canvas>
  <div class="glow-sphere glow-1"></div>
  <div class="glow-sphere glow-2"></div>

  <div class="container">
    <header class="hero">
      
      <div class="avatar-wrapper">
        <div class="butterfly-orbit">
          <div class="orbit-butterfly-icon">🦋</div>
        </div>

        <div class="profile-ring">
          <!-- =================================================================
               [EDIT SECTION 1: APNI PHOTO]
               Neeche 'src="..."' ke andar apni photo ka direct URL paste karein.
               ================================================================= -->
          <img src="https://i.ibb.co/6c2rVf7V/IMG-20260408-WA0004.jpg" alt="Profile" class="profile-img">
        </div>
      </div>

      <!-- =================================================================
           [EDIT SECTION 2: NAAM, TAGLINE & BIO]
           Apna naam aur intro yahan change karein.
           ================================================================= -->
      <h1 class="name-glow">Shahil singh </h1>
      <p class="tagline">Creative Media & Tech Enthusiast</p>
      <p class="bio">Crafting modern digital visual identities, building interactive experiences, and solving creative challenges.</p>

      <!-- =================================================================
           [EDIT SECTION 3: SOCIAL MEDIA LINKS]
           'href="..."' mein apne Instagram, YouTube, LinkedIn ya Email links daalein.
           ================================================================= -->
      <div class="social-links">
        <a href="https://www.instagram.com/sha_hil8756?utm_source=ig_web_button_share_sheet&stkn=ZDNlZDc0MzIxNw==" target="_blank" class="social-btn">📸 Instagram</a>
        
        <a href="https://www.linkedin.com/in/shahil-singh-94742b3b9?utm_source=share_via&utm_content=profile&utm_medium=member_android" target="_blank" class="social-btn">💼 LinkedIn</a>
        <a href="mailtp: shahilsingh504gmail.com" class="social-btn">✉️ Say Hello</a>
      </div>

      <!-- =================================================================
           [EDIT SECTION 4: STATS / HIGHLIGHT COUNTER]
           Yahan numbers aur labels badal sakte hain.
           ================================================================= -->
      <div class="stats-bar">
        <div class="stat-item">
          <div class="stat-num">3+</div>
          <div class="stat-label">Years Creating</div>
        </div>
        <div class="stat-item">
          <div class="stat-num">50+</div>
          <div class="stat-label">Visual Projects</div>
        </div>
        <div class="stat-item">
          <div class="stat-num">100%</div>
          <div class="stat-label">Passion & Focus</div>
        </div>
      </div>
    </header>

    <!-- =================================================================
         [EDIT SECTION 5: MY LIFE JOURNEY / TIMELINE]
         Yahan apne saal (years), title aur description badal sakte hain.
         Naya saal add karne ke liye poore <div class="timeline-item">...</div> ko copy-paste karein.
         ================================================================= -->
    <section>
      <h2 class="section-title">😊😘 My Life Journey</h2>
      
      <div class="timeline">
        <!-- Journey Milestone 1 With Photo -->
    <div class="timeline-item">
     <div class="timeline-card">
      <div class="timeline-year-month"> 2026-june to ----</div>
       <div class="timeline-title">College life </div>
      <p class="timeline-desc">college life ongoing.</p>
    
    <!-- PHOTO YAHAN ADD KAREIN -->
    <img src="https://i.ibb.co/6c3b8T3x/IMG-20260408-WA0004.jpg" 
         alt="Milestone Highlight" 
         class="timeline-photo">
     </div>
    </div>
        <!-- Journey Milestone 2-->
        <div class="timeline-item">
          <div class="timeline-card">
            <div class="timeline-year-month">2025 — june 2026, My college life(SSCBS)</div>
            <div class="timeline-title">Interactive Systems & Business Strategy</div>
            <p class="timeline-desc">Developing clean web portfolios, exploring modern deployment setups, and diving into case studies & data analytics.</p>
            
                  
          </div>
        </div>

        <!-- Journey Milestone 3 -->
        <div class="timeline-item">
          <div class="timeline-card">
            <div class="timeline-year">2025 — 2026</div>
            <div class="timeline-title">Creative Editing & AI Visual Media</div>
            <p class="timeline-desc">Mastered aesthetic digital concepts, stylized brand identity art, cinematic media, and visual storytelling.</p>
          </div>
        </div>

        <!-- Journey Milestone 4 -->
        <div class="timeline-item">
          <div class="timeline-card">
            <div class="timeline-year">2024 — 2025</div>
            <div class="timeline-title">Science, Logic & Analytical Foundations</div>
            <p class="timeline-desc">Built strong problem-solving discipline through chemistry, mathematics, and logical reasoning.</p>
          </div>
        </div>
        
      <!-- journey Milestone 5-->
        <div class="timeline-item">
          <div class="timeline-card">
           <div class="timeline-year">2023 — past life </div>
           <div class="timeline-title">Starting the Creative Journey and serious life </div>
           <p class="timeline-desc">I come from a small Tier-3 village and a humble background. I’m currently studying at a government college. I used to be a careless and directionless boy, but in 2023, my life changed when I started seeing my father’s hard work and sacrifices. That became my turning point. Since then, I’ve become more serious, focused, and determined to build a better future.</p>
     </div>
    </div>

      </div>
    </section>

    <!-- =================================================================
         [EDIT SECTION 6: FEATURED HIGHLIGHTS / PROJECTS]
         Yahan apne projects ke naam, details aur tags badlein.
         ================================================================= -->
    <section>
      <h2 class="section-title">✨ Featured Highlights</h2>

      <div class="grid">
        
        <!-- Project Card 1 -->
        <div class="card">
          <div>
            <div class="card-title">Digital Visual Identity</div>
            <p class="card-desc">Unique cinematic visual designs, neon color grading, custom typography, and high-engagement digital posters.</p>
          </div>
          <div class="tags">
            <span class="tag">Design</span>
            <span class="tag">Visual Art</span>
            <span class="tag">Creative</span>
          </div>
        </div>

        <!-- Project Card 2 -->
        <div class="card">
          <div>
            <div class="card-title">Strategic Growth Model</div>
            <p class="card-desc">Interactive analytical breakdown, live-service ecosystem planning, and presentation case studies.</p>
          </div>
          <div class="tags">
            <span class="tag">Strategy</span>
            <span class="tag">Analysis</span>
            <span class="tag">Business</span>
          </div>
        </div>

      </div>
    </section>

    <footer>
      <!-- =================================================================
           [EDIT SECTION 7: FOOTER COPYRIGHT]
           ================================================================= -->
      <p>© 2026 Shakti. Designed with passion, code & creativity.</p>
    </footer>
  </div>

  <!-- Interactive JavaScript Engine -->
  <script>
    /* ---------------------------------------------------------
       FLYING BUTTERFLIES ENGINE (Screen par udne wali butterflies)
       Agar butterflies ki sankhya kam/zyada karni ho toh 'butterflyCount' badlein.
       --------------------------------------------------------- */
    const butterflyContainer = document.getElementById('butterfly-container');
    const butterflyCount = 4; // Total butterflies screen par
    const butterflies = [];

    const glowColors = [
      'drop-shadow(0 0 10px #ff007f) drop-shadow(0 0 20px #00f2fe)',
      'drop-shadow(0 0 10px #00ffcc) drop-shadow(0 0 20px #7928ca)',
      'drop-shadow(0 0 10px #38bdf8) drop-shadow(0 0 20px #ff007f)',
      'drop-shadow(0 0 10px #facc15) drop-shadow(0 0 20px #ec4899)'
    ];

    for (let i = 0; i < butterflyCount; i++) {
      const el = document.createElement('div');
      el.className = 'floating-butterfly';
      el.innerHTML = '<span class="wing-flapping">🦋</span>';
      el.style.filter = glowColors[i % glowColors.length];
      butterflyContainer.appendChild(el);

      butterflies.push({
        el: el,
        x: Math.random() * window.innerWidth,
        y: Math.random() * window.innerHeight,
        vx: (Math.random() - 0.5) * 1.5,
        vy: (Math.random() - 0.5) * 1.5,
        targetX: Math.random() * window.innerWidth,
        targetY: Math.random() * window.innerHeight,
        angle: 0
      });
    }

    function animateButterflies() {
      butterflies.forEach(b => {
        const dx = b.targetX - b.x;
        const dy = b.targetY - b.y;
        const dist = Math.hypot(dx, dy);

        if (dist < 50) {
          b.targetX = Math.random() * window.innerWidth;
          b.targetY = Math.random() * window.innerHeight;
        }

        b.vx += (dx / dist) * 0.04;
        b.vy += (dy / dist) * 0.04;
        b.vx *= 0.98;
        b.vy *= 0.98;

        b.x += b.vx;
        b.y += b.vy;
        b.angle = Math.atan2(b.vy, b.vx) * (180 / Math.PI) + 90;

        b.el.style.left = `${b.x}px`;
        b.el.style.top = `${b.y}px`;
        b.el.style.transform = `rotate(${b.angle}deg)`;
      });

      requestAnimationFrame(animateButterflies);
    }
    animateButterflies();

    /* ---------------------------------------------------------
       PARTICLE STARFIELD BACKGROUND
       --------------------------------------------------------- */
    const canvas = document.getElementById('particles-canvas');
    const ctx = canvas.getContext('2d');
    let particles = [];

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }
    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    class Particle {
      constructor() {
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;
        this.size = Math.random() * 1.5 + 0.5;
        this.speedX = (Math.random() - 0.5) * 0.35;
        this.speedY = (Math.random() - 0.5) * 0.35;
        this.opacity = Math.random() * 0.7 + 0.2;
      }
      update() {
        this.x += this.speedX;
        this.y += this.speedY;
        if (this.x < 0) this.x = canvas.width;
        if (this.x > canvas.width) this.x = 0;
        if (this.y < 0) this.y = canvas.height;
        if (this.y > canvas.height) this.y = 0;
      }
      draw() {
        ctx.fillStyle = `rgba(255, 255, 255, ${this.opacity})`;
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
        ctx.fill();
      }
    }

    function initParticles() {
      particles = [];
      const count = Math.floor(window.innerWidth / 16);
      for (let i = 0; i < count; i++) {
        particles.push(new Particle());
      }
    }
    initParticles();

    function animateParticles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      particles.forEach(p => {
        p.update();
        p.draw();
      });
      requestAnimationFrame(animateParticles);
    }
    animateParticles();

    /* ---------------------------------------------------------
       CUSTOM GLOWING CURSOR SCRIPT
       --------------------------------------------------------- */
    const cursorDot = document.querySelector('.cursor-dot');
    const cursorOutline = document.querySelector('.cursor-outline');

    window.addEventListener('mousemove', (e) => {
      cursorDot.style.left = `${e.clientX}px`;
      cursorDot.style.top = `${e.clientY}px`;
      cursorOutline.style.left = `${e.clientX}px`;
      cursorOutline.style.top = `${e.clientY}px`;
    });

    /* ---------------------------------------------------------
       3D TILT EFFECT ON CARDS
       --------------------------------------------------------- */
    const cards = document.querySelectorAll('.card, .timeline-card');
    cards.forEach(card => {
      card.addEventListener('mousemove', (e) => {
        const rect = card.getBoundingClientRect();
        const x = e.clientX - rect.left - rect.width / 2;
        const y = e.clientY - rect.top - rect.height / 2;
        card.style.transform = `perspective(1000px) rotateX(${-y * 0.05}deg) rotateY(${x * 0.05}deg) translateY(-4px)`;
      });
      card.addEventListener('mouseleave', () => {
        card.style.transform = 'perspective(1000px) rotateX(0deg) rotateY(0deg) translateY(0)';
      });
    });
  </script>

</body>
</html>
