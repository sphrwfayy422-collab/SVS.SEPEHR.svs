<!DOCTYPE html>
<html lang="fa" dir="rtl" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>SVS Empire | آینده سرگرمی</title>
    
    <link href="https://cdn.jsdelivr.net/gh/rastikerdar/vazirmatn@v33.0.3/dist/font-face.css" rel="stylesheet" type="text/css" />
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700;900&display=swap" rel="stylesheet">
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.tailwindcss.com"></script>
    
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: { 
                        sans: ['Vazirmatn', 'sans-serif'],
                        en: ['Inter', 'sans-serif']
                    },
                    colors: {
                        brand: {
                            50: '#f0f9ff',
                            100: '#e0f2fe',
                            400: '#38bdf8',
                            500: '#0ea5e9', // SVS Blue
                            600: '#0284c7',
                            900: '#0c4a6e',
                        },
                        dark: {
                            bg: '#0f172a',
                            surface: '#1e293b',
                            text: '#f1f5f9'
                        },
                        gold: '#fbbf24'
                    },
                    animation: {
                        'fade-in': 'fadeIn 0.5s ease-out',
                        'slide-up': 'slideUp 0.4s ease-out',
                    },
                    keyframes: {
                        fadeIn: { '0%': { opacity: '0' }, '100%': { opacity: '1' } },
                        slideUp: { '0%': { transform: 'translateY(20px)', opacity: '0' }, '100%': { transform: 'translateY(0)', opacity: '1' } }
                    }
                }
            }
        }
    </script>

    <style>
        .glass { background: rgba(255, 255, 255, 0.7); backdrop-filter: blur(12px); -webkit-backdrop-filter: blur(12px); border-bottom: 1px solid rgba(255, 255, 255, 0.3); }
        .dark .glass { background: rgba(15, 23, 42, 0.8); border-bottom: 1px solid rgba(255, 255, 255, 0.05); }
        .glass-card { background: rgba(255, 255, 255, 0.5); backdrop-filter: blur(8px); border: 1px solid rgba(255, 255, 255, 0.2); box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.07); }
        .dark .glass-card { background: rgba(30, 41, 59, 0.5); border: 1px solid rgba(255, 255, 255, 0.05); box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.2); }
        .no-scrollbar::-webkit-scrollbar { display: none; }
        .no-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }
        .skeleton { background: linear-gradient(90deg, #e2e8f0 25%, #f1f5f9 50%, #e2e8f0 75%); background-size: 200% 100%; animation: loading 1.5s infinite; }
        .dark .skeleton { background: linear-gradient(90deg, #1e293b 25%, #334155 50%, #1e293b 75%); }
        @keyframes loading { 0% { background-position: 200% 0; } 100% { background-position: -200% 0; } }
        .btn-hover-effect { transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1); }
        .btn-hover-effect:active { transform: scale(0.95); }
        .heart-active { color: #ef4444; animation: heartBeat 0.3s forwards; }
        @keyframes heartBeat { 0% { transform: scale(1); } 50% { transform: scale(1.3); } 100% { transform: scale(1); } }
        details > summary { list-style: none; cursor: pointer; }
        details > summary::-webkit-details-marker { display: none; }
        details[open] summary ~ * { animation: slideUp 0.3s ease-in-out; }
        details[open] .arrow-icon { transform: rotate(180deg); }
        .payment-radio:checked + div { border-color: #0ea5e9; background-color: rgba(14, 165, 233, 0.1); }
        .payment-radio:checked + div .check-icon { opacity: 1; transform: scale(1); }
    </style>
</head>
<body class="bg-gray-50 text-gray-800 dark:bg-dark-bg dark:text-dark-text transition-colors duration-300 pb-24 md:pb-0">

    <div id="app" class="flex flex-col min-h-screen">
        
        <header class="fixed top-0 left-0 right-0 z-50 glass transition-all duration-300">
            <div class="container mx-auto px-4 h-16 md:h-20 flex items-center justify-between">
                <div class="flex items-center gap-3 cursor-pointer group" onclick="app.router('home')">
                    <div class="w-10 h-10 md:w-12 md:h-12 bg-gradient-to-tr from-brand-600 to-brand-400 rounded-xl flex items-center justify-center text-white shadow-lg shadow-brand-500/30 group-hover:rotate-12 transition-transform duration-500">
                        <i class="fas fa-crown text-xl"></i>
                    </div>
                    <div>
                        <h1 class="text-xl md:text-2xl font-black tracking-tight">SVS <span class="text-brand-500">Empire</span></h1>
                        <p class="text-[10px] text-gray-400 dark:text-gray-500 hidden md:block tracking-widest uppercase">Premium Store</p>
                    </div>
                </div>

                <div class="hidden md:flex flex-1 max-w-lg mx-10 relative">
                    <input type="text" id="search-input" placeholder="جستجو در امپراتوری..." class="w-full bg-gray-100 dark:bg-dark-surface border-none rounded-2xl py-3 px-12 focus:ring-2 focus:ring-brand-500 transition-all shadow-inner text-sm">
                    <i class="fas fa-search absolute right-4 rtl:right-4 ltr:left-4 ltr:right-auto top-1/2 -translate-y-1/2 text-gray-400"></i>
                </div>

                <div class="flex items-center gap-2 md:gap-4">
                    <button onclick="app.toggleTheme()" class="w-10 h-10 rounded-full hover:bg-gray-100 dark:hover:bg-white/10 flex items-center justify-center transition">
                        <i class="fas fa-moon dark:hidden text-gray-600"></i>
                        <i class="fas fa-sun hidden dark:block text-yellow-400"></i>
                    </button>
                    
                    <button onclick="app.router('cart')" class="relative w-10 h-10 rounded-full hover:bg-gray-100 dark:hover:bg-white/10 flex items-center justify-center transition group">
                        <i class="fas fa-shopping-bag text-xl group-hover:text-brand-500 transition"></i>
                        <span id="badge-count" class="absolute top-1 right-1 w-4 h-4 bg-red-500 text-white text-[10px] font-bold rounded-full flex items-center justify-center scale-0 transition-transform duration-300">0</span>
                    </button>

                    <div id="desktop-auth-btn"></div>
                </div>
            </div>
        </header>

        <main id="main-content" class="pt-24 md:pt-28 flex-1 container mx-auto px-4">
            <div id="loader" class="grid grid-cols-2 md:grid-cols-4 gap-6 animate-pulse">
                <div class="h-64 rounded-2xl skeleton col-span-2 md:col-span-4"></div>
                <div class="h-48 rounded-2xl skeleton"></div>
                <div class="h-48 rounded-2xl skeleton"></div>
            </div>
        </main>

        <footer id="main-footer" class="hidden mt-12 border-t border-gray-200 dark:border-white/5 pt-10 pb-24 md:pb-10 bg-white/50 dark:bg-dark-surface/30 backdrop-blur-lg">
            <div class="container mx-auto px-4">
                <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
                    <div>
                        <h3 class="text-xl font-black text-brand-500 mb-4">SVS Empire</h3>
                        <p class="text-gray-500 dark:text-gray-400 text-sm leading-relaxed" id="footer-desc">ما در SVS Empire متعهدیم تا جدیدترین و کمیاب‌ترین گجت‌های هوشمند را به دست شما برسانیم.</p>
                    </div>
                    <div>
                        <h4 class="font-bold mb-4 dark:text-white" id="footer-quick">دسترسی سریع</h4>
                        <ul class="space-y-2 text-sm text-gray-500 dark:text-gray-400">
                            <li><a onclick="app.router('home')" class="hover:text-brand-500 cursor-pointer transition">صفحه اصلی</a></li>
                            <li><a onclick="app.router('products')" class="hover:text-brand-500 cursor-pointer transition">محصولات</a></li>
                            <li><a onclick="app.router('about')" class="hover:text-brand-500 cursor-pointer transition">درباره ما</a></li>
                            <li><a onclick="app.router('faq')" class="hover:text-brand-500 cursor-pointer transition">سوالات متداول</a></li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="font-bold mb-4 dark:text-white" id="footer-service">خدمات مشتریان</h4>
                        <ul class="space-y-2 text-sm text-gray-500 dark:text-gray-400">
                            <li><a class="hover:text-brand-500 cursor-pointer transition">پیگیری سفارش</a></li>
                            <li><a class="hover:text-brand-500 cursor-pointer transition">شرایط بازگشت</a></li>
                            <li><a class="hover:text-brand-500 cursor-pointer transition">حریم خصوصی</a></li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="font-bold mb-4 dark:text-white">همراه ما باشید</h4>
                        <div class="flex gap-4">
                            <a class="w-10 h-10 bg-gray-100 dark:bg-white/10 rounded-xl flex items-center justify-center text-gray-600 dark:text-white hover:bg-brand-500 hover:text-white transition"><i class="fab fa-instagram"></i></a>
                            <a class="w-10 h-10 bg-gray-100 dark:bg-white/10 rounded-xl flex items-center justify-center text-gray-600 dark:text-white hover:bg-brand-500 hover:text-white transition"><i class="fab fa-twitter"></i></a>
                            <a class="w-10 h-10 bg-gray-100 dark:bg-white/10 rounded-xl flex items-center justify-center text-gray-600 dark:text-white hover:bg-brand-500 hover:text-white transition"><i class="fab fa-linkedin-in"></i></a>
                        </div>
                    </div>
                </div>
                <div class="text-center text-xs text-gray-400 mt-10 border-t border-gray-200 dark:border-white/5 pt-6">
                    © 2025 SVS Empire. Designed by Sepehr (Robak Tech). All rights reserved.
                </div>
            </div>
        </footer>

        <nav class="md:hidden fixed bottom-0 left-0 right-0 glass z-40 pb-safe pt-2 border-t border-gray-200 dark:border-gray-800">
            <div class="flex justify-around items-center px-2">
                <button onclick="app.router('home')" class="nav-item active flex flex-col items-center p-2 text-brand-500 transition">
                    <i class="fas fa-home text-xl mb-1"></i>
                    <span class="text-[10px] font-bold" id="nav-home">خانه</span>
                </button>
                <button onclick="app.router('products')" class="nav-item flex flex-col items-center p-2 text-gray-400 hover:text-brand-500 transition">
                    <i class="fas fa-layer-group text-xl mb-1"></i>
                    <span class="text-[10px] font-medium" id="nav-products">محصولات</span>
                </button>
                <div class="relative -top-6">
                    <button onclick="app.router('cart')" class="w-14 h-14 bg-brand-600 text-white rounded-full flex items-center justify-center shadow-xl shadow-brand-500/40 btn-hover-effect">
                        <i class="fas fa-shopping-cart"></i>
                    </button>
                </div>
                <button onclick="app.router('wishlist')" class="nav-item flex flex-col items-center p-2 text-gray-400 hover:text-brand-500 transition">
                    <i class="fas fa-heart text-xl mb-1"></i>
                    <span class="text-[10px] font-medium" id="nav-wishlist">علاقه‌ها</span>
                </button>
                <button onclick="app.router('profile')" class="nav-item flex flex-col items-center p-2 text-gray-400 hover:text-brand-500 transition">
                    <i class="fas fa-user text-xl mb-1"></i>
                    <span class="text-[10px] font-medium" id="nav-me">من</span>
                </button>
            </div>
        </nav>

        <div id="auth-modal" class="fixed inset-0 z-[60] hidden flex items-center justify-center px-4">
            <div class="absolute inset-0 bg-black/80 backdrop-blur transition-opacity"></div>
            <div class="relative bg-white dark:bg-dark-surface w-full max-w-sm rounded-3xl p-8 shadow-2xl animate-fade-in border border-white/10">
                <div class="flex bg-gray-100 dark:bg-black/30 rounded-xl p-1 mb-6">
                    <button onclick="app.setAuthTab('login')" id="tab-login" class="flex-1 py-2 rounded-lg text-sm font-bold transition-all bg-white dark:bg-white/10 shadow text-brand-600">ورود</button>
                    <button onclick="app.setAuthTab('signup')" id="tab-signup" class="flex-1 py-2 rounded-lg text-sm font-bold transition-all text-gray-500 dark:text-gray-400">ثبت‌نام</button>
                </div>
                <div class="text-center mb-6">
                    <h2 class="text-2xl font-bold dark:text-white" id="auth-title">خوش آمدید</h2>
                    <p class="text-sm text-gray-400 mt-2">برای ورود به امپراتوری SVS آماده‌اید؟</p>
                </div>
                <form onsubmit="app.handleAuthSubmit(event)" class="space-y-4">
                    <div id="field-name" class="hidden bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2 border border-transparent focus-within:border-brand-500 focus-within:bg-white dark:focus-within:bg-black/40 transition">
                        <label class="block text-xs text-gray-400 mb-1">نام کامل</label>
                        <input type="text" id="input-name" class="w-full bg-transparent border-none p-0 text-sm focus:ring-0 dark:text-white" placeholder="مثلا: سپهر">
                    </div>
                    <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2 border border-transparent focus-within:border-brand-500 focus-within:bg-white dark:focus-within:bg-black/40 transition">
                        <label class="block text-xs text-gray-400 mb-1">ایمیل</label>
                        <input type="email" id="input-email" required class="w-full bg-transparent border-none p-0 text-sm focus:ring-0 dark:text-white font-mono" placeholder="user@example.com">
                    </div>
                    <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2 border border-transparent focus-within:border-brand-500 focus-within:bg-white dark:focus-within:bg-black/40 transition">
                        <label class="block text-xs text-gray-400 mb-1">رمز عبور</label>
                        <input type="password" id="input-pass" required class="w-full bg-transparent border-none p-0 text-sm focus:ring-0 dark:text-white" placeholder="••••••">
                    </div>
                    <button type="submit" id="btn-submit-auth" class="w-full bg-brand-600 hover:bg-brand-500 text-white py-4 rounded-xl font-bold shadow-lg shadow-brand-500/30 transition-all btn-hover-effect mt-4">ورود به حساب</button>
                </form>
            </div>
        </div>

        <div id="product-modal" class="fixed inset-0 z-[60] hidden flex items-center justify-center px-4">
            <div class="absolute inset-0 bg-black/80 backdrop-blur transition-opacity" onclick="app.closeProductModal()"></div>
            <div class="relative bg-white dark:bg-dark-surface w-full max-w-lg rounded-3xl p-6 md:p-8 shadow-2xl animate-fade-in border border-white/10 max-h-[90vh] overflow-y-auto no-scrollbar">
                <div class="flex justify-between items-center mb-6">
                    <h2 class="text-2xl font-black dark:text-white" id="modal-product-title">محصول</h2>
                    <button onclick="app.closeProductModal()" class="w-8 h-8 bg-gray-100 dark:bg-white/10 rounded-full flex items-center justify-center hover:bg-red-50 hover:text-red-500 transition"><i class="fas fa-times"></i></button>
                </div>
                <form onsubmit="app.handleProductSubmit(event)" class="space-y-4">
                    <input type="hidden" id="prod-id">
                    <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2">
                        <label class="block text-xs text-gray-400 mb-1">نام محصول</label>
                        <input type="text" id="prod-name" required class="w-full bg-transparent border-none p-0 text-sm dark:text-white focus:ring-0">
                    </div>
                    <div class="grid grid-cols-2 gap-4">
                        <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2">
                            <label class="block text-xs text-gray-400 mb-1">قیمت (تومان)</label>
                            <input type="number" id="prod-price" required class="w-full bg-transparent border-none p-0 text-sm dark:text-white focus:ring-0">
                        </div>
                        <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2">
                            <label class="block text-xs text-gray-400 mb-1">دسته‌بندی</label>
                            <select id="prod-cat" class="w-full bg-transparent border-none p-0 text-sm dark:text-white focus:ring-0">
                                <option value="drone">Drone</option>
                                <option value="lego">Lego</option>
                                <option value="rc">RC</option>
                                <option value="console">Console</option>
                                <option value="vr">VR</option>
                                <option value="robot">Robot</option>
                            </select>
                        </div>
                    </div>
                    <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2">
                        <label class="block text-xs text-gray-400 mb-1">تصویر یا ویدیو (لینک یا گالری)</label>
                        <input type="file" id="prod-file" accept="image/*,video/*" onchange="app.handleFileSelect(event)" class="w-full text-xs mb-2 dark:text-gray-300">
                        <input type="text" id="prod-img" required class="w-full bg-transparent border-none p-0 text-sm dark:text-white focus:ring-0 text-left" dir="ltr" placeholder="لینک خودکار پر میشود...">
                    </div>
                    <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2">
                        <label class="block text-xs text-gray-400 mb-1">توضیحات</label>
                        <textarea id="prod-desc" required rows="3" class="w-full bg-transparent border-none p-0 text-sm dark:text-white focus:ring-0 resize-none"></textarea>
                    </div>
                    <button type="submit" class="w-full bg-brand-600 hover:bg-brand-500 text-white py-4 rounded-xl font-bold shadow-lg shadow-brand-500/30 transition-all btn-hover-effect mt-4">ذخیره محصول</button>
                </form>
            </div>
        </div>

        <div id="checkout-modal" class="fixed inset-0 z-[60] hidden flex items-center justify-center px-4">
            <div class="absolute inset-0 bg-black/80 backdrop-blur transition-opacity" onclick="app.closeCheckoutModal()"></div>
            <div class="relative bg-white dark:bg-dark-surface w-full max-w-lg rounded-3xl p-6 md:p-8 shadow-2xl animate-fade-in border border-white/10 max-h-[90vh] overflow-y-auto no-scrollbar">
                
                <div class="flex justify-between items-center mb-6">
                    <h2 class="text-2xl font-black dark:text-white">نهایی‌سازی سفارش</h2>
                    <button onclick="app.closeCheckoutModal()" class="w-8 h-8 bg-gray-100 dark:bg-white/10 rounded-full flex items-center justify-center hover:bg-red-50 hover:text-red-500 transition"><i class="fas fa-times"></i></button>
                </div>

                <form onsubmit="app.handleCheckoutSubmit(event)" class="space-y-4">
                    <div class="grid grid-cols-2 gap-4">
                        <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2">
                            <label class="block text-xs text-gray-400 mb-1">نام و نام خانوادگی</label>
                            <input type="text" id="chk-name" required class="w-full bg-transparent border-none p-0 text-sm dark:text-white focus:ring-0">
                        </div>
                        <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2">
                            <label class="block text-xs text-gray-400 mb-1">نام کاربری</label>
                            <input type="text" id="chk-username" required class="w-full bg-transparent border-none p-0 text-sm dark:text-white focus:ring-0">
                        </div>
                    </div>
                    <div class="grid grid-cols-2 gap-4">
                        <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2">
                            <label class="block text-xs text-gray-400 mb-1">ایمیل</label>
                            <input type="email" id="chk-email" required class="w-full bg-transparent border-none p-0 text-sm dark:text-white focus:ring-0 text-right ltr:text-left" dir="ltr">
                        </div>
                        <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2">
                            <label class="block text-xs text-gray-400 mb-1">شماره موبایل</label>
                            <input type="tel" id="chk-phone" required class="w-full bg-transparent border-none p-0 text-sm dark:text-white focus:ring-0 text-right ltr:text-left" dir="ltr">
                        </div>
                    </div>
                    
                    <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2">
                        <label class="block text-xs text-gray-400 mb-1">آدرس دقیق پستی</label>
                        <textarea id="chk-address" required rows="2" class="w-full bg-transparent border-none p-0 text-sm dark:text-white focus:ring-0 resize-none"></textarea>
                    </div>
                    
                    <div class="bg-gray-50 dark:bg-black/20 rounded-xl px-4 py-2 mb-6">
                        <label class="block text-xs text-gray-400 mb-1">کد پستی</label>
                        <input type="number" id="chk-zip" required class="w-full bg-transparent border-none p-0 text-sm dark:text-white focus:ring-0 text-right ltr:text-left" dir="ltr">
                    </div>

                    <div class="border-t border-gray-100 dark:border-white/10 pt-4">
                        <h3 class="font-bold text-sm mb-3 dark:text-white">روش پرداخت را انتخاب کنید</h3>
                        <div class="grid grid-cols-2 gap-4">
                            <label class="cursor-pointer relative">
                                <input type="radio" name="payment" value="credit" class="payment-radio hidden">
                                <div class="border border-gray-200 dark:border-white/10 rounded-xl p-4 flex flex-col items-center justify-center gap-2 hover:bg-gray-50 dark:hover:bg-white/5 transition h-full text-center">
                                    <i class="fas fa-credit-card text-2xl text-brand-500"></i>
                                    <span class="text-xs font-bold dark:text-white">کارت اعتباری</span>
                                    <i class="fas fa-check-circle absolute top-2 right-2 text-brand-500 opacity-0 transform scale-0 transition-all duration-300 check-icon"></i>
                                </div>
                            </label>
                            <label class="cursor-pointer relative">
                                <input type="radio" name="payment" value="online" class="payment-radio hidden" checked>
                                <div class="border border-gray-200 dark:border-white/10 rounded-xl p-4 flex flex-col items-center justify-center gap-2 hover:bg-gray-50 dark:hover:bg-white/5 transition h-full text-center">
                                    <i class="fas fa-globe text-2xl text-green-500"></i>
                                    <span class="text-xs font-bold dark:text-white">پرداخت آنلاین</span>
                                    <i class="fas fa-check-circle absolute top-2 right-2 text-brand-500 opacity-0 transform scale-0 transition-all duration-300 check-icon"></i>
                                </div>
                            </label>
                        </div>
                    </div>

                    <button type="submit" class="w-full bg-green-500 hover:bg-green-600 text-white py-4 rounded-xl font-bold shadow-lg shadow-green-500/30 transition-all btn-hover-effect mt-4">
                        پرداخت و تکمیل خرید
                        <i class="fas fa-check mr-2 rtl:mr-2 ltr:ml-2"></i>
                    </button>
                </form>
            </div>
        </div>

        <div id="quick-view-modal" class="fixed inset-0 z-[60] hidden">
            <div class="absolute inset-0 bg-black/60 backdrop-blur-sm transition-opacity" onclick="app.closeModal()"></div>
            <div class="absolute inset-x-0 bottom-0 md:top-1/2 md:left-1/2 md:bottom-auto md:-translate-x-1/2 md:-translate-y-1/2 md:w-[800px] bg-white dark:bg-dark-surface md:rounded-3xl rounded-t-3xl shadow-2xl overflow-hidden animate-slide-up md:animate-fade-in">
                <div id="quick-view-content" class="p-0"></div>
                <button onclick="app.closeModal()" class="absolute top-4 left-4 ltr:right-4 ltr:left-auto w-8 h-8 bg-gray-100 dark:bg-white/10 rounded-full flex items-center justify-center hover:bg-red-50 hover:text-red-500 transition"><i class="fas fa-times"></i></button>
            </div>
        </div>

        <div id="toast-box" class="fixed top-24 left-1/2 -translate-x-1/2 z-[70] flex flex-col gap-2 pointer-events-none w-full max-w-xs px-4"></div>

    </div>

    <script>
        window.app = {
            state: {
                lang: 'fa',
                products: [], 
                cart: [],
                wishlist: [],
                orders: [],
                user: null,
                authMode: 'login',
                currentPage: 'home',
                faq: [
                    { q: "چگونه می‌توانم به SVS Empire اعتماد کنم؟", a: "SVS Empire دارای نماد اعتماد الکترونیکی 5 ستاره و مجوز رسمی از اتحادیه کسب‌وکارهای مجازی است." },
                    { q: "آیا محصولات گارانتی دارند؟", a: "بله، تمام محصولات دارای گارانتی طلایی ۱۸ ماهه SVS هستند." },
                    { q: "ارسال سفارش چقدر طول می‌کشد؟", a: "برای تهران ارسال زیر ۲ ساعت و برای شهرستان‌ها ۲۴ تا ۴۸ ساعت کاری." },
                    { q: "آیا امکان پرداخت در محل وجود دارد؟", a: "بله، برای سفارش‌های زیر ۵۰ میلیون تومان." }
                ],
                translations: {
                    fa: {
                        home: "خانه", products: "محصولات", about: "درباره ما", faq: "سوالات متداول",
                        cart: "سبد خرید", wishlist: "علاقه‌ها", profile: "من", settings: "تنظیمات",
                        my_orders: "سفارش‌های من", logout: "خروج", login: "ورود / ثبت‌نام",
                        search: "جستجو در امپراتوری...", welcome: "خوش آمدید", 
                        empty_cart: "سبد خالی است", total: "مجموع", checkout: "پرداخت ایمن",
                        language: "زبان / Language", select_lang: "انتخاب زبان نمایش",
                        status_pending: "در انتظار بررسی", status_processing: "در حال پردازش", status_sent: "ارسال شده",
                        order_id: "کد سفارش", date: "تاریخ", items: "اقلام", price: "مبلغ",
                        curr: "تومان", admin_panel: "پنل مدیریت امپراتوری", delete_confirm: "آیا از حذف این محصول اطمینان دارید؟", deleted: "محصول با موفقیت حذف شد", saved: "محصول با موفقیت ذخیره شد"
                    },
                    en: {
                        home: "Home", products: "Products", about: "About Us", faq: "FAQ",
                        cart: "Cart", wishlist: "Wishlist", profile: "Me", settings: "Settings",
                        my_orders: "My Orders", logout: "Logout", login: "Login / Sign Up",
                        search: "Search Empire...", welcome: "Welcome", 
                        empty_cart: "Cart is Empty", total: "Total", checkout: "Checkout",
                        language: "Language", select_lang: "Select Display Language",
                        status_pending: "Pending", status_processing: "Processing", status_sent: "Shipped",
                        order_id: "Order ID", date: "Date", items: "Items", price: "Amount",
                        curr: "Toman", admin_panel: "Empire Admin Panel", delete_confirm: "Are you sure you want to delete this product?", deleted: "Product deleted successfully", saved: "Product saved successfully"
                    }
                }
            },

            init() {
                // چک کردن کاربر لاگین شده
                const savedUser = localStorage.getItem('user');
                if(savedUser) {
                    this.state.user = JSON.parse(savedUser);
                    this.updateAuthButton();
                }

                // لیست محصولات پیش‌فرض (برای وقتی که سرور خاموشه)
                const fallbackProducts = [
                    { id: 1, name: "SVS Drone X1 (Offline)", price: 135000000, cat: "drone", img: "https://images.unsplash.com/photo-1579829366248-204fe8413f31?w=800", rating: 5, badge: "جدید", desc: "پهپاد اختصاصی امپراتوری SVS..." },
                    { id: 2, name: "Lego Bugatti (Offline)", price: 19000000, cat: "lego", img: "https://images.unsplash.com/photo-1587654780291-39c940483719?w=800", rating: 4.8, badge: "پرفروش", desc: "۳۵۹۹ قطعه مهندسی دقیق..." }
                ];

                // *********** اتصال به سرور پایتون ***********
                fetch('/api/products/')
                .then(response => {
                    if (!response.ok) throw new Error("مشکل در اتصال به سرور");
                    return response.json();
                })
                .then(data => {
                    if(data.length > 0) {
                        this.state.products = data;
                    } else {
                        this.state.products = fallbackProducts;
                    }
                    this.finishLoading();
                })
                .catch(error => {
                    console.error("❌ سرور خاموش است یا خطا دارد. استفاده از حالت آفلاین.", error);
                    this.state.products = fallbackProducts;
                    this.finishLoading();
                });

                // تنظیمات تم و زبان
                if(localStorage.getItem('theme') === 'dark') document.documentElement.classList.add('dark');
                const savedLang = localStorage.getItem('lang');
                if (savedLang) this.setLanguage(savedLang, false);

                // لود کردن بقیه چیزها از حافظه
                const savedCart = localStorage.getItem('cart');
                if(savedCart) this.state.cart = JSON.parse(savedCart);
                
                const savedWish = localStorage.getItem('wishlist');
                if(savedWish) this.state.wishlist = JSON.parse(savedWish);
                
                const savedOrders = localStorage.getItem('orders');
                if(savedOrders) this.state.orders = JSON.parse(savedOrders);

                this.updateUIText();
            },

            finishLoading() {
                setTimeout(() => {
                    document.getElementById('loader').classList.add('hidden');
                    document.getElementById('main-footer').classList.remove('hidden');
                    
                    if (this.state.user) {
                        if (this.state.user.role === 'admin') this.router('admin');
                        else this.router('home');
                    } else {
                        this.router('home'); 
                        document.getElementById('auth-modal').classList.remove('hidden');
                    }
                }, 1000);
            },

            t(key) { return this.state.translations[this.state.lang][key] || key; },

            setLanguage(lang, reload = true) {
                this.state.lang = lang;
                localStorage.setItem('lang', lang);
                document.documentElement.dir = lang === 'fa' ? 'rtl' : 'ltr';
                document.documentElement.lang = lang;
                if (lang === 'en') {
                    document.body.classList.add('font-en');
                    document.body.classList.remove('font-sans');
                } else {
                    document.body.classList.add('font-sans');
                    document.body.classList.remove('font-en');
                }
                this.updateUIText();
                if(reload) this.router(this.state.currentPage);
            },

            updateUIText() {
                document.getElementById('nav-home').innerText = this.t('home');
                document.getElementById('nav-products').innerText = this.t('products');
                document.getElementById('nav-wishlist').innerText = this.t('wishlist');
                document.getElementById('nav-me').innerText = this.t('profile');
                document.getElementById('search-input').placeholder = this.t('search');
            },

            router(page) {
                window.scrollTo(0,0);
                this.state.currentPage = page;
                const content = document.getElementById('main-content');
                content.innerHTML = '';
                
                document.querySelectorAll('.nav-item').forEach(el => el.classList.remove('text-brand-500'));
                
                if (page === 'home') {
                    this.renderHome(content);
                    document.querySelector('.nav-item:nth-child(1)')?.classList.add('text-brand-500');
                } else if (page === 'products') {
                    this.renderProducts(content);
                    document.querySelector('.nav-item:nth-child(2)')?.classList.add('text-brand-500');
                } else if (page === 'cart') {
                    this.renderCart(content);
                } else if (page === 'wishlist') {
                    this.renderWishlist(content);
                    document.querySelector('.nav-item:nth-child(4)')?.classList.add('text-brand-500');
                } else if (page === 'profile') {
                    this.renderProfile(content);
                    document.querySelector('.nav-item:nth-child(5)')?.classList.add('text-brand-500');
                } else if (page === 'about') {
                    this.renderAbout(content);
                } else if (page === 'faq') {
                    this.renderFAQ(content);
                } else if (page === 'admin') {
                    this.renderAdmin(content);
                } else if (page === 'settings') {
                    this.renderSettings(content);
                } else if (page === 'orders') {
                    this.renderOrders(content);
                }
            },

            renderHome(c) {
                const isFa = this.state.lang === 'fa';
                c.innerHTML = `
                    <div class="relative w-full h-[500px] rounded-[2.5rem] overflow-hidden shadow-2xl mb-12 animate-fade-in group"><img src="https://images.unsplash.com/photo-1550745165-9bc0b252726f?w=1200" class="w-full h-full object-cover transition-transform duration-[2s] group-hover:scale-105"><div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/30 to-transparent flex flex-col justify-end p-8 md:p-16"><span class="bg-brand-500 text-white text-xs font-bold px-3 py-1 rounded-full w-fit mb-4 backdrop-blur-md bg-opacity-80">${isFa ? 'جشنواره SVS' : 'SVS Festival'}</span><h2 class="text-4xl md:text-6xl font-black text-white mb-4 leading-tight">${isFa ? 'آینده را <br>همین امروز لمس کنید' : 'Touch the Future<br>Today'}</h2><button onclick="app.router('products')" class="bg-white text-black px-8 py-3 rounded-xl font-bold hover:bg-gray-200 transition btn-hover-effect w-fit">${isFa ? 'مشاهده کلکسیون' : 'View Collection'}</button></div></div>
                    <div class="flex justify-between items-end mb-8"><div><h3 class="text-2xl font-bold dark:text-white">${isFa ? 'برترین‌های هفته' : 'Weekly Top Picks'}</h3><div class="h-1 w-20 bg-brand-500 mt-2 rounded-full"></div></div><a onclick="app.router('products')" class="text-brand-500 text-sm font-bold cursor-pointer">${isFa ? 'مشاهده همه' : 'View All'} <i class="fas fa-arrow-left rtl:rotate-0 ltr:rotate-180"></i></a></div>
                    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">${this.state.products.slice(0,4).map(p => this.createCard(p)).join('')}</div>`;
            },
            renderProducts(c) {
                const cats = this.state.lang === 'fa' ? ['همه', 'پهپاد', 'کنسول', 'رباتیک', 'لگو'] : ['All', 'Drone', 'Console', 'Robotic', 'Lego'];
                c.innerHTML = `<div class="flex gap-4 overflow-x-auto pb-4 mb-8 no-scrollbar md:justify-center">${cats.map(cat => `<button class="glass-card px-6 py-3 rounded-2xl whitespace-nowrap text-sm font-bold hover:bg-brand-500 hover:text-white transition dark:text-gray-300 dark:hover:text-white border-none">${cat}</button>`).join('')}</div><div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 animate-slide-up">${this.state.products.map(p => this.createCard(p)).join('')}</div>`;
            },
            renderWishlist(c) {
                const favs = this.state.products.filter(p => this.state.wishlist.includes(p.id));
                const emptyText = this.state.lang === 'fa' ? 'لیست علاقه‌ها خالی است' : 'Wishlist is empty';
                const btnText = this.state.lang === 'fa' ? 'مشاهده محصولات' : 'View Products';
                c.innerHTML = favs.length===0 ? `<div class="flex flex-col items-center justify-center min-h-[50vh] text-center animate-fade-in"><div class="w-32 h-32 bg-red-50 dark:bg-white/5 rounded-full flex items-center justify-center mb-6 text-red-200"><i class="fas fa-heart text-5xl"></i></div><h2 class="text-xl font-bold dark:text-white">${emptyText}</h2><button onclick="app.router('products')" class="mt-6 bg-brand-600 text-white px-8 py-3 rounded-xl font-bold shadow-lg btn-hover-effect">${btnText}</button></div>` : `<h2 class="text-2xl font-bold mb-6 dark:text-white">${this.t('wishlist')}</h2><div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 animate-slide-up">${favs.map(p => this.createCard(p)).join('')}</div>`;
            },
            renderProfile(c) {
                if (!this.state.user) {
                    this.toggleAuthModal();
                    return;
                }
                const isAdmin = this.state.user.role === 'admin';
                const processingCount = this.state.orders.filter(o => o.status === 'processing').length;
                
                c.innerHTML = `
                    <div class="max-w-4xl mx-auto animate-slide-up">
                        <div class="glass-card p-6 md:p-10 rounded-[2.5rem] flex flex-col md:flex-row items-center gap-6 md:gap-10 mb-8">
                            <div class="w-24 h-24 md:w-32 md:h-32 bg-gradient-to-tr from-brand-400 to-blue-600 rounded-full flex items-center justify-center text-4xl text-white shadow-xl ring-4 ring-white dark:ring-white/10">${this.state.user.name.charAt(0)}</div>
                            <div class="text-center md:text-right ltr:md:text-left flex-1"><h2 class="text-2xl md:text-3xl font-black dark:text-white mb-2">${this.state.user.name}</h2><p class="text-gray-500 dark:text-gray-400 font-mono text-sm">${this.state.user.email}</p></div>
                            <button onclick="app.logout()" class="bg-red-50 hover:bg-red-100 text-red-500 w-12 h-12 rounded-2xl flex items-center justify-center transition" title="${this.t('logout')}"><i class="fas fa-sign-out-alt"></i></button>
                        </div>
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-8"><div class="glass-card p-5 rounded-3xl text-center"><div class="text-brand-500 text-2xl font-black mb-1">${processingCount}</div><div class="text-xs text-gray-400">${this.state.lang === 'fa' ? 'جاری' : 'Active'}</div></div><div class="glass-card p-5 rounded-3xl text-center"><div class="text-green-500 text-2xl font-black mb-1">${this.state.orders.length}</div><div class="text-xs text-gray-400">${this.state.lang === 'fa' ? 'کل سفارش' : 'Total Orders'}</div></div><div class="glass-card p-5 rounded-3xl text-center"><div class="text-red-500 text-2xl font-black mb-1">${this.state.wishlist.length}</div><div class="text-xs text-gray-400">${this.t('wishlist')}</div></div><div class="glass-card p-5 rounded-3xl text-center"><div class="text-purple-500 text-2xl font-black mb-1">۰</div><div class="text-xs text-gray-400">${this.state.lang === 'fa' ? 'پیام' : 'Messages'}</div></div></div>
                        <div class="glass-card rounded-[2rem] overflow-hidden">
                            ${isAdmin ? `<div onclick="app.router('admin')" class="p-6 border-b border-gray-100 dark:border-white/5 hover:bg-yellow-50 dark:hover:bg-yellow-900/10 cursor-pointer flex justify-between items-center transition"><div class="flex items-center gap-4"><div class="w-10 h-10 bg-yellow-100 text-yellow-600 rounded-xl flex items-center justify-center"><i class="fas fa-crown"></i></div><span class="font-bold dark:text-yellow-400 text-yellow-700">${this.t('admin_panel')}</span></div><i class="fas fa-chevron-left rtl:rotate-0 ltr:rotate-180 text-yellow-500"></i></div>` : ''}
                            
                            <div onclick="app.router('orders')" class="p-6 border-b border-gray-100 dark:border-white/5 hover:bg-gray-50 dark:hover:bg-white/5 cursor-pointer flex justify-between items-center transition"><div class="flex items-center gap-4"><div class="w-10 h-10 bg-blue-50 text-blue-500 rounded-xl flex items-center justify-center"><i class="fas fa-box"></i></div><span class="font-bold dark:text-gray-200">${this.t('my_orders')}</span></div><i class="fas fa-chevron-left rtl:rotate-0 ltr:rotate-180 text-gray-300"></i></div>
                            
                            <div onclick="app.router('about')" class="p-6 border-b border-gray-100 dark:border-white/5 hover:bg-gray-50 dark:hover:bg-white/5 cursor-pointer flex justify-between items-center transition"><div class="flex items-center gap-4"><div class="w-10 h-10 bg-orange-50 text-orange-500 rounded-xl flex items-center justify-center"><i class="fas fa-info-circle"></i></div><span class="font-bold dark:text-gray-200">${this.t('about')}</span></div><i class="fas fa-chevron-left rtl:rotate-0 ltr:rotate-180 text-gray-300"></i></div>
                            
                            <div onclick="app.router('settings')" class="p-6 hover:bg-gray-50 dark:hover:bg-white/5 cursor-pointer flex justify-between items-center transition"><div class="flex items-center gap-4"><div class="w-10 h-10 bg-gray-100 text-gray-500 rounded-xl flex items-center justify-center"><i class="fas fa-cog"></i></div><span class="font-bold dark:text-gray-200">${this.t('settings')}</span></div><i class="fas fa-chevron-left rtl:rotate-0 ltr:rotate-180 text-gray-300"></i></div>
                        </div>
                    </div>`;
            },
            
            renderSettings(c) {
                const isFa = this.state.lang === 'fa';
                c.innerHTML = `
                    <div class="max-w-xl mx-auto animate-slide-up">
                        <div class="flex justify-between items-center mb-6">
                            <h2 class="text-2xl font-black dark:text-white">${this.t('settings')}</h2>
                            <button onclick="app.router('profile')" class="text-sm bg-gray-100 dark:bg-white/10 px-4 py-2 rounded-lg hover:bg-gray-200"><i class="fas fa-arrow-right rtl:ml-2 ltr:mr-2"></i> ${isFa ? 'بازگشت' : 'Back'}</button>
                        </div>
                        
                        <div class="glass-card rounded-2xl p-6 mb-6">
                            <h3 class="font-bold mb-4 dark:text-white flex items-center gap-2"><i class="fas fa-language text-brand-500"></i> ${this.t('language')}</h3>
                            <p class="text-xs text-gray-400 mb-4">${this.t('select_lang')}</p>
                            
                            <div class="flex gap-4">
                                <label class="flex-1 cursor-pointer">
                                    <input type="radio" name="lang_sel" class="hidden peer" ${isFa ? 'checked' : ''} onchange="app.setLanguage('fa')">
                                    <div class="border border-gray-200 dark:border-white/10 rounded-xl p-4 flex flex-col items-center gap-2 peer-checked:border-brand-50 peer-checked:bg-brand-50 dark:peer-checked:bg-brand-900/20 transition">
                                        <span class="text-2xl">🇮🇷</span>
                                        <span class="font-bold text-sm dark:text-white">فارسی</span>
                                    </div>
                                </label>
                                <label class="flex-1 cursor-pointer">
                                    <input type="radio" name="lang_sel" class="hidden peer" ${!isFa ? 'checked' : ''} onchange="app.setLanguage('en')">
                                    <div class="border border-gray-200 dark:border-white/10 rounded-xl p-4 flex flex-col items-center gap-2 peer-checked:border-brand-500 peer-checked:bg-brand-50 dark:peer-checked:bg-brand-900/20 transition">
                                        <span class="text-2xl">🇺🇸</span>
                                        <span class="font-bold text-sm dark:text-white">English</span>
                                    </div>
                                </label>
                            </div>
                        </div>
                    </div>
                `;
            },

            renderOrders(c) {
                const isFa = this.state.lang === 'fa';
                
                if (this.state.orders.length === 0) {
                    c.innerHTML = `
                        <div class="max-w-4xl mx-auto animate-slide-up">
                            <div class="flex justify-between items-center mb-6">
                                <h2 class="text-2xl font-black dark:text-white">${this.t('my_orders')}</h2>
                                <button onclick="app.router('profile')" class="text-sm bg-gray-100 dark:bg-white/10 px-4 py-2 rounded-lg hover:bg-gray-200">${isFa ? 'بازگشت' : 'Back'}</button>
                            </div>
                            <div class="flex flex-col items-center justify-center min-h-[40vh] text-center">
                                <div class="w-24 h-24 bg-gray-100 dark:bg-white/5 rounded-full flex items-center justify-center mb-4"><i class="fas fa-box-open text-3xl text-gray-300"></i></div>
                                <h3 class="text-lg font-bold dark:text-white">${isFa ? 'هنوز سفارشی ثبت نکرده‌اید' : 'No orders yet'}</h3>
                            </div>
                        </div>`;
                    return;
                }

                c.innerHTML = `
                    <div class="max-w-4xl mx-auto animate-slide-up">
                        <div class="flex justify-between items-center mb-6">
                            <h2 class="text-2xl font-black dark:text-white">${this.t('my_orders')}</h2>
                            <button onclick="app.router('profile')" class="text-sm bg-gray-100 dark:bg-white/10 px-4 py-2 rounded-lg hover:bg-gray-200">${isFa ? 'بازگشت' : 'Back'}</button>
                        </div>
                        <div class="space-y-6">
                            ${this.state.orders.slice().reverse().map(order => {
                                let statusText = this.t('status_pending');
                                let statusColor = "bg-yellow-100 text-yellow-700";
                                if (order.status === 'processing') { statusText = this.t('status_processing'); statusColor = "bg-blue-100 text-blue-700"; }
                                else if (order.status === 'sent') { statusText = this.t('status_sent'); statusColor = "bg-green-100 text-green-700"; }
                                return `
                                <div class="glass-card rounded-2xl p-6 overflow-hidden">
                                    <div class="flex flex-wrap justify-between items-center border-b border-gray-100 dark:border-white/5 pb-4 mb-4 gap-4">
                                        <div class="flex gap-4">
                                            <div>
                                                <div class="text-xs text-gray-400 mb-1">${this.t('order_id')}</div>
                                                <div class="font-mono font-bold text-lg dark:text-white">#${order.id}</div>
                                            </div>
                                            <div class="w-px bg-gray-200 dark:bg-white/10"></div>
                                            <div>
                                                <div class="text-xs text-gray-400 mb-1">${this.t('date')}</div>
                                                <div class="font-bold text-sm dark:text-white">${order.date}</div>
                                            </div>
                                        </div>
                                        <span class="${statusColor} px-3 py-1 rounded-lg text-xs font-bold">${statusText}</span>
                                    </div>
                                    <div class="flex gap-3 overflow-x-auto pb-2 no-scrollbar mb-4">
                                        ${order.items.map(item => `
                                            <div class="relative w-16 h-16 flex-shrink-0 bg-gray-50 dark:bg-black/20 rounded-lg overflow-hidden border border-gray-100 dark:border-white/5">
                                                <img src="${item.img}" class="w-full h-full object-cover">
                                                <span class="absolute bottom-0 right-0 bg-black/60 text-white text-[10px] px-1.5 rounded-tl-lg">${item.qty}</span>
                                            </div>
                                        `).join('')}
                                    </div>
                                    <div class="flex justify-between items-center pt-2">
                                        <span class="text-gray-400 text-sm">${order.items.length} ${this.t('items')}</span>
                                        <div class="text-brand-500 font-black text-xl">${order.total.toLocaleString()} <span class="text-xs text-gray-400">${this.t('curr')}</span></div>
                                    </div>
                                </div>
                                `;
                            }).join('')}
                        </div>
                    </div>
                `;
            },

            renderAdmin(c) {
                const isFa = this.state.lang === 'fa';
                c.innerHTML = `
                    <div class="max-w-4xl mx-auto animate-slide-up">
                        <div class="flex justify-between items-center mb-6">
                            <h2 class="text-2xl font-black dark:text-white">${this.t('admin_panel')}</h2>
                            <button onclick="app.router('profile')" class="text-sm bg-gray-100 dark:bg-white/10 px-4 py-2 rounded-lg hover:bg-gray-200">${isFa ? 'بازگشت' : 'Back'}</button>
                        </div>
                        <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-8">
                            <div class="glass-card p-5 rounded-2xl"><div class="text-3xl font-bold text-brand-500">${this.state.products.length}</div><div class="text-xs text-gray-400">${this.t('products')}</div></div>
                            <div class="glass-card p-5 rounded-2xl"><div class="text-3xl font-bold text-green-500">5.2M</div><div class="text-xs text-gray-400">View</div></div>
                        </div>
                        <div class="glass-card rounded-2xl overflow-hidden p-6">
                            <h3 class="font-bold mb-4 dark:text-white">${isFa ? 'مدیریت محصولات' : 'Product Management'}</h3>
                            <div class="space-y-4">
                                ${this.state.products.map(p => `
                                    <div class="flex items-center justify-between border-b border-gray-100 dark:border-white/5 pb-2">
                                        <div class="flex items-center gap-3">
                                            <img src="${p.img}" class="w-10 h-10 rounded-lg object-cover">
                                            <div>
                                                <div class="text-sm font-bold dark:text-gray-200">${p.name}</div>
                                                <div class="text-xs text-gray-400">${p.price.toLocaleString()}</div>
                                            </div>
                                        </div>
                                        <div class="flex gap-2">
                                            <button onclick="app.openProductModal(${p.id})" class="text-brand-500 hover:bg-blue-50 dark:hover:bg-blue-900/20 p-2 rounded transition"><i class="fas fa-edit"></i></button>
                                            <button onclick="app.deleteProduct(${p.id})" class="text-red-500 hover:bg-red-50 dark:hover:bg-red-900/20 p-2 rounded transition"><i class="fas fa-trash"></i></button>
                                        </div>
                                    </div>
                                `).join('')}
                            </div>
                            <button onclick="app.openProductModal()" class="w-full mt-4 bg-green-500 text-white py-3 rounded-xl font-bold hover:bg-green-600 transition shadow-lg shadow-green-500/20 btn-hover-effect">${isFa ? 'افزودن محصول جدید' : 'Add New Product'}</button>
                        </div>
                    </div>
                `;
            },
            renderCart(c) {
                if(this.state.cart.length === 0) { c.innerHTML = `<div class="flex flex-col items-center justify-center min-h-[50vh] text-center animate-fade-in"><div class="w-32 h-32 bg-gray-100 dark:bg-white/5 rounded-full flex items-center justify-center mb-6"><i class="fas fa-shopping-basket text-4xl text-gray-300"></i></div><h2 class="text-xl font-bold dark:text-white">${this.t('empty_cart')}</h2><button onclick="app.router('products')" class="mt-6 bg-brand-600 text-white px-8 py-3 rounded-xl font-bold shadow-lg btn-hover-effect">${this.state.lang === 'fa' ? 'بازگشت' : 'Go Back'}</button></div>`; return; }
                let total = this.state.cart.reduce((s, i) => s + (i.price * i.qty), 0);
                c.innerHTML = `<h2 class="text-2xl font-bold mb-6 dark:text-white">${this.t('cart')}</h2><div class="flex flex-col lg:flex-row gap-8"><div class="flex-1 space-y-4">${this.state.cart.map(i => `<div class="glass-card p-4 rounded-2xl flex gap-4 items-center"><img src="${i.img}" class="w-20 h-20 object-cover rounded-xl bg-gray-100"><div class="flex-1"><h3 class="font-bold text-sm dark:text-white">${i.name}</h3><div class="text-brand-500 font-bold text-sm mt-1">${i.price.toLocaleString()} ${this.t('curr')}</div></div><div class="flex flex-col items-center gap-2 bg-gray-50 dark:bg-white/5 rounded-lg p-1"><button onclick="app.changeQty(${i.id},1)" class="w-6 h-6 flex items-center justify-center bg-white dark:bg-white/10 rounded text-green-500"><i class="fas fa-plus text-xs"></i></button><span class="font-bold text-sm dark:text-white">${i.qty}</span><button onclick="app.changeQty(${i.id},-1)" class="w-6 h-6 flex items-center justify-center bg-white dark:bg-white/10 rounded text-red-500"><i class="fas fa-minus text-xs"></i></button></div></div>`).join('')}</div><div class="lg:w-96"><div class="glass-card p-6 rounded-2xl sticky top-28"><div class="flex justify-between mb-4 text-gray-500"><span>${this.t('total')}</span><span>${total.toLocaleString()}</span></div><div class="border-t pt-4 flex justify-between items-center mb-6"><span class="font-bold dark:text-white">${this.t('total')}</span><span class="text-xl font-black text-brand-500">${total.toLocaleString()}</span></div><button onclick="app.initCheckout()" class="w-full bg-brand-600 text-white py-4 rounded-xl font-bold shadow-lg btn-hover-effect">${this.t('checkout')}</button></div></div></div>`;
            },
            
            renderAbout(c) {
                const isFa = this.state.lang === 'fa';
                c.innerHTML = `
                    <div class="max-w-4xl mx-auto animate-slide-up">
                        <div class="relative rounded-[2.5rem] overflow-hidden h-64 md:h-80 mb-10 shadow-2xl"><img src="https://images.unsplash.com/photo-1522071820081-009f0129c71c?w=1200" class="w-full h-full object-cover"><div class="absolute inset-0 bg-black/60 flex flex-col justify-center items-center text-center p-6"><h2 class="text-4xl md:text-5xl font-black text-white mb-4">${this.t('about')} SVS Empire</h2><p class="text-gray-200 text-lg">${isFa ? 'جایی که تکنولوژی با رویاهای شما ملاقات می‌کند.' : 'Where technology meets your dreams.'}</p></div></div>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-12"><div class="glass-card p-8 rounded-[2rem]"><h3 class="text-2xl font-bold text-brand-500 mb-4">${isFa ? 'داستان ما' : 'Our Story'}</h3><p class="text-gray-500 dark:text-gray-300 leading-relaxed text-justify">${isFa ? 'SVS Empire در سال ۲۰۲۵ توسط سپهر تاسیس شد. ما باور داریم که تکنولوژی باید در دسترس همه باشد.' : 'SVS Empire was founded in 2025 by Sepehr. We believe technology should be accessible to everyone.'}</p></div><div class="glass-card p-8 rounded-[2rem]"><h3 class="text-2xl font-bold text-brand-500 mb-4">${isFa ? 'ماموریت ما' : 'Our Mission'}</h3><ul class="space-y-4 text-gray-500 dark:text-gray-300"><li class="flex items-center gap-3"><i class="fas fa-check-circle text-green-500"></i> ${isFa ? 'محصولات اورجینال' : 'Original Products'}</li><li class="flex items-center gap-3"><i class="fas fa-check-circle text-green-500"></i> ${isFa ? 'پشتیبانی ۲۴ ساعته' : '24/7 Support'}</li></ul></div></div>
                    </div>
                `;
            },
            renderFAQ(c) {
                c.innerHTML = `
                    <div class="max-w-3xl mx-auto animate-slide-up">
                        <div class="text-center mb-10"><h2 class="text-3xl font-black dark:text-white mb-2">${this.t('faq')}</h2><p class="text-gray-400">Q & A</p></div>
                        <div class="space-y-4">${this.state.faq.map(item => `<details class="glass-card rounded-2xl group overflow-hidden transition-all"><summary class="flex justify-between items-center p-6 cursor-pointer select-none font-bold dark:text-white hover:bg-gray-50 dark:hover:bg-white/5 transition"><span>${item.q}</span><i class="fas fa-chevron-down arrow-icon text-gray-400 transition-transform duration-300"></i></summary><div class="p-6 pt-0 text-gray-500 dark:text-gray-400 text-sm leading-7 text-justify border-t border-gray-100 dark:border-white/5 mt-2">${item.a}</div></details>`).join('')}</div>
                    </div>
                `;
            },

            createCard(p) {
                const isFav = this.state.wishlist.includes(p.id);
                return `<div class="group bg-white dark:bg-dark-surface rounded-3xl p-3 shadow-sm hover:shadow-2xl transition-all duration-500 relative overflow-hidden border border-gray-100 dark:border-white/5"><div class="relative h-48 bg-gray-100 dark:bg-black/20 rounded-2xl overflow-hidden mb-3"><img src="${p.img}" class="w-full h-full object-cover mix-blend-multiply dark:mix-blend-normal transition-transform duration-700 group-hover:scale-110">${p.badge ? `<span class="absolute top-3 right-3 bg-black/70 backdrop-blur text-white text-[10px] px-2 py-1 rounded-md font-bold">${p.badge}</span>`:''} <button onclick="app.openQuickView(${p.id})" class="absolute bottom-3 left-1/2 -translate-x-1/2 bg-white/90 text-black px-4 py-2 rounded-full text-xs font-bold shadow-lg translate-y-10 opacity-0 group-hover:translate-y-0 group-hover:opacity-100 transition-all duration-300 hover:bg-brand-500 hover:text-white">${this.state.lang === 'fa' ? 'نمایش سریع' : 'Quick View'}</button></div><div class="px-2"><div class="flex justify-between items-start mb-2"><h3 class="font-bold text-gray-800 dark:text-gray-100 truncate w-2/3">${p.name}</h3><div class="flex text-yellow-400 text-xs"><i class="fas fa-star"></i> ${p.rating}</div></div><div class="flex justify-between items-center mt-4"><div class="flex flex-col"><span class="text-brand-500 font-black text-lg">${p.price.toLocaleString()}</span></div><div class="flex gap-2"><button onclick="app.toggleWishlist(${p.id})" class="w-10 h-10 border border-gray-100 dark:border-white/10 rounded-full flex items-center justify-center transition-colors duration-300 ${isFav?'text-red-500 bg-red-50 dark:bg-red-900/20':'text-gray-400 hover:text-red-500'}"><i class="fas fa-heart" class="${isFav?'heart-active':''}"></i></button><button onclick="app.addToCart(${p.id})" class="w-10 h-10 bg-gray-100 dark:bg-white/10 rounded-full flex items-center justify-center text-gray-600 dark:text-white hover:bg-brand-500 hover:text-white transition-colors duration-300 shadow-sm"><i class="fas fa-plus"></i></button></div></div></div></div>`;
            },
            
            deleteProduct(id) {
                if(confirm(this.t('delete_confirm'))) {
                    this.state.products = this.state.products.filter(p => p.id !== id);
                    this.state.cart = this.state.cart.filter(c => c.id !== id);
                    this.state.wishlist = this.state.wishlist.filter(w => w !== id);
                    this.saveProducts();
                    this.saveCart();
                    localStorage.setItem('wishlist', JSON.stringify(this.state.wishlist));
                    this.renderAdmin(document.getElementById('main-content'));
                    this.updateBadge(); 
                    this.toast(this.t('deleted'), 'success');
                }
            },

            openProductModal(id = null) {
                const modal = document.getElementById('product-modal');
                const title = document.getElementById('modal-product-title');
                if(document.getElementById('prod-file')) document.getElementById('prod-file').value = "";
                if (id) {
                    const p = this.state.products.find(x => x.id === id);
                    document.getElementById('prod-id').value = p.id;
                    document.getElementById('prod-name').value = p.name;
                    document.getElementById('prod-price').value = p.price;
                    document.getElementById('prod-cat').value = p.cat;
                    document.getElementById('prod-img').value = p.img;
                    document.getElementById('prod-desc').value = p.desc;
                    title.innerText = "ویرایش محصول";
                } else {
                    document.getElementById('prod-id').value = '';
                    document.getElementById('prod-name').value = '';
                    document.getElementById('prod-price').value = '';
                    document.getElementById('prod-cat').value = 'drone';
                    document.getElementById('prod-img').value = '';
                    document.getElementById('prod-desc').value = '';
                    title.innerText = "افزودن محصول جدید";
                }
                modal.classList.remove('hidden');
            },

            handleFileSelect(event) {
                const file = event.target.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        document.getElementById('prod-img').value = e.target.result;
                    };
                    reader.readAsDataURL(file);
                }
            },

            closeProductModal() {
                document.getElementById('product-modal').classList.add('hidden');
            },

            handleProductSubmit(e) {
                e.preventDefault();
                const id = document.getElementById('prod-id').value;
                const name = document.getElementById('prod-name').value;
                const price = parseInt(document.getElementById('prod-price').value);
                const cat = document.getElementById('prod-cat').value;
                const img = document.getElementById('prod-img').value;
                const desc = document.getElementById('prod-desc').value;

                if (id) {
                    const index = this.state.products.findIndex(p => p.id == id);
                    if (index > -1) {
                        this.state.products[index] = { 
                            ...this.state.products[index], 
                            name, price, cat, img, desc 
                        };
                    }
                } else {
                    const newId = Math.max(...this.state.products.map(p => p.id), 0) + 1;
                    this.state.products.push({
                        id: newId,
                        name,
                        price,
                        cat,
                        img,
                        desc,
                        rating: 5, 
                        badge: "جدید"
                    });
                }
                this.saveProducts();
                this.closeProductModal();
                this.renderAdmin(document.getElementById('main-content'));
                this.toast(this.t('saved'), 'success');
            },

            addToCart(id) { const item = this.state.cart.find(x=>x.id===id); if(item) item.qty++; else this.state.cart.push({...this.state.products.find(x=>x.id===id),qty:1}); this.updateBadge(); this.saveCart(); this.toast('Added to cart','success'); },
            changeQty(id, d) { const item = this.state.cart.find(x=>x.id===id); if(item) { item.qty+=d; if(item.qty<=0) this.state.cart=this.state.cart.filter(x=>x.id!==id); this.saveCart(); this.updateBadge(); this.router('cart'); } },
            toggleWishlist(id) { 
                const idx = this.state.wishlist.indexOf(id); 
                if(idx>-1) {this.state.wishlist.splice(idx,1); this.toast('Removed','default');} 
                else {this.state.wishlist.push(id); this.toast('Saved','success');} 
                localStorage.setItem('wishlist', JSON.stringify(this.state.wishlist)); 
                const main = document.getElementById('main-content');
                if(this.state.currentPage==='home') this.renderHome(main);
                else if(this.state.currentPage==='products') this.renderProducts(main);
                else if(this.state.currentPage==='wishlist') this.renderWishlist(main);
            },
            toggleAuthModal() { const m=document.getElementById('auth-modal'); m.classList.toggle('hidden'); this.setAuthTab('login'); },
            setAuthTab(mode) { this.state.authMode=mode; document.getElementById('field-name').classList.toggle('hidden', mode==='login'); document.getElementById('auth-title').innerText = mode==='login'?this.t('login'):'Create Account'; document.getElementById('btn-submit-auth').innerText = mode==='login'?'Login':'Sign Up'; document.getElementById('tab-login').className = mode==='login' ? "flex-1 py-2 rounded-lg text-sm font-bold bg-white dark:bg-white/10 shadow text-brand-600" : "flex-1 py-2 rounded-lg text-sm font-bold text-gray-500"; document.getElementById('tab-signup').className = mode==='signup' ? "flex-1 py-2 rounded-lg text-sm font-bold bg-white dark:bg-white/10 shadow text-brand-600" : "flex-1 py-2 rounded-lg text-sm font-bold text-gray-500"; },
            
            // --- تابع ثبت‌نام و ورود که آپدیت شده است ---
            handleAuthSubmit(e) { 
                e.preventDefault(); 
                const nameIn = document.getElementById('input-name').value; 
                const emailIn = document.getElementById('input-email').value; 
                const passIn = document.getElementById('input-pass').value;

                // --- اگر دکمه ثبت‌نام زده شده بود ---
                if(this.state.authMode === 'signup') {
                     if(!nameIn) { this.toast('لطفا نام را وارد کنید','error'); return; }
                     
                     // ارسال درخواست ثبت‌نام به پایتون
                     fetch('/api/signup', {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify({ name: nameIn, email: emailIn, password: passIn })
                     })
                     .then(res => res.json())
                     .then(data => {
                         if(data.status === 'error') {
                             this.toast(data.message, 'error');
                         } else {
                             // ثبت نام موفق -> لاگین خودکار
                             this.state.user = { name: data.name, email: emailIn, role: data.role };
                             this.saveUserAndRedirect(data.message);
                         }
                     })
                     .catch(err => {
                         console.error(err);
                         this.toast('خطا در اتصال به سرور (مطمئن شوید uvicorn روشن است)', 'error');
                     });
                     return;
                }
                
                // --- اگر دکمه ورود زده شده بود ---
                fetch('/api/login', {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({ email: emailIn, password: passIn })
                })
                .then(response => response.json())
                .then(data => {
                    if(data.status === 'error') {
                        this.toast(data.message, 'error');
                    } else {
                        this.state.user = { name: data.name, email: emailIn, role: data.role };
                        this.saveUserAndRedirect(data.message);
                    }
                })
                .catch(error => {
                    console.error("Login Error:", error);
                    this.state.user = { name: "Guest (Offline)", email: emailIn, role: 'user' };
                    this.saveUserAndRedirect("شما آفلاین وارد شدید (سرور قطع است)");
                });
            },

            saveUserAndRedirect(msg) {
                localStorage.setItem('user', JSON.stringify(this.state.user)); 
                document.getElementById('auth-modal').classList.add('hidden'); 
                this.updateAuthButton(); 
                this.toast(msg, 'success');
                
                if (this.state.user.role === 'admin') {
                    this.router('admin');
                } else {
                    this.router('home');
                }
            },

            initCheckout() {
                if (!this.state.user) {
                    this.toast(this.state.lang === 'fa' ? 'لطفا ابتدا وارد شوید' : 'Please login first', 'error');
                    this.toggleAuthModal();
                    return;
                }
                document.getElementById('chk-name').value = this.state.user.name || '';
                document.getElementById('chk-email').value = this.state.user.email || '';
                document.getElementById('checkout-modal').classList.remove('hidden');
            },
            
            closeCheckoutModal() {
                document.getElementById('checkout-modal').classList.add('hidden');
            },

            handleCheckoutSubmit(e) {
                e.preventDefault();
                const btn = e.target.querySelector('button[type="submit"]');
                const originalText = btn.innerHTML;
                
                btn.disabled = true;
                btn.innerHTML = '<i class="fas fa-spinner fa-spin mr-2"></i> ...';
                
                setTimeout(() => {
                    const newOrder = {
                        id: Math.floor(100000 + Math.random() * 900000),
                        date: new Date().toLocaleDateString(this.state.lang === 'fa' ? 'fa-IR' : 'en-US'),
                        items: [...this.state.cart],
                        total: this.state.cart.reduce((s, i) => s + (i.price * i.qty), 0),
                        status: 'processing'
                    };

                    this.state.orders.push(newOrder);
                    localStorage.setItem('orders', JSON.stringify(this.state.orders));
                    this.state.cart = [];
                    this.saveCart();
                    this.updateBadge();
                    this.closeCheckoutModal();
                    this.toast(this.state.lang === 'fa' ? 'سفارش ثبت شد!' : 'Order Placed!', 'success');
                    this.router('orders');
                    btn.disabled = false;
                    btn.innerHTML = originalText;
                }, 2000);
            },

            logout() { 
                this.state.user=null; 
                localStorage.removeItem('user'); 
                location.reload(); 
            },
            
            updateAuthButton() { const btn=document.getElementById('desktop-auth-btn'); if(this.state.user) btn.innerHTML=`<button onclick="app.router('profile')" class="hidden md:flex bg-gray-100 dark:bg-white/10 hover:bg-gray-200 text-gray-800 dark:text-white px-4 py-2.5 rounded-xl font-bold text-sm transition items-center gap-2"><i class="fas fa-user-circle text-lg"></i><span>${this.state.user.name}</span></button>`; else btn.innerHTML=`<button onclick="app.toggleAuthModal()" class="hidden md:flex bg-brand-600 hover:bg-brand-700 text-white px-6 py-2.5 rounded-xl font-bold text-sm shadow-lg shadow-brand-500/20 transition-all hover:shadow-brand-500/40 items-center gap-2"><span>${this.t('login')}</span><i class="fas fa-arrow-left text-xs rtl:rotate-0 ltr:rotate-180"></i></button>`; },
            saveCart() { localStorage.setItem('cart', JSON.stringify(this.state.cart)); },
            saveProducts() { localStorage.setItem('products', JSON.stringify(this.state.products)); },
            updateBadge() { const c=this.state.cart.reduce((a,b)=>a+b.qty,0); document.getElementById('badge-count').innerText=c; document.getElementById('badge-count').classList.toggle('scale-0', c===0); },
            toggleTheme() { document.documentElement.classList.toggle('dark'); localStorage.setItem('theme', document.documentElement.classList.contains('dark')?'dark':'light'); },
            openQuickView(id) { const p=this.state.products.find(x=>x.id===id); document.getElementById('quick-view-modal').classList.remove('hidden'); document.getElementById('quick-view-content').innerHTML=`<div class="flex flex-col md:flex-row h-full"><div class="w-full md:w-1/2 h-64 md:h-auto bg-gray-100 dark:bg-black/20"><img src="${p.img}" class="w-full h-full object-cover"></div><div class="flex-1 p-6 md:p-10 flex flex-col justify-center dark:text-white"><span class="text-brand-500 font-bold text-xs uppercase tracking-wider mb-2">${p.cat}</span><h2 class="text-3xl font-black mb-4">${p.name}</h2><p class="text-gray-500 dark:text-gray-400 mb-6 leading-relaxed">${p.desc}</p><div class="text-3xl font-black mb-8">${p.price.toLocaleString()} <span class="text-sm font-normal text-gray-400">Toman</span></div><div class="flex gap-4"><button onclick="app.addToCart(${p.id}); app.closeModal()" class="flex-1 bg-brand-600 text-white py-4 rounded-xl font-bold shadow-lg hover:bg-brand-500 transition">Add to Cart</button></div></div></div>`; },
            closeModal() { document.getElementById('quick-view-modal').classList.add('hidden'); },
            toast(msg, type) { const box=document.getElementById('toast-box'); const el=document.createElement('div'); const clr=type==='success'?'bg-green-500':(type==='error'?'bg-red-500':'bg-gray-800'); el.className=`${clr} text-white px-6 py-4 rounded-2xl shadow-2xl flex items-center gap-3 animate-slide-up backdrop-blur-md bg-opacity-90`; el.innerHTML=`<i class="fas fa-${type==='success'?'check':'info'}-circle"></i><span class="text-sm font-bold">${msg}</span>`; box.appendChild(el); setTimeout(()=>{el.style.opacity='0'; setTimeout(()=>el.remove(),300)},3000); }
        };
        app.init();
    </script>
</body>
</html>
