# Fuel-Calculator
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sahi Chuna Kya - NEXA Comparison</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Rajdhani:wght@500;700&display=swap');

        :root {
            --primary-bg: #111;
            --panel-bg: #1a1a1a;
            --accent-blue: #00e5ff;
            --accent-green: #00ff88;
            --accent-red: #ff3366;
            --accent-gold: #ffb700;
            --text-light: #e0e0e0;
            --text-muted: #888;
            --border-color: #333;
        }

        body {
            font-family: 'Rajdhani', sans-serif;
            background-color: var(--primary-bg);
            background-image: 
                radial-gradient(circle at 100% 100%, #1a2a3a 0, transparent 50%),
                radial-gradient(circle at 0% 0%, #2a1a1a 0, transparent 50%);
            color: var(--text-light);
            margin: 0;
            padding: 20px;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            width: 100%;
        }

        .header h1 {
            font-family: 'Orbitron', sans-serif;
            color: var(--accent-blue);
            font-size: 3.5em;
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 3px;
            text-shadow: 0 0 15px rgba(0, 229, 255, 0.5);
        }

        .header p {
            color: var(--text-muted);
            font-size: 1.3em;
            letter-spacing: 1px;
        }

        .dashboard-container {
            width: 100%;
            max-width: 1200px;
            background: rgba(26, 26, 26, 0.8);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            padding: 30px;
            box-shadow: inset 0 0 50px rgba(0,0,0,0.5), 0 10px 30px rgba(0,0,0,0.8);
            backdrop-filter: blur(10px);
        }

        .control-panel {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-bottom: 40px;
            background: linear-gradient(145deg, #222, #111);
            padding: 25px;
            border-radius: 15px;
            border: 1px solid #333;
            box-shadow: 5px 5px 15px rgba(0,0,0,0.5), inset 2px 2px 5px rgba(255,255,255,0.05);
        }

        .input-group {
            flex: 1;
            min-width: 200px;
            display: flex;
            flex-direction: column;
        }

        .input-group label {
            font-family: 'Orbitron', sans-serif;
            font-size: 0.9em;
            color: var(--text-muted);
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .input-group select, .input-group input {
            background: #0a0a0a;
            color: var(--accent-blue);
            border: 1px solid var(--border-color);
            padding: 15px;
            border-radius: 8px;
            font-family: 'Orbitron', sans-serif;
            font-size: 1em;
            transition: all 0.3s ease;
            outline: none;
        }

        .input-group select:focus, .input-group input:focus {
            border-color: var(--accent-blue);
            box-shadow: 0 0 10px rgba(0, 229, 255, 0.2);
        }

        .comparison-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            margin-bottom: 40px;
        }

        .variant-card {
            background: linear-gradient(145deg, #1f1f1f, #151515);
            border: 1px solid #333;
            border-radius: 15px;
            padding: 30px;
            position: relative;
            overflow: hidden;
            box-shadow: 0 10px 20px rgba(0,0,0,0.5);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .variant-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.7);
            border-color: #444;
        }

        .odometer-display {
            background: #050505;
            border: 2px solid #222;
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 25px;
            text-align: center;
            position: relative;
            box-shadow: inset 0 0 20px rgba(0,0,0,0.8);
        }

        .odometer-display::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            background: linear-gradient(transparent 50%, rgba(255,255,255,0.02) 50%);
            background-size: 100% 4px;
            pointer-events: none;
        }

        .variant-card h3 {
            font-family: 'Orbitron', sans-serif;
            color: var(--text-light);
            font-size: 1.4em;
            margin: 0;
            text-shadow: 0 0 5px rgba(255,255,255,0.3);
        }

        .data-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
            padding-bottom: 8px;
            border-bottom: 1px dashed #333;
            font-size: 1.05em;
        }

        .data-row span:first-child {
            color: var(--text-muted);
        }

        .data-row span:last-child {
            font-family: 'Orbitron', sans-serif;
            color: var(--text-light);
            font-weight: 700;
        }

        .spec-highlight span:last-child {
            color: var(--accent-blue);
        }

        .total-cost {
            margin-top: 25px;
            padding-top: 20px;
            border-top: 2px solid var(--accent-red);
            font-size: 1.3em;
        }
        
        .total-cost span:last-child {
            color: var(--accent-red);
            text-shadow: 0 0 10px rgba(255, 51, 102, 0.4);
            font-size: 1.2em;
        }

        .savings-box {
            background: linear-gradient(135deg, rgba(0, 255, 136, 0.1), rgba(0, 0, 0, 0.8));
            border: 1px solid var(--accent-green);
            color: var(--accent-green);
            padding: 30px;
            border-radius: 15px;
            text-align: center;
            font-family: 'Orbitron', sans-serif;
            font-size: 1.8em;
            text-shadow: 0 0 15px rgba(0, 255, 136, 0.5);
            box-shadow: 0 0 30px rgba(0, 255, 136, 0.1), inset 0 0 20px rgba(0, 255, 136, 0.05);
            position: relative;
            overflow: hidden;
        }
        
        .savings-box::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(transparent, rgba(255,255,255,0.05), transparent);
            transform: rotate(45deg);
            animation: shine 4s infinite linear;
            pointer-events: none;
        }

        @keyframes shine {
            0% { transform: rotate(45deg) translateY(-100%); }
            100% { transform: rotate(45deg) translateY(100%); }
        }

        .savings-amount {
            font-size: 1.4em;
            display: block;
            margin-top: 5px;
            color: #fff;
        }

        .fd-amount {
            color: var(--accent-gold);
            text-shadow: 0 0 15px rgba(255, 183, 0, 0.6);
        }
        
        .savings-neutral {
            border-color: var(--text-muted);
            color: var(--text-light);
            background: #222;
            text-shadow: none;
            box-shadow: none;
        }

        @media (max-width: 900px) {
            .comparison-grid { grid-template-columns: 1fr; }
            .header h1 { font-size: 2.5em; }
            .savings-box { font-size: 1.4em; }
        }
    </style>
</head>
<body>

    <div class="header">
        <h1>Sahi Chuna Kya</h1>
        <p>SYSTEM BOOT: COMPARISON MATRIX ACTIVE</p>
    </div>

    <div class="dashboard-container">
        <div class="control-panel">
            <div class="input-group">
                <label for="variantA">SELECT VEHICLE ALPHA</label>
                <select id="variantA"></select>
            </div>
            <div class="input-group">
                <label for="variantB">SELECT VEHICLE BETA</label>
                <select id="variantB"></select>
            </div>
            <div class="input-group">
                <label for="monthlyKm">EST. RUNNING (KM/MONTH)</label>
                <input type="number" id="monthlyKm" value="1000" min="100" step="100">
            </div>
            <div class="input-group">
                <label for="tenure">TENURE (YEARS)</label>
                <select id="tenure">
                    <option value="1">1 Year</option>
                    <option value="2">2 Years</option>
                    <option value="3">3 Years</option>
                    <option value="4">4 Years</option>
                    <option value="5" selected>5 Years</option>
                    <option value="6">6 Years</option>
                    <option value="7">7 Years (Max)</option>
                </select>
            </div>
        </div>

        <div class="comparison-grid">
            <div class="variant-card" id="cardA">
                <div class="odometer-display">
                    <h3 id="nameA">LOADING...</h3>
                </div>
                <div class="data-row"><span>On-Road Valuation</span><span id="priceA">-</span></div>
                <div class="data-row spec-highlight"><span>Mileage</span><span id="mileageA">-</span></div>
                <div class="data-row spec-highlight"><span>Fuel Rate</span><span id="fuelRateA">-</span></div>
                <div class="data-row"><span>Financed Amount (80%)</span><span id="loanA">-</span></div>
                <div class="data-row"><span>Initial Capital</span><span id="downA">-</span></div>
                <div class="data-row"><span>Monthly Instalment (<span class="dyn-tenure">5</span>Y)</span><span id="emiA">-</span></div>
                <div class="data-row"><span>Total Finance Cost</span><span id="totalEmiA">-</span></div>
                <div class="data-row"><span>Energy Cost (<span class="dyn-tenure">5</span>Y)</span><span id="fuelA">-</span></div>
                <div class="data-row total-cost"><span>Total System Cost</span><span id="totalCostA">-</span></div>
            </div>
            
            <div class="variant-card" id="cardB">
                <div class="odometer-display">
                    <h3 id="nameB">LOADING...</h3>
                </div>
                <div class="data-row"><span>On-Road Valuation</span><span id="priceB">-</span></div>
                <div class="data-row spec-highlight"><span>Mileage</span><span id="mileageB">-</span></div>
                <div class="data-row spec-highlight"><span>Fuel Rate</span><span id="fuelRateB">-</span></div>
                <div class="data-row"><span>Financed Amount (80%)</span><span id="loanB">-</span></div>
                <div class="data-row"><span>Initial Capital</span><span id="downB">-</span></div>
                <div class="data-row"><span>Monthly Instalment (<span class="dyn-tenure">5</span>Y)</span><span id="emiB">-</span></div>
                <div class="data-row"><span>Total Finance Cost</span><span id="totalEmiB">-</span></div>
                <div class="data-row"><span>Energy Cost (<span class="dyn-tenure">5</span>Y)</span><span id="fuelB">-</span></div>
                <div class="data-row total-cost"><span>Total System Cost</span><span id="totalCostB">-</span></div>
            </div>
        </div>

        <div class="savings-box" id="savingsBox">
            AWAITING INPUT...
        </div>
    </div>

    <script>
        // Data populated from Excel
        const variantsData = [{"variant": "BALENO SIGMA 1.2L 5MT", "on_road_price": 681390, "mileage": 22.35, "fuel_price": 115}, {"variant": "BALENO DELTA 1.2L 5MT", "on_road_price": 785420, "mileage": 22.35, "fuel_price": 115}, {"variant": "BALENO ZETA 1.2L 5MT", "on_road_price": 892854, "mileage": 22.35, "fuel_price": 115}, {"variant": "BALENO ALPHA 1.2L 5MT", "on_road_price": 1014079, "mileage": 22.35, "fuel_price": 115}, {"variant": "BALENO DELTA 1.2L AGS", "on_road_price": 840515, "mileage": 22.94, "fuel_price": 115}, {"variant": "BALENO ZETA 1.2L AGS", "on_road_price": 948871, "mileage": 22.94, "fuel_price": 115}, {"variant": "BALENO ALPHA 1.2L AGS", "on_road_price": 1069470, "mileage": 22.94, "fuel_price": 115}, {"variant": "BALENO DELTA CNG 1.2L 5MT", "on_road_price": 891054, "mileage": 30.61, "fuel_price": 104}, {"variant": "BALENO ZETA CNG 1.2L 5MT", "on_road_price": 998923, "mileage": 30.61, "fuel_price": 104}, {"variant": "FRONX SIGMA 1.2L 5MT", "on_road_price": 776637, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX DELTA 1.2L 5MT", "on_road_price": 875783, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX DELTA+ 1.2L 5MT", "on_road_price": 919409, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX DELTA 1.2L AGS", "on_road_price": 930868, "mileage": 22.89, "fuel_price": 115}, {"variant": "FRONX DELTA+ 1.2L AGS", "on_road_price": 974490, "mileage": 22.89, "fuel_price": 115}, {"variant": "FRONX TURBO DELTA+ 1.0L 5MT", "on_road_price": 1000030, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX TURBO ZETA 1.0L 5MT", "on_road_price": 1086434, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX TURBO ALPHA 1.0L 5MT", "on_road_price": 1212398, "mileage": 21.79, "fuel_price": 115}, {"variant": "FRONX TURBO ZETA 1.0L 6AT", "on_road_price": 1261122, "mileage": 22.89, "fuel_price": 115}, {"variant": "FRONX TURBO ALPHA 1.0L 6AT", "on_road_price": 1358480, "mileage": 22.89, "fuel_price": 115}, {"variant": "FRONX SIGMA CNG 1.2L 5MT", "on_road_price": 891941, "mileage": 28.51, "fuel_price": 104}, {"variant": "FRONX DELTA CNG 1.2L 5MT", "on_road_price": 985637, "mileage": 28.51, "fuel_price": 104}, {"variant": "GRAND VITARA SIGMA 1.5L 5MT", "on_road_price": 1240470, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA DELTA 1.5L 5MT", "on_road_price": 1398900, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA ZETA 1.5L 5MT", "on_road_price": 1580345, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA ZETA(O) 1.5L 5MT", "on_road_price": 1596306, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA 1.5L 5MT", "on_road_price": 1749792, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA(O) 1.5L 5MT", "on_road_price": 1767173, "mileage": 21.11, "fuel_price": 115}, {"variant": "GRAND VITARA DELTA 1.5L 6AT", "on_road_price": 1551146, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA ZETA 1.5L 6AT", "on_road_price": 1734369, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA ZETA(O) 1.5L 6AT", "on_road_price": 1750487, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA 1.5L 6AT", "on_road_price": 1905477, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA(O) 1.5L 6AT", "on_road_price": 1921479, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA4WD 1.5L 6AT", "on_road_price": 2071211, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA(O)4WD 1.5L 6AT", "on_road_price": 2137392, "mileage": 20.58, "fuel_price": 115}, {"variant": "GRAND VITARA DELTA+ 1.5L CVT", "on_road_price": 1915307, "mileage": 27.97, "fuel_price": 115}, {"variant": "GRAND VITARA ZETA+ 1.5L CVT", "on_road_price": 2061954, "mileage": 27.97, "fuel_price": 115}, {"variant": "GRAND VITARA ZETA+(O) 1.5L CVT", "on_road_price": 2129047, "mileage": 27.97, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA+ 1.5L CVT", "on_road_price": 2243233, "mileage": 27.97, "fuel_price": 115}, {"variant": "GRAND VITARA ALPHA+(O) 1.5L CVT", "on_road_price": 2251007, "mileage": 27.97, "fuel_price": 115}, {"variant": "GRAND VITARA DELTA CNG 1.5L 5MT", "on_road_price": 1496002, "mileage": 26.6, "fuel_price": 104}, {"variant": "GRAND VITARA ZETA CNG 1.5L 5MT", "on_road_price": 1677510, "mileage": 26.6, "fuel_price": 104}, {"variant": "XL6 ZETA 1.5L 5MT", "on_road_price": 1336091, "mileage": 20.97, "fuel_price": 115}, {"variant": "XL6 ALPHA 1.5L 5MT", "on_road_price": 1448507, "mileage": 20.97, "fuel_price": 115}, {"variant": "XL6 ALPHA+ 1.5L 5MT", "on_road_price": 1503763, "mileage": 20.97, "fuel_price": 115}, {"variant": "XL6 ZETA 1.5L 6AT", "on_road_price": 1492551, "mileage": 20.27, "fuel_price": 115}, {"variant": "XL6 ALPHA 1.5L 6AT", "on_road_price": 1602947, "mileage": 20.27, "fuel_price": 115}, {"variant": "XL6 ALPHA+ 1.5L 6AT", "on_road_price": 1658202, "mileage": 20.27, "fuel_price": 115}, {"variant": "XL6 ZETA CNG 1.5L 5MT", "on_road_price": 1447048, "mileage": 26.32, "fuel_price": 104}, {"variant": "JIMNY ZETA 1.5L 5MT", "on_road_price": 1440507, "mileage": 16.94, "fuel_price": 115}, {"variant": "JIMNY ALPHA 1.5L 5MT", "on_road_price": 1545229, "mileage": 16.94, "fuel_price": 115}, {"variant": "JIMNY ZETA 1.5L 4AT", "on_road_price": 1561561, "mileage": 16.39, "fuel_price": 115}, {"variant": "JIMNY ALPHA 1.5L 4AT", "on_road_price": 1666282, "mileage": 16.39, "fuel_price": 115}, {"variant": "INVICTO ZETA+ 2.0L CVT 7 STR", "on_road_price": 2960369, "mileage": 23.24, "fuel_price": 115}, {"variant": "INVICTO ZETA+ 2.0L CVT 8 STR", "on_road_price": 3007531, "mileage": 23.24, "fuel_price": 115}, {"variant": "INVICTO ALPHA+ 2.0L CVT 7 STR", "on_road_price": 3401373, "mileage": 23.24, "fuel_price": 115}];

        const formatCurrency = (val) => {
            return '₹ ' + new Intl.NumberFormat('en-IN', { maximumFractionDigits: 0 }).format(val);
        };

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
            
            // Net Capital Out of Pocket for the vehicle itself (Downpayment + Total EMIs)
            const vehicleCapitalCost = downpayment + totalEmi;

            const totalCost = vehicleCapitalCost + fuelCost;
            
            return {
                onRoadPrice, loanAmount, downpayment, emi, totalEmi, vehicleCapitalCost, fuelCost, totalCost
            };
        }

        function animateValue(obj, start, end, duration) {
            let startTimestamp = null;
            const step = (timestamp) => {
                if (!startTimestamp) startTimestamp = timestamp;
                const progress = Math.min((timestamp - startTimestamp) / duration, 1);
                const easeProgress = 1 - Math.pow(1 - progress, 4);
                obj.innerHTML = formatCurrency(Math.floor(easeProgress * (end - start) + start));
                if (progress < 1) {
                    window.requestAnimationFrame(step);
                }
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

            // Populate Specs
            const isCngA = varA.variant.includes('CNG');
            document.getElementById('mileageA').innerText = `${varA.mileage} ${isCngA ? 'Km/Kg' : 'Km/L'}`;
            document.getElementById('fuelRateA').innerText = `${formatCurrency(varA.fuel_price)} ${isCngA ? '/ Kg' : '/ L'}`;

            const isCngB = varB.variant.includes('CNG');
            document.getElementById('mileageB').innerText = `${varB.mileage} ${isCngB ? 'Km/Kg' : 'Km/L'}`;
            document.getElementById('fuelRateB').innerText = `${formatCurrency(varB.fuel_price)} ${isCngB ? '/ Kg' : '/ L'}`;

            // Update Card A
            document.getElementById('nameA').innerText = varA.variant;
            document.getElementById('priceA').innerText = formatCurrency(costA.onRoadPrice);
            document.getElementById('loanA').innerText = formatCurrency(costA.loanAmount);
            document.getElementById('downA').innerText = formatCurrency(costA.downpayment);
            document.getElementById('emiA').innerText = formatCurrency(costA.emi);
            document.getElementById('totalEmiA').innerText = formatCurrency(costA.totalEmi);
            document.getElementById('fuelA').innerText = formatCurrency(costA.fuelCost);
            animateValue(document.getElementById('totalCostA'), 0, costA.totalCost, 1200);

            // Update Card B
            document.getElementById('nameB').innerText = varB.variant;
            document.getElementById('priceB').innerText = formatCurrency(costB.onRoadPrice);
            document.getElementById('loanB').innerText = formatCurrency(costB.loanAmount);
            document.getElementById('downB').innerText = formatCurrency(costB.downpayment);
            document.getElementById('emiB').innerText = formatCurrency(costB.emi);
            document.getElementById('totalEmiB').innerText = formatCurrency(costB.totalEmi);
            document.getElementById('fuelB').innerText = formatCurrency(costB.fuelCost);
            animateValue(document.getElementById('totalCostB'), 0, costB.totalCost, 1200);

            // Total System Difference
            const diff = costA.totalCost - costB.totalCost;
            const absDiff = Math.abs(diff);

            // Exact difference in Vehicle Capital Paid (Downpayment + EMIs, excluding fuel)
            const vehicleCapitalDiff = costA.vehicleCapitalCost - costB.vehicleCapitalCost;
            const fdPrincipal = Math.abs(vehicleCapitalDiff);
            
            // Fixed Deposit Return Logic (7% ROI, Compounded Quarterly)
            const r_fd = 0.07;
            const n_compounding = 4; // Quarterly compounding
            const fdMaturity = fdPrincipal * Math.pow(1 + (r_fd / n_compounding), n_compounding * tenureYears);

            const savingsBox = document.getElementById('savingsBox');
            savingsBox.classList.remove('savings-neutral');
            
            // Determine winner based on overall cost
            let winner = diff > 0 ? varB.variant : varA.variant;

            if (diff !== 0) {
                savingsBox.innerHTML = `
                    OPTIMAL ROUTE: <span style="color:#fff">${winner}</span><br>
                    <span style="font-size:0.5em; color:var(--text-light); letter-spacing: 2px;">TOTAL SYSTEM SAVINGS (${tenureYears} YEARS)</span>
                    <span class="savings-amount">${formatCurrency(absDiff)}</span>
                    
                    <div style="background: rgba(0,0,0,0.4); border-radius: 10px; padding: 15px; margin-top: 15px; font-size: 0.65em; text-align: left; line-height: 1.8; letter-spacing: 1px;">
                        <div style="display: flex; justify-content: space-between; border-bottom: 1px dashed #444; padding-bottom: 5px; margin-bottom: 5px;">
                            <span style="color: var(--text-light);">VEHICLE COST DIFFERENCE (FD PRINCIPAL):</span>
                            <span style="color: #fff; font-weight: bold;">${formatCurrency(fdPrincipal)}</span>
                        </div>
                        <div style="display: flex; justify-content: space-between;">
                            <span style="color: var(--text-light);">FD MATURITY AFTER ${tenureYears}Y (@ 7% P.A.):</span>
                            <span class="fd-amount" style="margin-top:0; font-weight: bold;">${formatCurrency(fdMaturity)}</span>
                        </div>
                    </div>
                `;
                savingsBox.style.borderColor = 'var(--accent-green)';
                savingsBox.style.color = 'var(--accent-green)';
                savingsBox.style.boxShadow = '0 0 30px rgba(0, 255, 136, 0.1), inset 0 0 20px rgba(0, 255, 136, 0.05)';
            } else {
                savingsBox.innerHTML = `PARITY ACHIEVED<br><span style="font-size:0.5em; color:#fff;">NO FISCAL VARIANCE DETECTED</span>`;
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

            if(variantsData.length > 1) {
                selectA.selectedIndex = 0; 
                selectB.selectedIndex = 7; 
            }

            selectA.addEventListener('change', updateDashboard);
            selectB.addEventListener('change', updateDashboard);
            document.getElementById('monthlyKm').addEventListener('input', updateDashboard);
            document.getElementById('tenure').addEventListener('change', updateDashboard);

            updateDashboard(); 
        };
    </script>
</body>
</html>
