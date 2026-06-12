# Farmacology
DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Yurak-Qon Tomir Farmakologiyasi — Test</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@300;400;600;700&family=IBM+Plex+Mono:wght@400;600&display=swap');
:root{--bg:#0a0e1a;--surface:#111827;--surface2:#1a2235;--border:#1e2d45;--accent:#00d4ff;--accent2:#ff6b35;--green:#00e676;--yellow:#ffd600;--red:#ff1744;--purple:#c084fc;--text:#e8eaf0;--muted:#6b7a9a}
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'IBM Plex Sans',sans-serif;background:var(--bg);color:var(--text);min-height:100vh}
.header{background:linear-gradient(135deg,#0a0e1a,#0d1b2e,#0a1628);border-bottom:1px solid var(--border);padding:16px 18px;position:sticky;top:0;z-index:100}
.header-title{font-size:14px;font-weight:700;color:var(--accent);letter-spacing:2px;text-transform:uppercase}
.header-sub{font-size:11px;color:var(--muted);margin-top:3px}
.progress-bar{height:4px;background:var(--border)}
.progress-fill{height:100%;background:linear-gradient(90deg,var(--accent),var(--green));transition:width .3s}
.container{max-width:760px;margin:0 auto;padding:20px 14px 100px}

/* INTRO SCREEN */
#intro{text-align:center;padding:40px 20px}
.intro-icon{font-size:48px;margin-bottom:14px}
.intro-title{font-size:22px;font-weight:700;margin-bottom:8px}
.intro-sub{font-size:13px;color:var(--muted);margin-bottom:24px;line-height:1.6}
.intro-stats{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:24px}
.intro-stat{background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:14px}
.intro-stat-val{font-family:'IBM Plex Mono',monospace;font-size:24px;font-weight:700;color:var(--accent)}
.intro-stat-label{font-size:11px;color:var(--muted);margin-top:3px}

/* QUESTION CARD */
#quiz-area{display:none}
.q-progress{display:flex;align-items:center;gap:10px;margin-bottom:16px;font-family:'IBM Plex Mono',monospace;font-size:12px;color:var(--muted)}
.q-counter{font-weight:700;color:var(--accent)}
.q-flag{margin-left:auto;cursor:pointer;font-size:18px;opacity:.4;transition:opacity .2s}
.q-flag.flagged{opacity:1}
.test-card{background:var(--surface);border:1px solid var(--border);border-radius:14px;padding:24px}
.test-q-num{font-family:'IBM Plex Mono',monospace;font-size:11px;color:var(--accent);font-weight:600;display:block;margin-bottom:8px}
.test-q{font-size:15px;font-weight:600;margin-bottom:18px;line-height:1.6}
.test-options{display:flex;flex-direction:column;gap:9px}
.test-opt{padding:13px 16px;background:var(--surface2);border:1px solid var(--border);border-radius:10px;cursor:pointer;font-size:14px;transition:all .15s}
.test-opt:hover{border-color:var(--accent);color:var(--accent)}
.test-opt.selected{border-color:var(--accent);background:rgba(0,212,255,.08);color:var(--accent)}
.test-opt.correct{background:rgba(0,230,118,.1);border-color:var(--green);color:var(--green)}
.test-opt.wrong{background:rgba(255,23,68,.1);border-color:var(--red);color:var(--red)}
.opt-letter{font-family:'IBM Plex Mono',monospace;font-weight:700;margin-right:8px}
.test-explanation{margin-top:14px;padding:13px;background:rgba(0,212,255,.06);border-radius:10px;font-size:13px;color:#aac;display:none;line-height:1.65}
.test-nav{display:flex;gap:10px;align-items:center;margin-top:18px;flex-wrap:wrap}
.btn{padding:11px 20px;border-radius:10px;border:none;cursor:pointer;font-family:'IBM Plex Sans',sans-serif;font-size:13px;font-weight:600;transition:all .15s}
.btn-primary{background:var(--accent);color:#000}
.btn-primary:hover{opacity:.85}
.btn-primary:disabled{opacity:.3;cursor:not-allowed}
.btn-outline{background:transparent;border:1px solid var(--border);color:var(--text)}
.btn-outline:hover{border-color:var(--accent);color:var(--accent)}
.btn-outline:disabled{opacity:.3;cursor:not-allowed}
.btn-green{background:rgba(0,230,118,.15);border:1px solid var(--green);color:var(--green)}
.btn-block{width:100%;padding:14px;font-size:15px}

/* RESULTS SCREEN */
#results{display:none;text-align:center;padding:30px 14px}
.result-circle{width:160px;height:160px;border-radius:50%;border:8px solid var(--border);display:flex;align-items:center;justify-content:center;margin:0 auto 20px;position:relative}
.result-pct{font-family:'IBM Plex Mono',monospace;font-size:36px;font-weight:700;color:var(--accent)}
.result-frac{font-size:12px;color:var(--muted);margin-top:4px}
.result-msg{font-size:16px;font-weight:600;margin-bottom:6px}
.result-sub{font-size:13px;color:var(--muted);margin-bottom:24px}
.result-breakdown{background:var(--surface);border:1px solid var(--border);border-radius:12px;padding:16px;margin-bottom:20px;text-align:left}
.breakdown-row{display:flex;justify-content:space-between;padding:7px 0;font-size:13px;border-bottom:1px solid var(--border)}
.breakdown-row:last-child{border-bottom:none}
.breakdown-cat{color:var(--muted)}
.breakdown-score{font-family:'IBM Plex Mono',monospace;font-weight:600}
.review-item{background:var(--surface);border:1px solid var(--border);border-left:3px solid var(--red);border-radius:10px;padding:14px;margin-bottom:10px;text-align:left}
.review-item.correct-item{border-left-color:var(--green)}
.review-q{font-size:13px;font-weight:600;margin-bottom:8px}
.review-ans{font-size:12px;color:#aac;line-height:1.6}
.review-ans .your{color:var(--red)}
.review-ans .right{color:var(--green)}
.section-label{font-size:11px;font-weight:700;letter-spacing:1.5px;color:var(--muted);text-transform:uppercase;margin:24px 0 10px;text-align:left}
@media(max-width:600px){.intro-stats{grid-template-columns:repeat(3,1fr)}.result-circle{width:130px;height:130px}.result-pct{font-size:28px}}
</style>
</head>
<body>

<div class="header">
  <div class="header-title">💉 Yurak-Qon Tomir Farmakologiyasi</div>
  <div class="header-sub">Antigipertenziv · Antianginal · Kardiotonik dorilar</div>
</div>
<div class="progress-bar"><div class="progress-fill" id="progressFill" style="width:0%"></div></div>

<div class="container">

<!-- INTRO -->
<div id="intro">
  <div class="intro-icon">🫀</div>
  <div class="intro-title">YQT Farmakologiya Testi</div>
  <div class="intro-sub">Antigipertenziv, antianginal va kardiotonik dorilar bo'yicha 38 ta savol. Har bir savol uchun javobni belgilang, oxirida natija va izohlar bilan chiqadi.</div>
  <div class="intro-stats">
    <div class="intro-stat"><div class="intro-stat-val">38</div><div class="intro-stat-label">Savol</div></div>
    <div class="intro-stat"><div class="intro-stat-val">5</div><div class="intro-stat-label">Mavzu</div></div>
    <div class="intro-stat"><div class="intro-stat-val">~25</div><div class="intro-stat-label">Daqiqa</div></div>
  </div>
  <button class="btn btn-primary btn-block" onclick="startQuiz()">▶ Testni boshlash</button>
</div>

<!-- QUIZ -->
<div id="quiz-area">
  <div class="q-progress">
    <span class="q-counter" id="qCounter">1 / 38</span>
    <span id="qCatLabel"></span>
    <span class="q-flag" id="qFlag" onclick="toggleFlag()">🚩</span>
  </div>
  <div class="test-card">
    <div class="test-q" id="qText"></div>
    <div class="test-options" id="qOptions"></div>
    <div class="test-explanation" id="qExp"></div>
  </div>
  <div class="test-nav">
    <button class="btn btn-outline" id="prevBtn" onclick="prevQ()">← Oldingi</button>
    <button class="btn btn-primary" id="nextBtn" onclick="nextQ()">Keyingi →</button>
    <button class="btn btn-green" id="finishBtn" onclick="finishQuiz()" style="display:none;margin-left:auto">✅ Yakunlash</button>
  </div>
</div>

<!-- RESULTS -->
<div id="results">
  <div class="result-circle"><div><div class="result-pct" id="resultPct">0%</div><div class="result-frac" id="resultFrac">0/38</div></div></div>
  <div class="result-msg" id="resultMsg"></div>
  <div class="result-sub" id="resultSub"></div>

  <div class="result-breakdown" id="breakdown"></div>

  <button class="btn btn-primary btn-block" onclick="restartQuiz()">🔄 Qaytadan boshlash</button>

  <div class="section-label">❌ Xato javoblar — Tahlil</div>
  <div id="reviewWrong"></div>

  <div class="section-label">✅ To'g'ri javoblar</div>
  <div id="reviewCorrect"></div>
</div>

</div>

<script>
const questions = [
  // ===== ANTIGIPERTENZIV — AKF, ARB, Renin =====
  {cat:'AKF/ARB', q:"AKF ingibitorlari (-pril) qaysi fermentni bloklaydi?", opts:["Reninni","Angiotenzin I → Angiotenzin II aylantiruvchi fermentni","Aldosteron sintazni","Fosfodiesteraza III"], ans:1, exp:"AKF (Angiotenzin Konvertlovchi Ferment) ingibitorlari — Angiotenzin I ni Angiotenzin II ga aylantiruvchi fermentni bloklaydi. Natijada AT-II↓ → vazokonstriksiya↓, aldosteron↓, AB↓."},
  {cat:'AKF/ARB', q:"AKF ingibitorlarining xarakterli nojo'ya ta'siri — quruq yo'tal sababi?", opts:["Histamin ko'payishi","Bradikinin parchalanishi kamayib, o'pkada to'planishi","Prostaglandin kamayishi","Aldosteron oshishi"], ans:1, exp:"AKF fermenti bradikininni ham parchalaydi. AKF bloklansa → bradikinin↑ → o'pkada to'planib quruq yo'tal va angioedema chaqiradi."},
  {cat:'AKF/ARB', q:"AKF ingibitorlari + K+ saqlovchi diuretiklar birgalikda berilganda xavfi?", opts:["Gipokalemiya", "Giperkalemiya", "Gipernatremiya", "Gipokalsemiya"], ans:1, exp:"Ikkisi ham K+ ni saqlaydi (AKF ingibitorlari aldosteron↓ orqali, K+ saqlovchi diuretiklar to'g'ridan-to'g'ri) → xavfli GIPERKALEMIYA."},
  {cat:'AKF/ARB', q:"Angiotenzin II retseptor blokatorlari (-sartan) qaysi retseptorni bloklaydi?", opts:["AT2", "AT1", "Beta-1", "D1"], ans:1, exp:"Losartan, Valsartan kabi -sartan dorilar AT1 retseptorini bloklaydi. AT1 orqali vazokonstriksiya, aldosteron↑ va NA chiqishi amalga oshadi — bularning hammasi bloklanadi."},
  {cat:'AKF/ARB', q:"Aliskiren qaysi bosqichda ta'sir qiladi?", opts:["AT-II retseptorini bloklaydi","To'g'ridan-to'g'ri reninni ingibirlaydi","AKF ni bloklaydi","Aldosteron retseptorini bloklaydi"], ans:1, exp:"Aliskiren — bevosita renin ingibitori. Renin-angiotenzin tizimining ENG BOSHIDA ta'sir qiladi → Angiotenzin I va II hosil bo'lishi kamayadi."},
  {cat:'AKF/ARB', q:"AKF ingibitori + Tiazid birga berilganda nima yuz beradi?", opts:["AB o'zgarmaydi","Tiazid suyuqlik hajmini kamaytirib, AKF ingibitor ta'sirini kuchaytiradi → gipotoniya xavfi","Faqat tiazid ishlaydi","Giperkalemiya"], ans:1, exp:"Tiazid Na+/H2O chiqarib qon hajmini kamaytiradi → bu AKF ingibitorining gipotenziv ta'sirini KUCHAYTIRADI → gipotoniya xavfi oshadi."},

  // ===== Ca KANAL BLOKATORLARI =====
  {cat:'Ca-blokator', q:"Ca²⁺ kanal blokatorlari (Verapamil, Diltiazem, Nifedipin) qaysi tip kanallarini bloklaydi?", opts:["T-tipli", "L-tipli", "N-tipli", "P-tipli"], ans:1, exp:"Bularning barchasi L-tipli Ca²⁺ kanallarini bloklaydi — qon tomir silliq mushaklariga ta'sir qilib, Ca²⁺ kirishini to'xtatadi → muskul bo'shashadi, vazodilyatatsiya."},
  {cat:'Ca-blokator', q:"Non-digidropiridin Ca-blokatorlari (Verapamil, Diltiazem) qaysi nojo'ya ta'sirga ko'proq moyil?", opts:["Refleksli taxikardiya", "Bradikardiya, qabziyat", "Teri qizarishi", "Gipertenziya"], ans:1, exp:"Non-digidropiridinlar (Verapamil, Diltiazem) — yurakka ko'proq ta'sir qiladi → BRADIKARDIYA va konstipatsiya (qabziyat) xarakterli. Digidropiridinlar (Amlodipin, Nifedipin) esa refleksli taxikardiya beradi."},
  {cat:'Ca-blokator', q:"β-blokator + Verapamil kombinatsiyasi nega XAVFLI?", opts:["Ikkisi ham AB oshiradi","Ikkisi ham SA va AV tugunga depressiv ta'sir qiladi → yurak yetishmovchiligi xavfi","Hech qanday xavf yo'q","Ikkisi bir-birini neytrallaydi"], ans:1, exp:"Ikkala dori ham SA va AV tugunlarga DEPRESSIV ta'sir qiladi — birgalikda berilsa qo'shimcha ta'sir → AV blokada, og'ir bradikardiya, yurak yetishmovchiligi. Bu kombinatsiya ISHLATILMAYDI!"},

  // ===== DIURETIKLAR =====
  {cat:'Diuretiklar', q:"Tiazid diuretiklari (Xlortiazid) qayerda ta'sir qiladi?", opts:["Genle qovuzlog'ida","Distal naychada Na+-Cl- simportini ingibirlaydi","Proksimal naychada","Yig'uvchi naylarda"], ans:1, exp:"Tiazidlar nefronning DISTAL naychasida Na+-Cl- ko-transporterini bloklaydi → Na+ va H2O chiqishi↑ → AB↓."},
  {cat:'Diuretiklar', q:"Tiazid diuretiklarining keksa bemorlardagi afzalligi nimada?", opts:["Ca²⁺ chiqarishni oshiradi → suyak mustahkamlanadi","Siydikda Ca²⁺ chiqishini kamaytiradi → suyak sinishini kamaytiradi","Faqat arzon bo'lgani uchun","Hech qanday afzalligi yo'q"], ans:1, exp:"Tiazidlar siydik bilan Ca²⁺ ekskretsiyasini KAMAYTIRADI (giperkalsemiyaga moyillik) — bu keksalarda suyak sinishini kamaytiradi, lekin giperkalsemiya nojo'ya ta'sir sifatida hisobga olinadi."},
  {cat:'Diuretiklar', q:"Furosemid (qovuzloq diuretiki) qaysi joyda ta'sir qiladi?", opts:["Distal naycha","Genle qovuzlog'ida Na+-K+-2Cl- simportini ingibirlaydi","Yig'uvchi nay","Proksimal naycha"], ans:1, exp:"Furosemid Genle qovuzlog'ining yuqori qismida Na+-K+-2Cl- ko-transporterini bloklaydi — kuchli diuretik, IV 5 daqiqada, peroral 30 daqiqada ta'sir qiladi."},
  {cat:'Diuretiklar', q:"Spironolakton qanday mexanizm bilan K+ saqlaydi?", opts:["Na+ kanalini to'g'ridan-to'g'ri bloklaydi","Yig'uvchi naylarda aldosteron mineralokortikoid retseptorini bloklaydi","K+ kanalini ochadi","Reninni bloklaydi"], ans:1, exp:"Spironolakton — aldosteron retseptori antagonisti. Aldosteron ta'siri yo'qoladi → Na+ reabsorbsiyasi↓, K+ sekretsiyasi↓ (K+ saqlanadi). Amilorid esa to'g'ridan Na+ kanalini bloklaydi."},
  {cat:'Diuretiklar', q:"Spironolakton erkaklarda ginekomastiya chaqirishi sababi?", opts:["Estrogen retseptorini stimullaydi","Androgen retseptorlarini bloklaydi","Testosteron sintezini oshiradi","Prolaktinni oshiradi"], ans:1, exp:"Spironolakton androgen retseptorlarini ham BLOKLAYDI (antiandrogen ta'sir) — natijada erkaklarda ginekomastiya va jinsiy disfunksiya kelib chiqishi mumkin."},

  // ===== SIMPATOLITIKLAR =====
  {cat:'Simpatolitik', q:"Klonidin qaysi retseptorni stimullaydi va qanday ta'sir qiladi?", opts:["Periferik α1 — vazokonstriksiya","MNS dagi α2 — simpatik aktivlikni susaytirib AB↓","β1 — yurak urishini oshiradi","D1 — vazodilyatatsiya"], ans:1, exp:"Klonidin — markaziy ta'sirli simpatolitik. MNS dagi α2-adrenoretseptorlarni stimullab simpatik chiqishni KAMAYTIRADI → AB↓."},
  {cat:'Simpatolitik', q:"Klonidinni TO'SATDAN to'xtatish qanday xavf tug'diradi?", opts:["Hech qanday xavf yo'q","Reflekslik gipertenziya (rebound) — gipertenziv kriz","Bradikardiya","Gipoglikemiya"], ans:1, exp:"Klonidin to'satdan to'xtatilsa → kompensator simpatik aktivlik kuchayib REBOUND gipertenziya/kriz rivojlanishi mumkin. Dozani sekin-asta kamaytirish kerak."},
  {cat:'Simpatolitik', q:"α-metildofa qanday nojo'ya ta'sirga sabab bo'lishi mumkin?", opts:["Aplastik anemiya","Gepatotoksiklik va autoimmun gemolitik anemiya","Buyrak toshi","Osteoporoz"], ans:1, exp:"α-metildofa — gepatotoksik ta'sir va AUTOIMMUN GEMOLITIK ANEMIYA chaqirishi mumkin. Homiladorlikda nisbatan xavfsiz hisoblanadi (eklampsiyada qo'llanilgan)."},
  {cat:'Simpatolitik', q:"Selektiv β1-blokatorlar (Atenolol, Metoprolol) qaysi mexanizm orqali AB ni kamaytiradi?", opts:["Faqat bronxlarga ta'sir qiladi","Yurak urish soni va qisqaruvchanligini ↓ + buyrakda renin ajralishini ↓","Vazodilyatatsiya chaqiradi","Aldosteronni bloklaydi"], ans:1, exp:"β-blokatorlar: 1) Yurakda — urish soni↓, qisqarish kuchi↓, otib berish↓ → AB↓; 2) Buyrakda — renin ajralishi↓ → Angiotenzin II↓ → AB↓."},
  {cat:'Simpatolitik', q:"β-blokatorlarning xarakterli nojo'ya ta'siri nima?", opts:["Tromboz","Bronxospazm va jinsiy disfunksiya","Gipernatremiya","Aplastik anemiya"], ans:1, exp:"β-blokatorlar (ayniqsa noselektiv — Propranolol) β2-retseptorlarni ham bloklab BRONXOSPAZM chaqiradi (astma bemorlarga xavfli) + jinsiy disfunksiya."},
  {cat:'Simpatolitik', q:"Prazozin (α1-blokator) yuborishda nima uchun ehtiyotkorlik talab qilinadi?", opts:["Aplastik anemiya xavfi","Birinchi doza ta'sirida postural (ortostatik) gipotenziya kuchli bo'lishi mumkin","Giperkalemiya xavfi","Bronxospazm"], ans:1, exp:"Prazozin — selektiv α1-blokator. Birinchi doza katta bo'lsa kuchli postural gipotenziya (yotgan/o'tirgandan turganda AB keskin tushishi) kelib chiqadi. Shu uchun kichik dozadan (1mg) boshlanadi."},
  {cat:'Simpatolitik', q:"Noselektiv α-adrenoblokatorlar (Fenoksibenzamin) presinaptik α2 ni bloklashi qanday natija beradi?", opts:["Noradrenalin chiqishi kamayadi","Noradrenalin chiqishi oshadi (refleksli taxikardiya kuchayadi)","Hech qanday o'zgarish bo'lmaydi","Dofamin chiqishi to'xtaydi"], ans:1, exp:"Presinaptik α2 retseptorlar — salbiy teskari aloqa orqali NA chiqishini cheklaydi. Bu retseptor bloklansa → NA chiqishi KO'PAYADI → refleksli taxikardiya kuchli bo'ladi."},

  // ===== VAZODILATATORLAR =====
  {cat:'Vazodilatator', q:"Minoksidil va Diazoksid qanday mexanizm bilan vazodilyatatsiya chaqiradi?", opts:["NO ajratadi","K+ kanallarini aktivlab, hujayradan K+ chiqishini oshiradi → giperpolyarizatsiya","Ca²⁺ kanalini bloklaydi","β-retseptorni stimullaydi"], ans:1, exp:"Minoksidil/Diazoksid — K+ kanal aktivatorlari. K+ chiqishi↑ → tomir silliq mushak giperpolyarizatsiyasi → Ca²⁺ kanallar ochilmaydi → vazodilyatatsiya, AB↓."},
  {cat:'Vazodilatator', q:"Na-nitroprussid va Gidralazinning umumiy ta'sir mexanizmi?", opts:["K+ kanalini ochadi","Endoteliydan NO chiqarilishini oshiradi → vazodilyatatsiya","Aldosteronni bloklaydi","Renin ingibirlaydi"], ans:1, exp:"Ikkalasi ham endoteliydan NO (azot oksidi) chiqishini oshiradi → guanilatsiklaza aktivlanadi → vazodilyatatsiya, AB↓."},
  {cat:'Vazodilatator', q:"Na-nitroprussidni uzoq vaqt qo'llashda qaysi toksik modda to'planishi mumkin?", opts:["Bradikinin","Sianid", "Histamin", "Kaliy"], ans:1, exp:"Na-nitroprussid metabolizmida SIANID (CN-) hosil bo'ladi. Uzoq/yuqori dozada qo'llanganda sianid intoksikatsiyasi xavfi bor — shuning uchun monitoring kerak."},
  {cat:'Vazodilatator', q:"Diazoksid (vazodilatator) qaysi nojo'ya ta'siri tiazid hosilasi ekanligi bilan bog'liq?", opts:["Bronxospazm","Giperglikemiya","Aplastik anemiya","Giperkalemiya"], ans:1, exp:"Diazoksid kimyoviy jihatdan tiazid hosilasi — pankreasdan insulin ajralishini kamaytiradi → GIPERGLIKEMIYA chaqirishi mumkin."},
  {cat:'Vazodilatator', q:"Fenoldopam qaysi retseptorga ta'sir qilib vazodilyatatsiya chaqiradi?", opts:["β1", "D1 (dofamin)", "α1", "AT1"], ans:1, exp:"Fenoldopam — D1 (dofamin) retseptor agonisti, qon tomirlarda vazodilyatatsiya chaqiradi. Nojo'ya: ko'z ichi bosimini oshirishi mumkin (glaukoma bemorlarda ehtiyotkorlik)."},

  // ===== GIPOTENZIV (qon bosimi past) DORILAR =====
  {cat:'Gipotenziv', q:"Angiotenzinamidning yurakka ta'siri qanday?", opts:["Yurak urishini sezilarli oshiradi","Yurakka va uning qon ta'minotiga deyarli ta'sir qilmaydi, faqat tomir tonusini oshiradi","Yurakni to'xtatadi","Bradikardiya chaqiradi"], ans:1, exp:"Angiotenzinamid — faqat periferik tomir tonusini oshiradi, yurak faoliyatiga deyarli ta'sir qilmaydi. O'tkir arterial gipotenziyada IV infuziya sifatida ishlatiladi."},
  {cat:'Gipotenziv', q:"Dofamin kam va yuqori dozada qanday farqli ta'sir ko'rsatadi?", opts:["Ikki dozada bir xil ta'sir","Kam doza — D1 (vazodilyatatsiya); Yuqori doza — α1 (vazokonstriksiya, AB↑)","Faqat yuqori dozada ishlaydi","Kam dozada AB ni oshiradi, yuqorida pasaytiradi"], ans:1, exp:"Dofamin doza-bog'liq ta'sir: Kam doza → D1 retseptor → vazodilyatatsiya; Yuqori doza → α1-adrenoretseptor → vazokonstriksiya → AB↑."},
  {cat:'Gipotenziv', q:"Surunkali gipotenziyada qaysi guruh dorilari qo'llaniladi?", opts:["AKF ingibitorlari", "Vazomotor markaz qo'zg'atuvchilari (Kofein, Kordiamin)", "Tiazid diuretiklari", "β-blokatorlar"], ans:1, exp:"Surunkali (xroniq) gipotenziyada: 1) Vazomotor markaz qo'zg'atuvchilari (Kofein, Kordiamin), 2) Simpatomimetiklar (Efedrin), 3) Mineralokortikoidlar (Deoksikortikosteron)."},

  // ===== ANTIANGINAL — NITRATLAR =====
  {cat:'Nitratlar', q:"Nitratlarning asosiy ta'sir mexanizmi qanday zanjir orqali boradi?", opts:["NO → guanilatsiklaza → cGMP↑ → MLCK fosforillanishi blok → Ca²⁺ kirishi blok → bo'shashish","cAMP → PKA → Ca²⁺ kirishi↑","Na+-K+-ATFaza ingibisiyasi","β-retseptor stimulyatsiyasi"], ans:0, exp:"Nitratlar → NO ajraladi → Guanilatsiklaza aktivlanadi → cGMP↑ → MLCK (myosin light chain kinase) fosforillanishi bloklanadi → Ca²⁺ kirishi to'xtaydi → vazodilyatatsiya."},
  {cat:'Nitratlar', q:"Nitratlar stenokardiyada qaysi mexanizm orqali ko'proq foyda beradi?", opts:["Arterial dilyatatsiya orqali kislorodga talabni oshirish","Venodilyatatsiya — preload kamayishi → O2 talab↓", "Yurak urishini oshirish", "Aldosteronni bloklash"], ans:1, exp:"Nitratlar ASOSAN venodilyatatsiya chaqiradi → venoz qaytim (preload)↓ → yurak ish yuki↓ → O2 ga talab↓. Shu bilan birga koronar dilyatatsiya → O2 yetkazilishi↑."},
  {cat:'Nitratlar', q:"Nitratlarning xarakterli nojo'ya ta'siri — qaysi javob TO'G'RI EMAS?", opts:["Postural gipotenziya", "Refleksli taxikardiya", "Metgemoglobinemiya", "Giperkalemiya"], ans:3, exp:"Nitratlar nojo'ya ta'sirlari: Metgemoglobinemiya, Tolerantlik, Postural gipotenziya, Refleksli taxikardiya — hammasi vazodilyatatsiya bilan bog'liq. Giperkalemiya NITRATLARGA xos emas."},
  {cat:'Nitratlar', q:"Nitrat + β-blokator (Propranolol) kombinatsiyasi qanday afzallik beradi?", opts:["Ikkisi ham bir xil ta'sir qiladi, foydasi yo'q","Bir-birining nojo'ya ta'sirini oldini oladi — nitrat refleks taxikardiyani propranolol oldini oladi","Faqat AB ni oshiradi","Bradikardiya kuchayadi va xavfli"], ans:1, exp:"Nitrat → refleksli taxikardiya chaqiradi, lekin Propranolol (β-blokator) buni oldini oladi. Propranolol esa β2 blokadasi orqali koronar spazm xavfini tug'dirishi mumkin, buni esa nitratlar oldini oladi — bir-birini to'ldiradi."},
  {cat:'Nitratlar', q:"Trimetazidin antiishemik ta'sirini qanday mexanizm bilan amalga oshiradi?", opts:["Vazodilyatatsiya chaqiradi","Yog' kislotalari oksidlanishini bloklab, energiya uchun glukoza oksidlanishiga o'tkazadi → O2 talabi↓","β-retseptorni bloklaydi","Na+ kanalini bloklaydi"], ans:1, exp:"Trimetazidin — metabolik antianginal. Yog' kislotalari oksidlanishi (ko'proq O2 talab qiladi) ni bloklaydi → miokard glukoza oksidlanishiga o'tadi (kamroq O2) → O2 ga ehtiyoj↓."},
  {cat:'Nitratlar', q:"Ranolazin qaysi kanalni bloklab ta'sir qiladi?", opts:["L-tipli Ca²⁺ kanali","Sekin tipdagi (late) Na+ kanali","K+ kanali","T-tipli Ca²⁺ kanali"], ans:1, exp:"Ranolazin — ishemiya paytida aktivlashuvchi SEKIN Na+ kanallarini bloklaydi → Na+-Ca²⁺ oqimi↓ → miokard qisqarishi↓ → O2 talab↓. Yog' kislota oksidlanishini ham ingibirlaydi."},

  // ===== KARDIOTONIK — DIGOKSIN =====
  {cat:'Digoksin', q:"Digoksin (yurak glikozidi) qaysi pompani ingibirlaydi va asosiy natijasi?", opts:["Ca²⁺-ATFaza — hujayra ichi Ca²⁺↓","Na+-K+-ATFaza — hujayra ichi Na+↑ → Ca²⁺ almashinuvi orqali hujayra ichi Ca²⁺↑","K+-H+ ATFaza","Na+-Cl- simporter"], ans:1, exp:"Digoksin Na+-K+-ATFaza ni ingibirlaydi → hujayra ichi Na+↑ → Na+-Ca²⁺ almashtirgich ishi kamayadi → Ca²⁺ chiqishi↓ → hujayra ichi Ca²⁺↑ → miokard qisqarishi↑ (musbat inotrop)."},
  {cat:'Digoksin', q:"Digoksin yurak urish soniga qanday ta'sir qiladi (kam doza)?", opts:["Tahikardiya chaqiradi (simpatik orqali)","n.vagus stimullanishi orqali bradikardiya","Ta'sir qilmaydi","AV blokadani yo'qotadi"], ans:1, exp:"Kam dozada Digoksin n.vagus (parasimpatik) ni stimullaydi → yurak urishi KAMAYADI (bradikardiya). Yuqori dozada esa simpatik aktivlik oshib taxikardiya/aritmiya chaqirishi mumkin."},
  {cat:'Digoksin', q:"Digoksin EKG da qanday o'zgarishlar chaqiradi?", opts:["QT интервал uzayishi","P-R interval uzayishi, ST depressiya, T tish inversiyasi","QRS kengayishi","P tish yo'qolishi"], ans:1, exp:"Digoksin tipik EKG o'zgarishlari: P-R interval uzayishi (AV o'tkazuvchanlik↓), ST segment depressiyasi, T tishning inversiyasi — bu 'digoksin effekti' deyiladi (toksiklik emas)."},
  {cat:'Digoksin', q:"Gipokalemiya Digoksin toksikligini qanday oshiradi?", opts:["Digoksin metabolizmini tezlashtiradi","Gipokalemiyada Digoksinning Na+-K+-ATFaza ga birikishi ortadi → toksiklik↑","Hech qanday bog'liqlik yo'q","Digoksin chiqarilishini tezlashtiradi"], ans:1, exp:"K+ va Digoksin Na+-K+-ATFaza ning bir xil bog'lanish joyiga ta'sir qiladi — K+ kam bo'lsa, Digoksin OSON va KO'P bog'lanadi → ta'siri (va toksikligi) ortadi. Tiazid/Furosemid (gipokalemiya chaqiradi) + Digoksin = xavfli kombinatsiya."},
  {cat:'Digoksin', q:"Digoksin zaharlanishida (toksiklik) antidot sifatida nima qo'llaniladi?", opts:["Atropin","Digoksin antiteloси (Digibind) + K+, Mg²+ preparatlari","Adrenalin","Vitamin K"], ans:1, exp:"Digoksin toksikligida: Digibind (digoksinga qarshi antitelo) — to'g'ridan-to'g'ri antidot; shuningdek K+ va Mg²+ preparatlari (Panangin, Asparkam) — elektrolit balansini tiklash uchun beriladi."},
  {cat:'Digoksin', q:"Digoksin qo'llash MUMKIN BO'LMAGAN holat qaysi?", opts:["Yurak yetishmovchiligi","Gipokalemiya, yaqqol bradikardiya, AV blokada","Atrial fibrillyatsiya","Surunkali yurak kasalligi"], ans:1, exp:"Digoksin gipokalemiya, yaqqol bradikardiya, AV blokada va o'tkir infeksion miokarditda QARSHI KO'RSATMA — chunki bu holatlarda toksiklik/aritmiya xavfi keskin oshadi."},

  // ===== KARDIOTONIK — NOGLIKOZID =====
  {cat:'Noglikozid', q:"Dobutamin o'rta dozada qaysi mexanizm orqali miokard qisqarishini oshiradi?", opts:["Na+-K+-ATFazani bloklaydi","β1-adrenoretseptor stimulyatsiyasi → cAMP↑ → hujayra ichi Ca²⁺↑","Fosfodiesterazani aktivlaydi","Troponin C ga bog'lanadi"], ans:1, exp:"Dobutamin — β1-adrenoretseptor stimulyatori → cAMP↑ → Ca²⁺ kanallari aktivlanadi → hujayra ichi Ca²⁺↑ → miokard qisqarishi↑ (musbat inotrop), Na+-K+-ATFaza ga ta'sir qilmaydi."},
  {cat:'Noglikozid', q:"Amrinon va Milrinon qaysi fermentni ingibirlab ta'sir qiladi?", opts:["Na+-K+-ATFaza","Fosfodiesteraza III — cAMP saqlanishini oshiradi","Guanilatsiklaza","Adenilatsiklaza"], ans:1, exp:"Amrinon/Milrinon — Fosfodiesteraza III ingibitorlari. PDE-3 odatda cAMP ni parchalaydi; bloklansa cAMP saqlanadi/ko'payadi → Ca²⁺↑ → miokard qisqarishi↑ + vazodilyatatsiya (qo'shimcha ta'sir)."},
  {cat:'Noglikozid', q:"Levosimendan qanday noyob mexanizm bilan ta'sir qiladi?", opts:["Na+-K+-ATFazani bloklaydi","Troponin C ga bog'lanib Ca²⁺ ga sezuvchanlikni oshiradi + K+ kanal aktivatori (vazodilyatatsiya)","β1-retseptorni bloklaydi","AKF ni ingibirlaydi"], ans:1, exp:"Levosimendan — ikki tomonlama: 1) Troponin C ga bog'lanib miofibrillalarning Ca²⁺ ga sezuvchanligini oshiradi (qo'shimcha O2 sarflamasdan qisqarish↑); 2) Tomir silliq mushaklarida K+ kanal aktivatori → vazodilyatatsiya."},
  {cat:'Noglikozid', q:"Levosimendanning afzalligi boshqa kardiotoniklardan nimada?", opts:["Doimiy ichish kerak","O2 sarfini oshirmasdan qisqarish kuchini oshiradi, ta'siri 1 haftagacha davom etadi","Faqat peroral ishlatiladi","Hech qanday afzalligi yo'q"], ans:1, exp:"Levosimendan — qisqarish kuchini OSHIRADI lekin qo'shimcha O2 sarfini talab qilmaydi (boshqa inotroplardan farqi). Yuborish 6-24 soat, lekin ta'siri 1 HAFTAGACHA davom etadi — o'tkir YYE da qo'llaniladi."},
  {cat:'Noglikozid', q:"Levosimendanning xarakterli nojo'ya ta'siri?", opts:["Bronxospazm","AB↓ va Gipokalemiya","Aplastik anemiya","Giperglikemiya"], ans:1, exp:"Levosimendan vazodilyatatsiya chaqirgani uchun AB↓ (gipotenziya) va Gipokalemiya nojo'ya ta'sirlari kuzatiladi."},

  // ===== ARALASH / QIYOSIY =====
  {cat:'Qiyosiy', q:"Digoksin va Dobutaminning hujayra ichi Ca²⁺ ni oshirish YO'LI farqi?", opts:["Ikkisi ham bir xil yo'l bilan", "Digoksin — Na+-K+-ATFaza orqali bilvosita; Dobutamin — β1→cAMP orqali to'g'ridan-to'g'ri", "Digoksin to'g'ridan-to'g'ri, Dobutamin bilvosita", "Ikkisi ham fosfodiesterazani bloklaydi"], ans:1, exp:"Digoksin: Na+-K+-ATFaza blokadasi → Na+↑ → Na+-Ca²⁺ almashinuv orqali BILVOSITA Ca²⁺↑. Dobutamin: β1 → cAMP↑ → Ca²⁺ kanal ochilishi → TO'G'RIDAN-TO'G'RI Ca²⁺↑."},
  {cat:'Qiyosiy', q:"Quyidagi qaysi dori GURUHI faqat \"o'tkir yurak dekompensatsiyasi\"da qo'llaniladi?", opts:["AKF ingibitorlari va ARB", "Amrinon/Milrinon va Levosimendan", "Tiazid diuretiklari", "Statinlar"], ans:1, exp:"Amrinon/Milrinon (PDE-3 inhibitorlari) va Levosimendan — ikkisi ham o'TKIR yurak dekompensatsiyasi bosqichlarida qo'llaniladi (surunkali davolashda emas)."},
  {cat:'Qiyosiy', q:"Qaysi dori klassi giperkaliyemiya VA giperglikemiyaga sabab bo'lishi mumkin (turlicha vakillar)?", opts:["Faqat AKF ingibitorlari","K+ saqlovchi diuretiklar (giperkaliyemiya) va Diazoksid (giperglikemiya)","Faqat nitratlar","Faqat β-blokatorlar"], ans:1, exp:"K+ saqlovchi diuretiklar (Spironolakton, Amilorid) → giperkaliyemiya. Diazoksid (tiazid hosilasi, vazodilatator) → giperglikemiya (insulin sekretsiyasini kamaytiradi)."},
];

let curQ=0, answered=new Array(questions.length).fill(null), flagged=new Set();

function startQuiz(){
  document.getElementById('intro').style.display='none';
  document.getElementById('quiz-area').style.display='block';
  renderQ();
}

function renderQ(){
  const q=questions[curQ];
  document.getElementById('qCounter').textContent=`${curQ+1} / ${questions.length}`;
  document.getElementById('qCatLabel').innerHTML=`<span style="background:rgba(0,212,255,.1);color:var(--accent);padding:2px 8px;border-radius:4px;font-size:11px">${q.cat}</span>`;
  document.getElementById('qFlag').classList.toggle('flagged', flagged.has(curQ));
  document.getElementById('qText').textContent=q.q;
  document.getElementById('progressFill').style.width=((curQ+1)/questions.length*100)+'%';

  let optsHtml='';
  q.opts.forEach((o,i)=>{
    let cls = answered[curQ]===i ? 'selected':'';
    optsHtml+=`<div class="test-opt ${cls}" onclick="selectOpt(${i})"><span class="opt-letter">${String.fromCharCode(65+i)}.</span>${o}</div>`;
  });
  document.getElementById('qOptions').innerHTML=optsHtml;
  document.getElementById('qExp').style.display='none';

  document.getElementById('prevBtn').disabled = curQ===0;
  document.getElementById('nextBtn').style.display = curQ===questions.length-1 ? 'none':'inline-block';
  document.getElementById('finishBtn').style.display = curQ===questions.length-1 ? 'inline-block':'none';
}

function selectOpt(i){
  answered[curQ]=i;
  renderQ();
}

function toggleFlag(){
  if(flagged.has(curQ)) flagged.delete(curQ);
  else flagged.add(curQ);
  document.getElementById('qFlag').classList.toggle('flagged');
}

function nextQ(){ if(curQ<questions.length-1){curQ++; renderQ();} }
function prevQ(){ if(curQ>0){curQ--; renderQ();} }

function finishQuiz(){
  document.getElementById('quiz-area').style.display='none';
  document.getElementById('results').style.display='block';
  document.getElementById('progressFill').style.width='100%';

  let score=0;
  const catScores={};
  questions.forEach((q,i)=>{
    if(!catScores[q.cat]) catScores[q.cat]={correct:0,total:0};
    catScores[q.cat].total++;
    if(answered[i]===q.ans){score++; catScores[q.cat].correct++;}
  });

  const pct=Math.round(score/questions.length*100);
  document.getElementById('resultPct').textContent=pct+'%';
  document.getElementById('resultFrac').textContent=`${score}/${questions.length}`;

  let msg, sub;
  if(pct>=85){msg="🎉 A'lo natija!";sub="Siz materialni juda yaxshi o'zlashtirgansiz!";}
  else if(pct>=70){msg="👍 Yaxshi natija!";sub="Yana bir oz takrorlash kifoya.";}
  else if(pct>=50){msg="📚 O'rtacha natija";sub="Xato javoblarni diqqat bilan o'qib chiqing.";}
  else{msg="💪 Davom eting!";sub="Konspektni qayta o'qib, testni takrorlang.";}
  document.getElementById('resultMsg').textContent=msg;
  document.getElementById('resultSub').textContent=sub;

  let breakdownHtml='';
  Object.entries(catScores).forEach(([cat,s])=>{
    const color = s.correct/s.total>=0.7?'var(--green)':s.correct/s.total>=0.4?'var(--yellow)':'var(--red)';
    breakdownHtml+=`<div class="breakdown-row"><span class="breakdown-cat">${cat}</span><span class="breakdown-score" style="color:${color}">${s.correct}/${s.total}</span></div>`;
  });
  document.getElementById('breakdown').innerHTML=breakdownHtml;

  let wrongHtml='', correctHtml='';
  questions.forEach((q,i)=>{
    const userAns=answered[i];
    const isCorrect=userAns===q.ans;
    const block=`<div class="review-item ${isCorrect?'correct-item':''}">
      <div class="review-q">${i+1}. ${q.q}</div>
      <div class="review-ans">
        ${userAns!==null?`<div class="${isCorrect?'right':'your'}">Sizning javobingiz: ${String.fromCharCode(65+userAns)}. ${q.opts[userAns]}</div>`:'<div class="your">Javob berilmagan</div>'}
        ${!isCorrect?`<div class="right">To'g'ri javob: ${String.fromCharCode(65+q.ans)}. ${q.opts[q.ans]}</div>`:''}
        <div style="margin-top:6px;opacity:.85">${q.exp}</div>
      </div>
    </div>`;
    if(isCorrect) correctHtml+=block; else wrongHtml+=block;
  });
  document.getElementById('reviewWrong').innerHTML = wrongHtml || "<p style=\"color:var(--green);font-size:13px\">Xato javob yo'q — ajoyib! 🎉</p>";
  document.getElementById('reviewCorrect').innerHTML = correctHtml || '<p style="color:var(--muted);font-size:13px">—</p>';
}

function restartQuiz(){
  curQ=0; answered=new Array(questions.length).fill(null); flagged=new Set();
  document.getElementById('results').style.display='none';
  document.getElementById('intro').style.display='block';
  document.getElementById('progressFill').style.width='0%';
}
</script>
</body>
</html>
