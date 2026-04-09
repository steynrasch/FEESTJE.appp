<!DOCTYPE html>
<html lang="nl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>FEESTJE — Cadeau voor Steyn</title>
  <style>
    :root {
      --bg: #050505;
      --panel: #0d0d0d;
      --panel-2: #111111;
      --text: #f5f5f5;
      --muted: #9fa3a7;
      --line: rgba(255,255,255,0.12);
      --accent: #b6ff00;
      --accent-2: #7fff00;
      --danger: #ff5f57;
      --shadow: 0 20px 50px rgba(0,0,0,0.45);
      --radius: 22px;
    }

    * { box-sizing: border-box; }

    html, body {
      margin: 0;
      padding: 0;
      background:
        radial-gradient(circle at top right, rgba(182,255,0,0.12), transparent 26%),
        linear-gradient(180deg, #050505 0%, #090909 100%);
      color: var(--text);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      min-height: 100%;
    }

    body {
      display: flex;
      justify-content: center;
      padding: 28px 14px;
    }

    .phone {
      width: 100%;
      max-width: 430px;
      min-height: calc(100vh - 28px);
      border: 1px solid var(--line);
      border-radius: 32px;
      background:
        linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.01)),
        var(--bg);
      box-shadow: var(--shadow);
      overflow: hidden;
      position: relative;
    }

    .noise::before {
      content: "";
      position: absolute;
      inset: 0;
      pointer-events: none;
      background-image:
        linear-gradient(rgba(255,255,255,0.02) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.02) 1px, transparent 1px);
      background-size: 28px 28px;
      opacity: 0.22;
      mix-blend-mode: screen;
    }

    .topbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 18px 18px 10px;
      position: relative;
      z-index: 1;
    }

    .brand {
      font-weight: 900;
      letter-spacing: 0.06em;
      font-size: 0.9rem;
    }

    .brand-dot { color: var(--accent); }

    .chip {
      border: 1px solid var(--line);
      color: var(--muted);
      padding: 7px 10px;
      border-radius: 999px;
      font-size: 0.78rem;
      background: rgba(255,255,255,0.02);
    }

    .hero {
      padding: 10px 18px 6px;
      position: relative;
      z-index: 1;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      color: var(--accent);
      font-weight: 700;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      font-size: 0.78rem;
      margin-bottom: 12px;
    }

    .eyebrow::before {
      content: "";
      width: 22px;
      height: 1px;
      background: var(--accent);
      display: inline-block;
    }

    h1 {
      margin: 0;
      font-size: clamp(2.2rem, 8vw, 3.4rem);
      line-height: 0.95;
      letter-spacing: -0.04em;
      text-transform: uppercase;
    }

    .subline {
      margin-top: 14px;
      color: var(--muted);
      font-size: 0.98rem;
      line-height: 1.5;
    }

    .accent-line {
      margin-top: 16px;
      width: 110px;
      height: 4px;
      background: linear-gradient(90deg, var(--accent), transparent);
      border-radius: 999px;
    }

    .grid {
      display: grid;
      gap: 12px;
      padding: 18px;
      position: relative;
      z-index: 1;
    }

    .card {
      background: linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.01));
      border: 1px solid var(--line);
      border-radius: var(--radius);
      padding: 16px;
      backdrop-filter: blur(6px);
    }

    .stats {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
    }

    .stat-number {
      font-size: 1.7rem;
      font-weight: 900;
      letter-spacing: -0.04em;
    }

    .stat-label {
      color: var(--muted);
      font-size: 0.85rem;
      margin-top: 4px;
    }

    .progress-wrap {
      margin-top: 14px;
    }

    .progress-meta {
      display: flex;
      justify-content: space-between;
      color: var(--muted);
      font-size: 0.84rem;
      margin-bottom: 8px;
    }

    .progress {
      width: 100%;
      height: 12px;
      border-radius: 999px;
      background: rgba(255,255,255,0.08);
      overflow: hidden;
    }

    .progress-bar {
      width: 80%;
      height: 100%;
      background: linear-gradient(90deg, var(--accent), var(--accent-2));
      box-shadow: 0 0 22px rgba(182,255,0,0.45);
    }

    .cta {
      display: block;
      width: 100%;
      border: none;
      border-radius: 18px;
      padding: 18px 16px;
      background: var(--accent);
      color: #0a0a0a;
      font-size: 1rem;
      font-weight: 900;
      text-transform: uppercase;
      letter-spacing: 0.04em;
      cursor: pointer;
      transition: transform .15s ease, box-shadow .15s ease;
      box-shadow: 0 12px 28px rgba(182,255,0,0.22);
    }

    .cta:hover { transform: translateY(-1px); }
    .cta:active { transform: translateY(1px); }

    .small {
      color: var(--muted);
      font-size: 0.83rem;
      margin-top: 10px;
      text-align: center;
    }

    .section-title {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 14px;
    }

    .section-title h2 {
      font-size: 0.95rem;
      margin: 0;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .people {
      display: grid;
      gap: 10px;
    }

    .person {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 12px 0;
      border-top: 1px solid rgba(255,255,255,0.08);
    }

    .person:first-child { border-top: 0; padding-top: 0; }

    .person-left {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .avatar {
      width: 38px;
      height: 38px;
      border-radius: 50%;
      border: 1px solid rgba(255,255,255,0.15);
      display: grid;
      place-items: center;
      color: #050505;
      background: linear-gradient(135deg, var(--accent), #d4ff75);
      font-weight: 900;
      font-size: 0.9rem;
    }

    .name {
      font-weight: 700;
    }

    .status {
      font-size: 0.85rem;
      color: var(--muted);
      font-weight: 700;
      letter-spacing: 0.02em;
    }

    .status.paid { color: var(--accent); }
    .status.pending { color: #ffbf69; }

    .footer-note {
      display: flex;
      justify-content: space-between;
      gap: 12px;
      color: var(--muted);
      font-size: 0.8rem;
      line-height: 1.5;
      padding: 0 18px 24px;
      position: relative;
      z-index: 1;
    }

    .modal {
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.68);
      display: none;
      align-items: flex-end;
      justify-content: center;
      padding: 12px;
      z-index: 30;
    }

    .modal.active { display: flex; }

    .sheet {
      width: 100%;
      max-width: 430px;
      background: #0a0a0a;
      border: 1px solid var(--line);
      border-radius: 24px 24px 16px 16px;
      padding: 18px;
      box-shadow: var(--shadow);
    }

    .sheet h3 {
      margin: 0 0 14px;
      text-transform: uppercase;
      letter-spacing: 0.05em;
      font-size: 1rem;
    }

    .amount-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;
      margin-bottom: 14px;
    }

    .amount-btn, .pay-btn, .close-btn {
      border: 1px solid var(--line);
      border-radius: 14px;
      padding: 14px 10px;
      font-weight: 800;
      cursor: pointer;
      background: var(--panel-2);
      color: var(--text);
      text-align: center;
    }

    .amount-btn.active {
      background: var(--accent);
      color: #050505;
      border-color: transparent;
    }

    .custom-row {
      display: flex;
      gap: 10px;
      margin-bottom: 14px;
    }

    .custom-row input {
      flex: 1;
      border-radius: 14px;
      border: 1px solid var(--line);
      background: var(--panel-2);
      color: var(--text);
      padding: 14px;
      font-size: 1rem;
    }

    .pay-btn {
      width: 100%;
      background: var(--accent);
      color: #050505;
      border: 0;
      margin-top: 6px;
    }

    .close-btn {
      width: 100%;
      margin-top: 10px;
      background: transparent;
    }

    .success {
      text-align: center;
      display: none;
    }

    .success.active { display: block; }

    .pulse {
      width: 72px;
      height: 72px;
      border-radius: 50%;
      margin: 8px auto 14px;
      display: grid;
      place-items: center;
      background: radial-gradient(circle, #d7ff7b 0%, var(--accent) 50%, rgba(182,255,0,0.15) 100%);
      color: #050505;
      font-size: 1.8rem;
      font-weight: 900;
      box-shadow: 0 0 30px rgba(182,255,0,0.35);
    }
  </style>
</head>
<body>
  <div class="phone noise">
    <div class="topbar">
      <div class="brand">FEESTJE<span class="brand-dot">.</span></div>
      <div class="chip">PRIVATE GIFT LINK</div>
    </div>

    <section class="hero">
      <div class="eyebrow">Gift drop</div>
      <h1>Cadeau<br>voor Steyn</h1>
      <div class="subline">Vrijdag 20:00 • Verjaardag • Amsterdam</div>
      <div class="accent-line"></div>
    </section>

    <main class="grid">
      <section class="card">
        <div class="stats">
          <div>
            <div class="stat-number" id="countDisplay">12</div>
            <div class="stat-label">mensen doen mee</div>
          </div>
          <div>
            <div class="stat-number">€<span id="amountDisplay">120</span></div>
            <div class="stat-label">nu verzameld</div>
          </div>
        </div>

        <div class="progress-wrap">
          <div class="progress-meta">
            <span>Doelbedrag</span>
            <span>€<span id="amountMeta">120</span> / €150</span>
          </div>
          <div class="progress"><div class="progress-bar" id="progressBar"></div></div>
        </div>
      </section>

      <section class="card">
        <button class="cta" id="openModalBtn">Doe mee aan het cadeau</button>
        <div class="small">Kies zelf je bedrag en reken direct af.</div>
      </section>

      <section class="card">
        <div class="section-title">
          <h2>Wie hebben betaald</h2>
          <span class="chip">LIVE</span>
        </div>
        <div class="people" id="peopleList">
          <div class="person">
            <div class="person-left">
              <div class="avatar">J</div>
              <div>
                <div class="name">Jan</div>
                <div class="status paid">€10 betaald</div>
              </div>
            </div>
            <div class="status paid">DONE</div>
          </div>
          <div class="person">
            <div class="person-left">
              <div class="avatar">L</div>
              <div>
                <div class="name">Lisa</div>
                <div class="status paid">€15 betaald</div>
              </div>
            </div>
            <div class="status paid">DONE</div>
          </div>
          <div class="person">
            <div class="person-left">
              <div class="avatar">E</div>
              <div>
                <div class="name">Emma</div>
                <div class="status paid">€10 betaald</div>
              </div>
            </div>
            <div class="status paid">DONE</div>
          </div>
          <div class="person">
            <div class="person-left">
              <div class="avatar">T</div>
              <div>
                <div class="name">Tom</div>
                <div class="status pending">nog niet betaald</div>
              </div>
            </div>
            <div class="status pending">PENDING</div>
          </div>
        </div>
      </section>
    </main>

    <div class="footer-note">
      <span>⚠️ Niet bedoeld voor Steyn.</span>
      <span>Deadline: donderdag 18:00</span>
    </div>
  </div>

  <div class="modal" id="modal">
    <div class="sheet" id="sheetDefault">
      <h3>Kies je bijdrage</h3>
      <div class="amount-grid">
        <button class="amount-btn" data-amount="5">€5</button>
        <button class="amount-btn active" data-amount="10">€10</button>
        <button class="amount-btn" data-amount="15">€15</button>
      </div>
      <div class="custom-row">
        <input id="customAmount" type="number" min="1" step="1" placeholder="Ander bedrag" />
      </div>
      <button class="pay-btn" id="payBtn">Betaal €10</button>
      <button class="close-btn" id="closeBtn">Sluiten</button>
    </div>

    <div class="sheet success" id="sheetSuccess">
      <div class="pulse">✓</div>
      <h3>Je doet mee</h3>
      <p style="color: var(--muted); margin-top: 0; line-height: 1.6;">Je bijdrage is toegevoegd. Het totaal en het aantal deelnemers zijn bijgewerkt.</p>
      <button class="pay-btn" id="doneBtn">Terug naar link</button>
    </div>
  </div>

  <script>
    let selectedAmount = 10;
    let currentCount = 12;
    let currentAmount = 120;
    const goal = 150;

    const modal = document.getElementById('modal');
    const openModalBtn = document.getElementById('openModalBtn');
    const closeBtn = document.getElementById('closeBtn');
    const doneBtn = document.getElementById('doneBtn');
    const payBtn = document.getElementById('payBtn');
    const amountButtons = document.querySelectorAll('.amount-btn');
    const customAmount = document.getElementById('customAmount');
    const sheetDefault = document.getElementById('sheetDefault');
    const sheetSuccess = document.getElementById('sheetSuccess');

    const countDisplay = document.getElementById('countDisplay');
    const amountDisplay = document.getElementById('amountDisplay');
    const amountMeta = document.getElementById('amountMeta');
    const progressBar = document.getElementById('progressBar');
    const peopleList = document.getElementById('peopleList');

    function updatePayButton() {
      payBtn.textContent = `Betaal €${selectedAmount}`;
    }

    function updateTopStats() {
      countDisplay.textContent = currentCount;
      amountDisplay.textContent = currentAmount;
      amountMeta.textContent = currentAmount;
      const percentage = Math.min((currentAmount / goal) * 100, 100);
      progressBar.style.width = percentage + '%';
    }

    function setActiveAmount(button) {
      amountButtons.forEach(btn => btn.classList.remove('active'));
      button.classList.add('active');
      selectedAmount = Number(button.dataset.amount);
      customAmount.value = '';
      updatePayButton();
    }

    amountButtons.forEach(button => {
      button.addEventListener('click', () => setActiveAmount(button));
    });

    customAmount.addEventListener('input', () => {
      amountButtons.forEach(btn => btn.classList.remove('active'));
      const value = Number(customAmount.value);
      selectedAmount = value > 0 ? value : 10;
      updatePayButton();
    });

    openModalBtn.addEventListener('click', () => {
      modal.classList.add('active');
      sheetDefault.style.display = 'block';
      sheetSuccess.classList.remove('active');
    });

    closeBtn.addEventListener('click', () => {
      modal.classList.remove('active');
    });

    doneBtn.addEventListener('click', () => {
      modal.classList.remove('active');
    });

    modal.addEventListener('click', (e) => {
      if (e.target === modal) {
        modal.classList.remove('active');
      }
    });
