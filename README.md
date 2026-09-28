# name-guesser-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Open Gmail Name Guesser</title>
  <style>
    body {
      margin: 0;
      min-height: 100vh;
      display: grid;
      place-items: center;
      background: linear-gradient(135deg, #10172e, #263d70);
      font-family: Arial, sans-serif;
    }
    .btn {
      display: inline-block;
      padding: 16px 28px;
      border-radius: 12px;
      background: linear-gradient(100deg, #6488ff, #8769ed);
      color: white;
      text-decoration: none;
      font-weight: 700;
      font-size: 18px;
      box-shadow: 0 12px 30px rgba(0,0,0,0.25);
    }
  </style>
</head>
<body>
  <a href="./gmail_name_guesser-1.html" class="btn" target="_blank" rel="noopener">
    Open Gmail Name Guesser
  </a>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Gmail Name Predictor</title>
  <style>
    :root {
      --bg-color: #0f172a;
      --card-bg: #1e293b;
      --accent-color: #38bdf8;
      --accent-hover: #0284c7;
      --text-color: #f8fafc;
      --text-muted: #94a3b8;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background-color: var(--bg-color);
      color: var(--text-color);
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 20px;
    }

    .container {
      background-color: var(--card-bg);
      padding: 40px;
      border-radius: 16px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5);
      width: 100%;
      max-width: 480px;
      text-align: center;
    }

    h1 {
      font-size: 1.8rem;
      margin-bottom: 8px;
    }

    p.subtitle {
      color: var(--text-muted);
      font-size: 0.95rem;
      margin-bottom: 24px;
    }

    .input-group {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-bottom: 24px;
    }

    input[type="text"] {
      width: 100%;
      padding: 14px 16px;
      border-radius: 8px;
      border: 1px solid #334155;
      background-color: #0f172a;
      color: var(--text-color);
      font-size: 1rem;
      outline: none;
      transition: border-color 0.2s;
    }

    input[type="text"]:focus {
      border-color: var(--accent-color);
    }

    button {
      padding: 14px;
      border: none;
      border-radius: 8px;
      background-color: var(--accent-color);
      color: #0f172a;
      font-weight: 600;
      font-size: 1rem;
      cursor: pointer;
      transition: background-color 0.2s, transform 0.1s;
    }

    button:hover {
      background-color: var(--accent-hover);
    }

    button:active {
      transform: scale(0.98);
    }

    .result-box {
      margin-top: 20px;
      padding: 20px;
      border-radius: 8px;
      background-color: #0f172a;
      display: none;
      animation: fadeIn 0.4s ease-in-out forwards;
    }

    .result-title {
      font-size: 0.85rem;
      color: var(--text-muted);
      text-transform: uppercase;
      letter-spacing: 1px;
      margin-bottom: 6px;
    }

    .predicted-name {
      font-size: 1.6rem;
      font-weight: bold;
      color: var(--accent-color);
    }

    .error-msg {
      color: #f87171;
      font-size: 0.9rem;
      margin-top: 10px;
      display: none;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Gmail Name Predictor</h1>
    <p class="subtitle">Enter a Gmail address to reveal the likely name behind it.</p>

    <div class="input-group">
      <input type="text" id="emailInput" placeholder="example: john.doe99@gmail.com">
      <button onclick="guessName()">Predict Name</button>
    </div>

    <div id="errorMsg" class="error-msg">Please enter a valid Gmail address (e.g., user@gmail.com).</div>

    <div id="resultBox" class="result-box">
      <div class="result-title">Predicted Name</div>
      <div class="predicted-name" id="predictedName">--</div>
    </div>
  </div>

  <script>
    function guessName() {
      const emailInput = document.getElementById('emailInput').value.trim();
      const errorMsg = document.getElementById('errorMsg');
      const resultBox = document.getElementById('resultBox');
      const predictedNameEl = document.getElementById('predictedName');

      // Validation for Gmail address format
      const gmailRegex = /^[a-zA-Z0-9._%+-]+@gmail\.com$/i;
      
      if (!gmailRegex.test(emailInput)) {
        errorMsg.style.display = 'block';
        resultBox.style.display = 'none';
        return;
      }

      errorMsg.style.display = 'none';

      // Extract username before @gmail.com
      let username = emailInput.split('@')[0];

      // Remove numbers and replace separators with spaces
      let cleaned = username.replace(/[0-9]/g, '').replace(/[._-]/g, ' ').trim();

      if (!cleaned) {
        cleaned = username;
      }

      // Format to Title Case
      const formattedName = cleaned
        .split(' ')
        .filter(word => word.length > 0)
        .map(word => word.charAt(0).toUpperCase() + word.slice(1).toLowerCase())
        .join(' ');

      predictedNameEl.textContent = formattedName;
      resultBox.style.display = 'block';
    }
  </script>

</body>
</html>

