<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="description" content="QH VisionX creates immersive digital experiences at the intersection of technology and imagination, specializing in AR/VR, AI, and blockchain solutions." />
    <title>قیس حیدری | QH VisionX - تجربیات دیجیتال غوطه‌ور</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css" />
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/three@0.128.0/build/three.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/vanta@latest/dist/vanta.globe.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;600;700&family=Poppins:wght@300;400;500;600&family=Tajawal:wght@300;400;500;700;900&display=swap" rel="stylesheet" />
    <style>
        :root {
            --color-primary: #00f0ff;
            --color-secondary: #5773ff;
            --color-accent: #ff007a;
            --color-dark: #0a0a12;
            --color-darker: #050508;
            --color-light: #f1f1f3;
            --color-gray: rgba(255, 255, 255, 0.7);
            --color-gray-dark: rgba(255, 255, 255, 0.4);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Poppins', 'Tajawal', sans-serif;
            background-color: var(--color-dark);
            color: var(--color-light);
            min-height: 100vh;
            line-height: 1.6;
            overflow-x: hidden;
        }

        .farsi {
            font-family: 'Tajawal', sans-serif;
        }

        .tech-font {
            font-family: 'Orbitron', sans-serif;
        }

        .section {
            min-height: 100vh;
            padding: 80px 20px;
            display: none;
            opacity: 0;
            transition: opacity 0.5s ease-in-out;
        }

        .section.active {
            display: block;
            opacity: 1;
        }

        .particle-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }

        .gradient-text {
            background: linear-gradient(90deg, var(--color-primary), var(--color-secondary), var(--color-accent));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .gradient-border {
            position: relative;
        }

        .gradient-border::before {
            content: '';
            position: absolute;
            inset: -2px;
            z-index: -1;
            background: linear-gradient(90deg, var(--color-primary), var(--color-secondary), var(--color-accent));
            border-radius: inherit;
            padding: 2px;
            -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            -webkit-mask-composite: xor;
            mask-composite: exclude;
        }

        .floating {
            animation: floating 8s ease-in-out infinite;
        }

        @keyframes floating {
            0% {
                transform: translateY(0px) rotate(0deg);
            }

            50% {
                transform: translateY(-30px) rotate(5deg);
            }

            100% {
                transform: translateY(0px) rotate(0deg);
            }
        }

        .holographic {
            background: linear-gradient(135deg, rgba(0, 240, 255, 0.1) 0%, rgba(87, 115, 255, 0.1) 50%, rgba(255, 0, 122, 0.1) 100%);
            backdrop-filter: blur(10px);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .pulse {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% {
                box-shadow: 0 0 0 0 rgba(0, 240, 255, 0.4);
            }

            70% {
                box-shadow: 0 0 0 15px rgba(0, 240, 255, 0);
            }

            100% {
                box-shadow: 0 0 0 0 rgba(0, 240, 255, 0);
            }
        }

        .nav-link {
            position: relative;
            transition: all 0.3s ease;
        }

        .nav-link::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -5px;
            left: 50%;
            transform: translateX(-50%);
            background: linear-gradient(90deg, var(--color-primary), var(--color-secondary), var(--color-accent));
            transition: width 0.3s ease;
        }

        .nav-link:hover::after,
        .nav-link.active::after {
            width: 100%;
        }

        .nav-link.active {
            color: var(--color-primary);
        }

        .scroll-down {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%,
            20%,
            50%,
            80%,
            100% {
                transform: translateY(0) translateX(-50%);
            }

            40% {
                transform: translateY(-20px) translateX(-50%);
            }

            60% {
                transform: translateY(-10px) translateX(-50%);
            }
        }

        .feature-panel {
            transform: translateY(50px);
            opacity: 0;
            transition: all 0.6s ease-out;
        }

        .feature-panel.visible {
            transform: translateY(0);
            opacity: 1;
        }

        .scanline {
            position: relative;
            overflow: hidden;
        }

        .scanline::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(to bottom, transparent 0%, rgba(0, 240, 255, 0.03) 50%, transparent 100%);
            animation: scanline 5s linear infinite;
            pointer-events: none;
        }

        @keyframes scanline {
            0% {
                transform: translateY(-100%);
            }

            100% {
                transform: translateY(100%);
            }
        }

        .tech-card {
            transition: all 0.3s ease;
            transform: translateY(0);
        }

        .tech-card:hover {
            transform: translateY(-10px);
        }

        .mobile-menu {
            transition: transform 0.5s ease;
            transform: translateX(100%);
        }

        .mobile-menu.open {
            transform: translateX(0);
        }

        /* Portfolio styling */
        .portfolio-item {
            overflow: hidden;
            position: relative;
            transition: all 0.3s ease;
        }

        .portfolio-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            opacity: 0;
            transition: all 0.3s ease;
        }

        .portfolio-item:hover .portfolio-overlay {
            opacity: 1;
        }

        /* Form styling */
        .input-field {
            background-color: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            color: #fff;
            transition: all 0.3s ease;
        }

        .input-field:focus {
            border-color: var(--color-primary);
            box-shadow: 0 0 0 2px rgba(0, 240, 255, 0.2);
            outline: none;
        }

        /* Timeline styling */
        .timeline-container {
            position: relative;
        }

        .timeline-container::before {
            content: '';
            position: absolute;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 2px;
            height: 100%;
            background: linear-gradient(to bottom, var(--color-primary), var(--color-secondary), var(--color-accent));
        }

        .timeline-item {
            position: relative;
            margin-bottom: 60px;
        }

        .timeline-item::after {
            content: '';
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            width: 15px;
            height: 15px;
            border-radius: 50%;
            background: linear-gradient(90deg, var(--color-primary), var(--color-secondary));
            z-index: 1;
        }

        .timeline-content {
            width: 45%;
            padding: 20px;
            position: relative;
        }

        .timeline-item:nth-child(odd) .timeline-content {
            margin-left: auto;
        }

        /* Team member styling */
        .team-member {
            transition: all 0.3s ease;
        }

        .team-member:hover {
            transform: translateY(-10px);
        }

        .team-social {
            transition: all 0.3s ease;
            opacity: 0;
            transform: translateY(20px);
        }

        .team-member:hover .team-social {
            opacity: 1;
            transform: translateY(0);
        }

        /* Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }

        ::-webkit-scrollbar-track {
            background: var(--color-dark);
        }

        ::-webkit-scrollbar-thumb {
            background: linear-gradient(to bottom, var(--color-primary), var(--color-secondary));
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: linear-gradient(to bottom, var(--color-primary), var(--color-accent));
        }

        /* Accessibility improvements */
        .sr-only {
            position: absolute;
            width: 1px;
            height: 1px;
            padding: 0;
            margin: -1px;
            overflow: hidden;
            clip: rect(0, 0, 0, 0);
            white-space: nowrap;
            border-width: 0;
        }

        /* Focus styles for accessibility */
        a:focus,
        button:focus,
        input:focus,
        select:focus,
        textarea:focus {
            outline: 2px solid var(--color-primary);
            outline-offset: 2px;
        }

        /* Skip to content link */
        .skip-link {
            position: absolute;
            top: -40px;
            left: 0;
            background: var(--color-primary);
            color: var(--color-dark);
            padding: 8px;
            z-index: 100;
            transition: top 0.3s;
        }

        .skip-link:focus {
            top: 0;
        }

        /* QH VisionX Logo styling */
        .qh-logo {
            width: 60px;
            height: 60px;
            margin-right: 10px;
        }

        /* RTL support */
        [dir="rtl"] .nav-link::after {
            left: auto;
            right: 50%;
            transform: translateX(50%);
        }

        [dir="rtl"] .timeline-item:nth-child(odd) .timeline-content {
            margin-right: auto;
            margin-left: 0;
        }

        /* Language switcher */
        .lang-switcher {
            display: flex;
            align-items: center;
            margin-left: 20px;
            cursor: pointer;
            padding: 5px 10px;
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
        }

        .lang-switcher:hover {
            background: rgba(255, 255, 255, 0.1);
        }
    </style>
</head>
<body>
    <a href="#main-content" class="skip-link">Skip to main content</a>

    <div id="vanta-bg" class="particle-bg" aria-hidden="true"></div>

    <header class="fixed top-0 left-0 w-full z-50 bg-opacity-20 bg-black backdrop-filter backdrop-blur-lg">
        <div class="container mx-auto px-6 py-4">
            <div class="flex justify-between items-center">
                <div class="flex items-center">
                    <img src="https://page.genspark.site/v1/base64_upload/65b706f0b5f18802c7fb489b59fd9fcd" alt="QH VisionX Logo, a stylized blue and pink futuristic globe with digital grid lines" class="qh-logo" />
                    <a href="#home" aria-label="QH VisionX Home" class="text-2xl font-bold tech-font gradient-text">QH VisionX</a>
                </div>

                <nav class="hidden md:flex items-center space-x-8" aria-label="Main navigation">
                    <a href="#home" class="nav-link active tech-font" data-section="home">
                        <span class="en">HOME</span>
                        <span class="farsi">خانه</span>
                    </a>
                    <a href="#services" class="nav-link tech-font" data-section="services">
                        <span class="en">SERVICES</span>
                        <span class="farsi">خدمات</span>
                    </a>
                    <a href="#portfolio" class="nav-link tech-font" data-section="portfolio">
                        <span class="en">PORTFOLIO</span>
                        <span class="farsi">نمونه کارها</span>
                    </a>
                    <a href="#about" class="nav-link tech-font" data-section="about">
                        <span class="en">ABOUT</span>
                        <span class="farsi">درباره ما</span>
                    </a>
                    <a href="#contact" class="nav-link tech-font" data-section="contact">
                        <span class="en">CONTACT</span>
                        <span class="farsi">تماس</span>
                    </a>
                </nav>

                <div class="flex items-center">
                    <div id="lang-switcher" class="lang-switcher ml-4" role="button" tabindex="0" aria-label="Toggle language">
                        <i class="fas fa-globe mr-2"></i>
                        <span id="current-lang">فارسی</span>
                    </div>

                    <div class="md:hidden ml-4">
                        <button id="mobile-menu-button" class="text-white focus:outline-none" aria-label="Open mobile menu" aria-expanded="false" aria-controls="mobile-menu">
                            <i class="fas fa-bars text-2xl"></i>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <div id="mobile-menu" class="mobile-menu fixed top-0 right-0 h-full w-64 bg-[#0a0a12] z-50 p-6 shadow-lg holographic" aria-label="Mobile navigation" aria-hidden="true">
        <div class="flex justify-end mb-8">
            <button id="close-menu" class="text-white focus:outline-none" aria-label="Close mobile menu">
                <i class="fas fa-times text-2xl"></i>
            </button>
        </div>

        <nav class="flex flex-col space-y-6">
            <a href="#home" class="nav-link active tech-font text-lg" data-section="home">
                <span class="en">HOME</span>
                <span class="farsi">خانه</span>
            </a>
            <a href="#services" class="nav-link tech-font text-lg" data-section="services">
                <span class="en">SERVICES</span>
                <span class="farsi">خدمات</span>
            </a>
            <a href="#portfolio" class="nav-link tech-font text-lg" data-section="portfolio">
                <span class="en">PORTFOLIO</span>
                <span class="farsi">نمونه کارها</span>
            </a>
            <a href="#about" class="nav-link tech-font text-lg" data-section="about">
                <span class="en">ABOUT</span>
                <span class="farsi">درباره ما</span>
            </a>
            <a href="#contact" class="nav-link tech-font text-lg" data-section="contact">
                <span class="en">CONTACT</span>
                <span class="farsi">تماس</span>
            </a>
        </nav>

        <div class="mt-8">
            <div id="mobile-lang-switcher" class="lang-switcher inline-block" role="button" tabindex="0" aria-label="Toggle language">
                <i class="fas fa-globe mr-2"></i>
                <span id="mobile-current-lang">فارسی</span>
            </div>
        </div>

        <div class="mt-8">
            <div class="flex space-x-4">
                <a href="https://www.youtube.com/@AfghanTreasures" target="_blank" class="text-white hover:text-red-500 transition-colors" aria-label="YouTube">
                    <i class="fab fa-youtube text-2xl"></i>
                </a>
                <a href="https://x.com/QhVision" target="_blank" class="text-white hover:text-blue-400 transition-colors" aria-label="Twitter">
                    <i class="fab fa-twitter text-2xl"></i>
                </a>
                <a href="https://www.instagram.com/17841474002610954/" target="_blank" class="text-white hover:text-pink-500 transition-colors" aria-label="Instagram">
                    <i class="fab fa-instagram text-2xl"></i>
                </a>
                <a href="https://www.linkedin.com/feed/" target="_blank" class="text-white hover:text-blue-500 transition-colors" aria-label="LinkedIn">
                    <i class="fab fa-linkedin-in text-2xl"></i>
                </a>
            </div>
        </div>
    </div>

    <main id="main-content">
        <section id="home" class="section active" aria-labelledby="home-heading">
            <div class="container mx-auto px-6 min-h-screen flex flex-col justify-center items-center text-center">
                <div class="space-helmet floating mb-8">
                    <img src="https://page.genspark.site/v1/base64_upload/65b706f0b5f18802c7fb489b59fd9fcd" alt="QH VisionX Logo, a stylized blue and pink futuristic globe with digital grid lines" class="w-32 h-32 md:w-48 md:h-48" />
                </div>

                <h1 id="home-heading" class="text-4xl md:text-6xl font-bold tech-font gradient-text mb-6" tabindex="-1">
                    <span class="en">QH VisionX</span>
                    <span class="farsi">قیس حیدری | QH VisionX</span>
                </h1>

                <p class="text-xl md:text-2xl mb-8 max-w-3xl">
                    <span class="en">I'm Qais Haidari, founder of this scientific and educational initiative. Our mission is to promote modern knowledge, digital education, and empower the youth of Afghanistan.</span>
                    <span class="farsi">من قیس حیدری، بنیان‌گذار این ابتکار علمی و آموزشی هستم. هدف ما ترویج دانش نوین، آموزش دیجیتال و توانمندسازی نسل جوان افغانستان است.</span>
                </p>

                <div class="flex flex-wrap justify-center gap-4 mb-12">
                    <a href="#services" class="gradient-border bg-[#0a0a12] px-8 py-3 rounded-full tech-font hover:opacity-80 transition-opacity">
                        <span class="en">EXPLORE SERVICES</span>
                        <span class="farsi">مشاهده خدمات</span>
                    </a>
                    <a href="#contact" class="px-8 py-3 rounded-full tech-font border border-[#5773ff] hover:bg-[#5773ff] hover:bg-opacity-20 transition-all">
                        <span class="en">GET IN TOUCH</span>
                        <span class="farsi">تماس با ما</span>
                    </a>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-5xl w-full">
                    <div class="holographic p-6 rounded-xl scanline tech-card">
                        <div class="w-16 h-16 rounded-full bg-gradient-to-br from-[#00f0ff] to-[#5773ff] flex items-center justify-center mx-auto mb-4">
                            <i class="fas fa-vr-cardboard text-2xl" aria-hidden="true"></i>
                        </div>
                        <h3 class="text-xl font-semibold tech-font mb-3">
                            <span class="en">Immersive Experiences</span>
                            <span class="farsi">تجربیات غوطه‌ور</span>
                        </h3>
                        <p class="text-gray-300">
                            <span class="en">Transforming ideas into captivating virtual realities that engage and inspire.</span>
                            <span class="farsi">تبدیل ایده‌ها به واقعیت‌های مجازی جذاب که مخاطب را درگیر و الهام‌بخش می‌کند.</span>
                        </p>
                    </div>

                    <div class="holographic p-6 rounded-xl scanline tech-card">
                        <div class="w-16 h-16 rounded-full bg-gradient-to-br from-[#5773ff] to-[#8148ff] flex items-center justify-center mx-auto mb-4">
                            <i class="fas fa-robot text-2xl" aria-hidden="true"></i>
                        </div>
                        <h3 class="text-xl font-semibold tech-font mb-3">
                            <span class="en">AI Integration</span>
                            <span class="farsi">یکپارچه‌سازی هوش مصنوعی</span>
                        </h3>
                        <p class="text-gray-300">
                            <span class="en">Harnessing the power of artificial intelligence to create smarter digital solutions.</span>
                            <span class="farsi">بهره‌گیری از قدرت هوش مصنوعی برای ایجاد راه‌حل‌های دیجیتال هوشمندتر.</span>
                        </p>
                    </div>

                    <div class="holographic p-6 rounded-xl scanline tech-card">
                        <div class="w-16 h-16 rounded-full bg-gradient-to-br from-[#8148ff] to-[#ff007a] flex items-center justify-center mx-auto mb-4">
                            <i class="fas fa-code text-2xl" aria-hidden="true"></i>
                        </div>
                        <h3 class="text-xl font-semibold tech-font mb-3">
                            <span class="en">Future-Ready Development</span>
                            <span class="farsi">توسعه آماده برای آینده</span>
                        </h3>
                        <p class="text-gray-300">
                            <span class="en">Building tomorrow's digital infrastructure with cutting-edge technologies.</span>
                            <span class="farsi">ساخت زیرساخت دیجیتال فردا با فناوری‌های پیشرفته.</span>
                        </p>
                    </div>
                </div>

                <div class="scroll-down" aria-hidden="true">
                    <i class="fas fa-chevron-down text-2xl gradient-text pulse"></i>
                </div>
            </div>
        </section>

        <section id="services" class="section" aria-labelledby="services-heading">
            <div class="container mx-auto px-6 py-24">
                <div class="text-center mb-16">
                    <h2 id="services-heading" class="text-4xl md:text-5xl font-bold tech-font gradient-text mb-4" tabindex="-1">
                        <span class="en">OUR SERVICES</span>
                        <span class="farsi">خدمات ما</span>
                    </h2>
                    <p class="text-xl max-w-3xl mx-auto">
                        <span class="en">We combine creativity with technical expertise to deliver cutting-edge digital solutions.</span>
                        <span class="farsi">ما خلاقیت را با تخصص فنی ترکیب می‌کنیم تا راه‌حل‌های دیجیتالی پیشرفته ارائه دهیم.</span>
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 mb-16">
                    <div class="feature-panel holographic p-8 rounded-xl scanline">
                        <div class="flex items-start mb-6">
                            <div class="w-12 h-12 rounded-lg bg-gradient-to-r from-[#00f0ff] to-[#5773ff] flex items-center justify-center mr-4" aria-hidden="true">
                                <i class="fas fa-mobile-alt text-xl"></i>
                            </div>
                            <h3 class="text-2xl font-semibold tech-font">
                                <span class="en">App Development</span>
                                <span class="farsi">توسعه اپلیکیشن</span>
                            </h3>
                        </div>
                        <p class="text-gray-300 mb-6">
                            <span class="en">Custom mobile and web applications built with the latest technologies to provide seamless user experiences across all devices.</span>
                            <span class="farsi">اپلیکیشن‌های موبایل و وب سفارشی که با آخرین فناوری‌ها ساخته شده‌اند تا تجربه کاربری یکپارچه در تمام دستگاه‌ها ارائه دهند.</span>
                        </p>
                        <ul class="space-y-2 mb-6">
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#00f0ff] mr-2" aria-hidden="true"></i>
                                <span class="en">Native & Cross-Platform Solutions</span>
                                <span class="farsi">راه‌حل‌های بومی و چند سکویی</span>
                            </li>
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#00f0ff] mr-2" aria-hidden="true"></i>
                                <span class="en">Progressive Web Applications</span>
                                <span class="farsi">اپلیکیشن‌های وب پیشرو</span>
                            </li>
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#00f0ff] mr-2" aria-hidden="true"></i>
                                <span class="en">API Development & Integration</span>
                                <span class="farsi">توسعه و یکپارچه‌سازی API</span>
                            </li>
                        </ul>
                        <a href="#contact" class="inline-block tech-font text-sm px-6 py-2 border border-[#00f0ff] rounded-full hover:bg-[#00f0ff] hover:bg-opacity-20 transition-all">
                            <span class="en">LEARN MORE</span>
                            <span class="farsi">اطلاعات بیشتر</span>
                        </a>
                    </div>

                    <div class="feature-panel holographic p-8 rounded-xl scanline">
                        <div class="flex items-start mb-6">
                            <div class="w-12 h-12 rounded-lg bg-gradient-to-r from-[#5773ff] to-[#8148ff] flex items-center justify-center mr-4" aria-hidden="true">
                                <i class="fas fa-vr-cardboard text-xl"></i>
                            </div>
                            <h3 class="text-2xl font-semibold tech-font">
                                <span class="en">AR/VR Experiences</span>
                                <span class="farsi">تجربیات واقعیت افزوده/مجازی</span>
                            </h3>
                        </div>
                        <p class="text-gray-300 mb-6">
                            <span class="en">Immersive augmented and virtual reality solutions that transport users into new dimensions and create unforgettable interactions.</span>
                            <span class="farsi">راه‌حل‌های غوطه‌ور واقعیت افزوده و مجازی که کاربران را به ابعاد جدیدی منتقل می‌کند و تعاملات فراموش‌نشدنی ایجاد می‌کند.</span>
                        </p>
                        <ul class="space-y-2 mb-6">
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#5773ff] mr-2" aria-hidden="true"></i>
                                <span class="en">Interactive VR Environments</span>
                                <span class="farsi">محیط‌های تعاملی واقعیت مجازی</span>
                            </li>
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#5773ff] mr-2" aria-hidden="true"></i>
                                <span class="en">AR Product Visualizations</span>
                                <span class="farsi">تجسم محصول با واقعیت افزوده</span>
                            </li>
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#5773ff] mr-2" aria-hidden="true"></i>
                                <span class="en">Spatial Computing Solutions</span>
                                <span class="farsi">راه‌حل‌های محاسبات فضایی</span>
                            </li>
                        </ul>
                        <a href="#contact" class="inline-block tech-font text-sm px-6 py-2 border border-[#5773ff] rounded-full hover:bg-[#5773ff] hover:bg-opacity-20 transition-all">
                            <span class="en">LEARN MORE</span>
                            <span class="farsi">اطلاعات بیشتر</span>
                        </a>
                    </div>

                    <div class="feature-panel holographic p-8 rounded-xl scanline">
                        <div class="flex items-start mb-6">
                            <div class="w-12 h-12 rounded-lg bg-gradient-to-r from-[#8148ff] to-[#ff007a] flex items-center justify-center mr-4" aria-hidden="true">
                                <i class="fas fa-robot text-xl"></i>
                            </div>
                            <h3 class="text-2xl font-semibold tech-font">
                                <span class="en">AI Solutions</span>
                                <span class="farsi">راه‌حل‌های هوش مصنوعی</span>
                            </h3>
                        </div>
                        <p class="text-gray-300 mb-6">
                            <span class="en">Intelligent systems and algorithms that learn, adapt, and evolve to provide smarter, more efficient digital experiences.</span>
                            <span class="farsi">سیستم‌ها و الگوریتم‌های هوشمندی که یاد می‌گیرند، سازگار می‌شوند و تکامل می‌یابند تا تجربیات دیجیتالی هوشمندتر و کارآمدتری ارائه دهند.</span>
                        </p>
                        <ul class="space-y-2 mb-6">
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#ff007a] mr-2" aria-hidden="true"></i>
                                <span class="en">Machine Learning Integration</span>
                                <span class="farsi">یکپارچه‌سازی یادگیری ماشینی</span>
                            </li>
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#ff007a] mr-2" aria-hidden="true"></i>
                                <span class="en">Natural Language Processing</span>
                                <span class="farsi">پردازش زبان طبیعی</span>
                            </li>
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#ff007a] mr-2" aria-hidden="true"></i>
                                <span class="en">Computer Vision Applications</span>
                                <span class="farsi">کاربردهای بینایی کامپیوتری</span>
                            </li>
                        </ul>
                        <a href="#contact" class="inline-block tech-font text-sm px-6 py-2 border border-[#ff007a] rounded-full hover:bg-[#ff007a] hover:bg-opacity-20 transition-all">
                            <span class="en">LEARN MORE</span>
                            <span class="farsi">اطلاعات بیشتر</span>
                        </a>
                    </div>

                    <div class="feature-panel holographic p-8 rounded-xl scanline">
                        <div class="flex items-start mb-6">
                            <div class="w-12 h-12 rounded-lg bg-gradient-to-r from-[#00f0ff] to-[#ff007a] flex items-center justify-center mr-4" aria-hidden="true">
                                <i class="fas fa-palette text-xl"></i>
                            </div>
                            <h3 class="text-2xl font-semibold tech-font">
                                <span class="en">UI/UX Design</span>
                                <span class="farsi">طراحی UI/UX</span>
                            </h3>
                        </div>
                        <p class="text-gray-300 mb-6">
                            <span class="en">Human-centered design approaches that create intuitive, engaging, and visually stunning digital interfaces.</span>
                            <span class="farsi">رویکردهای طراحی انسان‌محور که رابط‌های دیجیتالی بدیهی، جذاب و از نظر بصری خیره‌کننده ایجاد می‌کنند.</span>
                        </p>
                        <ul class="space-y-2 mb-6">
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#00f0ff] mr-2" aria-hidden="true"></i>
                                <span class="en">User Research & Testing</span>
                                <span class="farsi">تحقیق و آزمایش کاربر</span>
                            </li>
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#00f0ff] mr-2" aria-hidden="true"></i>
                                <span class="en">Interface Prototyping</span>
                                <span class="farsi">نمونه‌سازی رابط</span>
                            </li>
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#00f0ff] mr-2" aria-hidden="true"></i>
                                <span class="en">Motion & Interaction Design</span>
                                <span class="farsi">طراحی حرکت و تعامل</span>
                            </li>
                        </ul>
                        <a href="#contact" class="inline-block tech-font text-sm px-6 py-2 border border-[#00f0ff] rounded-full hover:bg-[#00f0ff] hover:bg-opacity-20 transition-all">
                            <span class="en">LEARN MORE</span>
                            <span class="farsi">اطلاعات بیشتر</span>
                        </a>
                    </div>

                    <div class="feature-panel holographic p-8 rounded-xl scanline">
                        <div class="flex items-start mb-6">
                            <div class="w-12 h-12 rounded-lg bg-gradient-to-r from-[#5773ff] to-[#00f0ff] flex items-center justify-center mr-4" aria-hidden="true">
                                <i class="fas fa-cubes text-xl"></i>
                            </div>
                            <h3 class="text-2xl font-semibold tech-font">
                                <span class="en">Blockchain Development</span>
                                <span class="farsi">توسعه بلاکچین</span>
                            </h3>
                        </div>
                        <p class="text-gray-300 mb-6">
                            <span class="en">Secure, transparent, and decentralized blockchain solutions for next-generation digital applications.</span>
                            <span class="farsi">راه‌حل‌های بلاکچین امن، شفاف و غیرمتمرکز برای برنامه‌های دیجیتال نسل بعدی.</span>
                        </p>
                        <ul class="space-y-2 mb-6">
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#5773ff] mr-2" aria-hidden="true"></i>
                                <span class="en">Smart Contract Development</span>
                                <span class="farsi">توسعه قراردادهای هوشمند</span>
                            </li>
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#5773ff] mr-2" aria-hidden="true"></i>
                                <span class="en">NFT Platforms & Marketplaces</span>
                                <span class="farsi">پلتفرم‌ها و بازارهای NFT</span>
                            </li>
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#5773ff] mr-2" aria-hidden="true"></i>
                                <span class="en">DeFi Application Integration</span>
                                <span class="farsi">یکپارچه‌سازی برنامه‌های DeFi</span>
                            </li>
                        </ul>
                        <a href="#contact" class="inline-block tech-font text-sm px-6 py-2 border border-[#5773ff] rounded-full hover:bg-[#5773ff] hover:bg-opacity-20 transition-all">
                            <span class="en">LEARN MORE</span>
                            <span class="farsi">اطلاعات بیشتر</span>
                        </a>
                    </div>

                    <div class="feature-panel holographic p-8 rounded-xl scanline">
                        <div class="flex items-start mb-6">
                            <div class="w-12 h-12 rounded-lg bg-gradient-to-r from-[#ff007a] to-[#8148ff] flex items-center justify-center mr-4" aria-hidden="true">
                                <i class="fas fa-server text-xl"></i>
                            </div>
                            <h3 class="text-2xl font-semibold tech-font">
                                <span class="en">Cloud Solutions</span>
                                <span class="farsi">راه‌حل‌های ابری</span>
                            </h3>
                        </div>
                        <p class="text-gray-300 mb-6">
                            <span class="en">Scalable, reliable, and cost-effective cloud infrastructure that powers your digital applications and services.</span>
                            <span class="farsi">زیرساخت ابری مقیاس‌پذیر، قابل اعتماد و مقرون به صرفه که برنامه‌های دیجیتالی و خدمات شما را قدرت می‌بخشد.</span>
                        </p>
                        <ul class="space-y-2 mb-6">
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#ff007a] mr-2" aria-hidden="true"></i>
                                <span class="en">Cloud Migration Strategies</span>
                                <span class="farsi">استراتژی‌های مهاجرت ابری</span>
                            </li>
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#ff007a] mr-2" aria-hidden="true"></i>
                                <span class="en">Serverless Architecture</span>
                                <span class="farsi">معماری بدون سرور</span>
                            </li>
                            <li class="flex items-center">
                                <i class="fas fa-check text-[#ff007a] mr-2" aria-hidden="true"></i>
                                <span class="en">DevOps & CI/CD Implementation</span>
                                <span class="farsi">پیاده‌سازی DevOps و CI/CD</span>
                            </li>
                        </ul>
                        <a href="#contact" class="inline-block tech-font text-sm px-6 py-2 border border-[#ff007a] rounded-full hover:bg-[#ff007a] hover:bg-opacity-20 transition-all">
                            <span class="en">LEARN MORE</span>
                            <span class="farsi">اطلاعات بیشتر</span>
                        </a>
                    </div>
                </div>

                <div class="holographic p-8 rounded-xl text-center feature-panel">
                    <h3 class="text-2xl font-semibold tech-font mb-4">
                        <span class="en">Need a Custom Solution?</span>
                        <span class="farsi">به راه‌حل سفارشی نیاز دارید؟</span>
                    </h3>
                    <p class="text-gray-300 mb-6 max-w-2xl mx-auto">
                        <span class="en">Our team specializes in crafting bespoke digital solutions tailored to your unique business challenges and opportunities.</span>
                        <span class="farsi">تیم ما در ساخت راه‌حل‌های دیجیتالی سفارشی متناسب با چالش‌ها و فرصت‌های منحصر به فرد کسب و کار شما تخصص دارد.</span>
                    </p>
                    <a href="#contact" class="gradient-border bg-[#0a0a12] px-8 py-3 rounded-full tech-font inline-block hover:opacity-80 transition-opacity">
                        <span class="en">DISCUSS YOUR PROJECT</span>
                        <span class="farsi">درباره پروژه خود گفتگو کنید</span>
                    </a>
                </div>
            </div>
        </section>

        <section id="portfolio" class="section" aria-labelledby="portfolio-heading">
            <div class="container mx-auto px-6 py-24">
                <div class="text-center mb-16">
                    <h2 id="portfolio-heading" class="text-4xl md:text-5xl font-bold tech-font gradient-text mb-4" tabindex="-1">
                        <span class="en">OUR WORK</span>
                        <span class="farsi">نمونه کارهای ما</span>
                    </h2>
                    <p class="text-xl max-w-3xl mx-auto">
                        <span class="en">Explore our collection of innovative digital projects that push the boundaries of technology.</span>
                        <span class="farsi">مجموعه‌ای از پروژه‌های نوآورانه دیجیتالی ما را کشف کنید که مرزهای فناوری را گسترش می‌دهند.</span>
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <div class="portfolio-item gradient-border bg-[#0a0a12] rounded-xl overflow-hidden feature-panel">
                        <div class="h-64 bg-gradient-to-br from-[#00f0ff] to-[#5773ff] flex items-center justify-center">
                            <div class="text-center p-6">
                                <i class="fas fa-vr-cardboard text-6xl text-white opacity-80" aria-hidden="true"></i>
                            </div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold tech-font mb-2">
                                <span class="en">NexusVR Platform</span>
                                <span class="farsi">پلتفرم NexusVR</span>
                            </h3>
                            <p class="text-gray-300 mb-4">
                                <span class="en">Virtual reality platform for immersive educational experiences.</span>
                                <span class="farsi">پلتفرم واقعیت مجازی برای تجربیات آموزشی غوطه‌ور.</span>
                            </p>
                            <div class="flex flex-wrap gap-2">
                                <span class="text-xs bg-[#00f0ff] bg-opacity-20 text-[#00f0ff] px-3 py-1 rounded-full">VR Development</span>
                                <span class="text-xs bg-[#5773ff] bg-opacity-20 text-[#5773ff] px-3 py-1 rounded-full">Education</span>
                                <span class="text-xs bg-[#ff007a] bg-opacity-20 text-[#ff007a] px-3 py-1 rounded-full">Unity 3D</span>
                            </div>
                        </div>
                    </div>

                    <div class="portfolio-item gradient-border bg-[#0a0a12] rounded-xl overflow-hidden feature-panel">
                        <div class="h-64 bg-gradient-to-br from-[#5773ff] to-[#8148ff] flex items-center justify-center">
                            <div class="text-center p-6">
                                <i class="fas fa-mobile-alt text-6xl text-white opacity-80" aria-hidden="true"></i>
                            </div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold tech-font mb-2">
                                <span class="en">AuroraAI Assistant</span>
                                <span class="farsi">دستیار هوشمند AuroraAI</span>
                            </h3>
                            <p class="text-gray-300 mb-4">
                                <span class="en">AI-powered personal productivity and wellness application.</span>
                                <span class="farsi">برنامه بهره‌وری و سلامتی شخصی مبتنی بر هوش مصنوعی.</span>
                            </p>
                            <div class="flex flex-wrap gap-2">
                                <span class="text-xs bg-[#5773ff] bg-opacity-20 text-[#5773ff] px-3 py-1 rounded-full">AI</span>
                                <span class="text-xs bg-[#00f0ff] bg-opacity-20 text-[#00f0ff] px-3 py-1 rounded-full">Mobile App</span>
                                <span class="text-xs bg-[#ff007a] bg-opacity-20 text-[#ff007a] px-3 py-1 rounded-full">Machine Learning</span>
                            </div>
                        </div>
                    </div>

                    <div class="portfolio-item gradient-border bg-[#0a0a12] rounded-xl overflow-hidden feature-panel">
                        <div class="h-64 bg-gradient-to-br from-[#8148ff] to-[#ff007a] flex items-center justify-center">
                            <div class="text-center p-6">
                                <i class="fas fa-cubes text-6xl text-white opacity-80" aria-hidden="true"></i>
                            </div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold tech-font mb-2">
                                <span class="en">Quantum Chain</span>
                                <span class="farsi">زنجیره کوآنتوم</span>
                            </h3>
                            <p class="text-gray-300 mb-4">
                                <span class="en">Blockchain-based marketplace for digital collectibles.</span>
                                <span class="farsi">بازار مبتنی بر بلاکچین برای کالاهای دیجیتال قابل جمع‌آوری.</span>
                            </p>
                            <div class="flex flex-wrap gap-2">
                                <span class="text-xs bg-[#ff007a] bg-opacity-20 text-[#ff007a] px-3 py-1 rounded-full">Blockchain</span>
                                <span class="text-xs bg-[#00f0ff] bg-opacity-20 text-[#00f0ff] px-3 py-1 rounded-full">NFT</span>
                                <span class="text-xs bg-[#5773ff] bg-opacity-20 text-[#5773ff] px-3 py-1 rounded-full">Smart Contracts</span>
                            </div>
                        </div>
                    </div>

                    <div class="portfolio-item gradient-border bg-[#0a0a12] rounded-xl overflow-hidden feature-panel">
                        <div class="h-64 bg-gradient-to-br from-[#00f0ff] to-[#ff007a] flex items-center justify-center">
                            <div class="text-center p-6">
                                <i class="fas fa-globe text-6xl text-white opacity-80" aria-hidden="true"></i>
                            </div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold tech-font mb-2">
                                <span class="en">Stellar Pulse</span>
                                <span class="farsi">ضربان ستاره‌ای</span>
                            </h3>
                            <p class="text-gray-300 mb-4">
                                <span class="en">Real-time data visualization platform for space exploration.</span>
                                <span class="farsi">پلتفرم تجسم داده‌های زمان واقعی برای اکتشاف فضا.</span>
                            </p>
                            <div class="flex flex-wrap gap-2">
                                <span class="text-xs bg-[#5773ff] bg-opacity-20 text-[#5773ff] px-3 py-1 rounded-full">Big Data</span>
                                <span class="text-xs bg-[#ff007a] bg-opacity-20 text-[#ff007a] px-3 py-1 rounded-full">WebGL</span>
                                <span class="text-xs bg-[#00f0ff] bg-opacity-20 text-[#00f0ff] px-3 py-1 rounded-full">Data Visualization</span>
                            </div>
                        </div>
                    </div>

                    <div class="portfolio-item gradient-border bg-[#0a0a12] rounded-xl overflow-hidden feature-panel">
                        <div class="h-64 bg-gradient-to-br from-[#5773ff] to-[#00f0ff] flex items-center justify-center">
                            <div class="text-center p-6">
                                <i class="fas fa-robot text-6xl text-white opacity-80" aria-hidden="true"></i>
                            </div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold tech-font mb-2">
                                <span class="en">Nova Intelligence</span>
                                <span class="farsi">هوش نوا</span>
                            </h3>
                            <p class="text-gray-300 mb-4">
                                <span class="en">AI-powered business analytics and forecasting platform.</span>
                                <span class="farsi">پلتفرم تجزیه و تحلیل و پیش‌بینی کسب و کار مبتنی بر هوش مصنوعی.</span>
                            </p>
                            <div class="flex flex-wrap gap-2">
                                <span class="text-xs bg-[#00f0ff] bg-opacity-20 text-[#00f0ff] px-3 py-1 rounded-full">AI</span>
                                <span class="text-xs bg-[#5773ff] bg-opacity-20 text-[#5773ff] px-3 py-1 rounded-full">Predictive Analytics</span>
                                <span class="text-xs bg-[#ff007a] bg-opacity-20 text-[#ff007a] px-3 py-1 rounded-full">Business Intelligence</span>
                            </div>
                        </div>
                    </div>

                    <div class="portfolio-item gradient-border bg-[#0a0a12] rounded-xl overflow-hidden feature-panel">
                        <div class="h-64 bg-gradient-to-br from-[#ff007a] to-[#8148ff] flex items-center justify-center">
                            <div class="text-center p-6">
                                <i class="fas fa-headset text-6xl text-white opacity-80" aria-hidden="true"></i>
                            </div>
                        </div>
                        <div class="p-6">
                            <h3 class="text-xl font-semibold tech-font mb-2">
                                <span class="en">Immersio</span>
                                <span class="farsi">ایمرسیو</span>
                            </h3>
                            <p class="text-gray-300 mb-4">
                                <span class="en">Augmented reality platform for immersive retail experiences.</span>
                                <span class="farsi">پلتفرم واقعیت افزوده برای تجربیات خرده‌فروشی غوطه‌ور.</span>
                            </p>
                            <div class="flex flex-wrap gap-2">
                                <span class="text-xs bg-[#ff007a] bg-opacity-20 text-[#ff007a] px-3 py-1 rounded-full">AR</span>
                                <span class="text-xs bg-[#00f0ff] bg-opacity-20 text-[#00f0ff] px-3 py-1 rounded-full">Retail</span>
                                <span class="text-xs bg-[#5773ff] bg-opacity-20 text-[#5773ff] px-3 py-1 rounded-full">3D Modeling</span>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="text-center mt-16 feature-panel">
                    <a href="#contact" class="gradient-border bg-[#0a0a12] px-8 py-3 rounded-full tech-font inline-block hover:opacity-80 transition-opacity">
                        <span class="en">START YOUR PROJECT</span>
                        <span class="farsi">پروژه خود را شروع کنید</span>
                    </a>
                </div>
            </div>
        </section>

        <section id="about" class="section" aria-labelledby="about-heading">
            <div class="container mx-auto px-6 py-24">
                <div class="text-center mb-16">
                    <h2 id="about-heading" class="text-4xl md:text-5xl font-bold tech-font gradient-text mb-4" tabindex="-1">
                        <span class="en">ABOUT US</span>
                        <span class="farsi">درباره ما</span>
                    </h2>
                    <p class="text-xl max-w-3xl mx-auto">
                        <span class="en">We're a team of digital innovators passionate about creating the future of technology.</span>
                        <span class="farsi">ما تیمی از نوآوران دیجیتال هستیم که مشتاقانه به ایجاد آینده فناوری می‌پردازیم.</span>
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-16">
                    <div class="feature-panel">
                        <h3 class="text-2xl font-semibold tech-font gradient-text mb-6">
                            <span class="en">Our Vision</span>
                            <span class="farsi">چشم‌انداز ما</span>
                        </h3>
                        <p class="text-gray-300 mb-4">
                            <span class="en">At QH VisionX, we envision a future where technology seamlessly enhances human experiences, creating more immersive, intuitive, and meaningful interactions with the digital world.</span>
                            <span class="farsi">در QH VisionX، ما آینده‌ای را متصور هستیم که در آن فناوری به‌طور یکپارچه تجربیات انسانی را ارتقا می‌دهد و تعاملات غوطه‌ور، بدیهی و معنادارتری با دنیای دیجیتال ایجاد می‌کند.</span>
                        </p>
                        <p class="text-gray-300">
                            <span class="en">We strive to be at the forefront of technological innovation, pushing the boundaries of what's possible and crafting solutions that transform how people work, learn, and play.</span>
                            <span class="farsi">ما تلاش می‌کنیم در خط مقدم نوآوری فناوری باشیم، مرزهای امکانات را گسترش دهیم و راه‌حل‌هایی بسازیم که نحوه کار، یادگیری و تفریح مردم را متحول می‌کند.</span>
                        </p>
                    </div>

                    <div class="feature-panel">
                        <h3 class="text-2xl font-semibold tech-font gradient-text mb-6">
                            <span class="en">Our Approach</span>
                            <span class="farsi">رویکرد ما</span>
                        </h3>
                        <p class="text-gray-300 mb-4">
                            <span class="en">We combine creative thinking with technical expertise to deliver cutting-edge solutions that address complex challenges. Our human-centered design process ensures we create technologies that are accessible, engaging, and impactful.</span>
                            <span class="farsi">ما تفکر خلاقانه را با تخصص فنی ترکیب می‌کنیم تا راه‌حل‌های پیشرفته‌ای ارائه دهیم که چالش‌های پیچیده را حل می‌کنند. فرآیند طراحی انسان‌محور ما اطمینان می‌دهد که ما فناوری‌هایی را خلق می‌کنیم که در دسترس، جذاب و تاثیرگذار هستند.</span>
                        </p>
                        <p class="text-gray-300">
                            <span class="en">With a focus on quality, innovation, and collaboration, we work closely with our clients to understand their needs and develop solutions that exceed expectations.</span>
                            <span class="farsi">با تمرکز بر کیفیت، نوآوری و همکاری، ما با مشتریان خود به‌طور نزدیک کار می‌کنیم تا نیازهای آنها را درک کنیم و راه‌حل‌هایی توسعه دهیم که از انتظارات فراتر می‌روند.</span>
                        </p>
                    </div>
                </div>

                <div class="holographic rounded-xl p-8 mb-16 feature-panel">
                    <h3 class="text-2xl font-semibold tech-font text-center gradient-text mb-8">
                        <span class="en">Our Core Values</span>
                        <span class="farsi">ارزش‌های اصلی ما</span>
                    </h3>

                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                        <div class="text-center">
                            <div class="w-16 h-16 rounded-full bg-gradient-to-br from-[#00f0ff] to-[#5773ff] flex items-center justify-center mx-auto mb-4" aria-hidden="true">
                                <i class="fas fa-lightbulb text-2xl"></i>
                            </div>
                            <h4 class="text-lg font-semibold tech-font mb-2">
                                <span class="en">Innovation</span>
                                <span class="farsi">نوآوری</span>
                            </h4>
                            <p class="text-gray-300">
                                <span class="en">Constantly exploring new technologies and creative solutions.</span>
                                <span class="farsi">کاوش مداوم فناوری‌های جدید و راه‌حل‌های خلاقانه.</span>
                            </p>
                        </div>

                        <div class="text-center">
                            <div class="w-16 h-16 rounded-full bg-gradient-to-br from-[#5773ff] to-[#8148ff] flex items-center justify-center mx-auto mb-4" aria-hidden="true">
                                <i class="fas fa-users text-2xl"></i>
                            </div>
                            <h4 class="text-lg font-semibold tech-font mb-2">
                                <span class="en">Collaboration</span>
                                <span class="farsi">همکاری</span>
                            </h4>
                            <p class="text-gray-300">
                                <span class="en">Working together to achieve exceptional results.</span>
                                <span class="farsi">همکاری با یکدیگر برای دستیابی به نتایج استثنایی.</span>
                            </p>
                        </div>

                        <div class="text-center">
                            <div class="w-16 h-16 rounded-full bg-gradient-to-br from-[#8148ff] to-[#ff007a] flex items-center justify-center mx-auto mb-4" aria-hidden="true">
                                <i class="fas fa-star text-2xl"></i>
                            </div>
                            <h4 class="text-lg font-semibold tech-font mb-2">
                                <span class="en">Excellence</span>
                                <span class="farsi">برتری</span>
                            </h4>
                            <p class="text-gray-300">
                                <span class="en">Committed to delivering the highest quality in everything we do.</span>
                                <span class="farsi">متعهد به ارائه بالاترین کیفیت در همه آنچه انجام می‌دهیم.</span>
                            </p>
                        </div>

                        <div class="text-center">
                            <div class="w-16 h-16 rounded-full bg-gradient-to-br from-[#ff007a] to-[#00f0ff] flex items-center justify-center mx-auto mb-4" aria-hidden="true">
                                <i class="fas fa-rocket text-2xl"></i>
                            </div>
                            <h4 class="text-lg font-semibold tech-font mb-2">
                                <span class="en">Impact</span>
                                <span class="farsi">تأثیرگذاری</span>
                            </h4>
                            <p class="text-gray-300">
                                <span class="en">Creating solutions that make a meaningful difference.</span>
                                <span class="farsi">ایجاد راه‌حل‌هایی که تفاوت معناداری ایجاد می‌کنند.</span>
                            </p>
                        </div>
                    </div>
                </div>

                <div class="mb-16">
                    <h3 class="text-2xl font-semibold tech-font text-center gradient-text mb-8">
                        <span class="en">Our Journey</span>
                        <span class="farsi">سفر ما</span>
                    </h3>

                    <div class="timeline-container py-8">
                        <div class="timeline-item feature-panel">
                            <div class="timeline-content holographic p-6 rounded-xl">
                                <h4 class="text-lg font-semibold tech-font mb-2">2018</h4>
                                <p class="text-gray-300">
                                    <span class="en">Founded as a small digital innovation lab with a focus on emerging technologies.</span>
                                    <span class="farsi">به عنوان یک آزمایشگاه کوچک نوآوری دیجیتال با تمرکز بر فناوری‌های نوظهور تأسیس شد.</span>
                                </p>
                            </div>
                        </div>

                        <div class="timeline-item feature-panel">
                            <div class="timeline-content holographic p-6 rounded-xl">
                                <h4 class="text-lg font-semibold tech-font mb-2">2020</h4>
                                <p class="text-gray-300">
                                    <span class="en">Expanded our team and capabilities to include AR/VR development and AI integration.</span>
                                    <span class="farsi">تیم و قابلیت‌های خود را گسترش دادیم تا توسعه AR/VR و یکپارچه‌سازی هوش مصنوعی را شامل شود.</span>
                                </p>
                            </div>
                        </div>

                        <div class="timeline-item feature-panel">
                            <div class="timeline-content holographic p-6 rounded-xl">
                                <h4 class="text-lg font-semibold tech-font mb-2">2021</h4>
                                <p class="text-gray-300">
                                    <span class="en">Launched our first major product, NexusVR, an immersive learning platform.</span>
                                    <span class="farsi">اولین محصول اصلی خود، NexusVR، یک پلتفرم یادگیری غوطه‌ور را راه‌اندازی کردیم.</span>
                                </p>
                            </div>
                        </div>

                        <div class="timeline-item feature-panel">
                            <div class="timeline-content holographic p-6 rounded-xl">
                                <h4 class="text-lg font-semibold tech-font mb-2">2022</h4>
                                <p class="text-gray-300">
                                    <span class="en">Established partnerships with leading tech companies and expanded globally.</span>
                                    <span class="farsi">مشارکت‌هایی با شرکت‌های پیشرو فناوری برقرار کردیم و به صورت جهانی گسترش یافتیم.</span>
                                </p>
                            </div>
                        </div>

                        <div class="timeline-item feature-panel">
                            <div class="timeline-content holographic p-6 rounded-xl">
                                <h4 class="text-lg font-semibold tech-font mb-2">
                                    <span class="en">Today</span>
                                    <span class="farsi">امروز</span>
                                </h4>
                                <p class="text-gray-300">
                                    <span class="en">Continuing to innovate and shape the future of digital experiences worldwide.</span>
                                    <span class="farsi">ادامه نوآوری و شکل‌دهی آینده تجربیات دیجیتال در سراسر جهان.</span>
                                </p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="feature-panel">
                    <h3 class="text-2xl font-semibold tech-font text-center gradient-text mb-8">
                        <span class="en">Our Team</span>
                        <span class="farsi">تیم ما</span>
                    </h3>

                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                        <div class="holographic p-6 rounded-xl text-center team-member">
                            <div class="w-24 h-24 rounded-full bg-gradient-to-br from-[#00f0ff] to-[#5773ff] mx-auto mb-4 overflow-hidden flex items-center justify-center" aria-hidden="true">
                                <i class="fas fa-user text-4xl text-white"></i>
                            </div>
                            <h4 class="text-lg font-semibold tech-font mb-1">قیس حیدری</h4>
                            <p class="text-sm text-[#00f0ff] mb-3">
                                <span class="en">Founder & CEO</span>
                                <span class="farsi">بنیانگذار و مدیرعامل</span>
                            </p>
                            <p class="text-gray-300 text-sm mb-4">
                                <span class="en">Visionary leader with 15+ years in emerging tech.</span>
                                <span class="farsi">رهبر آینده‌نگر با بیش از 15 سال تجربه در فناوری‌های نوظهور.</span>
                            </p>
                            <div class="team-social flex justify-center space-x-3">
                                <a href="https://www.linkedin.com/feed/" target="_blank" class="text-gray-300 hover:text-[#00f0ff] transition-colors" aria-label="LinkedIn">
                                    <i class="fab fa-linkedin-in"></i>
                                </a>
                                <a href="https://x.com/QhVision" target="_blank" class="text-gray-300 hover:text-[#00f0ff] transition-colors" aria-label="X/Twitter">
                                    <i class="fab fa-twitter"></i>
                                </a>
                            </div>
                        </div>

                        <div class="holographic p-6 rounded-xl text-center team-member">
                            <div class="w-24 h-24 rounded-full bg-gradient-to-br from-[#5773ff] to-[#8148ff] mx-auto mb-4 overflow-hidden flex items-center justify-center" aria-hidden="true">
                                <i class="fas fa-user text-4xl text-white"></i>
                            </div>
                            <h4 class="text-lg font-semibold tech-font mb-1">Maya Rodriguez</h4>
                            <p class="text-sm text-[#5773ff] mb-3">
                                <span class="en">CTO</span>
                                <span class="farsi">مدیر فنی</span>
                            </p>
                            <p class="text-gray-300 text-sm mb-4">
                                <span class="en">Expert in AI and immersive technologies.</span>
                                <span class="farsi">متخصص در هوش مصنوعی و فناوری‌های غوطه‌ور.</span>
                            </p>
                            <div class="team-social flex justify-center space-x-3">
                                <a href="https://www.linkedin.com/feed/" target="_blank" class="text-gray-300 hover:text-[#5773ff] transition-colors" aria-label="LinkedIn">
                                    <i class="fab fa-linkedin-in"></i>
                                </a>
                                <a href="#" class="text-gray-300 hover:text-[#5773ff] transition-colors" aria-label="GitHub">
                                    <i class="fab fa-github"></i>
                                </a>
                            </div>
                        </div>

                        <div class="holographic p-6 rounded-xl text-center team-member">
                            <div class="w-24 h-24 rounded-full bg-gradient-to-br from-[#8148ff] to-[#ff007a] mx-auto mb-4 overflow-hidden flex items-center justify-center" aria-hidden="true">
                                <i class="fas fa-user text-4xl text-white"></i>
                            </div>
                            <h4 class="text-lg font-semibold tech-font mb-1">Ravi Patel</h4>
                            <p class="text-sm text-[#8148ff] mb-3">
                                <span class="en">Lead Developer</span>
                                <span class="farsi">توسعه‌دهنده ارشد</span>
                            </p>
                            <p class="text-gray-300 text-sm mb-4">
                                <span class="en">Full-stack expert specializing in XR and blockchain.</span>
                                <span class="farsi">متخصص فول استک با تخصص در XR و بلاکچین.</span>
                            </p>
                            <div class="team-social flex justify-center space-x-3">
                                <a href="https://www.linkedin.com/feed/" target="_blank" class="text-gray-300 hover:text-[#8148ff] transition-colors" aria-label="LinkedIn">
                                    <i class="fab fa-linkedin-in"></i>
                                </a>
                                <a href="#" class="text-gray-300 hover:text-[#8148ff] transition-colors" aria-label="GitHub">
                                    <i class="fab fa-github"></i>
                                </a>
                            </div>
                        </div>

                        <div class="holographic p-6 rounded-xl text-center team-member">
                            <div class="w-24 h-24 rounded-full bg-gradient-to-br from-[#ff007a] to-[#00f0ff] mx-auto mb-4 overflow-hidden flex items-center justify-center" aria-hidden="true">
                                <i class="fas fa-user text-4xl text-white"></i>
                            </div>
                            <h4 class="text-lg font-semibold tech-font mb-1">Sophie Kim</h4>
                            <p class="text-sm text-[#ff007a] mb-3">
                                <span class="en">Design Director</span>
                                <span class="farsi">مدیر طراحی</span>
                            </p>
                            <p class="text-gray-300 text-sm mb-4">
                                <span class="en">Award-winning UX/UI designer and creative visionary.</span>
                                <span class="farsi">طراح برنده جایزه UX/UI و متخصص خلاق.</span>
                            </p>
                            <div class="team-social flex justify-center space-x-3">
                                <a href="https://www.linkedin.com/feed/" target="_blank" class="text-gray-300 hover:text-[#ff007a] transition-colors" aria-label="LinkedIn">
                                    <i class="fab fa-linkedin-in"></i>
                                </a>
                                <a href="#" class="text-gray-300 hover:text-[#ff007a] transition-colors" aria-label="Dribbble">
                                    <i class="fab fa-dribbble"></i>
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="contact" class="section" aria-labelledby="contact-heading">
            <div class="container mx-auto px-6 py-24">
                <div class="text-center mb-16">
                    <h2 id="contact-heading" class="text-4xl md:text-5xl font-bold tech-font gradient-text mb-4" tabindex="-1">
                        <span class="en">GET IN TOUCH</span>
                        <span class="farsi">تماس با ما</span>
                    </h2>
                    <p class="text-xl max-w-3xl mx-auto">
                        <span class="en">Have a project in mind? Let's create something amazing together.</span>
                        <span class="farsi">پروژه‌ای در ذهن دارید؟ بیایید با هم چیزی شگفت‌انگیز بسازیم.</span>
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-12 max-w-6xl mx-auto">
                    <div class="feature-panel">
                        <h3 class="text-2xl font-semibold tech-font gradient-text mb-6">
                            <span class="en">Contact Information</span>
                            <span class="farsi">اطلاعات تماس</span>
                        </h3>

                        <div class="space-y-6">
                            <div class="flex items-start">
                                <div class="w-10 h-10 rounded-lg bg-gradient-to-r from-[#00f0ff] to-[#5773ff] flex items-center justify-center mr-4 flex-shrink-0" aria-hidden="true">
                                    <i class="fas fa-envelope text-lg"></i>
                                </div>
                                <div>
                                    <h4 class="text-lg font-semibold mb-1">
                                        <span class="en">Email</span>
                                        <span class="farsi">ایمیل</span>
                                    </h4>
                                    <a href="mailto:qhvisionx@gmail.com" class="text-gray-300 hover:text-white transition-colors">qhvisionx@gmail.com</a>
                                </div>
                            </div>

                            <div class="flex items-start">
                                <div class="w-10 h-10 rounded-lg bg-gradient-to-r from-[#5773ff] to-[#8148ff] flex items-center justify-center mr-4 flex-shrink-0" aria-hidden="true">
                                    <i class="fas fa-phone-alt text-lg"></i>
                                </div>
                                <div>
                                    <h4 class="text-lg font-semibold mb-1">
                                        <span class="en">Phone</span>
                                        <span class="farsi">تلفن</span>
                                    </h4>
                                    <a href="tel:+18001234567" class="text-gray-300 hover:text-white transition-colors">+1 (800) 123-4567</a>
                                </div>
                            </div>

                            <div class="flex items-start">
                                <div class="w-10 h-10 rounded-lg bg-gradient-to-r from-[#8148ff] to-[#ff007a] flex items-center justify-center mr-4 flex-shrink-0" aria-hidden="true">
                                    <i class="fas fa-map-marker-alt text-lg"></i>
                                </div>
                                <div>
                                    <h4 class="text-lg font-semibold mb-1">
                                        <span class="en">Location</span>
                                        <span class="farsi">موقعیت</span>
                                    </h4>
                                    <address class="text-gray-300 not-italic">
                                        <span class="en">100 Innovation Avenue, San Francisco, CA 94103</span>
                                        <span class="farsi">خیابان نوآوری 100، سانفرانسیسکو، کالیفرنیا 94103</span>
                                    </address>
                                </div>
                            </div>

                            <div class="flex items-start">
                                <div class="w-10 h-10 rounded-lg bg-gradient-to-r from-[#ff007a] to-[#00f0ff] flex items-center justify-center mr-4 flex-shrink-0" aria-hidden="true">
                                    <i class="fas fa-clock text-lg"></i>
                                </div>
                                <div>
                                    <h4 class="text-lg font-semibold mb-1">
                                        <span class="en">Hours</span>
                                        <span class="farsi">ساعات کاری</span>
                                    </h4>
                                    <p class="text-gray-300">
                                        <span class="en">Monday - Friday: 9AM - 6PM PST</span>
                                        <span class="farsi">دوشنبه - جمعه: 9 صبح - 6 عصر به وقت PST</span>
                                    </p>
                                </div>
                            </div>
                        </div>

                        <div class="mt-8">
                            <h4 class="text-lg font-semibold mb-4">
                                <span class="en">Connect With Us</span>
                                <span class="farsi">با ما در ارتباط باشید</span>
                            </h4>
                            <div class="flex space-x-4">
                                <a href="https://x.com/QhVision" target="_blank" class="w-10 h-10 rounded-full bg-gradient-to-r from-[#00f0ff] to-[#5773ff] flex items-center justify-center hover:opacity-80 transition-opacity" aria-label="Twitter">
                                    <i class="fab fa-twitter"></i>
                                </a>
                                <a href="https://www.linkedin.com/feed/" target="_blank" class="w-10 h-10 rounded-full bg-gradient-to-r from-[#5773ff] to-[#8148ff] flex items-center justify-center hover:opacity-80 transition-opacity" aria-label="LinkedIn">
                                    <i class="fab fa-linkedin-in"></i>
                                </a>
                                <a href="https://www.instagram.com/17841474002610954/" target="_blank" class="w-10 h-10 rounded-full bg-gradient-to-r from-[#8148ff] to-[#ff007a] flex items-center justify-center hover:opacity-80 transition-opacity" aria-label="Instagram">
                                    <i class="fab fa-instagram"></i>
                                </a>
                                <a href="https://www.youtube.com/@AfghanTreasures" target="_blank" class="w-10 h-10 rounded-full bg-gradient-to-r from-[#ff007a] to-[#00f0ff] flex items-center justify-center hover:opacity-80 transition-opacity" aria-label="YouTube">
                                    <i class="fab fa-youtube"></i>
                                </a>
                            </div>
                        </div>
                    </div>

                    <div class="feature-panel">
                        <h3 class="text-2xl font-semibold tech-font gradient-text mb-6">
                            <span class="en">Send us a Message</span>
                            <span class="farsi">پیام بفرستید</span>
                        </h3>

                        <form action="#" method="POST" class="space-y-6" aria-label="Contact form">
                            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                                <div>
                                    <label for="name" class="block text-sm font-medium mb-2">
                                        <span class="en">Name</span>
                                        <span class="farsi">نام</span>
                                    </label>
                                    <input type="text" id="name" name="name" class="w-full px-4 py-3 rounded-lg input-field focus:outline-none" placeholder="نام شما / Your Name" required />
                                </div>

                                <div>
                                    <label for="email" class="block text-sm font-medium mb-2">
                                        <span class="en">Email</span>
                                        <span class="farsi">ایمیل</span>
                                    </label>
                                    <input type="email" id="email" name="email" class="w-full px-4 py-3 rounded-lg input-field focus:outline-none" placeholder="ایمیل شما / Your Email" required />
                                </div>
                            </div>

                            <div>
                                <label for="subject" class="block text-sm font-medium mb-2">
                                    <span class="en">Subject</span>
                                    <span class="farsi">موضوع</span>
                                </label>
                                <input type="text" id="subject" name="subject" class="w-full px-4 py-3 rounded-lg input-field focus:outline-none" placeholder="موضوع / Subject" required />
                            </div>

                            <div>
                                <label for="message" class="block text-sm font-medium mb-2">
                                    <span class="en">Message</span>
                                    <span class="farsi">پیام</span>
                                </label>
                                <textarea id="message" name="message" rows="5" class="w-full px-4 py-3 rounded-lg input-field focus:outline-none" placeholder="پیام شما / Your Message" required></textarea>
                            </div>

                            <div>
                                <label for="service" class="block text-sm font-medium mb-2">
                                    <span class="en">Interested in</span>
                                    <span class="farsi">علاقه‌مند به</span>
                                </label>
                                <select id="service" name="service" class="w-full px-4 py-3 rounded-lg input-field focus:outline-none">
                                    <option value="">انتخاب خدمات / Select a Service</option>
                                    <option value="app-development">App Development / توسعه اپلیکیشن</option>
                                    <option value="ar-vr">AR/VR Experiences / تجربیات واقعیت افزوده/مجازی</option>
                                    <option value="ai">AI Solutions / راه‌حل‌های هوش مصنوعی</option>
                                    <option value="ui-ux">UI/UX Design / طراحی UI/UX</option>
                                    <option value="blockchain">Blockchain Development / توسعه بلاکچین</option>
                                    <option value="cloud">Cloud Solutions / راه‌حل‌های ابری</option>
                                    <option value="other">Other / سایر</option>
                                </select>
                            </div>

                            <button type="submit" class="gradient-border bg-[#0a0a12] px-8 py-3 rounded-full tech-font hover:opacity-80 transition-opacity w-full">
                                <span class="en">SEND MESSAGE</span>
                                <span class="farsi">ارسال پیام</span>
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <footer class="bg-[#050508] py-12">
        <div class="container mx-auto px-6">
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 mb-12">
                <div>
                    <div class="flex items-center mb-4">
                        <img src="https://page.genspark.site/v1/base64_upload/65b706f0b5f18802c7fb489b59fd9fcd" alt="QH VisionX Logo, a stylized blue and pink futuristic globe with digital grid lines" class="w-10 h-10 mr-3" />
                        <h3 class="text-xl font-bold tech-font gradient-text">QH VisionX</h3>
                    </div>
                    <p class="text-gray-400 mb-6">
                        <span class="en">Creating immersive digital experiences at the intersection of technology and imagination.</span>
                        <span class="farsi">ایجاد تجربیات دیجیتال غوطه‌ور در تقاطع فناوری و تخیل.</span>
                    </p>
                    <div class="flex space-x-4">
                        <a href="https://x.com/QhVision" target="_blank" class="text-gray-400 hover:text-[#00f0ff] transition-colors" aria-label="Twitter">
                            <i class="fab fa-twitter"></i>
                        </a>
                        <a href="https://www.linkedin.com/feed/" target="_blank" class="text-gray-400 hover:text-[#5773ff] transition-colors" aria-label="LinkedIn">
                            <i class="fab fa-linkedin-in"></i>
                        </a>
                        <a href="https://www.instagram.com/17841474002610954/" target="_blank" class="text-gray-400 hover:text-[#8148ff] transition-colors" aria-label="Instagram">
                            <i class="fab fa-instagram"></i>
                        </a>
                        <a href="https://www.youtube.com/@AfghanTreasures" target="_blank" class="text-gray-400 hover:text-[#ff007a] transition-colors" aria-label="YouTube">
                            <i class="fab fa-youtube"></i>
                        </a>
                    </div>
                </div>

                <div>
                    <h3 class="text-lg font-semibold tech-font mb-6">
                        <span class="en">Services</span>
                        <span class="farsi">خدمات</span>
                    </h3>
                    <ul class="space-y-3">
                        <li><a href="#services" class="text-gray-400 hover:text-white transition-colors">
                            <span class="en">App Development</span>
                            <span class="farsi">توسعه اپلیکیشن</span>
                        </a></li>
                        <li><a href="#services" class="text-gray-400 hover:text-white transition-colors">
                            <span class="en">AR/VR Experiences</span>
                            <span class="farsi">تجربیات واقعیت افزوده/مجازی</span>
                        </a></li>
                        <li><a href="#services" class="text-gray-400 hover:text-white transition-colors">
                            <span class="en">AI Solutions</span>
                            <span class="farsi">راه‌حل‌های هوش مصنوعی</span>
                        </a></li>
                        <li><a href="#services" class="text-gray-400 hover:text-white transition-colors">
                            <span class="en">UI/UX Design</span>
                            <span class="farsi">طراحی UI/UX</span>
                        </a></li>
                        <li><a href="#services" class="text-gray-400 hover:text-white transition-colors">
                            <span class="en">Blockchain Development</span>
                            <span class="farsi">توسعه بلاکچین</span>
                        </a></li>
                    </ul>
                </div>

                <div>
                    <h3 class="text-lg font-semibold tech-font mb-6">
                        <span class="en">Quick Links</span>
                        <span class="farsi">لینک‌های سریع</span>
                    </h3>
                    <ul class="space-y-3">
                        <li><a href="#home" class="text-gray-400 hover:text-white transition-colors">
                            <span class="en">Home</span>
                            <span class="farsi">خانه</span>
                        </a></li>
                        <li><a href="#about" class="text-gray-400 hover:text-white transition-colors">
                            <span class="en">About Us</span>
                            <span class="farsi">درباره ما</span>
                        </a></li>
                        <li><a href="#portfolio" class="text-gray-400 hover:text-white transition-colors">
                            <span class="en">Portfolio</span>
                            <span class="farsi">نمونه کارها</span>
                        </a></li>
                        <li><a href="#contact" class="text-gray-400 hover:text-white transition-colors">
                            <span class="en">Contact</span>
                            <span class="farsi">تماس</span>
                        </a></li>
                    </ul>
                </div>

                <div>
                    <h3 class="text-lg font-semibold tech-font mb-6">
                        <span class="en">Newsletter</span>
                        <span class="farsi">خبرنامه</span>
                    </h3>
                    <p class="text-gray-400 mb-4">
                        <span class="en">Subscribe to our newsletter for the latest updates.</span>
                        <span class="farsi">برای دریافت آخرین به‌روزرسانی‌ها در خبرنامه ما عضو شوید.</span>
                    </p>
                    <form class="flex" aria-label="Newsletter subscription form">
                        <label for="newsletter-email" class="sr-only">Email</label>
                        <input type="email" id="newsletter-email" placeholder="ایمیل شما / Your Email" class="px-4 py-2 rounded-l-lg bg-[#111116] border border-[#333] focus:outline-none focus:border-[#00f0ff] text-white flex-grow" required />
                        <button type="submit" class="bg-gradient-to-r from-[#00f0ff] to-[#5773ff] px-4 py-2 rounded-r-lg" aria-label="Subscribe">
                            <i class="fas fa-paper-plane" aria-hidden="true"></i>
                        </button>
                    </form>
                </div>
            </div>

            <div class="border-t border-gray-800 pt-8">
                <div class="flex flex-col md:flex-row justify-between items-center">
                    <p class="text-gray-400 text-sm mb-4 md:mb-0">
                        <span class="en">&copy; 2023 QH VisionX. All rights reserved.</span>
                        <span class="farsi">&copy; ۲۰۲۳ قیس حیدری | QH VisionX. تمامی حقوق محفوظ است.</span>
                    </p>
                    <div class="flex space-x-6">
                        <a href="#" class="text-gray-400 text-sm hover:text-white transition-colors">
                            <span class="en">Privacy Policy</span>
                            <span class="farsi">سیاست حفظ حریم خصوصی</span>
                        </a>
                        <a href="#" class="text-gray-400 text-sm hover:text-white transition-colors">
                            <span class="en">Terms of Service</span>
                            <span class="farsi">شرایط خدمات</span>
                        </a>
                        <a href="#" class="text-gray-400 text-sm hover:text-white transition-colors">
                            <span class="en">Cookies Policy</span>
                            <span class="farsi">سیاست کوکی‌ها</span>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </footer>

    <script>
        let vantaEffect = null;
        function initVanta() {
            if (vantaEffect) vantaEffect.destroy();

            vantaEffect = VANTA.GLOBE({
                el: "#vanta-bg",
                mouseControls: true,
                touchControls: true,
                gyroControls: false,
                minHeight: 200.0,
                minWidth: 200.0,
                scale: 1.0,
                scaleMobile: 1.0,
                color: 0x5773ff,
                color2: 0xff007a,
                backgroundColor: 0x0a0a12,
                size: 1.5,
            });
        }

        function toggleLanguage() {
            const htmlTag = document.documentElement;
            const currentLang = htmlTag.getAttribute("lang");

            if (currentLang === "fa") {
                htmlTag.setAttribute("lang", "en");
                htmlTag.setAttribute("dir", "ltr");
                document.getElementById("current-lang").textContent = "English";
                document.getElementById("mobile-current-lang").textContent = "English";
                document.querySelectorAll(".en").forEach((el) => (el.style.display = "inline-block"));
                document.querySelectorAll(".farsi").forEach((el) => (el.style.display = "none"));
            } else {
                htmlTag.setAttribute("lang", "fa");
                htmlTag.setAttribute("dir", "rtl");
                document.getElementById("current-lang").textContent = "فارسی";
                document.getElementById("mobile-current-lang").textContent = "فارسی";
                document.querySelectorAll(".en").forEach((el) => (el.style.display = "none"));
                document.querySelectorAll(".farsi").forEach((el) => (el.style.display = "inline-block"));
            }
        }

        document.addEventListener("DOMContentLoaded", function () {
            initVanta();

            const htmlTag = document.documentElement;
            if (htmlTag.getAttribute("lang") === "fa") {
                document.querySelectorAll(".en").forEach((el) => (el.style.display = "none"));
                document.querySelectorAll(".farsi").forEach((el) => (el.style.display = "inline-block"));
            } else {
                document.querySelectorAll(".en").forEach((el) => (el.style.display = "inline-block"));
                document.querySelectorAll(".farsi").forEach((el) => (el.style.display = "none"));
            }

            document.getElementById("lang-switcher").addEventListener("click", toggleLanguage);
            document.getElementById("mobile-lang-switcher").addEventListener("click", toggleLanguage);

            const sections = document.querySelectorAll(".section");
            const navLinks = document.querySelectorAll(".nav-link");
            const mobileMenuButton = document.getElementById("mobile-menu-button");
            const mobileMenu = document.getElementById("mobile-menu");
            const closeMenuButton = document.getElementById("close-menu");

            mobileMenuButton.addEventListener("click", function () {
                mobileMenu.classList.add("open");
                mobileMenu.setAttribute("aria-hidden", "false");
                this.setAttribute("aria-expanded", "true");
                mobileMenu.querySelector("a").focus();
            });

            closeMenuButton.addEventListener("click", function () {
                mobileMenu.classList.remove("open");
                mobileMenu.setAttribute("aria-hidden", "true");
                mobileMenuButton.setAttribute("aria-expanded", "false");
                mobileMenuButton.focus();
            });

            navLinks.forEach((link) => {
                link.addEventListener("click", function (e) {
                    e.preventDefault();

                    const targetSectionId = this.getAttribute("data-section");

                    navLinks.forEach((link) => {
                        link.classList.remove("active");
                        link.setAttribute("aria-current", "false");
                    });
                    this.classList.add("active");
                    this.setAttribute("aria-current", "page");

                    sections.forEach((section) => {
                        section.classList.remove("active");
                        if (section.id === targetSectionId) {
                            section.classList.add("active");
                            window.scrollTo(0, 0);
                            const heading = section.querySelector("h1, h2");
                            if (heading) {
                                heading.setAttribute("tabindex", "-1");
                                heading.focus();
                            }
                        }
                    });

                    mobileMenu.classList.remove("open");
                    mobileMenu.setAttribute("aria-hidden", "true");
                    mobileMenuButton.setAttribute("aria-expanded", "false");
                });
            });

            const featurePanels = document.querySelectorAll(".feature-panel");
            const observer = new IntersectionObserver(
                (entries) => {
                    entries.forEach((entry) => {
                        if (entry.isIntersecting) {
                            entry.target.classList.add("visible");
                            observer.unobserve(entry.target);
                        }
                    });
                },
                { threshold: 0.1 }
            );

            featurePanels.forEach((panel) => {
                observer.observe(panel);
            });

            document.addEventListener("keydown", function (e) {
                if (e.key === "Escape" && mobileMenu.classList.contains("open")) {
                    mobileMenu.classList.remove("open");
                    mobileMenu.setAttribute("aria-hidden", "true");
                    mobileMenuButton.setAttribute("aria-expanded", "false");
                    mobileMenuButton.focus();
                }
            });

            let resizeTimer;
            window.addEventListener("resize", function () {
                clearTimeout(resizeTimer);
                resizeTimer = setTimeout(function () {
                    initVanta();
                }, 250);
            });
        });
    </script>
</body>
</html>
