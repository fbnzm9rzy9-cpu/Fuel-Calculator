<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Sahi Chuna Kya - Smart CNG Calculator</title>
    <style>
        /* Modern CSS Reset & Fonts */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Space+Mono:wght@700&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        :root {
            --bg-gradient: linear-gradient(135deg, #f6f8fd 0%, #f1f5f9 100%);
            --card-bg: #ffffff;
            --border-color: #e2e8f0;
            --text-main: #0f172a;
            --text-muted: #64748b;
            --accent-blue: #2563eb;
            --accent-blue-bg: #eff6ff;
            --accent-green: #10b981;
            --accent-red: #ef4444;
            --gauge-bg: #e2e8f0;
        }

        body {
            background: var(--bg-gradient);
            color: var(--text-main);
            padding: 30px 15px 60px 15px;
            display: flex;
            justify-content: center;
            min-height: 100vh;
        }

        .top-logo-container {
            position: absolute;
            top: 25px;
            left: 25px;
            z-index: 100;
        }

        .nexa-logo {
            height: 22px;
            /* Filters to dark for light theme */
            filter: brightness(0) opacity(0.8);
        }

        .app-container {
            width: 100%;
            max-width: 500px;
            display: flex;
            flex-direction: column;
            gap: 24px;
            margin-top: 30px;
        }

        .header-section {
            text-align: center;
            margin-bottom: 10px;
        }

        .header-section h1 {
            font-size: 2rem;
            font-weight: 700;
            color: var(--text-main);
            letter-spacing: -0.5px;
            margin-bottom: 5px;
        }

        .header-section p {
            font-size: 0.95rem;
            color: var(--text-muted);
            font-weight: 500;
        }

        /* --- CARDS --- */
        .card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 24px;
            padding: 28px;
            display: flex;
            flex-direction: column;
            gap: 24px;
            box-shadow: 0 12px 36px -12px rgba(0,0,0,0.08);
        }

        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-end;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 16px;
            margin-bottom: 4px;
        }

        .card-title-group p {
            color: var(--text-muted);
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-weight: 600;
            margin-bottom: 6px;
        }

        .card-title-group h2 {
            font-size: 1.4rem;
            font-weight: 700;
            letter-spacing: -0.5px;
            color: var(--text-main);
        }

        .reset-btn {
            background: #f8fafc;
            border: 1px solid var(--border-color);
            color: var(--text-muted);
            padding: 8px 14px;
            border-radius: 10px;
            font-size: 0.85rem;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
        }
        .reset-btn:hover { background: #e2e8f0; color: var(--text-main); }

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

        .pill-label input {
            display: none;
        }

        .pill-text {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 48px;
            background: #f8fafc;
            border: 1px solid var(--border-color);
            border-radius: 12px;
            color: var(--text-muted);
            font-size: 0.9rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
            text-align: center;
            padding: 0 8px;
            line-height: 1.2;
        }

        .pill-label input:checked + .pill-text {
            background: var(--accent-blue-bg);
            border-color: var(--accent-blue);
            color: var(--accent-blue);
            box-shadow: 0 4px 12px rgba(37, 99, 235, 0.15);
        }

        /* --- GAUGES --- */
        .gauge-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-top: 10px;
        }

        .gauge-svg {
            width: 100%;
            max-width: 280px;
            overflow: visible;
        }

        .gauge-text-container {
            text-align: center;
            margin-top: -30px;
        }

        .gauge-score {
            font-size: 3.5rem;
            font-weight: 800;
            line-height: 1;
            color: var(--text-main);
            letter-spacing: -1.5px;
        }

        .gauge-subtext {
            color: var(--text-muted);
            font-size: 0.9rem;
            font-weight: 500;
            margin-bottom: 10px;
        }

        .gauge-result-badge {
            padding: 8px 16px;
            border-radius: 10px;
            font-size: 0.9rem;
            font-weight: 700;
            margin-top: 15px;
            display: inline-block;
            letter-spacing: 0.5px;
        }

        /* --- CALCULATOR INPUTS --- */
        .variant-selectors {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 10px;
        }

        .input-box {
            display: flex;
            flex-direction: column;
            gap: 8px;
            margin-bottom: 15px;
        }

        .input-box label {
            font-size: 0.85rem;
            color: var(--text-muted);
            font-weight: 600;
        }

        .custom-input {
            background: #f8fafc;
            border: 1px solid var(--border-color);
            color: var(--text-main);
            padding: 14px 16px;
            border-radius: 12px;
            font-size: 1rem;
            font-weight: 500;
            outline: none;
            width: 100%;
            transition: 0.2s;
            appearance: none;
        }

        .custom-input:focus {
            border-color: var(--accent-blue);
            background: #ffffff;
            box-shadow: 0 0 0 4px rgba(37, 99, 235, 0.1);
        }

        select.custom-input {
            background-image: url("data:image/svg+xml,%3Csvg width='12' height='8' viewBox='0 0 12 8' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 1.5L6 6.5L11 1.5' stroke='%2364748b' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 16px center;
            padding-right: 40px;
            cursor: pointer;
        }

        .calc-subtitle {
            font-size: 0.9rem;
            color: var(--text-muted);
            margin-bottom: 20px;
            line-height: 1.5;
            text-align: center;
        }

        .calc-subtitle strong { color: var(--text-main); }

        /* --- ODOMETER --- */
        .odometer-section {
            text-align: center;
            margin: 20px 0;
            padding: 25px 0;
            border-top: 1px dashed var(--border-color);
            border-bottom: 1px dashed var(--border-color);
            background: #f8fafc;
            border-radius: 16px;
        }

        .odometer-title {
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            color: var(--text-muted);
            margin-bottom: 12px;
            font-weight: 700;
        }

        .odometer-display {
            display: flex;
            justify-content: center;
            gap: 6px;
            margin-bottom: 12px;
        }

        .odo-digit {
            background: #0f172a;
            color: #ffffff;
            font-family: 'Space Mono', monospace;
            font-size: 2.5rem;
            font-weight: 700;
            padding: 10px 14px;
            border-radius: 8px;
            border: 2px solid #334155;
            box-shadow: inset 0 2px 8px rgba(0,0,0,0.6), 0 4px 10px rgba(0,0,0,0.1);
            line-height: 1;
        }

        .odo-sub {
            font-size: 0.9rem;
            color: var(--text-muted);
            font-weight: 500;
            margin-bottom: 15px;
        }

        .savings-highlight {
            font-size: 1rem;
            font-weight: 500;
            color: var(--text-main);
        }
        .savings-highlight span {
            color: var(--accent-green);
            font-weight: 700;
        }

        @media (max-width: 600px) {
            .top-logo-container { position: relative; top: 0; left: 0; display: flex; justify-content: center; margin-bottom: 10px; width: 100%;}
            .app-container { margin-top: 10px;}
        }

    </style>
</head>
<body>

<div class="top-logo-container">
    <img src="https://upload.wikimedia.org/wikipedia/commons/4/4e/Nexa_logo.svg" alt="NEXA Logo" class="nexa-logo">
</div>

<div class="app-container">

    <div class="header-section">
        <h1>Sahi Chuna Kya</h1>
        <p>Interactive Diagnostics & Financial Calculator</p>
    </div>

    <!-- CARD 1: CUSTOMER PROFILE -->
    <div class="card">
        <div class="card-header">
            <div class="card-title-group">
                <p>Customer Profile</p>
                <h2>What matters to you?</h2>
            </div>
            <button class="reset-btn" onclick="resetProfile()">Reset</button>
        </div>

        <div class="question-block">
            <div class="question-label">Monthly driving</div>
            <div class="pill-group">
                <label class="pill-label"><input type="radio" name="q_drive" value="250" onchange="syncDriving(); calculateProfile()"><div class="pill-text">≤ 500 km</div></label>
                <label class="pill-label"><input type="radio" name="q_drive" value="750" onchange="syncDriving(); calculateProfile()"><div class="pill-text">500–1k</div></label>
                <label class="pill-label"><input type="radio" name="q_drive" value="1500" onchange="syncDriving(); calculateProfile()"><div class="pill-text">1k–2k</div></label>
                <label class="pill-label"><input type="radio" name="q_drive" value="2500" checked onchange="syncDriving(); calculateProfile()"><div class="pill-text">2,000+ km</div></label>
            </div>
        </div>

        <div class="question-block">
            <div class="question-label">Boot space importance</div>
            <div class="pill-group">
                <label class="pill-label"><input type="radio" name="q_boot" value="0" onchange="calculateProfile()"><div class="pill-text">Very<br>important</div></label>
                <label class="pill-label"><input type="radio" name="q_boot" value="50" onchange="calculateProfile()"><div class="pill-text">Somewhat</div></label>
                <label class="pill-label"><input type="radio" name="q_boot" value="100" checked onchange="calculateProfile()"><div class="pill-text">Not<br>important</div></label>
            </div>
        </div>

        <div class="question-block">
            <div class="question-label">Driving preference</div>
            <div class="pill-group">
                <label class="pill-label"><input type="radio" name="q_pref" value="0" onchange="calculateProfile()"><div class="pill-text">Performance</div></label>
                <label class="pill-label"><input type="radio" name="q_pref" value="50" onchange="calculateProfile()"><div class="pill-text">Balanced</div></label>
                <label class="pill-label"><input type="radio" name="q_pref" value="100" checked onchange="calculateProfile()"><div class="pill-text">Economy</div></label>
            </div>
        </div>

        <div class="question-block">
            <div class="question-label">CNG station convenience</div>
            <div class="pill-group">
                <label class="pill-label"><input type="radio" name="q_stn" value="0" onchange="calculateProfile()"><div class="pill-text">Inconvenient</div></label>
                <label class="pill-label"><input type="radio" name="q_stn" value="50" onchange="calculateProfile()"><div class="pill-text">Manageable</div></label>
                <label class="pill-label"><input type="radio" name="q_stn" value="100" checked onchange="calculateProfile()"><div class="pill-text">Easy access</div></label>
            </div>
        </div>

        <div class="question-block">
            <div class="question-label">Expected ownership</div>
            <div class="pill-group">
                <label class="pill-label"><input type="radio" name="q_own" value="0" onchange="calculateProfile()"><div class="pill-text">≤ 3 years</div></label>
                <label class="pill-label"><input type="radio" name="q_own" value="50" onchange="calculateProfile()"><div class="pill-text">4–5 years</div></label>
                <label class="pill-label"><input type="radio" name="q_own" value="100" checked onchange="calculateProfile()"><div class="pill-text">6+ years</div></label>
            </div>
        </div>
    </div>

    <!-- CARD 2: SUITABILITY METER -->
    <div class="card" id="suitability-card">
        <div class="gauge-container">
            <p style="font-size: 0.85rem; color: var(--text-muted); letter-spacing: 1px; text-transform: uppercase; font-weight: 700;">CNG Suitability Score</p>
            
            <svg class="gauge-svg" viewBox="0 0 200 110">
                <defs>
                    <linearGradient id="score-grad" x1="0%" y1="0%" x2="100%" y2="0%">
                        <stop offset="0%" stop-color="#ef4444" />
                        <stop offset="50%" stop-color="#f59e0b" />
                        <stop offset="100%" stop-color="#10b981" />
                    </linearGradient>
                </defs>
                <!-- Background Arc -->
                <path d="M 20 100 A 80 80 0 0 1 180 100" fill="none" stroke="var(--gauge-bg)" stroke-width="18" stroke-linecap="round"/>
                <!-- Colored Arc -->
                <path d="M 20 100 A 80 80 0 0 1 180 100" fill="none" stroke="url(#score-grad)" stroke-width="18" stroke-linecap="round"/>
                
                <!-- Text Labels -->
                <text x="20" y="115" fill="var(--text-muted)" font-size="10" text-anchor="middle" font-weight="700">0</text>
                <text x="180" y="115" fill="var(--text-muted)" font-size="10" text-anchor="middle" font-weight="700">100</text>
                <text x="45" y="45" fill="var(--text-main)" font-size="11" text-anchor="middle" font-weight="700" transform="rotate(-35, 45, 45)">PETROL</text>
                <text x="155" y="45" fill="var(--text-main)" font-size="11" text-anchor="middle" font-weight="700" transform="rotate(35, 155, 45)">CNG</text>

                <!-- Needle (Rotation adjusted: -90 points to 0, +90 points to 100) -->
                <g id="score-needle" style="transform-origin: 100px 100px; transform: rotate(90deg); transition: transform 1s cubic-bezier(0.34, 1.56, 0.64, 1);">
                    <circle cx="100" cy="100" r="8" fill="#0f172a"/>
                    <polygon points="96,100 104,100 100,25" fill="#0f172a"/>
                </g>
            </svg>

            <div class="gauge-text-container">
                <div class="gauge-score" id="score-val">86</div>
                <div class="gauge-subtext">out of 100</div>
                <div class="gauge-result-badge" id="score-badge">STRONG CNG FIT</div>
            </div>
        </div>
    </div>

    <!-- CARD 3: BREAK-EVEN CALCULATOR -->
    <div class="card">
        <div class="card-header">
            <div class="card-title-group">
                <p>Break-Even Calculator</p>
                <h2 id="calc-main-title">When does the extra ₹0 come back?</h2>
            </div>
        </div>

        <div class="calc-subtitle" id="calc-subtitle">
            Select variants to calculate.
        </div>

        <div class="variant-selectors">
            <div class="input-box">
                <label>Petrol Variant</label>
                <select id="variantA" class="custom-input"></select>
            </div>
            <div class="input-box">
                <label>CNG Variant</label>
                <select id="variantB" class="custom-input"></select>
            </div>
        </div>

        <div class="input-box">
            <label>Monthly running (km)</label>
            <input type="number" id="manualKm" class="custom-input" value="2500" oninput="syncPill(); calculateFinance()">
        </div>

        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px;">
            <div class="input-box">
                <label>Petrol mileage (km/L)</label>
                <input type="number" id="dispMilA" class="custom-input" readonly style="color: var(--text-muted); background: #f1f5f9;">
            </div>
            <div class="input-box">
                <label>CNG mileage (km/kg)</label>
                <input type="number" id="dispMilB" class="custom-input" readonly style="color: var(--text-muted); background: #f1f5f9;">
            </div>
        </div>

        <!-- ODOMETER SECTION -->
        <div class="odometer-section" id="odo-section">
            <div class="odometer-title">Break-Even Odometer</div>
            
            <div class="odometer-display" id="odometer">
                <div class="odo-digit">0</div>
                <div class="odo-digit">0</div>
                <div class="odo-digit">0</div>
                <div class="odo-digit">0</div>
                <div class="odo-digit">0</div>
                <div class="odo-digit">0</div>
            </div>
            
            <div class="odo-sub">kilometres required</div>
            <div class="savings-highlight" id="monthly-savings-text">Approx. fuel saving: <span>₹0/month</span></div>
        </div>

        <!-- TIME GAUGE -->
        <div class="gauge-container" id="time-section">
            <p class="odometer-title" style="margin-bottom: 0;">Break-Even Time</p>
            
            <svg class="gauge-svg" viewBox="0 0 200 120" style="max-width: 220px; margin-top: 10px;">
                <!-- Background Arc -->
                <path d="M 20 100 A 80 80 0 0 1 180 100" fill="none" stroke="var(--gauge-bg)" stroke-width="14" stroke-linecap="round"/>
                <!-- Colored Arc -->
                <path id="time-arc" d="M 20 100 A 80 80 0 0 1 180 100" fill="none" stroke="var(--accent-blue)" stroke-width="14" stroke-linecap="round" stroke-dasharray="251.2" stroke-dashoffset="251.2" style="transition: stroke-dashoffset 1s cubic-bezier(0.4, 0, 0.2, 1);"/>
                
                <text x="20" y="115" fill="var(--text-muted)" font-size="11" font-weight="600" text-anchor="middle">0 yr</text>
                <text x="180" y="115" fill="var(--text-muted)" font-size="11" font-weight="600" text-anchor="middle">8+ yr</text>

                <!-- Needle (Rotation adjusted: -90 points to 0, +90 points to max) -->
                <g id="time-needle" style="transform-origin: 100px 100px; transform: rotate(-90deg); transition: transform 1s cubic-bezier(0.34, 1.56, 0.64, 1);">
                    <circle cx="100" cy="100" r="7" fill="#0f172a"/>
                    <polygon points="97,100 103,100 100,25" fill="#0f172a"/>
                </g>
            </svg>

            <div class="gauge-text-container" style="margin-top: -35px;">
                <div class="gauge-score" id="time-val" style="font-size: 2.8rem;">0.0</div>
                <div class="gauge-subtext" style="font-size: 1.1rem; color: var(--text-main); font-weight: 700;">years</div>
                <div class="gauge-subtext" id="time-desc" style="margin-top: 8px; font-weight: 600;">-</div>
            </div>
        </div>

    </div>

</div>

<script>
    const variantsData = [{"variant": "BALENO SIGMA 1.2L 5MT", "on_road_price": 681390, "mileage": 22.35, "fuel_price": 115}, {"variant": "BALENO DELTA 1.2L 5MT", "on_road_price": 785420, "mileage": 22.35, "fuel_price": 115}, {"variant": "BALENO ZETA 1.2L 5MT", "on_road_price": 892854, "mileage": 22.35, "fuel_price": 115}, {"variant": "BALENO ALPHA 1.2L 5MT", "on_road_price": 1014079, "mileage": 22.35, "fuel_price": 115}, {"variant": "BALENO DELTA CNG 1.2L 5MT", "on_road_price": 891054, "mileage": 30.61, "fuel_price": 104}, {"variant": "BALENO ZETA CNG 1.2L 5MT", "on_road_price": 998923, "mileage": 30.61, "fuel_price": 104}, {"variant": "FRONX SIGMA 1.2L 5MT", "on_road_price": 776637, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX DELTA 1.2L 5MT", "on_road_price": 875783, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX SIGMA CNG 1.2L 5MT", "on_road_price": 891941, "mileage": 28.51, "fuel_price": 104}, {"variant": "FRONX DELTA CNG 1.2L 5MT", "on_road_price": 985637, "mileage": 28.51, "fuel_price": 104}, {"variant": "GRAND VITARA DELTA 1.5L 5MT", "on_road_price": 1398900, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA DELTA CNG 1.5L 5MT", "on_road_price": 1496002, "mileage": 26.6, "fuel_price": 104}, {"variant": "XL6 ZETA 1.5L 5MT", "on_road_price": 1336091, "mileage": 20.97, "fuel_price": 115}, {"variant": "XL6 ZETA CNG 1.5L 5MT", "on_road_price": 1447048, "mileage": 26.32, "fuel_price": 104}];

    const formatCurrency = (val) => '₹' + new Intl.NumberFormat('en-IN', { maximumFractionDigits: 0 }).format(val);

    // --- SETUP DROPDOWNS ---
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

        selectA.addEventListener('change', calculateFinance);
        selectB.addEventListener('change', calculateFinance);
    }

    // --- SYNC INPUTS ---
    function syncDriving() {
        const selected = document.querySelector('input[name="q_drive"]:checked').value;
        document.getElementById('manualKm').value = selected;
    }

    function syncPill() {
        const km = parseInt(document.getElementById('manualKm').value) || 0;
        let targetVal = "250";
        if(km > 500 && km <= 1000) targetVal = "750";
        else if(km > 1000 && km <= 2000) targetVal = "1500";
        else if(km > 2000) targetVal = "2500";
        
        document.querySelector(`input[name="q_drive"][value="${targetVal}"]`).checked = true;
        calculateProfile();
    }

    function resetProfile() {
        document.querySelector('input[name="q_drive"][value="250"]').checked = true;
        document.querySelector('input[name="q_boot"][value="100"]').checked = true;
        document.querySelector('input[name="q_pref"][value="100"]').checked = true;
        document.querySelector('input[name="q_stn"][value="100"]').checked = true;
        document.querySelector('input[name="q_own"][value="100"]').checked = true;
        syncDriving();
        calculateProfile();
    }

    // --- PROFILE CALCULATION ---
    function calculateProfile() {
        let score = 0;
        const q1 = parseInt(document.querySelector('input[name="q_drive"]:checked').value);
        if(q1 === 250) score += 0; else if(q1 === 750) score += 10; else if(q1 === 1500) score += 20; else score += 25;

        const q2 = parseInt(document.querySelector('input[name="q_boot"]:checked').value);
        score += (q2 * 0.15); // 0, 7.5, 15

        const q3 = parseInt(document.querySelector('input[name="q_pref"]:checked').value);
        score += (q3 * 0.20); // 0, 10, 20

        const q4 = parseInt(document.querySelector('input[name="q_stn"]:checked').value);
        score += (q4 * 0.25); // 0, 12.5, 25

        const q5 = parseInt(document.querySelector('input[name="q_own"]:checked').value);
        score += (q5 * 0.15); // 0, 7.5, 15

        score = Math.round(score);
        
        document.getElementById('score-val').innerText = score;
        
        // Gauge Fix: Arc spans 180 deg. -90 is Left (0 score). +90 is Right (100 score).
        const rotation = -90 + ((score / 100) * 180);
        document.getElementById('score-needle').style.transform = `rotate(${rotation}deg)`;

        const badge = document.getElementById('score-badge');
        if(score < 30) {
            badge.innerText = "STRONG PETROL FIT";
            badge.style.color = "#b91c1c";
            badge.style.borderColor = "#fca5a5";
            badge.style.background = "#fef2f2";
        } else if (score < 60) {
            badge.innerText = "BALANCED PROFILE";
            badge.style.color = "#b45309";
            badge.style.borderColor = "#fcd34d";
            badge.style.background = "#fffbeb";
        } else {
            badge.innerText = "STRONG CNG FIT";
            badge.style.color = "#047857";
            badge.style.borderColor = "#6ee7b7";
            badge.style.background = "#ecfdf5";
        }

        calculateFinance();
    }

    // --- FINANCE / BREAK-EVEN CALCULATION ---
    function updateOdometerDisplay(numberStr) {
        const padded = numberStr.padStart(6, '0');
        const digits = document.querySelectorAll('.odo-digit');
        for(let i=0; i<6; i++) {
            digits[i].innerText = padded[i];
        }
    }

    function calculateFinance() {
        const idxA = document.getElementById('variantA').value;
        const idxB = document.getElementById('variantB').value;
        if(idxA === "" || idxB === "") return;

        const varA = variantsData[idxA];
        const varB = variantsData[idxB];
        // Ensure at least 1km to prevent Infinity
        const monthlyKm = Math.max(parseFloat(document.getElementById('manualKm').value) || 1000, 1);

        document.getElementById('dispMilA').value = varA.mileage;
        document.getElementById('dispMilB').value = varB.mileage;

        const extraCost = varB.on_road_price - varA.on_road_price;
        const costPerKmA = varA.fuel_price / varA.mileage;
        const costPerKmB = varB.fuel_price / varB.mileage;
        const savingsPerKm = costPerKmA - costPerKmB;

        const mainTitle = document.getElementById('calc-main-title');
        const subTitle = document.getElementById('calc-subtitle');
        const odoSection = document.getElementById('odo-section');
        const timeSection = document.getElementById('time-section');

        if(extraCost <= 0) {
            mainTitle.innerText = "No Extra Cost Required";
            subTitle.innerHTML = `CNG variant is equally or less priced.`;
            odoSection.style.display = 'none';
            timeSection.style.display = 'none';
            return;
        }

        odoSection.style.display = 'block';
        timeSection.style.display = 'flex';

        mainTitle.innerText = `When does the extra ${formatCurrency(extraCost)} come back?`;
        subTitle.innerHTML = `Petrol ₹${varA.fuel_price}/L • CNG ₹${varB.fuel_price}/kg<br>Estimated fuel cost: Petrol ₹${costPerKmA.toFixed(2)}/km - CNG ₹${costPerKmB.toFixed(2)}/km`;

        if(savingsPerKm > 0) {
            const breakEvenKm = extraCost / savingsPerKm;
            updateOdometerDisplay(Math.round(breakEvenKm).toString());
            
            const monthlySaving = savingsPerKm * monthlyKm;
            document.getElementById('monthly-savings-text').innerHTML = `Approx. fuel saving: <span>${formatCurrency(monthlySaving)}/month</span>`;

            // Time Gauge
            const breakEvenYears = breakEvenKm / (monthlyKm * 12);
            document.getElementById('time-val').innerText = breakEvenYears.toFixed(1);
            
            // Time Arc Length (Radius 80 = Circumference 251.2)
            const timeRatio = Math.min(breakEvenYears / 8, 1);
            const offset = 251.2 - (timeRatio * 251.2);
            document.getElementById('time-arc').style.strokeDashoffset = offset;
            
            // Dial Fix: Rotate from -90 (0 yrs) to +90 (8+ yrs)
            const timeRotation = -90 + (timeRatio * 180);
            document.getElementById('time-needle').style.transform = `rotate(${timeRotation}deg)`;

            const timeDesc = document.getElementById('time-desc');
            if(breakEvenYears < 2) { 
                timeDesc.innerText = "Fast recovery at this running"; 
                timeDesc.style.color = "var(--accent-green)"; 
                document.getElementById('time-arc').style.stroke = "var(--accent-green)";
            } else if(breakEvenYears < 5) { 
                timeDesc.innerText = "Moderate recovery time"; 
                timeDesc.style.color = "#f59e0b"; 
                document.getElementById('time-arc').style.stroke = "#f59e0b";
            } else { 
                timeDesc.innerText = "Slow recovery at this running"; 
                timeDesc.style.color = "var(--accent-red)"; 
                document.getElementById('time-arc').style.stroke = "var(--accent-red)";
            }

        } else {
            updateOdometerDisplay("999999");
            document.getElementById('monthly-savings-text').innerHTML = `Approx. fuel saving: <span>None</span>`;
            document.getElementById('time-val').innerText = "Never";
            document.getElementById('time-desc').innerText = "CNG is costlier to run";
            document.getElementById('time-needle').style.transform = `rotate(90deg)`;
        }
    }

    // --- INIT ---
    window.onload = () => {
        setupDropdowns();
        calculateProfile();
    };

</script>
</body>
</html>