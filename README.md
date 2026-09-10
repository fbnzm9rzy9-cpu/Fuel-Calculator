
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>सही फ्यूल चुना क्या?</title>
    <style>
        /* Premium Fonts Setup */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Space+Mono:wght@700&family=Outfit:wght@300;400;500;600;700;800&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Outfit', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        :root {
            --bg-color: #05080f;
            --card-bg: #0f141e;
            --border-light: #1f2937;
            --input-bg: #111827;
            
            --text-main: #ffffff;
            --text-muted: #8b9bb4;
            
            --nexa-green: #10b981;
            --nexa-green-bg: rgba(16, 185, 129, 0.1);
            --serious-red: #ef4444;
            --serious-red-bg: rgba(239, 68, 68, 0.1);
        }

        body {
            background-color: var(--bg-color);
            background-image: radial-gradient(circle at 50% 0%, #111827 0%, transparent 100%);
            color: var(--text-main);
            padding: 20px 15px 60px 15px; 
            display: flex;
            justify-content: center;
            min-height: 100vh;
        }

        .app-container {
            width: 100%;
            max-width: 520px;
            display: flex;
            flex-direction: column;
            gap: 20px; 
            margin-top: 20px; 
        }

        .header-section {
            text-align: center;
            margin-bottom: 0px;
        }

        .header-section h1 {
            font-size: 2.5rem;
            font-weight: 800;
            color: var(--text-main);
            letter-spacing: -1px;
            margin-bottom: 0px;
        }

        /* --- CARDS --- */
        .card {
            background-color: var(--card-bg);
            border: 1px solid var(--border-light);
            border-radius: 24px;
            padding: 24px; 
            display: flex;
            flex-direction: column;
            gap: 20px; 
            box-shadow: 0 20px 40px -12px rgba(0,0,0,0.5);
        }

        /* --- INPUTS --- */
        .input-box {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .input-box label {
            font-size: 0.9rem;
            color: var(--text-main);
            font-weight: 600;
            display: flex;
            align-items: center;
        }

        .custom-input {
            background: var(--input-bg);
            border: 1px solid var(--border-light);
            color: var(--nexa-green);
            padding: 14px 16px;
            border-radius: 14px;
            font-size: 1.1rem;
            font-weight: 700;
            font-family: 'JetBrains Mono', monospace;
            outline: none;
            width: 100%;
            transition: 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            appearance: none;
        }

        .custom-input:focus {
            border-color: var(--nexa-green);
            background: #1f2937;
            box-shadow: 0 0 0 4px var(--nexa-green-bg);
        }

        select.custom-input {
            background-image: url("data:image/svg+xml,%3Csvg width='12' height='8' viewBox='0 0 12 8' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 1.5L6 6.5L11 1.5' stroke='%238b9bb4' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 16px center;
            cursor: pointer;
        }

        .input-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
        }

        /* --- TECHY ICONS & ANIMATIONS --- */
        .tech-icon {
            width: 22px;
            height: 22px;
            margin-right: 8px;
            stroke: var(--nexa-green);
            fill: none;
            stroke-width: 2;
            stroke-linecap: round;
            stroke-linejoin: round;
        }

        @keyframes dashMove {
            0% { transform: translateY(-5px); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateY(10px); opacity: 0; }
        }
        .anim-dash { animation: dashMove 1.5s infinite linear; }

        @keyframes steerWheel {
            0%, 100% { transform: rotate(0deg); }
            25% { transform: rotate(-25deg); }
            75% { transform: rotate(25deg); }
        }
        .anim-steer { 
            transform-origin: 12px 12px; 
            animation: steerWheel 3s infinite ease-in-out; 
        }

        @keyframes scanBox {
            0% { transform: translateY(0); stroke: var(--nexa-green); opacity: 0.5;}
            50% { transform: translateY(12px); stroke: #ffffff; opacity: 1;}
            100% { transform: translateY(0); stroke: var(--nexa-green); opacity: 0.5;}
        }
        .anim-scan { animation: scanBox 2s infinite ease-in-out; }

        @keyframes radarPulse {
            0% { r: 1; opacity: 1; stroke-width: 2;}
            100% { r: 10; opacity: 0; stroke-width: 0.5;}
        }
        .anim-radar { animation: radarPulse 1.5s infinite cubic-bezier(0.215, 0.610, 0.355, 1); transform-origin: center;}


        /* --- SEGMENTED CONTROLS (PILLS) --- */
        .question-block {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .question-label {
            font-size: 0.95rem;
            color: var(--text-main);
            font-weight: 600;
            display: flex;
            align-items: center;
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
            height: 48px;
            background: var(--input-bg);
            border: 1px solid var(--border-light);
            border-radius: 12px;
            color: var(--text-muted);
            font-size: 0.9rem;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            text-align: center;
            padding: 0 8px;
            line-height: 1.2;
        }

        .pill-label input:checked + .pill-text {
            background: var(--nexa-green-bg);
            border-color: var(--nexa-green);
            color: var(--nexa-green);
            font-weight: 700;
            box-shadow: 0 4px 15px rgba(16, 185, 129, 0.15);
        }

        /* --- BUTTONS --- */
        .btn-primary {
            background: var(--nexa-green);
            color: #000000;
            border: none;
            padding: 16px;
            border-radius: 14px;
            font-size: 1.1rem;
            font-weight: 800;
            letter-spacing: 0.5px;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 10px 25px rgba(16, 185, 129, 0.25);
            margin-top: 5px;
        }
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 15px 30px rgba(16, 185, 129, 0.4);
            background: #059669;
            color: #ffffff;
        }

        .btn-secondary {
            background: transparent;
            color: var(--text-muted);
            border: 1px solid var(--border-light);
            padding: 16px;
            border-radius: 14px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
        }
        .btn-secondary:hover {
            background: var(--input-bg);
            color: var(--text-main);
        }

        /* --- DIAGNOSTIC GAUGE (ANALOG DIAL) --- */
        .gauge-container {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .gauge-svg {
            width: 100%;
            max-width: 300px;
            overflow: visible;
        }

        .gauge-text-container {
            text-align: center;
            margin-top: 10px; 
        }

        .gauge-result-badge {
            padding: 12px 24px;
            border-radius: 14px;
            font-size: 1.6rem; 
            font-weight: 800;
            display: inline-block;
            letter-spacing: 0.5px;
            margin-top: 5px;
        }

        /* --- SERIOUS FINANCIALS --- */
        .total-cost-row {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background: rgba(0,0,0,0.4);
            padding: 25px 20px;
            border-radius: 16px;
            border: 1px solid rgba(255,255,255,0.05);
            gap: 10px; 
        }

        .total-cost-label {
            font-size: 1rem;
            color: var(--text-muted);
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            text-align: center;
            line-height: 1.4;
        }

        .total-cost-value {
            font-family: 'JetBrains Mono', monospace;
            font-size: 3.2rem;
            font-weight: 800;
            color: var(--serious-red);
            letter-spacing: -2px;
        }

        /* --- ODOMETER & TIME DISPLAY --- */
        .odometer-section {
            text-align: center;
            padding: 20px 0 5px 0;
            background: #080b11; 
            border-radius: 16px;
            border: 1px inset rgba(255,255,255,0.05);
        }

        .odometer-display {
            display: flex;
            justify-content: center;
            gap: 4px;
            margin-bottom: 15px;
        }

        .odo-digit {
            background: linear-gradient(180deg, #111827 0%, #030712 50%, #111827 100%);
            color: #ffffff;
            font-family: 'Space Mono', monospace;
            font-size: 2.6rem;
            font-weight: 700;
            width: 48px;
            height: 68px;
            border-radius: 6px;
            border: 1px solid #1f2937;
            box-shadow: inset 0 5px 15px rgba(0,0,0,1), 0 2px 5px rgba(0,0,0,0.5);
            overflow: hidden;
            position: relative;
        }
        
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

        .serious-time-box {
            text-align: center;
            padding: 15px;
            border-radius: 16px;
            background: var(--serious-red-bg); 
            border: 1px solid rgba(239, 68, 68, 0.2);
        }

        .serious-time-val {
            font-family: 'JetBrains Mono', monospace;
            font-size: 3.5rem;
            font-weight: 800;
            color: var(--serious-red);
            line-height: 1;
            margin: 5px 0;
            letter-spacing: -2px;
        }

        .ampersand {
            text-align: center;
            font-size: 2.5rem;
            font-weight: 800;
            color: var(--border-light);
            margin: 0; 
            font-family: 'Outfit', sans-serif;
            opacity: 0.5;
            line-height: 1;
        }

        /* --- UTILS & ANIMATIONS --- */
        .hidden { display: none !important; }
        
        @keyframes elegantFadeUp {
            0% { opacity: 0; transform: translateY(40px) scale(0.98); }
            100% { opacity: 1; transform: translateY(0) scale(1); }
        }

        .reveal-container { display: flex; flex-direction: column; gap: 20px; }
        .reveal-1 { animation: elegantFadeUp 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards; opacity: 0; }
        .reveal-2 { animation: elegantFadeUp 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.2s forwards; opacity: 0; }
        .reveal-3 { animation: elegantFadeUp 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.4s forwards; opacity: 0; }
        .reveal-4 { animation: elegantFadeUp 0.8s cubic-bezier(0.16, 1, 0.3, 1) 0.6s forwards; opacity: 0; }

        @media (max-width: 600px) {
            .app-container { margin-top: 10px;}
            .odo-digit { width: 40px; height: 58px; font-size: 2.2rem; }
            .header-section h1 { font-size: 2.2rem; }
        }

    </style>
</head>
<body>

<div class="app-container">

    <div class="header-section">
        <h1>सही फ्यूल चुना क्या?</h1>
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

            <div class="input-box" style="margin-top: 5px;">
                <!-- Animated Road Icon -->
                <label>
                    <svg class="tech-icon" viewBox="0 0 24 24">
                        <path d="M4 22L8 2m8 0l4 20" stroke="rgba(255,255,255,0.4)"/>
                        <line x1="12" y1="22" x2="12" y2="16" class="anim-dash" stroke="#ffffff"/>
                        <line x1="12" y1="10" x2="12" y2="2" opacity="0.3" stroke="#ffffff"/>
                    </svg>
                    Daily Running (in KMs)
                </label>
                <input type="number" id="dailyDrivingInput" class="custom-input" value="80">
            </div>

            <!-- New Question: Purpose of vehicle utility -->
            <div class="question-block" style="margin-top: 5px;">
                <label class="question-label">
                    <!-- Animated Briefcase / Car Icon -->
                    <svg class="tech-icon" viewBox="0 0 24 24">
                        <rect x="3" y="8" width="18" height="12" rx="2" stroke="rgba(255,255,255,0.4)"/>
                        <path d="M8 8V6a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2" stroke="rgba(255,255,255,0.4)"/>
                        <circle cx="12" cy="14" r="2" fill="rgba(255,255,255,0.8)" class="anim-radar"/>
                    </svg>
                    Purpose of vehicle utility
                </label>
                <div class="pill-group">
                    <label class="pill-label"><input type="radio" name="q_purpose" value="0" checked><div class="pill-text">Personal</div></label>
                    <label class="pill-label"><input type="radio" name="q_purpose" value="100"><div class="pill-text">Commercial</div></label>
                </div>
            </div>

            <!-- 1. Driving Preference (Economy -> Balanced -> Performance) -->
            <div class="question-block">
                <label class="question-label">
                    <!-- Animated Steering Wheel -->
                    <svg class="tech-icon" viewBox="0 0 24 24">
                        <g class="anim-steer">
                            <circle cx="12" cy="12" r="10" stroke="rgba(255,255,255,0.4)" stroke-width="2" fill="none"/>
                            <circle cx="12" cy="12" r="2" fill="rgba(255,255,255,0.6)"/>
                            <path d="M2 12h8M14 12h8M12 14v8" stroke="rgba(255,255,255,0.4)" stroke-width="2"/>
                        </g>
                    </svg>
                    Driving preference
                </label>
                <div class="pill-group">
                    <label class="pill-label"><input type="radio" name="q_pref" value="100"><div class="pill-text">Economy</div></label>
                    <label class="pill-label"><input type="radio" name="q_pref" value="50"><div class="pill-text">Balanced</div></label>
                    <label class="pill-label"><input type="radio" name="q_pref" value="0" checked><div class="pill-text">Performance</div></label>
                </div>
            </div>

            <!-- 2. Boot Space Importance (Not important -> Somewhat -> Very) -->
            <div class="question-block">
                <label class="question-label">
                    <!-- Animated Scan Box Icon -->
                    <svg class="tech-icon" viewBox="0 0 24 24">
                        <rect x="4" y="6" width="16" height="12" rx="2" stroke="rgba(255,255,255,0.4)"/>
                        <path d="M8 6V4h8v2" stroke="rgba(255,255,255,0.4)"/>
                        <line x1="3" y1="12" x2="21" y2="12" class="anim-scan"/>
                    </svg>
                    Boot space importance
                </label>
                <div class="pill-group">
                    <label class="pill-label"><input type="radio" name="q_boot" value="100"><div class="pill-text">Not<br>important</div></label>
                    <label class="pill-label"><input type="radio" name="q_boot" value="50"><div class="pill-text">Somewhat</div></label>
                    <label class="pill-label"><input type="radio" name="q_boot" value="0" checked><div class="pill-text">Very<br>important</div></label>
                </div>
            </div>

            <!-- 3. CNG station convenience (Inconvenient -> Manageable -> Easy) -->
            <div class="question-block">
                <label class="question-label">
                    <!-- Animated Radar/Pin Icon -->
                    <svg class="tech-icon" viewBox="0 0 24 24">
                        <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z" stroke="rgba(255,255,255,0.4)"/>
                        <circle cx="12" cy="10" r="1" class="anim-radar"/>
                    </svg>
                    CNG station convenience
                </label>
                <div class="pill-group">
                    <label class="pill-label"><input type="radio" name="q_stn" value="0" checked><div class="pill-text">Inconvenient</div></label>
                    <label class="pill-label"><input type="radio" name="q_stn" value="50"><div class="pill-text">Manageable</div></label>
                    <label class="pill-label"><input type="radio" name="q_stn" value="100"><div class="pill-text">Easy access</div></label>
                </div>
            </div>

            <button class="btn-primary" onclick="generateReport()">Generate Analysis Matrix</button>
        </div>
    </div>

    <!-- ================= PART 2: RESULTS ================= -->
    <div id="part2" class="hidden reveal-container">
        
        <!-- 1. SUITABILITY METER (ANALOG CAR DIAL) -->
        <div class="card reveal-1">
            <div class="gauge-container">
                <svg class="gauge-svg" viewBox="0 0 300 180">
                    <!-- Background Dark Arch mimicking the speedometer depth -->
                    <path d="M 20 150 A 130 130 0 0 1 280 150" fill="none" stroke="#111827" stroke-width="40" stroke-linecap="butt"/>
                    
                    <!-- Dynamic Ticks and Numbers injected via JS -->
                    <g id="dial-ticks"></g>
                    <g id="dial-labels"></g>
                    
                    <!-- Dial Subtext -->
                    <text x="150" y="110" fill="#8b9bb4" font-size="12" font-weight="600" text-anchor="middle" letter-spacing="2">SCORE</text>

                    <!-- Analog Car Needle -->
                    <g id="score-needle" style="transform-origin: 150px 150px; transform: rotate(-120deg); transition: transform 2s cubic-bezier(0.34, 1.56, 0.64, 1);">
                        <!-- Needle Body -->
                        <polygon points="147,150 153,150 151,35 149,35" fill="#ffffff"/>
                        <!-- Counterweight -->
                        <polygon points="148,165 152,165 153,150 147,150" fill="#ffffff" opacity="0.8"/>
                        <!-- Center Cap -->
                        <circle cx="150" cy="150" r="10" fill="#05080f" stroke="#ffffff" stroke-width="2"/>
                    </g>
                </svg>

                <div class="gauge-text-container">
                    <div class="gauge-result-badge" id="score-badge">-</div>
                </div>
            </div>
        </div>

        <!-- 2. ADDITIONAL COST -->
        <div class="card reveal-2" id="extra-cost-card">
            <div id="extra-cost-container">
                <div class="total-cost-row">
                    <span class="total-cost-label">Total additional cost of purchasing a CNG vehicle</span>
                    <span class="total-cost-value" id="total-extra-val">0</span>
                </div>
            </div>

            <div id="no-cost-msg" class="hidden" style="text-align: center; color: var(--text-muted); font-weight: 500; border: 1px solid var(--border-light); padding: 20px; border-radius: 12px;">
                CNG variant is equally or less priced than Petrol. No extra investment required.
            </div>
        </div>

        <!-- 3. SAVINGS START AFTER -->
        <div class="card reveal-3" id="break-even-card">
            <div style="text-align: center; margin-bottom: 5px;">
                <p style="color: var(--serious-red); font-size: 1.8rem; font-weight: 800; letter-spacing: 1px;">NO SAVINGS UPTO:</p>
            </div>

            <!-- ODOMETER -->
            <div class="odometer-section">
                <div class="odometer-display" id="odometer">
                    <!-- Dynamically generated by setupOdometer() -->
                </div>
                <div style="font-size: 0.85rem; color: var(--text-muted); font-weight: 600; text-transform: uppercase; letter-spacing: 2px;">Kilometres</div>
            </div>

            <div class="ampersand">&</div>

            <!-- SERIOUS TIME TEXT -->
            <div class="serious-time-box">
                <div class="serious-time-val" id="time-text-val">0.0 <span style="font-size: 1.2rem; font-weight: 600; color: var(--serious-red);">Yrs</span></div>
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
            // Strip engine details for cleaner look
            let displayName = variant.variant.replace(" 1.2L 5MT", "").replace(" 1.5L 5MT", "");
            
            if(!variant.variant.includes('CNG')) {
                selectA.add(new Option(displayName, index));
                if(petrolIndex === -1 && variant.variant.includes('BALENO DELTA')) petrolIndex = index;
            } else {
                selectB.add(new Option(displayName, index));
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

    // Function to draw the realistic analog car dial ticks and numbers
    function drawAnalogDial() {
        const ticksGroup = document.getElementById('dial-ticks');
        const labelsGroup = document.getElementById('dial-labels');
        
        let ticks = '';
        let labels = '';
        const cx = 150;
        const cy = 150;
        
        // Loop from 0 to 100 in steps of 2 for fine tick marks
        for (let i = 0; i <= 100; i += 2) {
            let angle = -120 + (i * 2.4);
            let rad = (angle - 90) * (Math.PI / 180);
            
            let rOuter = 130;
            let isMajor = (i % 20 === 0);
            let isMedium = (i % 10 === 0);
            
            let rInner = isMajor ? 112 : (isMedium ? 118 : 124);
            let strokeW = isMajor ? 3 : 2;
            
            let x1 = cx + rOuter * Math.cos(rad);
            let y1 = cy + rOuter * Math.sin(rad);
            let x2 = cx + rInner * Math.cos(rad);
            let y2 = cy + rInner * Math.sin(rad);
            
            ticks += `<line x1="${x1}" y1="${y1}" x2="${x2}" y2="${y2}" stroke="#ffffff" stroke-width="${strokeW}" opacity="${isMajor ? 1 : 0.6}" />`;
            
            if (isMajor) {
                let textR = 92;
                let tx = cx + textR * Math.cos(rad);
                let ty = cy + textR * Math.sin(rad) + 6; 
                labels += `<text x="${tx}" y="${ty}" fill="#ffffff" font-family="'Space Mono', monospace" font-size="16" font-weight="700" text-anchor="middle">${i}</text>`;
            }
        }
        
        ticksGroup.innerHTML = ticks;
        labelsGroup.innerHTML = labels;
    }

    function animateValue(obj, start, end, duration, formatAsCurrency = false, isFloat = false) {
        let startTimestamp = null;
        const step = (timestamp) => {
            if (!startTimestamp) startTimestamp = timestamp;
            const progress = Math.min((timestamp - startTimestamp) / duration, 1);
            const easeProgress = 1 - Math.pow(1 - progress, 3);
            const currentVal = (easeProgress * (end - start) + start);
            
            if (formatAsCurrency) {
                obj.innerHTML = formatCurrency(Math.floor(currentVal));
            } else if (isFloat) {
                obj.innerHTML = `${currentVal.toFixed(1)} <span style="font-size: 1.2rem; font-weight: 600; color: var(--serious-red);">Yrs</span>`;
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
        document.getElementById('part1').classList.add('hidden');
        
        const part2 = document.getElementById('part2');
        part2.classList.remove('hidden');
        part2.classList.remove('fade-in');
        void part2.offsetWidth;
        part2.classList.add('fade-in');

        document.getElementById('score-needle').style.transform = `rotate(-120deg)`;
        updateOdometerDisplay("0");

        setTimeout(() => {
            runCalculations();
        }, 100);
    }

    function goBack() {
        document.getElementById('part2').classList.add('hidden');
        document.getElementById('part1').classList.remove('hidden');
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function runCalculations() {
        // --- 1. CALCULATE PROFILE SCORE (Out of 100) ---
        let score = 0;
        const dailyKm = parseFloat(document.getElementById('dailyDrivingInput').value) || 0;
        const monthlyKmEquiv = dailyKm * 30; 
        
        // 1. Daily Running (Max 30 points)
        if (monthlyKmEquiv <= 500) score += 0;
        else if (monthlyKmEquiv <= 1000) score += 8; 
        else if (monthlyKmEquiv <= 2000) score += 18; 
        else score += 30;

        // 2. Purpose of Vehicle Utility (Max 15 points)
        const q1 = parseInt(document.querySelector('input[name="q_purpose"]:checked').value);
        if (q1 === 0) score += 0;       // Personal
        else score += 15;               // Commercial

        // 3. Boot Space (Max 20 points)
        const q2 = parseInt(document.querySelector('input[name="q_boot"]:checked').value);
        if (q2 === 0) score += 0; else if (q2 === 50) score += 10; else score += 20;

        // 4. Driving Preference (Max 15 points)
        const q3 = parseInt(document.querySelector('input[name="q_pref"]:checked').value);
        if (q3 === 0) score += 0; else if (q3 === 50) score += 7; else score += 15;

        // 5. Station Convenience (Max 20 points)
        const q4 = parseInt(document.querySelector('input[name="q_stn"]:checked').value);
        if (q4 === 0) score += 0; else if (q4 === 50) score += 10; else score += 20;

        score = Math.round(score);
        
        // Map score 0-100 to rotation -120 to +120
        const scoreRotation = -120 + ((score / 100) * 240);
        setTimeout(() => {
            document.getElementById('score-needle').style.transform = `rotate(${scoreRotation}deg)`;
        }, 200);

        const badge = document.getElementById('score-badge');
        setTimeout(() => {
            if(score < 50) {
                badge.innerText = "पेट्रोल ही सही है";
                badge.style.color = "#ef4444";
                badge.style.background = "rgba(239, 68, 68, 0.1)";
                badge.style.border = "1px solid rgba(239, 68, 68, 0.3)";
            } else if (score < 80) {
                badge.innerText = "पेट्रोल बेहतर रहेगा";
                badge.style.color = "#3b82f6";
                badge.style.background = "rgba(59, 130, 246, 0.1)";
                badge.style.border = "1px solid rgba(59, 130, 246, 0.3)";
            } else {
                badge.innerText = "सीएनजी (CNG) सही है";
                badge.style.color = "#10b981";
                badge.style.background = "rgba(16, 185, 129, 0.1)";
                badge.style.border = "1px solid rgba(16, 185, 129, 0.3)";
            }
        }, 1200);


        // --- 2. CALCULATE ADDITIONAL COST & ROUND OFF ---
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
        let totalExtraCost = orpDiff + intDiff;
        
        // Round off to next thousand
        const roundedExtraCost = Math.ceil(totalExtraCost / 1000) * 1000;

        const costPerKmA = pPrice / varA.mileage;
        const costPerKmB = cPrice / varB.mileage;
        const savingsPerKm = costPerKmA - costPerKmB;

        const extraCostBox = document.getElementById('extra-cost-container');
        const noCostMsg = document.getElementById('no-cost-msg');
        const breakEvenCard = document.getElementById('break-even-card');

        if(roundedExtraCost <= 0) {
            extraCostBox.classList.add('hidden');
            noCostMsg.classList.remove('hidden');
            breakEvenCard.classList.add('hidden');
            return;
        }

        extraCostBox.classList.remove('hidden');
        noCostMsg.classList.add('hidden');
        breakEvenCard.classList.remove('hidden');
        
        setTimeout(() => {
            animateValue(document.getElementById('total-extra-val'), 0, roundedExtraCost, 1500, true);
        }, 500);

        // --- 3. BREAK EVEN ---
        if(savingsPerKm > 0) {
            const breakEvenKm = roundedExtraCost / savingsPerKm;
            updateOdometerDisplay(Math.round(breakEvenKm).toString());
            
            const breakEvenYears = breakEvenKm / yearlyKm;
            
            setTimeout(() => {
                animateValue(document.getElementById('time-text-val'), 0, breakEvenYears, 2000, false, true);
            }, 800);

        } else {
            updateOdometerDisplay("999999");
            document.getElementById('time-text-val').innerHTML = `Never`;
            document.getElementById('time-text-val').style.color = "var(--serious-red)";
        }
        
        setTimeout(() => {
            window.scrollTo({ top: document.getElementById('part2').offsetTop - 20, behavior: 'smooth' });
        }, 200);
    }

    // --- INIT ---
    window.onload = () => {
        setupOdometer();
        setupDropdowns();
        drawAnalogDial();
    };

</script>
</body>
</html>
