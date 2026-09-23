<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🐸 GM COIN — Website Meme Paling Hidup</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  body {
    font-family: 'Comic Sans MS', 'Chalkboard SE', 'Segoe UI', cursive, sans-serif;
    background: #0b0b1a;
    color: #fff;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ====== Background gradien animasi ====== */
  .bg {
    position: fixed; inset: 0; z-index: -2;
    background: linear-gradient(-45deg, #1a0a3a, #0b0b1a, #3a0a3a, #0a1a3a);
    background-size: 400% 400%;
    animation: grad 12s ease infinite;
  }
  @keyframes grad { 0%{background-position:0% 50%} 50%{background-position:100% 50%} 100%{background-position:0% 50%} }

  /* ====== Blob cahaya bergerak ====== */
  .blob { position: fixed; border-radius: 50%; filter: blur(80px); opacity: .35; z-index: -1; animation: float 10s ease-in-out infinite; }
  .blob1 { width: 300px; height: 300px; background: #d000ff; top: -80px; left: -80px; }
  .blob2 { width: 250px; height: 250px; background: #00e5ff; bottom: -60px; right: -60px; animation-delay: -4s; }
  .blob3 { width: 200px; height: 200px; background: #ffd400; top: 50%; left: 60%; animation-delay: -7s; }

  /* ====== Emoji hujan (partikel melayang) ====== */
  .rain { position: fixed; inset: 0; z-index: 0; pointer-events: none; overflow: hidden; }
  .rain span {
    position: absolute; bottom: -60px; font-size: 2em; opacity: .7;
    animation: rise linear infinite;
  }
  @keyframes rise {
    0% { transform: translateY(0) rotate(0deg); opacity: 0; }
    10% { opacity: .7; }
    100% { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
  }

  /* ====== Ticker berjalan ====== */
  .ticker-wrap {
    position: fixed; top: 0; left: 0; right: 0; z-index: 20;
    background: #ffd400; color: #111; font-weight: bold;
    padding: 10px 0; overflow: hidden; white-space: nowrap;
    box-shadow: 0 4px 20px rgba(0,0,0,.6);
  }
  .ticker { display: inline-block; animation: scroll 30s linear infinite; }
  @keyframes scroll { 0% { transform: translateX(0); } 100% { transform: translateX(-50%); } }
  .ticker span { margin: 0 30px; }

  /* ====== Layout utama ====== */
  .wrap { max-width: 700px; margin: 0 auto; padding: 90px 20px 50px; text-align: center; position: relative; z-index: 5; }

  h1 {
    font-size: 2.6em; margin: 15px 0 5px; line-height: 1.1;
    background: linear-gradient(90deg,#ffd400,#d000ff,#00e5ff,#ffd400);
    background-size: 300% 100%;
    -webkit-background-clip: text; background-clip: text; color: transparent;
    animation: shimmer 6s linear infinite;
  }
  @keyframes shimmer { 0%{background-position:0% 0} 100%{background-position:300% 0} }

  .typewriter { color: #8ef; font-size: 1.05em; min-height: 1.6em; margin-bottom: 25px; }
  .cursor { display: inline-block; width: 10px; background: #8ef; animation: blink 1s step-end infinite; }
  @keyframes blink { 50% { opacity: 0; } }

  /* ====== Koin melayang + berputar ====== */
  .coin-wrap { position: relative; width: 160px; height: 160px; margin: 10px auto 20px; animation: bob 3s ease-in-out infinite; }
  @keyframes bob { 0%,100%{ transform: translateY(0); } 50% { transform: translateY(-18px); } }
  .coin {
    width: 160px; height: 160px; border-radius: 50%;
    background: radial-gradient(circle at 35% 30%, #fff2a8, #ffd400 45%, #c9a100);
    display: flex; align-items: center; justify-content: center;
    font-size: 3em; box-shadow: 0 10px 40px rgba(255,212,0,.5), inset 0 -8px 20px rgba(0,0,0,.25);
    border: 6px dashed #fff3b0;
    animation: spin 8s linear infinite;
  }
  @keyframes spin { 0%{ transform: rotateY(0);} 100% { transform: rotateY(360deg);} }
  .glow { position: absolute; inset: -25px; border-radius: 50%; border: 3px solid rgba(255,212,0,.4); animation: pulse 2s ease-in-out infinite; }
  @keyframes pulse { 0%,100%{ transform: scale(1); opacity:.6; } 50% { transform: scale(1.15); opacity:.2; } }

  /* ====== Kartu ====== */
  .card {
    background: rgba(26,26,51,.85); border: 3px dashed #d000ff; border-radius: 24px;
    padding: 25px 20px; margin: 20px 0; backdrop-filter: blur(4px);
    animation: cardGlow 4s ease-in-out infinite;
  }
  @keyframes cardGlow { 0%,100%{ box-shadow: 0 0 20px rgba(208,0,255,.25);} 50% { box-shadow: 0 0 40px rgba(208,0,255,.6);} }

  .coin-name { font-size: 2.2em; font-weight: bold; color: #ffd400; text-shadow: 3px 3px 0 #d000ff; word-break: break-word; }
  .coin-symbol { color: #8ef; margin: 5px 0 15px; }

  /* ====== Statistik grid + counter ====== */
  .stats { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin: 18px 0; }
  .stat {
    background: #12122a; border-radius: 14px; padding: 14px 10px; font-size: .85em;
    transition: transform .2s; border: 1px solid #333;
  }
  .stat:hover { transform: scale(1.05) rotate(-1deg); border-color: #d000ff; }
  .stat b { display: block; color: #ffd400; font-size: 1.2em; margin-top: 4px; }

  /* ====== Pump-o-meter ====== */
  .meter { margin: 18px 0; }
  .bar { height: 26px; background: #222; border-radius: 13px; overflow: hidden; margin-top: 8px; border: 1px solid #444; }
  .fill {
    height: 100%; width: 40%;
    background: linear-gradient(90deg,#22c55e,#ffd400,#f87171);
    background-size: 200% 100%; animation: fillSway 2s ease-in-out infinite;
    transition: width .5s;
  }
  @keyframes fillSway { 0%{background-position:0% 0} 100%{background-position:200% 0} }

  /* ====== Tombol ====== */
  .btn {
    background: #d000ff; color: #fff; border: none; border-radius: 50px;
    padding: 15px 32px; font-size: 1.05em; font-family: inherit; font-weight: bold;
    cursor: pointer; transition: .15s; box-shadow: 0 6px 0 #7a0099; margin: 6px;
  }
  .btn:hover { transform: translateY(-3px) scale(1.04); box-shadow: 0 9px 0 #7a0099; }
  .btn:active { transform: translateY(3px); box-shadow: 0 2px 0 #7a0099; }
  .btn.blue { background: #0ea5e9; box-shadow: 0 6px 0 #075985; }
  .btn.blue:hover { box-shadow: 0 9px 0 #075985; }

  /* ====== Confetti ====== */
  .confetti { position: fixed; z-index: 50; pointer-events: none; animation: confFall linear forwards; }
  @keyframes confFall {
    0% { transform: translateY(-20px) rotate(0); opacity: 1; }
    100% { transform: translateY(110vh) rotate(720deg); opacity: 0; }
  }

  .disclaimer { color: #888; font-size: .72em; margin-top: 25px; }
  .footer-tip { color: #666; font-size: .7em; margin-top: 8px; }
</style>
</head>
<body>

<div class="bg"></div>
<div class="blob blob1"></div><div class="blob blob2"></div><div class="blob blob3"></div>
<div class="rain" id="rain"></div>

<div class="ticker-wrap"><div class="ticker" id="ticker"></div></div>

<div class="wrap">
  <h1>🐸 GM COIN</h1>
  <div class="typewriter"><span id="typeText"></span><span class="cursor">&nbsp;</span></div>

  <!-- Koin melayang -->
  <div class="coin-wrap">
    <div class="glow"></div>
    <div class="coin" id="coinFace">🚀</div>
  </div>

  <div class="card">
    <div id="coinName" class="coin-name">JAMUR ENOKI</div>
    <div id="coinSymbol" class="coin-symbol">$ENOKI — "Jamur goreng gak pernah rugi"</div>

    <div class="stats">
      <div class="stat">Harga Live<b id="harga">$0.0000420</b></div>
      <div class="stat">Market Cap<b id="mcap">$69,420,000</b></div>
      <div class="stat">Liquidity<b id="liq">🔒 Kulkas dev 🧊</b></div>
      <div class="stat">Holder<b id="holder">1,337</b></div>
    </div>

    <div class="meter">
      <span>Tingkat FOMO Kamu:</span>
      <div class="bar"><div class="fill" id="fill"></div></div>
      <span id="meterLabel" style="font-size:.8em; color:#bbb;"></span>
    </div>

    <button class="btn" onclick="generate()">🎲 Generate Coin</button>
    <button class="btn blue" onclick="burst()">💥 Pump! (percaya doang)</button>
  </div>

  <p class="disclaimer">⚠️ Bukan saran finansial. Token ini fiktif 100% — bedanya sama token asli cuma satu: ini jujur kalau fiktif. DYOR atau tidur.</p>
  <p class="footer-tip">🖱️ Klik "Pump!" buat lihat animasi 🎉</p>
</div>

<script>
  // ====== Hujan emoji melayang ======
  const emojis = ['🐸','🚀','💎','🙌','🍄','💩','🔥','🌙','🐕','🥶','📈','🪙'];
  const rainBox = document.getElementById('rain');
  for (let i = 0; i < 22; i++) {
    const s = document.createElement('span');
    s.textContent = emojis[Math.floor(Math.random()*emojis.length)];
    s.style.left = Math.random()*100 + '%';
    s.style.fontSize = (1 + Math.random()*2.2) + 'em';
    s.style.animationDuration = (6 + Math.random()*10) + 's';
    s.style.animationDelay = (Math.random()*12) + 's';
    rainBox.appendChild(s);
  }

  // ====== Ticker ======
  const coins = ['$ENOKI 🍄','$JAMUR 🍄','$NASIBUNGKUS 🍚','$HAMMOCK 🛋️','$HUTANG 💸','$LIKUIDITAS 💧','$GENIUS 🧠','$GM 🐸','$WAGMI 🚀','$RUGPULL 💀','$PAPERHAND ✋','$BULLISH 📈'];
  let tick = coins.join(' &nbsp;•&nbsp; ');
  document.getElementById('ticker').innerHTML = tick + ' • ' + tick;

  // ====== Typewriter ======
  const phrases = [
    'Harga turun? Itu cuma "koreksi biar murah" 😌',
    'Diamond hands sampai kapan? Sampai makan nasi bungkus.',
    'GM di pagi hari, NGMI di malam hari. Siklus hidup.',
    'Likuiditas terkunci di kulkas dev 🧊',
    'Nasi bungkus: satu-satunya aset yang nggak rugi.',
    'Jamur enoki: volatility-nya lebih stabil dari BTC.',
  ];
  let pi = 0, ci = 0, deleting = false;
  const typeEl = document.getElementById('typeText');
  function type() {
    const word = phrases[pi];
    if (!deleting) {
      ci++;
      if (ci === word.length) { deleting = true; setTimeout(type, 2200); typeEl.textContent = word; return; }
    } else {
      ci--;
      if (ci === 0) { deleting = false; pi = (pi+1)%phrases.length; }
      typeEl.textContent = word.slice(0, ci);
    }
    setTimeout(type, deleting ? 30 : 60);
  }
  type();

  // ====== Generator coin ======
  const pre = ['GM','GN','FOMO','Anti','Turbo','Ultra','Mega','Super','Hodl','WAGMI','Based','Kopi','Sama','Giga'];
  const nouns = ['Jamur','Enoki','Nasi Bungkus','Hammock','Hutang','Likuiditas','Genius','Bullish','Rug','Paper Hand','Rendang','Sambal','Kentang','Shiba','Doge'];
  const suf = ['Inu','Chain','Swap','Token','X','AI','DAO','Finance','Core','Rex','Max','Net','Pad','Verse','King'];
  const tag = [
    '💸 Solusi buat masalah yang gak ada',
    '🍄 Jamur enoki, lambang komunitas yang enak',
    '🚀 Ke bulan. Atau ke warung. Tergantung liquidity',
    '🏖️ Kayak hammock: miring-miring terus',
    '🧠 Genius sampai gak butuh whitepaper',
    '🍚 Bukan cuma nasi bungkus, ini visi bungkus bungkus',
    '⚡ Cepat ruginya kayak lightning network',
    '🔫 Locked liquidity di dalam hati dev',
    '🛋️ Rug pull pakai empuk',
    '🐸 GM semua, NGMI setengahnya',
  ];
  const faces = ['🚀','🐸','💎','🍄','🦍','🌙','🐕','🔥','🪙','😎'];
  const pick = a => a[Math.floor(Math.random()*a.length)];

  function generate() {
    const name = Math.random() < .5 ? pick(pre)+' '+pick(nouns) : pick(pre)+pick(nouns)+' '+pick(suf);
    document.getElementById('coinName').textContent = name.toUpperCase();
    document.getElementById('coinSymbol').textContent = '$' + name.replace(/[^A-Za-z]/g,'').toUpperCase().slice(0,6) + ' — "' + pick(tag) + '"';
    document.getElementById('mcap').textContent = '$' + (Math.random()*999).toFixed(0) + 'K–$' + (Math.random()*99).toFixed(0) + 'B';
    document.getElementById('liq').textContent = pick(['🔒 Kulkas dev 🧊','🔓 Hati dev ❤️','⚠️ Gak ada (chaos)','🔒 100 tahun, dev lupa password']);
    document.getElementById('holder').textContent = (Math.floor(Math.random()*9000)+42).toLocaleString();
    document.getElementById('coinFace').textContent = pick(faces);
    // flash coin
    const c = document.getElementById('coinFace').parentElement;
    c.style.animation = 'none'; c.offsetHeight; c.style.animation = '';
    burst();
  }

  // ====== Harga live berubah sendiri ======
  let price = 0.0000420;
  setInterval(() => {
    price *= 1 + (Math.random() - 0.48) * 0.05;
    document.getElementById('harga').textContent = '$' + price.toFixed(8);
    // meter goyang
    const f = document.getElementById('fill');
    const pct = 20 + Math.random()*60;
    f.style.width = pct + '%';
    document.getElementById('meterLabel').textContent = pct > 70 ? 'FOMO PARAH 😱' : pct > 45 ? 'Agak fomo, masih mikir 🤔' : 'Tenang, gas tidur 😴';
  }, 1500);

  // ====== Confetti ======
  const cols = ['#ffd400','#d000ff','#00e5ff','#22c55e','#f87171','#fff'];
  function burst() {
    for (let i = 0; i < 60; i++) {
      const d = document.createElement('div');
      d.className = 'confetti';
      d.style.left = Math.random()*100 + 'vw';
      d.style.top = '-20px';
      d.style.width = d.style.height = (6 + Math.random()*8) + 'px';
      d.style.background = cols[Math.floor(Math.random()*cols.length)];
      d.style.animationDuration = (1.5 + Math.random()*2) + 's';
      d.style.animationDelay = (Math.random()*.4) + 's';
      d.style.borderRadius = Math.random() < .5 ? '50%' : '2px';
      document.body.appendChild(d);
      setTimeout(() => d.remove(), 4000);
    }
  }
</script>
</body>
</html>
