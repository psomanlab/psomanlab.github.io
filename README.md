<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Modular Assembly — Cell-seeded 3D Printed Hydrogel Modules</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Source+Serif+4:ital,opsz,wght@0,8..60,300;0,8..60,400;0,8..60,600;0,8..60,700;1,8..60,400&family=IBM+Plex+Sans:wght@300;400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg: #faf9f6;
      --bg-alt: #f0eee9;
      --text: #1a1a1a;
      --text-muted: #5c5c5c;
      --accent: #2c5f8a;
      --accent-dark: #1d3f5c;
      --accent-light: #e8f0f7;
      --border: #d4d0c8;
      --white: #ffffff;
      --serif: 'Source Serif 4', Georgia, serif;
      --sans: 'IBM Plex Sans', -apple-system, sans-serif;
      --mono: 'IBM Plex Mono', monospace;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      font-family: var(--sans);
      font-weight: 400;
      color: var(--text);
      background: var(--bg);
      line-height: 1.7;
      font-size: 16px;
    }

    /* ---- NAV ---- */
    nav {
      position: sticky;
      top: 0;
      z-index: 100;
      background: rgba(250, 249, 246, 0.92);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
    }
    nav .nav-inner {
      max-width: 1100px;
      margin: 0 auto;
      padding: 0.75rem 2rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 1.5rem;
    }
    nav .nav-brand {
      font-family: var(--serif);
      font-weight: 600;
      font-size: 1rem;
      color: var(--accent-dark);
      text-decoration: none;
      letter-spacing: -0.02em;
    }
    nav .nav-links {
      display: flex;
      gap: 1.75rem;
      list-style: none;
    }
    nav .nav-links a {
      text-decoration: none;
      color: var(--text-muted);
      font-size: 0.85rem;
      font-weight: 500;
      letter-spacing: 0.03em;
      text-transform: uppercase;
      transition: color 0.2s;
    }
    nav .nav-links a:hover { color: var(--accent); }

    /* ---- HERO ---- */
    .hero {
      max-width: 1100px;
      margin: 0 auto;
      padding: 5rem 2rem 3.5rem;
    }
    .hero .lab-tag {
      display: inline-block;
      font-family: var(--mono);
      font-size: 0.78rem;
      font-weight: 500;
      color: var(--accent);
      background: var(--accent-light);
      padding: 0.3rem 0.75rem;
      border-radius: 4px;
      margin-bottom: 1.25rem;
      letter-spacing: 0.04em;
    }
    .hero h1 {
      font-family: var(--serif);
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 700;
      line-height: 1.2;
      letter-spacing: -0.025em;
      color: var(--text);
      max-width: 850px;
      margin-bottom: 1.5rem;
    }
    .hero .subtitle {
      font-size: 1.1rem;
      color: var(--text-muted);
      max-width: 720px;
      line-height: 1.75;
    }
    .hero .subtitle a {
      color: var(--accent);
      text-decoration: underline;
      text-underline-offset: 3px;
    }

    /* ---- SECTION COMMON ---- */
    section {
      max-width: 1100px;
      margin: 0 auto;
      padding: 3rem 2rem;
    }
    section + section { padding-top: 1rem; }

    .section-label {
      font-family: var(--mono);
      font-size: 0.72rem;
      font-weight: 500;
      text-transform: uppercase;
      letter-spacing: 0.12em;
      color: var(--accent);
      margin-bottom: 0.5rem;
    }
    h2 {
      font-family: var(--serif);
      font-size: 1.75rem;
      font-weight: 600;
      letter-spacing: -0.02em;
      margin-bottom: 1.25rem;
      color: var(--text);
    }

    /* ---- CONTENTS GRID ---- */
    .contents-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.25rem;
      margin-top: 1.5rem;
    }
    .contents-card {
      background: var(--white);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 1.5rem;
      transition: box-shadow 0.25s, transform 0.25s;
    }
    .contents-card:hover {
      box-shadow: 0 4px 20px rgba(0,0,0,0.06);
      transform: translateY(-2px);
    }
    .contents-card h3 {
      font-family: var(--sans);
      font-weight: 600;
      font-size: 1rem;
      margin-bottom: 0.5rem;
      color: var(--text);
    }
    .contents-card p {
      font-size: 0.9rem;
      color: var(--text-muted);
      line-height: 1.6;
    }
    .contents-card .card-link {
      display: inline-flex;
      align-items: center;
      gap: 0.35rem;
      margin-top: 0.85rem;
      font-size: 0.85rem;
      font-weight: 500;
      color: var(--accent);
      text-decoration: none;
    }
    .contents-card .card-link:hover { text-decoration: underline; }
    .card-icon {
      width: 36px;
      height: 36px;
      border-radius: 8px;
      background: var(--accent-light);
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: 0.85rem;
      font-size: 1.1rem;
    }

    /* ---- VIDEOS ---- */
    .video-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
      gap: 1.5rem;
      margin-top: 1.5rem;
    }
    .video-card {
      background: var(--white);
      border: 1px solid var(--border);
      border-radius: 8px;
      overflow: hidden;
    }
    .video-card video {
      width: 100%;
      display: block;
      background: #000;
    }
    .video-card .video-caption {
      padding: 1rem 1.25rem;
      font-size: 0.9rem;
      color: var(--text-muted);
    }
    .video-card .video-caption strong {
      color: var(--text);
    }

    /* ---- TABLE ---- */
    .table-wrapper {
      overflow-x: auto;
      margin-top: 1.5rem;
      border: 1px solid var(--border);
      border-radius: 8px;
      background: var(--white);
    }
    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.88rem;
    }
    thead {
      background: var(--accent-light);
    }
    th {
      font-weight: 600;
      text-align: left;
      padding: 0.75rem 1rem;
      white-space: nowrap;
      border-bottom: 2px solid var(--border);
      font-size: 0.82rem;
      letter-spacing: 0.02em;
    }
    td {
      padding: 0.65rem 1rem;
      border-bottom: 1px solid #eae8e3;
    }
    tbody tr:last-child td { border-bottom: none; }
    tbody tr:hover { background: #faf8f5; }
    td a {
      color: var(--accent);
      text-decoration: none;
      font-weight: 500;
    }
    td a:hover { text-decoration: underline; }

    /* ---- MODIFICATIONS ---- */
    .mod-list {
      margin-top: 1.25rem;
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }
    .mod-item {
      background: var(--white);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 1.25rem 1.5rem;
    }
    .mod-item h4 {
      font-weight: 600;
      font-size: 0.95rem;
      margin-bottom: 0.4rem;
      color: var(--text);
    }
    .mod-item p {
      font-size: 0.9rem;
      color: var(--text-muted);
      line-height: 1.65;
    }
    .mod-item a {
      color: var(--accent);
      text-decoration: underline;
      text-underline-offset: 2px;
    }
    .mod-item ul {
      margin-top: 0.5rem;
      padding-left: 1.25rem;
      font-size: 0.88rem;
      color: var(--text-muted);
      line-height: 1.7;
    }
    .mod-item ul a { font-size: 0.88rem; }

    /* ---- FOOTER ---- */
    footer {
      max-width: 1100px;
      margin: 0 auto;
      padding: 3rem 2rem;
      border-top: 1px solid var(--border);
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 1rem;
    }
    footer p {
      font-size: 0.82rem;
      color: var(--text-muted);
    }
    footer a {
      color: var(--accent);
      text-decoration: none;
    }
    footer a:hover { text-decoration: underline; }

    /* ---- RESPONSIVE ---- */
    @media (max-width: 640px) {
      .hero { padding: 3rem 1.25rem 2rem; }
      section { padding: 2rem 1.25rem; }
      nav .nav-inner { padding: 0.6rem 1.25rem; }
      nav .nav-links { gap: 1rem; }
      nav .nav-links a { font-size: 0.78rem; }
      .video-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <div class="nav-inner">
      <a href="#" class="nav-brand">Modular Assembly</a>
      <ul class="nav-links">
        <li><a href="#contents">Contents</a></li>
        <li><a href="#videos">Videos</a></li>
        <li><a href="#bom">BOM</a></li>
        <li><a href="#modifications">Modifications</a></li>
      </ul>
    </div>
  </nav>

  <!-- HERO -->
  <header class="hero">
    <span class="lab-tag">psomanlab</span>
    <h1>Assembly of Cell-seeded 3D Printed Hydrogel Modules with Perfusable Channel Networks</h1>
    <p class="subtitle">
      This repository contains all the files and information needed to fabricate and customize multimaterial perfusion bioreactors. 
      Browse CAD models, print profiles, assembly videos, and a complete bill of materials below.
      <br><br>
      <a href="https://github.com/psomanlab/Modular-Assembly" target="_blank">View on GitHub &rarr;</a>
    </p>
  </header>

  <!-- CONTENTS -->
  <section id="contents">
    <p class="section-label">Repository Contents</p>
    <h2>What&rsquo;s Included</h2>
    <div class="contents-grid">
      <div class="contents-card">
        <div class="card-icon">&#9881;</div>
        <h3>Bioreactor CAD Models</h3>
        <p>STEP format CAD models for all printable bioreactor parts (all sizes in one file), plus 3MF project files with print profiles for Prusament PCCF and Recreus FilaFlex Pro 60A on the 5-Toolhead Prusa XL.</p>
        <a class="card-link" href="https://github.com/psomanlab/Modular-Assembly/tree/main/Bioreactors" target="_blank">
          Browse files &rarr;
        </a>
      </div>
      <div class="contents-card">
        <div class="card-icon">&#128295;</div>
        <h3>Printed Tools</h3>
        <p>STEP format CAD models for bioreactor racks, bioreactor shims, module slicing jig, and other assembly tools.</p>
        <a class="card-link" href="https://github.com/psomanlab/Modular-Assembly/tree/main/Tools" target="_blank">
          Browse files &rarr;
        </a>
      </div>
      <div class="contents-card">
        <div class="card-icon">&#127916;</div>
        <h3>Supplementary Videos</h3>
        <p>Video documentation of bioreactor assembly, perfusion, and module fabrication processes.</p>
        <a class="card-link" href="#videos">
          Watch below &darr;
        </a>
      </div>
    </div>
  </section>

  <!-- VIDEOS -->
  <section id="videos">
    <p class="section-label">Supplementary Information</p>
    <h2>Videos</h2>
    <p style="color: var(--text-muted); font-size: 0.95rem; margin-bottom: 0.5rem;">
      Supplementary video files from the publication are embedded below.
    </p>

    <div class="video-grid">

      <!--
        ============================================================
        TO CONFIGURE: Replace the <source src="..."> paths below
        with the actual filenames from your Videos/ folder.

        The src should be a relative path from this index.html,
        e.g., "Videos/Movie_S1.mp4"

        Add or remove <div class="video-card"> blocks as needed
        to match the number of videos in your repo.
        ============================================================
      -->

      <div class="video-card">
        <video controls preload="metadata">
          <source src="Videos/Video_S1.mp4" type="video/mp4">
          Your browser does not support the video tag.
        </video>
        <div class="video-caption">
          <strong>Video S1</strong> &mdash; Update this caption to describe the video content.
        </div>
      </div>

      <div class="video-card">
        <video controls preload="metadata">
          <source src="Videos/Video_S2.mp4" type="video/mp4">
          Your browser does not support the video tag.
        </video>
        <div class="video-caption">
          <strong>Video S2</strong> &mdash; Update this caption to describe the video content.
        </div>
      </div>

      <div class="video-card">
        <video controls preload="metadata">
          <source src="Videos/Video_S3.mp4" type="video/mp4">
          Your browser does not support the video tag.
        </video>
        <div class="video-caption">
          <strong>Video S3</strong> &mdash; Update this caption to describe the video content.
        </div>
      </div>

    </div>
  </section>

  <!-- BOM -->
  <section id="bom">
    <p class="section-label">Bill of Materials</p>
    <h2>Bioreactor BOM by Size</h2>
    <div class="table-wrapper">
      <table>
        <thead>
          <tr>
            <th>Bioreactor</th>
            <th><a href="https://www.mcmaster.com/91292A112/" target="_blank">M3&times;8 SHCS</a></th>
            <th><a href="https://www.mcmaster.com/91292A020/" target="_blank">M3&times;25 SHCS</a></th>
            <th><a href="https://www.mcmaster.com/91292A022/" target="_blank">M3&times;30 SHCS</a></th>
            <th><a href="https://www.mcmaster.com/97259A101/" target="_blank">M3 Square Nut</a></th>
            <th><a href="https://www.mcmaster.com/97700A110/" target="_blank">M3 Hex Nut</a></th>
            <th><a href="https://bolioptics.com/25pc-plane-slide-microscope-slide-glass-slides-3mm-25pc-sl39103102/" target="_blank">3mm Glass Slide</a></th>
            <th>3mm Laser Cut Acrylic</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>1&times;1</td><td>8</td><td>4</td><td>&mdash;</td><td>8</td><td>4</td><td>2</td><td>&mdash;</td></tr>
          <tr><td>2&times;1</td><td>8</td><td>4</td><td>&mdash;</td><td>8</td><td>4</td><td>2</td><td>&mdash;</td></tr>
          <tr><td>3&times;1</td><td>12</td><td>4</td><td>&mdash;</td><td>12</td><td>4</td><td>2</td><td>&mdash;</td></tr>
          <tr><td>2&times;2</td><td>16</td><td>4</td><td>&mdash;</td><td>16</td><td>4</td><td>&mdash;</td><td>2 (35 &times; 35 mm)</td></tr>
          <tr><td>2&times;3</td><td>16</td><td>4</td><td>&mdash;</td><td>16</td><td>4</td><td>&mdash;</td><td>2 (45 &times; 35 mm)</td></tr>
          <tr><td>3&times;3</td><td>16</td><td>4</td><td>&mdash;</td><td>16</td><td>4</td><td>&mdash;</td><td>2 (45 &times; 45 mm)</td></tr>
          <tr><td>3&times;6</td><td>24</td><td>&mdash;</td><td>6</td><td>24</td><td>6</td><td>&mdash;</td><td>2 (75 &times; 45 mm)</td></tr>
        </tbody>
      </table>
    </div>
    <p style="margin-top: 0.75rem; font-size: 0.82rem; color: var(--text-muted);">
      All screws are DIN 912 (SHCS). Square nuts are DIN 562; hex nuts are DIN 934. Click column headers for sourcing links.
    </p>
  </section>

  <!-- MODIFICATIONS -->
  <section id="modifications">
    <p class="section-label">Printer Setup</p>
    <h2>Prusa XL Modifications</h2>
    <p style="color: var(--text-muted); font-size: 0.95rem; margin-bottom: 0.25rem;">
      Minor modifications were required to enable printing of Prusament PCCF and Recreus FilaFlex 60A on the Prusa XL.
    </p>
    <div class="mod-list">
      <div class="mod-item">
        <h4>Nozzles</h4>
        <p>All nozzles were replaced with wear-resistant 0.4&nbsp;mm E3D ObXidian nozzles for PCCF printing. Standard flow nozzles were used, but high flow variants will also work. Phaetus SiC nozzles are not recommended for PCCF due to high nozzle buildup.</p>
      </div>
      <div class="mod-item">
        <h4>Enclosure</h4>
        <p>The official Prusa XL enclosure was installed for printing warp-prone materials. This may not be a firm requirement, but it helps with filament path modification.</p>
      </div>
      <div class="mod-item">
        <h4>Filament Path (Toolhead 5 &mdash; TPU)</h4>
        <p>To print Shore 60A TPU, the standard filament path must be modified to reduce friction and eliminate gaps:</p>
        <ul>
          <li>Toolhead 5 was modified with a <a href="https://www.printables.com/model/1486985-xl-nextruder-main-plate-for-bogie-idler-with-load" target="_blank">main plate</a> and <a href="https://www.printables.com/model/1365827-mk4s-xl-core-one-bogie-idler-with-more-pivot" target="_blank">idler lever</a> featuring a more constrained filament path.</li>
          <li>The filament sensor spring was replaced with two small magnets. <a href="https://www.printables.com/model/975519-xl-nextruder-super-constrained-main-plateidler-lev" target="_blank">Instructions here.</a></li>
          <li>The side-mounted filament sensor and PTFE tube were bypassed. Filament was fed via a <a href="https://www.printables.com/model/128189-magnetic-mounted-spool-holder" target="_blank">magnetic spool holder</a> on the enclosure top, through an empty rivet hole.</li>
          <li>Short PTFE tubing segments were clipped to the cable harness with <a href="https://www.printables.com/model/718498-prusa-xl-soft-tpu-cable-clip-to-extruder-prusa-xl" target="_blank">modified cable clips</a>.</li>
          <li><a href="https://www.printables.com/model/894119-diy-silicone-tube-nozzle-wiper-prusa-xl-mounting-h" target="_blank">Nozzle wipers</a> made from silicone tubing were installed for tool changes.</li>
        </ul>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <p>&copy; 2025 <a href="https://github.com/psomanlab" target="_blank">psomanlab</a>. Released under the repository license.</p>
    <p><a href="https://github.com/psomanlab/Modular-Assembly" target="_blank">GitHub Repository</a></p>
  </footer>

</body>
</html>
