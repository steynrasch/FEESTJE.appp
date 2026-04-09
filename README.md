<!DOCTYPE html>
<html lang="nl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>GiftLink Demo</title>
  <style>
    :root {
      --bg: #0b0f14;
      --card: #121922;
      --card-2: #182332;
      --text: #eef4ff;
      --muted: #9fb0c7;
      --line: #243246;
      --accent: #00d084;
      --accent-2: #00a66a;
      --danger: #ff7b7b;
      --warning: #ffd166;
      --shadow: 0 18px 50px rgba(0,0,0,.35);
      --radius: 22px;
    }

    * { box-sizing: border-box; }
    body {
      margin: 0;
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      background:
        radial-gradient(circle at top left, rgba(0,208,132,.13), transparent 30%),
        radial-gradient(circle at top right, rgba(255,209,102,.08), transparent 26%),
        linear-gradient(180deg, #0b0f14 0%, #0d1219 100%);
      color: var(--text);
      min-height: 100vh;
      padding: 32px 18px 60px;
    }

    .wrap {
      max-width: 1120px;
      margin: 0 auto;
      display: grid;
      grid-template-columns: 1.1fr 0.9fr;
      gap: 24px;
    }

    .card {
      background: linear-gradient(180deg, rgba(18,25,34,.95), rgba(14,19,27,.96));
      border: 1px solid var(--line);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
    }

    .hero {
      padding: 28px;
      overflow: hidden;
      position: relative;
    }

    .badge {
      display: inline-flex;
      gap: 8px;
      align-items: center;
      background: rgba(0,208,132,.12);
      color: #b5f4d8;
      border: 1px solid rgba(0,208,132,.25);
      padding: 8px 12px;
      border-radius: 999px;
      font-size: 13px;
      font-weight: 700;
      margin-bottom: 18px;
    }

    h1 {
      font-size: clamp(30px, 5vw, 52px);
      line-height: 1.02;
      margin: 0 0 12px;
      max-width: 680px;
      letter-spacing: -.03em;
    }

    .sub {
      color: var(--muted);
      font-size: 18px;
      line-height: 1.5;
      max-width: 690px;
      margin-bottom: 26px;
    }

    .cta-row {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
    }

    button, .btn {
      border: 0;
      border-radius: 14px;
      padding: 14px 18px;
      font-size: 15px;
      font-weight: 800;
      cursor: pointer;
      transition: transform .15s ease, opacity .15s ease, background .15s ease;
    }
    button:hover, .btn:hover { transform: translateY(-1px); }
    button:active, .btn:active { transform: translateY(0); }

    .btn-primary {
      background: var(--accent);
      color: #062215;
    }

    .btn-secondary {
      background: #1b2532;
      color: var(--text);
      border: 1px solid #2b3a50;
    }

    .grid-2 {
      margin-top: 22px;
      display: grid;
      grid-template-columns: repeat(2, minmax(0,1fr));
      gap: 16px;
    }

    .stat {
      background: rgba(255,255,255,.02);
      border: 1px solid var(--line);
      border-radius: 18px;
      padding: 18px;
    }
    .stat-label {
      color: var(--muted);
      font-size: 13px;
      margin-bottom: 8px;
    }
    .stat-value {
      font-size: 28px;
      font-weight: 900;
      letter-spacing: -.02em;
    }

    .phone {
      align-self: start;
      padding: 18px;
      position: sticky;
      top: 20px;
    }

    .phone-shell {
      max-width: 390px;
      margin: 0 auto;
      background: #0c1219;
      border: 1px solid #223043;
      border-radius: 34px;
      padding: 14px;
      box-shadow: inset 0 0 0 1px rgba(255,255,255,.03), var(--shadow);
    }

    .screen {
      background: linear-gradient(180deg, #111a24, #0d141d);
      border-radius: 26px;
      overflow: hidden;
      min-height: 760px;
      border: 1px solid rgba(255,255,255,.04);
    }

    .topbar {
      padding: 16px 18px 10px;
      display: flex;
      justify-content: space-between;
      color: var(--muted);
      font-size: 13px;
    }

    .gift-header {
      padding: 10px 18px 18px;
    }

    .gift-title {
      font-size: 27px;
      font-weight: 900;
      line-height: 1.05;
      margin-bottom: 10px;
      letter-spacing: -.03em;
    }

    .gift-desc {
      color: var(--muted);
      line-height: 1.45;
      font-size: 14px;
      margin-bottom: 16px;
    }

    .gift-box {
      background: linear-gradient(180deg, rgba(0,208,132,.10), rgba(0,208,132,.04));
      border: 1px solid rgba(0,208,132,.18);
      border-radius: 20px;
      padding: 16px;
      margin-bottom: 14px;
    }

    .gift-item {
      display: flex;
      gap: 14px;
      align-items: center;
    }

    .gift-icon {
      width: 54px;
      height: 54px;
      border-radius: 16px;
      display: grid;
      place-items: center;
      font-size: 28px;
      background: rgba(255,255,255,.08);
      border: 1px solid rgba(255,255,255,.08);
    }

    .gift-name { font-weight: 800; font-size: 16px; }
    .gift-price { color: var(--muted); font-size: 14px; margin-top: 3px; }

    .progress-wrap { margin-top: 14px; }
    .progress-head {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      margin-bottom: 8px;
    }
    .progress-big { font-size: 25px; font-weight: 900; }
    .progress-small { color: var(--muted); font-size: 13px; }
    .bar {
      width: 100%;
      height: 12px;
      background: #1a2531;
      border-radius: 999px;
      overflow: hidden;
      border: 1px solid #233246;
    }
    .fill {
      height: 100%;
      width: 0%;
      background: linear-gradient(90deg, var(--accent), #63f5b8);
      border-radius: 999px;
      transition: width .5s ease;
    }

    .section {
      padding: 0 18px 18px;
    }

    .section h3 {
      margin: 8px 0 12px;
      font-size: 15px;
      color: #dce7f8;
      letter-spacing: -.01em;
    }

    .contributors {
      display: grid;
      gap: 10px;
      margin-bottom: 18px;
    }

    .contrib {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 12px 14px;
      border-radius: 16px;
      background: #121b25;
      border: 1px solid #213043;
      font-size: 14px;
    }

    .pill-ok {
      color: #baf5da;
      background: rgba(0,208,132,.10);
      border: 1px solid rgba(0,208,132,.18);
      padding: 6px 10px;
      border-radius: 999px;
      font-size: 12px;
      font-weight: 800;
    }

    .amount-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;
      margin-bottom: 14px;
    }

    .amount-btn {
      background: #121b25;
      color: var(--text);
      border: 1px solid #233246;
      border-radius: 14px;
      padding: 13px 10px;
      text-align: center;
      font-weight: 800;
    }
    .amount-btn.active {
      background: rgba(0,208,132,.12);
      border-color: rgba(0,208,132,.34);
      color: #bbf8dd;
    }

    .field {
      display: grid;
      gap: 8px;
      margin-bottom: 12px;
    }

    .label {
      font-size: 13px;
      color: var(--muted);
    }

    input {
      width: 100%;
      background: #121b25;
      border: 1px solid #233246;
      color: var(--text);
      border-radius: 14px;
      padding: 14px;
      font-size: 15px;
      outline: none;
    }
    input:focus {
      border-color: rgba(0,208,132,.45);
      box-shadow: 0 0 0 4px rgba(0,208,132,.10);
    }

    .pay-btn {
      width: 100%;
      background: var(--accent);
      color: #052214;
      margin-top: 2px;
      padding: 15px 18px;
      border-radius: 16px;
      font-size: 16px;
      font-weight: 900;
    }

    .tiny {
      margin-top: 10px;
      color: var(--muted);
      font-size: 12px;
      line-height: 1.45;
      text-align: center;
    }

    .toast {
      position: fixed;
      right: 18px;
      bottom: 18px;
      background: #12231c;
      color: #d7ffe9;
      border: 1px solid rgba(0,208,132,.25);
      border-radius: 16px;
      padding: 14px 16px;
      box-shadow: var(--shadow);
      display: none;
      z-index: 20;
      max-width: 320px;
    }

    .ideas {
      margin-top: 24px;
      padding: 22px;
    }

    .ideas h2 {
      margin: 0 0 10px;
      font-size: 22px;
      letter-spacing: -.02em;
    }

    .ideas-list {
      display: grid;
      gap: 12px;
      color: var(--muted);
      line-height: 1.5;
    }

    .idea-item {
      background: rgba(255,255,255,.02);
      border: 1px solid var(--line);
      border-radius: 16px;
      padding: 14px 16px;
    }

    .emoji { margin-right: 8px; }

    @media (max-width: 940px) {
      .wrap { grid-template-columns: 1fr; }
      .phone { position: static; }
      .screen { min-height: unset; }
    }
  </style>
</head>
<body>
  <div class="wrap">
    <section>
      <div class="card hero">
        <div class="badge">🎁 Eén link voor een groepscadeau</div>
        <h1>Geen extra WhatsApp-groep. Geen Tikkie-chaos. Gewoon één cadeau-link.</h1>
        <div class="sub">
          Deze klikbare demo laat zien hoe mensen direct kunnen bijdragen aan een cadeau, live kunnen zien hoeveel er al is opgehaald en wie er al mee heeft gedaan.
        </div>
        <div class="cta-row">
          <button class="btn-primary" id="focusDemo">Probeer de demo</button>
          <button class="btn-secondary" id="simulate">Simuleer random bijdrage</button>
        </div>

        <div class="grid-2">
          <div class="stat">
            <div class="stat-label">Belofte voor de gebruiker</div>
            <div class="stat-value">1 link</div>
          </div>
          <div class="stat">
            <div class="stat-label">Wat je oplost</div>
            <div class="stat-value">0 gedoe</div>
          </div>
        </div>
      </div>

      <div class="card ideas">
        <h2>Waarom dit sterk is</h2>
        <div class="ideas-list">
          <div class="idea-item"><span class="emoji">✅</span>Iedereen ziet meteen het doelbedrag en de voortgang.</div>
          <div class="idea-item"><span class="emoji">✅</span>De host hoeft niet handmatig bij te houden wie al betaald heeft.</div>
          <div class="idea-item"><span class="emoji">✅</span>Het werkt direct vanuit een gedeelde link in WhatsApp, SMS of mail.</div>
        </div>
      </div>
    </section>

    <aside class="card phone" id="demo">
      <div class="phone-shell">
        <div class="screen">
          <div class="topbar">
            <span>giftlink.app/steyn-25</span>
            <span>🔒 demo</span>
          </div>

          <div class="gift-header">
            <div class="gift-title">🎉 Steyn wordt 25!</div>
            <div class="gift-desc">
              We leggen samen in voor een cadeau. Iedereen kan direct bijdragen en live zien hoeveel er al is opgehaald.
            </div>

            <div class="gift-box">
              <div class="gift-item">
                <div class="gift-icon">🎧</div>
                <div>
                  <div class="gift-name">AirPods Pro</div>
                  <div class="gift-price">Doelbedrag: <span id="goalText">€250</span></div>
                </div>
              </div>

              <div class="progress-wrap">
                <div class="progress-head">
                  <div class="progress-big"><span id="raisedText">€0</span></div>
                  <div class="progress-small">Nog <span id="leftText">€0</span> nodig</div>
                </div>
                <div class="bar"><div class="fill" id="fill"></div></div>
              </div>
            </div>
          </div>

          <div class="section">
            <h3>Al meegedaan</h3>
            <div class="contributors" id="contributors"></div>

            <h3>Doe mee</h3>
            <div class="amount-grid" id="amountGrid">
              <button class="amount-btn" data-value="5">€5</button>
              <button class="amount-btn active" data-value="10">€10</button>
              <button class="amount-btn" data-value="15">€15</button>
              <button class="amount-btn" data-value="20">€20</button>
              <button class="amount-btn" data-value="25">€25</button>
              <button class="amount-btn" data-value="50">€50</button>
            </div>

            <div class="field">
              <label class="label" for="nameInput">Je naam</label>
              <input id="nameInput" placeholder="Bijv. Lisa" value="Jij" />
            </div>

            <div class="field">
              <label class="label" for="customInput">Ander bedrag (optioneel)</label>
              <input id="customInput" placeholder="Bijv. 12,50" />
            </div>

            <button class="pay-btn" id="payBtn">Betaal nu</button>
            <div class="tiny">Demo-omgeving — er wordt geen echte betaling gedaan.</div>
          </div>
        </div>
      </div>
    </aside>
  </div>

  <div class="toast" id="toast"></div>

  <script>
    const goal = 250;
    let selectedAmount = 10;
    let contributors = [
      { name: 'Lisa', amount: 15 },
      { name: 'Mark', amount: 20 },
      { name: 'Sophie', amount: 10 },
      { name: 'Noor', amount: 25 }
    ];

    const contributorsEl = document.getElementById('contributors');
    const raisedText = document.getElementById('raisedText');
    const leftText = document.getElementById('leftText');
    const goalText = document.getElementById('goalText');
    const fill = document.getElementById('fill');
    const customInput = document.getElementById('customInput');
    const nameInput = document.getElementById('nameInput');
    const toast = document.getElementById('toast');
    const amountButtons = Array.from(document.querySelectorAll('.amount-btn'));

    goalText.textContent = euro(goal);

    function euro(value) {
      return new Intl.NumberFormat('nl-NL', { style: 'currency', currency: 'EUR' }).format(value);
    }

    function sumRaised() {
      return contributors.reduce((sum, c) => sum + c.amount, 0);
    }

    function showToast(message) {
      toast.textContent = message;
      toast.style.display = 'block';
      clearTimeout(showToast._timer);
      showToast._timer = setTimeout(() => toast.style.display = 'none', 2600);
    }

    function render() {
      contributorsEl.innerHTML = '';
      contributors.forEach((c) => {
        const row = document.createElement('div');
        row.className = 'contrib';
        row.innerHTML = `
          <div>${escapeHtml(c.name)}</div>
          <div style="display:flex; gap:10px; align-items:center;">
            <strong>${euro(c.amount)}</strong>
            <span class="pill-ok">betaald</span>
          </div>
        `;
        contributorsEl.appendChild(row);
      });

      const raised = sumRaised();
      const left = Math.max(goal - raised, 0);
      const progress = Math.min((raised / goal) * 100, 100);

      raisedText.textContent = euro(raised);
      leftText.textContent = euro(left);
      fill.style.width = progress + '%';

      if (raised >= goal) {
        showToast('🎉 Cadeau compleet! Het doelbedrag is bereikt.');
      }
    }

    function escapeHtml(str) {
      return str
        .replace(/&/g, '&amp;')
        .replace(/</g, '&lt;')
        .replace(/>/g, '&gt;')
        .replace(/"/g, '&quot;')
        .replace(/'/g, '&#039;');
    }

    amountButtons.forEach((btn) => {
      btn.addEventListener('click', () => {
        amountButtons.forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        selectedAmount = Number(btn.dataset.value);
        customInput.value = '';
      });
    });

    document.getElementById('payBtn').addEventListener('click', () => {
      const rawCustom = customInput.value.trim().replace(',', '.');
      const customAmount = rawCustom ? Number(rawCustom) : null;
      const amount = customAmount && customAmount > 0 ? customAmount : selectedAmount;
      const name = nameInput.value.trim() || 'Anoniem';

      if (!amount || amount <= 0 || Number.isNaN(amount)) {
        showToast('Vul een geldig bedrag in.');
        return;
      }

      contributors.unshift({ name, amount });
      render();
      showToast(`✅ ${name} heeft ${euro(amount)} bijgedragen`);
      nameInput.value = 'Jij';
      customInput.value = '';
    });

    document.getElementById('simulate').addEventListener('click', () => {
      const names = ['Emma', 'Daan', 'Mila', 'Lucas', 'Yara', 'Finn'];
      const amounts = [5, 10, 15, 20, 25];
      const name = names[Math.floor(Math.random() * names.length)];
      const amount = amounts[Math.floor(Math.random() * amounts.length)];
      contributors.unshift({ name, amount });
      render();
      document.getElementById('demo').scrollIntoView({ behavior: 'smooth', block: 'start' });
    });

    document.getElementById('focusDemo').addEventListener('click', () => {
      document.getElementById('demo').scrollIntoView({ behavior: 'smooth', block: 'start' });
    });

    render();
  </script>
</body>
</html>
