<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>D.Tail Salon | Lauren Metz</title>
  <style>
    :root{
      --bg: #0b0b10;
      --panel: rgba(255,255,255,0.06);
      --panel2: rgba(255,255,255,0.10);
      --text: rgba(255,255,255,0.92);
      --muted: rgba(255,255,255,0.68);
      --accent: #ff4fd8;
      --accent2:#55f7ff;
      --accent3:#ffe66b;
      --stroke: rgba(255,255,255,0.16);
      --shadow: 0 18px 55px rgba(0,0,0,0.55);
      --radius: 22px;
      --mono: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", monospace;
      --sans: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial;
    }

    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      color:var(--text);
      font-family:var(--sans);
      background:
        radial-gradient(900px 600px at 12% 10%, rgba(255,79,216,0.22), transparent 60%),
        radial-gradient(900px 600px at 88% 18%, rgba(85,247,255,0.18), transparent 55%),
        radial-gradient(800px 700px at 55% 90%, rgba(255,230,107,0.14), transparent 55%),
        linear-gradient(180deg, #07070b, #0b0b10);
      overflow-x:hidden;
    }

    /* subtle “retro scan” */
    .scan{
      position:fixed; inset:0;
      pointer-events:none;
      background: repeating-linear-gradient(
        to bottom,
        rgba(255,255,255,0.00),
        rgba(255,255,255,0.00) 2px,
        rgba(255,255,255,0.03) 3px
      );
      mix-blend-mode: overlay;
      opacity:0.25;
    }

    .wrap{
      min-height:100%;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:28px 16px 60px;
    }

    .card{
      width:min(980px, 100%);
      border:1px solid var(--stroke);
      border-radius:var(--radius);
      background: linear-gradient(180deg, rgba(255,255,255,0.07), rgba(255,255,255,0.04));
      box-shadow: var(--shadow);
      position:relative;
      overflow:hidden;
    }

    .card::before{
      content:"";
      position:absolute; inset:-2px;
      background: conic-gradient(from 210deg, rgba(255,79,216,0.25), rgba(85,247,255,0.22), rgba(255,230,107,0.18), rgba(255,79,216,0.25));
      filter: blur(26px);
      opacity:0.55;
      z-index:0;
    }

    .inner{
      position:relative;
      z-index:1;
      padding:24px;
    }

    .top{
      display:flex;
      gap:18px;
      align-items:flex-start;
      justify-content:space-between;
      flex-wrap:wrap;
      padding-bottom:18px;
      border-bottom:1px solid rgba(255,255,255,0.14);
    }

    .badge{
      display:inline-flex;
      align-items:center;
      gap:10px;
      padding:10px 12px;
      border-radius:999px;
      background:rgba(0,0,0,0.35);
      border:1px solid rgba(255,255,255,0.15);
      font-family:var(--mono);
      letter-spacing:0.02em;
      color:rgba(255,255,255,0.85);
    }

    .dot{
      width:10px; height:10px; border-radius:50%;
      background:var(--accent2);
      box-shadow: 0 0 0 3px rgba(85,247,255,0.15), 0 0 18px rgba(85,247,255,0.55);
    }

    .headline{
      margin:14px 0 6px;
      font-size:clamp(30px, 4vw, 48px);
      line-height:1.05;
      letter-spacing:-0.02em;
    }

    .headline span{
      background: linear-gradient(90deg, var(--accent), var(--accent2), var(--accent3));
      -webkit-background-clip:text;
      background-clip:text;
      color:transparent;
    }

    .sub{
      margin:0;
      color:var(--muted);
      font-size:clamp(15px, 2.2vw, 18px);
      max-width:58ch;
    }

    .grid{
      display:grid;
      grid-template-columns: 1.2fr 0.8fr;
      gap:18px;
      margin-top:18px;
    }

    @media (max-width: 860px){
      .grid{grid-template-columns:1fr}
    }

    .panel{
      border:1px solid rgba(255,255,255,0.14);
      background: rgba(0,0,0,0.35);
      border-radius:18px;
      padding:18px;
      position:relative;
      overflow:hidden;
    }

    .panel h3{
      margin:0 0 10px;
      font-size:14px;
      font-family:var(--mono);
      letter-spacing:0.12em;
      text-transform:uppercase;
      color:rgba(255,255,255,0.75);
    }

    .ctaRow{
      display:flex;
      flex-wrap:wrap;
      gap:10px;
    }

    .btn{
      appearance:none;
      border:1px solid rgba(255,255,255,0.18);
      background: linear-gradient(180deg, rgba(255,255,255,0.10), rgba(255,255,255,0.06));
      color:var(--text);
      padding:12px 14px;
      border-radius:14px;
      font-weight:650;
      letter-spacing:0.01em;
      cursor:pointer;
      transition: transform 160ms ease, border-color 160ms ease, background 160ms ease, box-shadow 160ms ease;
      display:inline-flex;
      align-items:center;
      gap:10px;
      text-decoration:none;
      user-select:none;
      position:relative;
      overflow:hidden;
    }

    .btn:focus{outline:2px solid rgba(85,247,255,0.55); outline-offset:2px}
    .btn:hover{transform: translateY(-1px); border-color: rgba(255,255,255,0.32); box-shadow: 0 10px 25px rgba(0,0,0,0.35)}
    .btn:active{transform: translateY(0px) scale(0.99)}

    .btn.primary{
      border-color: rgba(255,79,216,0.55);
      background: linear-gradient(180deg, rgba(255,79,216,0.28), rgba(255,79,216,0.12));
    }
    .btn.primary:hover{
      border-color: rgba(85,247,255,0.55);
      background: linear-gradient(180deg, rgba(85,247,255,0.24), rgba(255,79,216,0.12));
    }

    .pill{
      font-family:var(--mono);
      font-size:12px;
      padding:6px 9px;
      border-radius:999px;
      border:1px solid rgba(255,255,255,0.16);
      background: rgba(0,0,0,0.35);
      color: rgba(255,255,255,0.75);
    }

    .reveal{
      margin-top:14px;
      display:grid;
      grid-template-columns: 1fr 1fr;
      gap:12px;
    }
    @media (max-width: 560px){
      .reveal{grid-template-columns:1fr}
    }

    .tile{
      border:1px dashed rgba(255,255,255,0.22);
      border-radius:16px;
      padding:14px;
      background: rgba(255,255,255,0.04);
      transition: border-color 160ms ease, background 160ms ease, transform 160ms ease;
      cursor:pointer;
      min-height:78px;
      position:relative;
      overflow:hidden;
    }
    .tile:hover{
      transform: translateY(-1px);
      border-color: rgba(85,247,255,0.45);
      background: rgba(85,247,255,0.06);
    }

    .tile .label{
      font-family:var(--mono);
      letter-spacing:0.10em;
      text-transform:uppercase;
      font-size:12px;
      color:rgba(255,255,255,0.72);
      margin-bottom:8px;
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:10px;
    }

    .tile .value{
      font-size:16px;
      color:rgba(255,255,255,0.92);
      word-break:break-word;
      line-height:1.25;
    }

    .toast{
      position:fixed;
      left:50%;
      transform:translateX(-50%);
      bottom:18px;
      background:rgba(0,0,0,0.65);
      border:1px solid rgba(255,255,255,0.18);
      padding:10px 12px;
      border-radius:999px;
      font-family:var(--mono);
      color:rgba(255,255,255,0.88);
      box-shadow: 0 12px 30px rgba(0,0,0,0.45);
      opacity:0;
      pointer-events:none;
      transition: opacity 180ms ease, transform 180ms ease;
      z-index:10;
    }
    .toast.show{
      opacity:1;
      transform:translateX(-50%) translateY(-4px);
    }

    .footer{
      margin-top:16px;
      display:flex;
      flex-wrap:wrap;
      gap:10px;
      align-items:center;
      justify-content:space-between;
      color:rgba(255,255,255,0.66);
      font-size:13px;
    }

    /* tiny confetti */
    .confetti{
      position:fixed;
      inset:0;
      pointer-events:none;
      overflow:hidden;
      z-index:12;
    }
    .confetti i{
      position:absolute;
      width:10px; height:10px;
      border-radius:2px;
      opacity:0.9;
      animation: fall 1200ms linear forwards;
    }
    @keyframes fall{
      0%{ transform: translateY(-20px) rotate(0deg); opacity:0.0}
      10%{opacity:0.95}
      100%{ transform: translateY(calc(100vh + 40px)) rotate(520deg); opacity:0.0}
    }
  </style>
</head>

<body>
  <div class="scan"></div>
  <div class="wrap">
    <main class="card" aria-label="D.Tail Salon Online Business Card">
      <div class="inner">
        <section class="top">
          <div>
            <div class="badge"><span class="dot"></span> D.Tail Salon Terminal • Buffalo, NY</div>
            <h1 class="headline">You’ve entered the <span>D.Tail</span> zone.</h1>
            <p class="sub">
              I’m <strong>Lauren Metz</strong>. Precision cuts, color that behaves, and vibes that feel expensive without being loud about it.
              Tap around, steal my contact info, and book when you’re ready to look suspiciously great.
            </p>
          </div>

          <div class="badge" title="Try the keyboard Easter egg!">
            <span class="pill">Tip:</span> Type ↑ ↑ ↓ ↓ ← → ← → B A
          </div>
        </section>

        <section class="grid">
          <div class="panel">
            <h3>Quick Actions</h3>
            <div class="ctaRow">
              <a class="btn primary" href="https://dtailsalon.glossgenius.com" target="_blank" rel="noopener">
                ✨ Book Online <span class="pill">GlossGenius</span>
              </a>
              <a class="btn" href="https://getdtailed.com" target="_blank" rel="noopener">
                🕸️ Website <span class="pill">getdtailed.com</span>
              </a>
              <a class="btn" href="https://www.instagram.com/d.tailsalon" target="_blank" rel="noopener">
                📸 Instagram <span class="pill">@d.tailsalon</span>
              </a>
              <a class="btn" href="https://www.facebook.com/d.tailsalon" target="_blank" rel="noopener">
                🗞️ Facebook <span class="pill">/d.tailsalon</span>
              </a>
            </div>

            <div class="reveal" style="margin-top:14px">
              <div class="tile" data-copy="d.tailsalon@gmail.com" role="button" tabindex="0" aria-label="Copy email">
                <div class="label">Email <span class="pill">tap to copy</span></div>
                <div class="value">d.tailsalon@gmail.com</div>
              </div>

              <div class="tile" data-copy="7165783277" role="button" tabindex="0" aria-label="Copy phone number">
                <div class="label">Phone <span class="pill">tap to copy</span></div>
                <div class="value">(716) 578-3277</div>
              </div>

              <div class="tile" data-open="https://maps.google.com/?q=394+Franklin+St+Buffalo+NY+14202" role="button" tabindex="0" aria-label="Open address in maps">
                <div class="label">Location <span class="pill">open maps</span></div>
                <div class="value">394 Franklin St, Buffalo, NY 14202</div>
              </div>

              <div class="tile" data-vcard="true" role="button" tabindex="0" aria-label="Download contact card">
                <div class="label">Save Contact <span class="pill">vCard</span></div>
                <div class="value">Add “Lauren Metz” to your phone</div>
              </div>
            </div>

            <div class="footer">
              <div>Built like a business card. Behaves like a tiny experience. 🪩</div>
              <div class="pill" id="statusPill">Status: ready when you are</div>
            </div>
          </div>

          <aside class="panel">
            <h3>Mini Menu</h3>
            <p style="margin:0 0 12px; color:var(--muted); line-height:1.45;">
              Choose your vibe:
            </p>

            <div class="ctaRow">
              <button class="btn" id="btnGlow" type="button">💫 “Make it glossy”</button>
              <button class="btn" id="btnRetro" type="button">🕹️ “More retro”</button>
              <button class="btn" id="btnChill" type="button">🌙 “Calm it down”</button>
            </div>

            <div style="margin-top:14px; border-top:1px solid rgba(255,255,255,0.14); padding-top:14px;">
              <h3>One-liner</h3>
              <div id="oneLiner" style="font-size:16px; line-height:1.35;">
                Hair that looks like you have your life together. (Even if your group chat knows better.)
              </div>
              <div style="margin-top:12px">
                <button class="btn primary" id="btnRandom" type="button">🎲 New line</button>
              </div>
            </div>

            <div style="margin-top:14px; border-top:1px solid rgba(255,255,255,0.14); padding-top:14px;">
              <h3>Fastest Booking</h3>
              <p style="margin:0 0 10px; color:var(--muted); line-height:1.45;">
                Want the quickest route? Hit the button. Your future hair will thank you.
              </p>
              <a class="btn primary" href="https://dtailsalon.glossgenius.com" target="_blank" rel="noopener">
                🚀 Book Now
              </a>
            </div>
          </aside>
        </section>
      </div>
    </main>
  </div>

  <div class="toast" id="toast">Copied ✨</div>
  <div class="confetti" id="confetti"></div>

  <script>
    const toast = document.getElementById('toast');
    const statusPill = document.getElementById('statusPill');
    const confetti = document.getElementById('confetti');
    const oneLiner = document.getElementById('oneLiner');

    const lines = [
      "Hair that looks like you have your life together. (Even if your group chat knows better.)",
      "Clean lines, bold choices, zero regrets.",
      "Buffalo weather-proof hair, activated.",
      "Subtle flex: you leave looking like a before-and-after.",
      "Volume with intention. Shine with boundaries.",
      "If your hair had a resume, this would be the promotion."
    ];

    function showToast(msg){
      toast.textContent = msg;
      toast.classList.add('show');
      setTimeout(()=>toast.classList.remove('show'), 1200);
    }

    async function copyText(text){
      try{
        await navigator.clipboard.writeText(text);
        showToast("Copied ✨");
        statusPill.textContent = "Status: copied to clipboard";
        setTimeout(()=>statusPill.textContent = "Status: ready when you are", 1300);
      }catch(e){
        showToast("Copy not supported here");
      }
    }

    function downloadVCard(){
      const vcard =
`BEGIN:VCARD
VERSION:3.0
N:Metz;Lauren;;;
FN:Lauren Metz
ORG:D.Tail Salon
TEL;TYPE=CELL:7165783277
EMAIL:d.tailsalon@gmail.com
ADR;TYPE=WORK:;;394 Franklin St;Buffalo;NY;14202;USA
URL:https://getdtailed.com
NOTE:Online booking: https://dtailsalon.glossgenius.com
END:VCARD`;
      const blob = new Blob([vcard], {type: "text/vcard"});
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = "LaurenMetz-DTailSalon.vcf";
      document.body.appendChild(a);
      a.click();
      a.remove();
      URL.revokeObjectURL(url);
      showToast("Saved contact card 📇");
    }

    // Tiles: tap to copy/open/download
    document.querySelectorAll('.tile').forEach(tile=>{
      const copy = tile.getAttribute('data-copy');
      const open = tile.getAttribute('data-open');
      const vcard = tile.getAttribute('data-vcard');

      const activate = () => {
        if(copy) return copyText(copy);
        if(open) {
          window.open(open, "_blank", "noopener");
          showToast("Opening maps 🗺️");
          return;
        }
        if(vcard) return downloadVCard();
      };

      tile.addEventListener('click', activate);
      tile.addEventListener('keydown', (e)=>{
        if(e.key === "Enter" || e.key === " ") activate();
      });
    });

    // Vibe buttons
    const btnGlow = document.getElementById('btnGlow');
    const btnRetro = document.getElementById('btnRetro');
    const btnChill = document.getElementById('btnChill');
    const btnRandom = document.getElementById('btnRandom');

    let glowOn = true;
    btnGlow.addEventListener('click', ()=>{
      glowOn = !glowOn;
      document.querySelector('.scan').style.opacity = glowOn ? "0.25" : "0.10";
      statusPill.textContent = glowOn ? "Status: glossy mode" : "Status: matte mode";
      showToast(glowOn ? "Glossy mode 💫" : "Matte mode 🫧");
      setTimeout(()=>statusPill.textContent = "Status: ready when you are", 1400);
    });

    btnRetro.addEventListener('click', ()=>{
      document.body.style.background =
        "radial-gradient(900px 600px at 12% 10%, rgba(255,79,216,0.28), transparent 60%)," +
        "radial-gradient(900px 600px at 88% 18%, rgba(85,247,255,0.22), transparent 55%)," +
        "radial-gradient(800px 700px at 55% 90%, rgba(255,230,107,0.18), transparent 55%)," +
        "linear-gradient(180deg, #04040a, #0b0b10)";
      showToast("Retro boost 🕹️");
    });

    btnChill.addEventListener('click', ()=>{
      document.body.style.background =
        "radial-gradient(900px 600px at 30% 15%, rgba(85,247,255,0.14), transparent 60%)," +
        "radial-gradient(900px 600px at 78% 35%, rgba(255,79,216,0.12), transparent 55%)," +
        "linear-gradient(180deg, #07070b, #0b0b10)";
      showToast("Chill mode 🌙");
    });

    btnRandom.addEventListener('click', ()=>{
      const pick = lines[Math.floor(Math.random() * lines.length)];
      oneLiner.textContent = pick;
      showToast("Fresh line 🎲");
    });

    // Easter egg: Konami code
    const konami = ["ArrowUp","ArrowUp","ArrowDown","ArrowDown","ArrowLeft","ArrowRight","ArrowLeft","ArrowRight","b","a"];
    let kIndex = 0;

    function popConfetti(){
      for(let i=0;i<70;i++){
        const piece = document.createElement('i');
        const x = Math.random() * 100;
        const size = 6 + Math.random() * 10;
        piece.style.left = x + "vw";
        piece.style.top = (-10 - Math.random() * 30) + "px";
        piece.style.width = size + "px";
        piece.style.height = size + "px";
        piece.style.background = ["#ff4fd8","#55f7ff","#ffe66b","#ffffff"][Math.floor(Math.random()*4)];
        piece.style.animationDuration = (900 + Math.random()*900) + "ms";
        confetti.appendChild(piece);
        setTimeout(()=>piece.remove(), 2200);
      }
    }

    window.addEventListener('keydown', (e)=>{
      const key = e.key.length === 1 ? e.key.toLowerCase() : e.key;
      const target = konami[kIndex];
      if(key === target){
        kIndex++;
        if(kIndex === konami.length){
          popConfetti();
          showToast("Secret unlocked ✨");
          statusPill.textContent = "Status: VIP energy detected";
          oneLiner.textContent = "You found the secret. Now book like a legend. 🪩";
          setTimeout(()=>statusPill.textContent = "Status: ready when you are", 2400);
          kIndex = 0;
        }
      } else {
        kIndex = 0;
      }
    });
  </script>
</body>
</html>
