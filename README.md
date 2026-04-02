<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Brad Levels Up — 30th Birthday Bowling Bash</title>
  <style>
    :root{
      --text:#f8fafc;
      --muted:#b8c2e0;
      --yellow:#ffd84d;
      --pink:#ff5db1;
      --cyan:#45e6ff;
      --green:#6dff8b;
      --red:#ff5a5a;
      --shadow:0 24px 60px rgba(0,0,0,.4);
      --panel:rgba(10,16,33,.92);
      --panel-soft:rgba(255,255,255,.05);
      --line:rgba(255,255,255,.09);
    }

    *{box-sizing:border-box}
    html,body{margin:0;padding:0}

    body{
      font-family:Inter, Arial, sans-serif;
      color:var(--text);
      min-height:100vh;
      background:
        radial-gradient(circle at 15% 10%, rgba(69,230,255,.14), transparent 20%),
        radial-gradient(circle at 85% 15%, rgba(255,93,177,.16), transparent 20%),
        radial-gradient(circle at 50% 100%, rgba(255,216,77,.12), transparent 30%),
        linear-gradient(180deg, #0a0f1f, #0f1731 55%, #08101f);
      overflow-x:hidden;
    }

    .grid-bg{
      position:fixed;
      inset:0;
      pointer-events:none;
      background-image:
        linear-gradient(rgba(69,230,255,.08) 1px, transparent 1px),
        linear-gradient(90deg, rgba(69,230,255,.08) 1px, transparent 1px);
      background-size:32px 32px;
      mask-image:linear-gradient(to bottom, transparent, rgba(0,0,0,.7) 18%, rgba(0,0,0,.9) 70%, transparent);
      opacity:.45;
    }

    .sparkle{
      position:fixed;
      inset:0;
      pointer-events:none;
      overflow:hidden;
      z-index:10;
    }

    .confetti{
      position:absolute;
      top:-20px;
      width:10px;
      height:16px;
      opacity:.95;
      animation:fall linear forwards;
    }

    @keyframes fall{
      to{transform:translateY(110vh) rotate(560deg)}
    }

    .wrap{
      max-width:100%;
      margin:0 auto;
      padding:24px 18px 38px;
      position:relative;
      z-index:1;
    }

    .hero{
      position:relative;
      overflow:hidden;
      background:linear-gradient(180deg, rgba(18,25,51,.92), rgba(12,17,36,.92));
      border:1px solid rgba(69,230,255,.18);
      border-radius:28px;
      padding:28px;
      box-shadow:var(--shadow);
      margin-bottom:22px;
    }

    .hero::before{
      content:"";
      position:absolute;
      inset:0;
      background:linear-gradient(120deg, transparent 0 30%, rgba(255,255,255,.05) 48%, transparent 52% 100%);
      transform:translateX(-120%);
      animation:shine 7s linear infinite;
      pointer-events:none;
    }

    @media (min-width: 1200px){
      .wrap {
        max-width: 1400px;
      }
    }
    
    @keyframes shine{
      to{transform:translateX(120%)}
    }

    .badge-row{
      display:flex;
      flex-wrap:wrap;
      gap:10px;
      margin-bottom:16px;
    }

    .badge{
      border:1px solid rgba(255,255,255,.12);
      background:rgba(255,255,255,.05);
      padding:9px 14px;
      border-radius:999px;
      font-weight:800;
      font-size:.85rem;
      letter-spacing:.04em;
      color:var(--yellow);
      text-transform:uppercase;
    }

    .hero-grid{
      display:grid;
      grid-template-columns:1.2fr .8fr;
      gap:20px;
      align-items:start;
    }
    
    .hero-left{
      display: flex;
      flex-direction: column;
      gap: 14px; /* spacing between text and ball picker */
    }

    h1{
      margin:0 0 12px;
      font-size:clamp(2.3rem, 5vw, 4.4rem);
      line-height:.93;
      letter-spacing:-.04em;
    }

    .gradient{
      background:linear-gradient(90deg, var(--yellow), var(--pink), var(--cyan));
      -webkit-background-clip:text;
      background-clip:text;
      color:transparent;
    }

    .sub{
      max-width:700px;
      color:var(--muted);
      line-height:1.65;
      font-size:1.03rem;
      margin:0;
    }

    .pixel-card{
      background:linear-gradient(180deg, rgba(255,255,255,.04), rgba(255,255,255,.02));
      border:1px solid rgba(255,255,255,.1);
      border-radius:24px;
      padding:18px;
    }

    .xp-wrap{margin-top:10px}

    .xp-label{
      display:flex;
      justify-content:space-between;
      font-size:.9rem;
      color:var(--muted);
      margin-bottom:8px;
      font-weight:700;
    }

    .xp-bar{
      height:20px;
      border-radius:999px;
      background:#09101f;
      border:1px solid rgba(255,255,255,.08);
      overflow:hidden;
      position:relative;
    }

    .xp-fill{
      height:100%;
      width:92%;
      background:linear-gradient(90deg, var(--green), var(--cyan), var(--pink), var(--yellow));
      box-shadow:0 0 20px rgba(69,230,255,.25);
      position:relative;
    }

    .xp-fill::after{
      content:"";
      position:absolute;
      inset:0;
      background:linear-gradient(90deg, transparent, rgba(255,255,255,.28), transparent);
      transform:translateX(-100%);
      animation:shine 2.8s linear infinite;
    }

    .stat-grid{
      display:grid;
      grid-template-columns:repeat(2, 1fr);
      gap:12px;
      margin-top:14px;
    }

    .stat{
      background:rgba(255,255,255,.04);
      border:1px solid rgba(255,255,255,.08);
      border-radius:18px;
      padding:14px;
    }

    .stat .k{
      color:var(--muted);
      font-size:.82rem;
      text-transform:uppercase;
      letter-spacing:.08em;
      font-weight:800;
    }

    .stat .v{
      font-size:1.12rem;
      font-weight:900;
      margin-top:5px;
    }

    .layout{
      display:grid;
      grid-template-columns:.8fr 1.2fr;
      gap:22px;
      align-items:start;
    }

    .card{
      background:linear-gradient(180deg, rgba(18,25,51,.94), rgba(13,18,38,.94));
      border:1px solid rgba(255,255,255,.08);
      border-radius:26px;
      padding:22px;
      box-shadow:var(--shadow);
    }

    h2{
      margin:0 0 14px;
      font-size:1.35rem;
      letter-spacing:-.02em;
    }

    h3{
      margin:0 0 10px;
      font-size:1rem;
    }

    .quest-list{
      display:grid;
      gap:12px;
    }

    .quest{
      display:grid;
      grid-template-columns:110px 1fr;
      gap:12px;
      padding:12px 0;
      border-bottom:1px solid rgba(255,255,255,.08);
    }

    .quest:last-child{border-bottom:none}

    .label{
      color:var(--cyan);
      font-weight:900;
      font-size:.8rem;
      letter-spacing:.08em;
      text-transform:uppercase;
      padding-top:3px;
    }

    .value{
      color:var(--text);
      line-height:1.55;
    }

    .note{
      margin-top:12px;
      color:var(--muted);
      line-height:1.65;
      font-size:.95rem;
    }

    .tiny{
      color:var(--muted);
      font-size:.88rem;
      line-height:1.5;
    }

    .cta-row{
      display:flex;
      flex-wrap:wrap;
      gap:10px;
      margin-top:16px;
    }

    button{
      border:none;
      cursor:pointer;
      border-radius:999px;
      padding:12px 16px;
      font-weight:900;
      letter-spacing:.02em;
      transition:transform .15s ease, opacity .15s ease, border-color .15s ease;
      display:inline-flex;
      align-items:center;
      justify-content:center;
      font-family:inherit;
      font-size:.95rem;
    }

    button:hover{transform:translateY(-1px)}
    button:disabled{opacity:.55; cursor:not-allowed; transform:none}

    .primary{
      color:#08101f;
      background:linear-gradient(90deg, var(--yellow), var(--pink));
      box-shadow:0 10px 30px rgba(255,93,177,.2);
    }

    .ghost{
      color:var(--text);
      background:rgba(255,255,255,.05);
      border:1px solid rgba(255,255,255,.1);
    }

    .game-card{
      padding:16px;
    }

    .game-shell{
      position:relative;
      border-radius:28px;
      border:1px solid rgba(255,255,255,.08);
      background:linear-gradient(180deg, rgba(16,22,44,.96), rgba(9,14,29,.98));
      padding:14px;
      overflow:hidden;
    }

    .game-shell::before{
      content:"";
      position:absolute;
      inset:0;
      background:
        radial-gradient(circle at 10% 10%, rgba(69,230,255,.08), transparent 18%),
        radial-gradient(circle at 88% 12%, rgba(255,93,177,.08), transparent 20%),
        radial-gradient(circle at 50% 100%, rgba(255,216,77,.08), transparent 24%);
      pointer-events:none;
    }

    .top-hud{
      position:relative;
      z-index:2;
      display:grid;
      grid-template-columns:repeat(4, minmax(0,1fr));
      gap:10px;
      margin-bottom:12px;
    }

    .hud-pill{
      padding:10px 12px;
      border-radius:16px;
      background:rgba(255,255,255,.05);
      border:1px solid rgba(255,255,255,.08);
      text-align:center;
    }

    .hud-pill .k{
      display:block;
      color:var(--muted);
      font-size:.72rem;
      text-transform:uppercase;
      letter-spacing:.08em;
      font-weight:800;
      margin-bottom:4px;
    }

    .hud-pill .v{
      display:block;
      color:#fff6d0;
      font-weight:900;
      font-size:1rem;
    }

    .game-main{
      display:grid;
      grid-template-columns:1fr;
      gap:14px;
      grid-row: 2;
    }

    .lane-wrap{
      order:1;
    }

    .control-panel{
      order:2;
      display:grid;
      grid-template-columns: 1fr;
      gap: 14px;
    }

    .ball-picker-block {
      width: 100%;
      max-width: 100%;
    }
    
    .scoreboard-block {
      width: 100%;
      max-width: 100%;
      grid-row: 1;
    }

    .lane{
      position:relative;
      width:100%;
      aspect-ratio:8 / 10;
      min-height:420px;
      border-radius:24px;
      overflow:hidden;
      border:2px solid rgba(69,230,255,.18);
      background:
        linear-gradient(to top, rgba(8,16,31,.96), rgba(8,16,31,.35) 24%, transparent 24%),
        linear-gradient(to right,
          #553015 0%,
          #9b5c21 7%,
          #d79658 16%,
          #efbc84 26%,
          #f7cf9d 36%,
          #edc18c 50%,
          #f7cf9d 64%,
          #efbc84 74%,
          #d79658 84%,
          #9b5c21 93%,
          #553015 100%);
      box-shadow:inset 0 0 0 6px rgba(255,255,255,.04), 0 0 30px rgba(69,230,255,.08);
      user-select:none;
      touch-action:none;
    }

    .lane::before{
      content:"";
      position:absolute;
      inset:0;
      background:
        linear-gradient(180deg, rgba(255,255,255,.18), transparent 12%),
        linear-gradient(to right, transparent 49.5%, rgba(255,255,255,.11) 50%, transparent 50.5%),
        radial-gradient(circle at 50% 16%, rgba(255,255,255,.18), transparent 22%);
      pointer-events:none;
    }

    .lane-overlay-top{
      position:absolute;
      left:12px;
      right:12px;
      top:12px;
      display:flex;
      flex-wrap:wrap;
      justify-content:space-between;
      gap:8px;
      z-index:4;
    }

    .lane-badge{
      padding:8px 10px;
      border-radius:999px;
      background:rgba(8,16,31,.76);
      border:1px solid rgba(255,255,255,.08);
      color:var(--yellow);
      font-size:.8rem;
      font-weight:900;
      letter-spacing:.05em;
      text-transform:uppercase;
      backdrop-filter:blur(6px);
    }

    .pins {
      position: absolute;
      top: 12%;
      left: 50%;
      width: 100%;
      height: 100%;
      transform: translateX(-50%);
      display: block;
    }

    .pin {
      position: absolute;
      width: 18px;
      height: 35px; /* keep the cylinder height */
      border-radius: 12px 12px 9px 9px;
      background: linear-gradient(180deg, #fff, #e7ebf5);
      box-shadow: 0 4px 8px rgba(0,0,0,.25);
      transition: transform .55s ease, opacity .45s ease, filter .3s ease;
    }

    .pin::after {
      content: "";
      position: absolute;
      left: 1px; right: 1px;
      top: 10px; height: 5px;
      background: linear-gradient(90deg, var(--pink), #ff8ad0);
      border-radius: 4px;
    }

    /* Inverted bowling pin triangle (top-down view, pointing toward ball) */
    .pin1  { top: 36%; left: 50%; transform: translateX(-50%); } /* back row, widest */
    .pin2  { top: 24%; left: 42%; }
    .pin3  { top: 24%; left: 58%; }
    .pin4  { top: 12%; left: 34%; }
    .pin5  { top: 12%; left: 50%; }
    .pin6  { top: 12%; left: 66%; }
    .pin7  { top: 0%;  left: 26%; }
    .pin8  { top: 0%;  left: 42%; }
    .pin9  { top: 0%;  left: 58%; }
    .pin10 { top: 0%;  left: 74%; }

    .pin.hidden{
      opacity:0;
      transform:translateY(18px) rotate(38deg) scale(.82);
      filter:blur(1px);
    }

    .r1{grid-column:2 / span 1}
    .r2a{grid-column:2 / span 1}
    .r2b{grid-column:3 / span 1}
    .r3a{grid-column:1 / span 1}
    .r3b{grid-column:2 / span 1}
    .r3c{grid-column:3 / span 1}
    .r4a{grid-column:1 / span 1}
    .r4b{grid-column:2 / span 1}
    .r4c{grid-column:3 / span 1}
    .r4d{grid-column:4 / span 1}

    .aim{
      position:absolute;
      bottom:10%;
      width:3px;
      height:66%;
      background:linear-gradient(180deg, rgba(69,230,255,.15), rgba(69,230,255,.95), rgba(69,230,255,0));
      transform-origin:bottom center;
      pointer-events:none;
      z-index:2;
      box-shadow:0 0 12px rgba(69,230,255,.4);
    }

    .ball{
      position:absolute;
      width:48px;
      height:48px;
      border-radius:50%;
      bottom:8%;
      z-index:3;
      overflow:hidden;
      cursor:grab;
      touch-action:none;
      transition:box-shadow .2s ease, filter .2s ease;
      transform: translateX(-50%);
    }

    .ball.dragging{cursor:grabbing}

    .ball::before, .ball::after, .finger{
      content:"";
      position:absolute;
      width:6px;
      height:6px;
      border-radius:50%;
      background:rgba(0,0,0,.35);
      z-index:3;
    }

    .ball::before{top:10px; left:12px}
    .ball::after{top:16px; left:21px}
    .finger{top:22px; left:14px}

    .ball.flame{
      background:
        radial-gradient(circle at 28% 28%, rgba(255,255,255,.45), transparent 16%),
        radial-gradient(circle at 70% 75%, rgba(255,215,120,.28), transparent 22%),
        linear-gradient(135deg, #ffdd55 0%, #ff9832 35%, #ff4f31 68%, #7a0e14 100%);
      box-shadow:0 12px 28px rgba(0,0,0,.34), 0 0 22px rgba(255,110,30,.35);
    }

    .ball.sparkly{
      background:
        radial-gradient(circle at 20% 20%, rgba(255,255,255,.65), transparent 12%),
        radial-gradient(circle at 72% 28%, rgba(255,255,255,.48), transparent 9%),
        radial-gradient(circle at 60% 70%, rgba(255,255,255,.35), transparent 11%),
        linear-gradient(135deg, #ff8ad0 0%, #b467ff 45%, #6de7ff 100%);
      box-shadow:0 12px 28px rgba(0,0,0,.34), 0 0 24px rgba(255,93,177,.28);
    }

    .ball.blue{
      background:
        radial-gradient(circle at 25% 25%, rgba(255,255,255,.45), transparent 15%),
        radial-gradient(circle at 75% 78%, rgba(120,220,255,.26), transparent 24%),
        linear-gradient(135deg, #7de5ff 0%, #45baff 38%, #2749b4 100%);
      box-shadow:0 12px 28px rgba(0,0,0,.34), 0 0 24px rgba(69,230,255,.33);
    }

    .ball.red{
      background:
        radial-gradient(circle at 25% 25%, rgba(255,255,255,.45), transparent 15%),
        radial-gradient(circle at 75% 78%, rgba(255,80,100,.24), transparent 24%),
        linear-gradient(135deg, #ff8a8a 0%, #ff4040 38%, #7f101d 100%);
      box-shadow:0 12px 28px rgba(0,0,0,.34), 0 0 24px rgba(255,90,90,.33);
    }

    .ball.birthday{
      background:
        radial-gradient(circle at 26% 24%, rgba(255,255,255,.45), transparent 15%),
        linear-gradient(135deg, #fff8e8 0%, #ffe8f7 46%, #e8f7ff 100%);
      box-shadow:0 12px 28px rgba(0,0,0,.34), 0 0 22px rgba(255,216,77,.26);
    }

    .ball.birthday .sprinkles,
    .ball.sparkly .spark-stars,
    .ball.flame .flame-lines,
    .ball.blue .aura-rings,
    .ball.red .aura-rings{
      position:absolute;
      inset:0;
      pointer-events:none;
      z-index:1;
    }

    .ball.birthday .sprinkles::before,
    .ball.birthday .sprinkles::after{
      content:"";
      position:absolute;
      inset:0;
      background:
        linear-gradient(20deg, transparent 0 10%, #ff5db1 10% 12%, transparent 12% 22%, #45e6ff 22% 24%, transparent 24% 36%, #ffd84d 36% 38%, transparent 38% 52%, #6dff8b 52% 54%, transparent 54% 67%, #ff8855 67% 69%, transparent 69% 100%),
        linear-gradient(140deg, transparent 0 12%, #45e6ff 12% 14%, transparent 14% 30%, #ff5db1 30% 32%, transparent 32% 48%, #ffd84d 48% 50%, transparent 50% 66%, #6dff8b 66% 68%, transparent 68% 100%);
      opacity:.8;
      border-radius:50%;
      transform:scale(.95);
    }

    .ball.sparkly .spark-stars::before,
    .ball.sparkly .spark-stars::after{
      content:"✦";
      position:absolute;
      color:rgba(255,255,255,.85);
      font-size:10px;
      text-shadow:0 0 8px rgba(255,255,255,.4);
    }

    .ball.sparkly .spark-stars::before{top:8px; right:8px}
    .ball.sparkly .spark-stars::after{bottom:8px; left:8px}

    .ball.flame .flame-lines::before,
    .ball.flame .flame-lines::after{
      content:"";
      position:absolute;
      width:22px;
      height:22px;
      border-radius:50%;
      border-top:2px solid rgba(255,220,120,.85);
      border-right:2px solid transparent;
      border-bottom:2px solid transparent;
      border-left:2px solid transparent;
      transform:rotate(35deg);
    }

    .ball.flame .flame-lines::before{top:6px; right:5px}
    .ball.flame .flame-lines::after{bottom:4px; left:4px; transform:rotate(210deg)}

    .ball.blue .aura-rings::before,
    .ball.blue .aura-rings::after,
    .ball.red .aura-rings::before,
    .ball.red .aura-rings::after{
      content:"";
      position:absolute;
      border-radius:50%;
      inset:6px;
      border:1px solid rgba(255,255,255,.16);
    }

    .ball.blue .aura-rings::after,
    .ball.red .aura-rings::after{
      inset:12px;
      opacity:.7;
    }

    .foul{
      position:absolute;
      left:0; right:0;
      bottom:18%;
      height:4px;
      background:linear-gradient(90deg, transparent, rgba(255,255,255,.9), transparent);
    }

    .approach-dots{
      position:absolute;
      left:50%;
      bottom:24%;
      transform:translateX(-50%);
      width:55%;
      display:flex;
      justify-content:space-between;
      opacity:.45;
      z-index:1;
      pointer-events:none;
    }

    .approach-dots span{
      width:8px;
      height:8px;
      border-radius:50%;
      background:rgba(255,255,255,.55);
    }

    .approach-shine{
      position:absolute;
      left:0; right:0; bottom:0;
      height:25%;
      background:linear-gradient(180deg, transparent, rgba(255,255,255,.07));
      pointer-events:none;
      z-index:1;
    }

    .lane-hint{
      position:absolute;
      left:50%;
      bottom:2%;
      transform:translateX(-50%);
      padding:8px 12px;
      border-radius:999px;
      background:rgba(8,16,31,.7);
      border:1px solid rgba(255,255,255,.08);
      font-size:.76rem;
      color:var(--muted);
      z-index:4;
      backdrop-filter:blur(6px);
      white-space:nowrap;
    }

    .levelup{
      position:absolute;
      left:50%;
      top:48%;
      transform:translate(-50%, -50%) scale(.7);
      font-size:clamp(1.5rem, 4vw, 2.5rem);
      font-weight:1000;
      letter-spacing:.06em;
      text-transform:uppercase;
      color:var(--yellow);
      text-shadow:0 0 18px rgba(255,216,77,.45);
      opacity:0;
      z-index:6;
      pointer-events:none;
      text-align:center;
      width:90%;
    }

    .levelup.show{
      animation:pop 1.25s ease forwards;
    }

    @keyframes pop{
      0%{opacity:0; transform:translate(-50%, -40%) scale(.7)}
      20%{opacity:1; transform:translate(-50%, -50%) scale(1.05)}
      80%{opacity:1}
      100%{opacity:0; transform:translate(-50%, -58%) scale(1)}
    }

    @keyframes roll{
      0%{
        transform:translateX(-50%) translateY(0) scale(1) rotate(0deg);
      }
      100%{
        transform:translateX(calc(-50% + var(--drift))) translateY(calc(-1 * var(--distance))) scale(.48) rotate(720deg);
      }
    }

    .subcard{
      background:var(--panel-soft);
      border:1px solid var(--line);
      border-radius:18px;
      padding:14px;
    }

    .score-table{
      width:100%;
      border-collapse:collapse;
      overflow-x: auto;
      border-radius:14px;
      border:1px solid rgba(255,255,255,.08);
      background:rgba(255,255,255,.02);
      table-layout: fixed;
    }

    .score-table th,
    .score-table td{
      border:1px solid rgba(255,255,255,.08);
      padding:8px 10px;
      text-align:center;
      font-weight:800;
      font-size:.9rem;
      width: auto;
      max-width: 100%
      word-break: break-word;
    }

    .score-table thead th{
      background:rgba(255,255,255,.05);
      color:var(--yellow);
    }

    .score-table tbody th{
      background:rgba(255,255,255,.04);
      color:var(--cyan);
    }

    .score-table td{
      color:var(--text);
      min-width:44px;
    }

    .score-table .total-cell{
      color:var(--green);
      font-weight:900;
    }

    .ball-picker{
      display:grid;
      grid-template-columns:repeat(2, minmax(0,1fr));
      gap:10px;
    }

    .ball-option{
      display:flex;
      align-items:center;
      gap:10px;
      padding:10px;
      border-radius:16px;
      background:rgba(255,255,255,.03);
      border:1px solid rgba(255,255,255,.08);
      cursor:pointer;
      text-align:left;
      color:var(--text);
    }

    .ball-option.active{
      border-color:rgba(255,216,77,.7);
      box-shadow:0 0 0 1px rgba(255,216,77,.28) inset;
      background:rgba(255,216,77,.06);
    }

    .mini-ball{
      width:34px;
      height:34px;
      border-radius:50%;
      flex:0 0 auto;
    }

    .mini-ball.flame{
      background:linear-gradient(135deg, #ffdd55 0%, #ff9832 35%, #ff4f31 68%, #7a0e14 100%);
      box-shadow:0 0 12px rgba(255,110,30,.28);
    }

    .mini-ball.sparkly{
      background:linear-gradient(135deg, #ff8ad0 0%, #b467ff 45%, #6de7ff 100%);
      box-shadow:0 0 12px rgba(255,93,177,.25);
    }

    .mini-ball.blue{
      background:linear-gradient(135deg, #7de5ff 0%, #45baff 38%, #2749b4 100%);
      box-shadow:0 0 12px rgba(69,230,255,.25);
    }

    .mini-ball.red{
      background:linear-gradient(135deg, #ff8a8a 0%, #ff4040 38%, #7f101d 100%);
      box-shadow:0 0 12px rgba(255,90,90,.25);
    }

    .mini-ball.birthday{
      background:linear-gradient(135deg, #fff8e8 0%, #ffe8f7 46%, #e8f7ff 100%);
      box-shadow:0 0 12px rgba(255,216,77,.22);
    }

    .option-text{
      display:grid;
      gap:2px;
    }

    .option-text strong{
      font-size:.93rem;
    }

    .option-text span{
      color:var(--muted);
      font-size:.8rem;
      line-height:1.25;
    }

    .controls-block{
      grid-row: 3;
    }
    
    .slider-block{
      display:grid;
      gap:8px;
    }

    .slider-head{
      display:flex;
      justify-content:space-between;
      gap:10px;
      align-items:center;
      font-size:.86rem;
      color:var(--muted);
      font-weight:800;
    }

    input[type="range"]{
      width:100%;
      accent-color:var(--yellow);
    }

    .result{
      min-height:34px;
      font-weight:900;
      color:var(--yellow);
      font-size:1.03rem;
    }

    @media (max-width: 980px){
      .hero-grid,
      .layout,
      .game-main{
        grid-template-columns:1fr;
      }

      .top-hud{
        grid-template-columns:repeat(2, minmax(0,1fr));
      }
    }

    @media (max-width: 640px){
      .top-hud{
        grid-template-columns:1fr 1fr;
      }

      .ball-picker{
        grid-template-columns:1fr;
      }

      .quest{
        grid-template-columns:1fr;
        gap:6px;
      }

      .lane{
        min-height:380px;
      }
    }
  </style>
</head>
<body>
  <div class="grid-bg"></div>
  <div class="sparkle" id="sparkle"></div>

  <div class="wrap">
    <section class="hero">
      <div class="badge-row">
        <div class="badge">Main quest unlocked</div>
        <div class="badge">Level 30</div>
        <div class="badge">Bowling edition</div>
      </div>

      <div class="hero-grid">
        <div>
          <h1>Brad is <span class="gradient">Leveling Up</span><br>to 30 🎳</h1>
          <p class="sub">
            Join us for birthday bowling in honor of Brad hitting Level 30!
            Expect bowling, food, drinks, and a good time.
            Warm up for the party by taking a shot in the mini game below.
          </p>
        </div>

        <div class="pixel-card">
          <div style="font-weight:1000; font-size:1.05rem; color:var(--yellow);">Birthday Player Card</div>
          <div class="xp-wrap">
            <div class="xp-label">
              <span>XP Progress</span>
              <span>29 ➜ 30</span>
            </div>
            <div class="xp-bar"><div class="xp-fill"></div></div>
          </div>

          <div class="stat-grid">
            <div class="stat">
              <div class="k">Class</div>
              <div class="v">Birthday Boy</div>
            </div>
            <div class="stat">
              <div class="k">Special Skill</div>
              <div class="v">Drinking and Knowing Things</div>
            </div>
            <div class="stat">
              <div class="k">Buffs</div>
              <div class="v">Snacks + Friends</div>
            </div>
            <div class="stat">
              <div class="k">Boss Battle</div>
              <div class="v">Turning 30</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="layout">
      <div class="hero-left">
          <div class="card">
            <h2>Quest Details</h2>
            <div class="quest-list">
              <div class="quest">
                <div class="label">Date</div>
                <div class="value">Saturday, April 11, 2026</div>
              </div>
              <div class="quest">
                <div class="label">Time</div>
                <div class="value">5:00 PM bowling · 3:00 PM dinner</div>
              </div>
              <div class="quest">
                <div class="label">Location</div>
                <div class="value">Railroad + Strikerz at Angel of the Winds Casino</div>
              </div>
              <div class="quest">
                <div class="label">Objective</div>
                <div class="value">Bowl a few frames, eat good food, and celebrate Brad.</div>
              </div>
              <div class="quest">
                <div class="label">RSVP By</div>
                <div class="value">April 3, 2026</div>
              </div>
            </div>

            <p class="note">
              We’ll be eating an early dinner at Railroad at 3:00 PM before bowling at 5:00 PM.
              We’d love for you to join us for dinner too.
              Bowling is $10/person. If you want to bowl, you can Venmo Brad at <strong>@Bradley-Jarvensivu</strong>.
            </p>

            <div class="tiny" id="copyStatus" style="margin-top:10px;"></div>
          </div>

          <div class="subcard ball-picker-block">
            <h3>Pick Your Ball</h3>
            <div class="ball-picker">
              <button class="ball-option active" data-ball="sparkly" type="button">
                <div class="mini-ball sparkly"></div>
                <div class="option-text">
                  <strong>Sparkly</strong>
                  <span>Allison's Ball</span>
                </div>
              </button>

              <button class="ball-option" data-ball="flame" type="button">
                <div class="mini-ball flame"></div>
                <div class="option-text">
                  <strong>Fire Ball</strong>
                  <span>Always a good time!</span>
                </div>
              </button>

              <button class="ball-option" data-ball="blue" type="button">
                <div class="mini-ball blue"></div>
                <div class="option-text">
                  <strong>Blue Ball</strong>
                  <span>Don't laugh</span>
                </div>
              </button>

              <button class="ball-option" data-ball="red" type="button">
                <div class="mini-ball red"></div>
                <div class="option-text">
                  <strong>Red Ball</strong>
                  <span>Gives you wings</span>
                </div>
              </button>

              <button class="ball-option" data-ball="birthday" type="button" style="grid-column:1 / -1;">
                <div class="mini-ball birthday"></div>
                <div class="option-text">
                  <strong>Birthday Confetti</strong>
                  <span>Funfetti flavor</span>
                </div>
              </button>
            </div>
          </div>
      </div>
      
      <div class="hero-right">
        <div class="card game-card">
          <h2 style="margin-bottom:12px;">Bonus Round: Birthday Bowling</h2>

          <div class="game-shell">
            <div class="top-hud">
              <div class="hud-pill">
                <span class="k">Frame</span>
                <span class="v" id="frameValue">1 / 3</span>
              </div>
              <div class="hud-pill">
                <span class="k">Roll</span>
                <span class="v" id="rollValue">1 / 2</span>
              </div>
              <div class="hud-pill">
                <span class="k">Total</span>
                <span class="v" id="scoreValue">0</span>
              </div>
              <div class="hud-pill">
                <span class="k">High Score</span>
                <span class="v" id="highScore">0</span>
              </div>
            </div>
            <div class="control-panel">
                <div class="subcard scoreboard-block">
                  <h3>Scoreboard</h3>
                  <table class="score-table">
                    <thead>
                      <tr>
                        <th>Frame</th>
                        <th>R1</th>
                        <th>R2</th>
                        <th>Total</th>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <th>1</th>
                        <td id="f1r1">—</td>
                        <td id="f1r2">—</td>
                        <td id="f1t" class="total-cell">0</td>
                      </tr>
                      <tr>
                        <th>2</th>
                        <td id="f2r1">—</td>
                        <td id="f2r2">—</td>
                        <td id="f2t" class="total-cell">0</td>
                      </tr>
                      <tr>
                        <th>3</th>
                        <td id="f3r1">—</td>
                        <td id="f3r2">—</td>
                        <td id="f3t" class="total-cell">0</td>
                      </tr>
                    </tbody>
                  </table>
                  <div class="tiny" style="margin-top:8px;">Strike = X · Spare = /</div>
                </div>
            <div class="game-main">
              <div class="lane-wrap">
                <div class="lane" id="lane">
                  <div class="lane-overlay-top">
                    <div class="lane-badge">Guest Mode</div>
                    <div class="lane-badge" id="frameSummary">Frame 1 · Roll 1</div>
                  </div>

                    <div class="pins">
                      <div class="pin pin1"></div>
                      <div class="pin pin2"></div>
                      <div class="pin pin3"></div>
                      <div class="pin pin4"></div>
                      <div class="pin pin5"></div>
                      <div class="pin pin6"></div>
                      <div class="pin pin7"></div>
                      <div class="pin pin8"></div>
                      <div class="pin pin9"></div>
                      <div class="pin pin10"></div>
                    </div>

                  <div class="aim" id="aimLine"></div>

                  <div class="ball sparkly" id="ball">
                    <div class="spark-stars"></div>
                    <div class="finger"></div>
                  </div>

                  <div class="foul"></div>

                  <div class="approach-dots">
                    <span></span><span></span><span></span><span></span><span></span>
                  </div>

                  <div class="approach-shine"></div>
                  <div class="lane-hint">Drag ball or tap lane to move • then roll</div>
                  <div class="levelup" id="levelUpFlash">LEVEL UP!</div>
                </div>
              </div>

                <div class="subcard controls-block">
                  <div class="slider-block">
                    <div class="slider-head">
                      <span>Aim</span>
                      <span id="aimValue">0°</span>
                    </div>
                    <input id="aimSlider" type="range" min="-32" max="32" value="0" />
                  </div>

                  <div class="slider-block" style="margin-top:12px;">
                    <div class="slider-head">
                      <span>Power</span>
                      <span id="powerValue">74%</span>
                    </div>
                    <input id="powerSlider" type="range" min="40" max="100" value="74" />
                  </div>

                  <div class="slider-block" style="margin-top:12px;">
                    <div class="slider-head">
                      <span>Spin</span>
                      <span id="spinValue">0</span>
                    </div>
                    <input id="spinSlider" type="range" min="-30" max="30" value="0" />
                  </div>

                  <div class="cta-row">
                    <button class="primary" id="rollBtn" type="button">Send It</button>
                    <button class="ghost" id="resetBtn" type="button">Reset Game</button>
                  </div>

                  <div class="tiny" style="margin-top:8px;">
                    Keyboard: ← → move ball · A / D aim · ↑ ↓ power · J / L spin · Space roll
                  </div>

                  <div class="result" id="result" style="margin-top:10px;">Can you earn birthday bragging rights?</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>

  <script>
    document.addEventListener("DOMContentLoaded", function () {
      const aimSlider = document.getElementById("aimSlider");
      const powerSlider = document.getElementById("powerSlider");
      const spinSlider = document.getElementById("spinSlider");

      const aimValue = document.getElementById("aimValue");
      const powerValue = document.getElementById("powerValue");
      const spinValue = document.getElementById("spinValue");
      const frameValue = document.getElementById("frameValue");
      const rollValue = document.getElementById("rollValue");
      const scoreValue = document.getElementById("scoreValue");
      const frameSummary = document.getElementById("frameSummary");

      const lane = document.getElementById("lane");
      const aimLine = document.getElementById("aimLine");
      const ball = document.getElementById("ball");
      const rollBtn = document.getElementById("rollBtn");
      const resetBtn = document.getElementById("resetBtn");
      const result = document.getElementById("result");
      const pins = Array.from(document.querySelectorAll(".pin"));
      const highScoreEl = document.getElementById("highScore");
      const sparkle = document.getElementById("sparkle");
      const levelUpFlash = document.getElementById("levelUpFlash");
      const copyStatus = document.getElementById("copyStatus");
      const ballOptions = Array.from(document.querySelectorAll(".ball-option"));

      const scoreCells = {
        1: { r1: document.getElementById("f1r1"), r2: document.getElementById("f1r2"), t: document.getElementById("f1t") },
        2: { r1: document.getElementById("f2r1"), r2: document.getElementById("f2r2"), t: document.getElementById("f2t") },
        3: { r1: document.getElementById("f3r1"), r2: document.getElementById("f3r2"), t: document.getElementById("f3t") }
      };

      let rolling = false;
      let frame = 1;
      let roll = 1;
      let totalScore = 0;
      let framePinsRemaining = 10;
      let standingPins = new Set(pins.map((_, i) => i));
      let selectedBall = "sparkly";
      let frameScores = {
        1: { r1: null, r2: null, total: 0 },
        2: { r1: null, r2: null, total: 0 },
        3: { r1: null, r2: null, total: 0 }
      };

      let ballX = 50; // percentage across lane
      let dragging = false;

      let highScore = Number(localStorage.getItem("bradLevel30BowlingHighScoreV4") || 0);
      highScoreEl.textContent = highScore;

      function clamp(num, min, max) {
        return Math.max(min, Math.min(max, num));
      }

      function setBallStyle(style) {
        selectedBall = style;
        ball.className = "ball " + style;

        if (style === "sparkly") {
          ball.innerHTML = '<div class="spark-stars"></div><div class="finger"></div>';
        } else if (style === "flame") {
          ball.innerHTML = '<div class="flame-lines"></div><div class="finger"></div>';
        } else if (style === "blue") {
          ball.innerHTML = '<div class="aura-rings"></div><div class="finger"></div>';
        } else if (style === "red") {
          ball.innerHTML = '<div class="aura-rings"></div><div class="finger"></div>';
        } else if (style === "birthday") {
          ball.innerHTML = '<div class="sprinkles"></div><div class="finger"></div>';
        }

        ballOptions.forEach(btn => {
          btn.classList.toggle("active", btn.dataset.ball === style);
        });
      }

      function updateBallPositionVisual() {
        ball.style.left = `${ballX}%`;
        aimLine.style.left = `${ballX}%`;
      }

      function updateHud() {
        const angle = Number(aimSlider.value);
        const power = Number(powerSlider.value);
        const spin = Number(spinSlider.value);

        aimValue.textContent = `${angle}°`;
        powerValue.textContent = `${power}%`;
        spinValue.textContent = spin > 0 ? `+${spin}` : `${spin}`;
        frameValue.textContent = `${frame} / 3`;
        rollValue.textContent = `${roll} / 2`;
        scoreValue.textContent = totalScore;
        frameSummary.textContent = `Frame ${frame} · Roll ${roll}`;

        aimLine.style.transform = `translateX(-50%) rotate(${angle}deg)`;
        updateBallPositionVisual();
      }

      function renderScoreboard() {
        [1, 2, 3].forEach(f => {
          const data = frameScores[f];
          scoreCells[f].r1.textContent = data.r1 ?? "—";
          scoreCells[f].r2.textContent = data.r2 ?? "—";
          scoreCells[f].t.textContent = data.total || 0;
        });
      }

      function randomBetween(min, max) {
        return Math.random() * (max - min) + min;
      }

      function confettiBurst() {
        const colors = ["#ffd84d", "#ff5db1", "#45e6ff", "#6dff8b", "#ffffff", "#ff8b4d"];
        for (let i = 0; i < 82; i++) {
          const c = document.createElement("div");
          c.className = "confetti";
          c.style.left = `${Math.random() * 100}vw`;
          c.style.background = colors[Math.floor(Math.random() * colors.length)];
          c.style.animationDuration = `${randomBetween(1.9, 3.5)}s`;
          c.style.transform = `rotate(${Math.random() * 360}deg)`;
          sparkle.appendChild(c);
          setTimeout(() => c.remove(), 3800);
        }
      }

      function levelUp(text = "LEVEL UP!") {
        levelUpFlash.textContent = text;
        levelUpFlash.classList.remove("show");
        void levelUpFlash.offsetWidth;
        levelUpFlash.classList.add("show");
        confettiBurst();
      }

      function renderPins() {
        pins.forEach((pin, index) => {
          if (standingPins.has(index)) {
            pin.classList.remove("hidden");
          } else {
            pin.classList.add("hidden");
          }
        });
      }

      function resetFramePins() {
        framePinsRemaining = 10;
        standingPins = new Set(pins.map((_, i) => i));
        renderPins();
      }

      function saveHighScoreIfNeeded() {
        if (totalScore > highScore) {
          highScore = totalScore;
          localStorage.setItem("bradLevel30BowlingHighScoreV4", highScore);
          highScoreEl.textContent = highScore;
        }
      }

      function resetScoreData() {
        frameScores = {
          1: { r1: null, r2: null, total: 0 },
          2: { r1: null, r2: null, total: 0 },
          3: { r1: null, r2: null, total: 0 }
        };
        renderScoreboard();
      }

      function resetWholeGame() {
        frame = 1;
        roll = 1;
        totalScore = 0;
        ballX = 50;
        aimSlider.value = 0;
        powerSlider.value = 74;
        spinSlider.value = 0;
        resetFramePins();
        resetScoreData();
        result.textContent = "Can you earn birthday bragging rights?";
        ball.style.animation = "none";
        ball.style.removeProperty("--drift");
        ball.style.removeProperty("--distance");
        rolling = false;
        rollBtn.disabled = false;
        updateHud();
      }

      function finishGame() {
        saveHighScoreIfNeeded();
        if (totalScore == 30){
          result.textContent = `Game over. Final score: ${totalScore}. Perfect game!`;
        } else if (totalScore >= 20){
          result.textContent = `Game over. Final score: ${totalScore}. Not too shabby!`;
        } else if (totalScore >= 10){
          result.textContent = `Game over. Final score: ${totalScore}. Remarkably average.`;
        } else if (totalScore > 0){
          result.textContent = `Game over. Final score: ${totalScore}. You have some work to do.`;
        } else {
          result.textContent = `Game over. Final score: ${totalScore}. oof`;
        }
        levelUp("GAME OVER");
        rollBtn.disabled = true;
      }

      function nextFrame() {
        if (frame >= 3) {
          finishGame();
          return;
        }
        frame += 1;
        roll = 1;
        ballX = 50;
        resetFramePins();
        updateHud();
      }

      function ballStyleBonus() {
        switch (selectedBall) {
          case "flame": return { power: 0.45, strike: 0.03, spin: -0.02 };
          case "sparkly": return { power: 0.15, strike: 0.04, spin: 0.03 };
          case "blue": return { power: 0.1, strike: 0.05, spin: 0.08 };
          case "red": return { power: 0.2, strike: 0.04, spin: 0.02 };
          case "birthday": return { power: 0.25, strike: 0.08, spin: 0.01 };
          default: return { power: 0, strike: 0, spin: 0 };
        }
      }

      function scoreRoll(angle, power, spin, remainingPins) {
        const bonus = ballStyleBonus();
        const startOffsetPenalty = Math.abs(ballX - 50) * 0.11;
        const effectiveSpin = spin * (1 + bonus.spin);
        const accuracyPenalty = Math.abs(angle + effectiveSpin * 0.35) * 0.22 + startOffsetPenalty;
        const powerBonus = (power - 40) * (0.08 + bonus.power * 0.01);
        const spinBonus = 6 - Math.abs(effectiveSpin) * 0.08;
        const randomness = randomBetween(-1.8, 2.4);

        let score = Math.round(4 + powerBonus + spinBonus - accuracyPenalty + randomness);

        const strikeChance = 0.40 + bonus.strike;
        if (Math.abs(angle) <= 4 && power >= 74 && Math.abs(effectiveSpin) <= 12 && Math.abs(ballX - 50) <= 8 && Math.random() > (1 - strikeChance)) {
          score = Math.max(score, remainingPins);
        }

        return Math.max(0, Math.min(remainingPins, score));
      }

      function knockPins(count) {
        const available = Array.from(standingPins);
        const shuffled = available.sort(() => Math.random() - 0.5);
        const toKnock = shuffled.slice(0, count);

        toKnock.forEach((pinIndex, i) => {
          setTimeout(() => {
            standingPins.delete(pinIndex);
            pins[pinIndex].classList.add("hidden");
          }, i * 55);
        });
      }

      function writeRollToScoreboard(knocked, isStrike = false, isSpare = false) {
        if (roll === 1) {
          frameScores[frame].r1 = isStrike ? "X" : knocked;
        } else {
          frameScores[frame].r2 = isSpare ? "/" : knocked;
        }

        frameScores[frame].total =
          (typeof frameScores[frame].r1 === "number" ? frameScores[frame].r1 : frameScores[frame].r1 === "X" ? 10 : 0) +
          (typeof frameScores[frame].r2 === "number" ? frameScores[frame].r2 : frameScores[frame].r2 === "/" ? (10 - (typeof frameScores[frame].r1 === "number" ? frameScores[frame].r1 : 10)) : 0);

        renderScoreboard();
      }

      function finishRoll(knocked) {
        totalScore += knocked;
        framePinsRemaining -= knocked;
        saveHighScoreIfNeeded();

        if (roll === 1 && knocked === 10) {
          writeRollToScoreboard(knocked, true, false);
          result.textContent = "💥 STRIKE! Who do you think you are I am!";
          updateHud();
          levelUp("STRIKE!");
          setTimeout(() => nextFrame(), 950);
          return;
        }

        if (roll === 2 && framePinsRemaining === 0) {
          writeRollToScoreboard(knocked, false, true);
          result.textContent = "✨ Spare!";
          updateHud();
          levelUp("SPARE!");
          setTimeout(() => nextFrame(), 950);
          return;
        }

        writeRollToScoreboard(knocked, false, false);

        if (knocked === 0) {
          result.textContent = "Mark it zero!";
        } else if (knocked >= 7) {
          result.textContent = `${knocked} pins! Noice!`;
        } else if (knocked >= 4) {
          result.textContent = `${knocked} pins. Not too bad!`;
        } else {
          result.textContent = `${knocked} pins. At least it something!`;
        }

        if (roll === 1) {
          roll = 2;
          updateHud();
        } else {
          nextFrame();
        }
      }

      function rollBall() {
        if (rolling || frame > 3 || rollBtn.disabled) return;
        rolling = true;

        const angle = Number(aimSlider.value);
        const power = Number(powerSlider.value);
        const spin = Number(spinSlider.value);

        const drift = (angle * 2) + (spin * 1.4) + ((ballX - 50) * 1.6);
        const distance = 290 + (power * 1.75);

        ball.style.setProperty("--drift", `${drift}px`);
        ball.style.setProperty("--distance", `${distance}px`);
        ball.style.animation = "none";
        void ball.offsetWidth;
        ball.style.animation = `roll ${0.9 + (100 - power) / 80}s ease-out forwards`;

        const knocked = scoreRoll(angle, power, spin, framePinsRemaining);

        setTimeout(() => {
          knockPins(knocked);
          finishRoll(knocked);

          setTimeout(() => {
            ball.style.animation = "none";
            void ball.offsetWidth;
            rolling = false;
            updateBallPositionVisual();
          }, 650);
        }, 900);
      }

      async function copyInviteText() {
        const text = `🎳 Brad is leveling up to 30!

Join us for Brad’s birthday bowling bash
Saturday, April 11, 2026

Dinner: 3:00 PM at Railroad
Bowling: 5:00 PM at Strikerz at Angel of the Winds Casino

Bowling is $10/person.
If you want to bowl, Venmo Brad @Bradley-Jarvensivu`;

        try {
          await navigator.clipboard.writeText(text);
          copyStatus.textContent = "Invite text copied — just swap in your real link.";
        } catch (err) {
          copyStatus.textContent = "Clipboard access was blocked here, but the invite text is built into the code.";
        }
      }

      function setBallXFromClientX(clientX) {
        const rect = lane.getBoundingClientRect();
        const pct = ((clientX - rect.left) / rect.width) * 100;
        ballX = clamp(pct, 14, 86);
        updateBallPositionVisual();
      }

let dragStartX = 0;
let dragMoved = false;

      ball.addEventListener("pointerdown", (e) => {
        if (rolling) return;
        dragging = true;
        dragMoved = false;
        dragStartX = e.clientX;
        ball.classList.add("dragging");
        ball.setPointerCapture(e.pointerId);
      });

      ball.addEventListener("pointermove", (e) => {
        if (!dragging || rolling) return;
        dragMoved = true;
        setBallXFromClientX(e.clientX);
      });

      ball.addEventListener("pointerup", (e) => {
        dragging = false;
        ball.classList.remove("dragging");

        try { ball.releasePointerCapture(e.pointerId); } catch {}

        // If it wasn’t dragged → treat as a click
        if (!dragMoved && !rolling) {
          rollBall();
        }
      });

      ball.addEventListener("pointercancel", () => {
        dragging = false;
        ball.classList.remove("dragging");
      });

      function adjustSlider(slider, amount, min, max) {
        const next = clamp(Number(slider.value) + amount, min, max);
        slider.value = next;
        updateHud();
      }

      function adjustBall(amount) {
        ballX = clamp(ballX + amount, 14, 86);
        updateHud();
      }

      document.addEventListener("keydown", (e) => {
        if (e.key === "ArrowLeft") adjustBall(-2);
        if (e.key === "ArrowRight") adjustBall(2);
        if (e.key.toLowerCase() === "a") adjustSlider(aimSlider, -2, -32, 32);
        if (e.key.toLowerCase() === "d") adjustSlider(aimSlider, 2, -32, 32);
        if (e.key === "ArrowUp") adjustSlider(powerSlider, 2, 40, 100);
        if (e.key === "ArrowDown") adjustSlider(powerSlider, -2, 40, 100);
        if (e.key.toLowerCase() === "j") adjustSlider(spinSlider, -2, -30, 30);
        if (e.key.toLowerCase() === "l") adjustSlider(spinSlider, 2, -30, 30);

        if (e.code === "Space") {
          e.preventDefault();
          rollBall();
        }
      });

      aimSlider.addEventListener("input", updateHud);
      powerSlider.addEventListener("input", updateHud);
      spinSlider.addEventListener("input", updateHud);
      rollBtn.addEventListener("click", rollBall);
      resetBtn.addEventListener("click", resetWholeGame);

      ballOptions.forEach(btn => {
        btn.addEventListener("click", () => setBallStyle(btn.dataset.ball));
      });

      setBallStyle("sparkly");
      resetScoreData();
      resetFramePins();
      updateHud();
    });
  </script>
</body>
</html>
