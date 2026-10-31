
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PPM - Sistema de Mantenimiento Bilingüe (中/西)</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'system-ui', '-apple-system', 'sans-serif'],
                    },
                    colors: {
                        zhbrand: {
                            50: '#f0fdf4',
                            100: '#dcfce7',
                            500: '#22c55e',
                            600: '#16a34a',
                            700: '#15803d',
                            800: '#166534',
                            900: '#14532d',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }
        .touch-active:active {
            transform: scale(0.98);
        }

        /* =========================================================
           ANIMACIÓN DEL NUEVO LOGO PPM (MÉXICO Y CHINA + CÍRCULOS + PPM)
           Secuencia solicitada:
           1° Aparecen las franjitas del continente mexicano y chino
           2° Aparecen los círculos verdes con efecto de desvanecido
           3° Aparecen las letras PPM
           ========================================================= */

        /* --- Versión Pantalla de Carga (Misma animación al doble de velocidad x2: 2.1s) --- */
        @keyframes splashContinentStripes {
            0% { opacity: 0; stroke-dashoffset: 90; transform: scale(0.96); }
            14%, 86% { opacity: 1; stroke-dashoffset: 0; transform: scale(1); }
            97%, 100% { opacity: 0; transform: scale(0.98); }
        }
        @keyframes splashGreenCircles {
            0%, 15% { opacity: 0; }
            30%, 86% { opacity: 1; }
            97%, 100% { opacity: 0; }
        }
        @keyframes splashPpmLetters {
            0%, 31% { opacity: 0; transform: scale(0.93); }
            45%, 86% { opacity: 1; transform: scale(1); }
            97%, 100% { opacity: 0; transform: scale(0.98); }
        }

        .splash-continents {
            stroke-dasharray: 90;
            animation: splashContinentStripes 2.1s infinite ease-in-out;
            transform-origin: center;
            filter: drop-shadow(0px 0px 3px rgba(11, 110, 34, 0.85));
        }
        .splash-circles {
            animation: splashGreenCircles 2.1s infinite ease-in-out;
            transform-origin: center;
        }
        .splash-ppm-text {
            animation: splashPpmLetters 2.1s infinite ease-out;
            transform-origin: center;
        }

        /* --- Versión Pantalla Inicial Login (Ciclo de 12s) ---
           0% - 14%: 1° Aparecen las franjitas del continente mexicano y chino
           15% - 30%: 2° Aparecen los circulitos verdes con efecto desvanecido (fade-in)
           31% - 45%: 3° Aparecen las letras PPM
           45% - 86%: Se mantiene el logo completo
           86% - 100%: Se desvanece suavemente para repetir
        */
        @keyframes loginContinentStripes {
            0% { opacity: 0; stroke-dashoffset: 90; transform: scale(0.96); }
            14%, 86% { opacity: 1; stroke-dashoffset: 0; transform: scale(1); }
            97%, 100% { opacity: 0; transform: scale(0.98); }
        }
        @keyframes loginGreenCircles {
            0%, 15% { opacity: 0; }
            30%, 86% { opacity: 1; }
            97%, 100% { opacity: 0; }
        }
        @keyframes loginPpmLetters {
            0%, 31% { opacity: 0; transform: scale(0.93); }
            45%, 86% { opacity: 1; transform: scale(1); }
            97%, 100% { opacity: 0; transform: scale(0.98); }
        }

        .login-continents {
            stroke-dasharray: 90;
            animation: loginContinentStripes 12s infinite ease-in-out;
            transform-origin: center;
            filter: drop-shadow(0px 0px 3px rgba(11, 110, 34, 0.85));
        }
        .login-circles {
            animation: loginGreenCircles 12s infinite ease-in-out;
            transform-origin: center;
        }
        .login-ppm-text {
            animation: loginPpmLetters 12s infinite ease-out;
            transform-origin: center;
        }
    </style>
</head>
<body class="bg-slate-100 text-slate-800 min-h-screen flex flex-col">

    <!-- =====================================================
         PANTALLA DE CARGA (SPLASH SCREEN / SIN CONEXIÓN)
         Fondo gris con nuevo logo PPM animado y texto Chino/Español
         ===================================================== -->
    <div id="splash-screen" class="fixed inset-0 z-[100] bg-slate-200 flex flex-col items-center justify-center p-6 transition-opacity duration-500">
        <div class="flex flex-col items-center">
            <!-- Nuevo Logo PPM Animado (Continentes -> Círculos Verdes -> Letras PPM) -->
            <div class="w-48 h-28 flex items-center justify-center">
                <svg viewBox="0 0 360 210" class="w-full h-full overflow-visible">
                    <defs>
                        <linearGradient id="ppmGreenGradSplash" x1="0%" y1="0%" x2="15%" y2="100%">
                            <stop offset="0%" stop-color="#44c739" />
                            <stop offset="45%" stop-color="#1ca02d" />
                            <stop offset="100%" stop-color="#0b7222" />
                        </linearGradient>
                    </defs>

                    <!-- 2° CÍRCULOS VERDES CON EFECTO DESVANECIDO (en el fondo del globo) -->
                    <g class="splash-circles">
                        <circle cx="118" cy="105" r="92" fill="url(#ppmGreenGradSplash)" />
                        <circle cx="242" cy="105" r="92" fill="url(#ppmGreenGradSplash)" />
                    </g>

                    <!-- 1° FRANJITAS DEL CONTINENTE MEXICANO (IZQUIERDA) Y CHINO (DERECHA) -->
                    <g class="splash-continents" stroke="#ffffff" stroke-width="3.6" stroke-linecap="round">
                        <!-- Continente Americano / México (Hemisferio Izquierdo) -->
                        <line x1="74" y1="52" x2="106" y2="52" />
                        <line x1="115" y1="52" x2="145" y2="52" />
                        <line x1="60" y1="58" x2="64" y2="58" />
                        <line x1="72" y1="58" x2="148" y2="58" />
                        <line x1="56" y1="64" x2="138" y2="64" />
                        <line x1="145" y1="64" x2="152" y2="64" />
                        <line x1="42" y1="70" x2="54" y2="70" />
                        <line x1="62" y1="70" x2="142" y2="70" />
                        <line x1="36" y1="76" x2="46" y2="76" />
                        <line x1="54" y1="76" x2="136" y2="76" />
                        <line x1="48" y1="82" x2="128" y2="82" />
                        <line x1="58" y1="88" x2="120" y2="88" />
                        <line x1="65" y1="94" x2="112" y2="94" />
                        <line x1="70" y1="100" x2="108" y2="100" />
                        <line x1="76" y1="106" x2="115" y2="106" />
                        <line x1="82" y1="112" x2="122" y2="112" />
                        <line x1="78" y1="118" x2="118" y2="118" />
                        <line x1="74" y1="124" x2="114" y2="124" />
                        <line x1="80" y1="130" x2="120" y2="130" />
                        <line x1="84" y1="136" x2="128" y2="136" />
                        <line x1="88" y1="142" x2="132" y2="142" />
                        <line x1="94" y1="148" x2="126" y2="148" />
                        <line x1="92" y1="154" x2="122" y2="154" />
                        <line x1="95" y1="160" x2="116" y2="160" />
                        <line x1="94" y1="166" x2="110" y2="166" />
                        <line x1="96" y1="172" x2="105" y2="172" />

                        <!-- Continente Asiático / China (Hemisferio Derecho) -->
                        <line x1="210" y1="46" x2="236" y2="46" />
                        <line x1="252" y1="46" x2="262" y2="46" />
                        <line x1="178" y1="52" x2="188" y2="52" />
                        <line x1="196" y1="52" x2="294" y2="52" />
                        <line x1="168" y1="58" x2="310" y2="58" />
                        <line x1="160" y1="64" x2="318" y2="64" />
                        <line x1="158" y1="70" x2="306" y2="70" />
                        <line x1="313" y1="70" x2="319" y2="70" />
                        <line x1="152" y1="76" x2="298" y2="76" />
                        <line x1="150" y1="82" x2="292" y2="82" />
                        <line x1="148" y1="88" x2="288" y2="88" />
                        <line x1="296" y1="88" x2="302" y2="88" />
                        <line x1="154" y1="94" x2="294" y2="94" />
                        <line x1="160" y1="100" x2="286" y2="100" />
                        <line x1="166" y1="106" x2="282" y2="106" />
                        <line x1="170" y1="112" x2="278" y2="112" />
                        <line x1="172" y1="118" x2="272" y2="118" />
                        <line x1="176" y1="124" x2="264" y2="124" />
                        <line x1="174" y1="130" x2="216" y2="130" />
                        <line x1="248" y1="130" x2="278" y2="130" />
                        <line x1="178" y1="136" x2="212" y2="136" />
                        <line x1="256" y1="136" x2="284" y2="136" />
                        <line x1="182" y1="142" x2="206" y2="142" />
                        <line x1="264" y1="142" x2="290" y2="142" />
                        <line x1="184" y1="148" x2="202" y2="148" />
                        <line x1="268" y1="148" x2="296" y2="148" />
                        <line x1="188" y1="154" x2="198" y2="154" />
                        <line x1="262" y1="154" x2="298" y2="154" />
                        <line x1="266" y1="160" x2="294" y2="160" />
                        <line x1="272" y1="166" x2="288" y2="166" />
                        <line x1="280" y1="172" x2="286" y2="172" />
                    </g>

                    <!-- 3° LETRAS PPM INCLINADAS AL FRENTE -->
                    <g class="splash-ppm-text">
                        <text x="176" y="138"
                            text-anchor="middle"
                            fill="#ffffff"
                            stroke="#128327"
                            stroke-width="7"
                            stroke-linejoin="round"
                            paint-order="stroke fill"
                            font-family="Inter, 'Arial Black', sans-serif"
                            font-weight="900"
                            font-style="italic"
                            font-size="92"
                            letter-spacing="1">PPM</text>
                    </g>
                </svg>
            </div>

            <!-- Texto Cargando en Chino y Español -->
            <div class="mt-2 text-center">
                <p class="text-xs font-extrabold text-slate-700 tracking-wider">正在加载 / Cargando...</p>
                <p id="splash-offline-msg" class="hidden text-[11px] font-semibold text-amber-700 mt-1">
                    网络连接不稳定，正在重试 / Sin conexión a internet, esperando red...
                </p>
            </div>
        </div>
    </div>

    <!-- =====================================================
         CONTENEDOR PRINCIPAL ADAPTATIVO
         Móvil (max-w-md) para Login / Técnicos / QR
         Escritorio de PC (max-w-7xl) para Administrador
         ===================================================== -->
    <div id="app-shell" class="w-full max-w-md mx-auto min-h-screen flex flex-col bg-slate-50 shadow-xl transition-all duration-300">

        <!-- ENCABEZADO SUPERIOR -->
        <header id="main-header" class="hidden bg-slate-900 text-white px-4 py-3.5 shadow-md sticky top-0 z-30">
            <div class="flex items-center justify-between gap-2">
                <div class="flex items-center gap-2.5 min-w-0">
                    <div class="w-12 h-8 rounded-xl bg-white/95 p-0.5 flex items-center justify-center shrink-0 shadow-inner">
                        <svg viewBox="0 0 360 210" class="w-full h-full">
                            <circle cx="118" cy="105" r="92" fill="#1ca02d" />
                            <circle cx="242" cy="105" r="92" fill="#1ca02d" />
                            <text x="176" y="138" text-anchor="middle" fill="#ffffff" stroke="#0b7222" stroke-width="6" paint-order="stroke fill" font-family="Inter, sans-serif" font-weight="900" font-style="italic" font-size="92">PPM</text>
                        </svg>
                    </div>
                    <div class="truncate">
                        <h1 id="header-title" class="text-sm font-extrabold leading-tight truncate">Sistema de Mantenimiento</h1>
                        <p id="header-subtitle" class="text-[11px] text-emerald-400 font-semibold leading-tight truncate">Planta Industrial PPM</p>
                    </div>
                </div>

                <div class="flex items-center gap-2 shrink-0">
                    <span id="cloud-status-badge" class="px-2.5 py-1 rounded-lg bg-emerald-900/70 border border-emerald-600/60 text-[10px] font-extrabold text-emerald-300 flex items-center gap-1.5">
                        <span id="cloud-status-dot" class="w-2 h-2 rounded-full bg-amber-400 animate-pulse"></span>
                        <span id="cloud-status-text">Conectando Nube...</span>
                    </span>
                    <button type="button" onclick="openLanguageSelector()" id="header-lang-btn" class="touch-active bg-slate-800 hover:bg-slate-700 border border-slate-700 text-emerald-400 text-[11px] font-extrabold px-2.5 py-1 rounded-lg flex items-center gap-1 transition" title="Cambiar idioma">
                        <i class="fa-solid fa-globe"></i>
                        <span id="header-lang-code">ES</span>
                    </button>
                    <span id="user-badge" class="px-2.5 py-1 rounded-lg bg-slate-800 border border-slate-700 text-[11px] font-bold text-slate-200 truncate max-w-[140px]">
                        Usuario
                    </span>
                    <button type="button" onclick="handleLogout()" class="touch-active bg-rose-600 hover:bg-rose-700 text-white text-xs font-bold px-3 py-1.5 rounded-xl shadow flex items-center gap-1.5 transition">
                        <i class="fa-solid fa-right-from-bracket"></i>
                        <span id="btn-logout-text">Salir</span>
                    </button>
                </div>
            </div>
        </header>

        <!-- =====================================================
             0. PANTALLA DE SELECCIÓN DE IDIOMA (ESPAÑOL / INGLÉS / CHINO)
             Aparece antes de llegar a la pantalla de inicio
             ===================================================== -->
        <section id="screen-language" class="flex-1 flex flex-col justify-center p-6">
            <div class="bg-white rounded-3xl shadow-xl border border-slate-200/80 p-6 space-y-6 text-center">
                <div class="flex flex-col items-center pt-1">
                    <div class="w-56 h-32 flex items-center justify-center">
                        <svg viewBox="0 0 360 210" class="w-full h-full overflow-visible">
                            <defs>
                                <linearGradient id="ppmGreenGradLang" x1="0%" y1="0%" x2="15%" y2="100%">
                                    <stop offset="0%" stop-color="#44c739" />
                                    <stop offset="45%" stop-color="#1ca02d" />
                                    <stop offset="100%" stop-color="#0b7222" />
                                </linearGradient>
                            </defs>
                            <g class="login-circles">
                                <circle cx="118" cy="105" r="92" fill="url(#ppmGreenGradLang)" />
                                <circle cx="242" cy="105" r="92" fill="url(#ppmGreenGradLang)" />
                            </g>
                            <g class="login-continents" stroke="#ffffff" stroke-width="3.6" stroke-linecap="round">
                                <line x1="74" y1="52" x2="106" y2="52" /><line x1="115" y1="52" x2="145" y2="52" />
                                <line x1="60" y1="58" x2="64" y2="58" /><line x1="72" y1="58" x2="148" y2="58" />
                                <line x1="56" y1="64" x2="138" y2="64" /><line x1="145" y1="64" x2="152" y2="64" />
                                <line x1="42" y1="70" x2="54" y2="70" /><line x1="62" y1="70" x2="142" y2="70" />
                                <line x1="36" y1="76" x2="46" y2="76" /><line x1="54" y1="76" x2="136" y2="76" />
                                <line x1="48" y1="82" x2="128" y2="82" /><line x1="58" y1="88" x2="120" y2="88" />
                                <line x1="65" y1="94" x2="112" y2="94" /><line x1="70" y1="100" x2="108" y2="100" />
                                <line x1="76" y1="106" x2="115" y2="106" /><line x1="82" y1="112" x2="122" y2="112" />
                                <line x1="78" y1="118" x2="118" y2="118" /><line x1="74" y1="124" x2="114" y2="124" />
                                <line x1="80" y1="130" x2="120" y2="130" /><line x1="84" y1="136" x2="128" y2="136" />
                                <line x1="88" y1="142" x2="132" y2="142" /><line x1="94" y1="148" x2="126" y2="148" />
                                <line x1="92" y1="154" x2="122" y2="154" /><line x1="95" y1="160" x2="116" y2="160" />
                                <line x1="94" y1="166" x2="110" y2="166" /><line x1="96" y1="172" x2="105" y2="172" />
                                <line x1="210" y1="46" x2="236" y2="46" /><line x1="252" y1="46" x2="262" y2="46" />
                                <line x1="178" y1="52" x2="188" y2="52" /><line x1="196" y1="52" x2="294" y2="52" />
                                <line x1="168" y1="58" x2="310" y2="58" /><line x1="160" y1="64" x2="318" y2="64" />
                                <line x1="158" y1="70" x2="306" y2="70" /><line x1="313" y1="70" x2="319" y2="70" />
                                <line x1="152" y1="76" x2="298" y2="76" /><line x1="150" y1="82" x2="292" y2="82" />
                                <line x1="148" y1="88" x2="288" y2="88" /><line x1="296" y1="88" x2="302" y2="88" />
                                <line x1="154" y1="94" x2="294" y2="94" /><line x1="160" y1="100" x2="286" y2="100" />
                                <line x1="166" y1="106" x2="282" y2="106" /><line x1="170" y1="112" x2="278" y2="112" />
                                <line x1="172" y1="118" x2="272" y2="118" /><line x1="176" y1="124" x2="264" y2="124" />
                                <line x1="174" y1="130" x2="216" y2="130" /><line x1="248" y1="130" x2="278" y2="130" />
                                <line x1="178" y1="136" x2="212" y2="136" /><line x1="256" y1="136" x2="284" y2="136" />
                                <line x1="182" y1="142" x2="206" y2="142" /><line x1="264" y1="142" x2="290" y2="142" />
                                <line x1="184" y1="148" x2="202" y2="148" /><line x1="268" y1="148" x2="296" y2="148" />
                                <line x1="188" y1="154" x2="198" y2="154" /><line x1="262" y1="154" x2="298" y2="154" />
                                <line x1="266" y1="160" x2="294" y2="160" /><line x1="272" y1="166" x2="288" y2="166" />
                                <line x1="280" y1="172" x2="286" y2="172" />
                            </g>
                            <g class="login-ppm-text">
                                <text x="176" y="138" text-anchor="middle" fill="#ffffff" stroke="#128327" stroke-width="7" stroke-linejoin="round" paint-order="stroke fill" font-family="Inter, 'Arial Black', sans-serif" font-weight="900" font-style="italic" font-size="92" letter-spacing="1">PPM</text>
                            </g>
                        </svg>
                    </div>
                    <div class="mt-2 space-y-1">
                        <h2 class="text-base font-black text-slate-900">Selecciona tu idioma / Select Language / 请选择语言</h2>
                        <p class="text-xs font-semibold text-slate-500">Elige el idioma en el que deseas utilizar todo el sistema</p>
                    </div>
                </div>

                <div class="space-y-3">
                    <button type="button" onclick="selectAppLanguage('es')" class="touch-active w-full p-4 rounded-2xl border-2 border-slate-200 hover:border-emerald-500 hover:bg-emerald-50/60 flex items-center justify-between transition group">
                        <div class="flex items-center gap-3.5">
                            <!-- 1ª Imagen: Bandera Circular de México -->
                            <div class="w-12 h-12 rounded-full overflow-hidden shadow-md border border-slate-200 shrink-0 flex items-center justify-center bg-white">
                                <svg viewBox="0 0 100 100" class="w-full h-full">
                                    <defs>
                                        <clipPath id="clipFlagMx">
                                            <circle cx="50" cy="50" r="50" />
                                        </clipPath>
                                    </defs>
                                    <g clip-path="url(#clipFlagMx)">
                                        <rect x="0" y="0" width="33.4" height="100" fill="#006847" />
                                        <rect x="33.3" y="0" width="33.4" height="100" fill="#ffffff" />
                                        <rect x="66.6" y="0" width="33.4" height="100" fill="#ce1126" />
                                        <!-- Escudo Nacional Mexicano estilizado al centro -->
                                        <g transform="translate(50, 50)">
                                            <!-- Laurel y encino -->
                                            <path d="M-12,7 C-10,14 10,14 12,7" fill="none" stroke="#2e7d32" stroke-width="1.8" stroke-linecap="round" />
                                            <path d="M-4,12 L4,12" stroke="#ce1126" stroke-width="1.5" />
                                            <!-- Nopal y agua -->
                                            <path d="M-8,6 Q0,9 8,6" fill="none" stroke="#0288d1" stroke-width="1.8" />
                                            <ellipse cx="0" cy="4.5" rx="6" ry="2.2" fill="#2e7d32" />
                                            <circle cx="-4" cy="3" r="1.6" fill="#388e3c" />
                                            <circle cx="4" cy="3" r="1.6" fill="#388e3c" />
                                            <!-- Águila real -->
                                            <path d="M-2,3 L-5,-5 C-1,-8 4,-9 9,-3 C7,1 4,3 1,3 Z" fill="#6d4c41" />
                                            <path d="M0,-4 C5,-10 11,-6 8,2 C5,1 2,0 0,-4 Z" fill="#5d4037" />
                                            <circle cx="-3" cy="-5.5" r="1.8" fill="#6d4c41" />
                                            <path d="M-4.5,-5.5 L-6.5,-4.8 L-4.5,-4.2 Z" fill="#ffb300" />
                                            <!-- Serpiente -->
                                            <path d="M-6,-5 Q-9,-2 -6,1 Q-4,3 -6,5" fill="none" stroke="#558b2f" stroke-width="1.4" stroke-linecap="round" />
                                        </g>
                                    </g>
                                </svg>
                            </div>
                            <div class="text-left">
                                <p class="text-sm font-black text-slate-900 group-hover:text-emerald-800">Español</p>
                                <p class="text-[11px] font-semibold text-slate-500">Interfaz completa en español</p>
                            </div>
                        </div>
                        <i class="fa-solid fa-chevron-right text-slate-400 group-hover:text-emerald-600"></i>
                    </button>

                    <button type="button" onclick="selectAppLanguage('en')" class="touch-active w-full p-4 rounded-2xl border-2 border-slate-200 hover:border-blue-500 hover:bg-blue-50/60 flex items-center justify-between transition group">
                        <div class="flex items-center gap-3.5">
                            <!-- 2ª Imagen: Bandera Circular de Estados Unidos (English) -->
                            <div class="w-12 h-12 rounded-full overflow-hidden shadow-md border border-slate-200 shrink-0 flex items-center justify-center bg-white">
                                <svg viewBox="0 0 100 100" class="w-full h-full">
                                    <defs>
                                        <clipPath id="clipFlagUs">
                                            <circle cx="50" cy="50" r="50" />
                                        </clipPath>
                                    </defs>
                                    <g clip-path="url(#clipFlagUs)">
                                        <rect width="100" height="100" fill="#ffffff" />
                                        <!-- Franjas rojas y blancas -->
                                        <rect y="0" width="100" height="11.1" fill="#d32027" />
                                        <rect y="22.2" width="100" height="11.1" fill="#d32027" />
                                        <rect y="44.4" width="100" height="11.1" fill="#d32027" />
                                        <rect y="66.6" width="100" height="11.1" fill="#d32027" />
                                        <rect y="88.8" width="100" height="11.2" fill="#d32027" />
                                        <!-- Cantón azul con estrellas blancas -->
                                        <rect x="0" y="0" width="52" height="55.5" fill="#003580" />
                                        <g fill="#ffffff">
                                            <!-- Estrellas en el cantón -->
                                            <polygon points="14,10 15.5,14 19.8,14 16.3,16.5 17.6,20.5 14,18 10.4,20.5 11.7,16.5 8.2,14 12.5,14" />
                                            <polygon points="32,10 33.5,14 37.8,14 34.3,16.5 35.6,20.5 32,18 28.4,20.5 29.7,16.5 26.2,14 30.5,14" />
                                            <polygon points="23,21 24.5,25 28.8,25 25.3,27.5 26.6,31.5 23,29 19.4,31.5 20.7,27.5 17.2,25 21.5,25" />
                                            <polygon points="41,21 42.5,25 46.8,25 43.3,27.5 44.6,31.5 41,29 37.4,31.5 38.7,27.5 35.2,25 39.5,25" />
                                            <polygon points="14,32 15.5,36 19.8,36 16.3,38.5 17.6,42.5 14,40 10.4,42.5 11.7,38.5 8.2,36 12.5,36" />
                                            <polygon points="32,32 33.5,36 37.8,36 34.3,38.5 35.6,42.5 32,40 28.4,42.5 29.7,38.5 26.2,36 30.5,36" />
                                            <polygon points="9,43 10.5,47 14.8,47 11.3,49.5 12.6,53.5 9,51 5.4,53.5 6.7,49.5 3.2,47 7.5,47" />
                                            <polygon points="25,43 26.5,47 30.8,47 27.3,49.5 28.6,53.5 25,51 21.4,53.5 22.7,49.5 19.2,47 23.5,47" />
                                            <polygon points="41,43 42.5,47 46.8,47 43.3,49.5 44.6,53.5 41,51 37.4,53.5 38.7,49.5 35.2,47 39.5,47" />
                                        </g>
                                    </g>
                                </svg>
                            </div>
                            <div class="text-left">
                                <p class="text-sm font-black text-slate-900 group-hover:text-blue-800">English</p>
                                <p class="text-[11px] font-semibold text-slate-500">Full interface in English</p>
                            </div>
                        </div>
                        <i class="fa-solid fa-chevron-right text-slate-400 group-hover:text-blue-600"></i>
                    </button>

                    <button type="button" onclick="selectAppLanguage('zh')" class="touch-active w-full p-4 rounded-2xl border-2 border-slate-200 hover:border-amber-500 hover:bg-amber-50/60 flex items-center justify-between transition group">
                        <div class="flex items-center gap-3.5">
                            <!-- 3ª Imagen: Bandera Circular de China (中文) -->
                            <div class="w-12 h-12 rounded-full overflow-hidden shadow-md border border-slate-200 shrink-0 flex items-center justify-center bg-white">
                                <svg viewBox="0 0 100 100" class="w-full h-full">
                                    <circle cx="50" cy="50" r="50" fill="#de2910" />
                                    <!-- Estrella principal amarilla -->
                                    <polygon fill="#ffde00" points="34,26 38.5,39.8 53,39.8 41.3,48.3 45.7,62.1 34,53.6 22.3,62.1 26.7,48.3 15,39.8 29.5,39.8" />
                                    <!-- 4 Estrellas secundarias en arco a la derecha -->
                                    <polygon fill="#ffde00" transform="translate(63, 24) rotate(-25) scale(0.32)" points="0,-18 5.3,-5.5 19,-5.5 8,3 12.2,16.5 0,8.2 -12.2,16.5 -8,3 -19,-5.5 -5.3,-5.5" />
                                    <polygon fill="#ffde00" transform="translate(76, 37) rotate(-5) scale(0.32)" points="0,-18 5.3,-5.5 19,-5.5 8,3 12.2,16.5 0,8.2 -12.2,16.5 -8,3 -19,-5.5 -5.3,-5.5" />
                                    <polygon fill="#ffde00" transform="translate(76, 56) rotate(15) scale(0.32)" points="0,-18 5.3,-5.5 19,-5.5 8,3 12.2,16.5 0,8.2 -12.2,16.5 -8,3 -19,-5.5 -5.3,-5.5" />
                                    <polygon fill="#ffde00" transform="translate(63, 71) rotate(35) scale(0.32)" points="0,-18 5.3,-5.5 19,-5.5 8,3 12.2,16.5 0,8.2 -12.2,16.5 -8,3 -19,-5.5 -5.3,-5.5" />
                                </svg>
                            </div>
                            <div class="text-left">
                                <p class="text-sm font-black text-slate-900 group-hover:text-amber-800">中文 (简体)</p>
                                <p class="text-[11px] font-semibold text-slate-500">全中文系统界面</p>
                            </div>
                        </div>
                        <i class="fa-solid fa-chevron-right text-slate-400 group-hover:text-amber-600"></i>
                    </button>
                </div>
            </div>
        </section>

        <!-- =====================================================
             1. PANTALLA DE LOGIN INICIAL
             ===================================================== -->
        <section id="screen-login" class="hidden flex-1 flex flex-col justify-center p-6">
            <div class="bg-white rounded-3xl shadow-xl border border-slate-200/80 p-6 space-y-5">
                <!-- Botón superior para cambiar idioma -->
                <div class="flex justify-end">
                    <button type="button" onclick="openLanguageSelector()" class="touch-active text-xs font-extrabold text-slate-600 hover:text-emerald-700 bg-slate-100 hover:bg-emerald-50 px-3 py-1.5 rounded-xl flex items-center gap-1.5 transition">
                        <i class="fa-solid fa-globe text-emerald-600"></i>
                        <span id="login-change-lang-label">Cambiar idioma</span>
                    </button>
                </div>

                <!-- Nuevo Logo PPM con secuencia animada:
                     1° Continentes mexicano y chino (franjitas)
                     2° Círculos verdes con desvanecido
                     3° Letras PPM -->
                <div class="flex flex-col items-center pt-1">
                    <div class="w-64 h-36 flex items-center justify-center">
                        <svg viewBox="0 0 360 210" class="w-full h-full overflow-visible">
                            <defs>
                                <linearGradient id="ppmGreenGradLogin" x1="0%" y1="0%" x2="15%" y2="100%">
                                    <stop offset="0%" stop-color="#44c739" />
                                    <stop offset="45%" stop-color="#1ca02d" />
                                    <stop offset="100%" stop-color="#0b7222" />
                                </linearGradient>
                            </defs>

                            <!-- 2° CÍRCULOS VERDES CON EFECTO DE DESVANECIDO -->
                            <g class="login-circles">
                                <circle cx="118" cy="105" r="92" fill="url(#ppmGreenGradLogin)" />
                                <circle cx="242" cy="105" r="92" fill="url(#ppmGreenGradLogin)" />
                            </g>

                            <!-- 1° FRANJITAS DEL CONTINENTE MEXICANO (IZQ) Y CHINO (DER) DETRÁS DE LAS LETRAS -->
                            <g class="login-continents" stroke="#ffffff" stroke-width="3.6" stroke-linecap="round">
                                <!-- Continente Mexicano / Americano (Izquierda) -->
                                <line x1="74" y1="52" x2="106" y2="52" />
                                <line x1="115" y1="52" x2="145" y2="52" />
                                <line x1="60" y1="58" x2="64" y2="58" />
                                <line x1="72" y1="58" x2="148" y2="58" />
                                <line x1="56" y1="64" x2="138" y2="64" />
                                <line x1="145" y1="64" x2="152" y2="64" />
                                <line x1="42" y1="70" x2="54" y2="70" />
                                <line x1="62" y1="70" x2="142" y2="70" />
                                <line x1="36" y1="76" x2="46" y2="76" />
                                <line x1="54" y1="76" x2="136" y2="76" />
                                <line x1="48" y1="82" x2="128" y2="82" />
                                <line x1="58" y1="88" x2="120" y2="88" />
                                <line x1="65" y1="94" x2="112" y2="94" />
                                <line x1="70" y1="100" x2="108" y2="100" />
                                <line x1="76" y1="106" x2="115" y2="106" />
                                <line x1="82" y1="112" x2="122" y2="112" />
                                <line x1="78" y1="118" x2="118" y2="118" />
                                <line x1="74" y1="124" x2="114" y2="124" />
                                <line x1="80" y1="130" x2="120" y2="130" />
                                <line x1="84" y1="136" x2="128" y2="136" />
                                <line x1="88" y1="142" x2="132" y2="142" />
                                <line x1="94" y1="148" x2="126" y2="148" />
                                <line x1="92" y1="154" x2="122" y2="154" />
                                <line x1="95" y1="160" x2="116" y2="160" />
                                <line x1="94" y1="166" x2="110" y2="166" />
                                <line x1="96" y1="172" x2="105" y2="172" />

                                <!-- Continente Chino / Asiático (Derecha) -->
                                <line x1="210" y1="46" x2="236" y2="46" />
                                <line x1="252" y1="46" x2="262" y2="46" />
                                <line x1="178" y1="52" x2="188" y2="52" />
                                <line x1="196" y1="52" x2="294" y2="52" />
                                <line x1="168" y1="58" x2="310" y2="58" />
                                <line x1="160" y1="64" x2="318" y2="64" />
                                <line x1="158" y1="70" x2="306" y2="70" />
                                <line x1="313" y1="70" x2="319" y2="70" />
                                <line x1="152" y1="76" x2="298" y2="76" />
                                <line x1="150" y1="82" x2="292" y2="82" />
                                <line x1="148" y1="88" x2="288" y2="88" />
                                <line x1="296" y1="88" x2="302" y2="88" />
                                <line x1="154" y1="94" x2="294" y2="94" />
                                <line x1="160" y1="100" x2="286" y2="100" />
                                <line x1="166" y1="106" x2="282" y2="106" />
                                <line x1="170" y1="112" x2="278" y2="112" />
                                <line x1="172" y1="118" x2="272" y2="118" />
                                <line x1="176" y1="124" x2="264" y2="124" />
                                <line x1="174" y1="130" x2="216" y2="130" />
                                <line x1="248" y1="130" x2="278" y2="130" />
                                <line x1="178" y1="136" x2="212" y2="136" />
                                <line x1="256" y1="136" x2="284" y2="136" />
                                <line x1="182" y1="142" x2="206" y2="142" />
                                <line x1="264" y1="142" x2="290" y2="142" />
                                <line x1="184" y1="148" x2="202" y2="148" />
                                <line x1="268" y1="148" x2="296" y2="148" />
                                <line x1="188" y1="154" x2="198" y2="154" />
                                <line x1="262" y1="154" x2="298" y2="154" />
                                <line x1="266" y1="160" x2="294" y2="160" />
                                <line x1="272" y1="166" x2="288" y2="166" />
                                <line x1="280" y1="172" x2="286" y2="172" />
                            </g>

                            <!-- 3° LETRAS PPM INCLINADAS AL FRENTE -->
                            <g class="login-ppm-text">
                                <text x="176" y="138"
                                    text-anchor="middle"
                                    fill="#ffffff"
                                    stroke="#128327"
                                    stroke-width="7"
                                    stroke-linejoin="round"
                                    paint-order="stroke fill"
                                    font-family="Inter, 'Arial Black', sans-serif"
                                    font-weight="900"
                                    font-style="italic"
                                    font-size="92"
                                    letter-spacing="1">PPM</text>
                            </g>
                        </svg>
                    </div>

                    <h2 id="login-main-title" class="text-lg font-black text-slate-900 text-center mt-1">Sistema de Mantenimiento Industrial PPM</h2>
                    <p id="login-sub-title" class="text-xs font-bold text-emerald-700 text-center">Control y Gestión de Planta</p>
                </div>

                <!-- Formulario de Inicio de Sesión -->
                <form id="login-form" onsubmit="handleLogin(event)" class="space-y-4">
                    <div>
                        <label id="login-label-user" class="block text-xs font-bold text-slate-700 mb-1">
                            Usuario
                        </label>
                        <div class="relative">
                            <i class="fa-solid fa-user text-slate-400 absolute left-3.5 top-3 text-xs"></i>
                            <input type="text" id="login-user" required
                                class="w-full pl-9 pr-3.5 py-2.5 text-sm rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-emerald-500 font-medium"
                                placeholder="tecnico1 / 123">
                        </div>
                    </div>

                    <div>
                        <label id="login-label-pass" class="block text-xs font-bold text-slate-700 mb-1">
                            Contraseña
                        </label>
                        <div class="relative">
                            <i class="fa-solid fa-lock text-slate-400 absolute left-3.5 top-3 text-xs"></i>
                            <input type="password" id="login-pass" required
                                class="w-full pl-9 pr-3.5 py-2.5 text-sm rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-emerald-500 font-medium"
                                placeholder="••••••">
                        </div>
                    </div>

                    <div id="login-error" class="hidden p-2.5 rounded-xl bg-rose-50 border border-rose-200 text-rose-700 text-xs font-bold text-center">
                        Usuario o contraseña incorrectos
                    </div>

                    <button type="submit" class="touch-active w-full bg-emerald-600 hover:bg-emerald-700 text-white font-extrabold py-3 rounded-xl shadow-md text-sm flex items-center justify-center gap-2 transition">
                        <i class="fa-solid fa-right-to-bracket"></i>
                        <span id="login-btn-submit">Iniciar Sesión</span>
                    </button>
                </form>

                <!-- Enlace Gris para Reporte por Código QR (No Técnicos) -->
                <div class="pt-3 border-t border-slate-100 text-center">
                    <button type="button" onclick="openQrIdentification()" class="touch-active w-full py-2.5 px-3 rounded-xl hover:bg-slate-50 text-slate-500 hover:text-slate-700 transition flex flex-col items-center justify-center gap-0.5">
                        <span id="login-qr-link-text" class="text-sm font-extrabold underline decoration-slate-300 underline-offset-4">
                            ¿No eres técnico y quieres reportar un problema?
                        </span>
                    </button>
                </div>
            </div>
        </section>

        <!-- =====================================================
             2. PANTALLA DE IDENTIFICACIÓN QR (NO TÉCNICOS)
             ===================================================== -->
        <section id="screen-qr-id" class="hidden flex-1 flex flex-col justify-center p-6">
            <div class="bg-white rounded-3xl shadow-xl border border-slate-200 p-6 space-y-5">
                <div class="flex items-center justify-between border-b border-slate-100 pb-3">
                    <div class="flex items-center gap-2.5">
                        <div class="w-10 h-10 rounded-2xl bg-emerald-100 text-emerald-700 flex items-center justify-center text-lg font-bold">
                            <i class="fa-solid fa-qrcode"></i>
                        </div>
                        <div>
                            <h2 id="qr-title" class="text-base font-extrabold text-slate-900">Identificación de Planta</h2>
                        </div>
                    </div>
                    <button type="button" onclick="handleLogout()" class="text-slate-400 hover:text-slate-600 text-xs font-bold px-2.5 py-1.5 rounded-lg bg-slate-100">
                        <i class="fa-solid fa-arrow-left mr-1"></i> <span id="qr-btn-back">Volver</span>
                    </button>
                </div>

                <form id="qr-id-form" onsubmit="handleQrIdentifySubmit(event)" class="space-y-4">
                    <!-- Selección de Puesto -->
                    <div>
                        <label id="qr-label-position" class="block text-xs font-extrabold text-slate-700 mb-1.5 uppercase tracking-wide">
                            Puesto *
                        </label>
                        <select id="qr-position-select" required onchange="handleQrPositionChange()"
                            class="w-full rounded-xl border border-slate-300 px-3.5 py-2.5 text-sm font-bold text-slate-800 bg-slate-50 focus:bg-white focus:outline-none focus:ring-2 focus:ring-emerald-500">
                            <option value="" disabled selected id="qr-opt-placeholder">Selecciona tu puesto...</option>
                            <option value="SUPERVISOR" id="qr-opt-sup">SUPERVISOR</option>
                            <option value="GERENTE" id="qr-opt-mgr">GERENTE</option>
                            <option value="OPERADOR" id="qr-opt-op">OPERADOR</option>
                            <option value="OTRO" id="qr-opt-other">OTRO</option>
                        </select>
                    </div>

                    <!-- Cuadro adicional si elige OTRO -->
                    <div id="qr-other-container" class="hidden">
                        <input type="text" id="qr-other-input"
                            class="w-full rounded-xl border border-slate-300 px-3.5 py-2.5 text-sm font-medium text-slate-800 placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-emerald-500"
                            placeholder="Describe tu puesto">
                    </div>

                    <!-- ¿Cuál es tu nombre? -->
                    <div>
                        <label id="qr-label-name" class="block text-xs font-extrabold text-slate-700 mb-1.5 uppercase tracking-wide">
                            ¿Cuál es tu nombre? *
                        </label>
                        <input type="text" id="qr-name-input" required
                            class="w-full rounded-xl border border-slate-300 px-3.5 py-2.5 text-sm font-medium text-slate-800 placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-emerald-500"
                            placeholder="Escribe tu nombre completo">
                    </div>

                    <div id="qr-id-error" class="hidden p-2.5 rounded-xl bg-rose-50 border border-rose-200 text-rose-700 text-xs font-bold text-center">
                        Por favor completa tu puesto y tu nombre.
                    </div>

                    <button type="submit" class="touch-active w-full bg-emerald-600 hover:bg-emerald-700 text-white font-extrabold py-3.5 rounded-xl shadow-md text-sm flex items-center justify-center gap-2 transition">
                        <i class="fa-solid fa-id-card-clip"></i>
                        <span id="qr-btn-submit">Ya me he identificado</span>
                    </button>
                </form>
            </div>
        </section>

        <!-- =====================================================
             3. PANEL DE TÉCNICO E INVITADO QR
             ===================================================== -->
        <section id="screen-operator" class="hidden flex-1 p-4 space-y-5 pb-10">
            <!-- Tarjeta de Nuevo Reporte -->
            <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-4 space-y-4">
                <div class="flex items-center justify-between border-b border-slate-100 pb-3">
                    <div>
                        <h2 id="op-form-title" class="text-base font-extrabold text-slate-900">Levantar Reporte de Falla</h2>
                        <p id="op-form-subtitle" class="text-xs font-bold text-emerald-700">Registro de Mantenimiento en Planta</p>
                    </div>
                    <span id="operator-mode-pill" class="px-2.5 py-1 rounded-full text-[10px] font-extrabold bg-emerald-100 text-emerald-800">
                        TÉCNICO
                    </span>
                </div>

                <form id="ticket-form" onsubmit="handleFormSubmit(event)" class="space-y-3.5">
                    <!-- Punto 1: Fecha/Hora y Área (Área solo visible para Invitados QR) -->
                    <div id="row-datetime-area" class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                        <div>
                            <label id="label-field-datetime" class="block text-xs font-bold text-slate-700 mb-1">
                                1. Fecha y Hora *
                            </label>
                            <input type="datetime-local" id="field-datetime" required
                                class="w-full rounded-xl border border-slate-300 px-3 py-2 text-xs font-semibold text-slate-800 focus:outline-none focus:ring-2 focus:ring-emerald-500">
                        </div>

                        <div id="container-field-area">
                            <label id="label-field-area" class="block text-xs font-bold text-slate-700 mb-1">
                                Área o Línea *
                            </label>
                            <select id="field-area" required
                                class="w-full rounded-xl border border-slate-300 px-3 py-2 text-xs font-semibold text-slate-800 focus:outline-none focus:ring-2 focus:ring-emerald-500">
                                <option value="Apcom" id="opt-area-apcom">Apcom</option>
                                <option value="Ensamble" id="opt-area-ensamble">Ensamble</option>
                                <option value="Bosch" id="opt-area-bosch">Bosch</option>
                                <option value="CF motors" id="opt-area-cf">CF motors</option>
                                <option value="Pump Body" id="opt-area-pump">Pump Body</option>
                            </select>
                        </div>
                    </div>

                    <!-- Punto 2: Marca y Modelo -->
                    <div>
                        <label class="block text-xs font-bold text-slate-700 mb-1">
                            <span id="label-field-brand">2. Marca y Modelo</span> <span id="opt-label-2" class="text-slate-700 font-bold">*</span>
                        </label>
                        <input type="text" id="field-brand" required
                            class="w-full rounded-xl border border-slate-300 px-3 py-2 text-xs font-medium focus:outline-none focus:ring-2 focus:ring-emerald-500"
                            placeholder="Ej. Haitian MA1600 / Fanuc M-20iA">
                    </div>

                    <!-- Punto 3: Número de Serie -->
                    <div>
                        <label class="block text-xs font-bold text-slate-700 mb-1">
                            <span id="label-field-serial">3. Número de Serie</span> <span id="opt-label-3" class="text-slate-700 font-bold">*</span>
                        </label>
                        <input type="text" id="field-serial" required
                            class="w-full rounded-xl border border-slate-300 px-3 py-2 text-xs font-medium focus:outline-none focus:ring-2 focus:ring-emerald-500"
                            placeholder="Ej. SN-884920-A">
                    </div>

                    <!-- Punto 4: Tipo de Falla (Exclusivo para el Panel de Técnicos) -->
                    <div id="container-field-type">
                        <label id="label-field-type" class="block text-xs font-bold text-slate-700 mb-1">
                            4. Tipo de Falla *
                        </label>
                        <select id="field-type" required
                            class="w-full rounded-xl border border-slate-300 px-3 py-2 text-xs font-semibold text-slate-800 focus:outline-none focus:ring-2 focus:ring-emerald-500">
                            <option value="Eléctrica" id="opt-type-elec">Eléctrica</option>
                            <option value="Mecánica" id="opt-type-mech">Mecánica</option>
                            <option value="Hidráulica / Neumática" id="opt-type-hyd">Hidráulica / Neumática</option>
                            <option value="Sensores / PLC" id="opt-type-sens">Sensores / PLC</option>
                            <option value="Software / Robot" id="opt-type-soft">Software / Robot</option>
                            <option value="Otra falla" id="opt-type-other">Otra falla</option>
                        </select>
                    </div>

                    <!-- Descripción del Problema -->
                    <div>
                        <p id="label-problem-question" class="text-xs font-extrabold text-emerald-700 mb-0.5">
                            Problema (¿Por qué paró la línea?)
                        </p>
                        <label class="block text-xs font-bold text-slate-700 mb-1">
                            <span id="label-field-problem">Descripción del Problema</span> <span id="label-optional-tag" class="text-slate-400 font-normal">(Opcional)</span>
                        </label>
                        <textarea id="field-problem" rows="3"
                            class="w-full rounded-xl border border-slate-300 px-3 py-2 text-xs font-medium focus:outline-none focus:ring-2 focus:ring-emerald-500"
                            placeholder="Describe el problema..."></textarea>
                        <p class="text-[10px] font-semibold text-indigo-600 mt-1 flex items-center gap-1">
                            <i class="fa-solid fa-wand-magic-sparkles"></i>
                            <span id="label-ai-hint">IA activa: Los comentarios escritos en chino se interpretan automáticamente al español.</span>
                        </p>
                    </div>

                    <button type="submit" id="btn-submit-ticket"
                        class="touch-active w-full bg-emerald-600 hover:bg-emerald-700 text-white font-extrabold py-3 px-4 rounded-xl shadow-md text-xs flex items-center justify-center gap-2 transition">
                        <i class="fa-solid fa-paper-plane"></i>
                        <span id="btn-submit-ticket-text">Reportar Problema</span>
                    </button>
                </form>
            </div>

            <!-- Apartado de Problemas Activos en Planta (Visible para Técnicos, oculto para Invitado QR) -->
            <div id="operator-active-section" class="space-y-3">
                <div class="flex items-center justify-between px-1">
                    <div>
                        <h3 class="text-sm font-extrabold text-slate-800 flex items-center gap-1.5">
                            <i class="fa-solid fa-triangle-exclamation text-amber-500"></i>
                            <span id="op-active-title">Problemas activos en la planta</span>
                        </h3>
                        <p id="op-active-subtitle" class="text-[11px] text-slate-500 font-medium">
                            No olvides indicar cuando el problema ya se haya resuelto
                        </p>
                    </div>
                    <span id="operator-active-count" class="px-2.5 py-0.5 rounded-full text-xs font-extrabold bg-amber-100 text-amber-800">
                        0
                    </span>
                </div>

                <div id="operator-tickets-list" class="space-y-2.5"></div>
            </div>
        </section>

        <!-- =====================================================
             4. PANEL DE ADMINISTRADOR (FORMATO ESCRITORIO DE PC)
             ===================================================== -->
        <section id="screen-admin" class="hidden flex-1 p-4 md:p-6 space-y-6">
            <!-- Resumen de KPIs Superiores -->
            <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                <div class="bg-white p-4 rounded-2xl border border-slate-200 shadow-sm flex items-center justify-between">
                    <div>
                        <p id="kpi-title-total" class="text-xs font-bold text-slate-400 uppercase">Total del Periodo</p>
                        <p id="admin-kpi-total" class="text-2xl font-black text-slate-900 mt-0.5">0</p>
                        <p id="admin-kpi-period-label" class="text-[11px] font-semibold text-slate-500 mt-0.5">Mes actual</p>
                    </div>
                    <div class="w-12 h-12 rounded-2xl bg-slate-100 text-slate-700 flex items-center justify-center text-xl">
                        <i class="fa-solid fa-clipboard-list"></i>
                    </div>
                </div>

                <div class="bg-white p-4 rounded-2xl border border-amber-200 shadow-sm flex items-center justify-between">
                    <div>
                        <p id="kpi-title-open" class="text-xs font-bold text-amber-600 uppercase">Problemas Abiertos</p>
                        <p id="admin-kpi-open" class="text-2xl font-black text-amber-600 mt-0.5">0</p>
                        <p id="kpi-sub-open" class="text-[11px] font-semibold text-slate-500 mt-0.5">Técnicos + Invitados QR</p>
                    </div>
                    <div class="w-12 h-12 rounded-2xl bg-amber-100 text-amber-600 flex items-center justify-center text-xl">
                        <i class="fa-solid fa-screwdriver-wrench"></i>
                    </div>
                </div>

                <div class="bg-white p-4 rounded-2xl border border-emerald-200 shadow-sm flex items-center justify-between">
                    <div>
                        <p id="kpi-title-resolved" class="text-xs font-bold text-emerald-600 uppercase">Problemas Resueltos</p>
                        <p id="admin-kpi-resolved" class="text-2xl font-black text-emerald-600 mt-0.5">0</p>
                        <p id="kpi-sub-resolved" class="text-[11px] font-semibold text-slate-500 mt-0.5">Con hora de cierre registrada</p>
                    </div>
                    <div class="w-12 h-12 rounded-2xl bg-emerald-100 text-emerald-600 flex items-center justify-center text-xl">
                        <i class="fa-solid fa-circle-check"></i>
                    </div>
                </div>
            </div>

            <!-- Estructura de Escritorio PC: 12 Columnas (4 Cols Calendario / 8 Cols Detalle de Tickets) -->
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-start">

                <!-- COLUMNA IZQUIERDA (4 cols): Calendario Filtro de Mes y Año -->
                <div class="lg:col-span-4 bg-white rounded-2xl border border-slate-200 shadow-sm p-5 space-y-4">
                    <div class="flex items-center justify-between border-b border-slate-100 pb-3">
                        <div>
                            <h3 class="text-sm font-extrabold text-slate-900 flex items-center gap-1.5">
                                <i class="fa-regular fa-calendar-days text-emerald-600"></i>
                                <span id="admin-cal-title">Calendario de Fallas</span>
                            </h3>
                            <p id="admin-cal-subtitle" class="text-[11px] text-slate-500 font-medium">Filtra fallas por mes, año o día específico</p>
                        </div>
                        <button type="button" id="btn-admin-new-ticket" onclick="openTechnicianViewFromAdmin()" class="text-[11px] font-bold text-emerald-700 bg-emerald-50 hover:bg-emerald-100 px-2.5 py-1.5 rounded-xl transition">
                            + Nuevo Ticket
                        </button>
                    </div>

                    <!-- Selectores de Mes y Año -->
                    <div class="flex items-center justify-between gap-2">
                        <button type="button" onclick="changeCalendarMonth(-1)" class="p-2 rounded-xl bg-slate-100 hover:bg-slate-200 text-slate-700 text-xs font-bold">
                            <i class="fa-solid fa-chevron-left"></i>
                        </button>

                        <div class="flex items-center gap-1.5 flex-1 justify-center">
                            <select id="admin-cal-month" onchange="handleMonthYearSelect()"
                                class="rounded-xl border border-slate-300 px-2.5 py-1.5 text-xs font-extrabold text-slate-800 bg-slate-50 focus:outline-none focus:ring-2 focus:ring-emerald-500">
                                <option value="0">Enero</option>
                                <option value="1">Febrero</option>
                                <option value="2">Marzo</option>
                                <option value="3">Abril</option>
                                <option value="4">Mayo</option>
                                <option value="5">Junio</option>
                                <option value="6">Julio</option>
                                <option value="7">Agosto</option>
                                <option value="8">Septiembre</option>
                                <option value="9">Octubre</option>
                                <option value="10">Noviembre</option>
                                <option value="11">Diciembre</option>
                            </select>

                            <select id="admin-cal-year" onchange="handleMonthYearSelect()"
                                class="rounded-xl border border-slate-300 px-2.5 py-1.5 text-xs font-extrabold text-slate-800 bg-slate-50 focus:outline-none focus:ring-2 focus:ring-emerald-500">
                                <option value="2024">2024</option>
                                <option value="2025">2025</option>
                                <option value="2026">2026</option>
                                <option value="2027">2027</option>
                            </select>
                        </div>

                        <button type="button" onclick="changeCalendarMonth(1)" class="p-2 rounded-xl bg-slate-100 hover:bg-slate-200 text-slate-700 text-xs font-bold">
                            <i class="fa-solid fa-chevron-right"></i>
                        </button>
                    </div>

                    <!-- Cabecera de días de la semana -->
                    <div id="admin-cal-weekdays" class="grid grid-cols-7 gap-1 text-center text-[10px] font-extrabold text-slate-400 uppercase pt-1">
                        <div>Dom</div>
                        <div>Lun</div>
                        <div>Mar</div>
                        <div>Mié</div>
                        <div>Jue</div>
                        <div>Vie</div>
                        <div>Sáb</div>
                    </div>

                    <!-- Cuadrícula de días del mes -->
                    <div id="admin-calendar-grid" class="grid grid-cols-7 gap-1.5 text-center"></div>

                    <!-- Leyenda y botón para ver todo el mes -->
                    <div class="pt-2 border-t border-slate-100 flex flex-wrap items-center justify-between gap-2">
                        <div class="flex items-center gap-3 text-[11px] font-semibold text-slate-600">
                            <span class="flex items-center gap-1">
                                <span class="w-2.5 h-2.5 rounded-full bg-amber-500 inline-block"></span> <span id="legend-open">Abierto</span>
                            </span>
                            <span class="flex items-center gap-1">
                                <span class="w-2.5 h-2.5 rounded-full bg-emerald-500 inline-block"></span> <span id="legend-resolved">Resuelto</span>
                            </span>
                        </div>

                        <button type="button" id="btn-clear-day-filter" onclick="clearCalendarDayFilter()"
                            class="text-[11px] font-bold text-blue-600 hover:text-blue-800 underline">
                            Ver todo el mes completo
                        </button>
                    </div>

                    <!-- Apartado de Exportación a Excel (Día seleccionado o Mes completo) -->
                    <div class="pt-3 border-t border-slate-100 space-y-2">
                        <div class="flex items-center justify-between">
                            <span class="text-[11px] font-extrabold text-slate-700 flex items-center gap-1.5">
                                <i class="fa-solid fa-file-excel text-emerald-600"></i>
                                <span id="admin-excel-title">Exportar a Excel</span>
                            </span>
                            <span id="excel-export-scope-badge" class="text-[10px] font-bold px-2 py-0.5 rounded-full bg-emerald-50 text-emerald-700">
                                Mes completo
                            </span>
                        </div>

                        <div>
                            <button type="button" onclick="exportTicketsToExcel('SELECTED')"
                                class="touch-active w-full py-2.5 px-3 rounded-xl bg-emerald-600 hover:bg-emerald-700 text-white font-extrabold text-xs shadow-sm flex items-center justify-center gap-1.5 transition">
                                <i class="fa-solid fa-download"></i>
                                <span id="btn-excel-selected-label">Descargar Vista</span>
                            </button>
                        </div>
                    </div>

                    <!-- Apartado de Gestión de Usuarios y Contraseñas -->
                    <div class="pt-4 border-t border-slate-200 space-y-3">
                        <div class="flex items-center justify-between">
                            <div>
                                <h4 class="text-xs font-extrabold text-slate-900 flex items-center gap-1.5">
                                    <i class="fa-solid fa-users-gear text-blue-600"></i>
                                    <span id="admin-users-title">Usuarios y Contraseñas</span>
                                </h4>
                                <p id="admin-users-subtitle" class="text-[10px] text-slate-500 font-medium">Agregar, consultar o eliminar cuentas</p>
                            </div>
                            <span id="admin-users-count-badge" class="text-[10px] font-extrabold px-2 py-0.5 rounded-full bg-blue-50 text-blue-700">
                                0 cuentas
                            </span>
                        </div>

                        <!-- Formulario para Agregar o Actualizar Cuenta -->
                        <form id="admin-user-form" onsubmit="handleSaveUserAccount(event)" class="bg-slate-50 p-3 rounded-xl border border-slate-200/80 space-y-2.5">
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-2">
                                <div>
                                    <label id="label-acc-user" class="block text-[10px] font-extrabold text-slate-600 uppercase mb-0.5">
                                        Usuario *
                                    </label>
                                    <input type="text" id="new-account-username" required
                                        class="w-full rounded-lg border border-slate-300 px-2.5 py-1.5 text-xs font-bold text-slate-800 focus:outline-none focus:ring-2 focus:ring-blue-500"
                                        placeholder="ej. tecnico3">
                                </div>
                                <div>
                                    <label id="label-acc-pass" class="block text-[10px] font-extrabold text-slate-600 uppercase mb-0.5">
                                        Contraseña *
                                    </label>
                                    <input type="text" id="new-account-pass" required
                                        class="w-full rounded-lg border border-slate-300 px-2.5 py-1.5 text-xs font-bold text-slate-800 focus:outline-none focus:ring-2 focus:ring-blue-500"
                                        placeholder="ej. 1234">
                                </div>
                            </div>

                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-2">
                                <div>
                                    <label id="label-acc-name" class="block text-[10px] font-extrabold text-slate-600 uppercase mb-0.5">
                                        Nombre Visible *
                                    </label>
                                    <input type="text" id="new-account-name" required
                                        class="w-full rounded-lg border border-slate-300 px-2.5 py-1.5 text-xs font-medium text-slate-800 focus:outline-none focus:ring-2 focus:ring-blue-500"
                                        placeholder="ej. Luis Pérez">
                                </div>
                                <div>
                                    <label id="label-acc-role" class="block text-[10px] font-extrabold text-slate-600 uppercase mb-0.5">
                                        Rol *
                                    </label>
                                    <select id="new-account-role"
                                        class="w-full rounded-lg border border-slate-300 px-2.5 py-1.5 text-xs font-bold text-slate-800 bg-white focus:outline-none focus:ring-2 focus:ring-blue-500">
                                        <option value="OPERATOR" id="opt-role-tech">Técnico</option>
                                        <option value="ADMIN" id="opt-role-admin">Administrador</option>
                                    </select>
                                </div>
                            </div>

                            <div id="admin-user-feedback" class="hidden text-[11px] font-bold px-2.5 py-1.5 rounded-lg text-center"></div>

                            <button type="submit"
                                class="touch-active w-full py-2 px-3 rounded-xl bg-blue-600 hover:bg-blue-700 text-white font-extrabold text-xs shadow-sm flex items-center justify-center gap-1.5 transition">
                                <i class="fa-solid fa-user-plus"></i>
                                <span id="btn-acc-save">Agregar o Guardar Cuenta</span>
                            </button>
                        </form>

                        <!-- Lista de Cuentas Activas con Usuario, Contraseña y Botón Eliminar -->
                        <div id="admin-users-list" class="space-y-2 max-h-64 overflow-y-auto pr-0.5"></div>
                    </div>

                    <!-- Apartado de Código QR de Planta y Conexión Firebase en la Nube -->
                    <div class="pt-4 border-t border-slate-200 space-y-3">
                        <div class="flex items-center justify-between">
                            <div>
                                <h4 class="text-xs font-extrabold text-slate-900 flex items-center gap-1.5">
                                    <i class="fa-solid fa-qrcode text-emerald-600"></i>
                                    <span>QR de Planta y Nube Firebase</span>
                                </h4>
                                <p class="text-[10px] text-slate-500 font-medium">Sincronización en tiempo real entre celulares y PC</p>
                            </div>
                            <button type="button" onclick="openFirebaseConfigModal()" class="text-[10px] font-extrabold px-2.5 py-1 rounded-lg bg-slate-800 hover:bg-slate-900 text-white transition">
                                <i class="fa-solid fa-cloud mr-1"></i>Configurar Firebase
                            </button>
                        </div>

                        <div class="bg-slate-50 p-3 rounded-xl border border-slate-200 text-center space-y-2">
                            <p class="text-[10px] font-bold text-slate-600">
                                Pega aquí el link de tu página web publicada para generar el QR oficial de la planta:
                            </p>
                            <input type="url" id="qr-custom-url-input" oninput="updatePlantQrCode()"
                                class="w-full rounded-lg border border-slate-300 px-2.5 py-1.5 text-[11px] font-semibold text-slate-800 focus:outline-none focus:ring-2 focus:ring-emerald-500"
                                placeholder="https://tu-proyecto.web.app">
                            <div class="bg-white p-3 rounded-xl border border-slate-200 inline-block mx-auto shadow-sm">
                                <img id="plant-qr-image" alt="Código QR Planta PPM" class="w-36 h-36 mx-auto"
                                    src="https://api.qrserver.com/v1/create-qr-code/?size=220x220&data=https://ejemplo.web.app/?qr=1"
                                    onerror="this.src='https://placehold.co/220x220/ffffff/0f172a?text=QR+Planta'">
                            </div>
                            <p id="plant-qr-target-label" class="text-[10px] font-mono text-slate-500 break-all"></p>
                            <button type="button" onclick="printPlantQrPoster()"
                                class="touch-active w-full py-2 px-3 rounded-xl bg-emerald-600 hover:bg-emerald-700 text-white font-extrabold text-xs shadow-sm flex items-center justify-center gap-1.5 transition">
                                <i class="fa-solid fa-print"></i>
                                <span>Imprimir Cartel QR para Planta</span>
                            </button>
                        </div>
                    </div>
                </div>

                <!-- COLUMNA DERECHA (8 cols): Apartado Detallado de Problemas Abiertos y Resueltos -->
                <div class="lg:col-span-8 space-y-4">
                    <!-- Barra de Pestañas (Todos / Problemas Abiertos / Problemas Resueltos), Buscador y Botón Rápido Excel -->
                    <div class="bg-white rounded-2xl border border-slate-200 shadow-sm p-4 flex flex-col sm:flex-row items-stretch sm:items-center justify-between gap-3">
                        <div class="flex flex-wrap items-center gap-1.5 bg-slate-100 p-1 rounded-xl">
                            <button type="button" id="tab-btn-ALL" onclick="setAdminTab('ALL')"
                                class="px-3 py-2 rounded-lg text-xs font-extrabold transition bg-white text-slate-900 shadow-sm">
                                Todos
                            </button>
                            <button type="button" id="tab-btn-ABIERTO" onclick="setAdminTab('ABIERTO')"
                                class="px-3 py-2 rounded-lg text-xs font-extrabold transition text-slate-600 hover:text-slate-900">
                                <i class="fa-solid fa-circle-exclamation text-amber-500 mr-1"></i><span id="tab-label-open">Abiertos</span>
                            </button>
                            <button type="button" id="tab-btn-RESUELTO" onclick="setAdminTab('RESUELTO')"
                                class="px-3 py-2 rounded-lg text-xs font-extrabold transition text-slate-600 hover:text-slate-900">
                                <i class="fa-solid fa-circle-check text-emerald-600 mr-1"></i><span id="tab-label-resolved">Resueltos</span>
                            </button>
                        </div>

                        <div class="flex items-center gap-2 flex-1 max-w-md">
                            <div class="relative flex-1">
                                <i class="fa-solid fa-magnifying-glass text-slate-400 absolute left-3 top-2.5 text-xs"></i>
                                <input type="text" id="admin-search-input" oninput="renderAdminDashboard()"
                                    class="w-full pl-8 pr-3 py-1.5 text-xs rounded-xl border border-slate-300 focus:outline-none focus:ring-2 focus:ring-emerald-500"
                                    placeholder="Buscar área, ID, reportante o falla...">
                            </div>

                            <button type="button" onclick="exportTicketsToExcel('SELECTED')"
                                class="touch-active shrink-0 bg-emerald-600 hover:bg-emerald-700 text-white text-xs font-extrabold px-3 py-1.5 rounded-xl shadow-sm flex items-center gap-1.5 transition">
                                <i class="fa-solid fa-file-excel"></i>
                                <span id="btn-top-excel">Excel</span>
                            </button>
                        </div>
                    </div>

                    <!-- Listado Detallado de Tickets -->
                    <div id="admin-tickets-container" class="space-y-3.5"></div>
                </div>
            </div>
        </section>
    </div>

    <!-- =====================================================
         MODAL DE CONFIRMACIÓN DE ÉXITO AL ENVIAR REPORTE
         ===================================================== -->
    <div id="modal-report-success" class="hidden fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-sm flex items-center justify-center p-4">
        <div class="bg-white rounded-3xl max-w-sm w-full p-6 shadow-2xl border border-slate-200 text-center space-y-4">
            <div class="w-16 h-16 rounded-full bg-emerald-100 text-emerald-600 mx-auto flex items-center justify-center text-3xl shadow-inner">
                <i class="fa-solid fa-check"></i>
            </div>

            <div class="space-y-1">
                <h3 id="success-modal-title" class="text-base font-black text-slate-900">Reporte Enviado</h3>
                <p id="success-modal-message" class="text-sm font-bold text-slate-700 leading-snug">
                    Gracias, se ha enviado tu reporte con éxito
                </p>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 gap-2.5 pt-2">
                <button type="button" onclick="handleLogout()"
                    class="touch-active w-full py-2.5 px-4 rounded-xl border border-slate-300 bg-slate-100 hover:bg-slate-200 text-slate-700 font-extrabold text-xs transition">
                    <span id="btn-modal-exit">Salir</span>
                </button>
                <button type="button" onclick="handleReportAnother()"
                    class="touch-active w-full py-2.5 px-4 rounded-xl bg-emerald-600 hover:bg-emerald-700 text-white font-extrabold text-xs shadow-md transition">
                    <span id="btn-modal-another">Reportar otro problema</span>
                </button>
            </div>
        </div>
    </div>

    <!-- =====================================================
         MODAL PARA CERRAR / RESOLVER PROBLEMA (TÉCNICOS Y ADMIN)
         ===================================================== -->
    <div id="modal-resolve-ticket" class="hidden fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-sm flex items-center justify-center p-4">
        <div class="bg-white rounded-2xl max-w-md w-full p-5 shadow-2xl border border-slate-200 space-y-4">
            <div class="flex items-center justify-between border-b border-slate-100 pb-3">
                <div>
                    <h3 id="resolve-modal-title" class="text-sm font-extrabold text-slate-800">Cerrar Problema</h3>
                    <p id="resolve-modal-subtitle" class="text-xs text-slate-500 font-semibold"></p>
                </div>
                <button type="button" onclick="closeResolutionModal()" class="text-slate-400 hover:text-slate-600 p-1">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>

            <!-- Frase motivacional en el idioma elegido -->
            <div class="bg-emerald-50 border border-emerald-200/80 rounded-xl p-2.5 flex items-center gap-2.5">
                <div class="w-8 h-8 rounded-lg bg-emerald-100 text-emerald-700 flex items-center justify-center shrink-0">
                    <i class="fa-solid fa-lightbulb"></i>
                </div>
                <div>
                    <p id="resolve-motivational-quote" class="text-xs font-extrabold text-emerald-900 italic">“De los errores se aprende”</p>
                </div>
            </div>

            <input type="hidden" id="resolve-ticket-id">
            <div class="space-y-3">
                <div>
                    <label id="label-resolve-what-done" class="block text-xs font-bold text-slate-700 mb-1">
                        ¿Qué se hizo para solucionar el problema? *
                    </label>
                    <textarea id="resolve-what-done" rows="3" required
                        class="w-full rounded-xl border border-slate-300 px-3 py-2 text-xs focus:outline-none focus:ring-2 focus:ring-emerald-500"
                        placeholder="Describe la acción correctiva realizada..."></textarea>
                </div>
                <div>
                    <label id="label-resolve-lesson" class="block text-xs font-bold text-slate-700 mb-1">
                        Lección aprendida y mejora preventiva *
                    </label>
                    <textarea id="resolve-lesson" rows="2" required
                        class="w-full rounded-xl border border-slate-300 px-3 py-2 text-xs focus:outline-none focus:ring-2 focus:ring-emerald-500"
                        placeholder="Acción preventiva para evitar que vuelva a ocurrir..."></textarea>
                </div>
                <div id="resolve-error-msg" class="hidden p-2.5 rounded-xl bg-rose-50 border border-rose-200 text-rose-700 text-xs font-bold text-center">
                    Por favor llena ambas casillas obligatorias para cerrar el problema.
                </div>
            </div>
            <div class="flex justify-end gap-2 pt-2">
                <button type="button" onclick="closeResolutionModal()"
                    class="px-4 py-2 rounded-xl text-xs font-bold text-slate-600 bg-slate-100 hover:bg-slate-200">
                    <span id="btn-resolve-cancel">Cancelar</span>
                </button>
                <button type="button" onclick="confirmResolveTicket()"
                    class="px-4 py-2 rounded-xl text-xs font-bold text-white bg-emerald-600 hover:bg-emerald-700 shadow-sm flex items-center gap-1">
                    <i class="fa-solid fa-check"></i>
                    <span id="btn-resolve-confirm">Confirmar Cierre</span>
                </button>
            </div>
        </div>
    </div>

    <!-- =====================================================
         MODAL DE DETALLES COMPLETOS DEL TICKET
         ===================================================== -->
    <div id="modal-ticket-detail" class="hidden fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-sm flex items-center justify-center p-4">
        <div class="bg-white rounded-2xl max-w-md w-full p-5 shadow-2xl border border-slate-200 space-y-3">
            <div class="flex items-center justify-between border-b border-slate-100 pb-2.5">
                <h3 id="detail-modal-title" class="text-sm font-extrabold text-slate-800"></h3>
                <button type="button" onclick="closeDetailModal()" class="text-slate-400 hover:text-slate-600 p-1">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>
            <div id="detail-modal-body" class="space-y-2.5 text-xs text-slate-700"></div>
            <div class="pt-2 flex justify-end">
                <button type="button" onclick="closeDetailModal()" class="px-4 py-2 bg-slate-800 text-white font-bold text-xs rounded-xl">
                    <span id="btn-detail-close">Cerrar</span>
                </button>
            </div>
        </div>
    </div>

    <!-- =====================================================
         MODAL PARA PEGAR TU PROPIA CONFIGURACIÓN DE FIREBASE
         ===================================================== -->
    <div id="modal-firebase-config" class="hidden fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-sm flex items-center justify-center p-4">
        <div class="bg-white rounded-2xl max-w-lg w-full p-5 shadow-2xl border border-slate-200 space-y-4">
            <div class="flex items-center justify-between border-b border-slate-100 pb-2.5">
                <div class="flex items-center gap-2">
                    <div class="w-8 h-8 rounded-lg bg-amber-100 text-amber-600 flex items-center justify-center font-bold">
                        <i class="fa-solid fa-fire"></i>
                    </div>
                    <div>
                        <h3 class="text-sm font-extrabold text-slate-900">Conectar tu cuenta de Firebase</h3>
                        <p class="text-[11px] text-slate-500 font-medium">Base de datos Firestore en tiempo real para todos los equipos</p>
                    </div>
                </div>
                <button type="button" onclick="closeFirebaseConfigModal()" class="text-slate-400 hover:text-slate-600 p-1">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>

            <div class="bg-blue-50 border border-blue-200 rounded-xl p-3 text-[11px] text-blue-900 space-y-1">
                <p class="font-extrabold"><i class="fa-solid fa-circle-info mr-1"></i>¿Dónde encuentro esto en mi cuenta de Firebase?</p>
                <p>1. Entra a <strong>console.firebase.google.com</strong> y abre tu proyecto.</p>
                <p>2. En el menú izquierdo entra a <strong>Compilación &rarr; Firestore Database</strong>, dale a <strong>Crear base de datos</strong> y elige <strong>Modo de prueba (Test Mode)</strong>.</p>
                <p>3. En el menú izquierdo entra a <strong>Compilación &rarr; Authentication &rarr; Método de acceso</strong> y activa <strong>Anónimo (Anonymous)</strong>.</p>
                <p>4. Haz clic en el engrane ⚙️ (Configuración del proyecto), baja a <strong>Tus apps</strong>, elige el ícono Web <code>&lt;/&gt;</code> y pega aquí abajo el bloque <code>firebaseConfig</code>:</p>
            </div>

            <div>
                <label class="block text-xs font-extrabold text-slate-700 mb-1">
                    Objeto JSON o bloque firebaseConfig de tu proyecto:
                </label>
                <textarea id="firebase-config-textarea" rows="6"
                    class="w-full rounded-xl border border-slate-300 px-3 py-2 text-xs font-mono text-slate-800 focus:outline-none focus:ring-2 focus:ring-emerald-500"
                    placeholder='{"apiKey": "AIzaSy...", "authDomain": "tu-app.firebaseapp.com", "projectId": "tu-app", "storageBucket": "...", "messagingSenderId": "...", "appId": "..."}'></textarea>
                <p id="firebase-config-feedback" class="hidden text-xs font-bold mt-1.5 p-2 rounded-lg text-center"></p>
            </div>

            <div class="flex justify-end gap-2 pt-1">
                <button type="button" onclick="closeFirebaseConfigModal()" class="px-4 py-2 rounded-xl text-xs font-bold text-slate-600 bg-slate-100 hover:bg-slate-200">
                    Cancelar
                </button>
                <button type="button" onclick="saveCustomFirebaseConfig()" class="px-4 py-2 rounded-xl text-xs font-extrabold text-white bg-emerald-600 hover:bg-emerald-700 shadow-sm">
                    Guardar y Conectar Nube
                </button>
            </div>
        </div>
    </div>

    <!-- =====================================================
         LÓGICA JAVASCRIPT GLOBAL Y UNIFICADA (ES / EN / ZH)
         ===================================================== -->
    <script>
        const STORAGE_KEY = 'ppm_bilingual_tickets_v3';
        const USERS_STORAGE_KEY = 'ppm_bilingual_users_v1';
        const LANG_STORAGE_KEY = 'ppm_selected_lang_v1';
        const CUSTOM_FB_CONFIG_KEY = 'ppm_custom_firebase_config_v1';
        const CUSTOM_QR_URL_KEY = 'ppm_custom_qr_url_v1';

        // =========================================================================
        // SI VAS A SUBIR ESTE ARCHIVO (COMO index.html) A INTERNET, PUEDES PEGAR
        // TUS DATOS DE FIREBASE DIRECTAMENTE AQUÍ ABAJO PARA QUE TODOS LOS CELULARES
        // Y COMPUTADORAS SE CONECTEN AUTOMÁTICAMENTE A LA MISMA NUBE:
        // =========================================================================
        const HARDCODED_FIREBASE_CONFIG = null;
        /* Ejemplo de cómo pegarlo si lo editas en el código:
        const HARDCODED_FIREBASE_CONFIG = {
            apiKey: "TU_API_KEY",
            authDomain: "tu-proyecto.firebaseapp.com",
            projectId: "tu-proyecto",
            storageBucket: "tu-proyecto.firebasestorage.app",
            messagingSenderId: "123456789",
            appId: "1:123456789:web:abcdef"
        };
        */

        let currentLang = 'es'; // 'es' | 'en' | 'zh'

        // Diccionario completo por idioma (Español, Inglés y Chino)
        const I18N = {
            es: {
                code: 'ES',
                headerTitle: 'Sistema de Mantenimiento',
                headerSubtitle: 'Planta Industrial PPM',
                logout: 'Salir',
                changeLang: 'Cambiar idioma',
                loginMainTitle: 'Sistema de Mantenimiento Industrial PPM',
                loginSubTitle: 'Control y Gestión de Planta',
                loginUser: 'Usuario',
                loginPass: 'Contraseña',
                loginError: 'Usuario o contraseña incorrectos',
                loginSubmit: 'Iniciar Sesión',
                loginQrLink: '¿No eres técnico y quieres reportar un problema?',
                loginDemoTitle: 'Accesos Rápidos Demo',
                demoTech: 'Técnico (tecnico1)',
                demoAdmin: 'Admin PC (admin)',
                qrTitle: 'Identificación de Planta',
                qrBack: 'Volver',
                qrPositionLabel: 'Puesto *',
                qrOptPlaceholder: 'Selecciona tu puesto...',
                qrOptSup: 'SUPERVISOR',
                qrOptMgr: 'GERENTE',
                qrOptOp: 'OPERADOR',
                qrOptOther: 'OTRO',
                qrOtherPlaceholder: 'Describe tu puesto',
                qrNameLabel: '¿Cuál es tu nombre? *',
                qrNamePlaceholder: 'Escribe tu nombre completo',
                qrError: 'Por favor completa tu puesto y tu nombre.',
                qrSubmit: 'Ya me he identificado',
                opFormTitle: 'Levantar Reporte de Falla',
                opFormSubtitle: 'Registro de Mantenimiento en Planta',
                pillTech: 'TÉCNICO',
                pillQr: 'REPORTE QR PLANTA',
                fieldDatetime: '1. Fecha y Hora *',
                fieldArea: 'Área o Línea *',
                areaApcom: 'Apcom',
                areaEnsamble: 'Ensamble',
                areaBosch: 'Bosch',
                areaCf: 'CF motors',
                areaPump: 'Pump Body (Cuerpo de Bomba)',
                fieldBrand: '2. Marca y Modelo',
                brandPlaceholder: 'Ej. Haitian MA1600 / Fanuc M-20iA',
                fieldSerial: '3. Número de Serie',
                serialPlaceholder: 'Ej. SN-884920-A',
                fieldType: '4. Tipo de Falla *',
                typeElec: 'Eléctrica',
                typeMech: 'Mecánica',
                typeHyd: 'Hidráulica / Neumática',
                typeSens: 'Sensores / PLC',
                typeSoft: 'Software / Robot',
                typeOther: 'Otra falla',
                questionTech: 'Problema (¿Por qué paró la línea?)',
                questionQr: '¿Qué fue lo que pasó?',
                fieldProblem: 'Descripción del Problema',
                optionalTag: '(Opcional)',
                problemPlaceholder: 'Describe el problema...',
                aiHint: 'IA activa: Los comentarios escritos en chino se interpretan automáticamente al español.',
                submitTicket: 'Reportar Problema',
                analyzingBtn: 'Analizando reporte...',
                opActiveTitle: 'Problemas activos en la planta',
                opActiveSubtitle: 'No olvides indicar cuando el problema ya se haya resuelto',
                noActiveTickets: 'Sin fallas pendientes en planta',
                statusOpen: 'ABIERTO',
                statusResolved: 'RESUELTO',
                reportedBy: 'Reportado por',
                equipmentLabel: 'Equipo',
                serialShort: 'Serie',
                originalDescLabel: 'Descripción del Problema:',
                aiSpanishTranslationLabel: 'Interpretación IA (Chino → Español):',
                reanalyzeBtn: 'Re-interpretar con IA',
                reanalyzingBtn: 'Analizando...',
                detailsBtn: 'Detalles',
                viewSheetBtn: 'Ver Ficha',
                resolvedBtn: 'Problema resuelto',
                qrPlantTag: 'Reporte de Planta (QR)',
                noDescription: 'Sin descripción',
                kpiTotal: 'Total del Periodo',
                kpiOpen: 'Problemas Abiertos',
                kpiOpenSub: 'Técnicos + Invitados QR',
                kpiResolved: 'Problemas Resueltos',
                kpiResolvedSub: 'Con hora de cierre registrada',
                calTitle: 'Calendario de Fallas',
                calSubtitle: 'Filtra fallas por mes, año o día específico',
                newTicketBtn: '+ Nuevo Ticket',
                months: ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre'],
                weekdays: ['Dom', 'Lun', 'Mar', 'Mié', 'Jue', 'Vie', 'Sáb'],
                legendOpen: 'Abierto',
                legendResolved: 'Resuelto',
                clearDayFilter: 'Ver todo el mes completo',
                excelTitle: 'Exportar a Excel',
                excelScopeDay: 'Día',
                excelScopeMonth: 'Mes',
                excelBtnDay: 'Descargar Día',
                excelBtnMonth: 'Descargar Mes Actual',
                usersTitle: 'Usuarios y Contraseñas',
                usersSubtitle: 'Agregar, consultar o eliminar cuentas',
                accCountSingular: 'cuenta',
                accCountPlural: 'cuentas',
                accUser: 'Usuario *',
                accPass: 'Contraseña *',
                accName: 'Nombre Visible *',
                accRole: 'Rol *',
                roleTech: 'Técnico',
                roleAdmin: 'Administrador',
                accSaveBtn: 'Agregar o Guardar Cuenta',
                passLabel: 'Clave',
                tabAll: 'Todos',
                tabOpen: 'Abiertos',
                tabResolved: 'Resueltos',
                searchPlaceholder: 'Buscar área, ID, reportante o falla...',
                noFilteredTickets: 'No hay reportes en este filtro',
                noFilteredSub: 'Prueba seleccionando otro mes en el calendario o cambiando de pestaña.',
                closeTimeLabel: 'Hora de Cierre',
                whatWasDoneLabel: '¿Qué se hizo para solucionar el problema?',
                lessonLearnedLabel: 'Lección Aprendida y Mejora Preventiva',
                preliminaryObs: 'Observación preliminar:',
                withQuestionnaireBtn: 'Con Cuestionario',
                directCloseBtn: 'Cerrar Directo',
                successModalTitle: 'Reporte Enviado',
                successModalMsg: (name) => `Gracias ${name}, se ha enviado tu reporte con éxito`,
                reportAnotherBtn: 'Reportar otro problema',
                resolveModalTitle: 'Cerrar Problema',
                motivationalQuote: '“De los errores se aprende”',
                resolveWhatDoneReq: '¿Qué se hizo para solucionar el problema? *',
                resolveWhatDoneOpt: '¿Qué se hizo para solucionar el problema? (Opcional para Admin)',
                resolveWhatDonePh: 'Describe la acción correctiva realizada...',
                resolveLessonReq: 'Lección aprendida y mejora preventiva *',
                resolveLessonOpt: 'Lección aprendida y mejora preventiva (Opcional para Admin)',
                resolveLessonPh: 'Acción preventiva para evitar que vuelva a ocurrir...',
                resolveErrorMsg: 'Por favor llena ambas casillas obligatorias para cerrar el problema.',
                cancelBtn: 'Cancelar',
                confirmCloseBtn: 'Confirmar Cierre',
                detailModalTitle: 'Detalles del Ticket',
                detailState: 'Estado:',
                detailArea: 'Área / Tipo:',
                detailEquip: 'Marca y Serie:',
                detailCloseBtn: 'Cerrar',
                closedByAdminMsg: 'Cerrado directamente por Administración',
                closedByAdminLesson: 'Cierre administrativo sin cuestionario',
                userMissingFields: 'Completa usuario, contraseña y nombre',
                userUpdated: (u) => `Cuenta "${u}" actualizada`,
                userAdded: (u) => `Cuenta "${u}" agregada`,
                userCantDeleteAdmin: 'No puedes eliminar al único administrador',
                userDeleted: (u) => `Cuenta "${u}" eliminada`
            },
            en: {
                code: 'EN',
                headerTitle: 'Maintenance System',
                headerSubtitle: 'PPM Industrial Plant',
                logout: 'Log Out',
                changeLang: 'Change Language',
                loginMainTitle: 'PPM Industrial Maintenance System',
                loginSubTitle: 'Plant Control & Management',
                loginUser: 'Username',
                loginPass: 'Password',
                loginError: 'Invalid username or password',
                loginSubmit: 'Sign In',
                loginQrLink: 'Not a technician and want to report an issue?',
                loginDemoTitle: 'Quick Demo Access',
                demoTech: 'Technician (tecnico1)',
                demoAdmin: 'Admin PC (admin)',
                qrTitle: 'Plant Identification',
                qrBack: 'Back',
                qrPositionLabel: 'Position *',
                qrOptPlaceholder: 'Select your position...',
                qrOptSup: 'SUPERVISOR',
                qrOptMgr: 'MANAGER',
                qrOptOp: 'OPERATOR',
                qrOptOther: 'OTHER',
                qrOtherPlaceholder: 'Describe your position',
                qrNameLabel: 'What is your name? *',
                qrNamePlaceholder: 'Enter your full name',
                qrError: 'Please complete your position and name.',
                qrSubmit: 'I have identified myself',
                opFormTitle: 'Submit Fault Report',
                opFormSubtitle: 'Plant Maintenance Log',
                pillTech: 'TECHNICIAN',
                pillQr: 'PLANT QR REPORT',
                fieldDatetime: '1. Date & Time *',
                fieldArea: 'Area or Line *',
                areaApcom: 'Apcom',
                areaEnsamble: 'Assembly',
                areaBosch: 'Bosch',
                areaCf: 'CF motors',
                areaPump: 'Pump Body',
                fieldBrand: '2. Brand & Model',
                brandPlaceholder: 'E.g. Haitian MA1600 / Fanuc M-20iA',
                fieldSerial: '3. Serial Number',
                serialPlaceholder: 'E.g. SN-884920-A',
                fieldType: '4. Fault Type *',
                typeElec: 'Electrical',
                typeMech: 'Mechanical',
                typeHyd: 'Hydraulic / Pneumatic',
                typeSens: 'Sensors / PLC',
                typeSoft: 'Software / Robot',
                typeOther: 'Other fault',
                questionTech: 'Issue (Why did the line stop?)',
                questionQr: 'What happened?',
                fieldProblem: 'Problem Description',
                optionalTag: '(Optional)',
                problemPlaceholder: 'Describe the issue...',
                aiHint: 'AI active: Comments written in Chinese are automatically interpreted into Spanish.',
                submitTicket: 'Report Issue',
                analyzingBtn: 'Submitting report...',
                opActiveTitle: 'Active plant issues',
                opActiveSubtitle: 'Do not forget to mark when the issue is resolved',
                noActiveTickets: 'No pending issues in the plant',
                statusOpen: 'OPEN',
                statusResolved: 'RESOLVED',
                reportedBy: 'Reported by',
                equipmentLabel: 'Equipment',
                serialShort: 'Serial',
                originalDescLabel: 'Problem Description:',
                aiSpanishTranslationLabel: 'AI Interpretation (Chinese → Spanish):',
                reanalyzeBtn: 'Re-interpret with AI',
                reanalyzingBtn: 'Analyzing...',
                detailsBtn: 'Details',
                viewSheetBtn: 'View Details',
                resolvedBtn: 'Issue Resolved',
                qrPlantTag: 'Plant Report (QR)',
                noDescription: 'No description',
                kpiTotal: 'Total in Period',
                kpiOpen: 'Open Issues',
                kpiOpenSub: 'Technicians + QR Guests',
                kpiResolved: 'Resolved Issues',
                kpiResolvedSub: 'With recorded closing time',
                calTitle: 'Fault Calendar',
                calSubtitle: 'Filter issues by month, year or specific day',
                newTicketBtn: '+ New Ticket',
                months: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
                weekdays: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'],
                legendOpen: 'Open',
                legendResolved: 'Resolved',
                clearDayFilter: 'View entire month',
                excelTitle: 'Export to Excel',
                excelScopeDay: 'Day',
                excelScopeMonth: 'Month',
                excelBtnDay: 'Download Day',
                excelBtnMonth: 'Download Current Month',
                usersTitle: 'Users & Passwords',
                usersSubtitle: 'Add, view or remove accounts',
                accCountSingular: 'account',
                accCountPlural: 'accounts',
                accUser: 'Username *',
                accPass: 'Password *',
                accName: 'Display Name *',
                accRole: 'Role *',
                roleTech: 'Technician',
                roleAdmin: 'Administrator',
                accSaveBtn: 'Add or Save Account',
                passLabel: 'Password',
                tabAll: 'All',
                tabOpen: 'Open',
                tabResolved: 'Resolved',
                searchPlaceholder: 'Search area, ID, reporter or fault...',
                noFilteredTickets: 'No reports match this filter',
                noFilteredSub: 'Try selecting another month on the calendar or switching tabs.',
                closeTimeLabel: 'Closing Time',
                whatWasDoneLabel: 'What was done to solve the issue?',
                lessonLearnedLabel: 'Lesson Learned & Preventive Improvement',
                preliminaryObs: 'Preliminary note:',
                withQuestionnaireBtn: 'With Questionnaire',
                directCloseBtn: 'Direct Close',
                successModalTitle: 'Report Sent',
                successModalMsg: (name) => `Thank you ${name}, your report has been submitted successfully`,
                reportAnotherBtn: 'Report another issue',
                resolveModalTitle: 'Close Issue',
                motivationalQuote: '“We learn from our mistakes”',
                resolveWhatDoneReq: 'What was done to solve the issue? *',
                resolveWhatDoneOpt: 'What was done to solve the issue? (Optional for Admin)',
                resolveWhatDonePh: 'Describe the corrective action taken...',
                resolveLessonReq: 'Lesson learned and preventive action *',
                resolveLessonOpt: 'Lesson learned and preventive action (Optional for Admin)',
                resolveLessonPh: 'Preventive action to avoid recurrence...',
                resolveErrorMsg: 'Please fill in both required fields to close the issue.',
                cancelBtn: 'Cancel',
                confirmCloseBtn: 'Confirm Closure',
                detailModalTitle: 'Ticket Details',
                detailState: 'Status:',
                detailArea: 'Area / Type:',
                detailEquip: 'Brand & Serial:',
                detailCloseBtn: 'Close',
                closedByAdminMsg: 'Closed directly by Administration',
                closedByAdminLesson: 'Administrative closure without questionnaire',
                userMissingFields: 'Please complete username, password and name',
                userUpdated: (u) => `Account "${u}" updated`,
                userAdded: (u) => `Account "${u}" added`,
                userCantDeleteAdmin: 'Cannot delete the only administrator',
                userDeleted: (u) => `Account "${u}" deleted`
            },
            zh: {
                code: '中文',
                headerTitle: '工厂维护系统',
                headerSubtitle: 'PPM 工业厂区',
                logout: '退出',
                changeLang: '切换语言',
                loginMainTitle: 'PPM 工业设备维护管理系统',
                loginSubTitle: '厂区设备控制与管理',
                loginUser: '用户名',
                loginPass: '密码',
                loginError: '用户名或密码错误',
                loginSubmit: '登录系统',
                loginQrLink: '不是技术员但想报告问题？',
                loginDemoTitle: '快速测试账户',
                demoTech: '技术员 (tecnico1)',
                demoAdmin: '管理员电脑端 (admin)',
                qrTitle: '工厂身份识别',
                qrBack: '返回',
                qrPositionLabel: '职位 *',
                qrOptPlaceholder: '请选择您的职位...',
                qrOptSup: '主管',
                qrOptMgr: '经理',
                qrOptOp: '操作员',
                qrOptOther: '其他',
                qrOtherPlaceholder: '请描述您的职位',
                qrNameLabel: '您的姓名 *',
                qrNamePlaceholder: '请输入您的全名',
                qrError: '请填写您的职位和姓名。',
                qrSubmit: '我已完成身份识别',
                opFormTitle: '新建故障报告',
                opFormSubtitle: '车间设备维护登记',
                pillTech: '技术员',
                pillQr: '车间扫码报告',
                fieldDatetime: '1. 日期与时间 *',
                fieldArea: '区域或产线 *',
                areaApcom: 'Apcom 产线',
                areaEnsamble: '组装线',
                areaBosch: '博世产线',
                areaCf: '春风动力 CF Motors',
                areaPump: '泵体线 (Pump Body)',
                fieldBrand: '2. 机器品牌与型号',
                brandPlaceholder: '例如：Haitian MA1600 / Fanuc M-20iA',
                fieldSerial: '3. 序列号',
                serialPlaceholder: '例如：SN-884920-A',
                fieldType: '4. 故障类型 *',
                typeElec: '电气故障',
                typeMech: '机械故障',
                typeHyd: '液压 / 气动故障',
                typeSens: '传感器 / PLC故障',
                typeSoft: '软件 / 机器人故障',
                typeOther: '其他故障',
                questionTech: '问题（为什么产线停了？）',
                questionQr: '发生了什么事？',
                fieldProblem: '故障详细描述',
                optionalTag: '（可选）',
                problemPlaceholder: '请描述故障情况（中文评论将由AI自动解析为西班牙语供管理端查看）...',
                aiHint: 'AI 已启用：中文填写的故障描述将自动深度解析并翻译为西班牙语。',
                submitTicket: '提交故障报告',
                analyzingBtn: '正在提交并解析...',
                opActiveTitle: '车间当前活动工单',
                opActiveSubtitle: '问题解决后，请别忘了标记“已解决”',
                noActiveTickets: '车间暂无待处理故障',
                statusOpen: '待处理',
                statusResolved: '已解决',
                reportedBy: '报告人',
                equipmentLabel: '设备',
                serialShort: '序列号',
                originalDescLabel: '故障描述原文：',
                aiSpanishTranslationLabel: 'AI 西班牙语含义解读 (中文 → 西语)：',
                reanalyzeBtn: 'AI 重新解读为西语',
                reanalyzingBtn: '正在解析...',
                detailsBtn: '详情',
                viewSheetBtn: '查看详情',
                resolvedBtn: '问题已解决',
                qrPlantTag: '扫码报告 (QR)',
                noDescription: '无描述',
                kpiTotal: '本期总工单',
                kpiOpen: '待处理问题',
                kpiOpenSub: '技术员 + 扫码访客',
                kpiResolved: '已解决问题',
                kpiResolvedSub: '已记录准确关闭时间',
                calTitle: '故障日历筛选',
                calSubtitle: '按年、月或具体日期筛选故障',
                newTicketBtn: '+ 新建工单',
                months: ['1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月', '9月', '10月', '11月', '12月'],
                weekdays: ['日', '一', '二', '三', '四', '五', '六'],
                legendOpen: '待处理',
                legendResolved: '已解决',
                clearDayFilter: '查看全月所有工单',
                excelTitle: '导出 Excel',
                excelScopeDay: '当日',
                excelScopeMonth: '全月',
                excelBtnDay: '导出当日数据',
                excelBtnMonth: '导出本月数据',
                usersTitle: '账户与密码管理',
                usersSubtitle: '添加、查看或删除系统账户',
                accCountSingular: '个账户',
                accCountPlural: '个账户',
                accUser: '用户名 *',
                accPass: '密码 *',
                accName: '显示姓名 *',
                accRole: '角色 *',
                roleTech: '技术员',
                roleAdmin: '管理员',
                accSaveBtn: '添加或保存账户',
                passLabel: '密码',
                tabAll: '全部',
                tabOpen: '待处理',
                tabResolved: '已解决',
                searchPlaceholder: '搜索区域、工单号、报告人或故障...',
                noFilteredTickets: '当前筛选条件下暂无工单',
                noFilteredSub: '请尝试在日历中选择其他月份或切换标签页。',
                closeTimeLabel: '关闭时间',
                whatWasDoneLabel: '采取了什么措施解决该问题？',
                lessonLearnedLabel: '吸取的教训与预防改进措施',
                preliminaryObs: '初步备注：',
                withQuestionnaireBtn: '填写总结关闭',
                directCloseBtn: '直接关闭',
                successModalTitle: '报告已成功发送',
                successModalMsg: (name) => `感谢您 ${name}，您的故障报告已成功提交`,
                reportAnotherBtn: '继续报告其他问题',
                resolveModalTitle: '关闭故障工单',
                motivationalQuote: '“从错误中学习”',
                resolveWhatDoneReq: '采取了什么措施解决该问题？ *',
                resolveWhatDoneOpt: '采取了什么措施解决该问题？（管理员选填）',
                resolveWhatDonePh: '请描述所采取的维修措施...',
                resolveLessonReq: '吸取的教训与预防改进措施 *',
                resolveLessonOpt: '吸取的教训与预防改进措施（管理员选填）',
                resolveLessonPh: '如何防止类似故障再次发生...',
                resolveErrorMsg: '请填写所有必填项以关闭此问题。',
                cancelBtn: '取消',
                confirmCloseBtn: '确认关闭',
                detailModalTitle: '工单详情',
                detailState: '状态：',
                detailArea: '区域 / 类型：',
                detailEquip: '品牌与序列号：',
                detailCloseBtn: '关闭',
                closedByAdminMsg: '由管理员直接关闭',
                closedByAdminLesson: '管理员免填问卷直接关闭',
                userMissingFields: '请完整填写用户名、密码和姓名',
                userUpdated: (u) => `账户 "${u}" 已更新`,
                userAdded: (u) => `账户 "${u}" 已添加`,
                userCantDeleteAdmin: '不能删除唯一的管理员账户',
                userDeleted: (u) => `账户 "${u}" 已删除`
            }
        };

        function t(key) {
            const dict = I18N[currentLang] || I18N.es;
            return dict[key] !== undefined ? dict[key] : I18N.es[key];
        }

        // Detectar si un texto contiene caracteres chinos
        function containsChineseText(str) {
            return /[\u4e00-\u9fa5]/.test(str || '');
        }

        // Seleccionar idioma en la pantalla inicial y pasar a la pantalla de inicio de sesión
        function selectAppLanguage(lang) {
            if (!I18N[lang]) lang = 'es';
            currentLang = lang;
            try {
                localStorage.setItem(LANG_STORAGE_KEY, lang);
            } catch (e) {}

            applyLanguageToStaticUI();

            document.getElementById('screen-language').classList.add('hidden');
            if (currentUser) {
                enterApplicationByRole();
            } else {
                // Si la persona entró escaneando el código QR de la planta (?qr=1), llevarla directo a Identificación de Planta
                const urlParams = new URLSearchParams(window.location.search);
                if (urlParams.get('qr') === '1') {
                    openQrIdentification();
                } else {
                    document.getElementById('screen-login').classList.remove('hidden');
                }
            }
        }
        window.selectAppLanguage = selectAppLanguage;

        // Volver a abrir la pantalla de selección de idioma
        function openLanguageSelector() {
            document.getElementById('screen-login').classList.add('hidden');
            document.getElementById('screen-qr-id').classList.add('hidden');
            document.getElementById('screen-operator').classList.add('hidden');
            document.getElementById('screen-admin').classList.add('hidden');
            document.getElementById('main-header').classList.add('hidden');
            const shell = document.getElementById('app-shell');
            shell.classList.remove('max-w-7xl');
            shell.classList.add('max-w-md');
            document.getElementById('screen-language').classList.remove('hidden');
        }
        window.openLanguageSelector = openLanguageSelector;

        // Aplicar el idioma seleccionado a absolutamente todos los textos de la interfaz
        function applyLanguageToStaticUI() {
            document.documentElement.lang = currentLang;

            const setText = (id, val) => {
                const el = document.getElementById(id);
                if (el && val !== undefined) el.innerText = val;
            };
            const setPlaceholder = (id, val) => {
                const el = document.getElementById(id);
                if (el && val !== undefined) el.placeholder = val;
            };

            // Header
            setText('header-title', t('headerTitle'));
            setText('header-subtitle', t('headerSubtitle'));
            setText('header-lang-code', t('code'));
            setText('btn-logout-text', t('logout'));

            // Login
            setText('login-change-lang-label', t('changeLang'));
            setText('login-main-title', t('loginMainTitle'));
            setText('login-sub-title', t('loginSubTitle'));
            setText('login-label-user', t('loginUser'));
            setText('login-label-pass', t('loginPass'));
            setText('login-error', t('loginError'));
            setText('login-btn-submit', t('loginSubmit'));
            setText('login-qr-link-text', t('loginQrLink'));
            setText('login-demo-title', t('loginDemoTitle'));
            setText('demo-btn-tech', t('demoTech'));
            setText('demo-btn-admin', t('demoAdmin'));

            // QR Identification
            setText('qr-title', t('qrTitle'));
            setText('qr-btn-back', t('qrBack'));
            setText('qr-label-position', t('qrPositionLabel'));
            setText('qr-opt-placeholder', t('qrOptPlaceholder'));
            setText('qr-opt-sup', t('qrOptSup'));
            setText('qr-opt-mgr', t('qrOptMgr'));
            setText('qr-opt-op', t('qrOptOp'));
            setText('qr-opt-other', t('qrOptOther'));
            setPlaceholder('qr-other-input', t('qrOtherPlaceholder'));
            setText('qr-label-name', t('qrNameLabel'));
            setPlaceholder('qr-name-input', t('qrNamePlaceholder'));
            setText('qr-id-error', t('qrError'));
            setText('qr-btn-submit', t('qrSubmit'));

            // Operator / QR Form
            setText('op-form-title', t('opFormTitle'));
            setText('op-form-subtitle', t('opFormSubtitle'));
            setText('label-field-datetime', t('fieldDatetime'));
            setText('label-field-area', t('fieldArea'));
            setText('opt-area-apcom', t('areaApcom'));
            setText('opt-area-ensamble', t('areaEnsamble'));
            setText('opt-area-bosch', t('areaBosch'));
            setText('opt-area-cf', t('areaCf'));
            setText('opt-area-pump', t('areaPump'));
            setText('label-field-brand', t('fieldBrand'));
            setPlaceholder('field-brand', t('brandPlaceholder'));
            setText('label-field-serial', t('fieldSerial'));
            setPlaceholder('field-serial', t('serialPlaceholder'));
            setText('label-field-type', t('fieldType'));
            setText('opt-type-elec', t('typeElec'));
            setText('opt-type-mech', t('typeMech'));
            setText('opt-type-hyd', t('typeHyd'));
            setText('opt-type-sens', t('typeSens'));
            setText('opt-type-soft', t('typeSoft'));
            setText('opt-type-other', t('typeOther'));
            setText('label-field-problem', t('fieldProblem'));
            setText('label-optional-tag', t('optionalTag'));
            setPlaceholder('field-problem', t('problemPlaceholder'));
            setText('label-ai-hint', t('aiHint'));
            setText('btn-submit-ticket-text', t('submitTicket'));
            setText('op-active-title', t('opActiveTitle'));
            setText('op-active-subtitle', t('opActiveSubtitle'));

            // Admin Dashboard
            setText('kpi-title-total', t('kpiTotal'));
            setText('kpi-title-open', t('kpiOpen'));
            setText('kpi-sub-open', t('kpiOpenSub'));
            setText('kpi-title-resolved', t('kpiResolved'));
            setText('kpi-sub-resolved', t('kpiResolvedSub'));
            setText('admin-cal-title', t('calTitle'));
            setText('admin-cal-subtitle', t('calSubtitle'));
            setText('btn-admin-new-ticket', t('newTicketBtn'));
            setText('legend-open', t('legendOpen'));
            setText('legend-resolved', t('legendResolved'));
            setText('btn-clear-day-filter', t('clearDayFilter'));
            setText('admin-excel-title', t('excelTitle'));
            setText('admin-users-title', t('usersTitle'));
            setText('admin-users-subtitle', t('usersSubtitle'));
            setText('label-acc-user', t('accUser'));
            setText('label-acc-pass', t('accPass'));
            setText('label-acc-name', t('accName'));
            setText('label-acc-role', t('accRole'));
            setText('opt-role-tech', t('roleTech'));
            setText('opt-role-admin', t('roleAdmin'));
            setText('btn-acc-save', t('accSaveBtn'));
            setText('tab-btn-ALL', t('tabAll'));
            setText('tab-label-open', t('tabOpen'));
            setText('tab-label-resolved', t('tabResolved'));
            setPlaceholder('admin-search-input', t('searchPlaceholder'));
            setText('btn-top-excel', 'Excel');

            // Months & Weekdays in Admin Calendar
            const monthSelect = document.getElementById('admin-cal-month');
            const monthsArr = t('months');
            if (monthSelect && Array.isArray(monthsArr)) {
                Array.from(monthSelect.options).forEach((opt, idx) => {
                    if (monthsArr[idx]) opt.text = monthsArr[idx];
                });
            }
            const weekdaysContainer = document.getElementById('admin-cal-weekdays');
            const weekdaysArr = t('weekdays');
            if (weekdaysContainer && Array.isArray(weekdaysArr)) {
                weekdaysContainer.innerHTML = weekdaysArr.map(d => `<div>${d}</div>`).join('');
            }

            // Modals
            setText('success-modal-title', t('successModalTitle'));
            setText('btn-modal-exit', t('logout'));
            setText('btn-modal-another', t('reportAnotherBtn'));
            setText('resolve-modal-title', t('resolveModalTitle'));
            setText('resolve-motivational-quote', t('motivationalQuote'));
            setPlaceholder('resolve-what-done', t('resolveWhatDonePh'));
            setPlaceholder('resolve-lesson', t('resolveLessonPh'));
            setText('resolve-error-msg', t('resolveErrorMsg'));
            setText('btn-resolve-cancel', t('cancelBtn'));
            setText('btn-resolve-confirm', t('confirmCloseBtn'));
            setText('btn-detail-close', t('detailCloseBtn'));

            configureOperatorFormForMode();
            renderOperatorTickets();
            renderAdminDashboard();
            renderAdminUsersList();
        }

        // Usuarios registrados por defecto
        const DEFAULT_USERS = {
            tecnico1: { username: 'tecnico1', pass: '1234', role: 'OPERATOR', name: 'Carlos Mendoza (Técnico)' },
            tecnico2: { username: 'tecnico2', pass: '1234', role: 'OPERATOR', name: 'Wei Zhang (技术员)' },
            '123': { username: '123', pass: '123', role: 'ADMIN', name: 'Administrador de Planta' }
        };

        let USERS = { ...DEFAULT_USERS };

        function loadUsersFromLocalStorage() {
            try {
                const raw = localStorage.getItem(USERS_STORAGE_KEY);
                if (raw) {
                    const parsed = JSON.parse(raw);
                    if (parsed && typeof parsed === 'object' && Object.keys(parsed).length > 0) {
                        USERS = parsed;
                        // Asegurar que la cuenta de administrador 123 / 123 siempre esté activa y actualizada
                        delete USERS.admin;
                        USERS['123'] = { username: '123', pass: '123', role: 'ADMIN', name: 'Administrador de Planta' };
                        saveUsersToLocalStorage();
                        return;
                    }
                }
            } catch (e) {
                console.warn('Error leyendo usuarios de localStorage:', e);
            }
            USERS = { ...DEFAULT_USERS };
            saveUsersToLocalStorage();
        }

        function saveUsersToLocalStorage() {
            try {
                localStorage.setItem(USERS_STORAGE_KEY, JSON.stringify(USERS));
            } catch (e) {
                console.warn('Error guardando usuarios en localStorage:', e);
            }
            if (typeof window.syncUsersToCloud === 'function') {
                window.syncUsersToCloud(USERS);
            }
        }
        window.saveUsersToLocalStorage = saveUsersToLocalStorage;

        // Estado de sesión y filtros
        let currentUser = null;
        let isQrReporterSession = false;
        let adminSelectedYear = 2026;
        let adminSelectedMonth = 9; // Octubre (0-indexed: 9 = Octubre)
        let adminSelectedDay = null; // null = todo el mes
        let adminActiveTab = 'ALL'; // 'ALL' | 'ABIERTO' | 'RESUELTO'

        // Tickets iniciales de demostración (Con traducción IA únicamente de Chino -> Español)
        const DEFAULT_TICKETS = [
            {
                id: 'TK-1042',
                datetime: '2026-10-29T08:30',
                area: 'Apcom',
                brand: 'Haitian MA1600',
                serial: 'HT-99201-A',
                type: 'Hidráulica / Neumática',
                problemOriginal: '主液压阀漏油，系统压力下降，导致成型周期中断。',
                problemSpanish: '🧠 [Significado Real]: La inyectora Haitian detuvo su ciclo automático porque la válvula proporcional hidráulica principal tiene una fuga de aceite que impide alcanzar la presión de cierre y moldeo.\n🔧 [Diagnóstico IA]: Posible sello O-ring dañado o carrete de válvula desgastado.',
                aiDiagnosis: 'Fuga en válvula proporcional principal con pérdida de presión de cierre',
                cause: 'Desgaste de sello O-ring por alta temperatura',
                lesson: '',
                status: 'ABIERTO',
                operatorName: 'Wei Zhang (tecnico2)',
                createdAt: '2026-10-29T08:30:00.000Z',
                closedAt: null
            },
            {
                id: 'TK-1045',
                datetime: '2026-10-29T09:15',
                area: 'Ensamble',
                brand: 'Banda Transportadora B2',
                serial: 'N/A',
                type: 'Reporte QR (General)',
                problemOriginal: '输送带电机发出异响并且速度不稳定。',
                problemSpanish: '🧠 [Significado Real]: El motorreductor de la banda transportadora presenta vibración y ruido mecánico inusual acompañado de variaciones de velocidad en la línea de ensamble.\n🔧 [Diagnóstico IA]: Probable desgaste en rodamientos del reductor o sobrecarga en variador de frecuencia (VFD).',
                aiDiagnosis: 'Falla mecánica en rodamientos de motorreductor o inestabilidad en variador VFD',
                cause: 'Reportado desde código QR en línea',
                lesson: '',
                status: 'ABIERTO',
                operatorName: 'Roberto Gómez - SUPERVISOR [QR Planta]',
                createdAt: '2026-10-29T09:15:00.000Z',
                closedAt: null
            },
            {
                id: 'TK-1038',
                datetime: '2026-10-28T14:10',
                area: 'Pump Body',
                brand: 'Komatsu H2W-200',
                serial: 'KM-20048',
                type: 'Eléctrica / Sensores',
                problemOriginal: '光电安全传感器误报警，冲床无法启动。',
                problemSpanish: '🧠 [Significado Real]: La prensa Komatsu se bloquea por seguridad y no permite iniciar el golpe porque la cortina óptica detecta una interrupción falsa.\n🔧 [Diagnóstico IA]: Suciedad de neblina de aceite en los lentes o desalineación por vibración de la prensa.',
                aiDiagnosis: 'Bloqueo de seguridad por falsa detección en cortina fotoeléctrica',
                cause: 'Se limpió lente óptico, se recalibró alineación láser y se fijó soporte.',
                lesson: 'Incluir limpieza óptica diaria al inicio del turno.',
                status: 'RESUELTO',
                operatorName: 'Carlos Mendoza (tecnico1)',
                createdAt: '2026-10-28T14:10:00.000Z',
                closedAt: '16:05 hrs (28/10/2026)'
            }
        ];

        let tickets = [];

        // Cargar o inicializar almacenamiento local
        function loadFromLocalStorage() {
            try {
                const raw = localStorage.getItem(STORAGE_KEY);
                if (raw) {
                    const parsed = JSON.parse(raw);
                    if (Array.isArray(parsed) && parsed.length > 0) {
                        tickets = parsed;
                        return;
                    }
                }
            } catch (e) {
                console.warn('Error leyendo localStorage:', e);
            }
            tickets = [...DEFAULT_TICKETS];
            saveToLocalStorage();
        }

        function saveToLocalStorage() {
            try {
                localStorage.setItem(STORAGE_KEY, JSON.stringify(tickets));
            } catch (e) {
                console.warn('Error guardando localStorage:', e);
            }
        }
        window.saveToLocalStorage = saveToLocalStorage;

        // Funciones auxiliares para el Generador de QR y Modal de Firebase
        function updatePlantQrCode() {
            const input = document.getElementById('qr-custom-url-input');
            const img = document.getElementById('plant-qr-image');
            const label = document.getElementById('plant-qr-target-label');
            if (!img) return;

            let baseUrl = (input && input.value.trim()) ? input.value.trim() : window.location.origin + window.location.pathname;
            if (input && input.value.trim()) {
                try { localStorage.setItem(CUSTOM_QR_URL_KEY, baseUrl); } catch (e) {}
            }
            const separator = baseUrl.includes('?') ? '&' : '?';
            const finalQrUrl = `${baseUrl}${separator}qr=1`;

            img.src = `https://api.qrserver.com/v1/create-qr-code/?size=240x240&data=${encodeURIComponent(finalQrUrl)}`;
            if (label) label.innerText = finalQrUrl;
        }
        window.updatePlantQrCode = updatePlantQrCode;

        function printPlantQrPoster() {
            const img = document.getElementById('plant-qr-image');
            const label = document.getElementById('plant-qr-target-label');
            const qrSrc = img ? img.src : '';
            const targetUrl = label ? label.innerText : '';

            const w = window.open('', '_blank');
            if (!w) return;
            w.document.write(`
                <html>
                <head>
                    <title>Cartel QR Planta PPM</title>
                    <style>
                        body { font-family: Arial, sans-serif; text-align: center; padding: 40px; }
                        .card { border: 4px solid #16a34a; border-radius: 24px; padding: 32px; max-width: 460px; margin: 0 auto; }
                        h1 { color: #0f172a; margin-bottom: 6px; font-size: 26px; }
                        h2 { color: #16a34a; margin-top: 0; font-size: 18px; }
                        img { width: 260px; height: 260px; margin: 20px auto; display: block; }
                        p { color: #475569; font-size: 14px; font-weight: bold; }
                    </style>
                </head>
                <body>
                    <div class="card">
                        <h1>PPM 工厂维护系统</h1>
                        <h2>Reporte Rápido de Fallas en Planta / 扫码报修</h2>
                        <img src="${qrSrc}" onload="window.print()" />
                        <p>Escanea con la cámara de tu celular para reportar un problema en la línea.</p>
                        <p style="font-size:11px; color:#94a3b8;">${targetUrl}</p>
                    </div>
                </body>
                </html>
            `);
            w.document.close();
        }
        window.printPlantQrPoster = printPlantQrPoster;

        function openFirebaseConfigModal() {
            const modal = document.getElementById('modal-firebase-config');
            const textarea = document.getElementById('firebase-config-textarea');
            const saved = localStorage.getItem(CUSTOM_FB_CONFIG_KEY);
            if (textarea && saved) textarea.value = saved;
            if (modal) modal.classList.remove('hidden');
        }
        window.openFirebaseConfigModal = openFirebaseConfigModal;

        function closeFirebaseConfigModal() {
            const modal = document.getElementById('modal-firebase-config');
            if (modal) modal.classList.add('hidden');
        }
        window.closeFirebaseConfigModal = closeFirebaseConfigModal;

        function parseLooseFirebaseConfig(rawText) {
            const trimmed = (rawText || '').trim();
            if (!trimmed) return null;
            try {
                return JSON.parse(trimmed);
            } catch (e) {
                const match = trimmed.match(/\{[\s\S]*\}/);
                if (!match) return null;
                const objStr = match[0]
                    .replace(/(\w+)\s*:/g, '"$1":')
                    .replace(/'/g, '"')
                    .replace(/,\s*\}/g, '}');
                try {
                    return JSON.parse(objStr);
                } catch (e2) {
                    return null;
                }
            }
        }
        window.parseLooseFirebaseConfig = parseLooseFirebaseConfig;

        function saveCustomFirebaseConfig() {
            const textarea = document.getElementById('firebase-config-textarea');
            const feedback = document.getElementById('firebase-config-feedback');
            const parsed = parseLooseFirebaseConfig(textarea ? textarea.value : '');

            if (!parsed || !parsed.apiKey || !parsed.projectId) {
                if (feedback) {
                    feedback.innerText = 'El formato no es válido. Asegúrate de incluir apiKey y projectId.';
                    feedback.className = 'text-xs font-bold mt-1.5 p-2 rounded-lg text-center bg-rose-50 text-rose-700 border border-rose-200';
                    feedback.classList.remove('hidden');
                }
                return;
            }

            localStorage.setItem(CUSTOM_FB_CONFIG_KEY, JSON.stringify(parsed, null, 2));
            if (feedback) {
                feedback.innerText = '¡Configuración guardada! Conectando con tu nube Firebase...';
                feedback.className = 'text-xs font-bold mt-1.5 p-2 rounded-lg text-center bg-emerald-50 text-emerald-700 border border-emerald-200';
                feedback.classList.remove('hidden');
            }
            if (typeof window.initCloudFirebase === 'function') {
                window.initCloudFirebase();
            }
            setTimeout(() => {
                closeFirebaseConfigModal();
            }, 1000);
        }
        window.saveCustomFirebaseConfig = saveCustomFirebaseConfig;

        // =========================================================================
        // MOTOR DE IA GEMINI: EXCLUSIVAMENTE DE CHINO HACIA ESPAÑOL (NO VICEVERSA)
        // Si el comentario NO está escrito en chino, no realiza traducción inversa.
        // =========================================================================
        async function fetchGeminiWithBackoff(apiUrl, payload, maxRetries = 3) {
            let delay = 1000;
            for (let attempt = 0; attempt < maxRetries; attempt++) {
                try {
                    const response = await fetch(apiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });
                    if (response.ok) {
                        return await response.json();
                    }
                } catch (err) {
                    // Reintento silencioso con backoff exponencial
                }
                if (attempt < maxRetries - 1) {
                    await new Promise(res => setTimeout(res, delay));
                    delay *= 2;
                }
            }
            return null;
        }

        // Respaldo semántico local exclusivamente para comentarios en chino -> español
        function buildSmartOfflineInterpretation(text, contextInfo = {}) {
            const clean = (text || '').trim();
            if (!containsChineseText(clean)) {
                return {
                    formattedExplanation: '',
                    diagnosisSummary: ''
                };
            }

            const machine = contextInfo.brand || 'Equipo de planta';
            const areaOrType = contextInfo.areaOrType || 'Línea de producción';

            const semanticRules = [
                { keys: ['漏油', '油'], meaningEs: 'pérdida de fluido o fuga de aceite en el circuito hidráulico/lubricación', diag: 'Revisar sellos, mangueras y presión nominal' },
                { keys: ['压力'], meaningEs: 'inestabilidad o caída de presión operativa que impide completar el ciclo', diag: 'Verificar bomba, válvula proporcional o manómetro' },
                { keys: ['传感器', '光电', '电眼'], meaningEs: 'activación de sensor o bloqueo de seguridad por detección anómala en máquina', diag: 'Limpiar sensor, revisar cableado y alineación' },
                { keys: ['电机', '马达', '异响'], meaningEs: 'anomalía electromecánica en motor o transmisión (ruido, vibración o par inestable)', diag: 'Inspeccionar rodamientos, acoplamiento y corriente del variador' },
                { keys: ['温度', '过热', '热'], meaningEs: 'exceso de temperatura fuera del rango seguro de operación', diag: 'Revisar sistema de enfriamiento, ventilación y carga térmica' },
                { keys: ['无法启动', '不开机', '停', '卡'], meaningEs: 'paro total de línea o bloqueo de secuencia de arranque del equipo', diag: 'Verificar condiciones de home, paros de emergencia y PLC' }
            ];

            let matchedEs = [];
            let matchedDiag = [];

            semanticRules.forEach(rule => {
                if (rule.keys.some(k => clean.includes(k))) {
                    matchedEs.push(rule.meaningEs);
                    matchedDiag.push(rule.diag);
                }
            });

            if (matchedEs.length > 0) {
                return {
                    formattedExplanation: `🧠 [Significado Real en Español]: En el equipo ${machine} (${areaOrType}) el comentario en chino indica ${matchedEs.join(' y ')}.\n🔧 [Diagnóstico Sugerido]: ${matchedDiag[0]}`,
                    diagnosisSummary: matchedDiag[0]
                };
            }

            return {
                formattedExplanation: `🧠 [Significado Real en Español]: El operador reporta en chino una incidencia operativa en ${machine} (${areaOrType}): "${clean}". Se requiere revisión técnica en línea.`,
                diagnosisSummary: `Revisión operativa en ${machine}`
            };
        }

        // Función principal que envía el texto en CHINO a la API de Gemini para interpretarlo al ESPAÑOL (no viceversa)
        async function interpretMeaningWithGeminiAI(rawText, contextInfo = {}) {
            const clean = (rawText || '').trim();
            // Condición estricta: Solo traducir/interpretar si el comentario contiene chino
            if (!clean || !containsChineseText(clean)) {
                return {
                    formattedExplanation: '',
                    diagnosisSummary: ''
                };
            }

            const apiKey = ""; // Canvas inyecta automáticamente la clave en tiempo de ejecución
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-3-flash-preview:generateContent?key=${apiKey}`;

            const systemPrompt = `Eres un Ingeniero Senior de Mantenimiento Industrial experto en traducir e interpretar reportes técnicos escritos en CHINO MANDARÍN hacia el ESPAÑOL en una planta de manufactura.
Tu objetivo NO es hacer una traducción literal palabra por palabra, sino ENTENDER QUÉ PASÓ REALMENTE según el comentario en chino y explicarlo únicamente en ESPAÑOL claro y técnico para el Panel del Administrador.
IMPORTANTE: No devuelvas texto en chino. Devuelve todo exclusivamente en español.`;

            const userQuery = `Contexto del reporte en planta:
- Área o Tipo de Falla: ${contextInfo.areaOrType || 'Planta General'}
- Marca y Modelo de Máquina: ${contextInfo.brand || 'No especificado'}
- Número de Serie: ${contextInfo.serial || 'N/A'}
- Quién reporta: ${contextInfo.reporter || 'Personal de planta'}
- Comentario original en chino: "${clean}"

Interpreta el significado técnico real de este comentario chino hacia el español.`;

            const payload = {
                contents: [{ parts: [{ text: userQuery }] }],
                systemInstruction: { parts: [{ text: systemPrompt }] },
                generationConfig: {
                    responseMimeType: "application/json",
                    responseSchema: {
                        type: "OBJECT",
                        properties: {
                            realMeaningEs: { type: "STRING" },
                            technicalDiagnosisEs: { type: "STRING" }
                        },
                        propertyOrdering: ["realMeaningEs", "technicalDiagnosisEs"]
                    }
                }
            };

            const result = await fetchGeminiWithBackoff(apiUrl, payload, 3);
            const rawJsonText = result?.candidates?.[0]?.content?.parts?.[0]?.text;

            if (rawJsonText) {
                try {
                    const parsed = JSON.parse(rawJsonText);
                    const meaningEs = (parsed.realMeaningEs || '').trim();
                    const diag = (parsed.technicalDiagnosisEs || '').trim();

                    if (meaningEs) {
                        const formatted = [
                            `🧠 [Significado Real]: ${meaningEs}`,
                            diag ? `🔧 [Diagnóstico IA]: ${diag}` : ''
                        ].filter(Boolean).join('\n');

                        return {
                            formattedExplanation: formatted,
                            diagnosisSummary: diag || meaningEs
                        };
                    }
                } catch (parseErr) {
                    console.warn('Error interpretando JSON de Gemini:', parseErr);
                }
            }

            return buildSmartOfflineInterpretation(clean, contextInfo);
        }
        window.interpretMeaningWithGeminiAI = interpretMeaningWithGeminiAI;

        // Permitir al Administrador re-analizar comentarios escritos en chino con la IA Gemini
        async function reanalyzeTicketWithAI(ticketId) {
            const ticket = tickets.find(t => t.id === ticketId);
            if (!ticket || !containsChineseText(ticket.problemOriginal)) return;

            const btn = document.getElementById(`btn-ai-reanalyze-${ticketId}`);
            if (btn) {
                btn.disabled = true;
                btn.innerHTML = `<i class="fa-solid fa-spinner animate-spin"></i> <span>${t('reanalyzingBtn')}</span>`;
            }

            const aiResult = await interpretMeaningWithGeminiAI(ticket.problemOriginal, {
                areaOrType: `${ticket.area} / ${ticket.type || ''}`,
                brand: ticket.brand,
                serial: ticket.serial,
                reporter: ticket.operatorName
            });

            ticket.problemSpanish = aiResult.formattedExplanation;
            ticket.aiDiagnosis = aiResult.diagnosisSummary;

            saveToLocalStorage();
            if (typeof window.saveTicketToCloud === 'function') {
                window.saveTicketToCloud(ticket);
            }
            renderOperatorTickets();
            renderAdminDashboard();
        }
        window.reanalyzeTicketWithAI = reanalyzeTicketWithAI;

        // Configurar fecha y hora actual en el formulario
        function resetDatetimeField() {
            const field = document.getElementById('field-datetime');
            if (!field) return;
            const now = new Date();
            const tzOffset = now.getTimezoneOffset() * 60000;
            const localISO = new Date(now - tzOffset).toISOString().slice(0, 16);
            field.value = localISO;
        }
        window.resetDatetimeField = resetDatetimeField;

        // Autocompletar credenciales demo
        function fillDemoLogin(user, pass) {
            document.getElementById('login-user').value = user;
            document.getElementById('login-pass').value = pass;
            document.getElementById('login-error').classList.add('hidden');
        }
        window.fillDemoLogin = fillDemoLogin;

        // Manejo de Login
        function handleLogin(event) {
            if (event) event.preventDefault();
            const rawU = document.getElementById('login-user').value.trim().toLowerCase();
            const rawP = document.getElementById('login-pass').value.trim();
            // Permitir tanto "123" como "1 2 3"
            const u = rawU === '1 2 3' ? '123' : rawU;
            const p = rawP === '1 2 3' ? '123' : rawP;
            const errBox = document.getElementById('login-error');

            if (USERS[u] && USERS[u].pass === p) {
                errBox.classList.add('hidden');
                currentUser = USERS[u];
                isQrReporterSession = false;
                enterApplicationByRole();
            } else {
                errBox.classList.remove('hidden');
            }
        }
        window.handleLogin = handleLogin;

        // Configurar interfaz según el rol (Técnico, Invitado QR o Administrador en PC)
        function enterApplicationByRole() {
            const shell = document.getElementById('app-shell');
            const header = document.getElementById('main-header');
            const badge = document.getElementById('user-badge');

            document.getElementById('screen-language').classList.add('hidden');
            document.getElementById('screen-login').classList.add('hidden');
            document.getElementById('screen-qr-id').classList.add('hidden');
            header.classList.remove('hidden');

            if (currentUser && currentUser.role === 'ADMIN') {
                // Formato de Escritorio de PC para el Administrador
                shell.classList.remove('max-w-md');
                shell.classList.add('max-w-7xl');
                badge.innerText = `Admin PC • ${currentUser.name}`;

                document.getElementById('screen-operator').classList.add('hidden');
                document.getElementById('screen-admin').classList.remove('hidden');

                // Sincronizar selectores del calendario
                document.getElementById('admin-cal-month').value = String(adminSelectedMonth);
                document.getElementById('admin-cal-year').value = String(adminSelectedYear);
                renderAdminDashboard();
                renderAdminUsersList();
            } else {
                // Formato compacto para Técnico o Invitado QR
                shell.classList.remove('max-w-7xl');
                shell.classList.add('max-w-md');
                badge.innerText = currentUser ? currentUser.name : t('pillQr');

                document.getElementById('screen-admin').classList.add('hidden');
                document.getElementById('screen-operator').classList.remove('hidden');

                configureOperatorFormForMode();
                resetDatetimeField();
                renderOperatorTickets();
            }
        }

        // Ajustar campos opcionales y visibilidad según sea Técnico o Invitado QR
        function configureOperatorFormForMode() {
            const opt2 = document.getElementById('opt-label-2');
            const opt3 = document.getElementById('opt-label-3');
            const brandInput = document.getElementById('field-brand');
            const serialInput = document.getElementById('field-serial');
            const problemInput = document.getElementById('field-problem');
            const questionLabel = document.getElementById('label-problem-question');
            const pill = document.getElementById('operator-mode-pill');
            const activeSection = document.getElementById('operator-active-section');
            const rowDatetimeArea = document.getElementById('row-datetime-area');
            const areaContainer = document.getElementById('container-field-area');
            const areaSelect = document.getElementById('field-area');
            const typeContainer = document.getElementById('container-field-type');
            const typeSelect = document.getElementById('field-type');

            if (opt2) {
                opt2.innerText = '*';
                opt2.className = 'text-slate-700 font-bold';
            }
            if (opt3) {
                opt3.innerText = '*';
                opt3.className = 'text-slate-700 font-bold';
            }
            if (brandInput) brandInput.required = true;
            if (serialInput) serialInput.required = true;
            if (problemInput) problemInput.required = false;

            if (isQrReporterSession) {
                if (areaContainer) areaContainer.classList.remove('hidden');
                if (areaSelect) areaSelect.required = true;
                if (rowDatetimeArea) rowDatetimeArea.className = 'grid grid-cols-1 sm:grid-cols-2 gap-3';

                if (typeContainer) typeContainer.classList.add('hidden');
                if (typeSelect) typeSelect.required = false;

                if (questionLabel) {
                    questionLabel.innerText = t('questionQr');
                }
                if (pill) {
                    pill.innerText = t('pillQr');
                    pill.className = 'px-2.5 py-1 rounded-full text-[10px] font-extrabold bg-blue-100 text-blue-800';
                }
                if (activeSection) activeSection.classList.add('hidden');
            } else {
                if (areaContainer) areaContainer.classList.add('hidden');
                if (areaSelect) areaSelect.required = false;
                if (rowDatetimeArea) rowDatetimeArea.className = 'grid grid-cols-1 gap-3';

                if (typeContainer) typeContainer.classList.remove('hidden');
                if (typeSelect) typeSelect.required = true;

                if (questionLabel) {
                    questionLabel.innerText = t('questionTech');
                }
                if (pill) {
                    pill.innerText = t('pillTech');
                    pill.className = 'px-2.5 py-1 rounded-full text-[10px] font-extrabold bg-emerald-100 text-emerald-800';
                }
                if (activeSection) activeSection.classList.remove('hidden');
            }
        }

        // Salir a la pantalla de inicio de sesión
        function handleLogout() {
            currentUser = null;
            isQrReporterSession = false;

            const shell = document.getElementById('app-shell');
            shell.classList.remove('max-w-7xl');
            shell.classList.add('max-w-md');

            document.getElementById('main-header').classList.add('hidden');
            document.getElementById('screen-operator').classList.add('hidden');
            document.getElementById('screen-admin').classList.add('hidden');
            document.getElementById('screen-qr-id').classList.add('hidden');
            document.getElementById('screen-language').classList.add('hidden');
            document.getElementById('modal-report-success').classList.add('hidden');
            document.getElementById('screen-login').classList.remove('hidden');

            document.getElementById('login-form').reset();
        }
        window.handleLogout = handleLogout;

        // Flujo de Identificación para Invitados por Código QR
        function openQrIdentification() {
            document.getElementById('screen-login').classList.add('hidden');
            document.getElementById('screen-qr-id').classList.remove('hidden');
            document.getElementById('qr-id-form').reset();
            document.getElementById('qr-other-container').classList.add('hidden');
            document.getElementById('qr-id-error').classList.add('hidden');
        }
        window.openQrIdentification = openQrIdentification;

        function handleQrPositionChange() {
            const select = document.getElementById('qr-position-select');
            const otherContainer = document.getElementById('qr-other-container');
            const otherInput = document.getElementById('qr-other-input');

            if (select.value === 'OTRO') {
                otherContainer.classList.remove('hidden');
                otherInput.required = true;
                otherInput.focus();
            } else {
                otherContainer.classList.add('hidden');
                otherInput.required = false;
                otherInput.value = '';
            }
        }
        window.handleQrPositionChange = handleQrPositionChange;

        function handleQrIdentifySubmit(event) {
            if (event) event.preventDefault();
            const posSelect = document.getElementById('qr-position-select').value;
            const otherText = document.getElementById('qr-other-input').value.trim();
            const personName = document.getElementById('qr-name-input').value.trim();
            const errEl = document.getElementById('qr-id-error');

            if (!posSelect || !personName || (posSelect === 'OTRO' && !otherText)) {
                errEl.classList.remove('hidden');
                return;
            }
            errEl.classList.add('hidden');

            const finalPosition = posSelect === 'OTRO' ? otherText.toUpperCase() : posSelect;
            isQrReporterSession = true;
            currentUser = {
                username: 'qr_guest',
                role: 'GUEST_QR',
                name: personName,
                position: finalPosition
            };

            enterApplicationByRole();
        }
        window.handleQrIdentifySubmit = handleQrIdentifySubmit;

        // Enviar nuevo reporte de problema
        async function handleFormSubmit(event) {
            if (event) event.preventDefault();
            const submitBtn = document.getElementById('btn-submit-ticket');
            const originalBtnHtml = submitBtn.innerHTML;

            submitBtn.disabled = true;
            submitBtn.innerHTML = `<i class="fa-solid fa-wand-magic-sparkles animate-pulse"></i> <span>${t('analyzingBtn')}</span>`;

            const problemRawInput = document.getElementById('field-problem').value.trim();
            const problemRaw = problemRawInput || t('noDescription');

            let reporterLabel = 'Técnico 1';
            let reporterDisplayName = 'Usuario';

            if (isQrReporterSession && currentUser) {
                reporterLabel = `${currentUser.name} - ${currentUser.position || 'PLANTA'} [QR Planta]`;
                reporterDisplayName = currentUser.name;
            } else if (currentUser) {
                reporterLabel = `${currentUser.name} (${currentUser.username})`;
                reporterDisplayName = currentUser.name;
            }

            const dtValue = document.getElementById('field-datetime').value || new Date().toISOString().slice(0, 16);
            const selectedFaultType = document.getElementById('field-type')
                ? document.getElementById('field-type').value
                : 'Eléctrica';
            const areaOrTypeVal = isQrReporterSession
                ? (document.getElementById('field-area').value || 'Planta General (QR)')
                : selectedFaultType;
            const brandVal = document.getElementById('field-brand').value.trim() || 'N/A';
            const serialVal = document.getElementById('field-serial').value.trim() || 'N/A';

            // Llamar a la IA Gemini ÚNICAMENTE cuando el comentario contiene caracteres chinos (Chino -> Español, no viceversa)
            const hasChineseComment = containsChineseText(problemRawInput);
            const aiInterpretation = hasChineseComment
                ? await interpretMeaningWithGeminiAI(problemRawInput, {
                    areaOrType: areaOrTypeVal,
                    brand: brandVal,
                    serial: serialVal,
                    reporter: reporterLabel
                })
                : {
                    formattedExplanation: '',
                    diagnosisSummary: ''
                };

            const newTicket = {
                id: `TK-${Math.floor(1000 + Math.random() * 9000)}`,
                datetime: dtValue,
                area: areaOrTypeVal,
                brand: brandVal,
                serial: serialVal,
                type: isQrReporterSession ? 'Reporte QR (Planta)' : selectedFaultType,
                problemOriginal: problemRaw,
                problemSpanish: aiInterpretation.formattedExplanation,
                aiDiagnosis: aiInterpretation.diagnosisSummary,
                cause: aiInterpretation.diagnosisSummary || '',
                lesson: '',
                status: 'ABIERTO',
                operatorName: reporterLabel,
                createdAt: new Date().toISOString(),
                closedAt: null
            };

            tickets.unshift(newTicket);
            saveToLocalStorage();
            if (typeof window.saveTicketToCloud === 'function') {
                await window.saveTicketToCloud(newTicket);
            }

            const parsedDate = parseTicketDate(newTicket);
            adminSelectedYear = parsedDate.getFullYear();
            adminSelectedMonth = parsedDate.getMonth();
            adminSelectedDay = null;

            document.getElementById('ticket-form').reset();
            resetDatetimeField();

            submitBtn.disabled = false;
            submitBtn.innerHTML = originalBtnHtml;

            renderOperatorTickets();
            renderAdminDashboard();

            const msgEl = document.getElementById('success-modal-message');
            if (msgEl) {
                msgEl.innerText = t('successModalMsg')(reporterDisplayName);
            }
            document.getElementById('modal-report-success').classList.remove('hidden');
        }
        window.handleFormSubmit = handleFormSubmit;

        // Botón "Reportar otro problema" sin volver a identificarse
        function handleReportAnother() {
            document.getElementById('modal-report-success').classList.add('hidden');
            document.getElementById('ticket-form').reset();
            resetDatetimeField();
        }
        window.handleReportAnother = handleReportAnother;

        // Abrir modal para resolver/cerrar problema (Función global requerida)
        function openResolutionScreen(ticketId) {
            const ticket = tickets.find(t => t.id === ticketId);
            if (!ticket) return;

            const isAdminView = (currentUser && currentUser.role === 'ADMIN' && !document.getElementById('screen-admin').classList.contains('hidden'));

            document.getElementById('resolve-ticket-id').value = ticket.id;
            const subtitle = document.getElementById('resolve-modal-subtitle');
            if (subtitle) {
                subtitle.innerText = `${ticket.id} • ${ticket.area}`;
            }

            const whatDoneInput = document.getElementById('resolve-what-done');
            const lessonInput = document.getElementById('resolve-lesson');
            const labelWhat = document.getElementById('label-resolve-what-done');
            const labelLesson = document.getElementById('label-resolve-lesson');

            whatDoneInput.value = '';
            lessonInput.value = '';
            whatDoneInput.required = !isAdminView;
            lessonInput.required = !isAdminView;

            if (labelWhat && labelLesson) {
                if (isAdminView) {
                    labelWhat.innerText = t('resolveWhatDoneOpt');
                    labelLesson.innerText = t('resolveLessonOpt');
                } else {
                    labelWhat.innerText = t('resolveWhatDoneReq');
                    labelLesson.innerText = t('resolveLessonReq');
                }
            }

            const errEl = document.getElementById('resolve-error-msg');
            if (errEl) errEl.classList.add('hidden');
            document.getElementById('modal-resolve-ticket').classList.remove('hidden');
        }
        window.openResolutionScreen = openResolutionScreen;

        // Cierre directo e inmediato exclusivo para el Panel de Administrador (sin abrir cuestionario)
        function quickCloseTicketAdmin(ticketId) {
            const ticket = tickets.find(t => t.id === ticketId);
            if (!ticket) return;

            ticket.status = 'RESUELTO';
            ticket.cause = t('closedByAdminMsg');
            ticket.lesson = t('closedByAdminLesson');

            const now = new Date();
            const hours = String(now.getHours()).padStart(2, '0');
            const minutes = String(now.getMinutes()).padStart(2, '0');
            const day = String(now.getDate()).padStart(2, '0');
            const month = String(now.getMonth() + 1).padStart(2, '0');
            const year = now.getFullYear();
            ticket.closedAt = `${hours}:${minutes} hrs (${day}/${month}/${year})`;

            saveToLocalStorage();
            if (typeof window.saveTicketToCloud === 'function') {
                window.saveTicketToCloud(ticket);
            }
            renderOperatorTickets();
            renderAdminDashboard();
        }
        window.quickCloseTicketAdmin = quickCloseTicketAdmin;

        function closeResolutionModal() {
            document.getElementById('modal-resolve-ticket').classList.add('hidden');
        }
        window.closeResolutionModal = closeResolutionModal;

        // Confirmar cierre del problema registrando la hora exacta de cierre
        function confirmResolveTicket() {
            const ticketId = document.getElementById('resolve-ticket-id').value;
            const ticket = tickets.find(t => t.id === ticketId);
            if (!ticket) return;

            const isAdminView = (currentUser && currentUser.role === 'ADMIN' && !document.getElementById('screen-admin').classList.contains('hidden'));

            const whatDoneInput = document.getElementById('resolve-what-done');
            const lessonInput = document.getElementById('resolve-lesson');
            const errEl = document.getElementById('resolve-error-msg');

            const whatDone = whatDoneInput.value.trim();
            const lesson = lessonInput.value.trim();

            if (!isAdminView && (!whatDone || !lesson)) {
                if (errEl) errEl.classList.remove('hidden');
                if (!whatDone) {
                    whatDoneInput.focus();
                } else {
                    lessonInput.focus();
                }
                return;
            }

            if (errEl) errEl.classList.add('hidden');

            ticket.status = 'RESUELTO';
            ticket.cause = whatDone || t('closedByAdminMsg');
            ticket.lesson = lesson || t('closedByAdminLesson');

            const now = new Date();
            const hours = String(now.getHours()).padStart(2, '0');
            const minutes = String(now.getMinutes()).padStart(2, '0');
            const day = String(now.getDate()).padStart(2, '0');
            const month = String(now.getMonth() + 1).padStart(2, '0');
            const year = now.getFullYear();
            ticket.closedAt = `${hours}:${minutes} hrs (${day}/${month}/${year})`;

            saveToLocalStorage();
            if (typeof window.saveTicketToCloud === 'function') {
                window.saveTicketToCloud(ticket);
            }
            closeResolutionModal();
            renderOperatorTickets();
            renderAdminDashboard();
        }
        window.confirmResolveTicket = confirmResolveTicket;

        // Abrir modal de detalles del ticket
        function openModal(ticketId) {
            const ticket = tickets.find(t => t.id === ticketId);
            if (!ticket) return;

            const showChineseToSpanishAI = containsChineseText(ticket.problemOriginal) && ticket.problemSpanish;

            document.getElementById('detail-modal-title').innerText = `${t('detailModalTitle')} ${ticket.id}`;
            document.getElementById('detail-modal-body').innerHTML = `
                <div class="flex justify-between items-center bg-slate-50 p-2.5 rounded-xl border border-slate-100">
                    <span class="font-bold text-slate-500">${t('detailState')}</span>
                    <span class="px-2.5 py-0.5 rounded-full font-extrabold text-[11px] ${ticket.status === 'RESUELTO' ? 'bg-emerald-100 text-emerald-800' : 'bg-amber-100 text-amber-800'}">
                        ${ticket.status === 'RESUELTO' ? t('statusResolved') : t('statusOpen')}
                    </span>
                </div>
                <div><span class="font-bold text-slate-500">${t('detailArea')}</span> <p class="font-bold text-slate-900 mt-0.5">${ticket.area}</p></div>
                <div><span class="font-bold text-slate-500">${t('detailEquip')}</span> <p class="font-semibold text-slate-800 mt-0.5">${ticket.brand} (${ticket.serial || 'N/A'})</p></div>
                <div><span class="font-bold text-slate-500">${t('reportedBy')}:</span> <p class="font-semibold text-slate-800 mt-0.5">${ticket.operatorName}</p></div>
                <div class="bg-slate-50 p-3 rounded-xl border border-slate-200 space-y-1.5">
                    <span class="font-extrabold text-[11px] text-slate-600 block">
                        ${t('originalDescLabel')}
                    </span>
                    <p class="font-bold text-slate-900">${ticket.problemOriginal}</p>
                    ${showChineseToSpanishAI ? `
                        <div class="border-t border-indigo-200/70 pt-2 mt-1.5">
                            <span class="font-extrabold text-[11px] text-indigo-700 flex items-center gap-1 mb-0.5">
                                <i class="fa-solid fa-wand-magic-sparkles"></i>
                                <span>${t('aiSpanishTranslationLabel')}</span>
                            </span>
                            <p class="text-indigo-950 font-semibold whitespace-pre-line leading-relaxed">${ticket.problemSpanish}</p>
                        </div>
                    ` : ''}
                </div>
                ${ticket.cause ? `
                    <div class="bg-slate-50 p-2.5 rounded-xl border border-slate-200/70">
                        <span class="font-bold text-[11px] text-slate-500 block">${ticket.status === 'RESUELTO' ? t('whatWasDoneLabel') : t('preliminaryObs')}</span>
                        <p class="font-semibold text-slate-800 mt-0.5">${ticket.cause}</p>
                    </div>
                ` : ''}
                ${ticket.closedAt ? `
                    <div class="bg-emerald-50 border border-emerald-200 p-2.5 rounded-xl text-emerald-800 font-extrabold flex items-center gap-1.5">
                        <i class="fa-regular fa-clock"></i>
                        <span>${t('closeTimeLabel')}: ${ticket.closedAt}</span>
                    </div>
                ` : ''}
            `;
            document.getElementById('modal-ticket-detail').classList.remove('hidden');
        }
        window.openModal = openModal;

        function closeDetailModal() {
            document.getElementById('modal-ticket-detail').classList.add('hidden');
        }
        window.closeDetailModal = closeDetailModal;

        // Renderizar lista de problemas activos en el panel de técnicos
        function renderOperatorTickets() {
            const container = document.getElementById('operator-tickets-list');
            const counter = document.getElementById('operator-active-count');

            const activeTickets = tickets.filter(t => t.status === 'ABIERTO');
            if (counter) {
                counter.innerText = activeTickets.length;
            }
            if (!container) return;

            if (activeTickets.length === 0) {
                container.innerHTML = `
                    <div class="text-center py-6 bg-white rounded-xl border border-dashed border-slate-200">
                        <i class="fa-solid fa-circle-check text-emerald-500 text-2xl mb-1"></i>
                        <p class="text-xs font-bold text-slate-700">${t('noActiveTickets')}</p>
                    </div>
                `;
                return;
            }

            container.innerHTML = activeTickets.map(ticket => {
                const showChineseToSpanishAI = containsChineseText(ticket.problemOriginal) && ticket.problemSpanish;
                return `
                    <div class="bg-white p-3.5 rounded-xl border border-slate-200 shadow-sm space-y-2.5">
                        <div class="flex items-center justify-between">
                            <span class="font-extrabold text-slate-800 text-xs">${ticket.id}</span>
                            <span class="px-2 py-0.5 rounded text-[10px] font-bold bg-amber-100 text-amber-800">
                                ${t('statusOpen')}
                            </span>
                        </div>

                        <div>
                            <h4 class="font-bold text-slate-900 text-xs">${ticket.area}</h4>
                            <p class="text-[11px] text-slate-500">${ticket.brand} • ${t('reportedBy')}: <strong>${ticket.operatorName}</strong></p>
                        </div>

                        <div class="bg-slate-50 p-2.5 rounded-lg text-xs border border-slate-100 space-y-1.5">
                            <span class="text-[10px] font-bold text-slate-400 block">${t('originalDescLabel')}</span>
                            <p class="text-slate-800 font-medium">${ticket.problemOriginal}</p>
                            ${showChineseToSpanishAI ? `
                                <div class="pt-1.5 border-t border-slate-200/70">
                                    <span class="text-[10px] font-extrabold text-indigo-600 flex items-center gap-1 mb-0.5">
                                        <i class="fa-solid fa-wand-magic-sparkles"></i>
                                        <span>${t('aiSpanishTranslationLabel')}</span>
                                    </span>
                                    <p class="text-[11px] text-indigo-950 font-semibold whitespace-pre-line leading-relaxed">${ticket.problemSpanish}</p>
                                </div>
                            ` : ''}
                        </div>

                        <div class="flex items-center justify-between pt-1">
                            <button type="button" onclick="openModal('${ticket.id}')" class="text-emerald-700 hover:text-emerald-800 text-xs font-extrabold flex items-center gap-1">
                                <i class="fa-solid fa-circle-info"></i>
                                <span>${t('detailsBtn')}</span>
                            </button>

                            ${!isQrReporterSession ? `
                                <button type="button" onclick="openResolutionScreen('${ticket.id}')" class="touch-active bg-emerald-600 hover:bg-emerald-700 text-white text-xs font-bold py-2 px-3.5 rounded-xl shadow-sm flex items-center gap-1">
                                    <i class="fa-solid fa-check"></i>
                                    <span>${t('resolvedBtn')}</span>
                                </button>
                            ` : `
                                <span class="text-[11px] text-slate-400 italic">${t('qrPlantTag')}</span>
                            `}
                        </div>
                    </div>
                `;
            }).join('');
        }
        window.renderOperatorTickets = renderOperatorTickets;

        // Utilidad para obtener fecha de un ticket
        function parseTicketDate(ticket) {
            if (ticket.datetime) {
                const d = new Date(ticket.datetime);
                if (!isNaN(d.getTime())) return d;
            }
            if (ticket.createdAt) {
                const d2 = new Date(ticket.createdAt);
                if (!isNaN(d2.getTime())) return d2;
            }
            return new Date();
        }

        // Funciones del Calendario y Filtros del Panel de Administrador
        function changeCalendarMonth(delta) {
            adminSelectedMonth += delta;
            if (adminSelectedMonth < 0) {
                adminSelectedMonth = 11;
                adminSelectedYear--;
            } else if (adminSelectedMonth > 11) {
                adminSelectedMonth = 0;
                adminSelectedYear++;
            }
            adminSelectedDay = null;

            const monthSelect = document.getElementById('admin-cal-month');
            const yearSelect = document.getElementById('admin-cal-year');
            if (monthSelect) monthSelect.value = String(adminSelectedMonth);
            if (yearSelect) yearSelect.value = String(adminSelectedYear);

            renderAdminDashboard();
        }
        window.changeCalendarMonth = changeCalendarMonth;

        function handleMonthYearSelect() {
            const m = parseInt(document.getElementById('admin-cal-month').value, 10);
            const y = parseInt(document.getElementById('admin-cal-year').value, 10);
            if (!isNaN(m)) adminSelectedMonth = m;
            if (!isNaN(y)) adminSelectedYear = y;
            adminSelectedDay = null;
            renderAdminDashboard();
        }
        window.handleMonthYearSelect = handleMonthYearSelect;

        function selectCalendarDay(dayNumber) {
            if (adminSelectedDay === dayNumber) {
                adminSelectedDay = null;
            } else {
                adminSelectedDay = dayNumber;
            }
            renderAdminDashboard();
        }
        window.selectCalendarDay = selectCalendarDay;

        function clearCalendarDayFilter() {
            adminSelectedDay = null;
            renderAdminDashboard();
        }
        window.clearCalendarDayFilter = clearCalendarDayFilter;

        function setAdminTab(tab) {
            adminActiveTab = tab;
            ['ALL', 'ABIERTO', 'RESUELTO'].forEach(t => {
                const btn = document.getElementById(`tab-btn-${t}`);
                if (!btn) return;
                if (t === tab) {
                    btn.className = 'px-3 py-2 rounded-lg text-xs font-extrabold transition bg-white text-slate-900 shadow-sm';
                } else {
                    btn.className = 'px-3 py-2 rounded-lg text-xs font-extrabold transition text-slate-600 hover:text-slate-900';
                }
            });
            renderAdminDashboard();
        }
        window.setAdminTab = setAdminTab;

        function openTechnicianViewFromAdmin() {
            document.getElementById('screen-admin').classList.add('hidden');
            document.getElementById('screen-operator').classList.remove('hidden');
            configureOperatorFormForMode();
            resetDatetimeField();
            renderOperatorTickets();
        }
        window.openTechnicianViewFromAdmin = openTechnicianViewFromAdmin;

        // =====================================================
        // GESTIÓN DE USUARIOS Y CONTRASEÑAS (PANEL DE ADMIN)
        // =====================================================
        function showUserFeedback(msg, isError = false) {
            const box = document.getElementById('admin-user-feedback');
            if (!box) return;
            box.innerText = msg;
            box.className = `text-[11px] font-bold px-2.5 py-1.5 rounded-lg text-center ${
                isError
                    ? 'bg-rose-50 text-rose-700 border border-rose-200'
                    : 'bg-emerald-50 text-emerald-700 border border-emerald-200'
            }`;
            box.classList.remove('hidden');
            setTimeout(() => {
                box.classList.add('hidden');
            }, 3200);
        }

        function renderAdminUsersList() {
            const container = document.getElementById('admin-users-list');
            const badge = document.getElementById('admin-users-count-badge');
            if (!container) return;

            const userList = Object.values(USERS);
            if (badge) {
                badge.innerText = `${userList.length} ${userList.length === 1 ? t('accCountSingular') : t('accCountPlural')}`;
            }

            const adminCount = userList.filter(u => u.role === 'ADMIN').length;

            container.innerHTML = userList.map(u => {
                const isAdminRole = u.role === 'ADMIN';
                const isOnlyAdmin = isAdminRole && adminCount <= 1;

                return `
                    <div class="bg-white p-2.5 rounded-xl border border-slate-200 shadow-sm flex items-center justify-between gap-2">
                        <div class="min-w-0 flex-1">
                            <div class="flex items-center gap-1.5 flex-wrap">
                                <span class="text-xs font-black text-slate-900">${u.username}</span>
                                <span class="px-2 py-0.5 rounded-md text-[10px] font-extrabold ${
                                    isAdminRole ? 'bg-blue-100 text-blue-800' : 'bg-emerald-100 text-emerald-800'
                                }">
                                    ${isAdminRole ? t('roleAdmin').toUpperCase() : t('roleTech').toUpperCase()}
                                </span>
                            </div>
                            <p class="text-[11px] text-slate-600 font-semibold truncate">${u.name}</p>
                            <p class="text-[11px] text-slate-500 font-mono mt-0.5">
                                <i class="fa-solid fa-key text-amber-500 mr-1"></i>${t('passLabel')}: <strong class="text-slate-800 bg-slate-100 px-1.5 py-0.5 rounded">${u.pass}</strong>
                            </p>
                        </div>

                        <div class="flex items-center gap-1 shrink-0">
                            <button type="button" onclick="prefillEditUser('${u.username}')"
                                class="p-2 rounded-lg bg-slate-100 hover:bg-blue-50 text-slate-600 hover:text-blue-700 text-xs transition">
                                <i class="fa-solid fa-pen-to-square"></i>
                            </button>
                            ${!isOnlyAdmin ? `
                                <button type="button" onclick="handleDeleteUserAccount('${u.username}')"
                                    class="p-2 rounded-lg bg-rose-50 hover:bg-rose-600 text-rose-600 hover:text-white text-xs transition">
                                    <i class="fa-solid fa-trash-can"></i>
                                </button>
                            ` : `
                                <span class="text-[10px] font-bold text-slate-400 px-1.5">
                                    <i class="fa-solid fa-shield-halved"></i>
                                </span>
                            `}
                        </div>
                    </div>
                `;
            }).join('');
        }
        window.renderAdminUsersList = renderAdminUsersList;

        function prefillEditUser(usernameKey) {
            const u = USERS[usernameKey];
            if (!u) return;
            document.getElementById('new-account-username').value = u.username;
            document.getElementById('new-account-pass').value = u.pass;
            document.getElementById('new-account-name').value = u.name;
            document.getElementById('new-account-role').value = u.role;
            document.getElementById('new-account-pass').focus();
        }
        window.prefillEditUser = prefillEditUser;

        function handleSaveUserAccount(event) {
            if (event) event.preventDefault();
            const rawUsername = document.getElementById('new-account-username').value.trim().toLowerCase();
            const rawPass = document.getElementById('new-account-pass').value.trim();
            const rawName = document.getElementById('new-account-name').value.trim();
            const rawRole = document.getElementById('new-account-role').value || 'OPERATOR';

            if (!rawUsername || !rawPass || !rawName) {
                showUserFeedback(t('userMissingFields'), true);
                return;
            }

            const existed = Boolean(USERS[rawUsername]);
            USERS[rawUsername] = {
                username: rawUsername,
                pass: rawPass,
                role: rawRole,
                name: rawName
            };

            saveUsersToLocalStorage();
            renderAdminUsersList();
            document.getElementById('admin-user-form').reset();

            showUserFeedback(
                existed
                    ? t('userUpdated')(rawUsername)
                    : t('userAdded')(rawUsername)
            );
        }
        window.handleSaveUserAccount = handleSaveUserAccount;

        function handleDeleteUserAccount(usernameKey) {
            const target = USERS[usernameKey];
            if (!target) return;

            const adminCount = Object.values(USERS).filter(u => u.role === 'ADMIN').length;
            if (target.role === 'ADMIN' && adminCount <= 1) {
                showUserFeedback(t('userCantDeleteAdmin'), true);
                return;
            }

            delete USERS[usernameKey];
            saveUsersToLocalStorage();
            renderAdminUsersList();
            showUserFeedback(t('userDeleted')(usernameKey));
        }
        window.handleDeleteUserAccount = handleDeleteUserAccount;

        // Renderizar Panel de Administrador (Calendario + Tickets Abiertos y Resueltos)
        function renderAdminDashboard() {
            const grid = document.getElementById('admin-calendar-grid');
            const listContainer = document.getElementById('admin-tickets-container');
            if (!grid || !listContainer) return;

            const monthNames = t('months');

            // Filtrar tickets del mes y año seleccionados
            const monthTickets = tickets.filter(ticket => {
                const d = parseTicketDate(ticket);
                return d.getFullYear() === adminSelectedYear && d.getMonth() === adminSelectedMonth;
            });

            // Construir el calendario del mes
            const firstDayOfWeek = new Date(adminSelectedYear, adminSelectedMonth, 1).getDay();
            const daysInMonth = new Date(adminSelectedYear, adminSelectedMonth + 1, 0).getDate();

            let calHtml = '';
            for (let i = 0; i < firstDayOfWeek; i++) {
                calHtml += `<div class="h-10"></div>`;
            }

            for (let day = 1; day <= daysInMonth; day++) {
                const dayTickets = monthTickets.filter(ticket => parseTicketDate(ticket).getDate() === day);
                const hasOpen = dayTickets.some(ticket => ticket.status === 'ABIERTO');
                const hasResolved = dayTickets.some(ticket => ticket.status === 'RESUELTO');
                const isSelected = adminSelectedDay === day;

                calHtml += `
                    <button type="button" onclick="selectCalendarDay(${day})"
                        class="h-10 rounded-xl flex flex-col items-center justify-center relative border transition ${
                            isSelected
                                ? 'bg-slate-900 text-white border-slate-900 font-black shadow-sm'
                                : dayTickets.length > 0
                                    ? 'bg-slate-50 hover:bg-emerald-50 text-slate-800 border-slate-200 font-bold'
                                    : 'bg-white hover:bg-slate-50 text-slate-500 border-transparent font-medium'
                        } text-xs">
                        <span>${day}</span>
                        <div class="flex items-center gap-0.5 mt-0.5">
                            ${hasOpen ? `<span class="w-1.5 h-1.5 rounded-full bg-amber-500"></span>` : ''}
                            ${hasResolved ? `<span class="w-1.5 h-1.5 rounded-full bg-emerald-500"></span>` : ''}
                        </div>
                    </button>
                `;
            }
            grid.innerHTML = calHtml;

            const periodTickets = adminSelectedDay
                ? monthTickets.filter(ticket => parseTicketDate(ticket).getDate() === adminSelectedDay)
                : monthTickets;

            const openCount = periodTickets.filter(ticket => ticket.status === 'ABIERTO').length;
            const resolvedCount = periodTickets.filter(ticket => ticket.status === 'RESUELTO').length;

            document.getElementById('admin-kpi-total').innerText = periodTickets.length;
            document.getElementById('admin-kpi-open').innerText = openCount;
            document.getElementById('admin-kpi-resolved').innerText = resolvedCount;
            document.getElementById('admin-kpi-period-label').innerText = adminSelectedDay
                ? `${adminSelectedDay} - ${monthNames[adminSelectedMonth]} ${adminSelectedYear}`
                : `${monthNames[adminSelectedMonth]} ${adminSelectedYear}`;

            const scopeBadge = document.getElementById('excel-export-scope-badge');
            const selectedBtnLabel = document.getElementById('btn-excel-selected-label');
            if (scopeBadge) {
                scopeBadge.innerText = adminSelectedDay
                    ? `${t('excelScopeDay')} ${adminSelectedDay} ${monthNames[adminSelectedMonth]}`
                    : `${t('excelScopeMonth')}: ${monthNames[adminSelectedMonth]} ${adminSelectedYear}`;
            }
            if (selectedBtnLabel) {
                selectedBtnLabel.innerText = adminSelectedDay
                    ? `${t('excelBtnDay')} (${adminSelectedDay})`
                    : t('excelBtnMonth');
            }

            const searchQuery = (document.getElementById('admin-search-input')?.value || '').trim().toLowerCase();

            const filteredTickets = periodTickets.filter(ticket => {
                if (adminActiveTab !== 'ALL' && ticket.status !== adminActiveTab) return false;
                if (searchQuery) {
                    const haystack = `${ticket.id} ${ticket.area} ${ticket.brand} ${ticket.operatorName} ${ticket.problemOriginal} ${ticket.problemSpanish}`.toLowerCase();
                    if (!haystack.includes(searchQuery)) return false;
                }
                return true;
            });

            if (filteredTickets.length === 0) {
                listContainer.innerHTML = `
                    <div class="bg-white rounded-2xl border border-dashed border-slate-300 p-10 text-center space-y-2">
                        <i class="fa-regular fa-folder-open text-3xl text-slate-400"></i>
                        <p class="text-sm font-extrabold text-slate-700">${t('noFilteredTickets')}</p>
                        <p class="text-xs text-slate-500">${t('noFilteredSub')}</p>
                    </div>
                `;
                return;
            }

            listContainer.innerHTML = filteredTickets.map(ticket => {
                const isResolved = ticket.status === 'RESUELTO';
                const hasChineseComment = containsChineseText(ticket.problemOriginal);
                const showChineseToSpanishAI = hasChineseComment && ticket.problemSpanish;

                return `
                    <div class="bg-white rounded-2xl border ${isResolved ? 'border-emerald-200' : 'border-amber-200'} shadow-sm p-5 space-y-3.5">
                        <div class="flex flex-wrap items-start justify-between gap-2 border-b border-slate-100 pb-3">
                            <div>
                                <div class="flex items-center gap-2">
                                    <span class="text-xs font-black px-2.5 py-0.5 rounded-lg bg-slate-900 text-white">${ticket.id}</span>
                                    <span class="px-2.5 py-0.5 rounded-full text-[11px] font-extrabold ${
                                        isResolved ? 'bg-emerald-100 text-emerald-800' : 'bg-amber-100 text-amber-800'
                                    }">
                                        ${isResolved ? t('statusResolved') : t('statusOpen')}
                                    </span>
                                    <span class="text-xs text-slate-400 font-semibold">
                                        <i class="fa-regular fa-calendar mr-1"></i>${ticket.datetime.replace('T', ' ')}
                                    </span>
                                </div>
                                <h4 class="text-sm font-extrabold text-slate-900 mt-1.5">${ticket.area}</h4>
                                <p class="text-xs text-slate-500 font-medium">
                                    ${t('equipmentLabel')}: <strong>${ticket.brand}</strong> (${t('serialShort')}: ${ticket.serial || 'N/A'}) • ${t('reportedBy')}: <strong class="text-slate-800">${ticket.operatorName}</strong>
                                </p>
                            </div>

                            ${isResolved && ticket.closedAt ? `
                                <div class="bg-emerald-50 border border-emerald-200 rounded-xl px-3 py-2 text-right">
                                    <span class="text-[10px] font-extrabold text-emerald-600 uppercase block">${t('closeTimeLabel')}</span>
                                    <span class="text-xs font-black text-emerald-900 flex items-center gap-1">
                                        <i class="fa-regular fa-clock"></i> ${ticket.closedAt}
                                    </span>
                                </div>
                            ` : ''}
                        </div>

                        <!-- Descripción Original y (solo si fue escrito en Chino) su Traducción/Interpretación IA a Español -->
                        <div class="bg-slate-50 rounded-xl p-3.5 border border-slate-200/80 space-y-2">
                            <div class="flex flex-wrap items-center justify-between gap-2">
                                <span class="text-[11px] font-extrabold text-slate-500 uppercase block">
                                    ${t('originalDescLabel')} (${ticket.operatorName}):
                                </span>
                                ${hasChineseComment ? `
                                    <button type="button" id="btn-ai-reanalyze-${ticket.id}" onclick="reanalyzeTicketWithAI('${ticket.id}')"
                                        class="touch-active text-[11px] font-extrabold px-2.5 py-1 rounded-lg bg-indigo-100 hover:bg-indigo-200 text-indigo-800 flex items-center gap-1 transition">
                                        <i class="fa-solid fa-wand-magic-sparkles"></i>
                                        <span>${t('reanalyzeBtn')}</span>
                                    </button>
                                ` : ''}
                            </div>
                            <p class="text-xs font-bold text-slate-900 bg-white px-3 py-2 rounded-lg border border-slate-200/70">${ticket.problemOriginal}</p>

                            ${showChineseToSpanishAI ? `
                                <div class="bg-indigo-50/90 border border-indigo-200/80 rounded-xl p-3 space-y-1">
                                    <div class="flex items-center gap-1.5 text-[11px] font-black text-indigo-800 uppercase">
                                        <i class="fa-solid fa-brain text-indigo-600"></i>
                                        <span>${t('aiSpanishTranslationLabel')}</span>
                                    </div>
                                    <p class="text-xs font-semibold text-indigo-950 whitespace-pre-line leading-relaxed">${ticket.problemSpanish}</p>
                                </div>
                            ` : ''}
                        </div>

                        <!-- Detalles de Solución o Acciones -->
                        ${isResolved ? `
                            <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
                                <div class="bg-emerald-50/70 p-3 rounded-xl border border-emerald-200/80">
                                    <span class="text-[10px] font-extrabold text-emerald-700 uppercase block">
                                        ${t('whatWasDoneLabel')}
                                    </span>
                                    <p class="text-xs font-bold text-slate-800 mt-1">${ticket.cause || '-'}</p>
                                </div>
                                <div class="bg-blue-50/70 p-3 rounded-xl border border-blue-200/80">
                                    <span class="text-[10px] font-extrabold text-blue-700 uppercase block">
                                        ${t('lessonLearnedLabel')}
                                    </span>
                                    <p class="text-xs font-bold text-slate-800 mt-1">${ticket.lesson || '-'}</p>
                                </div>
                            </div>
                        ` : `
                            <div class="flex flex-wrap items-center justify-between gap-2 pt-1">
                                <div class="text-xs text-slate-600">
                                    ${ticket.cause ? `<span class="font-bold text-slate-400">${t('preliminaryObs')}</span> ${ticket.cause}` : ''}
                                </div>
                                <div class="flex flex-wrap items-center gap-2">
                                    <button type="button" onclick="openModal('${ticket.id}')"
                                        class="px-3 py-1.5 rounded-xl border border-slate-300 text-slate-700 hover:bg-slate-100 text-xs font-bold">
                                        ${t('viewSheetBtn')}
                                    </button>
                                    <button type="button" onclick="openResolutionScreen('${ticket.id}')"
                                        class="px-3 py-1.5 rounded-xl border border-emerald-300 bg-emerald-50 hover:bg-emerald-100 text-emerald-800 text-xs font-bold">
                                        ${t('withQuestionnaireBtn')}
                                    </button>
                                    <button type="button" onclick="quickCloseTicketAdmin('${ticket.id}')"
                                        class="touch-active px-3.5 py-1.5 rounded-xl bg-emerald-600 hover:bg-emerald-700 text-white text-xs font-extrabold shadow-sm flex items-center gap-1.5">
                                        <i class="fa-solid fa-bolt"></i>
                                        <span>${t('directCloseBtn')}</span>
                                    </button>
                                </div>
                            </div>
                        `}
                    </div>
                `;
            }).join('');
        }
        window.renderAdminDashboard = renderAdminDashboard;

        // Exportar reportes a un archivo de Excel (.xls con soporte UTF-8 para Chino y Español)
        function exportTicketsToExcel(mode) {
            const monthNames = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre'];

            // Filtrar los tickets del mes seleccionado
            const monthTickets = tickets.filter(t => {
                const d = parseTicketDate(t);
                return d.getFullYear() === adminSelectedYear && d.getMonth() === adminSelectedMonth;
            });

            // Si mode === 'SELECTED' y hay un día seleccionado en el calendario, exportar ese día; de lo contrario, todo el mes
            const useDayFilter = (mode === 'SELECTED' && adminSelectedDay !== null);
            const dataToExport = useDayFilter
                ? monthTickets.filter(t => parseTicketDate(t).getDate() === adminSelectedDay)
                : monthTickets;

            const periodTitle = useDayFilter
                ? `${adminSelectedDay}_${monthNames[adminSelectedMonth]}_${adminSelectedYear}`
                : `Mes_${monthNames[adminSelectedMonth]}_${adminSelectedYear}`;

            const escapeHtml = (str) => String(str ?? '')
                .replace(/&/g, '&amp;')
                .replace(/</g, '&lt;')
                .replace(/>/g, '&gt;')
                .replace(/"/g, '&quot;');

            const rowsHtml = dataToExport.map(t => `
                <tr>
                    <td style="border:1px solid #cbd5e1; padding:6px; font-weight:bold;">${escapeHtml(t.id)}</td>
                    <td style="border:1px solid #cbd5e1; padding:6px; background-color:${t.status === 'RESUELTO' ? '#dcfce7' : '#fef3c7'}; font-weight:bold;">
                        ${t.status === 'RESUELTO' ? '已解决 / RESUELTO' : '待处理 / ABIERTO'}
                    </td>
                    <td style="border:1px solid #cbd5e1; padding:6px;">${escapeHtml((t.datetime || '').replace('T', ' '))}</td>
                    <td style="border:1px solid #cbd5e1; padding:6px;">${escapeHtml(t.area)}</td>
                    <td style="border:1px solid #cbd5e1; padding:6px;">${escapeHtml(t.brand)}</td>
                    <td style="border:1px solid #cbd5e1; padding:6px;">${escapeHtml(t.serial || 'N/A')}</td>
                    <td style="border:1px solid #cbd5e1; padding:6px;">${escapeHtml(t.operatorName)}</td>
                    <td style="border:1px solid #cbd5e1; padding:6px;">${escapeHtml(t.problemOriginal)}</td>
                    <td style="border:1px solid #cbd5e1; padding:6px;">${escapeHtml(t.problemSpanish)}</td>
                    <td style="border:1px solid #cbd5e1; padding:6px;">${escapeHtml(t.cause || '')}</td>
                    <td style="border:1px solid #cbd5e1; padding:6px;">${escapeHtml(t.lesson || '')}</td>
                    <td style="border:1px solid #cbd5e1; padding:6px; font-weight:bold;">${escapeHtml(t.closedAt || 'Pendiente / 待处理')}</td>
                </tr>
            `).join('');

            const excelTemplate = `
                <html xmlns:o="urn:schemas-microsoft-com:office:office" xmlns:x="urn:schemas-microsoft-com:office:excel" xmlns="http://www.w3.org/TR/REC-html40">
                <head>
                    <meta charset="UTF-8">
                    <!--[if gte mso 9]>
                    <xml>
                        <x:ExcelWorkbook>
                            <x:ExcelWorksheets>
                                <x:ExcelWorksheet>
                                    <x:Name>Reporte_PPM_${periodTitle}</x:Name>
                                    <x:WorksheetOptions><x:DisplayGridlines/></x:WorksheetOptions>
                                </x:ExcelWorksheet>
                            </x:ExcelWorksheets>
                        </x:ExcelWorkbook>
                    </xml>
                    <![endif]-->
                </head>
                <body>
                    <table style="border-collapse:collapse; font-family:Arial, sans-serif; font-size:12px;">
                        <thead>
                            <tr>
                                <th colspan="12" style="background-color:#0f172a; color:#ffffff; padding:10px; font-size:14px; text-align:left;">
                                    PPM 工厂维护系统 - Reporte de Mantenimiento (${escapeHtml(periodTitle.replace(/_/g, ' '))})
                                </th>
                            </tr>
                            <tr style="background-color:#16a34a; color:#ffffff; font-weight:bold;">
                                <th style="border:1px solid #cbd5e1; padding:8px;">ID 工单</th>
                                <th style="border:1px solid #cbd5e1; padding:8px;">状态 / Estado</th>
                                <th style="border:1px solid #cbd5e1; padding:8px;">日期时间 / Fecha y Hora</th>
                                <th style="border:1px solid #cbd5e1; padding:8px;">区域 / Área</th>
                                <th style="border:1px solid #cbd5e1; padding:8px;">品牌型号 / Marca y Modelo</th>
                                <th style="border:1px solid #cbd5e1; padding:8px;">序列号 / N° Serie</th>
                                <th style="border:1px solid #cbd5e1; padding:8px;">报告人 / Reportado por</th>
                                <th style="border:1px solid #cbd5e1; padding:8px;">故障描述 (原文) / Problema Reportado</th>
                                <th style="border:1px solid #cbd5e1; padding:8px;">翻译 / Traducción</th>
                                <th style="border:1px solid #cbd5e1; padding:8px;">解决措施 / Qué se hizo</th>
                                <th style="border:1px solid #cbd5e1; padding:8px;">教训与预防 / Lección Aprendida</th>
                                <th style="border:1px solid #cbd5e1; padding:8px;">关闭时间 / Hora de Cierre</th>
                            </tr>
                        </thead>
                        <tbody>
                            ${rowsHtml || `<tr><td colspan="12" style="padding:12px; text-align:center;">Sin registros en este periodo / 该期间无记录</td></tr>`}
                        </tbody>
                    </table>
                </body>
                </html>
            `;

            const blob = new Blob(['\ufeff', excelTemplate], { type: 'application/vnd.ms-excel;charset=utf-8;' });
            const url = URL.createObjectURL(blob);
            const link = document.createElement('a');
            link.href = url;
            link.download = `Reporte_Planta_PPM_${periodTitle}.xls`;
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            URL.revokeObjectURL(url);
        }
        window.exportTicketsToExcel = exportTicketsToExcel;

        // Control de Pantalla de Carga (Splash Screen) y Detección de Conexión
        function initSplashAndNetwork() {
            const splash = document.getElementById('splash-screen');
            const offlineMsg = document.getElementById('splash-offline-msg');

            function updateNetworkStatus() {
                if (!navigator.onLine) {
                    splash.classList.remove('hidden', 'opacity-0', 'pointer-events-none');
                    if (offlineMsg) offlineMsg.classList.remove('hidden');
                } else {
                    if (offlineMsg) offlineMsg.classList.add('hidden');
                }
            }

            window.addEventListener('offline', updateNetworkStatus);
            window.addEventListener('online', () => {
                updateNetworkStatus();
                setTimeout(() => {
                    splash.classList.add('opacity-0', 'pointer-events-none');
                }, 400);
            });

            // Ocultar pantalla de carga tras la animación inicial si hay conexión
            setTimeout(() => {
                if (navigator.onLine !== false) {
                    splash.classList.add('opacity-0', 'pointer-events-none');
                } else {
                    updateNetworkStatus();
                }
            }, 2100);
        }

        // Inicialización al cargar la página
        window.addEventListener('DOMContentLoaded', () => {
            try {
                const savedLang = localStorage.getItem(LANG_STORAGE_KEY);
                if (savedLang && I18N[savedLang]) {
                    currentLang = savedLang;
                }
            } catch (e) {}

            loadUsersFromLocalStorage();
            loadFromLocalStorage();
            applyLanguageToStaticUI();
            resetDatetimeField();
            initSplashAndNetwork();

            try {
                const savedQrUrl = localStorage.getItem(CUSTOM_QR_URL_KEY);
                const qrInput = document.getElementById('qr-custom-url-input');
                if (qrInput && savedQrUrl) qrInput.value = savedQrUrl;
            } catch (e) {}
            updatePlantQrCode();
        });
    </script>

    <!-- =====================================================
         CONEXIÓN EN TIEMPO REAL CON FIREBASE FIRESTORE (NUBE)
         Sincroniza todos los reportes de QR, Técnicos y Admin
         en cualquier teléfono o computadora al instante
         ===================================================== -->
    <script type="module">
        import { initializeApp, getApps } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, setDoc, collection, onSnapshot } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        let db = null;
        let auth = null;
        let currentAuthUser = null;
        let activeAppId = typeof __app_id !== 'undefined' ? __app_id : 'ppm-planta-industrial';

        function setCloudStatusUI(connected, labelText) {
            const dot = document.getElementById('cloud-status-dot');
            const text = document.getElementById('cloud-status-text');
            if (dot) {
                dot.className = connected
                    ? 'w-2 h-2 rounded-full bg-emerald-400'
                    : 'w-2 h-2 rounded-full bg-amber-400 animate-pulse';
            }
            if (text) {
                text.innerText = labelText;
            }
        }

        function resolveFirebaseConfig() {
            if (typeof HARDCODED_FIREBASE_CONFIG !== 'undefined' && HARDCODED_FIREBASE_CONFIG && HARDCODED_FIREBASE_CONFIG.apiKey) {
                return HARDCODED_FIREBASE_CONFIG;
            }
            try {
                const savedCustom = localStorage.getItem('ppm_custom_firebase_config_v1');
                if (savedCustom) {
                    const parsed = JSON.parse(savedCustom);
                    if (parsed && parsed.apiKey) return parsed;
                }
            } catch (e) {}

            if (typeof __firebase_config !== 'undefined' && __firebase_config) {
                try {
                    return JSON.parse(__firebase_config);
                } catch (e) {}
            }
            return null;
        }

        async function initCloudFirebase() {
            const firebaseConfig = resolveFirebaseConfig();
            if (!firebaseConfig) {
                setCloudStatusUI(false, 'Modo Local (Configura Firebase)');
                return;
            }

            try {
                const appName = firebaseConfig.projectId || 'ppm-app';
                const existingApp = getApps().find(a => a.name === appName);
                const app = existingApp || initializeApp(firebaseConfig, appName);
                auth = getAuth(app);
                db = getFirestore(app);

                // REGLA 3: Autenticar primero antes de cualquier consulta a Firestore
                if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token && !localStorage.getItem('ppm_custom_firebase_config_v1')) {
                    await signInWithCustomToken(auth, __initial_auth_token);
                } else {
                    await signInAnonymously(auth);
                }

                onAuthStateChanged(auth, async (user) => {
                    currentAuthUser = user;
                    if (!user) return;

                    setCloudStatusUI(true, 'Nube Conectada (Tiempo Real)');

                    // REGLA 1 y 2: Rutas estrictas y consulta simple sin filtros complejos
                    const ticketsColRef = collection(db, 'artifacts', activeAppId, 'public', 'data', 'tickets');
                    onSnapshot(
                        ticketsColRef,
                        (snapshot) => {
                            if (snapshot.empty) {
                                // Si la nube está vacía, subimos los tickets locales iniciales
                                tickets.forEach(t => window.saveTicketToCloud(t));
                                return;
                            }
                            const cloudTickets = [];
                            snapshot.forEach(docSnap => {
                                const data = docSnap.data();
                                if (data && data.id) cloudTickets.push(data);
                            });
                            // Ordenar en memoria del más reciente al más antiguo
                            cloudTickets.sort((a, b) => new Date(b.createdAt || b.datetime || 0) - new Date(a.createdAt || a.datetime || 0));
                            tickets.splice(0, tickets.length, ...cloudTickets);
                            window.saveToLocalStorage();
                            window.renderOperatorTickets();
                            window.renderAdminDashboard();
                        },
                        (error) => {
                            console.warn('Error sincronizando tickets en Firestore:', error);
                            setCloudStatusUI(false, 'Revisar reglas Firestore');
                        }
                    );

                    // Sincronizar también cuentas de usuarios entre dispositivos
                    const usersDocRef = doc(db, 'artifacts', activeAppId, 'public', 'data', 'users', 'accounts_map');
                    onSnapshot(
                        usersDocRef,
                        (docSnap) => {
                            if (docSnap.exists()) {
                                const data = docSnap.data();
                                if (data && data.accountsJson) {
                                    try {
                                        const parsedUsers = JSON.parse(data.accountsJson);
                                        Object.assign(USERS, parsedUsers);
                                        USERS['123'] = { username: '123', pass: '123', role: 'ADMIN', name: 'Administrador de Planta' };
                                        window.renderAdminUsersList();
                                    } catch (e) {}
                                }
                            } else {
                                window.syncUsersToCloud(USERS);
                            }
                        },
                        (err) => {
                            console.warn('Error sincronizando usuarios en Firestore:', err);
                        }
                    );
                });
            } catch (err) {
                console.warn('Error inicializando Firebase:', err);
                setCloudStatusUI(false, 'Sin conexión Firebase');
            }
        }

        window.saveTicketToCloud = async function(ticket) {
            if (!db || !currentAuthUser || !ticket || !ticket.id) return;
            try {
                const ticketRef = doc(db, 'artifacts', activeAppId, 'public', 'data', 'tickets', ticket.id);
                await setDoc(ticketRef, ticket);
            } catch (err) {
                console.warn('No se pudo guardar el ticket en la nube:', err);
            }
        };

        window.syncUsersToCloud = async function(usersObj) {
            if (!db || !currentAuthUser || !usersObj) return;
            try {
                const usersRef = doc(db, 'artifacts', activeAppId, 'public', 'data', 'users', 'accounts_map');
                await setDoc(usersRef, {
                    accountsJson: JSON.stringify(usersObj),
                    updatedAt: new Date().toISOString()
                });
            } catch (err) {
                console.warn('No se pudieron sincronizar usuarios en la nube:', err);
            }
        };

        window.initCloudFirebase = initCloudFirebase;
        initCloudFirebase();
    </script>
</body>
</html>
