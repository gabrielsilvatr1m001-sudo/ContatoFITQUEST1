<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Fale Conosco</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Share+Tech+Mono&family=Exo+2:wght@300;400;600&display=swap" rel="stylesheet" />
  <style>
    :root {
      --neon-green: #39ff14;
      --neon-green-dim: #1aad00;
      --neon-green-glow: rgba(57, 255, 20, 0.18);
      --purple: #a855f7;
      --purple-dark: #7c3aed;
      --purple-glow: rgba(168, 85, 247, 0.18);
      --black: #050508;
      --black-card: #0c0c14;
      --black-input: #111120;
      --white: #f0f0f8;
      --white-dim: #8888aa;
      --border: rgba(168, 85, 247, 0.25);
      --border-focus: rgba(57, 255, 20, 0.6);
      --error: #ff4466;
      --error-bg: rgba(255, 68, 102, 0.1);
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--black);
      color: var(--white);
      font-family: 'Exo 2', sans-serif;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 2rem 1rem;
      position: relative;
      overflow-x: hidden;
    }

    /* ── Background grid ── */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image:
        linear-gradient(rgba(168,85,247,0.04) 1px, transparent 1px),
        linear-gradient(90deg, rgba(168,85,247,0.04) 1px, transparent 1px);
      background-size: 40px 40px;
      pointer-events: none;
      z-index: 0;
    }

    /* ── Corner glow blobs ── */
    body::after {
      content: '';
      position: fixed;
      top: -200px;
      right: -200px;
      width: 600px;
      height: 600px;
      background: radial-gradient(circle, rgba(168,85,247,0.12) 0%, transparent 70%);
      pointer-events: none;
      z-index: 0;
    }

    .blob-bottom {
      position: fixed;
      bottom: -200px;
      left: -150px;
      width: 500px;
      height: 500px;
      background: radial-gradient(circle, rgba(57,255,20,0.08) 0%, transparent 70%);
      pointer-events: none;
      z-index: 0;
    }

    /* ── Container ── */
    .container {
      position: relative;
      z-index: 1;
      width: 100%;
      max-width: 640px;
    }

    /* ── Header ── */
    .header {
      text-align: center;
      margin-bottom: 2.5rem;
    }

    .header-eyebrow {
      font-family: 'Share Tech Mono', monospace;
      font-size: 0.75rem;
      letter-spacing: 0.25em;
      color: var(--neon-green);
      text-transform: uppercase;
      margin-bottom: 0.75rem;
    }

    .header h1 {
      font-family: 'Orbitron', monospace;
      font-size: clamp(1.6rem, 5vw, 2.4rem);
      font-weight: 900;
      line-height: 1.1;
      background: linear-gradient(135deg, var(--white) 0%, var(--purple) 60%, var(--neon-green) 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 0.75rem;
    }

    .header p {
      color: var(--white-dim);
      font-size: 0.95rem;
      line-height: 1.6;
      font-weight: 300;
    }

    /* ── Decorative divider ── */
    .divider {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 2rem;
    }
    .divider-line {
      flex: 1;
      height: 1px;
      background: linear-gradient(90deg, transparent, var(--purple), transparent);
    }
    .divider-dot {
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: var(--neon-green);
      box-shadow: 0 0 8px var(--neon-green);
    }

    /* ── Card ── */
    .card {
      background: var(--black-card);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 2.5rem 2rem;
      position: relative;
      overflow: hidden;
    }

    .card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      height: 1px;
      background: linear-gradient(90deg, transparent, var(--purple), var(--neon-green), var(--purple), transparent);
    }

    /* ── Form rows ── */
    .form-row {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1rem;
    }

    @media (max-width: 520px) {
      .form-row { grid-template-columns: 1fr; }
      .card { padding: 2rem 1.25rem; }
    }

    /* ── Field group ── */
    .field {
      display: flex;
      flex-direction: column;
      gap: 6px;
      margin-bottom: 1.25rem;
    }

    .field:last-child { margin-bottom: 0; }

    .field label {
      font-family: 'Share Tech Mono', monospace;
      font-size: 0.7rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--purple);
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .field label .required-star {
      color: var(--neon-green);
    }

    /* ── Inputs ── */
    .field input,
    .field textarea,
    .field select {
      background: var(--black-input);
      border: 1px solid var(--border);
      border-radius: 8px;
      color: var(--white);
      font-family: 'Exo 2', sans-serif;
      font-size: 0.95rem;
      padding: 0.75rem 1rem;
      outline: none;
      transition: border-color 0.2s, box-shadow 0.2s, background 0.2s;
      width: 100%;
    }

    .field input::placeholder,
    .field textarea::placeholder {
      color: rgba(136, 136, 170, 0.5);
    }

    .field input:hover,
    .field textarea:hover {
      border-color: rgba(168, 85, 247, 0.5);
    }

    .field input:focus,
    .field textarea:focus {
      border-color: var(--neon-green);
      box-shadow: 0 0 0 3px var(--neon-green-glow), inset 0 0 20px rgba(57,255,20,0.03);
    }

    .field textarea {
      resize: vertical;
      min-height: 120px;
      line-height: 1.6;
    }

    /* ── Error state ── */
    .field.has-error input,
    .field.has-error textarea {
      border-color: var(--error);
      box-shadow: 0 0 0 3px var(--error-bg);
      background: rgba(255, 68, 102, 0.05);
    }

    .field-error {
      font-size: 0.75rem;
      color: var(--error);
      display: flex;
      align-items: center;
      gap: 4px;
      min-height: 16px;
      opacity: 0;
      transform: translateY(-4px);
      transition: opacity 0.2s, transform 0.2s;
    }

    .field.has-error .field-error {
      opacity: 1;
      transform: translateY(0);
    }

    /* ── Phone input wrapper ── */
    .phone-wrapper {
      position: relative;
      display: flex;
    }

    .phone-prefix {
      display: flex;
      align-items: center;
      padding: 0 0.75rem;
      background: rgba(168,85,247,0.1);
      border: 1px solid var(--border);
      border-right: none;
      border-radius: 8px 0 0 8px;
      color: var(--purple);
      font-family: 'Share Tech Mono', monospace;
      font-size: 0.85rem;
      white-space: nowrap;
      flex-shrink: 0;
    }

    .phone-wrapper input {
      border-radius: 0 8px 8px 0;
    }

    .field.has-error .phone-wrapper input {
      border-color: var(--error);
      box-shadow: 0 0 0 3px var(--error-bg);
    }

    /* ── Character counter ── */
    .char-counter {
      font-size: 0.7rem;
      color: var(--white-dim);
      text-align: right;
      font-family: 'Share Tech Mono', monospace;
    }

    .char-counter.warn { color: var(--error); }

    /* ── Submit button ── */
    .btn-submit {
      width: 100%;
      padding: 1rem 2rem;
      margin-top: 1.75rem;
      background: transparent;
      border: 1px solid var(--neon-green);
      border-radius: 8px;
      color: var(--neon-green);
      font-family: 'Orbitron', monospace;
      font-size: 0.85rem;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      cursor: pointer;
      position: relative;
      overflow: hidden;
      transition: color 0.25s, box-shadow 0.25s, background 0.25s;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
    }

    .btn-submit::before {
      content: '';
      position: absolute;
      inset: 0;
      background: var(--neon-green);
      transform: scaleX(0);
      transform-origin: left;
      transition: transform 0.3s ease;
      z-index: 0;
    }

    .btn-submit:hover:not(:disabled)::before { transform: scaleX(1); }
    .btn-submit:hover:not(:disabled) {
      color: var(--black);
      box-shadow: 0 0 24px var(--neon-green-glow);
    }

    .btn-submit:disabled {
      opacity: 0.5;
      cursor: not-allowed;
    }

    .btn-submit span,
    .btn-submit .loader {
      position: relative;
      z-index: 1;
    }

    /* ── Loader spinner ── */
    .loader {
      width: 18px;
      height: 18px;
      border: 2px solid rgba(57,255,20,0.3);
      border-top-color: var(--neon-green);
      border-radius: 50%;
      animation: spin 0.7s linear infinite;
      display: none;
    }

    .btn-submit.loading .loader { display: block; }
    .btn-submit.loading .btn-label { display: none; }

    @keyframes spin {
      to { transform: rotate(360deg); }
    }

    /* ── Status messages ── */
    .status-message {
      border-radius: 10px;
      padding: 1rem 1.25rem;
      font-size: 0.9rem;
      line-height: 1.5;
      display: none;
      align-items: flex-start;
      gap: 10px;
      margin-top: 1.25rem;
    }

    .status-message.show { display: flex; }

    .status-message.success {
      background: rgba(57,255,20,0.08);
      border: 1px solid rgba(57,255,20,0.35);
      color: var(--neon-green);
    }

    .status-message.error {
      background: var(--error-bg);
      border: 1px solid rgba(255,68,102,0.4);
      color: var(--error);
    }

    .status-icon {
      font-size: 1.1rem;
      flex-shrink: 0;
      margin-top: 1px;
    }

    /* ── Footer note ── */
    .footer-note {
      text-align: center;
      margin-top: 1.75rem;
      font-size: 0.75rem;
      color: var(--white-dim);
      font-family: 'Share Tech Mono', monospace;
      letter-spacing: 0.05em;
    }

    .footer-note a {
      color: var(--purple);
      text-decoration: none;
    }

    /* ── Hidden Google Form iframe ── */
    #gform-iframe {
      position: absolute;
      width: 1px;
      height: 1px;
      opacity: 0;
      pointer-events: none;
      border: none;
    }
  </style>
</head>
<body>
  <div class="blob-bottom" aria-hidden="true"></div>

  <!-- Hidden Google Form iframe for submission -->
  <iframe id="gform-iframe" name="gform-iframe" title="Google Form hidden" aria-hidden="true"></iframe>

  <div class="container">
    <header class="header">
      <p class="header-eyebrow">// INICIAR CONTATO</p>
      <h1>Fale Conosco</h1>
      <p>Preencha o formulário abaixo. Responderemos em até 24h.</p>
    </header>

    <div class="divider" aria-hidden="true">
      <div class="divider-line"></div>
      <div class="divider-dot"></div>
      <div class="divider-line"></div>
    </div>

    <!--
      ╔══════════════════════════════════════════════════════════╗
      ║  CONFIGURAÇÃO DO GOOGLE FORMS                            ║
      ║                                                          ║
      ║  1. Acesse seu Google Forms                              ║
      ║  2. Clique em ⋮ → "Obter link pré-preenchido"           ║
      ║  3. Preencha o formulário e clique em "Obter link"       ║
      ║  4. Copie os IDs entry.XXXXXXXX de cada campo            ║
      ║  5. Substitua os valores abaixo:                         ║
      ║     - GOOGLE_FORM_ACTION_URL → URL do seu formulário     ║
      ║     - entry.NOME, entry.EMAIL, etc → seus IDs reais      ║
      ╚══════════════════════════════════════════════════════════╝
    -->
    <form
      id="contact-form"
      novalidate
      autocomplete="off"
    >
      <!-- Campos ocultos para envio ao Google Forms (preenchidos via JS) -->
      <input type="hidden" id="gf-name"     name:entry.945852310 />
      <input type="hidden" id="gf-email"   email:entry.708940718 />
      <input type="hidden" id="gf-phone"   phone:entry.1292116560 />
      <input type="hidden" id="gf-message"  message:entry.1347743867 />

      <div class="form-row">
        <!-- Nome -->
        <div class="field" id="field-name">
          <label for="name">
            Nome Completo <span class="required-star" aria-hidden="true">*</span>
          </label>
          <input
            type="text"
            id="name"
            name="name"
            placeholder="Seu nome"
            autocomplete="name"
            aria-required="true"
            aria-describedby="err-name"
            maxlength="100"
          />
          <span class="field-error" id="err-name" role="alert" aria-live="polite"></span>
        </div>

        <!-- E-mail -->
        <div class="field" id="field-email">
          <label for="email">
            E-mail <span class="required-star" aria-hidden="true">*</span>
          </label>
          <input
            type="email"
            id="email"
            name="email"
            placeholder="seu@email.com"
            autocomplete="email"
            aria-required="true"
            aria-describedby="err-email"
            maxlength="120"
          />
          <span class="field-error" id="err-email" role="alert" aria-live="polite"></span>
        </div>
      </div>

      <!-- Telefone -->
      <div class="field" id="field-phone">
        <label for="phone">
          Telefone <span class="required-star" aria-hidden="true">*</span>
        </label>
        <div class="phone-wrapper">
          <span class="phone-prefix" aria-label="DDI Brasil">+55</span>
          <input
            type="tel"
            id="phone"
            name="phone"
            placeholder="(11) 99999-9999"
            autocomplete="tel"
            aria-required="true"
            aria-describedby="err-phone"
            maxlength="15"
            inputmode="numeric"
          />
        </div>
        <span class="field-error" id="err-phone" role="alert" aria-live="polite"></span>
      </div>

      <!-- Mensagem -->
      <div class="field" id="field-message">
        <label for="message">
          Mensagem <span class="required-star" aria-hidden="true">*</span>
        </label>
        <textarea
          id="message"
          name="message"
          placeholder="Descreva como podemos ajudar..."
          aria-required="true"
          aria-describedby="err-message"
          maxlength="1000"
        ></textarea>
        <div class="char-counter" id="char-counter" aria-live="polite">0 / 1000</div>
        <span class="field-error" id="err-message" role="alert" aria-live="polite"></span>
      </div>

      <!-- Botão de envio -->
      <button type="submit" class="btn-submit" id="btn-submit" aria-live="polite">
        <div class="loader" aria-hidden="true"></div>
        <span class="btn-label">Enviar Mensagem</span>
      </button>

      <!-- Mensagem de sucesso -->
      <div class="status-message success" id="msg-success" role="status" aria-live="polite">
        <span class="status-icon">✓</span>
        <div>
          <strong>Mensagem enviada!</strong><br />
          Recebemos seu contato e retornaremos em breve.
        </div>
      </div>

      <!-- Mensagem de erro -->
      <div class="status-message error" id="msg-error" role="alert" aria-live="polite">
        <span class="status-icon">⚠</span>
        <div>
          <strong>Falha no envio.</strong><br />
          Verifique sua conexão e tente novamente. Se o problema persistir, entre em contato por e-mail.
        </div>
      </div>
    </form>

    <p class="footer-note">
      Campos marcados com <span style="color:var(--neon-green);">*</span> são obrigatórios.
    </p>
  </div>

  <script>
    // ═══════════════════════════════════════════════════════
    //  CONFIGURAÇÃO — substitua pelos valores do seu Google Forms
    // ═══════════════════════════════════════════════════════
    const GOOGLE_FORM_ACTION =
      'https://docs.google.com/forms/d/e/1FAIpQLSd7x0T860R0WJQIWefLMoYlMmMrwSpqoSjLCDSU3AevTA_Mvw/formResponse';

    const FIELD_IDS = {
     name:    'entry.945852310', // ← substitua pelo ID real
     email:   'entry.708940718', // ← substitua pelo ID real
     phone:   'entry.1292116560',  // ← substitua pelo ID real
     message: 'entry.1347743867',  // ← substitua pelo ID real
    };
    // ═══════════════════════════════════════════════════════

    const form      = document.getElementById('contact-form');
    const btnSubmit = document.getElementById('btn-submit');
    const msgOk     = document.getElementById('msg-success');
    const msgErr    = document.getElementById('msg-error');
    const counter   = document.getElementById('char-counter');
    const messageEl = document.getElementById('message');

    // ── Character counter ──
    messageEl.addEventListener('input', () => {
      const len = messageEl.value.length;
      counter.textContent = `${len} / 1000`;
      counter.classList.toggle('warn', len > 900);
    });

    // ── Phone mask ──
    document.getElementById('phone').addEventListener('input', function () {
      let v = this.value.replace(/\D/g, '').slice(0, 11);
      if (v.length > 2) v = `(${v.slice(0,2)}) ${v.slice(2)}`;
      if (v.length > 10) v = v.slice(0, 10) + '-' + v.slice(10);
      this.value = v;
    });

    // ── Validation helpers ──
    function showError(fieldId, msg) {
      const wrap = document.getElementById('field-' + fieldId);
      const err  = document.getElementById('err-' + fieldId);
      wrap.classList.add('has-error');
      err.textContent = '⚠ ' + msg;
    }

    function clearError(fieldId) {
      const wrap = document.getElementById('field-' + fieldId);
      const err  = document.getElementById('err-' + fieldId);
      wrap.classList.remove('has-error');
      err.textContent = '';
    }

    function validateEmail(v) {
      return /^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/.test(v.trim());
    }

    function validatePhone(v) {
      return v.replace(/\D/g,'').length >= 10;
    }

    function validate() {
      let ok = true;
      const name    = document.getElementById('name').value.trim();
      const email   = document.getElementById('email').value.trim();
      const phone   = document.getElementById('phone').value.trim();
      const message = messageEl.value.trim();

      clearError('name');
      clearError('email');
      clearError('phone');
      clearError('message');

      if (!name) {
        showError('name', 'Nome é obrigatório.');
        ok = false;
      } else if (name.length < 2) {
        showError('name', 'Insira pelo menos 2 caracteres.');
        ok = false;
      }

      if (!email) {
        showError('email', 'E-mail é obrigatório.');
        ok = false;
      } else if (!validateEmail(email)) {
        showError('email', 'E-mail inválido.');
        ok = false;
      }

      if (!phone) {
        showError('phone', 'Telefone é obrigatório.');
        ok = false;
      } else if (!validatePhone(phone)) {
        showError('phone', 'Insira um telefone válido (DDD + número).');
        ok = false;
      }

      if (!message) {
        showError('message', 'Mensagem é obrigatória.');
        ok = false;
      } else if (message.length < 10) {
        showError('message', 'Mensagem muito curta (mín. 10 caracteres).');
        ok = false;
      }

      return ok;
    }

    // ── Inline validation on blur ──
    ['name','email','phone','message'].forEach(id => {
      const el = document.getElementById(id);
      el.addEventListener('blur', () => {
        if (el.value.trim()) clearError(id);
      });
    });

    // ── Submit ──
    form.addEventListener('submit', async (e) => {
      e.preventDefault();

      msgOk.classList.remove('show');
      msgErr.classList.remove('show');

      if (!validate()) {
        // Scroll to first error
        const firstErr = form.querySelector('.has-error input, .has-error textarea');
        if (firstErr) firstErr.focus();
        return;
      }

      // Populate Google Form hidden fields
      document.getElementById('gf-name').name    = FIELD_IDS.name;
      document.getElementById('gf-email').name   = FIELD_IDS.email;
      document.getElementById('gf-phone').name   = FIELD_IDS.phone;
      document.getElementById('gf-message').name = FIELD_IDS.message;

      document.getElementById('gf-name').value    = document.getElementById('name').value.trim();
      document.getElementById('gf-email').value   = document.getElementById('email').value.trim();
      document.getElementById('gf-phone').value   = '+55 ' + document.getElementById('phone').value.trim();
      document.getElementById('gf-message').value = messageEl.value.trim();

      // Loading state
      btnSubmit.disabled = true;
      btnSubmit.classList.add('loading');

      try {
        // Build FormData and POST to Google Forms via fetch (no-cors)
        const data = new FormData();
        data.append(FIELD_IDS.name,    document.getElementById('gf-name').value);
        data.append(FIELD_IDS.email,   document.getElementById('gf-email').value);
        data.append(FIELD_IDS.phone,   document.getElementById('gf-phone').value);
        data.append(FIELD_IDS.message, document.getElementById('gf-message').value);

        // Google Forms does not allow CORS, so we use no-cors (response is opaque — treat any finish as success)
        const response = await fetch(GOOGLE_FORM_ACTION, {
          method: 'POST',
          mode: 'no-cors',
          body: data,
        });

        // With no-cors, response.type === 'opaque'; we assume success
        form.reset();
        counter.textContent = '0 / 1000';
        msgOk.classList.add('show');
        msgOk.scrollIntoView({ behavior: 'smooth', block: 'nearest' });

      } catch (err) {
        console.error('Form submission error:', err);
        msgErr.classList.add('show');
        msgErr.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
      } finally {
        btnSubmit.disabled = false;
        btnSubmit.classList.remove('loading');
      }
    });
  </script>
</body>
</html>
