<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Instagram | Security Awareness (No OTP Display)</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: linear-gradient(145deg, #f5f7fa 0%, #eef2f5 100%);
      font-family: 'Inter', system-ui, -apple-system, 'Segoe UI', Roboto, Helvetica, sans-serif;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 1.5rem;
    }
    .sim-card {
      max-width: 440px;
      width: 100%;
      background: white;
      border-radius: 32px;
      box-shadow: 0 20px 35px -12px rgba(0, 0, 0, 0.15), 0 1px 3px rgba(0, 0, 0, 0.05);
      overflow: hidden;
      transition: all 0.2s ease;
    }

    .brand-header {
      text-align: center;
      padding: 32px 20px 16px 20px;
      border-bottom: 1px solid #efefef;
    }
    .brand-icon {
      font-size: 2.8rem;
      margin-bottom: 8px;
    }
    .brand-name {
      font-size: 1.7rem;
      font-weight: 600;
      background: linear-gradient(135deg, #262626, #6c6c6c);
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
      letter-spacing: -0.3px;
    }
    .demo-badge {
      background: #f0f2f5;
      display: inline-block;
      padding: 4px 12px;
      border-radius: 40px;
      font-size: 0.7rem;
      font-weight: 500;
      color: #3c4043;
      margin-top: 8px;
    }

    .views-container {
      padding: 28px 24px 32px;
    }

    .view {
      display: none;
      animation: fadeIn 0.25s ease;
    }

    .view.active {
      display: block;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(6px);}
      to { opacity: 1; transform: translateY(0);}
    }

    .input-group {
      margin-bottom: 16px;
    }
    input {
      width: 100%;
      padding: 12px 16px;
      font-size: 0.95rem;
      font-family: inherit;
      border: 1px solid #dbdbdb;
      border-radius: 12px;
      background: #fafafa;
      transition: 0.2s;
      outline: none;
    }
    input:focus {
      border-color: #0095f6;
      background: white;
      box-shadow: 0 0 0 3px rgba(0,149,246,0.1);
    }
    button {
      width: 100%;
      background: #0095f6;
      color: white;
      font-weight: 600;
      font-size: 0.95rem;
      padding: 12px;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      font-family: inherit;
      transition: 0.2s;
      margin-top: 8px;
    }
    button:hover {
      background: #1877f2;
      transform: scale(0.98);
    }
    button.secondary {
      background: #efefef;
      color: #262626;
      margin-top: 12px;
      border: 1px solid #dbdbdb;
    }
    button.secondary:hover {
      background: #e4e4e4;
      transform: none;
    }
    .forgot-link {
      text-align: center;
      margin-top: 20px;
      font-size: 0.85rem;
      color: #0095f6;
      font-weight: 500;
      cursor: pointer;
    }
    .forgot-link:hover {
      text-decoration: underline;
    }
    .warning-note {
      font-size: 0.7rem;
      text-align: center;
      color: #8e8e8e;
      margin-top: 20px;
      background: #fef7e0;
      padding: 8px 10px;
      border-radius: 12px;
    }

    .info-line {
      background: #f2f2f2;
      padding: 12px;
      border-radius: 14px;
      margin-bottom: 20px;
      font-size: 0.9rem;
      text-align: center;
    }

    .failure-icon {
      font-size: 3.5rem;
      text-align: center;
      margin: 10px 0 12px;
    }
    .result-title {
      text-align: center;
      font-weight: 700;
      font-size: 1.4rem;
      color: #ed4956;
      margin-bottom: 16px;
    }
    .tips-card {
      background: #f8f9fc;
      border-radius: 20px;
      padding: 18px;
      margin: 20px 0;
      border-left: 4px solid #0095f6;
    }
    .tips-card p {
      font-weight: 600;
      margin-bottom: 8px;
    }
    .tips-card ul {
      padding-left: 20px;
      font-size: 0.85rem;
      color: #2c3e50;
    }
    .tips-card li {
      margin: 8px 0;
    }

    .stats-area {
      background: #f9f9fb;
      margin-top: 20px;
      padding: 12px 16px;
      border-radius: 20px;
      font-size: 0.75rem;
      color: #5e5e5e;
      display: flex;
      justify-content: space-between;
      border-top: 1px solid #ececec;
    }
    .disclaimer-footer {
      text-align: center;
      font-size: 0.7rem;
      color: #8a8a8a;
      padding: 16px 20px 22px;
      background: #ffffff;
      border-top: 1px solid #efefef;
    }
  </style>
</head>
<body>

<div class="sim-card">
  <div class="brand-header">
    <div class="brand-icon">𓆩♛𓆪</div>
    <div class="brand-name">Instagram </div>
    <div class="demo-badge">🔐 SECURITY AWARENESS • RESET MODE</div>
  </div>

  <div class="views-container">
    <!-- LOGIN VIEW (Step 1) -->
    <div id="loginView" class="view active">
      <div class="input-group">
        <input type="text" id="usernameInput" placeholder="Username, email or phone number" autocomplete="off">
      </div>
      <div class="input-group">
        <input type="password" id="passwordInput" placeholder="Password (forget only)">
      </div>
      <button id="fakeLoginBtn">Log in</button>
      <div class="forgot-link" id="forgotPasswordTrigger">Forgot password?</div>
      <div class="warning-note">
        ⚡ This is an educational simulation. Use "Forgot password?" to experience how  pages request OTP.
      </div>
    </div>

    <!-- OTP VERIFICATION VIEW (Step 2) – No OTP code displayed -->
    <div id="otpView" class="view">
      <div class="info-line">
        🔐 Password reset for: <strong id="displayUsername"></strong>
      </div>
      <div class="input-group">
        <input type="text" id="otpCodeInput" placeholder="Enter verification code (OTP)" maxlength="6" autocomplete="off">
      </div>
      <button id="verifyOtpBtn">Verify & Log in</button>
      <button id="backToLoginFromOtp" class="secondary">← Back to login</button>
      <div style="font-size:0.7rem; text-align:center; margin-top:16px; color:#777;">
        💡 In a real  attack, you would receive an OTP via SMS/email.  
        Here, any code you enter will fail — showing how scammers trick victims.
      </div>
    </div>

    <!-- FAILURE + EDUCATIONAL VIEW (Step 3) -->
    <div id="resultView" class="view">
      <div class="failure-icon">⚠️❌</div>
      <div class="result-title">Login failed due to security reasons</div>
      <div class="tips-card">
        <p>🧠 <strong>What just happened?</strong></p>
        <p style="font-size:0.85rem; margin-bottom: 12px;">Even after entering an OTP, this simulation denied access — because real  pages can steal your credentials and still show errors to confuse you.</p>
        <p>✅ <strong>Security Tips to stay safe:</strong></p>
        <ul>
          <li>✔️ Always check the URL: real Instagram login is <strong>instagram.com</strong></li>
          <li>✔️ Never share your OTP with anyone — not even "support"</li>
          <li>✔️ Enable two-factor authentication inside the official app</li>
          <li>✔️ Beware of pages that ask for OTP outside the official app/website</li>
          <li>✔️ This simulation shows how  can mimic real interfaces without showing any real code</li>
        </ul>
      </div>
      <button id="resetFromResultBtn">🔄 Try simulation again</button>
    </div>
  </div>

  <!-- analytics & educational stats -->
  <div class="stats-area">
    <span>📊 Session stats (educational)</span>
    <span>🔁 OTP requests: <strong id="statOtpRequests">0</strong></span>
    <span>📤 OTP submissions: <strong id="statOtpSubmits">0</strong></span>
  </div>
  <div class="disclaimer-footer">
    ⚠️ EDUCATIONAL SIMULATION ONLY — No real Instagram login. No data is collected or transmitted.<br>
    Not affiliated with Instagram or Meta Platforms. For security training &  awareness.
  </div>
</div>

<script>
  // ---------- SIMULATION STATE (No OTP displayed, always fail after OTP entry) ----------
  let currentUsername = "";
  // Analytics counters (session-based)
  let otpRequestCount = 0;     // counts how many times user reached OTP screen
  let otpSubmitCount = 0;      // counts how many times user clicked "Verify"

  // DOM elements
  const loginView = document.getElementById('loginView');
  const otpView = document.getElementById('otpView');
  const resultView = document.getElementById('resultView');

  // Login view elements
  const usernameInput = document.getElementById('usernameInput');
  const passwordInput = document.getElementById('passwordInput');
  const fakeLoginBtn = document.getElementById('fakeLoginBtn');
  const forgotPasswordTrigger = document.getElementById('forgotPasswordTrigger');

  // OTP view elements
  const displayUsernameSpan = document.getElementById('displayUsername');
  const otpCodeInput = document.getElementById('otpCodeInput');
  const verifyOtpBtn = document.getElementById('verifyOtpBtn');
  const backToLoginFromOtp = document.getElementById('backToLoginFromOtp');

  // Result view
  const resetFromResultBtn = document.getElementById('resetFromResultBtn');

  // Analytics spans
  const statOtpRequestsSpan = document.getElementById('statOtpRequests');
  const statOtpSubmitsSpan = document.getElementById('statOtpSubmits');

  // Helper: update analytics UI
  function updateAnalyticsUI() {
    statOtpRequestsSpan.innerText = otpRequestCount;
    statOtpSubmitsSpan.innerText = otpSubmitCount;
  }

  // Helper: show specific view
  function showView(viewName) {
    loginView.classList.remove('active');
    otpView.classList.remove('active');
    resultView.classList.remove('active');
    if (viewName === 'login') loginView.classList.add('active');
    else if (viewName === 'otp') otpView.classList.add('active');
    else if (viewName === 'result') resultView.classList.add('active');
  }

  // Start OTP flow (called when user clicks "Forgot password?")
  function initiateOtpFlow() {
    let username = usernameInput.value.trim();
    if (username === "") {
      alert("🔍 Please enter a username to continue the security forgettenstration.\n(This simulates how  sites request your username first.)");
      return false;
    }
    // Store username for display
    currentUsername = username;
    displayUsernameSpan.innerText = currentUsername;
    
    // Clear any previous OTP input
    otpCodeInput.value = "";
    
    // Increment OTP request counter (user reached OTP screen)
    otpRequestCount++;
    updateAnalyticsUI();
    
    // Switch to OTP view (no code is shown anywhere)
    showView('otp');
    return true;
  }

  // Handle OTP verification: ALWAYS go to failure screen regardless of input
  // This matches the requirement: OTP enter karne ke baad bhi login fail ho jaye
  function handleOtpVerification() {
    // Increment submission counter (every time user clicks verify)
    otpSubmitCount++;
    updateAnalyticsUI();
    
    // Optional: capture the entered OTP for educational logging (not stored/transmitted)
    const enteredOtp = otpCodeInput.value.trim();
    // For forgettenstration, we can silently log to console (purely educational)
    if (enteredOtp !== "") {
      console.log(`[SIMULATION] User entered OTP: "${enteredOtp}" for username "${currentUsername}" — access denied (simulated  failure).`);
    } else {
      console.log(`[SIMULATION] User submitted empty OTP for "${currentUsername}" — access denied.`);
    }
    
    // Always show failure screen with security tips
    showView('result');
  }

  // Reset everything: back to login, clear fields, keep analytics counters (educational stats persist)
  function resetFromResult() {
    usernameInput.value = "";
    passwordInput.value = "";
    otpCodeInput.value = "";
    currentUsername = "";
    showView('login');
    // analytics counters are intentionally NOT reset to reflect total session attempts
  }

  // Back to login from OTP screen (without triggering failure)
  function backToLoginFromOtpHandler() {
    currentUsername = "";
    otpCodeInput.value = "";
    showView('login');
  }

  // Fake login button: educational alert
  function handleFakeLogin() {
    alert("🔐 This is a security simulation.\n\nReal Instagram would attempt login, but this forget is built to teach about OTP .\n👉 Please use 'Forgot password?' to experience how to pages trick users.\n\nNever enter your real Instagram credentials on untrusted pages.");
  }

  // ----- EVENT LISTENERS -----
  fakeLoginBtn.addEventListener('click', handleFakeLogin);
  forgotPasswordTrigger.addEventListener('click', initiateOtpFlow);
  verifyOtpBtn.addEventListener('click', handleOtpVerification);
  backToLoginFromOtp.addEventListener('click', backToLoginFromOtpHandler);
  resetFromResultBtn.addEventListener('click', resetFromResult);

  // Pressing Enter on OTP input also triggers verification
  otpCodeInput.addEventListener('keypress', (e) => {
    if (e.key === 'Enter') {
      e.preventDefault();
      handleOtpVerification();
    }
  });

  // Pressing Enter on username field (login view) triggers OTP flow (forgotten password simulation)
  usernameInput.addEventListener('keypress', (e) => {
    if (e.key === 'Enter') {
      e.preventDefault();
      initiateOtpFlow();
    }
  });

  // Initialize analytics UI
  updateAnalyticsUI();
  
  // Additional safety / educational console message
  console.log("Instagram Security loaded — OTP code never displayed. Any OTP entry leads to login failure,forget.");
</script>
</body>
</html>
