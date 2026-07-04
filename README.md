<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Serge Melchik MACKITA — Portfolio</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600;700&family=Manrope:wght@300;400;500;600;700;800&display=swap');

  :root{
    --bg-0:#070c0a;
    --bg-1:#0c1613;
    --bg-2:#111f1a;
    --moss:#173026;
    --fern:#1f7a4d;
    --leaf:#3ee08c;
    --leaf-soft:#8ff5c0;
    --dew:#5fd9d9;
    --amber:#e8b84b;
    --bark:#8a9a91;
    --paper:#eef5f0;
    --line: rgba(62,224,140,0.16);
  }

  *{box-sizing:border-box; margin:0; padding:0;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--bg-0);
    color:var(--paper);
    font-family:'Manrope', sans-serif;
    overflow-x:hidden;
    position:relative;
  }
  ::selection{background:var(--fern); color:#04140c;}

  a{color:inherit; text-decoration:none;}

  /* ---------- Ambient nature canvas (fireflies + mycelium network) ---------- */
  #veil{
    position:fixed; inset:0; z-index:0; pointer-events:none;
    background:
      radial-gradient(ellipse 70% 45% at 18% 8%, rgba(62,224,140,0.14), transparent 60%),
      radial-gradient(ellipse 60% 40% at 85% 15%, rgba(95,217,217,0.10), transparent 60%),
      radial-gradient(ellipse 80% 60% at 50% 100%, rgba(31,122,77,0.20), transparent 65%);
  }
  #canvas-fireflies{
    position:fixed; inset:0; z-index:0; width:100%; height:100%; pointer-events:none;
    opacity:0.9;
  }
  .grain{
    position:fixed; inset:0; z-index:1; pointer-events:none; opacity:0.035; mix-blend-mode:overlay;
    background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='120' height='120'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  }

  .wrap{position:relative; z-index:2; max-width:1180px; margin:0 auto; padding:0 32px;}

  /* ---------- Nav ---------- */
  nav{
    position:sticky; top:0; z-index:20;
    backdrop-filter: blur(14px);
    background:rgba(7,12,10,0.72);
    border-bottom:1px solid var(--line);
  }
  nav .wrap{display:flex; align-items:center; justify-content:space-between; padding-top:18px; padding-bottom:18px;}
  .brand{font-family:'JetBrains Mono', monospace; font-weight:700; font-size:15px; letter-spacing:0.5px; color:var(--leaf-soft);}
  .brand span{color:var(--bark);}
  .navlinks{display:flex; gap:30px; font-size:13.5px; font-family:'JetBrains Mono',monospace;}
  .navlinks a{color:var(--bark); position:relative; padding-bottom:3px; transition:color .25s;}
  .navlinks a:hover{color:var(--leaf-soft);}
  .navlinks a::after{content:""; position:absolute; left:0; bottom:0; width:0; height:1px; background:var(--leaf); transition:width .25s;}
  .navlinks a:hover::after{width:100%;}
  @media (max-width:760px){ .navlinks{display:none;} }

  /* ---------- Hero ---------- */
  .hero{position:relative; padding:96px 0 84px; min-height:88vh; display:flex; align-items:center;}
  .hero-grid{display:grid; grid-template-columns:1.15fr 0.85fr; gap:56px; align-items:center; width:100%;}
  @media (max-width:860px){ .hero-grid{grid-template-columns:1fr; text-align:left;} .hero{padding:56px 0;} }

  .eyebrow{
    font-family:'JetBrains Mono', monospace; font-size:12.5px; letter-spacing:2.5px; text-transform:uppercase;
    color:var(--leaf); display:flex; align-items:center; gap:10px; margin-bottom:22px;
  }
  .eyebrow .dot{width:7px; height:7px; border-radius:50%; background:var(--leaf); box-shadow:0 0 12px 3px rgba(62,224,140,0.7); animation:pulse-dot 2.4s ease-in-out infinite;}
  @keyframes pulse-dot{ 0%,100%{opacity:1; transform:scale(1);} 50%{opacity:.4; transform:scale(0.7);} }

  h1.name{
    font-family:'Space Grotesk', sans-serif; font-weight:700;
    font-size:clamp(38px, 6vw, 64px); line-height:1.02; letter-spacing:-1.2px;
    color:var(--paper); margin-bottom:6px;
  }
  h1.name em{
    font-style:normal;
    background:linear-gradient(100deg, var(--leaf-soft), var(--dew) 60%, var(--leaf));
    -webkit-background-clip:text; background-clip:text; color:transparent;
  }
  .roles{
    font-family:'JetBrains Mono', monospace; font-size:15px; color:var(--bark);
    margin:18px 0 26px; display:flex; flex-wrap:wrap; gap:10px 0;
  }
  .roles .r{padding:0 14px; border-right:1px solid var(--line);}
  .roles .r:first-child{padding-left:0;}
  .roles .r:last-child{border-right:none;}

  .lede{font-size:17px; line-height:1.75; color:#c9d9d0; max-width:52ch; margin-bottom:34px;}

  .cta-row{display:flex; flex-wrap:wrap; gap:14px;}
  .btn{
    font-family:'JetBrains Mono', monospace; font-size:13px; letter-spacing:0.3px;
    padding:13px 22px; border-radius:8px; display:inline-flex; align-items:center; gap:9px;
    transition:transform .2s, box-shadow .2s, background .2s;
  }
  .btn-primary{
    background:linear-gradient(135deg, var(--fern), #0e5c37);
    color:#eafff2; border:1px solid rgba(62,224,140,0.5);
    box-shadow:0 0 0 rgba(62,224,140,0);
  }
  .btn-primary:hover{ box-shadow:0 6px 30px -6px rgba(62,224,140,0.55); transform:translateY(-2px); }
  .btn-ghost{ border:1px solid var(--line); color:var(--paper); background:rgba(255,255,255,0.02); }
  .btn-ghost:hover{ border-color:var(--leaf); color:var(--leaf-soft); transform:translateY(-2px); }

  .portrait-wrap{position:relative; display:flex; justify-content:center;}
  .portrait-ring{
    position:relative; width:min(320px, 78vw); aspect-ratio:1/1; border-radius:50%;
    padding:6px;
    background:conic-gradient(from 210deg, var(--fern), var(--dew), var(--amber), var(--fern));
    animation:spin-ring 14s linear infinite;
  }
  @keyframes spin-ring{ to{ transform:rotate(360deg);} }
  .portrait-inner{
    width:100%; height:100%; border-radius:50%; overflow:hidden; background:var(--bg-1);
    border:5px solid var(--bg-0);
  }
  .portrait-inner img{width:100%; height:100%; object-fit:cover; object-position:center 18%; filter:saturate(1.05) contrast(1.03);}
  .portrait-glow{
    position:absolute; inset:-18px; border-radius:50%; z-index:-1;
    background:radial-gradient(circle, rgba(62,224,140,0.35), transparent 68%);
    filter:blur(18px);
    animation:breathe 4.5s ease-in-out infinite;
  }
  @keyframes breathe{ 0%,100%{opacity:0.55; transform:scale(0.96);} 50%{opacity:0.95; transform:scale(1.04);} }
  .loc-badge{
    position:absolute; bottom:8px; left:50%; transform:translateX(-50%);
    background:rgba(7,20,14,0.85); border:1px solid var(--line); backdrop-filter:blur(6px);
    padding:7px 16px; border-radius:999px; font-family:'JetBrains Mono',monospace; font-size:12px;
    color:var(--leaf-soft); white-space:nowrap;
  }

  /* ---------- Section shell ---------- */
  section{position:relative; z-index:2; padding:104px 0;}
  .sec-head{margin-bottom:52px;}
  .sec-eyebrow{font-family:'JetBrains Mono',monospace; font-size:12px; letter-spacing:3px; text-transform:uppercase; color:var(--fern); margin-bottom:10px;}
  .sec-title{font-family:'Space Grotesk',sans-serif; font-weight:700; font-size:clamp(26px,3.4vw,38px); letter-spacing:-0.5px; color:var(--paper);}
  .sec-title .accent{color:var(--leaf-soft);}
  .sec-sub{color:var(--bark); max-width:60ch; margin-top:12px; line-height:1.7; font-size:15px;}

  hr.divider{border:none; height:1px; background:linear-gradient(90deg, transparent, var(--line) 20%, var(--line) 80%, transparent);}

  /* ---------- About ---------- */
  .about-grid{display:grid; grid-template-columns:1.3fr 1fr; gap:60px;}
  @media (max-width:860px){ .about-grid{grid-template-columns:1fr;} }
  .about-text p{font-size:16px; line-height:1.85; color:#cbdcd3; margin-bottom:18px;}
  .about-text .quote{
    margin-top:26px; padding:20px 24px; border-left:2px solid var(--fern);
    background:rgba(62,224,140,0.05); font-family:'Space Grotesk',sans-serif; font-style:italic;
    color:var(--leaf-soft); font-size:15px; line-height:1.6;
  }
  .stat-col{display:flex; flex-direction:column; gap:20px;}
  .stat{
    border:1px solid var(--line); border-radius:12px; padding:22px 24px;
    background:linear-gradient(160deg, rgba(31,122,77,0.08), rgba(255,255,255,0.01));
    transition:border-color .25s, transform .25s;
  }
  .stat:hover{border-color:var(--fern); transform:translateY(-3px);}
  .stat .num{font-family:'Space Grotesk',sans-serif; font-weight:700; font-size:28px; color:var(--leaf-soft);}
  .stat .lbl{font-size:13px; color:var(--bark); margin-top:4px;}

  /* ---------- Skills ---------- */
  .skill-cols{display:grid; grid-template-columns:repeat(3,1fr); gap:28px;}
  @media (max-width:900px){ .skill-cols{grid-template-columns:1fr;} }
  .skill-card{
    border:1px solid var(--line); border-radius:14px; padding:28px 26px; position:relative; overflow:hidden;
    background:linear-gradient(180deg, rgba(255,255,255,0.015), transparent);
  }
  .skill-card::before{
    content:""; position:absolute; top:-40%; left:-20%; width:70%; height:70%; border-radius:50%;
    background:radial-gradient(circle, var(--glow, rgba(62,224,140,0.16)), transparent 70%);
    pointer-events:none;
  }
  .skill-card h3{font-family:'Space Grotesk',sans-serif; font-size:18px; color:var(--paper); margin-bottom:6px; position:relative;}
  .skill-card .tag{font-family:'JetBrains Mono',monospace; font-size:11px; color:var(--bark); text-transform:uppercase; letter-spacing:1.5px; margin-bottom:18px; display:block; position:relative;}
  .chips{display:flex; flex-wrap:wrap; gap:8px; position:relative;}
  .chip{
    font-family:'JetBrains Mono',monospace; font-size:12px; padding:7px 12px; border-radius:7px;
    border:1px solid var(--line); color:#d5e6dd; background:rgba(255,255,255,0.02);
    transition:all .2s;
  }
  .chip:hover{ border-color:var(--leaf); color:var(--leaf-soft); background:rgba(62,224,140,0.08); transform:translateY(-2px); }

  /* ---------- Timeline ---------- */
  .timeline{position:relative; padding-left:32px;}
  .timeline::before{content:""; position:absolute; left:6px; top:6px; bottom:6px; width:2px; background:linear-gradient(180deg, var(--fern), var(--dew), transparent);}
  .tl-item{position:relative; padding-bottom:52px;}
  .tl-item:last-child{padding-bottom:0;}
  .tl-dot{
    position:absolute; left:-32px; top:4px; width:14px; height:14px; border-radius:50%;
    background:var(--bg-0); border:2px solid var(--leaf); box-shadow:0 0 14px 2px rgba(62,224,140,0.5);
  }
  .tl-period{font-family:'JetBrains Mono',monospace; font-size:12px; color:var(--fern); letter-spacing:1px; margin-bottom:6px;}
  .tl-role{font-family:'Space Grotesk',sans-serif; font-weight:600; font-size:19px; color:var(--paper); margin-bottom:2px;}
  .tl-org{font-size:14px; color:var(--bark); margin-bottom:14px;}
  .tl-list{list-style:none; display:flex; flex-direction:column; gap:9px;}
  .tl-list li{font-size:14.5px; line-height:1.65; color:#c4d6cb; padding-left:18px; position:relative;}
  .tl-list li::before{content:"◆"; position:absolute; left:0; top:1px; font-size:8px; color:var(--dew);}
  .tl-list li b{color:var(--leaf-soft); font-weight:600;}

  /* ---------- Projects ---------- */
  .proj-grid{display:grid; grid-template-columns:1fr 1fr; gap:28px;}
  @media (max-width:860px){ .proj-grid{grid-template-columns:1fr;} }
  .proj-card{
    border:1px solid var(--line); border-radius:16px; padding:32px; position:relative; overflow:hidden;
    background:linear-gradient(165deg, rgba(17,31,26,0.6), rgba(7,12,10,0.4));
  }
  .proj-card::after{
    content:""; position:absolute; right:-60px; bottom:-60px; width:180px; height:180px; border-radius:50%;
    background:radial-gradient(circle, rgba(95,217,217,0.14), transparent 70%);
  }
  .proj-icon{font-size:26px; margin-bottom:16px;}
  .proj-card h3{font-family:'Space Grotesk',sans-serif; font-size:20px; color:var(--paper); margin-bottom:6px;}
  .proj-status{
    display:inline-block; font-family:'JetBrains Mono',monospace; font-size:11px; color:var(--leaf-soft);
    border:1px solid var(--fern); padding:3px 10px; border-radius:999px; margin-bottom:16px;
  }
  .proj-card p.desc{color:#bcd0c4; font-size:14.5px; line-height:1.65; margin-bottom:18px;}
  .proj-feats{list-style:none; display:flex; flex-direction:column; gap:8px; margin-bottom:20px;}
  .proj-feats li{font-size:13.5px; color:#c4d6cb; padding-left:16px; position:relative; line-height:1.5;}
  .proj-feats li::before{content:"›"; position:absolute; left:0; color:var(--dew); font-weight:700;}
  .proj-stack{display:flex; flex-wrap:wrap; gap:7px;}
  .stack-pill{font-family:'JetBrains Mono',monospace; font-size:10.5px; padding:5px 10px; border-radius:6px; background:rgba(255,255,255,0.04); color:var(--bark);}

  .impact-row{display:grid; grid-template-columns:repeat(4,1fr); gap:18px; margin-top:44px;}
  @media (max-width:700px){ .impact-row{grid-template-columns:repeat(2,1fr);} }
  .impact-card{text-align:center; border:1px solid var(--line); border-radius:12px; padding:24px 10px;}
  .impact-card .num{font-family:'Space Grotesk',sans-serif; font-weight:700; font-size:26px; color:var(--leaf-soft);}
  .impact-card .lbl{font-size:12px; color:var(--bark); margin-top:6px;}

  /* ---------- Education / Certs ---------- */
  .edu-grid{display:grid; grid-template-columns:1fr 1fr; gap:40px;}
  @media (max-width:860px){ .edu-grid{grid-template-columns:1fr;} }
  .edu-block h4{font-family:'JetBrains Mono',monospace; font-size:12px; letter-spacing:2px; text-transform:uppercase; color:var(--fern); margin-bottom:20px;}
  .edu-entry{border-bottom:1px solid var(--line); padding:18px 0;}
  .edu-entry:first-of-type{padding-top:0;}
  .edu-entry:last-child{border-bottom:none;}
  .edu-title{font-family:'Space Grotesk',sans-serif; font-weight:600; font-size:16px; color:var(--paper);}
  .edu-org{font-size:13px; color:var(--bark); margin:3px 0 6px;}
  .edu-period{font-family:'JetBrains Mono',monospace; font-size:11.5px; color:var(--dew);}
  .edu-desc{font-size:13.5px; color:#bcd0c4; margin-top:8px; line-height:1.6;}

  /* ---------- Languages / interests ---------- */
  .misc-row{display:grid; grid-template-columns:1fr 1fr; gap:40px;}
  @media (max-width:760px){ .misc-row{grid-template-columns:1fr;} }
  .pill-group{display:flex; flex-wrap:wrap; gap:10px;}
  .lang-pill{
    border:1px solid var(--line); border-radius:999px; padding:9px 18px; font-family:'JetBrains Mono',monospace; font-size:13px;
    display:flex; align-items:center; gap:8px; color:var(--paper);
  }
  .lang-pill .lvl{width:6px; height:6px; border-radius:50%; background:var(--leaf); box-shadow:0 0 8px 1px rgba(62,224,140,0.6);}

  /* ---------- Footer / contact ---------- */
  footer{position:relative; z-index:2; padding:100px 0 60px; text-align:center; border-top:1px solid var(--line); margin-top:40px;}
  footer h2{font-family:'Space Grotesk',sans-serif; font-weight:700; font-size:clamp(28px,4vw,44px); margin-bottom:18px;}
  footer h2 em{font-style:normal; color:var(--leaf-soft);}
  footer .sub{color:var(--bark); max-width:50ch; margin:0 auto 36px; line-height:1.7;}
  .contact-row{display:flex; flex-wrap:wrap; gap:16px; justify-content:center; margin-bottom:56px;}
  .foot-bottom{font-family:'JetBrains Mono',monospace; font-size:12px; color:var(--bark); opacity:0.7;}
  .foot-bottom span{color:var(--leaf);}

  @media (prefers-reduced-motion: reduce){
    *{animation:none !important; transition:none !important;}
  }
</style>
</head>
<body>

<div id="veil"></div>
<canvas id="canvas-fireflies"></canvas>
<div class="grain"></div>

<nav>
  <div class="wrap">
    <div class="brand">SERGE<span>·</span>MACKITA</div>
    <div class="navlinks">
      <a href="#about">Profil</a>
      <a href="#skills">Compétences</a>
      <a href="#experience">Expérience</a>
      <a href="#projects">Projets</a>
      <a href="#education">Formation</a>
      <a href="#contact">Contact</a>
    </div>
  </div>
</nav>

<header class="hero">
  <div class="wrap hero-grid">
    <div>
      <div class="eyebrow"><span class="dot"></span> Disponible pour de nouvelles opportunités</div>
      <h1 class="name">Serge Melchik<br><em>MACKITA</em></h1>
      <div class="roles">
        <span class="r">Architecte des Réseaux</span>
        <span class="r">Développeur Web</span>
        <span class="r">Cybersécurité</span>
        <span class="r">Support IT</span>
      </div>
      <p class="lede">Informaticien polyvalent — je conçois des réseaux robustes, je sécurise les infrastructures et je développe des solutions web complètes. Bac+3 en réseaux &amp; cybersécurité, certifié CCNA, avec une expérience de terrain en support et maintenance.</p>
      <div class="cta-row">
        <a class="btn btn-primary" href="mailto:mackitamelchick@gmail.com">✉ Me contacter</a>
        <a class="btn btn-ghost" href="tel:+242068991799">📞 +242 06 899 17 99</a>
      </div>
    </div>
    <div class="portrait-wrap">
      <div class="portrait-ring">
        <div class="portrait-glow"></div>
        <div class="portrait-inner">
          <img src="data:image/jpeg;base64,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" alt="Serge Melchik Mackita">
        </div>
      </div>
      <div class="loc-badge">📍 Pointe-Noire, Congo</div>
    </div>
  </div>
</header>

<section id="about">
  <div class="wrap">
    <div class="sec-head">
      <div class="sec-eyebrow">Profil</div>
      <div class="sec-title">Comprendre la panne, la <span class="accent">prévenir</span>, l'automatiser</div>
    </div>
    <div class="about-grid">
      <div class="about-text">
        <p>Informaticien polyvalent passionné par les systèmes, les réseaux, le développement web, la cybersécurité et le support informatique. Titulaire d'un niveau Bac+3 en informatique et d'une certification en réseaux informatiques (CCNA), reconnu pour son sens de l'organisation, sa rigueur et son esprit d'analyse.</p>
        <p>Motivé, autonome et orienté solutions, je mets mes compétences au service d'entreprises dynamiques tout en poursuivant mon développement professionnel — avec l'ambition de devenir un référent en cybersécurité défensive tout en continuant à concevoir des solutions web robustes et optimisées.</p>
        <div class="quote">« L'excellence en IT se reconnaît à la capacité de rendre l'invisible, indispensable. »</div>
      </div>
      <div class="stat-col">
        <div class="stat"><div class="num">Bac+3</div><div class="lbl">Réseaux &amp; Cybersécurité — ESIET-UAS, Tunis</div></div>
        <div class="stat"><div class="num">CCNA</div><div class="lbl">Cisco Certified Network Associate</div></div>
        <div class="stat"><div class="num">5+ ans</div><div class="lbl">Terrain — support &amp; maintenance réseau</div></div>
      </div>
    </div>
  </div>
</section>

<hr class="divider">

<section id="skills">
  <div class="wrap">
    <div class="sec-head">
      <div class="sec-eyebrow">Stack technique</div>
      <div class="sec-title">Une palette taillée pour l'<span class="accent">excellence opérationnelle</span></div>
      <p class="sec-sub">Trois domaines complémentaires — réseau, développement, systèmes — qui se renforcent mutuellement sur le terrain.</p>
    </div>
    <div class="skill-cols">
      <div class="skill-card" style="--glow: rgba(62,224,140,0.18)">
        <h3>🛡️ Réseaux &amp; Cybersécurité</h3>
        <span class="tag">Domaine de prédilection</span>
        <div class="chips">
          <span class="chip">TCP/IP</span><span class="chip">Câblage structuré</span><span class="chip">LAN/WAN</span>
          <span class="chip">VLAN</span><span class="chip">Routage dynamique</span><span class="chip">Dépannage N1/N2</span>
          <span class="chip">Pare-feu</span><span class="chip">VPN</span><span class="chip">Sécurité endpoints</span><span class="chip">Analyse de menaces</span>
        </div>
      </div>
      <div class="skill-card" style="--glow: rgba(232,184,75,0.16)">
        <h3>💻 Développement Web &amp; SEO</h3>
        <span class="tag">Conception full-stack</span>
        <div class="chips">
          <span class="chip">HTML5</span><span class="chip">CSS3</span><span class="chip">JavaScript</span><span class="chip">PHP</span>
          <span class="chip">MySQL</span><span class="chip">APIs REST</span><span class="chip">Git</span>
          <span class="chip">SEO On-Page</span><span class="chip">SEO Technique</span><span class="chip">Mots-clés</span>
        </div>
      </div>
      <div class="skill-card" style="--glow: rgba(95,217,217,0.18)">
        <h3>🖥️ Systèmes &amp; Outils</h3>
        <span class="tag">Support &amp; maintenance</span>
        <div class="chips">
          <span class="chip">Windows 10/11</span><span class="chip">Windows Server</span><span class="chip">Active Directory</span>
          <span class="chip">Linux (bases)</span><span class="chip">Diagnostic hardware</span><span class="chip">Microsoft 365</span>
          <span class="chip">Photoshop</span><span class="chip">Premiere Pro</span><span class="chip">Illustrator</span>
        </div>
      </div>
    </div>
  </div>
</section>

<hr class="divider">

<section id="experience">
  <div class="wrap">
    <div class="sec-head">
      <div class="sec-eyebrow">Parcours</div>
      <div class="sec-title">Expérience <span class="accent">professionnelle</span></div>
    </div>
    <div class="timeline">
      <div class="tl-item">
        <div class="tl-dot"></div>
        <div class="tl-period">05 JANV 2024 — 30 JUIN 2026</div>
        <div class="tl-role">Alternant en réseau informatique &amp; secrétariat</div>
        <div class="tl-org">COLOTRA — Conseil Logistique et Transport</div>
        <ul class="tl-list">
          <li>Assistance aux utilisateurs : <b>installation de logiciels</b>, résolution de problèmes réseau simples.</li>
          <li>Gestion et maintenance du parc informatique (PC, imprimantes, connexions réseau).</li>
          <li>Support réseau : câblage, vérification de connexion, <b>dépannage de premier niveau</b>.</li>
          <li>Saisie et traitement de documents administratifs, rédaction de comptes rendus.</li>
          <li>Appui à la direction dans la gestion des rendez-vous et du planning.</li>
        </ul>
      </div>
      <div class="tl-item">
        <div class="tl-dot"></div>
        <div class="tl-period">MARS 2021 — SEPT 2023</div>
        <div class="tl-role">Assistant Technique — Réseau Informatique</div>
        <div class="tl-org">Micro Finance LE CHRIST-VIT</div>
        <ul class="tl-list">
          <li>Support technique aux utilisateurs, augmentant la satisfaction client de <b>+20%</b>.</li>
          <li>Gestion du parc informatique, optimisant la disponibilité des équipements de <b>+15%</b>.</li>
          <li>Câblage réseau et vérifications de connexion — taux de résolution N1 de <b>90%</b>.</li>
          <li>Traitement administratif et classement optimisé des documents.</li>
          <li>Collaboration avec la direction pour une planification hebdomadaire sans faille.</li>
        </ul>
      </div>
    </div>
  </div>
</section>

<hr class="divider">

<section id="projects">
  <div class="wrap">
    <div class="sec-head">
      <div class="sec-eyebrow">Projet D-CLIC · OIF</div>
      <div class="sec-title">Réalisations pour l'<span class="accent">Organisation Internationale de la Francophonie</span></div>
      <p class="sec-sub">Deux plateformes conçues et développées de bout en bout, 2025 – 2026, en coordination avec une équipe multiculturelle de développeurs.</p>
    </div>
    <div class="proj-grid">
      <div class="proj-card">
        <div class="proj-icon">🛍️</div>
        <span class="proj-status">Terminé</span>
        <h3>Boutique en ligne — Site e-commerce</h3>
        <p class="desc">Un site marchand complet, de la conception à l'optimisation SEO.</p>
        <ul class="proj-feats">
          <li>Catalogue produits avec filtres dynamiques</li>
          <li>Panier &amp; tunnel de commande</li>
          <li>Back-office admin (stocks, commandes)</li>
          <li>Authentification &amp; espace client sécurisés</li>
          <li>SEO On-Page intégral (balisage, schema.org)</li>
        </ul>
        <div class="proj-stack">
          <span class="stack-pill">HTML5</span><span class="stack-pill">CSS3</span><span class="stack-pill">JavaScript</span><span class="stack-pill">PHP</span><span class="stack-pill">MySQL</span>
        </div>
      </div>
      <div class="proj-card">
        <div class="proj-icon">🎓</div>
        <span class="proj-status">Terminé</span>
        <h3>Plateforme de formation en ligne</h3>
        <p class="desc">Un LMS sur mesure pour la diffusion de cours et le suivi pédagogique.</p>
        <ul class="proj-feats">
          <li>Cours avec modules et leçons</li>
          <li>Quiz interactifs et évaluations notées</li>
          <li>Suivi de progression par apprenant</li>
          <li>Certificats PDF générés automatiquement</li>
          <li>Forum de discussion intégré par cours</li>
        </ul>
        <div class="proj-stack">
          <span class="stack-pill">HTML5</span><span class="stack-pill">CSS3</span><span class="stack-pill">JavaScript</span><span class="stack-pill">PHP</span><span class="stack-pill">MySQL</span>
        </div>
      </div>
    </div>
    <div class="impact-row">
      <div class="impact-card"><div class="num">+40%</div><div class="lbl">Trafic organique</div></div>
      <div class="impact-card"><div class="num">+30%</div><div class="lbl">Engagement utilisateur</div></div>
      <div class="impact-card"><div class="num">&gt;90/100</div><div class="lbl">Score SEO</div></div>
      <div class="impact-card"><div class="num">Top 10</div><div class="lbl">Mots-clés ciblés</div></div>
    </div>
  </div>
</section>

<hr class="divider">

<section id="education">
  <div class="wrap">
    <div class="sec-head">
      <div class="sec-eyebrow">Formation</div>
      <div class="sec-title">Éducation &amp; <span class="accent">Certifications</span></div>
    </div>
    <div class="edu-grid">
      <div class="edu-block">
        <h4>Éducation</h4>
        <div class="edu-entry">
          <div class="edu-title">Bac+3 — Réseau informatique / Cybersécurité</div>
          <div class="edu-org">ESIET-UAS, Tunis (cours en ligne / visio)</div>
          <div class="edu-period">2023 – 2026</div>
          <div class="edu-desc">Systèmes de réseaux et cybersécurité, projets pratiques, mise en œuvre de stratégies de sécurité et ateliers d'innovation.</div>
        </div>
        <div class="edu-entry">
          <div class="edu-title">Baccalauréat Série D</div>
          <div class="edu-org">Le Tabernacle de Dieu</div>
          <div class="edu-period">2022 – 2023</div>
        </div>
      </div>
      <div class="edu-block">
        <h4>Certifications</h4>
        <div class="edu-entry">
          <div class="edu-title">Cisco Certified Network Associate (CCNA)</div>
          <div class="edu-org">Centre Supérieur de Technologies SKILLGAT, Côte d'Ivoire</div>
          <div class="edu-period">Oct 2024 – Fév 2025</div>
        </div>
        <div class="edu-entry">
          <div class="edu-title">Référencement Naturel — SEO / Développement Web</div>
          <div class="edu-org">OIF — Projet D-CLIC, Pointe-Noire</div>
          <div class="edu-period">Fév 2025 – Déc 2025</div>
        </div>
        <div class="edu-entry">
          <div class="edu-title">Maintenance et Réseaux informatiques</div>
          <div class="edu-org">GODWILL-FORMATION</div>
          <div class="edu-period">Juin – Sept 2018</div>
        </div>
        <div class="edu-entry">
          <div class="edu-title">Infographie &amp; Design graphique</div>
          <div class="edu-org">GODWILL-FORMATION</div>
          <div class="edu-period">2017</div>
        </div>
      </div>
    </div>
  </div>
</section>

<hr class="divider">

<section id="misc">
  <div class="wrap">
    <div class="misc-row">
      <div>
        <h4 class="tl-role" style="font-size:15px; margin-bottom:16px; color:var(--fern); font-family:'JetBrains Mono',monospace; letter-spacing:1px; text-transform:uppercase;">Langues</h4>
        <div class="pill-group">
          <span class="lang-pill"><span class="lvl"></span>Français</span>
          <span class="lang-pill"><span class="lvl"></span>Anglais (technique)</span>
          <span class="lang-pill"><span class="lvl"></span>Lingala</span>
          <span class="lang-pill"><span class="lvl"></span>Kituba</span>
        </div>
      </div>
      <div>
        <h4 class="tl-role" style="font-size:15px; margin-bottom:16px; color:var(--fern); font-family:'JetBrains Mono',monospace; letter-spacing:1px; text-transform:uppercase;">Centres d'intérêt</h4>
        <div class="pill-group">
          <span class="lang-pill">📖 Lecture</span>
          <span class="lang-pill">⚽ Sports</span>
          <span class="lang-pill">🎵 Musique</span>
          <span class="lang-pill">🔎 Recherche</span>
        </div>
      </div>
    </div>
  </div>
</section>

<footer id="contact">
  <div class="wrap">
    <h2>Construisons quelque chose de <em>solide</em>.</h2>
    <p class="sub">Disponible pour des missions en réseau, cybersécurité, développement web ou support IT — à Pointe-Noire ou à distance.</p>
    <div class="contact-row">
      <a class="btn btn-primary" href="mailto:mackitamelchick@gmail.com">✉ mackitamelchick@gmail.com</a>
      <a class="btn btn-ghost" href="tel:+242068991799">📞 +242 06 899 17 99</a>
    </div>
    <div class="foot-bottom">© 2026 Serge Melchik Mackita <span>·</span> Pointe-Noire, Congo <span>·</span> Conçu avec rigueur et une touche de forêt luminescente</div>
  </div>
</footer>

<script>
// Bioluminescent firefly-network canvas — ambient, reduced-motion aware
(function(){
  const canvas = document.getElementById('canvas-fireflies');
  const ctx = canvas.getContext('2d');
  let w, h, particles, reduced;

  reduced = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  function resize(){
    w = canvas.width = window.innerWidth;
    h = canvas.height = document.documentElement.scrollHeight;
  }
  window.addEventListener('resize', resize);
  resize();

  const COUNT = Math.min(70, Math.floor(w/22));
  const colors = ['62,224,140', '95,217,217', '232,184,75', '143,245,192'];

  function makeParticle(){
    return {
      x: Math.random()*w,
      y: Math.random()*h,
      vx: (Math.random()-0.5)*0.15,
      vy: (Math.random()-0.5)*0.15,
      r: Math.random()*1.8+0.6,
      c: colors[Math.floor(Math.random()*colors.length)],
      phase: Math.random()*Math.PI*2,
      speed: 0.01+Math.random()*0.015
    };
  }
  particles = Array.from({length: COUNT}, makeParticle);

  let t = 0;
  function tick(){
    t += 1;
    ctx.clearRect(0,0,w,h);

    // update
    particles.forEach(p=>{
      p.x += p.vx; p.y += p.vy;
      if(p.x < -20) p.x = w+20; if(p.x > w+20) p.x = -20;
      if(p.y < -20) p.y = h+20; if(p.y > h+20) p.y = -20;
      p.phase += p.speed;
    });

    // connections (mycelium threads)
    for(let i=0;i<particles.length;i++){
      for(let j=i+1;j<particles.length;j++){
        const a = particles[i], b = particles[j];
        const dx = a.x-b.x, dy = a.y-b.y;
        const dist = Math.sqrt(dx*dx+dy*dy);
        if(dist < 150){
          const op = (1 - dist/150) * 0.18;
          ctx.strokeStyle = `rgba(62,224,140,${op})`;
          ctx.lineWidth = 0.6;
          ctx.beginPath();
          ctx.moveTo(a.x,a.y);
          ctx.lineTo(b.x,b.y);
          ctx.stroke();
        }
      }
    }

    // glow dots
    particles.forEach(p=>{
      const flicker = 0.5 + 0.5*Math.sin(p.phase);
      const alpha = 0.35 + flicker*0.55;
      const grad = ctx.createRadialGradient(p.x,p.y,0,p.x,p.y,p.r*6);
      grad.addColorStop(0, `rgba(${p.c},${alpha})`);
      grad.addColorStop(1, `rgba(${p.c},0)`);
      ctx.fillStyle = grad;
      ctx.beginPath();
      ctx.arc(p.x,p.y,p.r*6,0,Math.PI*2);
      ctx.fill();

      ctx.fillStyle = `rgba(${p.c},${Math.min(1,alpha+0.2)})`;
      ctx.beginPath();
      ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
      ctx.fill();
    });

    if(!reduced) requestAnimationFrame(tick);
  }
  tick();

  if(reduced){
    // static single render already drawn once via tick() call above (one frame only)
  }

  window.addEventListener('resize', ()=>{ resize(); });
})();
</script>

</body>
</html>
