
<style>
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');
*{box-sizing:border-box;margin:0;padding:0;}
body{background:#000;}
.root{font-family:'Press Start 2P',monospace;background:#0a0015;color:#e0e0e0;overflow-x:hidden;position:relative;}

/* Stars bg */
.stars{position:fixed;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:0;overflow:hidden;}
.star{position:absolute;background:#fff;border-radius:50%;animation:twinkle var(--d) ease-in-out infinite;}
@keyframes twinkle{0%,100%{opacity:0.1;}50%{opacity:1;}}

/* Scanlines */
.root::after{content:'';position:fixed;top:0;left:0;width:100%;height:100%;background:repeating-linear-gradient(0deg,transparent,transparent 3px,rgba(0,0,0,0.07) 3px,rgba(0,0,0,0.07) 4px);pointer-events:none;z-index:998;}

/* ─── HUD ─── */
.hud{position:relative;z-index:10;background:#100025;border-bottom:3px solid #a000ff;padding:10px 18px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:8px;}
.hud-hearts{color:#ff3366;font-size:13px;letter-spacing:3px;}
.hud-mid{text-align:center;}
.hud-title{font-size:7px;color:#a000ff;letter-spacing:3px;animation:colorshift 3s linear infinite;}
@keyframes colorshift{0%{color:#a000ff;}33%{color:#00e5ff;}66%{color:#ff3366;}100%{color:#a000ff;}}
.hud-name{font-size:10px;color:#fff;margin-top:3px;}
.hud-right{font-size:6px;color:#666;text-align:right;}
.exp-row{display:flex;align-items:center;gap:6px;margin-top:4px;}
.exp-bar{width:90px;height:7px;background:#200040;border:2px solid #a000ff;}
.exp-fill{height:100%;background:#a000ff;animation:expup 2s ease-out;}
@keyframes expup{from{width:0;}to{width:75%;}}
.exp-val{font-size:6px;color:#a000ff;}

/* ─── SCENE (world) ─── */
.scene{position:relative;z-index:5;width:100%;height:220px;background:linear-gradient(180deg,#00001a 0%,#0a0040 40%,#1a0050 60%,#2a0a0a 80%,#1a0500 100%);overflow:hidden;border-bottom:4px solid #a000ff;}

/* Moon */
.moon{position:absolute;top:20px;right:60px;width:40px;height:40px;background:#ffe87a;border-radius:50%;box-shadow:0 0 18px #ffe87a88;}

/* Mountains bg */
.mtn-bg{position:absolute;bottom:60px;left:0;width:100%;}
.mtn-fg{position:absolute;bottom:40px;left:0;width:100%;}

/* Ground */
.ground{position:absolute;bottom:0;left:0;width:100%;height:55px;background:#1a0500;}
.ground-top{position:absolute;bottom:52px;left:0;width:100%;height:6px;background:#2d8a00;}
.pixel-row{display:flex;height:6px;overflow:hidden;}
.px-g{width:8px;height:6px;background:#2d8a00;flex-shrink:0;}
.px-g.dark{background:#1a6600;}

/* Stars moving */
.shooting{position:absolute;height:2px;background:linear-gradient(90deg,#fff,transparent);animation:shoot linear infinite;opacity:0;}
@keyframes shoot{0%{opacity:1;transform:translateX(0) translateY(0);}100%{opacity:0;transform:translateX(-300px) translateY(80px);}}

/* Floating coins */
.coin{position:absolute;font-size:10px;animation:floatcoin 3s ease-in-out infinite;}
@keyframes floatcoin{0%,100%{transform:translateY(0);}50%{transform:translateY(-10px);}}

/* Trees pixel */
.tree{position:absolute;bottom:52px;}
.tree-top{width:20px;height:30px;background:#1a6600;border:2px solid #0d4400;margin:0 auto;}
.tree-trunk{width:8px;height:10px;background:#5c3a1e;margin:0 auto;}

/* Character sprite animated */
.char-wrap{position:absolute;bottom:52px;left:50%;transform:translateX(-50%);}
.char-canvas{image-rendering:pixelated;width:48px;height:64px;}

/* Clouds */
.cloud{position:absolute;opacity:0.5;animation:cloudmove linear infinite;}
@keyframes cloudmove{0%{transform:translateX(110%);}100%{transform:translateX(-20%);}}

/* ─── NAV TABS ─── */
.nav{position:relative;z-index:10;display:flex;background:#100025;border-bottom:2px solid #a000ff33;overflow-x:auto;}
.nav-tab{font-size:7px;padding:10px 14px;cursor:pointer;color:#666;border-bottom:3px solid transparent;white-space:nowrap;transition:all 0.15s;flex-shrink:0;}
.nav-tab:hover{color:#a000ff;}
.nav-tab.active{color:#a000ff;border-bottom-color:#a000ff;}

/* ─── PANELS ─── */
.panel{display:none;position:relative;z-index:5;padding:18px;}
.panel.active{display:block;}

/* Hero info */
.hero-row{display:flex;gap:20px;align-items:flex-start;flex-wrap:wrap;}
.avatar-big{flex-shrink:0;}
.char-profile{image-rendering:pixelated;width:96px;height:128px;border:4px solid #a000ff;background:#100025;}
.badge-row{display:flex;gap:6px;flex-wrap:wrap;margin:8px 0;}
.badge{font-size:6px;padding:3px 8px;border:2px solid;background:#100025;}
.badge.purple{border-color:#a000ff;color:#c77dff;}
.badge.cyan{border-color:#00e5ff;color:#80ffff;}
.badge.pink{border-color:#ff3366;color:#ff8fa3;}
.badge.gold{border-color:#ffd700;color:#ffd700;}
.hero-name-big{font-size:16px;color:#fff;margin-bottom:8px;}
.hero-role{font-size:8px;color:#a000ff;margin-bottom:10px;}
.hero-bio{font-size:7px;color:#aaa;line-height:2.2;max-width:360px;}
.hero-loc{font-size:6px;color:#666;margin-top:8px;}

/* Stats */
.stats-row{display:flex;flex-wrap:wrap;gap:8px;margin-top:14px;}
.stat{background:#1a003a;border:2px solid #a000ff44;padding:10px 14px;text-align:center;min-width:72px;position:relative;overflow:hidden;}
.stat::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:#a000ff;}
.stat-n{font-size:16px;color:#a000ff;display:block;animation:pulseval 2s ease-in-out infinite;}
@keyframes pulseval{0%,100%{text-shadow:0 0 4px #a000ff;}50%{text-shadow:0 0 12px #a000ff,0 0 24px #a000ff44;}}
.stat-l{font-size:6px;color:#666;margin-top:4px;display:block;}

/* Skills */
.skills-grid{display:flex;flex-wrap:wrap;gap:8px;}
.sk{font-size:7px;padding:6px 11px;border:2px solid;cursor:pointer;transition:all 0.12s;user-select:none;position:relative;}
.sk:active{transform:scale(0.88);}
.sk.lang{border-color:#a000ff;color:#c77dff;background:#1a003a;}
.sk.lang:hover{background:#a000ff;color:#fff;}
.sk.frame{border-color:#00e5ff;color:#80ffff;background:#001a1f;}
.sk.frame:hover{background:#00e5ff;color:#000;}
.sk.tool{border-color:#39ff14;color:#b2ff59;background:#001200;}
.sk.tool:hover{background:#39ff14;color:#000;}
.sk.db{border-color:#ff9100;color:#ffcc80;background:#1a0a00;}
.sk.db:hover{background:#ff9100;color:#000;}
.sk.ai{border-color:#ff3366;color:#ff8fa3;background:#1a0010;}
.sk.ai:hover{background:#ff3366;color:#fff;}

/* Progress */
.prog-item{margin-bottom:12px;}
.prog-head{display:flex;justify-content:space-between;margin-bottom:4px;}
.prog-nm{font-size:7px;color:#ddd;}
.prog-pc{font-size:7px;color:#a000ff;}
.prog-track{height:10px;background:#1a003a;border:2px solid #a000ff33;position:relative;overflow:hidden;}
.prog-fill{height:100%;position:relative;animation:barfill 1.5s ease-out both;}
@keyframes barfill{from{width:0!important;}}
.prog-fill::after{content:'';position:absolute;top:0;right:0;bottom:0;width:4px;background:rgba(255,255,255,0.5);}

/* Projects */
.proj-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:12px;}
.proj{background:#100025;border:2px solid #a000ff33;padding:14px;cursor:pointer;transition:all 0.15s;position:relative;overflow:hidden;}
.proj::before{content:'▶';position:absolute;top:10px;right:10px;font-size:8px;color:#a000ff;opacity:0;transition:opacity 0.2s;}
.proj:hover{border-color:#a000ff;transform:translateY(-3px);}
.proj:hover::before{opacity:1;}
.proj-title{font-size:8px;color:#fff;margin-bottom:6px;}
.proj-desc{font-size:6px;color:#888;line-height:2;margin-bottom:10px;}
.proj-tech{display:flex;gap:4px;flex-wrap:wrap;}
.proj-tech span{font-size:6px;padding:2px 6px;background:#0d0025;border:1px solid #a000ff44;color:#c77dff;}
.proj-stars{font-size:7px;color:#ffd700;margin-bottom:6px;}

/* Achievements */
.ach-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:10px;}
.ach{background:#100025;border:2px solid #ffd70033;padding:12px;text-align:center;position:relative;}
.ach.locked{opacity:0.35;filter:grayscale(1);}
.ach-icon{font-size:24px;display:block;margin-bottom:6px;}
.ach-name{font-size:6px;color:#ffd700;margin-bottom:4px;}
.ach-desc{font-size:5px;color:#888;line-height:1.8;}
.ach-unlocked{position:absolute;top:4px;right:6px;font-size:5px;color:#39ff14;}

/* Socials */
.soc-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(160px,1fr));gap:10px;}
.soc{display:flex;align-items:center;gap:10px;padding:12px 14px;border:2px solid;cursor:pointer;text-decoration:none;color:inherit;transition:all 0.15s;position:relative;overflow:hidden;}
.soc:hover{transform:scale(1.03);}
.soc::after{content:'→';position:absolute;right:10px;font-size:10px;opacity:0;transition:all 0.2s;}
.soc:hover::after{opacity:1;right:8px;}
.soc svg{width:16px;height:16px;flex-shrink:0;}
.soc-label{font-size:7px;}
.soc-sub{font-size:5px;margin-top:3px;opacity:0.7;}
.gh{border-color:#ffffff44;color:#fff;background:#100025;}
.gh:hover{background:#ffffff11;}
.ig{border-color:#e1306c66;color:#e1306c;background:#1a0010;}
.ig:hover{background:#e1306c22;}
.li{border-color:#0077b566;color:#0077b5;background:#00101a;}
.li:hover{background:#0077b522;}
.tw{border-color:#1da1f266;color:#1da1f2;background:#00101a;}
.tw:hover{background:#1da1f222;}
.yt{border-color:#ff000066;color:#ff4444;background:#1a0000;}
.yt:hover{background:#ff000022;}
.dc{border-color:#5865f266;color:#7289da;background:#00001a;}
.dc:hover{background:#5865f222;}

/* Section titles */
.stitle{font-size:9px;color:#a000ff;border-left:4px solid #a000ff;padding-left:10px;margin-bottom:16px;letter-spacing:2px;}

/* Pixel divider */
.divider{display:flex;gap:4px;margin:16px 0;align-items:center;}
.div-line{flex:1;height:2px;background:repeating-linear-gradient(90deg,#a000ff 0px,#a000ff 4px,transparent 4px,transparent 8px);}
.div-icon{font-size:10px;color:#a000ff;}

/* Dialog box */
.dialog{background:#0a0015;border:3px solid #a000ff;padding:14px;margin-top:16px;position:relative;}
.dialog::before{content:'';position:absolute;top:-10px;left:20px;border:5px solid transparent;border-bottom-color:#a000ff;}
.dialog-text{font-size:7px;color:#ddd;line-height:2.5;}
.cursor-blink{animation:blink 0.8s step-end infinite;color:#a000ff;}
@keyframes blink{50%{opacity:0;}}

/* Footer */
.footer{background:#100025;border-top:3px solid #a000ff;padding:14px;text-align:center;font-size:6px;color:#444;line-height:3;position:relative;z-index:5;}
.footer-anim{color:#a000ff;animation:colorshift 3s linear infinite;}
</style>

<div class="root">

<!-- Stars -->
<div class="stars" id="stars"></div>

<!-- HUD -->
<div class="hud">
  <div class="hud-hearts" id="hearts">♥ ♥ ♥</div>
  <div class="hud-mid">
    <div class="hud-title">◀ DEVELOPER PROFILE ▶</div>
    <div class="hud-name">TU_ALIAS</div>
  </div>
  <div class="hud-right">
    LVL 99
    <div class="exp-row">
      <span class="exp-val">EXP</span>
      <div class="exp-bar"><div class="exp-fill" style="width:75%"></div></div>
      <span class="exp-val">75%</span>
    </div>
  </div>
</div>

<!-- SCENE -->
<div class="scene" id="scene">
  <div class="moon"></div>

  <!-- Clouds -->
  <div class="cloud" style="top:30px;animation-duration:22s;animation-delay:0s;">
    <svg width="60" height="20" viewBox="0 0 60 20"><rect x="10" y="10" width="40" height="10" fill="#ffffff22"/><rect x="20" y="4" width="20" height="10" fill="#ffffff22"/><rect x="14" y="7" width="14" height="8" fill="#ffffff22"/></svg>
  </div>
  <div class="cloud" style="top:55px;animation-duration:30s;animation-delay:-10s;">
    <svg width="45" height="16" viewBox="0 0 45 16"><rect x="8" y="8" width="30" height="8" fill="#ffffff18"/><rect x="15" y="3" width="16" height="8" fill="#ffffff18"/></svg>
  </div>

  <!-- Shooting stars -->
  <div class="shooting" style="top:18px;right:20px;width:80px;animation-duration:4s;animation-delay:1s;"></div>
  <div class="shooting" style="top:40px;right:100px;width:60px;animation-duration:6s;animation-delay:3.5s;"></div>

  <!-- Mountains bg -->
  <svg class="mtn-bg" height="100" viewBox="0 0 800 100" preserveAspectRatio="none">
    <polygon points="0,100 80,20 160,100" fill="#1a0040"/>
    <polygon points="100,100 220,10 340,100" fill="#220050"/>
    <polygon points="280,100 400,30 520,100" fill="#1a0040"/>
    <polygon points="450,100 560,15 680,100" fill="#1e0045"/>
    <polygon points="600,100 720,25 840,100" fill="#1a0040"/>
  </svg>

  <!-- Mountains fg -->
  <svg class="mtn-fg" height="80" viewBox="0 0 800 80" preserveAspectRatio="none">
    <polygon points="0,80 60,30 120,80" fill="#2d0060"/>
    <polygon points="80,80 180,15 280,80" fill="#350070"/>
    <polygon points="220,80 320,25 420,80" fill="#2d0060"/>
    <polygon points="360,80 460,20 560,80" fill="#350070"/>
    <polygon points="500,80 600,30 700,80" fill="#2d0060"/>
    <polygon points="640,80 740,18 840,80" fill="#350070"/>
  </svg>

  <!-- Trees -->
  <div class="tree" style="left:8%"><div class="tree-top"></div><div class="tree-trunk"></div></div>
  <div class="tree" style="left:15%"><div class="tree-top" style="height:40px"></div><div class="tree-trunk"></div></div>
  <div class="tree" style="right:10%"><div class="tree-top"></div><div class="tree-trunk"></div></div>
  <div class="tree" style="right:18%"><div class="tree-top" style="height:36px"></div><div class="tree-trunk"></div></div>

  <!-- Floating coins -->
  <div class="coin" style="left:25%;top:80px;animation-delay:0s;">🪙</div>
  <div class="coin" style="left:70%;top:70px;animation-delay:1s;">🪙</div>
  <div class="coin" style="left:45%;top:90px;animation-delay:2s;">⭐</div>

  <!-- Ground -->
  <div class="ground-top"></div>
  <div class="ground"></div>

  <!-- Character canvas -->
  <div class="char-wrap">
    <canvas class="char-canvas" id="charCanvas" width="12" height="16"></canvas>
  </div>
</div>

<!-- NAV TABS -->
<div class="nav">
  <div class="nav-tab active" onclick="switchTab('profile')">👾 PERFIL</div>
  <div class="nav-tab" onclick="switchTab('skills')">⚔ SKILLS</div>
  <div class="nav-tab" onclick="switchTab('projects')">🗺 PROYECTOS</div>
  <div class="nav-tab" onclick="switchTab('achievements')">🏆 LOGROS</div>
  <div class="nav-tab" onclick="switchTab('socials')">🌐 REDES</div>
</div>

<!-- ═══ PANEL: PROFILE ═══ -->
<div class="panel active" id="panel-profile">
  <div class="hero-row">
    <div class="avatar-big">
      <canvas class="char-profile" id="profileCanvas" width="24" height="32"></canvas>
      <div style="font-size:6px;color:#a000ff;text-align:center;margin-top:6px;animation:blink 1s step-end infinite;">▶ PLAYER 1 ◀</div>
    </div>
    <div style="flex:1;min-width:200px;">
      <div class="hero-name-big" id="typedName">_</div>
      <div class="hero-role">⚔ FULL STACK DEVELOPER</div>
      <div class="badge-row">
        <span class="badge purple">Open Source</span>
        <span class="badge cyan">Full Stack</span>
        <span class="badge pink">Panameño 🇵🇦</span>
        <span class="badge gold">LVL 99</span>
      </div>
      <div class="dialog">
        <div class="dialog-text" id="dialogText"></div>
      </div>
      <div class="stats-row">
        <div class="stat"><span class="stat-n" id="sRepos">0</span><span class="stat-l">REPOS</span></div>
        <div class="stat"><span class="stat-n" id="sCommits">0</span><span class="stat-l">COMMITS</span></div>
        <div class="stat"><span class="stat-n" id="sProj">0</span><span class="stat-l">PROYECTOS</span></div>
        <div class="stat"><span class="stat-n" id="sYears">0</span><span class="stat-l">AÑOS XP</span></div>
        <div class="stat"><span class="stat-n" id="sPRs">0</span><span class="stat-l">PULL REQ</span></div>
      </div>
    </div>
  </div>
</div>

<!-- ═══ PANEL: SKILLS ═══ -->
<div class="panel" id="panel-skills">
  <div class="stitle">◈ INVENTARIO DE HABILIDADES</div>
  <div style="font-size:6px;color:#666;margin-bottom:14px;">Haz clic en cada skill para equiparla</div>
  <div style="margin-bottom:10px;font-size:7px;color:#888;">LENGUAJES</div>
  <div class="skills-grid" style="margin-bottom:16px;">
    <div class="sk lang" onclick="equipSkill(this)">JavaScript</div>
    <div class="sk lang" onclick="equipSkill(this)">TypeScript</div>
    <div class="sk lang" onclick="equipSkill(this)">Python</div>
    <div class="sk lang" onclick="equipSkill(this)">HTML / CSS</div>
    <div class="sk lang" onclick="equipSkill(this)">PHP</div>
    <div class="sk lang" onclick="equipSkill(this)">SQL</div>
  </div>
  <div style="margin-bottom:10px;font-size:7px;color:#888;">FRAMEWORKS</div>
  <div class="skills-grid" style="margin-bottom:16px;">
    <div class="sk frame" onclick="equipSkill(this)">React</div>
    <div class="sk frame" onclick="equipSkill(this)">Node.js</div>
    <div class="sk frame" onclick="equipSkill(this)">Next.js</div>
    <div class="sk frame" onclick="equipSkill(this)">Express</div>
    <div class="sk frame" onclick="equipSkill(this)">Vue.js</div>
    <div class="sk frame" onclick="equipSkill(this)">Tailwind</div>
  </div>
  <div style="margin-bottom:10px;font-size:7px;color:#888;">HERRAMIENTAS</div>
  <div class="skills-grid" style="margin-bottom:16px;">
    <div class="sk tool" onclick="equipSkill(this)">Git / GitHub</div>
    <div class="sk tool" onclick="equipSkill(this)">Docker</div>
    <div class="sk tool" onclick="equipSkill(this)">Linux</div>
    <div class="sk tool" onclick="equipSkill(this)">VS Code</div>
    <div class="sk tool" onclick="equipSkill(this)">Figma</div>
  </div>
  <div style="margin-bottom:10px;font-size:7px;color:#888;">BASES DE DATOS</div>
  <div class="skills-grid" style="margin-bottom:16px;">
    <div class="sk db" onclick="equipSkill(this)">MySQL</div>
    <div class="sk db" onclick="equipSkill(this)">MongoDB</div>
    <div class="sk db" onclick="equipSkill(this)">PostgreSQL</div>
    <div class="sk db" onclick="equipSkill(this)">Firebase</div>
  </div>
  <div style="margin-bottom:10px;font-size:7px;color:#888;">IA / CLOUD</div>
  <div class="skills-grid" style="margin-bottom:16px;">
    <div class="sk ai" onclick="equipSkill(this)">AWS</div>
    <div class="sk ai" onclick="equipSkill(this)">Vercel</div>
    <div class="sk ai" onclick="equipSkill(this)">OpenAI API</div>
  </div>

  <div class="divider"><div class="div-line"></div><div class="div-icon">⚔</div><div class="div-line"></div></div>
  <div class="stitle">◈ STATS DE COMBATE</div>
  <div class="prog-item">
    <div class="prog-head"><span class="prog-nm">Frontend</span><span class="prog-pc">90%</span></div>
    <div class="prog-track"><div class="prog-fill" style="width:90%;background:linear-gradient(90deg,#a000ff,#00e5ff);"></div></div>
  </div>
  <div class="prog-item">
    <div class="prog-head"><span class="prog-nm">Backend</span><span class="prog-pc">82%</span></div>
    <div class="prog-track"><div class="prog-fill" style="width:82%;background:linear-gradient(90deg,#a000ff,#39ff14);"></div></div>
  </div>
  <div class="prog-item">
    <div class="prog-head"><span class="prog-nm">UI / Diseño</span><span class="prog-pc">75%</span></div>
    <div class="prog-track"><div class="prog-fill" style="width:75%;background:linear-gradient(90deg,#ff3366,#a000ff);"></div></div>
  </div>
  <div class="prog-item">
    <div class="prog-head"><span class="prog-nm">DevOps / Cloud</span><span class="prog-pc">65%</span></div>
    <div class="prog-track"><div class="prog-fill" style="width:65%;background:linear-gradient(90deg,#ff9100,#ff3366);"></div></div>
  </div>
  <div class="prog-item">
    <div class="prog-head"><span class="prog-nm">Bases de Datos</span><span class="prog-pc">80%</span></div>
    <div class="prog-track"><div class="prog-fill" style="width:80%;background:linear-gradient(90deg,#ff9100,#00e5ff);"></div></div>
  </div>
  <div class="prog-item">
    <div class="prog-head"><span class="prog-nm">Problem Solving</span><span class="prog-pc">95%</span></div>
    <div class="prog-track"><div class="prog-fill" style="width:95%;background:linear-gradient(90deg,#ffd700,#39ff14);"></div></div>
  </div>
</div>

<!-- ═══ PANEL: PROJECTS ═══ -->
<div class="panel" id="panel-projects">
  <div class="stitle">◈ MISIONES COMPLETADAS</div>
  <div class="proj-grid">
    <div class="proj" onclick="sendPrompt('Cuéntame más del proyecto 1')">
      <div class="proj-stars">★★★★★ 24 stars</div>
      <div class="proj-title">Proyecto Épico #1</div>
      <div class="proj-desc">App full-stack que resuelve<br>problemas del mundo real.<br>Usuarios activos: 1,200+</div>
      <div class="proj-tech"><span>React</span><span>Node.js</span><span>MongoDB</span><span>AWS</span></div>
    </div>
    <div class="proj" onclick="sendPrompt('Cuéntame más del proyecto 2')">
      <div class="proj-stars">★★★★☆ 17 stars</div>
      <div class="proj-title">API REST Legendaria</div>
      <div class="proj-desc">Backend ultra-rápido con<br>auth JWT, docs Swagger<br>y deploy automático.</div>
      <div class="proj-tech"><span>Express</span><span>JWT</span><span>Docker</span><span>PostgreSQL</span></div>
    </div>
    <div class="proj" onclick="sendPrompt('Cuéntame más del proyecto 3')">
      <div class="proj-stars">★★★★☆ 9 stars</div>
      <div class="proj-title">Portfolio Pixel</div>
      <div class="proj-desc">Sitio personal con animaciones<br>pixel art, modo oscuro<br>y 100/100 en Lighthouse.</div>
      <div class="proj-tech"><span>Next.js</span><span>Tailwind</span><span>Framer</span></div>
    </div>
    <div class="proj" onclick="sendPrompt('Cuéntame más del proyecto 4')">
      <div class="proj-stars">★★★☆☆ 5 stars</div>
      <div class="proj-title">Bot Discord ⚡</div>
      <div class="proj-desc">Bot con comandos slash,<br>música, moderación y<br>integración con OpenAI.</div>
      <div class="proj-tech"><span>Discord.js</span><span>OpenAI</span><span>Node</span></div>
    </div>
    <div class="proj" onclick="sendPrompt('Cuéntame más del proyecto 5')">
      <div class="proj-stars">★★★★☆ 12 stars</div>
      <div class="proj-title">E-commerce Dashboard</div>
      <div class="proj-desc">Panel admin con métricas<br>en tiempo real, gráficas<br>y gestión de inventario.</div>
      <div class="proj-tech"><span>Vue.js</span><span>Firebase</span><span>Chart.js</span></div>
    </div>
    <div class="proj" style="border-style:dashed;cursor:default;opacity:0.5;">
      <div class="proj-stars" style="color:#666;">? ? ?</div>
      <div class="proj-title" style="color:#444;">????? ????</div>
      <div class="proj-desc" style="color:#333;">Próxima misión en<br>desarrollo...<br>Stay tuned 🚀</div>
      <div class="proj-tech"><span style="color:#333;border-color:#333;">???</span></div>
    </div>
  </div>
</div>

<!-- ═══ PANEL: ACHIEVEMENTS ═══ -->
<div class="panel" id="panel-achievements">
  <div class="stitle">◈ LOGROS DESBLOQUEADOS</div>
  <div class="ach-grid">
    <div class="ach">
      <span class="ach-unlocked">✓ UNLOCKED</span>
      <span class="ach-icon">💻</span>
      <div class="ach-name">PRIMER COMMIT</div>
      <div class="ach-desc">El viaje comienza con<br>una sola línea de código.</div>
    </div>
    <div class="ach">
      <span class="ach-unlocked">✓ UNLOCKED</span>
      <span class="ach-icon">🚀</span>
      <div class="ach-name">DEPLOY EN PROD</div>
      <div class="ach-desc">Sobreviviste tu primer<br>deploy a producción.</div>
    </div>
    <div class="ach">
      <span class="ach-unlocked">✓ UNLOCKED</span>
      <span class="ach-icon">🌙</span>
      <div class="ach-name">NOCHE DE BUGS</div>
      <div class="ach-desc">Codefixeaste hasta<br>las 3am. Sin dormir.</div>
    </div>
    <div class="ach">
      <span class="ach-unlocked">✓ UNLOCKED</span>
      <span class="ach-icon">🤝</span>
      <div class="ach-name">OPEN SOURCE</div>
      <div class="ach-desc">Primer pull request<br>aceptado en un repo.</div>
    </div>
    <div class="ach">
      <span class="ach-unlocked">✓ UNLOCKED</span>
      <span class="ach-icon">☕</span>
      <div class="ach-name">CAFEÍNA MAX</div>
      <div class="ach-desc">+100 commits hechos<br>con café puro.</div>
    </div>
    <div class="ach">
      <span class="ach-unlocked">✓ UNLOCKED</span>
      <span class="ach-icon">🌎</span>
      <div class="ach-name">MADE IN PANAMA</div>
      <div class="ach-desc">Desarrollador orgulloso<br>de Chiriquí 🇵🇦</div>
    </div>
    <div class="ach locked">
      <span class="ach-icon">🏆</span>
      <div class="ach-name">FULL STACK LEGEND</div>
      <div class="ach-desc">Domina todos los<br>niveles del stack.</div>
    </div>
    <div class="ach locked">
      <span class="ach-icon">🌟</span>
      <div class="ach-name">1K STARS</div>
      <div class="ach-desc">Un proyecto llega<br>a 1000 estrellas.</div>
    </div>
  </div>
</div>

<!-- ═══ PANEL: SOCIALS ═══ -->
<div class="panel" id="panel-socials">
  <div class="stitle">◈ CONECTAR CON EL HÉROE</div>
  <div class="soc-grid">
    <a class="soc gh" href="https://github.com/tuusuario" target="_blank">
      <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.48 2 2 6.48 2 12c0 4.42 2.87 8.17 6.84 9.49.5.09.66-.22.66-.48v-1.7c-2.78.6-3.37-1.34-3.37-1.34-.45-1.16-1.11-1.47-1.11-1.47-.91-.62.07-.61.07-.61 1 .07 1.53 1.03 1.53 1.03.89 1.52 2.34 1.08 2.91.83.09-.65.35-1.08.63-1.33-2.22-.25-4.55-1.11-4.55-4.94 0-1.09.39-1.98 1.03-2.68-.1-.25-.45-1.27.1-2.64 0 0 .84-.27 2.75 1.02A9.56 9.56 0 0 1 12 6.8c.85 0 1.71.11 2.51.33 1.91-1.29 2.75-1.02 2.75-1.02.55 1.37.2 2.39.1 2.64.64.7 1.03 1.59 1.03 2.68 0 3.84-2.34 4.68-4.57 4.93.36.31.68.92.68 1.85v2.74c0 .27.16.58.67.48A10.01 10.01 0 0 0 22 12c0-5.52-4.48-10-10-10z"/></svg>
      <div><div class="soc-label">GitHub</div><div class="soc-sub">@tuusuario</div></div>
    </a>
    <a class="soc ig" href="https://instagram.com/tuusuario" target="_blank">
      <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
      <div><div class="soc-label">Instagram</div><div class="soc-sub">@tuusuario</div></div>
    </a>
    <a class="soc li" href="https://linkedin.com/in/tuusuario" target="_blank">
      <svg viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
      <div><div class="soc-label">LinkedIn</div><div class="soc-sub">Tu Nombre</div></div>
    </a>
    <a class="soc tw" href="https://twitter.com/tuusuario" target="_blank">
      <svg viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.747l7.73-8.835L1.254 2.25H8.08l4.259 5.631zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
      <div><div class="soc-label">Twitter / X</div><div class="soc-sub">@tuusuario</div></div>
    </a>
    <a class="soc yt" href="https://youtube.com/@tuusuario" target="_blank">
      <svg viewBox="0 0 24 24" fill="currentColor"><path d="M23.498 6.186a3.016 3.016 0 0 0-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 0 0 .502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 0 0 2.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 0 0 2.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/></svg>
      <div><div class="soc-label">YouTube</div><div class="soc-sub">Tu Canal</div></div>
    </a>
    <a class="soc dc" href="https://discord.gg/tuservidor" target="_blank">
      <svg viewBox="0 0 24 24" fill="currentColor"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057c.002.022.015.04.033.05a19.899 19.899 0 0 0 5.993 3.03.078.078 0 0 0 .084-.028c.462-.63.874-1.295 1.226-1.994a.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.956 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.955-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.946 2.418-2.157 2.418z"/></svg>
      <div><div class="soc-label">Discord</div><div class="soc-sub">Tu servidor</div></div>
    </a>
  </div>

  <div class="divider" style="margin-top:20px;"><div class="div-line"></div><div class="div-icon">✉</div><div class="div-line"></div></div>
  <div style="text-align:center;margin-top:10px;">
    <div style="font-size:7px;color:#888;margin-bottom:10px;">¿Tienes un proyecto épico? ¡Hablemos!</div>
    <div style="font-size:8px;color:#a000ff;border:2px solid #a000ff;display:inline-block;padding:10px 20px;cursor:pointer;" onclick="sendPrompt('Quiero contactar al desarrollador')">
      ▶ ENVIAR MENSAJE
    </div>
  </div>
</div>

<!-- Footer -->
<div class="footer">
  <div class="footer-anim">◀ ■ ● ▲ ▶</div>
  MADE WITH ♥ + ☕ IN DAVID, CHIRIQUÍ 🇵🇦
  <div>© 2025 · INSERT COIN TO CONTINUE ████████░░ 80%</div>
</div>

</div>

<script>
// ─── Stars
const starsEl = document.getElementById('stars');
for(let i=0;i<80;i++){
  const s=document.createElement('div');
  s.className='star';
  const size=Math.random()*2.5+0.5;
  s.style.cssText=`left:${Math.random()*100}%;top:${Math.random()*100}%;width:${size}px;height:${size}px;--d:${2+Math.random()*4}s;animation-delay:${Math.random()*5}s;`;
  starsEl.appendChild(s);
}

// ─── Pixel sprite draw helper
function drawSprite(canvasId, scale=1){
  const c=document.getElementById(canvasId);
  if(!c)return;
  const ctx=c.getContext('2d');
  ctx.clearRect(0,0,c.width,c.height);
  const W=c.width,H=c.height;
  // colors
  const S='#a000ff',L='#c77dff',SK='#f5c5a3',H2='#2d1b00',B='#1a003a',SH='#7b0cf0',W2='#fff';
  // 12x16 sprite map (0=transparent)
  const sprite=[
    '000HHHHH000',
    '00HHHHHHH00',
    '00HSKSKSH00',
    '00HSSSSSH00',
    '00HSSSSSH00',
    '000HSSSH000',
    '00BSSSSSSB0',
    '0BBBSSSSBBB',
    '0BBBSSSSBB0',
    '00BBSSSSBB0',
    '00BSSSSSSB0',
    '000BSSSB000',
    '000BSSSB000',
    '000B000B000',
    '00BB000BB00',
    '0BBB000BBB0',
  ];
  const map={H:H2,S:SK,K:'#ff5555',B:S,SH:SH};
  const cmap={H:H2,S:SK,K:'#ff5555',B:'#a000ff',0:null};
  const pw=W/11,ph=H/16;
  sprite.forEach((row,y)=>{
    row.split('').forEach((ch,x)=>{
      const col=cmap[ch];
      if(col){ctx.fillStyle=col;ctx.fillRect(x*pw,y*ph,pw,ph);}
    });
  });
}

// ─── Animated character in scene
const charCanvas=document.getElementById('charCanvas');
let frame=0,waveFrame=0,facing=1;
const charSprites={
  walk0:[
    '000HHH000000',
    '00HHHHH00000',
    '00HSKSKH0000',
    '00HSSSSSH000',
    '000HSSSH0000',
    '00BSSSSB0000',
    '0BBBSSSBBB00',
    '00BBBSSBB000',
    '000BBSSB0000',
    '000BSSSSB000',
    '000B00SSB000',
    '00BB000BB000',
    '0BBB0000BB00',
  ],
  wave0:[
    '000HHH000000',
    '00HHHHH00000',
    '00HSKSKH0000',
    '00HSSSSSH000',
    '000HSSSH0000',
    '0BBSSSSB0000',
    'BBBSSSSBB000',
    '0BBBSSBBBB00',
    '00BBSSBB0000',
    '000BSSSSB000',
    '000BSSSSB000',
    '000B000B0000',
    '00BB000BB000',
  ],
  wave1:[
    '000HHH000000',
    '00HHHHH00000',
    '00HSKSKH0000',
    '00HSSSSSH000',
    '000HSSSH0000',
    '00BSSSSBBBB0',
    '0BBBSSSBBBBB',
    '00BBBSSBB000',
    '000BBSSB0000',
    '000BSSSSB000',
    '000B00SSB000',
    '00BB000BB000',
    '0BBB0000B000',
  ],
};

function drawChar(spriteData){
  if(!charCanvas)return;
  const ctx=charCanvas.getContext('2d');
  ctx.clearRect(0,0,charCanvas.width,charCanvas.height);
  const cmap={H:'#2d1b00',S:'#f5c5a3',K:'#ff5555',B:'#a000ff',0:null};
  const pw=charCanvas.width/12,ph=charCanvas.height/13;
  spriteData.forEach((row,y)=>{
    row.split('').forEach((ch,x)=>{
      const col=cmap[ch];
      if(col){ctx.fillStyle=col;ctx.fillRect(x*pw,y*ph,pw,ph);}
    });
  });
}

// Waving animation
let waveState=0;
setInterval(()=>{
  waveState=(waveState+1)%2;
  drawChar(waveState===0?charSprites.wave0:charSprites.wave1);
},350);

// Profile canvas
drawSprite('profileCanvas');

// ─── Tabs
function switchTab(id){
  document.querySelectorAll('.nav-tab').forEach((t,i)=>t.classList.remove('active'));
  document.querySelectorAll('.panel').forEach(p=>p.classList.remove('active'));
  const tabs=['profile','skills','projects','achievements','socials'];
  const idx=tabs.indexOf(id);
  if(idx>=0) document.querySelectorAll('.nav-tab')[idx].classList.add('active');
  const panel=document.getElementById('panel-'+id);
  if(panel) panel.classList.add('active');
}

// ─── Skill equip
let equipped=new Set();
function equipSkill(el){
  const name=el.textContent.trim();
  if(equipped.has(name)){
    equipped.delete(name);
    el.style.opacity='';
    el.style.transform='';
  } else {
    equipped.add(name);
    el.style.opacity='0.5';
    el.style.transform='scale(0.92)';
    // flash
    const orig=el.style.background;
    el.style.filter='brightness(2)';
    setTimeout(()=>el.style.filter='',150);
  }
}

// ─── Typewriter for hero name
const nameTarget='Tu Nombre';
let ni=0;
const nEl=document.getElementById('typedName');
function typeName(){
  if(ni<=nameTarget.length){
    nEl.textContent=nameTarget.slice(0,ni)+'_';
    ni++;
    setTimeout(typeName,85);
  } else {
    // blink cursor after done
    setInterval(()=>{
      nEl.textContent=nameTarget+(nEl.textContent.endsWith('_')?'':'_');
    },500);
  }
}
setTimeout(typeName,400);

// ─── Dialog typewriter
const messages=[
  'Bienvenido a mi perfil!',
  'Soy Full Stack Developer.',
  'David, Chiriqui, Panama.',
  'Disponible para proyectos!',
  'Haz clic en las tabs...',
];
let msgIdx=0,charIdx=0;
const dEl=document.getElementById('dialogText');
function typeDialog(){
  if(!dEl)return;
  const msg=messages[msgIdx];
  if(charIdx<msg.length){
    dEl.innerHTML=msg.slice(0,++charIdx)+'<span class="cursor-blink">█</span>';
    setTimeout(typeDialog,55);
  } else {
    setTimeout(()=>{
      charIdx=0;
      msgIdx=(msgIdx+1)%messages.length;
      typeDialog();
    },2200);
  }
}
setTimeout(typeDialog,1200);

// ─── Count-up stats
function countUp(id,target,duration=1500){
  const el=document.getElementById(id);
  if(!el)return;
  let start=null;
  const step=ts=>{
    if(!start)start=ts;
    const p=Math.min((ts-start)/duration,1);
    el.textContent=Math.floor(p*target)+(p<1?'':'');
    if(p<1)requestAnimationFrame(step);
  };
  requestAnimationFrame(step);
}
setTimeout(()=>{
  countUp('sRepos',42);
  countUp('sCommits',312,2000);
  countUp('sProj',7,1200);
  countUp('sYears',3,1000);
  countUp('sPRs',89,1800);
},300);

// ─── HUD hearts blink on hover
document.querySelector('.hud-hearts').addEventListener('click',()=>{
  const h=document.querySelector('.hud-hearts');
  h.style.color='#fff';
  setTimeout(()=>h.style.color='#ff3366',200);
});
</script>
