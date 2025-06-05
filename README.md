<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تطبيق التنبؤ بسباق الخيل</title>
    <link rel="manifest" href="data:application/json;base64,eyJuYW1lIjoi2KrYt9io2YrZgiDYp9mE2KrZhtio2KTYqCDYqNiz2KjYp9mCINin2YTYrtmK2YQiLCJzaG9ydF9uYW1lIjoi2LPYqNin2YIg2KfZhNiu2YrZhCIsInN0YXJ0X3VybCI6Ii8iLCJkaXNwbGF5Ijoic3RhbmRhbG9uZSIsImJhY2tncm91bmRfY29sb3IiOiIjNjY3ZWVhIiwidGhlbWVfY29sb3IiOiIjNjY3ZWVhIiwiaWNvbnMiOlt7InNyYyI6ImRhdGE6aW1hZ2Uvc3ZnK3htbDtiYXNlNjQsUEhOMlp5QjNhV1IwYUQwaU1qUWlJR2hsYVdkb2REMGlNalFpSUhabGNuTnBiMjQ5SWpFdU1TSWdlRzFzYm5NOUltaDBkSEE2THk5M2QzY3Vkek11YjNKbkx6SXdNREF2YzNabklpQm1hV3hzUFNJak5qWTNaV1ZoSWo0OGNHRjBhQ0JrUFNKTk9TNHpJRGN1TjBzeE1TNDFMUzQzVGpFeklERXlTRGM0VERneUxqVXVOa3N4TlMweElIWXhNbWd6TG5oMklpQm1hV3hzUFNKamRYSXlJaUF2UGp4d1lYUm9JR1E5SWswM0lEY3VObmd4TWk0MElEY3VObE0wUWk0eVNEUlJJRGRNT1M0MklEa3VORXcyTGpkekxqVXVOV3hnTVM0d05HMDVMalF3TlNBdUxqRnRPUzR0TWk0MU5IWXRNUzQ0U2pWRE56UXVPU0EyTGprZ056TXVNeUEyTGpFek56TXVOR1U0UW1JMElqNHZQand2YzNabkNnPT0iLCJzaXplcyI6IjUxMng1MTIiLCJ0eXBlIjoiaW1hZ2Uvc3ZnK3htbCJ9XX0=">
    <meta name="theme-color" content="#667eea">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 10px;
            color: #333;
            overflow-x: hidden;
        }

        .container {
            max-width: 500px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            backdrop-filter: blur(10px);
            animation: slideUp 0.8s ease-out;
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .header {
            text-align: center;
            margin-bottom: 25px;
            animation: fadeIn 1s ease-out 0.3s both;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .header h1 {
            color: #2c3e50;
            font-size: 24px;
            margin-bottom: 8px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }

        .header p {
            color: #7f8c8d;
            font-size: 14px;
        }

        .form-group {
            margin-bottom: 15px;
            animation: slideIn 0.6s ease-out forwards;
            opacity: 0;
        }

        .form-group:nth-child(1) { animation-delay: 0.1s; }
        .form-group:nth-child(2) { animation-delay: 0.2s; }
        .form-group:nth-child(3) { animation-delay: 0.3s; }
        .form-group:nth-child(4) { animation-delay: 0.4s; }
        .form-group:nth-child(5) { animation-delay: 0.5s; }
        .form-group:nth-child(6) { animation-delay: 0.6s; }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .form-group label {
            display: block;
            margin-bottom: 6px;
            font-weight: bold;
            color: #2c3e50;
            font-size: 13px;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e1e8ed;
            border-radius: 12px;
            font-size: 16px;
            background: #f8f9fa;
            transition: all 0.3s ease;
            -webkit-appearance: none;
            -moz-appearance: textfield;
        }

        .form-group input::-webkit-outer-spin-button,
        .form-group input::-webkit-inner-spin-button {
            -webkit-appearance: none;
            margin: 0;
        }

        .form-group input:focus, .form-group select:focus {
            outline: none;
            border-color: #667eea;
            background: white;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
            transform: scale(1.02);
        }

        .btn {
            width: 100%;
            padding: 15px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 20px;
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }

        .btn:hover::before {
            left: 100%;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 25px rgba(102, 126, 234, 0.4);
        }

        .btn:active {
            transform: translateY(-1px);
        }

        .btn:disabled {
            opacity: 0.7;
            cursor: not-allowed;
            transform: none;
        }

        .results {
            margin-top: 25px;
            padding: 20px;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            border-radius: 15px;
            color: white;
            display: none;
            animation: bounceIn 0.8s ease-out;
        }

        @keyframes bounceIn {
            0% {
                opacity: 0;
                transform: scale(0.3);
            }
            50% {
                opacity: 1;
                transform: scale(1.05);
            }
            70% {
                transform: scale(0.9);
            }
            100% {
                opacity: 1;
                transform: scale(1);
            }
        }

        .results h3 {
            margin-bottom: 15px;
            font-size: 18px;
            text-align: center;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
        }

        .schema-item {
            background: rgba(255,255,255,0.2);
            padding: 12px;
            margin: 8px 0;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            font-size: 13px;
            word-break: break-all;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255,255,255,0.3);
            transition: transform 0.2s ease;
        }

        .schema-item:hover {
            transform: translateX(5px);
        }

        .phase-separator {
            text-align: center;
            margin: 25px 0 20px;
            padding: 12px;
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            border-radius: 12px;
            color: #d63031;
            font-weight: bold;
            font-size: 16px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }

        .loading {
            display: none;
            text-align: center;
            margin: 20px 0;
            animation: pulse 1.5s ease-in-out infinite alternate;
        }

        @keyframes pulse {
            from {
                opacity: 0.6;
            }
            to {
                opacity: 1;
            }
        }

        .loading-spinner {
            border: 4px solid rgba(102, 126, 234, 0.3);
            border-top: 4px solid #667eea;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin: 0 auto 15px;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .input-row {
            display: flex;
            gap: 10px;
        }

        .input-row .form-group {
            flex: 1;
        }

        .highlight {
            background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
            padding: 15px;
            border-radius: 12px;
            margin: 10px 0;
            font-weight: bold;
            text-align: center;
            color: #2c3e50;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from {
                box-shadow: 0 4px 12px rgba(0,0,0,0.1);
            }
            to {
                box-shadow: 0 8px 20px rgba(102, 126, 234, 0.3);
            }
        }

        .copy-btn {
            background: rgba(255,255,255,0.3);
            border: 1px solid rgba(255,255,255,0.5);
            color: white;
            padding: 8px 12px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 12px;
            margin-top: 8px;
            transition: all 0.3s ease;
        }

        .copy-btn:hover {
            background: rgba(255,255,255,0.5);
            transform: scale(1.05);
        }

        .toast {
            position: fixed;
            top: 20px;
            right: 20px;
            background: #27ae60;
            color: white;
            padding: 12px 20px;
            border-radius: 8px;
            display: none;
            z-index: 1000;
            animation: slideInRight 0.3s ease-out;
        }

        @keyframes slideInRight {
            from {
                transform: translateX(100%);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        .install-prompt {
            background: linear-gradient(135deg, #27ae60 0%, #2ecc71 100%);
            color: white;
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 20px;
            text-align: center;
            display: none;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .install-prompt:hover {
            transform: scale(1.02);
        }

        @media (max-width: 600px) {
            .container {
                margin: 5px;
                padding: 15px;
                border-radius: 15px;
            }
            
            .header h1 {
                font-size: 20px;
            }
            
            .form-group input {
                padding: 10px 12px;
                font-size: 16px;
            }
            
            .btn {
                padding: 12px;
                font-size: 16px;
            }
            
            .input-row {
                flex-direction: column;
                gap: 0;
            }
        }

        @media (orientation: landscape) and (max-height: 500px) {
            .container {
                padding: 10px;
            }
            
            .form-group {
                margin-bottom: 10px;
            }
            
            .phase-separator {
                margin: 15px 0 10px;
                padding: 8px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="install-prompt" id="installPrompt">
            📱 اضغط هنا لتثبيت التطبيق على هاتفك
        </div>

        <div class="header">
            <h1>🏇 تطبيق التنبؤ بسباق الخيل</h1>
            <p>احسب توقعاتك بدقة عالية</p>
        </div>

        <form id="predictionForm">
            <!-- المعلومات الأساسية -->
            <div class="form-group">
                <label>رقم الاجتماع (R):</label>
                <input type="number" id="reunionNum" min="1" required>
            </div>

            <div class="form-group">
                <label>رقم السباق (C):</label>
                <input type="number" id="courseNum" min="1" required>
            </div>

            <div class="input-row">
                <div class="form-group">
                    <label>اليوم (1-31):</label>
                    <input type="number" id="jour" min="1" max="31" required>
                </div>
                <div class="form-group">
                    <label>الشهر (1-12):</label>
                    <input type="number" id="mois" min="1" max="12" required>
                </div>
            </div>

            <div class="phase-separator">
                📊 المرحلة الأولى
            </div>

            <div class="form-group">
                <label>العدد العام (عدد الخيول):</label>
                <input type="number" id="nombreGeneral1" min="1" required>
            </div>

            <div class="phase-separator">
                📈 المرحلة الثانية
            </div>

            <div class="form-group">
                <label>الرقم Y للمرحلة الثانية:</label>
                <input type="number" id="nombreY2" required>
            </div>

            <div class="form-group">
                <label>الأرقام المحظورة (مفصولة بمسافات):</label>
                <input type="text" id="interdits" placeholder="مثال: 2 5 8">
            </div>

            <div class="form-group">
                <label>رقمك المفضل:</label>
                <input type="number" id="favori" required>
            </div>

            <button type="submit" class="btn" id="calculateBtn">
                🔮 احسب التوقعات
            </button>
        </form>

        <div class="loading" id="loading">
            <div class="loading-spinner"></div>
            <p>⚡ جاري حساب التوقعات...</p>
        </div>

        <div class="results" id="results">
            <h3>🎯 النتائج المحسوبة</h3>
            <div id="schemasResults"></div>
        </div>
    </div>

    <div class="toast" id="toast">
        تم النسخ بنجاح! ✅
    </div>

    <script>
        // المتغيرات العامة
        let R, C;
        let deferredPrompt;
        
        // PWA Installation
        window.addEventListener('beforeinstallprompt', (e) => {
            e.preventDefault();
            deferredPrompt = e;
            document.getElementById('installPrompt').style.display = 'block';
        });

        document.getElementById('installPrompt').addEventListener('click', async () => {
            if (deferredPrompt) {
                deferredPrompt.prompt();
                const { outcome } = await deferredPrompt.userChoice;
                deferredPrompt = null;
                document.getElementById('installPrompt').style.display = 'none';
            }
        });

        // Service Worker Registration
        if ('serviceWorker' in navigator) {
            window.addEventListener('load', () => {
                const swScript = `
                    const CACHE_NAME = 'horse-racing-v1';
                    const urlsToCache = ['/'];
                    
                    self.addEventListener('install', (event) => {
                        event.waitUntil(
                            caches.open(CACHE_NAME)
                                .then((cache) => cache.addAll(urlsToCache))
                        );
                    });
                    
                    self.addEventListener('fetch', (event) => {
                        event.respondWith(
                            caches.match(event.request)
                                .then((response) => response || fetch(event.request))
                        );
                    });
                `;
                
                const blob = new Blob([swScript], { type: 'application/javascript' });
                const swUrl = URL.createObjectURL(blob);
                
                navigator.serviceWorker.register(swUrl)
                    .then(() => console.log('SW registered'))
                    .catch(() => console.log('SW registration failed'));
            });
        }
        
        // تحويل الكود Python إلى JavaScript
        function getUniqueNonzeroFrequencies(frequencies, exclude = []) {
            for (let [chiffre, _] of frequencies) {
                if (chiffre !== 0 && !exclude.includes(chiffre)) {
                    return chiffre;
                }
            }
            return null;
        }

        function genererPartieSommeUnique(partieGauche, interdits) {
            let chiffres = partieGauche.split('_').map(n => parseInt(n));
            chiffres = chiffres.filter(x => !interdits.includes(x));
            
            let uniques = [];
            for (let x of chiffres) {
                if (!uniques.includes(x)) {
                    uniques.push(x);
                }
            }
            
            let sommes = [];
            for (let i = 0; i < uniques.length; i++) {
                for (let j = i + 1; j < uniques.length; j++) {
                    let s = uniques[i] + uniques[j];
                    if (!interdits.includes(s) && !sommes.includes(s)) {
                        sommes.push(s);
                    }
                }
            }
            
            if (chiffres.length >= 2) {
                let sommeSupp = chiffres[chiffres.length - 1] + chiffres[chiffres.length - 2];
                if (!interdits.includes(sommeSupp) && !sommes.includes(sommeSupp)) {
                    sommes.push(sommeSupp);
                }
            }
            
            return sommes.sort((a, b) => a - b).slice(0, 4).join('_');
        }

        function removeDuplicatesInSchema(partieGauche, partieDroite, interdits) {
            let gauche = partieGauche.split('_').map(x => parseInt(x)).filter(x => !interdits.includes(x));
            let droite = partieDroite.split('_').map(x => parseInt(x)).filter(x => !interdits.includes(x));
            
            let droiteFiltre = [];
            for (let num of droite) {
                if (!gauche.includes(num) && !interdits.includes(num) && !droiteFiltre.includes(num)) {
                    droiteFiltre.push(num);
                }
            }
            
            return [gauche.join('_'), droiteFiltre.join('_')];
        }

        function filtrerSuperieurs(valeurs, limite) {
            return valeurs.filter(x => x <= limite);
        }

        function countFrequencies(arr) {
            let counts = {};
            arr.forEach(x => counts[x] = (counts[x] || 0) + 1);
            return Object.entries(counts).map(([k, v]) => [parseInt(k), v]).sort((a, b) => b[1] - a[1]);
        }

        function calculSchema() {
            // الحصول على القيم من النموذج
            const jour = parseInt(document.getElementById('jour').value);
            const mois = parseInt(document.getElementById('mois').value);
            const nombreGeneral1 = parseInt(document.getElementById('
