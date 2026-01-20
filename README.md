```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NeuralTrade AI - Advanced Trading Platform</title>
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
            padding: 10px 20px;
            border-radius: 10px;
            backdrop-filter: blur(10px);
        }

        .balance-amount {
            font-size: 24px;
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
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <div class="logo-icon">NT</div>
                <div class="logo-text">NeuralTrade AI</div>
            </div>
            <div class="user-menu">
                <div class="balance-card">
                    <div style="font-size: 12px; color: rgba(255, 255, 255, 0.7);">Total Balance</div>
                    <div class="balance-amount">$127,843.92</div>
                </div>
                <button class="btn btn-secondary" onclick="openSettings()">
                    <span>⚙️</span> Settings
                </button>
            </div>
        </header>

        <div class="dashboard-grid">
            <div class="card">
                <div class="card-title">Today's P&L</div>
                <div class="card-value positive">+$2,847.36</div>
                <div class="card-change positive">↑ +2.28%</div>
            </div>
            <div class="card">
                <div class="card-title">Active Strategies</div>
                <div class="card-value">8</div>
                <div class="card-change positive">↑ 2 running</div>
            </div>
            <div class="card">
                <div class="card-title">Win Rate</div>
                <div class="card-value">74.3%</div>
                <div class="card-change positive">↑ 1.2%</div>
            </div>
            <div class="card">
                <div class="card-title">Sharpe Ratio</div>
                <div class="card-value">2.41</div>
                <div class="card-change positive">↑ 0.15</div>
            </div>
        </div>

        <div class="main-content">
            <div class="ai-controls">
                <div class="ai-status">
                    <div class="status-indicator"></div>
                    <span>AI Engine Active • Monitoring 24 markets • Last signal: 2 min ago</span>
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
                                <option value="BTC-USD">Bitcoin (BTC-USD)</option>
                                <option value="ETH-USD">Ethereum (ETH-USD)</option>
                                <option value="SPY">S&P 500 (SPY)</option>
                                <option value="AAPL">Apple (AAPL)</option>
                                <option value="TSLA">Tesla (TSLA)</option>
                                <option value="EUR/USD">EUR/USD Forex</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label for="aiModel">AI Model Type</label>
                            <select id="aiModel">
                                <option value="lstm">LSTM Neural Network</option>
                                <option value="transformer">Transformer Model</option>
                                <option value="ensemble">Ensemble Learning</option>
                                <option value="rl">Reinforcement Learning</option>
                                <option value="hybrid">Hybrid AI</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label for="riskLevel">Risk Level: <span id="riskValue">Medium</span></label>
                            <div class="slider-container">
                                <span style="color: var(--secondary);">Low</span>
                                <input type="range" id="riskLevel" min="1" max="5" value="3" step="1">
                                <span style="color: var(--danger);">High</span>
                                <div class="slider-value" id="riskNumber">3</div>
                            </div>
                        </div>

                        <div class="form-group">
                            <label for="capital">Capital Allocation ($)</label>
                            <input type="number" id="capital" value="10000" min="100" step="100">
                        </div>

                        <div class="form-group">
                            <label for="parameters">AI Parameters (JSON)</label>
                            <textarea id="parameters" rows="4">{
  "lookback_period": 50,
  "confidence_threshold": 0.75,
  "max_position_size": 0.1,
  "stop_loss": 0.02,
  "take_profit": 0.04,
  "use_sentiment": true,
  "news_weight": 0.3
}</textarea>
                        </div>

                        <div class="btn-group">
                            <button class="btn btn-primary" onclick="backtestStrategy()">
                                <span>📊</span> Backtest
                            </button>
                            <button class="btn btn-success" onclick="deployStrategy()">
                                <span>🚀</span> Deploy Live
                            </button>
                            <button class="btn btn-secondary" onclick="optimizeAI()">
                                <span>⚡</span> Optimize AI
                            </button>
                        </div>
                    </div>
                </div>

                <div class="trading-view">
                    <h2 style="color: var(--dark); margin-bottom: 20px;">📈 Live Trading View</h2>
                    <div id="tradingChart" style="height: 300px; background: #f8fafc; border-radius: 10px; display: flex; align-items: center; justify-content: center; color: var(--gray);">
                        [Live Trading Chart Would Display Here]
                    </div>
                    <div class="btn-group" style="margin-top: 20px;">
                        <button class="btn btn-secondary" onclick="paperTrade()">
                            <span>📝</span> Paper Trade
                        </button>
                        <button class="btn btn-danger" onclick="emergencyStop()">
                            <span>🛑</span> Emergency Stop
                        </button>
                    </div>
                </div>
            </div>

            <div>
                <div class="strategy-builder">
                    <h2 style="color: var(--dark); margin-bottom: 20px;">📋 Active Strategies</h2>
                    
                    <div class="strategy-list" id="strategiesList">
                        <!-- Strategies will be loaded here -->
                    </div>
                </div>

                <div class="market-data">
                    <h2 style="color: var(--dark); margin-bottom: 20px;">🌐 Market Overview</h2>
                    
                    <table class="market-table">
                        <thead>
                            <tr>
                                <th>Symbol</th>
                                <th>Price</th>
                                <th>Change</th>
                                <th>AI Signal</th>
                            </tr>
                        </thead>
                        <tbody id="marketData">
                            <!-- Market data will be loaded here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>

    <!-- Modals -->
    <div class="modal" id="backtestModal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">📊 Backtest Results</div>
                <button class="close-modal" onclick="closeModal('backtestModal')">×</button>
            </div>
            <div id="backtestResults">
                <!-- Results will be displayed here -->
            </div>
            <button class="btn btn-primary" style="margin-top: 20px; width: 100%;" onclick="closeModal('backtestModal')">
                Close
            </button>
        </div>
    </div>

    <div class="modal" id="settingsModal">
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-title">⚙️ Platform Settings</div>
                <button class="close-modal" onclick="closeModal('settingsModal')">×</button>
            </div>
            <div class="strategy-form">
                <div class="form-group">
                    <label>API Configuration</label>
                    <input type="text" placeholder="Alpaca API Key">
                    <input type="text" placeholder="Alpaca Secret Key" style="margin-top: 10px;">
                </div>
                <div class="form-group">
                    <label>Risk Management</label>
                    <select>
                        <option>Conservative (Max 2% risk/trade)</option>
                        <option>Moderate (Max 5% risk/trade)</option>
                        <option>Aggressive (Max 10% risk/trade)</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Notifications</label>
                    <div>
                        <input type="checkbox" id="emailAlerts"> <label for="emailAlerts" style="display: inline;">Email Alerts</label><br>
                        <input type="checkbox" id="pushAlerts" checked> <label for="pushAlerts" style="display: inline;">Push Notifications</label>
                    </div>
                </div>
                <button class="btn btn-primary" style="width: 100%; margin-top: 20px;" onclick="saveSettings()">
                    Save Settings
                </button>
            </div>
        </div>
    </div>

    <div class="notification" id="notification">
        <span id="notificationText">Notification message</span>
    </div>

    <script>
        // Sample Data
        const strategies = [
            { id: 1, name: "Momentum AI v2.1", market: "BTC-USD", status: "active", pnl: "+$1,234", winRate: "78%", capital: "$10,000" },
            { id: 2, name: "Mean Reversion Bot", market: "ETH-USD", status: "active", pnl: "+$567", winRate: "65%", capital: "$5,000" },
            { id: 3, name: "News Sentiment AI", market: "SPY", status: "paused", pnl: "-$123", winRate: "72%", capital: "$15,000" },
            { id: 4, name: "Deep Learning NN", market: "AAPL", status: "stopped", pnl: "+$2,345", winRate: "81%", capital: "$8,000" }
        ];

        const marketData = [
            { symbol: "BTC-USD", price: "$42,567.89", change: "+2.34%", signal: "BUY" },
            { symbol: "ETH-USD", price: "$2,345.67", change: "+1.23%", signal: "HOLD" },
            { symbol: "SPY", price: "$456.78", change: "-0.45%", signal: "SELL" },
            { symbol: "AAPL", price: "$178.90", change: "+0.67%", signal: "BUY" },
            { symbol: "TSLA", price: "$234.56", change: "-1.23%", signal: "SELL" },
            { symbol: "EUR/USD", price: "1.0876", change: "+0.12%", signal: "HOLD" }
        ];

        // Initialize the platform
        function initPlatform() {
            loadStrategies();
            loadMarketData();
            updateRiskSlider();
            
            // Simulate live updates
            setInterval(simulateLiveData, 5000);
        }

        function loadStrategies() {
            const container = document.getElementById('strategiesList');
            container.innerHTML = '';
            
            strategies.forEach(strategy => {
                const statusClass = `status-${strategy.status}`;
                const item = document.createElement('div');
                item.className = 'strategy-item';
                item.innerHTML = `
                    <div class="strategy-header">
                        <div class="strategy-name">${strategy.name}</div>
                        <div class="strategy-status ${statusClass}">${strategy.status.toUpperCase()}</div>
                    </div>
                    <div>Market: ${strategy.market} • Capital: ${strategy.capital}</div>
                    <div class="performance-metrics">
                        <div class="metric">
                            <div class="metric-value">${strategy.pnl}</div>
                            <div class="metric-label">P&L</div>
                        </div>
                        <div class="metric">
                            <div class="metric-value">${strategy.winRate}</div>
                            <div class="metric-label">Win Rate</div>
                        </div>
                        <div class="metric">
                            <div class="metric-value">${strategy.status === 'active' ? '🔴' : '⏸️'}</div>
                            <div class="metric-label">Status</div>
                        </div>
                        <div class="metric">
                            <button class="btn btn-secondary" style="padding: 5px 10px; font-size: 12px;" onclick="toggleStrategy(${strategy.id})">
                                ${strategy.status === 'active' ? 'Pause' : 'Start'}
                            </button>
                        </div>
                    </div>
                `;
                container.appendChild(item);
            });
        }

        function loadMarketData() {
            const container = document.getElementById('marketData');
            container.innerHTML = '';
            
            marketData.forEach(item => {
                const changeClass = item.change.startsWith('+') ? 'positive' : 'negative';
                const signalClass = item.signal === 'BUY' ? 'positive' : item.signal === 'SELL' ? 'negative' : '';
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td><strong>${item.symbol}</strong></td>
                    <td>${item.price}</td>
                    <td class="${changeClass}">${item.change}</td>
                    <td class="${signalClass}"><strong>${item.signal}</strong></td>
                `;
                container.appendChild(row);
            });
        }

        function updateRiskSlider() {
            const slider = document.getElementById('riskLevel');
            const valueDisplay = document.getElementById('riskValue');
            const numberDisplay = document.getElementById('riskNumber');
            
            const riskLevels = ['Very Low', 'Low', 'Medium', 'High', 'Very High'];
            const riskColors = ['#10b981', '#34d399', '#f59e0b', '#f97316', '#ef4444'];
            
            slider.addEventListener('input', function() {
                const value = parseInt(this.value);
                numberDisplay.textContent = value;
                valueDisplay.textContent = riskLevels[value - 1];
                valueDisplay.style.color = riskColors[value - 1];
            });
        }

        function backtestStrategy() {
            const strategyName = document.getElementById('strategyName').value || 'Unnamed Strategy';
            const market = document.getElementById('market').value;
            const model = document.getElementById('aiModel').value;
            const risk = document.getElementById('riskLevel').value;
            const capital = document.getElementById('capital').value;
            
            // Simulate backtest results
            const results = {
                totalReturn: (Math.random() * 30).toFixed(2) + '%',
                sharpeRatio: (1.5 + Math.random()).toFixed(2),
                maxDrawdown: (5 + Math.random() * 10).toFixed(2) + '%',
                winRate: (60 + Math.random() * 25).toFixed(1) + '%',
                totalTrades: Math.floor(100 + Math.random() * 400),
                avgTrade: (Math.random() * 200).toFixed(2) + '%'
            };
            
            const modalContent = document.getElementById('backtestResults');
            modalContent.innerHTML = `
                <h3 style="margin-bottom: 15px; color: var(--dark);">${strategyName}</h3>
                <div style="background: #f8fafc; padding: 20px; border-radius: 10px;">
                    <div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 15px; margin-bottom: 20px;">
                        <div class="metric">
                            <div class="metric-value" style="color: var(--secondary);">${results.totalReturn}</div>
                            <div class="metric-label">Total Return</div>
                        </div>
                        <div class="metric">
                            <div class="metric-value">${results.sharpeRatio}</div>
                            <div class="metric-label">Sharpe Ratio</div>
                        </div>
                        <div class="metric">
                            <div class="metric-value" style="color: var(--danger);">${results.maxDrawdown}</div>
                            <div class="metric-label">Max Drawdown</div>
                        </div>
                        <div class="metric">
                            <div class="metric-value" style="color: var(--secondary);">${results.winRate}</div>
                            <div class="metric-label">Win Rate</div>
                        </div>
                    </div>
                    <div style="font-size: 14px; color: var(--gray);">
                        <p>Market: ${market}</p>
                        <p>AI Model: ${model}</p>
                        <p>Risk Level: ${risk}/5</p>
                        <p>Capital: $${capital}</p>
                    </div>
                    <div style="margin-top: 15px; padding: 15px; background: #d1fae5; border-radius: 8px; color: #065f46;">
                        <strong>✅ Backtest Passed:</strong> Strategy meets all risk parameters and shows profitable expectancy.
                    </div>
                </div>
            `;
            
            openModal('backtestModal');
            showNotification('Backtest completed successfully!');
        }

        function deployStrategy() {
            const strategyName = document.getElementById('strategyName').value || 'Unnamed Strategy';
            showNotification(`🚀 Strategy "${strategyName}" deployed successfully! AI is now trading live.`);
            
            // Simulate adding new strategy
            strategies.unshift({
                id: strategies.length + 1,
                name: strategyName,
                market: document.getElementById('market').value,
                status: 'active',
                pnl: '+$0',
                winRate: '0%',
                capital: '$' + document.getElementById('capital').value
            });
            
            loadStrategies();
        }

        function optimizeAI() {
            showNotification('🤖 AI optimization in progress... This may take a few minutes.');
            
            // Simulate optimization
            setTimeout(() => {
                const improvement = (Math.random() * 15).toFixed(1);
                showNotification(`⚡ AI optimized! Expected improvement: +${improvement}% in performance`);
            }, 3000);
        }

        function paperTrade() {
            showNotification('📝 Starting paper trading session with $100,000 virtual capital');
        }

        function emergencyStop() {
            if (confirm('⚠️ EMERGENCY STOP: This will immediately close all positions. Are you sure?')) {
                showNotification('🛑 EMERGENCY STOP ACTIVATED: All positions closed. Trading halted.');
                
                // Update all strategies to stopped
                strategies.forEach(strategy => {
                    strategy.status = 'stopped';
                });
                
                loadStrategies();
            }
        }

        function toggleStrategy(id) {
            const strategy = strategies.find(s => s.id === id);
            if (strategy) {
                strategy.status = strategy.status === 'active' ? 'paused' : 'active';
                showNotification(`Strategy "${strategy.name}" ${strategy.status === 'active' ? 'activated' : 'paused'}`);
                loadStrategies();
            }
        }

        function openSettings() {
            openModal('settingsModal');
        }

        function saveSettings() {
            showNotification('Settings saved successfully!');
            closeModal('settingsModal');
        }

        function openModal(modalId) {
            document.getElementById(modalId).style.display = 'flex';
        }

        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        function showNotification(message) {
            const notification = document.getElementById('notification');
            const text = document.getElementById('notificationText');
            
            text.textContent = message;
            notification.style.display = 'block';
            
            setTimeout(() => {
                notification.style.display = 'none';
            }, 5000);
        }

        function simulateLiveData() {
            // Simulate live price updates
            const randomSymbol = Math.floor(Math.random() * marketData.length);
            const change = (Math.random() - 0.5) * 2;
            const changeFormatted = change >= 0 ? `+${change.toFixed(2)}%` : `${change.toFixed(2)}%`;
            
            marketData[randomSymbol].price = `$${(Math.random() * 50000).toFixed(2)}`;
            marketData[randomSymbol].change = changeFormatted;
            
            // Update random signal
            const signals = ['BUY', 'SELL', 'HOLD'];
            marketData[randomSymbol].signal = signals[Math.floor(Math.random() * 3)];
            
            loadMarketData();
        }

        // Close modal when clicking outside
        window.onclick = function(event) {
            if (event.target.className === 'modal') {
                event.target.style.display = 'none';
            }
        }

        // Initialize platform when page loads
        window.onload = initPlatform;
    </script>
</body>
</html>
```
