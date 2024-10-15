<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>eCommerce Store</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Roboto', sans-serif;
        }

        body {
            background-color: #f4f4f4;
            color: #333;
            display: flex;
            flex-direction: column;
            min-height: 100vh;
            overflow-x: hidden;
        }

        header {
            width: 100%;
            height: 80px;
            background-color: #282c34;
            color: #fff;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 20px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .logo {
            font-size: 28px;
            font-weight: 700;
            letter-spacing: 1px;
        }

        .header-content {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        /* General styles for search input and button */
        .search-container {
            position: relative;
            display: flex;
            align-items: center;
        }

        .search-input {
            width: 0;
            padding: 0;
            border: 1px solid #ddd;
            border-radius: 20px;
            background-color: #fff;
            transition: width 0.4s ease-in-out, padding 0.4s ease-in-out;
            font-size: 16px;
            color: #333;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .search-input.open {
            width: 250px;
            /* Adjust as needed */
            padding: 10px;
        }

        .search-button {
            background-color: #ff5722;
            border: none;
            border-radius: 20px;
            color: #fff;
            cursor: pointer;
            font-size: 16px;
            padding: 10px 20px;
            margin-left: 10px;
            transition: background-color 0.3s ease, transform 0.3s ease;
            border: 1px solid transparent;
        }

        .search-button:hover {
            background-color: #e64a19;
            transform: scale(1.05);
        }

        .search-container i {
            position: absolute;
            right: 10px;
            top: 50%;
            transform: translateY(-50%);
            color: #fff;
            font-size: 18px;
        }


        nav {
            background: linear-gradient(135deg, #e0f7fa, #ffffff);
            backdrop-filter: blur(10px);
            display: flex;
            align-items: center;
            justify-content: center;
            height: 80px;
            position: sticky;
            top: 0;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            z-index: 1000;
        }

        nav ul {
            display: flex;
            gap: 30px;
            list-style: none;
            padding: 0;
        }

        nav li {
            font-size: 16px;
            font-weight: 600;
            color: #333;
            position: relative;
            display: flex;
            align-items: center;
        }

        nav li a {
            color: #333;
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: color 0.3s ease;
        }

        nav li a:hover {
            color: #ff5722;
        }

        .nav-icon {
            font-size: 20px;
            color: #ff5722;
        }

        .nav-icon:hover {
            color: #ff5722;
        }

        .hero {
            background-image: url('https://4kwallpapers.com/images/wallpapers/dark-background-abstract-background-network-3d-background-3840x2160-8324.png');
            background-size: cover;
            background-position: center;
            height: 400px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            text-align: center;
            position: relative;
            margin-bottom: 20px;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.4);
        }

        .hero-content {
            position: relative;
            z-index: 1;
        }

        .hero h1 {
            font-size: 48px;
            font-weight: 700;
            margin-bottom: 10px;
        }

        .hero p {
            font-size: 24px;
            margin-top: 10px;
        }

        .cta-button {
            background-color: #ff5722;
            color: #fff;
            padding: 12px 25px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            text-align: center;
            font-size: 16px;
            text-decoration: none;
            margin-top: 20px;
            transition: background-color 0.3s ease;
        }

        .cta-button:hover {
            background-color: #e64a19;
        }

        .main-content {
            padding: 20px;
            max-width: 1200px;
            margin: auto;
        }

        .section {
            margin-bottom: 40px;
        }

        .section h2 {
            font-size: 32px;
            margin-bottom: 20px;
            text-align: center;
            font-weight: 700;
            color: #282c34;
        }

        .product-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: space-between;
        }

        .product-card {
            background: #fff;
            border: 1px solid #ddd;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            flex: 1 1 calc(25% - 20px);
            /* 4 items per row with space between */
            margin-bottom: 20px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
        }

        .product-card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .product-card .info {
            padding: 15px;
        }

        .product-card h3 {
            font-size: 20px;
            margin-bottom: 10px;
            font-weight: 700;
        }

        .product-card p {
            font-size: 16px;
            color: #666;
        }

        .product-card .price {
            font-size: 18px;
            font-weight: 700;
            margin-top: 10px;
            color: #ff5722;
        }

        .price-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background: #ff5722;
            color: #fff;
            padding: 5px 10px;
            border-radius: 4px;
            font-size: 14px;
            font-weight: 700;
        }

        footer {
            background-color: #282c34;
            color: #fff;
            padding: 40px 20px;
            text-align: center;
        }

        .footer-content {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;
        }

        .footer-top {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .footer-logo {
            font-size: 28px;
            font-weight: 700;
            color: #fff;
        }

        .footer-links {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
        }

        .footer-link-section {
            max-width: 200px;
        }

        .footer-link-section h3 {
            font-size: 18px;
            margin-bottom: 10px;
            font-weight: 700;
        }

        .footer-link-section ul {
            list-style: none;
            padding: 0;
        }

        .footer-link-section ul li {
            margin-bottom: 8px;
        }

        .footer-link-section ul li a {
            color: #fff;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-link-section ul li a:hover {
            color: #ff5722;
        }

        .footer-bottom {
            margin-top: 20px;
        }

        .newsletter {
            margin-bottom: 20px;
        }

        .newsletter h3 {
            font-size: 18px;
            font-weight: 700;
            margin-bottom: 10px;
        }

        .newsletter-form {
            display: flex;
            justify-content: center;
            gap: 10px;
        }

        .newsletter-form input {
            padding: 10px;
            font-size: 16px;
            border: none;
            border-radius: 4px;
            width: 250px;
        }

        .newsletter-form button {
            background-color: #ff5722;
            color: #fff;
            border: none;
            padding: 10px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s ease;
        }

        .newsletter-form button:hover {
            background-color: #e64a19;
        }

        .social-icons {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
        }

        .social-icons a {
            color: #fff;
            font-size: 24px;
            transition: color 0.3s ease;
        }

        .social-icons a:hover {
            color: #ff5722;
        }

        footer p {
            font-size: 14px;
            color: #ccc;
        }


        .social-icons {
            display: flex;
            gap: 15px;
        }

        .social-icons a {
            color: #fff;
            font-size: 24px;
            transition: color 0.3s ease;
        }

        .social-icons a:hover {
            color: #ff5722;
        }

        .newsletter {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;
        }

        .newsletter input {
            padding: 10px;
            font-size: 16px;
            border: none;
            border-radius: 4px;
            width: 250px;
            margin-right: 10px;
        }

        .newsletter button {
            background-color: #ff5722;
            color: #fff;
            border: none;
            padding: 10px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s ease;
        }

        .newsletter button:hover {
            background-color: #e64a19;
        }

        footer {
            background-color: #282c34;
            color: #fff;
            padding: 40px 20px;
            text-align: center;
            position: relative;
            bottom: 0;
            width: 100%;
        }

        footer a {
            color: #ff5722;
            text-decoration: none;
            font-weight: 700;
        }

        footer a:hover {
            text-decoration: underline;
        }



        .customer-testimonials {
            background: #f4f4f4;
            padding: 40px 20px;
        }

        .customer-testimonials h2 {
            font-size: 32px;
            margin-bottom: 20px;
            text-align: center;
            font-weight: 700;
            color: #282c34;
        }

        .testimonials-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;
        }

        .testimonial-card {
            background: #fff;
            border: 1px solid #ddd;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            padding: 20px;
            max-width: 600px;
            text-align: center;
        }

        .testimonial-card p {
            font-size: 16px;
            color: #666;
            margin-bottom: 10px;
        }

        .testimonial-card .author {
            font-size: 18px;
            font-weight: 700;
            color: #282c34;
        }

        .featured-collections {
            padding: 40px 20px;
        }

        .featured-collections h2 {
            font-size: 32px;
            margin-bottom: 20px;
            text-align: center;
            font-weight: 700;
            color: #282c34;
        }

        .collections-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: space-between;
        }

        .collection-card {
            background: #fff;
            border: 1px solid #ddd;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            flex: 1 1 calc(33% - 20px);
            /* 3 items per row with space between */
            overflow: hidden;
            margin-bottom: 20px;
            text-align: center;
        }

        .collection-card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .collection-card .info {
            padding: 15px;
        }

        .collection-card h3 {
            font-size: 20px;
            font-weight: 700;
            color: #282c34;
        }

        .blog-section {
            padding: 40px 20px;
        }

        .blog-section h2 {
            font-size: 32px;
            margin-bottom: 20px;
            text-align: center;
            font-weight: 700;
            color: #282c34;
        }

        .blog-post {
            background: #fff;
            border: 1px solid #ddd;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            padding: 20px;
            margin-bottom: 20px;
        }

        .blog-post img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 8px;
        }

        .blog-post h3 {
            font-size: 20px;
            font-weight: 700;
            color: #282c34;
            margin-top: 10px;
        }

        .blog-post p {
            font-size: 16px;
            color: #666;
            margin-top: 10px;
        }

        .contact-section {
            background: #fff;
            padding: 40px 20px;
            text-align: center;
        }

        .contact-section h2 {
            font-size: 32px;
            margin-bottom: 20px;
            font-weight: 700;
            color: #282c34;
        }

        .contact-section p {
            font-size: 16px;
            color: #666;
            margin-bottom: 20px;
        }

        .contact-section form {
            max-width: 600px;
            margin: auto;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .contact-section input,
        .contact-section textarea {
            padding: 10px;
            font-size: 16px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        .contact-section button {
            background-color: #ff5722;
            color: #fff;
            border: none;
            padding: 10px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s ease;
        }

        .contact-section button:hover {
            background-color: #e64a19;
        }

        .fa {
            font-size: 20px;
        }

        .fa-facebook {
            color: #3b5998;
        }

        .fa-twitter {
            color: #1da1f2;
        }

        .fa-instagram {
            color: #e4405f;
        }

        .fa-linkedin {
            color: #0077b5;
        }

        .faq-section {
            background: #f4f4f4;
            padding: 40px 20px;
        }

        .faq-section h2 {
            font-size: 32px;
            margin-bottom: 20px;
            text-align: center;
            font-weight: 700;
            color: #282c34;
        }

        .faq-item {
            background: #fff;
            border: 1px solid #ddd;
            border-radius: 8px;
            margin-bottom: 20px;
            padding: 15px;
        }

        .faq-item h3 {
            font-size: 20px;
            font-weight: 700;
            color: #282c34;
            margin-bottom: 10px;
        }

        .faq-item p {
            font-size: 16px;
            color: #666;
        }




        /* -- External Social Link CSS Styles -- */

        #source-link {
            top: 120px;
        }

        #source-link>i {
            color: rgb(94, 106, 210);
        }

        #yt-link {
            top: 65px;
        }

        #yt-link>i {
            color: rgb(219, 31, 106);

        }

        #Fund-link {
            top: 10px;
        }

        #Fund-link>i {
            color: rgb(255, 251, 0);

        }

        .meta-link {
            align-items: center;
            backdrop-filter: blur(3px);
            background-color: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 6px;
            box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.1);
            cursor: pointer;
            display: inline-flex;
            gap: 5px;
            left: 10px;
            padding: 10px 20px;
            position: fixed;
            text-decoration: none;
            transition: background-color 600ms, border-color 600ms;
            z-index: 10000;
        }

        .meta-link:hover {
            background-color: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .meta-link>i,
        .meta-link>span {
            height: 20px;
            line-height: 20px;
        }

        .meta-link>span {
            color: white;
            font-family: "Rubik", sans-serif;
            transition: color 600ms;
        }
    </style>
<!-- Code injected by live-server -->
<script>
	// <![CDATA[  <-- For SVG support
	if ('WebSocket' in window) {
		(function () {
			function refreshCSS() {
				var sheets = [].slice.call(document.getElementsByTagName("link"));
				var head = document.getElementsByTagName("head")[0];
				for (var i = 0; i < sheets.length; ++i) {
					var elem = sheets[i];
					var parent = elem.parentElement || head;
					parent.removeChild(elem);
					var rel = elem.rel;
					if (elem.href && typeof rel != "string" || rel.length == 0 || rel.toLowerCase() == "stylesheet") {
						var url = elem.href.replace(/(&|\?)_cacheOverride=\d+/, '');
						elem.href = url + (url.indexOf('?') >= 0 ? '&' : '?') + '_cacheOverride=' + (new Date().valueOf());
					}
					parent.appendChild(elem);
				}
			}
			var protocol = window.location.protocol === 'http:' ? 'ws://' : 'wss://';
			var address = protocol + window.location.host + window.location.pathname + '/ws';
			var socket = new WebSocket(address);
			socket.onmessage = function (msg) {
				if (msg.data == 'reload') window.location.reload();
				else if (msg.data == 'refreshcss') refreshCSS();
			};
			if (sessionStorage && !sessionStorage.getItem('IsThisFirstTime_Log_From_LiveServer')) {
				console.log('Live reload enabled.');
				sessionStorage.setItem('IsThisFirstTime_Log_From_LiveServer', true);
			}
		})();
	}
	else {
		console.error('Upgrade your browser. This Browser is NOT supported WebSocket for Live-Reloading.');
	}
	// ]]>
</script>
</head>

<body>

    <header>
        <div class="logo">VpnOptiStore</div>
        <div class="header-content">
            <div class="search-container">
                <input type="text" id="searchInput" class="search-input" placeholder="Search..." />
                <button id="searchButton" class="search-button">
                    <i class="fa-solid fa-search"></i>
                </button>
            </div>
        </div>
    </header>

    <nav>
        <ul>
            <li><a href="#"><i class="fa-solid fa-home nav-icon"></i> Home</a></li>
            <li><a href="#"><i class="fa-solid fa-shop nav-icon"></i> Shop</a></li>
                         <li><a href="#"><i class="fa-solid fa-envelope nav-icon"></i> Contact</a></li>
        </ul>
    </nav>

    <div class="hero">
        <div class="hero-content">
            <h1>Welcome to VpnOptiStore</h1>
             <a href="#" class="cta-button">Shop Now</a>
          </div>
    </div>

    <div class="main-content">
        <div class="section">
            <h2>پیشنهادهای محبوب</h2>
            <div class="product-grid">
                <div class="product-card">
                    <img src="https://www.designtagebuch.de/wp-content/uploads/mediathek//2013/04/spotify.jpg"
                        alt="Product 1">
                    <div class="info">
                        <h3>Spotify</h3>
                        <p>Llisten to music anywhere in the word
                        <div class="price">2$ and more ..</div>
                    </div>
                    <div class="price-badge">New</div>
                </div>
                <div class="product-card">
                    <img src="https://th.bing.com/th/id/OIP.v6bYD02fjOtov9s4DgyDJAHaHa?rs=1&pid=ImgDetMain"
                        alt="Product 2">
                    <div class="info">
                        <h3>YouTube Premium</h3>
                        <p>Watch your favorite movies without restrictions</p>
                        <div class="price">2$ and more ..</div>
                    </div>
                </div>
                <div class="product-card">
                    <img src="https://www.privacyjournal.net/wp-content/uploads/2022/10/nordvpn-review.jpg"
                        alt="Product 3">
                    <div class="info">
                        <h3>Nord VPN</h3>
                        <p>Very Fast VPN in The Word </p>
                        <div class="price">4$ and more ..</div>
                    </div>
                </div>
                <div class="product-card">
                    <img src="https://www.privacyjournal.net/wp-content/uploads/2022/10/expressvpn-review.jpg"
                        alt="Product 4">
                    <div class="info">
                        <h3>Exprees</h3>
                        <p>Fast and Safe Vpn</p>
                        <div class="price">3$ and more ..</div>
                    </div>
                </div>
            </div>
        </div>

        <div class="section">
            <h2>پیشنهاد های فوق ویژه</h2>
            <div class="product-grid">
                <div class="product-card">
                    <img src="https://giftcardgo.ir/wp-content/uploads/2023/08/74.jpg"
                        alt="Promotion 1">
                    <div class="info">
                        <h3>Telegram Premium</h3>
                        <p>ه پرمیوم تلگرام یا Telegram Premium نسخه پولی تلگرام است که امکانات و ویژگی‌های جذابی نظیر عکس پروفایل متحرک، مدیریت چت، حذف تبلیغات و دانلود سریعتر فایل‌ها و … را به کاربران ارائه می‌دهد.</p>
                        <div class="price">4$ and more ..</div>
                    </div>
                    <div class="price-badge">Special</div>
                </div>
                <div class="product-card">
                    <img src="https://figma-alpha-api.s3.us-west-2.amazonaws.com/images/71458231-ce82-4213-b67d-ce5e1867b1b1"
                        alt="Promotion 2">
                    <div class="info">
                        <h3>Wise Visa Card</h3>
                        <p>ایز (Wise) یک سرویس بین‌المللی انتقال پول آنلاین است که به کاربران امکان انجام تراکنش‌های ارزی به صورت سریع فراهم می‌کند. این سرویس از سال ۲۰۱۱ تاکنون به عنوان وایز (Wise) شناخته می‌شود. قبلاً این سرویس به نام “ترانسفر‌وایز” (TransferWise) شناخته می‌شد.</p>
                        <div class="price">48$ and more ..</div>
                    </div>
                <div class="price-badge">Special</div>
            </div>
        </div>

        <div class="customer-testimonials">
            <h2>نظرات خریداران</h2>
            <div class="testimonials-container">
                <div class="testimonial-card">
                    <p>"خدمات خیلی خوبی داشتن و راضی بودم"</p>
                    <div class="author">REZA</div>
                </div>
                <div class="testimonial-card">
                    <p>"چند بار ازشون خرید کردم و راضی هستم"</p>
                    <div class="author">PARSA</div>
                </div>
                <div class="testimonial-card">
                    <p>"بهترین سایت برای خدمات تلگرام هستش خیلی خوبه"</p>
                    <div class="author">AMIR</div>
                </div>
            </div>
        </div>

        <div class="featured-collections">
            <h2>HOT Offer</h2>
            <div class="collections-grid">
                <div class="collection-card">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/MasterCard_Logo.svg/1280px-MasterCard_Logo.svg.png"
                        alt="pro 1">
                    <div class="info">
                        <h3>Master Card Turkey</h3>
                        <p>این نوع مستر کارت از کشور ترکیه صادر میشود وامکان خرید در جاهای مختلف را دارد</p>
                        <div class="price">3$ and more ..</div>
                    </div>
                </div>
                <div class="collection-card">
                    <img src="https://fortune.com/img-assets/wp-content/uploads/2024/07/Recommends_Hostinger-logo.jpg?w=1440&q=75"
                        alt="Collection 2">
                    <div class="info">
                        <h3>hostinger</h3>
                        <p>بهترین سایت برای خرید دامنه مخصوص خودتان</p>
                        <div class="price">0.99$ and more ..</div>
                    </div>
                </div>
                <div class="collection-card">
                    <img src="https://pbs.twimg.com/media/Fj3AD3tXEAAmMB8.png:large"
                        alt="Collection 3">
                    <div class="info">
                        <h3>Fups Visa Card</h3>
                        <p>ویزا کارت مخصوص کشور ترکیه با امنیت بالا</p>
                        <div class="price">20$ and more ..</div>
                    </div>
                </div>
            </div>
        </div>
        <div class="contact-section">
            <h2>Contact Me </h2>
            <p>If you have any questions or need assistance, feel free to reach out to us.</p>
            <form>
                <input type="text" placeholder="Your Name" required>
                            <textarea rows="5" placeholder="Your Message" required></textarea>
                <button type="submit">Send Message</button>
            </form>
        </div>
