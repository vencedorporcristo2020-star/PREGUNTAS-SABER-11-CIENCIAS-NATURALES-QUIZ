<!DOCTYPE html>
<html lang="es" class="h-full bg-slate-50">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Taller de Física y Química: Leyes de Gases y Energía</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=Merriweather:ital,wght@0,300;0,400;0,700;1,300;1,400&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        serif: ['Merriweather', 'serif'],
                    },
                    colors: {
                        brand: {
                            50: '#f0f9ff',
                            100: '#e0f2fe',
                            500: '#0284c7',
                            600: '#0369a1',
                            700: '#075985',
                            800: '#0c4a6e',
                            900: '#0f172a',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        .custom-scrollbar::-webkit-scrollbar {
            width: 6px;
        }
        .custom-scrollbar::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
</head>
<body class="h-full font-sans text-slate-800 flex flex-col justify-between antialiased selection:bg-brand-500 selection:text-white">

    <header class="bg-brand-900 text-white border-b border-slate-800 sticky top-0 z-50 shadow-md">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
            <div class="flex items-center space-x-3">
                <div class="bg-brand-500 text-white font-black px-2.5 py-1 rounded-lg text-xs sm:text-sm tracking-wider uppercase">
                    FÍSICA / QUÍMICA
                </div>
                <div>
                    <h1 class="text-sm sm:text-base font-bold tracking-tight text-white leading-none">Gases, Energía y Trabajo</h1>
                    <p class="text-[10px] sm:text-xs text-slate-400 mt-0.5">10 Preguntas con Ilustrales Gráficas</p>
                </div>
            </div>
            
            <div class="flex items-center space-x-2 sm:space-x-4">
                <button id="open-grid-btn" class="hidden sm:flex items-center space-x-1.5 text-xs bg-slate-800 hover:bg-slate-700 text-slate-200 px-3 py-1.5 rounded-lg border border-slate-700 transition">
                    <span>📱 Matriz (1-10)</span>
                </button>
                <span id="question-tracker" class="text-xs sm:text-sm font-medium bg-slate-800 px-3 py-1.5 rounded-full border border-slate-700 text-slate-300">
                    <span id="current-q-num" class="text-white font-bold">1</span> / <span id="total-q-num">10</span>
                </span>
                <button id="reset-btn" class="text-xs text-slate-400 hover:text-white underline transition">Reiniciar</button>
            </div>
        </div>
        <!-- Progress Bar -->
        <div class="w-full bg-slate-800 h-1.5">
            <div id="progress-bar" class="bg-brand-500 h-1.5 transition-all duration-300 ease-out" style="width: 10%"></div>
        </div>
    </header>

    <main class="flex-1 max-w-7xl w-full mx-auto p-3 sm:p-6 lg:p-8 flex flex-col justify-center">
        
        <!-- Welcome View -->
        <div id="welcome-view" class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6 sm:p-10 my-auto max-w-3xl mx-auto text-center">
            <div class="w-16 h-16 bg-brand-100 text-brand-600 rounded-2xl flex items-center justify-center mx-auto mb-5 text-3xl font-bold shadow-inner">
                ⚡
            </div>
            <h2 class="text-2xl sm:text-3xl font-extrabold text-slate-900 mb-3 tracking-tight">Taller Evaluativo Interactivo</h2>
            <p class="text-slate-600 mb-6 leading-relaxed text-sm sm:text-base">
                Este simulador abarca los conceptos clave de la <strong class="text-slate-900">Ley de los Gases, Energía Potencial Gravitacional, Energía Cinética y Trabajo Mecánico</strong>. Incluye esquemas vectoriales e ilustraciones didácticas para cada situación problema.
            </p>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-3 text-left mb-6 text-xs sm:text-sm">
                <div class="p-3.5 bg-slate-50 rounded-xl border border-slate-200">
                    <span class="inline-block px-2 py-0.5 bg-blue-100 text-blue-800 rounded font-bold text-[10px] uppercase mb-1.5">Termodinámica</span>
                    <h3 class="font-bold text-slate-800 mb-1">Leyes de los Gases y Cineticoquímica</h3>
                    <p class="text-slate-600">Comportamiento P, V, T y teoría de colisiones moleculares.</p>
                </div>
                <div class="p-3.5 bg-slate-50 rounded-xl border border-slate-200">
                    <span class="inline-block px-2 py-0.5 bg-amber-100 text-amber-800 rounded font-bold text-[10px] uppercase mb-1.5">Mecánica Clásica</span>
                    <h3 class="font-bold text-slate-800 mb-1">Trabajo y Conservación de Energía</h3>
                    <p class="text-slate-600">Relación $W = F \cdot d \cos\theta$, $E_p$, $E_k$ y pérdidas de energía.</p>
                </div>
            </div>

            <button id="start-btn" class="w-full sm:w-auto px-8 py-3.5 bg-brand-600 hover:bg-brand-700 text-white font-bold rounded-xl shadow-lg hover:shadow-brand-500/20 transition-all text-sm sm:text-base tracking-wide">
                Iniciar Taller Interactivo
            </button>
        </div>

        <!-- Quiz Interface -->
        <div id="quiz-view" class="hidden flex-1 grid grid-cols-1 lg:grid-cols-12 gap-6 items-stretch">
            
            <!-- Left Side: Diagram Panel -->
            <div class="lg:col-span-6 bg-white rounded-2xl shadow-sm border border-slate-200 p-5 sm:p-6 flex flex-col h-[400px] lg:h-[calc(100vh-140px)] min-h-[380px] overflow-hidden">
                <div class="flex items-center justify-between pb-3 mb-3 border-b border-slate-200 shrink-0">
                    <div class="flex items-center space-x-2 overflow-hidden">
                        <span id="topic-badge" class="px-2.5 py-1 bg-slate-100 text-slate-700 rounded-lg text-[10px] sm:text-xs font-bold uppercase tracking-wider whitespace-nowrap">
                            Física
                        </span>
                        <span id="graphic-title" class="text-xs text-slate-500 font-medium truncate">Ilustración del Contexto</span>
                    </div>
                    <span class="text-[10px] sm:text-xs text-slate-400 font-medium shrink-0">📊 Diagrama Explicativo</span>
                </div>
                
                <div id="graphic-container" class="flex-1 flex flex-col items-center justify-center bg-slate-50 rounded-xl p-4 overflow-y-auto custom-scrollbar border border-slate-100">
                    <!-- SVG Diagrams and context injected dynamically -->
                </div>
            </div>

            <!-- Right Side: Question & Answers Panel -->
            <div class="lg:col-span-6 flex flex-col justify-between bg-white rounded-2xl shadow-sm border border-slate-200 p-5 sm:p-6 lg:h-[calc(100vh-140px)] overflow-y-auto custom-scrollbar">
                <div>
                    <div class="flex items-center justify-between mb-3 flex-wrap gap-2">
                        <span id="topic-tag" class="px-2.5 py-1 bg-blue-50 text-blue-700 border border-blue-200 rounded-full text-xs font-semibold">
                            Energía Mecánica
                        </span>
                        <span id="question-category" class="text-xs text-slate-400 font-medium">
                            Pregunta 1 de 10
                        </span>
                    </div>

                    <!-- Question Context & Text -->
                    <div id="question-stem" class="text-xs sm:text-sm text-slate-600 mb-3 leading-relaxed space-y-2">
                        <!-- Stem injected via JS -->
                    </div>

                    <h3 id="question-text" class="text-sm sm:text-base font-bold text-slate-900 mb-5 leading-snug">
                        ¿Cargando pregunta...?
                    </h3>

                    <!-- Options List -->
                    <div id="options-container" class="space-y-2.5">
                        <!-- Options injected via JS -->
                    </div>

                    <!-- Feedback Box -->
                    <div id="feedback-box" class="hidden mt-5 p-4 rounded-xl text-xs sm:text-sm leading-relaxed border transition-all">
                        <div class="font-bold mb-1 flex items-center space-x-2" id="feedback-title">
                            <!-- Correct/Incorrect Icon & Title -->
                        </div>
                        <p id="feedback-text" class="text-slate-700"></p>
                    </div>
                </div>

                <!-- Footer Nav Buttons -->
                <div class="mt-6 pt-4 border-t border-slate-100 flex items-center justify-between shrink-0">
                    <button id="prev-btn" class="px-4 py-2 text-xs sm:text-sm font-medium text-slate-600 hover:text-slate-900 bg-slate-100 hover:bg-slate-200 rounded-lg transition disabled:opacity-40 disabled:cursor-not-allowed">
                        ← Anterior
                    </button>

                    <button id="grid-toggle-mobile" class="sm:hidden text-xs text-slate-500 bg-slate-100 px-3 py-2 rounded-lg font-medium">
                        Matriz
                    </button>
                    
                    <button id="next-btn" class="px-6 py-2.5 text-xs sm:text-sm font-semibold text-white bg-brand-600 hover:bg-brand-700 rounded-lg shadow-sm transition disabled:opacity-50">
                        Siguiente →
                    </button>
                </div>
            </div>
        </div>

        <!-- Results View -->
        <div id="results-view" class="hidden bg-white rounded-2xl shadow-sm border border-slate-200 p-6 sm:p-10 max-w-3xl mx-auto w-full my-auto text-center">
            <div class="w-16 h-16 bg-emerald-100 text-emerald-600 rounded-full flex items-center justify-center mx-auto mb-4 text-3xl font-bold">
                🎯
            </div>
            <h2 class="text-2xl sm:text-3xl font-extrabold text-slate-900 mb-1">¡Taller Finalizado!</h2>
            <p class="text-slate-600 text-xs sm:text-sm mb-6">Resultados cualitativos y cuantitativos por tema conceptual.</p>

            <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 mb-6">
                <div class="p-3.5 bg-slate-50 border border-slate-200 rounded-xl">
                    <span class="text-[10px] text-slate-500 uppercase font-bold tracking-wider">Aciertos Totales</span>
                    <div id="final-score" class="text-2xl sm:text-3xl font-black text-slate-900 mt-0.5">0/10</div>
                    <span id="final-percentage" class="text-xs font-semibold text-slate-600">0% de efectividad</span>
                </div>
                <div class="p-3.5 bg-slate-50 border border-slate-200 rounded-xl">
                    <span class="text-[10px] text-slate-500 uppercase font-bold tracking-wider">Nivel Desempeño</span>
                    <div id="performance-level" class="text-base font-bold text-brand-600 mt-1">Satisfactorio</div>
                </div>
                <div class="p-3.5 bg-slate-50 border border-slate-200 rounded-xl">
                    <span class="text-[10px] text-slate-500 uppercase font-bold tracking-wider">Estado</span>
                    <div id="pass-status" class="text-base font-bold text-emerald-600 mt-1">Aprobado</div>
                </div>
            </div>

            <div class="flex flex-col sm:flex-row gap-3">
                <button id="review-btn" class="flex-1 py-3 px-4 bg-slate-100 hover:bg-slate-200 text-slate-800 font-bold rounded-xl transition text-xs sm:text-sm">
                    🔍 Revisar Pregunta por Pregunta
                </button>
                <button id="restart-btn" class="flex-1 py-3 px-4 bg-brand-600 hover:bg-brand-700 text-white font-bold rounded-xl shadow-md transition text-xs sm:text-sm">
                    🔄 Reiniciar Taller
                </button>
            </div>
        </div>

    </main>

    <!-- Modal Grid Navigator -->
    <div id="grid-modal" class="hidden fixed inset-0 bg-slate-900/60 backdrop-blur-sm z-50 flex items-center justify-center p-4">
        <div class="bg-white rounded-2xl max-w-md w-full p-6 shadow-xl border border-slate-200">
            <div class="flex justify-between items-center mb-4 pb-2 border-b">
                <h3 class="font-bold text-slate-900 text-base">Navegación de Preguntas (1 - 10)</h3>
                <button id="close-grid-btn" class="text-slate-400 hover:text-slate-600 text-lg font-bold">&times;</button>
            </div>
            <div id="grid-buttons-container" class="grid grid-cols-5 gap-2 mb-6">
                <!-- Grid buttons -->
            </div>
            <button id="close-grid-modal-btn" class="w-full py-2.5 bg-slate-100 text-slate-700 font-bold text-xs rounded-lg hover:bg-slate-200">
                Cerrar
            </button>
        </div>
    </div>

    <script>
        const quizData = [
            {
                id: 1,
                topic: "Energía Mecánica",
                title: "1. Golpe de Martillo en un Clavo",
                stem: "Camilo observa un martillo adherido a un eje de giro que golpea un clavo sobre madera. Luego de golpear el clavo, el martillo sube a una altura menor que la del primer golpe para luego volver a golpear. Esto ocurre repetidamente hasta detenerse.",
                question: "Teniendo en cuenta la información anterior, ¿cómo es la variación de la energía mecánica del martillo y del clavo cuando el martillo ha regresado a una altura menor?",
                options: [
                    "La energía mecánica del martillo ha disminuido y la del clavo ha permanecido constante.",
                    "La energía mecánica del martillo ha aumentado mientras que la del clavo ha disminuido.",
                    "La energía mecánica del clavo y del martillo han aumentado tras cada golpe.",
                    "La energía mecánica que poseen el martillo y el clavo ha permanecido constante."
                ],
                correct: 0,
                explanation: "Al golpear el clavo, parte de la energía del martillo se transfiere al clavo (en forma de trabajo de deformación y calor por fricción), reduciendo la energía mecánica del martillo en cada rebote. Como el clavo permanece inmóvil una vez hincado y en reposo, su energía mecánica final no aumenta permanentemente.",
                svg: `
                    <svg viewBox="0 0 300 200" class="w-full h-full max-h-60">
                        <rect x="50" y="160" width="200" height="30" fill="#a16207" rx="4"/>
                        <line x1="150" y1="130" x2="150" y2="160" stroke="#64748b" stroke-width="6"/>
                        <polygon points="145,160 155,160 150,170" fill="#475569"/>
                        <!-- Pivot and Hammer -->
                        <circle cx="80" cy="50" r="8" fill="#334155"/>
                        <line x1="80" y1="50" x2="150" y2="110" stroke="#94a3b8" stroke-width="4"/>
                        <rect x="135" y="100" width="30" height="20" fill="#475569" rx="2"/>
                        <!-- Bounce arcs -->
                        <path d="M 150 110 A 70 70 0 0 0 80 50" fill="none" stroke="#0284c7" stroke-width="2" stroke-dasharray="4"/>
                        <path d="M 150 110 A 50 50 0 0 0 105 65" fill="none" stroke="#f59e0b" stroke-width="2" stroke-dasharray="4"/>
                        <text x="180" y="80" font-size="10" fill="#0369a1" font-weight="bold">h1 (Mayor)</text>
                        <text x="160" y="100" font-size="10" fill="#d97706" font-weight="bold">h2 (Menor)</text>
                    </svg>
                `
            },
            {
                id: 2,
                topic: "Leyes de los Gases",
                topicTag: "Ley de Boyle",
                title: "2. Variación de Presión en un Gas",
                stem: "Un grupo de estudiantes se pregunta: ¿Qué sucede con un gas al variar su presión? Realizan un experimento con un gas en un recipiente con émbolo móvil, ejercen presión y observan que el volumen disminuye.",
                question: "¿Cuál de las siguientes hipótesis se evalúa con este experimento?",
                options: [
                    "La relación directa entre la presión y el volumen.",
                    "La relación directa entre la presión y la distancia de las moléculas.",
                    "La relación inversa entre el volumen y la distancia de las moléculas.",
                    "La relación inversa entre la presión y el volumen."
                ],
                correct: 3,
                explanation: "El experimento evalúa la Ley de Boyle, que establece que a temperatura constante, la presión y el volumen de un gas son inversamente proporcionales ($P \propto 1/V$). Al aumentar la presión ejercida, el volumen disminuye.",
                svg: `
                    <svg viewBox="0 0 300 200" class="w-full h-full max-h-60">
                        <!-- Cylinder 1 -->
                        <rect x="40" y="60" width="80" height="110" fill="none" stroke="#334155" stroke-width="3"/>
                        <rect x="42" y="80" width="76" height="15" fill="#64748b"/>
                        <line x1="80" y1="30" x2="80" y2="80" stroke="#334155" stroke-width="4"/>
                        <circle cx="60" cy="120" r="3" fill="#0284c7"/><circle cx="90" cy="140" r="3" fill="#0284c7"/><circle cx="75" cy="100" r="3" fill="#0284c7"/>
                        <text x="50" y="185" font-size="11" fill="#475569" font-weight="bold">Baja P, Alto V</text>

                        <!-- Arrow -->
                        <path d="M 135 110 L 165 110" stroke="#0284c7" stroke-width="3" marker-end="url(#arrow)"/>

                        <!-- Cylinder 2 -->
                        <rect x="180" y="60" width="80" height="110" fill="none" stroke="#334155" stroke-width="3"/>
                        <rect x="182" y="120" width="76" height="15" fill="#64748b"/>
                        <line x1="220" y1="30" x2="220" y2="120" stroke="#334155" stroke-width="4"/>
                        <!-- Down force arrows -->
                        <path d="M 220 15 L 220 30" stroke="#ef4444" stroke-width="3"/>
                        <circle cx="200" cy="140" r="3" fill="#0284c7"/><circle cx="230" cy="150" r="3" fill="#0284c7"/><circle cx="215" cy="130" r="3" fill="#0284c7"/>
                        <text x="190" y="185" font-size="11" fill="#475569" font-weight="bold">Alta P, Bajo V</text>
                    </svg>
                `
            },
            {
                id: 3,
                topic: "Leyes de los Gases",
                topicTag: "Ley de Charles",
                title: "3. Expansión Térmica en Llantas de Bus",
                stem: "Una estudiante observa que al viajar de un pueblo frío a uno caliente, las llantas del bus se ven más grandes porque el volumen del aire interior aumenta. Ella busca diseñar un experimento en casa para demostrar este fenómeno.",
                question: "¿Cuál de los siguientes experimentos le permite corroborar sus observaciones?",
                options: [
                    "Inflar un globo con aire y luego apretarlo con las manos hasta que se estalle.",
                    "Fijar un globo en la boca de una botella de vidrio y luego meter la botella en un balde con agua fría.",
                    "Inflar un globo con aire y luego esperar varios días hasta que se desinfle completamente.",
                    "Fijar un globo en la boca de una botella de vidrio y luego acercar la botella a la llama de una vela."
                ],
                correct: 3,
                explanation: "Acercar la botella con el globo a una vela incrementa la temperatura del aire en su interior, aumentando la energía cinética de las moléculas y provocando su expansión (Ley de Charles: $V \propto T$), lo que infla el globo.",
                svg: `
                    <svg viewBox="0 0 300 200" class="w-full h-full max-h-60">
                        <path d="M 135 120 L 135 150 A 15 15 0 0 0 165 150 L 165 120 L 158 90 L 158 70 L 142 70 L 142 90 Z" fill="#e2e8f0" stroke="#475569" stroke-width="2"/>
                        <!-- Balloon inflated -->
                        <path d="M 142 70 C 120 40, 180 40, 158 70 Z" fill="#ef4444" opacity="0.8"/>
                        <!-- Candle / Flame -->
                        <rect x="145" y="170" width="10" height="20" fill="#fde047"/>
                        <path d="M 150 160 Q 155 167 150 170 Q 145 167 150 160" fill="#f97316"/>
                        <text x="175" y="60" font-size="11" fill="#ef4444" font-weight="bold">↑ Temp  → ↑ Vol</text>
                    </svg>
                `
            },
            {
                id: 4,
                topic: "Cineticoquímica",
                topicTag: "Teoría de Colisiones",
                title: "4. Efecto de la Temperatura en Reacciones",
                stem: "Un laboratorio realiza dos experimentos de una misma reacción química. El primero toma 5 minutos. En el segundo se varía la temperatura y se obtiene un menor tiempo de reacción.",
                question: "Dada la información, ¿por qué el experimento 2 tiene menor tiempo de reacción?",
                options: [
                    "Porque al aumentar la temperatura hay mayor cantidad de choques entre las moléculas.",
                    "Porque al disminuir la temperatura hay mayor cantidad de choques entre las moléculas.",
                    "Porque al aumentar la temperatura hay menor cantidad de choques entre las moléculas.",
                    "Porque al disminuir la temperatura hay menor cantidad de choques entre las moléculas."
                ],
                correct: 0,
                explanation: "Al incrementar la temperatura, la energía cinética media de las moléculas aumenta, provocando que se muevan más rápido y colisionen con mayor frecuencia y energía efectiva, lo que acelera la reacción.",
                svg: `
                    <svg viewBox="0 0 300 200" class="w-full h-full max-h-60">
                        <circle cx="80" cy="100" r="18" fill="#3b82f6" opacity="0.7"/>
                        <circle cx="130" cy="100" r="18" fill="#3b82f6" opacity="0.7"/>
                        <path d="M 98 100 L 112 100" stroke="#1e3a8a" stroke-width="2" stroke-dasharray="2"/>
                        <text x="60" y="150" font-size="11" fill="#1e40af">T Baja: Pocos choques</text>

                        <circle cx="200" cy="100" r="18" fill="#ef4444" opacity="0.8"/>
                        <circle cx="240" cy="100" r="18" fill="#ef4444" opacity="0.8"/>
                        <path d="M 218 100 L 222 100" stroke="#991b1b" stroke-width="4"/>
                        <text x="180" y="150" font-size="11" fill="#b91c1c" font-weight="bold">↑ T: ¡Colisiones frecuentes!</text>
                    </svg>
                `
            },
            {
                id: 5,
                topic: "Trabajo y Energía",
                topicTag: "Trabajo Mecánico",
                title: "5. Trabajo Realizado por Helena",
                stem: "Helena camina por una pendiente de longitud $d$ y altura $h$, y luego atraviesa un tramo recto de longitud $d$ cargando una maleta de masa $m = 10\\text{ kg}$. El terreno no ejerce resistencia y avanza con rapidez constante ($g = 10\\text{ m/s}^2$). El trabajo ejercido sobre la maleta es $W = mgh$ (cambio en energía potencial). $h = 50\\text{ m}$, $d = 70\\text{ m}$.",
                question: "¿Cuál es el valor del trabajo que ejerce Helena sobre la maleta durante todo su recorrido?",
                options: [
                    "500 J",
                    "700 J",
                    "1.000 J",
                    "1.400 J"
                ],
                correct: 0,
                explanation: "El trabajo total es igual a la variación nula o positiva de energía potencial vertical $\\Delta E_p = m \\cdot g \\cdot h$. En el tramo plano, la fuerza aplicada es perpendicular al desplazamiento (cos 90° = 0), por lo que el trabajo plano es 0 J. Por tanto, $W = 10\\text{ kg} \\cdot 10\\text{ m/s}^2 \\cdot 50\\text{ m} = 500\\text{ J}$.",
                svg: `
                    <svg viewBox="0 0 300 200" class="w-full h-full max-h-60">
                        <!-- Incline -->
                        <path d="M 30 160 L 150 70 L 260 70" fill="none" stroke="#475569" stroke-width="4"/>
                        <path d="M 30 160 L 150 160 L 150 70" fill="none" stroke="#94a3b8" stroke-width="2" stroke-dasharray="4"/>
                        
                        <!-- Values -->
                        <text x="80" y="180" font-size="11" fill="#64748b">Tramo inclinado d</text>
                        <text x="160" y="120" font-size="11" fill="#ef4444" font-weight="bold">h = 50 m</text>
                        <text x="190" y="60" font-size="11" fill="#64748b">Tramo recto d</text>
                        <circle cx="150" cy="70" r="5" fill="#0284c7"/>
                        <text x="20" y="50" font-size="11" fill="#0369a1" font-weight="bold">W_total = m·g·h = 500 J</text>
                    </svg>
                `
            },
            {
                id: 6,
                topic: "Leyes de los Gases",
                topicTag: "Análisis de Gráficas",
                title: "6. Evaluación de Gráfica de Ley de Boyle",
                stem: "Estudiantes indagan sobre la Ley de Boyle (a temperatura constante, si $P$ aumenta, $V$ disminuye). Al realizar un experimento con una jeringa, obtienen una gráfica donde la curva muestra que al aumentar la presión, el volumen también se incrementa de forma directa.",
                question: "Después de analizar la gráfica, una compañera comenta que los resultados no corresponden con la Ley de Boyle. ¿Qué falencia se encuentra en la gráfica?",
                options: [
                    "La gráfica muestra que, al aumentar la presión, también aumenta el volumen, lo que contradice la ley de Boyle.",
                    "La gráfica indica que al aumentar el volumen, la presión es constante, lo que no coincide con la ley de Boyle.",
                    "La gráfica indica que, al disminuir la presión, el volumen permanece constante, lo que contradice la ley de Boyle.",
                    "La gráfica muestra que, a una presión constante, el volumen es constante, lo que no se ajusta a la ley de Boyle."
                ],
                correct: 0,
                explanation: "La falencia radica en que la gráfica muestra una relación directamente proporcional (al subir $P$ sube $V$), lo cual contradice frontalmente la Ley de Boyle que establece una relación inversamente proporcional.",
                svg: `
                    <svg viewBox="0 0 300 200" class="w-full h-full max-h-60">
                        <line x1="50" y1="160" x2="250" y2="160" stroke="#334155" stroke-width="2"/>
                        <line x1="50" y1="160" x2="50" y2="30" stroke="#334155" stroke-width="2"/>
                        <text x="240" y="180" font-size="10">Presión (P)</text>
                        <text x="15" y="40" font-size="10">Volumen (V)</text>

                        <!-- Incorrect Line shown in experiment -->
                        <line x1="60" y1="150" x2="220" y2="50" stroke="#ef4444" stroke-width="3"/>
                        <text x="140" y="80" font-size="10" fill="#ef4444" font-weight="bold">Gráfica Incorrecta (Directa)</text>

                        <!-- Correct Boyle Line -->
                        <path d="M 70 50 Q 90 140 230 150" fill="none" stroke="#22c55e" stroke-width="2" stroke-dasharray="4"/>
                        <text x="160" y="130" font-size="10" fill="#15803d">Teoría Boyle (Inversa)</text>
                    </svg>
                `
            },
            {
                id: 7,
                topic: "Energía Mecánica",
                topicTag: "Energía Potencial y Cinética",
                title: "7. Cuchara de Retroexcavadora en Ascenso",
                stem: "La cuchara de una retroexcavadora alcanza una altura máxima tras recoger material del suelo. Como es controlada por el motor, su velocidad de subida es constante.",
                question: "De acuerdo con lo anterior, ¿cómo cambian la energía potencial gravitacional y la energía cinética a medida que la cuchara asciende?",
                options: [
                    "La energía potencial gravitacional disminuye y la energía cinética se mantiene constante.",
                    "La energía potencial gravitacional aumenta y la energía cinética se mantiene constante.",
                    "La energía potencial gravitacional aumenta y la energía cinética aumenta.",
                    "La energía potencial gravitacional disminuye y la energía cinética aumenta."
                ],
                correct: 1,
                explanation: "Como la altura $h$ aumenta, la energía potencial gravitacional ($E_p = mgh$) aumenta. Al subir con velocidad $v$ constante, la energía cinética ($E_k = \\frac{1}{2}mv^2$) permanece constante.",
                svg: `
                    <svg viewBox="0 0 300 200" class="w-full h-full max-h-60">
                        <rect x="40" y="150" width="80" height="30" fill="#eab308" rx="4"/>
                        <circle cx="60" cy="180" r="8" fill="#334155"/>
                        <circle cx="100" cy="180" r="8" fill="#334155"/>
                        <line x1="100" y1="150" x2="180" y2="70" stroke="#475569" stroke-width="6"/>
                        <!-- Bucket -->
                        <path d="M 180 70 L 210 80 L 200 110 Z" fill="#ca8a04"/>
                        <path d="M 215 100 L 215 60" stroke="#0284c7" stroke-width="3" marker-end="url(#arrow)"/>
                        <text x="220" y="80" font-size="11" fill="#0284c7" font-weight="bold">v = cte (Ek cte)</text>
                        <text x="220" y="95" font-size="11" fill="#15803d" font-weight="bold">↑ h (Ep aumenta)</text>
                    </svg>
                `
            },
            {
                id: 8,
                topic: "Energía Mecánica",
                topicTag: "Transformación de Energía",
                title: "8. Esfera Descendiendo por una Rampa",
                stem: "Se suelta una esfera desde la parte superior de una rampa sin fricción. La esfera desciende aumentando su velocidad, luego se separa de la rampa y continúa descendiendo hasta chocar con el suelo.",
                question: "Durante el tiempo que desciende por la rampa, ¿qué le sucede a la energía potencial de la esfera?",
                options: [
                    "Permanece constante, porque la esfera desciende en contacto con la rampa.",
                    "Aumenta, porque la velocidad de la esfera aumenta, y esto le permite seguir la trayectoria punteada.",
                    "Se transforma en energía cinética, porque la esfera aumenta su rapidez y pierde altura.",
                    "Se transforma en energía mecánica, porque la esfera debe frenar y disminuir la energía cinética."
                ],
                correct: 2,
                explanation: "Al perder altura, la energía potencial gravitacional se reduce y se transforma progresivamente en energía cinética, incrementando la rapidez de la esfera según el principio de conservación de la energía mecánica.",
                svg: `
                    <svg viewBox="0 0 300 200" class="w-full h-full max-h-60">
                        <path d="M 40 40 Q 120 160 200 160" fill="none" stroke="#334155" stroke-width="4"/>
                        <circle cx="50" cy="45" r="10" fill="#ef4444"/>
                        <circle cx="130" cy="135" r="10" fill="#ef4444"/>
                        <path d="M 200 160 Q 240 160 270 190" fill="none" stroke="#94a3b8" stroke-width="2" stroke-dasharray="4"/>
                        <text x="65" y="40" font-size="10" fill="#d97706">Alto Ep, Bajo Ek</text>
                        <text x="145" y="130" font-size="10" fill="#16a34a">Bajo Ep, Alto Ek</text>
                    </svg>
                `
            },
            {
                id: 9,
                topic: "Trabajo y Energía",
                topicTag: "Fuerza Normal y Ángulo",
                title: "9. Trabajo de la Fuerza Normal",
                stem: "Raúl empuja un carrito de biblioteca que pesa $500\\text{ N}$. El piso ejerce una fuerza normal de $500\\text{ N}$ hacia arriba y Raúl desplaza el carrito $10\\text{ m}$ horizontalmente. $W = F \\cdot d \\cos\\theta$, donde $\\theta$ es el ángulo entre fuerza y desplazamiento ($\\cos 90^\\circ = 0$, $\\cos 0^\\circ = 1$).",
                question: "¿Cuál es el trabajo que realiza la fuerza normal durante el desplazamiento de 10 m?",
                options: [
                    "5.000 J",
                    "0 J",
                    "50 J",
                    "10 J"
                ],
                correct: 1,
                explanation: "La fuerza normal apunta verticalmente hacia arriba ($90^\\circ$ respecto al desplazamiento horizontal). Como $\\cos 90^\\circ = 0$, el trabajo realizado por la fuerza normal es $W = 500\\text{ N} \\cdot 10\\text{ m} \\cdot 0 = 0\\text{ J}$.",
                svg: `
                    <svg viewBox="0 0 300 200" class="w-full h-full max-h-60">
                        <line x1="30" y1="160" x2="270" y2="160" stroke="#334155" stroke-width="3"/>
                        <rect x="110" y="100" width="80" height="50" fill="#38bdf8" rx="4"/>
                        <!-- Force Normal Arrow -->
                        <path d="M 150 100 L 150 40" stroke="#16a34a" stroke-width="4" marker-end="url(#arrow)"/>
                        <text x="155" y="50" font-size="11" fill="#16a34a" font-weight="bold">FN = 500 N (90°)</text>
                        <!-- Displacement Arrow -->
                        <path d="M 190 125 L 250 125" stroke="#0284c7" stroke-width="3"/>
                        <text x="195" y="145" font-size="11" fill="#0284c7">d = 10 m</text>
                        <text x="50" y="50" font-size="12" fill="#d97706" font-weight="bold">W = F·d·cos(90°) = 0 J</text>
                    </svg>
                `
            },
            {
                id: 10,
                topic: "Energía Mecánica",
                topicTag: "Evaluación Temporal de Energía",
                title: "10. Esfera en Rampa a los 2s, 4s y 8s",
                stem: "Una esfera se deja libre desde una altura $h$ en una rampa sin rozamiento. La figura muestra las posiciones descendentes de la esfera cuando han transcurrido $2\\text{ s}$, $4\\text{ s}$ y $8\\text{ s}$, respectivamente.",
                question: "Teniendo en cuenta la información anterior, ¿cuál de las siguientes afirmaciones sobre los tipos de energía mecánica es correcta?",
                options: [
                    "La energía potencial es mayor a los 4 s que a los 8 s.",
                    "La energía cinética es igual a los 8 s que a los 4 s.",
                    "La energía potencial es mayor a los 2 s que a los 4 s.",
                    "La energía cinética es mayor a los 8 s que a los 2 s."
                ],
                correct: 2,
                explanation: "A los 2 s la esfera se encuentra a mayor altura que a los 4 s, por lo que su energía potencial ($mgh$) es mayor a los 2 s. De igual manera, a los 8 s está más abajo y tiene mayor rapidez que a los 2 s.",
                svg: `
                    <svg viewBox="0 0 300 200" class="w-full h-full max-h-60">
                        <path d="M 30 30 L 250 170" stroke="#334155" stroke-width="4"/>
                        <!-- Positions -->
                        <circle cx="60" cy="50" r="8" fill="#ef4444"/>
                        <text x="75" y="55" font-size="11" font-weight="bold">t = 2s (Mayor h)</text>

                        <circle cx="120" cy="90" r="8" fill="#ef4444"/>
                        <text x="135" y="95" font-size="11" font-weight="bold">t = 4s</text>

                        <circle cx="210" cy="145" r="8" fill="#ef4444"/>
                        <text x="220" y="140" font-size="11" font-weight="bold">t = 8s (Menor h)</text>
                    </svg>
                `
            }
        ];

        let currentQuestionIndex = 0;
        let userAnswers = new Array(quizData.length).fill(null);

        // DOM Elements
        const welcomeView = document.getElementById('welcome-view');
        const quizView = document.getElementById('quiz-view');
        const resultsView = document.getElementById('results-view');

        const startBtn = document.getElementById('start-btn');
        const prevBtn = document.getElementById('prev-btn');
        const nextBtn = document.getElementById('next-btn');
        const resetBtn = document.getElementById('reset-btn');
        const reviewBtn = document.getElementById('review-btn');
        const restartBtn = document.getElementById('restart-btn');

        const currentQNum = document.getElementById('current-q-num');
        const totalQNum = document.getElementById('total-q-num');
        const progressBar = document.getElementById('progress-bar');

        const topicBadge = document.getElementById('topic-badge');
        const graphicTitle = document.getElementById('graphic-title');
        const graphicContainer = document.getElementById('graphic-container');

        const topicTag = document.getElementById('topic-tag');
        const questionCategory = document.getElementById('question-category');
        const questionStem = document.getElementById('question-stem');
        const questionText = document.getElementById('question-text');
        const optionsContainer = document.getElementById('options-container');
        const feedbackBox = document.getElementById('feedback-box');
        const feedbackTitle = document.getElementById('feedback-title');
        const feedbackText = document.getElementById('feedback-text');

        // Modal Elements
        const gridModal = document.getElementById('grid-modal');
        const openGridBtn = document.getElementById('open-grid-btn');
        const closeGridBtn = document.getElementById('close-grid-btn');
        const closeGridModalBtn = document.getElementById('close-grid-modal-btn');
        const gridToggleMobile = document.getElementById('grid-toggle-mobile');
        const gridButtonsContainer = document.getElementById('grid-buttons-container');

        document.addEventListener('DOMContentLoaded', () => {
            totalQNum.textContent = quizData.length;
            
            startBtn.addEventListener('click', startQuiz);
            prevBtn.addEventListener('click', goToPrevQuestion);
            nextBtn.addEventListener('click', handleNextClick);
            resetBtn.addEventListener('click', resetQuiz);
            restartBtn.addEventListener('click', resetQuiz);
            reviewBtn.addEventListener('click', reviewQuiz);

            openGridBtn.addEventListener('click', openGrid);
            gridToggleMobile.addEventListener('click', openGrid);
            closeGridBtn.addEventListener('click', closeGrid);
            closeGridModalBtn.addEventListener('click', closeGrid);
        });

        function startQuiz() {
            welcomeView.classList.add('hidden');
            resultsView.classList.add('hidden');
            quizView.classList.remove('hidden');
            currentQuestionIndex = 0;
            renderQuestion();
        }

        function renderQuestion() {
            const data = quizData[currentQuestionIndex];

            // Progress Header
            currentQNum.textContent = currentQuestionIndex + 1;
            const progressPct = ((currentQuestionIndex + 1) / quizData.length) * 100;
            progressBar.style.width = `${progressPct}%`;

            // Graphic Panel
            topicBadge.textContent = data.topic;
            graphicTitle.textContent = data.title;
            graphicContainer.innerHTML = data.svg;

            // Question Panel
            topicTag.textContent = data.topicTag || data.topic;
            questionCategory.textContent = `Pregunta ${data.id} de ${quizData.length}`;
            questionStem.innerHTML = `<p>${data.stem}</p>`;
            questionText.textContent = data.question;

            // Render Options
            optionsContainer.innerHTML = '';
            const selectedOption = userAnswers[currentQuestionIndex];

            data.options.forEach((opt, idx) => {
                const letter = String.fromCharCode(65 + idx);
                const optBtn = document.createElement('button');
                
                let btnStyles = "border-slate-200 hover:border-slate-300 hover:bg-slate-50 text-slate-700";
                let badgeStyles = "bg-white text-slate-500 border-slate-300";

                if (selectedOption === idx) {
                    btnStyles = "border-brand-600 bg-brand-50 text-brand-900 font-medium shadow-sm ring-1 ring-brand-500";
                    badgeStyles = "bg-brand-600 text-white border-brand-600";
                }

                optBtn.className = `w-full text-left p-3 sm:p-3.5 rounded-xl border text-xs sm:text-sm flex items-start space-x-3 transition-all cursor-pointer ${btnStyles}`;

                optBtn.innerHTML = `
                    <span class="w-5 h-5 sm:w-6 sm:h-6 rounded-full flex items-center justify-center border text-[11px] sm:text-xs font-bold shrink-0 ${badgeStyles}">${letter}</span>
                    <span class="pt-0.5 leading-snug">${opt}</span>
                `;

                optBtn.addEventListener('click', () => selectOption(idx));
                optionsContainer.appendChild(optBtn);
            });

            // Feedback Handling
            if (selectedOption !== null) {
                showFeedback(selectedOption);
            } else {
                feedbackBox.classList.add('hidden');
            }

            // Controls
            prevBtn.disabled = currentQuestionIndex === 0;
            if (currentQuestionIndex === quizData.length - 1) {
                nextBtn.textContent = "Finalizar Taller";
                nextBtn.className = "px-5 py-2.5 text-xs sm:text-sm font-bold text-white bg-emerald-600 hover:bg-emerald-700 rounded-lg shadow-sm transition";
            } else {
                nextBtn.textContent = "Siguiente →";
                nextBtn.className = "px-5 py-2.5 text-xs sm:text-sm font-bold text-white bg-brand-600 hover:bg-brand-700 rounded-lg shadow-sm transition";
            }
        }

        function selectOption(optionIndex) {
            userAnswers[currentQuestionIndex] = optionIndex;
            renderQuestion();
        }

        function showFeedback(selectedIdx) {
            const data = quizData[currentQuestionIndex];
            const isCorrect = selectedIdx === data.correct;

            feedbackBox.classList.remove('hidden');
            
            if (isCorrect) {
                feedbackBox.className = "mt-4 p-3.5 rounded-xl text-xs sm:text-sm leading-relaxed border bg-emerald-50 border-emerald-200 text-emerald-900";
                feedbackTitle.innerHTML = `<span class="text-emerald-600 font-bold">✓ Respuesta Correcta</span>`;
            } else {
                feedbackBox.className = "mt-4 p-3.5 rounded-xl text-xs sm:text-sm leading-relaxed border bg-rose-50 border-rose-200 text-rose-900";
                feedbackTitle.innerHTML = `<span class="text-rose-600 font-bold">✕ Respuesta Incorrecta (Opción correcta: ${String.fromCharCode(65 + data.correct)})</span>`;
            }

            feedbackText.textContent = data.explanation;
        }

        function handleNextClick() {
            if (currentQuestionIndex < quizData.length - 1) {
                currentQuestionIndex++;
                renderQuestion();
            } else {
                calculateResults();
            }
        }

        function goToPrevQuestion() {
            if (currentQuestionIndex > 0) {
                currentQuestionIndex--;
                renderQuestion();
            }
        }

        function openGrid() {
            gridButtonsContainer.innerHTML = '';
            quizData.forEach((q, idx) => {
                const btn = document.createElement('button');
                const isAnswered = userAnswers[idx] !== null;
                const isCurrent = idx === currentQuestionIndex;

                let stateClasses = "bg-slate-100 text-slate-700 hover:bg-slate-200";
                if (isAnswered) {
                    stateClasses = "bg-brand-600 text-white font-bold";
                }
                if (isCurrent) {
                    stateClasses += " ring-2 ring-offset-1 ring-brand-500 font-black";
                }

                btn.className = `p-2.5 rounded-lg text-xs transition ${stateClasses}`;
                btn.textContent = idx + 1;
                btn.addEventListener('click', () => {
                    currentQuestionIndex = idx;
                    renderQuestion();
                    closeGrid();
                });
                gridButtonsContainer.appendChild(btn);
            });
            gridModal.classList.remove('hidden');
        }

        function closeGrid() {
            gridModal.classList.add('hidden');
        }

        function calculateResults() {
            quizView.classList.add('hidden');
            resultsView.classList.remove('hidden');

            let totalCorrect = 0;
            quizData.forEach((q, idx) => {
                if (userAnswers[idx] === q.correct) totalCorrect++;
            });

            const scorePct = Math.round((totalCorrect / quizData.length) * 100);
            document.getElementById('final-score').textContent = `${totalCorrect}/${quizData.length}`;
            document.getElementById('final-percentage').textContent = `${scorePct}% de aciertos`;

            const perfElem = document.getElementById('performance-level');
            const passElem = document.getElementById('pass-status');

            if (scorePct >= 80) {
                perfElem.textContent = "Nivel Alto / Excelente";
                perfElem.className = "text-base font-bold text-emerald-600 mt-1";
                passElem.textContent = "Aprobado con Distinción";
                passElem.className = "text-base font-bold text-emerald-600 mt-1";
            } else if (scorePct >= 60) {
                perfElem.textContent = "Nivel Satisfactorio";
                perfElem.className = "text-base font-bold text-blue-600 mt-1";
                passElem.textContent = "Aprobado";
                passElem.className = "text-base font-bold text-blue-600 mt-1";
            } else {
                perfElem.textContent = "Nivel Bajo / Requiere Refuerzo";
                perfElem.className = "text-base font-bold text-rose-600 mt-1";
                passElem.textContent = "No Aprobado";
                passElem.className = "text-base font-bold text-rose-600 mt-1";
            }
        }

        function reviewQuiz() {
            resultsView.classList.add('hidden');
            quizView.classList.remove('hidden');
            currentQuestionIndex = 0;
            renderQuestion();
        }

        function resetQuiz() {
            userAnswers = new Array(quizData.length).fill(null);
            currentQuestionIndex = 0;
            resultsView.classList.add('hidden');
            quizView.classList.add('hidden');
            welcomeView.classList.remove('hidden');
            progressBar.style.width = '10%';
        }
    </script>
</body>
</html>
