<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="description" content="A digital museum of Philippine pop culture: the 2000s, today, and 2030.">
<style>:root{padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}body{margin:0}img{max-width:100%}</style>
<title>What's Poppin', Pinoy? Museum</title>
<meta name="claude:viewport-fit-sides" content="cover">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Gloock&family=Hanken+Grotesk:wght@400;500;600;700&family=Anton&family=Archivo:wght@400;600;700&family=Overpass:wght@700;800&family=Roboto:wght@400;500;700&family=Source+Sans+3:ital,wght@0,400;0,600;0,700;1,400&family=Silkscreen&family=Space+Mono:wght@400;700&family=Courier+Prime:wght@400;700&family=Special+Elite&family=VT323&family=Noto+Sans+Tagalog&display=swap">
<style>
/* Layout: a Filipino museum building. Each gallery area re-skins the whole museum (see Area themes below).
   Floor plan: ground floor = Kaliwang Pakpak | Pangunahing Bulwagan | Kanang Pakpak; second floor = Ang Hinaharap (2030) | Palaruan (games). */
:root{
  --bg:#FFFDF7; --panel:#FFFFFF; --ink:#23182B; --muted:#675870; --line:#EADFD3;
  --frame:#8A4B22; --past:#C2185B; --now:#1565C0; --next:#6A35B5; --main:#C96A00; --ok:#1B7A44; --bad:#B3261E; --scrim:rgba(35,24,43,.5);
  --d1:rgba(194,24,91,.32); --d2:rgba(21,101,192,.28); --d3:rgba(240,180,0,.55); --d4:rgba(30,158,90,.30); --glow:rgba(245,197,24,.20);
  --f1:#E0245E; --f2:#F28C28; --f3:#F5C518; --f4:#1E9E5A; --f5:#1D6FD1; --f6:#7B3FBF;
  --lcd-bg:#9DB08A; --lcd-ink:#1F2A18; --lcd-edge:#3B4733;
  --show-fiesta:block; --show-pasko:none;
  --room:var(--main);
  --display:"Gloock","Playfair Display",Georgia,serif;
  --body:"Hanken Grotesk",system-ui,-apple-system,"Segoe UI",sans-serif;
  --lcd:"VT323",ui-monospace,Menlo,monospace;
  --baybayin:"Noto Sans Tagalog",serif;
}

*{box-sizing:border-box}
[hidden]{display:none!important}
body{background-color:var(--bg);
  background-image:
    radial-gradient(ellipse 120% 60% at 50% 0%,var(--glow),transparent 65%),
    radial-gradient(circle at 18% 26%,var(--d1) 0 2.6px,transparent 3.2px),
    radial-gradient(circle at 64% 58%,var(--d2) 0 2.2px,transparent 2.8px),
    radial-gradient(circle at 40% 82%,var(--d3) 0 3px,transparent 3.6px),
    radial-gradient(circle at 86% 14%,var(--d4) 0 2px,transparent 2.6px);
  background-size:100% 1000px,96px 104px,132px 118px,78px 126px,150px 90px;
  background-repeat:no-repeat,repeat,repeat,repeat,repeat;
  color:var(--ink);font-family:var(--body);font-size:15.5px;line-height:1.55;
  padding-left:max(16px,env(safe-area-inset-left,0px));padding-right:max(16px,env(safe-area-inset-right,0px));padding-block:0 40px}
.wrap{max-width:1140px;margin:0 auto;display:flex;flex-direction:column;gap:30px}
h1,h2,h3{font-family:var(--display);font-weight:400;text-wrap:balance;margin:0;line-height:1.08}
p{margin:0}
a{color:inherit}
button,input,textarea,select{font:inherit;color:inherit}
button{cursor:pointer}
:focus-visible{outline:2px solid var(--main);outline-offset:3px}
.eyebrow{font-size:11.5px;font-weight:600;letter-spacing:.16em;text-transform:uppercase;color:var(--muted)}
.tl{font-style:italic;color:var(--muted);font-weight:400}

/* Decorations */
.deco{position:relative;height:96px;margin-inline:calc(-1 * max(16px,env(safe-area-inset-left,0px)));overflow:hidden;pointer-events:none}
.fiesta{display:var(--show-fiesta)} .pasko{display:var(--show-pasko)}
.deco svg{position:absolute;inset:0;width:100%;height:100%}
.sway{transform-origin:top center;animation:sway 3.2s ease-in-out infinite alternate}
.twinkle{animation:twinkle 1.6s ease-in-out infinite alternate}
.glowing{filter:drop-shadow(0 0 10px rgba(247,201,72,.55))}
@keyframes sway{from{transform:rotate(-3deg)}to{transform:rotate(3deg)}}
@keyframes twinkle{from{opacity:.35}to{opacity:1}}

.deco.bottom{height:70px;transform:scaleY(-1)}
.deco.pasko{height:128px;margin-bottom:-32px}

header.entrance{display:grid;grid-template-columns:minmax(0,1.4fr) minmax(0,1fr);gap:28px;align-items:end;margin-top:-20px}
header h1{font-size:clamp(40px,7.4vw,84px);letter-spacing:-.01em}
header h1 .pin{color:var(--past)}
header .sub{display:flex;flex-direction:column;gap:10px;color:var(--muted);max-width:48ch;background:color-mix(in srgb,var(--bg) 85%,transparent);padding:6px 0}
.bay{font-family:var(--baybayin);font-size:26px;color:var(--frame);letter-spacing:.1em}
.mode{align-self:flex-start;display:inline-flex;border:1px solid var(--frame);background:var(--panel)}
.mode button{background:none;border:0;padding:7px 12px;font-size:12.5px;font-weight:600}
.mode button+button{border-left:1px solid var(--frame)}
.mode button[aria-pressed="true"]{background:var(--frame);color:var(--panel)}
@media (max-width:780px){header.entrance{grid-template-columns:1fr}}

/* Floor plan: two floors */
.plan{display:grid;grid-template-columns:1fr 1.3fr 1fr;border:3px solid var(--frame);background:var(--panel)}
.plan button{background:none;border:0;padding:16px 16px 18px;text-align:left;display:flex;flex-direction:column;gap:3px;position:relative;min-width:0;transition:background .2s}
.plan .g1+.g1{border-left:3px solid var(--frame)}
.plan .f2{border-top:3px solid var(--frame)}
.plan .f2.wide{grid-column:span 2}
.plan .f2+.f2{border-left:3px solid var(--frame)}
.plan button:hover{background:color-mix(in srgb,var(--rc) 7%,transparent)}
.plan button[aria-current="true"]{background:color-mix(in srgb,var(--rc) 14%,transparent)}
.plan .rname{font-family:var(--display);font-size:clamp(18px,2.4vw,25px);line-height:1.12}
.plan button[aria-current="true"] .rname{color:var(--rc)}
.plan .rsub{font-size:12.5px;color:var(--muted)}
.plan .here{font-size:10.5px;font-weight:700;letter-spacing:.14em;text-transform:uppercase;color:var(--rc);visibility:hidden}
.plan button[aria-current="true"] .here{visibility:visible}
.plan .floor{position:absolute;right:10px;top:8px;font-size:10px;font-weight:700;letter-spacing:.12em;color:var(--muted)}
.plan-note{display:flex;justify-content:space-between;gap:12px;flex-wrap:wrap;margin-top:8px}
@media (max-width:580px){.plan{grid-template-columns:1fr}.plan .g1+.g1,.plan .f2+.f2{border-left:0;border-top:3px solid var(--frame)}.plan .f2.wide{grid-column:auto}}

/* Rooms */
.room{display:flex;flex-direction:column;gap:22px}
.room-head{display:flex;justify-content:space-between;align-items:end;gap:20px;flex-wrap:wrap;background:color-mix(in srgb,var(--bg) 88%,transparent);padding:10px 12px;margin-inline:-12px}
.room-head h2{font-size:clamp(30px,4.8vw,50px);color:var(--room)}
.room-head p{color:var(--muted);max-width:54ch}
.chips{display:flex;gap:8px;flex-wrap:wrap}
.chip{background:var(--panel);border:1px solid var(--line);padding:7px 13px;display:flex;flex-direction:column;align-items:flex-start;line-height:1.2}
.chip small{font-size:11px;color:var(--muted);font-style:italic}
.chip:hover{border-color:var(--room)}
.chip[aria-pressed="true"]{background:var(--room);border-color:var(--room);color:var(--panel)}
.chip[aria-pressed="true"] small{color:inherit;opacity:.85}
.frame{background:var(--panel);border:1px solid var(--line);outline:6px solid color-mix(in srgb,var(--frame) 85%,transparent);outline-offset:-1px;
  padding:22px;display:flex;flex-direction:column;gap:14px;min-width:0;margin:6px}
.frame h3{font-size:23px}
.cat{font-size:11px;font-weight:700;letter-spacing:.14em;text-transform:uppercase;color:var(--room)}

/* Photos */
figure{margin:0;display:flex;flex-direction:column;gap:5px;min-width:0}
figure .ph{position:relative;aspect-ratio:3/2;max-width:100%;background:color-mix(in srgb,var(--sc,var(--room)) 10%,var(--panel));border:1px solid var(--line);overflow:hidden}
figure img{width:100%;height:100%;object-fit:cover;display:block}
figure .ph .era{position:absolute;left:8px;top:8px;font-size:10.5px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;background:var(--panel);color:var(--sc,var(--room));padding:3px 7px}
figcaption{font-size:12px;color:var(--muted);line-height:1.4}
figcaption a{color:var(--muted)}

/* Main hall */
.tnn{display:flex;flex-direction:column;border:2px solid var(--main);background:var(--panel)}
.tnn button{display:grid;grid-template-columns:150px repeat(3,minmax(0,1fr));gap:12px;align-items:center;background:none;border:0;border-top:1px solid var(--line);padding:10px 14px;text-align:left}
.tnn button:first-child{border-top:0}
.tnn button:hover,.tnn button[aria-current="true"]{background:color-mix(in srgb,var(--main) 10%,transparent)}
.tnn b{font-family:var(--display);font-weight:400;font-size:17px}
.tnn span{font-size:13.5px}
.tnn .p{color:var(--past)} .tnn .n{color:var(--now)} .tnn .x{color:var(--next)}
.tnn .arrowed::before{content:"→ ";color:var(--muted)}
@media (max-width:760px){.tnn button{grid-template-columns:1fr}.tnn .arrowed::before{content:"↓ "}}
.versus{display:grid;grid-template-columns:minmax(0,1fr) auto minmax(0,1fr) auto minmax(0,1fr);gap:14px;align-items:stretch}
@media (max-width:900px){.versus{grid-template-columns:1fr}.versus .arrow{transform:rotate(90deg);justify-self:center}}
.side{display:flex;flex-direction:column;gap:12px;padding:16px;border-top:5px solid var(--sc);background:color-mix(in srgb,var(--sc) 6%,var(--panel));min-width:0}
.side .when{font-family:var(--display);font-size:28px;color:var(--sc);line-height:1}
.side dt{font-size:11.5px;font-weight:700;letter-spacing:.12em;text-transform:uppercase;color:var(--muted)}
.side dd{margin:2px 0 0}
.side dl{margin:0;display:flex;flex-direction:column;gap:12px}
.arrow{align-self:center;font-family:var(--display);font-size:34px;color:var(--frame)}
.impacts{display:grid;grid-template-columns:1fr 1fr;gap:14px}
@media (max-width:760px){.impacts{grid-template-columns:1fr}}
.impact{border:2px solid var(--ic,var(--main));padding:16px 18px;display:flex;flex-direction:column;gap:6px}
.impact .eyebrow{color:var(--frame)}
.impact p{font-family:var(--display);font-size:clamp(17px,2vw,21px);line-height:1.3}
.srcs{display:flex;flex-direction:column;gap:6px;font-size:13px;color:var(--muted)}
.srcs ul{margin:0;padding-left:18px;display:flex;flex-direction:column;gap:3px}
.srcs a{overflow-wrap:anywhere}
.lessons{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:14px}
@media (max-width:860px){.lessons{grid-template-columns:repeat(2,minmax(0,1fr))}}
@media (max-width:520px){.lessons{grid-template-columns:1fr}}
.lesson{background:var(--panel);border:1px solid var(--line);padding:14px;text-align:left;display:flex;flex-direction:column;gap:6px;min-width:0}
.lesson:hover{border-color:var(--main)}
.lesson b{font-family:var(--display);font-weight:400;font-size:19px}
.lesson span{font-size:13.5px;color:var(--muted)}

/* Wings */
.wing-top{display:grid;grid-template-columns:minmax(0,1.1fr) minmax(0,1fr);gap:18px;align-items:start}
@media (max-width:760px){.wing-top{grid-template-columns:1fr}}
.gallery{display:grid;grid-template-columns:repeat(6,minmax(0,1fr));gap:14px}
.ex{grid-column:span 2;background:var(--panel);border:1px solid var(--line);padding:16px;text-align:left;display:flex;flex-direction:column;gap:8px;min-width:0;transition:transform .18s,box-shadow .18s}
.ex.big{grid-column:span 3}
.ex:hover{transform:translateY(-2px);box-shadow:0 12px 24px -16px rgba(0,0,0,.45);border-color:var(--room)}

.ex .label{font-size:11px;font-weight:700;letter-spacing:.13em;text-transform:uppercase;color:var(--room)}
.ex .txt{font-size:15px}
.ex .more{margin-top:auto;font-size:12px;color:var(--frame);font-weight:600}
@media (max-width:860px){.ex,.ex.big{grid-column:span 3}}
@media (max-width:540px){.ex,.ex.big{grid-column:span 6}}
.lcd{align-self:flex-start;font-family:var(--lcd);font-size:19px;line-height:1;padding:4px 8px 3px;background:var(--lcd-bg);color:var(--lcd-ink);border:2px solid var(--lcd-edge);letter-spacing:.04em}
.app{align-self:flex-start;font-size:11.5px;font-weight:700;padding:4px 10px;border-radius:999px;background:var(--now);color:var(--panel);letter-spacing:.04em}
.holo{align-self:flex-start;font-size:11.5px;font-weight:700;padding:4px 10px;border-radius:6px;border:1.5px solid var(--next);color:var(--next);letter-spacing:.06em;background:color-mix(in srgb,var(--next) 10%,transparent)}
.note{font-size:13px;color:var(--muted);border-left:3px solid var(--next);padding-left:10px}

/* Plaque panel */
.scrim{position:fixed;inset:0;background:var(--scrim);z-index:20}
.panel{position:fixed;top:0;right:0;bottom:0;width:min(560px,100%);background:var(--panel);z-index:21;border-left:6px solid var(--frame);
  padding:calc(26px + env(safe-area-inset-top,0px)) calc(24px + env(safe-area-inset-right,0px)) calc(28px + env(safe-area-inset-bottom,0px)) 24px;
  overflow-y:auto;display:flex;flex-direction:column;gap:16px;animation:slide .28s ease-out}
@keyframes slide{from{transform:translateX(26px);opacity:.4}}

.panel h3{font-size:30px}
.pair{display:flex;flex-direction:column;gap:12px}
.pair .side .when{font-size:22px}
.pair .side.cur{outline:2px solid var(--sc);outline-offset:-2px}
.actions{display:flex;gap:10px;flex-wrap:wrap}
.btn{background:var(--panel);border:1px solid var(--ink);padding:8px 14px;font-size:13px;font-weight:600}
.btn:hover{background:color-mix(in srgb,var(--ink) 8%,var(--panel))}
.btn.primary{background:var(--room);border-color:var(--room);color:var(--panel)}
.btn:disabled{opacity:.45;cursor:default}
.close{align-self:flex-end}

/* Palaruan (games) */
.games{display:grid;grid-template-columns:1fr 1fr;gap:18px}
@media (max-width:860px){.games{grid-template-columns:1fr}}
.game{gap:14px}
.score{font-family:var(--display);font-size:20px;color:var(--room)}
.clue{font-family:var(--display);font-size:clamp(18px,2.2vw,22px);line-height:1.35;min-height:4.2em}
.opts{display:flex;flex-direction:column;gap:8px}
.opt{background:var(--panel);border:1.5px solid var(--line);padding:10px 14px;text-align:left;font-weight:500}
.opt:hover:not(:disabled){border-color:var(--room)}
.opt.right{border-color:var(--ok);background:color-mix(in srgb,var(--ok) 14%,var(--panel))}
.opt.wrong{border-color:var(--bad);background:color-mix(in srgb,var(--bad) 12%,var(--panel))}
.eras{display:grid;grid-template-columns:repeat(3,1fr);gap:8px}
.eras button{padding:12px 8px;border:2px solid var(--ec);background:var(--panel);color:var(--ec);font-weight:700}
.eras button:hover:not(:disabled){background:color-mix(in srgb,var(--ec) 10%,var(--panel))}
.feedback{font-size:14px;min-height:1.5em}
.feedback.ok{color:var(--ok)} .feedback.no{color:var(--bad)}
/* Nokia-style phone */
.phone{align-self:center;width:min(300px,100%);background:#2E3B55;border-radius:36px 36px 46px 46px;padding:22px 20px 26px;display:flex;flex-direction:column;gap:14px;box-shadow:inset 0 -6px 0 rgba(0,0,0,.25)}
.phone .brand{text-align:center;color:#DDE3EE;font-weight:700;letter-spacing:.3em;font-size:12px}
.phone .screen{background:var(--lcd-bg);border:4px solid #1B2436;border-radius:8px;padding:10px;color:var(--lcd-ink);font-family:var(--lcd);font-size:20px;line-height:1.1;display:flex;flex-direction:column;gap:6px;min-height:170px}
.phone .screen .bar{display:flex;justify-content:space-between;font-size:17px}
.phone textarea{background:transparent;border:0;resize:none;font-family:var(--lcd);font-size:20px;color:var(--lcd-ink);min-height:88px;outline:none}
.phone textarea::placeholder{color:#4A5A3E}
.phone .keys{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.phone .keys button{background:#C8D0DE;color:#1B2436;border:0;border-radius:14px;padding:9px 6px;font-weight:700;font-size:13px}
.phone .keys button:hover{background:#E1E6EF}
.gb-form{display:flex;flex-direction:column;gap:10px}
.gb-form label{font-size:13px;font-weight:600;display:flex;flex-direction:column;gap:4px}
.gb-form input,.gb-form textarea,.gb-form select{background:var(--panel);border:1px solid var(--line);padding:9px 10px;border-radius:0}
.gb-form textarea{min-height:90px;resize:vertical}
.gb-list{display:flex;flex-direction:column;gap:8px}
.gb-note{border:1px solid var(--line);border-left:4px solid var(--main);padding:10px 12px;background:var(--panel)}
.gb-note b{font-weight:600}

footer{display:flex;flex-direction:column;gap:14px}
.desk{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:18px}
@media (max-width:860px){.desk{grid-template-columns:repeat(2,minmax(0,1fr))}}
@media (max-width:540px){.desk{grid-template-columns:1fr}}
.desk h4{margin:0 0 6px;font-family:var(--display);font-weight:400;font-size:18px}
.desk ul{margin:0;padding-left:18px;display:flex;flex-direction:column;gap:4px;font-size:13px;color:var(--muted)}
.desk a{overflow-wrap:anywhere}
.desk .wide{grid-column:1/-1}
.desk .wide ul{columns:2;column-gap:28px;display:block}
.desk .wide li{break-inside:avoid;margin-bottom:4px}
@media (max-width:700px){.desk .wide ul{columns:1}}
.colophon{display:flex;justify-content:space-between;gap:12px;flex-wrap:wrap;font-size:13px;color:var(--muted);border-top:1px solid var(--line);padding-top:14px}

/* ================= Area themes: the whole museum re-skins for the gallery you pick =================
   social = 2000s Friendster-style profile · economic = old desktop computer · political = EDSA billboards
   cultural = videoke screen · environmental = emergency alert text · others = Philippine passport */
:root{--on-bg:var(--ink);--on-bg-muted:var(--muted);--on-bg-accent:var(--main);--radius:0px;--chip-on:var(--main);--chip-on-ink:#fff}
body{transition:background-color .3s}

header.entrance,.room-head,.plan-note,.colophon,.bglabel{color:var(--on-bg)}
header.entrance .eyebrow,.room-head .eyebrow,.room-head p,.plan-note .eyebrow,.colophon,.bglabel .eyebrow,header .sub p{color:var(--on-bg-muted)}
header h1{font-family:var(--display);color:var(--on-bg)}
header h1 .pin,.bay,.room-head h2{color:var(--on-bg-accent)}
.room-head{background:transparent}
header .sub{background:transparent}
h1,h2,h3,.plan .rname,.side .when,.lesson b,.desk h4,.impact p,.clue,.score,.tnn b{font-family:var(--display)}
.frame{border-radius:var(--radius)}
.chip[aria-pressed="true"]{background:var(--chip-on);border-color:var(--chip-on);color:var(--chip-on-ink)}
.chip[aria-pressed="true"] small{color:inherit}
footer .desk{background:var(--panel);border:1px solid var(--line);padding:20px;border-radius:var(--radius)}
.note{color:var(--on-bg-muted)}
.wing-top figcaption,.wing-top figcaption a{color:var(--on-bg-muted)}
.bglabel>.eyebrow{color:var(--on-bg-muted)}
.tnn,.lessons{color:var(--ink)}
.themeline{font-size:13px;font-weight:600;color:var(--on-bg-accent)}

/* Banner at the top of the page, rebuilt for each theme */
#banner{margin-inline:calc(-1 * max(16px,env(safe-area-inset-left,0px)));min-height:56px;display:flex;align-items:center;gap:16px;flex-wrap:wrap;padding:10px max(16px,env(safe-area-inset-left,0px));font-size:14px}
#banner .grow{flex:1}
#banner{overflow:hidden;box-sizing:border-box;width:calc(100% + 2 * max(16px,env(safe-area-inset-left,0px)))}
#banner>*{min-width:0;max-width:100%}
#banner .led{min-width:0}
.mrz{white-space:pre-wrap;font-family:"Courier New",monospace;font-size:clamp(11px,1.6vw,16px);letter-spacing:.12em;line-height:1.5;overflow-wrap:anywhere;color:var(--ink);background:var(--panel);padding:12px 16px;border-top:1px dashed var(--line)}



/* ================= Realism, fonts and motion per theme ================= */
.wrap{animation:fadeIn .45s ease-out}
body.switching .wrap{animation:switchIn .5s ease-out}
@keyframes fadeIn{from{opacity:0}to{opacity:1}}
@keyframes switchIn{from{opacity:.25;transform:translateY(6px)}to{opacity:1;transform:none}}
.gallery .ex{animation:var(--ex-anim,popIn) .5s both}
.gallery .ex:nth-child(2){animation-delay:.07s}.gallery .ex:nth-child(3){animation-delay:.14s}.gallery .ex:nth-child(4){animation-delay:.21s}.gallery .ex:nth-child(5){animation-delay:.28s}
@keyframes popIn{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:none}}
.fx{position:fixed;inset:0;pointer-events:none;z-index:15;display:none}

@keyframes glitter{to{background-position:300% 0}}
@keyframes wiggleIn{0%{opacity:0;transform:scale(.9) rotate(-2deg)}60%{opacity:1;transform:scale(1.03) rotate(1deg)}100%{transform:none}}
@keyframes blink{to{visibility:hidden}}
@keyframes marquee{to{transform:translateX(-100%)}}
@keyframes twinkleS{from{opacity:.2;transform:scale(.7)}to{opacity:1;transform:scale(1.15)}}
@keyframes winOpen{from{opacity:0;transform:scale(.92)}to{opacity:1;transform:none}}
@keyframes dial{from{background-position:100% 0}to{background-position:0 0}}
@keyframes lamp{0%,92%,100%{filter:none}94%{filter:brightness(.4)}96%{filter:none}97%{filter:brightness(.5)}}
@keyframes flickerOn{0%{opacity:0}20%{opacity:.8}25%{opacity:.2}40%{opacity:1}45%{opacity:.6}100%{opacity:1}}
@keyframes traffic{to{background-position:90px 0,-45px 0}}
@keyframes beams{to{transform:rotate(360deg)}}
@keyframes sing{0%{background-position:100% 0}35%,100%{background-position:0 0}}
@keyframes eq{from{height:4px}to{height:18px}}
@keyframes bubbleIn{0%{opacity:0;transform:translateY(12px) scale(.96)}100%{opacity:1;transform:none}}
@keyframes alertIn{from{transform:translateY(-120%);opacity:0}to{transform:none;opacity:1}}
@keyframes buzz{0%,100%{transform:none}20%{transform:translateX(-4px)}40%{transform:translateX(4px)}60%{transform:translateX(-3px)}80%{transform:translateX(3px)}}
@keyframes rain{to{background-position:-40px 200px}}
@keyframes pulse{50%{background:#B71C1C}}
@keyframes dots{0%,60%,100%{opacity:.3;transform:none}30%{opacity:1;transform:translateY(-3px)}}
@keyframes stampIn{0%{opacity:0;transform:scale(1.8) rotate(-8deg)}70%{opacity:1;transform:scale(.97) rotate(-1deg)}100%{transform:rotate(-1.2deg)}}
@keyframes stampIn2{0%{opacity:0;transform:scale(1.8) rotate(8deg)}70%{opacity:1;transform:scale(.97) rotate(2deg)}100%{transform:rotate(1deg)}}
@keyframes pageTurn{from{transform:perspective(1200px) rotateY(-14deg);transform-origin:left center;opacity:.4}to{transform:none;opacity:1}}
@keyframes emboss{from{text-shadow:0 1px 0 #2A0A10}to{text-shadow:0 1px 0 #2A0A10,0 0 10px rgba(242,213,138,.45)}}



/* ======================= AREA THEMES v2 ======================= */

/* ---------- SOCIAL · Nokia 3310 green LCD ---------- */
body[data-area="social"]{--bg:#A6CB37;--panel:#B8DB4C;--ink:#1D2A08;--muted:#3C4D16;--line:#1D2A08;--frame:#1D2A08;--past:#1D2A08;--now:#1D2A08;--next:#1D2A08;--main:#1D2A08;--ok:#1D2A08;--bad:#5A1A00;
  --display:"Silkscreen","VT323",monospace;--body:"Space Mono","Courier New",monospace;--radius:0px;--on-bg:#1D2A08;--on-bg-muted:#34460F;--on-bg-accent:#1D2A08;--chip-on:#1D2A08;--chip-on-ink:#B8DB4C;--ex-anim:pixelIn;
  --lcd-bg:#B8DB4C;--lcd-ink:#1D2A08;--lcd-edge:#1D2A08;
  background-image:linear-gradient(rgba(29,42,8,.07) 1px,transparent 1px),linear-gradient(90deg,rgba(29,42,8,.07) 1px,transparent 1px);background-size:6px 6px;font-size:13.5px}
body[data-area="social"] h1,body[data-area="social"] h2,body[data-area="social"] h3{font-weight:400;text-transform:uppercase;letter-spacing:.02em}
body[data-area="social"] header h1{font-size:clamp(34px,6vw,70px);line-height:1.05}
body[data-area="social"] .frame{outline:0;border:3px solid #1D2A08;box-shadow:6px 6px 0 #1D2A08;background:#B8DB4C}
body[data-area="social"] .frame::before{content:"▮▮▮▯  ✉ 1   MENU";position:absolute;left:0;right:0;top:0;background:#1D2A08;color:#B8DB4C;font:13px "VT323",monospace;padding:3px 10px;letter-spacing:.08em}
body[data-area="social"] .frame{position:relative;padding-top:38px}
body[data-area="social"] .ex,body[data-area="social"] .side,body[data-area="social"] .lesson,body[data-area="social"] .tnn,body[data-area="social"] .plan,body[data-area="social"] footer .desk{background:#B8DB4C;border:3px solid #1D2A08;border-radius:0;box-shadow:4px 4px 0 #1D2A08}
body[data-area="social"] .side{border-top-width:3px}
body[data-area="social"] .ex .txt{font-size:13px}
body[data-area="social"] .chip,body[data-area="social"] .btn{background:#B8DB4C;border:2px solid #1D2A08;border-radius:0;color:#1D2A08;font-family:"Silkscreen",monospace;font-size:12px}
body[data-area="social"] .chip small{font-family:"Space Mono",monospace}
body[data-area="social"] .plan button,body[data-area="social"] .plan .g1+.g1,body[data-area="social"] .plan .f2{border-color:#1D2A08!important}
@keyframes pixelIn{0%{opacity:0;clip-path:inset(0 0 100% 0)}25%{opacity:1;clip-path:inset(0 0 75% 0)}50%{clip-path:inset(0 0 50% 0)}75%{clip-path:inset(0 0 25% 0)}100%{clip-path:inset(0 0 0 0)}}
body[data-area="social"] .gallery .ex{animation-timing-function:steps(1,end)}
body[data-area="social"] #banner{background:#1D2A08;color:#B8DB4C;font-family:"VT323",monospace;font-size:20px;position:relative;overflow:hidden;min-height:64px}
body[data-area="social"] #banner .soft{border:2px solid #B8DB4C;padding:0 8px}
body[data-area="social"] .snake{position:absolute;left:0;bottom:6px;height:8px;width:72px;background:repeating-linear-gradient(90deg,#B8DB4C 0 8px,transparent 8px 10px);animation:snake 9s steps(60) infinite}
body[data-area="social"] .apple{position:absolute;bottom:6px;width:8px;height:8px;background:#B8DB4C;left:72%;animation:blink 1s steps(2,start) infinite}
@keyframes snake{from{transform:translateX(-80px)}to{transform:translateX(calc(100vw + 20px))}}
body[data-area="social"] .room-head h2::after{content:"_";animation:blink 1s steps(2,start) infinite}

/* ---------- ECONOMIC · Windows XP-era desktop ---------- */
body[data-area="economic"]{--bg:#5A8FD6;--panel:#ECE9D8;--ink:#111111;--muted:#3D3D3D;--line:#7F9DB9;--frame:#0A3AA8;--past:#A31515;--now:#0A3AA8;--next:#5B2C83;--main:#0A3AA8;--ok:#1D7A1D;--bad:#A31515;
  --display:"Trebuchet MS",Tahoma,sans-serif;--body:Tahoma,Verdana,"Segoe UI",sans-serif;--radius:0px;--on-bg:#FFFFFF;--on-bg-muted:#F2F7FF;--on-bg-accent:#FFFFFF;--chip-on:#2A6BE0;--chip-on-ink:#fff;--ex-anim:winOpen;
  background-image:radial-gradient(ellipse 70% 18% at 22% 18%,rgba(255,255,255,.85),transparent 70%),radial-gradient(ellipse 50% 12% at 70% 12%,rgba(255,255,255,.7),transparent 70%),radial-gradient(ellipse 140% 60% at 30% 108%,#5FB238 0 52%,transparent 53%),radial-gradient(ellipse 110% 55% at 95% 112%,#3E8F25 0 50%,transparent 51%),linear-gradient(180deg,#1B57C6 0%,#4E8DE6 35%,#A9CDF2 62%,#DDEBF8 75%);
  background-size:100% 100%;background-attachment:fixed;font-size:13.5px;padding-bottom:64px}
body[data-area="economic"] header h1,body[data-area="economic"] .room-head h2{font-family:"Trebuchet MS",Tahoma,sans-serif;font-weight:700;text-shadow:1px 2px 3px rgba(0,0,0,.45)}
body[data-area="economic"] header .sub p,body[data-area="economic"] .room-head p,body[data-area="economic"] .eyebrow{text-shadow:0 1px 2px rgba(0,0,0,.5)}
body[data-area="economic"] .frame,body[data-area="economic"] footer .desk,body[data-area="economic"] .plan,body[data-area="economic"] .tnn{outline:0;border:3px solid #0A3AA8;border-top:0;border-radius:8px 8px 0 0;background:#ECE9D8;box-shadow:2px 4px 14px rgba(0,0,0,.35);position:relative}
body[data-area="economic"] .frame{padding-top:44px}
body[data-area="economic"] .frame::before{content:"Museo ng Ekonomiya";position:absolute;left:-3px;right:-3px;top:0;height:30px;border-radius:8px 8px 0 0;background:linear-gradient(180deg,#3C8CF8 0%,#0A5AE0 12%,#0A50D6 50%,#0848C8 88%,#063AA4 100%);color:#fff;font:700 13px "Trebuchet MS",Tahoma,sans-serif;padding:7px 12px;box-sizing:border-box;text-shadow:1px 1px 1px #0A246A}
body[data-area="economic"] .frame::after{content:"✕";position:absolute;right:6px;top:4px;width:21px;height:21px;border-radius:3px;border:1px solid #fff;background:linear-gradient(#E87A5B,#C7401E);color:#fff;font:700 12px/19px Tahoma,sans-serif;text-align:center}
body[data-area="economic"] .ex,body[data-area="economic"] .side,body[data-area="economic"] .lesson{background:#FFFFFF;border:1px solid #7F9DB9;border-radius:0}
body[data-area="economic"] .btn,body[data-area="economic"] .chip,body[data-area="economic"] .opt,body[data-area="economic"] .eras button{background:linear-gradient(#FFFFFF,#ECEBE6 85%,#D6D0C5);border:1px solid #003C74;border-radius:3px;color:#111}
body[data-area="economic"] .chip[aria-pressed="true"]{background:linear-gradient(#FFF4D6,#FFD679);color:#111;border-color:#E5A700;box-shadow:inset 0 -2px 0 #E5A700}
body[data-area="economic"] .chip[aria-pressed="true"] small{color:#3D3D3D}
@keyframes winOpen{from{opacity:0;transform:scale(.9)}to{opacity:1;transform:none}}
body[data-area="economic"] #banner{position:fixed;left:0;right:0;bottom:0;width:auto;z-index:18;margin:0;min-height:36px;padding:0 env(safe-area-inset-right,0px) env(safe-area-inset-bottom,0px) env(safe-area-inset-left,0px);gap:6px;flex-wrap:nowrap;background:linear-gradient(180deg,#3F8CF3 0%,#245EDC 10%,#225BD6 85%,#1941A5 100%);color:#fff;font:12px Tahoma,sans-serif}
body[data-area="economic"] #banner .start{font:italic 700 18px "Trebuchet MS",Tahoma,sans-serif;padding:4px 22px 5px 14px;border-radius:0 12px 12px 0;background:linear-gradient(180deg,#5EB75A 0%,#3C9A38 50%,#2F8A2C 100%);text-shadow:1px 1px 2px #1A4D18;box-shadow:inset -2px 0 3px rgba(0,0,0,.25);animation:startGlow 3s ease-in-out infinite;white-space:nowrap}
@keyframes startGlow{50%{filter:brightness(1.12)}}
body[data-area="economic"] #banner .task{background:linear-gradient(#3C81F3,#1F5FD8);border:1px solid #1941A5;border-radius:3px;padding:5px 10px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;max-width:180px}
body[data-area="economic"] #banner .tray{margin-left:auto;background:linear-gradient(#0F8EEC,#0B76D6);border-left:1px solid #0A5AB0;padding:8px 12px;white-space:nowrap;align-self:stretch;display:flex;align-items:center;gap:10px}
body[data-area="economic"] #banner .balloon{position:absolute;right:12px;bottom:46px;background:#FFFFE1;color:#111;border:1px solid #333;border-radius:8px;padding:8px 12px;font:12px Tahoma,sans-serif;box-shadow:2px 3px 8px rgba(0,0,0,.35);animation:balloon 7s ease-in-out 1s both;max-width:260px}
@keyframes balloon{0%{opacity:0;transform:translateY(8px)}8%,80%{opacity:1;transform:none}100%{opacity:0;transform:translateY(8px);visibility:hidden}}
@media (max-width:560px){body[data-area="economic"] #banner .task:nth-of-type(3){display:none}}

/* ---------- POLITICAL · EDSA: road sign, LED txt brigade, billboards, skyline, jeepney ---------- */
body[data-area="political"]{--bg:#25282D;--panel:#FBF7EC;--ink:#1B1B1B;--muted:#4A4A4A;--line:#CFC6AE;--frame:#2B2F35;--past:#C1121F;--now:#1D4ED8;--next:#7C3AED;--main:#C1121F;--ok:#1B7A44;--bad:#B3261E;
  --display:"Anton",Impact,sans-serif;--body:"Archivo",Arial,sans-serif;--on-bg:#F5F5F0;--on-bg-muted:#C9CCD2;--on-bg-accent:#FFD43B;--chip-on:#FFD43B;--chip-on-ink:#1B1B1B;--ex-anim:flickerOn;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='1200' height='260' viewBox='0 0 1200 260'%3E%3Cg fill='%23181A1E'%3E%3Crect x='0' y='120' width='70' height='140'/%3E%3Crect x='80' y='60' width='60' height='200'/%3E%3Crect x='150' y='140' width='90' height='120'/%3E%3Crect x='250' y='30' width='55' height='230'/%3E%3Crect x='315' y='100' width='80' height='160'/%3E%3Crect x='410' y='70' width='50' height='190'/%3E%3Crect x='470' y='150' width='100' height='110'/%3E%3Crect x='585' y='20' width='65' height='240'/%3E%3Crect x='660' y='110' width='75' height='150'/%3E%3Crect x='745' y='50' width='60' height='210'/%3E%3Crect x='815' y='130' width='95' height='130'/%3E%3Crect x='920' y='80' width='55' height='180'/%3E%3Crect x='985' y='40' width='70' height='220'/%3E%3Crect x='1065' y='120' width='60' height='140'/%3E%3Crect x='1135' y='90' width='65' height='170'/%3E%3C/g%3E%3Cg fill='%23F5D27A' opacity='.55'%3E%3Crect x='92' y='80' width='6' height='8'/%3E%3Crect x='112' y='110' width='6' height='8'/%3E%3Crect x='262' y='60' width='6' height='8'/%3E%3Crect x='282' y='130' width='6' height='8'/%3E%3Crect x='598' y='50' width='6' height='8'/%3E%3Crect x='620' y='90' width='6' height='8'/%3E%3Crect x='758' y='80' width='6' height='8'/%3E%3Crect x='998' y='70' width='6' height='8'/%3E%3Crect x='1020' y='120' width='6' height='8'/%3E%3Crect x='425' y='95' width='6' height='8'/%3E%3C/g%3E%3Cg%3E%3Crect x='330' y='110' width='50' height='26' fill='%23C1121F'/%3E%3Crect x='830' y='140' width='64' height='30' fill='%231D4ED8'/%3E%3Crect x='160' y='150' width='70' height='28' fill='%23FFD43B'/%3E%3C/g%3E%3C/svg%3E"),repeating-linear-gradient(90deg,transparent 0 180px,rgba(255,212,59,.25) 180px 260px);
  background-repeat:repeat-x,repeat-x;background-position:0 100%,0 calc(100% - 4px);background-size:1100px 200px,100% 6px;background-attachment:fixed,fixed}
body[data-area="political"] h2,body[data-area="political"] h3,body[data-area="political"] header h1{text-transform:uppercase;letter-spacing:.02em}
body[data-area="political"] .frame{outline:0;border:10px solid #2B2F35;box-shadow:0 0 0 2px #5B6169,0 18px 30px -18px #000;position:relative;margin-bottom:58px;background-color:#FBF7EC;background-image:linear-gradient(180deg,rgba(255,246,200,.35),transparent 30%)}
body[data-area="political"] .frame::after{content:"";position:absolute;left:0;right:0;bottom:-60px;height:50px;background:linear-gradient(90deg,transparent 0 17%,#5B6169 17% 19.5%,transparent 19.5% 80.5%,#5B6169 80.5% 83%,transparent 83%);pointer-events:none}
body[data-area="political"] .frame::before{content:"";position:absolute;left:12%;right:12%;top:-22px;height:12px;background:radial-gradient(circle at 10% 50%,#FFF6C8 0 5px,#5B6169 5.5px 7px,transparent 7.5px) 0 0/25% 100% repeat-x;animation:lamp 5s infinite}
@keyframes lamp{0%,92%,100%{filter:none}94%{filter:brightness(.4)}96%{filter:none}97%{filter:brightness(.5)}}
@keyframes flickerOn{0%{opacity:0}20%{opacity:.8}25%{opacity:.2}40%{opacity:1}45%{opacity:.6}100%{opacity:1}}
body[data-area="political"] .ex{background:#FFFFFF;border:6px solid #2B2F35;border-radius:0;background-image:repeating-linear-gradient(180deg,transparent 0 22px,rgba(0,0,0,.03) 22px 23px)}
body[data-area="political"] .ex .label{background:#FFD43B;color:#1B1B1B;align-self:flex-start;padding:2px 6px}
body[data-area="political"] .plan{border-color:#FFD43B}
body[data-area="political"] .plan button{border-color:#FFD43B!important}
body[data-area="political"] #banner{flex-direction:column;align-items:stretch;gap:0;padding:0;background:#111}
body[data-area="political"] #banner .road{display:flex;align-items:center;gap:16px;flex-wrap:wrap;background:#0B6E3D;color:#fff;border-top:4px solid #fff;border-bottom:4px solid #fff;padding:10px max(16px,env(safe-area-inset-left,0px));font-family:"Overpass",Arial,sans-serif;font-weight:800;position:relative;overflow:hidden}
body[data-area="political"] #banner .sign{font-family:"Overpass",Arial,sans-serif;font-weight:800;font-size:30px;letter-spacing:.04em;border:3px solid #fff;padding:0 12px;border-radius:6px}
body[data-area="political"] #banner .exits{display:flex;gap:18px;flex-wrap:wrap;font-size:15px}
body[data-area="political"] #banner .led{overflow:hidden;white-space:nowrap;background:#0A0A0A;color:#FFB020;font-family:"VT323",monospace;font-size:22px;padding:4px 0;text-shadow:0 0 6px rgba(255,176,32,.8);border-bottom:2px solid #333}
body[data-area="political"] #banner .led span{display:inline-block;padding-left:100%;animation:marquee 26s linear infinite}
body[data-area="political"] #banner .street{position:relative;height:46px;background:linear-gradient(#2A2D32,#1E2024);overflow:hidden}
body[data-area="political"] #banner .street::after{content:"";position:absolute;left:0;right:0;top:50%;height:3px;background:repeating-linear-gradient(90deg,#FFD43B 0 40px,transparent 40px 80px);animation:lane 1.2s linear infinite}
@keyframes lane{to{background-position:-80px 0}}
body[data-area="political"] .jeep{position:absolute;bottom:4px;left:0;width:120px;height:42px;animation:drive 12s linear infinite;z-index:1}
@keyframes drive{from{transform:translateX(-140px)}to{transform:translateX(calc(100vw + 20px))}}
@keyframes marquee{to{transform:translateX(-100%)}}

/* ---------- CULTURAL · 2000s MP3 player ---------- */
body[data-area="cultural"]{--bg:#DDE3EA;--panel:#FFFFFF;--ink:#1D2129;--muted:#5A6270;--line:#C7CFD8;--frame:#2A2F36;--past:#D2335C;--now:#1F6FD1;--next:#7B3FBF;--main:#1F6FD1;--ok:#1B7A44;--bad:#B3261E;
  --display:"Source Sans 3","Myriad Pro",Arial,sans-serif;--body:"Source Sans 3","Myriad Pro",Arial,sans-serif;--radius:26px;--on-bg-accent:#1F6FD1;--chip-on:#1F6FD1;--ex-anim:popIn;
  background-image:linear-gradient(115deg,rgba(255,255,255,.75) 0 30%,transparent 30.2%),linear-gradient(180deg,#EEF2F6,#CBD3DC);background-attachment:fixed;font-size:15px}
body[data-area="cultural"] h1,body[data-area="cultural"] h2,body[data-area="cultural"] h3{font-weight:700;letter-spacing:-.01em}
body[data-area="cultural"] .frame{outline:0;border:1px solid #C3CBD4;background:linear-gradient(180deg,#FFFFFF,#EEF1F5);box-shadow:0 18px 40px -20px rgba(20,30,50,.45),inset 0 1px 0 #fff;position:relative;padding-top:58px}
body[data-area="cultural"] .frame::before{content:"▶  Now Playing";position:absolute;left:18px;right:18px;top:14px;height:30px;border-radius:6px 6px 0 0;border:3px solid #2A2F36;border-bottom:0;background:linear-gradient(#F3F7FB,#C9D5E2);font:700 15px "Source Sans 3",Arial,sans-serif;color:#1D2129;padding:3px 10px;box-sizing:border-box;text-align:center}
body[data-area="cultural"] .frame::after{content:"";position:absolute;right:30px;top:23px;width:22px;height:11px;border-radius:2px;background:linear-gradient(90deg,#3DBA4E 75%,#9AA3AD 75%);box-shadow:inset 0 0 0 1px #2E7D32}
body[data-area="cultural"] .ex,body[data-area="cultural"] .side,body[data-area="cultural"] .lesson,body[data-area="cultural"] .tnn,body[data-area="cultural"] .plan,body[data-area="cultural"] footer .desk{background:linear-gradient(180deg,#F7FBFF,#DDE9F5);border:3px solid #2A2F36;border-radius:6px}
body[data-area="cultural"] .ex{position:relative;padding-bottom:28px}
body[data-area="cultural"] .ex::after{content:"";position:absolute;left:16px;right:16px;bottom:12px;height:8px;border-radius:4px;border:1px solid #8FA3B8;background:linear-gradient(#78B4F0,#2F7BD1) 0 0/0% 100% no-repeat,linear-gradient(#FFFFFF,#E3E8EE);animation:track 8s linear infinite}
body[data-area="cultural"] .ex:nth-child(2)::after{animation-delay:-2s}body[data-area="cultural"] .ex:nth-child(3)::after{animation-delay:-4s}body[data-area="cultural"] .ex:nth-child(4)::after{animation-delay:-1s}body[data-area="cultural"] .ex:nth-child(5)::after{animation-delay:-5s}
@keyframes track{to{background-size:100% 100%,100% 100%}}
body[data-area="cultural"] .btn,body[data-area="cultural"] .chip{border-radius:999px}
body[data-area="cultural"] #banner{background:linear-gradient(#F3F7FB,#C9D5E2);color:#1D2129;border-bottom:3px solid #2A2F36;font-family:"Source Sans 3",Arial,sans-serif;font-weight:600}
body[data-area="cultural"] #banner .np{font-weight:700}
body[data-area="cultural"] #banner .prog{flex:1;min-width:140px;height:12px;border:1px solid #8FA3B8;border-radius:6px;background:linear-gradient(#78B4F0,#2F7BD1) 0 0/0% 100% no-repeat,linear-gradient(#FFFFFF,#E3E8EE);animation:track 30s linear infinite}
body[data-area="cultural"] #banner .eq{display:inline-flex;gap:3px;align-items:flex-end;height:16px}
body[data-area="cultural"] #banner .eq i{width:4px;background:#2F7BD1;animation:eq .9s ease-in-out infinite alternate}
body[data-area="cultural"] #banner .eq i:nth-child(2){animation-delay:-.3s}body[data-area="cultural"] #banner .eq i:nth-child(3){animation-delay:-.6s}body[data-area="cultural"] #banner .eq i:nth-child(4){animation-delay:-.15s}
@keyframes eq{from{height:4px}to{height:16px}}

/* ---------- ENVIRONMENTAL · inside a bus in heavy rain, emergency alerts ---------- */
body[data-area="environmental"]{--bg:#0E1420;--panel:#2A2430;--ink:#EEE8F4;--muted:#B9B0C4;--line:#4A4152;--frame:#E5413A;--past:#FF8A80;--now:#82B1FF;--next:#A5D6A7;--main:#FF8A80;--ok:#A5D6A7;--bad:#FF8A80;
  --display:"Roboto",Arial,sans-serif;--body:"Roboto",Arial,sans-serif;--radius:26px;--on-bg:#F1F3F8;--on-bg-muted:#BFC6D4;--on-bg-accent:#FFB4A9;--chip-on:#E5413A;--chip-on-ink:#fff;--ex-anim:bubbleIn;
  background-image:radial-gradient(circle at 12% 30%,rgba(255,170,60,.35) 0 18px,transparent 60px),radial-gradient(circle at 78% 22%,rgba(255,60,60,.3) 0 14px,transparent 50px),radial-gradient(circle at 55% 65%,rgba(255,220,150,.25) 0 22px,transparent 70px),radial-gradient(circle at 30% 80%,rgba(120,180,255,.22) 0 16px,transparent 55px),radial-gradient(circle at 90% 70%,rgba(255,200,80,.3) 0 12px,transparent 48px),linear-gradient(180deg,#0B1220,#18233A 60%,#0E1420);
  background-attachment:fixed;color-scheme:dark}
body[data-area="environmental"] #fx{display:block;z-index:0;background:repeating-linear-gradient(100deg,transparent 0 9px,rgba(190,210,255,.10) 9px 10px),radial-gradient(circle at 20% 30%,rgba(255,255,255,.18) 0 3px,transparent 4px),radial-gradient(circle at 70% 60%,rgba(255,255,255,.15) 0 2.5px,transparent 3.5px),radial-gradient(circle at 45% 80%,rgba(255,255,255,.14) 0 3px,transparent 4px);background-size:220px 220px,140px 180px,190px 150px,160px 210px;animation:rainfall .45s linear infinite,flash 9s 3s infinite}
body[data-area="environmental"] .wrap{position:relative;z-index:1}
@keyframes rainfall{to{background-position:-40px 220px,0 180px,0 150px,0 210px}}
@keyframes flash{0%,95%,100%{box-shadow:inset 0 0 0 9999px rgba(255,255,255,0)}96%{box-shadow:inset 0 0 0 9999px rgba(255,255,255,.18)}97%{box-shadow:inset 0 0 0 9999px rgba(255,255,255,0)}98%{box-shadow:inset 0 0 0 9999px rgba(255,255,255,.12)}}
body[data-area="environmental"]::before{content:"";position:fixed;inset:0;pointer-events:none;z-index:0;background:linear-gradient(90deg,#05080E 0 1.5%,transparent 1.5% 33%,#05080E 33% 34%,transparent 34% 66%,#05080E 66% 67%,transparent 67% 98.5%,#05080E 98.5%);opacity:.65}
body[data-area="environmental"] .frame{outline:0;border:0;background:#2A2430;box-shadow:0 20px 50px -20px rgba(0,0,0,.8);position:relative;padding-top:64px}
body[data-area="environmental"] .frame::before{content:"Emergency alert: Extreme";position:absolute;left:22px;top:20px;padding-left:40px;color:#F4EEF8;font:500 20px "Roboto",Arial,sans-serif;background:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 32 28'%3E%3Cpath d='M16 0 32 28H0Z' fill='%23E5413A'/%3E%3Crect x='14.5' y='9' width='3' height='10' rx='1.5' fill='%23fff'/%3E%3Ccircle cx='16' cy='23' r='1.8' fill='%23fff'/%3E%3C/svg%3E") 0 50%/30px 26px no-repeat;line-height:28px}
body[data-area="environmental"] .ex,body[data-area="environmental"] .side,body[data-area="environmental"] .lesson,body[data-area="environmental"] .tnn,body[data-area="environmental"] .plan,body[data-area="environmental"] footer .desk{background:#332C3A;border:1px solid #463E4F;border-radius:22px}
body[data-area="environmental"] .ex{position:relative;padding-bottom:44px}
body[data-area="environmental"] .ex::after{content:"OK";position:absolute;left:0;right:0;bottom:12px;text-align:center;font:500 15px "Roboto",Arial,sans-serif;color:#F4EEF8;letter-spacing:.04em}
body[data-area="environmental"] .ex .label{color:#FFB4A9}
@keyframes bubbleIn{0%{opacity:0;transform:scale(.92)}100%{opacity:1;transform:none}}
body[data-area="environmental"] .opt,body[data-area="environmental"] .gb-form input,body[data-area="environmental"] .gb-form textarea,body[data-area="environmental"] .gb-form select{background:#332C3A}
body[data-area="environmental"] #banner{flex-direction:column;align-items:stretch;gap:0;padding:0;background:#05080E;position:relative}
body[data-area="environmental"] #banner .dest{display:flex;align-items:center;gap:12px;padding:8px max(16px,env(safe-area-inset-left,0px));background:#111;border-bottom:2px solid #222}
body[data-area="environmental"] #banner .busno{font:700 22px "VT323",monospace;color:#FF8C1A;text-shadow:0 0 6px rgba(255,140,26,.8);border:1px solid #333;padding:0 8px}
body[data-area="environmental"] #banner .led{flex:1;overflow:hidden;white-space:nowrap;font:22px "VT323",monospace;color:#FF8C1A;text-shadow:0 0 6px rgba(255,140,26,.8)}
body[data-area="environmental"] #banner .led span{display:inline-block;padding-left:100%;animation:marquee 18s linear infinite}
body[data-area="environmental"] #banner .modal{align-self:center;width:min(560px,92%);margin:16px 0;background:#2A2430;border-radius:28px;padding:20px 24px 12px;color:#F4EEF8;font-family:"Roboto",Arial,sans-serif;animation:alertIn .6s ease-out both,buzz .5s .6s 2;box-shadow:0 20px 40px rgba(0,0,0,.6)}
body[data-area="environmental"] #banner .modal .t{display:flex;align-items:center;gap:12px;font-size:20px;font-weight:500}
body[data-area="environmental"] #banner .modal p{margin:12px 0 6px;font-size:15.5px;line-height:1.45;color:#E2DBE9}
body[data-area="environmental"] #banner .modal .ok{display:block;margin:6px auto 4px;background:none;border:0;color:#F4EEF8;font:500 15px "Roboto",Arial,sans-serif;cursor:pointer}
@keyframes alertIn{from{transform:translateY(-40px);opacity:0}to{transform:none;opacity:1}}
@keyframes buzz{0%,100%{transform:none}20%{transform:translateX(-5px)}40%{transform:translateX(5px)}60%{transform:translateX(-3px)}80%{transform:translateX(3px)}}

/* ---------- OTHERS · Philippine passport data page (museum specimen) ---------- */
body[data-area="others"]{--bg:#F4E9EE;--panel:#FBF5F4;--ink:#2B2340;--muted:#5D5470;--line:#D9C9D6;--frame:#2F3A8F;--past:#B3263B;--now:#2F3A8F;--next:#6A3FA0;--main:#2F3A8F;--ok:#2E6B3A;--bad:#B3263B;
  --display:"Source Sans 3",Arial,sans-serif;--body:"Source Sans 3",Arial,sans-serif;--radius:4px;--on-bg-accent:#2F3A8F;--chip-on:#2F3A8F;--ex-anim:stampIn;
  background-image:repeating-radial-gradient(circle at 15% 25%,rgba(214,120,160,.10) 0 1px,transparent 1px 7px),repeating-radial-gradient(circle at 85% 70%,rgba(90,120,210,.10) 0 1px,transparent 1px 8px),repeating-linear-gradient(35deg,rgba(150,110,200,.05) 0 1px,transparent 1px 6px),linear-gradient(160deg,#F9E3EC,#E9E6F6 50%,#F3E8EF);background-attachment:fixed;font-size:15px}
body[data-area="others"] h1,body[data-area="others"] h2,body[data-area="others"] h3{font-weight:700;letter-spacing:.01em}
body[data-area="others"] .room-head h2{text-transform:uppercase;letter-spacing:.06em;font-size:clamp(26px,4.2vw,42px)}
body[data-area="others"] .frame,body[data-area="others"] footer .desk,body[data-area="others"] .plan,body[data-area="others"] .tnn{outline:0;border:1px solid #D9C9D6;box-shadow:0 10px 24px -14px rgba(60,40,90,.45);position:relative;
  background-color:#FBF5F4;background-image:repeating-radial-gradient(circle at 0 100%,rgba(47,58,143,.06) 0 1px,transparent 1px 9px),repeating-radial-gradient(circle at 100% 0,rgba(179,38,59,.05) 0 1px,transparent 1px 9px)}
body[data-area="others"] .frame{padding-top:46px}
body[data-area="others"] .frame::before{content:"REPUBLIKA NG PILIPINAS  |  REPUBLIC OF THE PHILIPPINES";position:absolute;left:0;right:0;top:0;padding:7px 14px 7px 40px;font:600 11.5px "Source Sans 3",Arial,sans-serif;letter-spacing:.14em;color:#2B2340;border-bottom:1px solid #D9C9D6;
  background:linear-gradient(180deg,#0038A8 0 50%,#CE1126 50%) 12px 50%/18px 11px no-repeat}
body[data-area="others"] .frame::after{content:"SPECIMEN · MUSEUM EXHIBIT";position:absolute;right:16px;bottom:10px;font:700 12px "Source Sans 3",Arial,sans-serif;letter-spacing:.2em;color:rgba(179,38,59,.45);pointer-events:none}
body[data-area="others"] .wing-top .frame h3::before,body[data-area="others"] .wing-top .frame .cat::before{display:block;font:italic 400 11px "Source Sans 3",Arial,sans-serif;letter-spacing:0;color:#5D5470;text-transform:none}
body[data-area="others"] .wing-top .frame .cat::before{content:"Galeriya / Gallery"}
body[data-area="others"] .wing-top .frame h3::before{content:"Pangalan / Name"}
body[data-area="others"] .ex{background:rgba(251,245,244,.92);border:3px double var(--stamp,#2F3A8F);border-radius:14px;color:var(--ink)}
body[data-area="others"] .ex .label,body[data-area="others"] .ex .holo,body[data-area="others"] .ex .app{font-family:"Special Elite","Courier New",monospace}
body[data-area="others"] .ex .txt{font-family:"Courier Prime","Courier New",monospace;font-size:14.5px}
body[data-area="others"] .ex:nth-child(odd){transform:rotate(-1.2deg)}
body[data-area="others"] .ex:nth-child(even){transform:rotate(1deg)}
body[data-area="others"] .ex:nth-child(3n){--stamp:#B3263B}
body[data-area="others"] .ex:nth-child(3n+2){--stamp:#2E6B3A}
body[data-area="others"] .ex .label{color:var(--stamp,#2F3A8F);letter-spacing:.14em}
body[data-area="others"] .ex:hover{transform:rotate(0) translateY(-2px)}
@keyframes stampIn{0%{opacity:0;transform:scale(1.8) rotate(-8deg)}70%{opacity:1;transform:scale(.97) rotate(-1deg)}100%{transform:rotate(-1.2deg)}}
body[data-area="others"] .gallery .ex:nth-child(even){animation-name:stampIn2}
@keyframes stampIn2{0%{opacity:0;transform:scale(1.8) rotate(8deg)}70%{opacity:1;transform:scale(.97) rotate(2deg)}100%{transform:rotate(1deg)}}
body[data-area="others"] .mrz{font-family:"Courier Prime","Courier New",monospace;font-weight:700;background:#FBF5F4;color:#2B2340}
body[data-area="others"] #banner{padding:0;display:block;min-height:0;background:#F9E3EC}
body[data-area="others"] #banner svg{display:block;width:100%;height:90px}
body[data-area="others"] #banner .flagline{display:flex;justify-content:space-between;gap:10px;flex-wrap:wrap;padding:8px max(16px,env(safe-area-inset-left,0px));font:600 12px "Source Sans 3",Arial,sans-serif;letter-spacing:.16em;color:#2B2340;background:rgba(255,255,255,.6);border-bottom:1px solid #D9C9D6}
body[data-area="others"] .wave{animation:wave 6s ease-in-out infinite alternate;transform-origin:50% 50%}
@keyframes wave{to{transform:translateY(4px) skewY(-1deg)}}
body[data-area="economic"] .room-head,body[data-area="economic"] header .sub,body[data-area="economic"] .plan-note,body[data-area="economic"] .bglabel>.eyebrow,body[data-area="economic"] .note,body[data-area="economic"] .colophon{background:rgba(8,40,120,.55);border-radius:6px;padding:8px 12px}
body[data-area="economic"] .room-head{margin-inline:0}
body[data-area="political"] .room-head,body[data-area="political"] header .sub{background:rgba(37,40,45,.82);border-radius:4px}
body[data-area="environmental"] .room-head,body[data-area="environmental"] header .sub{background:rgba(14,20,32,.7);border-radius:12px}

/* Look picker + classic museum look (always used in the Pangunahing Bulwagan) */
.lookpick{display:flex;align-items:center;gap:8px;flex-wrap:wrap}
.lookpick label{font-size:12px;font-weight:700;letter-spacing:.1em;text-transform:uppercase;color:var(--on-bg-muted)}
.lookpick select{background:var(--panel);color:var(--ink);border:1px solid var(--line);padding:7px 10px;font-size:14px;border-radius:var(--radius);max-width:100%}
body[data-area="museo"]{--display:"Gloock","Playfair Display",Georgia,serif;--body:"Hanken Grotesk",system-ui,sans-serif;--on-bg-accent:var(--past)}
body[data-area="museo"] .room-head h2{color:var(--room)}
body[data-area="museo"] #banner{padding:0;min-height:96px;display:block}
body[data-area="museo"] #banner svg{display:block;width:100%;height:96px}


/* ================= Ambient motion per look (switch off with the Animations button) ================= */
html.calm *,html.calm *::before,html.calm *::after{animation:none!important;transition:none!important}
.motionbtn{background:var(--panel);color:var(--ink);border:1px solid var(--line);padding:7px 10px;font-size:13px;font-weight:600;border-radius:var(--radius)}
.fx::before,.fx::after{content:"";position:absolute;inset:0}

/* Classic museo: confetti drifting down, shimmering title, light sweep on frames */
body[data-area="museo"] #fx{display:block}
body[data-area="museo"] #fx::before{background:radial-gradient(circle,var(--f1) 0 3px,transparent 3.5px) 0 0/170px 210px,radial-gradient(circle,var(--f3) 0 3px,transparent 3.5px) 60px 40px/230px 190px,radial-gradient(circle,var(--f5) 0 2.5px,transparent 3px) 120px 90px/200px 240px,radial-gradient(circle,var(--f4) 0 2.5px,transparent 3px) 30px 140px/260px 220px;opacity:.55;animation:confetti 14s linear infinite}
@keyframes confetti{to{background-position:40px 210px,20px 230px,160px 330px,-10px 360px}}
body[data-area="museo"] header h1 .pin{background:linear-gradient(90deg,var(--past),var(--f2),var(--past));background-size:200% 100%;-webkit-background-clip:text;background-clip:text;color:transparent;animation:shimmer 5s linear infinite}
@keyframes shimmer{to{background-position:200% 0}}
body[data-area="museo"] .frame{background-image:linear-gradient(110deg,transparent 40%,rgba(255,255,255,.55) 50%,transparent 60%);background-size:250% 100%;background-repeat:no-repeat;animation:sheen 7s ease-in-out infinite}
@keyframes sheen{0%,60%{background-position:150% 0}100%{background-position:-60% 0}}

/* Nokia: moving LCD refresh line, backlight pulse, flickering pixels */
body[data-area="social"] #fx{display:block}
body[data-area="social"] #fx::before{background:linear-gradient(180deg,transparent 0,rgba(29,42,8,.10) 48%,rgba(29,42,8,.16) 50%,transparent 52%);background-size:100% 260px;animation:refresh 3.5s linear infinite}
@keyframes refresh{to{background-position:0 260px}}
body[data-area="social"] #banner{animation:backlight 4s ease-in-out infinite}
@keyframes backlight{50%{box-shadow:inset 0 0 0 999px rgba(184,219,76,.06)}}
body[data-area="social"] .ex .lcd{animation:blinkSoft 2.4s steps(2,start) infinite}
@keyframes blinkSoft{50%{opacity:.55}}
body[data-area="social"] header h1{animation:jitter 6s steps(1) infinite}
@keyframes jitter{0%,96%,100%{transform:none}97%{transform:translateX(2px)}98%{transform:translateX(-2px)}}

/* Windows XP: drifting clouds, pulsing start, loading bar in each window title */
body[data-area="economic"]{animation:clouds 60s linear infinite}
@keyframes clouds{from{background-position:0 0,0 0,0 0,0 0,0 0}to{background-position:900px 0,-700px 0,0 0,0 0,0 0}}
body[data-area="economic"] .side,body[data-area="economic"] .ex{background-image:linear-gradient(90deg,#3A8E3A 0 0) ;background-repeat:no-repeat;background-size:0 3px;background-position:0 100%;animation:loadbar 4s ease-in-out infinite}
@keyframes loadbar{0%{background-size:0 3px}70%,100%{background-size:100% 3px}}
body[data-area="economic"] .frame{animation:winFocus 9s ease-in-out infinite}
@keyframes winFocus{0%,100%{box-shadow:2px 4px 14px rgba(0,0,0,.35)}50%{box-shadow:2px 6px 22px rgba(0,0,0,.5)}}

/* EDSA: headlight beams sweeping, twinkling skyline windows, billboard lights */
body[data-area="political"] #fx{display:block;z-index:0}
body[data-area="political"] .wrap{position:relative;z-index:1}
body[data-area="political"] #fx::before{top:auto;height:220px;background:radial-gradient(circle,rgba(255,226,140,.9) 0 2px,transparent 3px) 0 0/97px 41px,radial-gradient(circle,rgba(255,226,140,.8) 0 1.5px,transparent 2.5px) 40px 20px/131px 53px;animation:windows 3s steps(3) infinite;opacity:.45}
@keyframes windows{33%{opacity:.25}66%{opacity:.55}}
body[data-area="political"] #fx::after{top:auto;height:160px;background:radial-gradient(ellipse 160px 40px at 50% 100%,rgba(255,240,180,.28),transparent 70%) 0 100%/600px 160px repeat-x;animation:beam 6s linear infinite}
@keyframes beam{to{background-position:600px 100%}}
body[data-area="political"] .frame{animation:billboard 7s ease-in-out infinite}
@keyframes billboard{0%,100%{box-shadow:0 0 0 2px #5B6169,0 18px 30px -18px #000}50%{box-shadow:0 0 0 2px #5B6169,0 0 40px rgba(255,240,180,.25),0 18px 30px -18px #000}}

/* MP3: floating notes, glossy sheen sweeping, pulsing play icon */
body[data-area="cultural"] #fx{display:block}
body[data-area="cultural"] #fx::before,body[data-area="cultural"] #fx::after{inset:auto;bottom:-40px;font-size:34px;color:rgba(31,111,209,.35);white-space:pre;animation:notes 9s linear infinite}
body[data-area="cultural"] #fx::before{content:"♪            ♫                 ♪           ♬";left:5%}
body[data-area="cultural"] #fx::after{content:"♫         ♪              ♬          ♪";left:20%;animation-delay:-4.5s;color:rgba(210,51,92,.3)}
@keyframes notes{0%{transform:translateY(0);opacity:0}10%{opacity:1}100%{transform:translateY(-110vh);opacity:0}}
body[data-area="cultural"] .frame{background-image:linear-gradient(115deg,transparent 35%,rgba(255,255,255,.9) 48%,transparent 60%),linear-gradient(180deg,#FFFFFF,#EEF1F5);background-size:260% 100%,100% 100%;background-repeat:no-repeat;animation:gloss 6s ease-in-out infinite}
@keyframes gloss{0%,55%{background-position:160% 0,0 0}100%{background-position:-60% 0,0 0}}
body[data-area="cultural"] #banner .np{animation:pulsePlay 1.2s ease-in-out infinite alternate}
@keyframes pulsePlay{to{color:#1F6FD1}}

/* Bus in the rain: the bus sways, city lights drift past the window, wipers */
body[data-area="environmental"] .wrap{animation:sway2 5s ease-in-out infinite}
@keyframes sway2{0%,100%{transform:translateY(0)}50%{transform:translateY(2px) rotate(.08deg)}}
body[data-area="environmental"]{animation:passing 20s linear infinite}
@keyframes passing{to{background-position:-800px 0,-600px 0,-900px 0,-700px 0,-1000px 0,0 0}}
body[data-area="environmental"] #banner .dest{position:relative;overflow:hidden}
body[data-area="environmental"] #banner .dest::after{content:"";position:absolute;left:50%;bottom:-60px;width:4px;height:120px;background:#000;transform-origin:50% 100%;animation:wiper 2.4s ease-in-out infinite;opacity:.8}
@keyframes wiper{0%,100%{transform:rotate(-70deg)}50%{transform:rotate(70deg)}}

/* Passport: holographic shimmer over each page, waving flag, stamps thud in */
body[data-area="others"] .frame{background-image:linear-gradient(115deg,transparent 30%,rgba(255,170,220,.25) 42%,rgba(150,220,255,.28) 50%,rgba(255,240,170,.25) 58%,transparent 70%),repeating-radial-gradient(circle at 0 100%,rgba(47,58,143,.06) 0 1px,transparent 1px 9px),repeating-radial-gradient(circle at 100% 0,rgba(179,38,59,.05) 0 1px,transparent 1px 9px);background-size:300% 100%,auto,auto;animation:holo 6s ease-in-out infinite}
@keyframes holo{0%,100%{background-position:120% 0,0 0,0 0}50%{background-position:-20% 0,0 0,0 0}}
body[data-area="others"] .ex .label{animation:inkfade 4s ease-in-out infinite alternate}
@keyframes inkfade{to{opacity:.75}}

body[data-area="others"] .ex{overflow-wrap:anywhere}
body[data-area="others"] .ex .label{letter-spacing:.06em}
html,body{overflow-x:clip}
/* 2000s OPM playlist, shown in the MP3 player look */
.playlist{display:none}
body[data-area="cultural"] .playlist{display:grid;grid-template-columns:minmax(0,1fr);gap:10px;background:linear-gradient(180deg,#FFFFFF,#EEF1F5);border:1px solid #C3CBD4;border-radius:26px;padding:18px;box-shadow:0 18px 40px -20px rgba(20,30,50,.45)}
@media (min-width:860px){body[data-area="cultural"] .playlist{grid-template-columns:minmax(0,1fr) minmax(0,1fr);column-gap:22px;align-items:start}}
.pl-left{display:flex;flex-direction:column;gap:12px}
.pl-screen{border:3px solid #2A2F36;border-radius:8px;overflow:hidden;background:linear-gradient(#F7FBFF,#DDE9F5)}
.pl-head{display:flex;justify-content:space-between;align-items:center;border-bottom:1px solid #9FB0C2;background:linear-gradient(#F3F7FB,#C9D5E2);padding:5px 10px;font-weight:700}
.pl-bat{width:24px;height:12px;border-radius:2px;background:linear-gradient(90deg,#3DBA4E 75%,#9AA3AD 75%);box-shadow:inset 0 0 0 1px #2E7D32}
.pl-now{padding:12px 14px 6px;display:flex;flex-direction:column;gap:2px}
.pl-now b{font-size:20px;line-height:1.2}
.pl-now span{color:#5A6270}
.pl-bar{padding:4px 14px 14px}
.pl-bar span{display:block;height:10px;border:1px solid #8FA3B8;border-radius:5px;background:linear-gradient(#78B4F0,#2F7BD1) 0 0/0% 100% no-repeat,linear-gradient(#FFFFFF,#E3E8EE)}
.pl-bar span.run{animation:track var(--dur,18s) linear forwards}
.pl-list{margin:0;padding:0;list-style:none;display:flex;flex-direction:column;border:2px solid #2A2F36;border-radius:6px;overflow:hidden;background:#F7FBFF}
.pl-list button{width:100%;display:grid;grid-template-columns:28px minmax(0,1fr) auto;gap:8px;align-items:center;text-align:left;background:none;border:0;border-top:1px solid #D6DEE7;padding:7px 10px;font-size:14px;color:#1D2129}
.pl-list li:first-child button{border-top:0}
.pl-list button:hover{background:#E7F0FA}
.pl-list button[aria-current="true"]{background:linear-gradient(#5CA0EC,#2F7BD1);color:#fff}
.pl-list small{opacity:.75}
.pl-ctrl{display:flex;gap:10px;justify-content:center}
.pl-ctrl button{width:52px;height:52px;border-radius:50%;border:1px solid #B9C3CE;background:radial-gradient(circle at 50% 35%,#FFFFFF,#DCE2E9);font-size:18px;color:#2A2F36;box-shadow:0 3px 8px rgba(20,30,50,.18)}
.pl-ctrl button:active{transform:translateY(1px)}
.pl-note{font-size:12.5px;color:#5A6270;text-align:center}

/* Exhibit tag per look */
body[data-area="social"] .ex .label,body[data-area="social"] .cat{color:#1D2A08}
.tag{align-self:flex-start;font-size:11.5px;font-weight:700;padding:4px 9px;line-height:1.2;letter-spacing:.03em}
body[data-area="museo"] .tag{font-family:var(--display);font-weight:400;font-size:13px;border:1px solid var(--frame);color:var(--frame);background:var(--panel)}
body[data-area="museo"] .tag[data-era="0"]{color:var(--past);border-color:var(--past)}
body[data-area="museo"] .tag[data-era="1"]{color:var(--now);border-color:var(--now)}
body[data-area="museo"] .tag[data-era="2"]{color:var(--next);border-color:var(--next)}
body[data-area="social"] .tag{font-family:"VT323",monospace;font-weight:400;font-size:19px;padding:3px 8px 2px;background:#1D2A08;color:#B8DB4C;border:2px solid #1D2A08;letter-spacing:.04em}
body[data-area="economic"] .tag{font:11.5px Tahoma,sans-serif;color:#0A246A;background:linear-gradient(#FFFFFF,#E3E1D6);border:1px solid #7F9DB9;border-radius:3px}
body[data-area="political"] .tag{font-family:"Overpass",Arial,sans-serif;font-weight:800;font-size:12px;letter-spacing:.06em;background:#0B6E3D;color:#fff;border:2px solid #fff;box-shadow:0 0 0 1.5px #0B6E3D;border-radius:4px}
body[data-area="cultural"] .tag{font-family:"Source Sans 3",Arial,sans-serif;font-size:12.5px;color:#fff;background:linear-gradient(#5CA0EC,#2F7BD1);border-radius:999px;padding:4px 11px}
body[data-area="environmental"] .tag{font-family:"Roboto",Arial,sans-serif;font-weight:500;font-size:12px;color:#fff;border-radius:6px;background:#FF9500}
body[data-area="environmental"] .tag[data-era="1"]{background:#E5413A}
body[data-area="environmental"] .tag[data-era="2"]{background:#6D4C9F}
body[data-area="others"] .tag{font-family:"Special Elite","Courier New",monospace;font-weight:400;font-size:13px;text-transform:uppercase;letter-spacing:.08em;color:var(--stamp,#2F3A8F);border:2px solid var(--stamp,#2F3A8F);border-radius:3px;transform:rotate(-3deg);background:transparent}

/* Hero title: popcorn letters, sticker with starburst, flipping tagline */
header h1.hero{display:flex;flex-wrap:wrap;align-items:center;column-gap:.22em;row-gap:0;font-size:clamp(44px,8.2vw,104px);line-height:.95;letter-spacing:-.02em}
.h-what{display:inline-block;animation:slideUp .7s cubic-bezier(.2,.9,.3,1.2) both}
.h-pop{display:inline-flex;color:var(--on-bg-accent)}
.h-pop i{font-style:normal;display:inline-block;animation:popIn2 .55s cubic-bezier(.2,1.6,.4,1) both,popcorn 3.2s ease-in-out infinite;animation-delay:calc(var(--i) * 70ms + .25s),calc(var(--i) * 180ms + 1.2s)}
@keyframes slideUp{from{opacity:0;transform:translateY(40%)}to{opacity:1;transform:none}}
@keyframes popIn2{0%{opacity:0;transform:translateY(60%) scale(.2) rotate(-20deg)}100%{opacity:1;transform:none}}
@keyframes popcorn{0%,80%,100%{transform:none}86%{transform:translateY(-14%) rotate(-6deg) scale(1.08)}92%{transform:translateY(0) rotate(3deg)}}
.h-sticker{position:relative;display:inline-grid;place-items:center;margin:.06em .1em 0;font-size:.9em;animation:stickerIn .8s 1s cubic-bezier(.2,1.5,.4,1) both}
.h-sticker .burst{position:absolute;left:50%;top:50%;width:calc(100% + .9em);height:2.1em;transform:translate(-50%,-50%);fill:var(--burst,var(--f3));opacity:.9;animation:burstPulse 2.6s ease-in-out infinite;z-index:0;pointer-events:none}
@keyframes burstPulse{0%,100%{transform:translate(-50%,-50%) scale(1) rotate(0)}50%{transform:translate(-50%,-50%) scale(1.07) rotate(4deg)}}
.h-what,.h-pop{position:relative;z-index:2}
.h-sticker{isolation:isolate;z-index:1}
.h-pinoy{position:relative;z-index:1;display:inline-block;padding:.08em .28em .14em;background:var(--chip-on);color:var(--chip-on-ink);transform:rotate(-4deg);box-shadow:.06em .06em 0 var(--ink);border-radius:var(--radius);animation:wobble 4s 2s ease-in-out infinite}
@keyframes stickerIn{0%{opacity:0;transform:scale(2.2) rotate(18deg)}100%{opacity:1;transform:none}}
@keyframes spin{to{transform:rotate(360deg)}}
@keyframes wobble{0%,100%{transform:rotate(-4deg)}50%{transform:rotate(2deg) scale(1.03)}}
.tagline{position:relative;z-index:5;margin-top:clamp(22px,3.4vw,44px);width:fit-content;max-width:100%;padding:8px 14px;background:var(--panel);color:var(--ink);border:1px solid var(--line);border-radius:var(--radius);box-shadow:0 6px 18px -8px rgba(0,0,0,.35);font-size:clamp(15px,1.9vw,19px);display:flex;flex-wrap:wrap;align-items:baseline;gap:.35em}
.tagline .tg-l{color:color-mix(in srgb,var(--ink) 60%,transparent)!important}.tagline b{color:var(--room,var(--past))!important}.tagline .tg-arrow{color:var(--ink)!important}
.tagline .tg-l{font-size:.72em;font-weight:700;letter-spacing:.14em;text-transform:uppercase;color:var(--on-bg-muted)}
.tagline b{display:inline-block;color:var(--on-bg-accent);font-family:var(--display)}
.tagline b.flip{animation:flip .5s ease-out both}
.tagline .tg-arrow{color:var(--on-bg-muted)}
@keyframes flip{0%{opacity:0;transform:rotateX(90deg) translateY(-6px)}100%{opacity:1;transform:none}}
body[data-area="museo"]{--burst:var(--f3);--chip-on:var(--past);--chip-on-ink:#fff}
body[data-area="social"]{--burst:#1D2A08}
body[data-area="social"] .h-pinoy{box-shadow:.06em .06em 0 #1D2A08}
body[data-area="economic"]{--burst:#FFD43B}
body[data-area="economic"] .h-pinoy{background:linear-gradient(180deg,#5EB75A,#2F8A2C);font-style:italic;border-radius:0 .3em .3em 0}
body[data-area="political"]{--burst:#FFD43B}
body[data-area="political"] .h-pinoy{background:#0B6E3D;color:#fff;border:.05em solid #fff}
body[data-area="cultural"]{--burst:#78B4F0}
body[data-area="cultural"] .h-pinoy{border-radius:.4em}
body[data-area="environmental"]{--burst:#E5413A}
body[data-area="environmental"] .h-pinoy{border-radius:.3em;box-shadow:none}
body[data-area="others"]{--burst:#FCD116}
body[data-area="others"] .h-pinoy{background:#2F3A8F;color:#FBF5F4}

</style>
</head>
<body>

<div class="fx" id="fx" aria-hidden="true"></div>
<div class="wrap">
  <div id="banner"></div>

  <header class="entrance">
    <div style="display:flex;flex-direction:column;gap:10px">
      <span class="eyebrow">MO-HUM080 · Mabuhay! Welcome to the museum</span>
      <h1 class="hero" aria-label="What's Poppin', Pinoy?">
        <span class="h-what" aria-hidden="true">What's</span>
        <span class="h-pop" id="heroPop" aria-hidden="true">Poppin'</span>
        <span class="h-sticker" aria-hidden="true"><svg class="burst" viewBox="0 0 100 100" preserveAspectRatio="none"><polygon points="50,0 58,22 80,10 72,33 98,32 78,48 98,64 72,66 80,90 58,78 50,100 42,78 20,90 28,66 2,64 22,48 2,32 28,33 20,10 42,22"/></svg><span class="h-pinoy">Pinoy?</span></span>
      </h1>
      <p class="tagline" aria-live="polite"><span class="tg-l">Noon</span> <b id="tgA">Friendster</b> <span class="tg-arrow">→</span> <span class="tg-l">Ngayon</span> <b id="tgB">TikTok</b> <span class="tg-arrow">→</span> <span class="tg-l">Bukas</span> <b id="tgC">AI friends</b></p>
    </div>
    <div class="sub">
      <span class="bay" lang="tl" aria-label="Pinoy, written in Baybayin">ᜉᜒᜈᜓᜌ᜔</span>
      <p>The past, present and future of Philippine popular culture. Walk from the 2000s to today, climb up to 2030, then test yourself in the Palaruan. Pick a museum look to see the rooms in a 2000s style.</p>
      <div class="lookpick">
        <label for="themePick">Museum look</label>
        <select id="themePick">
          <option value="museo">Museo · classic fiesta</option>
          <option value="match">Match the gallery I pick</option>
          <option value="social">Nokia 3310</option>
          <option value="economic">Windows XP desktop</option>
          <option value="political">EDSA billboards</option>
          <option value="cultural">MP3 player</option>
          <option value="environmental">Bus in the rain</option>
          <option value="others">Passport</option>
        </select>
        <button class="motionbtn" id="motionBtn" type="button" aria-pressed="true">Animations: On</button>
      </div>
      <p class="themeline" id="themeLine"></p>
    </div>
  </header>

  <nav aria-label="Museum floor plan">
    <div class="plan" id="plan">
      <button class="g1" data-room="left-wing" style="--rc:var(--past)"><span class="here">Nandito ka · You are here</span><span class="rname">Kaliwang Pakpak</span><span class="rsub">Left Wing · The 2000s (2000–2010)</span></button>
      <button class="g1" data-room="main" style="--rc:var(--main)"><span class="here">Nandito ka · You are here</span><span class="rname">Pangunahing Bulwagan</span><span class="rsub">Main Display · Noon, Ngayon at Bukas</span></button>
      <button class="g1" data-room="right-wing" style="--rc:var(--now)"><span class="here">Nandito ka · You are here</span><span class="rname">Kanang Pakpak</span><span class="rsub">Right Wing · The Present Time</span></button>
      <button class="f2 wide" data-room="future" style="--rc:var(--next)"><span class="floor">2F</span><span class="here">Nandito ka · You are here</span><span class="rname">Ang Hinaharap</span><span class="rsub">Second Floor · Philippine pop culture in 2030</span></button>
      <button class="f2" data-room="palaruan" style="--rc:var(--f2)"><span class="floor">2F</span><span class="here">Nandito ka · You are here</span><span class="rname">Palaruan</span><span class="rsub">Games, quiz and guestbook</span></button>
    </div>
    <div class="plan-note"><span class="eyebrow">Mapa ng museo · Floor plan</span><span class="eyebrow">Tap a room to walk in</span></div>
  </nav>

  <aside class="playlist" id="playlist" aria-label="2000s OPM playlist">
    <div class="pl-left">
      <div class="pl-screen">
        <div class="pl-head"><span>▶ Playlist · 2000s OPM</span><span class="pl-bat" aria-hidden="true"></span></div>
        <div class="pl-now" id="plNow"></div>
        <div class="pl-bar"><span id="plBar"></span></div>
      </div>
      <div class="pl-ctrl">
        <button type="button" id="plPrev" aria-label="Previous song">⏮</button>
        <button type="button" id="plPlay" aria-label="Pause">⏸</button>
        <button type="button" id="plNext" aria-label="Next song">⏭</button>
      </div>
      <p class="pl-note">Song titles only. Search them on Spotify or YouTube to listen.</p>
    </div>
    <ol class="pl-list" id="plList"></ol>
  </aside>

  <!-- MAIN DISPLAY -->
  <section class="room" id="room-main">
    <div class="room-head">
      <div style="display:flex;flex-direction:column;gap:6px"><span class="eyebrow">Pangunahing Bulwagan · Main Display</span><h2>Noon, Ngayon at Bukas</h2></div>
      <p>Then, now and next, side by side. Pick an area of Filipino life to see how the 2000s shaped today, and where it is heading by 2030.</p>
    </div>
    <div class="bglabel" style="display:flex;flex-direction:column;gap:10px">
      <span class="eyebrow">At a glance · Then → Now → Next</span>
      <div class="tnn" id="tnn"></div>
    </div>
    <div class="chips" id="mainChips" role="group" aria-label="Choose an area"></div>
    <article class="frame">
      <div style="display:flex;justify-content:space-between;gap:12px;flex-wrap:wrap;align-items:baseline">
        <h3 id="mainTitle"></h3><span class="cat" id="mainCat"></span>
      </div>
      <div class="versus" id="versus"></div>
      <div class="impacts">
        <div class="impact" style="--ic:var(--main)"><span class="eyebrow">Impact of the past to the present</span><p id="mainImpact"></p></div>
        <div class="impact" style="--ic:var(--next)"><span class="eyebrow">Impact to 2030</span><p id="mainImpact30"></p></div>
      </div>
      <div class="srcs"><span class="eyebrow">Sources for this gallery</span><ul id="mainSrcs"></ul></div>
      <div class="actions">
        <button class="btn" data-go="left-wing">← The 2000s gallery</button>
        <button class="btn" data-go="right-wing">Today's gallery →</button>
        <button class="btn" data-go="future">Up to 2030 ↑</button>
      </div>
    </article>
    <div class="bglabel" style="display:flex;flex-direction:column;gap:12px">
      <span class="eyebrow">Anim na aral · Six lessons from the 2000s</span>
      <div class="lessons" id="lessons"></div>
    </div>
  </section>

  <!-- WINGS (filled by script) -->
  <section class="room" id="room-left-wing" hidden>
    <div class="room-head">
      <div style="display:flex;flex-direction:column;gap:6px"><span class="eyebrow">Kaliwang Pakpak · Left Wing</span><h2>Ang Dekada 2000</h2></div>
      <p>Unli-txt, Friendster, internet cafes, mall tambay culture and the golden era of OPM. Tap an exhibit to compare it with today and 2030.</p>
    </div>
    <div class="chips" data-chips role="group" aria-label="Choose a gallery"></div>
    <div class="wing-top" data-top></div>
    <div class="gallery" data-gallery></div>
  </section>

  <section class="room" id="room-right-wing" hidden>
    <div class="room-head">
      <div style="display:flex;flex-direction:column;gap:6px"><span class="eyebrow">Kanang Pakpak · Right Wing</span><h2>Ang Kasalukuyan</h2></div>
      <p>TikTok, GCash, P-Pop and streaming. Tap an exhibit to see where it began in the 2000s and where it is going.</p>
    </div>
    <div class="chips" data-chips role="group" aria-label="Choose a gallery"></div>
    <div class="wing-top" data-top></div>
    <div class="gallery" data-gallery></div>
  </section>

  <section class="room" id="room-future" hidden>
    <div class="room-head">
      <div style="display:flex;flex-direction:column;gap:6px"><span class="eyebrow">Ikalawang Palapag · Second Floor</span><h2>Ang Hinaharap · 2030</h2></div>
      <p>Our predictions for Philippine pop culture in 2030, based on the patterns that carried from the 2000s to today.</p>
    </div>
    <p class="note">These are the group's predictions from Workbook 3, not facts. Photos on this floor show today's early signs of each trend.</p>
    <div class="chips" data-chips role="group" aria-label="Choose a gallery"></div>
    <div class="wing-top" data-top></div>
    <div class="gallery" data-gallery></div>
  </section>

  <!-- PALARUAN -->
  <section class="room" id="room-palaruan" hidden>
    <div class="room-head">
      <div style="display:flex;flex-direction:column;gap:6px"><span class="eyebrow">Palaruan · Second Floor</span><h2>Laro tayo!</h2></div>
      <p>Test what you learned, try texting like it's 2005, and leave a note for the curators.</p>
    </div>
    <div class="games">
      <article class="frame game" id="gameEra">
        <div style="display:flex;justify-content:space-between;align-items:baseline;gap:10px;flex-wrap:wrap"><h3>Noon, Ngayon o Bukas?</h3><span class="score" id="eraScore">0 / 0</span></div>
        <p style="color:var(--muted);font-size:14px">Read the exhibit card. Is it from the 2000s, today, or our 2030 predictions?</p>
        <p class="cat" id="eraArea"></p>
        <p class="clue" id="eraClue"></p>
        <div class="eras" id="eraBtns">
          <button data-era="0" style="--ec:var(--past)">Noon · 2000s</button>
          <button data-era="1" style="--ec:var(--now)">Ngayon · Today</button>
          <button data-era="2" style="--ec:var(--next)">Bukas · 2030</button>
        </div>
        <p class="feedback" id="eraFeedback" aria-live="polite"></p>
        <div class="actions"><button class="btn primary" id="eraNext">Next card</button><button class="btn" id="eraReset">Start over</button></div>
      </article>

      <article class="frame game" id="gameQuiz">
        <div style="display:flex;justify-content:space-between;align-items:baseline;gap:10px;flex-wrap:wrap"><h3>Pop Quiz</h3><span class="score" id="quizScore"></span></div>
        <p class="cat" id="quizCount"></p>
        <p class="clue" id="quizQ" style="min-height:0"></p>
        <div class="opts" id="quizOpts"></div>
        <p class="feedback" id="quizFeedback" aria-live="polite"></p>
        <div class="actions"><button class="btn primary" id="quizNext" disabled>Next question</button><button class="btn" id="quizReset">Restart quiz</button></div>
      </article>

      <article class="frame game">
        <div style="display:flex;justify-content:space-between;align-items:baseline;gap:10px;flex-wrap:wrap"><h3>Unli-txt Simulator</h3><span class="score" id="loadBal">Load: ₱20.00</span></div>
        <p style="color:var(--muted);font-size:14px">In the 2000s, every text cost ₱1 and only 160 characters fit in one message. Type a GM and see how fast your load runs out.</p>
        <div class="phone">
          <span class="brand">NOKIA-ISH</span>
          <div class="screen">
            <div class="bar"><span id="smsCount">160/1</span><span>▮▮▮▯</span></div>
            <label for="smsText" style="position:absolute;width:1px;height:1px;overflow:hidden">Text message</label>
            <textarea id="smsText" maxlength="480" placeholder="gud pm po! musta n kau? :)"></textarea>
            <span id="smsStatus" aria-live="polite"></span>
          </div>
          <div class="keys">
            <button id="smsSend">Send (₱1)</button>
            <button id="smsGM">GM to 10 (₱10)</button>
            <button id="smsUnli">Register Unli</button>
            <button id="smsLoad">Reload ₱20</button>
          </div>
        </div>
      </article>

      <article class="frame game">
        <h3>Guestbook</h3>
        <p style="color:var(--muted);font-size:14px">Leave a note for the curators. What surprised you most?</p>
        <form class="gb-form" id="gbForm" name="guestbook" method="POST" data-netlify="true" netlify-honeypot="bot-field">
          <input type="hidden" name="form-name" value="guestbook">
          <p hidden><label>Leave this empty <input name="bot-field"></label></p>
          <label>Your name<input id="gbName" name="name" maxlength="40" required placeholder="Juan dela Cruz"></label>
          <label>Your reaction
            <select id="gbReact" name="reaction"><option>🎉 Nakakatuwa!</option><option>😮 Hindi ko alam 'yon!</option><option>😂 Relate much</option><option>❤️ Proud Pinoy</option></select>
          </label>
          <label>Message<textarea id="gbMsg" name="message" maxlength="280" required placeholder="Ang galing ng Ondoy exhibit..."></textarea></label>
          <button class="btn primary" type="submit" style="align-self:flex-start">Sign the guestbook</button>
          <p class="feedback" id="gbFeedback" aria-live="polite"></p>
        </form>
        <div class="gb-list" id="gbList"></div>
      </article>
    </div>
  </section>

  <footer>
    <div class="room-head" style="align-items:baseline"><div style="display:flex;flex-direction:column;gap:6px"><span class="eyebrow">Information desk</span><h2 style="font-size:32px;color:var(--on-bg-accent)">Mga Sanggunian · Sources</h2></div></div>
    <div class="desk" id="desk"></div>
    <div class="colophon">
      <span>MO-HUM080 · What's Poppin', Pinoy? · Final group work · Workbook by Frances Ava Torregosa</span>
      <span>Chosen decade: 2000–2010 · Predictions: 2030</span>
    </div>
    <div class="mrz" id="mrz" hidden aria-hidden="true"></div>
  </footer>
</div>

<div class="scrim" id="scrim" hidden></div>
<aside class="panel" id="panel" role="dialog" aria-modal="true" aria-labelledby="pTitle" hidden>
  <button class="btn close" id="closePanel">Isara · Close ✕</button>
  <span class="cat" id="pCat"></span>
  <h3 id="pTitle"></h3>
  <div class="pair" id="pPair"></div>
  <div class="actions" id="pActions"></div>
</aside>

<script>
(function(){
const $=id=>document.getElementById(id);
const esc=s=>String(s).replace(/[&<>"]/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[c]));
const store={get(k,d){try{const v=localStorage.getItem(k);return v?JSON.parse(v):d}catch(e){return d}},set(k,v){try{localStorage.setItem(k,JSON.stringify(v))}catch(e){}}};

const root=document.documentElement;

/* ---------- Content: [2000s, today, 2030] ---------- */
const ERAS=[{name:"2000–2010",short:"2000s",tag:"Noon",c:"var(--past)"},{name:"Ngayon · Today",short:"Today",tag:"Ngayon",c:"var(--now)"},{name:"Bukas · 2030",short:"2030",tag:"Bukas",c:"var(--next)"}];
const ASPECTS=[
  {key:"event",label:"Key Event / Highlight"},
  {key:"a1",label:"Aspect 1 · Technology & Communication"},
  {key:"a2",label:"Aspect 2 · Media & Entertainment"},
  {key:"a3",label:"Aspect 3 · Places & Spaces"},
  {key:"trend",label:"Overall Observable Trend",label30:"Impact to 2030"}
];
const D=[
 {id:"social",en:"Social",tl:"Panlipunan",tnn:["Friendster & unli-txt","TikTok & group chats","AI and AR social life"],
  event:["Rise of youth subcultures around internet cafes, Friendster, and text-messaging communities (unli-txt culture).","Omnipresent social media integration via TikTok, Facebook groups, and real-time chat communities.","AI-curated social life: AI companions, AR filters, and short-video and livestream platforms blur online and offline friendships, alongside a growing 'digital detox' and offline meetup movement."],
  a1:["Introduction of dial-up/broadband internet cafes as socialization hubs; Friendster profile customization.","Mobile-first, algorithmically curated social feeds and instant video messaging.","AI-powered feeds, real-time translated voice and video chats, and AR or smart-glass messaging over faster 5G networks."],
  a2:["Mass communal viewing of prime-time TV fantaseryes and reality TV text-voting (PBB, StarStruck).","Fragmented, on-demand streaming consumption (Netflix, YouTube, TikTok trends).","Hyper-personalized, AI-generated and interactive short-form content; shared viewing through virtual watch parties and livestreams."],
  a3:["Expansion of mega-malls (SM, Ayala) as the primary public square for youth hangout and tambay culture.","Hybrid physical-digital hangout spaces, mall culture blended with food delivery and pickup hubs.","Malls reinvented as experience hubs (events, e-sports, pop-ups) linked to quick-commerce, while many hangouts move into virtual spaces."],
  trend:["Shift from face-to-face neighborhood socialization to early digital-mediated socialization (SMS/Friendster).","Fully hyper-connected, round-the-clock digital social engagement.","Today's always-online habits will deepen into AI-mediated social life, making digital wellness and real-world connection major concerns for Filipino youth by 2030."],
  impact:"The 2000s habit of building online social circles through text and early platforms established the baseline expectation for constant, digital-first social validation and connection today.",
  src:[["Social media use in the Philippines","Wikipedia","https://en.wikipedia.org/wiki/Social_media_use_in_the_Philippines"],
       ["From Friendster to Facebook and beyond","GMA News","https://www.gmanetwork.com/news/scitech/content/176875/from-friendster-to-facebook-and-beyond/story"],
       ["Eat, pray, shop: Philippine malls become the new town plazas","The Jakarta Post","https://www.thejakartapost.com/news/2015/07/30/eat-pray-shop-philippine-malls-become-new-town-plazas"]]},
 {id:"economic",en:"Economic",tl:"Pang-ekonomiya",tnn:["BPO and call center boom","Gig work and freelancing","AI-assisted work"],
  event:["Explosive boom of the Business Process Outsourcing (BPO) / call center industry in Metro Manila and key provinces.","Diversified digital economy including remote freelance work, gig economies, e-commerce, and content creation.","AI reshapes the BPO industry toward higher-skill, AI-assisted roles, while the creator, gig, and remote-work economy keeps expanding."],
  a1:["High cost of mobile text load and internet cafe hourly rates shaping tight consumer budgeting.","Ubiquitous cheap mobile data bundles and digital e-wallets (GCash, Maya).","Cashless by default: e-wallets, QR payments, and digital banks for most daily transactions, with AI tools used in everyday work."],
  a2:["Commercial dominance of physical CDs, pirated DVD stalls in malls, and paid SMS voting.","Subscription-based streaming models and influencer-driven marketing.","Live-selling and content creation become mainstream careers; AI-generated ads and virtual influencers become common in marketing."],
  a3:["Commercial growth centered around 24/7 BPO districts (Libis, Ortigas, BGC) altering urban land value.","Mixed-use township developments combining residential condos, co-working hubs, and lifestyle malls.","Growth of IT hubs and smart townships in provincial cities beyond Metro Manila, with hybrid offices and regional co-working spaces."],
  trend:["Transition to a service-oriented, night-shift economy fueled by global outsourcing.","Decentralized digital entrepreneurship and gig work.","The BPO-built service workforce will need upskilling as AI automates routine tasks, pushing Filipinos toward digital, creative, and tech-skilled work by 2030."],
  impact:"The 2000s BPO boom laid the financial and infrastructural foundation for the Philippines' modern service and digital freelance workforce.",
  src:[["Business process outsourcing in the Philippines","Wikipedia","https://en.wikipedia.org/wiki/Business_process_outsourcing_in_the_Philippines"],
       ["Timeline: BPO in PH","Inquirer Business","https://business.inquirer.net/261556/timeline-bpo-in-ph/amp"],
       ["There was a time when SMS was free","GMA News","https://gmanetwork.com/news/opinion/content/101788/there-was-a-time-when-sms-was-free/story"]]},
 {id:"political",en:"Political",tl:"Pampulitika",tnn:["Text brigades at EDSA Dos","Influencer-led campaigns","AI and deepfake-era politics"],
  event:["EDSA Dos (2001) mobilization significantly driven by text-messaging ('Text Brigade' coordination).","Political mobilization, polarization, and electoral campaigns driven heavily by TikTok, Facebook, and influencer commentary.","The 2028 national elections and later campaigns run on AI-targeted content, raising concerns about deepfakes and a stronger push for digital regulation."],
  a1:["SMS broadcast chains used for rapid political assembly and protest coordination.","Algorithmic political content, viral video discourse, and digital echo chambers.","AI-generated political content and deepfakes, met by stronger fact-checking tools and digital literacy campaigns."],
  a2:["Celebrity crossover into politics (actors turning into senators/congressmen via high TV name-recall).","Social media influencers and online personalities shaping civic discourse and political branding.","Vloggers, streamers, and online-native personalities become key political voices and even candidates."],
  a3:["Street rallies concentrated around historical public spaces (EDSA Shrine, Mendiola).","Shift toward digital activism, online petitions, and hybrid protest formats.","Hybrid civic participation: livestreamed rallies, online petitions, and more government services and public consultations done digitally."],
  trend:["Birth of 'Text-Mobility' in Philippine political action.","Digital-first, algorithm-driven political engagement.","Mobile-driven mobilization that began with text brigades will become AI-driven, making media literacy and the regulation of disinformation central to Philippine politics."],
  impact:"The 2000s proved that mobile technology could direct political action, paving the way for today's social media-fueled political landscapes.",
  src:[["The Text-messaging Revolutions","CIDOB","https://www.cidob.org/en/publications/text-messaging-revolutions"],
       ["New Media Played a Role in the People's Uprising","Nieman Reports","https://niemanreports.org/?p=2166"],
       ["Celebrity Politics and the Politics of Celebrities in the Philippines","UP Halalan","https://halalan.up.edu.ph/celebrity-politics-and-the-politics-of-celebrities-in-the-philippines/"],
       ["Like, Subscribe and Vote: Political Influencers in the 2022 Philippine Elections","ISEAS","https://www.iseas.edu.sg/articles-commentaries/iseas-perspective/2024-19-like-subscribe-and-vote-the-role-of-political-influencers-in-the-2022-philippine-elections-and-beyond2024-19-by-fatima-gaw-and-aries-a-arugay/"]]},
 {id:"cultural",en:"Cultural",tl:"Pangkultura",tnn:["OPM, MYX and Meteor Garden","K-pop and P-pop","P-pop goes global"],
  event:["Golden era of OPM alternative rock bands and MYX music culture; early wave of Asian pop integration (Meteor Garden / Korean drama dubs).","Global K-Pop (BTS, Blackpink) and P-Pop (SB19, BINI) mainstream dominance alongside globalized streaming.","P-Pop and Filipino creators become an established global presence alongside other Asian pop, with more Filipino content made for international audiences."],
  a1:["Exchanging ringtones via infrared/Bluetooth, downloading song lyrics from early blog sites.","Streaming global tracks instantly via Spotify and participating in global fandom fan-wars on X/Twitter.","AI-assisted music and video creation, immersive VR/AR concerts, and streaming as the main way to experience music."],
  a2:["Local network rivalries (ABS-CBN vs. GMA) dominating daily household conversation.","Content creation across borders, collaboration with international digital creators.","Filipino series and creators on global streaming platforms, with frequent collaborations between P-Pop and international artists."],
  a3:["Mall-based autograph signings, CD release tours, and youth subculture fashion (skater/emo looks).","Pop-up merchandise events, fan-cafes, and TikTok dance challenge flash mobs.","Hybrid live and virtual concerts and fan meets, with bigger local venues hosting global-scale P-Pop events."],
  trend:["Hybridization of local pop culture with imported Asian media trends.","Fully borderless, hyper-globalized cultural consumption.","The openness to foreign pop that started with Asianovelas will turn into Filipinos exporting their own pop culture, with P-Pop and Filipino creators competing globally."],
  impact:"The 2000s opened the gateway for foreign cultural assimilation (like Asianovelas), making modern Filipino youth uniquely receptive to global pop trends like K-Pop and P-Pop.",
  src:[["From Meteor Garden to BL? 20 Years of Taiwanese Pop Culture in the Philippines","Taiwan Insight","https://taiwaninsight.org/2021/11/18/from-meteor-garden-to-bl-20-years-of-taiwanese-pop-culture-in-the-philippines/"],
       ["Network War: From Black and White to Fireworks","PEP.ph","https://www.pep.ph/lifestyle/18457/part-i-network-war-from-black-and-white-to-fireworks"],
       ["What Is P-pop? How BINI and SB19 Are Taking Pinoy Pop Global","Chartmetric","https://hmc.chartmetric.com/what-is-pinoy-ppop-bini-sb19-cup-of-joe/"]]},
 {id:"environmental",en:"Environmental",tl:"Pangkapaligiran",tnn:["Ondoy and SMS relief","Disaster apps and mapping","Climate-smart communities"],
  event:["Severe urban vulnerability highlighted by natural disasters (e.g., Typhoon Ondoy in 2009), triggering massive online relief organization.","Heightened climate change awareness, plastic reduction policies, and digital disaster-response mapping.","Climate adaptation becomes urgent as stronger typhoons and flooding continue, with wider renewable energy use and resilience planning."],
  a1:["Transition from radio bulletins to SMS broadcast warnings during typhoons.","Real-time crowdsourced hazard mapping, weather tracking apps, and instant social media SOS messaging.","AI- and satellite-based early warnings, smart flood sensors, and real-time alerts on every phone."],
  a2:["Telethons and celebrity-led benefit concerts broadcasted on major TV networks.","Influencer-driven fundraising drives, viral TikTok awareness campaigns, and online crowdfunding (e.g., GCash donation drives).","Eco-influencers and climate content creators, gamified awareness campaigns, and instant e-wallet donation drives during disasters."],
  a3:["Overcrowded urban flooding in Metro Manila exposing the limits of concrete suburban expansion and mega-mall development.","Push for sustainable urban planning, green architecture, and flood-resilient community designs.","More flood-resilient, green, and walkable communities, with wider use of solar and wind power (like the Bangui Wind Farm)."],
  trend:["Recognition of urban ecological fragility combined with nascent digital crisis communication.","Digital-native climate activism and tech-enabled disaster management.","Digital disaster response that began with Ondoy will evolve into tech-enabled climate resilience, with citizens using data and apps to prepare for disasters, not just react to them."],
  impact:"The crisis response models forged during 2000s disasters (like Ondoy using SMS/early web tools) laid the foundation for today's digitally organized disaster relief networks.",
  src:[["Philippines: Helping flood victims through social media (2009)","Global Voices","https://globalvoices.org/2009/09/28/philippines-helping-flood-victims-through-social-media/"],
       ["Philippines: Worst Flooding in 40 Years (2009)","Global Voices","https://globalvoices.org/2009/09/27/philippines-worst-flooding-in-40-years/"],
       ["GCash extends assistance to users affected by typhoon Carina","Inquirer","https://globalnation.inquirer.net/243599/gcash-extends-assistance-to-users-affected-by-typhoon-carina/amp"]]},
 {id:"others",en:"Others · OFW & Diaspora",tl:"Iba Pa",tnn:["Webcam kamustahan","HD video calls","VR family gatherings"],
  event:["Massive global migration wave of Overseas Filipino Workers (OFWs) utilizing webcamming (Yahoo Messenger/Skype) to maintain family ties.","Digital nomadism, long-distance remote parenting via video calls, and global Pinoy online diaspora communities.","More Filipinos work for foreign companies remotely from home ('digital OFWs'), while families abroad stay connected through always-on video and VR."],
  a1:["Internet cafe webcam sessions for 'virtual kamustahan' between OFWs and families left behind.","High-definition FaceTime, Zoom, and Messenger video calls connecting households across continents seamlessly.","Real-time translated video calls, AR/VR family gatherings, and AI assistants that help long-distance families stay in touch."],
  a2:["TFC (The Filipino Channel) subscriptions and recorded local TV show VHS/DVD shipments abroad.","Direct global access to Philippine YouTube channels, local news livestreams, and P-Pop content worldwide.","Livestreamed fiestas, masses, and family celebrations for the diaspora, with Filipino content available anywhere in the world."],
  a3:["Remittance-fueled suburban housing developments and provincial 'padala' culture.","Digital banking remittances (GCash/Remitly) supporting local domestic consumption.","Instant, low-cost digital remittances, with OFWs managing homes and small businesses back home entirely online."],
  trend:["Digital bridging of transnational families separated by labor migration.","Omnipresent virtual presence of overseas family members.","Digital long-distance family life will become even more seamless, letting Filipinos abroad take part in daily family and community life back home."],
  impact:"The 2000s normalized digital long-distance family connection, evolving into today's borderless transnational households enabled by mobile tech.",
  src:[["How Filipinos Kept in Touch with their OFW Relatives","Maya","https://maya.ph/stories/how-filipinos-kept-in-touch-with-their-ofw-relatives-through-the-years"],
       ["The Impact of Cybercafés on the Connectedness of Children Left Behind by OFWs","University of Washington","https://digital.lib.washington.edu/researchworks/items/57c5fcd0-d4e1-4bf9-8061-983e9eed1d3e"],
       ["The Filipino Channel","Wikipedia","https://en.wikipedia.org/wiki/The_Filipino_Channel"]]}
];

/* ---------- Photos from Wikimedia Commons: [2000s, today, 2030] ---------- */
const CC={"CC BY 2.0":"https://creativecommons.org/licenses/by/2.0/","CC BY-SA 2.0":"https://creativecommons.org/licenses/by-sa/2.0/","CC BY-SA 2.5":"https://creativecommons.org/licenses/by-sa/2.5/","CC BY-SA 3.0":"https://creativecommons.org/licenses/by-sa/3.0/","CC BY-SA 4.0":"https://creativecommons.org/licenses/by-sa/4.0/"};
const W="https://commons.wikimedia.org/wiki/File:";
const T=path=>`https://thumb.wikimedia.org/wikipedia/commons/thumb/${path}/1280px-${path.split("/").pop()}`;
const O=path=>`https://upload.wikimedia.org/wikipedia/commons/${path}`;
const ph=(src,file,alt,caption,author,license)=>({src,link:W+file,alt,caption,author,license});
const PHOTOS={
  social:[ph(O("2/2f/A_boy_in_a_yellow_shirt_plays_games_in_a_computer_shop_in_2007.jpg"),"A_boy_in_a_yellow_shirt_plays_games_in_a_computer_shop_in_2007.jpg","A boy playing computer games at a computer shop in 2007","A computer shop in 2007, the hangout spot of 2000s kids","nina.bruja","CC BY-SA 2.0"),
          ph(T("d/d6/Metro_Manila_Portal_at_night%2C_with_crowd.jpg"),"Metro_Manila_Portal_at_night,_with_crowd.jpg","A crowd taking phone photos at the Metro Manila Portal at night","Everyone has a phone out: the Metro Manila Portal at night","Chlod","Public domain"),
          ph(T("9/9a/VR_headset_with_smartphone_and_stereoscopy_image.jpg"),"VR_headset_with_smartphone_and_stereoscopy_image.jpg","A VR headset holding a smartphone","Smartphone VR, an early sign of AR and VR social life","Bert Niehaus","CC BY-SA 4.0")],
  economic:[ph(O("d/df/Teletech_call_cent_BACOLOD.jpg"),"Teletech_call_cent_BACOLOD.jpg","Rows of workstations in a call center in Bacolod","A call center floor in Bacolod (2008), the face of the BPO boom","Maverx","CC BY-SA 3.0"),
            ph(T("0/08/Bonifacio_Global_City_Skyline.jpg"),"Bonifacio_Global_City_Skyline.jpg","The Bonifacio Global City skyline","Bonifacio Global City, a mixed-use township of offices, condos and malls","Lawrence Ruiz","CC BY-SA 4.0"),
            ph(T("7/79/New_Clark_City_Sports_Hub_%28Aerial_View%2C_June_30%2C_2020%29.jpg"),"New_Clark_City_Sports_Hub_(Aerial_View,_June_30,_2020).jpg","Aerial view of New Clark City","New Clark City in Tarlac, a planned smart city outside Metro Manila","Bases Conversion and Development Authority","Public domain")],
  political:[ph(T("4/4d/EDSA_Shrine_Robinsons_Galleria.jpg"),"EDSA_Shrine_Robinsons_Galleria.jpg","The EDSA Shrine in Ortigas","EDSA Shrine, the rally site of EDSA Dos in 2001","Matthew Gan","CC BY-SA 4.0"),
             ph(T("c/c0/University_of_the_Philippines_Manila_pre-September_21_rally_against_corruption.jpg"),"University_of_the_Philippines_Manila_pre-September_21_rally_against_corruption.jpg","Students at a rally against corruption in Manila","A 2025 student rally against corruption at UP Manila","Kej Andrés (Ryomaandres)","CC BY-SA 4.0"),
             ph(T("b/b0/COMELEC_Smartmatic_VCM_Demo_SM_Marikina_subo_%28Marcos_Highway%2C_Marikina%3B_04-22-2022%29.jpg"),"COMELEC_Smartmatic_VCM_Demo_SM_Marikina_subo_(Marcos_Highway,_Marikina;_04-22-2022).jpg","A vote counting machine demonstration","A vote counting machine demo (2022): elections keep going digital","Patrickroque01","CC BY-SA 4.0")],
  cultural:[ph(T("3/31/Nokia_3310_blue.jpg"),"Nokia_3310_blue.jpg","A blue Nokia 3310 phone","The Nokia 3310, icon of the texting and ringtone era","Michael Brandtner","Public domain"),
            ph(T("9/96/DSC_6202_Audience_members_hold_up_smartphones_to_capture_a_live_event_screens_glowing_in_the_dim_venue.jpg"),"DSC_6202_Audience_members_hold_up_smartphones_to_capture_a_live_event_screens_glowing_in_the_dim_venue.jpg","Concert audience holding up smartphones","A concert crowd filming on their phones","PattayaPatrol","CC BY-SA 4.0"),
            ph(T("8/8e/2019_SEA_Games_Esports_Tekken_7_THA_vs_PHI.jpg"),"2019_SEA_Games_Esports_Tekken_7_THA_vs_PHI.jpg","An esports match on stage at the 2019 SEA Games","Esports at the 2019 SEA Games in the Philippines: digital entertainment as a live show","Hariboneagle927","CC BY-SA 3.0")],
  environmental:[ph(T("7/7e/Flooding_from_Typhoon_Ondoy_%28Ketsana%29%2C_Philippines_2009._Photo-_AusAID_%2810695725136%29.jpg"),"Flooding_from_Typhoon_Ondoy_(Ketsana),_Philippines_2009._Photo-_AusAID_(10695725136).jpg","A flooded street after Typhoon Ondoy","Flooding from Typhoon Ondoy, 2009","Department of Foreign Affairs and Trade (AusAID)","CC BY 2.0"),
                 ph(T("2/2d/Bangui_Wind_Mills.JPG"),"Bangui_Wind_Mills.JPG","Wind turbines along the coast of Bangui","Bangui Wind Farm in Ilocos Norte","Ignacio Malapitan III","CC BY-SA 3.0"),
                 ph(T("7/76/50_MWAC_San_Miguel_Solar_Farm_Project.jpg"),"50_MWAC_San_Miguel_Solar_Farm_Project.jpg","A solar farm in the Philippines","A 50 MW solar farm in San Miguel: renewable energy scaling up","FBenjr123","CC BY-SA 4.0")],
  others:[ph(T("6/6e/Balikbayan_Boxes.jpg"),"Balikbayan_Boxes.jpg","Taped balikbayan boxes","Balikbayan boxes on their way home","OAlexander","CC BY-SA 2.5"),
          ph(T("9/92/NAIA_T3_Interior_Arrival_Area_-_Sep_2018.jpg"),"NAIA_T3_Interior_Arrival_Area_-_Sep_2018.jpg","The NAIA Terminal 3 arrival area","NAIA Terminal 3 arrivals, where OFWs come home","RoyKabanlit","CC BY-SA 4.0"),
          ph(T("7/7b/Child_shows_drawing_to_family_member_on_video_call_at_home_during_day.jpg"),"Child_shows_drawing_to_family_member_on_video_call_at_home_during_day.jpg","A child showing a drawing on a video call","Family life over video calls, the everyday reality of long-distance families","Shixart1985","CC BY 2.0")]
};
const credit=p=>{const lic=CC[p.license]?`<a href="${CC[p.license]}" target="_blank" rel="noopener">${p.license}</a>`:p.license;return `Photo: <a href="${p.link}" target="_blank" rel="noopener">${esc(p.author)}</a>, ${lic}, via Wikimedia Commons`;};


/* ---------- Area themes ---------- */
function mkBunting(){
  const W=1400,cols=["var(--f1)","var(--f2)","var(--f3)","var(--f4)","var(--f5)","var(--f6)"];let h="";
  [[0,10,34,22],[1,46,70,18]].forEach(([row,y0,sag,size])=>{const n=row?34:28,step=W/n;
    h+=`<path d="M0 ${y0} Q ${W/2} ${y0+sag} ${W} ${y0}" stroke="var(--frame)" stroke-width="1.5" fill="none" opacity=".6"/>`;
    for(let k=0;k<n;k++){const x=step*k+step/2,t=x/W,y=(1-t)*(1-t)*y0+2*(1-t)*t*(y0+sag)+t*t*y0;
      h+=`<g class="sway" style="animation-delay:${(k%5)*-.6}s;transform-box:fill-box"><path d="M${x-size/2} ${y} L${x+size/2} ${y} L${x} ${y+size*1.25} Z" fill="${cols[(k+row*3)%cols.length]}"/></g>`;}});
  return `<svg viewBox="0 0 ${W} 96" preserveAspectRatio="none" aria-hidden="true">${h}</svg>`;
}
const THEMES={
 museo:{name:"Museo · classic fiesta",html:mkBunting()},
 social:{name:"Social · a Nokia 3310 screen",html:`<span class="soft">Menu</span><span>▮▮▮▯</span><span class="grow"></span><span>PINOY 2004</span><span class="grow"></span><span>▰▰▰▱</span><span class="soft">Names</span><div class="snake" aria-hidden="true"></div><div class="apple" aria-hidden="true"></div>`},
 economic:{name:"Economic · a 2000s office computer",html:`<span class="start">start</span><span class="task">📁 Museo ng Ekonomiya</span><span class="task">🌐 Dial-up · 56 Kbps</span><span class="tray"><span aria-hidden="true">🔊</span><span id="clock">2:04 AM</span></span><div class="balloon"><b>Night shift</b><br>The BPO boom kept Metro Manila working 24/7.</div>`},
 political:{name:"Political · billboards along EDSA",html:`<div class="road"><span class="sign">EDSA</span><div class="exits"><span>↖ Ortigas · Shrine</span><span>↑ Cubao</span><span>↗ Mendiola</span></div><span class="grow"></span><span>SLOW DOWN · RALLY AHEAD</span></div><div class="led"><span>TXT BRIGADE ··· Wear black. Go 2 EDSA Shrine 2nite. Pass it on 2 10 friends! ··· FWD: Rally @ Ortigas cor. EDSA ··· Text is the new rally call ···</span></div><div class="street"><svg class="jeep" viewBox="0 0 120 42" aria-hidden="true"><rect x="8" y="6" width="96" height="6" rx="2" fill="#C9CED6"/><rect x="10" y="12" width="92" height="18" rx="2" fill="#E8B021"/><rect x="14" y="14" width="12" height="9" fill="#2B2F35"/><rect x="29" y="14" width="12" height="9" fill="#2B2F35"/><rect x="44" y="14" width="12" height="9" fill="#2B2F35"/><rect x="59" y="14" width="12" height="9" fill="#2B2F35"/><rect x="74" y="14" width="10" height="9" fill="#2B2F35"/><rect x="10" y="24" width="92" height="3" fill="#C1121F"/><rect x="102" y="16" width="14" height="14" rx="2" fill="#C9CED6"/><rect x="113" y="20" width="4" height="4" fill="#FFF3B0"/><rect x="104" y="6" width="3" height="10" fill="#C9CED6"/><circle cx="28" cy="32" r="7" fill="#111"/><circle cx="28" cy="32" r="3" fill="#C9CED6"/><circle cx="92" cy="32" r="7" fill="#111"/><circle cx="92" cy="32" r="3" fill="#C9CED6"/></svg></div>`},
 cultural:{name:"Cultural · a 2000s MP3 player",html:`<span class="np">▶ Now Playing</span><span id="nowTrack"></span><span class="eq" aria-hidden="true"><i></i><i></i><i></i><i></i></span><span class="prog" aria-hidden="true"></span><span id="vtime">0:00</span>`},
 environmental:{name:"Environmental · a bus ride in heavy rain",html:`<div class="dest"><span class="busno">24</span><div class="led"><span>EDSA CAROUSEL · MONUMENTO – PITX ··· HEAVY RAIN · DRIVE SAFELY ··· BAHA SA ESPAÑA ···</span></div></div><div class="modal" id="alertModal" role="alertdialog" aria-label="Emergency alert"><div class="t"><svg width="30" height="26" viewBox="0 0 32 28" aria-hidden="true"><path d="M16 0 32 28H0Z" fill="#E5413A"/><rect x="14.5" y="9" width="3" height="10" rx="1.5" fill="#fff"/><circle cx="16" cy="23" r="1.8" fill="#fff"/></svg> Emergency alert: Extreme</div><p>NDRRMC(9:41PM,26Sep09) Museum recreation: Red Rainfall Warning sa Metro Manila. Nagbabanta ang matinding pag-ulan at pagbaha. Walk through this gallery to see how alerts went from radio to SMS to apps.</p><button class="ok" type="button" id="alertOk">OK</button></div>`},
 others:{name:"Others · a Philippine passport (museum specimen)",html:`<svg viewBox="0 0 1200 90" preserveAspectRatio="none" aria-hidden="true"><g class="wave"><path d="M0 0H1200V34Q900 62 600 38T0 44Z" fill="#0038A8"/><path d="M0 44Q300 34 600 48T1200 34V90H0Z" fill="#CE1126"/></g><polygon points="0,0 170,45 0,90" fill="#FFFFFF"/><circle cx="52" cy="45" r="13" fill="#FCD116"/><circle cx="16" cy="13" r="4" fill="#FCD116"/><circle cx="16" cy="77" r="4" fill="#FCD116"/><circle cx="140" cy="45" r="4" fill="#FCD116"/></svg><div class="flagline"><span>REPUBLIKA NG PILIPINAS</span><span>PASAPORTE / PASSPORT</span><span>SPECIMEN · MUSEUM EXHIBIT</span></div>`}
};
let clockTimer=null,scoreTimer=null,lastArea=null;
let room0="main", lookChoice=store.get("wpp-look","museo");
if(!(lookChoice in THEMES)&&lookChoice!=="match") lookChoice="museo";
function applyTheme(){
  const id=lookChoice==="match"?D[cur].id:lookChoice;
  document.body.dataset.area=id;
  if(lastArea!==id){
    $("banner").innerHTML=THEMES[id].html;
    if(lastArea!==null){document.body.classList.remove("switching");void document.body.offsetWidth;document.body.classList.add("switching");setTimeout(()=>document.body.classList.remove("switching"),650);}
    clearInterval(clockTimer);clearInterval(scoreTimer);if(typeof songTimer!=="undefined")clearInterval(songTimer);
    if(id==="economic"){const tick=()=>{const c=$("clock");if(c)c.textContent=new Date().toLocaleTimeString("en-PH",{hour:"numeric",minute:"2-digit"});};tick();clockTimer=setInterval(tick,15000);}
    if(id==="cultural"){startPlayer();}
    if(id==="environmental"){const ok=$("alertOk");if(ok)ok.onclick=()=>{$("alertModal").hidden=true;};}
    lastArea=id;
    if(typeof WING!=="undefined") Object.keys(WING).forEach(renderWing);
  }
  $("themeLine").textContent="Now showing: "+THEMES[id].name;
  $("mrz").hidden=id!=="others";
  $("mrz").textContent="P<PHLWHATS<POPPIN<<PINOY<<<<<<<<<<<<<<<<<<<<<<\nMO0HUM0802PHL0001017M3010316<<<<<<<<<<<<<<04";
  store.set("wpp-area",cur);
}

/* Animations on/off: starts from the device setting, the button overrides it */
let calm=store.get("wpp-calm",null); if(calm===null) calm=matchMedia("(prefers-reduced-motion: reduce)").matches;
function setMotion(){root.classList.toggle("calm",!!calm);$("motionBtn").textContent="Animations: "+(calm?"Off":"On");$("motionBtn").setAttribute("aria-pressed",String(!calm));}
$("motionBtn").addEventListener("click",()=>{calm=!calm;store.set("wpp-calm",calm);setMotion();});
setMotion();
$("themePick").value=lookChoice;
$("themePick").addEventListener("change",e=>{lookChoice=e.target.value;store.set("wpp-look",lookChoice);applyTheme();});


/* ---------- 2000s OPM playlist (titles only, no audio) ---------- */
const SONGS=[
 ["Maskara","Eraserheads",2001,"Carbon Stereoxide","https://en.wikipedia.org/wiki/Carbon_Stereoxide"],
 ["Your Song","Parokya ni Edgar",2003,"Bigotilyo","https://en.wikipedia.org/wiki/Bigotilyo"],
 ["Noypi","Bamboo",2004,"As the Music Plays","https://en.wikipedia.org/wiki/Bamboo_(Filipino_band)"],
 ["Jeepney","Sponge Cola",2005,"Palabas","https://en.wikipedia.org/wiki/Palabas"],
 ["The Day You Said Goodnight","Hale",2005,"Hale","https://en.wikipedia.org/wiki/Hale_(album)"],
 ["Hanggang Kailan (Umuwi Ka Na Baby)","Orange and Lemons",2005,"Strike Whilst the Iron Is Hot","https://en.wikipedia.org/wiki/Strike_Whilst_the_Iron_Is_Hot"],
 ["Bagsakan","Parokya ni Edgar ft. Francis Magalona & Gloc-9",2005,"Halina Sa Parokya","https://en.wikipedia.org/wiki/Halina_Sa_Parokya"],
 ["Akin Ka Na Lang","The Itchyworms",2005,"Noontime Show","https://en.wikipedia.org/wiki/The_Itchyworms"],
 ["Narda","Kamikazee",2006,"Maharot","https://en.wikipedia.org/wiki/Maharot"],
 ["Magbalik","Callalily",2007,"Destination XYZ","https://en.wikipedia.org/wiki/Destination_XYZ"]
];
let song=store.get("wpp-song",0)%SONGS.length, playing=true, songTimer=null, secs=0;
const SONG_LEN=18;
function showSong(){
  const [t,a,y,al]=SONGS[song];
  $("plNow").innerHTML=`<span>${song+1} of ${SONGS.length}</span><b>${esc(t)}</b><span>${esc(a)}</span><span>${esc(al)} · ${y}</span>`;
  $("plList").querySelectorAll("button").forEach((b,i)=>b.setAttribute("aria-current",String(i===song)));
  const nt=$("nowTrack"); if(nt) nt.textContent=`${song+1} of ${SONGS.length} · ${t} — ${a} (${y})`;
  const bar=$("plBar"); bar.classList.remove("run"); void bar.offsetWidth; bar.style.setProperty("--dur",SONG_LEN+"s"); if(playing) bar.classList.add("run");
  const pb=document.querySelector("#banner .prog"); if(pb){pb.style.animation="none";void pb.offsetWidth;pb.style.animation=`track ${SONG_LEN}s linear forwards`;}
  secs=0; store.set("wpp-song",song);
}
function tickSong(){ if(!playing) return; secs++; const el=$("vtime"); if(el) el.textContent="0:"+String(secs).padStart(2,"0"); if(secs>=SONG_LEN){song=(song+1)%SONGS.length;showSong();} }
function startPlayer(){ clearInterval(songTimer); showSong(); songTimer=setInterval(tickSong,1000); }
$("plList").innerHTML=SONGS.map((s,i)=>`<li><button type="button" data-i="${i}"><span>${i+1}</span><span><b>${esc(s[0])}</b><br><small>${esc(s[1])}</small></span><small>${s[2]}</small></button></li>`).join("");
$("plList").querySelectorAll("button").forEach(b=>b.onclick=()=>{song=+b.dataset.i;playing=true;$("plPlay").textContent="⏸";showSong();});
$("plPrev").onclick=()=>{song=(song-1+SONGS.length)%SONGS.length;showSong();};
$("plNext").onclick=()=>{song=(song+1)%SONGS.length;showSong();};
$("plPlay").onclick=()=>{playing=!playing;$("plPlay").textContent=playing?"⏸":"▶";$("plPlay").setAttribute("aria-label",playing?"Pause":"Play");const bar=$("plBar");bar.style.animationPlayState=playing?"running":"paused";const pb=document.querySelector("#banner .prog");if(pb)pb.style.animationPlayState=playing?"running":"paused";};


/* Hero: popcorn letters + flipping tagline */
(function(){
  const pop=$("heroPop"), word=pop.textContent; pop.innerHTML=[...word].map((c,i)=>`<i style="--i:${i}">${c}</i>`).join("");
  const TG=[["Friendster","TikTok","AI friends"],["call centers","gig work","AI co-workers"],["text brigades","influencers","deepfake checks"],["Meteor Garden","P-pop","P-pop world tours"],["SMS warnings","disaster apps","climate-smart cities"],["webcam kamustahan","video calls","VR family reunions"]];
  let t=0;
  setInterval(()=>{t=(t+1)%TG.length;["tgA","tgB","tgC"].forEach((id,j)=>{const b=$(id);b.classList.remove("flip");void b.offsetWidth;b.textContent=TG[t][j];b.style.animationDelay=(j*.15)+"s";b.classList.add("flip");});},3200);
})();

/* ---------- Rendering ---------- */
const ROOMS={"main":"var(--main)","left-wing":"var(--past)","right-wing":"var(--now)","future":"var(--next)","palaruan":"var(--f2)"};
const WING={"left-wing":0,"right-wing":1,"future":2};
function show(room){
  if(!ROOMS[room]) room="main";
  document.querySelectorAll(".room").forEach(s=>s.hidden=s.id!=="room-"+room);
  document.querySelectorAll("#plan button").forEach(b=>b.setAttribute("aria-current",b.dataset.room===room?"true":"false"));
  root.style.setProperty("--room",ROOMS[room]);
  room0=room; applyTheme();
}
function go(room){ if(location.hash!=="#"+room) location.hash=room; else show(room); window.scrollTo({top:document.querySelector("nav").offsetTop-10,behavior:"smooth"}); }
document.querySelectorAll("#plan button").forEach(b=>b.addEventListener("click",()=>go(b.dataset.room)));
document.querySelectorAll("[data-go]").forEach(b=>b.addEventListener("click",()=>go(b.dataset.go)));
window.addEventListener("hashchange",()=>show(location.hash.slice(1)));

function photo(id,era,withEra){
  const p=(PHOTOS[id]||[])[era]; if(!p) return "";
  return `<figure style="--sc:${ERAS[era].c}"><div class="ph"><img src="${p.src}" alt="${esc(p.alt)}" loading="lazy" referrerpolicy="no-referrer" onerror="this.closest('figure').remove()">${withEra?`<span class="era">${ERAS[era].tag}</span>`:''}</div>
    <figcaption>${esc(p.caption)} · ${credit(p)}</figcaption></figure>`;
}
const srcList=d=>d.src.map(s=>`<li><a href="${s[2]}" target="_blank" rel="noopener">${esc(s[0])}</a> · ${esc(s[1])}</li>`).join("");
const label=(a,era)=>era===2&&a.label30?a.label30:a.label;

let cur=Math.min(Math.max(0,+store.get("wpp-area",0)||0),5);
function chips(el){
  el.innerHTML=D.map((d,i)=>`<button class="chip" data-i="${i}" aria-pressed="${i===cur}"><span>${d.en}</span><small>${d.tl}</small></button>`).join("");
  el.querySelectorAll(".chip").forEach(c=>c.onclick=()=>{cur=+c.dataset.i;renderAll();});
}
function renderMain(){
  const d=D[cur];
  $("mainTitle").innerHTML=`${d.en} <span class="tl">· ${d.tl}</span>`;
  $("mainCat").textContent=`Gallery ${cur+1} of ${D.length}`;
  $("versus").innerHTML=[0,1,2].map(e=>`<div class="side" style="--sc:${ERAS[e].c}">${photo(d.id,e)}<span class="when">${ERAS[e].name}</span>
     <dl><div><dt>Key event / highlight${e===2?" (prediction)":""}</dt><dd>${esc(d.event[e])}</dd></div>${e<2?`<div><dt>Overall trend</dt><dd>${esc(d.trend[e])}</dd></div>`:""}</dl></div>`).join(`<div class="arrow" aria-hidden="true">→</div>`);
  $("mainImpact").textContent=d.impact;
  $("mainImpact30").textContent=d.trend[2];
  $("mainSrcs").innerHTML=srcList(d);
  document.querySelectorAll("#tnn button").forEach((b,i)=>b.setAttribute("aria-current",String(i===cur)));
}

/* Exhibit tags: wording follows the museum look */
function tagText(look,e,k){
  const era=["2000s","Ngayon","2030"][e];
  const T={
    museo:()=>`Exhibit ${k+1} · ${era}`,
    social:()=>`${["TXT","1","2","3",e===2?"IMPACT":"TREND"][k]} · ${era.toUpperCase()}`,
    economic:()=>`📁 ${era}\\${["Highlight.doc","Aspect1.xls","Aspect2.wmv","Aspect3.jpg",e===2?"Impact.ppt":"Trend.ppt"][k]}`,
    political:()=>`EXIT ${k+1} · ${era.toUpperCase()}`,
    cultural:()=>`▶ Track ${String(k+1).padStart(2,"0")} · ${era}`,
    environmental:()=>`${["⚠ Alert","ℹ Advisory 1","ℹ Advisory 2","ℹ Advisory 3","📢 Bulletin"][k]} · ${era}`,
    others:()=>`${["Entry","Stamp 1","Stamp 2","Stamp 3",e===2?"Visa":"Exit"][k]} · ${era}`
  };
  return (T[look]||T.museo)();
}
function renderWing(room){
  const era=WING[room], sec=$("room-"+room), d=D[cur];
  sec.querySelector("[data-top]").innerHTML=`${photo(d.id,era,true)}<div class="frame" style="margin:6px"><span class="cat">${d.tl} · Gallery ${cur+1}</span><h3>${d.en}</h3><p>${esc(d.trend[era])}</p></div>`;
  const tags=[0,1,2].map(e=>k=>`<span class="tag" data-era="${e}">${esc(tagText(document.body.dataset.area,e,k))}</span>`);
  const more=["Compare with today and 2030 →","See where it began and where it's going","← See how we got here"];
  const g=sec.querySelector("[data-gallery]");
  g.innerHTML=ASPECTS.map((a,k)=>`<button class="ex ${k<2?'big':''}" data-k="${k}">${tags[era](k)}
      <span class="label">${label(a,era)}</span><span class="txt">${esc(d[a.key][era])}</span><span class="more">${more[era]}</span></button>`).join("");
  g.querySelectorAll(".ex").forEach(b=>b.onclick=()=>openPlaque(+b.dataset.k,era));
}
function renderAll(){
  applyTheme();
  document.querySelectorAll("#mainChips,[data-chips]").forEach(chips);
  renderMain(); Object.keys(WING).forEach(renderWing);
}
$("tnn").innerHTML=D.map((d,i)=>`<button data-i="${i}"><b>${d.en.replace(" · OFW & Diaspora"," (OFW)")}</b><span class="p">${d.tnn[0]}</span><span class="n arrowed">${d.tnn[1]}</span><span class="x arrowed">${d.tnn[2]}</span></button>`).join("");
document.querySelectorAll("#tnn button").forEach(b=>b.onclick=()=>{cur=+b.dataset.i;renderAll();$("mainTitle").scrollIntoView({behavior:"smooth",block:"center"});});
$("lessons").innerHTML=D.map((d,i)=>`<button class="lesson" data-i="${i}"><span class="eyebrow" style="color:var(--frame)">${d.tl}</span><b>${d.en}</b><span>${esc(d.impact)}</span></button>`).join("");
document.querySelectorAll(".lesson").forEach(b=>b.onclick=()=>{cur=+b.dataset.i;renderAll();$("mainTitle").scrollIntoView({behavior:"smooth",block:"center"});});

/* Information desk */
(function renderDesk(){
  let html=D.map(d=>`<div><h4>${d.en} <span class="tl" style="font-size:14px">· ${d.tl}</span></h4><ul>${srcList(d)}</ul></div>`).join("");
  html+=`<div class="wide"><h4>Photo credits</h4><ul>${D.map(d=>PHOTOS[d.id].map((p,e)=>`<li><b>${d.en.split(" ·")[0]}, ${ERAS[e].short}:</b> ${esc(p.caption)}. ${credit(p)}</li>`).join("")).join("")}</ul></div>`;
  html+=`<div class="wide"><h4>2000s OPM playlist (MP3 player look)</h4><ul>${SONGS.map(x=>`<li>“${esc(x[0])}” · ${esc(x[1])} (${x[2]}), from <a href="${x[4]}" target="_blank" rel="noopener">${esc(x[3])}</a></li>`).join("")}</ul></div>`;
  html+=`<div class="wide"><h4>Content</h4><ul><li>MO-HUM080 Workbook, Phase 2 Worksheet 2: the 2000s vs. the present (group's own work)</li><li>MO-HUM080 Workbook, Phase 3 Worksheet 3: 2030 predictions (group's own work)</li></ul></div>`;
  $("desk").innerHTML=html;
})();

/* Plaques */
let lastFocus=null;
function openPlaque(k,era){
  const d=D[cur],a=ASPECTS[k];lastFocus=document.activeElement;
  $("pCat").textContent=`${d.en} · ${d.tl}`;
  $("pTitle").textContent=a.label.replace(/^Aspect \d · /,"");
  $("pPair").innerHTML=[0,1,2].map(e=>`<div class="side${e===era?" cur":""}" style="--sc:${ERAS[e].c}">${photo(d.id,e)}<span class="when">${ERAS[e].name}</span>${e===2&&a.label30?`<span class="eyebrow">${a.label30}</span>`:""}<p>${esc(d[a.key][e])}</p></div>`).join("")+
    `<div class="impact"><span class="eyebrow">How the past shaped the present</span><p style="font-size:17px">${esc(d.impact)}</p></div>
     <div class="srcs"><span class="eyebrow">Sources</span><ul>${srcList(d)}</ul></div>`;
  const rooms=[["left-wing","Kaliwang Pakpak · 2000s"],["right-wing","Kanang Pakpak · Today"],["future","Ang Hinaharap · 2030"]].filter((_,i)=>i!==era);
  $("pActions").innerHTML=rooms.map(r=>`<button class="btn" data-room="${r[0]}">Walk to ${r[1]}</button>`).join("")+`<button class="btn primary" data-room="main">Main Display</button>`;
  $("pActions").querySelectorAll("button").forEach(b=>b.onclick=()=>{closePlaque();go(b.dataset.room);});
  $("scrim").hidden=false;$("panel").hidden=false;$("closePanel").focus();
}
function closePlaque(){$("scrim").hidden=true;$("panel").hidden=true;lastFocus&&document.contains(lastFocus)&&lastFocus.focus();}
$("closePanel").onclick=closePlaque;$("scrim").onclick=closePlaque;
document.addEventListener("keydown",e=>{if(e.key==="Escape"&&!$("panel").hidden)closePlaque();});

/* ---------- Palaruan: Noon, Ngayon o Bukas? ---------- */
const shuffle=a=>{for(let i=a.length-1;i>0;i--){const j=Math.floor(Math.random()*(i+1));[a[i],a[j]]=[a[j],a[i]];}return a;};
let eraDeck=[],eraCard=null,eraRight=0,eraTotal=0,eraDone=false;
function eraNew(){eraDeck=shuffle(D.flatMap(d=>ASPECTS.slice(0,4).flatMap(a=>[0,1,2].map(e=>({d,a,e})))));eraRight=0;eraTotal=0;eraNext();}
function eraNext(){
  if(!eraDeck.length) eraDeck=shuffle(D.flatMap(d=>ASPECTS.slice(0,4).flatMap(a=>[0,1,2].map(e=>({d,a,e})))));
  eraCard=eraDeck.pop();eraDone=false;
  $("eraArea").textContent=`${eraCard.d.en} · ${eraCard.a.label.replace(/^Aspect \d · /,"")}`;
  $("eraClue").textContent=`“${eraCard.d[eraCard.a.key][eraCard.e]}”`;
  $("eraFeedback").textContent="";$("eraFeedback").className="feedback";
  $("eraBtns").querySelectorAll("button").forEach(b=>b.disabled=false);
  $("eraScore").textContent=`${eraRight} / ${eraTotal}`;
}
$("eraBtns").querySelectorAll("button").forEach(b=>b.onclick=()=>{
  if(eraDone) return; eraDone=true; eraTotal++;
  const ok=+b.dataset.era===eraCard.e; if(ok) eraRight++;
  $("eraFeedback").textContent=ok?`Tama! That's ${ERAS[eraCard.e].tag} (${ERAS[eraCard.e].short}).`:`Hindi. That one is ${ERAS[eraCard.e].tag} (${ERAS[eraCard.e].short}).`;
  $("eraFeedback").className="feedback "+(ok?"ok":"no");
  $("eraBtns").querySelectorAll("button").forEach(x=>x.disabled=true);
  $("eraScore").textContent=`${eraRight} / ${eraTotal}`;
});
$("eraNext").onclick=eraNext; $("eraReset").onclick=eraNew;
eraNew();

/* ---------- Palaruan: Pop Quiz ---------- */
const QUIZ=[
  {q:"What did Filipinos use to quickly gather crowds during EDSA Dos in 2001?",o:["Text messages","Facebook events","TV ads","Radio only"],a:0,why:"Text brigades spread the call to EDSA by SMS."},
  {q:"Which typhoon in 2009 sparked massive online relief efforts?",o:["Yolanda","Ondoy","Pepeng","Ulysses"],a:1,why:"Typhoon Ondoy (Ketsana) flooded Metro Manila in September 2009."},
  {q:"Which industry boomed in Metro Manila in the 2000s?",o:["Car manufacturing","BPO and call centers","Mining","Shipbuilding"],a:1,why:"The BPO boom built a night-shift, service economy."},
  {q:"Where did 2000s Filipino youth usually hang out?",o:["Co-working spaces","Malls like SM and Ayala","Esports arenas","Rooftop bars"],a:1,why:"Mega-malls were the main public square for tambay culture."},
  {q:"How did OFWs see their families in the 2000s?",o:["HD FaceTime","Webcams at internet cafes","VR headsets","Hologram calls"],a:1,why:"Families went to internet cafes for webcam kamustahan on Yahoo Messenger or Skype."},
  {q:"Which Taiwanese drama helped start the Asianovela craze?",o:["Meteor Garden","Crash Landing on You","Squid Game","Hotel del Luna"],a:0,why:"Meteor Garden opened the door to Asian pop in the Philippines."},
  {q:"Which band released the 2006 hit “Narda”?",o:["Hale","Kamikazee","Callalily","Sponge Cola"],a:1,why:"“Narda” is from Kamikazee's 2006 album Maharot."},
  {q:"What do we predict for P-Pop by 2030?",o:["It will disappear","It will stay local only","It will become a global presence","It will only be on radio"],a:2,why:"Our Workbook 3 predicts Filipinos will export their own pop culture."},
  {q:"What is one 2030 concern we predicted for Philippine politics?",o:["Fax machines","AI deepfakes and disinformation","Too few TV channels","Paper-only voting"],a:1,why:"AI-generated content will make media literacy central."}
];
let qOrder=[],qi=0,qScore=0,qAnswered=false;
function quizNew(){qOrder=shuffle([...QUIZ.keys()]);qi=0;qScore=0;quizShow();}
function quizShow(){
  qAnswered=false;$("quizNext").disabled=true;$("quizFeedback").textContent="";$("quizFeedback").className="feedback";
  if(qi>=qOrder.length){
    const msg=qScore===QUIZ.length?"Perfect! Certified Pinoy pop culture expert.":qScore>=6?"Galing! You really walked through the museum.":qScore>=4?"Not bad! Visit the wings again and retry.":"Balik ka sa museum and try again!";
    $("quizCount").textContent="Tapos na!";$("quizQ").textContent=`You got ${qScore} out of ${QUIZ.length}. ${msg}`;$("quizOpts").innerHTML="";$("quizScore").textContent=`${qScore} / ${QUIZ.length}`;return;
  }
  const Q=QUIZ[qOrder[qi]];
  $("quizCount").textContent=`Question ${qi+1} of ${QUIZ.length}`;$("quizScore").textContent=`Score: ${qScore}`;
  $("quizQ").textContent=Q.q;
  $("quizOpts").innerHTML=Q.o.map((o,i)=>`<button class="opt" data-i="${i}">${esc(o)}</button>`).join("");
  $("quizOpts").querySelectorAll(".opt").forEach(b=>b.onclick=()=>{
    if(qAnswered) return; qAnswered=true;
    const ok=+b.dataset.i===Q.a; if(ok) qScore++;
    $("quizOpts").querySelectorAll(".opt").forEach(x=>{x.disabled=true;if(+x.dataset.i===Q.a)x.classList.add("right");});
    if(!ok) b.classList.add("wrong");
    $("quizFeedback").textContent=(ok?"Tama! ":"Mali. ")+Q.why;$("quizFeedback").className="feedback "+(ok?"ok":"no");
    $("quizScore").textContent=`Score: ${qScore}`;$("quizNext").disabled=false;$("quizNext").focus();
  });
}
$("quizNext").onclick=()=>{qi++;quizShow();}; $("quizReset").onclick=quizNew;
quizNew();

/* ---------- Palaruan: Unli-txt simulator ---------- */
let load=20,unli=false;
const peso=v=>"₱"+v.toFixed(2);
function smsUpdate(){
  const n=$("smsText").value.length, parts=Math.max(1,Math.ceil(n/160));
  $("smsCount").textContent=`${parts*160-n||160}/${parts}`;
  $("loadBal").textContent=unli?"Load: UNLI-TXT":"Load: "+peso(load);
}
function send(count){
  const txt=$("smsText").value.trim();
  if(!txt){$("smsStatus").textContent="Type a message first.";return;}
  const parts=Math.ceil(txt.length/160), cost=unli?0:count*parts;
  if(cost>load){$("smsStatus").textContent=`Insufficient load! Need ${peso(cost)}. Pasaload ka muna.`;return;}
  load-=cost;$("smsStatus").textContent=count>1?`GM sent to ${count} contacts!${unli?"":" -"+peso(cost)}`:`Message sent!${unli?"":" -"+peso(cost)}`;
  $("smsText").value="";smsUpdate();
}
$("smsText").addEventListener("input",smsUpdate);
$("smsSend").onclick=()=>send(1);
$("smsGM").onclick=()=>send(10);
$("smsUnli").onclick=()=>{if(unli){$("smsStatus").textContent="You're already on Unli-txt.";return;}if(load<15){$("smsStatus").textContent="Unli-txt costs ₱15. Reload first.";return;}load-=15;unli=true;$("smsStatus").textContent="Registered! Unli-txt to all networks for 1 day.";smsUpdate();};
$("smsLoad").onclick=()=>{load+=20;$("smsStatus").textContent="Reloaded ₱20 at the sari-sari store.";smsUpdate();};
smsUpdate();

/* ---------- Palaruan: Guestbook ---------- */
function gbRender(){
  const notes=store.get("wpp-guestbook",[]);
  $("gbList").innerHTML=notes.length?`<span class="eyebrow">Your notes on this device</span>`+notes.slice().reverse().map(n=>`<div class="gb-note"><b>${esc(n.name)}</b> · ${esc(n.reaction)}<p>${esc(n.message)}</p></div>`).join(""):"";
}
$("gbForm").addEventListener("submit",async e=>{
  e.preventDefault();
  const note={name:$("gbName").value.trim(),reaction:$("gbReact").value,message:$("gbMsg").value.trim()};
  if(!note.name||!note.message) return;
  const notes=store.get("wpp-guestbook",[]);notes.push(note);store.set("wpp-guestbook",notes);gbRender();
  let sent=false;
  try{
    const body=new URLSearchParams(new FormData($("gbForm"))).toString();
    const r=await fetch("/",{method:"POST",headers:{"Content-Type":"application/x-www-form-urlencoded"},body});
    sent=r.ok;
  }catch(err){}
  $("gbFeedback").textContent=sent?"Salamat! Your note was sent to the curators.":"Salamat! Your note is saved on this device.";
  $("gbFeedback").className="feedback ok";
  $("gbMsg").value="";
});
gbRender();

renderAll();
show(location.hash.slice(1));
})();
</script>
</body>
</html>
  $("eraArea").textContent=`${eraCard.d.en} · ${eraCard.a.label.replace(/^Aspect \d · /,"")}`;
  $("eraClue").textContent=`“${eraCard.d[eraCard.a.key][eraCard.e]}”`;
  $("eraFeedback").textContent="";$("eraFeedback").className="feedback";
  $("eraBtns").querySelectorAll("button").forEach(b=>b.disabled=false);
  $("eraScore").textContent=`${eraRight} / ${eraTotal}`;
}
$("eraBtns").querySelectorAll("button").forEach(b=>b.onclick=()=>{
  if(eraDone) return; eraDone=true; eraTotal++;
  const ok=+b.dataset.era===eraCard.e; if(ok) eraRight++;
  $("eraFeedback").textContent=ok?`Tama! That's ${ERAS[eraCard.e].tag} (${ERAS[eraCard.e].short}).`:`Hindi. That one is ${ERAS[eraCard.e].tag} (${ERAS[eraCard.e].short}).`;
  $("eraFeedback").className="feedback "+(ok?"ok":"no");
  $("eraBtns").querySelectorAll("button").forEach(x=>x.disabled=true);
  $("eraScore").textContent=`${eraRight} / ${eraTotal}`;
});
$("eraNext").onclick=eraNext; $("eraReset").onclick=eraNew;
eraNew();

/* ---------- Palaruan: Pop Quiz ---------- */
const QUIZ=[
  {q:"What did Filipinos use to quickly gather crowds during EDSA Dos in 2001?",o:["Text messages","Facebook events","TV ads","Radio only"],a:0,why:"Text brigades spread the call to EDSA by SMS."},
  {q:"Which typhoon in 2009 sparked massive online relief efforts?",o:["Yolanda","Ondoy","Pepeng","Ulysses"],a:1,why:"Typhoon Ondoy (Ketsana) flooded Metro Manila in September 2009."},
  {q:"Which industry boomed in Metro Manila in the 2000s?",o:["Car manufacturing","BPO and call centers","Mining","Shipbuilding"],a:1,why:"The BPO boom built a night-shift, service economy."},
  {q:"Where did 2000s Filipino youth usually hang out?",o:["Co-working spaces","Malls like SM and Ayala","Esports arenas","Rooftop bars"],a:1,why:"Mega-malls were the main public square for tambay culture."},
  {q:"How did OFWs see their families in the 2000s?",o:["HD FaceTime","Webcams at internet cafes","VR headsets","Hologram calls"],a:1,why:"Families went to internet cafes for webcam kamustahan on Yahoo Messenger or Skype."},
  {q:"Which Taiwanese drama helped start the Asianovela craze?",o:["Meteor Garden","Crash Landing on You","Squid Game","Hotel del Luna"],a:0,why:"Meteor Garden opened the door to Asian pop in the Philippines."},
  {q:"Which band released the 2006 hit “Narda”?",o:["Hale","Kamikazee","Callalily","Sponge Cola"],a:1,why:"“Narda” is from Kamikazee's 2006 album Maharot."},
  {q:"What do we predict for P-Pop by 2030?",o:["It will disappear","It will stay local only","It will become a global presence","It will only be on radio"],a:2,why:"Our Workbook 3 predicts Filipinos will export their own pop culture."},
  {q:"What is one 2030 concern we predicted for Philippine politics?",o:["Fax machines","AI deepfakes and disinformation","Too few TV channels","Paper-only voting"],a:1,why:"AI-generated content will make media literacy central."}
];
let qOrder=[],qi=0,qScore=0,qAnswered=false;
function quizNew(){qOrder=shuffle([...QUIZ.keys()]);qi=0;qScore=0;quizShow();}
function quizShow(){
  qAnswered=false;$("quizNext").disabled=true;$("quizFeedback").textContent="";$("quizFeedback").className="feedback";
  if(qi>=qOrder.length){
    const msg=qScore===QUIZ.length?"Perfect! Certified Pinoy pop culture expert.":qScore>=6?"Galing! You really walked through the museum.":qScore>=4?"Not bad! Visit the wings again and retry.":"Balik ka sa museum and try again!";
    $("quizCount").textContent="Tapos na!";$("quizQ").textContent=`You got ${qScore} out of ${QUIZ.length}. ${msg}`;$("quizOpts").innerHTML="";$("quizScore").textContent=`${qScore} / ${QUIZ.length}`;return;
  }
  const Q=QUIZ[qOrder[qi]];
  $("quizCount").textContent=`Question ${qi+1} of ${QUIZ.length}`;$("quizScore").textContent=`Score: ${qScore}`;
  $("quizQ").textContent=Q.q;
  $("quizOpts").innerHTML=Q.o.map((o,i)=>`<button class="opt" data-i="${i}">${esc(o)}</button>`).join("");
  $("quizOpts").querySelectorAll(".opt").forEach(b=>b.onclick=()=>{
    if(qAnswered) return; qAnswered=true;
    const ok=+b.dataset.i===Q.a; if(ok) qScore++;
    $("quizOpts").querySelectorAll(".opt").forEach(x=>{x.disabled=true;if(+x.dataset.i===Q.a)x.classList.add("right");});
    if(!ok) b.classList.add("wrong");
    $("quizFeedback").textContent=(ok?"Tama! ":"Mali. ")+Q.why;$("quizFeedback").className="feedback "+(ok?"ok":"no");
    $("quizScore").textContent=`Score: ${qScore}`;$("quizNext").disabled=false;$("quizNext").focus();
  });
}
$("quizNext").onclick=()=>{qi++;quizShow();}; $("quizReset").onclick=quizNew;
quizNew();

/* ---------- Palaruan: Unli-txt simulator ---------- */
let load=20,unli=false;
const peso=v=>"₱"+v.toFixed(2);
function smsUpdate(){
  const n=$("smsText").value.length, parts=Math.max(1,Math.ceil(n/160));
  $("smsCount").textContent=`${parts*160-n||160}/${parts}`;
  $("loadBal").textContent=unli?"Load: UNLI-TXT":"Load: "+peso(load);
}
function send(count){
  const txt=$("smsText").value.trim();
  if(!txt){$("smsStatus").textContent="Type a message first.";return;}
  const parts=Math.ceil(txt.length/160), cost=unli?0:count*parts;
  if(cost>load){$("smsStatus").textContent=`Insufficient load! Need ${peso(cost)}. Pasaload ka muna.`;return;}
  load-=cost;$("smsStatus").textContent=count>1?`GM sent to ${count} contacts!${unli?"":" -"+peso(cost)}`:`Message sent!${unli?"":" -"+peso(cost)}`;
  $("smsText").value="";smsUpdate();
}
$("smsText").addEventListener("input",smsUpdate);
$("smsSend").onclick=()=>send(1);
$("smsGM").onclick=()=>send(10);
$("smsUnli").onclick=()=>{if(unli){$("smsStatus").textContent="You're already on Unli-txt.";return;}if(load<15){$("smsStatus").textContent="Unli-txt costs ₱15. Reload first.";return;}load-=15;unli=true;$("smsStatus").textContent="Registered! Unli-txt to all networks for 1 day.";smsUpdate();};
$("smsLoad").onclick=()=>{load+=20;$("smsStatus").textContent="Reloaded ₱20 at the sari-sari store.";smsUpdate();};
smsUpdate();

/* ---------- Palaruan: Guestbook ---------- */
function gbRender(){
  const notes=store.get("wpp-guestbook",[]);
  $("gbList").innerHTML=notes.length?`<span class="eyebrow">Your notes on this device</span>`+notes.slice().reverse().map(n=>`<div class="gb-note"><b>${esc(n.name)}</b> · ${esc(n.reaction)}<p>${esc(n.message)}</p></div>`).join(""):"";
}
$("gbForm").addEventListener("submit",async e=>{
  e.preventDefault();
  const note={name:$("gbName").value.trim(),reaction:$("gbReact").value,message:$("gbMsg").value.trim()};
  if(!note.name||!note.message) return;
  const notes=store.get("wpp-guestbook",[]);notes.push(note);store.set("wpp-guestbook",notes);gbRender();
  let sent=false;
  try{
    const body=new URLSearchParams(new FormData($("gbForm"))).toString();
    const r=await fetch("/",{method:"POST",headers:{"Content-Type":"application/x-www-form-urlencoded"},body});
    sent=r.ok;
  }catch(err){}
  $("gbFeedback").textContent=sent?"Salamat! Your note was sent to the curators.":"Salamat! Your note is saved on this device.";
  $("gbFeedback").className="feedback ok";
  $("gbMsg").value="";
});
gbRender();

renderAll();
show(location.hash.slice(1));
})();
</script>
</body>
</html>
