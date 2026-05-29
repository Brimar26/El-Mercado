
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
            overflow-y: auto;
        }

        /* BARRA SUPERIOR RESPONSIVA */
        .barra-superior {
            background: var(--mined-green);
            color: white;
            padding: 12px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-weight: bold;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            flex-wrap: wrap;
            gap: 10px;
        }

        .info-nivel {
            text-align: center;
            order: 2;
        }
        
        .info-nivel h1 {
            font-size: clamp(18px, 4vw, 22px); /* Ajustado el mínimo a 18px */
            font-weight: 800;
        }
        
        .info-nivel span {
            font-size: 13px;
            opacity: 0.9;
        }

        .btn-volver {
            background: transparent;
            border: none;
            color: white;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 5px;
            order: 1;
        }

        .indicadores-derecha {
            display: flex;
            gap: 10px;
            align-items: center;
            order: 3;
        }

        .badge-superior {
            background: rgba(255, 255, 255, 0.2);
            padding: 6px 12px;
            border-radius: 20px;
            font-size: clamp(14px, 3.5vw, 16px); /* Garantiza legibilidad en celular */
            display: flex;
            align-items: center;
            gap: 5px;
            white-space: nowrap;
        }

        /* CONTENEDOR DE JUEGO ADAPTATIVO */
        .contenido-juego {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: clamp(15px, 4vw, 30px);
            width: 100%;
            max-width: 800px;
            margin: 0 auto;
        }

        .tarjeta-juego {
            width: 100%;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .bloque-problema {
            background: #E8F8F5;
            border: 3px solid var(--mined-green);
            border-radius: 24px;
            padding: clamp(20px, 5vw, 30px);
            position: relative;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        }

        .encabezado-problema {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            gap: 15px;
        }

        .icono-producto {
            font-size: clamp(36px, 8vw, 48px);
            background: white;
            padding: 8px;
            border-radius: 16px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.05);
            flex-shrink: 0;
        }

        .btn-audio-control {
            background: white;
            border: 2px solid var(--mined-green);
            color: var(--mined-dark-green);
            padding: 10px 22px;
            border-radius: 25px;
            font-weight: bold;
            font-size: 15px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all 0.2s ease;
            box-shadow: 0 3px 6px rgba(0,0,0,0.05);
            white-space: nowrap;
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
            50% { transform: scale(1.03); }
            100% { transform: scale(1); }
        }

        .texto-problema {
            font-size: clamp(18px, 4.5vw, 24px); /* Evita que el problema se encoja demasiado */
            line-height: 1.6;
            font-weight: 700;
            color: var(--text-dark);
        }

        /* CUADRÍCULA OPTIMIZADA PARA MÓVILES */
        .cuadrícula-opciones {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: clamp(12px, 3vw, 20px);
        }

        .btn-opcion {
            background: white;
            border-radius: 18px;
            padding: clamp(20px, 5vw, 28px); /* Mayor espacio de toque interno */
            font-size: clamp(22px, 6vw, 32px); /* Números grandes y claros en móviles */
            font-weight: 800;
            color: var(--text-dark);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            transition: background-color 0.2s, border-color 0.2s;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
            min-height: 70px; /* Evita que el botón colapse de tamaño */
        }

        .btn-opcion::before {
            content: '';
            position: absolute;
            left: 18px;
            top: 50%;
            transform: translateY(-50%);
            width: 14px;
            height: 14px;
            border-radius: 50%;
        }

        .opcion-azul { border: 3px solid var(--blue-option); }
        .opcion-azul::before { background-color: var(--blue-option); }

        .opcion-amarilla { border: 3px solid var(--yellow-option); }
        .opcion-amarilla::before { background-color: var(--yellow-option); }

        .opcion-naranja { border: 3px solid var(--orange-option); }
        .opcion-naranja::before { background-color: var(--orange-option); }

        .opcion-verde { border: 3px solid var(--green-option); }
        .opcion-verde::before { background-color: var(--green-option); }

        .btn-opcion.error-seleccion {
            background-color: var(--pastel-error);
            border-color: var(--soft-red);
            color: var(--soft-red);
            opacity: 0.7;
            cursor: not-allowed;
        }

        .btn-opcion.correcto-seleccion {
            background-color: #E8F8F5;
            border-color: var(--mined-green);
            color: var(--mined-dark-green);
        }

        /* PANTALLAS DE ESTADO AJUSTADAS */
        .pantalla-estado {
            background: white;
            padding: clamp(25px, 6vw, 40px) clamp(20px, 5vw, 30px);
            border-radius: 24px;
            text-align: center;
            box-shadow: 0 10px 25px rgba(0,0,0,0.05);
            max-width: 500px;
            width: 100%;
            margin: auto;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .pantalla-estado h2 {
            font-size: clamp(20px, 5vw, 26px);
        }

        .btn-grande {
            background: var(--mined-green);
            color: white;
            border: none;
            padding: 16px 32px;
            font-size: clamp(16px, 4vw, 19px);
            font-weight: bold;
            border-radius: 16px;
            cursor: pointer;
            box-shadow: 0 4px 0 var(--mined-dark-green);
            width: 100%; /* Ocupa el ancho disponible en la tarjeta */
        }

        .marcador-final {
            font-size: clamp(44px, 10vw, 60px);
            font-weight: 900;
            color: var(--mined-dark-green);
        }

        .detalles-finales {
            font-size: clamp(14px, 4vw, 16px);
            color: var(--text-dark);
            line-height: 1.8;
            background: #F8FAFC;
            padding: 15px;
            border-radius: 16px;
            text-align: left;
        }

        .linea-detalle {
            display: flex;
            justify-content: space-between;
            border-bottom: 1px dashed #E2E8F0;
            padding: 6px 0;
            gap: 10px;
        }

        /* REGLAS DE ADAPTACIÓN PARA SMARTPHONES (BREAKPOINT HASTA 600PX) */
        @media (max-width: 600px) {
            .barra-superior {
                padding: 10px 15px;
            }
            
            .info-nivel {
                width: 100%;
                order: 1; /* El título se coloca arriba en el centro */
                margin-bottom: 2px;
            }
            
            .btn-volver {
                order: 2;
            }
            
            .indicadores-derecha {
                order: 3;
            }

            .cuadrícula-opciones {
                grid-template-columns: 1fr; /* Una opción por fila en celular para maximizar espacio táctil */
                gap: 14px;
            }

            .btn-opcion {
                padding: 22px;
                justify-content: center;
                font-size: 28px; /* Forzado a tamaño grande en móvil */
            }
            
            .btn-opcion::before {
                left: 25px; /* Mantiene el círculo decorativo bien posicionado */
            }
        }
    </style>
</head>
<body>

    <div class="barra-superior">
        <button class="btn-volver" onclick="irAlInicio()">← Volver</button>
        <div class="info-nivel">
            <h1>El Mercado</h1>
            <span>Nivel 10</span>
        </div>
        <div class="indicadores-derecha">
            <div class="badge-superior">⭐ <span id="txt-puntos">0</span> pts</div>
            <div class="badge-superior">⏱️ <span id="txt-tiempo">0s</span></div>
        </div>
    </div>

    <div class="contenido-juego">
        
        <div id="pantalla-inicio" class="pantalla-estado">
            <h2>🛍️ ¡Bienvenido al Mercado!</h2>
            <p style="color: var(--text-muted); font-size: clamp(15px, 3.5vw, 16px);">Pulsa el botón de audio cuando desees escuchar la lectura del problema o pausarla en cualquier momento.</p>
            <button class="btn-grande" onclick="iniciarJuego()">¡Comenzar Reto! 🚀</button>
        </div>

        <div id="pantalla-juego" class="tarjeta-juego" style="display: none;">
            <div class="bloque-problema">
                <div class="encabezado-problema">
                    <span class="icono-producto" id="prod-icono">🍅</span>
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
                <div class="linea-detalle"><span>Puntaje Base (10 ejercicios):</span> <span id="lbl-puntos-base">100 pts</span></div>
                <div class="linea-detalle" style="color: var(--soft-red);"><span>Puntos menos por errores:</span> <span id="lbl-penalizacion">-0 pts</span></div>
                <div class="linea-detalle" style="margin-top: 8px; border-top: 2px solid #CBD5E1; padding-top: 8px; font-weight: 800;"><span>Tiempo Total Empleado:</span> <span id="lbl-tiempo-total">0s</span></div>
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
                btn.innerHTML = "▶️ Continuar";
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
                
                emitirVozObligatoria("Incorrecto, vuelve a intentar.");
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
