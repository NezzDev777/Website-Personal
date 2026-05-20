<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>NezzEssent — Premium Minecraft Server Tools</title>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
<style>
:root{
  --primary:#6366f1;
  --primary-glow:#818cf8;
  --bg:#0a0a0f;
  --card:#12121a;
  --border:#ffffff08;
  --text:#ffffff;
  --muted:#9ca3af;
}
*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{font-family:'Outfit',sans-serif;color:var(--text);background:var(--bg);overflow-x:hidden;}

/* LOADER */
.loader-overlay{position:fixed;inset:0;z-index:9999;background:var(--bg);display:flex;flex-direction:column;align-items:center;justify-content:center;transition:opacity .6s,visibility .6s}
.loader-overlay.hidden{opacity:0;visibility:hidden;pointer-events:none}
.loader-logo-wrap{position:relative;margin-bottom:40px;text-align:center;width:100%}
.loader-logo{width:120px;height:auto;display:inline-block;animation:loaderPulse 1.5s ease-in-out infinite}
@keyframes loaderPulse{0%,100%{transform:scale(1);filter:drop-shadow(0 0 20px rgba(99,102,241,.6)) drop-shadow(0 0 40px rgba(99,102,241,.3))}50%{transform:scale(1.05);filter:drop-shadow(0 0 40px rgba(99,102,241,1)) drop-shadow(0 0 60px rgba(99,102,241,.5))}}
.loader-glow{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:200px;height:200px;background:radial-gradient(circle,rgba(99,102,241,.5) 0%,transparent 70%);filter:blur(40px);animation:loaderGlowPulse 2s ease-in-out infinite;pointer-events:none}
@keyframes loaderGlowPulse{0%,100%{opacity:.5;transform:translate(-50%,-50%) scale(1)}50%{opacity:1;transform:translate(-50%,-50%) scale(1.2)}}
.loader-bar{width:200px;height:4px;background:#1a1a24;border-radius:4px;overflow:hidden}
.loader-progress{height:100%;width:0;background:linear-gradient(90deg,var(--primary),var(--primary-glow));border-radius:4px;animation:loadBar 2s ease-in-out forwards}
@keyframes loadBar{0%{width:0}50%{width:70%}100%{width:100%}}
.loader-text{font-size:14px;color:var(--muted);margin-top:24px;letter-spacing:2px}

/* BG */
.bg{position:fixed;inset:0;z-index:0;background:var(--bg)}
.bg-gradient{position:absolute;inset:0;background:radial-gradient(ellipse at 20% 50%,rgba(99,102,241,.15) 0%,transparent 50%),radial-gradient(ellipse at 80% 50%,rgba(139,92,246,.1) 0%,transparent 50%),radial-gradient(ellipse at 50% 100%,rgba(99,102,241,.08) 0%,transparent 40%)}
.bg-grid{position:absolute;inset:0;background-image:linear-gradient(rgba(255,255,255,.02) 1px,transparent 1px),linear-gradient(90deg,rgba(255,255,255,.02) 1px,transparent 1px);background-size:60px 60px;mask-image:radial-gradient(ellipse at center,black 20%,transparent 80%)}
.bg-glow{position:absolute;top:-200px;left:50%;transform:translateX(-50%);width:600px;height:600px;background:radial-gradient(circle,rgba(99,102,241,.3) 0%,transparent 70%);filter:blur(80px);animation:glowPulse 4s ease-in-out infinite}
@keyframes glowPulse{0%,100%{opacity:.5;transform:translateX(-50%) scale(1)}50%{opacity:.8;transform:translateX(-50%) scale(1.1)}}

/* NAV */
nav{position:fixed;top:0;left:0;right:0;z-index:500;height:64px;display:flex;align-items:center;justify-content:space-between;padding:0 40px;background:rgba(10,10,15,.8);backdrop-filter:blur(20px);border-bottom:1px solid var(--border)}
.nav-logo-wrap{position:relative;display:flex;align-items:center}
.nav-logo-wrap img{height:36px;filter:drop-shadow(0 0 10px rgba(99,102,241,.5));transition:filter .3s}
.nav-logo-wrap:hover img{filter:drop-shadow(0 0 20px rgba(99,102,241,.8)) drop-shadow(0 0 40px rgba(99,102,241,.4))}
.nav-links{display:flex;gap:32px;list-style:none}
.nav-links a{font-size:14px;font-weight:600;color:var(--muted);text-decoration:none;transition:color .2s}
.nav-links a:hover{color:var(--text)}
.nav-links a.dev-link{color:var(--primary)}
.nav-links a.dev-link:hover{color:var(--primary-glow)}
.btn-nav{font-size:14px;font-weight:700;padding:10px 24px;background:var(--primary);color:#fff;border:none;border-radius:8px;cursor:pointer;text-decoration:none;transition:all .2s;box-shadow:0 4px 20px rgba(99,102,241,.3)}
.btn-nav:hover{background:var(--primary-dark);box-shadow:0 4px 30px rgba(99,102,241,.5);transform:translateY(-2px)}

/* HERO */
.hero{position:relative;z-index:10;min-height:100vh;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:120px 24px}
.hero-logo-wrap{position:relative;margin-bottom:32px;text-align:center;width:100%}
.hero-logo{height:clamp(80px,12vw,140px);width:auto;display:inline-block;animation:float 3s ease-in-out infinite}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-10px)}}
.hero-glow{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:250px;height:250px;background:radial-gradient(circle,rgba(99,102,241,.5) 0%,transparent 70%);filter:blur(50px);animation:heroGlow 3s ease-in-out infinite;pointer-events:none}
@keyframes heroGlow{0%,100%{opacity:.6;transform:translate(-50%,-50%) scale(1)}50%{opacity:1;transform:translate(-50%,-50%) scale(1.1)}}
.hero-title{font-size:clamp(28px,5vw,56px);font-weight:800;line-height:1.2;margin-bottom:20px;text-shadow:0 0 40px rgba(99,102,241,.3)}
.hero-title span{color:var(--primary);text-shadow:0 0 30px rgba(99,102,241,.5)}
.hero-desc{font-size:18px;color:var(--muted);max-width:500px;line-height:1.6;margin-bottom:40px}
.hero-btns{display:flex;gap:16px;flex-wrap:wrap;justify-content:center;margin-bottom:60px}
.btn-primary{font-size:16px;font-weight:700;padding:16px 36px;background:var(--primary);color:#fff;border:none;border-radius:12px;cursor:pointer;text-decoration:none;transition:all .2s;box-shadow:0 8px 30px rgba(99,102,241,.4)}
.btn-primary:hover{background:var(--primary-dark);transform:translateY(-3px);box-shadow:0 12px 40px rgba(99,102,241,.5)}
.btn-secondary{font-size:16px;font-weight:600;padding:16px 36px;background:transparent;color:#fff;border:2px solid rgba(255,255,255,.15);border-radius:12px;cursor:pointer;text-decoration:none;transition:all .3s}
.btn-secondary:hover{border-color:var(--primary);background:rgba(99,102,241,.1);box-shadow:0 0 30px rgba(99,102,241,.2)}
.hero-stats{display:flex;gap:2px}
.stat{padding:20px 40px;background:var(--card);border:1px solid var(--border);text-align:center;position:relative;overflow:hidden}
.stat::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,var(--primary),transparent);opacity:0}
.stat:hover::before{opacity:1}
.stat:first-child{border-radius:12px 0 0 12px}
.stat:last-child{border-radius:0 12px 12px 0}
.stat-v{font-size:20px;font-weight:800;color:var(--primary);margin-bottom:4px;text-shadow:0 0 20px rgba(99,102,241,.5)}
.stat-l{font-size:12px;font-weight:600;color:var(--muted)}

/* SECTIONS */
.sec{position:relative;z-index:10;padding:80px 24px}
.sec-in{max-width:1100px;margin:0 auto}
.sec-tag{font-size:12px;font-weight:700;color:var(--primary);letter-spacing:2px;text-transform:uppercase;text-align:center;margin-bottom:12px;text-shadow:0 0 20px rgba(99,102,241,.3)}
.sec-h{font-size:clamp(24px,4vw,40px);font-weight:800;text-align:center;margin-bottom:16px}
.sec-sub{font-size:16px;color:var(--muted);text-align:center;max-width:500px;margin:0 auto 48px;line-height:1.6}

/* FEATURES COMPACT */
.feat-list{display:flex;flex-wrap:wrap;gap:10px;justify-content:center;margin-top:24px}
.feat-tag{display:inline-flex;align-items:center;gap:8px;padding:10px 18px;background:var(--card);border:1px solid var(--border);border-radius:50px;font-size:13px;font-weight:600;color:var(--muted);transition:all .3s}
.feat-tag:hover{border-color:var(--primary);color:var(--text);transform:translateY(-3px);box-shadow:0 8px 25px rgba(99,102,241,.2)}
.feat-tag span{font-size:18px}

/* PRICING */
.price-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:24px;max-width:800px;margin:0 auto}
@media(max-width:700px){.price-grid{grid-template-columns:1fr}}
.pc{background:var(--card);border:1px solid var(--border);border-radius:20px;padding:48px 40px 40px;transition:all .3s;text-align:center;position:relative;overflow:hidden}
.pc::before{content:'';position:absolute;top:0;left:-100%;width:100%;height:100%;background:linear-gradient(90deg,transparent,rgba(99,102,241,.1),transparent);transition:left .5s}
.pc:hover::before{left:100%}
.pc:hover{transform:translateY(-8px);box-shadow:0 20px 60px rgba(99,102,241,.2)}
.pc.hot{border-color:var(--primary);box-shadow:0 0 40px rgba(99,102,241,.2);transform:translateY(-4px)}
.pc-badge{position:absolute;top:-16px;left:50%;transform:translateX(-50%);background:linear-gradient(135deg,var(--primary),#8b5cf6);color:#fff;font-size:12px;font-weight:700;padding:8px 20px;border-radius:20px;box-shadow:0 4px 20px rgba(99,102,241,.4);z-index:10;white-space:nowrap}
.pc-name{font-size:20px;font-weight:700;margin-bottom:8px}
.pc-price{font-size:32px;font-weight:800;color:var(--primary);margin-bottom:4px;text-shadow:0 0 20px rgba(99,102,241,.4)}
.pc-period{font-size:14px;color:var(--muted);margin-bottom:24px}
.pc-list{list-style:none;margin-bottom:24px;text-align:left}
.pc-list li{font-size:15px;color:var(--muted);padding:10px 0;border-bottom:1px solid var(--border)}
.pc-list li::before{content:"✓ ";color:var(--primary);font-weight:700}
.btn-price{font-size:15px;font-weight:700;padding:16px;width:100%;border-radius:12px;border:none;cursor:pointer;text-decoration:none;display:block;text-align:center;transition:all .2s}
.btn-vip{background:linear-gradient(135deg,var(--primary),#8b5cf6);color:#fff;box-shadow:0 8px 30px rgba(99,102,241,.4)}
.btn-vip:hover{box-shadow:0 12px 40px rgba(99,102,241,.5);transform:translateY(-2px)}
.btn-custom{background:transparent;color:var(--primary);border:2px solid var(--primary)}
.btn-custom:hover{background:rgba(99,102,241,.1)}

/* STEPS */
.steps{display:grid;grid-template-columns:repeat(4,1fr);gap:24px}
@media(max-width:900px){.steps{grid-template-columns:repeat(2,1fr)}}
@media(max-width:500px){.steps{grid-template-columns:1fr}}
.step{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:32px;text-align:center;transition:all .3s;position:relative}
.step:hover{transform:translateY(-4px);border-color:rgba(99,102,241,.3)}
.step-num{font-size:36px;font-weight:800;color:var(--primary);margin-bottom:16px;text-shadow:0 0 30px rgba(99,102,241,.5)}
.step-title{font-size:16px;font-weight:700;margin-bottom:8px}
.step-desc{font-size:14px;color:var(--muted);line-height:1.5}

/* CTA */
#cta{text-align:center;padding:100px 24px;background:linear-gradient(180deg,var(--card) 0%,var(--bg) 100%);position:relative}
#cta::before{content:'';position:absolute;top:0;left:50%;transform:translateX(-50%);width:600px;height:300px;background:radial-gradient(ellipse,rgba(99,102,241,.2) 0%,transparent 70%);filter:blur(60px)}
.cta-title{font-size:clamp(24px,4vw,40px);font-weight:800;margin-bottom:16px}
.cta-title span{color:var(--primary);text-shadow:0 0 30px rgba(99,102,241,.5)}
.cta-desc{font-size:18px;color:var(--muted);margin-bottom:32px}
.cta-note{font-size:13px;color:var(--muted);margin-top:20px}

/* FOOTER */
footer{position:relative;z-index:10;padding:48px 24px;text-align:center;border-top:1px solid var(--border)}
.footer-logo-wrap{position:relative;display:inline-block;margin-bottom:24px}
.footer-logo-wrap img{height:44px;filter:drop-shadow(0 0 15px rgba(99,102,241,.4));transition:filter .3s}
.footer-logo-wrap:hover img{filter:drop-shadow(0 0 25px rgba(99,102,241,.6)) drop-shadow(0 0 50px rgba(99,102,241,.3))}
.footer-links{display:flex;gap:32px;justify-content:center;flex-wrap:wrap;margin-bottom:24px}
.footer-links a{font-size:14px;color:var(--muted);text-decoration:none;transition:color .2s}
.footer-links a:hover{color:var(--primary)}
.footer-dev{font-size:14px;color:var(--primary);margin-bottom:16px;text-decoration:none;transition:all .2s;display:inline-block}
.footer-dev:hover{color:var(--primary-glow);text-shadow:0 0 20px rgba(99,102,241,.5)}
.footer-copy{font-size:14px;color:var(--muted)}

/* MODAL */
.modal-overlay{position:fixed;inset:0;z-index:1000;background:rgba(0,0,0,.85);backdrop-filter:blur(8px);display:flex;align-items:center;justify-content:center;padding:20px;opacity:0;pointer-events:none;transition:opacity .3s}
.modal-overlay.active{opacity:1;pointer-events:all}
.modal{background:var(--card);border:1px solid rgba(99,102,241,.3);border-radius:20px;width:100%;max-width:440px;padding:32px;position:relative;transform:translateY(20px);transition:transform .3s;box-shadow:0 0 60px rgba(99,102,241,.2)}
.modal-overlay.active .modal{transform:translateY(0)}
.modal-close{position:absolute;top:16px;right:16px;background:none;border:none;color:var(--muted);font-size:24px;cursor:pointer;transition:color .2s}
.modal-close:hover{color:var(--text)}
.modal-logo-wrap{position:relative;display:block;text-align:center;margin-bottom:24px}
.modal-logo-wrap img{height:48px;width:auto;filter:drop-shadow(0 0 15px rgba(99,102,241,.5));display:block;margin:0 auto}
.modal-title{font-size:20px;font-weight:700;text-align:center;margin-bottom:8px}
.modal-sub{font-size:14px;color:var(--muted);text-align:center;margin-bottom:24px}
.pay-tabs{display:flex;gap:12px;margin-bottom:24px}
.pay-tab{flex:1;padding:14px;border-radius:10px;border:2px solid var(--border);background:none;color:var(--muted);font-size:14px;font-weight:600;cursor:pointer;transition:all .2s}
.pay-tab.active{border-color:var(--primary);background:rgba(99,102,241,.1);color:#fff}
.pay-tab:hover{border-color:var(--primary)}
.pay-content{display:none}
.pay-content.active{display:block}
.qris-label{font-size:11px;font-weight:700;color:var(--primary);letter-spacing:2px;text-transform:uppercase;text-align:center;margin-bottom:12px}
.qris-amount{font-size:28px;font-weight:800;color:var(--primary);text-align:center;margin-bottom:16px;text-shadow:0 0 20px rgba(99,102,241,.4)}
.qris-wrap{background:#fff;border-radius:12px;padding:12px;margin-bottom:20px;box-shadow:0 0 20px rgba(99,102,241,.1)}
.qris-wrap img{width:100%;border-radius:8px;display:block}
.qris-note{font-size:14px;color:var(--muted);text-align:center;line-height:1.5;margin-bottom:20px}
.btn-confirm{display:block;width:100%;padding:16px;background:var(--primary);color:#fff;font-size:15px;font-weight:700;border:none;border-radius:12px;cursor:pointer;text-decoration:none;text-align:center;transition:all .2s;box-shadow:0 8px 30px rgba(99,102,241,.3)}
.btn-confirm:hover{background:var(--primary-dark);box-shadow:0 8px 40px rgba(99,102,241,.4)}

/* DEV MODAL */
.dev-modal .modal{max-width:500px;text-align:center}
.dev-modal .modal-title{font-size:24px;margin-bottom:16px}
.dev-modal .modal-sub{font-size:16px;color:var(--muted);margin-bottom:24px}
.dev-avatar{width:120px;height:120px;border-radius:50%;margin:0 auto 20px;background:linear-gradient(135deg,var(--primary),#8b5cf6);display:flex;align-items:center;justify-content:center;font-size:48px;box-shadow:0 0 40px rgba(99,102,241,.4)}
.dev-name{font-size:20px;font-weight:700;color:var(--text);margin-bottom:4px}
.dev-role{font-size:14px;color:var(--primary);margin-bottom:24px}
.dev-info{font-size:15px;color:var(--muted);line-height:1.6;margin-bottom:24px}
.dev-social{display:flex;gap:16px;justify-content:center}
.dev-social a{display:flex;align-items:center;justify-content:center;width:48px;height:48px;background:var(--card);border:1px solid var(--border);border-radius:12px;color:var(--muted);text-decoration:none;transition:all .2s;font-size:20px}
.dev-social a:hover{border-color:var(--primary);color:var(--primary);transform:translateY(-3px);box-shadow:0 8px 30px rgba(99,102,241,.2)}

/* TOAST */
#toast{position:fixed;bottom:24px;left:50%;transform:translateX(-50%) translateY(100px);background:var(--card);border:1px solid var(--primary);color:#fff;padding:14px 24px;border-radius:12px;font-size:14px;font-weight:600;z-index:2000;opacity:0;transition:all .4s;box-shadow:0 0 30px rgba(99,102,241,.3)}
#toast.show{transform:translateX(-50%) translateY(0);opacity:1}

/* RESPONSIVE */
@media(max-width:768px){
  nav{padding:0 16px}
  .nav-links{display:none}
  .hero{padding:100px 16px 60px}
  .hero-stats{flex-direction:column;gap:4px}
  .stat:first-child,.stat:last-child{border-radius:12px}
  .sec{padding:60px 16px}
}
</style>
</head>
<body>

<!-- LOADER -->
<div class="loader-overlay" id="loader">
  <div class="loader-logo-wrap">
    <div class="loader-glow"></div>
    <img class="loader-logo" src="https://plain-apac-prod-public.komododecks.com/202605/20/28aiSIEGQ6eNlKCXAHWg/image.png" alt="Loading">
  </div>
  <div class="loader-bar"><div class="loader-progress"></div></div>
  <div class="loader-text">LOADING</div>
</div>

<div class="bg">
  <div class="bg-glow"></div>
  <div class="bg-gradient"></div>
  <div class="bg-grid"></div>
</div>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo-wrap"><img src="https://plain-apac-prod-public.komododecks.com/202605/20/28aiSIEGQ6eNlKCXAHWg/image.png" alt="NezzEssent"></a>
  <ul class="nav-links">
    <li><a href="#">Beranda</a></li>
    <li><a href="#fitur">Fitur</a></li>
    <li><a href="#harga">Harga</a></li>
    <li><a href="#cara">Cara Order</a></li>
    <li><a href="#" class="dev-link" onclick="openDevModal();return false;">Dev</a></li>
  </ul>
  <a href="#harga" class="btn-nav">Mulai Sekarang</a>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-logo-wrap">
    <div class="hero-glow"></div>
    <img class="hero-logo" src="https://plain-apac-prod-public.komododecks.com/202605/20/28aiSIEGQ6eNlKCXAHWg/image.png" alt="NezzEssent">
  </div>
  <h1 class="hero-title">Server Minecraft<br><span>Premium</span> Tools</h1>
  <p class="hero-desc">Atur server lo gapake lama. Plug & Play, anti-lag, support semua versi.</p>
  <div class="hero-btns">
    <a href="#fitur" class="btn-primary">Lihat Fitur</a>
    <a href="https://wa.me/6289684943741" target="_blank" class="btn-secondary">Hubungi WhatsApp</a>
  </div>
  <div class="hero-stats">
    <div class="stat"><div class="stat-v">10K+</div><div class="stat-l">Server</div></div>
    <div class="stat"><div class="stat-v">4.9</div><div class="stat-l">Rating</div></div>
    <div class="stat"><div class="stat-v">All</div><div class="stat-l">Versions</div></div>
    <div class="stat"><div class="stat-v">24/7</div><div class="stat-l">Support</div></div>
  </div>
</section>

<!-- FITUR -->
<section class="sec" id="fitur">
  <div class="sec-in">
    <div class="sec-tag">Fitur Unggulan</div>
    <h2 class="sec-h">Powerful Addon Minecraft</h2>
    <p class="sec-sub">19+ fitur premium untuk pengalaman server terbaik</p>
    <div class="feat-list">
      <div class="feat-tag">Gacha</div>
      <div class="feat-tag">Boss RPG</div>
      <div class="feat-tag">Clans</div>
      <div class="feat-tag">NPC 3D/4D</div>
      <div class="feat-tag">Rank Shop</div>
      <div class="feat-tag">PVP Arena</div>
      <div class="feat-tag">Weapon</div>
      <div class="feat-tag">Shop/Sell</div>
      <div class="feat-tag">Floating Menu</div>
      <div class="feat-tag">Fisch</div>
      <div class="feat-tag">Grow Garden</div>
      <div class="feat-tag">Claim Land</div>
      <div class="feat-tag">Set Home</div>
      <div class="feat-tag">TPA</div>
      <div class="feat-tag">RTP</div>
      <div class="feat-tag">Ore Gen</div>
      <div class="feat-tag">Casino</div>
      <div class="feat-tag">Scoreboard</div>
      <div class="feat-tag">Pet RPG</div>
    </div>
  </div>
</section>

<!-- HARGA -->
<section class="sec" id="harga">
  <div class="sec-in">
    <div class="sec-tag">Harga</div>
    <h2 class="sec-h">Pilih Paket</h2>
    <p class="sec-sub">Harga transparan, tidak ada biaya tersembunyi</p>
    <div class="price-grid">
      <div class="pc hot">
        <div class="pc-badge">POPULER</div>
        <div class="pc-name">NezzEssent VIP</div>
        <div class="pc-price">Rp 80.000</div>
        <div class="pc-period">per bulan</div>
        <ul class="pc-list">
          <li>Semua Addon Premium</li>
          <li>Update Otomatis</li>
          <li>Support Prioritas</li>
          <li>Akses Fitur Baru</li>
          <li>Lisensi Server Pribadi</li>
        </ul>
        <a href="#" class="btn-price btn-vip" onclick="openPayModal();return false;">Beli Sekarang</a>
      </div>
      <div class="pc">
        <div class="pc-name">Custom Addon</div>
        <div class="pc-price">Rp 50rb+</div>
        <div class="pc-period">per proyek</div>
        <ul class="pc-list">
          <li>Request Fitur Bebas</li>
          <li>Support Semua Versi</li>
          <li>Dikerjakan Tim Ahli</li>
          <li>Revisi Included</li>
        </ul>
        <a href="https://wa.me/6289684943741" target="_blank" class="btn-price btn-custom">Hubungi Kami</a>
      </div>
    </div>
  </div>
</section>

<!-- CARA ORDER -->
<section class="sec" id="cara">
  <div class="sec-in">
    <div class="sec-tag">Cara Order</div>
    <h2 class="sec-h">4 Langkah Mudah</h2>
    <p class="sec-sub">Proses order yang simpel dan transparan</p>
    <div class="steps">
      <div class="step">
        <div class="step-num">01</div>
        <div class="step-title">Pilih Paket</div>
        <div class="step-desc">Pilih paket yang sesuai dengan kebutuhan server kamu</div>
      </div>
      <div class="step">
        <div class="step-num">02</div>
        <div class="step-title">Bayar</div>
        <div class="step-desc">Bayar via QRIS atau PayPal dengan mudah</div>
      </div>
      <div class="step">
        <div class="step-num">03</div>
        <div class="step-title">Konfirmasi</div>
        <div class="step-desc">Hubungi kami via WhatsApp dengan bukti transfer</div>
      </div>
      <div class="step">
        <div class="step-num">04</div>
        <div class="step-title">Selesai</div>
        <div class="step-desc">Addon langsung bisa digunakan!</div>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->
<section id="cta">
  <div class="sec-in">
    <h2 class="cta-title">Siap tingkatkan server kamu?</h2>
    <p class="cta-desc">Gabung ribuan server yang sudah menggunakan NezzEssent</p>
    <a href="#harga" class="btn-primary">Mulai Sekarang</a>
    <p class="cta-note">★ Cancel kapan aja · No hidden fee ★</p>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo-wrap"><img src="https://plain-apac-prod-public.komododecks.com/202605/20/28aiSIEGQ6eNlKCXAHWg/image.png" alt="NezzEssent"></div>
  <div class="footer-links">
    <a href="#">Beranda</a>
    <a href="#fitur">Fitur</a>
    <a href="#harga">Harga</a>
    <a href="https://wa.me/6289684943741" target="_blank">WhatsApp</a>
  </div>
  <a href="#" class="footer-dev" onclick="openDevModal();return false;">Dibuat oleh AkuOness ✦</a>
  <p class="footer-copy">© 2026 NezzEssent — Built for Minecraft Servers</p>
</footer>

<!-- PAYMENT MODAL -->
<div class="modal-overlay" id="payModal">
  <div class="modal">
    <button class="modal-close" onclick="closePayModal()">×</button>
    <div class="modal-logo-wrap"><img src="https://plain-apac-prod-public.komododecks.com/202605/20/28aiSIEGQ6eNlKCXAHWg/image.png" alt="NezzEssent"></div>
    <div class="modal-title">Metode Pembayaran</div>
    <div class="modal-sub">VIP NezzEssent — Rp 80.000/bulan atau $7 USD</div>
    <div class="pay-tabs">
      <button class="pay-tab active" onclick="switchPayTab('qris')">QRIS</button>
      <button class="pay-tab" onclick="switchPayTab('paypal')">PayPal</button>
    </div>
    <div id="payQris" class="pay-content active">
      <div class="qris-label">SCAN & PAY</div>
      <div class="qris-amount">Rp 80.000</div>
      <div class="qris-wrap"><img src="https://plain-apac-prod-public.komododecks.com/202605/20/6FAQhg4DbfeBMWhKbQ0a/image.jpg" alt="QRIS"></div>
      <div class="qris-note">Scan dengan aplikasi e-wallet atau m-banking</div>
      <a href="https://wa.me/6289684943741?text=Halo%2C%20saya%20sudah%20bayar%20VIP%20NezzEssent%20via%20QRIS%20Rp%2080.000" target="_blank" class="btn-confirm">Sudah Bayar — Chat WhatsApp</a>
    </div>
    <div id="payPaypal" class="pay-content">
      <div class="qris-label">PAYPAL</div>
      <div class="qris-amount">$7.00 USD</div>
      <div class="qris-wrap"><img src="https://i.pinimg.com/736x/9d/53/7b/9d537bc22ed8fa98360c1d9b3ae8cdcb.jpg" alt="PayPal"></div>
      <div class="qris-note">Kirim pembayaran ke akun PayPal kami</div>
      <a href="https://wa.me/6289684943741?text=Halo%2C%20saya%20sudah%20bayar%20VIP%20NezzEssent%20via%20PayPal%20%247" target="_blank" class="btn-confirm">Sudah Bayar — Chat WhatsApp</a>
    </div>
  </div>
</div>

<!-- DEV MODAL -->
<div class="modal-overlay dev-modal" id="devModal">
  <div class="modal">
    <button class="modal-close" onclick="closeDevModal()">×</button>
    <div class="dev-avatar">👑</div>
    <div class="dev-name">AkuOness</div>
    <div class="dev-role">Developer & Designer</div>
    <p class="dev-info">Dibuat dengan passion dan dedikasi untuk memberikan pengalaman terbaik dalam server Minecraft. NezzEssent adalah bukti inovasi dan kualitas.</p>
    <div class="dev-social">
      <a href="https://wa.me/6289684943741" target="_blank" title="WhatsApp">💬</a>
      <a href="#" title="Discord">🎮</a>
    </div>
  </div>
</div>

<div id="toast"></div>

<script>
// Loader
window.addEventListener('load',function(){
  setTimeout(function(){
    document.getElementById('loader').classList.add('hidden');
  },2200);
});

// Payment Modal
function openPayModal(){document.getElementById('payModal').classList.add('active');document.body.style.overflow='hidden'}
function closePayModal(){document.getElementById('payModal').classList.remove('active');document.body.style.overflow=''}
document.getElementById('payModal').addEventListener('click',function(e){if(e.target===this)closePayModal()});
document.addEventListener('keydown',function(e){if(e.key==='Escape')closePayModal()});

function switchPayTab(tab){
  document.querySelectorAll('.pay-tab').forEach(t=>t.classList.remove('active'));
  document.querySelectorAll('.pay-content').forEach(c=>c.classList.remove('active'));
  document.querySelector('.pay-tab:nth-child('+(tab==='qris'?'1':'2')+')').classList.add('active');
  document.getElementById('pay'+tab.charAt(0).toUpperCase()+tab.slice(1)).classList.add('active');
}

// Dev Modal
function openDevModal(){document.getElementById('devModal').classList.add('active');document.body.style.overflow='hidden'}
function closeDevModal(){document.getElementById('devModal').classList.remove('active');document.body.style.overflow=''}
document.getElementById('devModal').addEventListener('click',function(e){if(e.target===this)closeDevModal()});
</script>
</body>
</html>
