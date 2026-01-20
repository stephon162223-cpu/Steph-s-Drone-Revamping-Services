require("dotenv").config();
const express = require("express");
const cors = require("cors");
const Alpaca = require("alpaca-trade-api");

const app = express();
app.use(cors());
app.use(express.json());

const alpaca = new Alpaca({
  keyId: process.env.ALPACA_KEY,
  secretKey: process.env.ALPACA_SECRET,
  paper: true
});

/* =========================
   ACCOUNT INFO
========================= */
app.get("/account", async (req, res) => {
  try {
    const account = await alpaca.getAccount();
    res.json({
      cash: account.cash,
      equity: account.equity
    });
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
});

/* =========================
   POSITIONS
========================= */
app.get("/positions", async (req, res) => {
  try {
    const positions = await alpaca.getPositions();
    res.json(positions);
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
});

/* =========================
   PLACE TRADE
========================= */
app.post("/trade", async (req, res) => {
  const { symbol, qty, side } = req.body;

  if (!symbol || !qty || !side) {
    return res.status(400).json({ error: "Missing fields" });
  }

  try {
    const order = await alpaca.createOrder({
      symbol: symbol.toUpperCase(),
      qty: Number(qty),
      side,
      type: "market",
      time_in_force: "gtc"
    });

    res.json(order);
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
});

/* =========================
   SIMPLE BOT (AUTOMATION)
========================= */
app.post("/bot", async (req, res) => {
  try {
    // Example strategy: Buy 1 share of AAPL
    const order = await alpaca.createOrder({
      symbol: "AAPL",
      qty: 1,
      side: "buy",
      type: "market",
      time_in_force: "gtc"
    });

    res.json({
      message: "Bot executed",
      order
    });
  } catch (err) {
    res.status(500).json({ error: err.message });
  }
});

/* =========================
   SERVER START
========================= */
const PORT = 3000;
app.listen(PORT, () => {
  console.log(`✅ Backend running on http://localhost:${PORT}`);
});
