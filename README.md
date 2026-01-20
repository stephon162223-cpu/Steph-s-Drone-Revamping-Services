<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Paper Trading Platform</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #0f172a;
      color: #e5e7eb;
      margin: 0;
      padding: 0;
    }
    header {
      background: #020617;
      padding: 15px;
      text-align: center;
      font-size: 20px;
      font-weight: bold;
    }
    .container {
      max-width: 1000px;
      margin: auto;
      padding: 20px;
    }
    input, button, select {
      padding: 10px;
      margin: 5px 0;
      width: 100%;
      border-radius: 6px;
      border: none;
    }
    button {
      background: #22c55e;
      font-weight: bold;
      cursor: pointer;
    }
    button:hover {
      background: #16a34a;
    }
    .card {
      background: #020617;
      padding: 15px;
      border-radius: 10px;
      margin-bottom: 20px;
    }
    .row {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 15px;
    }
    .hidden {
      display: none;
    }
    table {
      width: 100%;
      border-collapse: collapse;
    }
    th, td {
      padding: 10px;
      border-bottom: 1px solid #334155;
      text-align: left;
    }
  </style>
</head>

<body>
<header>📈 Paper Trading Dashboard</header>

<div class="container">

  <!-- LOGIN -->
  <div id="loginBox" class="card">
    <h3>Login</h3>
    <input id="username" placeholder="Username" />
    <button onclick="login()">Login</button>
  </div>

  <!-- DASHBOARD -->
  <div id="dashboard" class="hidden">

    <div class="row">

      <!-- ACCOUNT -->
      <div class="card">
        <h3>Account</h3>
        <p>Cash: <span id="cash">$0</span></p>
        <p>Equity: <span id="equity">$0</span></p>
        <button onclick="loadAccount()">Refresh</button>
      </div>

      <!-- TRADE -->
      <div class="card">
        <h3>Place Trade</h3>
        <input id="symbol" placeholder="Symbol (AAPL)" />
        <input id="qty" type="number" placeholder="Quantity" />
        <select id="side">
          <option value="buy">Buy</option>
          <option value="sell">Sell</option>
        </select>
        <button onclick="placeTrade()">Execute</button>
      </div>

    </div>

    <!-- POSITIONS -->
    <div class="card">
      <h3>Open Positions</h3>
      <table>
        <thead>
          <tr><th>Symbol</th><th>Qty</th><th>Avg Price</th></tr>
        </thead>
        <tbody id="positions"></tbody>
      </table>
    </div>

    <!-- AUTOMATION -->
    <div class="card">
      <h3>Strategy Automation</h3>
      <p>This executes a backend strategy (example: buy AAPL).</p>
      <button onclick="runBot()">Run Bot</button>
    </div>

  </div>
</div>

<script>
const API = "http://localhost:3000"; // backend URL

function login() {
  const user = document.getElementById("username").value;
  if (!user) return alert("Enter username");

  localStorage.setItem("user", user);
  document.getElementById("loginBox").classList.add("hidden");
  document.getElementById("dashboard").classList.remove("hidden");
  loadAccount();
  loadPositions();
}

async function loadAccount() {
  const res = await fetch(`${API}/account`);
  const data = await res.json();
  document.getElementById("cash").innerText = `$${Number(data.cash).toFixed(2)}`;
  document.getElementById("equity").innerText = `$${Number(data.equity).toFixed(2)}`;
}

async function placeTrade() {
  const symbol = document.getElementById("symbol").value;
  const qty = document.getElementById("qty").value;
  const side = document.getElementById("side").value;

  const res = await fetch(`${API}/trade`, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ symbol, qty, side })
  });

  const data = await res.json();
  alert("Trade submitted");
  loadPositions();
}

async function loadPositions() {
  const res = await fetch(`${API}/positions`);
  const data = await res.json();
  const tbody = document.getElementById("positions");
  tbody.innerHTML = "";

  data.forEach(p => {
    tbody.innerHTML += `
      <tr>
        <td>${p.symbol}</td>
        <td>${p.qty}</td>
        <td>$${Number(p.avg_entry_price).toFixed(2)}</td>
      </tr>`;
  });
}

async function runBot() {
  await fetch(`${API}/bot`, { method: "POST" });
  alert("Strategy executed");
  loadPositions();
}
</script>
</body>
</html>
