<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>پنل حرفه ای V2Ray</title>
    <style>
        :root {
            --neon-blue: #00f3ff;
            --deep-space: #0a0a2e;
            --cyber-purple: #8a2be2;
            --matrix-green: #00ff00;
        }

        body {
            margin: 0;
            padding: 0;
            background: var(--deep-space);
            font-family: 'Segoe UI', Tahoma, sans-serif;
            height: 100vh;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        #loader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--deep-space);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            transition: opacity 0.5s;
        }

        .cyber-spinner {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background: conic-gradient(
                var(--neon-blue) 0%,
                var(--cyber-purple) 30%,
                transparent 70%
            );
            position: relative;
            animation: spin 1.5s linear infinite;
            box-shadow: 0 0 40px var(--neon-blue);
        }

        .cyber-spinner::after {
            content: '';
            position: absolute;
            inset: 5px;
            background: var(--deep-space);
            border-radius: 50%;
        }

        .main-content {
            text-align: center;
            opacity: 0;
            animation: contentFade 1s 3s forwards;
        }

        .cyber-title {
            font-size: 2.5rem;
            background: linear-gradient(45deg, var(--neon-blue), var(--cyber-purple));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 1.5rem;
            text-shadow: 0 0 15px rgba(0, 243, 255, 0.5);
        }

        .cyber-subtitle {
            color: rgba(255, 255, 255, 0.9);
            font-size: 1.2rem;
            margin-bottom: 3rem;
            line-height: 1.6;
        }

        /* استایل دکمه‌ها */
        .whatsapp-btn,
        .price-btn {
            color: white;
            padding: 18px 45px;
            border: none;
            border-radius: 50px;
            font-size: 1.3rem;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            margin: 10px;
        }

        .whatsapp-btn {
            background: linear-gradient(135deg, var(--neon-blue) 0%, var(--cyber-purple) 100%);
            box-shadow: 0 0 25px var(--neon-blue);
        }

        .price-btn {
            background: linear-gradient(135deg, var(--matrix-green) 0%, var(--neon-blue) 100%);
            box-shadow: 0 0 25px var(--matrix-green);
        }

        .whatsapp-btn::before,
        .price-btn::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255,255,255,0.2), transparent);
            transform: rotate(45deg);
            animation: btnGlow 3s infinite;
        }

        .whatsapp-btn:hover,
        .price-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 0 40px var(--neon-blue);
        }

        /* استایل مودال */
        .price-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 1000;
            overflow-y: auto;
        }

        .modal-content {
            background: var(--deep-space);
            max-width: 800px;
            margin: 50px auto;
            padding: 30px;
            border-radius: 15px;
            border: 2px solid var(--neon-blue);
            box-shadow: 0 0 40px var(--neon-blue);
            color: white;
            position: relative;
            line-height: 1.8;
            max-height: 80vh;
            overflow-y: auto;
        }

        .close-modal {
            position: absolute;
            top: 15px;
            left: 20px;
            color: var(--neon-blue);
            font-size: 30px;
            cursor: pointer;
            transition: 0.3s;
        }

        .close-modal:hover {
            transform: rotate(90deg);
        }

        /* فوتر */
        .footer {
            position: fixed;
            bottom: 20px;
            width: 100%;
            text-align: center;
            font-family: 'Courier New', monospace;
            color: var(--neon-blue);
            text-shadow: 0 0 10px rgba(0, 243, 255, 0.5);
            font-size: 1rem;
        }

        /* انیمیشن‌ها */
        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        @keyframes contentFade {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes btnGlow {
            0% { left: -50%; }
            100% { left: 150%; }
        }

        .floating {
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
    </style>
</head>
<body>
    <div id="loader">
        <div class="cyber-spinner"></div>
    </div>

    <div class="main-content">
        <div class="floating">
            <h1 class="cyber-title">پیکربندی حرفه ای V2Ray</h1>
        </div>
        <p class="cyber-subtitle">
            بهترین سرویس های کانفیگ با پشتیبانی 24 ساعته
        </p>
        
        <button class="price-btn" onclick="showPriceModal()">
            <span>📋</span>
            مشاهده لیست قیمت
            <span>💎</span>
        </button>

        <button class="whatsapp-btn" onclick="window.open('https://wa.me/989999248297')">
            <span>💎</span>
            ارتباط در واتساپ
            <span>🚀</span>
        </button>
    </div>

    <!-- مودال لیست قیمت -->
    <div class="price-modal" id="priceModal">
        <div class="modal-content">
            <span class="close-modal" onclick="closePriceModal()">&times;</span>
            <div class="modal-text">
                <h2 style="color: var(--neon-blue); text-align: center; margin-bottom: 25px;">لیست قیمت کانفیگ V2Ray</h2>
                
                <strong>پلن‌های یک‌ماهه (تک کاربر):</strong><br>
                ▪️ ۱۰ گیگ: ۲۵,۰۰۰ تومان<br>
                ▪️ ۲۰ گیگ: ۵۰,۰۰۰ تومان<br>
                ▪️ ۳۰ گیگ: ۷۵,۰۰۰ تومان<br>
                ▪️ ۴۰ گیگ: ۱۰۰,۰۰۰ تومان<br>
                ▪️ ۵۰ گیگ: ۱۲۵,۰۰۰ تومان<br>
                
                <hr>
                
                <strong>پلن‌های یک‌ماهه (دو کاربر):</strong><br>
                ▪️ ۱۰ گیگ: ۳۵,۰۰۰ تومان<br>
                ▪️ ۲۰ گیگ: ۷۰,۰۰۰ تومان<br>
                ▪️ ۳۰ گیگ: ۱۰۵,۰۰۰ تومان<br>
                ▪️ ۴۰ گیگ: ۱۴۰,۰۰۰ تومان<br>
                ▪️ ۵۰ گیگ: ۱۷۵,۰۰۰ تومان<br>
                
                <hr>
                
                <strong>توضیحات:</strong><br>
                ▪️ هر گیگابایت در پلن‌های تک کاربر به طور میانگین ۲,۵۰۰ تومان<br>
                ▪️ در پلن‌های دو کاربر به طور میانگین ۳,۵۰۰ تومان<br>
                ▪️ قیمت هر گیگابایت پس از خرید ثابت می‌ماند<br>
                
                <hr>
                
                <strong style="color: var(--matrix-green);">تخفیف‌های ویژه:</strong><br>
                💎 خرید سوم: ۱۵,۰۰۰ تومان تخفیف<br>
                🎁 معرفی سه نفر: کانفیگ رایگان یک‌ماهه<br>
                
                <hr>
                
                <div style="text-align: center; margin-top: 25px;">
                    <strong>راه های ارتباطی:</strong><br>
                    📱 واتساپ: 09999248297<br>
                    ✈️ تلگرام: @v2rayng_baloch13<br>
                    🔷 روبیکا: @pe3ar4k_baloch<br>
                </div>
            </div>
        </div>
    </div>

    <!-- فوتر انگلیسی -->
    <div class="footer">
        Crafted with ♥ by Balooch
    </div>

    <script>
        // مدیریت لودر
        setTimeout(() => {
            document.getElementById('loader').style.opacity = '0';
            setTimeout(() => {
                document.getElementById('loader').style.display = 'none';
            }, 500);
        }, 3000);

        // مدیریت مودال
        function showPriceModal() {
            document.getElementById('priceModal').style.display = 'block';
        }

        function closePriceModal() {
            document.getElementById('priceModal').style.display = 'none';
        }

        // بستن مودال با کلیک خارج از آن
        window.onclick = function(event) {
            const modal = document.getElementById('priceModal');
            if (event.target == modal) {
                modal.style.display = 'none';
            }
        }
    </script>
</body>
</html>
