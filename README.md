
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Sahi Fuel Chuna Kya?</title>
    <style>
        /* Premium Fonts Setup */
        @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@500;700;800&family=Outfit:wght@300;400;500;600;700;800&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Outfit', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        :root {
            /* Premium Light Theme */
            --bg-color: #f4f6f9;
            --card-bg: #ffffff;
            --border-light: #e5e9f0;
            
            /* Premium Dark Theme for "Serious" Cards */
            --dark-card-bg: #0f141e;
            --dark-card-border: #1f2937;
            --dark-text-muted: #8b9bb4;

            /* Text Colors */
            --text-main: #111827;
            --text-muted: #6b7280;
            
            /* Brand Accents */
            --nexa-blue: #1d4ed8;
            --nexa-blue-light: #eff6ff;
            --positive-green: #10b981;
            --positive-green-bg: #ecfdf5;
            --serious-red: #ef4444;
            --serious-red-bg: rgba(239, 68, 68, 0.1);
        }

        body {
            background-color: var(--bg-color);
            background-image: radial-gradient(circle at 50% 0%, #ffffff 0%, transparent 100%);
            color: var(--text-main);
            padding: 30px 15px 80px 15px;
            display: flex;
            justify-content: center;
            min-height: 100vh;
        }

        .top-logo-container {
            position: absolute;
            top: 25px;
            left: 30px;
            z-index: 100;
            font-weight: 800;
            font-size: 1.3rem;
            letter-spacing: 3px;
            color: var(--text-main);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .top-logo-container::before {
            content: '';
            display: inline-block;
            width: 4px;
            height: 20px;
            background: var(--text-main);
            border-radius: 2px;
        }

        .app-container {
            width: 100%;
            max-width: 520px;
            display: flex;
            flex-direction: column;
            gap: 28px;
            margin-top: 50px;
        }

        .header-section {
            text-align: center;
            margin-bottom: 5px;
        }

        .header-section h1 {
            font-size: 2.5rem;
            font-weight: 800;
            color: var(--text-main);
            letter-spacing: -1px;
            margin-bottom: 8px;
        }

        .header-section p {
            font-size: 1rem;
            color: var(--text-muted);
            font-weight: 400;
            letter-spacing: 0.5px;
        }

        /* --- CARDS --- */
        .card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-light);
            border-radius: 24px;
            padding: 32px;
            display: flex;
            flex-direction: column;
            gap: 24px;
            box-shadow: 0 20px 40px -15px rgba(0,0,0,0.05);
        }

        .serious-card {
            background-color: var(--dark-card-bg);
            border: 1px solid var(--dark-card-border);
            color: #ffffff;
            box-shadow: 0 25px 50px -12px rgba(0,0,0,0.25);
        }

        .card-title-group p {
            color: var(--text-muted);
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            font-weight: 700;
            text-align: center;
        }

        .serious-card .card-title-group p {
            color: var(--dark-text-muted);
        }

        .card-title-group h2 {
            font-size: 1.5rem;
            font-weight: 800;
            letter-spacing: -0.5px;
            color: var(--text-main);
            text-align: center;
            margin-top: 8px;
        }

        .serious-card .card-title-group h2 {
            color: #ffffff;
        }

        /* --- INPUTS --- */
        .input-box {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .input-box label {
            font-size: 0.9rem;
            color: var(--text-main);
            font-weight: 600;
        }

        .custom-input {
            background: #f8fafc;
            border: 1px solid var(--border-light);
            color: var(--text-main);
            padding: 16px;
            border-radius: 14px;
            font-size: 1.05rem;
            font-weight: 500;
            outline: none;
            width: 100%;
            transition: 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            appearance: none;
        }

        .custom-input:focus {
            border-color: var(--nexa-blue);
            background: #ffffff;
            box-shadow: 0 0 0 4px var(--nexa-blue-light);
        }

        select.custom-input {
            background-image: url("data:image/svg+xml,%3Csvg width='12' height='8' viewBox='0 0 12 8' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 1.5L6 6.5L11 1.5' stroke='%2364748b' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 16px center;
            cursor: pointer;
        }

        .input-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
        }

        /* --- SEGMENTED CONTROLS (PILLS) --- */
        .question-block {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .question-label {
            font-size: 0.95rem;
            color: var(--text-main);
            font-weight: 600;
        }

        .pill-group {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        .pill-label {
            flex: 1;
            min-width: 30%;
            position: relative;
        }

        .pill-label input { display: none; }

        .pill-text {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 52px;
            background: #f8fafc;
            border: 1px solid var(--border-light);
            border-radius: 14px;
            color: var(--text-muted);
            font-size: 0.95rem;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            text-align: center;
            padding: 0 8px;
            line-height: 1.2;
        }

        .pill-label input:checked + .pill-text {
            background: var(--positive-green-bg);
            border-color: var(--positive-green);
            color: #059669; /* Darker green for text readability */
            font-weight: 700;
            box-shadow: 0 4px 15px rgba(16, 185, 129, 0.15);
        }

        /* --- BUTTONS --- */
        .btn-primary {
            background: var(--text-main);
            color: #ffffff;
            border: none;
            padding: 18px;
            border-radius: 16px;
            font-size: 1.1rem;
            font-weight: 700;
            letter-spacing: 0.5px;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 10px 25px rgba(17, 24, 39, 0.2);
            margin-top: 10px;
        }
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 15px 30px rgba(17, 24, 39, 0.3);
        }

        .btn-secondary {
            background: transparent;
            color: var(--text-muted);
            border: 1px solid var(--border-light);
            padding: 16px;
            border-radius: 16px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
        }
        .btn-secondary:hover {
            background: #f8fafc;
            color: var(--text-main);
            border-color: #cbd5e1;
        }

        /* --- DIAGNOSTIC GAUGE --- */
        .gauge-container {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .gauge-svg {
            width: 100%;
            max-width: 280px;
            overflow: visible;
        }

        .gauge-text-container {
            text-align: center;
            margin-top: 15px;
        }

        .gauge-score {
            font-family: 'JetBrains Mono', monospace;
            font-size: 4rem;
            font-weight: 800;
            line-height: 1;
            color: var(--text-main);
            letter-spacing: -3px;
        }

        .gauge-subtext {
            color: var(--text-muted);
            font-size: 0.95rem;
            font-weight: 500;
            margin-bottom: 15px;
        }

        .gauge-result-badge {
            padding: 10px 20px;
            border-radius: 12px;
            font-size: 0.95rem;
            font-weight: 800;
            display: inline-block;
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        /* --- SERIOUS FINANCIALS --- */
        .cost-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 16px;
        }

        .cost-label {
            font-size: 0.95rem;
            color: var(--dark-text-muted);
            font-weight: 500;
        }

        .cost-value {
            font-family: 'JetBrains Mono', monospace;
            font-size: 1.1rem;
            font-weight: 700;
            color: #ffffff;
        }

        .cost-divider {
            border-top: 1px dashed var(--dark-card-border);
            margin: 20px 0;
        }

        .total-cost-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(0,0,0,0.3);
            padding: 20px;
            border-radius: 16px;
            border: 1px solid rgba(255,255,255,0.05);
        }

        .total-cost-label {
            font-size: 1rem;
            color: var(--dark-text-muted);
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .total-cost-value {
            font-family: 'JetBrains Mono', monospace;
            font-size: 1.6rem;
            font-weight: 800;
            color: var(--serious-red); /* Stark red for serious tone */
        }

        /* --- ODOMETER (PREMIUM REALISTIC) --- */
        .odometer-section {
            text-align: center;
            padding: 30px 0 10px 0;
            background: #080b11; /* Even darker inner core */
            border-radius: 16px;
            border: 1px inset rgba(255,255,255,0.05);
            margin-top: 10px;
        }

        .odometer-display {
            display: flex;
            justify-content: center;
            gap: 4px;
            margin-bottom: 20px;
        }

        .odo-digit {
            background: linear-gradient(180deg, #111827 0%, #030712 50%, #111827 100%);
            color: #ffffff;
            font-family: 'Space Mono', monospace;
            font-size: 2.8rem;
            font-weight: 700;
            width: 52px;
            height: 72px;
            border-radius: 6px;
            border: 1px solid #1f2937;
            box-shadow: inset 0 5px 15px rgba(0,0,0,1), 0 2px 5px rgba(0,0,0,0.5);
            overflow: hidden;
            position: relative;
        }
        
        /* Glossy overlay for realism */
        .odo-digit::after {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0; height: 40%;
            background: linear-gradient(180deg, rgba(255,255,255,0.1) 0%, transparent 100%);
            pointer-events: none;
        }

        .odo-roller {
            display: flex;
            flex-direction: column;
            height: 1000%; 
            transition: transform 2s cubic-bezier(0.22, 1, 0.36, 1);
        }

        .odo-number {
            height: 10%;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* --- SERIOUS TIME TEXT --- */
        .serious-time-box {
            text-align: center;
            margin-top: 25px;
            padding: 20px;
            border-radius: 16px;
            background: rgba(239, 68, 68, 0.05); /* Slight red tint */
            border: 1px solid rgba(239, 68, 68, 0.2);
        }

        .serious-time-val {
            font-family: 'JetBrains Mono', monospace;
            font-size: 3.5rem;
            font-weight: 800;
            color: var(--serious-red);
            line-height: 1;
            margin: 10px 0;
            letter-spacing: -2px;
        }

        /* --- UTILS & ANIMATIONS --- */
        .hidden { display: none !important; }
        
        /* Elegant Staggered Display */
        @keyframes elegantFadeUp {
            0% { opacity: 0; transform: translateY(40px) scale(0.98); }
            100% { opacity: 1; transform: translateY(0) scale(1); }
        }

        .reveal-container { display: flex; flex-direction: column; gap: 24px; }
        .reveal-1 { animation: elegantFadeUp 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards; opacity: 0; }
        .reveal-2 { animation: elegantFadeUp 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.3s forwards; opacity: 0; }
        .reveal-3 { animation: elegantFadeUp 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.6s forwards; opacity: 0; }
        .reveal-4 { animation: elegantFadeUp 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.9s forwards; opacity: 0; }

        @media (max-width: 600px) {
            .top-logo-container { position: relative; top: 0; left: 0; display: flex; justify-content: center; margin-bottom: 5px; width: 100%;}
            .app-container { margin-top: 10px;}
            .odo-digit { width: 42px; height: 60px; font-size: 2.2rem; }
            .header-section h1 { font-size: 2rem; }
        }

    </style>
</head>
<body>

<div class="top-logo-container">
    NEXA
</div>

<div class="app-container">

    <div class="header-section">
        <h1>Sahi Fuel Chuna Kya?</h1>
        <p id="sub-header-text">Configure your profile below</p>
    </div>

    <!-- ================= PART 1: INPUT QUESTIONNAIRE ================= -->
    <div id="part1">
        <div class="card">
            
            <div class="input-grid">
                <div class="input-box">
                    <label>Petrol Variant</label>
                    <select id="variantA" class="custom-input"></select>
                </div>
                <div class="input-box">
                    <label>CNG Variant</label>
                    <select id="variantB" class="custom-input"></select>
                </div>
            </div>

            <div class="input-grid">
                <div class="input-box">
                    <label>Petrol Price (₹/L)</label>
                    <input type="number" id="petrolPriceInput" class="custom-input" value="104">
                </div>
                <div class="input-box">
                    <label>CNG Price (₹/kg)</label>
                    <input type="number" id="cngPriceInput" class="custom-input" value="89">
                </div>
            </div>

            <div class="input-box">
                <label>Daily driving (km)</label>
                <input type="number" id="dailyDrivingInput" class="custom-input" value="80">
            </div>

            <div class="question-block" style="margin-top: 5px;">
                <div class="question-label">Boot space importance</div>
                <div class="pill-group">
                    <label class="pill-label"><input type="radio" name="q_boot" value="0"><div class="pill-text">Very<br>important</div></label>
                    <label class="pill-label"><input type="radio" name="q_boot" value="50"><div class="pill-text">Somewhat</div></label>
                    <label class="pill-label"><input type="radio" name="q_boot" value="100" checked><div class="pill-text">Not<br>important</div></label>
                </div>
            </div>

            <div class="question-block">
                <div class="question-label">Driving preference</div>
                <div class="pill-group">
                    <label class="pill-label"><input type="radio" name="q_pref" value="0"><div class="pill-text">Performance</div></label>
                    <label class="pill-label"><input type="radio" name="q_pref" value="50"><div class="pill-text">Balanced</div></label>
                    <label class="pill-label"><input type="radio" name="q_pref" value="100" checked><div class="pill-text">Economy</div></label>
                </div>
            </div>

            <div class="question-block">
                <div class="question-label">CNG station convenience</div>
                <div class="pill-group">
                    <label class="pill-label"><input type="radio" name="q_stn" value="0"><div class="pill-text">Inconvenient</div></label>
                    <label class="pill-label"><input type="radio" name="q_stn" value="50"><div class="pill-text">Manageable</div></label>
                    <label class="pill-label"><input type="radio" name="q_stn" value="100" checked><div class="pill-text">Easy access</div></label>
                </div>
            </div>

            <div class="question-block">
                <div class="question-label">Expected ownership</div>
                <div class="pill-group">
                    <label class="pill-label"><input type="radio" name="q_own" value="0"><div class="pill-text">≤ 3 years</div></label>
                    <label class="pill-label"><input type="radio" name="q_own" value="50"><div class="pill-text">4–5 years</div></label>
                    <label class="pill-label"><input type="radio" name="q_own" value="100" checked><div class="pill-text">6+ years</div></label>
                </div>
            </div>

            <button class="btn-primary" onclick="generateReport()">Generate Analysis Matrix</button>
        </div>
    </div>

    <!-- ================= PART 2: RESULTS ================= -->
    <div id="part2" class="hidden reveal-container">
        
        <!-- 1. SUITABILITY METER -->
        <div class="card reveal-1">
            <div class="card-title-group">
                <p>Diagnostic Result</p>
                <h2>CNG Suitability Meter</h2>
            </div>
            <div class="gauge-container" style="margin-top: 0;">
                <svg class="gauge-svg" viewBox="0 0 200 110">
                    <defs>
                        <linearGradient id="score-grad" x1="0%" y1="0%" x2="100%" y2="0%">
                            <stop offset="0%" stop-color="#ef4444" />
                            <stop offset="50%" stop-color="#3b82f6" />
                            <stop offset="100%" stop-color="#10b981" />
                        </linearGradient>
                    </defs>
                    <path d="M 20 100 A 80 80 0 0 1 180 100" fill="none" stroke="var(--gauge-bg)" stroke-width="16" stroke-linecap="round"/>
                    <path d="M 20 100 A 80 80 0 0 1 180 100" fill="none" stroke="url(#score-grad)" stroke-width="16" stroke-linecap="round"/>
                    
                    <text x="20" y="105" fill="var(--text-muted)" font-size="10" text-anchor="middle" font-weight="700">0</text>
                    <text x="180" y="105" fill="var(--text-muted)" font-size="10" text-anchor="middle" font-weight="700">100</text>
                    
                    <!-- Needle -->
                    <g id="score-needle" style="transform-origin: 100px 100px; transform: rotate(-90deg); transition: transform 2s cubic-bezier(0.34, 1.56, 0.64, 1);">
                        <circle cx="100" cy="100" r="8" fill="#111827"/>
                        <polygon points="96,100 104,100 100,25" fill="#111827"/>
                    </g>
                </svg>

                <div class="gauge-text-container">
                    <div class="gauge-score" id="score-val">0</div>
                    <div class="gauge-result-badge" id="score-badge">-</div>
                </div>
            </div>
        </div>

        <!-- 2. ADDITIONAL COST (SERIOUS CARD) -->
        <div class="card serious-card reveal-2" id="extra-cost-card">
            <div class="card-title-group">
                <p>Investment Breakdown</p>
                <h2>Additional Cost for CNG</h2>
            </div>
            
            <div id="extra-cost-container" style="margin-top: 10px;">
                <div class="cost-row">
                    <span class="cost-label">Difference in On-Road Price</span>
                    <span class="cost-value" id="orp-diff-val">₹0</span>
                </div>
                <div class="cost-row">
                    <span class="cost-label">Additional EMI Interest (5 Yrs)</span>
                    <span class="cost-value" id="int-diff-val">₹0</span>
                </div>
                
                <div class="cost-divider"></div>
                
                <div class="total-cost-row">
                    <span class="total-cost-label">Total Extra Debt</span>
                    <span class="total-cost-value" id="total-extra-val">0</span>
                </div>
            </div>

            <div id="no-cost-msg" class="hidden" style="text-align: center; color: var(--dark-text-muted); font-weight: 500; border: 1px solid rgba(255,255,255,0.1); padding: 20px; border-radius: 12px;">
                CNG variant is equally or less priced than Petrol. No extra investment required.
            </div>
        </div>

        <!-- 3. SAVINGS START AFTER (SERIOUS CARD) -->
        <div class="card serious-card reveal-3" id="break-even-card">
            <div class="card-title-group">
                <p style="color: #f87171;">No Savings Upto:</p>
            </div>

            <!-- ODOMETER -->
            <div class="odometer-section">
                <div class="odometer-title">Distance Required</div>
                <div class="odometer-display" id="odometer">
                    <!-- Dynamically generated by setupOdometer() -->
                </div>
                <div style="font-size: 0.85rem; color: var(--dark-text-muted); font-weight: 600; text-transform: uppercase; letter-spacing: 2px;">Kilometres</div>
            </div>

            <!-- SERIOUS TIME TEXT -->
            <div class="serious-time-box">
                <p style="font-size: 0.8rem; text-transform: uppercase; letter-spacing: 2px; color: var(--dark-text-muted); font-weight: 700;">Time Required</p>
                <div class="serious-time-val" id="time-text-val">0.0 <span style="font-size: 1.2rem; font-weight: 600; color: var(--dark-text-muted);">Yrs</span></div>
                <div id="time-text-desc" style="font-size: 1rem; font-weight: 600; margin-top: 5px; color: var(--dark-text-muted);">-</div>
            </div>
        </div>

        <button class="btn-secondary reveal-4" onclick="goBack()">Recalculate Details</button>
    </div>

</div>

<script>
    const variantsData = [{"variant": "BALENO SIGMA 1.2L 5MT", "on_road_price": 681390, "mileage": 22.35}, {"variant": "BALENO DELTA 1.2L 5MT", "on_road_price": 785420, "mileage": 22.35}, {"variant": "BALENO ZETA 1.2L 5MT", "on_road_price": 892854, "mileage": 22.35}, {"variant": "BALENO ALPHA 1.2L 5MT", "on_road_price": 1014079, "mileage": 22.35}, {"variant": "BALENO DELTA CNG 1.2L 5MT", "on_road_price": 891054, "mileage": 30.61}, {"variant": "BALENO ZETA CNG 1.2L 5MT", "on_road_price": 998923, "mileage": 30.61}, {"variant": "FRONX SIGMA 1.2L 5MT", "on_road_price": 776637, "mileage": 21.79}, {"variant": "FRONX DELTA 1.2L 5MT", "on_road_price": 875783, "mileage": 21.79}, {"variant": "FRONX SIGMA CNG 1.2L 5MT", "on_road_price": 891941, "mileage": 28.51}, {"variant": "FRONX DELTA CNG 1.2L 5MT", "on_road_price": 985637, "mileage": 28.51}, {"variant": "GRAND VITARA DELTA 1.5L 5MT", "on_road_price": 1398900, "mileage": 21.11}, {"variant": "GRAND VITARA DELTA CNG 1.5L 5MT", "on_road_price": 1496002, "mileage": 26.6}, {"variant": "XL6 ZETA 1.5L 5MT", "on_road_price": 1336091, "mileage": 20.97}, {"variant": "XL6 ZETA CNG 1.5L 5MT", "on_road_price": 1447048, "mileage": 26.32}];

    const formatCurrency = (val) => '₹' + new Intl.NumberFormat('en-IN', { maximumFractionDigits: 0 }).format(val);

    function setupDropdowns() {
        const selectA = document.getElementById('variantA');
        const selectB = document.getElementById('variantB');
        
        let cngIndex = -1, petrolIndex = -1;

        variantsData.forEach((variant, index) => {
            if(!variant.variant.includes('CNG')) {
                selectA.add(new Option(variant.variant, index));
                if(petrolIndex === -1 && variant.variant.includes('BALENO DELTA')) petrolIndex = index;
            } else {
                selectB.add(new Option(variant.variant, index));
                if(cngIndex === -1 && variant.variant.includes('BALENO DELTA CNG')) cngIndex = index;
            }
        });

        selectA.value = petrolIndex !== -1 ? petrolIndex : 0;
        selectB.value = cngIndex !== -1 ? cngIndex : 0;
    }

    function setupOdometer() {
        const odoContainer = document.getElementById('odometer');
        odoContainer.innerHTML = '';
        for(let i=0; i<6; i++) {
            let columnHTML = `<div class="odo-digit"><div class="odo-roller" id="odo-${i}">`;
            for(let j=0; j<10; j++) {
                columnHTML += `<div class="odo-number">${j}</div>`;
            }
            columnHTML += `</div></div>`;
            odoContainer.innerHTML += columnHTML;
        }
    }

    function updateOdometerDisplay(numberStr) {
        const padded = numberStr.padStart(6, '0');
        for(let i=0; i<6; i++) {
            const digit = parseInt(padded[i]);
            const roller = document.getElementById(`odo-${i}`);
            if(roller) {
                roller.style.transition = 'none';
                roller.style.transform = `translateY(0%)`;
                
                void roller.offsetWidth; // Reflow

                roller.style.transition = `transform 2.5s cubic-bezier(0.22, 1, 0.36, 1) ${0.8 + (i * 0.15)}s`;
                roller.style.transform = `translateY(-${digit * 10}%)`;
            }
        }
    }

    // Elegant Number Counter Animation
    function animateValue(obj, start, end, duration, formatAsCurrency = false, isFloat = false) {
        let startTimestamp = null;
        const step = (timestamp) => {
            if (!startTimestamp) startTimestamp = timestamp;
            const progress = Math.min((timestamp - startTimestamp) / duration, 1);
            // Ease out cubic
            const easeProgress = 1 - Math.pow(1 - progress, 3);
            const currentVal = (easeProgress * (end - start) + start);
            
            if (formatAsCurrency) {
                obj.innerHTML = formatCurrency(Math.floor(currentVal));
            } else if (isFloat) {
                obj.innerHTML = `${currentVal.toFixed(1)} <span style="font-size: 1.2rem; font-weight: 600; color: var(--dark-text-muted);">Yrs</span>`;
            } else {
                obj.innerHTML = Math.floor(currentVal);
            }

            if (progress < 1) {
                window.requestAnimationFrame(step);
            }
        };
        window.requestAnimationFrame(step);
    }

    function calculateEMI(principal, annualRate, months) {
        if (principal === 0) return 0;
        const r = annualRate / 12 / 100;
        return (principal * r * Math.pow(1 + r, months)) / (Math.pow(1 + r, months) - 1);
    }

    function generateReport() {
        // Switch views
        document.getElementById('part1').classList.add('hidden');
        
        // Remove and re-add class to restart CSS reveal animations
        const part2 = document.getElementById('part2');
        part2.classList.remove('hidden');
        part2.classList.remove('fade-in');
        void part2.offsetWidth; // Reflow
        part2.classList.add('fade-in');

        document.getElementById('sub-header-text').innerText = "Matrix Analytics Report";
        
        // Reset gauges visually to 0 before calculating
        document.getElementById('score-needle').style.transform = `rotate(-90deg)`;
        updateOdometerDisplay("0");

        // Small delay to allow display:block to render before calculating height/transitions
        setTimeout(() => {
            runCalculations();
        }, 100);
    }

    function goBack() {
        document.getElementById('part2').classList.add('hidden');
        document.getElementById('part1').classList.remove('hidden');
        document.getElementById('sub-header-text').innerText = "Configure your profile below";
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function runCalculations() {
        // --- 1. CALCULATE PROFILE SCORE ---
        let score = 0;
        const dailyKm = parseFloat(document.getElementById('dailyDrivingInput').value) || 0;
        const monthlyKmEquiv = dailyKm * 30; 
        
        if (monthlyKmEquiv <= 500) score += 0;
        else if (monthlyKmEquiv <= 1000) score += 5; 
        else if (monthlyKmEquiv <= 2000) score += 12; 
        else score += 25;

        const q2 = parseInt(document.querySelector('input[name="q_boot"]:checked').value);
        if (q2 === 0) score += 0; else if (q2 === 50) score += 4; else score += 15;

        const q3 = parseInt(document.querySelector('input[name="q_pref"]:checked').value);
        if (q3 === 0) score += 0; else if (q3 === 50) score += 5; else score += 20;

        const q4 = parseInt(document.querySelector('input[name="q_stn"]:checked').value);
        if (q4 === 0) score += 0; else if (q4 === 50) score += 8; else score += 25;

        const q5 = parseInt(document.querySelector('input[name="q_own"]:checked').value);
        if (q5 === 0) score += 0; else if (q5 === 50) score += 5; else score += 15;

        score = Math.round(score);
        
        // Animate Score Number
        animateValue(document.getElementById('score-val'), 0, score, 1500);
        
        // Animate Needle
        const scoreRotation = -90 + ((score / 100) * 180);
        setTimeout(() => {
            document.getElementById('score-needle').style.transform = `rotate(${scoreRotation}deg)`;
        }, 200);

        const badge = document.getElementById('score-badge');
        setTimeout(() => {
            if(score < 50) {
                badge.innerText = "STRONG PETROL FIT";
                badge.style.color = "#b91c1c";
                badge.style.background = "#fef2f2";
                badge.style.border = "1px solid #fca5a5";
            } else if (score < 80) {
                badge.innerText = "PETROL RECOMMENDED";
                badge.style.color = "#2563eb";
                badge.style.background = "#eff6ff";
                badge.style.border = "1px solid #bfdbfe";
            } else {
                badge.innerText = "CNG FEASIBLE";
                badge.style.color = "#047857";
                badge.style.background = "#ecfdf5";
                badge.style.border = "1px solid #6ee7b7";
            }
        }, 1200);


        // --- 2. CALCULATE ADDITIONAL COST ---
        const idxA = document.getElementById('variantA').value;
        const idxB = document.getElementById('variantB').value;
        const varA = variantsData[idxA];
        const varB = variantsData[idxB];
        
        const yearlyKm = Math.max(dailyKm * 365, 365);
        const pPrice = parseFloat(document.getElementById('petrolPriceInput').value) || 104;
        const cPrice = parseFloat(document.getElementById('cngPriceInput').value) || 89;

        const orpDiff = varB.on_road_price - varA.on_road_price;

        let loanA = Math.round((varA.on_road_price * 0.8) / 100000) * 100000;
        let loanB = Math.round((varB.on_road_price * 0.8) / 100000) * 100000;
        
        if (loanA > varA.on_road_price) loanA = varA.on_road_price;
        if (loanB > varB.on_road_price) loanB = varB.on_road_price;

        let emiA = calculateEMI(loanA, 8.5, 60);
        let emiB = calculateEMI(loanB, 8.5, 60);

        let intA = (emiA * 60) - loanA;
        let intB = (emiB * 60) - loanB;
        if (intA < 0) intA = 0; if (intB < 0) intB = 0;

        const intDiff = intB - intA;
        const totalExtraCost = orpDiff + intDiff;

        const costPerKmA = pPrice / varA.mileage;
        const costPerKmB = cPrice / varB.mileage;
        const savingsPerKm = costPerKmA - costPerKmB;

        const extraCostBox = document.getElementById('extra-cost-container');
        const noCostMsg = document.getElementById('no-cost-msg');
        const breakEvenCard = document.getElementById('break-even-card');

        if(totalExtraCost <= 0) {
            extraCostBox.classList.add('hidden');
            noCostMsg.classList.remove('hidden');
            breakEvenCard.classList.add('hidden');
            return;
        }

        extraCostBox.classList.remove('hidden');
        noCostMsg.classList.add('hidden');
        breakEvenCard.classList.remove('hidden');

        document.getElementById('orp-diff-val').innerText = formatCurrency(orpDiff);
        document.getElementById('int-diff-val').innerText = formatCurrency(intDiff);
        
        // Elegant Number Animation for Total Extra Cost
        setTimeout(() => {
            animateValue(document.getElementById('total-extra-val'), 0, totalExtraCost, 1500, true);
        }, 500);

        // --- 3. BREAK EVEN ---
        if(savingsPerKm > 0) {
            const breakEvenKm = totalExtraCost / savingsPerKm;
            updateOdometerDisplay(Math.round(breakEvenKm).toString());
            
            const breakEvenYears = breakEvenKm / yearlyKm;
            
            setTimeout(() => {
                animateValue(document.getElementById('time-text-val'), 0, breakEvenYears, 2000, false, true);
                
                // Set alarming styling if over 2 years
                const timeDesc = document.getElementById('time-desc');
                const timeValBlock = document.getElementById('time-text-val');
                
                if(breakEvenYears <= 2) { 
                    timeDesc.innerText = "Fast recovery at this running"; 
                    timeValBlock.style.color = "var(--positive-green)";
                } else if (breakEvenYears <= 4.5) {
                    timeDesc.innerText = "Moderate recovery time"; 
                    timeValBlock.style.color = "#f59e0b";
                } else { 
                    timeDesc.innerText = "Severe recovery lag"; 
                    timeValBlock.style.color = "var(--serious-red)"; 
                }
            }, 800);

        } else {
            updateOdometerDisplay("999999");
            document.getElementById('time-text-val').innerHTML = `Never`;
            document.getElementById('time-text-desc').innerText = "CNG is costlier to run";
            document.getElementById('time-text-val').style.color = "var(--serious-red)";
        }
        
        // Scroll slightly down so Results are cleanly in view
        setTimeout(() => {
            window.scrollTo({ top: document.getElementById('part2').offsetTop - 20, behavior: 'smooth' });
        }, 200);
    }

    // --- INIT ---
    window.onload = () => {
        setupOdometer();
        setupDropdowns();
    };

</script>
</body>
</html>