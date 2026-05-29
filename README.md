<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MateVida Digital: El Mercado</title>
    <style>
        :root {
            --bg-light: #F4F6F9;
            --mined-green: #2ECC71;
            --mined-dark-green: #27AE60;
            --blue-option: #4A90E2;
            --yellow-option: #F5A623;
            --orange-option: #E67E22;
            --green-option: #2ECC71;
            --text-dark: #2C3E50;
            --text-muted: #7F8C8D;
            --card-bg: #FFFFFF;
            --pastel-error: #FADBD8;
            --soft-red: #C0392B;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Roboto, sans-serif;
            user-select: none;
            -webkit-user-select: none;
        }

        body {
            background-color: var(--bg-light);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            color: var(--text-dark);
        }

        /* BARRA SUPERIOR COMPACTA (FUSIONADA Y OPTIMIZADA) */
        .barra-superior {
            background: var(--mined-green);
            color: white;
            padding: 8px 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-weight: bold;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }

        .seccion-izquierda {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .btn-volver {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            color: white;
            font-size: 14px;
            font-weight: bold;
            padding: 5px 10px;
            border-radius: 12px;
            cursor: pointer;
            display: flex;
            align-items: center;
        }

        .info-titulo-nivel {
            display: flex;
            flex-direction: column;
        }
        
        .info-titulo-nivel h1 {
            font-size: 16px;
            font-weight: 800;
            line-height: 1.1;
        }
        
        .info-titulo-nivel span {
            font-size: 11px;
            opacity: 0.9;
        }

        .indicators-derecha {
            display: flex;
            gap: 6px;
            align-items: center;
        }

        .badge-superior {
            background: rgba(255, 255, 255, 0.25);
            padding: 4px 8px;
            border-radius: 12px;
            font-size: 13px;
            display: flex;
            align-items: center;
            gap: 3px;
            white-space: nowrap;
        }

        /* CONTENEDOR DE JUEGO ADAPTATIVO */
        .contenido-juego {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: flex-start; /* Sube el contenido en móviles */
            padding: 12px;
            width: 100%;
            max-width: 800px;
            margin: 0 auto;
        }

        .tarjeta-juego {
            width: 100%;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .bloque-problema {
            background: #E8F8F5;
            border: 2.5px solid var(--mined-green);
            border-radius: 18px;
            padding: 15px;
            position: relative;
            box-shadow: 0 3px 10px rgba(0,0,0,0.04);
        }

        .encabezado-problema {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }

        .icono-producto {
            font-size: 36px;
            background: white;
            padding: 6px;
            border-radius: 12px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            display: flex;
            align-items: center;
            justify-content: center;
            width: 50px;
            height: 50px;
        }

        .btn-audio-control {
            background: white;
            border: 2px solid var(--mined-green);
            color: var(--mined-dark-green);
            padding: 6px 14px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 13px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 6px;
            transition: all 0.2s ease;
        }

        .btn-audio-control.activo {
            background: #E8F8F5;
            border-color: var(--mined-dark-green);
            animation: pulsoSuave 2s infinite ease-in-out;
        }

        .btn-audio-control.pausado {
            background: #FCF3CF;
            border-color: var(--yellow-option);
            color: #B7950B;
        }

        @keyframes pulsoSuave {
            0% { transform: scale(1); }
            50% { transform: scale(1.02); }
            100% { transform: scale(1); }
        }

        .texto-problema {
            font-size: 17px;
            line-height: 1.4;
            font-weight: 700;
            color: var(--text-dark);
        }

        /* CUADRÍCULA DE OPCIONES COMPACTA */
        .cuadrícula-opciones {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
        }

        .btn-opcion {
            background: white;
            border-radius: 14px;
            padding: 12px 8px;
            font-size: 24px;
            font-weight: 800;
            color: var(--text-dark);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            box-shadow: 0 3px 5px rgba(0,0,0,0.04);
            min-height: 55px;
            transition: background-color 0.1s;
        }

        /* Indicador circular de color */
        .btn-opcion::before {
            content: '';
            position: absolute;
            left: 12px;
            top: 50%;
            transform: translateY(-50%);
            width: 10px;
            height: 10px;
            border-radius: 50%;
        }

        .opcion-azul { border: 2.5px solid var(--blue-option); }
        .opcion-azul::before { background-color: var(--blue-option); }

        .opcion-amarilla { border: 2.5px solid var(--yellow-option); }
        .opcion-amarilla::before { background-color: var(--yellow-option); }

        .opcion-naranja { border: 2.5px solid var(--orange-option); }
        .opcion-naranja::before { background-color: var(--orange-option); }

        .opcion-verde { border: 2.5px solid var(--green-option); }
        .opcion-verde::before { background-color: var(--green-option); }

        .btn-opcion.error-seleccion {
            background-color: var(--pastel-error);
            border-color: var(--soft-red);
            color: var(--soft-red);
            opacity: 0.7;
        }

        .btn-opcion.correcto-seleccion {
            background-color: #E8F8F5;
            border-color: var(--mined-green);
            color: var(--mined-dark-green);
        }

        /* PANTALLAS DE ESTADO */
        .pantalla-estado {
            background: white;
            padding: 20px 15px;
            border-radius: 18px;
            text-align: center;
            box-shadow: 0 6px 15px rgba(0,0,0,0.05);
            max-width: 450px;
            width: 100%;
            margin-top: 10px;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .pantalla-estado h2 {
            font-size: 20px;
        }

        .btn-grande {
            background: var(--mined-green);
            color: white;
            border: none;
            padding: 14px 28px;
            font-size: 16px;
            font-weight: bold;
            border-radius: 12px;
            cursor: pointer;
            box-shadow: 0 4px 0 var(--mined-dark-green);
            width: 100%;
        }

        .marcador-final {
            font-size: 40px;
            font-weight: 900;
            color: var(--mined-dark-green);
        }

        .detalles-finales {
            font-size: 14px;
            color: var(--text-dark);
            line-height: 1.6;
            background: #F8FAFC;
            padding: 12px;
            border-radius: 12px;
        }

        .linea-detalle {
            display: flex;
            justify-content: space-between;
            border-bottom: 1px dashed #E2E8F0;
            padding: 5px 0;
        }
    </style>
</head>
<body>

    <!-- BARRA ÚNICA REESTRUCTURADA: SIN DOBLE TÍTULO Y SIN BLOQUE VERDE GIGANTE -->
    <div class="barra-superior">
        <div class="seccion-izquierda">
            <button class="btn-volver" onclick="irAlInicio()">←</button>
            <div class="info-titulo-nivel">
                <h1>El Mercado</h1>
                <span>Nivel 10</span>
            </div>
        </div>
        <div class="indicators-derecha">
            <div class="badge-superior">⭐ <span id="txt-puntos">0</span> pts</div>
            <div class="badge-superior">⏱️ <span id="txt-tiempo">0s</span></div>
        </div>
    </div>

    <div class="contenido-juego">
        
        <div id="pantalla-inicio" class="pantalla-estado">
            <h2>🛍️ ¡Bienvenido al Mercado!</h2>
            <p style="color: var(--text-muted); font-size: 14px;">Pulsa el botón de audio cuando desees escuchar la lectura del problema o pausarla en cualquier momento.</p>
            <button class="btn-grande" onclick="iniciarJuego()">¡Comenzar Reto! 🚀</button>
        </div>

        <div id="pantalla-juego" class="tarjeta-juego" style="display: none;">
            <div class="bloque-problema">
                <div class="encabezado-problema">
                    <span class="icono-producto" id="prod-icono">🛍️</span>
                    <button class="btn-audio-control" id="btn-audio" onclick="alternarAudioEnunciado()">🔊 Escuchar</button>
                </div>
                <p class="texto-problema" id="prod-enunciado">Generando desafío...</p>
            </div>

            <div class="cuadrícula-opciones">
                <button class="btn-opcion opcion-azul" onclick="verificarRespuesta(0, this)" id="opt-0">0</button>
                <button class="btn-opcion opcion-amarilla" onclick="verificarRespuesta(1, this)" id="opt-1">0</button>
                <button class="btn-opcion opcion-naranja" onclick="verificarRespuesta(2, this)" id="opt-2">0</button>
                <button class="btn-opcion opcion-verde" onclick="verificarRespuesta(3, this)" id="opt-3">0</button>
            </div>
        </div>

        <div id="pantalla-final" class="pantalla-estado" style="display: none;">
            <h2>🏆 ¡Resultado Final!</h2>
            <p style="color: var(--text-muted);">Circuito del mercado completado.</p>
            <div class="marcador-final" id="score-total">0 pts</div>
            
            <div class="detalles-finales">
                <div class="linea-detalle"><span>Puntaje Base:</span> <span id="lbl-puntos-base">100 pts</span></div>
                <div class="linea-detalle" style="color: var(--soft-red);"><span>Errores:</span> <span id="lbl-penalizacion">-0 pts</span></div>
                <div class="linea-detalle" style="margin-top: 5px; border-top: 1px solid #CBD5E1; padding-top: 5px; font-weight: bold;"><span>Tiempo Empleado:</span> <span id="lbl-tiempo-total">0s</span></div>
            </div>
            
            <button class="btn-grande" onclick="irAlInicio()">Volver a Jugar 🔄</button>
        </div>

    </div>

    <script>
        let problemas = [];
        let indiceActual = 0;
        let puntosBaseAcumulados = 0;
        let totalCorreccionesModoJuego = 0;
        let tiempoSegundos = 0;
        let intervaloTiempo = null;
        let audioCtx = null;
        let blockAccionSeleccion = false;
        let discursoActual = null;
        let estadoAudio = "detenido"; 

        const plantillasProblemas = [
            {
                icono: "🛍️",
                generar: () => {
                    let total = Math.floor(Math.random() * 50) + 100; 
                    let gasto = Math.floor(Math.random() * 40) + 20;   
                    let sol = total - gasto;
                    return {
                        texto: `Papá fue al mercado con C$${total}. Gastó C$${gasto} en verduras. ¿Cuánto dinero le sobra?`,
                        lectura: `Papá fue al mercado con ${total} córdobas. Gastó ${gasto} córdobas en verduras. ¿Cuánto dinero le sobra?`,
                        correcta: sol
                    };
                }
            },
            {
                icono: "🍅",
                generar: () => {
                    let t = Math.floor(Math.random() * 10) + 10; 
                    let c = Math.floor(Math.random() * 10) + 5; 
                    let sol = t + c;
                    return {
                        texto: `El puesto tiene ${t} tomates y ${c} cebollas. ¿Cuántas verduras hay en total?`,
                        lectura: `El puesto tiene ${t} tomates y ${c} cebollas. ¿Cuántas verduras hay en total?`,
                        correcta: sol
                    };
                }
            },
            {
                icono: "🍌",
                generar: () => {
                    let docenas = Math.floor(Math.random() * 2) + 2; 
                    let sol = docenas * 12;
                    return {
                        texto: `Doña María compró ${docenas} docenas de bananos. ¿Cuántas unidades tiene en total?`,
                        lectura: `Doña María compró ${docenas} docenas de bananos. ¿Cuántas unidades tiene en total?`,
                        correcta: sol
                    };
                }
            },
            {
                icono: "🧀",
                generar: () => {
                    let precioLibra = Math.floor(Math.random() * 10) + 60; 
                    let libras = 2;        
                    let sol = precioLibra * libras;
                    return {
                        texto: `La libra de queso cuesta C$${precioLibra}. Si compramos ${libras} libras, ¿cuánto pagaremos?`,
                        lectura: `La libra de queso cuesta ${precioLibra} córdobas. Si compramos ${libras} libras, ¿cuánto pagaremos?`,
                        correcta: sol
                    };
                }
            },
            {
                icono: "🍊",
                generar: () => {
                    let naranjas = Math.floor(Math.random() * 20) + 30; 
                    let danadas = Math.floor(Math.random() * 5) + 3;   
                    let sol = naranjas - danadas;
                    return {
                        texto: `En un balde hay ${naranjas} naranjas. Se encontraron ${danadas} dañadas. ¿Cuántas buenas quedan?`,
                        lectura: `En un balde hay ${naranjas} naranjas. Se encontraron ${danadas} dañadas. ¿Cuántas buenas quedan?`,
                        correcta: sol
                    };
                }
            }
        ];

        function inicializarAudio() {
            if (!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
        }

        function alternarAudioEnunciado() {
            if (!('speechSynthesis' in window)) return;
            const btn = document.getElementById('btn-audio');

            if (estadoAudio === "detenido") {
                window.speechSynthesis.cancel();
                discursoActual = new SpeechSynthesisUtterance(problemas[indiceActual].lectura);
                discursoActual.lang = 'es-ES';
                discursoActual.rate = 0.95;
                discursoActual.onend = () => { resetearBotonAudio(); };

                estadoAudio = "reproduciendo";
                btn.innerHTML = "⏸️ Pausar";
                btn.className = "btn-audio-control activo";
                window.speechSynthesis.speak(discursoActual);

            } else if (estadoAudio === "reproduciendo") {
                window.speechSynthesis.pause();
                estadoAudio = "pausado";
                btn.innerHTML = "▶️ Cont.";
                btn.className = "btn-audio-control pausado";

            } else if (estadoAudio === "pausado") {
                window.speechSynthesis.resume();
                estadoAudio = "reproduciendo";
                btn.innerHTML = "⏸️ Pausar";
                btn.className = "btn-audio-control activo";
            }
        }

        function detenerAudioLimpio() {
            if ('speechSynthesis' in window) window.speechSynthesis.cancel();
            resetearBotonAudio();
        }

        function resetearBotonAudio() {
            estadoAudio = "detenido";
            const btn = document.getElementById('btn-audio');
            if(btn) {
                btn.innerHTML = "🔊 Escuchar";
                btn.className = "btn-audio-control";
            }
        }

        function emitirVozObligatoria(texto) {
            if ('speechSynthesis' in window) {
                window.speechSynthesis.cancel(); 
                resetearBotonAudio();
                const u = new SpeechSynthesisUtterance(texto);
                u.lang = 'es-ES';
                u.rate = 1.0;
                window.speechSynthesis.speak(u);
            }
        }

        function sonarEfectoInclusivo(tipo) {
            inicializarAudio();
            if(!audioCtx) return;

            const osc = audioCtx.createOscillator();
            const gain = audioCtx.createGain();
            osc.connect(gain);
            gain.connect(audioCtx.destination);

            if (tipo === 'correcto') {
                osc.type = 'sine';
                osc.frequency.setValueAtTime(440, audioCtx.currentTime); 
                osc.frequency.exponentialRampToValueAtTime(554.37, audioCtx.currentTime + 0.1); 
                gain.gain.setValueAtTime(0.05, audioCtx.currentTime);
                gain.gain.linearRampToValueAtTime(0, audioCtx.currentTime + 0.25);
                osc.start(); osc.stop(audioCtx.currentTime + 0.25);
            } else if (tipo === 'incorrecto') {
                osc.type = 'sine';
                osc.frequency.setValueAtTime(261.63, audioCtx.currentTime); 
                gain.gain.setValueAtTime(0.06, audioCtx.currentTime);
                gain.gain.linearRampToValueAtTime(0, audioCtx.currentTime + 0.15);
                osc.start(); osc.stop(audioCtx.currentTime + 0.15);
            }
        }

        function construirSetProblemas() {
            let combinacion = [...plantillasProblemas, ...plantillasProblemas].sort(() => Math.random() - 0.5);
            return combinacion.map(p => {
                let datos = p.generar();
                return {
                    icono: p.icono,
                    texto: datos.texto,
                    lectura: datos.lectura,
                    correcta: datos.correcta,
                    opciones: crearOpciones(datos.correcta)
                };
            });
        }

        function crearOpciones(correcta) {
            let opciones = new Set([correcta]);
            while(opciones.size < 4) {
                let desvio = Math.floor(Math.random() * 6) + 1;
                let distractor = Math.random() > 0.5 ? correcta + desvio : correcta - desvio;
                if(distractor > 0) opciones.add(distractor);
            }
            return [...opciones].sort(() => Math.random() - 0.5);
        }

        function iniciarJuego() {
            inicializarAudio();
            problemas = construirSetProblemas();
            indiceActual = 0;
            puntosBaseAcumulados = 0;
            totalCorreccionesModoJuego = 0;
            tiempoSegundos = 0;
            blockAccionSeleccion = false;

            document.getElementById('txt-puntos').innerText = puntosBaseAcumulados;
            document.getElementById('txt-tiempo').innerText = tiempoSegundos + "s";

            document.getElementById('pantalla-inicio').style.display = 'none';
            document.getElementById('pantalla-final').style.display = 'none';
            document.getElementById('pantalla-juego').style.display = 'flex';

            clearInterval(intervaloTiempo);
            intervaloTiempo = setInterval(() => {
                tiempoSegundos++;
                document.getElementById('txt-tiempo').innerText = tiempoSegundos + "s";
            }, 1000);

            desplegarProblema();
        }

        function desplegarProblema() {
            blockAccionSeleccion = false;
            detenerAudioLimpio(); 
            
            let p = problemas[indiceActual];
            document.getElementById('prod-icono').innerText = p.icono;
            document.getElementById('prod-enunciado').innerText = p.texto;

            for(let i = 0; i < 4; i++) {
                let btn = document.getElementById(`opt-${i}`);
                btn.innerText = p.opciones[i];
                btn.className = `btn-opcion ${obtenerClaseColorEstilo(i)}`;
            }
        }

        function obtenerClaseColorEstilo(indice) {
            if(indice === 0) return 'opcion-azul';
            if(indice === 1) return 'opcion-amarilla';
            if(indice === 2) return 'opcion-naranja';
            return 'opcion-verde';
        }

        function verificarRespuesta(idxSeleccionado, botonElemento) {
            if(blockAccionSeleccion || botonElemento.classList.contains('error-seleccion')) return;

            let p = problemas[indiceActual];
            let respuestaElegida = p.opciones[idxSeleccionado];

            if (respuestaElegida == p.correcta) {
                blockAccionSeleccion = true; 
                sonarEfectoInclusivo('correcto');
                botonElemento.classList.add('correcto-seleccion');
                
                puntosBaseAcumulados += 10; 
                document.getElementById('txt-puntos').innerText = puntosBaseAcumulados;
                
                emitirVozObligatoria("¡Excelente!");

                setTimeout(() => {
                    indiceActual++;
                    if(indiceActual < 10) {
                        desplegarProblema();
                    } else {
                        concluirJuego();
                    }
                }, 1200);

            } else {
                sonarEfectoInclusivo('incorrecto');
                botonElemento.classList.add('error-seleccion'); 
                totalCorreccionesModoJuego++; 
                emitirVozObligatoria("Intenta de nuevo.");
            }
        }

        function concluirJuego() {
            clearInterval(intervaloTiempo);
            detenerAudioLimpio();

            document.getElementById('pantalla-juego').style.display = 'none';
            document.getElementById('pantalla-final').style.display = 'flex';

            let penalizacionPorErrores = totalCorreccionesModoJuego * 3; 
            let scoreFinalNeto = puntosBaseAcumulados - penalizacionPorErrores;
            if(scoreFinalNeto < 0) scoreFinalNeto = 0;

            document.getElementById('score-total').innerText = scoreFinalNeto + " pts";
            document.getElementById('lbl-puntos-base').innerText = puntosBaseAcumulados + " pts";
            document.getElementById('lbl-penalizacion').innerText = `-${penalizacionPorErrores} pts (${totalCorreccionesModoJuego} errores)`;
            document.getElementById('lbl-tiempo-total').innerText = tiempoSegundos + " segundos";
        }

        function irAlInicio() {
            clearInterval(intervaloTiempo);
            detenerAudioLimpio();
            document.getElementById('txt-puntos').innerText = "0";
            document.getElementById('txt-tiempo').innerText = "0s";
            document.getElementById('pantalla-juego').style.display = 'none';
            document.getElementById('pantalla-final').style.display = 'none';
            document.getElementById('pantalla-inicio').style.display = 'flex';
        }
    </script>
</body>
</html>
