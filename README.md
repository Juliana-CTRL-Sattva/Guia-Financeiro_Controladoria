<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Guia Financeiro · Sattva Controladoria</title>
<meta name="description" content="Guia Financeiro da Sattva Controladoria: conceitos, boas práticas e plano de contas explicados de forma simples, com exemplos práticos.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,400;0,500;0,600;0,700;0,800;1,500&display=swap" rel="stylesheet">
<style>
:root{
  --azul-escuro:  #04384B;
  --azul-sattva:  #064A63;
  --azul-claro:   #3B7387;
  --azul-muito-claro: #AFC7D1;
  --amarelo:      #F7A600;
  --amarelo-claro:#FFD27A;
  --grafite:      #505456;
  --cinza-medio:  #8A8E90;
  --cinza-claro:  #D9DDDD;
  --fundo:        #F2F4F5;
  --branco:       #FFFFFF;
  --verde-ok:     #1F8A4C;
  --verde-ok-bg:  #E6F4EC;
  --vermelho:     #C1442C;
  --vermelho-bg:  #FBEAE6;

  --font: 'Montserrat', system-ui, sans-serif;
  --radius: 8px;
  --shadow: 0 2px 10px rgba(4,56,75,0.08);
  --shadow-lg: 0 10px 30px rgba(4,56,75,0.14);
}
*{ box-sizing:border-box; }
html{ scroll-behavior:smooth; }
body{
  margin:0; background:var(--fundo); color:var(--azul-sattva);
  font-family:var(--font); line-height:1.6; font-size:15px;
}
h1,h2,h3,h4{ font-family:var(--font); color:var(--azul-sattva); margin:0 0 10px; }
p{ margin:0 0 12px; color:var(--grafite); }
a{ color:var(--azul-claro); }
.container{ max-width:1180px; margin:0 auto; padding:0 28px; }
strong{ color:var(--azul-sattva); }

/* ---------- toast ---------- */
#toast{
  position:fixed; bottom:26px; left:50%; transform:translateX(-50%) translateY(20px);
  background:var(--azul-escuro); color:#fff; padding:10px 18px; border-radius:6px;
  font-size:0.85rem; font-weight:600; opacity:0; pointer-events:none;
  transition: opacity .25s ease, transform .25s ease; z-index:999; box-shadow:var(--shadow-lg);
}
#toast.show{ opacity:1; transform:translateX(-50%) translateY(0); }

/* ---------- top header ---------- */
.top-header{ position:sticky; top:0; z-index:80; background:#fff; border-bottom:1px solid var(--cinza-claro); box-shadow:0 1px 0 rgba(4,56,75,0.04); }
.top-header-inner{ display:flex; align-items:center; justify-content:space-between; gap:16px; padding:14px 28px; max-width:1180px; margin:0 auto; }
.brand-block{ display:flex; align-items:center; gap:10px; }
.brand-logo-img{ height:32px; width:auto; display:block; flex:none; }
.logo-fallback{ display:none; align-items:center; font-weight:800; font-size:1.05rem; color:var(--azul-sattva); letter-spacing:-0.01em; white-space:nowrap; }
.wordmark{ font-weight:800; font-size:0.74rem; letter-spacing:0.06em; text-transform:uppercase; color:var(--azul-sattva); opacity:0.75; }
.wordmark small{ display:block; font-weight:800; font-size:0.74rem; letter-spacing:0.08em; text-transform:uppercase; color:var(--azul-sattva); opacity:0.75; }
.gf-divider{ width:1px; align-self:stretch; margin:2px 0; background:var(--cinza-claro); flex:none; }
.gf-title{ font-weight:700; font-size:1rem; color:var(--azul-sattva); line-height:1; display:flex; align-items:center; }
.top-actions{ display:flex; gap:10px; align-items:center; }
.menu-toggle{ display:none; border:1.5px solid var(--azul-sattva); background:#fff; border-radius:6px; width:38px; height:38px; align-items:center; justify-content:center; cursor:pointer; flex:none; }

@media (max-width:480px){
  .top-header-inner{ padding:12px 16px; }
  .wordmark{ display:none; }
}
@media (max-width:400px){
  .gf-divider{ display:none; }
}

/* ---------- layout ---------- */
.layout{ display:flex; gap:0; align-items:flex-start; max-width:1180px; margin:0 auto; padding:0 28px; }
.sidebar{ position:sticky; top:70px; width:264px; flex:none; padding:30px 20px 30px 0; max-height: calc(100vh - 70px); overflow-y:auto; }
.sidebar nav{ display:flex; flex-direction:column; gap:2px; }
.sidebar a{ text-decoration:none; font-size:0.85rem; font-weight:600; color:var(--grafite); padding:9px 12px; border-radius:6px; display:flex; align-items:center; gap:10px; border-left:3px solid transparent; }
.sidebar a .n{ font-weight:700; font-size:0.7rem; color:#fff; background:var(--cinza-medio); width:20px; height:20px; border-radius:50%; display:flex; align-items:center; justify-content:center; flex:none; }
.sidebar a:hover{ background:var(--fundo); color:var(--azul-sattva); }
.sidebar a.active{ background:#fff; color:var(--azul-sattva); border-left-color:var(--amarelo); box-shadow:var(--shadow); }
.sidebar a.active .n{ background:var(--amarelo); }
.sidebar .search-mini{ margin:0 0 16px; }

.content{ flex:1; min-width:0; padding:34px 0 90px 34px; border-left:1px solid var(--cinza-claro); }

@media (max-width: 980px){
  .sidebar{ position:fixed; top:65px; left:0; bottom:0; width:78%; max-width:320px; background:#fff; box-shadow:var(--shadow-lg); padding:20px; transform:translateX(-105%); transition:transform .25s ease; z-index:70; max-height:none; }
  .sidebar.open{ transform:translateX(0); }
  .content{ border-left:none; padding-left:0; }
  .menu-toggle{ display:flex; }
}

/* ---------- section ---------- */
.section{ padding:10px 0 46px; border-bottom:1px dashed var(--cinza-claro); margin-bottom:36px; scroll-margin-top:84px; }
.section:last-child{ border-bottom:none; }
.section-eyebrow{ font-size:0.72rem; font-weight:700; letter-spacing:0.1em; text-transform:uppercase; color:var(--amarelo); display:flex; align-items:center; gap:8px; margin-bottom:8px; }
.section-eyebrow .dot{ width:8px; height:8px; border-radius:50%; background:var(--amarelo); }
.section h2{ font-size:1.5rem; font-weight:800; margin-bottom:16px; }

.card{ background:#fff; border:1px solid var(--cinza-claro); border-radius:var(--radius); padding:22px; box-shadow:var(--shadow); }
.grid-2{ display:grid; grid-template-columns:1fr 1fr; gap:18px; }
.grid-3{ display:grid; grid-template-columns:repeat(3,1fr); gap:18px; }
.grid-4{ display:grid; grid-template-columns:repeat(4,1fr); gap:16px; }
@media (max-width:820px){ .grid-2,.grid-3,.grid-4{ grid-template-columns:1fr 1fr; } }
@media (max-width:560px){ .grid-2,.grid-3,.grid-4{ grid-template-columns:1fr; } }

/* ---------- hero / inicio ---------- */
.hero-eyebrow{ font-family:var(--font); font-size:0.78rem; letter-spacing:0.1em; text-transform:uppercase; color:var(--azul-claro); font-weight:700; display:flex; align-items:center; gap:8px; margin-bottom:14px; }
.hero-eyebrow::before{ content:""; width:22px; height:2px; background:var(--azul-claro); display:inline-block; }
.hero h1{ font-size:clamp(1.8rem, 3.4vw, 2.6rem); font-weight:800; max-width:18ch; }
.hero-sub{ font-size:1.02rem; max-width:60ch; }

.search-box{ display:flex; align-items:center; gap:10px; background:#fff; border:1.5px solid var(--azul-sattva); border-radius:8px; padding:6px 6px 6px 16px; max-width:560px; box-shadow:var(--shadow); margin-top:18px; }
.search-box svg{ flex:none; color:var(--grafite); }
.search-box input{ flex:1; border:none; outline:none; background:transparent; font-family:var(--font); font-size:0.95rem; padding:10px 0; color:var(--azul-sattva); }
.search-box button{ font-family:var(--font); font-weight:700; font-size:0.85rem; background:var(--azul-sattva); color:#fff; border:none; border-radius:5px; padding:10px 16px; cursor:pointer; }
.search-box button:hover{ background:var(--azul-escuro); }
.search-box.mini{ max-width:none; padding:4px 4px 4px 12px; margin: 0 0 18px; }
.search-box.mini input{ font-size:0.82rem; padding:8px 0; }
.search-box.mini button{ padding:8px 12px; font-size:0.76rem; }

.pillars{ display:grid; grid-template-columns:repeat(3,1fr); gap:16px; margin-top:26px; }
@media (max-width:900px){ .pillars{ grid-template-columns:1fr 1fr; } }
@media (max-width:560px){ .pillars{ grid-template-columns:1fr; } }
.pillar-card{ background:#fff; border:1px solid var(--cinza-claro); border-radius:var(--radius); padding:22px 20px; box-shadow:var(--shadow); text-decoration:none; display:flex; flex-direction:column; gap:8px; transition:transform .15s ease, box-shadow .15s ease; }
.pillar-card:hover{ transform:translateY(-4px); box-shadow:var(--shadow-lg); text-decoration:none; }
.pillar-tag{ display:inline-flex; align-items:center; gap:6px; font-size:0.7rem; font-weight:800; letter-spacing:.05em; text-transform:uppercase; color:#fff; background:var(--azul-sattva); padding:4px 10px; border-radius:5px; width:fit-content; }
.pillar-card h3{ font-size:1.08rem; margin:6px 0 0; }
.pillar-card p{ font-size:0.88rem; margin:0; }
.pillar-card .go{ font-weight:700; font-size:0.85rem; color:var(--azul-claro); display:inline-flex; align-items:center; gap:6px; margin-top:6px; }

/* ---------- stamps ---------- */
.stamp{ display:inline-flex; align-items:center; gap:6px; font-size:0.7rem; font-weight:800; letter-spacing:.04em; text-transform:uppercase; padding:4px 10px; border-radius:20px; border:1.5px solid currentColor; }
.stamp.azul{ color:var(--azul-sattva); background:var(--fundo); }
.stamp.amarelo{ color:#8a5a00; background:var(--amarelo-claro); }
.stamp.verde{ color:var(--verde-ok); background:var(--verde-ok-bg); }
.stamp.vermelho{ color:var(--vermelho); background:var(--vermelho-bg); }

/* ---------- boxes: exemplo / errado / dica ---------- */
.exemplo{ border-left:3px solid var(--verde-ok); background:var(--verde-ok-bg); padding:14px 18px; border-radius:0 6px 6px 0; margin:14px 0; }
.exemplo .rotulo{ font-size:0.7rem; font-weight:800; text-transform:uppercase; letter-spacing:.05em; color:var(--verde-ok); margin-bottom:6px; display:block; }
.errado{ border-left:3px solid var(--vermelho); background:var(--vermelho-bg); padding:14px 18px; border-radius:0 6px 6px 0; margin:14px 0; }
.errado .rotulo{ font-size:0.7rem; font-weight:800; text-transform:uppercase; letter-spacing:.05em; color:var(--vermelho); margin-bottom:6px; display:block; }
.dica{ border-left:3px solid var(--amarelo); background:#FEF3E0; padding:14px 18px; border-radius:0 6px 6px 0; margin:14px 0; }
.dica .rotulo{ font-size:0.7rem; font-weight:800; text-transform:uppercase; letter-spacing:.05em; color:#8a5a00; margin-bottom:6px; display:block; }
.exemplo p, .errado p, .dica p{ color:var(--azul-sattva); margin:0; }

/* ---------- compare table ---------- */
.compare-table{ width:100%; border-collapse:collapse; margin-top:14px; font-size:0.9rem; }
.compare-table th, .compare-table td{ padding:12px 14px; border:1px solid var(--cinza-claro); text-align:left; vertical-align:top; }
.compare-table thead th{ background:var(--azul-sattva); color:#fff; font-size:0.75rem; text-transform:uppercase; letter-spacing:.04em; }
.compare-table tbody tr:nth-child(odd){ background:var(--fundo); }

/* ---------- checklist ---------- */
.checklist{ list-style:none; margin:0; padding:0; display:flex; flex-direction:column; gap:10px; }
.checklist li{ display:flex; align-items:flex-start; gap:12px; background:#fff; border:1px solid var(--cinza-claro); border-radius:6px; padding:12px 14px; }
.checklist .box{ flex:none; width:20px; height:20px; border:2px solid var(--azul-sattva); border-radius:4px; margin-top:2px; }
.checklist strong{ display:block; font-size:0.95rem; }
.checklist span.desc{ color:var(--grafite); font-size:0.85rem; }

/* ---------- accordion ---------- */
.accordion-item{ border:1px solid var(--cinza-claro); border-radius:6px; margin-bottom:10px; background:#fff; overflow:hidden; }
.accordion-item summary{ cursor:pointer; list-style:none; padding:15px 18px; font-weight:700; font-size:0.92rem; display:flex; justify-content:space-between; align-items:center; gap:12px; }
.accordion-item summary::-webkit-details-marker{ display:none; }
.accordion-item summary::after{ content:"+"; font-size:1.2rem; color:var(--azul-claro); flex:none; font-weight:700; }
.accordion-item[open] summary::after{ content:"–"; }
.accordion-item .accordion-body{ padding:0 18px 18px; color:var(--grafite); font-size:0.9rem; }

/* ---------- plano de contas: filtro ---------- */
.filter-bar{ display:flex; flex-wrap:wrap; gap:10px; align-items:center; margin:6px 0 8px; padding:16px; background:#fff; border:1px solid var(--cinza-claro); border-radius:8px; }
.filter-bar .label{ font-size:0.72rem; text-transform:uppercase; letter-spacing:.05em; color:var(--grafite); margin-right:4px; font-weight:700; }
.chip{ font-family:var(--font); font-weight:700; font-size:0.82rem; padding:7px 14px; border-radius:20px; border:1.5px solid var(--cinza-claro); background:var(--fundo); color:var(--grafite); cursor:pointer; }
.chip:hover{ border-color:var(--azul-sattva); color:var(--azul-sattva); }
.chip.active{ background:var(--azul-sattva); color:#fff; border-color:var(--azul-sattva); }
.download-btn{ margin-left:auto; display:inline-flex; align-items:center; gap:8px; background:var(--amarelo); color:var(--azul-escuro); font-weight:800; font-size:0.85rem; padding:10px 18px; border-radius:6px; text-decoration:none; }
.download-btn:hover{ background:var(--amarelo-claro); text-decoration:none; }
.count-note{ font-size:0.8rem; color:var(--grafite); margin:10px 2px 0; }
.chip.fav-chip{ margin-left:4px; }
.chip.fav-chip.active{ background:var(--amarelo); color:var(--azul-escuro); border-color:var(--amarelo); }

/* ---------- favoritos: painel de acesso rapido ---------- */
.fav-panel{ background:#FEF3E0; border:1px solid var(--amarelo-claro); border-radius:8px; padding:14px 16px; margin:16px 0 0; }
.fav-panel-label{ font-size:0.72rem; font-weight:800; text-transform:uppercase; letter-spacing:.05em; color:#8a5a00; margin-bottom:10px; }
.fav-pill-row{ display:flex; flex-wrap:wrap; gap:8px; }
.fav-pill{ font-family:var(--font); font-size:0.78rem; font-weight:700; color:var(--azul-sattva); background:#fff; border:1px solid var(--amarelo-claro); border-radius:20px; padding:6px 12px; cursor:pointer; }
.fav-pill:hover{ border-color:var(--amarelo); }

/* ---------- favoritos: botao estrela na ficha ---------- */
.fav-btn{ background:none; border:none; font-size:1.3rem; line-height:1; cursor:pointer; color:var(--cinza-medio); padding:0 0 0 6px; }
.fav-btn.active{ color:var(--amarelo); }
.fav-btn:hover{ color:var(--amarelo); }

.ficha.just-favorited{ animation: favPulse 0.6s ease; }
@keyframes favPulse{ 0%{ box-shadow:0 0 0 0 rgba(247,166,0,0.5);} 100%{ box-shadow:0 0 0 12px rgba(247,166,0,0);} }
.ficha.jump-highlight{ outline:2px solid var(--amarelo); outline-offset:2px; }

.ficha-loading, .ficha-error{ grid-column:1/-1; text-align:center; padding:30px; color:var(--grafite); font-size:0.9rem; }
.ficha-error{ background:var(--vermelho-bg); color:var(--vermelho); border-radius:8px; font-weight:600; }

/* ---------- conciliação: linha do tempo ---------- */
.timeline{ position:relative; padding-left:30px; margin-top:18px; }
.timeline::before{ content:""; position:absolute; left:9px; top:6px; bottom:6px; width:2px; background:var(--cinza-claro); }
.timeline-item{ position:relative; margin-bottom:22px; }
.timeline-item:last-child{ margin-bottom:0; }
.timeline-item::before{ content:""; position:absolute; left:-30px; top:2px; width:14px; height:14px; border-radius:50%; background:var(--azul-sattva); border:3px solid #fff; box-shadow:0 0 0 1px var(--cinza-claro); }
.timeline-item h4{ margin:0 0 4px; font-size:0.95rem; }
.timeline-item .freq{ display:inline-flex; align-items:center; gap:6px; font-weight:800; color:var(--verde-ok); font-size:0.85rem; }
.timeline-item p{ margin:4px 0 0; font-size:0.85rem; }

/* ---------- conciliação: passo a passo ---------- */
.steps{ display:grid; grid-template-columns:repeat(4,1fr); gap:16px; margin-top:16px; }
@media (max-width:900px){ .steps{ grid-template-columns:1fr 1fr; } }
@media (max-width:560px){ .steps{ grid-template-columns:1fr; } }
.step-card{ background:#fff; border:1px solid var(--cinza-claro); border-radius:8px; padding:18px; position:relative; }
.step-num{ width:32px; height:32px; border-radius:50%; background:var(--azul-sattva); color:#fff; display:flex; align-items:center; justify-content:center; font-weight:800; font-size:0.9rem; margin-bottom:12px; }
.step-card h4{ font-size:0.92rem; margin-bottom:6px; }
.step-card p{ font-size:0.83rem; margin:0; }
.step-card ul{ margin:8px 0 0; padding-left:16px; font-size:0.8rem; color:var(--grafite); }
.step-card ul li{ margin-bottom:4px; }

/* ---------- conciliação: grade "o que conferir" ---------- */
.conf-grid{ display:grid; grid-template-columns:repeat(3,1fr); gap:10px; margin-top:14px; }
@media (max-width:820px){ .conf-grid{ grid-template-columns:1fr 1fr; } }
@media (max-width:560px){ .conf-grid{ grid-template-columns:1fr; } }
.conf-item{ display:flex; align-items:center; gap:9px; background:#fff; border:1px solid var(--cinza-claro); border-radius:6px; padding:10px 12px; font-size:0.85rem; font-weight:600; color:var(--azul-sattva); }
.conf-item .dotc{ width:8px; height:8px; border-radius:50%; background:var(--azul-claro); flex:none; }

/* ---------- conciliação: checklist final interativo ---------- */
.progress-bar-wrap{ background:var(--cinza-claro); border-radius:20px; height:10px; overflow:hidden; margin:16px 0 8px; }
.progress-bar-fill{ height:100%; background:var(--verde-ok); border-radius:20px; transition:width .3s ease; width:0%; }
.progress-label{ font-size:0.82rem; color:var(--grafite); font-weight:600; }
.final-checklist li{ cursor:pointer; user-select:none; transition:background .15s ease, border-color .15s ease; }
.final-checklist li.done{ background:var(--verde-ok-bg); border-color:var(--verde-ok); }
.final-checklist li.done strong{ color:var(--verde-ok); }
.final-checklist .box{ position:relative; transition:background .15s ease, border-color .15s ease; }
.final-checklist li.done .box{ background:var(--verde-ok); border-color:var(--verde-ok); }
.final-checklist li.done .box::after{ content:"✓"; color:#fff; font-size:12px; font-weight:800; position:absolute; inset:0; display:flex; align-items:center; justify-content:center; }
.reset-checklist{ font-family:var(--font); font-size:0.78rem; font-weight:700; color:var(--grafite); background:none; border:1px solid var(--cinza-claro); border-radius:20px; padding:6px 12px; cursor:pointer; margin-top:12px; }
.reset-checklist:hover{ border-color:var(--vermelho); color:var(--vermelho); }

/* ---------- ficha (conta comentada) ---------- */
.ficha-grid{ display:grid; grid-template-columns:repeat(2,1fr); gap:16px; margin-top:20px; }
@media (max-width:900px){ .ficha-grid{ grid-template-columns:1fr; } }
.ficha{ background:#fff; border:1px solid var(--cinza-claro); border-radius:8px; padding:20px 18px; box-shadow:var(--shadow); border-top:3px solid var(--azul-sattva); }
.ficha-head{ display:flex; justify-content:space-between; align-items:flex-start; gap:10px; margin-bottom:8px; }
.ficha-head .ficha-side{ display:flex; flex-direction:column; align-items:flex-end; gap:6px; }
.ficha-code{ font-size:0.75rem; color:var(--grafite); font-family: monospace; }
.ficha-title{ font-weight:700; font-size:1rem; margin:2px 0 0; color:var(--azul-sattva); }
.ficha dl{ margin:12px 0 0; }
.ficha dt{ font-size:0.68rem; text-transform:uppercase; letter-spacing:.05em; color:var(--cinza-medio); margin-top:10px; font-weight:700; }
.ficha dt:first-child{ margin-top:0; }
.ficha dd{ margin:4px 0 0; font-size:0.88rem; color:var(--azul-sattva); }
.hidden{ display:none !important; }

/* ---------- cta ---------- */
.cta-card{ background:var(--azul-sattva); color:#fff; border-radius:8px; padding:28px; text-align:center; }
.cta-card p{ color:#C9D6DC; }
.cta-card a{ display:inline-flex; align-items:center; gap:8px; background:var(--amarelo); color:var(--azul-escuro); font-weight:800; padding:11px 20px; border-radius:6px; text-decoration:none; margin-top:8px; }

/* ---------- footer ---------- */
.brand-footer{ background:var(--azul-escuro); color:#fff; padding:28px 0; margin-top:0; }
.brand-footer .container{ display:flex; align-items:center; justify-content:space-between; gap:20px; flex-wrap:wrap; }
.footer-brand{ display:flex; align-items:center; gap:14px; }
.footer-logo-img{ height:30px; width:auto; display:block; background:#fff; padding:6px 10px; border-radius:6px; flex:none; }
.brand-footer .tagline{ font-weight:800; font-size:0.9rem; }
.brand-footer .tagline span{ color:var(--amarelo); }
.brand-footer .desc{ font-size:0.78rem; color:#C9D6DC; max-width:40ch; }
/* ---------- ícones ilustrativos de subseção ---------- */
.sec-icon-h3{ display:flex; align-items:center; gap:10px; }
.sec-icon{ flex:none; width:30px; height:30px; border-radius:50%; background:var(--azul-sattva); display:flex; align-items:center; justify-content:center; color:#fff; }
.sec-icon svg{ width:16px; height:16px; }

/* ---------- conceitos: bloco custo x despesa / provisão ---------- */
.concept-block{ margin-top:26px; }
.concept-block:first-child{ margin-top:0; }

/* ---------- escolher conta: perguntas numeradas ---------- */
.q-cards{ display:grid; grid-template-columns:repeat(3,1fr); gap:16px; margin-top:16px; }
@media (max-width:900px){ .q-cards{ grid-template-columns:1fr; } }
.q-card{ background:#fff; border:1px solid var(--cinza-claro); border-radius:8px; padding:18px; }
.q-num{ width:28px; height:28px; border-radius:50%; background:var(--amarelo); color:var(--azul-escuro); font-weight:800; display:flex; align-items:center; justify-content:center; margin-bottom:10px; font-size:0.85rem; }
.q-card h4{ font-size:0.9rem; margin-bottom:6px; }
.q-card p{ font-size:0.83rem; margin:0; }

/* ---------- nova conta: fluxograma de decisão ---------- */
.flow{ display:flex; flex-direction:column; align-items:center; gap:0; margin-top:18px; }
.flow-box{ background:#fff; border:1.5px solid var(--azul-sattva); border-radius:8px; padding:12px 20px; font-size:0.85rem; font-weight:700; color:var(--azul-sattva); text-align:center; max-width:320px; }
.flow-arrow{ color:var(--cinza-medio); font-size:1.1rem; line-height:1; padding:4px 0; }
.flow-branches{ display:flex; gap:24px; margin-top:0; flex-wrap:wrap; justify-content:center; }
.flow-branch{ display:flex; flex-direction:column; align-items:center; }
.flow-branch .flow-tag{ font-size:0.72rem; font-weight:800; text-transform:uppercase; letter-spacing:.04em; color:var(--grafite); margin-bottom:6px; }
.flow-result{ border-radius:8px; padding:10px 18px; font-size:0.83rem; font-weight:700; text-align:center; }
.flow-result.sim{ background:var(--verde-ok-bg); color:var(--verde-ok); border:1.5px solid var(--verde-ok); }
.flow-result.nao{ background:var(--vermelho-bg); color:var(--vermelho); border:1.5px solid var(--vermelho); }

/* ---------- conciliação: fluxo "se encontrar diferença" ---------- */
.diff-flow{ display:flex; flex-wrap:wrap; gap:10px; margin-top:14px; }
.diff-flow-step{ background:#fff; border:1px solid var(--cinza-claro); border-radius:20px; padding:9px 16px; font-size:0.83rem; font-weight:600; color:var(--azul-sattva); }
.diff-flow-arrow{ align-self:center; color:var(--cinza-medio); }

/* ---------- boas práticas / lançamentos: cards de recomendação ---------- */
.rec-cards{ display:grid; grid-template-columns:repeat(4,1fr); gap:14px; margin-top:14px; }
@media (max-width:900px){ .rec-cards{ grid-template-columns:1fr 1fr; } }
@media (max-width:560px){ .rec-cards{ grid-template-columns:1fr; } }
.rec-card{ background:#fff; border:1px solid var(--cinza-claro); border-radius:8px; padding:14px; font-size:0.83rem; font-weight:600; color:var(--azul-sattva); display:flex; align-items:center; gap:10px; }
.rec-card .dotc{ width:8px; height:8px; border-radius:50%; background:var(--verde-ok); flex:none; }
</style>
</head>
<body>

<div id="toast">Copiado!</div>

<header class="top-header">
  <div class="top-header-inner">
    <div class="brand-block">
      <img src="assets/sattva-logo.webp" alt="Sattva Controladoria" class="brand-logo-img" id="headerLogoImg" onerror="window.handleLogoError && window.handleLogoError(this)">
      <span class="logo-fallback" id="headerLogoFallback">Sattva</span>
      <div class="wordmark"><small>Controladoria</small></div>
      <div class="gf-divider"></div>
      <div class="gf-title">Guia Financeiro</div>
    </div>
    <div class="top-actions">
      <button class="menu-toggle" id="menuToggle" aria-label="Abrir índice">☰</button>
    </div>
  </div>
</header>

<div class="layout">
  <aside class="sidebar" id="sidebar">
    <div class="search-box mini">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="7"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
      <input type="text" id="sideSearch" placeholder="Buscar no guia...">
      <button id="sideSearchBtn">Ir</button>
    </div>
    <nav>
      <a href="#inicio" class="nav-link"><span class="n">•</span> Início</a>
      <a href="#conceitos" class="nav-link"><span class="n">1</span> Conceitos Financeiros</a>
      <a href="#lancamentos" class="nav-link"><span class="n">2</span> Lançamentos</a>
      <a href="#escolher-conta" class="nav-link"><span class="n">3</span> Escolher a Conta Certa</a>
      <a href="#nova-conta" class="nav-link"><span class="n">4</span> Criar Nova Conta</a>
      <a href="#conciliacao" class="nav-link"><span class="n">5</span> Conciliação Bancária</a>
      <a href="#plano-contas" class="nav-link"><span class="n">6</span> Plano de Contas</a>
      <a href="#faq" class="nav-link"><span class="n">7</span> Perguntas Frequentes</a>
    </nav>
  </aside>

  <div class="content">

    <!-- INÍCIO -->
    <section class="section" id="inicio">
      <p class="hero-eyebrow">A organização do seu financeiro começa na consistência dos lançamentos</p>
      <h1>Um guia prático para apoiar a rotina financeira da sua empresa.</h1>
      <p class="hero-sub">Desenvolvido pela equipe de Controladoria da Sattva, este guia reúne orientações simples para ajudar no registro correto das movimentações financeiras, na utilização do plano de contas, na realização de conciliações bancárias e na adoção de boas práticas que garantem informações mais confiáveis para a gestão.</p>

      <form class="search-box" id="heroSearchForm">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="7"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
        <input type="text" id="heroSearch" placeholder="Ex.: como lançar o pagamento da fatura do cartão?">
        <button type="submit">Buscar</button>
      </form>

      <div class="card" style="margin-top:28px;">
        <h3 style="font-size:1rem;">Como utilizar este guia</h3>
        <p>Sempre que surgir uma dúvida durante um lançamento, consulte este guia antes de criar uma nova conta ou registrar uma movimentação. Aqui você encontrará orientações sobre:</p>
        <ul style="padding-left:18px; color:var(--grafite); columns:2; column-gap:24px; margin:0;">
          <li style="margin-bottom:8px;">Conceitos financeiros básicos</li>
          <li style="margin-bottom:8px;">Como realizar lançamentos corretamente</li>
          <li style="margin-bottom:8px;">Como utilizar o plano de contas</li>
          <li style="margin-bottom:8px;">Como fazer a conciliação bancária</li>
          <li style="margin-bottom:8px;">Boas práticas para a rotina financeira</li>
          <li style="margin-bottom:8px;">Perguntas frequentes</li>
          <li>Exemplos práticos</li>
        </ul>
        <div class="dica" style="margin-top:16px;"><p class="mt-0">Este guia deve ser utilizado como um material de consulta para o dia a dia da sua empresa.</p></div>
      </div>

      <div class="pillars">
        <a class="pillar-card" href="#conceitos">
          <span class="pillar-tag">01 · Fundamento</span>
          <h3>Conceitos Financeiros</h3>
          <p>Custo x despesa, regime de caixa x competência e provisão o básico explicado sem economês.</p>
          <span class="go">Entender os conceitos →</span>
        </a>
        <a class="pillar-card" href="#lancamentos">
          <span class="pillar-tag">02 · Prática</span>
          <h3>Lançamentos</h3>
          <p>Como lançar pagamentos, recebimentos, Pix e cartão de crédito, com a descrição certa.</p>
          <span class="go">Ver como lançar →</span>
        </a>
        <a class="pillar-card" href="#escolher-conta">
          <span class="pillar-tag">03 · Prática</span>
          <h3>Escolher a Conta Certa</h3>
          <p>As perguntas certas para nunca ficar em dúvida sobre onde lançar algo.</p>
          <span class="go">Ver o passo a passo →</span>
        </a>
        <a class="pillar-card" href="#nova-conta">
          <span class="pillar-tag">04 · Prática</span>
          <h3>Criar Nova Conta</h3>
          <p>Quando vale a pena criar uma conta nova e quando isso pode virar bagunça.</p>
          <span class="go">Ver quando criar →</span>
        </a>
        <a class="pillar-card" href="#conciliacao">
          <span class="pillar-tag">05 · Conferência</span>
          <h3>Conciliação Bancária</h3>
          <p>Como bater o que está no seu controle com o que realmente aconteceu no banco.</p>
          <span class="go">Aprender a conciliar →</span>
        </a>
        <a class="pillar-card" href="#plano-contas">
          <span class="pillar-tag">06 · Consulta</span>
          <h3>Plano de Contas</h3>
          <p>Catálogo comentado por segmento, com Excel pronto para baixar.</p>
          <span class="go">Consultar o plano de contas →</span>
        </a>
      </div>
    </section>

    <!-- 1. CONCEITOS FINANCEIROS -->
    <section class="section" id="conceitos">
      <p class="section-eyebrow"><span class="dot"></span>01 · Fundamento</p>
      <h2 class="sec-icon-h3"><span class="sec-icon"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M4 19h16M6 15V9M12 15V6M18 15v-4"/></svg></span> Conceitos Financeiros</h2>
      <p>O básico que muda a forma como você entende os números da sua empresa.</p>

      <div class="concept-block">
        <h3 style="font-size:1.05rem;">Custo × Despesa</h3>
        <div class="card">
          <p><strong>Custo</strong> é todo gasto ligado diretamente ao que a empresa vende ou produz. <strong>Despesa</strong> é o gasto necessário para a empresa funcionar, mas que não entra direto no produto ou serviço vendido.</p>
          <div class="exemplo"><span class="rotulo">Exemplo</span><p>Uma marcenaria compra madeira para fabricar uma mesa → <strong>Custo</strong>. A mesma marcenaria paga o salário do vendedor da loja → <strong>Despesa</strong>.</p></div>
        </div>
      </div>

      <div class="concept-block">
        <h3 style="font-size:1.05rem;">Entrada × Saída</h3>
        <div class="card">
          <p><strong>Entrada</strong> é toda movimentação que aumenta o saldo da conta bancária. <strong>Saída</strong> é toda movimentação que reduz o saldo da conta bancária.</p>
          <div class="dica"><span class="rotulo">Importante</span><p>Nem toda entrada representa uma receita, e nem toda saída representa uma despesa.</p></div>
          <p style="margin-top:14px;">Movimentações como estas alteram o saldo da conta, mas não são receita nem despesa:</p>
          <div class="conf-grid" style="grid-template-columns:repeat(2,1fr);">
            <div class="conf-item"><span class="dotc"></span>Empréstimos</div>
            <div class="conf-item"><span class="dotc"></span>Transferências entre contas</div>
            <div class="conf-item"><span class="dotc"></span>Aplicações financeiras</div>
            <div class="conf-item"><span class="dotc"></span>Resgates de aplicações</div>
          </div>
          <p style="margin-top:14px; font-size:0.85rem;">Veja como classificar cada uma dessas situações em <a href="#lancamentos">Orientações Práticas de Lançamento</a>.</p>
        </div>
      </div>

      <div class="concept-block">
        <h3 style="font-size:1.05rem;">Crédito × Débito</h3>
        <div class="card">
          <p>Nos extratos bancários, <strong>crédito</strong> significa entrada de dinheiro na conta, e <strong>débito</strong> significa saída de dinheiro da conta.</p>
          <div class="errado"><span class="rotulo">Atenção</span><p>No extrato bancário, crédito e débito representam entradas e saídas de dinheiro. Esses conceitos são diferentes da terminologia usada na contabilidade.</p></div>
        </div>
      </div>

      <div class="concept-block">
        <h3 style="font-size:1.05rem;">Regime de Caixa × Regime de Competência</h3>
        <div class="card">
          <p>Essa é a distinção mais importante deste guia. Os dois regimes respondem à mesma pergunta ("quando eu registro isso?"), mas em momentos diferentes.</p>
          <div class="grid-2" style="margin-top:16px;">
            <div class="exemplo"><span class="rotulo">Regime de Caixa</span><p>Registra o fato <strong>quando o dinheiro entra ou sai de verdade</strong> do caixa, banco ou cartão.</p></div>
            <div class="exemplo"><span class="rotulo">Regime de Competência</span><p>Registra o fato <strong>quando ele acontece de verdade</strong> na operação da empresa, independente do dinheiro.</p></div>
          </div>

          <h4 style="margin-top:22px; font-size:0.95rem;">Um exemplo do dia a dia</h4>
          <p>Sua empresa vendeu um serviço no dia 5 de junho, mas combinou de receber só no dia 5 de julho, via boleto.</p>
          <table class="compare-table">
            <thead><tr><th>Regime</th><th>Quando a venda aparece</th><th>O que ele responde</th></tr></thead>
            <tbody>
              <tr><td><strong>Competência</strong></td><td>Em <strong>junho</strong> — mês em que o serviço foi entregue.</td><td>"A empresa está vendendo e performando bem?"</td></tr>
              <tr><td><strong>Caixa</strong></td><td>Em <strong>julho</strong> — mês em que o dinheiro cai na conta.</td><td>"Vai ter dinheiro em caixa para pagar as contas?"</td></tr>
            </tbody>
          </table>

          <div class="dica">
            <span class="rotulo">Por que usamos os dois</span>
            <p>A <strong>DRE</strong> normalmente olha por <strong>competência</strong>. O <strong>Fluxo de Caixa</strong> olha por <strong>caixa</strong>. Por isso é comum uma empresa estar "lucrativa no papel" e, ainda assim, apertada de dinheiro no mês.</p>
          </div>

          <h4 style="margin-top:22px; font-size:0.95rem;">Outro exemplo, com uma despesa</h4>
          <p>Você contratou um seguro anual em janeiro, pagando os R$ 1.200,00 de uma vez.</p>
          <ul style="padding-left:18px; color:var(--grafite);">
            <li style="margin-bottom:6px;"><strong>Caixa:</strong> os R$ 1.200,00 saem do banco inteiros em janeiro.</li>
            <li><strong>Competência:</strong> o custo é espalhado, R$ 100,00 por mês, de janeiro a dezembro.</li>
          </ul>
        </div>
      </div>

      <div class="concept-block">
        <h3 style="font-size:1.05rem;">Provisão</h3>
        <div class="card">
          <p><strong>Provisão</strong> é reservar, hoje, um valor para um gasto que você sabe que vai acontecer no futuro, mesmo sem ainda saber o valor exato.</p>
          <div class="exemplo"><span class="rotulo">Exemplo</span><p>Sua empresa sabe que vai pagar 13º salário em dezembro. Em vez de sentir o baque de um gasto grande de uma vez só, você guarda uma parte todo mês ao longo do ano — isso é provisionar.</p></div>
          <div class="dica"><span class="rotulo">Por que isso ajuda</span><p>Provisionar evita surpresas de caixa em meses de gasto mais pesado, como 13º salário, férias ou IPTU anual.</p></div>
        </div>
      </div>
    </section>

    <!-- 2. LANÇAMENTOS -->
    <section class="section" id="lancamentos">
      <p class="section-eyebrow"><span class="dot"></span>02 · Prática</p>
      <h2 class="sec-icon-h3"><span class="sec-icon"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M12 19V5M5 12l7-7 7 7"/></svg></span> Lançamentos</h2>
      <p>Tudo o que você precisa para registrar uma movimentação corretamente, do porquê até o exemplo prático.</p>

      <h3 style="margin-top:8px; font-size:1.05rem;">Por que lançar certo importa</h3>
      <div class="card">
        <p>Pense no financeiro da empresa como um <strong>diário</strong>. Cada pagamento, recebimento, boleto ou Pix é um "fato" que aconteceu no dia a dia do negócio. O papel deste guia é garantir que, quando você registra esse fato, você registra do <strong>mesmo jeito</strong> toda vez — na conta certa, com a descrição certa, na data certa.</p>
        <p>Isso importa porque três relatórios da sua empresa são construídos automaticamente a partir desses lançamentos:</p>
        <div class="grid-3" style="margin-top:16px;">
          <div class="card" style="box-shadow:none; border-style:dashed;">
            <span class="stamp azul">Relatório</span>
            <h4 style="margin-top:10px; font-size:1rem;">DRE</h4>
            <p style="font-size:0.85rem;">Demonstração do Resultado. Mostra se a empresa deu lucro ou prejuízo, receitas menos custos e despesas.</p>
          </div>
          <div class="card" style="box-shadow:none; border-style:dashed;">
            <span class="stamp azul">Relatório</span>
            <h4 style="margin-top:10px; font-size:1rem;">Fluxo de Caixa (DFC)</h4>
            <p style="font-size:0.85rem;">Mostra o dinheiro que de fato entrou e saiu do caixa/banco no período.</p>
          </div>
          <div class="card" style="box-shadow:none; border-style:dashed;">
            <span class="stamp azul">Relatório</span>
            <h4 style="margin-top:10px; font-size:1rem;">Indicadores</h4>
            <p style="font-size:0.85rem;">Margem, ponto de equilíbrio, custo fixo x variável — calculados a partir dos lançamentos.</p>
          </div>
        </div>
        <div class="grid-4" style="margin-top:16px;">
          <div class="card"><span class="stamp verde">Ganho</span><h4 style="margin-top:10px; font-size:0.95rem;">Facilita a gestão</h4><p style="font-size:0.84rem;">Entender o mês em minutos, sem abrir extrato por extrato.</p></div>
          <div class="card"><span class="stamp verde">Ganho</span><h4 style="margin-top:10px; font-size:0.95rem;">Evita retrabalho</h4><p style="font-size:0.84rem;">Lançamento certo da primeira vez é lançamento que ninguém precisa arrumar depois.</p></div>
          <div class="card"><span class="stamp verde">Ganho</span><h4 style="margin-top:10px; font-size:0.95rem;">Melhora indicadores</h4><p style="font-size:0.84rem;">Margem e ponto de equilíbrio só fazem sentido com contas certas.</p></div>
          <div class="card"><span class="stamp verde">Ganho</span><h4 style="margin-top:10px; font-size:0.95rem;">Reduz dúvidas</h4><p style="font-size:0.84rem;">Descrição clara elimina perguntas três meses depois.</p></div>
        </div>
        <div class="dica" style="margin-top:16px;"><span class="rotulo">Como confirmar que está funcionando</span><p>A <a href="#conciliacao">Conciliação Bancária</a> é o jeito de garantir, na prática, que esses relatórios estão batendo com a realidade do banco.</p></div>
      </div>

      <h3 style="margin-top:26px; font-size:1.05rem;">Como lançar pagamentos e recebimentos</h3>
      <div class="grid-2">
        <div class="card">
          <span class="stamp vermelho">Saída</span>
          <h4 style="margin-top:10px; font-size:1rem;">Lançando um pagamento</h4>
          <p>Todo pagamento deve ter: <strong>data</strong>, <strong>valor</strong>, <strong>conta</strong> do plano de contas e uma <strong>descrição</strong> clara.</p>
          <div class="exemplo"><span class="rotulo">Exemplo</span><p>Pix de R$ 480,00 para a gráfica → conta <strong>"Marketing e Publicidade"</strong>, descrição <strong>"Pix — Gráfica Rápida — panfletos julho"</strong>.</p></div>
        </div>
        <div class="card">
          <span class="stamp verde">Entrada</span>
          <h4 style="margin-top:10px; font-size:1rem;">Lançando um recebimento</h4>
          <p>Todo recebimento deve ter: <strong>data</strong>, <strong>valor</strong>, <strong>conta</strong> de receita e uma <strong>descrição</strong> com cliente/origem.</p>
          <div class="exemplo"><span class="rotulo">Exemplo</span><p>Cartão de R$ 2.300,00 → conta <strong>"Receita de Vendas"</strong>, descrição <strong>"Cartão — Cliente Maria Souza — pedido 1042"</strong>.</p></div>
        </div>
      </div>
      <div class="dica" style="margin-top:16px;"><span class="rotulo">Regra de ouro</span><p>Lance no dia em que o fato acontece, ou no máximo no dia seguinte. Lançamento acumulado é a principal causa de erro. Para saber em qual conta classificar cada tipo de pagamento ou recebimento, veja "Pagamentos e Recebimentos" em Orientações Práticas de Lançamento, mais abaixo.</p></div>

      <h3 style="margin-top:26px; font-size:1.05rem;">Regras para a descrição dos lançamentos</h3>
      <div class="card">
        <p>Uma boa descrição responde: <strong>o que foi</strong>, <strong>para quem/de quem</strong>, e <strong>qual a referência</strong>. Use sempre a mesma ordem.</p>
        <div class="grid-2" style="margin-top:14px;">
          <div class="errado"><span class="rotulo">Evite</span><p>"pagamento" · "pix diverso" · "boleto" · "transferência 25/06"</p></div>
          <div class="exemplo"><span class="rotulo">Prefira</span><p>"Boleto — Fornecedor ABC Materiais — NF 3321 — compra de insumos"</p></div>
        </div>
        <p style="margin-top:14px; font-size:0.9rem;">Modelo mental: <code style="background:var(--fundo); padding:2px 8px; border-radius:4px; font-size:0.85rem;">[forma de pagamento] — [quem recebeu/pagou] — [referência/motivo]</code></p>
        <div class="dica" style="margin-top:14px;"><span class="rotulo">Por que isso importa ainda mais na conciliação</span><p>Se toda entrada aparecer só como "Pix", fica impossível saber o que já foi conferido. Veja como isso afeta a <a href="#conciliacao">Conciliação Bancária</a>.</p></div>
      </div>

      <h3 style="margin-top:26px; font-size:1.05rem;">Orientações Práticas de Lançamento</h3>
      <p>Abaixo estão algumas das movimentações que mais geram dúvidas durante os lançamentos financeiros. Utilize estas orientações sempre que precisar registrar uma movimentação no ERP ou na planilha.</p>

      <details class="accordion-item">
        <summary>Pagamentos e Recebimentos</summary>
        <div class="accordion-body">
          <p>Os pagamentos e recebimentos devem ser registrados conforme a natureza da movimentação, e não apenas pela entrada ou saída de dinheiro.</p>
          <p style="margin-top:12px;"><strong>Pagamentos</strong> — sempre registre utilizando a categoria correspondente ao gasto:</p>
          <div class="conf-grid" style="grid-template-columns:1fr;">
            <div class="conf-item" style="justify-content:space-between;"><span>Conta de energia</span><strong>→ Energia Elétrica</strong></div>
            <div class="conf-item" style="justify-content:space-between;"><span>Compra de mercadorias</span><strong>→ Insumos ou Produtos para Revenda</strong></div>
            <div class="conf-item" style="justify-content:space-between;"><span>Honorários do contador</span><strong>→ Honorários Contábeis</strong></div>
            <div class="conf-item" style="justify-content:space-between;"><span>Aluguel</span><strong>→ Aluguel</strong></div>
          </div>
          <p style="margin-top:16px;"><strong>Recebimentos</strong> — sempre registre conforme a origem:</p>
          <div class="conf-grid" style="grid-template-columns:1fr;">
            <div class="conf-item" style="justify-content:space-between;"><span>Venda de produtos</span><strong>→ Receita de Vendas</strong></div>
            <div class="conf-item" style="justify-content:space-between;"><span>Prestação de serviços</span><strong>→ Receita de Serviços</strong></div>
            <div class="conf-item" style="justify-content:space-between;"><span>Recebimento de cliente</span><strong>→ Recebimento de Venda</strong></div>
            <div class="conf-item" style="justify-content:space-between;"><span>Rendimento de aplicação</span><strong>→ Receitas Financeiras</strong></div>
          </div>
          <div class="dica" style="margin-top:14px;"><p class="mt-0">A forma de pagamento (Pix, boleto, cartão, dinheiro ou transferência) não altera a classificação da movimentação. O que define a conta correta é a natureza da operação.</p></div>
        </div>
      </details>

      <details class="accordion-item">
        <summary>Pix</summary>
        <div class="accordion-body">
          <p>Pix é apenas a forma de pagamento ou recebimento. A classificação deve considerar a natureza da movimentação.</p>
          <div class="conf-grid" style="grid-template-columns:1fr;">
            <div class="conf-item" style="justify-content:space-between;"><span>Venda</span><strong>→ Receita</strong></div>
            <div class="conf-item" style="justify-content:space-between;"><span>Pagamento de energia</span><strong>→ Energia Elétrica</strong></div>
            <div class="conf-item" style="justify-content:space-between;"><span>Transferência entre contas</span><strong>→ Transferência entre Contas</strong></div>
          </div>
          <div class="dica" style="margin-top:14px;"><p class="mt-0">O Pix nunca deve ser utilizado como categoria do plano de contas.</p></div>
        </div>
      </details>

      <details class="accordion-item">
        <summary>Cartão de Crédito</summary>
        <div class="accordion-body">
          <p>As compras devem ser registradas individualmente conforme sua natureza. O pagamento da fatura apenas quita essas despesas.</p>
          <div class="dica"><p class="mt-0">O pagamento da fatura não representa uma nova despesa.</p></div>
        </div>
      </details>

      <details class="accordion-item">
        <summary>Transferência entre Contas</summary>
        <div class="accordion-body">
          <p>Quando o dinheiro é movimentado entre contas bancárias da própria empresa, não existe receita nem despesa.</p>
          <p><strong>Registrar:</strong> saída na conta de origem e entrada na conta de destino. <strong>Categoria:</strong> Transferência entre Contas.</p>
          <div class="dica"><p class="mt-0">Toda saída deve possuir uma entrada correspondente.</p></div>
          <div class="dica" style="margin-top:10px;"><p class="mt-0">Ao analisar todos os lançamentos classificados como Transferência entre Contas, o saldo deve ser igual a zero.</p></div>
        </div>
      </details>

      <details class="accordion-item">
        <summary>Aplicação Financeira</summary>
        <div class="accordion-body">
          <p>Uma aplicação financeira acontece quando o dinheiro sai da conta corrente e é transferido para uma aplicação do próprio banco (como CDB, fundo de investimento ou aplicação automática). O dinheiro continua sendo da empresa, apenas mudou de lugar.</p>
          <p><strong>Registrar:</strong> Saída. <strong>Categoria:</strong> Aplicações Financeiras.</p>
          <div class="dica"><p class="mt-0">Aplicação financeira não é despesa.</p></div>
        </div>
      </details>

      <details class="accordion-item">
        <summary>Resgate de Aplicação</summary>
        <div class="accordion-body">
          <p>O resgate acontece quando o dinheiro retorna da aplicação para a conta corrente.</p>
          <p><strong>Registrar:</strong> Entrada. <strong>Categoria:</strong> Resgate de Aplicações. Se houver rendimento, o rendimento entra em <strong>Receitas Financeiras → Rendimento de Aplicação</strong>.</p>
          <div class="dica"><p class="mt-0">O resgate não é uma receita. Apenas o rendimento é considerado receita financeira.</p></div>
        </div>
      </details>

      <details class="accordion-item">
        <summary>Empréstimo Bancário</summary>
        <div class="accordion-body">
          <p>Quando a empresa recebe um empréstimo do banco, o dinheiro entra na conta, mas não representa receita.</p>
          <p><strong>Registrar:</strong> Entrada. <strong>Categoria:</strong> Empréstimos e Financiamentos.</p>
          <div class="dica"><p class="mt-0">Os juros e IOF devem ser classificados em Despesas Financeiras.</p></div>
        </div>
      </details>

      <details class="accordion-item">
        <summary>Empréstimo entre Empresas</summary>
        <div class="accordion-body">
          <p>Quando uma empresa empresta dinheiro para outra empresa do grupo:</p>
          <p><strong>Empresa que empresta:</strong> Saída. <strong>Empresa que recebe:</strong> Entrada. <strong>Categoria:</strong> Empréstimos entre Empresas.</p>
          <div class="dica"><p class="mt-0">Essa movimentação não é receita nem despesa.</p></div>
        </div>
      </details>

      <details class="accordion-item">
        <summary>Estorno</summary>
        <div class="accordion-body">
          <p>O estorno deve ser registrado utilizando a mesma categoria do lançamento original. O objetivo é anular a movimentação anterior.</p>
          <div class="dica"><p class="mt-0">Não crie uma categoria chamada "Estorno". Utilize sempre a mesma conta do lançamento original.</p></div>
          <p style="margin-top:12px;">Mesmo que a movimentação tenha sido estornada, ela deve ser registrada para que o controle financeiro represente corretamente o extrato bancário.</p>
        </div>
      </details>

      <div class="dica" style="margin-top:16px;"><span class="rotulo">Próximo passo</span><p>Depois de lançar certo, o próximo passo é conferir se está tudo certo — veja como em <a href="#conciliacao">Conciliação Bancária</a>.</p></div>

      <h3 style="margin-top:26px; font-size:1.05rem;">Rotina recomendada</h3>
      <div class="card">
        <p>Além de lançar certo, lançar <strong>no tempo certo</strong> evita bagunça:</p>
        <div class="rec-cards">
          <div class="rec-card"><span class="dotc"></span>Lançar pagamentos pendentes toda semana</div>
          <div class="rec-card"><span class="dotc"></span>Lançar recebimentos da semana</div>
          <div class="rec-card"><span class="dotc"></span>Revisar lançamentos genéricos antes do fechamento</div>
          <div class="rec-card"><span class="dotc"></span>Enviar dúvidas à controladoria — não "chutar" a conta</div>
        </div>
      </div>
    </section>


    <!-- 3. ESCOLHER A CONTA CERTA -->
    <section class="section" id="escolher-conta">
      <p class="section-eyebrow"><span class="dot"></span>03 · Prática</p>
      <h2 class="sec-icon-h3"><span class="sec-icon"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><circle cx="12" cy="12" r="9"/><path d="M9.5 9a2.5 2.5 0 0 1 5 0c0 1.7-2.5 2-2.5 4"/><circle cx="12" cy="17" r="0.6" fill="#fff"/></svg></span> Como escolher a conta correta</h2>
      <p>Antes de lançar, faça a si mesmo estas perguntas, nesta ordem:</p>

      <div class="q-cards">
        <div class="q-card"><div class="q-num">1</div><h4>O dinheiro está entrando ou saindo?</h4><p>Separa "Receitas" de "Custos/Despesas".</p></div>
        <div class="q-card"><div class="q-num">2</div><h4>É ligado direto ao que eu vendo, ou é pra manter a empresa funcionando?</h4><p>O primeiro é <strong>Custo</strong>; o segundo, <strong>Despesa</strong>.</p></div>
        <div class="q-card"><div class="q-num">3</div><h4>Já existe uma conta que descreve exatamente isso?</h4><p>Consulte o <a href="#plano-contas">Plano de Contas</a> antes de decidir.</p></div>
      </div>

      <div class="grid-2" style="margin-top:16px;">
        <div class="exemplo"><span class="rotulo">Exemplo (comércio)</span><p>Padaria compra farinha → <strong>Custo (Matéria-Prima)</strong>. A mesma padaria paga a conta de luz → <strong>Despesa (Água, Luz e Internet)</strong>.</p></div>
        <div class="exemplo"><span class="rotulo">Exemplo (serviços)</span><p>Agência contrata um freelancer para entregar parte do projeto de um cliente → <strong>Custo</strong>. A mesma agência paga a mensalidade do sistema de gestão → <strong>Despesa</strong>.</p></div>
      </div>
    </section>

    <!-- 4. CRIAR NOVA CONTA -->
    <section class="section" id="nova-conta">
      <p class="section-eyebrow"><span class="dot"></span>04 · Prática</p>
      <h2 class="sec-icon-h3"><span class="sec-icon"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></span> Quando criar uma conta nova</h2>
      <div class="grid-2">
        <div class="card"><span class="stamp verde">Pode criar</span>
          <ul style="padding-left:18px; color:var(--grafite); margin:12px 0 0;">
            <li style="margin-bottom:8px;">O gasto/receita é <strong>recorrente</strong> e não existe conta parecida.</li>
            <li style="margin-bottom:8px;">O valor é <strong>relevante</strong> o suficiente para acompanhar separado.</li>
            <li>Você conferiu que não há conta que sirva.</li>
          </ul>
        </div>
        <div class="card"><span class="stamp vermelho">Evite criar</span>
          <ul style="padding-left:18px; color:var(--grafite); margin:12px 0 0;">
            <li style="margin-bottom:8px;">Criar por não ter procurado no plano de contas.</li>
            <li style="margin-bottom:8px;">Criar uma conta genérica tipo "Outras Despesas".</li>
            <li>Criar conta para um gasto único que já cabe numa conta existente.</li>
          </ul>
        </div>
      </div>

      <h3 style="margin-top:26px; font-size:1.05rem;">Fluxograma de decisão</h3>
      <div class="card">
        <div class="flow">
          <div class="flow-box">1. O gasto ou receita é recorrente?</div>
          <div class="flow-arrow">↓</div>
          <div class="flow-box">2. É relevante o suficiente para acompanhar separado?</div>
          <div class="flow-arrow">↓</div>
          <div class="flow-box">3. Já conferiu que não existe conta parecida?</div>
          <div class="flow-arrow">↓</div>
          <div class="flow-branches">
            <div class="flow-branch"><span class="flow-tag">Alguma resposta foi não</span><div class="flow-result nao">Não crie — use uma conta existente</div></div>
            <div class="flow-branch"><span class="flow-tag">As 3 respostas foram sim</span><div class="flow-result sim">Pode criar a conta nova</div></div>
          </div>
        </div>
      </div>
    </section>

    <!-- 5. CONCILIAÇÃO BANCÁRIA -->
    <section class="section" id="conciliacao">
      <p class="section-eyebrow"><span class="dot"></span>05 · Conferência</p>
      <h2 class="sec-icon-h3"><span class="sec-icon"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M9 11l3 3L22 4"/><path d="M21 12v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V7a2 2 0 0 1 2-2h11"/></svg></span> Conciliação Bancária</h2>
      <p>O passo a passo para conferir se tudo que está no seu ERP ou planilha realmente aconteceu no banco — sem economês, com exemplo prático em cada parte.</p>

      <h3 style="font-size:1.05rem;">O que é Conciliação Bancária?</h3>
      <div class="card">
        <p>É o processo de comparar todas as movimentações registradas no seu controle financeiro (ERP ou planilha) com aquelas que realmente aconteceram na conta bancária. O objetivo é garantir que todos os recebimentos, pagamentos, transferências e demais movimentações estejam registrados corretamente, sem esquecimentos, duplicidades ou classificações incorretas.</p>
        <div class="dica">
          <span class="rotulo">⚠️ Destaque</span>
          <p>Ao final da conciliação, o saldo do seu controle financeiro deve ser <strong>exatamente igual</strong> ao saldo do extrato bancário.</p>
        </div>
      </div>

      <h3 style="margin-top:26px; font-size:1.05rem;">Por que a Conciliação Bancária é importante?</h3>
      <div class="grid-3">
        <div class="card"><span class="stamp verde">Benefício</span><h4 style="margin-top:10px; font-size:0.92rem;">Evita esquecimentos</h4><p style="font-size:0.84rem;">Identifica lançamentos que nunca chegaram a ser registrados.</p></div>
        <div class="card"><span class="stamp verde">Benefício</span><h4 style="margin-top:10px; font-size:0.92rem;">Evita duplicados</h4><p style="font-size:0.84rem;">Pagamentos ou recebimentos lançados mais de uma vez.</p></div>
        <div class="card"><span class="stamp verde">Benefício</span><h4 style="margin-top:10px; font-size:0.92rem;">Relatórios confiáveis</h4><p style="font-size:0.84rem;">DRE, Fluxo de Caixa e indicadores refletindo a realidade.</p></div>
        <div class="card"><span class="stamp verde">Benefício</span><h4 style="margin-top:10px; font-size:0.92rem;">Facilita o fechamento</h4><p style="font-size:0.84rem;">O mês fecha sem correria de última hora.</p></div>
        <div class="card"><span class="stamp verde">Benefício</span><h4 style="margin-top:10px; font-size:0.92rem;">Reduz retrabalho</h4><p style="font-size:0.84rem;">Menos idas e vindas entre empresa e controladoria.</p></div>
        <div class="card"><span class="stamp verde">Benefício</span><h4 style="margin-top:10px; font-size:0.92rem;">Ajuda a decidir</h4><p style="font-size:0.84rem;">Decisões tomadas em cima de números reais.</p></div>
      </div>

      <h3 style="margin-top:26px; font-size:1.05rem;">Como fazer a Conciliação Bancária?</h3>
      <div class="card">
        <ol style="padding-left:20px; color:var(--grafite); margin:0;">
          <li style="margin-bottom:10px;">Acesse o extrato bancário.</li>
          <li style="margin-bottom:10px;">Compare com o ERP ou planilha.</li>
          <li style="margin-bottom:10px;">Confira: valor, data, descrição e plano de contas.</li>
          <li style="margin-bottom:10px;">Corrija as diferenças encontradas.</li>
          <li>Confira o saldo final.</li>
        </ol>
        <div class="dica" style="margin-top:14px;"><p class="mt-0" style="text-align:center; font-weight:800; font-size:0.95rem;">Saldo Banco = Saldo ERP</p></div>
      </div>

      <h3 style="margin-top:26px; font-size:1.05rem;">Quando considerar uma movimentação conciliada?</h3>
      <div class="card">
        <p style="margin-bottom:4px;">Clique em cada item conforme for conferindo o progresso fica salvo neste navegador.</p>
        <div class="progress-bar-wrap"><div class="progress-bar-fill" id="conciliaProgressFill"></div></div>
        <p class="progress-label" id="conciliaProgressLabel">0 de 6 conferidos</p>
        <ul class="checklist final-checklist" id="conciliaChecklist">
          <li data-item="extrato"><span class="box"></span><div><strong>Está no extrato</strong></div></li>
          <li data-item="erp"><span class="box"></span><div><strong>Está no ERP ou planilha</strong></div></li>
          <li data-item="valor"><span class="box"></span><div><strong>O valor está correto</strong></div></li>
          <li data-item="data"><span class="box"></span><div><strong>A data está correta</strong></div></li>
          <li data-item="classificacao"><span class="box"></span><div><strong>A classificação está correta</strong></div></li>
          <li data-item="saldo"><span class="box"></span><div><strong>O saldo confere</strong></div></li>
        </ul>
        <button class="reset-checklist" id="resetConciliaChecklist">Reiniciar checklist</button>
        <div class="errado" style="margin-top:16px;"><span class="rotulo">Atenção</span><p>Conciliação não significa apenas "saldo igual" — os 6 pontos acima precisam estar certos ao mesmo tempo.</p></div>
      </div>

      <h3 style="margin-top:26px; font-size:1.05rem;">Se encontrar uma diferença</h3>
      <div class="card">
        <p>Verifique, nesta ordem:</p>
        <div class="diff-flow">
          <div class="diff-flow-step">Lançamento não registrado</div>
          <div class="diff-flow-arrow">→</div>
          <div class="diff-flow-step">Duplicado</div>
          <div class="diff-flow-arrow">→</div>
          <div class="diff-flow-step">Valor</div>
          <div class="diff-flow-arrow">→</div>
          <div class="diff-flow-step">Classificação</div>
          <div class="diff-flow-arrow">→</div>
          <div class="diff-flow-step">Saldo</div>
        </div>

        <h4 style="margin-top:22px; font-size:0.95rem;">Diferenças mais comuns</h4>
        <div class="conf-grid">
          <div class="conf-item"><span class="dotc"></span>Movimentação não lançada</div>
          <div class="conf-item"><span class="dotc"></span>Duplicidade</div>
          <div class="conf-item"><span class="dotc"></span>Valor incorreto</div>
          <div class="conf-item"><span class="dotc"></span>Data incorreta</div>
          <div class="conf-item"><span class="dotc"></span>Conta errada</div>
          <div class="conf-item"><span class="dotc"></span>Tarifa bancária</div>
          <div class="conf-item"><span class="dotc"></span>Rendimentos esquecidos</div>
          <div class="conf-item"><span class="dotc"></span>Transferência registrada como receita</div>
        </div>

        <div class="errado" style="margin-top:16px;"><span class="rotulo">Alerta</span><p>Nunca altere um lançamento conciliado sem identificar primeiro a origem da diferença.</p></div>
      </div>

      <h3 style="margin-top:26px; font-size:1.05rem;">Boas práticas</h3>
      <div class="card">
        <div class="rec-cards">
          <div class="rec-card"><span class="dotc"></span>Conciliar frequentemente</div>
          <div class="rec-card"><span class="dotc"></span>Não acumular movimentações</div>
          <div class="rec-card"><span class="dotc"></span>Registrar lançamentos rapidamente</div>
          <div class="rec-card"><span class="dotc"></span>Utilizar descrições completas</div>
          <div class="rec-card"><span class="dotc"></span>Guardar comprovantes</div>
          <div class="rec-card"><span class="dotc"></span>Padronizar o plano de contas</div>
          <div class="rec-card"><span class="dotc"></span>Revisar antes do fechamento</div>
        </div>
      </div>

      <h3 style="margin-top:26px; font-size:1.05rem;">Dúvidas frequentes sobre conciliação</h3>
      <details class="accordion-item">
        <summary>O saldo do banco bate. Ainda preciso conferir os lançamentos?</summary>
        <div class="accordion-body">Sim. Saldo igual não garante que cada lançamento está certo, pode haver um erro cancelando o outro (um valor a mais em um lançamento e a menos em outro, por exemplo). Confira item por item, não só o saldo final.</div>
      </details>
      <details class="accordion-item">
        <summary>O que fazer quando encontrar uma diferença?</summary>
        <div class="accordion-body">Siga a ordem: verifique se o lançamento não foi registrado, se não está duplicado, se o valor está certo, se a classificação está certa e, por último, se o saldo confere. Veja o fluxo completo mais acima nesta página.</div>
      </details>
      <details class="accordion-item">
        <summary>Posso alterar um lançamento já conciliado?</summary>
        <div class="accordion-body">Não sem antes identificar a origem da diferença. Alterar um lançamento já conciliado sem entender o motivo pode mascarar um erro real, em vez de corrigi-lo.</div>
      </details>
      <details class="accordion-item">
        <summary>Preciso conciliar aplicações financeiras?</summary>
        <div class="accordion-body">Sim. Aplicações, resgates e rendimentos aparecem no extrato como qualquer outra movimentação e também precisam ser conferidos. Veja como classificar cada um em <a href="#lancamentos">Orientações Práticas de Lançamento</a>.</div>
      </details>
      <details class="accordion-item">
        <summary>Como identificar movimentações pendentes?</summary>
        <div class="accordion-body">São lançamentos que existem em um lugar (extrato ou ERP) mas ainda não no outro por exemplo, um cheque emitido mas ainda não compensado. Enquanto isso, a movimentação é uma pendência, não uma conciliação completa.</div>
      </details>
      <details class="accordion-item">
        <summary>O que fazer quando existir uma movimentação no extrato que não está no ERP?</summary>
        <div class="accordion-body">Registre a movimentação no ERP ou planilha, na conta correta, antes de considerar aquele item conciliado. Ela existiu de verdade — só ainda não tinha sido lançada.</div>
      </details>
      <details class="accordion-item">
        <summary>O que fazer quando existe um lançamento no ERP que não aparece no extrato?</summary>
        <div class="accordion-body">Verifique se não foi lançado por engano, duplicado ou com data errada. Se o lançamento realmente não aconteceu no banco, ele precisa ser corrigido ou removido do controle.</div>
      </details>

      <div class="cta-card" style="margin-top:24px;">
        <p style="color:#fff; font-weight:600; max-width:60ch; margin:0 auto 8px;">A conciliação bancária é uma das principais rotinas da gestão financeira. Quanto mais organizada ela for, mais confiáveis serão os relatórios e menor será o retrabalho entre a empresa e a equipe da Controladoria Sattva.</p>
        <a href="#plano-contas">Consultar o Plano de Contas →</a>
      </div>
    </section>

    <!-- 6. PLANO DE CONTAS -->
    <section class="section" id="plano-contas">
      <p class="section-eyebrow"><span class="dot"></span>06 · Consulta</p>
      <h2 class="sec-icon-h3"><span class="sec-icon"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><path d="M4 6h16M4 12h16M4 18h10"/></svg></span> Plano de Contas</h2>
      <p>Filtre pelo segmento do seu negócio, procure pelo nome da conta, marque suas favoritas e baixe a planilha em Excel para consulta offline.</p>

      <div class="filter-bar">
        <span class="label">Segmento</span>
        <button class="chip" data-filter="todos">Todos</button>
        <button class="chip" data-filter="comercio">Comércio</button>
        <button class="chip" data-filter="servicos">Serviços</button>
        <button class="chip" data-filter="industria">Indústria</button>
        <button class="chip fav-chip" id="favOnlyChip" title="Mostrar somente contas marcadas como favoritas">★ Só favoritas</button>
        <a class="download-btn" data-dl href="downloads/plano-de-contas-guia-financeiro.xlsx" download>
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4"><path d="M12 3v12"/><polyline points="7 10 12 15 17 10"/><path d="M5 21h14"/></svg>
          Baixar plano de contas (Excel)
        </a>
      </div>
      <div class="search-box" style="max-width:100%; margin-top:12px;">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="7"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
        <input type="text" id="fichaSearch" placeholder="Buscar uma conta pelo nome... ex.: aluguel, pró-labore, matéria-prima">
      </div>
      <p class="count-note" id="countNote"></p>

      <div class="fav-panel hidden" id="favPanel"></div>

      <div class="ficha-grid" id="fichaGrid">
        <div class="ficha-loading">Carregando plano de contas…</div>
      </div>

      <div class="card" style="margin-top:20px;">
        <span class="stamp verde">Sobre o Excel</span>
        <h3 style="margin-top:10px; font-size:1rem;">O que vem na planilha baixada</h3>
        <p>O arquivo <strong>plano-de-contas-guia-financeiro.xlsx</strong> traz uma aba de instruções e uma aba por segmento (Comércio, Serviços e Indústria), com todas as contas comentadas — código, categoria, definição, quando usar, quando não usar, exemplo prático e observações.</p>
      </div>
      <p style="font-size:0.78rem; color:var(--cinza-medio); margin-top:10px;">As contas mostradas aqui vêm de <code style="background:var(--fundo); padding:1px 6px; border-radius:4px;">data/plano-de-contas.json</code>. Suas favoritas ficam salvas só neste navegador.</p>
    </section>

    <!-- 7. FAQ -->
    <section class="section" id="faq">
      <p class="section-eyebrow"><span class="dot"></span>07 · Dúvidas</p>
      <h2 class="sec-icon-h3"><span class="sec-icon"><svg viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2"><circle cx="12" cy="12" r="9"/><path d="M9.5 9a2.5 2.5 0 0 1 5 0c0 1.7-2.5 2-2.5 4"/><circle cx="12" cy="17" r="0.6" fill="#fff"/></svg></span> Perguntas Frequentes</h2>
      <p>Dúvidas gerais sobre o guia, o plano de contas e os lançamentos. Para dúvidas específicas de conciliação bancária, veja o acordeão dentro da própria página de <a href="#conciliacao">Conciliação Bancária</a>.</p>
      <details class="accordion-item">
        <summary>Preciso saber contabilidade para usar este guia?</summary>
        <div class="accordion-body">Não. O Guia Financeiro foi escrito para quem nunca estudou finanças ou contabilidade, com exemplos práticos do dia a dia.</div>
      </details>
      <details class="accordion-item">
        <summary>Uso planilha do Excel, não ERP. O guia serve para mim?</summary>
        <div class="accordion-body">Serve — e é especialmente útil. As mesmas regras de conta e descrição valem para ERP ou planilha.</div>
      </details>
      <details class="accordion-item">
        <summary>Posso lançar tudo de uma vez no fim do mês?</summary>
        <div class="accordion-body">Pode, mas não é recomendado. Quanto mais tempo passa, maior a chance de esquecer detalhes. Lançar em bloco semanal já é um bom equilíbrio.</div>
      </details>
      <details class="accordion-item">
        <summary>E se eu não souber em qual conta lançar algo?</summary>
        <div class="accordion-body">Consulte o <a href="#plano-contas">Plano de Contas</a> — cada conta tem exemplos práticos. Se restar dúvida, pergunte à controladoria antes do fechamento do mês.</div>
      </details>
      <details class="accordion-item">
        <summary>Vale a pena lançar valores muito pequenos?</summary>
        <div class="accordion-body">Sim. Muitos valores pequenos somados distorcem o relatório tanto quanto um valor grande esquecido.</div>
      </details>

      <div class="cta-card" style="margin-top:24px;">
        <h3 style="color:#fff; margin-bottom:8px;">Ficou alguma dúvida?</h3>
        <p>Fale com sua controladoria — melhor perguntar do que lançar errado.</p>
        <a href="#inicio">Voltar ao início</a>
      </div>
    </section>

  </div>
</div>

<footer class="brand-footer">
  <div class="container">
    <div class="footer-brand">
      <img src="assets/sattva-logo.webp" alt="Sattva Controladoria" class="footer-logo-img" onerror="this.style.display='none';">
      <div class="tagline">GUIA FINANCEIRO · <span>SATTVA CONTROLADORIA</span></div>
    </div>
    <div class="desc">Material de consulta da controladoria financeira — feito para simplificar, não para complicar.</div>
  </div>
</footer>

<script>
/* ---------- fallback elegante para a logo (evita ícone de imagem quebrada) ---------- */
window.handleLogoError = function(imgEl){
  console.error('[Guia Financeiro] Não foi possível carregar a logo em "' + imgEl.getAttribute('src') + '". Verifique se o arquivo existe com esse nome exato (sensível a maiúsculas/minúsculas) na pasta "assets/".');
  imgEl.style.display = 'none';
  const fallback = document.getElementById('headerLogoFallback');
  if (fallback) fallback.style.display = 'inline-flex';
};

const toast = document.getElementById('toast');
let toastTimer;
function showToast(msg){
  toast.textContent = msg;
  toast.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(()=> toast.classList.remove('show'), 1500);
}

/* mobile sidebar */
const sidebar = document.getElementById('sidebar');
document.getElementById('menuToggle').addEventListener('click', () => sidebar.classList.toggle('open'));
document.querySelectorAll('.nav-link').forEach(a => a.addEventListener('click', () => sidebar.classList.remove('open')));

/* active section highlight */
const links = document.querySelectorAll('.nav-link');
const sections = document.querySelectorAll('.section');
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    const id = entry.target.getAttribute('id');
    const link = document.querySelector(`.nav-link[href="#${id}"]`);
    if (entry.isIntersecting) {
      links.forEach(l => l.classList.remove('active'));
      if (link) link.classList.add('active');
    }
  });
}, { rootMargin: '-35% 0px -55% 0px', threshold: 0 });
sections.forEach(s => observer.observe(s));

/* keyword -> section map, used by both search boxes */
const SEARCH_MAP = [
  { words: ['dre','competencia','competência','caixa','fluxo','indicador','conceito','regime','custo','provisao','provisão','entrada','saida','saída','credito','crédito','debito','débito'], id: 'conceitos' },
  { words: ['nova conta','criar conta','fluxograma'], id: 'nova-conta' },
  { words: ['escolher conta','conta certa'], id: 'escolher-conta' },
  { words: ['extrato','conciliacao','conciliação','saldo bate','duplicado','duplicidade','tarifa','cheque','pendente','pendencia','pendência'], id: 'conciliacao' },
  { words: ['descricao','descrição','lancar','lançar','pagamento','recebimento','rotina','pix','cartao','cartão','fatura','transferencia','transferência','aplicacao','aplicação','resgate','emprestimo','empréstimo','estorno','iof','juros','rendimento'], id: 'lancamentos' },
  { words: ['plano de contas','conta','excel','planilha','segmento','categoria'], id: 'plano-contas' },
  { words: ['duvida','dúvida','pergunta','faq'], id: 'faq' },
];
function goToSearch(term){
  const q = term.toLowerCase();
  let dest = 'plano-contas';
  for (const m of SEARCH_MAP) { if (m.words.some(w => q.includes(w))) { dest = m.id; break; } }
  document.getElementById(dest).scrollIntoView({behavior:'smooth'});
}
document.getElementById('heroSearchForm').addEventListener('submit', (e) => {
  e.preventDefault();
  goToSearch(document.getElementById('heroSearch').value);
});
document.getElementById('sideSearchBtn').addEventListener('click', () => goToSearch(document.getElementById('sideSearch').value));
document.getElementById('sideSearch').addEventListener('keydown', (e) => { if (e.key === 'Enter') goToSearch(e.target.value); });

/* ======================================================================
   PLANO DE CONTAS — carregado de data/plano-de-contas.json
   ====================================================================== */
const FAV_KEY = 'guiafinanceiro_contas_favoritas';
let CONTAS = [];
let favOnly = false;
let memFavFallback = []; // usado só se localStorage não estiver disponível

function loadFavorites(){
  try {
    const raw = localStorage.getItem(FAV_KEY);
    return raw ? JSON.parse(raw) : [];
  } catch (e) {
    return memFavFallback;
  }
}
function saveFavorites(arr){
  try {
    localStorage.setItem(FAV_KEY, JSON.stringify(arr));
  } catch (e) {
    memFavFallback = arr;
  }
}
function isFavorite(codigo){ return loadFavorites().includes(codigo); }

function fichaTemplate(c){
  const fav = isFavorite(c.codigo);
  return `
    <article class="ficha" data-segmento="${c.segmentos.join(' ')}" data-codigo="${c.codigo}" id="conta-${c.codigo}">
      <div class="ficha-head">
        <div><span class="ficha-code">${c.codigo}</span><h3 class="ficha-title">${c.titulo}</h3></div>
        <div class="ficha-side">
          <span class="stamp ${c.cor}">${c.categoria}</span>
          <button class="fav-btn ${fav ? 'active' : ''}" data-fav-toggle="${c.codigo}" aria-label="Marcar como favorita" title="Marcar como favorita">${fav ? '★' : '☆'}</button>
        </div>
      </div>
      <dl>
        <dt>Definição</dt><dd>${c.definicao}</dd>
        <dt>Quando usar</dt><dd>${c.quandoUsar}</dd>
        <dt>Quando não usar</dt><dd>${c.quandoNaoUsar}</dd>
        <dt>Exemplo prático</dt><dd>${c.exemplo}</dd>
        <dt>Observação</dt><dd>${c.observacao}</dd>
      </dl>
    </article>`;
}

const fichaGrid = document.getElementById('fichaGrid');
const favPanel = document.getElementById('favPanel');
const countNote = document.getElementById('countNote');
const fichaSearch = document.getElementById('fichaSearch');
const segChips = document.querySelectorAll('.chip[data-filter]');
const favOnlyChip = document.getElementById('favOnlyChip');
const dlLinks = document.querySelectorAll('[data-dl]');

function renderGrid(){
  fichaGrid.innerHTML = CONTAS.map(fichaTemplate).join('');
  applyFilters();
}

function renderFavPanel(){
  const favs = loadFavorites();
  if (!favs.length){ favPanel.classList.add('hidden'); favPanel.innerHTML = ''; return; }
  favPanel.classList.remove('hidden');
  const pills = favs.map(codigo => {
    const c = CONTAS.find(x => x.codigo === codigo);
    if (!c) return '';
    return `<button class="fav-pill" data-jump="${codigo}">★ ${c.titulo}</button>`;
  }).join('');
  favPanel.innerHTML = `<div class="fav-panel-label">Suas contas favoritas (acesso rápido)</div><div class="fav-pill-row">${pills}</div>`;
}

function applyFilters(){
  const activeSeg = document.querySelector('.chip[data-filter].active');
  const segVal = activeSeg ? activeSeg.getAttribute('data-filter') : 'todos';
  const term = fichaSearch.value.toLowerCase().trim();
  const favs = loadFavorites();
  let visible = 0;
  fichaGrid.querySelectorAll('.ficha').forEach(f => {
    const codigo = f.getAttribute('data-codigo');
    const segs = f.getAttribute('data-segmento').split(' ');
    const matchesSeg = segVal === 'todos' || segs.includes(segVal);
    const matchesFav = !favOnly || favs.includes(codigo);
    const matchesText = term === '' || f.textContent.toLowerCase().includes(term);
    const show = matchesSeg && matchesFav && matchesText;
    f.classList.toggle('hidden', !show);
    if (show) visible++;
  });
  countNote.textContent = favOnly && !favs.length
    ? 'Você ainda não marcou nenhuma conta como favorita — clique na ☆ de qualquer conta.'
    : `Mostrando ${visible} conta(s) comentada(s)`;
  dlLinks.forEach(a => {
    a.href = segVal === 'todos' ? 'downloads/plano-de-contas-guia-financeiro.xlsx#geral' : `downloads/plano-de-contas-guia-financeiro.xlsx#${segVal}`;
  });
}

segChips.forEach(c => c.addEventListener('click', () => {
  segChips.forEach(x => x.classList.remove('active'));
  c.classList.add('active');
  applyFilters();
}));

favOnlyChip.addEventListener('click', () => {
  favOnly = !favOnly;
  favOnlyChip.classList.toggle('active', favOnly);
  applyFilters();
});

fichaSearch.addEventListener('input', applyFilters);

fichaGrid.addEventListener('click', (e) => {
  const btn = e.target.closest('[data-fav-toggle]');
  if (!btn) return;
  const codigo = btn.getAttribute('data-fav-toggle');
  let favs = loadFavorites();
  const nowFav = !favs.includes(codigo);
  favs = nowFav ? [...favs, codigo] : favs.filter(c => c !== codigo);
  saveFavorites(favs);
  btn.textContent = nowFav ? '★' : '☆';
  btn.classList.toggle('active', nowFav);
  if (nowFav) {
    const ficha = btn.closest('.ficha');
    ficha.classList.add('just-favorited');
    setTimeout(() => ficha.classList.remove('just-favorited'), 650);
  }
  renderFavPanel();
  if (favOnly) applyFilters();
});

favPanel.addEventListener('click', (e) => {
  const pill = e.target.closest('[data-jump]');
  if (!pill) return;
  const codigo = pill.getAttribute('data-jump');
  segChips.forEach(x => x.classList.remove('active'));
  document.querySelector('.chip[data-filter="todos"]').classList.add('active');
  favOnly = false;
  favOnlyChip.classList.remove('active');
  fichaSearch.value = '';
  applyFilters();
  const el = document.getElementById('conta-' + codigo);
  if (el) {
    el.classList.remove('hidden');
    el.scrollIntoView({ behavior: 'smooth', block: 'center' });
    el.classList.add('jump-highlight');
    setTimeout(() => el.classList.remove('jump-highlight'), 1600);
  }
});

// carrega o plano de contas do JSON externo
fetch('data/plano-de-contas.json')
  .then(r => { if (!r.ok) throw new Error('HTTP ' + r.status); return r.json(); })
  .then(data => {
    CONTAS = data.contas || [];
    document.querySelector('.chip[data-filter="todos"]').classList.add('active');
    renderGrid();
    renderFavPanel();
  })
  .catch(err => {
    fichaGrid.innerHTML = `<div class="ficha-error">Não foi possível carregar <code>data/plano-de-contas.json</code>.<br>
      Se você abriu este arquivo diretamente no navegador (file://), o carregamento do JSON é bloqueado por segurança.<br>
      Publique a pasta em uma hospedagem, ou rode um servidor local (ex.: <code>npx serve</code>) e acesse via http://.</div>`;
  });

/* ======================================================================
   CONCILIAÇÃO BANCÁRIA — checklist final interativo
   ====================================================================== */
const CONCILIA_KEY = 'guiafinanceiro_checklist_conciliacao';
let conciliaMemFallback = [];

function loadConciliaDone(){
  try {
    const raw = localStorage.getItem(CONCILIA_KEY);
    return raw ? JSON.parse(raw) : [];
  } catch (e) {
    return conciliaMemFallback;
  }
}
function saveConciliaDone(arr){
  try { localStorage.setItem(CONCILIA_KEY, JSON.stringify(arr)); }
  catch (e) { conciliaMemFallback = arr; }
}

const conciliaList = document.getElementById('conciliaChecklist');
const conciliaFill = document.getElementById('conciliaProgressFill');
const conciliaLabel = document.getElementById('conciliaProgressLabel');
const conciliaReset = document.getElementById('resetConciliaChecklist');

function renderConciliaProgress(){
  if (!conciliaList) return;
  const items = conciliaList.querySelectorAll('li[data-item]');
  const done = loadConciliaDone();
  let count = 0;
  items.forEach(li => {
    const isDone = done.includes(li.getAttribute('data-item'));
    li.classList.toggle('done', isDone);
    if (isDone) count++;
  });
  const total = items.length;
  conciliaFill.style.width = total ? `${(count / total) * 100}%` : '0%';
  conciliaLabel.textContent = `${count} de ${total} conferidos`;
}

if (conciliaList) {
  conciliaList.addEventListener('click', (e) => {
    const li = e.target.closest('li[data-item]');
    if (!li) return;
    const key = li.getAttribute('data-item');
    let done = loadConciliaDone();
    done = done.includes(key) ? done.filter(k => k !== key) : [...done, key];
    saveConciliaDone(done);
    renderConciliaProgress();
  });
  conciliaReset.addEventListener('click', () => {
    saveConciliaDone([]);
    renderConciliaProgress();
  });
  renderConciliaProgress();
}
</script>
</body>
</html>
