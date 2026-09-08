
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Sahi Chuna Kya - NEXA Comparison</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Rajdhani:wght@500;600;700&display=swap');

        * { margin: 0; padding: 0; box-sizing: border-box; }

        :root {
            --primary-bg: #0a0a0a;
            --accent-blue: #00e5ff;
            --accent-green: #00ff88;
            --accent-red: #ff4d79;
            --accent-gold: #ffc107;
            --text-light: #ffffff;
            --text-muted: #a0aab5;
            --border-color: rgba(255, 255, 255, 0.15);
            --panel-bg: rgba(20, 22, 28, 0.75);
        }

        body {
            font-family: 'Rajdhani', sans-serif;
            background-color: var(--primary-bg);
            background-image: 
                linear-gradient(rgba(10, 12, 16, 0.85), rgba(10, 12, 16, 0.95)), 
                url('https://imgd.aeplcdn.com/1280x720/n/cw/ec/123185/grand-vitara-exterior-right-front-three-quarter-4.jpeg');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            color: var(--text-light);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px 10px;
            overflow-x: hidden;
            position: relative;
        }

        .bg-video {
            position: fixed; top: 0; left: 0; width: 100vw; height: 100vh;
            object-fit: cover; z-index: -2; pointer-events: none;
        }

        .bg-overlay {
            position: fixed; top: 0; left: 0; width: 100vw; height: 100vh;
            background: linear-gradient(rgba(10, 12, 16, 0.85), rgba(10, 12, 16, 0.95));
            z-index: -1; pointer-events: none;
        }

        .top-logo-container {
            position: absolute; top: 20px; left: 30px; z-index: 100;
        }

        .nexa-logo { height: 20px; filter: brightness(0) invert(1); }

        .header { text-align: center; margin-bottom: 20px; width: 100%; margin-top: 30px; }
        .header h1 {
            font-family: 'Orbitron', sans-serif; color: var(--accent-blue);
            font-size: clamp(2rem, 4vw, 3.5rem); margin-bottom: 5px;
            text-transform: uppercase; letter-spacing: 3px;
            text-shadow: 0 0 20px rgba(0, 229, 255, 0.4); line-height: 1.2;
        }
        .header p {
            color: var(--text-muted); font-size: clamp(1rem, 1.5vw, 1.2rem);
            font-weight: 500; letter-spacing: 1px;
        }

        .tabs {
            display: flex; gap: 10px; margin-bottom: 20px; width: 100%; max-width: 1350px;
            background: rgba(0,0,0,0.5); padding: 10px; border-radius: 16px; border: 1px solid var(--border-color);
            backdrop-filter: blur(10px);
        }
        .tab-btn {
            flex: 1; padding: 15px; background: transparent; border: none;
            color: var(--text-muted); font-family: 'Orbitron', sans-serif; font-size: clamp(0.9rem, 1.5vw, 1.2rem);
            cursor: pointer; border-radius: 10px; transition: all 0.3s;
            text-transform: uppercase; letter-spacing: 1px; font-weight: bold;
        }
        .tab-btn.active {
            background: rgba(0, 229, 255, 0.15); color: var(--accent-blue);
            box-shadow: inset 0 0 10px rgba(0, 229, 255, 0.2); border: 1px solid rgba(0, 229, 255, 0.3);
        }
        .tab-content { display: none; width: 100%; max-width: 1350px; animation: fadeIn 0.4s ease; }
        .tab-content.active { display: block; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

        .dashboard-container {
            background: var(--panel-bg); border: 1px solid var(--border-color);
            border-radius: 24px; padding: clamp(20px, 4vw, 40px);
            box-shadow: 0 20px 50px rgba(0,0,0,0.5), inset 0 0 0 1px rgba(255,255,255,0.05);
            backdrop-filter: blur(15px); -webkit-backdrop-filter: blur(15px);
        }

        /* Diagnostic Form Styles */
        .diag-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; margin-bottom: 30px;
        }
        .diag-item {
            background: rgba(0,0,0,0.4); padding: 20px; border-radius: 15px; border: 1px solid rgba(255,255,255,0.1);
        }
        .diag-item label {
            display: block; font-family: 'Orbitron', sans-serif; color: var(--accent-gold);
            margin-bottom: 15px; font-size: 1rem;
        }
        .diag-options { display: flex; flex-direction: column; gap: 10px; }
        .diag-option {
            display: flex; align-items: center; cursor: pointer; padding: 10px 15px;
            background: rgba(255,255,255,0.05); border-radius: 8px; border: 1px solid transparent;
            transition: all 0.2s; font-size: 1.1rem;
        }
        .diag-option:hover { background: rgba(255,255,255,0.1); border-color: rgba(255,255,255,0.2); }
        .diag-option input { margin-right: 15px; transform: scale(1.3); accent-color: var(--accent-blue); }

        .diag-btn-container { text-align: center; }
        .calc-btn {
            background: linear-gradient(135deg, var(--accent-blue), #0088ff); color: #000;
            border: none; padding: 15px 40px; font-family: 'Orbitron', sans-serif; font-size: 1.2rem;
            font-weight: bold; border-radius: 12px; cursor: pointer; text-transform: uppercase;
            box-shadow: 0 0 20px rgba(0, 229, 255, 0.4); transition: transform 0.2s, box-shadow 0.2s;
        }
        .calc-btn:hover { transform: scale(1.05); box-shadow: 0 0 30px rgba(0, 229, 255, 0.6); }

        .result-box {
            margin-top: 30px; background: rgba(0,0,0,0.6); border: 1px solid var(--accent-blue);
            border-radius: 16px; padding: 30px; text-align: center; display: none;
        }
        .result-score { font-family: 'Orbitron', sans-serif; font-size: 3rem; margin-bottom: 10px; }
        .result-desc { font-size: 1.4rem; color: var(--text-light); line-height: 1.6; }

        /* Comparison Styles */
        .control-panel {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px;
            margin-bottom: 30px; background: rgba(0, 0, 0, 0.4); padding: 25px; border-radius: 16px;
            border: 1px solid rgba(255,255,255,0.1);
        }
        .input-group { display: flex; flex-direction: column; width: 100%; }
        .input-group label {
            font-family: 'Orbitron', sans-serif; font-size: 0.9rem; color: var(--text-muted);
            margin-bottom: 10px; text-transform: uppercase; letter-spacing: 1px;
        }
        .input-group select, .input-group input {
            background: rgba(10, 10, 10, 0.8); color: var(--accent-blue); border: 1px solid var(--border-color);
            padding: 15px; border-radius: 10px; font-family: 'Orbitron', sans-serif; font-size: 1rem;
            outline: none; box-shadow: inset 0 2px 5px rgba(0,0,0,0.5); width: 100%;
        }
        .input-group select {
            appearance: none; cursor: pointer; padding-right: 40px;
            background-image: url("data:image/svg+xml;charset=US-ASCII,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%22292.4%22%20height%3D%22292.4%22%3E%3Cpath%20fill%3D%22%2300e5ff%22%20d%3D%22M287%2069.4a17.6%2017.6%200%200%200-13-5.4H18.4c-5%200-9.3%201.8-12.9%205.4A17.6%2017.6%200%200%200%200%2082.2c0%205%201.8%209.3%205.4%2012.9l128%20127.9c3.6%203.6%207.8%205.4%2012.8%205.4s9.2-1.8%2012.8-5.4L287%2095c3.5-3.5%205.4-7.8%205.4-12.8%200-5-1.9-9.2-5.5-12.8z%22%2F%3E%3C%2Fsvg%3E");
            background-repeat: no-repeat; background-position: right 15px center; background-size: 14px;
        }

        .dashboard-grid {
            display: grid; grid-template-columns: 1fr 1fr; gap: 30px; margin-bottom: 30px;
        }
        
        .variant-card {
            background: rgba(0, 0, 0, 0.5); border: 1px solid rgba(255,255,255,0.1);
            border-radius: 20px; padding: 25px; box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            transition: transform 0.3s;
        }
        .variant-card:hover { transform: translateY(-5px); border-color: rgba(255,255,255,0.3); }

        .odometer-display {
            background: rgba(10, 10, 10, 0.8); border: 1px solid rgba(255,255,255,0.05);
            border-radius: 12px; padding: 15px; margin-bottom: 25px; text-align: center;
            box-shadow: inset 0 5px 15px rgba(0,0,0,0.8);
        }
        .variant-card h3 {
            font-family: 'Orbitron', sans-serif; color: var(--text-light); font-size: 1.3rem; margin: 0;
        }

        .data-row {
            display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px;
            padding-bottom: 8px; border-bottom: 1px solid rgba(255, 255, 255, 0.05); font-size: 1.1rem;
        }
        .data-row span:first-child { color: var(--text-muted); font-weight: 500; }
        .data-row span:last-child { font-family: 'Orbitron', sans-serif; color: var(--text-light); font-weight: 700; }
        .spec-highlight span:last-child { color: var(--accent-blue); }

        .total-cost { margin-top: 20px; padding-top: 20px; border-top: 2px solid rgba(255, 77, 121, 0.5); font-size: 1.3rem; }
        .total-cost span:last-child { color: var(--accent-red); text-shadow: 0 0 10px rgba(255, 77, 121, 0.4); }

        /* Break Even Meter */
        .breakeven-meter {
            background: linear-gradient(135deg, rgba(0, 229, 255, 0.1), rgba(0, 0, 0, 0.8));
            border: 1px solid var(--accent-blue); padding: 25px; border-radius: 16px;
            margin-bottom: 30px; text-align: center; display: none;
            box-shadow: 0 10px 30px rgba(0, 229, 255, 0.1), inset 0 0 20px rgba(0, 229, 255, 0.05);
        }
        .be-title { font-family: 'Orbitron', sans-serif; color: var(--accent-blue); font-size: 1.4rem; margin-bottom: 15px; text-transform: uppercase; letter-spacing: 2px;}
        .be-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px; margin-bottom: 20px; }
        .be-box { background: rgba(0,0,0,0.6); padding: 15px; border-radius: 12px; border: 1px solid rgba(255,255,255,0.1); }
        .be-label { display: block; font-size: 0.9rem; color: var(--text-muted); margin-bottom: 5px; text-transform: uppercase; }
        .be-val { font-family: 'Orbitron', sans-serif; font-size: 1.3rem; font-weight: bold; color: var(--text-light); }
        .be-final {
            background: rgba(0, 229, 255, 0.15); padding: 20px; border-radius: 12px;
            border: 1px dashed var(--accent-blue); display: inline-block; width: 100%;
        }
        .be-final-val { font-family: 'Orbitron', sans-serif; font-size: 1.8rem; color: var(--accent-blue); text-shadow: 0 0 10px rgba(0, 229, 255, 0.5); }

        .savings-box {
            background: linear-gradient(135deg, rgba(0, 255, 136, 0.15), rgba(0, 0, 0, 0.8));
            border: 1px solid var(--accent-green); color: var(--accent-green); padding: 30px;
            border-radius: 16px; text-align: center; font-family: 'Orbitron', sans-serif; font-size: 1.6rem;
            box-shadow: 0 10px 30px rgba(0, 255, 136, 0.1);
        }
        .savings-amount { font-size: 1.5em; display: block; margin-top: 8px; color: #ffffff; font-weight: bold; }
        .savings-neutral { border-color: rgba(255,255,255,0.2); color: var(--text-light); background: rgba(0, 0, 0, 0.6); }

        @media (max-width: 900px) {
            .dashboard-grid { grid-template-columns: 1fr; gap: 20px; }
            .tabs { flex-direction: column; }
            .header h1 { font-size: 2.2rem; }
            .top-logo-container { position: relative; top: 0; left: 0; text-align: center; display: flex; justify-content: center; width: 100%; margin-bottom: 10px; }
        }
    </style>
</head>
<body>

    <video class="bg-video" autoplay loop muted playsinline>
        <source src="video_c58f00.mp4" type="video/mp4">
    </video>
    <div class="bg-overlay"></div>

    <div class="top-logo-container">
        <img src="https://upload.wikimedia.org/wikipedia/commons/4/4e/Nexa_logo.svg" alt="NEXA Logo" class="nexa-logo">
    </div>

    <div class="header">
        <h1>Sahi Chuna Kya</h1>
        <p>Smart Decision Matrix: Diagnostics & Financials</p>
    </div>

    <!-- TABS -->
    <div class="tabs">
        <button class="tab-btn active" onclick="openTab('diagnostic')">1. Suitability Score</button>
        <button class="tab-btn" onclick="openTab('financial')">2. Financial Calculator</button>
    </div>

    <!-- TAB 1: DIAGNOSTIC TOOL -->
    <div id="diagnostic" class="tab-content active">
        <div class="dashboard-container">
            <div style="text-align: center; margin-bottom: 30px;">
                <h2 style="font-family: 'Orbitron', sans-serif; color: var(--text-light); font-size: 1.8rem; margin-bottom: 10px;">CNG Suitability Score</h2>
                <p style="color: var(--text-muted); font-size: 1.1rem;">Let's find out which powertrain matches your lifestyle.</p>
            </div>

            <div class="diag-grid">
                <div class="diag-item">
                    <label>1. Average Monthly Running</label>
                    <div class="diag-options">
                        <label class="diag-option"><input type="radio" name="q1" value="p" checked> Less than 1,000 km</label>
                        <label class="diag-option"><input type="radio" name="q1" value="e"> 1,000 km to 2,000 km</label>
                        <label class="diag-option"><input type="radio" name="q1" value="c"> More than 2,000 km</label>
                    </div>
                </div>
                <div class="diag-item">
                    <label>2. Expected Ownership Period</label>
                    <div class="diag-options">
                        <label class="diag-option"><input type="radio" name="q2" value="p" checked> Short (1 - 3 Years)</label>
                        <label class="diag-option"><input type="radio" name="q2" value="e"> Medium (3 - 5 Years)</label>
                        <label class="diag-option"><input type="radio" name="q2" value="c"> Long (5+ Years)</label>
                    </div>
                </div>
                <div class="diag-item">
                    <label>3. Boot Space Requirement</label>
                    <div class="diag-options">
                        <label class="diag-option"><input type="radio" name="q3" value="p" checked> Essential (Full Boot Needed)</label>
                        <label class="diag-option"><input type="radio" name="q3" value="e"> Neutral (Occasional Use)</label>
                        <label class="diag-option"><input type="radio" name="q3" value="c"> Unimportant (Rarely Used)</label>
                    </div>
                </div>
                <div class="diag-item">
                    <label>4. Frequency of Long Highway Trips</label>
                    <div class="diag-options">
                        <label class="diag-option"><input type="radio" name="q4" value="p" checked> Frequently</label>
                        <label class="diag-option"><input type="radio" name="q4" value="e"> Occasionally</label>
                        <label class="diag-option"><input type="radio" name="q4" value="c"> Rarely (Mostly City)</label>
                    </div>
                </div>
                <div class="diag-item">
                    <label>5. CNG Station Accessibility Near You</label>
                    <div class="diag-options">
                        <label class="diag-option"><input type="radio" name="q5" value="p" checked> Poor / Long Queues</label>
                        <label class="diag-option"><input type="radio" name="q5" value="e"> Average</label>
                        <label class="diag-option"><input type="radio" name="q5" value="c"> Good / Easily Accessible</label>
                    </div>
                </div>
                <div class="diag-item">
                    <label>6. Primary Driving Focus</label>
                    <div class="diag-options">
                        <label class="diag-option"><input type="radio" name="q6" value="p" checked> Max Performance & Pick-up</label>
                        <label class="diag-option"><input type="radio" name="q6" value="e"> Balanced</label>
                        <label class="diag-option"><input type="radio" name="q6" value="c"> Maximum Fuel Economy</label>
                    </div>
                </div>
            </div>

            <div class="diag-btn-container">
                <button class="calc-btn" onclick="calculateScore()">Generate Suitability Score</button>
            </div>

            <div id="scoreResult" class="result-box">
                <div class="result-score" id="resScoreText">PETROL FIT: 0/100</div>
                <div class="result-desc" id="resDescText">-</div>
                <button class="calc-btn" style="margin-top:20px; font-size:1rem; padding: 10px 20px; background: rgba(255,255,255,0.1); border: 1px solid #fff; color:#fff;" onclick="openTab('financial')">Proceed to Financial Comparison →</button>
            </div>
        </div>
    </div>

    <!-- TAB 2: FINANCIAL CALCULATOR -->
    <div id="financial" class="tab-content">
        <div class="dashboard-container">
            <div class="control-panel">
                <div class="input-group">
                    <label>Select Vehicle A</label>
                    <select id="variantA"></select>
                </div>
                <div class="input-group">
                    <label>Select Vehicle B</label>
                    <select id="variantB"></select>
                </div>
                <div class="input-group">
                    <label>Est. Running (Km/Month)</label>
                    <input type="number" id="monthlyKm" value="1000" min="100" step="100">
                </div>
                <div class="input-group">
                    <label>Ownership Tenure</label>
                    <select id="tenure">
                        <option value="1">1 Year</option>
                        <option value="2">2 Years</option>
                        <option value="3">3 Years</option>
                        <option value="4">4 Years</option>
                        <option value="5" selected>5 Years</option>
                        <option value="6">6 Years</option>
                        <option value="7">7 Years</option>
                    </select>
                </div>
            </div>

            <!-- Break Even Meter -->
            <div class="breakeven-meter" id="breakEvenMeter">
                <div class="be-title">⚡ Your Investment Break-Even Meter</div>
                <div class="be-grid">
                    <div class="be-box">
                        <span class="be-label">Your Driving</span>
                        <span class="be-val" id="be-driving">-</span>
                    </div>
                    <div class="be-box">
                        <span class="be-label">Extra Upfront Investment</span>
                        <span class="be-val" id="be-invest" style="color: var(--accent-red);">-</span>
                    </div>
                    <div class="be-box">
                        <span class="be-label">Estimated Fuel Saving</span>
                        <span class="be-val" id="be-saving" style="color: var(--accent-green);">-</span>
                    </div>
                </div>
                <div class="be-final">
                    <span class="be-label" style="margin-bottom: 10px;">Investment Recovered In</span>
                    <div class="be-final-val" id="be-result">-</div>
                </div>
            </div>

            <div class="dashboard-grid">
                <div class="variant-card" id="cardA">
                    <div class="odometer-display"><h3 id="nameA">LOADING...</h3></div>
                    <div class="data-row"><span>On-Road Valuation</span><span id="priceA">-</span></div>
                    <div class="data-row spec-highlight"><span>Mileage</span><span id="mileageA">-</span></div>
                    <div class="data-row spec-highlight"><span>Fuel Rate</span><span id="fuelRateA">-</span></div>
                    <div class="data-row"><span>Financed Amount (80%)</span><span id="loanA">-</span></div>
                    <div class="data-row"><span>Monthly Instalment (<span class="dyn-tenure">5</span>Y)</span><span id="emiA">-</span></div>
                    <div class="data-row"><span>Total Fuel Cost (<span class="dyn-tenure">5</span>Y)</span><span id="fuelA">-</span></div>
                    <div class="data-row total-cost"><span>Total System Cost</span><span id="totalCostA">-</span></div>
                </div>
                
                <div class="variant-card" id="cardB">
                    <div class="odometer-display"><h3 id="nameB">LOADING...</h3></div>
                    <div class="data-row"><span>On-Road Valuation</span><span id="priceB">-</span></div>
                    <div class="data-row spec-highlight"><span>Mileage</span><span id="mileageB">-</span></div>
                    <div class="data-row spec-highlight"><span>Fuel Rate</span><span id="fuelRateB">-</span></div>
                    <div class="data-row"><span>Financed Amount (80%)</span><span id="loanB">-</span></div>
                    <div class="data-row"><span>Monthly Instalment (<span class="dyn-tenure">5</span>Y)</span><span id="emiB">-</span></div>
                    <div class="data-row"><span>Total Fuel Cost (<span class="dyn-tenure">5</span>Y)</span><span id="fuelB">-</span></div>
                    <div class="data-row total-cost"><span>Total System Cost</span><span id="totalCostB">-</span></div>
                </div>
            </div>

            <div class="savings-box" id="savingsBox">AWAITING INPUT...</div>
        </div>
    </div>

    <script>
        const variantsData = [{"variant": "BALENO SIGMA 1.2L 5MT", "on_road_price": 681390, "mileage": 22.35, "fuel_price": 115}, {"variant": "BALENO DELTA 1.2L 5MT", "on_road_price": 785420, "mileage": 22.35, "fuel_price": 115}, {"variant": "BALENO ZETA 1.2L 5MT", "on_road_price": 892854, "mileage": 22.35, "fuel_price": 115}, {"variant": "BALENO ALPHA 1.2L 5MT", "on_road_price": 1014079, "mileage": 22.35, "fuel_price": 115}, {"variant": "BALENO DELTA 1.2L AGS", "on_road_price": 840515, "mileage": 22.94, "fuel_price": 115}, {"variant": "BALENO ZETA 1.2L AGS", "on_road_price": 948871, "mileage": 22.94, "fuel_price": 115}, {"variant": "BALENO ALPHA 1.2L AGS", "on_road_price": 1069470, "mileage": 22.94, "fuel_price": 115}, {"variant": "BALENO DELTA CNG 1.2L 5MT", "on_road_price": 891054, "mileage": 30.61, "fuel_price": 104}, {"variant": "BALENO ZETA CNG 1.2L 5MT", "on_road_price": 998923, "mileage": 30.61, "fuel_price": 104}, {"variant": "FRONX SIGMA 1.2L 5MT", "on_road_price": 776637, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX DELTA 1.2L 5MT", "on_road_price": 875783, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX DELTA+ 1.2L 5MT", "on_road_price": 919409, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX DELTA 1.2L AGS", "on_road_price": 930868, "mileage": 22.89, "fuel_price": 115}, {"variant": "FRONX DELTA+ 1.2L AGS", "on_road_price": 974490, "mileage": 22.89, "fuel_price": 115}, {"variant": "FRONX TURBO DELTA+ 1.0L 5MT", "on_road_price": 1000030, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX TURBO ZETA 1.0L 5MT", "on_road_price": 1086434, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX TURBO ALPHA 1.0L 5MT", "on_road_price": 1212398, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX TURBO ZETA 1.0L 6AT", "on_road_price": 1261122, "mileage": 22.89, "fuel_price": 115}, {"variant": "FRONX TURBO ALPHA 1.0L 6AT", "on_road_price": 1358480, "mileage": 22.89, "fuel_price": 115}, {"variant": "FRONX SIGMA CNG 1.2L 5MT", "on_road_price": 891941, "mileage": 28.51, "fuel_price": 104}, {"variant": "FRONX DELTA CNG 1.2L 5MT", "on_road_price": 985637, "mileage": 28.51, "fuel_price": 104}, {"variant": "GRAND VITARA SIGMA 1.5L 5MT", "on_road_price": 1240470, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA DELTA 1.5L 5MT", "on_road_price": 1398900, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA ZETA 1.5L 5MT", "on_road_price": 1580345, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA ZETA(O) 1.5L 5MT", "on_road_price": 1596306, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA 1.5L 5MT", "on_road_price": 1749792, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA(O) 1.5L 5MT", "on_road_price": 1767173, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA DELTA 1.5L 6AT", "on_road_price": 1551146, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA ZETA 1.5L 6AT", "on_road_price": 1734369, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA ZETA(O) 1.5L 6AT", "on_road_price": 1750487, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA 1.5L 6AT", "on_road_price": 1905477, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA(O) 1.5L 6AT", "on_road_price": 1921479, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA4WD 1.5L 6AT", "on_road_price": 2071211, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA(O)4WD 1.5L 6AT", "on_road_price": 2137392, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA DELTA+ 1.5L CVT", "on_road_price": 1915307, "mileage": 27.97, "fuel_price": 115}, {"variant": "GRAND VITARA ZETA+ 1.5L CVT", "on_road_price": 2061954, "mileage": 27.97, "fuel_price": 115}, {"variant": "GRAND VITARA ZETA+(O) 1.5L CVT", "on_road_price": 2129047, "mileage": 27.97, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA+ 1.5L CVT", "on_road_price": 2243233, "mileage": 27.97, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA+(O) 1.5L CVT", "on_road_price": 2251007, "mileage": 27.97, "fuel_price": 115}, {"variant": "GRAND VITARA DELTA CNG 1.5L 5MT", "on_road_price": 1496002, "mileage": 26.6, "fuel_price": 104}, {"variant": "GRAND VITARA ZETA CNG 1.5L 5MT", "on_road_price": 1677510, "mileage": 26.6, "fuel_price": 104}, {"variant": "XL6 ZETA 1.5L 5MT", "on_road_price": 1336091, "mileage": 20.97, "fuel_price": 115}, {"variant": "XL6 ALPHA 1.5L 5MT", "on_road_price": 1448507, "mileage": 20.97, "fuel_price": 115}, {"variant": "XL6 ALPHA+ 1.5L 5MT", "on_road_price": 1503763, "mileage": 20.97, "fuel_price": 115}, {"variant": "XL6 ZETA 1.5L 6AT", "on_road_price": 1492551, "mileage": 20.27, "fuel_price": 115}, {"variant": "XL6 ALPHA 1.5L 6AT", "on_road_price": 1602947, "mileage": 20.27, "fuel_price": 115}, {"variant": "XL6 ALPHA+ 1.5L 6AT", "on_road_price": 1658202, "mileage": 20.27, "fuel_price": 115}, {"variant": "XL6 ZETA CNG 1.5L 5MT", "on_road_price": 1447048, "mileage": 26.32, "fuel_price": 104}, {"variant": "JIMNY ZETA 1.5L 5MT", "on_road_price": 1440507, "mileage": 16.94, "fuel_price": 115}, {"variant": "JIMNY ALPHA 1.5L 5MT", "on_road_price": 1545229, "mileage": 16.94, "fuel_price": 115}, {"variant": "JIMNY ZETA 1.5L 4AT", "on_road_price": 1561561, "mileage": 16.39, "fuel_price": 115}, {"variant": "JIMNY ALPHA 1.5L 4AT", "on_road_price": 1666282, "mileage": 16.39, "fuel_price": 115}, {"variant": "INVICTO ZETA+ 2.0L CVT 7 STR", "on_road_price": 2960369, "mileage": 23.24, "fuel_price": 115}, {"variant": "INVICTO ZETA+ 2.0L CVT 8 STR", "on_road_price": 3007531, "mileage": 23.24, "fuel_price": 115}, {"variant": "INVICTO ALPHA+ 2.0L CVT 7 STR", "on_road_price": 3401373, "mileage": 23.24, "fuel_price": 115}];

        const formatCurrency = (val) => '₹ ' + new Intl.NumberFormat('en-IN', { maximumFractionDigits: 0 }).format(val);

        // Tab System
        function openTab(tabName) {
            document.querySelectorAll('.tab-content').forEach(tab => tab.classList.remove('active'));
            document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));
            document.getElementById(tabName).classList.add('active');
            event.currentTarget.classList.add('active');
        }

        // Diagnostic Logic
        function calculateScore() {
            let cngScore = 0; let petrolScore = 0;
            
            const q1 = document.querySelector('input[name="q1"]:checked').value;
            if(q1==='p') { petrolScore+=20; } else if(q1==='e') { petrolScore+=10; cngScore+=10; } else { cngScore+=20; }

            const q2 = document.querySelector('input[name="q2"]:checked').value;
            if(q2==='p') { petrolScore+=15; } else if(q2==='e') { petrolScore+=7; cngScore+=8; } else { cngScore+=15; }

            const q3 = document.querySelector('input[name="q3"]:checked').value;
            if(q3==='p') { petrolScore+=15; } else if(q3==='e') { petrolScore+=8; cngScore+=7; } else { cngScore+=15; }

            const q4 = document.querySelector('input[name="q4"]:checked').value;
            if(q4==='p') { petrolScore+=15; cngScore+=0; } else if(q4==='e') { petrolScore+=8; cngScore+=7; } else { cngScore+=15; petrolScore+=5; }

            const q5 = document.querySelector('input[name="q5"]:checked').value;
            if(q5==='p') { petrolScore+=20; } else if(q5==='e') { petrolScore+=10; cngScore+=10; } else { cngScore+=20; }

            const q6 = document.querySelector('input[name="q6"]:checked').value;
            if(q6==='p') { petrolScore+=15; } else if(q6==='e') { petrolScore+=7; cngScore+=8; } else { cngScore+=15; }

            const total = petrolScore + cngScore;
            const cngPercent = Math.round((cngScore / total) * 100);
            const petrolPercent = Math.round((petrolScore / total) * 100);

            const resBox = document.getElementById('scoreResult');
            const resScore = document.getElementById('resScoreText');
            const resDesc = document.getElementById('resDescText');

            resBox.style.display = 'block';

            // Sync Monthly Km input to financial tab based on Q1
            const mKmInput = document.getElementById('monthlyKm');
            if(q1==='p') mKmInput.value = 800;
            if(q1==='e') mKmInput.value = 1500;
            if(q1==='c') mKmInput.value = 2500;
            updateDashboard();

            if (cngPercent > petrolPercent) {
                resBox.style.borderColor = 'var(--accent-green)';
                resScore.style.color = 'var(--accent-green)';
                resScore.innerText = `CNG FIT: ${cngPercent}/100`;
                resDesc.innerText = `With your profile, CNG deserves serious consideration. It perfectly aligns with your usage and will deliver maximum long-term value.`;
            } else {
                resBox.style.borderColor = 'var(--accent-blue)';
                resScore.style.color = 'var(--accent-blue)';
                resScore.innerText = `PETROL FIT: ${petrolPercent}/100`;
                resDesc.innerText = `Based on your usage, Petrol may be the more suitable choice. It offers the right blend of convenience, space, and performance for your needs.`;
            }
        }

        // Financial Calculation Logic
        function calculateEMI(principal, annualRate, months) {
            if (principal === 0) return 0;
            const r = annualRate / 12 / 100;
            return (principal * r * Math.pow(1 + r, months)) / (Math.pow(1 + r, months) - 1);
        }

        function computeCosts(variant, monthlyKm, tenureYears) {
            const onRoadPrice = variant.on_road_price;
            let loanAmount = Math.round((onRoadPrice * 0.8) / 100000) * 100000;
            if (loanAmount > onRoadPrice) loanAmount = onRoadPrice;
            const downpayment = onRoadPrice - loanAmount;
            
            const tenureMonths = tenureYears * 12;
            const emi = calculateEMI(loanAmount, 8.5, tenureMonths);
            const totalEmi = emi * tenureMonths;
            
            const totalKm = monthlyKm * 12 * tenureYears; 
            const fuelCost = (totalKm / variant.mileage) * variant.fuel_price;
            const monthlyFuelCost = fuelCost / tenureMonths;

            const vehicleCapitalCost = downpayment + totalEmi;
            const totalCost = vehicleCapitalCost + fuelCost;
            
            return { onRoadPrice, loanAmount, downpayment, emi, totalEmi, vehicleCapitalCost, fuelCost, monthlyFuelCost, totalCost };
        }

        function animateValue(obj, start, end, duration) {
            let startTimestamp = null;
            const step = (timestamp) => {
                if (!startTimestamp) startTimestamp = timestamp;
                const progress = Math.min((timestamp - startTimestamp) / duration, 1);
                const easeProgress = 1 - Math.pow(1 - progress, 4);
                obj.innerHTML = formatCurrency(Math.floor(easeProgress * (end - start) + start));
                if (progress < 1) window.requestAnimationFrame(step);
            };
            window.requestAnimationFrame(step);
        }

        function updateDashboard() {
            const idxA = document.getElementById('variantA').value;
            const idxB = document.getElementById('variantB').value;
            const monthlyKm = parseFloat(document.getElementById('monthlyKm').value) || 0;
            const tenureYears = parseInt(document.getElementById('tenure').value) || 5;

            if (idxA === "" || idxB === "") return;

            document.querySelectorAll('.dyn-tenure').forEach(el => el.innerText = tenureYears);

            const varA = variantsData[idxA];
            const varB = variantsData[idxB];
            const costA = computeCosts(varA, monthlyKm, tenureYears);
            const costB = computeCosts(varB, monthlyKm, tenureYears);

            // Populate Specs A
            const isCngA = varA.variant.includes('CNG');
            document.getElementById('mileageA').innerText = `${varA.mileage} ${isCngA ? 'Km/Kg' : 'Km/L'}`;
            document.getElementById('fuelRateA').innerText = `${formatCurrency(varA.fuel_price)} ${isCngA ? '/ Kg' : '/ L'}`;
            document.getElementById('nameA').innerText = varA.variant;
            document.getElementById('priceA').innerText = formatCurrency(costA.onRoadPrice);
            document.getElementById('loanA').innerText = formatCurrency(costA.loanAmount);
            document.getElementById('downA').innerText = formatCurrency(costA.downpayment);
            document.getElementById('emiA').innerText = formatCurrency(costA.emi);
            document.getElementById('totalEmiA').innerText = formatCurrency(costA.totalEmi);
            document.getElementById('fuelA').innerText = formatCurrency(costA.fuelCost);
            animateValue(document.getElementById('totalCostA'), 0, costA.totalCost, 1000);

            // Populate Specs B
            const isCngB = varB.variant.includes('CNG');
            document.getElementById('mileageB').innerText = `${varB.mileage} ${isCngB ? 'Km/Kg' : 'Km/L'}`;
            document.getElementById('fuelRateB').innerText = `${formatCurrency(varB.fuel_price)} ${isCngB ? '/ Kg' : '/ L'}`;
            document.getElementById('nameB').innerText = varB.variant;
            document.getElementById('priceB').innerText = formatCurrency(costB.onRoadPrice);
            document.getElementById('loanB').innerText = formatCurrency(costB.loanAmount);
            document.getElementById('downB').innerText = formatCurrency(costB.downpayment);
            document.getElementById('emiB').innerText = formatCurrency(costB.emi);
            document.getElementById('totalEmiB').innerText = formatCurrency(costB.totalEmi);
            document.getElementById('fuelB').innerText = formatCurrency(costB.fuelCost);
            animateValue(document.getElementById('totalCostB'), 0, costB.totalCost, 1000);

            // Break-Even Meter Logic
            const beMeter = document.getElementById('breakEvenMeter');
            document.getElementById('be-driving').innerText = `${monthlyKm} km/month`;

            // Identify which car is more expensive to buy (Investment) but cheaper to run
            let invCar = null, baseCar = null;
            if (costA.onRoadPrice > costB.onRoadPrice && costA.monthlyFuelCost < costB.monthlyFuelCost) {
                invCar = {name: varA.variant, cost: costA}; baseCar = {name: varB.variant, cost: costB};
            } else if (costB.onRoadPrice > costA.onRoadPrice && costB.monthlyFuelCost < costA.monthlyFuelCost) {
                invCar = {name: varB.variant, cost: costB}; baseCar = {name: varA.variant, cost: costA};
            }

            if (invCar && baseCar) {
                const extraInvest = invCar.cost.onRoadPrice - baseCar.cost.onRoadPrice;
                const monthlySave = baseCar.cost.monthlyFuelCost - invCar.cost.monthlyFuelCost;
                const beMonths = Math.ceil(extraInvest / monthlySave);
                const beKm = Math.ceil(beMonths * monthlyKm);

                document.getElementById('be-invest').innerText = formatCurrency(extraInvest);
                document.getElementById('be-saving').innerText = `${formatCurrency(monthlySave)} / month`;
                
                let timeStr = beMonths > 12 ? `${Math.floor(beMonths/12)} Yrs & ${beMonths%12} Mos` : `${beMonths} Months`;
                document.getElementById('be-result').innerText = `${timeStr} (${beKm.toLocaleString('en-IN')} km)`;
                beMeter.style.display = 'block';
            } else {
                beMeter.style.display = 'none'; // Hide if no valid break-even scenario exists
            }

            // Total System Difference & FD calculation
            const diff = costA.totalCost - costB.totalCost;
            const absDiff = Math.abs(diff);
            const fdPrincipal = Math.abs(costA.vehicleCapitalCost - costB.vehicleCapitalCost);
            const fdMaturity = fdPrincipal * Math.pow(1 + (0.07 / 4), 4 * tenureYears);

            const savingsBox = document.getElementById('savingsBox');
            savingsBox.classList.remove('savings-neutral');
            
            if (diff !== 0) {
                let winner = diff > 0 ? varB.variant : varA.variant;
                savingsBox.innerHTML = `
                    <span style="font-family: 'Rajdhani', sans-serif; font-size: 0.6em; color: var(--text-light); text-transform: uppercase;">Most Cost-Effective Choice:</span><br>
                    <span style="color:#ffffff;">${winner}</span><br>
                    <span style="font-family: 'Rajdhani', sans-serif; font-size: 0.6em; color:var(--text-light); letter-spacing: 2px; margin-top: 15px; display: inline-block;">NET SAVINGS OVER ${tenureYears} YEARS</span>
                    <span class="savings-amount">${formatCurrency(absDiff)}</span>
                `;
                savingsBox.style.borderColor = 'var(--accent-green)';
                savingsBox.style.color = 'var(--accent-green)';
            } else {
                savingsBox.innerHTML = `EQUAL VALUE<br><span style="font-family: 'Rajdhani', sans-serif; font-size:0.6em; color:#ffffff;">No cost difference over ${tenureYears} years</span>`;
                savingsBox.classList.add('savings-neutral');
            }
        }

        window.onload = () => {
            const selectA = document.getElementById('variantA');
            const selectB = document.getElementById('variantB');
            variantsData.forEach((variant, index) => {
                selectA.add(new Option(variant.variant, index));
                selectB.add(new Option(variant.variant, index));
            });
            if(variantsData.length > 1) { selectA.selectedIndex = 0; selectB.selectedIndex = 7; }

            selectA.addEventListener('change', updateDashboard);
            selectB.addEventListener('change', updateDashboard);
            document.getElementById('monthlyKm').addEventListener('input', updateDashboard);
            document.getElementById('tenure').addEventListener('change', updateDashboard);
            updateDashboard(); 
        };
    </script>
</body>
</html>