<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AnestesiaPro | Suite Completa</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Lato:wght@300;400;700&family=Montserrat:wght@400;600;700&display=swap" rel="stylesheet">
    
    <style>
        /* --- ESTILOS VISUALES (Mantenidos) --- */
        :root {
            --primary: #0f4c75; /* Azul profundo */
            --secondary: #3282b8; /* Azul medio */
            --accent: #bbe1fa; /* Azul claro */
            --danger: #e94560; /* Rojo Emergencia */
            --text-main: #1b262c;
            --bg-light: #f0f5f9;
            --card-bg: #ffffff;
            --shadow: 0 10px 20px rgba(0,0,0,0.08);
            --radius: 12px;
            --gold: #ffc107;
        }

        * { box-sizing: border-box; scroll-behavior: smooth; }

        body {
            font-family: 'Lato', sans-serif;
            margin: 0;
            background-color: var(--bg-light);
            color: var(--text-main);
            line-height: 1.6;
        }

        h1, h2, h3, h4 { font-family: 'Montserrat', sans-serif; margin-top: 0; }

        /* HERO HEADER */
        header {
            background: linear-gradient(rgba(15, 76, 117, 0.95), rgba(50, 130, 184, 0.9)), 
                        url('https://images.unsplash.com/photo-1551076805-e1869033e561?ixlib=rb-4.0.3');
            background-size: cover;
            background-position: center;
            color: white;
            padding: 1rem 0 3rem 0;
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            flex-wrap: wrap;
        }

        .logo { font-size: 1.5rem; font-weight: 700; color: var(--accent); display: flex; align-items: center; gap: 10px; }
        
        nav ul { list-style: none; display: flex; gap: 15px; padding: 0; margin: 10px 0; }
        nav a { color: white; text-decoration: none; font-size: 0.9rem; font-weight: 600; transition: 0.3s; padding: 5px 10px; border-radius: 4px; }
        nav a:hover { background: rgba(255,255,255,0.1); color: var(--accent); }

        /* CONTENEDOR PRINCIPAL */
        .container { max-width: 1200px; margin: -40px auto 0; padding: 0 20px; position: relative; z-index: 10; }

        section {
            background: var(--card-bg);
            border-radius: var(--radius);
            padding: 2rem;
            margin-bottom: 2rem;
            box-shadow: var(--shadow);
        }

        .section-title {
            display: flex; align-items: center; gap: 10px; color: var(--primary);
            border-bottom: 2px solid var(--bg-light); padding-bottom: 1rem; margin-bottom: 2rem;
        }
        
        /* GRIDS & LAYOUTS */
        .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; }
        .grid-3 { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 1.5rem; }
        .grid-4 { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1rem; }

        /* PROTOCOLOS EMERGENCIA */
        .emergency-bar {
            background: var(--danger); color: white; border-radius: 8px; padding: 15px;
            display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px;
        }
        .emergency-btn {
            background: white; color: var(--danger); padding: 8px 15px; border-radius: 20px;
            text-decoration: none; font-weight: bold; font-size: 0.9rem; transition: 0.3s;
        }
        .emergency-btn:hover { background: #ffebeb; transform: scale(1.05); }

        /* TARJETAS (Guías, Artículos, Resúmenes) */
        .resource-card {
            border: 1px solid #eee; border-radius: var(--radius); overflow: hidden;
            transition: 0.3s; display: flex; flex-direction: column;
        }
        .resource-card:hover { transform: translateY(-5px); box-shadow: var(--shadow); border-color: var(--secondary); }
        
        .card-img { height: 150px; background: #ddd; display: flex; align-items: center; justify-content: center; color: #666; }
        .card-content { padding: 1.5rem; flex-grow: 1; }
        .card-meta { font-size: 0.8rem; color: #888; margin-bottom: 0.5rem; display: block; }
        .card-btn {
            display: block; text-align: center; background: var(--bg-light); color: var(--primary);
            padding: 10px; text-decoration: none; font-weight: 600; margin-top: auto;
        }
        .card-btn:hover { background: var(--primary); color: white; }

        /* CALCULADORAS & RISK SCALES */
        .risk-box { background: #f8f9fa; padding: 1.5rem; border-radius: 8px; border: 1px solid #eee; height: 100%; }
        .checkbox-group label { display: flex; align-items: center; gap: 10px; margin-bottom: 8px; cursor: pointer; font-size: 0.9rem; }
        .btn-calc {
            background: var(--primary); color: white; border: none; padding: 10px; width: 100%;
            border-radius: 6px; cursor: pointer; font-weight: bold; margin-top: 10px;
        }
        .result-display {
            margin-top: 15px; padding: 10px; background: #e3f2fd; border-radius: 4px;
            text-align: center; color: var(--primary); font-weight: bold; display: none;
        }

        /* PREMIUM LOCK (Pediatría) */
        .premium-wrapper { position: relative; overflow: hidden; min-height: 400px; }
        .blur-content { filter: blur(6px); pointer-events: none; user-select: none; opacity: 0.4; transition: 0.5s; }
        .lock-overlay {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            z-index: 5; background: rgba(255,255,255,0.7);
        }
        .lock-badge {
            background: white; padding: 2rem; border-radius: var(--radius); box-shadow: var(--shadow);
            text-align: center; max-width: 350px; border: 2px solid var(--gold);
        }
        .btn-gold { 
            background: linear-gradient(45deg, #FFD700, #FFA500); color: #333; border: none;
            padding: 12px 25px; border-radius: 25px; font-weight: bold; cursor: pointer; margin-top: 10px;
        }

        /* RESPONSIVE */
        @media (max-width: 768px) {
            .grid-2 { grid-template-columns: 1fr; }
            .nav-container { flex-direction: column; gap: 10px; padding-bottom: 10px; }
            nav ul { flex-wrap: wrap; justify-content: center; }
        }
    </style>
</head>
<body>

<header>
    <div class="nav-container">
        <div class="logo"><i class="fas fa-heartbeat"></i> AnestesiaPro</div>
        <nav>
            <ul>
                <li><a href="#guias">Guías</a></li>
                <li><a href="#riesgo">Riesgo Qx</a></li>
                <li><a href="#resumenes">Resúmenes</a></li>
                <li><a href="#articulos">Artículos</a></li>
                <li><a href="#pediatria" style="color: var(--gold);"><i class="fas fa-crown"></i> Pediatría</a></li>
            </ul>
        </nav>
    </div>
    <div style="text-align: center; margin-top: 2rem;">
        <h1 style="font-size: 2.5rem; margin-bottom: 0;">Portal del Especialista</h1>
        <p style="opacity: 0.9;">Recursos clínicos, algoritmos y educación continua.</p>
    </div>
</header>

<div class="container">

    <div class="emergency-bar">
        <div style="display: flex; align-items: center; gap: 15px;">
            <i class="fas fa-ambulance fa-2x"></i>
            <div>
                <h3 style="margin:0; color:white;">Protocolos de Emergencia</h3>
                <small>Acceso directo a manuales AHA actualizados</small>
            </div>
        </div>
        <div style="display: flex; gap: 10px; flex-wrap: wrap;">
            <a href="https://cpr.heart.org/en/resuscitation-science/cpr-and-ecc-guidelines/algorithms" target="_blank" class="emergency-btn">Algoritmos ACLS</a>
            <a href="https://cpr.heart.org/en/resuscitation-science/cpr-and-ecc-guidelines/algorithms#pediatric" target="_blank" class="emergency-btn">Algoritmos PALS</a>
        </div>
    </div>

    <section id="guias">
        <div class="section-title">
            <i class="fas fa-book-medical fa-2x"></i>
            <h2>Guías Clínicas (Acceso Directo)</h2>
        </div>
        <div class="grid-4">
            <div class="resource-card">
                <div class="card-content">
                    <h4><i class="fas fa-flag-usa"></i> ASA Standards</h4>
                    <p style="font-size:0.8rem">Guías oficiales americanas.</p>
                </div>
                <a href="https://www.asahq.org/standards-and-guidelines" target="_blank" class="card-btn">Ver Guías</a>
            </div>
            <div class="resource-card">
                <div class="card-content">
                    <h4><i class="fas fa-globe-europe"></i> ESAIC</h4>
                    <p style="font-size:0.8rem">Sociedad Europea.</p>
                </div>
                <a href="https://www.esaic.org/resources/guidelines/" target="_blank" class="card-btn">Ver Guías</a>
            </div>
            <div class="resource-card">
                <div class="card-content">
                    <h4><i class="fas fa-brain"></i> SNACC</h4>
                    <p style="font-size:0.8rem">Neuroanestesia y Críticos.</p>
                </div>
                <a href="https://www.snacc.org/guidelines/" target="_blank" class="card-btn">Ver Guías</a>
            </div>
            <div class="resource-card">
                <div class="card-content">
                    <h4><i class="fas fa-baby"></i> SPA (Pediatría)</h4>
                    <p style="font-size:0.8rem">Sociedad de Anestesia Pediátrica.</p>
                </div>
                <a href="https://pedsanesthesia.org/" target="_blank" class="card-btn">Ver Web</a>
            </div>
        </div>
    </section>

    <section id="riesgo">
        <div class="section-title">
            <i class="fas fa-clipboard-check fa-2x"></i>
            <h2>Valoración de Riesgo Anestésico</h2>
        </div>
        
        <div class="grid-2">
            <div style="display: flex; flex-direction: column; gap: 20px;">
                
                <div class="risk-box">
                    <h4><i class="fas fa-notes-medical"></i> Clasificación ASA</h4>
                    <ul style="font-size: 0.85rem; padding-left: 20px; margin: 0;">
                        <li><strong>ASA I:</strong> Sano.</li>
                        <li><strong>ASA II:</strong> Enf. leve controlada (HTA, DM).</li>
                        <li><strong>ASA III:</strong> Enf. grave, limitante.</li>
                        <li><strong>ASA IV:</strong> Amenaza constante la vida.</li>
                    </ul>
                </div>

                <div class="risk-box">
                    <h4><i class="fas fa-bed"></i> Cuestionario STOP-BANG (SAHOS)</h4>
                    <div class="checkbox-group">
                        <label><input type="checkbox" class="sb-check"> <strong>S</strong>noring (Ronquidos fuertes)</label>
                        <label><input type="checkbox" class="sb-check"> <strong>T</strong>ired (Cansancio diurno)</label>
                        <label><input type="checkbox" class="sb-check"> <strong>O</strong>bserved (Apneas observadas)</label>
                        <label><input type="checkbox" class="sb-check"> <strong>P</strong>ressure (HTA)</label>
                        <label><input type="checkbox" class="sb-check"> <strong>B</strong>MI > 35 kg/m2</label>
                        <label><input type="checkbox" class="sb-check"> <strong>A</strong>ge > 50 años</label>
                        <label><input type="checkbox" class="sb-check"> <strong>N</strong>eck (Cuello >40cm)</label>
                        <label><input type="checkbox" class="sb-check"> <strong>G</strong>ender (Masculino)</label>
                    </div>
                    <button class="btn-calc" onclick="calcStopBang()">Calcular Riesgo SAHOS</button>
                    <div id="sb-result" class="result-display"></div>
                </div>

            </div>

            <div style="display: flex; flex-direction: column; gap: 20px;">
                
                <div class="risk-box">
                    <h4><i class="fas fa-heart-pulse"></i> Índice Cardíaco de Lee (RCRI)</h4>
                    <div class="checkbox-group">
                        <label><input type="checkbox" class="rcri-check"> Cx Alto Riesgo (Vascular/Torácica/Abd)</label>
                        <label><input type="checkbox" class="rcri-check"> Historia Cardiopatía Isquémica</label>
                        <label><input type="checkbox" class="rcri-check"> Historia Insuficiencia Cardíaca</label>
                        <label><input type="checkbox" class="rcri-check"> Enf. Cerebrovascular</label>
                        <label><input type="checkbox" class="rcri-check"> Diabetes insulinodependiente</label>
                        <label><input type="checkbox" class="rcri-check"> Creatinina > 2.0 mg/dL</label>
                    </div>
                    <button class="btn-calc" onclick="calcRCRI()">Calcular RCRI</button>
                    <div id="rcri-result" class="result-display"></div>
                </div>

                <div class="risk-box">
                    <h4><i class="fas fa-user-md"></i> Escala Apfel (NVPO)</h4>
                    <div class="checkbox-group" style="display: grid; grid-template-columns: 1fr 1fr;">
                        <label><input type="checkbox" id="apfel-female"> Mujer</label>
                        <label><input type="checkbox" id="apfel-nosmoke"> No Fuma</label>
                        <label><input type="checkbox" id="apfel-hist"> Hist. NVPO</label>
                        <label><input type="checkbox" id="apfel-opioid"> Opioides Post</label>
                    </div>
                    <button class="btn-calc" onclick="calcApfel()">Calcular NVPO</button>
                    <div id="apfel-result" class="result-display"></div>
                </div>

            </div>
        </div>
    </section>

    <section id="pediatria" class="premium-wrapper">
        <div class="section-title">
            <i class="fas fa-baby fa-2x"></i>
            <h2>Anestesia Pediátrica & PALS</h2>
        </div>

        <div class="lock-overlay" id="premiumLock">
            <div class="lock-badge">
                <i class="fas fa-crown fa-3x" style="color: var(--gold); margin-bottom:10px;"></i>
                <h3>Contenido Exclusivo</h3>
                <p>Accede a calculadoras de dosis, tubos endotraqueales y algoritmos PALS completos.</p>
                <button class="btn-gold" onclick="unlockPremium()">Suscribirse / Ingresar</button>
            </div>
        </div>

        <div class="blur-content" id="pediatricContent">
            
            <div class="grid-2">
                <div class="risk-box">
                    <h4>Calculadora Vía Aérea Pediátrica</h4>
                    <label>Edad (años): <input type="number" id="pedAge" style="width:60px;"></label>
                    <button class="btn-calc" onclick="calcPedAirway()">Calcular Tubo ET</button>
                    <div id="ped-airway-res" style="margin-top:10px; font-weight:bold;"></div>
                </div>

                <div class="risk-box">
                    <h4>Drogas Vasoactivas (Niños)</h4>
                    <label>Peso (kg): <input type="number" id="pedWeight" style="width:80px;"></label>
                    <p style="font-size:0.8rem; color:#666;">Incluye Adrenalina, Milrinona y Dobutamina.</p>
                    <button class="btn-calc">Abrir Calculadora Completa</button>
                </div>
            </div>

            <div style="margin-top: 2rem;">
                <h4>Manuales y Algoritmos PALS (Descarga)</h4>
                <div class="grid-3">
                    <div class="resource-card">
                        <div class="card-content">
                            <h5>Algoritmo Paro Cardíaco</h5>
                            <small>Actualización AHA 2020-2024</small>
                        </div>
                        <a href="#" class="card-btn">Ver PDF</a>
                    </div>
                    <div class="resource-card">
                        <div class="card-content">
                            <h5>Taquicardia con Pulso</h5>
                            <small>Manejo de arritmias ped.</small>
                        </div>
                        <a href="#" class="card-btn">Ver PDF</a>
                    </div>
                    <div class="resource-card">
                        <div class="card-content">
                            <h5>Bradicardia Sintomática</h5>
                            <small>Algoritmo completo</small>
                        </div>
                        <a href="#" class="card-btn">Ver PDF</a>
                    </div>
                </div>
            </div>

        </div>
    </section>

    <section id="resumenes">
        <div class="section-title">
            <i class="fas fa-graduation-cap fa-2x"></i>
            <h2>Resúmenes y Clases</h2>
        </div>
        <div class="grid-3">
            <div class="resource-card">
                <div class="card-img">
                    

[Image of lungs diagram]
 <br>
                </div>
                <div class="card-content">
                    <span class="card-meta">Fisiología Respiratoria</span>
                    <h4>Ventilación Unipulmonar</h4>
                    <p>Puntos clave sobre el manejo del tubo de doble lumen y bloqueadores bronquiales.</p>
                </div>
                <a href="#" class="card-btn">Leer Resumen</a>
            </div>
            <div class="resource-card">
                <div class="card-img">
                    <i class="fas fa-brain fa-3x"></i>
                </div>
                <div class="card-content">
                    <span class="card-meta">Neuroanestesia</span>
                    <h4>Manejo de la PIC</h4>
                    <p>Fisiopatología y estrategias farmacológicas para el control de la presión intracraneal.</p>
                </div>
                <a href="#" class="card-btn">Leer Resumen</a>
            </div>
            <div class="resource-card">
                <div class="card-img">
                    <i class="fas fa-syringe fa-3x"></i>
                </div>
                <div class="card-content">
                    <span class="card-meta">Regional</span>
                    <h4>Bloqueos de Fascia</h4>
                    <p>ESP Block vs Paravertebral: Indicaciones y técnica ecoguiada.</p>
                </div>
                <a href="#" class="card-btn">Ver Video</a>
            </div>
        </div>
    </section>

    <section id="articulos">
        <div class="section-title">
            <i class="fas fa-newspaper fa-2x"></i>
            <h2>Artículos Recientes</h2>
        </div>
        <div class="grid-2">
            <div style="border-left: 4px solid var(--secondary); padding-left: 15px;">
                <span class="card-meta">Publicado: 28 Oct 2024</span>
                <h3>Uso de Dexmedetomidina en Pediatría</h3>
                <p>Revisión sistemática sobre la seguridad de la dexmedetomidina intranasal como premedicación...</p>
                <a href="#" style="color: var(--primary); font-weight: bold;">Leer artículo completo &rarr;</a>
            </div>
            <div style="border-left: 4px solid var(--secondary); padding-left: 15px;">
                <span class="card-meta">Publicado: 15 Oct 2024</span>
                <h3>Hipotensión Intraoperatoria y Daño Renal</h3>
                <p>Nuevos umbrales de presión arterial media sugeridos por el estudio POISE-3 para evitar AKI...</p>
                <a href="#" style="color: var(--primary); font-weight: bold;">Leer artículo completo &rarr;</a>
            </div>
            <div style="border-left: 4px solid var(--secondary); padding-left: 15px;">
                <span class="card-meta">Publicado: 01 Oct 2024</span>
                <h3>Actualización GLP-1 y Ayuno</h3>
                <p>Nuevas directrices de la ASA sobre pacientes que toman agonistas GLP-1 (Ozempic/Wegovy)...</p>
                <a href="#" style="color: var(--primary); font-weight: bold;">Leer artículo completo &rarr;</a>
            </div>
        </div>
    </section>

</div>

<footer style="background: var(--text-main); color: #ccc; padding: 3rem 0; text-align: center; margin-top: 3rem;">
    <div class="container">
        <p>&copy; 2024 Portal de Anestesiología. Todos los derechos reservados.</p>
        <p style="font-size: 0.8rem; opacity: 0.6; max-width: 600px; margin: 0 auto;">
            DISCLAIMER: Esta aplicación es una ayuda cognitiva. Los cálculos de riesgo y dosis deben ser verificados clínicamente. 
            El autor no se responsabiliza por errores médicos derivados del uso de este software.
        </p>
    </div>
</footer>

<script>
    // --- 1. LÓGICA DE SUSCRIPCIÓN ---
    function unlockPremium() {
        const code = prompt("Ingrese su código de suscripción (Demo: 'MEDICINA'):");
        if(code && code.toUpperCase() === 'MEDICINA') {
            document.getElementById('premiumLock').style.display = 'none';
            document.getElementById('pediatricContent').classList.remove('blur-content');
            alert("Acceso Premium Desbloqueado");
        } else {
            alert("Código incorrecto.");
        }
    }

    // --- 2. CALCULADORA RCRI (LEE) ---
    function calcRCRI() {
        const checks = document.querySelectorAll('.rcri-check');
        let count = 0;
        checks.forEach(c => { if(c.checked) count++; });

        let result = "";
        if(count === 0) result = "Clase I (0.4% Riesgo Complicaciones)";
        else if(count === 1) result = "Clase II (0.9% Riesgo Complicaciones)";
        else if(count === 2) result = "Clase III (6.6% Riesgo Complicaciones)";
        else result = `Clase IV (>11% Riesgo). ${count} Factores presentes.`;

        const display = document.getElementById('rcri-result');
        display.style.display = 'block';
        display.innerText = result;
    }

    // --- 3. CALCULADORA APFEL ---
    function calcApfel() {
        let score = 0;
        if(document.getElementById('apfel-female').checked) score++;
        if(document.getElementById('apfel-nosmoke').checked) score++;
        if(document.getElementById('apfel-hist').checked) score++;
        if(document.getElementById('apfel-opioid').checked) score++;

        let risk = "10%";
        if(score === 1) risk = "21%";
        if(score === 2) risk = "39%";
        if(score === 3) risk = "61%";
        if(score === 4) risk = "79%";

        const display = document.getElementById('apfel-result');
        display.style.display = 'block';
        display.innerHTML = `Puntaje: ${score}/4. Riesgo NVPO: ${risk}`;
    }

    // --- 4. CALCULADORA STOP-BANG (NUEVA) ---
    function calcStopBang() {
        const checks = document.querySelectorAll('.sb-check');
        let score = 0;
        checks.forEach(c => { if(c.checked) score++; });

        let riskLevel = "";
        let color = "";

        if(score <= 2) {
            riskLevel = "Riesgo BAJO de SAHOS";
            color = "#28a745"; // Verde
        } else if (score >= 3 && score <= 4) {
            riskLevel = "Riesgo INTERMEDIO de SAHOS";
            color = "#ffc107"; // Amarillo oscuro
        } else {
            riskLevel = "Riesgo ALTO de SAHOS";
            color = "#dc3545"; // Rojo
        }

        const display = document.getElementById('sb-result');
        display.style.display = 'block';
        display.style.color = color;
        display.innerHTML = `Puntaje: ${score}/8 <br> <strong>${riskLevel}</strong>`;
    }

    // --- 5. CALCULADORA TUBOS PEDIÁTRICOS (SIMPLE) ---
    function calcPedAirway() {
        const age = parseFloat(document.getElementById('pedAge').value);
        if(!age) return;

        // Fórmulas clásicas (Cole)
        const tubeUncuffed = (age / 4) + 4;
        const tubeCuffed = (age / 4) + 3.5;
        const depth = (age / 2) + 12;

        document.getElementById('ped-airway-res').innerHTML = `
            Tubo s/balón: ${tubeUncuffed} <br>
            Tubo c/balón: ${tubeCuffed} <br>
            Profundidad a labios: ${depth} cm
        `;
    }
</script>

</body><script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-firestore-compat.js"></script>

<script>
    // Tu lógica existente (unlockPremium, calcRCRI, etc.)
</script>
</html>
