<!DOCTYPE html>
<html lang="en" class="dark">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>S. Rahul Kumar — Autonomous Engineering Portfolio</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=Inter:wght@300;400;500;600;700;800;900&family=JetBrains+Mono:wght@400;500;600;700&display=swap" rel="stylesheet">
  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          fontFamily: {
            sans: ['Inter', 'system-ui', 'sans-serif'],
            mono: ['JetBrains Mono', 'monospace'],
            serif: ['Instrument Serif', 'Georgia', 'serif']
          },
          colors: {
            void: '#040406',
            card: '#0a0a0e',
            crimson: '#ff1e1e',
            blueprint: '#ff1e1e'
          }
        }
      }
    }
  </script>
  <style>
    :root { color-scheme: dark; }
    body {
      background-color: #040406;
      color: #f4f4f6;
      font-family: 'Inter', sans-serif;
      overflow-x: hidden;
    }
    ::selection { background: #ff1e1e; color: #ffffff; }

    /* Giant Outlined PORTFOLIO Title (00:02 - 00:05) */
    .portfolio-giant {
      font-family: 'Inter', sans-serif;
      font-weight: 900;
      letter-spacing: -0.045em;
      color: rgba(255, 30, 30, 0.06);
      -webkit-text-stroke: 2px #ff1e1e;
      text-shadow: 0 0 60px rgba(255, 30, 30, 0.22);
      line-height: 0.84;
      user-select: none;
    }
    @media (max-width: 640px) {
      .portfolio-giant { -webkit-text-stroke: 1.3px #ff1e1e; }
    }

    .arch-card {
      background: linear-gradient(180deg, rgba(14, 14, 19, 0.92) 0%, rgba(8, 8, 12, 0.96) 100%);
      border: 1px solid rgba(255, 255, 255, 0.07);
      transition: border-color 0.25s ease, box-shadow 0.25s ease;
    }
    .arch-card:hover {
      border-color: rgba(255, 30, 30, 0.42);
      box-shadow: 0 12px 40px -12px rgba(255, 30, 30, 0.16);
    }

    .red-left-accent { border-left: 2.5px solid #ff1e1e; }

    .red-underline {
      color: #ffffff;
      font-weight: 600;
      text-decoration: underline;
      text-decoration-color: #ff1e1e;
      text-underline-offset: 4px;
      text-decoration-thickness: 1.5px;
    }

    /* =========================================================
       STRICT CURSOR-FIRST DRAG-TO-OPEN STATES (Zero Preloading!)
       ========================================================= */
    [data-construct] {
      position: relative;
    }
    /* Before cursor arrives: 100% invisible (zero border, zero background, zero text) */
    [data-construct]:not(.building):not(.built),
    [data-construct].unbuilt {
      opacity: 0 !important;
      pointer-events: none !important;
    }

    /* While cursor is actively dragging the box: parent is transparent, ONLY the wireframe box is visible! */
    [data-construct].building {
      opacity: 1 !important;
      border-color: transparent !important;
      border-left-color: transparent !important;
      background: transparent !important;
      box-shadow: none !important;
    }
    [data-construct].building > *:not(.wireframe-overlay) {
      opacity: 0 !important;
      visibility: hidden !important;
    }

    /* Only AFTER the cursor finishes dragging the wireframe box to 100% does the content open! */
    [data-construct].built {
      opacity: 1 !important;
      animation: popOpenNode 0.28s cubic-bezier(0.16, 1, 0.3, 1) forwards;
    }
    [data-construct].built > *:not(.wireframe-overlay) {
      opacity: 1 !important;
      visibility: visible !important;
    }
    @keyframes popOpenNode {
      0% { opacity: 0; transform: scale(0.97) translateY(4px); }
      100% { opacity: 1; transform: scale(1) translateY(0); }
    }

    /* Wireframe Selection Box Drawn Dynamically by the Cursor */
    .wireframe-overlay {
      position: absolute;
      top: -2px;
      left: -2px;
      width: var(--wf-w, 100%);
      height: var(--wf-h, 100%);
      border: 1.5px solid #ff1e1e;
      background: rgba(255, 30, 30, 0.08);
      pointer-events: none;
      z-index: 30;
      opacity: 0;
    }
    [data-construct].building > .wireframe-overlay {
      opacity: 1;
    }
    .wf-corner {
      position: absolute;
      width: 6px;
      height: 6px;
      background: #ffffff;
      border: 1.5px solid #ff1e1e;
    }
    .wf-tl { top: -3.5px; left: -3.5px; }
    .wf-tr { top: -3.5px; right: -3.5px; }
    .wf-bl { bottom: -3.5px; left: -3.5px; }
    .wf-br { bottom: -3.5px; right: -3.5px; }
    .wf-tag {
      position: absolute;
      bottom: -18px;
      left: 0;
      background: #ff1e1e;
      color: #ffffff;
      font-family: 'JetBrains Mono', monospace;
      font-size: 8px;
      font-weight: 700;
      padding: 1px 5px;
      border-radius: 2px;
      white-space: nowrap;
      letter-spacing: 0.04em;
    }
    .wf-progress {
      position: absolute;
      left: 10%;
      right: 10%;
      top: 50%;
      height: 4px;
      transform: translateY(-50%);
      background: rgba(255, 255, 255, 0.08);
      border-radius: 2px;
      overflow: hidden;
    }
    .wf-progress-bar {
      height: 100%;
      background: linear-gradient(90deg, #ff1e1e, #ff5252);
      width: 0%;
      transition: width 0.55s linear;
    }
    [data-construct].building .wf-progress-bar {
      width: 100%;
    }

    /* Bold, Unique Cybernetic Page & Profile Links */
    .cyber-nav-link {
      position: relative;
      font-family: 'JetBrains Mono', monospace;
      font-weight: 800;
      font-size: 11px;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: #e4e4e7;
      padding: 6px 12px;
      border-radius: 6px;
      border: 1px solid rgba(255, 255, 255, 0.08);
      background: rgba(255, 255, 255, 0.02);
      transition: all 0.22s cubic-bezier(0.16, 1, 0.3, 1);
    }
    .cyber-nav-link:hover,
    .cyber-nav-link.active {
      color: #ffffff;
      background: linear-gradient(135deg, rgba(255, 30, 30, 0.22) 0%, rgba(255, 30, 30, 0.06) 100%);
      border-color: rgba(255, 30, 30, 0.65);
      box-shadow: 0 0 20px rgba(255, 30, 30, 0.28);
      transform: translateY(-1px);
    }

    .cyber-social-card {
      position: relative;
      overflow: hidden;
      background: linear-gradient(135deg, rgba(20, 20, 28, 0.95) 0%, rgba(10, 10, 15, 0.98) 100%);
      border: 1.5px solid rgba(255, 30, 30, 0.35);
      box-shadow: 0 8px 30px -10px rgba(255, 30, 30, 0.22);
      transition: all 0.25s cubic-bezier(0.16, 1, 0.3, 1);
    }
    .cyber-social-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 4px;
      height: 100%;
      background: #ff1e1e;
      box-shadow: 0 0 12px #ff1e1e;
    }
    .cyber-social-card:hover {
      border-color: #ff1e1e;
      background: linear-gradient(135deg, rgba(255, 30, 30, 0.18) 0%, rgba(14, 14, 20, 0.98) 100%);
      box-shadow: 0 14px 40px -8px rgba(255, 30, 30, 0.42);
      transform: translateY(-3px) scale(1.015);
    }

    /* Tab Click Pulse Highlight when Cursor Clicks a Tab */
    .cursor-clicking-tab {
      outline: 2px solid #ff1e1e !important;
      box-shadow: 0 0 22px rgba(255, 30, 30, 0.75) !important;
      transform: scale(0.96);
    }

    ::-webkit-scrollbar { width: 5px; height: 5px; }
    ::-webkit-scrollbar-track { background: #040406; }
    ::-webkit-scrollbar-thumb { background: #22222a; border-radius: 3px; }
    ::-webkit-scrollbar-thumb:hover { background: #ff1e1e; }
  </style>
</head>
<body class="bg-void text-zinc-100 antialiased relative min-h-screen">

  <!-- =========================================================
       INTRO BOOT OVERLAY (Matches 00:00 - 00:01 Circle & Counter)
       ========================================================= -->
  <div id="bootOverlay" class="fixed inset-0 z-40 bg-void flex flex-col items-center justify-center gap-4 transition-opacity duration-500 cursor-pointer">
    <div class="w-12 h-12 rounded border border-white/20 bg-zinc-900/80 flex items-center justify-center font-mono text-xs text-zinc-300 shadow-[0_0_30px_rgba(255,30,30,0.2)]">
      <span id="bootCounter">100</span>
    </div>
    <div class="font-mono text-[10px] tracking-widest uppercase text-crimson animate-pulse">
      [ CLICK ANYWHERE FOR HACKER SYNTH AUDIO ]
    </div>
  </div>

  <!-- AUTONOMOUS UI-BUILDER & TAB-CLICKER CURSOR CANVAS -->
  <canvas id="agentCursorCanvas" class="fixed inset-0 pointer-events-none z-50"></canvas>

  <!-- Ambient Crimson Backdrop -->
  <div class="fixed inset-0 pointer-events-none z-0 overflow-hidden">
    <div class="absolute -top-36 left-1/3 w-[600px] h-[600px] bg-crimson/10 rounded-full blur-[160px]"></div>
    <div class="absolute bottom-10 right-1/4 w-[450px] h-[450px] bg-crimson/5 rounded-full blur-[150px]"></div>
  </div>

  <!-- =========================================================
       TOP NAVIGATION BAR (Matches 00:04 - 00:56)
       ========================================================= -->
  <header class="fixed top-0 left-0 right-0 z-30 bg-void/85 backdrop-blur-md border-b border-white/[0.06]">
    <div class="max-w-[1240px] mx-auto px-5 sm:px-8 h-14 flex items-center justify-between">
      <a href="#home" class="flex items-center gap-2.5">
        <span class="w-4 h-4 rounded-[3px] bg-crimson inline-block shadow-[0_0_12px_#ff1e1e]"></span>
        <span class="font-sans font-black text-xs tracking-wider uppercase text-white">RAHUL.</span>
      </a>

      <nav class="hidden md:flex items-center gap-2.5">
        <a href="#home" class="cyber-nav-link active"><span class="text-crimson mr-1">01.</span>Home</a>
        <a href="#about" class="cyber-nav-link"><span class="text-crimson mr-1">02.</span>About</a>
        <a href="#flagships" class="cyber-nav-link"><span class="text-crimson mr-1">03.</span>Flagships</a>
        <a href="#matrix" class="cyber-nav-link"><span class="text-crimson mr-1">04.</span>Matrix</a>
        <a href="#contact" class="cyber-nav-link"><span class="text-crimson mr-1">05.</span>Contact</a>
      </nav>

      <div class="flex items-center gap-3">
        <button id="agentStatusBadge" type="button" title="Toggle Agent Inspecting Nodes ON/OFF" class="inline-flex items-center gap-1.5 px-2.5 py-1.5 rounded bg-crimson/15 hover:bg-crimson/25 border border-crimson/50 font-mono text-[9px] font-bold text-white transition cursor-pointer">
          <span id="agentPingDot" class="w-1.5 h-1.5 rounded-full bg-crimson animate-ping"></span>
          <span id="agentTaskText">AGENTS: INSPECTING [ON]</span>
        </button>
        <button id="hackerAudioBtn" type="button" class="px-2.5 py-1.5 rounded border border-crimson/60 bg-crimson/15 hover:bg-crimson text-white font-mono text-[9px] font-bold uppercase tracking-wider transition shadow-[0_0_15px_rgba(255,30,30,0.3)]">
          🔊 AUDIO: ENGAGE
        </button>
        <button id="autoScrollToggleBtn" type="button" class="px-2.5 py-1.5 rounded border border-crimson/50 bg-crimson/15 hover:bg-crimson/25 text-white font-mono text-[9px] font-bold uppercase tracking-wider transition">
          ● AUTO-SCROLL: ON
        </button>
        <a href="#contact" class="px-3 py-1.5 rounded border border-crimson/50 bg-crimson/10 hover:bg-crimson text-crimson hover:text-white font-mono text-[10px] font-semibold uppercase tracking-widest transition">
          INITIATE BRIEFING ↗
        </a>
      </div>
    </div>
  </header>

  <main class="relative z-10 pt-16">

    <!-- =========================================================
         HERO SECTION (Matches 00:01 - 00:07)
         ========================================================= -->
    <section id="home" class="max-w-[1240px] mx-auto px-5 sm:px-8 pt-4 pb-12">
      <div data-construct="HERO_PORTFOLIO_TITLE" class="w-full overflow-hidden">
        <h1 class="portfolio-giant text-[15.2vw] xl:text-[186px] text-center leading-none tracking-tighter">
          PORTFOLIO
        </h1>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-end -mt-3 sm:-mt-7 relative z-20">

        <!-- Left Column (5 Cols) -->
        <div class="lg:col-span-5 space-y-5">
          <div data-construct="HERO_NAME">
            <p class="font-serif italic text-2xl sm:text-3xl text-zinc-200 mb-1.5">
              Hello, I'm
            </p>
            <div class="inline-block bg-crimson px-5 py-2 shadow-[0_0_35px_rgba(255,30,30,0.4)]">
              <span class="font-sans font-black text-3xl sm:text-5xl tracking-tight text-white uppercase block">
                RAHUL.
              </span>
            </div>
          </div>

          <div data-construct="HERO_ROLE" class="flex items-center gap-2 font-mono text-[10px] sm:text-[11px] font-bold uppercase tracking-widest text-crimson">
            <span class="w-2 h-2 rounded-full bg-crimson animate-pulse"></span>
            <span>B.TECH ECE • ROBOTICS | EMBEDDED | AUTOMATION | AUTOMOTIVE</span>
          </div>

          <div data-construct="HERO_BIO">
            <p class="text-zinc-300 text-xs sm:text-sm leading-relaxed max-w-md">
              Building intelligent systems through engineering at <strong class="text-white">SRM Institute of Science and Technology, Ramapuram (2026–2030)</strong> — integrating <strong class="text-white">Raspberry Pi 4, Delta DVP12SE11T PLC, u-blox NEO-M8N GNSS, BTS7960 motor drivers, and ROS 2 Jazzy</strong>.
            </p>
          </div>

          <div data-construct="HERO_CTAS" class="space-y-3 pt-1">
            <div class="flex flex-wrap items-center gap-3">
              <a href="#flagships" class="px-4 py-2.5 rounded bg-crimson hover:bg-red-600 text-white border border-crimson font-mono text-[11px] uppercase tracking-widest font-extrabold transition shadow-[0_0_25px_rgba(255,30,30,0.4)] flex items-center gap-2">
                <span>INITIATE BRIEFING</span>
                <span>→</span>
              </a>
              <a href="#matrix" class="px-4 py-2.5 rounded bg-zinc-900/90 hover:bg-white/10 text-white border border-white/20 hover:border-crimson font-mono text-[11px] uppercase tracking-widest font-bold transition">
                EXPLORE ARCHITECTURE
              </a>
            </div>
            <div class="flex flex-wrap items-center gap-2.5">
              <a href="https://www.linkedin.com/in/rahul-kumar-715b32423" target="_blank" rel="noopener noreferrer" class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-md bg-[#0d0d14] hover:bg-crimson/20 border border-crimson/45 hover:border-crimson text-white font-mono text-[11px] font-extrabold tracking-wider uppercase transition shadow-[0_0_15px_rgba(255,30,30,0.18)]">
                <span class="w-4 h-4 rounded-sm bg-crimson text-white flex items-center justify-center font-sans font-black text-[10px]">in</span>
                <span>LINKEDIN PROFILE</span>
                <span class="text-crimson font-black">↗</span>
              </a>
              <a href="https://github.com/Rahulkumar2k8" target="_blank" rel="noopener noreferrer" class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-md bg-[#0d0d14] hover:bg-crimson/20 border border-crimson/45 hover:border-crimson text-white font-mono text-[11px] font-extrabold tracking-wider uppercase transition shadow-[0_0_15px_rgba(255,30,30,0.18)]">
                <span class="w-4 h-4 rounded-sm bg-white text-black flex items-center justify-center font-mono font-black text-[9px]">&lt;/&gt;</span>
                <span>GITHUB // RAHULKUMAR2K8</span>
                <span class="text-crimson font-black">↗</span>
              </a>
            </div>
          </div>

          <div data-construct="HERO_METRICS" class="grid grid-cols-3 gap-4 pt-5 border-t border-white/10">
            <div>
              <div class="font-sans text-sm sm:text-base font-extrabold text-white">
                <span class="text-crimson">6-Wheel</span> Rover
              </div>
              <div class="font-mono text-[9px] text-zinc-500 uppercase mt-0.5">30kg • 10L • 2–3 Acres</div>
            </div>
            <div>
              <div class="font-sans text-sm sm:text-base font-extrabold text-white">
                <span class="text-crimson">ROS 2</span> Jazzy
              </div>
              <div class="font-mono text-[9px] text-zinc-500 uppercase mt-0.5">rover_core • NEO-M8N</div>
            </div>
            <div>
              <div class="font-sans text-sm sm:text-base font-extrabold text-white">
                <span class="text-crimson">B.Tech</span> ECE
              </div>
              <div class="font-mono text-[9px] text-zinc-500 uppercase mt-0.5">SRMIST 2026–2030</div>
            </div>
          </div>
        </div>

        <!-- Center Column: Red Silhouette Suit Portrait (3 Cols, Matches 00:03 - 00:06) -->
        <div class="lg:col-span-3 flex flex-col items-center">
          <div data-construct="PORTRAIT_NODE" class="relative w-full max-w-[260px] rounded overflow-hidden border border-crimson/40 bg-[#1a0303] shadow-[0_0_50px_rgba(255,30,30,0.24)] group">
            <div class="w-full aspect-[4/4.7] relative overflow-hidden bg-gradient-to-b from-[#ff1e1e] via-[#b80d0d] to-[#120202]">
              <img
                src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAMCAgMCAgMDAwMEAwMEBQgFBQQEBQoHBwYIDAoMDAsKCwsNDhIQDQ4RDgsLEBYQERMUFRUVDA8XGBYUGBIUFRT/2wBDAQMEBAUEBQkFBQkUDQsNFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBT/wAARCALuAlgDASIAAhEBAxEB/8QAHQAAAgIDAQEBAAAAAAAAAAAAAgMEBQABBgcICf/EAEsQAAEDAgQCBQkIAQQCAgACCwECAxEABAUSITEGQRMiUWFyBzIzcYGRkrHRCBQjQlJTocHwFUNi4STxFoIXJaKyk8IJNDZzdIOz/8QAHAEAAgMBAQEBAAAAAAAAAAAAAgMAAQQFBgcI/8QANBEAAgIBAwMDAgMIAwEBAQAAAAECEQMEITESQVEFEyIyYQZxgSNCkaGxwdHwFBXhUjPx/9oADAMBAAIRAxEAPwD4KedWHVgLUBmPOtJec/cV7zQvemc8RrBpXl+x99cnb3D6dz9xfxGmMvOFZlaj1Tz7jSKawOsfCr5GqaDhJ2tzfTufuK+I1gfcP+4v4jQVtIqUglJ+RnTufuK+I0wPOFlRzqnMOfrpFNR6FfiHyNU6Gxk75N9M5+4r3mth5z9xXxGl0QEVVBKT8jOnc/cV8RpinXMrZzq1T295pA1pq/Mb8P8AZoHQ2LdPczpnP3Fe80Qec/cV8RpY1oqlIJN+Q+nc/cV8RpjrrgeWAtQAUdJpAE0570zniPzqqQ5OVcmdM5+4r31nTufuL+I0G9EBFUy1J+RzLrmYytR6qufcawPOfuK+I1pkQo+FXyNDQjbdch9M5+4r3miDzn7iviNLAoqlJBJy8jg850KjnVOYc/XQh50/7i/iNYkfgq8Q+RoaEbbpbh9M5+4r3ms6Zz9xXvNBWwJqUgk35HLecytwtWqe3vNCHXf3F/EaJaeo14f7NDEUIxt3yEHXP3Fe80XTOfuK95oK2E1KJb8jHnXA6sBagAo86EPO/rV7zRPD8ZzxH50FUkhjbt7hdK7+4r4jRtOrKjK1Hqnc9xpVMZHXPhV8jUaQUW7W5rpnP3Fe+s6Zz9xXvoctby1Nirl5N9M5+4r30Ydc6JRzqnMOfrpeWjA/BV4h8jU2Ci3fIPTOfuK99Z0zn7ivfWstZlqbA3Lyb6Zz9xXvo1uryt9dQlPb3mlZaNwdRvw/2amxabp7g9K5+4r4jWi87+4r4jWqyrpAW/JvpnP3Fe+iedcDqwFqACjzoCJonx+M54j86qkS3XIJdc/cV7zQF1z9xfxGt1qrF3LyE084VmVq81XPuNL6dz9xXvNMaT1j4VfI0kiKtVZG3XIXTOfuK95rRedH+4v4jQ1lFQpuXkYHnOhUc6pzDn66WXnP3FfEaKPwV+IfI0uoipN0tzOmc/cV7zWdM5+4r3mtETQ0VCW5eQ3HXMrfXUDl7e80rp3R/uL+I0xwShvw/wBmlEVEVJvyb6Zz9xXvoS85+4r4jWiIrKJUKbfkN55wPOALUBmOk0svOfuK+I0T4/Hc8R+dLqJAzbt7mdM5+4r3mibdcKj11earn3GlkRRNecfCr5GrpC03a3B6dz9xXxGhLzn7iviNaIitb0SFOUvJvpnP3Fe81sPOdEo51TmGs+ul7UX+yrxD+6sFN3ya6dz9xXxGhLzgPpFfEaGtKFFSFOUvIXTufuK+I1t15wJbhahKe3vNLonR1G/D/ZqUgep77g9O5+4v4jWi85HpFe80NZVinJ+TOmc/cV76ygrKKkB1PyMdH47niPzrVNcaUXnDKdVH8woehV2o+MfWhsY4yt7AU5nzz4VfI0IZVO6fjH1prTSgo6p81X5h2GqbQyEX1LYTRDSiDKp3T8Y+tF0Ku1Hxj61LRai/AunJEMq8Q/uhDKp3T8Y+tNS0rolCU+cPzDvoWx0Yu+BSRRUfQq7U/GPrWdCrtT8Y+tU2WovwCkUxzzG/D/ZrOhV2p+MfWmLZUUt6p0T+odpoR0YunsKArdH0Ku1Hxj61sMq7U/GPrUtBqL8AgRTHvTOeI1nQq7U/GPrTXWVdKsynVR/MKFsaouuBIEUQFEGVdqfjH1ouhV2o+MfWqtBKD8GM+efCr5GhApzLKs51T5p/MOw1roVdqPjH1qrQ5QdLYCtgUYYV2p+MfWi6FXan4x9aqwlB+DQ9CrxD5Ggp6WVFlQlPnD8w760GFdqfjH1obQ3pdLYWE0YEUwMqHNPxj61nQq7U/GPrVWWoS8GOeY34f7NABNPWycreqdE/qHaa10Ku1Hxj61SaGuDvgWBFZTOgV2p+MfWiDJ7U/GPrUtFqEvALw/Gc8R+dDlp7zSi6vVPnH8woOhV2o+MfWhsY4O3sBRs+efCr5Gs6FXan4x9aYyyoKOqfNV+YdhqNoKMHa2EVlN+7q7U/GPrW/u6v+Pxj61LRXQ/AmjHoF+IfI0f3c9qfjH1owweiUJT5w/MO+qbQSg74I1ZTvu57UfGKz7ur/j8Y+tXaB6H4E0bnmN+H+zRfd1dqfjH1onGVZW9U6J/UO01VoJQdPYRWopvQq7U/GPrWuhV2o+MfWisX0S8CiKN/0zniPzouhV2o+MfWieZJdXqnzj+YVL3J0OuCPE1opppYV2p+MfWs6FXaj4x9aK0LcH4AZ88+FXyNLImpDbJCjqnzT+YdhpfQq7U/GPrVWinB1wIKa0RFSOhV2o+MfWhLCu1Pxj60VinCXgWPQq8Q+RpZFSOhUGVap84fmHfQdCrtT8Y+tWmipQdLYTWiKaWFdqfjH1rXQq7UfGPrRJiXB+AHPMa8P9mlkVIdZUUt6p839Q7TS+hV2o+MfWomgZRd8CSJodqcWVdqfjH1rRYUeaPjH1orEuL8APiXnPEfnSqkvNKLzhlPnH8wpRZV2p+MfWrTVFTi7ewoia2z558KvkaPoVdqPjH1rbbKgs6p81X5h2GrtC1F9S2I5GlapvQq7U/GPrQllXan4x9auxDi/Asitj0K/EP7o+hV2o+MfWs6JQaUJT5w/MO+rspRfgjVlNLKu1Pxj61roVdqPjH1o7QpxfgTRueY14f7NbUyrtT8Y+tEtpRS3qnRP6h2mpaB6XT2Ix3rKaplXan4x9aHoVdqPjH1qWhLjLwKVvWUxTKu1Pxj61lEmgOmXg296ZzxH50FG96ZzxGgoUE/qYQ2pjPnnwq+RoKNnzz4VfI1HwMhygRtW6ytjWrCRsbU1HoV+IfI0umpEMK8Q+RoGNjyDW0itUVVyEjKavzG/D/ZpYEmmueY14f7NUx8eGBRDStJFGBNUEkYBTX/AE7niPzpdNeH4zniPzoO41cAgRWATWUQEVYaQxnzz4VfI0IFEz558Kvka1QdxyXxRlbArAKMCapsJINI/BX4h8jWqNPoF+IfI0IE0I6tkaAmiiKytgTUCSDWJS34f7NCBFMUklLQAnq/2amM4BiNwwXm7N5TQ3WEGKrkZKlyQKyrdzhi8atw4pspJ/KRrVzgnkr4j4gShVjhrzoVoDlgGoot8IXLLjguqUkkcm8PxnPEfnWktk7AmvacJ8jdrhtlc3PEbrpUFqSi0w5pVy+pY1KSEA5YBHnRvW7DyicD8MYnZYe/wSq5QC2H7h+5KnWJcCFBTYQApSZnKFROmaZrXj0eXIrqjzmv/E/p+im4uXU/tueM9AsEAoVJ20qww3AMRxB1SbayeeISowlBPI17Biv2ifJ61iLTyeFmV4Uh1bSnVtFq7QkNiHUNFJQpIXyKwYG01Z8Ifao4TRiTF7iTLvD7ycPQ4vC8HtkYkxdmZIR0vRhpQAkuKUQZyhJrUvTZ95HAl+OdKq9vE2/ueE3OA4jZuZH7N5pXYpBFRnLN9rz2Vp9aTXq/lN+1Tcqxlq9tsLewTClKQfu+LYcwrPlUvMkFLcDMCkGDpkMb1A4Z+1LgOKYx/ovFPCanrZwQ5fAttOMkpQBCOjTCR11aknrDWE62/TpLiRWP8c6ZtKeJo8ygzEa1Z2HD+I4ky4Lazeegg9VBPI16lw8zgHEGJXauHbDC7Oxtsz7+McRvrcabYSqFvJaaAzASAkFWZalJSlJJ0psX8pvH3kr4sxW3Cw5hzLRf+5YhbMIWgO9W3DqWwQy5llQbzdUzmJIpcPT8kvqdGrVfjXR4V+wi5/yR569hN5bqKXLZ1BG4KTpUVSSkwQQe+vu7yfYAzx5w3gR4hwhFvid/haL0346NDRcUElSFgKkLUVlSQUwEIGory/y1+QG3w4IXh60pv3M/RsFIBeKfOAjqkjbQ+wHSl5dHkx7rc3+n/ijSa5qMl0t+T5go3BKWvD/ZrqrbyZ488oKcw95tnWVlBioeJ8G4vYJCzYXHQoBHSdGY3NYGn3R7COXG7SkjnSmtFFNcaW2qFpKVdhEUFUHQspon/TueI/OiiaK4T+M54j86hK2EVoiaIprVWLaNtCFnwq+RpdOa84+FXyNKIq0ymviARFZRVoiiEtGRDK/EPkaURTx6BfiHyNKIiqQMlshdaIoyKGjFNG3PMa8P9mlERTnRCW/D/ZpW9WmDNbg0JEUREVoiaIQ0buBLzniPzpVOf9O54j86URUQMuWLIija84+FXyNaIrbPnnwq+RomLX1ITWiNKIitVYlg0X+wrxD5GhIg0Y9AvxD5GrAXIk6igo6E70aFM0dq255jXh/s1qtu6Jb8P9moD2Ys7UNHQHerEsysrKyoAG/6ZzxH50I3prwb6ZcqVOY/l/7rSUt/rV8I+tUhzi7YNMY88+FXyNahv9a/hH1prCW8xhSvNV+XuPfUbGQi7QmiTRQ3+tfwj60QS3Hnq+EfWqbCUWCN6aPQL8Q+RrSUt/rV8I+tMAb6FXWVGYfl9ffQtjYRdik1ujCWwPPV8I+tbCWz+dXwj61XAaiwQNKY55rXh/s1kN/rV8I+tMUlvK31lebp1e899DY+MXTFiiAiiSlv9SvhH1oob/Wv4R9apsJRYAE01/0zniPzrAlsfnV8I+tMdS2XlypU5j+Xv9dVY6MXQoCt0cN/rV8I+tbCW/1K+EfWqbDUWbZHWPhV8jQgU9lLeY9ZXmq/L3Hvocrf61/CPrQWO6XSAAmipgS2Pzq+EfWthLZ/Mr4R9aqwlBmJEsr8Q+RoacA30SusqMw/L6++tBLf6lfCPrVWP6HSAAqzwPh++4hvmrWyt1vurUAAhM1K4W4Wd4pxIWrCy2hKS4684AENoAlSlGdABrWeVPypWfCuDscL8GP3SEuW/S3+JtZWl3TahEJPnpRuIBBPPStWn08tRLbg876z6zh9HxXPeb4R0OIcQ4HwqpjCuH7PD8cxttSmbnEr58G2t3EpUtSW2wczuUCCvzEkgdarbDPtd3mB3tpgGIcJYVeWSwm3XcMsKQ8tZeKVuBAJBUEgoSlJylQzSZgfNPFPGq/9Gw7CcNZbsbOzYUhx63WSq6UvzyokDQmNtoHYI5q1xMutDpXSktoJQrMeqrNOh5amvR49PjxxpI+Haz1rW6zK8k8j+y7I/RLygcYcKcE44cSxGxQnhx+wYxC1+9WSW7uxKnOiCXW+kPTNKcGRSkfitkyUKTWY39obhLB+GMEvbPF37u7cuVPN2Nv0bVilQaUrpluuspfLKW1KCQ0kZyNFAma+HuEPK3eYDYN4ecKtMTLSA00X20AQXw8orWlIWqSEjVR05iAKsvKJ5Rbvi/iC4xTEsPt8M++tlBsLZotIW2HJAXJlXWT3bazrLFjhHhGHNrtTqF05Mja/M9I8oPlqveIbu+usOtcPsLNdw1e4ZbO24tre2KRkzIZa0zkQsqWdY3cIBrzXF7nGLOybxK/ebubS+ddU3iQKgq5VnDmoUokKmFQRISQT5wrleKcaF05afdytRSyErTlGXPrsANojfXSuUuXVuFBcUVBQ0J9dMRifJf4vi7NzeW2dtN82y2pBBUUSCSd0wdyYqVht4lKTaNIDS1OEIA6xTmIITm3I0GprnbG2uVBT1ulyG/zJSeeg12G8e2rD/TH7ppsFxDS2xGfNsB2nu5d1QoLEcUuMVeRaKdWtgO+YpZIgbH/O2pIvHbRtbr63FPlRU4tSjmM8iTrOnyprDDFqw3bXF2gMvLDjbiEArBEga+onTSpeIs2icWXai7DqFZslwEqQHQBooBQOqtsp5iKos9A4C8peCC3s2Lvh+yxVxrK2BcWhKgkNqRmlsjrJBK80Sp1SVHRArLJ688onGF48thrDnL15+5AYeSw1anISlKlrOXokBBEHWAQDKq4Zg2uC4glNvYOuENELWs9ATPaQQAKBtdu/ZrQ/iDDQJSlFo0Dk3nc6mN/WRU3Ie5cL/aVc4KdGKYFgFqDZjLh7mKLU8lJcaDdy84kmXVuhKQJOVCZSBXNeUr7YPGnlCu2H38RTYM2qw61hlgjoLcPZMirhSZJcdVqSpUkE6RXjmIrfsLdXSL1dWFlGbzQR1QfZr7aqsMu2WsTH3jK5aOKCXSWwshE6kSNxvpV0WpNcHuHD/wBpfymYvjKCnivEH7ta56AlGQkAdXIUZQCEjYeuu/xP7SPFuOcOOLvr44WtDIDV4zastuApcUpQcGQlQIJTlEahO4EH5wv1q4axC4U27BCsqXLZYUnLyWmeRHLvqvxXHrnHLjpekKStUEyciu+P65VXSvA338v/ANP+J75gXl3wLiq4bwjjy1bsrgpKRjdvbdG425PVDjaOqpMESoBJHYat8f8AJ3iOEtqu7Us4rhZPUvrB1LzSh4kkivDcH4abxdm4avwLe+kQtSgetEpV3g+0KHeKTw9xnxX5L8dW/hOJLti4Cy4GtWXCU6pKT1VRO8aEA6Gufn0MMu8dmez9I/Feq9PXt5v2kPvyv1PTltlBIIKSORrb/pnPEfnXqHB7mCeXDBr5mzsBhvFNowHZaXmZvkgAKUgHrJWJkpM7yD2eeYph68PvXmbhLjbiVkEFHf6689mwzwSqR9o9M9T0/quB5dO/zXdFcRNCU0/I3+tXwj61qG/1r+EfWk2dRwYpodc+FXyNLqU2hvOYUrzVfl7j30ooa/Wr4R9auynF0JIoadlb/Uv4R9a0Utn8yvhH1okxTgwI/BX4h8jS6kAN9ErrKjMPy+vvpZS3+pXwj61LAlB0hJEUJFPKW/1r+EfWhKWx+dXwj61diXFi3B1G/D/ZpREVKdS3lb6yvN/T3nvpRS2fzK+H/uiTAnHcSRNDTob/AFr+EfWhKW/1q+EfWjsS4sC4EPueI/Ol1JfS2XXJUqcx/L/3Ssrf61/CPrUTAnF2xJrbQhZ8KvkaNSW/1q+EfWttpbzGFK81X5e499FewtRdojkTQU6G/wBa/hH1oSlufPV8I+tEmJcWKVRD0C/EPkaLK3+tXwj61sBvoldZUZh+X199QBRdkdW9CqnFLceer4R9aEpb/Wr4R9aKxLixNE75rfh/s0UN/rX8I+tE6lsob6yvN/T3nvorB6XTI9Cqmw3+tfwj61pSW489Xwj61LEuLFVlHDf61/CPrWVAOlmP+nc8R+daG1bf9O54j86youAnyzKaz5x8KvkaUN6cz558Kvkaj4GQ+pADeirSRRDeqYRumo9CrxD5Gl0xHoV+If3QsdDkGiSKGjqMNGU5Y6jfh/s0pNOUOq14f7NAx8eGCNK2BrWqICBVBI3TXh+M54j86WBrTX/TOeI/OqY+K2AAmjAmtARRgRQsNBs+efCr5GtARRMDrnwq+RrVCPS+KMAmirAIokpKjoJqg0g0D8FXiHyNXvC/CNxxEbh9Tjdph1ogu3V4+crbSBuSf6511nk68kiuJsNu8Uxm9ZwHBLYZ3b++cDTSQAfzK+Qk91cf5afLRhWC8POcF8E27wwtxQcfv3UlLt8RBSSgiUIB1AOqtCQNq2afSyzO3weW9a/EOD0zG4Qd5Oy/yV3lT8qtvgtgvhzhtlyyslIyPulOW5vVyNV/obG4b3OhUfyjwZxalJUkhP3gytQVqSe2e2p1pduXOa7vFrlCcqFFE51TqJPt9sDaojjhbtHIg3D7gClKHmjkAe8kz2RXpYQjjSjE+E6vV5tblebPK2zWHMvPuOsiXEKQtRGWcwHPu23pYWm0YclpuFiBG4/z61Pwu5ctXbtFo8kB5hxtbikHMoH8gOwzRPtqHibfRt9GlWZB64Mbjl8zTDGKtMVUy0ptXoyrOUDQFUQDTfvgfX0pK3VElTpWZUfV7KrGwkqSCrLrqa7TDOFHMJwZzE8TcYtErCFt2rpHSqBkhUfl2GneO2qohUtrtnLwqdYL8aJQqRk71a/xU/8A1FTVxausItGXLZeZtX3Vvbtgpg+0GqF3EUpZKGUiSZnKAfr76glS1qKlEgkVZC2v8cuVuw6QpWbMVTJV6zU6xxFGIqat3r5Vo3lyDqhQTrO5j+ffVBZW67u5DYbU6Tukbx7a6/DcBsGXEO3LrLGUR0ay+p3PyEoEDTnEDvqEJOK8JFFgw5c3CFrdUpLRU3lzAAahQ0IM7AzptXN3FrcYelaHHApSDorOZPYROxHrFdHiPFLtqzdWLV+8bJ5AKmVLlCCPzbdbTTUazVCy83ekKW9OUZVAjfs0qEN4W6rFx0D5MrORIKhJV6yQAO81NtMEfwtDt2ltKlJ/DC3QMqSYkAdqswAPrNV7jKAlzowWAZIUtUAka9sHuoWsVvPuy2Hk9My8mE5iSk9/rG3dJqEK+7unXy6XZK1LBzHuECgVcJJbKW8jwOqkfm747akXbqmrZbGQsoCwpKInNI3J5iowuHW1JCEIREao0k771CGMZrh5LRnIomClM6ers7q73A+EkrwRN7aXNv8AecxD9ldOdGh9tOudpceek7jzhvETPEIxq6ZcbcS6oqbBSlCgFJyndMdndU3EeLr+/tOgUGm7UgJ6NtOmmwJMkxykkidDFQhOxbiG4usSzMIRboaX1YSB0fdA0j1aeqnWN1a3TxavEBxpawVuAHqnYqHOuXtxKFEzNSFuKTdKAUUAgFShyAGvtqEPReDePLvgPiT7/hn3i3XbXKLm36F0JyZZEmUnMkgwRpoT7PeOPn3ONsFwvi9m2+7G8R0d9bhMdBcpAzpjkDIUO5Qr5ftMQyW9r0iQt4A5ZMQDvPcP7NeleTny23XDrl7guKWtxjXDdwleeyQ8lJS6TIdQog5VSTM+dOvKMGqwe9Clyj1X4d9WXpWrU5/RLZ/5LUpI3FCRNdrw9hHC/lRSlrg7G/8A83jrYHiaQzdTzCBMOf8A1J9lRMV8mPE2Dry3GEXKe8NkivNzw5MbqSPvml9S0etj14MiZy7QhZ8KvkaWRNXNzwzimGjNdWD7CSlRBWgjkap1JKTqKTw9zoWpRTTFkUJEU0iaEiiFNGo/BX4h8jSqfEMr8Q+RpRFWmDJbIWRFaImj3odqIQ0Y55jXh/s0oiKe6Oo2f+P9mlb1FsBNbiyKEiaMihoxLRj/AKdzxH50pQp1wPx3PEfnSzrVrgCfLArbQ658Kvka1RNjrnwq+RqxS+pCDpWiNKJVaoxLAov9lfiHyNaOlF/sL8Q+Rq+wC5FUFHQqqxDAO9G55jXh/s0JGlE55jXh/s0RXZia1WzvWVYlgVlYd6yoLYx707niPzrVMcWkPOfhpPWOuvb6610if2ke8/WqHNK3uCmms+efCr5GtJcTHok+8/WmsLSVH8NI6p5nsPfVN7DIJWtxVEmt9In9pHvP1og4mPRJ95+tUEkvINNT6BXiT8jWg4mfRJ95+tNC09Cr8NPnDTXv76pj4JXyJG9FRBaY9En+frRBaT/tJ95+tDYaivIIECnL8xrw/wBmhC0k+iT7z9actacjf4aT1e/tPfQNjopU9xIGtFRBaY9En3n60QWkn0SfefrUDUV5BAgU10fjueI/OtdIn9pPvP1prq0h1Y6NJ6x3n60Le49JVyKSKLejC0j/AGk+8/WiC0/tJ95+tDfcNRXk2z5x8KvkaECmsrSVn8NI6p7ew99a6RP7afefrQmhRVLc022p1YSkFSjoAK9M4T4QTwrg6uK8ew128tmjFtYpUEF9QGYkqVolKQCons0AJIFQPJDgAx7iy1bVboW0FZlkkgADUkkmAO+h+035V+GuM8bXhOAqRieHYPa/dLdS0noFLJBU42hRASdPPIJjnqI6OkwLLLqlwjxH4m9Zl6bh9nD9cu/g818oflTxri68evEvB3D20dHbsPoStplUhUo6oAgjQgabTqa8vXdu3dy5c3ChdDLOSSCs9pPISfbU9Fww6+u1dcbet2zK1hUA+rkBOyRqas1cA4s7hbl1/o9/9xKRcJubPK6nJJTmUPzGSmAkwnXQzNejSS2Phk5yyScpO2zj3by7u75ptxtRQyU5GB5qEiBoNvbScRWtt1hc9YjONJA1IHyr0niK5wFp1h6y4dGEXFnbIS+HLxx83KmxCnkpcTmanTM3mVBOmmg5nCuG3uO7gItGuif2CWkQhOuojYe8VYBzLV+4zeouSOkUnQlZJkRGtW1qq1xRQbdeDSxoAdRJ7COR7Iq7/wDw/ucFeWjEiwtlt4pUhLyCsgdqUqKkg98VDvuJ1Wi1WGE2LDAUTD6Wg4+o5QmAqJA6o27zzqyERxr7rcsrsm2mFobzC4fXKSUjVSc4iSRpvrtUHF1PqYbQ6vplpT0ilnzlFRnMokyo6xPZVvhmDuqU3f4ndNFuS2hCoWVKA0SBqPcDFWLeEYY3mN7dXdy8E+jbbWoA7QogaVZDiLdBcWFEFxROqZ6xH+c6ksYO7fqdWhTLaEyooW6EmOQE7nWK7PE3LIsOs4e+tloNpC2yhsgwdAT56T3/ANVz/wB0DiVKQ8RAgpPWk/zVWQRbJwrCyU3+H3Ny4kyVIuEpg8gNCCO81cYZxfhwxi0fuGYsmXEE2ykqBUgGSmW1JEnYmBvVP9yS8yUwElCjnWQRM7Ag9kcu2ha4buFn/wAS6tbsZoWhDoCkjtKFQY7xNROyCrsDFHbi7ZQGm3X1lLJlRb1kCecA7xypTrC7ZCHlaIWnpEERKoOXblqDXX8J4Sywly2vXm7UXDiJWuFAphWZCVA6GQme0aUOJ4BaYVjreGsvpcuXksshwDMhCyElWu2YZiecR2kRCHLqm4eQp5zo0yASROnNIHOl512CnGUKllSh5w8w8j7quMW4eVhtkzfBXSIU0h10J16PM4oJSe/KmY76qcZf6PEn2W0KbQlWXITrpB19s1SINyC+caS66GVzlJOqI7e0UoZUo6NIdIKyYiSDEf56qjQtASHCVJiUa+aJ3py3XMg1hCdQoaDTn/VWQF1KXHG3E9ZOcDQaAdlJdShsq5JJzAA/xVp96S04GXGkwoDMVjX2HkO7Uc9KrL1lFvcIAJdbV1hroQTpUIEhzobZpST50yO+dKsrWycJabSjK8R0rz6tYB0H09c1lrh/SuWrDKC/dLMpbQnmo6R/H+a1FxG4eaLiSr8QulJTmkjLoPmahBilsMuOZXFO50ZUgiIk8h6vnUmyxBVopOSAomFSQVDvpGGYQ68toLCWy5MlaoKQNCSN/XzreIWicKfSlYUG19VRSiAlQ5jXXt7wahCW9euuXAuWChNwk5kLAIKSO/kof+q7bhzy48b210hxzjDG0uFHRBT2JOKaHVCRoSYICUiT2V530waW08hWqSC8iJB10I7iKbizTLLyXbaGm1TnaMxzJI7o5VVIKMpR3i6PT8L+0TxtY40lpfEFxiFo/cZSzfJ6dJSqAQelkCCSOXbMV6Pwp5ZeB8cxhVnx1gjeGWqcwGNYMkkSNitiScp/Ug6b5Yr5lSpDlsp5aikHQECYMRJ+VOvMSUr7pbqLKlshQW4DKXDz12Ow9ppM8OOf1I6em9V1uk//ABytfqfYPGPkVW3ci44deViFi8wLpmWXEBxogHM2pSQlwagykmARMTXlt9h7+HvqZuG1NOJ3ChXWfZT+1hc8H4UfJ7xiw/ieB3L6P9Ou0KSLjCnoyoKAqAtMqHVJGggGFEH1/wAuvkoDuAtcWWKra5YfzKP3ZwLQCFFKwkpUZAUCO7Ywa4mq0ft/OHB9Z/D34meua0+raUuz8nzcB+AvxD5GlERUoqHRL/DTooaa9/fSukT+0n3n61yT6PKKpbkciK0RNOK0/tp/n60JWn9tPvP1okxDivIDnmNeH+zSSIqU6tIS3+Gk9Xv7T30orSf9pPvP1q0xc4q+RKhQKFP6RP7SfefrQlaf2k+8/WiEOK8gP6vOeI/Ok1JeWkPL/DSesddfrSlLT+0n3n60SewE4q3uJUKJrzj4VfI0ZWk/7SfefrW2lpKj+GkdVXb2Hvq2KUVa3IpFDTytIPok+8/WgK0z6JPvP1okxDX3FKoh6BfiHyNEVpI9En+frWwtPQq/DT5w017++isClfJGrR2ppWn9pPvP1rXSJ/aT7z9aIS0vImtu6Jb8P9mi6RP7SfefrROrTkbPRp83tPae+pYFKnuRlVqmlxMeiT7z9aHpE/tI95+tEKaXkUrespinE/tJ95+tZRci6Xkx30zniPzoaJ70zniPzoaoJ8sIbU5jRR8KvkaUN6az558KvkaGQyH1IAUdCneiqgkbTTU+hX4h8jSxtTEehX4h8jVPgfDk1RAUI1NHQsNG001eqWvD/ZpY2pqvMb8P9mhHx4YNENqEamjqmMSNgU50fjOeI/OlAU570zniPzoB64AAmjrQFEBVMYkMYHWPhV8jXQ8HcMDirEmbJskOrUBVDatLddyoSVKKVaATyNe2eQbhW5w/FU4peIbsrJkdK5e3p6NhkD8y1GAAN6PHHqmkJ1mZafTvJdNWejcceT+28jvk6t02jVpd4jjKP9PYsMxTcXLq09ZWYjJlS2VryqISISpZy5Ur/P8AvGCy2lNrbOOoUtLjrBaJRkAkHNtBGmu+/Ovd/tLeWrCOKb5x3CuJ77EcPbbRhlnbKtSHBbkrcffDubKC+4EZgUg5A2kdVEV4knip3GU9Fb2rLasrbTanVqW6G0IKAkqKgMoEGI3AjQRXq8cFCKUUfm3W6rLrM0suWVsrUs4tjKF3LLDLNqMzpQlIShKeYSgbc++pzvFuKM2ruTGb23fdSE5mX1tpBgZFBKSAOp1dBsBUvH+ILnhyyTha+nLzMFan3Fq1ICtArbcbAD171zD141f2IISlDzbaeqO7QH3UwwG7vElXDCbVaip3KpGYbZDlgevq/wA1I4ZxZ3AX1gtl7NIKi/kSBtGm/PnXNKKm7hSVaFKtJ5GpFq4H3WhcKBaQoqUhZICoE5dNpiPbREOx4sSs2dtdWyGrBh+czNsvOpJ1CAoAASrcROhB5iqnhyw/1BWRQTkQrrqCwlThJgJ19Ww356UTd/f8W3Nui7ccCSuUIYQAUoBJAQOQHInaB6qvsNtncMeYQ3h/3FtSipS7tOsEwACUqHZqf4qEK2zusmlj93QpMgISoLeA5weXbpI76YxilwgtNsOpuHFpI6MjpCs9m8A929XuP4jcXrQllJWJSWXGEul0AflUN/UIPdXKOYczboTd2zTamnEBS2So9SeQVy2O/ZUIPXiFhetulWFsloQtWR0p6w02jfU7xpUXFxYvMOP2o6KN0KMynt7fWOXq1q5wY2jjLLrJbZKD93dzJCVIzE9GpR2JkkTqCIBqsdwNV/ibLQUlLd02FAHUNqIVA96FAeyoQoD95bvAyVpQ8VBPpBlExG2ka1f3mIXCbD7u0txxpaw2BEdMRoCY1idhUW/4eTYYQi5QQ4S6otqGspCoG3bFKtcRt2rZLjYWm4YnoiQOqrrHMfVI27J5VCELEOmF+5YtJIUhzIEpJUZB3980+8cdcvUuKWouoGYAfqn++2u88nHB9rjuLJZLxaxC4ctkpSdcrS1nOr1wEesLrk+L7L/R7m5bG63VICjzjf8AiPiqEJ1/iCsSwbB7d0i4d+8LbJEbpCQAD2AKgequfwptF/jj63yEtpS66rN2AE0OG33StLbWQChfTJJHOIV/Ee6oAfP35a25hZUBG8Kkf3VkLv8A+PXC8aatXQUW5/ECxqMhUUyO9REAdsUONNJeuzbtp6NkCekTqknlr+kD36nnXd3VovEOErG4Y6RD6rdxjKFghRIU4hYjY+kT2ia4W9CwizQQQbhsO5UaGCYT7yPcE1CEa3dtkLdQ46p1gIhL2X8wERG4HZVk9g1paOWjTjby3gEAtE6jMZkmNE9YGBJ7xNLssGX98uAtttLSUypTiTBUkZso7zp766Ni4E2Yu2Vi9aKUF1RnVKspnsjQRVEKDEHUNv4mptH3dtKiG20GDCYbQDO+pJPbBqus0fdvx1+nuAUNFW2pykj+dfXU+/t1OXOMBQCpcTyPNS4InbWNv7qtcuFWF30bqUPJayhA0W2oDYjTUHU+2oQusQZvcBxBpy4S2tSCUwo9ZqD/AJp69qXimJu4pYKuX2myM/RoQDoFbhU9kdvM95qsu313Fm2UMNlsmQEjqo7R3Uy3vEW5twyVLWEqCgojUk6xpvt7qhDDhVwyEvMo6S53LSVpWY5yOY9X8VKUy1fILjSOiEpC2DJDSjMCTuDBq1dwpFxhCsRZYD7CCP8AymytLraxuF9YgeuPdvUXFXhf2KH0oW2tICLhaCesAZCiO7n2gzoQaohz7IU0XGRuk6A79tH0aXnAFApSrLKgmY13im36Sl9t3L1nUjMe/n76W2UFp0LkNiQDG5japZBi3b/Bblws9MyshSSMsSgiCCOYI5bV9y/Y145w7j3h1vgvHkhro7EvWCnkFLQeZbKHUNKmCpduptakaGWJgzI+Fvu5UAoEmBAIOkxv7oru/I1xdiHCnlE4cubM9K7bXrTrdotauicWVBMJSNCpSFLQM2nXInahklJNM06fLLDljOLqj2Tyl8Nt8K8U4jYNEZEOiAOW+lcgRXrn2heEr7AeLLi6uZU1eKDrayIOUgkSORg15JXjZrpm0fqHS5Fn02PIndrkAiaAimERQkUI1o04Oo34f7NKpzohLfh/s0pQokBNbgEQaFVGRIoaIztGrgfjOeI/OlHUU64H4zniPzpVWgJ8sCtteefCr5GsO9bb84+FXyNGxKXyQk7UJEijoaghgVsaMr8Q+RrCINb/ANlXiHyNEAuRKtq1RGhoxDBO9E55jfh/s0KqJzzGvD/ZqAdmJoaNVAd6MSzR2rKysq0AMe9M54jQDenOvOB1YC1ABR0mhS+5+4r4jQoa0rMTtTGfPPhV8jWB5yPSK95o2nnCoytR6qufcaBjIV1IUmiog+5HpFfEaIPuT6RXxGr3DSiDTUehX4h8jWunc/cV8RpqHnOhUc6pzDWfXQsfBRsUkUQ3ow84P9xXxGtpec/cX8RoXYaUQacsQhrw/wBmhD7k+kV8Rpq3nAhuFqEp7e80JoilTFJogJNGHnB/uK+I0Qecj0i/iNU7GJRBG9Oe9O54j860HnI9Ir4jTHXnA85C1ABRgTQj4pULqVh9ui5vGWlqypWoJJ7KZhVle4zftWdp0jr7pypSCdTXs3DHk2t+D7hv/WsmI44tpT7WGNulRQkZQCsJ7SoQCU8ySAKZjxTyuoowa71DS+nYnkzzr+pe39j5Ofs6cOWWNcQ4mb3HMSaS5YYQyjpH3U58ufYhDZIIKjroQnXUfN3Gn2kca44cvrBYt14A+haGbG/w5h/oRBTmDi0kpXrMojKdjpNd19onghHC/BWDYtxHjV7inHXErxuFYYphSWbRtk5UBKjEBAXkCUgjVWoOlfL76HWXw9dytpbxlQA60HrAd06euvT4sMcUUkj4B6j6nn1+WUpzbj2/L8izxO9tcWxRS7hLsrSEB4nMFBIAEA6wABEdlWWEYO1hBTdoc6VAJzLEpUhW4B2Ov9VTIxBl1la02iQtSs2dThAA/T2n11a2Tly4m8Su4ZW2+ejC0ZoWSkKPna8+esinO0cdEDH8WXjGJG9uiq46XVRWrQjYCeXZ7qqW7F9KkuIQFgaTyUnsNTHbZKmHAshl1kx1vNI217jFSbC1bffcbC1WrqSFJhQAUY3Sdj3jnVrgoj3mEB9sXaAsoAENpAUowdT3gczSrW0ZS/cFxSXWWesAQR0o/LHYdh/6q5dsWLDOHLgfeWiT93DamlBZ3EHYgCSRptzoWcCtLkJvLp0KJQXVMpcHbpJPcc2vZUIMwq3OHZLg3Kbe3KwXVujMV94g8hMA6Vd3WNqvsJQ3ntFphOrPWnXUDXu3/ikMpwjFm0N4fh9i9kAQ4y68tThQOaVAgA9pj21SX5uMJxG6ZEKSucoUEFIG6TE7CI0FWQif65c27hdNwu4DbkqYeiFCe75jbup9zirSLp1u3dbcZu05lKeJSWydsyh+YECdN0ioON4g3etMONhpK1IClhgGEKPLrCezaRruap0haCsOAwZ3B1NQh0Vi6/YouEmW1XDa2nGSkflKVAjtAPL11ZYHfPYc7fXaFtFC0IQ3mMQpSyUmD3zUO8VdXGPYc7cNIJU030JSOopOTqz6zEn1zSyttt69W2S4wtHWQvrKCQodImTzG4PYBUITuKbxh6yYCUluFuZktiQUqMkjvCgP5ri1rHRoKVHOfOntnT+K6nG7dVlh4U6VLFwkQ8NAXBopQHMEFBPfJrlChQUlJAnsOlRFs6zhPiW44affvrd0oeC0pbUJCkgnfsAGnvqkxPFbrE3Mt28pQK1K1iASolUdmppCVdPYKQmVLQvpCI0ywBNTbi0Yt71DSni815xdaESCJkT/AGORqFFaliXDDyG4BIzkj2bVMtOH729aLrDXTBIzHoTmIHbApqLFF1dlphbrTJjIHACo98Ac6MXr2HvuoGQlEohMp0nZJTB17/bVfkWXPCXEi8HxFpi9bWm3L6VukpiQmYJ7DqZNMxtNvZYlb31u0FixeFs5JkZcgLCz3Rp/9KY7jTbNitd21couVtpUlp1gELAMFRKiCIT+ZO8ajnVXfWjeJ4eq4s0ZWQpIWEnzhB0Pbr27T7aiZR2tu9h195PsMt23HW7lD7qiFgFSnF5UdY9gQwI8dc7YOJXZ8RF19bjobLVsCIUVFxCyo90pCY/591VeHPlWGrZbccTdMOh5AEkgDzjl5wJJ9VXOHW1te3FspfTquHlKzDToyopEFJ5yACPUashz1tfZb5LziVKQ6kBaZ3VJIPdr/NRcWDq1IUlJ6N0FSI569ZPsPzrocfwdm4uXLjDXU3L7TykOWmXzssSUQet2kb6yJ1jnbHpFKU8ptRPSBAABIRzJ7jGlQhHtbh2xIcC8yQYUiZHqIp1679/SFNtpR1p6vqqz4Qw60x7HU2D6PwXpBVmjL3jsP+RVo9gauD8UU264nFMJDhUgpSUoc0IBJ3B122kc6hCx4KvQxhV2halsPr/8dwgGCYzJJ9k68iDyMUCcNLTFzettFZZGV22iUllUpWpKRtuQR+U6jQipmAYOrEsKxRSEhVvbpS7miVpyTABG4hR09W0xVnbOK+74jblUq+7qSlaVxnIGoncKBA15wKEs83vYCENpIDVs4UJVmkFO4PeTP81EuSgOrQkqDWY5EqGsHmY0nar3HsMTaYWXkhKQu7SiToYyqGo27NRv3VXYhh7zj6YSEq6FnMdgPwxJ94qyiPauKCEpkAKEGTyg1dYTfOWC2cUZCQ+2ElvMmRKdZI5zEeqagHDkNocUYUkLKBmVGcj5Dt9wp+HquPvrSUIIUs9GhJAKIUMp30/NA7Kos+/vtTP2mJ8H8J3toZbXh1ksJjLlSq3SUaSYBA2kx2mvmJQr6r8seFrxjyJ8GuW3SNKssLtLd9twEONqbagoWSASUgoBMbg18sqdcCiOkV8RrymsTWZn6Q/DU45PS8VPj/IgiaA608vOfuL+I0JecH+4v4jWTc9I0hbo6jfh/s0mpTrrgS2QtWqdde80kvOfuK+I1aFzSsTQnenF5z9xXxGhU85+4r4jRoztIC59O54j86SRrUp95wOuALUAFGNaSXnCPSL+I1aFTStiVbVtrVR8KvkaPp3P3FfEaxp5wrIK1Hqq59xouwpJWiNQnenF9yfSK+I0KnnP3F/EaIztRFEaVn+wrxD+6Z07n7iviNZ0rnQr66pzDWe41YCSsjUJ3p3TufuL+I0Jec/cV8Ro9xDSFHatueY14f7NGX3P3FfEaxbzgS311ap7e81NwKVMQdqBW9P6Zz9xXvNLU+5+4r4jRIS+nyLrKPp3P3FfEayrFujH/TOeI/OhTRP+nc8R+daTUXAT5YdGz558KvkaCmM+efCr5GhYyH1IGiTWq2naoGjdPR6FfiHyNJG9PR6BXiH90LNEQaIbUI1oqENG005fmteH+zShtTVea34f7NCaIcM0NTRgSaFIowKENG6c96ZzxH50ob01707niPzoXyaIrY7fyb3SsFw3iXG7OFYvh2HuPWaSkKhe2eDvlBKvZXN+Tnyo4hg10/dOXjAxCzwq5QXrhpTylvEwIAUkKX1pKlGEhMwSAK9N8jDeA8F21xxZxa6pGElDjCLVpOd276hKmkJ5qUOoJ0zLFfO9gDxxxHjOIYXbpwi3zum1w8u5xatZoQyVEAqyphMkSQhSjsTXoNBFrHbR8V/GOWE9coxldLdeDmcd45xTiLjHE8dxS7cucSuCtwvukqIUoRI7IkwKqnLX/Vbf7w6oNNtJDTDRWMyuxISNZ3PeTV/b8L2d9dutKvWzmabdW6yJyBSErKRPMSQe8dm77jjG14eumrLAcPFtctnJ97LQdfR3NzolR5qjNykbV1DwRVp4DxTD0uqvrB22KWwpLbwCHFztlSoz3yY2o77AnsFwtsO2d42h5SXMymiEzqImSNQTseylXN1d4kl5RsB0y3JcdczdOSe0jUDugUD2BP2DYceYumw2rNC83RrMaAEgVCEayl4t3Lp6ZhCki4mUmCYJG+/Pf1V1nDjSMP8Av0Wqb+3MpVbl1OYDcGFDKr1giuHtsXftSsJUVW+UdI0CQlQPLSp2F3brqXFWd040+kx0RAGZPLWqITTh7+J4i5cNh10uDO596bIJUVHOmSetqN+fdV4nC7TFba4aZhxxlILtu2BmABEyncbD/uqm1xlvIoLF6t8JIy9MkJQZ/Lp26/Or9s2buHJcNjbYjLZ6Va2SXAueSwuUnwq9dUQpcS/0fCXGn7Ri8s1tkFpwCELVEKSqeY331k1T4veP37Da7oLdQuVsLeSJHJSQobip15jruJvls2reH2z2VCw4hSwrLzjdX+a1zrrby2s7aMjaVHNlGVOsRvVlhWjLzJ+8WqA9rlTIkhUagA76ctd6QlawFKbSchUElvdM9kb1OCrdjD+kQsm5Uci2cu3YpJIIPsgiluYivEsXVd3rylPOKzLfACVJMbwNPYKsomWt0phaFrYcWhpPRLaJkpOwKT6iR7IpQKcMxdKluBVuopKswglB0J79CZ9taU6hKlqbXGVGYBM9cEgQROnbpUa4xK8eCM7zzjAkDpST7CedVyQ6jih9g8MsWzWZSbZ/o0BSpjU8+8fxFcY+HngFKC1hACQValIGw9lXtgtvE7Ju0daU45M5krCVKSPXzGv+TVVeYeu2uOhIWlxQMJ7eyotti2SsEUrD7hClsh1bjKkot1adIlQ1nTmNue1PurNu7db6EltkOZAgrHUVE5JJ331Ok+2hzTiH3x51CrkrS6iFCAkwROu4GmXlGvZVphbLDtk828i3tG0RlzNZnHj3kkdszsOVQoqsQvF4etDLLbtv1SjI5lCyCdzAGsaUFibcALK1IcSrrKyS2E+sazO2kVahVm81b2z67hxzMGkOJIUkSZUuDtlScsTG5qQLvDnkdIlbn4q1uuNltIbbQDlbEz6+WtUWTLa6Zx1phq2tw+4p7o3HlaGSCBCY2y98nnRYG01aW96hhC7cB10BR66OqlUZgRscsEa7igwbFTa41hSLdJLTdwHVlLcJjTMZOqtBE6b+oBbnEqLu8Q04zlStt5eQmF6oKUAq/UZJJ/5AcqrkhCasba4xxb1slbNvlzhTS8q2zAzFBOhAJmDyIrpbtT2DsW2GXrycPKCAh51gvWziVGU6o6yJOsEGDJSRXFs3abD7syl1xsWq88HQ9fRUiCJACZHcRXU4tYv4nhVult1q9tQ2VtBJzKajfIZzJHdKh3CoW0UeJo/1bF3Lxl5m1uXXytxhoKLSiASXEezXWDr64k2uI3j9w+/cpF8sJzqabWQsq0SmdDmEKmTrAOtLW6yo2t82V2zq2cr2QZgVSUlaQdCFJUdORnbSqm4u3lX6HWXFWxDbLa1N+cFIASCR60g1LIXOBXbdpiTVzctB22Q8kl9TQUpszqladx6xqN9RpVpxJcrbxbLBtwXusDqheoIUPWP5EcxXL4Ji8XCUvpJ6SEKBMIWnsPZ3Hkddq67FbX/WwzYKdP3phWZTzume0UkguK/5NkQrtgHtq+Cux2PDfRYHg+JOXCEIdxFlDrnRGUhRcSiABtmUsGOUHlVRhdgpfTOvhUtQ66pKdFHrHQc40n1VQP8AELgwB0NFa0XTiHm85ylLLS5TMbTE6V33B79vjt8MJQhJeDSGlKUqMyghrMABuZWv2A1ZRxXFGCXF1hzrSG0qK3UqCE6hOVCtB2iR7jT8Pwm2V9+vFswhtGiVGchKAYHdtFdZxCxaYZheCuEtpUth91eSZXkeypCtdCcyiY5ACoPEzdn/AKk2LZbjqCwh9BCEoJISgRppBBTr3HeoQ4fE8AdTaMuoQlCC30yQVyFFUJTJPin2GrHgdm0w/HGE4i0bixU+2p1C1KSh9tslxY7YOUJnfWuuZtbbErlqzNuVFGRKQBAARAAnvyke2ugseBHcf4xugy+4hLLL6cjLYUXMuVPRoT3qUlI7KEs+sMZwl2y+zzg7F1fOv3rdiq6u2nlhTqHXUBZbXOsAONlM/pkEg18duDrGvu7jJWCt8KcTN4ZhLljghvhhlmtWVCXLVm3lDwESU5ukyqUSpQcmYgD4Yu0p+8OhPm5jFea16/aH338HyvQtNdyKRpQkSKMiKEiDXOR7iSMc8xrw/wBmkqFPd81vw/2aUoUSFTW4o6ihozoaA70Yhox/07niPzpRGtOuPTueI/OlESKtcCZ8sWd6216Q+FXyNbI0rG/OPhV8jRdhS5QlVCdqI7UNEZ2DW/8AZV4h8jWjvRf7C/EP7qxa5EHehVRK3rR2o0JYNY55rfh/s1lbd81vw/2asX2YugVR0KudWhDArKysogGOeaUXlmU+cfzCsSyoc0/GPrQPenc8R+dYneh7DXXUN6FXan4x9aYy0oLOqfNP5h2GkU1jzj4VfI0IyFWjfQq7UfGPrRBlUbp+MfWlUVXuMVeBqWVTun4x9aclo9EoSncfmHfUZNPHoV+IfI0tj41ZsMq7U/GPrRdCrtR8Y+tLG1bG9UMVeBoZV2p+MfWmqaUUN6p839Q7TUenqHVa8P8AZoXZohVMIMq7U/GPrRdCrtT8Y+tKTvRVW4yNDUsq7U/GPrTXWlF5wynzj+YVHG1Oe9M54j86B8miNVwerYnbvvfZ0dbW4iW7tN4u3Q+ptb9swQopzJSY/EU2JlJBUImvla4vX8Lub1uwbNmhxL2VtDhUUJV54zHUgAlMnUhPea+ovJret8W4Jf8AB16F5nrd42bqH+hhZTqhSoIyKyiQQRoDyrwTyh8KP8LcUYrZXJaunk5ggMqzBIJgIVoIUDKT7xIIJ9JopqWNJdj4L+KtNkweoynJbS3RyPDN1dIfffQlK85QkIVzABj1bDXsBrpU2jOCoZS50SHD+M68yOtnPmjTrQBJHaTUrh3DcMRastZ8ziWy48pQ9MvUmDyQMsAbmNdBBrHcXOEqt7lhabm9W4XVuLM5ufVGwEg+7XTSugeOL2/xK2wAKZtcMu7RgIS0td8lIJcUJCi2NEk7wcxA3NUGP47iKrZlN+wU2RCS2pgJ6HOOfVAgkEj3VKsuIkKxhK8UtMOcbIK0lKFdYqMhcQrTll05yZqVxsrClFasHfQy6kqS5atoGRwRIUJElJB806pMg8jVkOawfBELt7y4t227lhIDoStMqA5pI30+RqrxENKcFzh9stlDSAXcqytIVm0IPIGrDhjiFBvWm7pz7vchIQi8JgFIGiXNRIjQHcdvKivsHUt564SW2mVOSsMKKkq7xHL2eyoQo04khN0Xwsws6pUkH39telWHG6WsISym1sCWUZAHUFpoZo6wyRrziO3Q15ipDQVK9FIMAA+d36VpeMOqUyMxDbaiQABzqEO8VwtfYs8i7au7NwKUlQcQyEthG8kkAj1GD6qqMY4Zu8EdU4bYtQcweaUVk66GFfWr7gm6ssWfdbub+5DSmusVsw00ByCUkBR7AdO40WL2lhiiFZsTvX7duF9NdNEnJsAjqJBmNhO1QhwbNk1cuOPOl1LSZl24cCVKO8Acz7fbUXoUOvEMNEp3IJkxVvd4QzcPLFqL11tCRC320ttoSdpKiAJ9lMzssW6LW3u33HWgU5mW0pZJJ1g+cr1ns7KploKww3DBZOG5cQbhcpZQttQBUDBAUDB17DPcaiP4Y20+yznUBI6iTIBO55Ewe7lFdI5dot7FqzU6HVrGb7q27+II5kjzT3bnsqgfbbW03bs2ZZJX1VXb4Us+oAAA9+tCnZb2JF1gxbbt0MutM3YeJbWHwChIEg9mwHZB01mlO4+4sBi9bRiLQWSpCmg31iPOC06zptt3Vpy2N3btssXSHXUEmEIJcBmTKuYknapFlgrzy3lPrbaMSHVkZoB5EkST2QapyS5LUHLhFTdoN08hq3yMuJgISndXPVUCSJ3PZT7fCcR6B5xi1W8hDmZd2JnbQFU6Dc99WS3W7VYZBBKurmaaBUqDJM+rTkACaNy6buXyhmy+8OmMrhOiT2aRPvoHN0NWNPbuVf3S7etwENFbzpU2HmmiEDaRoInv7K0vBX7WQpDjICQErWg5f4mSdda7ywwjEsQZtytbrOXkzIKUxqfWf4E1b4d5LcWvngbW3eIeTKXHUEk67Ann9azS1UIcs2Q0WSb2R56u9cbXclS1LKwhJe1lJBB0ECNqj3d6w9iHSMJNulw/iga5uZQR2Tz7I7K9bv8AyO49Z29sn7pcrZIMIUpMmdSR/c1Ro4OxO1S40vDFpcYbUVlxlJVkmc8a6jbMmRESNJpcNVCXDG5NDkh9SZwicJcxV5BaQEXicriw0oEQT50HcSNddNNDU+0vBgN87eNvBl4IUF5xIWVAgkpGkyZHeBVxb2rls4tDV2WX0mEhcNmO7TWrVngV42JuLhYU6oguBvrQntyqjXloBvT/AHYmX2JnNYNfNuur+9YVbutvQ2VBkqbWSJ6QtpIyk9qYqexY2LzoQbFFpdJC0od6eW3BqrzjuRqAFa7CTXQnBbph1x61tU4chSJC1wXBA1iTlST2gE9lTsT4XDFkWcQbQ9dBSUuSQtKgY1Jn1a9szFLeoituRkdLNq6o8yRw2bb7zr92SCQlSjoFQTIPdEEGNxTcMxB2xxqzeugHGeiLL6lHXKpvrRy/MPdXp15g+F4RhVo45Y3b7TmZAdbUdOUAkdYiDGumxmAa5bHODrlyyHRpUho6tPqgEk5sqVgbGBEH11IahN2+C8mlaVLk5G8uythmzBSGWlsNBMQSMqUqk8wSCY7quODMdOAcRu3Tjhbcb6UiD1h0iFJXr2mfZUzEuFHr9tbqbdKHLcoS63mEhWVJmNxqNOR1A10qpucLOLqbdtm1JlnonHDsMkgKPrTlHsrX7iMPtsvuOuN04tYWtwpCQ86lSxlQE9QhSCIGkdQH1g1Ew7ih68Rbv3IbdUm0ZYaLaYIIUpMesjJPqFcpc8O3xUpJbcysSlyU6aHXL27j31PaYxHD2Xm3kLYT0vRjNCcqgSCEzzSOznA3olJAdDXY7bhjiW2RjBbZlIQtKGyVkk5ToSPXmPtr3byT2BuOJ7JTb/T4Y3apdu3LZWZxxTiistA8pSgKWAZyyJBMV8h8J3dwvH2+kchQ6n4wKjBEEQNToTX6P/Zq4Kxu94at8Sads8K4YLrQdyWyHLh9QlKUJCgQmJUrraJICilRSmLbokYObpHU+XLE3LLyPsryMttPBa2kggqUlRytmdIhAI0EEyBonX4lU0okmU/GPrXvH2luJV2mKJ4bsSGsMtNENAqMAlUaq6x0ga66V4IRXk9Zk9zM67H6T/DOiej9NxqfMt/4mlsK7U/GPrQKZV2p+MfWiUJFLNZNz0r6fAbrKihvVOif1DtNK6FXan4x9aNzzW/D/ZpNEhU6s0phXan4x9aBTKu1Pxj60ShSyKJWZnXgO4ZUXVmU+cfzCldCrtT8Y+tG/wCmc8R+dJolwKnVvY2WVdqfjH1rSGlBR1T5p/MOw1pVY2OufCr5GiEqupC+hV2p+MfWh6FXan4x9a1Qnei3M7rwbUyrtT8Y+tbDSuiUJT5w/MO+gOtbHoV+IfI0QvaxamVdqfjH1oSyqN0/GPrWLoKJWIfT4N9CrtR8Y+tbdaUUt6p0T+odppdE75jfh/s1e4G1MHoVdqfjH1oVMqPNPxj61qtKolYh9Pg10Ku1Hxj61lAd6yrA2GO+nc8R+dYmtu+mc8R+daTU7Ef1M3TmfOPhV8jSacz558KvkaF8DYfUgKKhG9FUGINFOHoF+IfI0pNNT6FXiT/dAx8OTVbTvWqJNUxiNjepCvMb8P8AZpA3p6/Mb8P9mgZojwzSa2N60NqJO9UNiFTnR+OvxH50kb0930rniNAzRHgs+GMVuMExyzvLVWV9twFJ9tdr9ryxwbDuHcEfbaFrxLjiPvF8pDgA+7FYypDYAABU2pR9QHOuCwl5FtiVq4sShDiSR7a6D7WrD3EPGmD3TFyl6zODMuqQXcymQlKj0YT+XYnTfNJ1rq+n7ye585/GqrT45dPerPH7ofcMHYKiUS4pttlR1CSj8xHco7VzDjyjij1+gNNDOQhRQChtIEQlOugHLfb11d8SX5vEJfSGwpCDo2mAFk8vco1yiLlCcjCjmbRBIBICj9NzXePjR6bw5g9ljGFKunbZq5GVRRbqUhSgU698BQ0MGUmDOhrkOMLO3uSy/YP3BWhvOli4JU40kGCjMSfNPIk6Gm8KXr2IY7aXTjbbNnYoK0JQcgmIzntPr05RGlBdm6xoPuJLaLxSczlsxr0jZOh7p09eh2NWQ4d5Sy4rpJzzrIirS1u1WDKixdl0ckZeqPWDy7qVf27guVJMKjTkSPdShb9JCFOhsgeaflpzq7IEt1y9U5cBhISnVYaSUpR7eU0KbV1ZLnQZUaGIMdldba4TZ4ZhZu7pfSltIUll1XUC+XVG8d5k9lRMPxjK5buXgW9ZJUoqbJgBBCpMDnmUCKpkKRF3d26umbeyHpElQJ6uYbSnbTvr0ewumsWwKzbtOjv8Va6qm2WUhCUglQAUkgzvuDua4PCMJub826LdCnzm6QhtQEaDUk6CCI/913r+GXHCGFqVYoctsqpQ/IK3dNVGQI3POYqiHNcQIxXE3lh5N0ElXSf+QgJyHlEASeWlVmHYcpT5cu31tsI6qpUZUez399aursvn0hSFGcylwv2qnbumrDh7Dr/F8TaYweyXid55jKUozSrt/wC+Q50LaS3DjFt0lYhFuw3cqKWSjpPRkDLAG6j2JHbvO1dHwN5HOIPKPiYYw63W4lzV25IIShHt29VfRHkV+xPi+L3VvjfGr+UOkK+5oMyAJAMaRpsNq+yuFfJXhvDbbLVlYs2zbKcqAyjL3kntPtrz2s9WjjuODd+T1Oh9Flkqeo2Xg+R+HvslItsIR0yMt2OqtxeYFYjSSBoe/wB9QsZ+ytaXTLXRtLs30ef0ip57iY+UGvu9OF9XXY6+aCDTf/jrD6CSlOU6EZQZHYa8+vUM931Hp36fpunp6EfnO19nq8sLgffUXFw2QYdFspzMZ7QOY74rqOH/ACBurdacbYRbttguZktq6buCgZju2A5mvvU8MWjkBDDbbglOcJEwd/6qKzwTY2u7XSFapMq0J7xNFPX5Z8sDF6fhx8I+Z8E8iNvahnpWW2m1IhwBAzH/AL7967vBvJkzauh1thYWEjKo/lOx9de0t8O2YUHEshKgfOSP8mpicPQhGVKQkRFc7JlnLds6WOEIbRR4/d+TJt/LmHSAqBOYAED1x/EVSY55GcOxRgJew9bikghKh1iOUjXTsr3dVhoZkgbzUYWTaVRGnZS1lkt7GvHGR8x3P2cbJmVW6Lu3KdXLcuApV2dp91SMG+z1hdsiVtEuhzOc5zDTaEnSK+kF4ShboXlEd+tOVgzUJISBoOetG9Tlaqxa0+JO6R8+4l5IsMdWy0vD2lFKgsLKBm21AHLWPUDXmfG/kQubrFizYPi3twhKcnQpUUqUrUAgiNDsqda+xncJSpCg2ciu2AKqrjhv/wAttxSAUpVmIAG8an10WLUTxu0ys2nx5VTR8a435KMXwthqzaWEotApa1XLkh/Koq6kDTN26RO1cOLa5wm9dGOLcZwy7SEM3dsyXXVJOqQppQKTHMKjXY19tY3gpxC5Um2ZBezKQXFjMhlR0B7zrI0051wnFfk0VbNpawy0XcrWUauNBanYV11kHXu7hXVxax105EcjNoY31YnwfLmNcDWtja2t1aB64vnWHWXba3bIWsRorKZE6SUZtO3QVxjPCuIvYLa31myt9t5GchbJyLhStSNpnNrImOcV9Q455OcZwPEULt2W7QhLiJQgFAcczQkRtlkA+s91RPJVgzTGA8QYZfJaaCllLKW1ecmCUo1OyCmQRtqe2enDV9ONuO5yJ6FTyJS2Pn9ri3DMGwZg43hqL+/UyGUOWauhLa0Hq9KgAkq0BBSojSSmvN+IPKk7fXTJTa23R2qFpQbplDzhUeS1kSo/8hHbANWvlow5GC8d379otLVrdhKlNpHVWoaEkdpICvaa81ukrfbWXEJUtJzdJHW7wTzG29drBCEkp1yee1GScJPHfALmIzcqfQnIVmSmc2WdhJ31r6K8hX2qMb4eu8GwribiC6ThVgyq3srpLCVLtJlQz5E5ndYH4mcRpAGo+a0OBxIMdbKRHaOz3VMsVBDikriRBC55bg1u4Odbuz7W+0FZO3fEv+stuN3lliLTVwzdW5KmnUqTOZJkyPaa8jIMV0/2dPLjYJxC08nvFxad4bxMKRZPrSM+HXaiMqZIP4LitI5FcgjrUrjiwTg3EF7h6Wi2ll1SRmEHevK6zTvDPq7M/Rn4Z9ah6ppVhUaljSTOapahBpp3oVCawo9c0A75rfh/s0pVOdHUb8P9mlHaiQqa3AO1LUKbS1DSjRlZp/07niPzpR3p1x6ZfiPzpKqJCp8sE7Vtrzj4VfI1lY15x8KvkaJiV9SEHehVRK3oVbUZnYNbHoV+If3WqL/ZX4k/I1YruJXS6Yql0aEME70bnmNeH+zQHejc8xrw/wBmrF9mJrSq2d60rarEMBVZWztWUQA50N9KuVKnMfy9/rrQS3+pXwj60L3pnPEa0nah7DG1b2GgNz56vhH1prQbznrK81X5e499RhvTmfPPhV8jVNbDoNWtjYDc+er4R9aIJbnz1/CPrSk70Sd6phprwOSG/wBavhH1pqQ30SusqMw/L3HvpCdqaj0K/EP7oGPg14Chv9avhH1raQ3Hnr+EfWlUQ2qmNTXgclLc+cr4R9acsN5W5Urzf09576jIp6/Na8P9mgfJoi1vsFlb/Ur4R9aJKW/1q+EfWlUQ2qmNi14GpS3+pXwj609xLfSrlSpzH8v/AHUZO1Pd9O54j86DuaYtVwSbFDS7xhJUqCsDzR2+uu08sWCHEMe4kQy392ftbW1DTq30IUq2Nq2lWVBMlJV0gJE8hXBIWULSpJggyK7zylXlxxFwVgXETDqW7noThF0pxCVIOVYUgqJ83qLcM/8ACOddLQSSyNPueA/GmCeXQxyR4i9z5vxZZwl9dh0aJbbQkgLk5imYIPMwCeyYrmcy7Nb7gS24rROZxOaJ1kV23E+HKvuIMQduAC6tZcFwIStS80lR5Aa7R2dlcreCW3UwG7kdVaCNNNJHr/ivRI+HjuHrzoH0pfQ2/wBNCUl05gBOojlpInWrHF2HP9Rury4QqzQp/pUW4MZxMpJI871jQcoqFbWqFYEzcv2wUy24oNxOZwwCR3dvq9lPGOuONPMG5KbZwJWW1NpWGlQCMgOqTy0350RBNwu+xe5V0to2C5r0nRZFKBJIMiJ/6q4w3hpp5xKEKUp/8rLJS6sQJ60wlPtNQ7fHLSx0til59XWm9BSnN7FT7Sac7jbmLKYtsSvVOtNgfhNDKw0n9KU/mM/m/k71RY/FLiyuH22+s90ehVcKS6ARuAluEeySO2qy9wp9KGw2jpUqMZCQFHMdvfzrqegtbMMC2t86WVKFv940C1EQVAHlMGT+kV2vk04Xw2/6S6xhx55xspNoixEpBkglYUOtpBH9VmyZOhWzViw+5smcKjC08PYE09aqH31lXXcQUJhJHnSoEHWUwOtpMQRSbq7c4rtc+IpW6lJS30xWpev5Up0EqPYkdpr1m88g+I8Y43bIskpt7AErCFtpCzrGiEFUk+ua9h4E+yLaW1y1c3jDji0OEplxSuj5SJMA6bj+awZNfixR5tnVxemZs8uKR8s8P+RbG8fuUotbNwOr6gK4mY0QByMctwJJiv0A8gv2bsB8lmEW2ZgXmMrQA/fEdUKMEpSO4yO+vQuAfJThvDq2XGbVCHG2yhEJ0SCdY7Ce3evXLDCW0MIKkchJAk15zU67JqV08I9VpfT8OkfUt2UuF4MhGQFASZEwIA07vZV6MOQlCcsFIE5R/VSOi6MgJA5SkD301xA6TTQAawJrl9Pk6nV4KtWHoWICJjlyNEizDaIyBOxkD3irNKMk5RA589KF5IcQRCe/soOmidVlatsFUiSqTy2owhC0wUyYmBpU0NpyGdO8f53VHXlJ3MTtyPbVNBJ2KbbQOWkg6GSKwgZic4Hq1+dEpRWBrIP1pK3NZHuOlAw0jFsgDzpGuwqG7bGZAIHMxPvqe0S4FEwdZiPZSnEhJOmg27KFpMNOmQlgoIAO+pmsQClQKoUNBJ0imuCVzA2Pto2+qrUye8a0FbjG9iQLQ5SdSCZMwPVUJy1Cw51AAoGQD37VYtIBO8AU0NBaAVEiO6d60xijO5NFK9YoLQCUIaBgQgae7t/yKrL3BPvFwlHnFJJQQopIJGsHt7q6tTADaZ37jr7qjqtwhoJCdicpgHb+jRNAKW55Xx3w+Le0XcBAfdbMhncSIAJ5aRMnavlHEeMgrii/PR5UlxbJ6NAQJUIEE8+rqBqc1fbXHNkq6sFjIsoUmCW9IEax7Na/PXyvYUnhzjm4vAEttIWrIVpC4BEAJJ23ER666OgqcnBnN9QuEFNHi/lKWq8fvLi4Ki4XczebUK/WZ3gSBPMz2GuKx5ktYk2Lchxh1tCk5RoJTBkewevL310PFuN//IV2bTYAKkwoJECNv4kn310mH8K2S8NwW3vEqTfvMFIDadDIbAE9oWhRn/ka9zjj0x2PnOafVK2eaPYU+cWfZWypt1YD4CtxpJ9hk1Abll5IWDBAI9UwR7q9PYwlxzyhYul9nMy2ytm3S6SR0imyhKj2gK63rAoMT4KYssMVcqBXcOYQlwMNpJyPrh0x2QmBrzI5mmibObwDDEXNw4hVy1avNNl23WpRkOIggDsJGoB0kaHlX0xxLjafKfwFg/GqmlN4iVKssTyNgBT6NCsCdlbz69BEV4ujAGn+L8aasw2hm0VbXTR3JtlkNrnvhxKvZXqXkk6a28kfGeF3LiHHLW9TDQGqVJWpKiO6QD7a5+tgp4XfY9n+E9XPS+qY4x4lszmFJb/Wr4R9aEpbjz1fCPrWEb0FeVR+jZNeAnUt5W+srzf09576SUt/rV8I+tMeHUb8P9mkHeiQmbXgyG/1q+EfWhUlv9avhH1rR3oVUaMsmvBt9LfSrlSgcx/L/wB0pSW489Xwj60dwPxnPEaSdqtCptW9jcN/rV8I+tY2G85hStj+XuPfQVtv0h8KvkaNme1a2FrS3+pXwj60JDceev4R9axdAdqNGdteDcN/rV8I+tbhvoldZUZh+X199Kov9lXiHyNX2F2r4BIbjzlfCPrSylufPX8I+tbO1AqjRnbXgxQbnz1fCPrROBvK31leb+nvPfSlUTnmNeH+zVgWqewJDc+er4R9aEpbjzlfCPrWjvQnarM7a8Gylv8AWr4R9aygrKIW5fYN70zniNaTtW3vTOeI1pO1TsW+WEN6az558KvkaUN6az558KvkaFjofUgU70aaBO9GNqjDQadqaj0K/EP7pQ2pqPQr8Q/ugZohyDRjago6pjYhopy/Na8P9mlJpyvNa8P9mlj4cMGiG1DR1THRDTyp7vpnPEfnSE0970zniPzoGaY8Ajeu34Gu7PGcOvuFsUW23a34Krd91IUm3uMqkoWQdx1iD3HTWK4lNOtnSw8hxPnJUCKuM3jkpIXqdNj1mCWDIrUkXfl94Dv/ACbDBbq/s3LNt22dR97aShxT0jOnNBKAoZko6pMICVHrKIrwi5tnHXF3CytK3Wwp5LYBKWvOg9hMT3aV9reU7ipvyvfZhxJm9senf4aLd204khJSjMELJ7UgKJIGu3ZXxai2cbt7dZbyG4dUlTiHMwWNQZT3k+rq6CvW4ciywUkfmr1PQz9O1MsE+39CvZucty4paEZhmHRZZ01AMcgBEVXwU5yUwmQcpgxpyHP+q6C+sim3Nw2ouoyqQ8tKpzqIToT3T7Kp2QLJkBQSp0rCp3hIBIHvpxyha8QdJSx0aVspVIAQArMQATJBPdVzZ3CLFCnUWzS1DRIfX0hKu1IiBHbFV569468kdKlgBtIQISoA7n595IrMOQsvArRKQro20a9dW2/ZMz3A1TYSR615JOFVcT8X4c/iifvjCSFFgg5VKBBCT2iO3vr7j4J8jeGW2B2TS7QvOpRknKAkamdB6vlXzP8AZ6wRw3uHOBoPOlYZQ55ubXMtR7NZPdtX3XwQzFggOHVKlELPMTp768Z6pml10me99Iwx9vqofw/wczgrIShltvQkZEzCogewDSr62wdttSC2hRETCiADyGnd21PZg8hG+25p7SOjXmJAG8ASa4MW+56F0ZbMoZVmAlQO0bVZMOysAEGBvvNQF9bUGEnmToaJt3I4dSdtj/NNsEuGkNdJnWMw10Jo3VNEpDYEjSOR76rTcrOgMa86YpfVnrFW8gmomD0slKdM6wR2E0Xm5TBHPTWoCnzzJGsd3qo0uBIMq3Gx7KFsnSyQ4VARodJio6kqUZ/ih6XOYnMJkA6f4aY2SNAqeW9Kb3GrZC8ioGkiD31pLCVCCNtp51KaAylMETrvSXFdGvQGdOW1QtPc020lsmfWYNLfbzCZ1I3il9IrPME9nLSkXDzmbUEA7aUuw0nYDhUkCFagwYpTavxQFbA6c4oXXcyf+R1gHYUTUOHMTEa6af8AuqW43gnlS05Mp00me7+qZlkA/mnl9ahuPgZcqgddzExQh9xQTlkrSd+0/wB1qjsZ2WRQAgdWZjX/ADvoejCU9VOUanTlRl0Lb6ykkQBO80p1vKDBCo1BmKNieSpx94M4bmKgkkFAWRtOhns3r87ftBsFziq9QppeUKSG2ynQAqGndOhr9DeIGunwy4aKcpAmFGR7Z5TXw95f8BVhVrdX5yqU248VpVoUzJSJPYnL7q3aBqOVHP8AUYuWBnx41harRDlxBKm1gJSeQSgKj2jNV3f8UKcuXXbZS0hlkFqOsW3C6gp15SUqPtprtocQcdtUOpZXcOCGFHKSetH/AOsR7aoP9BuFYtZOO5lvPNreccVpqEyme8GPeK92nsj5w423R0tljROGYhdtOrRiLhP4mbzSp5OSO/quE90VrGeNlcRYhbtMu9BblBcyR5uQSFKjsCY9sVyDyr1lt4sJWlTud0DeAHchEdsxrVhgOHi3bZfU71nUlTjZBhIz5lz8IHtV2UaFtUdZZXyGOJr5xLQITYJZUVKICpUhGXTfY+1Ir13ha2GGcC8S4gpCWxc9CxKh1lvLJfcjuAUge6vN8Mw63urRpbzCkPOi2U5rCjnfASI5EhRPtr1Lyl3DeDJY4Ztikps1Kdu3EbOXCvPPqEBA7kiubr8ix4mvJ7n8HaCes9SjlX0493/Y8+VqSaA70aqBW9eXP0PI295rfh/s1HUKkO+Y14f7NIWKJCZ8i1UJ2olUJ2ozLIy59O54j86RT7n0zniPzpB3okJnywKJvzz4VfI0J3om/PPhV8jRiP3kJVS6YqlneiRmYFF/sK8Q+RoaL/YV4h8jRdhfcUdqBW1GdqE7URmYtVE55jXh/s0KqJzzGvD/AGaIDsxSt6E7USt6E7URnYNZWVlWKY51aQ6v8NJ6x11+taDiY9Gn3n60L3pnPEa0nahrYd1O2NDiZ9En3n601pacx/DT5qu3sPfUYb05nzz4VfI1UkOhJ2jaXEz6JPvP1pgcTHo0+8/WkJ3plC0GpMaHEx6NPvP1pqFp6JX4afOGmvf31HG1NR6FfiH90LRog3YXSJ/aT7z9aMOJn0afefrSKYN6FjYyY5Lif2k+8/WnKWnK3+Gnze/tPfUZNOV5jfh/s0Jog3uEHE/tJ95+tEHE/tJ95+tJG9GN6FodGTHhxMejT7z9ac6tIdX+Gk9Y7z9ajjanPemc8RoGaIt0ElxP7SfefrRoWn9tPvP1pI2piNqFofGTPSfJDxZYWGI3GD43bJucBxJpVvd25JhaDuN+6vKfKr5LLfyfcYYlg+H3xvkOtJuLR1tUBFuoFTYIKZKyJBIMDN2zFrbKKFyDBCVa+w12nEuFo478mdvi7Sulx7hgLdcCVfiO2YlRSBzymT3Aqrq6DP0T9uXDPnX4x9HWo0//ADsa+UefyPmzEAu1K7EOlTQCSQ2mRAETpqTrB07Oyot5ZKfRbhCQXFQEQOsdSdvfUrEHHUOWanWU29w4k5kNgxyMSeYkd0iortyFKbynI40hSRkOx17NtzXoz4aSLItG0tFhDqoKnngCAFEGYGnbG/ZUfCXH3L9lTQAQ0eqqIKSrn/nZU1DLpwhTbbZLhbSkJVIy5iII9nbp1q7/AMnXkyuOKeKGcPsyEnpujUrLnCQITObbWCdOys+SaxxcmacWOWWSjFcnu/2ZeFblx+ydeSt1sFaGiJylPSZSs+uFH2CvtbCsNNoy0yFdQDYcoFcH5JvJPa8GWrYBzqKUELA0UYGaByGm3ea9YQyFIy7Ead9fOdZneoyuS4Pp+j060+JRfI61USnraxUhBkkE6DfSo7QATEwJ1pa7rIonMBG5O1ZkzU0TFhLaiJ0GwProEEBWh7tgaqLjiWzZJBfbEaZlLCEz3E1Nsr5u6ZLyQC0T1VJEZp7JitMcc5dhDywjyyzSVFX6hUkI6QgAKPOI5RSLJ/pTA0k7b61YW6ukUoDrQJgabbiKZ7ElyUs0XwRVWmYkwZEajc1sNnLqO+U66VZG0K+sTMcjy+u9aLZC8qECdgZilyg0GpplepCU6+yfrUhDaVoBJ7jFGq0JObZJExzo2rYt6CY7jvSPsMdUICIJhUiJEGklCnO8jmRViGFBBBPaNB8vdQt25TJkzGvvq+myk6K9NvKepO/bWl2hI1SY7JiKt2mIJ0Gp1nagcSdwBBO1RQLUygGHhSgYPbAposBmAzRrzV9atFJSEmRqSRoajPFKJ622u1MjibI8tENdulC4UQtAOpnU0vqNqEAFMnnz7Kj4liZtiQttSNgeroP7OlchifH1pbFQS6FJQCSk7hM7667032ZpbIz+9B8s7xL51M856xpwVmB1k8xXBWHGVncoCmrhCtBKM4BSewia6izxVtxEJWFGOrzFA7WzQSae6ZJvUh7pEnSRBIr52+0L5PGuKMBu3+gLgSkqW0jqqKoCQoH1CCPXXvz1wpZB3MawIiqbHsLXiFitDchxY0gRz29X/dTHN45qSJkxrLDpZ+Sl+03bXi7dKFtdE4UqdcMyM8TEaVZsWaH3XXQYcdKXCkHMInKkd0kT7BX015d/IA1gNhimK2H/AIyF9M4hS05spVByTukAk+6vmm8xc3Lw6Ztu2unykuqY8+UgJGflCTJEdo7K91ptRHUwUonzzVaWWlyNS7nNfc0tNm4acDgb6NhOdXXGZ4RMaE5gT7KsMcurR2ydQ0Q2noQ3mSJzAgA/xJnu76gXmFf/AJCpTLribv7yHW2iiE9UkmDPaTAjnFMt8Ks7p6wYL0dK22lSlSOjJWAT3wAfea6a4OQ+WeveSLhz7zxS1f3LKxa4Y2MUvEvH8qD+Ej2ry/z2VDx3Ff8AV8Xu7xbaczzilnU8z667bC32sL4A4tvkNlJxG6YtWnpgqCQtahHqW3XnCq8x6lk68vT4P0F+BtEtP6e9Q1vN/wAkaUtP7Sf5+tLU4n9pPvP1olUo7Vy6PoUmw3VjI3+Gnze/tPfSVrTHo0+8/WmO+Y34f7NJVtRIRNuwS4mPRJ95+tD0if20+8/WtHahozJKTDfWOlc/DSese3t9dILiZ9Ej3n60x/0zniPzpCt6JITNvqZhcTPok+8/WttrTmP4aR1VdvYe+lnett+cfCr5Gj7CLdoFTif2k+8/WllxM+iT7z9aw7UCqJIzOTMLiZ9En3n61vOnoVfhp84aa9/fSzvW/wDYV4h8jRUK6nZouJj0afefrQdIn9tPvP1rR2oaKjO5M0pxP7SfefrROLTkb/DT5vf2nvpS96JzzGvD/ZogOp0wS4mfRp95+tCXEx6NPvP1rR3oTtRUZ3JhdIn9pHvP1rKXWVdCnJhvemc8RrSa296ZzxGtJqdgu7NjenM+efCr5GkjenM+efCr5GqlwOh9SBTvTKWnemULDQQ2pqPQr8Q/ulDamo9CvxD+6FmiHINMTS6YmhY1Bp2pyvMb8P8AZpKdqcrzG/D/AGaB9jRDuaG9GnegG9GmqY6IwU570zniNJpz3pnPEaB8mmHBobUxO1LG1NG1Ax8RzHnHwq+RruvIq+w3xzZM3BHQXOZhaFapWlQKSkjmDNcKx5x8Kvkal4NfLwzE7W6bOVbTgWD6jVRl0yTDzYvewSx+U1/I8j4kt1sOssPJWh1sqSttaiSlQWQQSeUj+KrUWaXLooFwhbi0BSUxzP5fXXrnlv4cbHFV2u3bSlq+CLtgCcqUukGEzqeuViJgEGK8bFtcJvG9Sp4hQSVaAgDQeyK9tCXXFSR+UNThlp888UuYto6HC0PFlGdJc6ZBXHaBIEnsAST7q+4/sqeTdNpgTOI3CEpz5l9IB1lEgAHugFQ9tfHfA7Oa8TakrCy8llKxqAnqTHwmv058n1izhfCOGstJytdCnKTuRA19tea9ZzOMFjj3PSehYFObyS7HZtlLSRkSEpSIojdlAzaQe2q5a1FJ00jUCvHfK55TcVFw7gWB57N9tGd68kBYHYmdE+vU+qvLYcEssqR63NnjiVs9S4o8ouDcNsrN/iLTDqSB0eYFZVyEdtfOnGv2k3sdeU3hKFtss9dJuOjbSsTAKiToDvryry17B+Kr3EFOoswyFLVD7yunIJgA9aJUdZ9Y761deRniq/aQspVduNtl51myeY6RxSTq2RnkEjUDTmJ2r1Gm9PwYvlOVs8tqvUNRl+OODSLdny2Ylh12km8tbu9QS64pJBbbAGYQTorYwJg7QTFS8L+0wLLMXLyVJSUpdIlaVzoUlUgGJ11PZXHXfkG4kuWBd3gcW90oShi2YQvO0DIQpIKSByPWrl+JuB+JcJxB22Rw3ivRNrzG0Zt+iS8iOw6pI5bg91dqEdOlVo4M56q+GfR3Bn2vw3hlsu+tlracfLSC2olalEGMylECNDrXonC/2xeDVNld7cOWa3OogMtKeRmGh6w0MDv19lfnLjONrXiFxYnDX8NQtKUrsltlK0kaSQoAz6hyqFeYhfWFqi3bbdRbpAl68WCk8ylB82TyE92tSelwz4JDW6iHLP2R4R8sOA8VsqVY4lb3bhBX+GqQEdp0EabzERXX4fi9jiISpm5bWFHzgqR/Ffj5wRg+LtYszilnc5lqCyg2l45bLbUB1UgwRJGoTsdu6vpryOeU7ifDjYsP3aTcuPBKrZ+FA8iYEESY0mCe+uFqNJBX0s9DptZOVdaPvT76hQA2IHL51JaRnIUANdxXmXCPE9/eW7C760cUSohTqUgA8u3+K9Ns3EFlOhQYMgjYVwpRSZ34ytG3UpTpECO2o7qkoAMQOZNSLpZSCSIEb9lU1/dr6JWU94j/ANUpvcauBtxijVq0pxa0gJSVDaSB2VzPEPlEsMBtHX3nEFKEZykHradg56cvlXB8e8Q3bTqWltp6J5SrdRBylCloIGnKZT7cp514X5V+JLx9oWmG3RYvLq2atekcTIQQMzqgOatPUMvOTW/DhU2rZhzZnjTaR6Txt9qTCcOfLVo4ucnUWsEBS9QOWwMz6h7OCxP7W94lbYtbR95wplTbxaIKZhOiVSknrGFQddtJrwDiBt5jiZhpw3Fy20Qp/onZKEoTo0mdCZygk7SeZJrgsYxJxtZtbNHRWieqsu6uPK/MQBPVnTvgz2V6HDpsKSPNZ9Znk32Pf+KPtM4rxM6w9ZssYEyjM4tanOnDxSCE5EIOZPeqNYHnDWuG4g8q1zi1syoXF0t1tSelWwVdKkLmJCpAG8EQTXm7uA8T4u+q4w2y+5Wz8NMhlgsqeQnTPKuuqT3e7avR+C/s58Y49es50sWxCQVLUtWUGOsCAk5tece3Sa2t6fGvlRzY/wDKyv42yZcce47ZWbd046+WcwDbzT+ZSgkcwuFExyUB3V3fCn2ksa4fsGbt5hm9w0KKVLILTie5SdQT3SDrzreC/ZY4gtlhTz6pVKFMEkqXroqOscvPfWu4sPsvNXGI3Sr5u6uGi2T0DbaUNoVyKjnSPYQY7KyZZaTIt1Zuwx1uN2nR3fkx8v8Aw75Q0qat7tLN+gpQuzdUAsEiQU8lAjYg92h0r1i0uEuJ6RIJzjqmvlnEPINdYLf271zZqJQ4hTbVsoIUiDMqUdExGn8xXvnA+JF/C2UEoXlAIcbdCwQdAdCYM6Ed4I0rzOp08IvqxvY9XpdROa6cvJL8oOENcQ8IYlYuBP8A5DRRKhISe32V+X/FlvcWNw50zBU5bvFkKA2SDEEacufPQ7g1+q14gvMLjYiCO7Y1+e/2ncMawHjvGrcOBpLpC22kp2BTIPv0rb6RPpyvG+5h9bxdWFZF2PCOKcZUu3tktoCS0qD0aiCrMe/UGU0HCuH3N7idu4wtVz0CSoogyoJQowD2k+3aix1bBxZCWXAkfcy+tMEkDNJEdpJ9gBNej/Zxw8YrxHmU2G7HCkuXN0sqKSW21pIg9qiUD4q9jKShG32PE4MMtTmjihzJ0d9x803w3gmF8LIUFvWEu3SkklJeclShJ1MaJk/prz87VccQ4o5jOKX966cy3n85Prmqg868RkyPJOUn3P1votJDQ6TFp4cRVCztSzzpp2pR51SGSMc8xvw/2aSdqe55jXh/s0g7US4M+TkUaGjO9BTDLIx/07niPzpCqe/6dzxH50lVEuBM/qYtW9bb84+FXyNaVvW2/OPhV8jRdhC+pCjtQKoztQHajMrFnet/7CvEPka0d63/ALCvEPkaLsL7ijtQ0R2oaIzSFr3onPMa8P8AZoVUTnmNeH+zVgdmKO9CraiO9CrajM7BrKysqxTHOvOB1YC1AZjoDWkvuT6RXxGhe9M54j86Eb1SSG9Tt7jenc/cX8RpzTzhWeurzVc+41GpzPnHwq+RoZIdCTtbmw+5PpF/EaYH3P3Fe80hO9GNqFoYpPyOS+5HpFfEaah5wtKOdU5hz9dR07U1HoV+If3QtD4Sd8hdO5+4r4jTEvuR6RXvNR6YnaqaGqUvI5L7n7iviNOU85lb66tU9veajJpyvMb8P9mgaNMJPfcIPuT6RXxGmJfc/cV8RpA3pg2oWhqk/I7p3P3FfEaa684HVgLUBmOxqPTnvTOeI0DRqjJ1yEH3NPxFfEaaH3I9Ir4jUccqaNqFpD4yfkksvOFRlavNPPuNYl9wR+Ir3mhtwSuBqSlXyNe3eSb7P7vE1m3iWKoWGXNWrcHKVD9RPIfOgpbt8F59XDS41PIzzTjSzd4y8m9hiaHMt9w7ctsvrjMs2rrqIUJ/QuD6lmvB3r37va25cCFOB9Oqh1h5yY9RzH3Cvu/HuEMM8mzeJWmJ8NvXeB4jbOWl0vDXSX221pIzpQvqrKZColO29fDuJ4GFuvW7bqHWg4FM3JSUAqDmoIOqT1j1TqJFek9Ozwy4ulSuj8+fivHjlrnqMUWlPffydp5IMMVi/G+G27KxHTFPSnYkL1jv1r9PcDw4WeG2zSBKWmwgA9kRX56fZVwRavLLZWoAeYtVlwkDqwlvKT6yr5V+kGHo/AQCnWBMVwfWXedR+w70NVp3L7kS9T0Fk+qRmykBROx5euuNwvyeItVvO3DFvcB13pOkUwguKO8qVqTr216b0GVIUeR07qqMXxENJUtZiK4kcvtqondeP3JJsrF8O4XlClYfaFxKeqroEAj2gf1QoGH261h1LI0kqUASfWYryzjPynY0i++44JZArWcoubgkISOaso1IHsrzfjniLA/J/g6sV464jucXxC4SHG8NTKQrmEIaToB2lU+utOP3szST5BmsOGLcux7xjfFPCtiotOYjZt6nMyHAT/Gvsrg8Y8qPClsAHFP3KEg9dFu6QPbFeLYh5cPKBhXAV3xhwzwBYcH8NtFItsSxS2DtxcFZyJyIUMu5JBiNJkxXknlS4v8ALbacAcMcRY9jlxbcN48gnDstyzLyQkEnIgApER53b667OL0uc95zOHk9Vxwv24WvJ7fxfxtwJjmJtuX7JcLaSlt+4s15kSRMGJjTbbWqi6wbgPiAON4au0cQ9otlJgK7ik7V8wWflj4oug43eqaxFIhRdW0MyATEyOUmK9ASjEWrm2exCwcwtd0gO2zqgcr47UK5weW9HLRZMC+p/wAQIa/FqH9C/VHueAeS2yw55xyxWlDbqgSy8kLTHMa6xtoa9EwXgS1as1FTCX3mV9Lbq3W2SNQlW8dx+leY8AeUBbxZs7+G3UQjpCfPnYn6+/tP0Jwswp4NqV1mzABAArkZ8uaD3Z28OnwZI/FUdzwbcLw+yYtumWvKlJVmSR6zHf8AWvUsMvStrqwBuCd/VXAYRh6CJGqtDqK6/DFJYUUnkJ7K5yn1S3NixdK2OiD5cABO4pD9mcmaUkTGhiKUxdIBBiYJmrNu6Q82Y3HaKtO2C012PMeNOFXMbeShBCF5hmWIJJTqk/5sQO2uCv8AyM4ats3T6OnfJWcromJMkeo5RrXvN82kpKiAI0HfXnXFOLfcc6ivI0J6x5UxZpp/EH2YyVSPEv8A8GsEwZV9d31yy249qpDcFKU/pHYP87Z87xPjnyTcM4tc/eXTjGJZglxNq10xSAICeqAEwNIkRyiuR8uPHGLeUrFrnCMBuHmMGZWUXN2glPTEbpSf0jmedcdhdlwrwBgD91e2r2Ii2KQ4LdMNoUrzQtyCEzyG55V1sWOeRXOTt9kcrJKGF/CKpd3/AGPfOHvtAcCKxFH3bAr60BT0cpwyOr60ya9s4W8sXC+KuIQw6tsGDleYUn5iK/PDiP7Q2IYe/wDd8HwCzwtnKeheS2tXSpnRaVOCVTyMAd1db5E/L/xvinE1haG0wq7++XbdugYnZuJtv0hKnmdWwSUyopMTJgTTJ+l5Jbrb9RMfVMEduf0P0ywTifB7hwrZfYW4s5lFBGY+vnVuby2vISlUifNSqBvXyNiflaw7hriTD8F8q/BN75OcWuHlJYvnCm4w1xIO6X0yY7dO/SvWmnV4Ewi+wPE04nhLqpS4w6bltOkykySpHcCSnlI0HOy4cuD6jp4MmDUbwe57JdYDhtzbPINu2Q4NZTJPaJMmuGXwEqxxhFxZ5WW0ggpaSEGDvJjX1GrPhHiZeN2qVKy5h+lWYH1Gusac6ZBBiTpSPclJBvGoOjj3mVJbIPLevh/7cODqw7HsLxJtSGW7ppWZcSQpohQnmBvX3ziVgG1FQABI3FfHP23rNp7BMJ+8nI0q7Tb5wJIz9U/wa1enzcdVD7mb1CCyaPJ9lZ8RS27xAHCC2hLYSEqV2p835ivpv7Mt6/iHCV5w9heAWd2L24Lt7i7y1pW+kCENpSmAlIEnUmVKJ00rwHD+AsU4p4pGH4ex+MpSR0wGZCEApIJPMae2a/Sj7OPkTsPJzwXYs3Ceiu3kgojYI5KPeo7D213/AFbWe1FYcb+T5+yOJ+H9LJZf+XNOo8fd/wDh82+VryN3HDWGrxSwZdZbQsB1npM+XfUHsnt2rxVTzkkdIv4jX3njLrK+NLrhq8baNreFQQndKVn18jsfX3V8f+V3gVzgTi25tcik27iiprMNQJ1B7wZHsrzuGayxbfK2f+T776drsmRLBme9Wn5X+UcR0zh/3FfEaWX3J9Ir4jW6Wd60JI68pPyE485kb66tU9veaSX3P3FfEaY55jXh/s0g7USWwjJJ3yaL7k+kV8RoOnc/cV8RrDvQUykZZSfkN55wPLAWoAKOk0lT7mv4iviNG/6dzxH50k6zRJIzzk+p7mlPuT6RXxGttvOFRlaj1Tz7jS1b1tvzj4VfI0dbCOp9S3BL7kekV8RoC+5HpFfEa0rahO1HSMzlLyaL7k+kV8RrfTOdCo51TmHP10qi/wBhXiHyNXSFdTvkEvuR6RXxGh6dz9xXvNaO1CaKkZ5Sl5NKfcn0i/iNE485lb66tU9veaUqic8xrw/2aKhfU6e4Jfcn0iviNCp9z9xXxGhoVb0dCHKXkIvufuK+I1lAdqypSFOT8hu+mc8R+dCN6Y40S85qnVR/MO2tdCrtR8Y+tRNBOLt7Gqaz5x8KvkaHoVdqfjH1prLRBOqfNP5h2GqdDoRdrYWnejG1YllU7o+MfWjDSu1Pxj60DaGKMvBpNOR6FfiH90CWVTun4x9aalpXRKEp84fmHYaFs0Qi/AumI2rOhV2p+MfWjQ0rtT8Y+tU2hqi/BiacrzW/D/ZoEsqndPxj601TSsreqdE/qHaaBs0Qi6ewsb00bUPQq7U/GPrTQyqN0/GPrQtocoy8GDanPemc8RoA0qN0/GPrTXWlF1ZlPnHdQoGzVCLrgFPKmDatIZVpqn4x9aYllXan4x9aFsfGL8HbeR/hA8ZcaWdosH7uiXHSP0ga19JcYXzD3G2EcN2Li7d2wyurWysp6NY2iOYiPZXK/ZP4fbwu2vMdugmSFFEwZSgZj71ZR7a6fyRYQ9xb5VcdxtakltsLK1rjYa6d8xXL1knKUcUX9/8AB53U5FlzycuIbfx5PYn+GTxNhhtcSCVXZQClRHnA9or43+0P9me74dF7i+D26lAK6d5lAjMBOvrHKvvPhy3ON2N5chP4mzChukDQH1b6UAwljHELtsUCQ4SWl5hIPKIpGmzTwTWTG+f5nkdZix6iM8OVWl/L8j4X+xrw8XPKFjV64lGa1YICxuSuFa+w/wAV9yWKcoM6E18vfZSwcL4l47xNtIRbrxRbDQT5iUJUowP/ANH3V9VWyQlKSBy3rp+oz687f2RwPTMft6ZRXl/1JuWWoVsRpArjOJ7Jb5UlMBMag13AjoTI1A7arL6xQ9mWoa6nWuYkjqxlTPmryq8NcQO4etjh11uzu3B1rpQgNjtJI399Qvsx+Qrgy58oLD/GT6eLMXB/CvcTWSyXQmdEL/5aAKHKecV77ifD4vmSgglKtk8q89xPya/dXnH7VRtXRs4kkz3BO3tM10tPqfaSUdjNm08MzbmrtV+X3SPTPtg+SFfHPkTxrD8Lsn7q5tQL1mztCELcLYMJTIIMDYc9q/JzjXGuKeJOEcA4axXF3H8KwJKkWFi60lP3UqEKRoArlEKJiv0v4fxvygYHalpri8Mtk9Rq/tunQlHeQZB9WleP+Wzye2nlPxBOLY7gmCDFlIccdfwm1W0twgwhK1pUkKKhrsSJ1rvYNbCC6rpnns3pmZvoStfqv4nwzwdwnjGI4i3w5hbi3/8AUFIFw20gGUhQVqYnKCAd4kCvu/H+FrG04JwnC8RtG7k2qUqyupBCTz+lchwZwUrg5h+1wRpnDrlxA69qznezRrKjJImuwseCcRxl5P39L1ytwQEvOq0MiSRPr99ZNRrllf5GrS+lyxLejh7TyWOXuNPtWTCE2dtbKu7k3T4aLEa9VatpMJAVuYEia+nPJphjd3wVhK4C3lN9IbgnKpaPy5kHzSBoe2Jrl8N8jWGW9rbLVZMlyfxcyJBHaJr0HC8MtMOCWbRj7rbpGVLTc5Uj/DXHzzuNHoYpOdx2Rd2aE26ZgAHardklaSrtGgqpaSoxt66ubRISiACRHKubW5qJNu4Q2U5YMRvFT7VamtVc+2qtKujdzBMa6ntqybdSWyJOtEkwJeBGJ3OdICdTtB7a8P8ALh95ueGbu6cuThuFMNKz3NqkqulkSpYaT+qNJ/LvXsOKqlCgDHP1d9eZ+UDhJPGWEGyUp1LjagUKS4pGQg5pBGo110pmCTU6YvJFdJ8O2HEyeKsUYwXDGk4PhJeDS1gyvLE89ST+o6TOlfSXl78h+Gq+zR0PCtgMtm6xf3aG5Up5KAoKWr9ShnJJ3gd1USvs44RaXYxVbNxdYgtalKcUog6bGeZmu8wziXi7gyyVZYdfJesXW+jLGIWaLhCRGuVQgwZ5mvQY9TihtHY4mo0eXL8uT89vL1xrxP5aeKMBxDFWMPZVheFW+Dsf6c30LPRNFRSrJJCSc2oTA00Ar6z+y9ig8nX2fV4LbXttivE3FuJPW1vgdhdgXyXHkpYbKgJLYCEKdKiNBHOqfHPs4WeO3zt4rDXLa7eKniMNeLTJUToMpBCZknTTSvV/Ir5OuJ/JnflfD3D2AWWKLQW/9dxVS7y5Qg7pSdQkHmAB36V0f+xjOPTZzYemz083k6E7233SPr7yh+TnhjG/Juu04vsrC/wdu3CHziMFCSEQFhR1CpEgiDXwDhmFXvk14rUngfiW4xDhJN0tI4fvSc7bJykLt1L0OpVocpOXnNfT2McD8U8YNp/+X8U/6kEJStCLVsoQk80hKiQmO0D5UnDPJBhdgoLatAXFee4slSlEbEk1yc+fq+NbfxOpptNHFHqbuXniv7suOEVNKtWbtkgm4SHFKDRbnTmDzr0PDoW3mBGvIf5665bCcDFiwlltAbQiYAED1V0diejGXzeyuTsjoSfUDi8hP86dtfLX2yOHf9Z8ldzdtM9I/Y3jD6QDGocE619SX+Z5KhA0514/5dMHXiPkz4ntEDM6qzcdaET10DpE/wApq9PPozRl4aAzQ68E4eUzxP7CnDdlifDD92/hRduXLt0ovVFKkoQkJAzDcZdYkdYkRzj69x3AHrDCmDbkrU2Q8pKTt/x9g/ma8V+zQhng77OfC13lLb791cKcbIIC1F5SoIO8JyiR2RrXtWGcZDF7dxBTJVqCRz5+yq12XHlz5IS2djvTMWXHpcWSG8Uv/wCnzL5dcWTwx5RsNvbRRIdtm31R2zrFV/2geH1cdcAscUJSlb4HSlaBvsF/NJ9pqt+0/wBNhnFeFPPN5GHCttKuW85a6PgJC+M/Jxe4ehQVbtgpy9yxlme5WQ+ykYMlZ4y7T2Z7eMvbx48q5h/Q+OdqWd6ssXwxzDcSurVeUKacUgjOOR9dQFMq11T8Y+tdfg9k02rSAc8xrw/2aQdqkuNHI3qnRP6h2mkllUbp+MfWiT2EZIu+BCt6CnKZV2p+MfWg6FXan4x9aZZllGXgB/07niPzpJ2qS80S84ZT5x/MKSWVRun4x9aJNCMkXb2EHett+cfCr5GiLKp3T8Y+tbbaUFbp81X5h2GjsR0u1sRlUKtqaplXan4x9aBTSo3T8Y+tHZllF+BFF/sq8Q+RouhV2p+MfWt9ErolCU+cPzDvq7F9Lvgjq2oTtTVMq7U/GPrQFpUbp+MfWiszOL8CVUTnmN+H+zW1Mq7UfGPrW3GjkRqnzf1DtNFsL6XT2I9Cd6b0Ku1Pxj60JZVO6PjH1o7QhxfgWdqyiUyrtT8Y+tZUtCul+DHvTueI/Ohrb3p3PEfnWqi4LfLDFMY84+FXyNKG1NY88+FXyNR8DofUjE70aaBO9EN6BhoMb01PoVeJP90kb04egX4h8jQs0Q5NUaKCjTyqmNQY3py/Na8P9mkjenL81rw/2aBmmHDNUxO1LpiNqFjUGNqe96ZzxH50hNOd9M54j86BmqPBiKajUxSkb01vzh66Fj4n17wva/8AxHyGsXyHNVsAQOZWSo/wlNXX2Zn+k4V4geOr924hls+slSj7gKrHVBz7O7DSuSEKH/7P/wB1b/Y8wN+74cvMTfUU2TdwUpzk5eqOsQO3WK4+Z3lyPvx/I8bOTWKbf/0/62fReABeCYYhKEkZoHsqq41xtnCLV/EbVBccbtnHHGxrmWhBUI9cRV5iXFNizZKPUgJmDXzD5cPtJX7VtfcOYJZsWrbrZSu6YH4iTEBUwTIOu9LS6nHEtziPrcZZHHiyw+yjh4t/Jo3cuPB5+6unnXFCMuYxIEbwoqFe82/VGxmvGfsyWC8P8jvDbZBCS0tYkclOrNe0siIk6Hl3Vr1jvNL8zlaNVgh+SJiDnQaWpMqif4qQ0JSI5/zTkWpXqBvWNGvYgi1BVOWB6qXfYDbXWq0T2wKuDhzriZSlRjsomrJQSUrGbkJpi/Ip/mcnc8FYVcCFW7izPJ5QBqCvgDCnkQMNYJRPWeUpZPsJiu/FqEIOg921JU2nOodojupt12KTflnBI4QYt3srVu222fyNICBHs/upzXD7dsQUtpkiRlEGuqdZlQBOgHKkrQNAADp7arrYVXyUBw9U9cQY29laVZJZToJJ1mrRxKkKHVOWNDGgqNdrShJBMKOlZ5SsdFFenMHEoSJE699XdsCGAACSBO1V9tbha0q2510FuwMgkyfXt2UMUG2Q2miRBSAo7AinpacQzoMpiNKlsMDNrM8pFSFoQU9YR2CmUDKRRllT0mJmq97CZcVqRH8VfKQG1kjQHtoLhAWjOPaKV0vknVezOdXh3VKSkHkCez/JqL/8baJ9GBJnSuobQHPOnf3Uz7skDaDTFJlWkc0zwxbITlU0lae0Dn7Kt8N4eYtQOqsH9SXD8jVg3bkKjLPZAqxacDSAN+WtMjXImUmVyMLaCwVpVvMrnWpaLdKQIWI7hTwrQaxryrSZUf8Aj76JulSF03yLDISBCdPVSyejUAFaf1U0NrBAKT6+ysVb5kgmP83pfJSSRXXSylJVtOtctjtui8ZLTgCm1dVU9h0NdY+yVCJIEc65zE0ZUKJAECai5Gdj5+8ifleZ4RscN8n2NYMLqxwN+5sunWsKyj7y4pIncHKU+yK+pre44eurFC8OtgwSOrCpNfIePcLlzF+KsQaZDBaxUgxu4S2hZV/+mn4u6uw4L8pSMNtehuHcq20+co0rPk6NRKVXZ0NNpoz0sHFtOO3O3Pg7H7Snkub4/wDJ5fixbzYnaD7xbEDdxOsT3iU+2vFPsu377HD2ItPiErt19VQ1nMI9te88B8eo4rxZdnmDqFpUmEnlB1rxngFLeGcX8Y4MgBt+1uHwhMbgqzj+DQPIpOLitrTOxgUliyYpu9j5f49//rDF/wD/ACV/OucVzrsfKvhS8G4+xq2WZULhR95rjlc678lTZ7fDJSxRa8Ix3zG/D/ZpKtqc76Nvw/2aQqrRWTkBdBRLoDtRmWRu49M54j86Sdqdcemc8R+dIVtRIRk5Ys0Tfnnwq+Roa216Q+FXyNGI/eQpW9AqiO9ArnRmaQFF/sr8SfkaGtj0K/EP7q+wruKVvQqojvQKojPIFVbd8xvw/wBmtKrHfMa8P9miF9mLoKM7UFGZ2aVWVo71lQUw3/TueI/OtUx4Nl1cqUDmP5f+60A3Hnr+EfWqQynbNJprHnnwq+RoAG589Xwj601oN5zCleafy9x76jY6CdoFO9EN6wBufOV8I+tHDf61/CPrQMYkzVOT6BXiT8jQQ3+tXwj601Ib6FXWVGYfl9ffQs0QTsAbUSdqwBv9avh/7o0huPPX8I+tU2NUWbpznmNeH+zSwG489Xwj605QbyNypXm6dXvPfQM0QTpgUaKwBuPPV8I+tEgN/rV8I+tCxyTNpp7vpnPEfnSwG589Xwj605wN9MuVKmT+X/ugZpinQCd6agwoUADc+er4R9aaA3+tXwj60Nj4o+xsJftsX8gLCEwqLZKVHmCM4r0TyNMp4V8gWDpIAUppLzpGk58y9ue9eSeSq2+/eRVbDaioutOASNilQjn/AMq9Uwy1fPkVsg0rMpDDSQAdsqIP8zXF1j6ckq+39DxU4VJwvbqf9Sm4g4xVe2rzVv50HnXF8N+TtvE2Mfvr9hVw4bV1KUpMKkpkEHu39lVnBly5fcQP2rqsys+UgmvpXCuH7HBOGbm7cUDbKtnEvToSkoIMeoSP/VIxJxkukRqX7eOUX3OM8guJ/wCq+Tbh9xASEhjKEo2SAtQAgbbV6swQTsDXiP2aLxq34HGGJLhdw68ubV3pQAvMHlK1A8Ve1W7hKxIFdDUqps8zpX+ziW1upJVAPmiSTVvapQAM28VSWpKyD/WlWbclUZefLnWSLNkl2LZm46AQBpEEitOOIUf51pTacwJgkUwtlzYkDsmtK3E0kR3YUSSKhPtwDlB7RVmtsH1689qg3NtvryjahcXyMi0VqnShRPvB/mttHpFJSN+0g6U3oklSjmA0O+x0qvccIUhKZgan1VQxknF7hmyToM7kdUDnPdXJPC5ubjM5I7AKvm0C6vnFK3Byg1cpwhno85Ox2J3pM022kFjqCtlVhtpCUlQKiREdlXbbawiUo0POaBu4trVxKQBA5VftvWjtqDmKVTsPpR44p9xc5uLToq7VmZOo7jQ3aYAjzQKs22Elwmer3Vq7ZayJzEgjedaPp+IHufI4/Eb4st6DbWOVVNlxE6l38Zoqa2zDlXY3eAt3rSspzDs7arG+Hm22wkoI7gNqQ4zTs0xcGqJQQ24wl5JBQoBQIqMl1WcAmd/WKG2tVWSnGM5LcZkj9PI+qntoQXAVQVTsKv6twOG0xqXBAzEHnMaUeQKBBBB222oSklKYMctRTEpIUEwd96JAjZyjTX1609iee3urbbQyyqDprPKprbQCSJjT1Uai2KlJJGmmkgSR69N6B5OXbnpHOpiGYBnnUe46gMyYM6TqKJxaQlStlTdgJSOfaa53FWypBAHVKTrXVXCArTQpHMVz2JrSkrJ2jak8M0p2fOxtby/4q4otWXFFRxBtZQ/AbM27aOrzJhJEQBABB008w8qeG3/DN2tBBSiDHLSuu4d8oxwry68UWrzTV1bJumnEhavR9GiEkk77q03iaoPtFeUexxUtWdupK7lWhKNz3UzNifvL8ka/TszcHGtrZG+z1xi/b8X2qCVrSpwSkDfXavQcYw3/AE77Q2NBtHRfe7UXCk7dbIpP9Cqr7JvkzOJ4gcUvklthrrk7V2ycVsOKfK7xJj9qQqxs2zaMLJnOG0kFQPeskD1Vhf1Nrhuj0PVHrlGPaO/9j5P8uy+k8pmLq/UsH+K87VXoXluetrjyk4wWnVKQlzLISDtp21wBDc+ev4R9a9HL6meu0sWtPj/Jf0Ad8xvw/wBmkq3qQ6G8rfWV5unV7z30ohufPV8I+tRDMi3EL3oFbU1QbJ89Xwj60Cg3+tXwj60aMskwbn0zniPzpC9qkvhvplypUyfy/wDdJWG/1q+EfWiTETT6mJrbXnnwq+RoiG/1q+EfWsbDYUYUrzT+XuPfRCKdojmgVzp0N/rV8I+tAQ3Hnr+EfWjsyyTE1segX4h8jRENx56vh/7rcN9CvrKjMPy9x76IXTsjUJ3psN/rV8I+tDDf61/CPrRGZpilVjvmt+H+zRqDc+cr4R9axwNlLcqV5v6e899EBTpkdW1DTVBv9avhH1oSG489fwj60VmdxYqso4b/AFr+EfWsqCnFmPemc8RoU1t30zniPzoRvVoj5YY3prPnnwq+RpNOY84+FXyNU+B0PqRobUdLTTBtVDEENqaj0K/EPkaUmmo9CvxD5GgfBohyYmjTSxvRp3qmMQxNNV5jfh/s0lO9OV5rXh/s0DNMOGYmiTQDejTvQjUMFOe9MvxH50kbU570zniPzoO5qjwZTE6ilDamINCPifT32XcYbvMDvMMdUVdG4RlOsJWI/wD1kpr33yeXbNzYYpwm5EoKlMDmUEyI9RJB9lfHH2eeJf8AROOWrVbmRm9SWiSdArdJ94FfU2Kqu2XbHHcMBbuWjnCQND+pJ7jXK1sd4zffY8vrMTjmmvO6PKuN+Ccf4D4rbxTDrO4ubZ53K42ykqWNfOAG47a9Ra4wssX8nmJ217dO2DiGVJXZNqLalykiTrIMkGBAMazNd7YcW2XG71uh2zcZWUqUpC0RBMTB9dU3lD4I4eVhi3baxbXeZVBtxYBUDFYoT6Wr7HHyTeROE+Txj7LnFlovi7jjD2nJa/1Fb7YU4pajm3USokme3nX1JbPAxHWVtXwR5Nj/APhz9oK8wZSm21OBpq5DaswJDStZ5HRJg9pr7swxRdZSokDTcV2NfFKSkuGjzGgk3FwfKbOpsSMneNYqxbIKwf7qjtXw2CSqBtVnbuyImT3iuTFnWaLi3KUjl301lMnUz2Haq+3dOQyeex2qelzJ9TyrbFpGeSfYLo4QZ5SZqK8mcxgpO29SiiEFRUOsJkUi5fQ2lRVAn/BTHLYFFHeKJWpIkdk1BclOfRQUrsH8/wCd1XQUlwFcSf8Al/P+d9RyUJjqzpEAa1m+5oTrYoi83Z3/AFlBKVwpKuU9lcR5ZvLhZeS/hhy/dZdvrwrDdvaW6gFOrOwk7DtNdvizttm6N1QOf8pgRXk/GHk84a4txOz+9F24uG1hTeR45QTqDG2wPuNVScrfASltVnnvCPlP8vnHOLWN7a8M8P4bgq1hRbuw64sonmsKBBjmBX0/b4u/bBtNyA07lBWhCswSeYnsqn4ZwS1sS3YturQCmEyoajtpWOcN4gzfoct7xKkKBBCzqabl3V9NC4dKe0rO2suJLeQhTm+sdtcb5XvKBxDwvgL93w7w0rHH2wDkduOiT/CVE/xUazsLq1dSvpQVkSBED312/DuIIt7F0XJbd6Q/7mxE7UGJp7MPIlH5HhfBv2wHGW0W3G/Cd/wu7MKuGz09uO8kAKA74NfROC4/ZcSYc3c2z7b7ToC0OIIII3BFcV5ReFMD47woWb+RsKJEtgBR5xpVNwPwYxwZYGzw3FLh5hBCeiKh+H3CjnafxAUcclfDPQMSdbRf5G4K8mvcZ0FISgle2UyDAM8/+6LDsPZYzOAlbitVEnn7aO7c6NIAE942pUk+5aaukOkSO3mRUhlklSToddqpW7oh4BW57qt2lABPWEbUtOwpJosW2CrsVrtFTUsFIiJMVItkpCUkk8ye6mEJUrKNRt6q6EYKjmTyOyKpvKg8j2io7yUhJBMd01NcMoMHsioT0ZlBR5RrQT2Cg2ytKQUqJPtrkuLXEMWby1udG2hJWtf6QBqZrrVIgETpM14/9oPHzw55OcfuklZWLdwANedoJMd+hpEIdckjVKXRFyZ8leSvgG98o/lVxa4t8TRbWr964vVcqUhJcM+qdP8A719Jv/Z0wPB8JVc4mm3u32JebeVq4hUQSD6q477KOAs4fgasWWQ+m8ecQ0tQ5BCVhadBKVawrnrtz9f4jvDiiXmbd0AgArQdiBy9tDr53mbvg0enqSwKPndnAca8Y2HCfAjHCHBq82LXoy3D7GpYbO+v6iNB3meVR8Pwu28m3kxU++EoWtPSrkQcqdY98D212+B8KYe025dXFqyhQVmJCACO+vnP7UnlSN6+OHrNeVCIDoSdgNkn+SfXVaWHuSU2tonodLjlmksEO7ts+esdxFWLYteXi/OecUs+01WnejUdKWa63J7ylFUjbvmt+H+zSTtTXT1G/D/ZpCzpRITk5ANCd6KgNGjLJm3/AE7niPzpCqdcemc8R+dIVRIRk+pgnatt+cfCr5GhVW2/PPhV8jRiP3kKO1AraiVQqojMwFVv/YV4h8jQnet/7KvEPkaIV3FnagolbUJ2ozOwTWOeY14f7NaO1bc8xrw/2asX2Yo70Ktq3Wlb0QhmqytHasq6FWE76dzxH51qmOuJDy/w0nrHXX61rpE/tI95+tUMpW9zVNY84+FXyNCHEx6JPvP1pjLgzn8NI6p7ew99Ux0ErW4A3o01rpE/tI95+tGHE/tp95+tUw0l5MG9NT6FXiT8jQ9In9pPvP1pqXE9Co9Gnzhpr2HvoGaIJXyBRg7VoOJj0SfefrRBxP7afefrVDYpeTY0pznmteH+zQBxMeiT7z9aapwZG/w0nq9p7T30BoglT3AoxvWBxMeiT7z9aMOJj0afefrQsbFLybTTnfTOeI/OlhxP7SfefrTnXEh5f4aT1jrJ+tAaYpVyCmiQYrA4mfRp95+tGlxM+iT7z9aFj415JeGXbljet3DSilxuVJI5ECvt7yD+UK2474fyuoSq6R1XkqOgcjf1Hf1z218OsuAq9GkdVXM9h769L8hXlKb4C4nSq4ARZ3BCVqE9Ug6HelTgskXB/wCsx+oab38HVH6l/wCWfbjGGHDbvpW2FKWrSQdEirXC8Lfxi+zXJllGpChA76XgnHOCYxYW7qLhAKkzOaQrvB2rXE3HWG4NhTwtHDcv5ZyW6StR7NtB7a4ftSi+lrjseKab/M+HPtGlzhb7SSL911v7v94IQWWinpUttpCcyZmSQEk9xI0r7Q4Bv3b7hyxceUlTnRhKlJMgkaSPdPtr5+8p+F2HGvBXFeJsMnEeIrLLiDht3kpSylCFjJmg5ozFSgNDEDYGvXPJNiSrrhqzcSsrt1NtLQ4V5ipKmkEmTrvNd7U429Lj6luebjGWn1uSD70z1JkEICZgzNXeGrzNp1mO2qWzV0yQas7JcK0OkyDXAqmdhytF2wjpNN4/mpRIToYiNqhsvAJ6u5G4qSpf4cwCT30+AiW4DjilKSBIE/xUV5eVxAKgeZFPbd3JMDfSqnE75qxt7i4uFlDVukuET2a8/dTlu6Ae2466fatGAtxaUoJjUxqTpXFYz5QsPwxDeZS4UVHOQYIgxB/mvJPKv5XfvGPuYW3espbbCUqQknMXlCShJnZCTqo7Sr1jzTGsXxDF8PDzN4XUt9cILcIVMAJ/VzPuPZWyOBqrMcs93R6NxR5Ulow5b14g3jb9opCFNJUtPTgnUlMEQmSANDJk6QfG8S8uKFl66aXdJaUvKQ0iCgJEGASIUmYI2Uk6QRB9IwTgHFMQ4fbcvUoPRNfe2e5SxCMw282VmeZSNAmK4viz7MKMQ/8AKD5tnVA9IpbgSlZnMFdbRR5RzAHZWvH7MdpmKcc+TfGZg/2iHUP3CfvDTjbCVLYvMqh0hjQDsVqQJEEiNJr0nyc+V+7uVPIxa4abM9ElawesTCpnUCElOnr51wnCv2dcHZU3cY1i6VrQek6G1BKFKPaOW3aRXYYl5NuG3ktG1W9a5JGZAIjXQmO6lahRlSjHY36TDkivnLc7u58pdu02C9cIASOqlKpzneB393OuL438t7lh0YtHMoQpD62lK1Wk80jmDIOmxHrqpe8lzmMdE7bY44AHOlWhTaSrqjfuEV0dh5IcCxGwW3iNwp95KT1lp1HqjbflWGMIxdxTZ0JY8klU2kefO/aMt8Ev7m6tn3y4s9ZlRK0wY1A5GdPbXWcEeWsO2rt5eAqtnwl5t3KZ6VU5RHcIPdNQF/ZUsMUW+5ZYlqoz0ChlWpMbFR7+z+qZ/wDgXi+DouG1W7i3EIQllavRoKjAIHaAkn2JrW/ZaSqmc1xzwk7aaPcuH/KTbqZt0vuJcW4lSlKQoJgjUpgnkBO/bXcNX7V22lSFgggEajnXxtxBw9jODG5fsWDKnsqX4UsdI2qRIkboVlkfpI510HDnlie4dwBq0vElKnHR0ag6coSrXSdRCkkb809poHgU1cHYC1Dxyqao+o1T0qEqUBG4qxs3lOFInXnPrFeR8HeU6wxW8RldcWn0ZbJzQoD9Xv7IivUba4Sh9A5HWe3/ADSubODhKjqQydcUztLNzM0nU6napPSAqmRpIH+dlVlrcENDXfnvtFPQ71QoxBV7K1RkYJR3Y51yJPsmKrn3VdJmmBp7qnKhaTy32qBcrSUkDTlr/NLnIbjSK69uJblPIR2Sa+ZvtW4peYjgCcDsWXbh+6dAm2BU4FAFZypGp6qVHT9Jr6Dx2/TYWpWYJBzEztXz9xfd2eI8cMYu6yjLhDS7lBeSeu5BykjbqkKIHKSddq16GKnlV9gNUpSx+3DmWy/VnTfZk4Ms7Xya2LCVq6dbIVk6UqQyCAcqOzvjTsgV6Ng/Ab2GXjqy6txtxRknX318jcIfacOCYpdP3DSrV110qWq1SOic11UUHQE8yInnXe4v9ty2trFTFm05cLUnzgjJr65NZZ6Z5Mjk3+v/AIetfpeswJYoQ22/2z2fysY1YcEcKXFyp5tp4DMQSOWo950r82MfxR3GcXu7x5ZccecUsqJ7TXa+Ujyy415SHFm9UG7ULBSwlRjnqdda89Lqf20+8/WtcIrHHoies9N9Plo4OWV/J/yErNLVTlOJn0afefrSy4n9tPvP1pp1JJeQXfNb8P8AZpCzUl1xOVs9Gk9Xv7T30hTif2k+8/WiRnnV8ijtQK2pqnE/tp95+tAXEz6NPvP1o0ZZJeTVz6ZzxH50g71IfcT0zn4aT1jqZ+tJLif20+8/WiQmaVvcUd6xr0h8KvkaIuJj0SfefrWNuJzH8NI6p5nsPfR9hFLqW4g70B3pvSJ/bT7z9aAuJ/bT/P1okZml5FVv/ZX4h8jRFxMeiT7z9awLT0Kvw0+cNNe/vohVK+SOrehVTekT+0n3n60JcTPok+8/WiM7S8iVUTvo2/D/AGa2XEz6NHvP1rbrgyt/hpPV7+099EBSp7kehO9NLiY9En3n60PSJ/aR7z9aIztLyKVWUZcTPo0e8/Wsq0KaXk0/6dzxH51obVt70zniNCmp2I+WGmms+efCr5GkjSnM+efCr5GqfA6H1I1RDagG1EmqYxDBrTUH8BfiHyNJTTkehX4h8jQsfB7mk0Y3pY3o6EbEYmnK8xvw/wBmkJOtOWYS14f7NAzRB7MxNEmgGlGNKpjYsYNqc96ZzxH50hJpzvp3PEfnS2aYvY2NqMGlpokmqY6LJNueufCr5GsSaG3PWPhV8jWA0tmqL+KOl4d4+x7hczh2JP24/SlZj3VLxnymcScQDLe4q+4iIyhUD3VyQOtMSanU6qyLDicutxV+aPUvInxqrBceXh11mesMU/8AEfTOpSsEGvrTyN4UjCeDmMLHSTY5mAp9GVxSEqhOYQIOXLoNPXvXwbgV4uxv7a4bOVbb6FA++v0C4KdecZavFFTrVwylfSK2MgaJPMCAO7ajbc9PKL7Ozwf4o08Meow6mK3kmn/VHasyjqpHVHKptm+Qoagaa1AQQXAdh2VOtwIMga6156XJxY8Foy7AEH31K+9kETqmO2qvOUgjbvppehOUxFDYVEu7vA00pSVZQBJI7K8b8qvFNxhmF4g6h1aAmWmwkSsqUhUxOgOwBOiRmOsCvU7t4hggQpStBXzZ5dLq6vsHxDC860qcUXXnEpy/hCBln3exXfWvA05KzNmT6XR4LgWFOYnj11d3ji71Tbak9IVklxSgMxA7DCh6iSTXquE3WFM2Nki9dSlSFJCmEqCkTMrBPMxp6iY3M8DYcN4qeFrpVgHba4uUqcMiVEq1y8soJj1TrO1cVwx5KeOMSxe5usSbf+4qkINo4mS5pBJIIiNSBqe0V25v3d+pJI4+OHtNLobs+o77yz2OCq+74cpsOPaqKiClPcBy/wC65R/jxvG3vvZu1u3AmAtWg0Og7P8AqqThzgHAcKbU1iuH3V1cKW2VO3JJWEpkqSnkMxgE9gr1Xg7gzhxFmH3Lg26lnO4yGERJOgB5ACBHd2mqhihBXF2zsx65bNUjjGeK7a2aYuXHUhNwVJQFKmSBMR2xOlW9hxJhuIttoTdIbD4UQhShMZdO/WT7q6fEvJi+3fKdF0V2RSIQ2UpSSrVPWJGumg9tXHDfkcsn4fvmG3pXIDkGRtv21H1cNM6kNNjrq60UOBY3hdhctJcurdlOctpzEa9Uzr360rEeNMLsrhDZvWQhQSpTgdBAlRE6dw+Veh415NcHzNNtsspR93UVIQgQF5hl/gmqVPkowkshu1abXmczEBIgAgSR7QqheNx4CjjhlW7r9Dn2eO7HEHEt2l0w4tKC6oBwgoTOk98SatEeWG6s0Mpzl1J1CHetKRpMVb2/kuw7D7dbDuEC9WpKs2VKQoCYzJM78o7q5G+8mFozOKOWi7ZkpLPRrdPSEA6KMHRQIiAI+dX7ba3MeTFGMqtNHe2mPcM8UYYqzci3uJCuiQsZFKncHluda8D8r/D9jhF5dWiL1OcPLubTpG0gpSoDqyNDrJjTcxV5xJwLeXdk69w1aX1peKEJWFlSEKjfrctDp9K8fu/Iz5Ury6F/ieP/AHs6oLSmgZSeXtpMIxhPaaObqI2toNlTwVjT3DeJDNfG0fUoujITCVBSDmBO/mgx6wZ5/c/AOIuYnhDLq1FahKkSdUg65fZMeqK+OsR8kt86LV+6ZdRcJKUu5I2JHLvjfbtjn9S+RxLtrg4beSttwL8xwQSkAAH3CPUkUGrnHJFNcitJCWFtPjse02jxShKImddTrVlnJbhIBOv+TVQymSDrBM1YtnSSeXbXMi6Nk1e47MpLYzRM/wAVV3asoBkGNhUxy4iUk6gbHlVc+6FJSFJAGXQAVTdkiqOdxtIdbUpxIUmdiYB9tfMf2gblzAOHsUeDqUqvuitmshGraJBnWdSPdX01jr34amW4CiCCVa5RE5vZv7K+K/tP4o0u6wezYuOlSlnpFiIkq1k9vr/qK6Ok+MJy/T+J1fS8K1HqOKL4jv8Aw/8ATwdRpSjRqNLJmiR9dkwv9hXiHyNIUabP4K/EPkaQo0SM83wCTQHaiUaAnWjMsmbePUa8P9mkHenPHqN+H+zSCdKJCJvcEmgJolbUCqYZpMK49M54j86QqnXJ/Gc8R+dIO9WhM3uwVVtvzj4VfI0J3rbR658KvkaMRfyQo7UCqJVAdTRIzM0qtz+AvxD5GhO9b/2VeIfI0Yu9xVATRHahVRGdg1t3zW/D/ZrR2rbnmNeH+zVi72YpVarDvWjtRCGDWVlZRCmw3vTOeI0IMGmOvOB1YC1ABR50PTufuL+I0Ibq2ZTWPOPhV8jQh9yPSK+I0xh9wrMrUeqefcap8DoVaFpoxvWdO5+4r4jRdO5+4r4jVbjFXkwb05PoV+IfI0HTufuK+I01LzhZUc6pzDn66B2OhVgUQMisS+5+4r4jRJfc/cV8RqmNVeTE7U9ZlDXh/s0sPuT6RXxGnKecCW+urVPb3mgd2aI1uADIoxtWkvuT6RXxGjD7k+kV8Rqtxsa8mJNPeP46/EfnSg+5PpFfEae4+4HVgLUBmOk0G9mmNVyADRg1iX3P3FfEaJL7n7iviNDuOjXkbbnrnwq+RrEmtsPuFRlaj1Tz7jWxcOfuL+I0G9mlVSNg6UYNaD7n7iviNGH3J9Ir4jQ7j4uPkc2qGlEadZP919g/Zs4iXxBgFoF3BU9ZhVu62pWik7p058/cK+PkPudErrqnMNZ9derfZ34xewTjBNkp5QbvE5BKjAX+X+fnRY3u4vvscj1zSrVaJ1zHdfofdKFoyCeqO+ntPEqBE6jbsqmYxBF3atupGi0ztGtTrJzqyduXqrh5IdLaZ83xTtIuEuFSJHnfOjS7pB1B7RyqAXSlBjmKch4rABnNWdGlUOuSMhKdecf1XmnG/DTeNXQJEqgoWdwQTJkczt7q9GdclmN4EyKrHLNLjgUUyI1mji6ZTSaOJw/hBhuyS0plKglIBETNX1rgDFujqNJCcw0AroGLVtKk6AVLctkAJSnQEaxyrR1OwK2ooHOE2LqFllsqEkZkg1VYvwk26lTlu22yoCChOm1doy24w0lMlwa6Ryrj+K7i4w1CkZy0lahCFKOZRk7d1aVKUeGBCU4u0UZ/1RQ6NxATboP4eukxE+4D3VdW3ETlrbG3L8FCQIWd5JmvO8c4oxLB3Clu0euC6tSUJSCAmdpzRHPfsrzTjryhYxg6y7csllxbkBvLGYzrqnfT3SK1weSbrqDl6h0R3gfRTPEBeS7D5nQE8hO3s0p+F4s9ZrCnFK3jfQxEezevk624p4ixBx+5becWgIaKmc/VSlUEiBsJ1nlpXTf/AIhcS4Q22xlWgpSAG3hoI2JXsQf1Ax6qa4ZEtpbio+qbu4bH1Qm5VjCkoWlZbVGmYp7SSY31NX2G8OWanEu3X/k67EyJr5+8nfHOPYwyfvTL6GlukthQEtrBhaD3QZFe6cLuXHQNpdCs2wVzKeYNZp5Mi+MmVLN7m8VsX1zhaCytptCQ0T5oGndVOvhhpa0y0kpSSZIrqEuQ3kUvMffRBoFO+o5Vle+4tSfc8zx7g63vFgQULScwVpE1fYJgjbRRCR5ySY5ACI901d39oOkCinqka1JsEoScw/nl3UqV9xye2xYNMgNIlUxpJ9VPKsuXWIHIUkujMBOnOtuH8NROp7RQ2LoQ6UElQGZUASSaiXLiYVqc3d3U4qyNKI0jYEVUXrhQlRTO8dsCgb3HRicV5SHknBru2fdLTTqAkrnTLJUv1aJj2zX5++UXHDj/ABdiN30xeQp1WQk8p0Ar62+0jxqcF4ZvGkqUHnkm2SAYgkSr+AmviZdy4ST0i5P/ACNdaFwxRh+p7r8OaVRjPVS77L9BSjQE0wvufuK+I0JuHP3FfEatWevk15Bn8BfiHyNIJ51I6dzoVddU5hz9dJL7n7iviNEhE2qW4omgJ0ppfcn0iviNAX3J9Ir4jRqzLJx8gveY14f7NJJk0919zK2c6tU9veaSX3I9Ir4jRITOhZMmgJk00vuR6RXxGgL7kekV8Ro1ZllXkG4P4zniPzpJ0FPfecDywFqAzHY0pT7n7iviNEhU6t7ijpW2j1z4VfI0Sn3P3FfEaxt5wqIK1Hqq59xonYja1uRydKA6U1T7k+kV8RoVPufuK+I0aszuhVbGrK/EPkaIvuR6RXxGsDznQqOdU5hz7jRCtrEK3oFb03p3P3FfEaEvuT6RXxGiVmd15FKrbuiG/D/ZrZfcn0iviNbdfcCW+urzdde81YG1MRQk603p3P3F/EaDp3P3FfEaLcQ68gVlGX3I9Ir3msq9xWxp30zniNDWOn8dzxH51lWR/Uzaaaz558KvkaSNKcz558KvkapjYfUjVENqBO1EDBoRiYwbU1HoV+IfI0lNNT6FXiT8jQMdDkwb0VBRAyKg1MZTlnqNH/j/AGajpNOV5jfh/s0tmiL2ZujpY2okmqGRYwGac6fxnPEfnSEmmvH8dzxH50L5NMXsEDFGDSwdKIGhY2LJDHnnwq+RrEmhYPWPhV8jWJNAzUn8UNSaMGlUYNCxsWSEH8FXiH91PwDElYTjFneIMKZdSuR3Gq5J/BV4h/dYkxQmh1KNM/RTgfGGcdwC2ukrlt1IUnKqdCCQPeCPZXWW6QltIB2r5Y+zV5QH7jD3sFWQp+1BetwoxnAGqJ9W1fRGFY797Zt3W8qw8kqCgZGXSD6jWfV4r/aR4Z8j1OB6LUywS/T8jpmlHYiRPtpzA6LXc6ioTNxnSkHU7+ujN0U6q5D3VxWqG2TSuYOwO3fWgSEqPPvqILsFQE6RAprV2Fpyxm12q0UNYUvpYOnIZu+pzLRzp3IJ5D2xUNACkA/zFTEJUEJOubkaamC0Tm207EgaSJ5d1UmI26HEFcAOA6kjSIO3vPuqyYKlrg9vI1l1ZLdkjQDUaba/9VrUlQmtzz/E8IZvWng62gOSCtayITAA7/8AD315ljXk/s8avlMLbDNuklarkKIznYJGuvYE7SSa93xDCUvt5EnNMjIdCrmYnflXM4/wjbX1qpoOfd3OsnQxBKSEk+0/zVdUl9IxRhXyR5Xw35OMFw69FwiGEPAI/wDIOdC0gEDxDTT31d2XkxYcvrdxN0lKUNLaCJzdIlRkAg9gj3a1YXPDCbBdw2HVrbbITk0VkISkpIG4AI/iut4UWcTsBlSNEJc7ITmgGNhIk+qO2reSb7g+3CrodgfBtrZ3zV1b27TZbRkJSNSDpEj/ADSu5w9kMIzJgFIqoZSsEtrUtJ3OVQMawB/Bq0sGM7gbJKiNQeygtsjiiWySXJynIec1ZNI6RJI3jX10kKypCI0mNtfXWJuC2AlOubb11a25Fy+wVw0X4AISDNY0OhBT3UcBKRBExHtpaliN49Y2oZbki+xIJAkTr20py502OU0K3EpbmfaKhOvpLc5gTrSmn2CVdxrzxUCSdKocaxNuwacfdMNpmAN1HQR/Ipr2LpWwrKon8pKdcp7Sa8m8pPF1yeGMRuGEwi1adV0hGilAZer6ideYIp+DF1yTlwMjc5rHHlnzL9oXjdPEXFq7G2eDlpaBYOUyC4ZKj768dJmpDr6rm8ddWSVLzkk+o1FJroSfVJs+wafBHS6eGGHCMJoFGsJoFGrRJMKfwV+IfI0kmmT+CvxD5Gkk0SEzeyNE0JOlbJmgUaMytm3fNb8P9mkkyaY6eo34f7NKJiiQqb3BJk0CjRExS1GjMzYT/pnPEfnSqZcn8ZzxH50omiXAqb3YJ1rbR658KvkaE7Vtrzj4VfI1YhP5IVQEzRE6UJ0piM7YJ3rf+wrxD5GhrYMsr8Q+Rq2LvcWaA7UatqWo0SM7NVt3VLfh/s1o7VtzzGvD/ZogOzFqoa2TJrVWIZpVZQqNZRoXYx1pXTLMp84/mFbDSo3T8Y+tLf8ATOeI/OtJNDvQbatjuhV2p+MfWmsNKCjqnzVfmHYaj0xjzz4VfI0LsbBq0EGlA7o+MfWj6FXan4x9aTRAyKjDTXgclpXan4x9acGldCoSnzh+Yd9RAaen0KvEP7pbHxasMNK7U/GPrWw0oc0/GPrSRvRVNxiaHhpQ5p+MfWmqbOVvVPm/qHaajAzTVeY34f7NC0aItUxgaVO6fjH1og0rtT8Y+tJBoxrQjE0ODSu1Pxj6011oqdWZT5x3UKipNOeP47niPzoDRFqhqWldqPjH1og0rtT8Y+tRwdaYDIqtxqaJLLRCiZT5p/MOw1gaV2p+MfWlsHrnwq+RrQNBW5pTXSiSltRG6fjH1og0oc0/GPrUdJg0wGaHcanElJbIaUJT5w/MO+sDSu1Pxj60pB/BV4h8jWgaCjSpKkdXwDxIrhLiO1vyErbQoZk5gQRzBHMV9b4JxXYFCb6zW2zh182t5lSnAEoc2DY5DLrpz0jY18QA19Q+Q9DPFPk3bsXrdLq7N9ZazCQVlOk+zNTYyXQ4y4PIfiTSRy4VqYL5x2/Q9ta4xaSWCMoS8JSkqGYHmP8AurdnFvvsZSJyyRNeC4yzj/C145eYopn7ml1oNkEj8OQVADYECdJ1gxroZjHHcraUUOtMLygpdOXMM+QAydp5cyeysU9IpfKDtHgIatw+ORUz1xHFCLu7uLYZg02kAKSYzKOseqPnV3g9yHVKClkJGgAECvLUcWW94l24tA3060ErJVkShWYhPWg9bKBsDyrpcI4maDibe4KWltQYbUSkE6AE81b6eus0sLrZGiOZXuenMqzADNIG1Sw9ECNZ5Vy+E49bXDZyuCCohJ/V2x2+urS2xu1cWpzpEhoJUCobEDcfOs3Q06ZpU4tWdGpSWUIMiF7k/wCf5pScVxhFrbKcEEIEA9/aa8+xzjy3sbgtl4mFkDPpKjoAP5J7I1rz93yntXVypDj4SwrrJWoEAkgkKg+IR3RWqMG0Kckj1K84qaafdfRBWhIW0knSCTJPKP6NV2OcXtDDn3EqgIh1eY9ZQ0CgBtO/srxLGPKCpvF1ZrpoNKZLZDjgSMpynMO3QE155xB5WXhcOMJdKWFB3ME7LTMgnt5e0U+GCc+BU9RDGtz3G64zaxO/bSpSmnlp64SrfPqduwR7pq5wPygW+CXDanHCtT7CAQggjpM2TX2pAHi7q+OnvKJcYa+rIp0tgQhRVtIyzPrWY7qv8F8oZ4kWyyyRZBpaEuOIUSUNlZ1PqBmR2CtT0ckYlroS2PufB8WYuUFXT5lglaSBEpGnPfmfbXVYO9mQHFqTlUDlEbqj118n8C8dPYulqyDy7VTCfxFOKKVNgFfm67FGUGddI0r1vh/j/wC7vYdblwLQhnJnCo2Gk9iuoqR6+6sbxOL3Nqzda2PcHXukQVdgEEGoyAC8Z0y9lcrY8UpU8lvpUrayZ1KIiBJEeuQoR3A86sHOILdm8bbzjrgqMnUQJPu+lId2NTVF8u5Q2mXSlKSYMkCKh4hdJZUo5ojlXnvFvlLtsFet1LzLs3l5FLQjMUCYJjZQHMbj3A16ePS7jT7CSl9gIQMhgAhQJSpKtiIB9kd1Gsbe4p5Vwj0R7E2mFD8QZyQnU6knurm+IOJE2TvQ5S9lST+GCVCDEx2ajavLcZ8qLTTyWrnNZBCXEKYcUCoLbSpasqtpATyO0d9cw/imKcfcW/6VgjqnLlvOL+4Vclv7m2oQJTlKVL80hPaJMCmw0ztuWyEy1K2Ud2ep3ePO4i4m2tE9IV9ZSG1wpATGbu2UNP7rmfL7etYH5Or5DCEkFgMlWiZKiBJ+Gu64M4KTwthdtZmbp9DSW1Xa15luEblWg3OteY/asurex4DubdS/xXFtgA8/ONTHNSyqMeFf9Dtem4b1GNz3ba/qfFyEHOoynUK/MOw0ktK7U/GPrWNGFnwq+RpRNOS3Pr0pLpCLShzT8Y+tAWldqfjH1oFKoSaMzOSG9GeiUJT5w/MO+lFpXan4x9ayYYX4h8jSqJITOSpBlpQG6fjH1pRaV2p+MfWhUZNCTRpMztoa40SlvVOif1DtNJLSjzT8Y+tbdPUaH/H+zSjpRJCptWEppXan4x9aWWldqfjH1oVHWhUaNWZm4jXmlF5wynzjuoUotKPNPxj61u4P4zniPzpVWhU2rYRaV2p+MfWsbaUFnVPmq/MOw0omsbPWPhV8jRCU11I0WlHmn4x9aFTSu1Pxj60NBR7mdtBlpUbp+MfWthpXQqEp84fmHfSlUQ9CrxD+6m4u1YKmldqfjH1oOhV2o+MfWhUaEmKPcQ2gi0o80/GPrW3WlZG9U+b+odppVbd81vw/2aIC1TNdCrtT8Y+tYWldqfjH1oKFRq9zO2jZaVO6PjH1rKXWUe4FxDe9M54j86FNbdP47niPzoRvVdinyxgMimM+efCr5GlA601nzz4VfI0L4GQfyRlYDrWgdK3UGJhU9syyrxD5GkAzTUH8FXiHyNAx8HuboqAGaJJoQ0wgacswlrw/2aRTlmUNeH+zVM0QezNpNEk0pJpgoQ0w6c96ZzxH50kGaY8Yfc8R+dC+TRF7GwZo0mlAxRg1TGpkhnzz4VfI1oGaxg9Y+FXyNCDFAaE9kMBmjSqKUDRgzQjUySn0KvEPkaEGa02r8FXiHyNaoTReyGg19MfZNxMu219YFMpQ+h2ezQj+6+ZAZr3P7LGLuW3E1/aJGjrIXPhUDVVs19mc31SPXpJrxT/mfWuMYa3fWzzLls1dNvJKFJegpyncHTbuFeCca8Bu4IxeW2AOPkBIDVv0YU2lQVJKVGVakQe3XaK+lbZgPtwIM6GfnS3MDbzOKKUp/NmA51ycOplhlaPnWbTxzRqR8P8A/wA3vuGLtmyxzDncIQwkLS0gjrrU5qidj1BGbaVGotv5Y2cWxJm7UpltTb4Q2gLKkIWoEqSEp88hKQAOZMnc19UeUXyP2PE1u48/ZC7VkIyqRmJJ2KTyV6jrseRHxV5RPI/ieA4tdPMOItU2rarthx1zIBmcUFZcggzkjfsGu1ej02fBqV8lUjy+q0+o0z+D6onrlj5b7hq8tFEOpZeU6lJuVhEIQgAEgTuSpUersFXnD/l9S5aOJeKUpaBfCkk5nNTlbSOSlyAOzTma+LLzGsbw9a7e+Uptu3PpVg6pMpO2smQPZrS73je4S2tKFdGdAFE7nQjTsmNfVWx+nwkYI+pThyfYXGvlEfx95bFp1bdm3dW26nQqUuWoA3gHOB25Z5iuEu+O1XtpdKa/GWh5Abb2mCEp9gAn/wCteM4V5RLi5Fq4XS2GEpYgkypSSVCR2dY+01OxnjRSnHFWbfQuOHYDMCZKtjtJUs+0CqWjUKVDHr3JOVnacT8boukJYYUAsIAUM2ySsKJB79TXCO8RP4qFBWYKdDalAHVKyYVHtTPsrkLvGQpZcCpQlpC15CYyghP0HuoRiDOHuJXnHSpSUKCpImCrkddTEd1boaeMNqOfl1csm9l1f8Ru/c2rRlUdGno2lK1U4QkgrV2DOrQdgqfwXxA/hqlIZuFoD9sW8ze+YgJ0PLWNew1xrmIIK2B5uZpHSJI1kqOc6dsx6qsMDxJqwBcdIVkSHpUeqpWpI+SfbFPljVUkZI5X1W2e8W/FzGD2rK7Z55KnGiVHXrhRhSfh19ciuy4H8qr7rKWeiU462+ypKlqCQVKG0xIzZo15EGK+aP8A5an7w+lSs7SE9VQXBdlOae4CdhtoNzUzhfjBWBYzZ3T7y3mUudIlCHcvSlJKGlkkGdSe85Z7652TRprjc62LXuLW+x932PlDV/pVqpDrc3Ci4vMuR0acyilPNRMkzHL1Txl55elNPYhhL1wXlCVMXDDozAT1VgnmMyQe7X9QHzxe+VC6wsvosbharkNp+6pbOdLeVQUopGukAA8oCu2uAvuM3LnFbp62ZV94WtLy7fOMqm1ohYQdwQSDGuhPfWbFobb6jTm9QSS6eT6mHlgdd4Us8QeuSplLyzcJzCAsJAUCORKEyO3qxtWrPyrmwVZYai6+83irZblsGoSlwmehQTzSEq01/LNfPPDGDY5xq/Z2mFW5DAc6IrcJCVLJJAPKU7wNhJmvsXyS/Zxt+HrJq5dcau7srzJceUVpSkCMoGUaEyRBETsY1HUvBpV8t34D0i1GreypeSk8n3AmN8bY8F4ihL+CJaStxl0SlbgWdVIGsjQHlrzGlfTvBPA1lwlhgtbNhDaFKkhExPaSdSe8ye+pPCnCbWGoU63bMWqlgDqJA6o7wNdZNde1a9EggAA6ak6mvOZ9RPM74Xg9Pg00MKpbvyVnQBtBGhOxUBse6vlv7Y4P+iWrk6KuMoHqT/3X1PiSjmISOrEAdhr46+155R+EMG4iw/hLiV/ELK5ct04g3eWzSXWkhaigJUmQoejJkTvRaKDyZWo80dfS6jHpM0MuZ1FPk+Z2jCj4VfI0lSq6+04Qw7iNCnOFOILLiAhClG2bJbuIg/7awFH2A1yV1bO2Tymn21NOpMFKhBFdGWOUHUkfRsOrw6mClhkmhRMUJMVhNDvVJFyYY9CvxD5GkqVTCYYX4h8jSCaJIVJ7I0TFCTFYTQkzRGeTDc8xrw/2aUo0x09Rvw/2aQo0SFTe5omKGsJmhJozO2E/6dzxH50tRpj+jzniPzpJq1wKm92aUaxoys+FXyNCo1towo+FXyNEKT3QtRoaytE0RnbNHWtkwwrxD+6GsJllfiHyNWLT3FVpRrZMUNGhLZlbd81vw/2aEmBW3PMa8P8AZqxd7MA6UtVEo0B3q0JZlZWiayiFjHg30y5UoHMfy/8AdYA3+tXwj60D/pnPEfnQpNVQbkrew8BuPPX8I+tNaDeYwpXmn8vce+oyaax558KvkaFoZBrqWwYDY/Or4R9aKG/1q+EfWk0QM1A1JeBoDY/Or4R9aaA30KusqMw/L6++o1NQfwF+IfI0LQ+ElfAxPR/rV8I+tEA3+tXwj61HSaYDNC0GpLwOAbP5lfCPrTFhsJb6yvN/T3nvqODTHPMb8P8AZoWh8ZKnsHDf61/CPrTE9GfzK+EfWo4NEDBqmhikvBIAbH51fCPrTXQ30q5UoHMdk/8AdRgZprp/Gc8R+dDQ+MlXAYDf61fCPrRAN/rX8I+tIogZoaGxkvBLY6PMYUrzT+XuPfWANn8yvhH1pTB658KvkawGhrcepKlsPAbH51/CPrRANj86vhH1pAM0QMVTQ1SXglJ6PoldZUZh+X199bSW/wBavhH1pKTDK/EPka0DQUP6lS2JSEIUoBKlknYBH/de2+RBmz8nvEmH3mP3osX8YiysLIpl59bhyJVlnqokiVGB6zpXn/C9va8M8M3vFmIsJuCyrobC3cHVdeicyhzSkant0HOvGbDyhX+NeV3h7GL65W+8jFrV0qWrUw8n3COQ25VvwaZzi5s8Z6/63HSwengt3sz9dMNUpk6kdsVe2ik3CYKRlPIaVzeGuypSVCSFKH810tmjIjq7Krxc9pHMXBKXh+dpaW4gpIISYJ5fL/3XmnG/k3t8ZsX272xdWQCW1s5QQFedqZ0MCQZE8pr1JglCjOk86fcNofbhSQokaFQmmQm07QmcE9mj83PKL9n9GHYpeLUbvO4oFtRTnaCDu2RAEQRG3mkcxXheNeSJ95q6TaJW5cs5ytB3CRH5eUQZn5V+sfFXDCL+zeSWwUrTClI0UOY130OorwnHvIBaP4xd3Von7mzfAi46J1aFqBBzayRKp1Mfl7TI9Bp/VHDabOBqvSY5PljR+ctzhNzhdupKm3EP264XKTmQANFGdwdI7qrLrGH3HAl5R6MgAKQDlOgGb/8ARH819v4r9nPCnC+hWGuM4ip3oWrlSx0KkxoSNcxAE5SPUezzjFPstu4a43b2zzzxClJ6ZxhLjYTlI1TIIPW0iRJnSCK7mP1PBLk87k9I1EN4nzRYPuoaFw4cyVDownnO4+ft1mq64vlk50IDaFgplRnKeR+dfQGKeRdzD1ytm4tm7aG31rSjKHCkpSADE9bdQJgETBNcpfeSN5x0NNNJUhJQkZT5yY6x/mZitMdZie7Zll6fmXCPLLO5BZbTkJITMkmVGTP9ad1OfvHG71CpUQAElKE7oO+neY9tews+Q24w1S2UW6ruS0EkTLcq1GYAb7Axzk112A/Z6tOJMTeRcNLQEFSCplHWbB0SMuw7p2gnWgfqGFW72GL0rUNpVufOLNvcXd6yssgoVJWEggJR+aSNhXR2mEY1xA0RYWDl1fuKSFtoSTlby9UgcgIPcABX2Jwj5D7d26Vh4wlNu2FMqU82gqyjQ5EncTl9qSO8VaM/Z0xPBRlwUMN2pccl5Si2qFOaLKQk5zk6uUZQREESRWZ+p4mqWxrXo+WPyluvsfIvDHkx4i4lZXd2lqEIbeQ25cvXXRKcKgQGxPVGbKdVdmpFfRfk7+zdaOWLWLKZW0oguIN0Mquj/Lma11PYTzEV6/hH2fbXAL1gOXy79JUVLt0NBttABJSVpSSFATqCYkkxFeycO8KpsB15eOYKQhYMnnOg7Z3339fJ1fqUpLpxs6+i9KhB9WRWeeeT3yJYLwzesJw20SlSSQA6npFKKhqrX/lJ0FfQVhh9tbpTkQhU7AaBMaR3+uo+H4aGESsQRBOUARz/AOquGClKxkAEabf5pXAlOWR3J2ekUIwXTBUiW20ENjs322PZROuJQgnQ6E6+ulOLUQQjUnlFKeDgbJ5xsNteVA5FqJV4ouEKI1UNa/K3/wDiB4qrEftA5FGRbYTatQeU51//AL1fqliCQhBJ2PbX5MfbvKj9ofFVHzV2VoUjsHRx/Rrteiq9S/yf9ji+tutJ+q/ueL4JjtzhV4xcWry2XW1BSSlREEcx2GvqbhniG38tfDS03YCeK7NrO2+lIm9QkSoK7VgazzAPMa/HzThQoEcq9e8j3EFzhON2r1svo3G1pdQsflO4P/Veuz4lNdLOd6D6jk0+ZdLOtdaS04pCytKkmCCj/ulnox+dXwj613vlbwJpq9tcdsWw3YYojpcidm3Pzo9h/givOya8zKDhJxZ9yxZ45sayJcjvw+iV1lRmH5fX30ohs/nX8I+tYDLK/EPkaUTVJBykqWwZ6M/nV8I+tCQ2PzK+EfWhoCaKjPKS8Dnejyt9ZXm/p7z30ghv9a/hH1rbx6jfh/s0kmiSFzkr4DIbH51fCPrQw3+tXwj60G9aJiiSM7kvA1/oy6uVKBzH8v8A3SldGB5yvh/7rb5h5zxH50hRk1aQuclb2DIbP51/CPrWNhvOYUrzVfl7j30omK2z558KvkaOthSkrWxkN/rV8I+tCQ2fzq+EfWhUaEmKujO5LwEro/1q+H/usAb6FXWVGYfl9ffSlGtzDC/EPkaKhakvBohv9avhH1rUN/rV8I+tBWiYFHQlyXgIhv8AWr4R9a24G8rcqVGX9Pee+lVt3zW/D/ZqhfUqexhDf61/CPrQQ3+tXwj60KqEmjSFNrwEQ2fzr+EfWspdZRULteA3vTOeI0FG8Zec8R+dBU7FN7sMHnTmfPPhV8jUcGnsecfCr5GhfAyD+SNAzWwYoQYoqoJMOjSYZV4h8jSkmmj0C/EPkapj4Pc1Rg0sGiSaENMbTVmUN+H+zSAaas9Vrw/2aEfF7M1RgzQVsGKoNMYkxTnvTL8R+dR6e6r8ZzxH50D5Hp7GAzWwYoQYot6jGJjmfPPhV8jWkqrTBhZ8Kvka0DQGhP4oaDFFvS0qowYqg0xyTDK/EPkadh9qu+vWbdsFS3VhIA5zSEmWVeIfI13/AJGMIafx9/FrpOa0wplVyqdioeaPaqKkY9cqQWbKsWNzfZFV9oTEBhGH2vD1oQLfDGQw4E/meVBcV74T/wDWvmKwvzbY3a3Q3afQ4J7lA/1XtHlQvl4qu7uFqK1OOKcUTuSTNeFK6rqhtE16fFFJdJ8J9dySlmUmz9s8AxBvEWW7lJB6QBYIPbrXZWTqVBM6dkb1495IcTRiXBuD3AM9JZsq15EoTXq+HO9WvmE9pNM97HeKaOgYIc2Gb+DRqbMgiQnaaiMLCJ01qUhwnMQJgQT9amwO5GvEQlYHv5HSubvLMOEgpAk7DmK6pSE6nzTOtQLqxS8ZQCkk6a6UNBqjhbrCULQ4FpSQoiRHL/3VZd4G0pMqVqnWCkR3axrXaYhbKtdFomDIVVFcoCl9SUnu213HqqOVFqKZwWOcFt4g280u2aet35DjREgzpInnGlc0jySMBDyehZQ0oEIUGikwSSc3tPL+Nq9bUjoxMzEjTWa0XgURGhGmoEireeSVJhLDFu6OCw7ye2jAGZPSKUBm6xGo21rpeHfJ3b2ii42hKHyc6nG15T3Adw/quitEFwCUZp9XZV1h6ljQzl5wAf6pcZuT3YyUYpbFezwwyy2QyhPSCAguAEnf83cVKgHtqxtsAAUkuSWkjqNwCAR2nb/DvyvbRTakgFQGu3YfUKmZGkuZswUoaJjQfzWqK25MMuSpt8MDZcDbSG2lqzRkgq7SZ7+X8U8WyGRlQglPPv7Nef8AmlTlTm3JPrrTLeZYlMgEb1TdlpJC0NuOhtI6qBuBU5phKFCUGVSRr7YqWloNpEJzHkBtSl5iogdVJ105+2qTojdm9SIMHTSB76VdLA3EdwqWlEDkKr7lQlUa89fnQthRoq8ZRNssjWRO9flB9vXK55cQ6jVKsNZTPeFLFfqhxHfm3sXlZohJr8pPtjPf6n5QlXG6228uvZmP1rr+iyrV39jj+uQvQv8ANHz2DBmvUvJkCzdWywYPRJJn1qry1KS4oJSCVEwBXsfBFiph1IMAoZaTptOWf7r3eXseT9Fg5ZnLwfQvD6meLuH3eG7lQDj8rs1K/I+BIT6lCR6wmvIL+zdw+8dtnklDrSilSTuCK6/Brn7vcJVnylGVQUNCCOY95q38o+GtcU4U3xRYpBuEwziTaB5rnJyOxQE+sEVx9Xhte4j696bquh+1Lh/1PM5/BX4h8jS6MaMr8Q+RpRM1ykelk9kYTNApVbUqKWTNGkIbDc8xvw/2aUTNG6eo14f7NLq0Lm9zCYod6wmaFRijM7YVyfxnPEaTTH9X3PEfnSSZq1wBN7swmaJrzj4VfI0FbaPXPhV8jVik/kgKEmtk0CjRIQ2aOtbmWV+IfI0BNEPQL8Q+RogL3AoSZrZNDRCGzCYrbnmNeH+zQEzRO6Ib8P8AZqAXsxROtAda2o1qjEsysrCYrKICxjriQ8v8NJ6x11+ta6RP7afefrQPemc8RrSTVJbBOTtjOkT+0j3n605hxJUfw0jqnt7D31GpjPnnwq+RoWhkJO0N6RP7SPefrWw4n9tPvP1pKTW6FoJSY7pE/tp95+tNS4ktKPRp84aa9/fUcGaYkwyvxD5GhaHwk7C6RP7SfefrRB1P7aPefrSqwGKjQakyQHE/tJ95+tNU4Mjf4afN7+099RUmnLMJa8P9mgaHRk9ww6n9tPvP1oukT+0n3n60mtg1Gg1Njg6n9tHvP1prriQ8v8NJ6x1k/WotNeP4zniPzoaHqew0OpP+2n3n60QdSP8AbT7z9ajpNMBmhoNTZJZcSVH8NPmnt7D30IdSP9tPvP1oGD1z4VfI1qhaNCm+lDukT+2j3n60aXk/tp95+tRwYogaqg1NkxCwW1Q2mcwEa9/fXsCbdvgfyX/d1oCcSxWHnEiZS3qEA+vVXsHbXDeTDhscR48g3HUw+0IuLpyNEtpBJrpPKNi/+rxcLT0fSLUvohshOyU+xIA9lb9HiuTm+xxvVNQ+lYo/m/7HkHEwS/b3BkklBMT3V45i7H3XEn24gAyB6xP917XiVuLhpSTIzJI+deV8aWCmrq3uIJDjSASe3KK62N1Oj5h6zicsKmlwfpL9l7iFGKeTjAylYKkWzaFCeYSAflX0dhSwQBm20ivz/wDseccC1w1rDnHeqkwEk193YDdofYaVmEkbivnOuxPHnkvues0ORZdPF/Y6xBGQiSR2VIbUQnQamq5t3SORjnUthRUOwdtZE9jVJEjMSSdB3GtLUnSNJ7RWl9WMu/ZSFZioZp1HvqwUbeQh9MLBVMET21W3+BWb0KaUptQEwnb3fSrFwEAEA+oGoD7hzkKRrEyBrVt+URJ9mc/d8P3TbkIlSYkkGo3+lvISoLToORG9dY251QCToRCTWlyZGU9s1nkl2NEZNcnPWNi4ESlOvcmrW2t1KBACo2IKasbdzIPNk6aGpDLhBPVAEbmiigJNsjtW7rMGVL23+lTrVDq1SpASJGu0H31IZUVawQNNY2qQCExG47BE1oihLb4GsWjZSdxNEtsICQJyyTAFRws9JJ1E6AmaIPyopElXb6qa6oTTscgpECAIEVrQER/NGlWgAUIiZNRXlhCgQRM86XwGlZOC8qdYiqm/ukNhRUqD2CmP4ilhGvrnsrjOIuIEW7biyoGJn1UDl2GRhTOV8p3FqMMw15RUAIOgr8vvLnjH+ucU3T6jIkifbX2L5eOPgm0eaSuCQRA32r4a4yUq9unFgZlrVp3zXofScXTLrZwvWMilj9tHLcO4b94xDpSD0bf8q5V7Bw0zkuro5R6XKJ0gJAT/AFXI8P4ai0Ns3BKi4nMfbJrsOGXOlYLw85alLI9ZJ/uvWOTk7Mvp2mWCKj3e509q6UuqnYzr2Vf8GY8jB8SWLhs3FjcoLF0xPntk6/8A2BgjvHfXLKdy5tCDOndShcKStMKhUzUatUzvKXS1RY8d8MHhTF3mEpQ9ZulLts+mcrragSlQ17K5dTqR/tp95+tetYW5bcecMHhy5gYmyC7hrpO51KmvbqR3yOYryO6t3LS4cZdSUOIJSUnka4WbD7cq7HstLq/fxq+VyCXUn/aT7z9aEup/bT7z9aAmtUqjS5sc44nI3+Gnze09p76UXU/tp95+tbdPUb8P9mlExVpC5zdhl1I/20+8/Wll1J/2ke8/WhUaAmKJIQ5Mc+4kPLHRpPWOsn60vpE/tJ95+tY/6dzxH50smKtICcnbCLqf20+8/WttuJzH8NI6p5nsPfSq20ZWfCr5GiaFKTtGukT+0n3n60JdT+0j3n60KjSyZokhDkw+kT+0n3n60QcT0Sj0afOGmvf30qtz+CvxD5GraA6nZnSJP+0n3n60JcSP9tPvP1odqHeroS5MPpE/tI95+tY64kJb/DSer2ntPfSyYrTvmt+H+zV0ApbM10if2ke8/Ws6RP7afefrQVomjSFOTCLif20+8/WspdZV0LcmG8fxnPEfnQVt4w+54j861UXALe7DBmjZ88+FXyNKBims+efCr5Go+BsH8kCk0wGaVRpNCEmGDFNHoF+IfI0mmoP4KvEPkaBjYPc0DRUFEDNWGmEDT1mUNeH+zUemqV1GvD/ZoWPi9mbBiioK2DVBJjAZpj/pnPEfnSdqa96ZzxH50LW4+L2NAzRg0qjSZOm9UGmSGDKz4VfI0IMVecM8FY1xPcZMOw95/qmVBJyjQ7mutZ8mOEYHK+JOIbdlxvVdnYfju+rTqg+s1cccpvZAz1OLEvlI86bbU6oJQkqUeQFddgnkux3F2PvK2E4fYje6vVhlsf8A2VAq1HlAwrh95DPDeCM2qScovsQSHnye0A9VPuPrquxHFrvi7Fc1/eXF0hkgqU8srJM6JA2E90QJrZDSN/UzlZPVe2JHb3f+ncCcIWuE4ZeN31xiSw5d3jIISUpOiEkgSmdSdjp2VyPErpdskEmJga94ml4rfrv75llaswaGVAI79f5pePS5aIMk9Y10YwWOPSjnSnLJcpOzmAiXUjfUb89a47iDAlYtw4A0nM8y2VIA55FqSR7hXbhIKFEaq39lVtskWzrjRGiXXR6gSFj/APXNLba3Rz82GOVdEuGmv40c/wCRXipfD+LMqSsp17a/RbyS+UNGM4dby6CUiDrqK/NXG8NHD+OIfYlLFwStIiAlU6gfP219CeRLyhqsXGkKc0IAIJrgep6dZV7iOd6bllpJvT5Ox+hthfJeQCk5qvbNYBSZnurxvgjixN60glcgjadRXqeHXyHGkjzhtpXkulpnq3uti+K5PKCKjvEBeYbTrB1oWXQkgg7bzRxnmPlRChcEnXUTrIrHLQrbkdbn20xQ6MiJj1bUxbhyaap7ByqueSFU5bqM6HTsFPt2oAkmToARW1LhYUNv0g862bwtbwjQxpQNIO2SQgbBYHfNbCY/PmEeuoDl/JgE6/wKl2t6HEctB+aqtLYjsnNDqxJEd1NCgTOpO5kzVcm6KoAggHYCeVORcFXMpGxk++mqVCmrJCpUDrlnXStJUAs7ZpPOlLOUSF6A7b1E6bIoQI0mBV2WolkpzKgcjG4qE/eBCTqdN6A4gEpIkTG41qjxrGEtNqJ5Dt1oXIOMdxWN4slpokOZedeOcf8AGQt7dwJUdjBmrviziXo2lnPO+k14Dxxjqrkrg6EnSaPDDre4WWShE8p8p+MuYo851yrnXjLlr0l6pax1W9h/yr1HiVsqUtRmDvXAXQShWhMcynnXsdFGlseYnD3cnVLsItVKt3pygZG3HNe0J0rouH0KYskJOgAAjviuedaLdvcKKh6FKdB+pwA/xXT4KgLtioJIgzqeVdjsbcC+df7/ALsTFKnUR6jSnAS7qCCNzTkJJXEQOaorS4TqQI5VadG1xvclWV4u0u2X21qbcaUFoWFQUkEQR3123EHCaPKdboxrBVNIxhQAvLBRCC4vYrbneeYGoJ7IrzoqIOug7qt8LxFLdqtpSc6Zko/UNiPdr6wKGeOOVUw8OeeGfVEosY4bxPALhTN/ZPWrg3DiCKrCa9DsvKFjXDry8FxB1vG7FIC2G8Sb6VK2ztBJzJPLQjUGmPO8CcR+ms77hy6Vuu3i4YB9RhQHvrny0sl9O52MfqcJbZFTPOXTCGvD/ZpJNejXfkfusQbS5w/iVljqAmejt3Mru5/21Qr+K4fFsAxHBHlNX1m9bODQhxBFZXCUfqRvWfHkfxZXk0O9Ya1tUI2G+fxnPEfnSqN/0zniPzpZNWuAJvdmiaJowo+FXyNBW21dc+FXyNWKT+SFKNarK0TFGJbMJitj0C/EPkaCin8FXiHyNRgJ7iyZrVZQqNEhLZpRrbnmNeH+zQHWjc8xvw/2aIG9mBQkzWE1qiEtmExWUJM1lQCxzzzgeWAtQGY86FL7n7iveaF4/jOeI/OhqkgnN29x3TufuL+I0xl5ZUQVqPVPPuNRwZpjPnnwq+RqNIZCT6luF07n7i/iNbFw5+4v4jSgZrdU0Epy8j03Dn7iveaaHnOhUc6pzDn66igzTkmWF+IfI0DQ2M3fIYuHP3FfEa307n7iviNJ2ogZqUGpy8jg+5+4r3mjW84Et9dWqe3vNRwYprnmN+H+zQ0h0ZunuGm4c/cV8Rounc/cV8RqOJnSuh4a4Ixviq5DOHWDz55qywlI7SeVTp8FvJ0q2yoFw5+4r4jUxi1vb+7LVqh55ZWQEok867hrgzhnhVcY/iisTvkn/wDkMLhQB7FOnqj2Se6rK+46ubJhtnA7a34etFmSLMZrlY7VOnX4ctPjp5S3exln6gopqG5V2fksvrNtD/EWJM8PsKEpRcrJeWP+LaZUfdXSMf8Aw/g23S+mzucUuN0OYirIFHtDSTMeIj1VwuM8RNqvX7hlZuLgCCsqJIXA1UszJ15SfVXM3eK3OJKLbjykpj8m/vOtbIafHHlHLzeoZXt1fwO14z8qGMYx0TYvTbYasEi0YV0LSY5FIgHlvNcQ5jKfv8G5CmyJ6sk6b8tagFsNNqQjRShqtep99Qr51Fu1kSczh3JNaUkuDiZMs/qbLa/xH7ywu5aQVZFANz1QD2RzrqsFbfYU0XXNWklxzLoMx+m3srh+GEKXdgQSygFxaNxpt/MV2bb5TbjXN0isxge7+/fVj9O+v5sscLl65euVaZZieVScTeKMOaznVQJj21ET/wCLZpSDCnFSdeVPxswhlKwUpSlKZ9lUzqLaO5UJPWBOsgbVAu0TiLyRr1kOR60FJ/lsVZ/hqaToJzQDI/yarn21MYkpRAUlVsrKd+shSVgfDm91JYqVJL8yr4hwwYxhbjSRlebOdon9Q+u3tqFwBiy7a5blRTB91X5hzUkEdpqgxCy/03FE3DYCW7jrwNgrn796y5V1QaOZrcL6lqI9uT658mPGKg00FODWOdfRvCHESbpCZUFZvy18GeT/AIhW1kBVzGhNfTPAHFfSdFmWREDfavIanD0vY6ulz9caZ9L218laACqdqs7Z1JhQgDnFefYLi5cQCFZx3V1NhfgqSFaDnp7q5m6N7OicSTH5pPqrCyMnLXekpcJSFAgjfStm4CQSFaHXcVTYC32IlwkoJAI9UVDe22EkawamvqLgBI56wQPfUIkZ45zQ2GhKFQCDrRJchWVKonsrTiSiMo1rbKgVSSdDtVJ7h/clMEhMToe0U1hwoWIAI5QKiqXlUNYHOKW7dgJManaTUbKqyc7cwoyJzab6CodxcoROo0EVCfuiuesBB7dRVLf4olqZVmVruaPsRR3J1/iyWpAMTt2VyOPY6EpUSo69p1pWK4kp2e6QCRXI4m+pZUVqKjvqapRT5D/I5zijFS6Vyrfsry7H0LcUpRGUb16BjELKj7D/AO64/FGukkCPbXRxbGPKmzyfi5abewcJ0Uo5R2/5FebOS47lnqmu08pl30eJJtkqkNpk68z/ANRXEs9VYzDMmdINew0cOnEn5OXJVsNeSXLdaSZKnWE7bDMT/VdFg6g02URuO2qN1koQhWUR07Zif+KzrV3hQ6VAVMie2a3jcH1blkYCY/NzE0p7LASOr39tMGxESBseYqOlcvFJEnlPzqjdIQ8SqR2HYVjDymnEqEq5RT7i2/DKk689KipH6iYNGtjM7sZj1qcaw9C2lReWhzMgnVxB85P9jvHfVbhjqr5ZYDiXAmAFhUgmKs1JW3kUk+aZEb1FxTDm12dxetKLLpKVZ0HKpK+0HvqMzuPy6kYu5XZEdG6pKk7KCo17RXR4R5Yces0Czvnk4zYxAt8ST0wA7lHrD2EVwWI4kp5tqSlIQBK0JOsnmBt8qa0pt9MpWHVpRmOXT/uq6U+Qfe+VQfB6Wtzgvi0pSV3PC98rXMCX7ZR9nWT7j66rMY8lePWVuq8w9aMasOVzYO9IB6wNR6jXG2alXSSpo5gDJEV0eCYniOFOpetbpyzeGzjTpSr+DNZ56eD4VHRw6/NHbqtHOXybm0uHG3A40oKIyqkRrUbp3P3F/Ea9cPGzGOsdBxThTOKJOgu2gGrgd+ZIhX/2B9dV135KbDiBlT/CmKounIn/AE67hp/1J1hfsJPdWSWCUeNzpx1yn9Wx5kq4c/cX8RrGnnCsytXmq59xqTi2BYhglyti+tHbZ1JgpcSRUNrzj4VfI0mqRqjNtqmZ07n7iviNCX3P3FfEaAmtVdCXOXkM3Dg/3FfEa2HnOhUc6pzDn66STNEDDC/EPkalAKbvkxVw5+4r3mgVcOfuL+I0JNBR0hTnLyH07n7i/iNE48sJb66pKe3vNKJituapb8P9mrpA9bp7mdO5+4v4jWlPufuK95oCYoaukJc5eQ+nc/cX8RrKWTFZV0B1y8hPGH3PEfnWqN5pReWZTqo/mFCGlDmn4x9am1EadvY0DFOZ88+FXyNB0Ku1Pxj60xltSVnVPmn8w7DVbDIJ2thYMUVb6FXan4x9awNKHNHxj61LQSUvBgMU1OjK/EPkaDoldqfjH1pqGldCoSmcw/MO/voWNinfAAM1sGKuuH+CMa4nfDWG2LlyTuURA9Zru7LyY4Dw+30vEWMt3FwjVVhhykrUO5S5yj2Se6ijBy+kXLLHHyeZ2djcX7yWrZlbzijAShMk16Hg/kTxe5t2LjFnWcEtSmf/AClfiESfNQOsfdVs95Q7XBmFMcM2FvhIAgvMdd4+t1Ua+GK4nFOMcXvlup6R1KXBlK1rLij2kk9vtrVHTXvIxz13Tstv9/gds0rg7g9a0YfYKxy8QNbvETlZSe5AOvtUPVVXi3lWxK9bWw5ep+6hOlpZNhpnukJABjvk15viNy5bIDhWp1at1rMx6hsKWXFXDSCFbannJrVGEY8I5k9RKb+5Ou8YW68oISVFZkKWrb3fWhexJ6/SUuvkJSMgQjqgiecb+2q9xRAOXQk691LbJJUaKjMptvctW2wlsNpICE9m3fW0sSJ2J0OkVGZfAHbPZT0PToOXZQmlUxDyClQImdfdVHfJJWZOtdKpAdB0J7RO9VOI23VUQgZhyokzNnhatE3hhss4e+6ZCnl5RryH/Z/iust2MxTm80QIPKqzDMONu1aMSPw0BSu3NEn+TVzaJKnkaEISZg1Ddp4dEFFkxduq4xJlgTCSBlArn/KdxpbcKuIababu7txQUW1HRGmpPfXUYc4UO3d+8AG2gVyox7PkPbXzhxfiysa4ivLpRnMvLMzMaT7aKMbe5i9V1stLgrH9UmXFv5VceZezLdaebz5i2poAd405V23D/Gdlxi9bW6k/c74OSWxJSpJSpKoj/ion2bV4xU/AcWcwLGLW/a1UwsKjtHMe6mygmjyel9Uz4ppZJXF83ue6MWqmLJtDiFJXlB15yKQ/Zff2FsL0J8w7wobGpynkXAauLdZ+6XSBcNJjYKEkewn5VoSgyASoyNtq50o9j6KumcKfBD4aul2j4SZSoGCk8jXvXAWOEKblXdFeHfdP/ILyRBPna13PB2ILYdQJIB7dq4GrhTZzcUHhn0M+ueF8bCmEAq10Jg16PhOJBTYlQUdInWvn7gzFVOZAT2bGvXsDuQCmFEJPfXnMipneg7R6AxcKUEkKIke+n9M9uk5td6qLN9QQAmYHZqDVim4SUwdNRSWrQzgYu4UAQQn1A70CnIknTu7KIHQajtG/yoj1uqMoNDQJHNwk7gnt0rHX0pTIjQ7xTlWnPXukUroM5AiUg7GpRaBadStEZR9aUpClkhQGWN41qUm2yEyJ7qVcHoZJ07ooS91wVd2ehTqSQDXNYm5JMDYVeYldBYUZKu2RXM3q9SdfWTtVJjUn3KW8cJJJI1MamKo8RbUoHWJn1VePJGfTf1VCubeUq1kDmRTE6Lo4i+aJzaeyK5PGUptErddOVtCSpSuwASf4r0HEbcBR7u6vKvLHiSMK4TuUpKUu3SwyCN4Oqv4Ee2uhp08k4wXcy5NkfPnEeJLxfEbi6OgdWVR3cqr27fMuZInXq05VupxRWvMADGaNDoD/AHUi1cSlaEhIzmUgqE17yK6VSOM95bi1JD1qhBnMbkgdphGs/EPfV9hrXRNQJga/xp/Nch5QeJzwmbGxslD/AFOVXFwpQGVCVgAIIHM5Qe7Ttqgwvyx4rbLbF6yxfNhYUrMmFEU5Y21aMMvU9NpsrxZXuu/Y9XSNetoVHnzpTbYF1MHTWKosE8omC46UpLqsPuSZ6N/VB07e331erZWs9MnrIIPWa66PeNqFprk62PPjzx6sck0MdXqEggRqNKjpQjpBPVAOop/RLU6QlIXIGrZzDWklRCvNJG0moMbGpQCZHvoVsFIWFgKbc6pR2z/mlYIB7CeQOlMbQXcwUCpPOOXqNWLo88xu3cwjEHm3iS26nqrjcToadgty2lRDqQ6jSAT1k94PKup4lwtOMYS5DY6a3SVAg8h53199eeMtu2jshRIHOr5OLljLT5U1ujpM9xbOLabcVkKgRmAUFDtmrWzfWyCp1BcCwSC2Zg9kH61T4dfhwZTt3irlhuW4TAA62n9VTN2Hd2iRYXy1LKQ6jMTAQrQz6jrVlaY22Hyy43K9pbMR31Q9CJ64zAKnLvSwXG3syLhbYGgzgLA7tdf5qjR1SietYbxwVp+44uWsZsgkDoMRQCtPgcHWHvjuqLiXkwwPiRZd4cvvuN2tJjD71QgmNkObH2wa83VizmZsOBCjBPSIME+wz86uMOxNLiUZXlNduYxr69qCcIz5Q7Hm6ZfF0UOP8L4pwzdqtsSs3bV1PJaSAfVVQTNexYXx3dOWybLEm2sVsEiPu96nMI/4q3T7KG78nPDfGKSvAL//AEjEDvYX6hkJ7Eube+KySwtfSbY6i/qPHq2DLK/EPkau+JeCcZ4Uu1MYlZqt1DZSiMpHaDzqm6JQZUJTOYfmHf31ne2xpj8t0IJrVH0Su1Pxj61otK7U/GPrRqhbT8CyZo3PMa8P9ms6FXan4x9a262opbEp0T+odpqA06ewgmayj6FXan4x9a0WldqfjH1qxLUvAsmayi6FXaj4x9ayitAVLwY8Zec8R+dBW3j+MvxH51reogW92EDTGfPPhV8jSadbgrcgCSUq0HqNCxkH8kCDRoQpxQSlJUo7AV2/DPklxHFrZF/ib7OB4UdfvV6rLmH/ABTur2CupYxfhzglhX/x/DW8Ru06DFcTTmTPahvb3z7KbHHKYp5orZbnLcN+SXGMatBfXRawnDZj71eqyJPckbqPcAa6u3wvgzgm2WpIXxRisjIlxJbt0HXUjzjvsctc3jHF+I48tT2JYg7dqOgR5qQOwAcu7burnFXsr5BI2A0HurVHDFc7mSeeT7ncY15V8XfsTYMIRYWmks26A236siTr/wDYk1xzt07c6rcKjMyeXqG1RkKTcdUmTvrSlKLMkieym8cGe2+eDLq9+7dUak6kmoTS1XLkqMiaF1fSzO55GgsHg0/CzANX2M7fySfBNvrTNb6An2VV2KlMryqJFdGpHTM6ERvvVVe2KkdYaKqkMy43anE28AUyN9oqGgQNSPVTGldIhQBOYcqalgE+aI7zUAq3YLQAjnT2FdYjtma2ECQmdJiZ1NOQ0M0kwB2cqg5Jrge2nMJrEWX3q8t2wBqse4amnMpChEQak2LeW4UuSSlBjTt0+tRDenqpMlMgqceVoNkkg7mZP9VY2yxISrmACKiWSR0fMlSioSI5x/VTEqZs2Hrx+Cy2ZMmAQNh7flNWaI0tyg8q/E54e4bZsLbq3V36Q80Dl9fhrwWr3jPiR7ifHbm7WtSmlLJQknSNpjvj5VRCtEVSPnfqWr/5edyX0rZf79zKytwSJrQBJijOUeyeRzEXcbwTEcLdOc2CPvDawSVNtzCjHNAJ1PIGeVdo397wK6buWlZXWljQ68tUntBBIPaDXhnBHEWL8EcQ2WOYJeu4filqvMy+0YIkEEHtSQSCDoQSK9J4d48CyLXEQA0ogtvZPRf8T3fwe6seSFu0e69L1qeJYM/bZP8AydDcPsffXnLRtdvaFZLTK15yhP6c0ax2kV1XDCkuLgCHERmHKDsa59yzacaztwpB1DiD1Vd3/VA5f3mFqXc2JCLgJKQlwZkK5gH+B261y9Rh9yNLk9LLHcb5PoDg+6U3cNp312Fe48O3SXEtgkaRNfIXk/8AK/aXVwy1ibP+mPHQuA5mie87p9vvr6Z4SxhD4ZUhxK21iUqSZB9RrymqwzxP5Kh+CSaPXbF/qJIV7TuKsQ4AgECZOormrG6SEJ7Yirhl6UJBOmmnZXNexqXJZh7qmDpEdv8ANbZeVmFLbTLUzrypcLSDEme0UO4SSZYJeKkkbCjZSDHdUBt5SUmREbimN3RAOkTsaoqn2JjpJE791QbxzqHYmI1oy+sgkJM8qrr1xSgQT6x2VRaW5V3apKgTvzNUN6M8gT64q4uTMiTtppVa+0DJMernVDyjcahWulKcSAkgyFd29TXk5liNxoRXI8Q+Ufhvh2/Njf4xb290lUKQcysh/wCRAISfXT4Y5ZHUE2LclHlmsQZUVEA6zAmvmXyvYuriPi1diwsC1sD0Uzpn/OqfZHsrrPKH5enr6/cw7hS6YaakIViailRJJ16MHQDQ9Y9nLevKE3VkypbtzcfeFFZWrozAMk7q589p516n0/RZMb93Iq8HPyZcc9rKlxtxa+ht2lqSVlWdzSTEaCdKHG7u34FwQYrc5Hb9w5La1mJXE5lDeBufYOc1CxryjtYPZj/TWENvwU5ikwPUZkn3V5Pj2J3mL3Rub15TzyhoVbJHYByFeljDyeb1vqEMEHHFvLz2RAxHELjFb5+7unC9cPLK1rVzJqPW41o1tFEVs2R4F9UrkxdXWAcXYtw4+HLG8W3yykyk+yqgNmQIoktkKiKptDMbyY5dUG0/sen2HliVddCMTsErWlXp7c5VAequwsuJsKxgAW9+2CshIbuRlXHrrwdCMqoqU6/kZyg6mKQ4o9Lg9V1EF+1+X58n0I9hpQM+VSASN9URP6hWOyhMd4kiIryzAeJsVw22bLF64AIBSpWYEe2u2wnjFi5AVetptiTGdoSJnSU7Utxo9Lh1mPN9mXDhBemNCNe0xpp7DXA31l/p2Iu2itW0qyoJ7N0/wRXolxah5hD9sQ63I66DIPb6jrtXL8UWBF824qIcREp1hST9CKpMvU4/jZSs2hFwFjqk7iuhYcCWQYkEb1AtGlPIQuCFjzu89tS3wLdkicsidaj3Kwx6N0Rbm7yFXJVVtxieVBEjXSKiYtfkEgazzqlQ65cPpB1GwmiSMGbUVKkX1sF3T6ZJKRpFXzLxtkpCYAO8c6i4Jh8NJKwJO1Wd2OiSOW9U32N2GDUepkhNwtppKmFhBAnIoSgj1cvZFNYxeFoddSpkmesjrJn5iq2zckxqo8qlrSUhRIEH8lUaFfKO6wrj+8RbJtLhDOM4Uoa290OkQO3Kd0n1EUOJeTvh7jC2W9w5df6ZiBIKsOvFjKTr5jm3sMVwhItyHm19GtI85JgnXSrKxxlxCEryBwgRLfVUDO8bH+KCUFLkaslO+GczxBwxinDF2q2xKzdtXU/rTAPqqor3Oz40/wBRwdVjiFuzjdm2mVW1ySlbY55FRmQde9PdVBi3kmt8etVX3CjrrrgGZeFXQAuEDtTGix3p9oFZ5YmuBqy//X8Tyomic8xrw/2aZe2Nxh76mbllbLqTBSsQRS3TCG/D/ZpDGp7MWTFDWb1lEJbMJisoSZrKsCwnj+M54j86EGKkt2S727U2wh11wqICUInWfXXo2CeSVrCrRGK8V3KsNtNFN2UD7w/2AJnQd5/narScuCTai3bOQ4T4MxLjG++72LXVSCpx5w5W20jdSlHQDvr0rDMI4c8n7o+6hvijHYguOCLS3Mb66qI93rrMR4mcucMTYYdbIwfBjoi0Y0W6RsVq3Pbr7AmuUvr8NMlhkAH82XQeqtccSXJncpPd7Im8ScUP43eqevHvvrwEAr0QnuSnYAcv6qhxC6efQQ6CByNRHiZBk69tTsNeQ/Dbhn16xTrFpKfxKN24KTBkR31tJzoJ0nbU1Y4xg6kEkSU6nNFVCF9Euew1XJncZQlUiWygpWDBqU7qjXQ91IZVqmNvlUlREjTvnsqhyWxQ37am3ZGkHXvpTag64gK3NXF+xnQpXaN6oHgWHJ5jY0SdmHInjdnRWS4GWduR51IeSFgymRFVmH3IXAB1iDU7pCUjcDlFCzfBpxKx63LT4UkabxTWV9fvnt0qZkKtSJmlP2mVYUjSal2K6OndANtGZHIzTM0LI1k/xWmVhCdQJmiQklKlbdtRhpXwSmj1jBmdN+VWVuS0w+ogySAkga6Sf7FV1qnMTJg8yTXS2uHFxlnNGVADjilHKkTrBPqioPgm+DdnZQ+rOUoZaSBmPVHVEqPcO+vK/KfxqvErlWGWaymzaJCyNCs9h/zu7a6fjzid1q2Vb4etSGlekdiCs9o7uwe3sjx26OZRNMitzz3q2rcYvDj/AF/wRiZrEgqMCtoQVmBVrh2GKWsFSdO+nt0eRx4pZHsbw3ClXKNU0i/w1yxdzZTkrucGw4JCRliNTTsYwhNy0sZOVK6tzv8A/XdWG1ycphYRcNgpjN31dW7WYCdxXLKZdwq5OWck10OH4mh5KTICo11qMmnkr6Z7M63AuJnsKaSw4M7CdjEx3Ecx2cxy7K6t3FbHFbRsofTbBUKUFqGiUncHmeUbydq88QoKBk6d3OilTas7Rg7ac6VKCZ6HFqZ449PKL9TCjfvKCQhSFFKklcaztXYcCeULiHgi4Dlk+ttmZctngVsr9aeXrEGvPW8YvXW3SoMrUQStwohR7+yT21mF2l++ApbzjQMwAqDSJ4lNOM1aNEM+66E9z7h8mPl7wvi0tWdyTYYoYAt1qlK+9CufqOvrr27DcSS8gEGUnsr81rUuWhaMrzo6yXJIVPaD219J+R7y7rvRb4Ri7v8A5w6rb6z6aOR/5/OvLa703217mLjx4Oxiy2vkfWDd8onLoRGk1ID/AEkCSdTEGuPwnGU3jaCFSCPXXQW9yowQNewV55prY1rfgtFZlIBkpn2gGmI80azyIjWo6H86IylR7qYwekAmRHqigYSQbiso2E7zNVd04VEyR6xzqe8nIg6k8gIqsu4KVGTPMUNBJFbcuFK5JkCdedVtw7EgSZ9tTrjUK0mIOprivKJxnZ8A4DcYnfgqSkZWmQYU65+VI/s8gCabjhKclFLdlydKyDx9xfa8I4Fc3r9wlh4oULZJIzOOx1UpG51g18SYoVX2KpvX3XVvyYXnI60yTodyauMd44xbjriNzFL54qbbJyoT5qByQgckj+dzVBeXjbAKioCNdTsRXutBpP8Aiwd/UzlZckcit8FbdoSvElPFtBDYKVuZQCud0zudqpccxcNIU2gBIAIkVOxPEyhqRKQZygdnMmuMxB8uypREgbGuwkcDV5ljTUO5BtUrxTFIXKkpkxyqFi6ZunOwGNK6Ph+yyW7r6hqR7qobpBevVpHaRRp7nncuN+0m+ZMh2Nkbi6bQBKSdamXtrmuVBIkA5RFXfD2GdZxwp0SmaNGHS6J8XvqORePSfs/zKM4f0brUjfQ09zDMqtBV5dWCUhkxJmNKsBYhxtMJknsqmzXDR22qOKdtiFmB7aUu1WpSQfaa664wsDYTyNKtMFLz05SUkxUsTLRybpCbJJbZSmCatLf8RK50M6a1LOElAGkCKI2K2AFZdgDQto6uPDKHKLfCMWusPbKrZZhIgIVqhfcocwfeOVXeM3Fpi+FsXLJ6J4uhCmFTmScpkjtG1cshakpypBB7tasbXMqFAHqxHaKA6uOTrp7MmMtBvYacqr8ae6JGkkAakdlWLjuROggRNczjV1nzD/DVLkLLLogc5euqdeIG9WOBYap53MQCO+q9DRccJ7TNddw5bGEqUk6/zTXsjiafH7mW2dBZ2vQMjUCBzqpxa8ABGm8Cr97qMQDrEjvrjsVUC7kJO8zSluz0GV+3CiVhtwel1iDpV4pWZAVlMHQ91c7h6RMH1Ga6NsEtJA987UTF4ntRAUlazljqyRUxsFhsGcsTFPTboQFErAiq3EbpSZCYkGBVWPcFBdTJIvkOlIUcykmQqYI9R5Vc4dxBeWrTK0HOW1RmScrg7Dyn+D31yli0p2VqkSe2ru3SG2jrJ5zUFwcuUd2/juFccshniC2VdpAyjEGEgXTB/wCe3SD1wrvNcbxX5HsUwy1F/hSk43hIGlza9Yp1Oik7pPrFY04qVONktupEp6MwY5j3cjpVzw9xpe4S/dMturYWpEpdYWUAiNCQNtd4kd1LlBSGJ1xt/T/w8ldZWwsocQpChuFCKUTX0Td4fhnlKbYsr60YTij3UavrcJbXnI0CwISoE6cjrzrwPFcNOEYhcWj4cbdZWUKSpEHT21nlFxDTbdPkgkxWVshs/nX8I+tZQl0e+P27HkqvH8HwoNu4ywopvr3KCULHnJCjOUJ2kdYkGCANeSxvFV4piyy6tby1Jla1qJPLQT28+dJxvE3OnSFddx9ZfeWfzazB7ydTVY48pVwt1Q1VrNdFJRVIyJX+fcfc363HQScqUzl5CqtwqdEKBmalOKHRmB5w1BqIpBShKyOqaq7I4tPcEoUWZie6oyFrt1yn3CrO3Wl1JAMkjmKXeWgiRsaG7KcO6LKzvU3trlXCjlM61z+L2C2HVQNO2mWTy7W6CZOWd9q6K4YRcW4XlEEbb61OBle9DflHGsuKzhInUVPZeygTryNZcWBS6SkQZochRGpAqGdJxDeRmTrrG3aKqLq3lShqeVWfS7aSOzsrHWMxzQO2KidA5F1oqLUm1dSogwdKuGnZbBEHTeoD7JLWqfdyoba5KFBCjAPM1YvG+l9PYsErEkRNGlZ03INBBTrMg1tC5TofZUNNVyY+zKSUj3VGaWtK1ASDVuw0p1GvqmKS5bjptUgAcx66llOHDRuzXnPWG2gq64gxdWKGI6O2zSltBgxGk99UqiExAyneRTekyqjziefs3qhqbScTmOJx06VaSAK4FeHOvOkBJia9UvMOTcqB5HTWoysEQymQkTTE6OBqtE887fBxGG4GQoFQroLayS2kaAHerY2BbAOQJEnTsrarPKQRp2QKuwsekWJbIO0AQkQPVUko6VOgEEzrSG21IMJTMzyqUycqTOvOP89VCzqRW1HO4vgyVpXlGh7q5NVmu1Wcs6cq9NXbC4TBSCY51zeKYWW1EhGmxq0zmarSKXziU1niC24SrQVb292hwxzFUvQqQtQy/wAUXRq0Ugme6rMeOc4bPc6lt0tqDjRyqHaKusOxNF4vo3IbejbYK05Vwdpiq0kIcEQZk1ctvJfTmQesNjOooaOng1Cb+P8AA7NRIIVB5QTW2VqYWlaFFCkwpJBggg6R31S2ONHMG7k5f0uDYnvq5QoGCNUnTq7UtrsdeE1NWj6Q8ivlpTfBnDMUcy4iNEOE6Pgc/F3c96+kcFxJF4ylQUSFCZr830Ou2zzb7C1NutrzIcQYKSIgj3V9OeRby1t4xbosb5aW8QbAC07BY/Un+xyrynqGh6P2mNbd/sbsWWvjI+p7Z6ZAIk7CnFYEnmdJFUOE4mi8YQpJJBqxLuoKvaew15xqjbF2SStSwQQZ3g7xVW+lSXFayOw1ZAyPNST2A0h5GYEnSNz/AHVJB2UOKXbVhbu3Fw50Fu0grW4owlIAkk90TXw/5aPKa75ReJQi2WpNiyVN2bBSeq3zWR+pW/cIFesfaj8rQaWvg/DnSswF4gto6knVDA9eilewdtfNLzoskuOLcBu16rWNmx2D6+uvW+l6Toj701u+Dn58nU+hcdxd1ft4ZbloKGYjrRv6qorpZuXElwkJT1lDnHIe+tIBfc6R07Scp5CqXEsXSpbyWyNI19VejSOLnzxUbfArGcQCnTG0R7aolEvpVzJmK2pTl0vSSE71dYLho+9W4IkJ6xJ9f1pvCOA+rUzLRVqLDCEJIhRGvurk7K2Llz0mXUqNdhjiitBSDIGpNV2E4dlZZKh1lDN6taFM25sPXljCPCLLDbUMYWVHRawTQMsCSYg6RNWr1uUNpSkdSN6xi1grgEEa69vKhvc6SwpJJdiudtCUqUPy84qTagBsEgdXTSpymiGldWk2VuQqDIEbmpYahUkRH7cqICdAak2NmlkAyQd5qcq0HSZjGg0mnsoSkiNCOY7Kq7GxxpO2LWA7lPsNIuU9QIyiIqwebSkAgzIBkDWoLwS3BJ1Jqg5pEJGYu5SNtqt2GxkjSDpqdNqjNJBAgSR2iprRAQNMw98VGVjjW5Ful5kHII01BrnMRbzAk9vuror0SNBAP0qhvgVLgCJFRCdRutystrf8QACQa7LCGy00FHUDaPlVJhdjnclQMTIJGldZbNpbZjVMEQD6qKTK0mKn1MG5eOU7giuLxNybwiuvvElCT2nsricQ0uM0c6qI7Wukixw9RUsD+a6W3cnnHfXK4c+CpIAk8jXSIKkt6aHQxVsXp990Df3XRgjNuI2qqbKrt0pk6Gn3IU+6U61Z4bhwSrMoTGtCth9PJOuw21teia0Ok71uI6tPeX0beUA9u1LQpK5JHsqGhxS2Rq1WponLvtFMYWlVylKgRHP5j1VpWVCtBqBB7KRboUt7OBOUz66uxTVUXOF4ouwuGVlax0LqVLyjVaQYk+zWRrpVp5VeGhxbhKuKLITfW0M4kyPOJGgd9Suff6xVC0pTZcKtN9SY1rp+GOJF2mIP3HRpfZzFh5o+a+yoeae/zh60+qhaUlRTi3xz2PDtqyu18qXBjfCuLt3FiovYRfo6e1dI/KfynvBkHvFZWVqtilK1Y/HzkdYWPNyxPfQttdJ+bsA91TcTR9+scgOrZ0P87++qvD7iVwTGtbgfpl+YdwhSN1AAaEmnJt0v20bk6yazF2VNsuOJSYGum1HhziQwDIOxiqDX1OLKZJNq8UKkzIBq2acS615s6bVHxK1LiswEDczzobJ2GjOhqnuAl0OiHiCMhCk6gdlWmDXvTNFs7mo120lYSQZkbVDtP/EuQQBBIG9WDG4SvyW90yHFlR151AdZCttuwVdrhbW3fpUFxOqoAgbRQjpQKd1jIQZJjX1VtR01MVMW2VLgzHfQLtiQDHtHdUsQ4UQlJGTt1moD7JLyikT/AHVupmQJI5mJpDtqVN6KHtq0xEo7AWalPNBKpKu+jVDQE6kj20ltCmXNSDHOnXSC6kESO2oFFtrfkbb3WUxBHP21L6XpQIAMCdtapELLajmOhPMVMtrnKdFctRU5DTrZklKZUet66YRCVSZjbWgWOoo/m3miacKz2QIqhlDM3V7IM+2hC0rXB/8AdZBKiCk+zsrSspAiRrRWVQa20uDUHtka0hQAAG6e/epPSRBJ7oNLW0Ve+KhKQtDRUjX6USmsp7huKklASnKoad1YW9Np09vr+VSydIhtqOyOcb0L1kl8SUyCKlIEaaEb60Z/C09hH/qpZainycxe4EAFECeyKpzYFtaeX8V3LwCwSRA95qvds0FURMHarTMeXTqTtHIPWAXKvlUAOvWDoUDKOfZXYvYWUz1eqRMdlQV4SFohUjtmiTMGTTSv47MjWeIN3KYJEcqurLGjhwCXUdIzmEHmnvrlbzC3bNeZsx3CmWeJhf8A49z1ZgZiPZUaKx55Y30z2Z6ILlNw2ChCtNNBzqGnFLjCL5F3auli4ZVnQ4N9P82qjwC9cw5xxlzroBgCdh3VY4ypK2EvNQps9lKlG9mdVZVkx9XDR9beQfy5M8T2qba5WGbtqEvNqVoDyUO1J/6r6Qs71F41nbUCnuMjavykwXiS94VxhrEcPcyPNbp5LTzSe4193/Z78stnxrgzPXHSAZFNqPWSrmDXkdfofZfXBfE16TV9b6JPc9/ZlSDvOuhrgPLZ5TmPJdwXc4lnQb178CxYOvSvEaac0p84+ztrtnMVtbKzfvH30W9qwguOvLMJbSkSVE9ggmvg/wAtnlUX5UeLXsWUkt4exLOG2qx5jQOq1D9azqfYOVZNDpf+Rk3+lc/4Ojkm0tjgcQu3rq4XeXTyn799SnFqWZgq1JJ5kzv/ANVzeJ3hQgJT5zioA7e2p1xdDKZIKicxVVY7cpDxJIAQiTrzP/oV7mKrY42aW1Jldi959ytlpSqXAgFap5kwB865u0YU9ZOPKmVr37hqam44lS15E/7r2aOUDQVNYsVM4a0gjQI19Zpi2OFPqzZGnwkV9oyEkiIFdLgVnl6V9XLT61XWmHqhJKe4TzrqG7QWliEkQY3nnVNnQ0uGvlRUXw6ZZQBmkxppVlb2PQpZITAG1LtmhLZUBMHWdatIASmdDuBVGyELfUwMv4JEDU6g1tiUqV1cw0ERWCQYHuimNDKo6zIjbehs0uNiF5VLIGk0FsAbkHtOg7aeWxKlRqP5pYISQQCTMiKsBqiUsECeZ5GDpQKPWBkgju/iiU4no06bgClIlR025e+hGdg1deAmYE6kVEe6+g320qwySkCYPaDUcoSCfVUAaF2zZSSDCv8AN6mlOUCNAOXbSUJyp00VHIc6PP1CToOfKoMWyoiXYJMbSZqrcYKlzHPSrlwgtyDKo2NI6MqUNUkRJ7qtGeceoDD2AkiAR/FXiEwCIMgag1GtmAhI2IFSVJIgAkx21TNuKPSiDfqzggbc65DEkypXIV2dy1nmdSdq5TGWihZ5a1cTHq7atkbDCcyTE91dR0+VAQNJAAMzXL2CQVACuotWi9l5hMSKNiNNxSJljZoU4pxQ6sTJqwDqEtpQiAJgGK3kLTaQYTAk6VHY/EeSmZAMaUB1VFQ2Rly1O+hFKSr7ugmAJ7eVT70pSAZIHfVS++gIGs99UVP4sS5dFTqgnnVphrWUBREDeTVfhdibglaxA3roDbJQyTrtsPV21LAxxb+TK6+Wlm1edOoSglUp5c9qPhwLYwpzOCHFpL0zsSqf7FKxQdIlmzQoKQ6sFwRpkTqRPeYHtqwYSplpWoAyFOnrGlX2KSud+Dr8JwlvyiYF/wDGVAG6uVZ8PWf9u45o7gvT2x21lVmC3f3Fxp5hSm3EqS80U6FKgayqcU+SsmnnN9WOVfoc8hIKwkAAKlMRvXOXzSsMuw5HUUrSuizQkJ0z7yJgmoeM2qcRtFJSIWnrJMUYuceqNrlG70dNhoWkgymqXBLqVlsnRJ58quLBXS4apo6FM6z2/wCGuVQ4bTFlA6BW4q0JyvplGR1ZAuGgCCSOc1VrHQvdxMHWrBlYAkaTBqLfJlzq6xQmiVNAEQTPWkbVFuEhRJywZzVOZSVoAI27eygdaC0EfnB1qxTV8E/C3+lbSFaQNZp10ymdvZULDh0QVpPbUl5zpZ1ECYqjSt4pkXKCqNK2pJIkjQjblRBI1lMkd1YpKjOg91UDyIUwVEEHbXWlPsZUkzGkmBU8gJJE6DXXnWinOBJBA01qAOCZRvNQhKvfFE0sBBSesJ0irG4turDfPQVXuWy0rAA9lQS4uL2GPspdSCkQedQS2W1QBrP8VLaJbUEqjej6IKlXPbfnUsjXVuR0PdUjmf5prSglxJ5DmKSpHRKkiZ2p7KwnrCAqasiuxyyDrPW27KCDmAJABO6YNPcAUkieykKMLjWagbJAgCYVHqo0qOpnrdlY20VoHLs12rHuoEnUGKsgQ6wB1M6VsbETpGvOtNGUAGZP8VIQEaj8vcNqoKiOEnIBsBtpWQCATsZgzPOmlGogRzM0paJKTl1nWoiUYZUN9ZO9JbbUHNonU01AKjHbrNbGhkDQc4qbkNLAAMxtEVHcZQQRzjY8qklU6AjTQUpwhQ1MzoIqICSsrryxS6NAI5VS4lgaHUHqjMBv3V0rrqdYnfY1HdAcIkbUS2MuXFHIqaOMtnnbC4Q1ck9DmhLp3T3E9nyq/snS6ytCznaVoQN/X66zEbFq5ZU2Ua9tUds7dYS6psKKmokD+qLk5y6tPKnujL9KrS4KFnQ9ZKuRHbXQ+Tzj698nvEbF/bOEWrigHkco/VFVryGsasNNHU696T2+rtrOGMJOJ3jtvcoKGmCC6uJBHIDtmlThHJFxkAozWVOD54PqPyweXt7ivhaywLDXCi1caQ5fOgx0qplLY/4jcjmYGwM+E3NwASs+ZqNTRYhcp1UAG20CMo2AG1c1iuMKeR0TRJA1mOVIwYIYY9EEdzLn9tfIbdXwuH0pCpBVtzPdUJkrxS8U2g/hlySrfqp5fxWsNY6AKedUFLgmOYFWNgz92tXVNoSnqBO2uZRj+zWmqOb8srTfBWlgXl1nynzjl05VdOsQpOkHQa6cqkM2rbamWwBAAJIHt1pymw5ClbTM+uoaoYem75AsbcDo5Emd6l3RUm3Ke6D3nnRW4yLBEbGBFafPSZUgTrOlCbYpKNCbVjqmQBIEa99SsvZMClo0GmwO9NEECQZnYmruyJUbKglAJ0UfbApSMxUQDBGtPbSV6gADfQVnRkZZ1B2NCMpiVx1jM5v4rSEkglU7c6eAkAaTrqO+tKCUo9R51dg1ZHZJIidQY0qWyEjzk6+uoyYCpSNzzqSYBmCdRP8A3UJE2qNIETIrOizBOw9Q3rOkGZP5dIijCcyQmRtOtUHQpaOsU5YHYD/FCtMCI/8AVOJlZOnt7K0oFJ3kHkedQlEdCNASNuZGlbbCSpIAgab86apOdOwPP1ihZaIXPfv21CUiY2jKiAI5dmtElOdekgbGT3UxhpSgAnXuNYU9GFEiKo0K0iPctygmRpz7YrkscSSSmJ1rrnCFFWkzp7K5zGLfMCQZolyZc8bgyksBDoI3767bCUBaByHOuOtgA4AIBNdtgreVCSEkg70cjJpVTHXa8ratcpmNKrrN/wDFygkxJ1qRjDgaQog8zNVGFvS/J1M9tAjdknU0i4xS4DLQJkaSBVZYIN8tInQGTT8WUbhOk90U7BbVbDBWvaRqai2QLXXkotsgtWAIhXf696kKLhQhCjGZWkjUc9qonbxVzfobSefIbVfOOoamRohPWAG9CaFJSteCMhlN1iqnCEkIAQkAQJ3J9/yqVdFtoLQlORagBHIxqT/Irdi2kNlSkgKIzEz9a08lBfQgjVJMwN53/wA7qsGthlkkqKWs3WiQQfdWUCVHpAsdWDFZVmhUkUiEykAkhSND3xH9U5J6qhAKhqBPL/PnSGn0C9SF+a51dufKpob6MapSO2df47aNnPiR7VAadWEjqKEjsrj+KP8AwsUbc2B5iuxdQGhlGubURBg9lc9xlZfeLRL3OJJioI1Mf2T6exNtXQ6ylWadN6etsEZlD6Vz3DeJJftEtrMqGhrqGkhQJGyuyqYWKSyQTRFZUltREaa7UaModXOx/mohSUuQNdfdUwAApMeuoEjTZ6PXmd57aclSXNJ0nnUF5ZKxEmNKnWDSgkuEGd49dUMg+wSkiI0E6RvQrMgCBoBzqSsjeBoPdSVtggknWdT21QVC18yd+WlLBIkkkyeznUgpCU6dZXaTyojbw2QIJI/zWoX02JzBcTtNY60lUEjTtFBqVAA6ds6U0ozITGsDeKgNWRlWoWEkD3Ckt2xjcxM1YNK0IUO2JrEDKo6EQZkVYLiiscsyrv1pKLVTZkpI51cEDMSBO3vrZZQ4NeZ1INQpRKjKoq5RJ2oxKlgkGP8ANKlm3Qk9WRpQloGFRG5AqiNNG0QGwY0ka0DoWBsNqNaVJaASoBI2BrY2QpR5cu2rIkYwk5QdR6qaoaRrqdZFAJSlKQO8k6UwpJSIAABO391RK7GIgJMgE95rTwSNtopkecFKpS9Un19lQuqQhs5nCI0GszTlJA6xza6e2KFsEnXs5UatZA27OQqwd+wpZBBgSe2kLQVToQZ11p5Qdhz7qWU6xECTqOVQpkRwZVJgyTtUVx0mT31KeSSrt5b1AeEQdNeyrM8tgXCFJkGDz0pCrZu5cR1QdY9lYtZSOzWsQ7lSI3nSrMknbplY/YXFldJVaEKWohITyVNdmzYXFu1a2Vqx01w+vVIMCeZJ5AT/ADULBmkvum5W2ChodUbyo/SvSPI3b2fFHGOM4a5P363s2HGW23EocWhSlpXkKtAcy2NToNzoDUbKqOCDnfLpFTxN5HMewPgV/Fm37bFrZsF24+7ZukagZl6KHWSncgGQBmKQASPKbJhV0lJSfO591fU3kzOM8IYTxLZcYW/ENk5/ptipu0xq2CEjKVBBzTJdjRQjY69lfOuDMW9kL1LGtv8AenkMEj/bCyE/wKi2MmGUs01GT2oWixCGVeIDsqUiAq3QDmBWT6sqfqqprLYeaEI0KiSnt/6oVs/+ewkgpAZWrQRusD/92qs6yglVfYxDZzFQnTsp/QKW4nQgDUa0zKcyQATTyRmJIggQDQmuiGW1SQCJnTSmpaShpGvXy61txPXMCJT/ADWIEgATHrqBUg+jSkAATzMCgIlxXVnSnQpIAIIMbbUsAhtwqEaxrvt/3UsuqBYORs7600wUxEAfzRW7KEglRjTatFOWdyO3tqglwaUkJT1VExO/OlhsAdbrCaIOdYwdjtWlKIT1QBm7KhVCVarBAjnUkkKSAJjfTt/9UgqXnAiMu8CKelOoJ3G3dUstIEghcxoFbfKpLaIB0OvaPeKSkEKE+aDzqQhZywoEd5FQvpsX0aEr017PpW3COjjMCaJxPqJjftqPclSphOx59lTkj2DC0qBgRA33om4MjMI9cVFbQuFmNTzqQyMo7Fdu9UUrZZWjiTqdNue1A+5KVScunroEJSUmFyeQOhrCVE5hBBOs1DRwthKkpPXB17KqMaUkZteXPnVspQQ2ZkSe2ubxMm4fjPIG9WuTNnlUaRAtGlLeSSMpnsrucIyhkEiSdYNc3a2QQvPGmYb10tiQ2lIIGhP+TRNitPBxZDxxvResSTpXPWKgi5A5/wB11GMt6L1J2O+2lcgtRZufryqImofyTOoaR08TGvdpU26ULazIiIHqqFgrgWEyYVy00o+ILnJbEHaNJ3qNDouoOTK7Ax96xRxXnBImD2V0SglSyhSMwUqRHMb/AOeuqThVpKg8sDUAyZjlVzahxdwVxGUZettPOqZMK+F+Sc650LXVb0Ak66nXQVHLQQGo6ypiTTbhQKBOuseqN/nW2lDMCRAUfcaE00mxSkrStX/LU1lSkgJTtBB27RNZUsI5S4tw4nMlUHeCNiOdWVtku0hbioEQQTsqqdi66RtKVanl/dSkfgFSSSErie48jTWc2D7lg+EPILYUBGxB1quv0Ju7R5lRAXlzCO311OSsAFLTeiRBVJE9tQXrdTz6XApSUmYEe41Qb32PO7K4VheJLaPmlWxr0KxeSplOvqrjuOcOUw63dNpyzrtVvw3eG7wtlzc7R6qtnL0zeLLLC+3Bb3DQSvSAO6tF8ob21nlTs6ejOgkDMI31pLTP3hZMkJ2A7ao6SbsUw2VrKiNxyq3t3ChrLtyJFRkNBtyBBM7mnrVCSr2T2VBkdhLi4WrTescclCdTpvPOkqdSskbk7a1nRKcGuiZ9lUSx3TZgZITyrX3nPKRvG3ZQFgtpzKMAa61jTLeiwozzFQpNokss5WyTAnb5zS3XE5UjePrUlAJSQrs0qK6gpg6z3iaoM20oESowRsaxZypEkHYmKQoqmI2GoH+bUy0bKlQZSAkkknQd/wDnbUFvkFtXWGaR2kVIWvKmZgRtRPNAD8x00kACffSlBSu3bX+6thIQhyVdYAmPfW1QqCSNeVYhIJ/6qQpsSMpB9RqkRoU4QQBHLQDel75dCe4nWnOMqHarsM7UKmwU7E1ZW4nKTnHZqNamoASkDWeVRi2lK463vgbVKSodHtynvmqCQpcgQdZjTmKWpRzGdD2U5awTAIiOQ2reQLHMEnc+uoU9xTaCecabf1Tw2QYKTGxzVgPR8gecxy5VpxyZGXUad9QlKhRIykpJI33pbkKJ0HZR5QAZ6s9o76BQBSIBGlWAyG6mEa6ae2qq8QdOSQauHhlBTvpzFQXwmNQSOdQzZOCkfUUJIB5yDQhRWkiYIBiO3lSsSeLa1QIERFWXDdkL9+3SQJUsAgmjRzb6p9COkRZItbC3YSrUQpRjcx/6qvDd3hfFOH45hV67h2KWy0oTctJCuqZSQUnRSSCUlJBBBIIIq9dSEvOaAieqY2qMpvckCZEGdN+VKvc6+TDHJDoaOq428sXEvFeG2ttdWtnaX/3dCXbtDj6yyYg9EhbhShUbK1y/lymCPP7OwZYSltOqG0wkA6CNqsX2G8oQBl20SdKj21sEKUo6iNY5USYiGmx4ncVySc4gagAaga/5yoW2VG9dc1ISy0kE9+ZR+YrXQJW4nP6PTke+paUttvPBBKUw2AB4B9ahpSurEtoUF7xypkpSpKBME6zRIR+Isg+aO3n2UhTYC1mZHLsqg+DHEkSRr66YycsactQKW47AAg6aUSFFaCToSI03NUEvsE4ZHMj1VlsAtkTtvAOlbUvqlJ0POPpW7dom33Om/vqFdxuU7pgilLTGWAcwG1MSoNTsSfpSukBc7E7QKgbYJTEqIMnb11gBkAjlm1OwrWY9HMctu2slKnCdtIBNUUYEhS82gImQKY0OsQYkHY0CIJBJJ0FGiQSQAYG/bULTs0skExBnlzo2G+sCVTrrRJGpk6jQd9EhGbQEjvMa1GGlZooITIkkiIHqpS3CCBBBkEEaRUhSsqIJzSdo/wA7aQ+2VEZTIInQ71CMYhYSYyiB31iAlStRofdQJSoIkjWTvRNGFq1JV3bioUiTlGh0Bj3mtJglZ0zHs3mtAqQqAQIigyDVRIEbirGX4FXaAnMADGlVjVuhx0kgSToKs3SMvWPW20NQWm8lxHWgDsqITPcmIZTCgdO/sqS0RlEKkJUYmgEFKzuAuaJiCUADMIkyajGQ2DvT0qYIHmiuNxFvo7gxtO21dxdNAoSZ1I1rkccgvyAAD2bVaM+qXxsuMA6yEGezSoHE1xlzIGhJ1FT8ASPuZMwoCK5vHni7fpTMwdZq/wB4Vll06c6zg63/APyx4kk5iBt7dKumgUNrUojKJUR3b86hcNsBvBGxsVLj11Mu1dC0USVdIuCTyG5+VC+TVj+EEREywGpXOkgctd/7pzRU84mCCjtiorySVrUUwlWpnc9lSmHASCCEAbGag2JOd/DghQKoA1G9ZQ9MJMwZg+usoR9nn2EuZ5bWOsNgTV2RmKpOaBBrmrN0t4k4g9vOuhSrKnq8xT2cXA7jRKQ62lhRWo6DUgc/X3/1WmlhSfMyj8pOmvqqI28gryLOVKoBO9TnVEqKUKORBMwIJ7qE0JtkDG7NGIYXKkpzJkGOXMf3XO8GpLdq8zHonCBPfrXXuFC7dxCiCSN65PhkZby+QZGZU+6rMuSCWaEl3tHSNILqkp2EQeygeuOgUEpAB7e2mKX93ZUSdTvrVMq6L70A8+dUanLpVdy/RDiQsGe0Up1cHKDI5a1jCf8Ax0xtJBFClGedtagV3sJRbKUtR84cjVi663bNSYntFalLTSid8vbXM4vixLmXNVAylHGrZIvsX6R0pBjv7K3auuQkics9tU7CVvvzqZ3rprBoBpIIjQ7f3ViIdU3ZMZezM6gnTQGtpHTNnX3D+KQUqC9AIG9S7VkrbjRMdun+c6E2J+SOhsAqjWYAmjRAmfO9XKjdAaTpqZmYmkAkL1MDXbQ1CDTO8zpJI0rQlMpJgHT2ViEwvVW4g6U4ETqTlOw7TVkoVBUsHUZt4FEWygAwSdd9hW80AAGRO3bQuuAymNP8ihLo2oAghXMUpxKUqMHTnRlBIBJmNJrT9vlSFawYEAVYDI7plciKc08UtkQDJPL2UKjlSc0yBGvbWIQVJAmB3VZEbRoCer2d01rpOjnQ7b9utNDZiY5b0JQFqjXtnnVFsLztZgnUTS0kBUEFPs2o0qKRoo6aRtWlpJWTMnUx31CkjFJJSFczvrSS2pPeDrFSEOdQggRvQLUErg9g2151RGkiC+nrGdeWvZUK5OVPPX+asnRmEFMRyFRnmxlHV0599WIlGzkcTjMJFdBwUjo7plZMAJUvXuFc1j/4NwlI1JI1rreDwEJWpRgC2IkdpMUzscrCr1FeC+cbDuVQJJ50hwZEaqAHICpWgSSNDliI51DJC1gQTAGwpJ3xBkrMyQK2ElCQZ3O5pT5UJImO6jbeGUJMHTYjnRiiQlUQViTG551tIKXniYgKRrsPRppKCSRIHOSfZW3JS8+c+2QD/wDZp5VAL3Qxl8FTiTvMaVkArJKTtpSMPWVl3SSDzO2lPylSVazyHfVDeUmhbgQScu07VtsdGkJJ0CtDO1bKQIGmpG1GrrKGm3KoVQLmqT+og/4KZbwlCtzuAJoE6KM7bweZrRciBoeWoqguHY9RzQNYJkgd9KcVlk7GdxRFYKD8jSSvQgyTGsioXsglAKggkbRrQpAzbCefdRISCqSN++jyBLmbSNINQoFkEBWkDfspqRDiTyns3rMpKkqj2xRFYJmTAMa/521C0jeQRsY762s5BEH1DtNMWEo1BmRoBypJBzSCZNTkOmjaklQGUb6bb0xlmEExmiRJraQAjMQc07jSe6iBITEp579tUEgXQAkGN+daQhLaiAJB1mtrTOp0AFaZAWSDpyEa+yoimGrUyoQdDptWIbGwEj/PrTSiWUjQgVXXd45bnzoSNNNKst7KwnrdaVAkkQT6qQmS8ZmYHt76lW9+i7ASqNRy/wA9dKurMoWFjrD11BddW8eAgS0hYB3NOZEknLJ0HtqMhJf7u0ka1NtUysaaDsqMKKoe+grCAqJrlsfY6NWxIJrr3AEtNqG/d2VzXEKQU5hpzkdtUitQrgOwIEWzip2QYJrkLt0nGVIiRMRXVWC+gw50TASDBrjrVX3nF5iZXl03pi5OXqHUIRPU8OQW7C1b0EpLkAxOse6l4rdJbKUJTLnJM89P89tMdT92W2Apag20ElAHdrURRD7vSKJEpGUkRpuCffQHX/d6WZMtDNBVAB1o2CqCE8jQIQHFSVT7alJSA2QBl+dQKKGFeVaVTmA1g1laaMqzEDafYKypYxKzzTEgbHGFGeqpW/I10bNyHGkzBMdtQeJcO6dJJ0VvNQsJvZR93dP4iDA76acHG3iyOD4ZfKbzA6g8xrUltTj7aUIPR75hG0f+/wCagmUI6u+8TRWtwtL5BhQIMR/nZNVRqjKmTMg8wKMg6qidP85VScPWxZvrxaj1TqZ1q8ZdbdWQgdUc4qvvHUWCXEJQUuEnNO81CTSTU32I+IXYW4tGbUd9RGBkcBKpzHYVWB5artUyVTFW9kwVKSDomQRPZV8GSM/clZf2utsDliDsdaktJCZMDaBpvUZtJDCQIBGvZFMuXeiaKgozE6mgs6a2VlNj2Km0lP6tq5JtxV9cgzz0pnEl+XXiJ1B1qRw5ZKUQtWs67USVbnDy5HmzdC4L3CrTKnMRrvJ7avGz0LaRAHdNKt2QhKYG49tSpBUBEx7qF7nZxroVCxCnAdYO8CpDTnRJ6wAB5TrWlgKJyqBjkDtQuELMwNDNQclsC8CobkKO3ZvWIaClyRPPXSmJSFAiDI1JolgBo9kdu1QES6wqZRz+lbaBMTPsoyCmBP8AH80GYdg0O/YaiLsxZhW8qmdaxSJSTr6id6UpzrARCTW3nSUmIPafnUJY4pyCAQRIFA4eoqUzrRB0KETBEGgcUVK1EHu5VRVhi2UsToR2fWgOieUbgT2VgeLaT1jlHtiozqlLKfdvvV2VaJaDA3kwYAoGnICtgZ58hUZKSuATPfTW0kKUkAEb61CGz+MQARtuRUhCAluABM6n1aUkJ6NStQSBsOVNCpEdvbuBVFxFAwJnSPUKWpsGdSI0HbTHZBAI2ikg5iT1dKhTNHKqNh/dKcGZGg0iSeelSijVMazO1Rhmyq1g67Cogao4niduLlpRGg0rpuFBnt3hpIbA05HNXP8AFgCX2APzK1Hrq/4Q9BdCJIyJns3M0b+k5ODbVs6PIErAUZlJie2aQ6hCCOWxgUzNDohJjLrpGutA44QNRIOhmknddPgirSkpOsqP6qUrqrkxO29OeWkFJmNfXSENqKgQoGewUaQiT8D1QVgggAVCvnM11cFOgKkf/wDNNSnHIMEFO50PPSoFyom9uZUT10b/AP8AbTVoTN8L/eB2DqJLmpAk7GDVmFCSTqdKhYSwSlagYjfn/FSZWkHcKqmNgqirNEEug+qY1rAR064TBAiO/nUqyt+lfUQAdIPMbUhtOZ+4IEoSv1RrUYS5s06pKQvcnNueVC2Ok1EaR5wrYOZImSVEmOVbJAKdd1DU91RBc7mOAB4pykgGCTvFJUZBjQ7Ua5nNMDkN6Bo5kgmSKgL3ZiUaAk6RoO/WnpV1tSACNTSymJAI7v8AqikKEc4keuqKqgydDuBGp9VEghSQmATJj3UmRrOoO06c6kIR10cgOQGtQNOjQJKSDM8xA5ViXBmSVbxBmmFKVrJMgQfbQLSoCNOQ9dUGn5GFZAjX1TRNKK4/ydKWkKWEGdTIo0IyqChJERE1ArCWkBJOo57zSSkzoRCTTXHCoQQSCI1OtKW5mCgNBAqEH27hBETNQsbaDtuVp0UPbFSWpyiR7R2UD0gFKh5wIOlUW940cfYYr0dwQV5UpMb11dlirVxlSSlSSO3n2Vx2O4Oq0St1A05RVNY4uu0dBKykgiQdKZVo4v8AyJaafRM9OuW1tOJKCcg7dqdaKOmZMd+lQeHMXbxVshxYJ10O9Wa2C0uSNAqYmgO3jcckeuPA938RsRCRFUOMNqW3rsBOlXKnQkamSTIJqBibcs6mNefKoTKuqLKi5f6LCnY0VG8RVDwjbC6xhpJByqWPnU7HHOisFKneRRcCMZLhTp2QknWmLZHDn888I+Dur2Xm3i3AcJKkk8hO1UjVyp91Q3RmIzHmKsnlFpkuBSUlJghRjYTVO26FJKxKWxzI39VAdact0WhcQykn1Sqm2n46wqTkAiO2qizQu+fgq/DHdNXJeQxbhtBgAbjepwHCTkrfBl9chAKEKgkRI2rKikFxZnrFUzHKsqBNt7og4w2FgxzE7yDXHXTPWKkHKtJkEV2t2npWweaREiuTxdtVu8XEiUyAYpqORqVW5Jw3ES7+G55+lW7LYKxlMpzaxuK5QEAJeaMLSZgdlXljiKX0jrQoGo0DiyXsy3aulqASygBcmT2Hn/nqqLiVuEJSowVZcpPyqIu5Xa4gAFJCHdAR2x/n8U+4U3bMqLrqS6RBJ5eqqob19Sd9jmrohp8HYgwRzq9wRZuFSNeXfVBftrLpIGUAwedX/Dg6JhxZkEJPLarfBlwX7tHQ9UkCYkT3eqqrGLro2iTKTHbW7TE03KXUKIDiOfd2iuf4lxAoaUJ7pOvKhSNmbKo43JM5PELn7xfBIO53rvsAY6O3SqJnka85w1BvMSSDqJr1HDkBppAIOgiO2jeyOR6euucpss0kiZEGJogYEwZ9VYlMSM0kd3OiOQKgp5+rWlnoEwmnAWzB7ifbQtKUSdZ03J762VJCMo5DkaFJARMgzFQuxiBIMEgAb1twFLc66GZ7qWhycw7T2Vt90BOsGeUb1C72CQ4ANSRPMjegcTIHLkQaWRmQCBqR20bbRTMmTU4IrYswFAGIn31JQEhzUCZjb3UotgKAAmRy33rRBkSdBULY0hCRrI7SaWVCdiSYiDWwJAA22JNKcUAco1J2kcqoHcJeVQ231isSk5fN57jlQpB86Z57cqelslOgPPcVCIT6NQgxOk8tqMKSIVI05fWhcaKglXdMzzmgSJBBTm7gdahYxkpPSD+TTFShGkwI7p9VJAGUxoT28zTVaoGgIiI51bLRFWVF+ASRS1pIUOtl5/8AVNUJc3OhisUSJ7IOhFUSkzaDOubUbxzraGpkwRrIB+dJJKiQCDGomnsLX1CYg1AedjiuOEKafZWJ84AA1ecCo6XC7hwKIJuEjQTplqm48UYb1/OB/NXfASSjA5M+nUdOwJFH+6cfGq1rR0KiG3YMnl2VHcCZCZk7iNqbcPkrlIlKUgyTNK6IkTG2hmlncb8ERSCCNpnmZ9labTkE5ikDWO+pKECZ3V3cq30BKhpp3moKoS4M6kyfYDVddSm+uAdwtB11j8NJq1UEqy7TrB7Nqg3jZcurlR5qRr//AK0VYmauv97DMMUvI4Cf+Xt2qctYW23r1iY63MCarGFZEnL3Rr301D4KgdgNpq63GRe1FlbP9ElwidoHaKUjVlxYMSqY9lIW4pLKCPOJg1ItyDbqnT61Qcd3uIQCADp7507KJClLQ3oT1txvvWvMWkjYpmBpW2lFLQIEgEmYjnULXNGlTKlESNduWulbQ1ljUA71p1AGYk7GADzraBJSFQCEipZKox9B0O+sDXY99LaUS4ZIgxTXvNgpnU70LaASQBsZqFOrGlaJEQD6opjStjExoYM0lSICgSOwVvMUpJ1VzIqi+CQsxqdZBG9Ct0FqRJO1bCNTMwdDQrbgqgg7D1eyoHfkNtIPRiJJmOe9MVKgDpIM6DviKTEKOXkTGutMalTZJg8t6oJb7DEtJMGee/bW+hQsozDzpkDTnWMr6mvV005UY1SOYPI/KoGt0ClOdYECPNJNauW5GhJPKdKYhISVGMwB5cq0vrTodBoNxVF/Yq7lgPtFBTm5RXm3FWHKtVlaUwOWleputmCYEdo99UuMYSjEGVBQ6xB0NEnRzdZpvehS5PNcAxtywu0FK8oJia9lwjEhiVo2oEZyBP1rwvHMNcwi9KSOrPVNegcAY107SElQB2InnTJK1Zx/S9TLFleCZ3vQSRJhXdVdjBKbYwZJ0I51YuvQJmQd6osRuS64lAJBnTvpZ6fK6jRU8TMFrCWeZPbvVtwlaAYYNU5nFRCo1AGvsk1B4mOc2dmCc64qzat127LaWCcrPUJSdD2n3/Ki7HOhGs7l4RcYtZ//AJe4c+VSk69h1Fc6grxF1LLQ/Db0UdqtcVvl3eFlpoytS0AlPIb+rlPtoUBnDbQJbSM8TPbVGqa65bcdyQ021YsBsAE9szNRZW44nrCTyFJD61rywSrUSeWlWVnapQgKUrOqdz20I5NSVLgfbsG3aM+erSsoLq6Skjv2isqxl1sitUgDQHICOf8AdUGOI6p1q2dvAmAmARuO0d1RLxPTpM9YRFMRz8tSjRxjD5buYCtKu8OQhw5gIOhIFUWKW33G8zpBynbWrLCbkEp/LzomcXDLpn0yC4rbfS0h5heqREd4qPhuMrxezznIhxMpWk7hVdBiDSF20x1VCYiuAfdGE4mpaTkZc6rkch2+yogdTJ4MnW38Xz/k6hLiFWqkpIUpB/KOX/X0q7wcf+M6Dp1d65Rd60plK7VxKwN4OhHZV7aYu0xZ9IhRVmR1RFQ04MkXK2+wNg5GMqbKh1kq+U/1XPcW3MOET207DL5dxxBbE7Fe/sNUnFdyXLwioluYdRm/YOvJJ4RbBuy4Roedei2YWBKQIJ9dcPwYhOUKVvXeNAoSATynSozb6dGsSJbjjmQFJHbI21qOt6ddZHaaPpCW4I12ioqgc86HNvrtQHWZYNKKxI0BHOtoGZKRud49VLtVfhBMabwKe0s5dBBToM2nPaoGkCqUDqg66k9tCtZWcsmOynEhRkiRI0/qkFIChPqnY1CmMYOsRPMUwKypVEUtrLJ62sRHZRrRqU847KgSbNrCoOpGw150gKIzTM9lSCVJIBIgyd+7elqASlMnUzp3RVENpXBOs6k6mhGWRCdj7aFslIMkBU93dTWzJPWE+qoFaNpTlTrAnvo+khJkxmkGKFSkCFBUq9VLfWAoGOwmoS/BtxZIUdyoyTtQNGSATvvQBAXJzdmgp7aQFaHrHSrB7inEGOqCSddqJAUpGsb1ihCAQRqaWles7+qqoszLBJzER2UJJzmDpEa702CZAET31oICiSCRp7aqyI1lEDXWloUoQJ0Ea9grbpU2RlnU7VphSVEyCQdY7KsFvejkfKAAhlCo1zp1q/4PlGBW5CfPcWdPYK5zygrUpSWhso9vfXS8HjouH7WSQTn5f8jrV/unJxb66X5Fy8c5K8oAMRy5ChSvryCRpNA8Qmcs6HmNaFoKbCz/AB30HB22wwQSZnurRUFHNptvPfS4JzRA0FG3JUUqIjTWoACpsECFFBEq3mOyP5qBcuq6a4Svrdca8/MRVncISElSxGhmDrzioT6RnuyRKi8U6+FNWhc96oitApQo7GRr/NaU4GirWJ5e2mtpHRrPLNGusUl9onWIJqxb4QwPlbaQNasbWTZFRHOD/VU6VBsjXv3qdbXB+7lJ6oKtNdqnYKEqZKUoJ3kmI7wKC0WlaUZuUz3xTn20lmZMQJ79NaholvzQdSSP7oUOb3H3hJUY0nXatMmSNomdqW24olQjbWfZNJtHsojXqkJioU3bJ7xIVuI12pCcxnLqQT8qJk9Ivo1an3a05DQQQrTuHM1CVe4lLpckaAwZE1tLZUARsDqO3sobpAYJeQITBzAD+aZbOFQ0yKB2mrLi+zJSYKomSdaFa1ACNDPrmizZXNtQTBIrISEd8iKoM2jVMyAqJiNJrZUgSAZ0nXTsoww3lUQrXYJB+VLeSlKhooggGRMjtqBLY3nlBKSNSD3UDVzlKxEZjvOvdWISnJCQqTvrqDS3UnLKRBjaagTvsTWnAUFUkgTp2RRgJhRSNTprVXbOqb6pO5q4aQFpGugTqaouLsUtPVAzAiNfdUJQI1g61MWodUjSO+lOEhI5DmRpUI9zi+NMBGI2YWkZnAeQ5VxfCDq7LF1MLJSQZAr1m6RnlCoKTyrzjivDhgmPWdyiA29KTHbTovajzOvwe3kjqo9mr/oes2iEXFmFHUgczVIwkv4yEI9899SMEvemwjOInKIjX1zS8EBbuHblYnMYHYaWd6UlNQ+5IxWwQ/cs3BEqaMDf2bUaVtqt1OtOFTgEKSTvyqZCVrKwMyANhyqHeWzaHgq3AAiSDyP+T/FVyE1VtdzTyDaWlvlMvOLUskdug195qFcKDkoUZOsxWYxiabQtoP5Wh7yZP9VSpxBx0LCNZ1JNWkZcmWMX0l0b5JcJHnKPt1q6ttLYrUNR86pcJw8BxLrnWV2E1bPuFeUCQNYI/uoacNtWwX0hSzOsmdqyttpzALiI5H+KyqGnKrX0p84T2VJbWtaSF7jn2ioj7aCsGC0sd2k01CygSQFgdnOmnKTKbiNmUZ+2qfDbnKrfbaunxNKbi1XlArilk210Y2olucjUr28imjvWHTc2BkiUiDrXC8U2hR+IO3lXY4G70tqpJiCNPXVBjbiZKFiNYNUuRusSyYUzhrW8csnMyDpzSdjXS4biqLlPRE5W3DoCfMX9DXNXrIbeUBtNKZeLKpGx0I7ac11KzyWLPPTz6Xwd5hdutnGGz5uQKVr3JNc9xCCrEDqSTV7wtiQvkuFXWeZZUCT+YHQH+qocUPSYgrSNYApXc7GZxlgTjw2dXwZbgpzbCYrsEqKeqYnb1iua4UaLLIJ0q9deKdQkd8UMj0WjXTiSJbSpOqgZMUZaC4XO06xUVt/OPNiak9KdEmd9RQo2khhEQodnOmBfV0SNBM/xQtJyNzty7aAAkZsxCB/FQddUGh05J1TEb6c6wnWYJ0mZ76jFQExvMEU9pYAylRHLTlUA3bo2FlBHV6oOX60YdKjr6pA51oIEzBVHImtrcASQEgSNdKhdUbkuKG+3MURQAAkwSdwPl6qBLhCiJBE6SOVaC+lUJ1Kuc1QS3NuJVlA2gR/dAVEbTEazRlSSJggbbf520lZ6x5A661Cmw0JIGgJnWe81jiTuSDWNJITJ10iKIt5oAHLsqEBtVABUASR2xTEKUTqnXsGwoUtABR2G/ZWFXQpmDr27xUJQSySkJVpoaWEhAncnTesS6XlADTcAgzWyVBYBmY0gzrVIs2pZJgDc7xRqCSZnQzJpYkCO2J5VpzUADzSd6sq6Yh54gqT2d9CwiCpR/mtFOZQSRGvLlTioJYUO7Q86gKXU7OB4yWXMRYbBka12/DbYGA4encqaKo/+xrgcZJu8fTInLJM16RhDSWcJsEiYFulW3MiTRPg5Wj+WpyT/AN7DFAJSpM7HkdIoElZkaBR1E8qx11SlqB2J3zSB7edaCfOJkCdxrQHcBSpRJASJmfbTQlKQogjrHcHfvpKiEmRoodvPWtMFS3Bl0gRVAdw7hcJUTB0iCTUda8yrlQmC85z/AOUf1TXcy8yI1jc9lQOkCVOAER0jipV4zVi3s9yS0oBiTqd4NacmIzR3ittJDjbYBG+5pboyoB0I/mqLq0RXUHMJg6aQa0XC20nUiFT/ABTQsqHIwIn2Up1MMjNp1jqNqIQ1TsntXpcJGbaKltN9XfaRoJiqRt3osyp0AEzVxZ3rD9uq4QuUqURkM7xBju1GvfVD45I1uEgdHmVvHyqE42psLcSJBUSe2pinw4wsJKcwBIyqE6GO2hCVtBSXGlp56pnl3VCNprYXZvnpCrUgDQRHvqSpwnMACfVVY3cpt7lSFGAobnSpaH0rJ589Dyqyoy2olBSXmSARJ0qJh/8A4r67dWxP4Z7qaFELSdd5HZWsQC3MqmwA4kggzuOyqLk/3l2LG2bL85tAVcjtUVxwpcIIjKTtrUu1uemYQ4nQqTqR20pxErOhE6xtVDtqTRjS1SY1Om9bgqIBICpJA91aS2AoqJiQYBFbWSACNQDGg7KhZpQyKCs0axp3TTUEOaATtvqKU0olMGUkaDNW2VZXiRASreKgUWKvWDBIABGxP91qzvCuUKVBGwJ33qb0fSJVPLl2VR3I+73AVrlnYHvqci5/B9SL9DiUgKVCpPPsredLuYiCFe+o4UXbMlO5ImPVVM++/bk5UkwI22FDQ2U1FW0WpYLi9UkDUTIPOuK8qlmpWDWq0iFNvlZPYMsV0NvxAUEJUMp2OYVSeUC4Rc8LvqEaFJEHv1o47NHL1s4ZdNkX2IfCHEyThqWFDNnEETtV0m6Ve3jVsx1UNiVE6BJPIntrx7CbxVpcghRAO4mu1s8fNp1itKQdf8FNlGmcLR+oPJjUZvg7pGJ3GGXSm4kHXKSVCOU91WzKkvuIWAApR1AOgNee2XEyX7kOEa6dtWN3xE/Z27t42no2oUlHSDVaiCAEjsG5PdS6O3DVwrqvZFfjWJf6hjFytJ/CKyltI5AaD5VdYRaZUhahAHvrkeGbJ29cDqycoOWa9GtQhlkQgzsZFE9tjNpLzt5ZLkWh9bagkDLB51Ot3BH4iwTvFQXHXFKACUgCmW5SiCSDE6k0s68W0S1uLXCUiB2jSKylsly6cBEADasqPYbFOSsolX7bxPTMZdtQKjLLSpLTgBOwNTlXTKtIgGq67w61dUVBRAJ5GDTTlztrbc2y2sqy5goKmBzrmOILE27uYDQ6+qr1OHraUclwsdnMUvFrM3diFLIU4BCiOdWjDmh142mt0QeGcRyvIQowDvWcUsrCSspkidYqntVqs7oHkDrXTY24HsIU+RmhGaJ3q+5khJ5MEovseb3LhdJkCahkRTnH87hMRJmKWrXanLY8lkanujqOCUZLTE3j5uVCB7ST/VAlhK7ouObA6JFT+FUhnht1QTmU4+eXYAP7pRtz04JnU7UtvdnoMWOsGNfr/FnQ4HcqdA0hMRV+q3z5ezvqowC180ARGoro20J2AMCIpTPT6eL6FYsANiN4GunKpjaAVDQbfxSwjKNJOkDlNMQOjWAQT6udUbEG86Qk8pPKoodUkAZTTVrzo3kDWBzqMXQoE6mfbVIknubYlsqmACTyn11tKsoJSInXega/EKlCZkwaNuVg5Ud+tQCx4cISCInWIrFKVIMA69tKSS0FTMAT3VtKwpQAHVPdJqyWPSrMIIkEanburAkkEEGY05ilgdWSIO3cedEDA561Aw3FbCfZQRzMGRtGtaI6RZkx7Nq04spMHQAwT7aqyxhMAgGABpHro83nDaowe6oEb9prfSZhyg/SoyJ7klshSdBOsVjqErACxA29VBbyFCNIj/PnRONlI0ABAjQ99UEgGGxqeQ1JSdhW1IAzExpsa0ykNyToDpEU3OlSZzCNtt6oukRFrhQiAd6xTuZczABBgUxaZOY6kcu2oZO4g6mKtIXIkLTBKgcyUnQk6GhvXMlk5qJAmaYylMdYzy/qouNp6OwWRAOXlzqWU30ps4Nh1L2MvqUdgI/mvT+hDDLSQrRLaE6TOwrybDAXr50iSQrWK9RKFBZiM4MHXTTvFFI5Xp7tSf3CcSSgGSZ6xmhDsJAyydzWO+bqTI0kGg/NlO5G5oDsrY044HFHs0g/zFbYBzz7aWshB3BnsNFauAOfoGaCTUK7jYSpxCYElSREdsVSBZIB2zFR96iavLd9HSp68dcEjLB0/wDVULMBhmdyhJ07xNEjPN20Wjax0KRz7Y1pDj0LA0HIiKDpxnAUDEzQA/inXUqOnroaD6+w11ISnNJMmtXQi1a0PPUb70y5SSkJOw0FG+MzbY55QBFFwTmyvUM9u8SmClNWXDT/AN1wO1USQXOkWADE6gbc6i334VjdLgaAj16VM4cWlOC4e26ZIZkJPKVK93Kr7CoqsvPb+6LF8JcsHCtRWqIlUc9xqDURxJbGZtSsh5dntqTdOBpjJBAKgnKNJ1n+qgtqISW1bDY9tCaGkmAp9a1HrE6agieffRIcBWQpptR2nJ9KWlGRaiRCgPbW21S+o5gI7O2rArySVtpXsz0cc0OGKxttBiQ4BHODP8U4GJJOblEa1oQXDMlJ5j/O6qGdKF2s27qkodlCjIStHM8pFSXnHEnqqQABBGaD8qQ9KssaGZ/7peYZ1SMxTvr/ADVESrYsGit5E5SokTIUDWBxSFkqbcIOolB19tRrYwlOgMjQRyqQlfWnVBMyQYqhybo07eNLSYUlMclSI1oEqBh1KhlMhUHvqc2uEQVkjSJVOvqrEIQ9lCmm17DVsSI35VCdLsjs6QTsSRqahYkBlHV2IntqyetWUgkMJGsjKSn+6iO2LbyMpzgxJhw/3ULldUPwhwC3KFbAcv4orhsBSioAwN6FjB0QAh99AEnMkJVP8UKLdTPRocedWpZMaJUAnfU6cv5qApuKpo57HmENqU4EgBIknlXm/FPESrto2qDDc6gV6VxU2Rhbym+qeiPtrxAqLrpKtZNPxq9zyPrOaWJrHHbqBQ2paoSCTV5huFvPZQo5R2b1rDLLMAY511uF4eQpIjfspkpWcrR6Pqdsl4FhbFg2X3soQ2MylObADeoFzer4kvOlCSi2T1Wm+SU/U03iMu3iEWDMlpBl0p/Mrs9nz9VTcFw9uxYCVGVEe6lPizvKLlL2Yr4rn7sm4Y23YISEoGfmDV428t9C5IQDyjnVegJUgEN5OYjlUlMlEAQmYB2oHudfGuhUjG21hZzapJH90TALtyEzKZituv5klIjQbTvQ4Y2S9KiND6xUHqro6G1Shq3AkIMRB51lKubgJIA5axFZQmvaOxzbrLLmmgnnUB2wXCihZkHTnRPMhGy1JE1sFYBh1KyR20048mnyiud+8NK0UNDJnSltXT6SAtGZsxIidKlXDrqARl37DNRFXq0x+Ed9I7aiMktnyVuNWvRqU6kSknTSp2EvC+wh1lXWKCR6wR/Rj30TlwMQQthaCkgSJ51Bwkrwy7U2odRfVNEZqUclrhnF4rZKsrtxCuR0qIkzoa7TjLDsyBcJTqncgb1xUwfVTou0eV1eF6fM12O9wBGThVnTzlrM+2P6o7RkvORWYQR/8bsQTIyqMDxGrPDLbO6kgQZpL5PVYMfVDGvsv6F1hDRaaBAggRVikiNAAmJNaZyobgxA10oFvoLqUyBttzpZ30lBJImtgqCTBg8uytOpIM8ojSkodCQBPm6ds1nTETlMjTX61C2xVwpShlnrDWRUdoLB36o7aa66FqknTt7qBLkKJSkADvqhb23GNOhAECY7tDRocGbzQJ1PI0ouZBqZMeuo7qytQg693bUCb2J0hSgkAGTPaazo8i85Os0q2JJgH19woySlZBOo1mrLq0E4ouFMebJkmjbdSvQknvpIXlCtM0jtrIg6qieyRVFJ0xzjwUBAjltrSlLzQE7x76W4vKTrBnUmti6RlSDqO6pwS7JCHgkAaaaTyG5itrUDpOhGpqveucqCAo7ToND6qBL5nQ8we+oD1lsxmUJKj3af5/hqSpQUCQZHyqNhj4cgbnkO2phQE5gANaFmuFNbEZSgJiI3mZrNEIBBHYP7olylZPPXelOAlZAIyzVEYq4uYCk6RqQajZCme06anvOlOcaBMaa8iK2UdIAAo6D/ADWjQl7htEiB7N4qn4svhbWahJBiNquygoCjsqR/7rj+MHSWzuJGxNUt2Z9TJwwtlHww2XL5kH/ccE++vUFHc7ErMaQK4DglpKcVsypMhLgV641rvbg5EpJAPWzbUczJ6bFrE5AXj7NnbLuLg5Gk9XTUlROgA5k9lWnDXDOMcV4vbNW2H9HcPKS201dwM0nUEHaQI1pXCN1aN+UvgcYgptuyN+4vM75ofDKugJnscKY767Diewcd4gUbWzxdeIotrtWa1cyMobBBSBz6Upy5e4ig2SCy6ifuyhHZKv8AJyXF3B+McCYsrDsbs1Wb2dSEKJ6qiIOWeRAIMEDQgiQQaqGkECRqVE6eyvoXy/P4Kfs4cNrUL1jFxbW7ls3jCkqxAEOW6Wg6QPOJN57Ok7DXgVsArITBJBmd5q2qJo9TLUJqS3QDCUi3ccIAKG1rkA8kmqtbQQWUDklAGv8AxFWzykt4fdlED/xnN1Hmk/WoTet2UmCE7e7Soja+UiLdMlDgIiBO1RelzL3jnE1bXLeZYM8tqqHmwhRMcqiF5F0skG4DpSDqNoqxcJNygSeWk86oUunpBuOUVbdKt26QDyUKjLxyW9i8bPR4UvXqqPWIHKas8OR0bNuhKgAhpsDN4Qf7qhx5wu2aGNQXFADXtNXuWbpwahIVHMbADn6qnYpO8jrtX9xt0+EoZzbqVsO4UClhYCsmTlqK3dMgsJTmKYJO/s/ukOOKbSUqKgRrI7Ko0/Tuzb2pBiddRNJTCbmBqN9RT1Zw2CCFDuFKKRKXIBIPvqwXvuTkdGWtgNZGkTQSAZUqOcUQGZoADKQN+2tgJ3OgmZOulC0NsEqTBTOpMa0CvxlL1ynQeo01bQVlKSROutMbt1BZjWTuO7nVr7krwKaQWV5TsORnSpraCWiQoaxAJ19dR3GiDBAPV5VtDhDapjuM1QxcE1uXETGbXYUIOQqEmZ7KjJuw4BB11BNPQQQZVlnSYqg0ODgWkTp30JUOj7T7poW1JBJJ0I0kVilkpUEkSI1BqEsah0fdnADBIOo5Ul5aEKR5xyNZYBEGTpp2wD76022pYDaYkn+P8ioWIvm3tX3yQA1nJGo0Sn/3tVgN1uznuOMZRh2B3KScyl9RAO+teN2zanXQlIkmrHiHiC4x25KnFktpPVTUrhvDunJcO52rTFdET57q9R/2GqSh9KL3BLEJASRMxJir/GMSGA4fDUKu3Uw0QPN7Vez50vpLbBbIPv6x5qRutXIVRPXwxK4U4+JWo6lJ0A7B3UvlnbtafH0Rfyf8h+FYkGGW0KnMBqTudfnV9b4o2Tlkdm9c2m1t1LAJO+4NWNth6M5CDPKpReGWSKov04k0sEJ01jSiFy0szE9XtqFb2S0SYnXerBjDFKCSqY1BjSaGkdKLnJbofYJRcJVAMzJk1apSi2TA3Eb8qiMlu2hKBtzihU4ZnQ66c6E3wXTHfkctRdUTM67VlaQlbiAAAAffWVA7ZSu3TaNSD3SKBWIsIAGWOZPbTFXDTpSkoM0m5YROZIj10w5j6uzEKvGnCI07qU4ps9bMCJ7Na25aNrjTXtpKrYFEAx7KszyUiC5dKbclOUHkadcoRcMofagGRoOXbQLsEEFRMxyocPItbgt6lLkCOw8jUMqu+mXDJ7qUX2FOJWmVZYJ5ivL7xnoLhaOw16NeOOW5UlJCQd4rhseaCbwxsaZDk5fqkVOCl3R23DtsXsCsSE6ZNx6zNdHh9ulkpPZrqNqoPJ7dB/BEsqB/DWpAPdv/AHXWhsJbme6lS5PRaJRlghP7L+hHvH0tpSABuKrF3hW8FA849lHid2UHaagsqC4PYapBzyfKjoW3SoAjU7amjkZd5INC0AGEK20imwlKYI3AOlCaRBBKiIEmiUnozB7q0o65R3wJoQorTJM9s1CKmadcJ0jtGlJAlZgR66NUAajQawKFKZB9dQq+xKYdS0ZgzFGshS+e1JbSCuDrzidKNSgFbazFQM2RlWdOtM+qkqdKTqZimqUTz2POoi3AFKkAgEcqgLaSNLeMyDI23qOt3Y8xNbfcyyAIqH0hc7pFQyzn2H5i44kk6bDWasra3KkExy01qNbsJCATvPKrJJyJgcqjHY41uwrZAadSQDMSYq0bQoglQ3005VW2686teWk1YBZSpPZHKhe5rx7AXLRT1hr31GyrWdwDy7qlOvEJSO0EbVFDsJCtY7qgbe4ta1JUNdBqaa2nNqZHKlqKulTtrTSQ2lEbRNXuLtWbuVp6MgwD84FefcVPl1xQB2MRXcYirKCRyrz3H1ZljlKquHJzfUH+zot+Dms2JWpGhhR//RNds6yXW0AHX9RM8q47gxUYg2kDXIoyfCa7htILKJ7Yjt0q5cjtCv2Nf72KrEMKRilsbZ8aSFoUkwUqGxFTbPiPiq2VZsN4st9NopKUOr0WhsgkSoEZgCIAMxOkCpJSG1I01J0ioxcyKUBp3jSgHzwwk7fIXFPFmOce3lrc47coWzbqzMW7SSlOaMocWSSVrygAEmEjRIAJlVto6FFWkCBt/wCqTOcHSBG3ZTG+o8oqOYbVdlY8UMKqCMvSDh1yEABXQwSTqJIH90hlQFytUE6Rp86O6WDaOgjdSB/+mmktLJUQfzVC7uV/73Jjx6ZWWJjlVTcMQkkRH871YBRzJ5mTvWrtkJZUZ5E1SYckpIoG2x0wkc+dWFm+lt3rHlz11AqJaguuqEmNaBoy4oHadffRmRPpSaJeKsIuHrBGsruEIATvymp2W5bWFi6Lja1KJK0hShPInnUAvZsUwwATlU46Ae0JMVYM3IebSkgjn6z31QcKcpP/AHgY65dpJJ6J0QZ6sTP9wP8A1Qoebum4U1lc27DtFTGlBZM6jKBttTl2qIC41nedTVGhq+CtXdtsM5FdIDEAEyNBt7aVZuNXK205lyIJAHIDWpN2lC0HMN+yqthwW1zEHL3VaQuXxkk+C9zpSB1p6gjTQmflFbahWYAgkAn6Vpkh1uSOcxWNtpGfQ7f3VD/uSEJIy5UzlJkg78+dCq4OVJ1TCc23KYpSmEpaJBKdZ357UsoUoGFH29lVQadDX3UGfyqOgj3ViSQgBMHSNKAKdyAhSSJghSaUq/WhQKm0EkHUd51qFdaT3HJbMGAcs+6pyE5xKUxyM1CTctrKj0UHtFPZeSFwc3WOo9tQOLQ1skJkQRm91Hl6hBMSYpjTYVlShR0M9Yc6kizKUyqFBM8/85VA+SG3DaVKBgIG/wD1XK8dX6bDhS8k6r/BGvNW/wDddCt8W5LSwpSyqVdaUk77HYV5/wCVZ0jA7FAPVcuFqV3kJgfOiirdHO1+X2tNkmvH/h5i02XXUoG6jFejcN2abOwdddQQhlBcWewDeuJ4csvv2L26CYSFBRrruOcX+426cKt0lHTJDjy+1M6JHtEmtE92kjxXp6jhxT1Eu3BT4hjDuL3BdKMrYENo/SPr20Nvm/KDMc+dRbJs9GNe+rZlQbTETIpZoh1ZH1ye4pJdQQQDBq0w+4eU4mCeQFQhcEr7uyumwS0RBcIBIAI051TOhgh1SpMvGWioJJ0SRtzpyXCrqp741rTKQ+haiAI27akJQGTI9lAj0aVGJQrINgZ9VLDausSTExqdKLpSqI5aCRRxmKZPOqoYmhyWSNCT2isqQqFKBGkCf6rKodsf/9k="
                alt="S. Rahul Kumar Portrait"
                class="w-full h-full object-cover object-top group-hover:scale-105 transition duration-500"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-[#080203] via-transparent to-transparent opacity-60 pointer-events-none"></div>
            </div>
            <div class="bg-[#08080c]/95 border-t border-white/15 px-3 py-2 flex items-center justify-center gap-2">
              <span class="w-2 h-2 rounded-full bg-crimson animate-pulse"></span>
              <span class="font-mono text-[9px] tracking-widest uppercase text-zinc-200 font-semibold">
                S. RAHUL KUMAR: ACTIVE
              </span>
            </div>
          </div>
        </div>

        <!-- Right Column: 3 Stacked Spec Callouts (4 Cols, Matches 00:02 - 00:06) -->
        <div class="lg:col-span-4 space-y-5 pl-1">
          <div data-construct="HERO_CARD_1" class="red-left-accent pl-4 py-1">
            <h2 class="font-bold text-sm sm:text-base text-white">Autonomous Navigation Robot</h2>
            <p class="font-mono text-[11px] text-zinc-400 leading-relaxed mt-1">
              6-Wheel Agricultural Rover • RPi 4 (ROS 2 Jazzy <code class="text-zinc-200">rover_core</code>) • Delta DVP12SE11T PLC • u-blox NEO-M8N GNSS
            </p>
          </div>

          <div data-construct="HERO_CARD_2" class="red-left-accent pl-4 py-1">
            <h2 class="font-bold text-sm sm:text-base text-white">Embedded, PLC &amp; Sensor Systems</h2>
            <p class="font-mono text-[11px] text-zinc-400 leading-relaxed mt-1">
              Arduino Uno • ESP32 • BTS7960 &amp; Orange MG555 Motors • 12.8V 30Ah LiFePO4 • AutoCAD 2025
            </p>
          </div>

          <div data-construct="HERO_CARD_3" class="red-left-accent pl-4 py-1">
            <h2 class="font-bold text-sm sm:text-base text-white">European Automotive &amp; Robotics Ambition</h2>
            <p class="font-mono text-[11px] text-zinc-400 leading-relaxed mt-1">
              ECU &amp; Powertrain Electronics • Intelligent Control Systems • Target: BMW, Bosch &amp; Siemens (Germany)
            </p>
          </div>
        </div>

      </div>

      <div data-construct="SEC_INDEX_01" class="unbuilt mt-12 pt-4 border-t border-white/[0.08] font-mono text-[11px] text-zinc-400 tracking-wider">
        <span>// 01.00 SEC_ABOUT.INDEX [01/05]</span>
      </div>
    </section>

    <!-- =========================================================
         SECTION 1: BACKGROUND & PHILOSOPHY (Matches 00:08 - 00:14)
         ========================================================= -->
    <section id="about" class="max-w-[1240px] mx-auto px-5 sm:px-8 py-14">
      <div data-construct="ABOUT_HDR" class="mb-8">
        <div class="font-mono text-[10px] uppercase tracking-[0.2em] text-crimson font-bold mb-2">
          ENGINEER PROFILE
        </div>
        <h2 class="text-3xl sm:text-5xl font-extrabold tracking-tight text-white">
          Background &amp; Philosophy
        </h2>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-10 items-start">
        <div class="lg:col-span-7 space-y-5 text-zinc-300 text-xs sm:text-[14px] leading-[1.75]">
          <div data-construct="ABOUT_P1">
            <p>
              I am <strong class="text-white font-semibold">S. Rahul Kumar</strong> — an <span class="red-underline">Electronics and Communication Engineering (B.Tech ECE)</span> undergraduate at <span class="red-underline">SRM Institute of Science and Technology, Ramapuram</span> (Academic Batch: <span class="red-underline">2026–2030</span>, Chennai, Tamil Nadu, India; Schooling: <span class="red-underline">Sri Venkateswara Matric. Hr. Sec. School</span>), with a strong interest in robotics, embedded systems, electronics, industrial automation, and automotive technologies.
            </p>
          </div>

          <div data-construct="ABOUT_P2">
            <p>
              I enjoy exploring the integration of hardware and software to develop practical engineering solutions across <strong class="text-white">Arduino Uno, ESP32, Raspberry Pi 4 (4GB), Python, C++, ROS 2 Jazzy, Delta DVP12SE11T PLC, u-blox NEO-M8N GNSS</strong>, and <strong class="text-white">AutoCAD 2025</strong>. My primary engineering project is an <strong class="text-white">Autonomous Navigation Robot</strong> designed for agricultural surveillance and monitoring, and my long-term ambition is to pursue engineering opportunities in Germany with <span class="red-underline">BMW, Bosch, and Siemens</span>.
            </p>
          </div>

          <div data-construct="ABOUT_QUOTE" class="p-5 bg-[#0b0b10] border border-white/[0.06] red-left-accent rounded-r">
            <p class="italic text-white font-medium text-xs sm:text-sm leading-relaxed">
              "Career Objective: To develop into a skilled embedded systems and robotics engineer and contribute to innovative technologies in the automotive, automation and intelligent systems industries — Building intelligent systems through engineering."
            </p>
          </div>
        </div>

        <div class="lg:col-span-5 space-y-3.5">
          <div data-construct="PHIL_1" class="arch-card p-4 rounded-lg flex items-start gap-3.5">
            <div class="w-8 h-8 rounded bg-crimson/15 border border-crimson/40 flex items-center justify-center text-crimson shrink-0 mt-0.5 font-mono text-xs font-bold">
              01
            </div>
            <div>
              <h3 class="font-bold text-sm text-white mb-1">10 Core Career Interests &amp; Germany Ambition</h3>
              <p class="text-xs text-zinc-400 leading-relaxed">
                Embedded Systems • Robotics &amp; Autonomous Systems • Industrial Automation • Automotive Electronics &amp; Embedded • ECUs • IoT • Intelligent Control • Autonomous Vehicles • Powertrain Electronics (Target: BMW, Bosch, Siemens in Germany).
              </p>
            </div>
          </div>

          <div data-construct="PHIL_2" class="arch-card p-4 rounded-lg flex items-start gap-3.5">
            <div class="w-8 h-8 rounded bg-crimson/15 border border-crimson/40 flex items-center justify-center text-crimson shrink-0 mt-0.5 font-mono text-xs font-bold">
              02
            </div>
            <div>
              <h3 class="font-bold text-sm text-white mb-1">Achievement: Rajyapuraskar Certificate</h3>
              <p class="text-xs text-zinc-400 leading-relaxed">
                Received the <strong class="text-zinc-200">Rajyapuraskar Certificate in Scouts and Guides</strong>, representing a formal recognition in a structured scouting programme alongside practical robotics and embedded engineering experimentation.
              </p>
            </div>
          </div>

          <div data-construct="PHIL_3" class="arch-card p-4 rounded-lg flex items-start gap-3.5">
            <div class="w-8 h-8 rounded bg-crimson/15 border border-crimson/40 flex items-center justify-center text-crimson shrink-0 mt-0.5 font-mono text-xs font-bold">
              03
            </div>
            <div>
              <h3 class="font-bold text-sm text-white mb-1">Experience, Certifications &amp; 12 Learning Tracks</h3>
              <p class="text-xs text-zinc-400 leading-relaxed">
                Hands-on experience via personal robotics, RPi 4, ROS 2, and PLC projects (no internships/employment or course certifications reported yet). Actively learning Python, C++, ROS 2, Linux, MQTT/IoT, Node-RED, PLC/SCADA, ECU systems, and German.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- =========================================================
         SECTION 2: FLAGSHIP DEPLOYMENTS (Matches 00:15 - 00:35)
         ========================================================= -->
    <section id="flagships" class="max-w-[1240px] mx-auto px-5 sm:px-8 py-14">
      <div data-construct="FLAGSHIP_HDR" class="mb-8">
        <div class="font-mono text-[10px] uppercase tracking-[0.2em] text-crimson font-bold mb-2">
          ARCHITECTURAL DOSSIER
        </div>
        <h2 class="text-3xl sm:text-5xl font-extrabold tracking-tight text-white">
          Flagship Deployments
        </h2>
        <p class="text-zinc-400 text-xs sm:text-sm mt-2 max-w-2xl">
          Multidisciplinary robotics, industrial automation, and embedded control systems spanning Raspberry Pi 4, ROS 2 Jazzy, Delta PLC, and Arduino.
        </p>
      </div>

      <!-- MAIN FLAGSHIP BOX (Each internal block is opened individually by the cursors!) -->
      <div id="flagshipMainCard" class="arch-card rounded-xl p-6 sm:p-8 mb-6 border border-white/10">
        <div data-construct="FLAGSHIP_ABSTRACT" class="unbuilt">
          <div class="mb-4 flex items-center justify-between">
            <span class="inline-flex items-center gap-1.5 px-2.5 py-1 rounded bg-crimson/15 border border-crimson/40 font-mono text-[9px] uppercase tracking-widest text-crimson font-bold">
              ● STATUS: SOFTWARE DEVELOPMENT AND TESTING
            </span>
            <span class="font-mono text-[10px] text-crimson">● AUTO-AGENT TAB INSPECTION ACTIVE</span>
          </div>

          <h3 class="text-xl sm:text-3xl font-extrabold text-white tracking-tight mb-2.5">
            FEATURED PROJECT — Autonomous Navigation Robot (Agricultural Surveillance) <span class="text-zinc-500 font-normal">↗</span>
          </h3>
          <p class="text-zinc-400 text-xs sm:text-sm leading-relaxed max-w-3xl mb-6">
            A six-wheel differential-drive agricultural surveillance and monitoring rover (30 kg including 10L water tank, 2–3 acres coverage) combining <strong class="text-zinc-200">Raspberry Pi 4 (4GB, Ubuntu 24.04.5 LTS, ROS 2 Jazzy)</strong>, <strong class="text-zinc-200">Delta DVP12SE11T PLC</strong> safety supervision, <strong class="text-zinc-200">u-blox NEO-M8N GNSS</strong> positioning, <strong class="text-zinc-200">BTS7960</strong> motor drivers, and <strong class="text-zinc-200">Orange MG555 (12V, 100RPM)</strong> motors powered by a <strong class="text-zinc-200">12.8V, 30Ah LiFePO4</strong> battery.
          </p>
        </div>

        <div class="grid grid-cols-2 sm:grid-cols-4 gap-4 py-5 border-y border-white/[0.08] mb-6 text-center">
          <div data-construct="ROVER_METRIC_1" class="unbuilt">
            <div class="font-sans text-xl sm:text-2xl font-black text-crimson">30 kg</div>
            <div class="font-mono text-[9px] text-zinc-500 uppercase tracking-widest mt-0.5">6× 7" WHEELS • 10L TANK</div>
          </div>
          <div data-construct="ROVER_METRIC_2" class="unbuilt">
            <div class="font-sans text-xl sm:text-2xl font-black text-crimson">3 Modes</div>
            <div class="font-mono text-[9px] text-zinc-500 uppercase tracking-widest mt-0.5">MANUAL • ASSISTED • AUTO</div>
          </div>
          <div data-construct="ROVER_METRIC_3" class="unbuilt">
            <div class="font-sans text-xl sm:text-2xl font-black text-crimson">NEO-M8N</div>
            <div class="font-mono text-[9px] text-zinc-500 uppercase tracking-widest mt-0.5">1 Hz /gps/fix • 10 SATS</div>
          </div>
          <div data-construct="ROVER_METRIC_4" class="unbuilt">
            <div class="font-sans text-xl sm:text-2xl font-black text-crimson">rover_core</div>
            <div class="font-mono text-[9px] text-zinc-500 uppercase tracking-widest mt-0.5">ROS 2 JAZZY • COLCON</div>
          </div>
        </div>

        <div>
          <div data-construct="ROVER_STACK_TABS" class="unbuilt">
            <div class="font-mono text-[10px] uppercase tracking-widest text-zinc-400 font-bold mb-3">
              7-LAYER ROVER ARCHITECTURAL STACK
            </div>
            <!-- 7 Layer Buttons -->
            <div id="layerTabs" class="flex flex-wrap gap-2 mb-4"></div>
          </div>

          <!-- Active Layer Box -->
          <div id="layerDetailBox" data-construct="LAYER_PANEL" class="unbuilt p-5 rounded-lg bg-[#07070a] border border-white/[0.08] red-left-accent"></div>
        </div>
      </div>

      <!-- 3 SUB-FLAGSHIP CARDS: SECTION 7 OTHER TECHNICAL PROJECT CATEGORIES & SECTION 16 ROADMAP -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-5">
        <div data-construct="TIER_1_ARM" class="arch-card rounded-xl p-5 flex flex-col justify-between">
          <div>
            <div class="font-mono text-[9px] uppercase tracking-widest text-crimson font-bold mb-2">
              CATEGORY 01 // EMBEDDED &amp; MICROCONTROLLERS
            </div>
            <h4 class="text-base sm:text-lg font-extrabold text-white mb-2">
              Arduino, ESP32 &amp; Raspberry Pi Applications <span class="text-zinc-500 font-normal">↗</span>
            </h4>
            <p class="text-xs text-zinc-400 leading-relaxed mb-4">
              Practical microcontroller experiments, sensor interfacing, motor control, and embedded Linux applications documented with objectives, circuit diagrams, source code, and test results.
            </p>
            <ul class="space-y-1.5 font-mono text-[11px] text-zinc-300 mb-5">
              <li><span class="text-crimson">•</span> Arduino Uno &amp; ESP32 Experiments</li>
              <li><span class="text-crimson">•</span> Raspberry Pi 4 Embedded Applications</li>
              <li><span class="text-crimson">•</span> Sensor Interfacing &amp; BTS7960 Control</li>
            </ul>
          </div>
          <div class="pt-3 border-t border-white/[0.07] flex flex-wrap items-center gap-3 font-mono text-[10px] text-zinc-400">
            <span>Arduino Uno</span>
            <span>ESP32</span>
            <span>Raspberry Pi 4</span>
          </div>
        </div>

        <div data-construct="TIER_2_IRRIG" class="arch-card rounded-xl p-5 flex flex-col justify-between">
          <div>
            <div class="font-mono text-[9px] uppercase tracking-widest text-crimson font-bold mb-2">
              CATEGORY 02 // INDUSTRIAL &amp; AUTOMOTIVE
            </div>
            <h4 class="text-base sm:text-lg font-extrabold text-white mb-2">
              Delta PLC Automation, Circuits &amp; ECU Learning <span class="text-zinc-500 font-normal">↗</span>
            </h4>
            <p class="text-xs text-zinc-400 leading-relaxed mb-4">
              Industrial automation using Delta DVP12SE11T PLC and HMI, electronic circuit and TPA3255 amplifier design, and automotive electronics / ECU and powertrain learning.
            </p>
            <ul class="space-y-1.5 font-mono text-[11px] text-zinc-300 mb-5">
              <li><span class="text-crimson">•</span> Industrial Automation via Delta PLC</li>
              <li><span class="text-crimson">•</span> Electronic Circuit &amp; Amplifier Design</li>
              <li><span class="text-crimson">•</span> Automotive Electronics &amp; ECU Systems</li>
            </ul>
          </div>
          <div class="pt-3 border-t border-white/[0.07] flex flex-wrap items-center gap-3 font-mono text-[10px] text-zinc-400">
            <span>Delta DVP12SE11T</span>
            <span>TPA3255</span>
            <span>Automotive ECU</span>
          </div>
        </div>

        <div data-construct="TIER_3_TURRET" class="arch-card rounded-xl p-5 flex flex-col justify-between">
          <div>
            <div class="font-mono text-[9px] uppercase tracking-widest text-crimson font-bold mb-2">
              CATEGORY 03 // ROBOTICS &amp; PORTFOLIO ROADMAP
            </div>
            <h4 class="text-base sm:text-lg font-extrabold text-white mb-2">
              ROS 2 Software Experiments &amp; Future Deliverables <span class="text-zinc-500 font-normal">↗</span>
            </h4>
            <p class="text-xs text-zinc-400 leading-relaxed mb-4">
              Ongoing ROS 2 Jazzy software experiments and planned portfolio deliverables including mechanical CAD drawings, circuit diagrams, GitHub repositories, demo videos, and downloadable PDF resume.
            </p>
            <ul class="space-y-1.5 font-mono text-[11px] text-zinc-300 mb-5">
              <li><span class="text-crimson">•</span> ROS 2 Jazzy &amp; Nav2 Experiments</li>
              <li><span class="text-crimson">•</span> AutoCAD 2025 &amp; Circuit Schematics</li>
              <li><span class="text-crimson">•</span> GitHub Repos &amp; Testing Reports</li>
            </ul>
          </div>
          <div class="pt-3 border-t border-white/[0.07] flex flex-wrap items-center gap-3 font-mono text-[10px] text-zinc-400">
            <span>ROS 2 Jazzy</span>
            <span>AutoCAD 2025</span>
            <span>GitHub Repos</span>
          </div>
        </div>
      </div>
    </section>

    <!-- =========================================================
         SECTION 3: THE SYSTEMS MATRIX (Matches 00:36 - 00:46)
         ========================================================= -->
    <section id="matrix" class="max-w-[1240px] mx-auto px-5 sm:px-8 py-14">
      <div data-construct="MATRIX_HDR" class="mb-6">
        <div class="font-mono text-[10px] uppercase tracking-[0.2em] text-crimson font-bold mb-2">
          ENGINEERING INDEX
        </div>
        <h2 class="text-3xl sm:text-5xl font-extrabold tracking-tight text-white">
          The Systems Matrix
        </h2>
        <p class="text-zinc-400 text-xs sm:text-sm mt-2 max-w-2xl">
          Specialized architectures, documented accomplishments, hardware inventory, and research domains spanning ROS 2, Delta PLC, embedded systems, and automotive ECU engineering.
        </p>
      </div>

      <!-- Filter Pills Row -->
      <div id="matrixFilterBar" data-construct="MATRIX_FILTERS" class="flex flex-wrap gap-2 mb-8"></div>

      <!-- 3-Column Matrix Grid -->
      <div id="matrixCardsContainer" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5"></div>
    </section>

    <!-- =========================================================
         SECTION 4: DIRECT CHANNEL / FOOTER (Matches 00:47 - 00:56)
         ========================================================= -->
    <section id="contact" class="max-w-[900px] mx-auto px-5 sm:px-8 pt-20 pb-14 text-center">
      <div data-construct="CONTACT_HEADER_BLOCK">
      <div class="font-mono text-[10px] uppercase tracking-[0.25em] text-crimson font-bold mb-3">
        DIRECT CHANNEL
      </div>
      <h2 class="text-3xl sm:text-5xl font-extrabold tracking-tight text-white leading-tight mb-4">
        Let's Architect Something<br />Extraordinary.
      </h2>
      <p class="text-zinc-400 text-xs sm:text-sm max-w-lg mx-auto mb-8 leading-relaxed">
        Available for embedded systems engineering, ROS 2 autonomous robotics, industrial PLC automation, and automotive electronics collaborations in Chennai, Tamil Nadu, India.
      </p>
      </div>

      <div data-construct="CONTACT_CTA" class="inline-flex flex-col sm:flex-row items-center gap-2 p-2 rounded-lg bg-[#0c0c12] border border-white/10 shadow-2xl mb-8">
        <span class="px-4 py-2 font-mono text-xs sm:text-sm text-zinc-200 select-all">
          rahulkumar.rk2958454@gmail.com
        </span>
        <button id="initiateTransmissionBtn" type="button" class="w-full sm:w-auto px-5 py-2.5 rounded bg-crimson hover:bg-red-600 text-white font-mono text-[11px] font-bold uppercase tracking-widest transition shadow-[0_0_25px_rgba(255,30,30,0.4)]">
          ⚡ INITIATE TRANSMISSION
        </button>
      </div>

      <div data-construct="CONTACT_LINKS" class="unbuilt grid grid-cols-1 sm:grid-cols-3 gap-4 max-w-4xl mx-auto mb-12 text-left">
        <!-- Bold Unique LinkedIn Command Card -->
        <a href="https://www.linkedin.com/in/rahul-kumar-715b32423" target="_blank" rel="noopener noreferrer" class="cyber-social-card rounded-xl p-4 pl-5 flex items-center justify-between group">
          <div class="flex items-center gap-3.5">
            <div class="w-10 h-10 rounded-lg bg-crimson/20 border border-crimson/50 flex items-center justify-center text-white font-sans font-black text-base shadow-[0_0_15px_rgba(255,30,30,0.35)] group-hover:bg-crimson transition">
              in
            </div>
            <div>
              <div class="font-mono text-[9px] uppercase tracking-widest text-crimson font-bold">PROFESSIONAL NETWORK</div>
              <div class="font-sans text-sm sm:text-base font-black text-white tracking-tight group-hover:text-crimson transition">LinkedIn Profile</div>
              <div class="font-mono text-[10px] text-zinc-300 font-semibold">rahul-kumar-715b32423</div>
            </div>
          </div>
          <span class="font-mono text-lg font-black text-crimson group-hover:translate-x-1 group-hover:-translate-y-1 transition transform">↗</span>
        </a>

        <!-- Bold Unique GitHub Command Card -->
        <a href="https://github.com/Rahulkumar2k8" target="_blank" rel="noopener noreferrer" class="cyber-social-card rounded-xl p-4 pl-5 flex items-center justify-between group">
          <div class="flex items-center gap-3.5">
            <div class="w-10 h-10 rounded-lg bg-crimson/20 border border-crimson/50 flex items-center justify-center text-white font-mono font-black text-xs shadow-[0_0_15px_rgba(255,30,30,0.35)] group-hover:bg-crimson transition">
              &lt;/&gt;
            </div>
            <div>
              <div class="font-mono text-[9px] uppercase tracking-widest text-crimson font-bold">CODE REPOSITORIES</div>
              <div class="font-sans text-sm sm:text-base font-black text-white tracking-tight group-hover:text-crimson transition">GitHub Portfolio</div>
              <div class="font-mono text-[10px] text-zinc-300 font-semibold">github.com/Rahulkumar2k8</div>
            </div>
          </div>
          <span class="font-mono text-lg font-black text-crimson group-hover:translate-x-1 group-hover:-translate-y-1 transition transform">↗</span>
        </a>

        <!-- Bold Unique Institution Command Card -->
        <a href="#about" class="cyber-social-card rounded-xl p-4 pl-5 flex items-center justify-between group">
          <div class="flex items-center gap-3.5">
            <div class="w-10 h-10 rounded-lg bg-crimson/20 border border-crimson/50 flex items-center justify-center text-white font-mono font-black text-xs shadow-[0_0_15px_rgba(255,30,30,0.35)] group-hover:bg-crimson transition">
              ECE
            </div>
            <div>
              <div class="font-mono text-[9px] uppercase tracking-widest text-crimson font-bold">ACADEMIC INSTITUTION</div>
              <div class="font-sans text-sm sm:text-base font-black text-white tracking-tight group-hover:text-crimson transition">SRMIST Ramapuram</div>
              <div class="font-mono text-[10px] text-zinc-300 font-semibold">B.Tech ECE (2026–2030)</div>
            </div>
          </div>
          <span class="font-mono text-lg font-black text-crimson group-hover:translate-y-0.5 transition transform">↑</span>
        </a>
      </div>

      <div data-construct="CONTACT_COPYRIGHT" class="unbuilt pt-6 border-t border-white/[0.06] font-mono text-[10px] text-zinc-400">
        <span>S. RAHUL KUMAR — Electronics &amp; Communication Engineering // Building intelligent systems through engineering.</span>
      </div>
    </section>

  </main>

  <div id="copyToast" class="fixed bottom-5 right-5 z-50 hidden px-4 py-2.5 rounded bg-zinc-900 border border-crimson text-white font-mono text-xs shadow-2xl">
    Copied contact &amp; engineering database details to clipboard!
  </div>

  <script>
    // =========================================================================
    // 1. 7-LAYER ROVER STACK DATA & RENDERER
    // =========================================================================
    const roverLayers = [
      {
        id: 'L1',
        tab: 'L1: ROS 2 & CLI',
        eyebrow: 'SECTION 6.5 & 6.6 // ROS 2 JAZZY IMPLEMENTATION & CLI COMMANDS',
        title: 'Nodes (/rover_mode_node, /rover_status_node) & NavSatFix GPS',
        desc: 'Built rover_core on Ubuntu 24.04.5 LTS via "colcon build --packages-select rover_core" and "ros2 run rover_core rover_status_node". Tested topics /gps/fix, /gps/satellites, /parameter_events, /rosout, and /rover/mode_command using "ros2 node list", "ros2 topic list", "ros2 topic echo /gps/fix --once", and "ros2 topic hz /gps/fix".',
        pills: ['Msg: sensor_msgs/msg/NavSatFix', 'Frame ID: gps_link @ ~1 Hz (10 Sats)', 'Outputs: ROVER ONLINE – MANUAL / ASSISTED / AUTONOMOUS']
      },
      {
        id: 'L2',
        tab: 'L2: 3 Operating Modes',
        eyebrow: 'SECTION 6.7 // ROBOT OPERATING MODES',
        title: 'Manual Mode, Assisted Mode & Automatic Response Mode',
        desc: '(1) Manual Mode: Direct operator control using FlySky FS-i6S RC transmitter and receiver. (2) Assisted Mode: Operator-controlled movement with planned safety and obstacle-response assistance. (3) Automatic Response Mode: Sensor-triggered automatic responses, alerts, and irrigation functions.',
        pills: ['ROVER ONLINE – MANUAL MODE', 'ROVER ONLINE – ASSISTED MODE', 'ROVER ONLINE – AUTONOMOUS']
      },
      {
        id: 'L3',
        tab: 'L3: Control & PLC',
        eyebrow: 'SECTION 6.8 // SYSTEM CONTROL ARCHITECTURE',
        title: 'Raspberry Pi 4 (4GB) Processing + Delta DVP12SE11T PLC Supervision',
        desc: 'The Raspberry Pi 4 (4GB) handles higher-level robotics processing, navigation software, camera processing, and ROS 2 communication. The Delta DVP12SE11T PLC is intended to supervise hardwired emergency stops, safety interlocks, sensor faults, and watchdog functions.',
        pills: ['Main Computer: RPi 4 (4GB)', 'PLC: Delta DVP12SE11T', 'OS: Ubuntu 24.04.5 LTS + SSH']
      },
      {
        id: 'L4',
        tab: 'L4: Mechanical Specs',
        eyebrow: 'SECTION 6.2 & 6.3 // MECHANICAL SPECIFICATIONS & OBJECTIVES',
        title: 'Six-Wheel Differential Drive (7" Wheels, 30 kg w/ 10L Water Tank)',
        desc: 'Six-wheel differential-steering mobile rover powered by six Orange MG555 (12V, 100RPM) DC motors with 7-inch wheels. Total weight specification is 30 kg including a 10-litre water tank, designed for agricultural surveillance across 2–3 acres.',
        pills: ['6 Wheels (7 Inches)', 'Weight: 30 kg w/ 10L Tank', 'Coverage: 2–3 Acres']
      },
      {
        id: 'L5',
        tab: 'L5: Electrical & Power',
        eyebrow: 'SECTION 6.4 // ELECTRICAL & ELECTRONIC SPECIFICATIONS',
        title: '12.8V 30Ah LiFePO4 Battery, BTS7960 Drivers & Ultrasonic Sensors',
        desc: 'Powered by a 12.8V, 30Ah LiFePO4 battery driving six Orange MG555 (12V, 100RPM) motors through BTS7960 motor drivers, integrated with ultrasonic obstacle sensors and FlySky FS-i6S remote control.',
        pills: ['Battery: 12.8V 30Ah LiFePO4', 'Driver: BTS7960', 'Motors: 6× Orange MG555 12V 100RPM']
      },
      {
        id: 'L6',
        tab: 'L6: NEO-M8N & Comms',
        eyebrow: 'SECTION 6.9 // NAVIGATION AND COMMUNICATION',
        title: 'u-blox NEO-M8N GNSS Positioning, SIM Connectivity & LoRa',
        desc: 'Uses a u-blox NEO-M8N GNSS module streaming position data to the Raspberry Pi 4 (~1 Hz, 10 satellites recorded), paired with a Google Maps route/waypoint concept via a mounted Android phone, SIM-based connectivity, and LoRa under consideration.',
        pills: ['GNSS: u-blox NEO-M8N', 'Comms: SIM-Based Connectivity', 'Long-Range: LoRa Under Consideration']
      },
      {
        id: 'L7',
        tab: 'L7: Future & Status',
        eyebrow: 'SECTION 6.10 & 6.11 // FUTURE DEVELOPMENT & STATUS NOTE',
        title: 'Nav2, Waypoints, AI Object Detection & Field Validation Roadmap',
        desc: 'Future development: GPS waypoint navigation, ROS 2 Nav2 integration, obstacle avoidance, camera surveillance, AI-assisted object detection, automated irrigation, and remote dashboard. Note: Currently in software development and testing; complete physical autonomous navigation and field performance have not yet been verified.',
        pills: ['Status: Software Dev & Testing', 'Next: ROS 2 Nav2 & Waypoints', 'Planned: AI Vision & Field Testing']
      }
    ];

    let activeLayerIdx = 0;
    const layerTabsEl = document.getElementById('layerTabs');
    const layerDetailEl = document.getElementById('layerDetailBox');

    function renderLayers(triggerWireframe = false) {
      layerTabsEl.innerHTML = '';
      roverLayers.forEach((l, idx) => {
        const active = idx === activeLayerIdx;
        const btn = document.createElement('button');
        btn.type = 'button';
        btn.setAttribute('data-layer-btn', idx);
        btn.className = active
          ? 'px-3 py-1.5 rounded font-mono text-[10px] font-bold bg-crimson text-white shadow-[0_0_15px_rgba(255,30,30,0.4)] transition'
          : 'px-3 py-1.5 rounded font-mono text-[10px] text-zinc-400 bg-[#0d0d12] hover:text-white border border-white/10 transition';
        btn.textContent = l.tab;
        btn.addEventListener('click', () => {
          activeLayerIdx = idx;
          renderLayers(true);
        });
        layerTabsEl.appendChild(btn);
      });

      const curr = roverLayers[activeLayerIdx];
      layerDetailEl.innerHTML = `
        <div class="wireframe-overlay">
          <span class="wf-corner wf-tl"></span><span class="wf-corner wf-tr"></span>
          <span class="wf-corner wf-bl"></span><span class="wf-corner wf-br"></span>
          <span class="wf-tag">TAB_OPEN // ${curr.id}</span>
          <div class="wf-progress"><div class="wf-progress-bar"></div></div>
        </div>
        <div class="font-mono text-[9px] uppercase tracking-widest text-crimson font-bold mb-1">${curr.eyebrow}</div>
        <h4 class="text-base sm:text-lg font-bold text-white mb-1.5">${curr.title}</h4>
        <p class="text-xs text-zinc-400 leading-relaxed mb-3.5">${curr.desc}</p>
        <div class="flex flex-wrap gap-2">
          ${curr.pills.map(p => `<span class="px-2.5 py-1 rounded bg-zinc-900 border border-white/10 font-mono text-[10px] text-zinc-200">${p}</span>`).join('')}
        </div>
      `;

      if (triggerWireframe) {
        triggerConstructAnimation(layerDetailEl, 420);
      }
    }

    // =========================================================================
    // 2. THE SYSTEMS MATRIX DATA & RENDERER
    // =========================================================================
    const matrixData = [
      {
        code: 'SEC // 04.1',
        cat: 'Robotics & ROS 2',
        title: 'ROS 2 Jazzy & rover_core Implementation',
        desc: 'Nodes: /rover_mode_node & /rover_status_node. Topics: /gps/fix (sensor_msgs/msg/NavSatFix, frame gps_link, ~1 Hz), /gps/satellites (10 sats), /parameter_events, /rosout, and /rover/mode_command.',
        tags: ['ROS 2 Jazzy', 'Colcon', 'NavSatFix', 'gps_link']
      },
      {
        code: 'SEC // 05.1',
        cat: 'Robotics & ROS 2',
        title: 'u-blox NEO-M8N GNSS & Mobile Robotics',
        desc: 'NEO-M8N GNSS module streaming position to Raspberry Pi 4 (4GB), differential drive kinematics, ultrasonic obstacle sensors, and FlySky FS-i6S RC transmitter.',
        tags: ['u-blox NEO-M8N', 'Ultrasonic', 'FlySky FS-i6S', 'Differential Drive']
      },
      {
        code: 'SEC // 06.10',
        cat: 'Robotics & ROS 2',
        title: 'Future Rover Roadmap & Nav2 Integration',
        desc: 'Planned upgrades: GPS waypoint navigation, ROS 2 Nav2 integration, obstacle avoidance, camera surveillance, AI object detection, automated irrigation, and field testing.',
        tags: ['ROS 2 Nav2', 'AI Object Detection', 'Waypoints', 'Field Testing']
      },
      {
        code: 'SEC // 04.2',
        cat: 'Embedded & IoT',
        title: 'Arduino Uno, ESP32 & Raspberry Pi 4 (4GB)',
        desc: 'Microcontroller programming, sensor interfacing, hardware-software integration, Python (basic knowledge), and C++ (learning and development).',
        tags: ['Arduino Uno', 'ESP32', 'Raspberry Pi 4', 'Python & C++']
      },
      {
        code: 'SEC // 04.6',
        cat: 'Embedded & IoT',
        title: 'SIM Connectivity, MQTT & LoRa Communication',
        desc: 'SIM-based connectivity for remote rover communication, MQTT (learning interest), Node-RED, LoRa (under consideration), and wireless remote monitoring concepts.',
        tags: ['SIM Connectivity', 'MQTT', 'LoRa', 'Node-RED']
      },
      {
        code: 'SEC // 05.2',
        cat: 'Embedded & IoT',
        title: 'Actuators & Audio Power Electronics',
        desc: 'Additional components explored: NEMA17 stepper motor, DS5160 high-torque servo, TPA3255 amplifier board, amplifier circuits, and electronic sensor modules.',
        tags: ['NEMA17 Stepper', 'DS5160 Servo', 'TPA3255 Amp', 'Circuits']
      },
      {
        code: 'SEC // 04.4',
        cat: 'PLC & Power',
        title: 'Delta DVP12SE11T PLC & HMI Automation',
        desc: 'Industrial control concepts, PLC safety supervision (hardwired E-stop, safety interlocks, sensor faults, watchdog), HMI, and SCADA learning.',
        tags: ['Delta DVP12SE11T', 'HMI & SCADA', 'Safety Interlocks', 'Watchdog']
      },
      {
        code: 'SEC // 06.4',
        cat: 'PLC & Power',
        title: '12.8V 30Ah LiFePO4, BTS7960 & MG555 Drive',
        desc: 'Six Orange MG555 (12V, 100RPM) DC motors driven by BTS7960 motor drivers and powered by a 12.8V, 30Ah LiFePO4 battery pack for the 30 kg (10L tank) rover.',
        tags: ['12.8V 30Ah LiFePO4', 'BTS7960', 'Orange MG555', '30 kg / 10L']
      },
      {
        code: 'SEC // 03.1',
        cat: 'Automotive & CAD',
        title: 'Automotive Electronics, ECUs & Germany Goal',
        desc: 'Focused on Automotive Embedded Engineering, Electronic Control Units (ECU), Powertrain Electronics, Autonomous Vehicles, and German language toward BMW, Bosch, and Siemens.',
        tags: ['BMW • Bosch • Siemens', 'ECU & Powertrain', 'Germany', 'German Language']
      },
      {
        code: 'SEC // 08.1',
        cat: 'Automotive & CAD',
        title: 'AutoCAD 2025 & Engineering Development Stack',
        desc: 'Ubuntu 24.04.5 LTS, Windows 11, ROS 2 Jazzy, Colcon, Linux Terminal, SSH remote access, AutoCAD 2025 engineering drawings, and GitHub (Rahulkumar2k8).',
        tags: ['AutoCAD 2025', 'Ubuntu 24.04.5', 'Windows 11', 'GitHub']
      },
      {
        code: 'SEC // 09.1',
        cat: 'AI & Workstation',
        title: 'Rajyapuraskar Certificate & Practical Experience',
        desc: 'Received the Rajyapuraskar Certificate in Scouts and Guides. Practical experience built through personal robotics, RPi 4, ROS 2, PLC, and hardware experimentation.',
        tags: ['Rajyapuraskar Award', 'Scouts & Guides', 'Practical Projects']
      },
      {
        code: 'SEC // 16.1',
        cat: 'AI & Workstation',
        title: 'Future Portfolio Deliverables & Documentation',
        desc: 'Planned additions: project photos, CAD drawings, circuit & architecture diagrams, ROS 2 GitHub repos, demo videos, test reports, and downloadable resume/portfolio PDFs.',
        tags: ['CAD & Schematics', 'GitHub Repos', 'Demo Videos', 'Resume PDF']
      }
    ];

    const matrixCategories = [
      'All Systems',
      'Robotics & ROS 2',
      'Embedded & IoT',
      'PLC & Power',
      'Automotive & CAD',
      'AI & Workstation'
    ];
    let currentMatrixCat = 'All Systems';
    const filterBarEl = document.getElementById('matrixFilterBar');
    const matrixGridEl = document.getElementById('matrixCardsContainer');

    function renderMatrix(animateCards = false) {
      filterBarEl.innerHTML = '';
      matrixCategories.forEach((cat, idx) => {
        const count = cat === 'All Systems'
          ? matrixData.length
          : matrixData.filter(m => m.cat === cat).length;
        const active = cat === currentMatrixCat;
        const btn = document.createElement('button');
        btn.type = 'button';
        btn.setAttribute('data-matrix-btn', idx);
        btn.className = active
          ? 'px-3.5 py-1.5 rounded font-mono text-[10px] font-bold bg-crimson text-white shadow-[0_0_15px_rgba(255,30,30,0.35)] transition'
          : 'px-3.5 py-1.5 rounded font-mono text-[10px] text-zinc-400 bg-[#0c0c12] hover:text-white border border-white/10 transition';
        btn.textContent = `${cat} (${count})`;
        btn.addEventListener('click', () => {
          currentMatrixCat = cat;
          renderMatrix(true);
        });
        filterBarEl.appendChild(btn);
      });

      const items = currentMatrixCat === 'All Systems'
        ? matrixData
        : matrixData.filter(m => m.cat === currentMatrixCat);

      matrixGridEl.innerHTML = items.map((item, i) => `
        <div data-construct="MATRIX_CARD_${i}" class="arch-card rounded-xl p-5 flex flex-col justify-between ${animateCards ? 'building' : 'unbuilt'}">
          <div class="wireframe-overlay">
            <span class="wf-corner wf-tl"></span><span class="wf-corner wf-tr"></span>
            <span class="wf-corner wf-bl"></span><span class="wf-corner wf-br"></span>
            <span class="wf-tag">${item.code} // BUILD</span>
            <div class="wf-progress"><div class="wf-progress-bar"></div></div>
          </div>
          <div>
            <div class="flex items-center justify-between font-mono text-[9px] uppercase tracking-widest mb-3">
              <span class="text-crimson font-bold">${item.cat}</span>
              <span class="text-zinc-500">${item.code}</span>
            </div>
            <h3 class="text-base font-extrabold text-white mb-2">${item.title}</h3>
            <p class="text-xs text-zinc-400 leading-relaxed mb-5">${item.desc}</p>
          </div>
          <div class="pt-3 border-t border-white/[0.06] flex flex-wrap gap-2 font-mono text-[10px] text-zinc-300">
            ${item.tags.map(t => `<span class="px-2 py-0.5 rounded bg-zinc-900/90 border border-white/[0.07]">${t}</span>`).join('')}
          </div>
        </div>
      `).join('');

      if (animateCards) {
        matrixGridEl.querySelectorAll('[data-construct]').forEach((el, idx) => {
          triggerConstructAnimation(el, 480, idx * 140);
        });
      } else if (typeof bootPhase !== 'undefined' && !bootPhase) {
        observeConstructElements();
      }
    }

    // =========================================================================
    // 3. CURSOR-FIRST DRAG-TO-OPEN ENGINE (Content Opens ONLY After Cursor Drags Box)
    // =========================================================================
    const buildQueue = []; // Active cursor-drag jobs: { el, agentIdx, phase: 'APPROACH' | 'DRAG', startTime, dragDuration }

    function injectWireframeOverlays() {
      document.querySelectorAll('[data-construct]').forEach((el) => {
        const tag = el.getAttribute('data-construct') || 'NODE';
        if (tag.startsWith('ABOUT_P') || tag === 'HERO_BIO') {
          el.classList.add('text-typing-mode');
        }
        if (!el.querySelector('.wireframe-overlay')) {
          const ov = document.createElement('div');
          ov.className = 'wireframe-overlay';
          ov.innerHTML = `
            <span class="wf-corner wf-tl"></span><span class="wf-corner wf-tr"></span>
            <span class="wf-corner wf-bl"></span><span class="wf-corner wf-br"></span>
            <span class="wf-tag">${tag}</span>
            <div class="wf-progress"><div class="wf-progress-bar" style="transition:none;"></div></div>
          `;
          el.appendChild(ov);
        }
        if (!el.classList.contains('built')) {
          el.classList.add('unbuilt');
        }
      });
    }

    function triggerConstructAnimation(el, dragDuration = 540, delayMs = 0) {
      if (!agentInspectEnabled) {
        el.classList.remove('unbuilt', 'building');
        el.classList.add('built');
        return;
      }
      // Ensure element is 100% invisible (.unbuilt) until the cursor physically reaches it and finishes dragging!
      el.classList.remove('built', 'building');
      el.classList.add('unbuilt');
      el.dataset.queued = '1';

      buildQueue.push({
        el,
        agentIdx: -1, // Assigned dynamically to a free cursor when readyAt is reached
        phase: 'WAIT_STAGGER',
        readyAt: performance.now() + delayMs,
        dragDuration
      });
    }

    let io;
    function observeConstructElements() {
      if (io) io.disconnect();
      io = new IntersectionObserver((entries) => {
        // Sort intersecting unbuilt elements top-to-bottom, left-to-right for natural sequential cursor opening
        const visibleNew = entries
          .filter(e => e.isIntersecting && e.target.classList.contains('unbuilt') && e.target.dataset.queued !== '1')
          .map(e => e.target)
          .sort((a, b) => {
            const ra = a.getBoundingClientRect();
            const rb = b.getBoundingClientRect();
            if (Math.abs(ra.top - rb.top) > 28) return ra.top - rb.top;
            return ra.left - rb.left;
          });

        visibleNew.forEach((el, idx) => {
          el.dataset.queued = '1';
          // Stagger each element so cursors fly to them and open them in a visible sequence
          triggerConstructAnimation(el, 520, idx * 190);
        });
      }, { threshold: 0.08 });

      document.querySelectorAll('[data-construct]:not(.built)').forEach((el) => {
        el.classList.add('unbuilt');
        if (el.dataset.queued !== '1') {
          io.observe(el);
        }
      });
    }

    // =========================================================================
    // 4. AUTONOMOUS CURSOR ENGINE (Constructs Boxes + Opens Tabs + Orbits)
    // =========================================================================
    const canvas = document.getElementById('agentCursorCanvas');
    const ctx = canvas.getContext('2d');
    let w = (canvas.width = window.innerWidth);
    let h = (canvas.height = window.innerHeight);

    window.addEventListener('resize', () => {
      w = canvas.width = window.innerWidth;
      h = canvas.height = window.innerHeight;
    });

    const palette = ['#ffffff', '#ff1e1e', '#ff4d4d', '#ff0000', '#fca5a5', '#f87171'];
    const agentNames = ['UI_BUILD_01', 'TAB_OPENER', 'DOM_LAYOUT', 'ROS2_SYNC', 'PLC_WIRE', 'CAD_LOCK'];
    const clickRipples = [];

    const agents = Array.from({ length: 16 }, (_, i) => ({
      x: w / 2 + Math.cos((i / 16) * Math.PI * 2) * 55,
      y: h / 2 + Math.sin((i / 16) * Math.PI * 2) * 55,
      vx: 0,
      vy: 0,
      targetX: w / 2,
      targetY: h / 2,
      angle: (i / 16) * Math.PI * 2,
      color: palette[i % palette.length],
      tag: i < agentNames.length ? agentNames[i] : null
    }));

    let bootPhase = true;
    const bootOverlay = document.getElementById('bootOverlay');
    const bootCounter = document.getElementById('bootCounter');
    const agentTaskText = document.getElementById('agentTaskText');

    // Boot Sequence (00:00 - 00:01)
    let bootVal = 100;
    const bootTimer = setInterval(() => {
      bootVal += 80;
      if (bootVal >= 500) {
        bootCounter.textContent = '500';
        clearInterval(bootTimer);
        setTimeout(() => {
          bootOverlay.style.opacity = '0';
          setTimeout(() => {
            bootOverlay.style.display = 'none';
            bootPhase = false;
            observeConstructElements();
            startAutoScrollDirector();
          }, 450);
        }, 250);
      } else {
        bootCounter.textContent = String(bootVal);
      }
    }, 110);

    let agentInspectEnabled = true; // Toggled by button: when false, cursors disappear completely!
    let cursorsHaltedAtEnd = false; // Set true when scroll reaches the end so cursors stop moving
    const agentStatusBadgeBtn = document.getElementById('agentStatusBadge');
    const agentPingDot = document.getElementById('agentPingDot');

    function updateAgentToggleUI() {
      if (!agentStatusBadgeBtn || !agentTaskText) return;
      if (!agentInspectEnabled) {
        agentTaskText.textContent = 'AGENTS: OFF (HIDDEN)';
        agentStatusBadgeBtn.className = 'inline-flex items-center gap-1.5 px-2.5 py-1.5 rounded bg-zinc-900 hover:bg-zinc-800 border border-zinc-600 font-mono text-[9px] font-bold text-zinc-400 transition cursor-pointer';
        if (agentPingDot) agentPingDot.className = 'w-1.5 h-1.5 rounded-full bg-zinc-500';
        if (canvas) canvas.style.display = 'none';
      } else if (cursorsHaltedAtEnd) {
        agentTaskText.textContent = 'AGENTS: HALTED AT END [ON]';
        agentStatusBadgeBtn.className = 'inline-flex items-center gap-1.5 px-2.5 py-1.5 rounded bg-crimson/15 hover:bg-crimson/25 border border-crimson/50 font-mono text-[9px] font-bold text-white transition cursor-pointer';
        if (agentPingDot) agentPingDot.className = 'w-1.5 h-1.5 rounded-full bg-crimson';
        if (canvas) canvas.style.display = 'block';
      } else {
        agentTaskText.textContent = 'AGENTS: INSPECTING [ON]';
        agentStatusBadgeBtn.className = 'inline-flex items-center gap-1.5 px-2.5 py-1.5 rounded bg-crimson/15 hover:bg-crimson/25 border border-crimson/50 font-mono text-[9px] font-bold text-white transition cursor-pointer';
        if (agentPingDot) agentPingDot.className = 'w-1.5 h-1.5 rounded-full bg-crimson animate-ping';
        if (canvas) canvas.style.display = 'block';
      }
    }

    if (agentStatusBadgeBtn) {
      agentStatusBadgeBtn.addEventListener('click', () => {
        agentInspectEnabled = !agentInspectEnabled;
        if (!agentInspectEnabled) {
          // Clear canvas and reveal all sections cleanly when agents are turned OFF
          ctx.clearRect(0, 0, w, h);
          document.querySelectorAll('[data-construct]').forEach((el) => {
            el.classList.remove('unbuilt', 'building');
            el.classList.add('built');
          });
        } else {
          // Turning agents back ON resumes active inspection
          cursorsHaltedAtEnd = false;
          agents.forEach((a) => {
            a.nextMoveAt = 0;
          });
        }
        updateAgentToggleUI();
      });
    }

    // Autonomous Tab-Opener Loop (Clicks L1..L7 tabs when Flagship card is in view!)
    setInterval(() => {
      if (bootPhase || !agentInspectEnabled || cursorsHaltedAtEnd) return;
      const flagshipCard = document.getElementById('flagshipMainCard');
      if (!flagshipCard) return;
      const rect = flagshipCard.getBoundingClientRect();
      const inView = rect.top < h * 0.75 && rect.bottom > h * 0.25;

      if (inView) {
        const nextIdx = (activeLayerIdx + 1) % roverLayers.length;
        const btn = document.querySelector(`[data-layer-btn="${nextIdx}"]`);
        if (btn) {
          const bRect = btn.getBoundingClientRect();
          const tx = bRect.left + bRect.width / 2;
          const ty = bRect.top + bRect.height / 2;

          // Send Lead Tab-Opener Agent (#1) directly to the tab button
          agents[1].targetX = tx;
          agents[1].targetY = ty;
          agentTaskText.textContent = `AGENT: OPENING TAB ${roverLayers[nextIdx].id}`;

          setTimeout(() => {
            btn.classList.add('cursor-clicking-tab');
            if (typeof playTabClickSfx === 'function') playTabClickSfx();
            clickRipples.push({ x: tx, y: ty, r: 2, alpha: 1 });
            activeLayerIdx = nextIdx;
            renderLayers(true);
            setTimeout(() => btn.classList.remove('cursor-clicking-tab'), 320);
          }, 520);
        }
      } else if (agentInspectEnabled) {
        agentTaskText.textContent = buildQueue.length > 0 ? 'AGENTS: CONSTRUCTING [ON]' : 'AGENTS: INSPECTING [ON]';
      }
    }, 1350);

    // =========================================================================
    // 4B. SMOOTH AUTOMATIC SCROLL DIRECTOR (Matches 00:02 -> 00:56 Video Tour)
    // =========================================================================
    let autoScrollEnabled = true;
    let autoScrollStarted = false;
    let virtualScrollY = 0;
    let pauseScrollUntil = 0;
    let tourCompleted = false;
    let lastStageTriggered = -1;
    const autoScrollBtn = document.getElementById('autoScrollToggleBtn');

    function updateAutoScrollBtnUI() {
      if (!autoScrollBtn) return;
      if (tourCompleted) {
        autoScrollBtn.textContent = '↻ REPLAY AUTO-TOUR';
        autoScrollBtn.className = 'px-2.5 py-1.5 rounded border border-crimson/60 bg-crimson/15 hover:bg-crimson text-white font-mono text-[9px] font-bold uppercase tracking-wider transition';
      } else if (autoScrollEnabled) {
        autoScrollBtn.textContent = '● AUTO-SCROLL: ON';
        autoScrollBtn.className = 'px-2.5 py-1.5 rounded border border-crimson/50 bg-crimson/15 hover:bg-crimson/25 text-white font-mono text-[9px] font-bold uppercase tracking-wider transition';
      } else {
        autoScrollBtn.textContent = '❚❚ AUTO-SCROLL: PAUSED';
        autoScrollBtn.className = 'px-2.5 py-1.5 rounded border border-zinc-600 bg-zinc-900 hover:bg-zinc-800 text-zinc-300 font-mono text-[9px] font-bold uppercase tracking-wider transition';
      }
    }

    if (autoScrollBtn) {
      autoScrollBtn.addEventListener('click', () => {
        if (tourCompleted) {
          tourCompleted = false;
          cursorsHaltedAtEnd = false;
          agentInspectEnabled = true;
          if (audioCtx && audioCtx.state === 'running') {
            audioMuted = false;
            if (masterGain) masterGain.gain.setValueAtTime(0.28, audioCtx.currentTime);
            updateAudioBtnUI();
          }
          updateAgentToggleUI();
          lastStageTriggered = -1;
          virtualScrollY = 0;
          window.scrollTo(0, 0);
          document.querySelectorAll('[data-construct]').forEach((el) => {
            el.classList.remove('built', 'building');
            el.classList.add('unbuilt');
          });
          observeConstructElements();
          autoScrollEnabled = true;
          pauseScrollUntil = performance.now() + 1800;
        } else {
          autoScrollEnabled = !autoScrollEnabled;
          if (autoScrollEnabled) {
            virtualScrollY = window.scrollY;
          }
        }
        updateAutoScrollBtnUI();
      });
    }

    // Pause automatic scroll if the user manually wheels or drags, so they can inspect freely
    window.addEventListener('wheel', () => {
      if (autoScrollEnabled && !tourCompleted) {
        autoScrollEnabled = false;
        updateAutoScrollBtnUI();
      }
    }, { passive: true });

    window.addEventListener('touchmove', () => {
      if (autoScrollEnabled && !tourCompleted) {
        autoScrollEnabled = false;
        updateAutoScrollBtnUI();
      }
    }, { passive: true });

    function shutdownAtBottomEnd() {
      if (tourCompleted) return;
      tourCompleted = true;
      autoScrollEnabled = false;
      cursorsHaltedAtEnd = true;

      // 1. Automatically turn OFF Agent & hide all cursors
      agentInspectEnabled = false;
      if (ctx) ctx.clearRect(0, 0, w, h);
      document.querySelectorAll('[data-construct]').forEach((el) => {
        el.classList.remove('unbuilt', 'building');
        el.classList.add('built');
      });
      updateAgentToggleUI();

      // 2. Automatically turn OFF Audio
      audioMuted = true;
      if (audioCtx && masterGain) {
        try {
          masterGain.gain.setValueAtTime(0, audioCtx.currentTime);
        } catch (e) {}
      }
      if (typeof updateAudioBtnUI === 'function') updateAudioBtnUI();

      updateAutoScrollBtnUI();
    }

    function startAutoScrollDirector() {
      virtualScrollY = window.scrollY;
      // Hold on Hero for 2.2s while cursors finish constructing the Hero cards (00:01 - 00:05)
      pauseScrollUntil = performance.now() + 400;
      autoScrollStarted = true;
    }

    function stepAutoScroll(now) {
      if (!autoScrollStarted || !autoScrollEnabled || tourCompleted) return;
      if (now < pauseScrollUntil) return;
      // Wait while cursors are actively flying to and dragging open elements in the current viewport!
      if (agentInspectEnabled && buildQueue.length > 0) return;

      const maxScroll = Math.max(0, document.documentElement.scrollHeight - window.innerHeight);
      if (maxScroll <= 0) return;

      // Check milestone waypoints so the scroll pauses naturally while the cursor clicks tabs
      const flagshipEl = document.getElementById('flagshipMainCard');
      const matrixEl = document.getElementById('matrix');

      if (flagshipEl && lastStageTriggered < 1) {
        const fTop = flagshipEl.getBoundingClientRect().top;
        // When Flagship 7-Layer Stack is centered in viewport (00:22 - 00:29), pause 4.2s to watch cursor open tabs
        if (fTop <= window.innerHeight * 0.16 && fTop >= -40) {
          lastStageTriggered = 1;
          pauseScrollUntil = now + 4200;
          return;
        }
      }

      if (matrixEl && lastStageTriggered < 2) {
        const mTop = matrixEl.getBoundingClientRect().top;
        // When Systems Matrix arrives (00:37 - 00:42), pause 2.6s while cursor clicks filter tabs
        if (mTop <= window.innerHeight * 0.18 && mTop >= -40) {
          lastStageTriggered = 2;
          pauseScrollUntil = now + 2600;
          // Have cursor #1 click a Matrix filter tab and then back to All Systems
          const filterBtn = document.querySelector('[data-matrix-btn="1"]');
          if (filterBtn) {
            const bRect = filterBtn.getBoundingClientRect();
            agents[1].targetX = bRect.left + bRect.width / 2;
            agents[1].targetY = bRect.top + bRect.height / 2;
            setTimeout(() => {
              filterBtn.classList.add('cursor-clicking-tab');
              clickRipples.push({ x: agents[1].targetX, y: agents[1].targetY, r: 2, alpha: 1 });
              currentMatrixCat = 'Robotics & ROS 2';
              renderMatrix(true);
            }, 450);
            setTimeout(() => {
              currentMatrixCat = 'All Systems';
              renderMatrix(true);
            }, 1700);
          }
          return;
        }
      }

      // Smooth continuous glide speed (~1.15 px per 60fps frame = ~70px/sec, matching the 55s video pace)
      virtualScrollY += 1.15;
      if (virtualScrollY >= maxScroll) {
        virtualScrollY = maxScroll;
        window.scrollTo(0, maxScroll);
        // Wait for any active footer wireframe drags in buildQueue to finish opening before shutting down
        if (buildQueue.length === 0) {
          shutdownAtBottomEnd();
        }
      } else {
        window.scrollTo(0, virtualScrollY);
      }
    }

    // Assign stationary inspection waypoints on visible DOM cards (no spinning/rotating!)
    function pickViewportWaypoint(agentIdx) {
      const nodes = Array.from(document.querySelectorAll('[data-construct].built')).filter((el) => {
        const rect = el.getBoundingClientRect();
        return rect.top > 40 && rect.bottom < h - 20 && rect.width > 40;
      });
      if (nodes.length === 0) {
        return { x: w * (0.2 + (agentIdx % 5) * 0.15), y: h * (0.25 + ((agentIdx * 3) % 5) * 0.12) };
      }
      const chosen = nodes[(agentIdx * 3) % nodes.length];
      const rect = chosen.getBoundingClientRect();
      const offsets = [
        [rect.left + 18, rect.top + 18],
        [rect.right - 24, rect.top + 18],
        [rect.left + rect.width * 0.5, rect.bottom - 14],
        [rect.right - 20, rect.bottom - 16]
      ];
      const pt = offsets[agentIdx % offsets.length];
      return {
        x: Math.max(24, Math.min(w - 60, pt[0])),
        y: Math.max(60, Math.min(h - 30, pt[1]))
      };
    }

    function drawAgentCursor(a) {
      ctx.save();
      ctx.translate(a.x, a.y);
      // Fixed upright pointer orientation — never rotates!
      ctx.beginPath();
      ctx.moveTo(0, 0);
      ctx.lineTo(0, 12);
      ctx.lineTo(3.4, 9.0);
      ctx.lineTo(6.2, 14.0);
      ctx.lineTo(8.1, 13.0);
      ctx.lineTo(5.3, 8.0);
      ctx.lineTo(9.8, 8.0);
      ctx.closePath();

      ctx.fillStyle = a.color;
      ctx.fill();
      ctx.lineWidth = 0.9;
      ctx.strokeStyle = '#000000';
      ctx.stroke();
      ctx.restore();

      if (a.tag && w > 768) {
        ctx.fillStyle = 'rgba(220, 20, 20, 0.9)';
        ctx.fillRect(a.x + 11, a.y + 10, a.tag.length * 5.4 + 6, 12);
        ctx.font = '600 8px "JetBrains Mono", monospace';
        ctx.fillStyle = '#ffffff';
        ctx.fillText(a.tag, a.x + 14, a.y + 19);
      }
    }

    function animateAgents(now) {
      stepAutoScroll(now);
      ctx.clearRect(0, 0, w, h);

      // If the user turned OFF the agent, clear the canvas and do not draw any cursors
      if (!bootPhase && !agentInspectEnabled) {
        requestAnimationFrame(animateAgents);
        return;
      }

      // Automatically turn OFF both Agent (cursors disappear) and Audio when reaching the bottom of the page
      const maxDocScroll = Math.max(0, document.documentElement.scrollHeight - window.innerHeight);
      if (!bootPhase && !tourCompleted && buildQueue.length === 0 && maxDocScroll > 0 && window.scrollY >= maxDocScroll - 5) {
        shutdownAtBottomEnd();
      }

      // Track which agents are actively assigned to a job
      const busyAgents = new Set();
      if (!bootPhase) {
        buildQueue.forEach((j) => {
          if (j.agentIdx >= 0) busyAgents.add(j.agentIdx);
        });

        // Process active jobs ONLY after bootPhase finishes!
        for (let q = 0; q < buildQueue.length; q++) {
          const job = buildQueue[q];
          if (now < job.readyAt) continue;

          // Assign the closest available free cursor (excluding agent #1 Tab-Opener)
          if (job.agentIdx === -1) {
            const rInit = job.el.getBoundingClientRect();
            let bestIdx = -1;
            let bestDist = Infinity;
            for (let cIdx = 0; cIdx < agents.length; cIdx++) {
              if (cIdx === 1 || busyAgents.has(cIdx)) continue;
              const d = Math.hypot(agents[cIdx].x - rInit.left, agents[cIdx].y - rInit.top);
              if (d < bestDist) {
                bestDist = d;
                bestIdx = cIdx;
              }
            }
            if (bestIdx === -1) continue; // Wait until a cursor frees up!
            job.agentIdx = bestIdx;
            job.phase = 'APPROACH';
            busyAgents.add(bestIdx);
          }

          const r = job.el.getBoundingClientRect();
          const a = agents[job.agentIdx];

          if (job.phase === 'APPROACH') {
            // Fly cursor physically to top-left corner of the still-100%-invisible element
            a.targetX = Math.max(12, Math.min(w - 24, r.left));
            a.targetY = Math.max(16, Math.min(h - 24, r.top));
            const dist = Math.hypot(a.targetX - a.x, a.targetY - a.y);

            // ONLY start dragging the box AFTER the cursor physically reaches the top-left corner!
            if (dist < 15) {
              job.phase = 'DRAG';
              job.dragStart = now;
              job.el.classList.remove('unbuilt');
              job.el.classList.add('building');
              job.el.style.setProperty('--wf-w', '8%');
              job.el.style.setProperty('--wf-h', '12%');
              if (typeof playWireframeChirp === 'function') playWireframeChirp();
              clickRipples.push({ x: a.x, y: a.y, r: 2, alpha: 0.95 });
            }
          } else if (job.phase === 'DRAG') {
            const p = Math.min(1, (now - job.dragStart) / job.dragDuration);
            const easeP = 1 - Math.pow(1 - p, 2);
            const wPct = Math.round(8 + easeP * 92);
            const hPct = Math.round(12 + easeP * 88);

            // Cursor drags to the bottom-right corner, and the wireframe box expands directly with the cursor!
            a.targetX = Math.max(12, Math.min(w - 16, r.left + r.width * (wPct / 100)));
            a.targetY = Math.max(16, Math.min(h - 16, r.top + r.height * (hPct / 100)));

            job.el.style.setProperty('--wf-w', wPct + '%');
            job.el.style.setProperty('--wf-h', hPct + '%');

            const bar = job.el.querySelector('.wf-progress-bar');
            if (bar) bar.style.width = Math.round(easeP * 100) + '%';

            const tagEl = job.el.querySelector('.wf-tag');
            if (tagEl) {
              tagEl.textContent = `${job.el.getAttribute('data-construct') || 'NODE'} // ${Math.round(r.width * easeP)}×${Math.round(r.height * easeP)}`;
            }

            if (p >= 1) {
              // Cursor finished dragging the box! NOW unlock and reveal the content!
              job.el.classList.remove('building');
              job.el.classList.add('built');
              clickRipples.push({ x: a.x, y: a.y, r: 2, alpha: 1.0 });
              buildQueue.splice(q, 1);
              q--;
            }
          }
        }
      }

      agents.forEach((a, i) => {
        if (bootPhase) {
          const r = 46 + (i % 3) * 14;
          a.targetX = w / 2 + Math.cos(a.angle) * r;
          a.targetY = h / 2 + Math.sin(a.angle) * r;
          a.x += (a.targetX - a.x) * 0.12;
          a.y += (a.targetY - a.y) * 0.12;
        } else if (busyAgents.has(i)) {
          // Crisp cursor travel to top-left corner and smooth drag across box
          a.x += (a.targetX - a.x) * 0.34;
          a.y += (a.targetY - a.y) * 0.34;
        } else if (!cursorsHaltedAtEnd) {
          if (buildQueue.length > 0 && i !== 1) {
            // Helper cursors assist at the top-right / bottom-left corners of active DRAG jobs
            const dragJobs = buildQueue.filter(j => j.phase === 'DRAG');
            if (dragJobs.length > 0) {
              const dj = dragJobs[i % dragJobs.length];
              const r = dj.el.getBoundingClientRect();
              a.targetX = (i % 2 === 0) ? r.right : r.left;
              a.targetY = (i % 2 === 0) ? r.top : r.bottom;
            }
          } else if (i !== 1) {
            if (!a.nextMoveAt || now >= a.nextMoveAt) {
              const wp = pickViewportWaypoint(i + Math.floor(now / 1800));
              a.targetX = wp.x;
              a.targetY = wp.y;
              a.nextMoveAt = now + 1800 + (i % 5) * 420;
            }
          }
          a.x += (a.targetX - a.x) * 0.11;
          a.y += (a.targetY - a.y) * 0.11;
        }
        drawAgentCursor(a);
      });

      for (let i = clickRipples.length - 1; i >= 0; i--) {
        const rp = clickRipples[i];
        ctx.beginPath();
        ctx.arc(rp.x, rp.y, rp.r, 0, Math.PI * 2);
        ctx.strokeStyle = `rgba(255, 30, 30, ${rp.alpha})`;
        ctx.lineWidth = 2;
        ctx.stroke();
        rp.r += 1.6;
        rp.alpha -= 0.04;
        if (rp.alpha <= 0) clickRipples.splice(i, 1);
      }

      requestAnimationFrame(animateAgents);
    }

    document.getElementById('initiateTransmissionBtn').addEventListener('click', () => {
      const text = 'S. Rahul Kumar | B.Tech ECE @ SRMIST Ramapuram (2026–2030) | Chennai, TN, India | Email: rahulkumar.rk2958454@gmail.com | LinkedIn: https://www.linkedin.com/in/rahul-kumar-715b32423 | GitHub: https://github.com/Rahulkumar2k8';
      const ta = document.createElement('textarea');
      ta.value = text;
      document.body.appendChild(ta);
      ta.select();
      try { document.execCommand('copy'); } catch (e) {}
      document.body.removeChild(ta);
      const toast = document.getElementById('copyToast');
      toast.classList.remove('hidden');
      setTimeout(() => toast.classList.add('hidden'), 3000);
    });

    // =========================================================================
    // 5. WEB AUDIO API HACKER DARKSYNTH & TELEMETRY SFX ENGINE
    // =========================================================================
    let audioCtx = null;
    let masterGain = null;
    let audioMuted = false;
    let seqInterval = null;
    let seqStep = 0;
    const hackerAudioBtn = document.getElementById('hackerAudioBtn');

    function updateAudioBtnUI() {
      if (!hackerAudioBtn) return;
      if (!audioCtx || audioCtx.state === 'suspended') {
        hackerAudioBtn.textContent = '🔊 AUDIO: CLICK TO START';
        hackerAudioBtn.className = 'px-2.5 py-1.5 rounded border border-crimson bg-crimson/20 hover:bg-crimson text-white font-mono text-[9px] font-bold uppercase tracking-wider transition animate-pulse shadow-[0_0_15px_rgba(255,30,30,0.45)]';
      } else if (audioMuted) {
        hackerAudioBtn.textContent = '🔇 AUDIO: MUTED';
        hackerAudioBtn.className = 'px-2.5 py-1.5 rounded border border-zinc-600 bg-zinc-900 hover:bg-zinc-800 text-zinc-400 font-mono text-[9px] font-bold uppercase tracking-wider transition';
      } else {
        hackerAudioBtn.textContent = '🔊 HACKER SYNTH: ON';
        hackerAudioBtn.className = 'px-2.5 py-1.5 rounded border border-crimson/60 bg-crimson text-white font-mono text-[9px] font-bold uppercase tracking-wider transition shadow-[0_0_18px_rgba(255,30,30,0.5)]';
      }
    }

    function initHackerAudio() {
      try {
        if (!audioCtx) {
          const AC = window.AudioContext || window.webkitAudioContext;
          audioCtx = new AC();
          masterGain = audioCtx.createGain();
          masterGain.gain.value = 0.28;
          masterGain.connect(audioCtx.destination);
        }
        if (audioCtx.state === 'suspended') {
          audioCtx.resume().then(() => {
            updateAudioBtnUI();
          }).catch(() => {});
        }
        if (!seqInterval) {
          startDarksynthSequencer();
        }
        updateAudioBtnUI();
      } catch (e) {}
    }

    // Darksynth / Phonk 16-step patterns in D Phrygian / Minor (matches the heavy dark-tech vibe of the video)
    // Bass frequencies (D1=36.71, F1=43.65, G1=49.00, Ab1=51.91, A1=55.00, Bb1=58.27, C2=65.41, D2=73.42)
    const bassPattern = [
      36.71, 36.71, 73.42, 36.71,
      43.65, 43.65, 49.00, 51.91,
      36.71, 36.71, 73.42, 36.71,
      58.27, 55.00, 49.00, 43.65
    ];

    // Hypnotic Cybernetic Phonk/Darksynth Lead Arpeggio (D4=293.66, F4=349.23, A4=440.00, Bb4=466.16, C#4=277.18, E4=329.63)
    const arpPattern = [
      293.66, 349.23, 440.00, 466.16,
      440.00, 349.23, 293.66, 349.23,
      293.66, 349.23, 440.00, 587.33,
      466.16, 440.00, 329.63, 277.18
    ];

    function playKick(t) {
      const osc = audioCtx.createOscillator();
      const g = audioCtx.createGain();
      osc.type = 'sine';
      osc.frequency.setValueAtTime(135, t);
      osc.frequency.exponentialRampToValueAtTime(34, t + 0.14);
      g.gain.setValueAtTime(0.85, t);
      g.gain.exponentialRampToValueAtTime(0.001, t + 0.24);
      osc.connect(g);
      g.connect(masterGain);
      osc.start(t);
      osc.stop(t + 0.25);
    }

    function playSnareOrHat(t, isSnare) {
      const bufSize = audioCtx.sampleRate * (isSnare ? 0.14 : 0.04);
      const buf = audioCtx.createBuffer(1, bufSize, audioCtx.sampleRate);
      const data = buf.getChannelData(0);
      for (let i = 0; i < bufSize; i++) {
        data[i] = Math.random() * 2 - 1;
      }
      const noise = audioCtx.createBufferSource();
      noise.buffer = buf;

      const filter = audioCtx.createBiquadFilter();
      filter.type = isSnare ? 'bandpass' : 'highpass';
      filter.frequency.setValueAtTime(isSnare ? 1800 : 7500, t);

      const g = audioCtx.createGain();
      g.gain.setValueAtTime(isSnare ? 0.32 : 0.11, t);
      g.gain.exponentialRampToValueAtTime(0.001, t + (isSnare ? 0.14 : 0.04));

      noise.connect(filter);
      filter.connect(g);
      g.connect(masterGain);
      noise.start(t);
    }

    function playBassNote(t, freq) {
      const osc = audioCtx.createOscillator();
      const sub = audioCtx.createOscillator();
      const filter = audioCtx.createBiquadFilter();
      const g = audioCtx.createGain();

      osc.type = 'sawtooth';
      osc.frequency.setValueAtTime(freq * 2, t);
      sub.type = 'triangle';
      sub.frequency.setValueAtTime(freq, t);

      filter.type = 'lowpass';
      filter.frequency.setValueAtTime(420, t);
      filter.frequency.exponentialRampToValueAtTime(110, t + 0.11);
      filter.Q.value = 4.5;

      g.gain.setValueAtTime(0.36, t);
      g.gain.exponentialRampToValueAtTime(0.01, t + 0.12);

      osc.connect(filter);
      sub.connect(filter);
      filter.connect(g);
      g.connect(masterGain);

      osc.start(t);
      sub.start(t);
      osc.stop(t + 0.125);
      sub.stop(t + 0.125);
    }

    function playArpNote(t, freq, accent) {
      const osc = audioCtx.createOscillator();
      const filter = audioCtx.createBiquadFilter();
      const g = audioCtx.createGain();

      osc.type = accent ? 'sawtooth' : 'square';
      osc.frequency.setValueAtTime(freq, t);

      filter.type = 'lowpass';
      filter.frequency.setValueAtTime(accent ? 2400 : 1450, t);
      filter.frequency.exponentialRampToValueAtTime(380, t + 0.11);

      g.gain.setValueAtTime(accent ? 0.16 : 0.09, t);
      g.gain.exponentialRampToValueAtTime(0.001, t + 0.115);

      osc.connect(filter);
      filter.connect(g);
      g.connect(masterGain);

      osc.start(t);
      osc.stop(t + 0.12);
    }

    function startDarksynthSequencer() {
      // 122 BPM -> 16th note = ~123ms
      seqInterval = setInterval(() => {
        if (!audioCtx || audioCtx.state !== 'running' || audioMuted) return;
        const t = audioCtx.currentTime + 0.01;
        const step = seqStep % 16;

        // Driving 4-on-the-floor + syncopated kick
        if (step === 0 || step === 4 || step === 8 || step === 12 || step === 14) {
          playKick(t);
        }
        // Snare on 4 & 12, crisp hats on every 16th
        if (step === 4 || step === 12) {
          playSnareOrHat(t, true);
        } else {
          playSnareOrHat(t, false);
        }

        // Darksynth rolling bass
        playBassNote(t, bassPattern[step]);

        // Cybernetic arpeggio
        playArpNote(t, arpPattern[step], step % 4 === 0);

        seqStep++;
      }, 123);
    }

    // Telemetry Wireframe Chirp SFX (triggered when cursors construct blue boxes)
    let lastChirpTime = 0;
    function playWireframeChirp() {
      if (!audioCtx || audioCtx.state !== 'running' || audioMuted) return;
      const now = performance.now();
      if (now - lastChirpTime < 140) return;
      lastChirpTime = now;

      const t = audioCtx.currentTime;
      const osc = audioCtx.createOscillator();
      const g = audioCtx.createGain();
      osc.type = 'sine';
      const baseF = 1100 + Math.random() * 700;
      osc.frequency.setValueAtTime(baseF, t);
      osc.frequency.exponentialRampToValueAtTime(baseF * 1.45, t + 0.045);

      g.gain.setValueAtTime(0.055, t);
      g.gain.exponentialRampToValueAtTime(0.001, t + 0.05);

      osc.connect(g);
      g.connect(masterGain);
      osc.start(t);
      osc.stop(t + 0.055);
    }

    // Tab Click Confirmation SFX (triggered when cursor opens L1..L7 or Matrix tabs)
    function playTabClickSfx() {
      if (!audioCtx || audioCtx.state !== 'running' || audioMuted) return;
      const t = audioCtx.currentTime;
      const osc = audioCtx.createOscillator();
      const g = audioCtx.createGain();
      osc.type = 'triangle';
      osc.frequency.setValueAtTime(1680, t);
      osc.frequency.setValueAtTime(2240, t + 0.03);

      g.gain.setValueAtTime(0.14, t);
      g.gain.exponentialRampToValueAtTime(0.001, t + 0.085);

      osc.connect(g);
      g.connect(masterGain);
      osc.start(t);
      osc.stop(t + 0.09);
    }

    if (hackerAudioBtn) {
      hackerAudioBtn.addEventListener('click', (e) => {
        e.stopPropagation();
        if (!audioCtx || audioCtx.state === 'suspended') {
          audioMuted = false;
          initHackerAudio();
        } else {
          audioMuted = !audioMuted;
          masterGain.gain.setValueAtTime(audioMuted ? 0 : 0.28, audioCtx.currentTime);
          updateAudioBtnUI();
        }
      });
    }

    // Unlock audio automatically on first user gesture anywhere in the page
    ['pointerdown', 'keydown', 'touchstart'].forEach((evt) => {
      window.addEventListener(evt, () => {
        if (!audioCtx || audioCtx.state === 'suspended') {
          initHackerAudio();
        }
      }, { once: false, passive: true });
    });

    window.addEventListener('DOMContentLoaded', () => {
      initHackerAudio();
      renderLayers(false);
      renderMatrix(false);
      injectWireframeOverlays();
      requestAnimationFrame(animateAgents);
    });
  </script>
</body>
</html>
