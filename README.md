 <html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Shakti | Portfolio & Journey</title>
  <style>
    :root {
      --bg: #0b0f19;
      --card-bg: rgba(22, 30, 46, 0.75);
      --accent: #38bdf8;
      --text: #f8fafc;
      --muted: #94a3b8;
      --border: rgba(255, 255, 255, 0.12);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    }

    body {
      color: var(--text);
      line-height: 1.6;
      padding: 0 1.5rem;
      min-height: 100vh;
      /* Background Image Overlay */
      background: linear-gradient(rgba(11, 15, 25, 0.88), rgba(11, 15, 25, 0.92)),
                  url('https://images.unsplash.com/photo-1518709268805-4e9042af9f23?q=80&w=1920&auto=format&fit=crop') center/cover no-repeat fixed;
    }

    .container {
      max-width: 850px;
      margin: 0 auto;
      padding: 4rem 0;
    }

    /* Hero Section */
    .hero {
      text-align: center;
      margin-bottom: 5rem;
    }

    /* Ring-Light RGB Neon Glow Animation */
    @keyframes rgbGlow {
      0% {
        box-shadow: 0 0 20px #ff0055, inset 0 0 15px #ff0055;
        border-color: #ff0055;
      }
      25% {
        box-shadow: 0 0 20px #00f2fe, inset 0 0 15px #00f2fe;
        border-color: #00f2fe;
      }
      50% {
        box-shadow: 0 0 20px #4facfe, inset 0 0 15px #4facfe;
        border-color: #4facfe;
      }
      75% {
        box-shadow: 0 0 20px #fa709a, inset 0 0 15px #fa709a;
        border-color: #fa709a;
      }
      100% {
        box-shadow: 0 0 20px #ff0055, inset 0 0 15px #ff0055;
        border-color: #ff0055;
      }
    }

    /* Color Shift for Gradient Text */
    @keyframes textColorShift {
      0% { filter: hue-rotate(0deg); }
      50% { filter: hue-rotate(180deg); }
      100% { filter: hue-rotate(360deg); }
    }

    /* Animated Avatar Ring Light */
    .avatar {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      background: #0f172a;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 1.5rem;
      border: 3px solid #ff0055;
      animation: rgbGlow 6s linear infinite;
    }

    .avatar-letter {
      font-size: 3rem;
      font-weight: 800;
      background: linear-gradient(135deg, #ff007f, #7928ca, #00f2fe);
      background-size: 200% 200%;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      animation: textColorShift 5s ease infinite;
    }

    /* Animated Gradient Name */
    .name-glow {
      font-size: 3rem;
      font-weight: 900;
      margin-bottom: 0.5rem;
      letter-spacing: -0.5px;
      background: linear-gradient(90deg, #ff007f, #4facfe, #00f2fe, #f093fb, #ff007f);
      background-size: 300% 300%;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      animation: textColorShift 5s ease infinite alternate;
    }

    .tagline {
      color: var(--accent);
      font-weight: 500;
      font-size: 1.15rem;
      margin-bottom: 1rem;
    }

    .bio {
      color: var(--muted);
      max-width: 580px;
      margin: 0 auto 1.8rem;
    }

    .cta-btn {
      display: inline-block;
      padding: 0.75rem 1.6rem;
      background: rgba(56, 189, 248, 0.1);
      color: #38bdf8;
      border: 1px solid #38bdf8;
      border-radius: 8px;
      text-decoration: none;
      font-weight: 600;
      transition: all 0.3s ease;
    }

    .cta-btn:hover {
      background: #38bdf8;
      color: #0b0f19;
      box-shadow: 0 0 15px rgba(56, 189, 248, 0.6);
    }

    /* Section Titles */
    .section-title {
      font-size: 1.6rem;
      margin-bottom: 2rem;
      border-bottom: 1px solid var(--border);
      padding-bottom: 0.5rem;
    }

    /* Journey Timeline */
    .timeline {
      position: relative;
      border-left: 2px solid var(--border);
      margin-left: 1rem;
      padding-left: 1.5rem;
      margin-bottom: 5rem;
    }

    .timeline-item {
      position: relative;
      margin-bottom: 2.5rem;
    }

    .timeline-item::before {
      content: '';
      position: absolute;
      left: -1.95rem;
      top: 0.35rem;
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background: var(--accent);
      box-shadow: 0 0 10px var(--accent);
      border: 3px solid var(--bg);
    }

    .timeline-year {
      font-size: 0.85rem;
      color: var(--accent);
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 0.05em;
    }

    .timeline-title {
      font-size: 1.25rem;
      font-weight: 600;
      margin: 0.2rem 0;
    }

    .timeline-desc {
      color: var(--muted);
      font-size: 0.95rem;
    }

    /* Projects Grid */
    .projects-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1.5rem;
      margin-bottom: 5rem;
    }

    .project-card {
      background: var(--card-bg);
      backdrop-filter: blur(10px);
      border: 1px solid var(--border);
      padding: 1.5rem;
      border-radius: 12px;
      transition: transform 0.2s ease, border-color 0.2s ease;
    }

    .project-card:hover {
      transform: translateY(-4px);
      border-color: rgba(56, 189, 248, 0.4);
    }

    .project-title {
      font-size: 1.2rem;
      font-weight: 600;
      margin-bottom: 0.5rem;
    }

    .project-desc {
      color: var(--muted);
      font-size: 0.9rem;
      margin-bottom: 1rem;
    }

    .tags {
      display: flex;
      flex-wrap: wrap;
      gap: 0.5rem;
    }

    .tag {
      font-size: 0.75rem;
      background: rgba(56, 189, 248, 0.1);
      color: var(--accent);
      padding: 0.25rem 0.6rem;
      border-radius: 4px;
    }

    footer {
      text-align: center;
      color: var(--muted);
      font-size: 0.85rem;
      border-top: 1px solid var(--border);
      padding-top: 2rem;
    }

    @media (max-width: 600px) {
      .projects-grid {
        grid-template-columns: 1fr;
      }
      .name-glow {
        font-size: 2.3rem;
      }
    }
  </style>
</head>
<body>

  <div class="container">
    <header class="hero">
      <!-- Animated S Avatar with Ring Glow -->
      <div class="avatar">
        <span class="avatar-letter">S k</span>
      </div>

      <!-- Animated Name -->
      <h1 class="name-glow"> Shahil </h1>
      <p class="tagline">Creator & Tech Enthusiast</p>
      <p class="bio">Passionate about building digital experiences, exploring creative media, and solving technical challenges.</p>
      <a href="mailto:your-email@example.com" class="cta-btn">Get In Touch</a>
    </header>

    <section>
      <h2 class="section-title">My Journey</h2>
      <div class="timeline">
        <div class="timeline-item">
          <div class="timeline-year">2026->june — Present</div>
          <div class="timeline-title">Exploring Advanced Tech & Case Studies</div>
          <p class="timeline-desc">Diving into data environments, technical problem solving, and analytical strategy projects.</p>
        </div>

        <div class="timeline-item">
          <div class="timeline-year">2025 — 2026</div>
          <div class="timeline-title">Creative Media & Digital Design</div>
          <p class="timeline-desc">Experimented with visual design, generative media workflows, and custom digital branding layouts.</p>
        </div>

        <div class="timeline-item">
          <div class="timeline-year">2024 — 2025</div>
          <div class="timeline-title">Foundations & Academic Milestones</div>
          <p class="timeline-desc">Strengthened analytical foundations in science and higher mathematics, sparking an interest in code and logic.</p>
          </div>

        <div class="timeline-item">
           <div class="timeline-year">2024-my born</div>
           <div class ="timeline-year"> I come from a small Tier-3 village and a humble background. i studied in a government school and i am now pursuing mu education at a government college. my jounrney has been simple but it was taught  me to dream big and keep moving forward.  
      </div>
      
    </section>

    <section>
      <h2 class="section-title">Featured Highlights</h2>
      <div class="projects-grid">
        <div class="project-card">
          <div class="project-title">Strategy & Analytical Deck</div>
          <p class="project-desc">A deep dive into ecosystem growth, financial modeling, and structured case analysis.</p>
          <div class="tags">
            <span class="tag">Strategy</span>
            <span class="tag">Analytics</span>
          </div>
        </div>

        <div class="project-card">
          <div class="project-title">Creative Digital Branding</div>
          <p class="project-desc">Crafted unique visual graphics, custom typography overlays, and cinematic digital concepts.</p>
          <div class="tags">
            <span class="tag">Design</span>
            <span class="tag">Media</span>
          </div>
        </div>
      </div>
    </section>

    <footer>
      <p>© 2026 Shahil. All rights reserved.</p>
    </footer>
  </div>

</body>
</html>
