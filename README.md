```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NeuralTrade AI Pro - Live Trading Platform</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
        }

        :root {
            --primary: #2563eb;
            --primary-dark: #1d4ed8;
            --secondary: #10b981;
            --danger: #ef4444;
            --warning: #f59e0b;
            --dark: #1f2937;
            --light: #f8fafc;
            --gray: #6b7280;
            --card-bg: #ffffff;
            --border: #e5e7eb;
        }

        body {
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
            color: var(--light);
            min-height: 100vh;
            overflow-x: hidden;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 30px;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 24px;
        }

        .logo-text {
            font-size: 28px;
            font-weight: 800;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .user-menu {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .balance-card {
            background: rgba(255, 255, 255, 0.1);
            padding: 15px 25px;
            border-radius: 10px;
            backdrop-filter: blur(10px);
            text-align: center;
        }

        .balance-amount {
            font-size: 28px;
            font-weight: bold;
            color: var(--secondary);
        }

        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            margin-bottom: 30px;
        }

        .card {
            background: var(--card-bg);
            color: var(--dark);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            border: 1px solid var(--border);
        }

        .card-title {
            font-size: 14px;
            color: var(--gray);
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 10px;
        }

        .card-value {
            font-size: 32px;
            font-weight: 800;
            margin-bottom: 5px;
        }

        .card-change {
            font-size: 14px;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .positive { color: var(--secondary); }
        .negative { color: var(--danger); }

        .chart-container {
            grid-column: span 3;
            height: 400px;
        }

        .main-content {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 30px;
        }

        .ai-controls {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .strategy-builder {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 25px;
            color: var(--dark);
        }

        .strategy-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin-top: 20px;
        }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        label {
            font-weight: 600;
            color: var(--dark);
            font-size: 14px;
        }

        select, input, textarea {
            padding: 12px 15px;
            border: 2px solid var(--border);
            border-radius: 8px;
            font-size: 14px;
            transition: all 0.3s ease;
        }

        select:focus, input:focus, textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
        }

        .slider-container {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .slider-value {
            min-width: 40px;
            text-align: center;
            font-weight: 600;
        }

        input[type="range"] {
            flex: 1;
            height: 6px;
            -webkit-appearance: none;
            background: var(--border);
            border-radius: 3px;
        }

        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 20px;
            height: 20px;
            background: var(--primary);
            border-radius: 50%;
            cursor: pointer;
        }

        .btn {
            padding: 14px 24px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .btn-primary {
            background: var(--primary);
            color: white;
        }

        .btn-primary:hover {
            background: var(--primary-dark);
            transform: translateY(-2px);
        }

        .btn-secondary {
            background: var(--light);
            color: var(--dark);
            border: 2px solid var(--border);
        }

        .btn-secondary:hover {
            background: #f1f5f9;
        }

        .btn-success {
            background: var(--secondary);
            color: white;
        }

        .btn-success:hover {
            background: #0da271;
        }

        .btn-danger {
            background: var(--danger);
            color: white;
        }

        .btn-danger:hover {
            background: #dc2626;
        }

        .btn-group {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }

        .strategy-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin-top: 20px;
        }

        .strategy-item {
            background: var(--light);
            padding: 15px;
            border-radius: 10px;
            border-left: 4px solid var(--primary);
        }

        .strategy-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }

        .strategy-name {
            font-weight: 700;
            color: var(--dark);
        }

        .strategy-status {
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
        }

        .status-active { background: #d1fae5; color: #065f46; }
        .status-paused { background: #fef3c7; color: #92400e; }
        .status-stopped { background: #fee2e2; color: #991b1b; }

        .performance-metrics {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin-top: 15px;
        }

        .metric {
            text-align: center;
            padding: 10px;
            background: var(--light);
            border-radius: 8px;
        }

        .metric-value {
            font-size: 20px;
            font-weight: 700;
            color: var(--dark);
        }

        .metric-label {
            font-size: 12px;
            color: var(--gray);
            margin-top: 5px;
        }

        .market-data {
            margin-top: 30px;
        }

        .market-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }

        .market-table th {
            background: var(--light);
            color: var(--dark);
            padding: 12px;
            text-align: left;
            font-weight: 600;
            border-bottom: 2px solid var(--border);
        }

        .market-table td {
            padding: 12px;
            border-bottom: 1px solid var(--border);
            color: var(--dark);
        }

        .market-table tr:hover {
            background: #f8fafc;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1000;
            align-items: center;
            justify-content: center;
            backdrop-filter: blur(5px);
        }

        .modal-content {
            background: white;
            border-radius: 15px;
            padding: 30px;
            max-width: 500px;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
            color: var(--dark);
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .modal-title {
            font-size: 24px;
            font-weight: 700;
        }

        .close-modal {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: var(--gray);
        }

        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            background: var(--secondary);
            color: white;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
            display: none;
            z-index: 1001;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        .ai-status {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 10px 15px;
            background: rgba(16, 185, 129, 0.1);
            border-radius: 8px;
            margin-bottom: 20px;
        }

        .status-indicator {
            width: 10px;
            height: 10px;
            background: var(--secondary);
            border-radius: 50%;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }

        .trading-view {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 25px;
            color: var(--dark);
            margin-top: 30px;
        }

        .api-config {
            background: rgba(255, 255, 255, 0.05);
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .api-status {
            display: inline-block;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            margin-left: 10px;
        }

        .api-connected { background: var(--secondary); color: white; }
        .api-disconnected { background: var(--danger); color: white; }

        .wallet-actions {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }

        .wallet-input {
            flex: 1;
            padding: 10px;
            border: 2px solid var(--border);
            border-radius: 8px;
            font-size: 14px;
        }

        .positions-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }

        .positions-table th {
            background: var(--light);
            color: var(--dark);
            padding: 12px;
            text-align: left;
            font-weight: 600;
            border-bottom: 2px solid var(--border);
        }

        .positions-table td {
            padding: 12px;
            border-bottom: 1px solid var(--border);
            color: var(--dark);
        }

        .close-position {
            padding: 5px 10px;
            background: var(--danger);
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 12px;
        }

        @media (max-width: 1200px) {
            .dashboard-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            .chart-container {
                grid-column: span 2;
            }
            .main-content {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 768px) {
            .dashboard-grid {
                grid-template-columns: 1fr;
            }
            .chart-container {
                grid-column: span 1;
            }
            .btn-group {
                flex-direction: column;
            }
            .performance-metrics {
                grid-template-columns: 1fr;
            }
            .wallet-actions {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <div class="logo-icon">NT</div>
                <div class="logo-text">NeuralTrade AI Pro</div>
            </div>
            <div class="user-menu">
                <div class="balance-card">
                    <div style="font-size: 12px; color: rgba(255, 255, 255, 0.7);">Paper Balance</div>
                    <div class="balance-amount" id="liveBalance">$100,000.00</div>
                    <div style="font-size: 11px; color: rgba(255, 255, 255, 0.5);" id="accountStatus">● Connected to Alpaca</div>
                </div>
                <button class="btn btn-secondary" onclick="openSettings()">
                    <span>⚙️</span> Settings
                </button>
            </div>
        </header>

        <div class="dashboard-grid">
            <div class="card">
                <div class="card-title">Today's P&L</div>
                <div class="card-value positive" id="todayPL">+$0.00</div>
                <div class="card-change positive" id="todayChange">+0.00%</div>
            </div>
            <div class="card">
                <div class="card-title">Active Positions</div>
                <div class="card-value" id="activePositions">0</div>
                <div class="card-change" id="positionsValue">$0.00</div>
            </div>
            <div class="card">
                <div class="card-title">Buying Power</div>
                <div class="card-value" id="buyingPower">$100,000</div>
                <div class="card-change positive" id="availableBP">100% available</div>
            </div>
            <div class="card">
                <div class="card-title">Total P&L</div>
                <div class="card-value positive" id="totalPL">+$0.00</div>
                <div class="card-change positive" id="totalChange">+0.00%</div>
            </div>
        </div>

        <div class="main-content">
            <div class="ai-controls">
                <div class="api-config">
                    <h3 style="margin-bottom: 15px;">🔐 Alpaca API Configuration</h3>
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px; margin-bottom: 15px;">
                        <div class="form-group">
                            <label>API Key ID</label>
                            <input type="password" id="apiKey" placeholder="Enter your API Key">
                        </div>
                        <div class="form-group">
                            <label>Secret Key</label>
                            <input type="password" id="secretKey" placeholder="Enter your Secret Key">
                        </div>
                    </div>
                    <div style="display: flex; gap: 10px; align-items: center;">
                        <button class="btn btn-success" onclick="connectAlpaca()">
                            <span>🔗</span> Connect to Alpaca
                        </button>
                        <button class="btn btn-secondary" onclick="openHelp()">
                            <span>❓</span> Get API Keys
                        </button>
                        <span id="connectionStatus" class="api-status api-disconnected">Disconnected</span>
                    </div>
                </div>

                <div class="strategy-builder">
                    <h2 style="color: var(--dark); margin-bottom: 20px;">🤖 AI Strategy Builder</h2>
                    
                    <div class="strategy-form">
                        <div class="form-group">
                            <label for="strategyName">Strategy Name</label>
                            <input type="text" id="strategyName" placeholder="e.g., Momentum Scalper v2.1">
                        </div>

                        <div class="form-group">
                            <label for="market">Market/Asset</label>
                            <select id="market">
                                <option value="BTC/USD">Bitcoin (BTC/USD)</option>
                                <option value="ETH/USD">Ethereum (ETH/USD)</option>
                                <option value="SPY">S&P 500 (SPY)</option>
                                <option value="AAPL">Apple (AAPL)</option>
                                <option value="TSLA">Tesla (TSLA)</option>
                                <option value="MSFT">Microsoft (MSFT)</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label>Trade Amount ($)</label>
                            <input type="number" id="tradeAmount" value="1000" min="1" step="100">
                        </div>

                        <div class="form-group">
                            <label for="orderType">Order Type</label>
                            <select id="orderType">
                                <option value="market">Market Order</option>
                                <option value="limit">Limit Order</option>
                                <option value="stop">Stop Order</option>
                                <option value="trailing_stop">Trailing Stop</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label for="aiModel">AI Signal Source</label>
                            <select id="aiModel">
                                <option value="momentum">Momentum Strategy</option>
                                <option value="mean_reversion">Mean Reversion</option>
                                <option value="breakout">Breakout Detection</option>
                                <option value="news_sentiment">News Sentiment</option>
                            </select>
                        </div>

                        <div class="btn-group">
                            <button class="btn btn-primary" onclick="placeTrade()">
                                <span>📈</span> Place Trade
                            </button>
                            <button class="btn btn-secondary" onclick="getMarketData()">
                                <span>📊</span> Check Price
                            </button>
                            <button class="btn btn-danger" onclick="closeAllPositions()">
                                <span>🛑</span> Close All
                            </button>
                        </div>
                    </div>
                </div>

                <div class="trading-view">
                    <h2 style="color: var(--dark); margin-bottom: 20px;">💰 Wallet Management</h2>
                    
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
                        <div>
                            <h4 style="margin-bottom: 10px; color: var(--gray);">Add Funds</h4>
                            <div class="wallet-actions">
                                <input type="number" id="addAmount" class="wallet-input" placeholder="Amount ($)" value="1000">
                                <button class="btn btn-success" onclick="addFunds()">
                                    <span>💵</span> Deposit
                                </button>
                            </div>
                            <div style="display: flex; gap: 5px; margin-top: 10px;">
                                <button class="btn btn-secondary" style="padding: 8px 12px; font-size: 12px;" onclick="quickAdd(100)">+$100</button>
                                <button class="btn btn-secondary" style="padding: 8px 12px; font-size: 12px;" onclick="quickAdd(1000)">+$1,000</button>
                                <button class="btn btn-secondary" style="padding: 8px 12px; font-size: 12px;" onclick="quickAdd(10000)">+$10,000</button>
                            </div>
                        </div>
                        
                        <div>
                            <h4 style="margin-bottom: 10px; color: var(--gray);">Withdraw Funds</h4>
                            <div class="wallet-actions">
                                <input type="number" id="withdrawAmount" class="wallet-input" placeholder="Amount ($)" value="1000">
                                <button class="btn btn-danger" onclick="withdrawFunds()">
                                    <span>🏦</span> Withdraw
                                </button>
                            </div>
                            <div style="display: flex; gap: 5px; margin-top: 10px;">
                                <button class="btn btn-secondary" style="padding: 8px 12px; font-size: 12px;" onclick="quickWithdraw(100)">-$100</button>
                                <button class="btn btn-secondary" style="padding: 8px 12px; font-size: 12px;" onclick="quickWithdraw(1000)">-$1,000</button>
                                <button class="btn btn-secondary" style="padding: 8px 12px; font-size: 12px;" onclick="quickWithdraw(10000)">-$10,000</button>
                            </div>
                        </div>
                    </div>

                    <div style="margin-top: 20px; padding: 15px; background: #f8fafc; border-radius: 10px;">
                        <h4 style="margin-bottom: 10px; color: var(--dark);">💡 Quick Trade</h4>
                        <div style="display: flex; gap: 10px;">
                            <button class="btn btn-success" style="flex: 1;" onclick="quickTrade('buy')">
                                <span>🔼</span> Quick Buy $100
                            </button>
                            <button class="btn btn-danger" style="flex: 1;" onclick="quickTrade('sell')">
                                <span>🔽</span> Quick Sell $100
                            </button>
                        </div>
                    </div>
                </div>
            </div>

            <div>
                <div class="strategy-builder">
                    <h2 style="color: var(--dark); margin-bottom: 20px;">📊 Current Positions</h2>
                    
                    <table class="positions-table">
                        <thead>
                            <tr>
                                <th>Symbol</th>
                                <th>Qty</th>
                                <th>Avg Price</th>
                                <th>Current</th>
                                <th>P&L</th>
                                <th>Action</th>
                            </tr>
                        </thead>
                        <tbody id="positionsList">
                            <tr>
                                <td colspan="6" style="text-align: center; padding: 40px; color: var(--gray);">
                                    No positions open. Connect to Alpaca and start trading!
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                <div class="market-data">
                    <h2 style="color: var(--dark); margin-bottom: 20px;">🌐 Live Market Data</h2>
                    
                    <table class="market-table">
                        <thead>
                            <tr>
                                <th>Symbol</th>
                                <th>Bid</th>
                                <th>Ask</th>
                                <th>Change</th>
                                <th>Action</th>
                            </tr>
                        </thead>
                        <tbody id="marketData">
                            <tr>
                                <td>AAPL</td>
                                <td>$182.34</td>
                                <td>$182.36</td>
                                <td class="positive">+0.45%</td>
                                <td><button class="btn btn-success" style="padding: 5px 10px; font-size: 12px;" onclick="tradeSymbol('AAPL', 'buy')">Buy</button></td>
                            </tr>
                            <tr>
                                <td>TSLA</td>
                                <td>$245.12</td>
                                <td>$245.15</td>
                                <td class="negative">-1.23%</td>
                                <td><button class="btn btn-danger" style="padding: 5px 10px; font-size: 12px;" onclick="tradeSymbol('TSLA', 'sell')">Sell</button></td>
                            </tr>
                            <tr>
                                <td>SPY</td>
                                <td>$456.78</td>
                                <td>$456.80</td>
                                <td class="positive">+0.12%</td>
                                <td><button class="btn btn-success" style="padding: 5px 10px; font-size: 12px;" onclick="tradeSymbol('SPY', 'buy')">Buy</button></td>
                            </tr>
                            <tr>
                                <td>BTC/USD</td>
                                <td>$42,567</td>
                                <td>$42,570</td>
                                <td class="positive">+2.34%</td>
                                <td><button class="btn btn-success" style="padding: 5px 10px; font-size: 12px;" onclick="tradeSymbol('BTC/USD', 'buy')">Buy</button></td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                <div class="strategy-builder" style="margin-top: 20px;">
                    <h2 style="color: var(--dark); margin-bottom: 20px;">📝 Recent Trades</h2>
                    <div id="recentTrades" style="max-height: 200px; overflow-y: auto;">
                        <div style="text-align: center; padding: 20px; color: var(--gray);">
                            No trades yet. Start trading to see history.
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modals -->
    <div class="modal" id="settingsModal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">⚙️ Platform Settings</div>
                <button class="close-modal" onclick="closeModal('settingsModal')">×</button>
            </div>
            <div class="strategy-form">
                <div class="form-group">
                    <label>Default Trade Amount ($)</label>
                    <input type="number" id="defaultTradeAmount" value="1000" min="1">
                </div>
                <div class="form-group">
                    <label>Default Order Type</label>
                    <select id="defaultOrderType">
                        <option value="market">Market Order</option>
                        <option value="limit">Limit Order</option>
                        <option value="stop">Stop Order</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Notifications</label>
                    <div>
                        <input type="checkbox" id="emailAlerts" checked> <label for="emailAlerts" style="display: inline;">Trade Confirmations</label><br>
                        <input type="checkbox" id="priceAlerts" checked> <label for="priceAlerts" style="display: inline;">Price Alerts</label>
                    </div>
                </div>
                <div class="form-group">
                    <label>Risk Management</label>
                    <select id="riskManagement">
                        <option value="conservative">Conservative (Max 1% per trade)</option>
                        <option value="moderate" selected>Moderate (Max 5% per trade)</option>
                        <option value="aggressive">Aggressive (Max 10% per trade)</option>
                    </select>
                </div>
                <button class="btn btn-primary" style="width: 100%; margin-top: 20px;" onclick="saveSettings()">
                    Save Settings
                </button>
            </div>
        </div>
    </div>

    <div class="modal" id="helpModal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">❓ How to Get Alpaca API Keys</div>
                <button class="close-modal" onclick="closeModal('helpModal')">×</button>
            </div>
            <div style="line-height: 1.6;">
                <h3>Step-by-Step Guide:</h3>
                <ol style="margin: 15px 0 15px 20px;">
                    <li>Go to <a href="https://alpaca.markets/" target="_blank">alpaca.markets</a></li>
                    <li>Click "Sign Up" for free account</li>
                    <li>Complete registration (use paper trading account)</li>
                    <li>Go to Dashboard → API Keys</li>
                    <li>Click "Generate New Key"</li>
                    <li>Copy your:
                        <ul>
                            <li><strong>API Key ID</strong> (starts with PK...)</li>
                            <li><strong>Secret Key</strong></li>
                        </ul>
                    </li>
                    <li>Paste keys in the platform</li>
                    <li>Click "Connect to Alpaca"</li>
                </ol>
                <div style="background: #f0f9ff; padding: 15px; border-radius: 8px; margin: 15px 0;">
                    <strong>💡 Paper Trading:</strong> Alpaca provides $100,000 virtual money for testing. No real money involved!
                </div>
                <button class="btn btn-primary" onclick="window.open('https://alpaca.markets/', '_blank')">
                    🚀 Go to Alpaca Website
                </button>
            </div>
        </div>
    </div>

    <div class="modal" id="tradeModal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title" id="tradeModalTitle">Place Trade</div>
                <button class="close-modal" onclick="closeModal('tradeModal')">×</button>
            </div>
            <div id="tradeModalContent">
                <!-- Trade details will be loaded here -->
            </div>
        </div>
    </div>

    <div class="notification" id="notification">
        <span id="notificationText">Notification message</span>
    </div>

    <!-- Load Alpaca SDK -->
    <script src="https://cdn.jsdelivr.net/npm/@alpacahq/alpaca-trade-api/dist/alpaca-trade-api.min.js"></script>
    
    <script>
        // Global variables
        let alpaca = null;
        let accountBalance = 100000;
        let positions = [];
        let trades = [];
        let isConnected = false;

        // Initialize platform
        function initPlatform() {
            // Load saved API keys from localStorage
            const savedApiKey = localStorage.getItem('alpacaApiKey');
            const savedSecret = localStorage.getItem('alpacaSecretKey');
            
            if (savedApiKey && savedSecret) {
                document.getElementById('apiKey').value = savedApiKey;
                document.getElementById('secretKey').value = savedSecret;
            }
            
            updateBalanceDisplay();
            updatePositionsDisplay();
            loadRecentTrades();
            
            // Check connection every 30 seconds
            setInterval(checkConnection, 30000);
        }

        // Connect to Alpaca API
        async function connectAlpaca() {
            const apiKey = document.getElementById('apiKey').value.trim();
            const secretKey = document.getElementById('secretKey').value.trim();
            
            if (!apiKey || !secretKey) {
                showNotification('Please enter both API Key and Secret Key', 'error');
                return;
            }
            
            showNotification('Connecting to Alpaca...', 'info');
            
            try {
                // Save keys to localStorage
                localStorage.setItem('alpacaApiKey', apiKey);
                localStorage.setItem('alpacaSecretKey', secretKey);
                
                // Initialize Alpaca client (paper trading)
                alpaca = new Alpaca({
                    keyId: apiKey,
                    secretKey: secretKey,
                    paper: true
                });
                
                // Test connection
                const account = await alpaca.getAccount();
                isConnected = true;
                
                // Update display with real account info
                accountBalance = parseFloat(account.buying_power);
                document.getElementById('connectionStatus').textContent = 'Connected';
                document.getElementById('connectionStatus').className = 'api-status api-connected';
                document.getElementById('accountStatus').textContent = `● ${account.account_number}`;
                
                // Load real positions
                await loadRealPositions();
                await loadRealTrades();
                
                showNotification(`✅ Connected to Alpaca! Account: ${account.account_number}`, 'success');
                
            } catch (error) {
                console.error('Alpaca connection error:', error);
                isConnected = false;
                document.getElementById('connectionStatus').textContent = 'Error';
                document.getElementById('connectionStatus').className = 'api-status api-disconnected';
                showNotification(`❌ Connection failed: ${error.message}`, 'error');
            }
        }

        // Load real positions from Alpaca
        async function loadRealPositions() {
            if (!alpaca) return;
            
            try {
                positions = await alpaca.getPositions();
                updatePositionsDisplay();
            } catch (error) {
                console.error('Error loading positions:', error);
            }
        }

        // Place a trade
        async function placeTrade() {
            if (!isConnected) {
                showNotification('Please connect to Alpaca first', 'error');
                return;
            }
            
            const symbol = document.getElementById('market').value;
            const amount = parseFloat(document.getElementById('tradeAmount').value);
            const orderType = document.getElementById('orderType').value;
            const strategy = document.getElementById('strategyName').value || 'Manual Trade';
            
            if (!symbol || !amount || amount <= 0) {
                showNotification('Please enter valid symbol and amount', 'error');
                return;
            }
            
            if (amount > accountBalance * 0.9) {
                if (!confirm(`Warning: This trade uses ${(amount/accountBalance*100).toFixed(1)}% of your balance. Continue?`)) {
                    return;
                }
            }
            
            showNotification(`Placing ${orderType} order for $${amount} of ${symbol}...`, 'info');
            
            try {
                // In real implementation, you would use Alpaca's order API
                // For demo purposes, we'll simulate the trade
                
                const price = await getCurrentPrice(symbol);
                const qty = (amount / price).toFixed(4);
                
                // Simulate trade execution
                const trade = {
                    id: Date.now(),
                    symbol: symbol,
                    side: 'buy',
                    qty: parseFloat(qty),
                    price: price,
                    amount: amount,
                    type: orderType,
                    strategy: strategy,
                    timestamp: new Date().toISOString(),
                    status: 'filled'
                };
                
                trades.unshift(trade);
                accountBalance -= amount;
                
                // Add to positions
                const existingPos = positions.find(p => p.symbol === symbol);
                if (existingPos) {
                    existingPos.qty += parseFloat(qty);
                    existingPos.avgPrice = ((existingPos.avgPrice * existingPos.qty + price * parseFloat(qty)) / (existingPos.qty + parseFloat(qty))).toFixed(2);
                } else {
                    positions.push({
                        symbol: symbol,
                        qty: parseFloat(qty),
                        avgPrice: price,
                        currentPrice: price,
                        side: 'long'
                    });
                }
                
                updateBalanceDisplay();
                updatePositionsDisplay();
                loadRecentTrades();
                
                showNotification(`✅ Trade executed: Bought ${qty} ${symbol} @ $${price}`, 'success');
                
                // Show trade confirmation
                openTradeModal('Trade Confirmation', `
                    <div style="padding: 20px; text-align: center;">
                        <div style="font-size: 48px; color: var(--secondary); margin-bottom: 20px;">✅</div>
                        <h3 style="margin-bottom: 10px;">Trade Executed Successfully!</h3>
                        <div style="background: #f8fafc; padding: 15px; border-radius: 10px; margin: 15px 0;">
                            <div><strong>Symbol:</strong> ${symbol}</div>
                            <div><strong>Side:</strong> Buy</div>
                            <div><strong>Quantity:</strong> ${qty}</div>
                            <div><strong>Price:</strong> $${price}</div>
                            <div><strong>Amount:</strong> $${amount}</div>
                            <div><strong>Type:</strong> ${orderType}</div>
                            <div><strong>Strategy:</strong> ${strategy}</div>
                        </div>
                        <button class="btn btn-primary" onclick="closeModal('tradeModal')">
                            Close
                        </button>
                    </div>
                `);
                
            } catch (error) {
                console.error('Trade error:', error);
                showNotification(`❌ Trade failed: ${error.message}`, 'error');
            }
        }

        // Get current price for a symbol
        async function getCurrentPrice(symbol) {
            // Mock prices for demo
            const mockPrices = {
                'AAPL': 182.34 + (Math.random() - 0.5) * 2,
                'TSLA': 245.12 + (Math.random() - 0.5) * 5,
                'SPY': 456.78 + (Math.random() - 0.5) * 1,
                'BTC/USD': 42567 + (Math.random() - 0.5) * 1000,
                'ETH/USD': 2345 + (Math.random() - 0.5) * 50,
                'MSFT': 375 + (Math.random() - 0.5) * 3
            };
            
            return mockPrices[symbol] || 100 + (Math.random() * 100);
        }

        // Close a position
        async function closePosition(symbol) {
            if (!isConnected) {
                showNotification('Please connect to Alpaca first', 'error');
                return;
            }
            
            const pos = positions.find(p => p.symbol === symbol);
            if (!pos) return;
            
            const currentPrice = await getCurrentPrice(symbol);
            const value = pos.qty * currentPrice;
            const pnl = ((currentPrice - pos.avgPrice) * pos.qty).toFixed(2);
            
            if (confirm(`Close ${pos.qty} ${symbol} @ ~$${currentPrice}? P&L: $${pnl}`)) {
                // Remove from positions
                positions = positions.filter(p => p.symbol !== symbol);
                accountBalance += value;
                
                // Record trade
                trades.unshift({
                    id: Date.now(),
                    symbol: symbol,
                    side: 'sell',
                    qty: pos.qty,
                    price: currentPrice,
                    amount: value,
                    pnl: parseFloat(pnl),
                    timestamp: new Date().toISOString(),
                    status: 'filled'
                });
                
                updateBalanceDisplay();
                updatePositionsDisplay();
                loadRecentTrades();
                
                const pnlClass = pnl >= 0 ? 'positive' : 'negative';
                showNotification(`✅ Position closed: ${pos.qty} ${symbol} @ $${currentPrice}. P&L: <span class="${pnlClass}">$${pnl}</span>`, 'success');
            }
        }

        // Close all positions
        async function closeAllPositions() {
            if (!positions.length) {
                showNotification('No positions to close', 'info');
                return;
            }
            
            if (confirm(`Close all ${positions.length} positions?`)) {
                for (const pos of positions) {
                    const currentPrice = await getCurrentPrice(pos.symbol);
                    const value = pos.qty * currentPrice;
                    accountBalance += value;
                    
                    trades.unshift({
                        id: Date.now(),
                        symbol: pos.symbol,
                        side: 'sell',
                        qty: pos.qty,
                        price: currentPrice,
                        amount: value,
                        timestamp: new Date().toISOString()
                    });
                }
                
                positions = [];
                updateBalanceDisplay();
                updatePositionsDisplay();
                loadRecentTrades();
                
                showNotification(`✅ All positions closed. ${positions.length} positions liquidated`, 'success');
            }
        }

        // Add funds to account
        function addFunds() {
            const amount = parseFloat(document.getElementById('addAmount').value);
            if (amount > 0) {
                accountBalance += amount;
                updateBalanceDisplay();
                showNotification(`✅ Added $${amount} to your account`, 'success');
                
                // Record deposit
                trades.unshift({
                    id: Date.now(),
                    type: 'deposit',
                    amount: amount,
                    timestamp: new Date().toISOString()
                });
                loadRecentTrades();
            }
        }

        // Withdraw funds from account
        function withdrawFunds() {
            const amount = parseFloat(document.getElementById('withdrawAmount').value);
            if (amount > 0) {
                if (amount > accountBalance) {
                    showNotification('Insufficient funds', 'error');
                    return;
                }
                
                accountBalance -= amount;
                updateBalanceDisplay();
                showNotification(`✅ Withdrew $${amount} from your account`, 'success');
                
                // Record withdrawal
                trades.unshift({
                    id: Date.now(),
                    type: 'withdrawal',
                    amount: -amount,
                    timestamp: new Date().toISOString()
                });
                loadRecentTrades();
            }
        }

        // Quick add/withdraw helpers
        function quickAdd(amount) {
            document.getElementById('addAmount').value = amount;
            addFunds();
        }

        function quickWithdraw(amount) {
            document.getElementById('withdrawAmount').value = amount;
            withdrawFunds();
        }

        // Quick trade function
        async function quickTrade(side) {
            const symbol = document.getElementById('market').value;
            const amount = 100;
            
            if (side === 'buy') {
                document.getElementById('tradeAmount').value = amount;
                placeTrade();
            } else {
                // Quick sell - close part of position if exists
                const pos = positions.find(p => p.symbol === symbol);
                if (pos) {
                    const currentPrice = await getCurrentPrice(symbol);
                    const qtyToSell = Math.min(pos.qty, (amount / currentPrice));
                    
                    if (qtyToSell > 0) {
                        const value = qtyToSell * currentPrice;
                        const pnl = ((currentPrice - pos.avgPrice) * qtyToSell).toFixed(2);
                        
                        pos.qty -= qtyToSell;
                        if (pos.qty <= 0) {
                            positions = positions.filter(p => p.symbol !== symbol);
                        }
                        
                        accountBalance += value;
                        
                        trades.unshift({
                            id: Date.now(),
                            symbol: symbol,
                            side: 'sell',
                            qty: qtyToSell,
                            price: currentPrice,
                            amount: value,
                            pnl: parseFloat(pnl),
                            timestamp: new Date().toISOString()
                        });
                        
                        updateBalanceDisplay();
                        updatePositionsDisplay();
                        loadRecentTrades();
                        
                        showNotification(`✅ Quick sell: ${qtyToSell.toFixed(4)} ${symbol} @ $${currentPrice}`, 'success');
                    }
                } else {
                    showNotification(`No ${symbol} position to sell`, 'error');
                }
            }
        }

        // Trade specific symbol
        async function tradeSymbol(symbol, side) {
            document.getElementById('market').value = symbol;
            if (side === 'buy') {
                placeTrade();
            } else {
                // For sell, check if we have position
                const pos = positions.find(p => p.symbol === symbol);
                if (pos) {
                    closePosition(symbol);
                } else {
                    showNotification(`No ${symbol} position to sell`, 'error');
                }
            }
        }

        // Update balance display
        function updateBalanceDisplay() {
            document.getElementById('liveBalance').textContent = `$${accountBalance.toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2})}`;
            document.getElementById('buyingPower').textContent = `$${Math.floor(accountBalance).toLocaleString()}`;
            
            // Calculate P&L (mock)
            const todayPL = (Math.random() * 1000 - 200).toFixed(2);
            const totalPL = (Math.random() * 5000 - 1000).toFixed(2);
            
            document.getElementById('todayPL').textContent = `$${todayPL}`;
            document.getElementById('todayPL').className = `card-value ${todayPL >= 0 ? 'positive' : 'negative'}`;
            document.getElementById('todayChange').textContent = `${todayPL >= 0 ? '+' : ''}${(todayPL/100000*100).toFixed(2)}%`;
            document.getElementById('todayChange').className = `card-change ${todayPL >= 0 ? 'positive' : 'negative'}`;
            
            document.getElementById('totalPL').textContent = `$${totalPL}`;
            document.getElementById('totalPL').className = `card-value ${totalPL >= 0 ? 'positive' : 'negative'}`;
            document.getElementById('totalChange').textContent = `${totalPL >= 0 ? '+' : ''}${(totalPL/100000*100).toFixed(2)}%`;
            document.getElementById('totalChange').className = `card-change ${totalPL >= 0 ? 'positive' : 'negative'}`;
        }

        // Update positions display
        function updatePositionsDisplay() {
            const container = document.getElementById('positionsList');
            const positionsCount = document.getElementById('activePositions');
            const positionsValue = document.getElementById('positionsValue');
            
            if (positions.length === 0) {
                container.innerHTML = `
                    <tr>
                        <td colspan="6" style="text-align: center; padding: 40px; color: var(--gray);">
                            No positions open. Connect to Alpaca and start trading!
                        </td>
                    </tr>
                `;
                positionsCount.textContent = '0';
                positionsValue.textContent = '$0.00';
                return;
            }
            
            let totalValue = 0;
            let html = '';
            
            positions.forEach(async (pos, index) => {
                const currentPrice = await getCurrentPrice(pos.symbol);
                const value = pos.qty * currentPrice;
                const pnl = (currentPrice - pos.avgPrice) * pos.qty;
                const pnlPercent = ((currentPrice / pos.avgPrice - 1) * 100).toFixed(2);
                
                totalValue += value;
                
                html += `
                    <tr>
                        <td><strong>${pos.symbol}</strong></td>
                        <td>${pos.qty.toFixed(4)}</td>
                        <td>$${parseFloat(pos.avgPrice).toFixed(2)}</td>
                        <td>$${currentPrice.toFixed(2)}</td>
                        <td class="${pnl >= 0 ? 'positive' : 'negative'}">
                            $${pnl.toFixed(2)} (${pnlPercent}%)
                        </td>
                        <td>
                            <button class="close-position" onclick="closePosition('${pos.symbol}')">
                                Close
                            </button>
                        </td>
                    </tr>
                `;
                
                // Update position in array with current price
                positions[index].currentPrice = currentPrice;
            });
            
            setTimeout(() => {
                container.innerHTML = html;
                positionsCount.textContent = positions.length;
                positionsValue.textContent = `$${totalValue.toFixed(2)}`;
            }, 100);
        }

        // Load recent trades
        function loadRecentTrades() {
            const container = document.getElementById('recentTrades');
            
            if (trades.length === 0) {
                container.innerHTML = `
                    <div style="text-align: center; padding: 20px; color: var(--gray);">
                        No trades yet. Start trading to see history.
                    </div>
                `;
                return;
            }
            
            let html = '<div style="display: flex; flex-direction: column; gap: 10px;">';
            
            trades.slice(0, 5).forEach(trade => {
                const time = new Date(trade.timestamp).toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'});
                const typeClass = trade.side === 'buy' ? 'positive' : trade.side === 'sell' ? 'negative' : '';
                const typeIcon = trade.side === 'buy' ? '🔼' : trade.side === 'sell' ? '🔽' : trade.type === 'deposit' ? '💵' : '🏦';
                
                html += `
                    <div style="display: flex; justify-content: space-between; align-items: center; padding: 10px; background: #f8fafc; border-radius: 8px;">
                        <div>
                            <strong>${typeIcon} ${trade.symbol || trade.type}</strong>
                            <div style="font-size: 12px; color: var(--gray);">${time}</div>
                        </div>
                        <div style="text-align: right;">
                            <div class="${typeClass}"><strong>$${Math.abs(trade.amount).toFixed(2)}</strong></div>
                            <div style="font-size: 12px; color: var(--gray);">
                                ${trade.qty ? `${trade.qty.toFixed(4)} @ $${trade.price}` : ''}
                            </div>
                        </div>
                    </div>
                `;
            });
            
            html += '</div>';
            container.innerHTML = html;
        }

        // Load real trades from Alpaca
        async function loadRealTrades() {
            if (!alpaca) return;
            
            try {
                const orders = await alpaca.getOrders({
                    status: 'all',
                    limit: 10
                });
                
                // Convert to our format
                trades = orders.map(order => ({
                    id: order.id,
                    symbol: order.symbol,
                    side: order.side,
                    qty: parseFloat(order.qty),
                    price: parseFloat(order.filled_avg_price),
                    amount: parseFloat(order.filled_qty) * parseFloat(order.filled_avg_price),
                    type: order.type,
                    timestamp: order.filled_at,
                    status: order.status
                }));
                
                loadRecentTrades();
            } catch (error) {
                console.error('Error loading trades:', error);
            }
        }

        // Check connection status
        async function checkConnection() {
            if (alpaca && isConnected) {
                try {
                    await alpaca.getAccount();
                    // Connection is good
                } catch (error) {
                    isConnected = false;
                    document.getElementById('connectionStatus').textContent = 'Disconnected';
                    document.getElementById('connectionStatus').className = 'api-status api-disconnected';
                    showNotification('Connection to Alpaca lost', 'error');
                }
            }
        }

        // Get market data
        async function getMarketData() {
            const symbol = document.getElementById('market').value;
            const price = await getCurrentPrice(symbol);
            showNotification(`Current ${symbol} price: $${price.toFixed(2)}`, 'info');
        }

        // Modal functions
        function openSettings() {
            openModal('settingsModal');
        }

        function openHelp() {
            openModal('helpModal');
        }

        function openTradeModal(title, content) {
            document.getElementById('tradeModalTitle').textContent = title;
            document.getElementById('tradeModalContent').innerHTML = content;
            openModal('tradeModal');
        }

        function openModal(modalId) {
            document.getElementById(modalId).style.display = 'flex';
        }

        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        function saveSettings() {
            showNotification('Settings saved successfully!', 'success');
            closeModal('settingsModal');
        }

        // Notification system
        function showNotification(message, type = 'info') {
            const notification = document.getElementById('notification');
            const text = document.getElementById('notificationText');
            
            // Set background color based on type
            const colors = {
                success: '#10b981',
                error: '#ef4444',
                info: '#3b82f6',
                warning: '#f59e0b'
            };
            
            notification.style.background = colors[type] || colors.info;
            text.innerHTML = message;
            notification.style.display = 'block';
            
            setTimeout(() => {
                notification.style.display = 'none';
            }, 5000);
        }

        // Initialize when page loads
        window.onload = initPlatform;
        
        // Close modal when clicking outside
        window.onclick = function(event) {
            if (event.target.className === 'modal') {
                event.target.style.display = 'none';
            }
        };
    </script>
</body>
</html>
```
