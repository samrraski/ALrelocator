<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>AL Relocator</title>

  <style>
    :root{
      --bg:#f6f8ff;
      --card:#ffffff;
      --text:#0f172a;
      --muted:#475569;
      --border:rgba(15,23,42,.10);
      --shadow:0 18px 45px rgba(15,23,42,.08);
      --primary:#2f6bff;
      --primary2:#1d4ed8;
      --pill:#0f172a;
      --radius:22px;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Arial, "Apple Color Emoji","Segoe UI Emoji";
      color:var(--text);
      background:linear-gradient(180deg, #ffffff 0%, var(--bg) 80%);
    }
    a{color:inherit; text-decoration:none}
    .wrap{max-width:1120px; margin:0 auto; padding:0 20px;}

    /* Top header */
    .topbar{
      position:sticky; top:0; z-index:50;
      padding:18px 0;
      backdrop-filter:saturate(140%) blur(10px);
      background:rgba(255,255,255,.75);
      border-bottom:1px solid rgba(15,23,42,.06);
    }
    .nav{
      display:flex; align-items:center; justify-content:space-between;
      gap:14px;
    }
    .brand{
      display:flex; align-items:center; gap:12px;
      font-weight:800;
    }
    .logo{
      width:38px; height:38px; border-radius:12px;
      display:grid; place-items:center;
      background:#ffe7d6;
      border:1px solid rgba(15,23,42,.08);
      font-size:18px;
    }
    .tagline{
      font-weight:600;
      color:var(--muted);
      font-size:12px;
      margin-left:6px;
    }
    .menu{
      display:flex; align-items:center; gap:18px;
      color:#111827;
      font-weight:600;
      font-size:14px;
    }
    .menu a{opacity:.9}
    .menu a:hover{opacity:1}
    .actions{
      display:flex; align-items:center; gap:10px;
    }
    .pill{
      display:inline-flex; align-items:center; gap:8px;
      padding:10px 14px;
      border-radius:999px;
      border:1px solid var(--border);
      background:var(--card);
      box-shadow:0 8px 18px rgba(15,23,42,.06);
      font-weight:700;
      font-size:13px;
      white-space:nowrap;
    }
    .pill.dark{
      background:var(--pill);
      color:#fff;
      border-color:rgba(255,255,255,.08);
    }
    .iconbtn{
      width:40px; height:40px; border-radius:999px;
      border:1px solid var(--border);
      background:var(--card);
      display:grid; place-items:center;
      box-shadow:0 8px 18px rgba(15,23,42,.06);
      font-weight:900;
    }

    /* Hero */
    .hero{
      padding:38px 0 26px;
    }
    .heroCard{
      background:rgba(255,255,255,.9);
      border:1px solid rgba(15,23,42,.08);
      border-radius:28px;
      box-shadow:var(--shadow);
      padding:34px;
      overflow:hidden;
      position:relative;
    }
    .heroGrid{
      display:grid;
      grid-template-columns: 1.15fr .85fr;
      gap:22px;
      align-items:center;
    }
    .crumb{
      color:var(--muted);
      font-weight:700;
      font-size:13px;
      margin-bottom:14px;
    }
    h1{
      font-size:56px;
      line-height:1.02;
      margin:0 0 16px;
      letter-spacing:-.03em;
    }
    .sub{
      font-size:18px;
      color:var(--muted);
      line-height:1.5;
      margin:0 0 22px;
      max-width:620px;
    }
    .sub b{color:var(--primary)}
    .ctaRow{
      display:flex; gap:12px; flex-wrap:wrap;
      margin:0 0 26px;
    }
    .btn{
      padding:14px 18px;
      border-radius:999px;
      border:1px solid var(--border);
      background:var(--card);
      font-weight:800;
      font-size:14px;
      box-shadow:0 10px 22px rgba(15,23,42,.06);
    }
    .btn.primary{
      background:var(--primary);
      color:#fff;
      border-color:rgba(255,255,255,.15);
    }
    .btn.primary:hover{background:var(--primary2)}
    .btn:hover{transform:translateY(-1px)}
    .stats{
      display:flex; gap:30px; flex-wrap:wrap;
      padding-top:6px;
    }
    .stat{
      min-width:160px;
    }
    .stat .big{
      font-size:22px;
      font-weight:900;
      margin-bottom:4px;
    }
    .stat .small{
      font-size:12px;
      color:var(--muted);
      font-weight:700;
    }

    /* Illustration (right side) */
    .art{
      position:relative;
      min-height:320px;
    }
    .blob{
      position:absolute; inset:0;
      border-radius:28px;
      background:
        radial-gradient(circle at 30% 40%, rgba(47,107,255,.14) 0 38%, transparent 40%),
        radial-gradient(circle at 70% 60%, rgba(255,167,38,.18) 0 35%, transparent 37%),
        radial-gradient(circle at 50% 50%, rgba(15,23,42,.06) 0 52%, transparent 54%);
      filter: blur(.2px);
    }
    .face{
      position:absolute;
      right:18px; top:30px;
      width:210px; height:210px;
      border-radius:999px;
      background:#ffcc8a;
      border:10px solid #111;
      display:grid; place-items:center;
      box-shadow:0 25px 50px rgba(15,23,42,.18);
    }
    .eyes{
      display:flex; gap:22px; margin-top:-18px;
    }
    .eye{
      width:48px; height:48px; border-radius:999px;
      background:#fff; border:8px solid #111;
      position:relative;
    }
    .eye::after{
      content:"";
      width:16px; height:16px; border-radius:999px;
      background:#111;
      position:absolute; left:14px; top:14px;
    }
    .moustache{
      width:130px; height:42px;
      margin-top:12px;
      border-radius:40px;
      background:#111;
      transform:skewX(-10deg);
      position:relative;
    }
    .moustache::after{
      content:"";
      position:absolute; right:-10px; top:0;
      width:70px; height:42px; border-radius:40px;
      background:#111;
      transform:skewX(20deg);
    }
    .cardMini{
      position:absolute;
      right:16px; bottom:16px;
      width:240px;
      background:#ff7a2f;
      color:#fff;
      border-radius:18px;
      padding:14px 14px 12px;
      box-shadow:0 18px 40px rgba(15,23,42,.18);
      display:flex; gap:12px;
      align-items:center;
    }
    .miniBadge{
      width:44px; height:44px; border-radius:14px;
      background:rgba(255,255,255,.22);
      border:1px solid rgba(255,255,255,.25);
      display:grid; place-items:center;
      font-weight:900;
    }
    .miniText{font-weight:900; font-size:14px; line-height:1.2}
    .miniText span{display:block; font-weight:700; opacity:.9; font-size:12px; margin-top:4px}

    /* Section title below */
    .section{
      padding:22px 0 60px;
    }
    .section h2{
      font-size:44px;
      letter-spacing:-.03em;
      margin:18px 0 0;
    }

    /* Responsive */
    @media (max-width: 900px){
      .menu{display:none;}
      h1{font-size:44px}
      .heroGrid{grid-template-columns:1fr}
      .art{min-height:280px}
      .face{right:10px; top:18px; width:190px; height:190px}
      .cardMini{width:220px}
    }
  </style>
</head>

<body>

  <!-- Top Nav -->
  <div class="topbar">
    <div class="wrap">
      <div class="nav">
        <div class="brand">
          <div class="logo">🙂</div>
          <div>
            <div style="display:flex;align-items:center;gap:10px;">
              <div style="font-size:16px;">AL Relocator</div>
              <div class="tagline">We help you move (UAE / Spain)</div>
            </div>
          </div>
        </div>

        <div class="menu">
          <a href="#services">Services</a>
          <a href="#guides">Guides</a>
          <a href="#blog">Blog</a>
          <a href="#prices">Price List</a>
          <a href="#faq">FAQ</a>
          <a href="#cases">Cases</a>
          <a href="#reviews">Reviews</a>
        </div>

        <div class="actions">
          <div class="pill">English ▾</div>
          <a class="pill dark" href="tel:+1-000-000-0000">📞 +1 (000) 000-0000</a>
          <a class="iconbtn" href="#" title="WhatsApp">🟢</a>
          <a class="iconbtn" href="#" title="Telegram">✈️</a>
        </div>
      </div>
    </div>
  </div>

  <!-- Hero -->
  <div class="hero">
    <div class="wrap">
      <div class="heroCard">
        <div class="heroGrid">
          <div>
            <div class="crumb">Home</div>
            <h1>Turnkey relocation to Dubai from 6 weeks</h1>
            <p class="sub">
              We help you obtain a residence permit for the whole family
              with a <b>minimum tax</b> burden and clear step-by-step support.
            </p>

            <div class="ctaRow">
              <a class="btn primary" href="#consult">Get a free consultation</a>
              <a class="btn" href="#services">Select the type of residence permit</a>
            </div>

            <div class="stats">
              <div class="stat">
                <div class="big">From 0%</div>
                <div class="small">Tax burden (depends on program)</div>
              </div>
              <div class="stat">
                <div class="big">From 6 weeks</div>
                <div class="small">Estimated processing time</div>
              </div>
              <div class="stat">
                <div class="big">5 years</div>
                <div class="small">Path to long-term residency</div>
              </div>
            </div>
          </div>

          <div class="art">
            <div class="blob"></div>

            <div class="face" aria-hidden="true">
              <div style="text-align:center;">
                <div class="eyes">
                  <div class="eye"></div>
                  <div class="eye"></div>
                </div>
                <div class="moustache"></div>
              </div>
            </div>

            <div class="cardMini" aria-hidden="true">
              <div class="miniBadge">ID</div>
              <div class="miniText">
                Residence permit
                <span>Documents • Timeline • Support</span>
              </div>
            </div>

          </div>
        </div>
      </div>

      <div class="section">
        <h2>Benefits of Relocation</h2>
      </div>
    </div>
  </div>

</body>
</html>
