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
            font-size: clamp(18px, 4vw, 22px);
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
            font-size: clamp(14px, 3.5vw, 16px);
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
            font-size: clamp(18px, 4.5vw, 24px);
            line-height: 1.6;
            font-weight: 700;
            color: var(--text-dark);
        }

        /* CUADRÍCULA OPTIMIZADA (Se reducen gaps para móviles de forma fluida) */
        .cuadrícula-opciones {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: clamp(10px, 3vw, 20px);
        }

        .btn-opcion {
            background: white;
            border-radius: 18px;
            padding: clamp(14px, 4.5vw, 28px); /* Reducción adaptativa del relleno vertical */
            font-size: clamp(22px, 6vw, 32px);
            font-weight: 800;
            color: var(--text-dark);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            transition: background-color 0.2s, border-color 0.2s;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
            min-height: 60px; /* Tamaño mínimo optimizado para evitar desborde vertical */
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
            width: 100%;
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

        /* REGLAS DE ADAPTACIÓN ESPECÍFICAS PARA SMARTPHONES */
        @media (max-width: 600px) {
            .barra-superior {
                padding: 10px 15px;
            }
            
            .info-nivel {
                width: 100%;
                order: 1;
                margin-bottom: 2px;
            }
            
            .btn-volver {
                order: 2;
            }
            
            .indicadores-derecha {
                order: 3;
            }

            .contenido-juego {
                padding: 10px; /* Reduce espacio en bordes de pantalla externa */
            }

            .tarjeta-juego {
                gap: 12px; /* Espaciado general entre tarjeta e interfaz reducido */
            }

            .bloque-problema {
                padding: 15px; /* Comprime la caja de problemas para ganar altura vertical */
            }

            .texto-problema {
                font-size: 1.1rem; /* Modera el texto del problema en pantallas muy chicas */
                line-height: 1.4;
            }

            .cuadrícula-opciones {
                grid-template-columns: repeat(2, 1fr); /* Se mantienen 2 columnas para optimizar espacio vertical */
                gap: 10px; /* Espacios mínimos entre casillas */
            }

            .btn-opcion {
                padding: 14px 10px; /* Menor padding vertical en móvil garantizando que no se corte */
                font-size: 24px; /* Tamaño claro y equilibrado */
                min-height: 55px;
            }
            
            .btn-opcion::before {
                left: 12px; /* Mantiene el punto decorativo alineado a la izquierda */
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
