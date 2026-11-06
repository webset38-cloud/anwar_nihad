
<!DOCTYPE html>
<html lang="en" class="scroll-smooth" dir="ltr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nihad & Anwar's Wedding Invitation</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Cormorant Garamond, Montserrat & Amiri (for Arabic) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Amiri:ital,wght@0,400;0,700;1,400&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400;1,600&family=Montserrat:wght@200;300;400;500;600&display=swap" rel="stylesheet">
    <!-- FontAwesome for icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        champagne: {
                            50: '#fcfbfa',
                            100: '#f5f0eb',
                            200: '#e8ded4',
                            300: '#d7c7b8',
                            400: '#c4ab96',
                            500: '#b0937a',
                            600: '#9d7f67',
                            700: '#826652',
                            800: '#6a5343',
                            900: '#564337',
                        },
                        gold: {
                            light: '#dfc28d',
                            DEFAULT: '#c5a059',
                            dark: '#9a7b3c',
                            metallic: '#d4af37'
                        },
                        ivory: '#FAF8F5',
                        charcoal: '#222222'
                    },
                    fontFamily: {
                        serif: ['"Cormorant Garamond"', 'serif'],
                        sans: ['Montserrat', 'sans-serif'],
                        arabic: ['Amiri', 'serif'],
                    }
                }
            }
        }
    </script>

    <style>
        body {
            font-family: 'Montserrat', sans-serif;
            background-color: #FAF8F5;
            color: #222222;
            overflow-x: hidden;
        }

        body.lang-ar {
            font-family: 'Amiri', serif;
        }

        h1, h2, h3, h4, .font-serif {
            font-family: 'Cormorant Garamond', serif;
        }

        body.lang-ar h1, body.lang-ar h2, body.lang-ar h3, body.lang-ar h4, body.lang-ar .font-serif {
            font-family: 'Amiri', serif;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f5f0eb;
        }
        ::-webkit-scrollbar-thumb {
            background: #c5a059;
            border-radius: 4px;
        }

        /* Envelope open animations */
        .envelope-container {
            perspective: 1500px;
        }
        
        .envelope-flap-top {
            transform-origin: top;
            transition: transform 1.2s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .envelope-open .envelope-flap-top {
            transform: rotateX(180deg);
            z-index: 10;
        }

        .invitation-card {
            transition: all 1.5s cubic-bezier(0.16, 1, 0.3, 1);
            transform: translateY(0) scale(0.95);
        }

        .envelope-open .invitation-card {
            transform: translateY(-160px) scale(1);
            box-shadow: 0 25px 50px -12px rgba(197, 160, 89, 0.25);
        }

        @media (min-width: 768px) {
            .envelope-open .invitation-card {
                transform: translateY(-200px) scale(1);
            }
        }

        /* Foil Shimmer effect */
        .gold-foil {
            background: linear-gradient(135deg, #bf953f 0%, #fcf6ba 25%, #b38728 50%, #fbf5b7 75%, #aa771c 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* Wax seal pulse */
        @keyframes pulse-gold {
            0% { box-shadow: 0 0 0 0 rgba(197, 160, 89, 0.6); }
            70% { box-shadow: 0 0 0 20px rgba(197, 160, 89, 0); }
            100% { box-shadow: 0 0 0 0 rgba(197, 160, 89, 0); }
        }

        .wax-seal {
            animation: pulse-gold 2s infinite;
        }

        /* Subtle float animation */
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-8px); }
            100% { transform: translateY(0px); }
        }

        .floating {
            animation: float 4s ease-in-out infinite;
        }

        /* Paper texture overlay */
        .paper-texture {
            background-color: #FAF8F5;
            background-image: radial-gradient(circle at 50% 50%, rgba(212, 175, 55, 0.03) 0%, rgba(0, 0, 0, 0.02) 100%);
        }
    </style>
</head>
<body class="paper-texture antialiased selection:bg-gold/20 selection:text-gold-dark">

    <!-- Language Switcher Bar -->
    <div class="fixed top-4 left-4 z-50 flex items-center bg-white/90 backdrop-blur-md border border-gold/40 rounded-full shadow-lg p-1">
        <button onclick="setLanguage('en')" id="langEn" class="px-3 py-1 text-xs font-semibold rounded-full transition-all text-charcoal hover:text-gold">EN</button>
        <button onclick="setLanguage('fr')" id="langFr" class="px-3 py-1 text-xs font-semibold rounded-full transition-all text-charcoal hover:text-gold">FR</button>
        <button onclick="setLanguage('ar')" id="langAr" class="px-3 py-1 text-xs font-semibold rounded-full transition-all bg-gold text-white">العربية</button>
    </div>

    <!-- Audio Element (Maher Zain - Baraka Allah Lakuma) -->
    <audio id="bgMusic" loop preload="auto">
        <source src="https://cdn.jsdelivr.net/gh/ann-project/audio-repo@main/MaherZainBarakaAllah.mp3" onerror="this.src='https://assets.mixkit.co/music/preview/mixkit-wedding-march-482.mp3'" type="audio/mpeg">
    </audio>

    <!-- Floating Music & Audio Control Widget -->
    <div id="musicControl" class="fixed bottom-6 right-6 z-50 hidden opacity-0 transition-opacity duration-700">
        <button onclick="toggleMusic()" id="musicBtn" class="flex items-center gap-2 bg-white/90 backdrop-blur-md border border-gold/40 text-charcoal px-4 py-3 rounded-full shadow-lg hover:bg-gold hover:text-white transition-all duration-300 group">
            <div class="w-6 h-6 flex items-center justify-center text-gold group-hover:text-white">
                <i id="musicIcon" class="fa-solid fa-music animate-spin" style="animation-duration: 3s;"></i>
            </div>
            <span id="musicText" class="text-xs tracking-widest uppercase font-medium pr-1">موسيقى الزفاف</span>
        </button>
    </div>

    <!-- Notification Toast -->
    <div id="toast" class="fixed top-6 left-1/2 -translate-x-1/2 z-50 transform -translate-y-24 opacity-0 transition-all duration-500 bg-charcoal text-white px-6 py-3 rounded-full shadow-2xl border border-gold/40 text-sm tracking-wider flex items-center gap-3">
        <i class="fa-solid fa-heart text-gold"></i>
        <span id="toastMessage">Notification message</span>
    </div>

    <!-- ========================================== -->
    <!-- SECTION 1: THE LUXURY SEALED ENVELOPE      -->
    <!-- ========================================== -->
    <div id="envelopeScreen" class="fixed inset-0 z-45 bg-[#121110] flex items-center justify-center p-4 transition-opacity duration-1000 overflow-hidden">
        
        <div class="absolute w-[500px] h-[500px] bg-gold/10 rounded-full blur-3xl pointer-events-none"></div>

        <div class="envelope-container relative w-full max-w-lg aspect-[4/3] sm:aspect-[16/11] flex items-center justify-center">
            
            <div id="envelope" class="absolute inset-0 bg-[#f7f3ed] rounded-lg shadow-2xl border border-champagne-300 overflow-hidden transition-transform duration-700">
                
                <div id="slidingCard" class="invitation-card absolute left-4 right-4 top-12 bottom-4 bg-white border-2 border-gold/40 rounded-md p-6 sm:p-8 text-center flex flex-col justify-between shadow-inner z-0">
                    <div class="absolute inset-0 pointer-events-none border border-gold/20 m-2"></div>
                    
                    <div class="space-y-2 mt-2">
                        <p class="text-xs uppercase tracking-[0.3em] text-gold-dark" data-i18n="envSubtitle">بدعوة كريمة منّا إليكم</p>
                        <h2 class="text-2xl sm:text-3xl font-serif text-charcoal font-medium tracking-wide">نهاد & أنور</h2>
                        <div class="w-12 h-[1px] bg-gold mx-auto my-2"></div>
                        <p class="text-xs tracking-[0.2em] text-stone-500">07 • 07 • 2027</p>
                    </div>

                    <div class="my-auto py-4">
                        <p class="text-xs sm:text-sm text-stone-600 italic font-serif" data-i18n="envQuote">"بداية أبدیتنا السعيدة..."</p>
                    </div>

                    <div>
                        <span class="inline-block text-[10px] tracking-[0.25em] uppercase px-4 py-2 bg-champagne-100 text-gold-dark rounded-full" data-i18n="envVenue">قاعة خوالو • الفنيدق</span>
                    </div>
                </div>

                <div class="absolute inset-0 z-20 pointer-events-none">
                    <div class="absolute left-0 top-0 bottom-0 w-1/2 bg-gradient-to-r from-[#eadecc] to-[#f0e6da] clip-left-flap shadow-inner"></div>
                    <div class="absolute right-0 top-0 bottom-0 w-1/2 bg-gradient-to-l from-[#eadecc] to-[#f0e6da] clip-right-flap shadow-inner"></div>
                    <div class="absolute bottom-0 left-0 right-0 h-1/2 bg-gradient-to-t from-[#e4d6c2] to-[#f5eee3] shadow-lg"></div>
                </div>

                <div id="envelopeFlap" class="envelope-flap-top absolute top-0 left-0 right-0 h-1/2 bg-gradient-to-b from-[#f2ece2] to-[#e4d6c2] z-30 shadow-md border-b border-champagne-300">
                    <div class="absolute bottom-0 left-0 right-0 h-[1px] bg-gold/30"></div>
                </div>

                <div id="waxSealContainer" class="absolute top-[45%] left-1/2 -translate-x-1/2 -translate-y-1/2 z-40 cursor-pointer group transition-transform duration-300 hover:scale-105">
                    <div class="wax-seal w-16 h-16 sm:w-20 sm:h-20 bg-gradient-to-br from-amber-800 via-amber-900 to-amber-950 rounded-full flex items-center justify-center shadow-2xl border-2 border-amber-600 relative">
                        <div class="absolute inset-1.5 rounded-full border border-amber-700/60 flex items-center justify-center">
                            <span class="font-serif text-amber-200 text-lg sm:text-xl font-bold tracking-tighter drop-shadow-md">N & A</span>
                        </div>
                    </div>
                    <div class="absolute -bottom-10 left-1/2 -translate-x-1/2 whitespace-nowrap bg-charcoal/90 text-gold text-[10px] tracking-[0.2em] uppercase px-3 py-1 rounded-full opacity-90 group-hover:opacity-100 transition-opacity shadow-lg" data-i18n="clickSeal">
                        انقر على الختم للفتح
                    </div>
                </div>

            </div>

        </div>

        <div class="absolute bottom-12 left-0 right-0 text-center z-40 px-4">
            <button onclick="openInvitation()" id="openBtn" class="bg-gradient-to-r from-gold via-amber-500 to-gold-dark text-white font-medium text-xs sm:text-sm tracking-[0.25em] uppercase px-8 py-4 rounded-full shadow-2xl hover:shadow-gold/50 hover:scale-105 transition-all duration-300 border border-gold-light/40">
                <i class="fa-solid fa-envelope-open mr-2"></i> <span data-i18n="openBtnText">افتح بطاقة الدعوة</span>
            </button>
        </div>

    </div>


    <!-- ========================================== -->
    <!-- SECTION 2: MAIN WEBSITE CONTENT            -->
    <!-- ========================================== -->
    <div id="mainContent" class="opacity-0 pointer-events-none transition-opacity duration-1000">

        <!-- Hero Section -->
        <section class="relative min-h-screen flex flex-col items-center justify-center px-4 py-20 bg-gradient-to-b from-[#FAF8F5] via-[#f5f0eb] to-[#FAF8F5]">
            <div class="absolute inset-0 opacity-10 bg-[radial-gradient(#c5a059_1px,transparent_1px)] [background-size:24px_24px] pointer-events-none"></div>

            <div class="max-w-4xl w-full mx-auto bg-white border border-gold/30 rounded-2xl shadow-2xl overflow-hidden relative my-auto">
                <div class="absolute top-4 left-4 w-12 h-12 border-t-2 border-l-2 border-gold/50 pointer-events-none"></div>
                <div class="absolute top-4 right-4 w-12 h-12 border-t-2 border-r-2 border-gold/50 pointer-events-none"></div>
                <div class="absolute bottom-4 left-4 w-12 h-12 border-b-2 border-l-2 border-gold/50 pointer-events-none"></div>
                <div class="absolute bottom-4 right-4 w-12 h-12 border-b-2 border-r-2 border-gold/50 pointer-events-none"></div>

                <div class="grid grid-cols-1 md:grid-cols-12 items-center">
                    
                    <div class="md:col-span-6 relative h-[380px] md:h-[580px] overflow-hidden">
                        <img src="https://images.unsplash.com/photo-1519741497674-611481863552?auto=format&fit=crop&w=1200&q=80" 
                             alt="Nihad and Anwar Wedding" 
                             class="w-full h-full object-cover object-center transform hover:scale-105 transition-transform duration-1000"
                             onerror="this.src='https://placehold.co/800x1200/e8ded4/564337?text=Nihad+%26+Anwar'">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/50 via-transparent to-transparent md:hidden"></div>
                    </div>

                    <div class="md:col-span-6 p-8 sm:p-12 text-center flex flex-col justify-center space-y-6">
                        
                        <div class="space-y-2">
                            <span class="text-xs uppercase tracking-[0.35em] text-gold-dark font-medium" data-i18n="heroSubtitle">حفل الزفاف الميمون</span>
                            <h1 class="text-4xl sm:text-5xl font-serif font-normal text-charcoal tracking-wide">
                                نهاد <span class="text-gold font-light italic">&</span> أنور
                            </h1>
                            <div class="w-16 h-[1px] bg-gold mx-auto my-3"></div>
                        </div>

                        <p class="text-stone-600 text-sm sm:text-base font-serif italic leading-relaxed px-2" data-i18n="invitationMsg">
                            "بكل الحب والسعادة، نتشرف بدعوتكم لحضور حفل زفافنا ومشاركتنا بداية رحلتنا الأبدية. حضوركم يزيد يومنا جمالاً وبهجة."
                        </p>

                        <div class="pt-2 space-y-1">
                            <p class="text-xs tracking-[0.25em] uppercase text-gold-dark font-semibold" data-i18n="weddingDateStr">الأربعاء، 7 يوليو 2027</p>
                            <p class="text-xs tracking-[0.2em] text-stone-500 uppercase" data-i18n="weddingLocationStr">قاعة خوالو • الفنيدق، المغرب</p>
                        </div>

                        <div class="pt-4">
                            <a href="#details" class="inline-block text-xs uppercase tracking-[0.25em] text-charcoal hover:text-gold transition-colors font-medium border-b border-charcoal/30 hover:border-gold pb-1">
                                <span data-i18n="discoverDetails">اكتشف التفاصيل</span> <i class="fa-solid fa-arrow-down ml-1 text-[10px]"></i>
                            </a>
                        </div>

                    </div>

                </div>
            </div>

            <div class="absolute bottom-6 left-1/2 -translate-x-1/2 text-center floating hidden sm:block">
                <a href="#details" class="text-gold-dark text-sm">
                    <i class="fa-solid fa-chevron-down"></i>
                </a>
            </div>
        </section>


        <!-- ========================================== -->
        <!-- SECTION 3: COUNTDOWN TIMER                 -->
        <!-- ========================================== -->
        <section id="details" class="py-20 px-4 bg-champagne-100 relative">
            <div class="max-w-4xl mx-auto text-center space-y-12">
                
                <div class="space-y-3">
                    <span class="text-xs uppercase tracking-[0.3em] text-gold-dark font-medium" data-i18n="countdownSub">العد التنازلي للحظة الكبرى</span>
                    <h2 class="text-3xl sm:text-4xl font-serif text-charcoal" data-i18n="weddingDayTitle">يوم الزفاف</h2>
                    <div class="w-12 h-[1px] bg-gold mx-auto"></div>
                </div>

                <!-- Timer Grid -->
                <div class="grid grid-cols-2 sm:grid-cols-4 gap-4 sm:gap-6 max-w-2xl mx-auto">
                    
                    <div class="bg-white/90 backdrop-blur border border-gold/30 rounded-xl p-6 shadow-md">
                        <span id="days" class="text-3xl sm:text-4xl font-serif font-bold text-charcoal block">00</span>
                        <span class="text-[10px] sm:text-xs uppercase tracking-[0.2em] text-stone-500 mt-1 block" data-i18n="daysLabel">أيام</span>
                    </div>

                    <div class="bg-white/90 backdrop-blur border border-gold/30 rounded-xl p-6 shadow-md">
                        <span id="hours" class="text-3xl sm:text-4xl font-serif font-bold text-charcoal block">00</span>
                        <span class="text-[10px] sm:text-xs uppercase tracking-[0.2em] text-stone-500 mt-1 block" data-i18n="hoursLabel">ساعات</span>
                    </div>

                    <div class="bg-white/90 backdrop-blur border border-gold/30 rounded-xl p-6 shadow-md">
                        <span id="minutes" class="text-3xl sm:text-4xl font-serif font-bold text-charcoal block">00</span>
                        <span class="text-[10px] sm:text-xs uppercase tracking-[0.2em] text-stone-500 mt-1 block" data-i18n="minutesLabel">دقائق</span>
                    </div>

                    <div class="bg-white/90 backdrop-blur border border-gold/30 rounded-xl p-6 shadow-md">
                        <span id="seconds" class="text-3xl sm:text-4xl font-serif font-bold text-charcoal block">00</span>
                        <span class="text-[10px] sm:text-xs uppercase tracking-[0.2em] text-stone-500 mt-1 block" data-i18n="secondsLabel">ثوانٍ</span>
                    </div>

                </div>

                <!-- Venue Card -->
                <div class="max-w-xl mx-auto bg-white border border-gold/30 rounded-2xl p-8 shadow-xl relative mt-12 text-center space-y-6">
                    <div class="w-12 h-12 bg-champagne-100 text-gold rounded-full flex items-center justify-center mx-auto text-xl shadow-inner">
                        <i class="fa-solid fa-location-dot"></i>
                    </div>

                    <div class="space-y-2">
                        <h3 class="text-2xl font-serif text-charcoal" data-i18n="venueTitle">قاعة خوالو</h3>
                        <p class="text-xs uppercase tracking-[0.25em] text-gold-dark">Khawalo Hall</p>
                        <p class="text-stone-600 text-sm" data-i18n="venueCity">الفنيدق، المغرب</p>
                    </div>

                    <div>
                        <a href="https://www.google.com/maps/place//data=!4m2!3m1!19sChIJa-h83ZihDA0ROPqancTimdo" target="_blank" rel="noopener noreferrer" 
                           class="inline-flex items-center gap-2 bg-charcoal text-white hover:bg-gold transition-colors text-xs uppercase tracking-[0.2em] px-6 py-3 rounded-full shadow-md">
                            <i class="fa-solid fa-map-location-dot"></i> <span data-i18n="viewLocation">عرض الموقع على الخريطة</span>
                        </a>
                    </div>
                </div>

            </div>
        </section>


        <!-- ========================================== -->
        <!-- SECTION 4: ROMANTIC PHOTO GALLERY          -->
        <!-- ========================================== -->
        <section class="py-24 px-4 bg-white">
            <div class="max-w-6xl mx-auto space-y-12">
                
                <div class="text-center space-y-3">
                    <span class="text-xs uppercase tracking-[0.3em] text-gold-dark font-medium" data-i18n="gallerySub">لحظات من الحب</span>
                    <h2 class="text-3xl sm:text-4xl font-serif text-charcoal" data-i18n="galleryTitle">معرض الصور</h2>
                    <div class="w-12 h-[1px] bg-gold mx-auto"></div>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    
                    <div class="group relative overflow-hidden rounded-xl shadow-lg aspect-[3/4]">
                        <img src="https://images.unsplash.com/photo-1583939003579-730e3918a45a?auto=format&fit=crop&w=800&q=80" 
                             alt="Romantic Bride and Groom" 
                             class="w-full h-full object-cover transform group-hover:scale-105 transition-transform duration-700"
                             onerror="this.src='https://placehold.co/600x800/e8ded4/564337?text=Moment+1'">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end p-6">
                            <p class="text-white text-xs uppercase tracking-[0.2em] font-medium" data-i18n="galleryCaption1">معاً للأبد</p>
                        </div>
                    </div>

                    <div class="group relative overflow-hidden rounded-xl shadow-lg aspect-[3/4] md:-translate-y-6">
                        <img src="https://images.unsplash.com/photo-1532712938310-34cb3982ef74?auto=format&fit=crop&w=800&q=80" 
                             alt="Wedding Ring Details" 
                             class="w-full h-full object-cover transform group-hover:scale-105 transition-transform duration-700"
                             onerror="this.src='https://placehold.co/600x800/e8ded4/564337?text=Moment+2'">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end p-6">
                            <p class="text-white text-xs uppercase tracking-[0.2em] font-medium" data-i18n="galleryCaption2">الوعد</p>
                        </div>
                    </div>

                    <div class="group relative overflow-hidden rounded-xl shadow-lg aspect-[3/4]">
                        <img src="https://images.unsplash.com/photo-1511285560929-80b456fea0bc?auto=format&fit=crop&w=800&q=80" 
                             alt="Joyful Celebration" 
                             class="w-full h-full object-cover transform group-hover:scale-105 transition-transform duration-700"
                             onerror="this.src='https://placehold.co/600x800/e8ded4/564337?text=Moment+3'">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end p-6">
                            <p class="text-white text-xs uppercase tracking-[0.2em] font-medium" data-i18n="galleryCaption3">فرحة لا تنتهي</p>
                        </div>
                    </div>

                </div>

            </div>
        </section>


        <!-- ========================================== -->
        <!-- SECTION 5: FINAL CLOSING SECTION           -->
        <!-- ========================================== -->
        <section class="py-24 px-4 bg-gradient-to-t from-[#f5f0eb] to-white text-center relative overflow-hidden">
            <div class="absolute inset-0 opacity-5 bg-[radial-gradient(#c5a059_1px,transparent_1px)] [background-size:24px_24px] pointer-events-none"></div>

            <div class="max-w-2xl mx-auto space-y-8 relative z-10">
                <div class="w-16 h-16 bg-gold/10 text-gold rounded-full flex items-center justify-center mx-auto text-2xl">
                    <i class="fa-solid fa-heart"></i>
                </div>

                <div class="space-y-4">
                    <span class="text-xs uppercase tracking-[0.3em] text-gold-dark font-medium" data-i18n="closingSub">بكل شوق واهتمام</span>
                    <h2 class="text-3xl sm:text-5xl font-serif text-charcoal" data-i18n="closingTitle">ننتظركم بفارغ الصبر لنحتفل معاً!</h2>
                    <div class="w-16 h-[1px] bg-gold mx-auto"></div>
                </div>

                <div class="space-y-2">
                    <p class="text-2xl font-serif text-charcoal tracking-wide">نهاد & أنور</p>
                    <p class="text-xs uppercase tracking-[0.25em] text-stone-500">07 • 07 • 2027</p>
                </div>

                <div class="pt-6">
                    <button onclick="showToast(translations[currentLang].toastWish)" class="bg-gold hover:bg-gold-dark text-white text-xs uppercase tracking-[0.25em] px-8 py-4 rounded-full shadow-lg transition-all duration-300">
                        <i class="fa-solid fa-glass-cheers mr-2"></i> <span data-i18n="sendWishes">إرسال التهاني</span>
                    </button>
                </div>
            </div>

            <footer class="mt-20 pt-8 border-t border-champagne-300 text-stone-500 text-xs tracking-widest uppercase" data-i18n="footerText">
                &copy; 2027 حفل زفاف نهاد وأنور • صُمم بفخامة
            </footer>
        </section>

    </div>


    <!-- JavaScript Application Logic & Translations -->
    <script>
        const translations = {
            ar: {
                envSubtitle: "بدعوة كريمة منّا إليكم",
                envQuote: '"بداية أبدیتنا السعيدة..."',
                envVenue: "قاعة خوالو • الفنيدق",
                clickSeal: "انقر على الختم للفتح",
                openBtnText: "افتح بطاقة الدعوة",
                heroSubtitle: "حفل الزفاف الميمون",
                invitationMsg: '"بكل الحب والسعادة، نتشرف بدعوتكم لحضور حفل زفافنا ومشاركتنا بداية رحلتنا الأبدية. حضوركم يزيد يومنا جمالاً وبهجة."',
                weddingDateStr: "الأربعاء، 7 يوليو 2027",
                weddingLocationStr: "قاعة خوالو • الفنيدق، المغرب",
                discoverDetails: "اكتشف التفاصيل",
                countdownSub: "العد التنازلي للحظة الكبرى",
                weddingDayTitle: "يوم الزفاف",
                daysLabel: "أيام",
                hoursLabel: "ساعات",
                minutesLabel: "دقائق",
                secondsLabel: "ثوانٍ",
                venueTitle: "قاعة خوالو",
                venueCity: "الفنيدق، المغرب",
                viewLocation: "عرض الموقع على الخريطة",
                gallerySub: "لحظات من الحب",
                galleryTitle: "معرض الصور",
                galleryCaption1: "معاً للأبد",
                galleryCaption2: "الوعد",
                galleryCaption3: "فرحة لا تنتهي",
                closingSub: "بكل شوق واهتمام",
                closingTitle: "ننتظركم بفارغ الصبر لنحتفل معاً!",
                sendWishes: "إرسال التهاني",
                footerText: "© 2027 حفل زفاف نهاد وأنور • صُمم بفخامة",
                musicOn: "موسيقى الزفاف",
                musicOff: "إيقاف الموسيقى",
                toastWelcome: "مرحباً بكم في حفل زفاف نهاد وأنور!",
                toastMusicPlay: "تم تشغيل نشيد بارك الله لكما (ماهر زين).",
                toastMusicPause: "تم إيقاف الموسيقى.",
                toastAudioErr: "تعذر تشغيل الصوت تلقائياً. يرجى استخدام زر الموسيقى في الأسفل.",
                toastWish: "شكراً لمشاعركم الطيبة! نتطلع لرؤيتكم قريباً."
            },
            fr: {
                envSubtitle: "Vous êtes cordialement invités",
                envQuote: '"Le début de notre éternité..."',
                envVenue: "Salle Khawalo • Fnideq",
                clickSeal: "Cliquez sur le sceau pour ouvrir",
                openBtnText: "Ouvrir votre invitation",
                heroSubtitle: "La Célébration du Mariage",
                invitationMsg: '"C\'est avec amour et bonheur que nous vous invitons à célébrer le début de notre éternité. Votre présence rendra notre journée encore plus belle."',
                weddingDateStr: "Mercredi 7 Juillet 2027",
                weddingLocationStr: "Salle Khawalo • Fnideq, Maroc",
                discoverDetails: "Découvrir les détails",
                countdownSub: "Compte à rebours vers l'éternité",
                weddingDayTitle: "Le Jour du Mariage",
                daysLabel: "Jours",
                hoursLabel: "Heures",
                minutesLabel: "Minutes",
                secondsLabel: "Secondes",
                venueTitle: "Salle Khawalo",
                venueCity: "Fnideq, Maroc",
                viewLocation: "Voir l'emplacement",
                gallerySub: "Moments d'Amour",
                galleryTitle: "Notre Galerie",
                galleryCaption1: "À jamais vôtres",
                galleryCaption2: "La Promesse",
                galleryCaption3: "Joie Infinie",
                closingSub: "Avec une joie immense",
                closingTitle: "Nous avons hâte de célébrer avec vous !",
                sendWishes: "Envoyer vos voeux",
                footerText: "© 2027 Mariage Nihad & Anwar • Conçu avec Luxe",
                musicOn: "Musique de mariage",
                musicOff: "Musique désactivée",
                toastWelcome: "Bienvenue à l'invitation de mariage de Nihad & Anwar !",
                toastMusicPlay: "Musique de fond en lecture.",
                toastMusicPause: "Musique de fond en pause.",
                toastAudioErr: "Impossible de lancer l'audio. Veuillez vérifier les autorisations.",
                toastWish: "Merci pour vos vœux chaleureux ! Nous avons hâte de vous voir."
            },
            en: {
                envSubtitle: "You're Cordially Invited",
                envQuote: '"The beginning of our forever..."',
                envVenue: "Khawalo Hall • Fnideq",
                clickSeal: "Click Seal to Open",
                openBtnText: "Open Your Invitation",
                heroSubtitle: "The Wedding Celebration",
                invitationMsg: '"With love and happiness, we invite you to celebrate the beginning of our forever. Your presence will make our special day even more beautiful."',
                weddingDateStr: "Wednesday, July 7, 2027",
                weddingLocationStr: "Khawalo Hall • Fnideq, Morocco",
                discoverDetails: "Discover Details",
                countdownSub: "Counting Down to Forever",
                weddingDayTitle: "The Wedding Day",
                daysLabel: "Days",
                hoursLabel: "Hours",
                minutesLabel: "Minutes",
                secondsLabel: "Seconds",
                venueTitle: "Khawalo Hall",
                venueCity: "Fnideq, Morocco",
                viewLocation: "View Location",
                gallerySub: "Moments of Love",
                galleryTitle: "Our Gallery",
                galleryCaption1: "Forever Yours",
                galleryCaption2: "The Promise",
                galleryCaption3: "Endless Joy",
                closingSub: "With Joyful Anticipation",
                closingTitle: "We Can't Wait to Celebrate With You!",
                sendWishes: "Send Best Wishes",
                footerText: "© 2027 Nihad & Anwar Wedding • Designed with Luxury",
                musicOn: "Wedding Music",
                musicOff: "Music Off",
                toastWelcome: "Welcome to Nihad & Anwar's Wedding Invitation!",
                toastMusicPlay: "Background music playing.",
                toastMusicPause: "Background music paused.",
                toastAudioErr: "Unable to auto-play audio. Please check browser permissions.",
                toastWish: "Thank you for confirming your excitement! We look forward to seeing you."
            }
        };

        let currentLang = 'ar'; // Default language set to Arabic

        function setLanguage(lang) {
            currentLang = lang;
            const htmlTag = document.documentElement;
            const bodyTag = document.body;

            if (lang === 'ar') {
                htmlTag.setAttribute('dir', 'rtl');
                bodyTag.classList.add('lang-ar');
                document.getElementById('langAr').className = "px-3 py-1 text-xs font-semibold rounded-full transition-all bg-gold text-white";
                document.getElementById('langEn').className = "px-3 py-1 text-xs font-semibold rounded-full transition-all text-charcoal hover:text-gold";
                document.getElementById('langFr').className = "px-3 py-1 text-xs font-semibold rounded-full transition-all text-charcoal hover:text-gold";
            } else if (lang === 'fr') {
                htmlTag.setAttribute('dir', 'ltr');
                bodyTag.classList.remove('lang-ar');
                document.getElementById('langFr').className = "px-3 py-1 text-xs font-semibold rounded-full transition-all bg-gold text-white";
                document.getElementById('langEn').className = "px-3 py-1 text-xs font-semibold rounded-full transition-all text-charcoal hover:text-gold";
                document.getElementById('langAr').className = "px-3 py-1 text-xs font-semibold rounded-full transition-all text-charcoal hover:text-gold";
            } else {
                htmlTag.setAttribute('dir', 'ltr');
                bodyTag.classList.remove('lang-ar');
                document.getElementById('langEn').className = "px-3 py-1 text-xs font-semibold rounded-full transition-all bg-gold text-white";
                document.getElementById('langFr').className = "px-3 py-1 text-xs font-semibold rounded-full transition-all text-charcoal hover:text-gold";
                document.getElementById('langAr').className = "px-3 py-1 text-xs font-semibold rounded-full transition-all text-charcoal hover:text-gold";
            }

            // Update all elements with data-i18n attribute
            const elements = document.querySelectorAll('[data-i18n]');
            elements.forEach(el => {
                const key = el.getAttribute('data-i18n');
                if (translations[lang][key]) {
                    el.textContent = translations[lang][key];
                }
            });
        }

        // Initialize Arabic on load
        setLanguage('ar');

        // Custom Toast Notification System
        function showToast(message) {
            const toast = document.getElementById('toast');
            const toastMessage = document.getElementById('toastMessage');
            toastMessage.textContent = message;
            
            toast.classList.remove('-translate-y-24', 'opacity-0');
            toast.classList.add('translate-y-0', 'opacity-100');
            
            setTimeout(() => {
                toast.classList.remove('translate-y-0', 'opacity-100');
                toast.classList.add('-translate-y-24', 'opacity-0');
            }, 4000);
        }

        // Music Control State
        let isPlaying = false;
        const bgMusic = document.getElementById('bgMusic');
        const musicControl = document.getElementById('musicControl');
        const musicIcon = document.getElementById('musicIcon');
        const musicText = document.getElementById('musicText');

        function toggleMusic() {
            if (isPlaying) {
                bgMusic.pause();
                isPlaying = false;
                musicIcon.className = "fa-solid fa-music";
                musicText.textContent = translations[currentLang].musicOff;
                showToast(translations[currentLang].toastMusicPause);
            } else {
                bgMusic.play().then(() => {
                    isPlaying = true;
                    musicIcon.className = "fa-solid fa-music animate-spin";
                    musicText.textContent = translations[currentLang].musicOn;
                    showToast(translations[currentLang].toastMusicPlay);
                }).catch(e => {
                    console.error("Audio playback error:", e);
                    showToast(translations[currentLang].toastAudioErr);
                });
            }
        }

        // Envelope Opening Interaction
        function openInvitation() {
            const envelopeScreen = document.getElementById('envelopeScreen');
            const envelope = document.getElementById('envelope');
            const mainContent = document.getElementById('mainContent');

            envelope.classList.add('envelope-open');

            bgMusic.volume = 0.5;
            bgMusic.play().then(() => {
                isPlaying = true;
                musicControl.classList.remove('hidden');
                setTimeout(() => {
                    musicControl.classList.remove('opacity-0');
                }, 100);
            }).catch(e => {
                console.log("Autoplay restricted, showing music control so user can start manually.");
                musicControl.classList.remove('hidden');
                setTimeout(() => {
                    musicControl.classList.remove('opacity-0');
                }, 100);
            });

            setTimeout(() => {
                envelopeScreen.style.opacity = '0';
                setTimeout(() => {
                    envelopeScreen.style.display = 'none';
                    mainContent.classList.remove('opacity-0', 'pointer-events-none');
                    showToast(translations[currentLang].toastWelcome);
                }, 1000);
            }, 1400);
        }

        document.getElementById('waxSealContainer').addEventListener('click', openInvitation);

        // Real-Time Countdown Timer Calculator for July 7, 2027
        const weddingDate = new Date('July 7, 2027 00:00:00').getTime();

        function updateCountdown() {
            const now = new Date().getTime();
            const distance = weddingDate - now;

            if (distance < 0) {
                document.getElementById('days').textContent = '00';
                document.getElementById('hours').textContent = '00';
                document.getElementById('minutes').textContent = '00';
                document.getElementById('seconds').textContent = '00';
                return;
            }

            const days = Math.floor(distance / (1000 * 60 * 60 * 24));
            const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((distance % (1000 * 60)) / 1000);

            document.getElementById('days').textContent = String(days).padStart(2, '0');
            document.getElementById('hours').textContent = String(hours).padStart(2, '0');
            document.getElementById('minutes').textContent = String(minutes).padStart(2, '0');
            document.getElementById('seconds').textContent = String(seconds).padStart(2, '0');
        }

        setInterval(updateCountdown, 1000);
        updateCountdown();
    </script>
</body>
</html>
