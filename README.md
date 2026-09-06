<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Portfolio & Journey</title>
  <style>
    :root {
      --bg: #0f172a;
      --card-bg: #1e293b;
      --accent: #38bdf8;
      --text: #f8fafc;
      --muted: #94a3b8;
      --border: #334155;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    }

    body {
      background-color: var(--bg);
      color: var(--text);
      line-height: 1.6;
      padding: 0 1.5rem;
    }

    .container {
      max-width: 800px;
      margin: 0 auto;
      padding: 4rem 0;
    }

    /* Hero Section */
    .hero {
      text-align: center;
      margin-bottom: 5rem;
    }

    .avatar {
      width: 110px;
      height: 110px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--accent), #818cf8);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2.2rem;
      font-weight: bold;
      color: var(--bg);
      margin: 0 auto 1.5rem;
    }

    h1 {
      font-size: 2.5rem;
      margin-bottom: 0.5rem;
    }

    .tagline {
      color: var(--accent);
      font-weight: 500;
      font-size: 1.1rem;
      margin-bottom: 1rem;
    }

    .bio {
      color: var(--muted);
      max-width: 550px;
      margin: 0 auto 1.5rem;
    }

    .cta-btn {
      display: inline-block;
      padding: 0.7rem 1.4rem;
      background: var(--accent);
      color: var(--bg);
      border-radius: 8px;
      text-decoration: none;
      font-weight: 600;
      transition: opacity 0.2s ease;
    }

    .cta-btn:hover {
      opacity: 0.9;
    }

    /* Section Headings */
    .section-title {
      font-size: 1.6rem;
      margin-bottom: 2rem;
      border-bottom: 1px solid var(--border);
      padding-bottom: 0.5rem;
    }

    /* Timeline / Journey */
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
      top: 0.3rem;
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background: var(--accent);
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
      font-size: 1.2rem;
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
      border: 1px solid var(--border);
      padding: 1.5rem;
      border-radius: 10px;
    }

    .project-title {
      font-size: 1.15rem;
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
      padding: 0.2rem 0.55rem;
      border-radius: 4px;
    }

    /* Footer */
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
    }
  </style>
</head>
<body>

  <div class="container">
    <header class="hero">
      <div class="avatar">S</div>
      <h1>Shakti</h1>
      <p class="tagline">Creator & Tech Enthusiast</p>
      <p class="bio">Passionate about building digital experiences, exploring creative media, and solving technical challenges.</p>
      <a href="mailto:your-email@example.com" class="cta-btn">Get In Touch</a>
    </header>

    <section>
      <h2 class="section-title">My Journey</h2>
      <div class="timeline">
        <div class="timeline-item">
          <div class="timeline-year">2026 — Present</div>
          <div class="timeline-title">Exploring Advanced Tech & Case Studies</div>
          <p class="timeline-desc">Diving into data environments, technical problem solving, and analytical strategy projects.</p>
        </div>

        <div class="timeline-item">
          <div class="timeline-year">2025 — 2026</div>
          <div class="timeline-title">Creative Media & Digital Design</div>
          <p class="timeline-desc">Experimented with visual design, generative AI workflows, and cinematic poster layouts under custom branding projects.</p>
        </div>

        <div class="timeline-item">
          <div class="timeline-year">2024 — 2025</div>
          <div class="timeline-title">Foundations & Academic Milestones</div>
          <p class="timeline-desc">Strengthened analytical foundations in science and higher mathematics, sparking an interest in coding and logic.</p>
        </div>
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
          <p class="project-desc">Crafted unique visual graphics, custom typography overlays, and cinematic art concepts.</p>
          <div class="tags">
            <span class="tag">Design</span>
            <span class="tag">AI Media</span>
          </div>
        </div>
      </div>
    </section>

    <footer>
      <p>© 2026 Shakti. Built with HTML & CSS.</p>
    </footer>
  </div>

</body>
</html>
