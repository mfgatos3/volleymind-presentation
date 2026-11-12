# VolleyMind & LifeLab - Estado del Proyecto y Memoria de Sesión

**Fecha de actualización:** 11 de noviembre de 2026  
**Proyecto:** VolleyMind & LifeLab  
**Objetivo:** Simulador 2D interactivo en HTML5 Canvas con evento Quick Time Event (QTE) calibrado a 2.5s, 3 finales narrativos definitorios, gestor de audio con fallbacks sintéticos/transcripción y conexión con Dashboard LifeLab y Módulo Formativo de Autorregulación Socioemocional.

---

## 1. Archivos en este Directorio

* **`animacion_voleyball.html`**: Simulador completo e interactivo (HTML5 Canvas 2D + Web Audio API + Dashboard + Módulo de Autorregulación).
* **`index.html`**: Presentación Reveal.js de la plataforma VolleyMind & LifeLab (calibrada a 2.5s QTE).
* **`presentacion_volleymind_lifelab.html`**: Copia espejo de la presentación.
* **`HISTORIAL_CONVERSACION.md`**: Registro histórico de requerimientos.
* **`RESUMEN_PROYECTO.md`**: Este documento de síntesis arquitectónica y técnica.

---

## 2. Implementación de Requisitos

### 1. Calibración del Tiempo QTE a 2.5s
* **Temporizador exacto de 2.50 segundos** (`2500ms`) vía `performance.now()` para simular una carga adrenérgica real bajo presión temporal.
* **Freeze-Frame táctico:** En el segundo 2.5, la acción se congela exactamente en las yemas de los dedos del armador #8 suspendido en el aire.
* **Indicador Visual Circular de Alta Presión:**
  * Indicador SVG circular con gradiente de tensión y cuenta regresiva (`2.5s` -> `0.0s`).
  * Transición de color adrenérgica: Cian/Lima (`#00f2fe`) -> Ámbar (`#ffd700`) -> Rojo/Carmesí palpitante (`#ff1744`) cuando el tiempo restante es inferior a 0.8s.
  * Pulso cardíaco acelerado vía Web Audio API (`audio.playHeartbeat()`).
* **Botones de Decisión Táctica:**
  * **Ruta de Servicio (PASAR):** Probabilidad de éxito del 85%, juego colectivo, rematador #10 libre.
  * **Ruta de Ego (REMATAR):** Probabilidad de éxito del 12%, autoafirmación individual, triple bloqueo rival.

### 2. Secuencias Visuales y Keyframes en Canvas (Estilo Webtoon/Manga Neón)
* **A. Secuencia Inicial Pre-QTE:**
  * Saque rival con estelas cinéticas rojas cruzando la red.
  * Recepción milagrosa del Líbero #5 en plancha baja (`dive_receive`) con parábola dorada ascendente.
  * Carrera y posicionamiento del Armador #8 situándose debajo del balón.
  * **Pausa Dramática:** Zoom táctico centrado en el armador con viñeta radial oscura y anotaciones holográficas en Canvas:
    * Anillo y flecha verde/cian hacia Zona 4: `[ZONA 4: DESMARCADA • ÉXITO 85%]`.
    * Muro y advertencia roja en la red: `[TRIPLE BLOQUEO ALINEADO • ÉXITO 12%]`.
* **B. Final 1: Ruta de Servicio (PASAR / 85% Éxito):**
  * Colocación parabólica suave y limpia hacia Zona 4.
  * Rematador #10 salta desmarcado y ejecuta un remate demoledor en cancha rival (`¡¡DOOON!!`, ondas de choque, destello blanco y temblor sísmico).
  * **Frame de Cierre Definitorio (Celebración con Trofeo):**
    * Auras resplandecientes cian y doradas rotando sobre fondo negro.
    * Los 4 jugadores (#8, #10, #5, #3) abrazados en el centro de la cancha.
    * Gráfico vectorial detallado de trofeo dorado de campeonato con estrella y rayos solares.
    * Rótulo destacado: `"25-24 ¡PUNTO Y VICTORIA POR SERVICIO COLECTIVO!"`.
    * Lluvia continua de partículas de confeti.
* **C. Final 2: Ruta de Ego (REMATAR / 12% Éxito):**
  * Armador ignora al compañero, salta solo a la red e intenta rematar.
  * Choque violento contra las 6 manos del triple bloqueo rival (`¡¡MONSTER BLOCK!!`, fracturas de pantalla tipo manga y sonido metálico seco).
  * Balón rebrota hacia el suelo de nuestro campo.
  * **Frame de Cierre Definitorio (Bloqueo Brutal y Frustración):**
    * Escena iluminada en densos tonos rojos y magenta (`#ff1744`, `#d946ef`).
    * Balón botando en el suelo de nuestro campo.
    * Armador #8 arrodillado con las manos en la cabeza en profunda lamentación (`kneel_regret`).
    * Compañeros con hombros caídos y gestos de desilusión (`disappointed_teammate`).
    * Rótulo: `"24-25 ¡BLOQUEO BRUTAL! FRUSTRACIÓN POR EGO INDIVIDUAL"`.
* **D. Final 3: Parálisis por Ansiedad (0.0s sin selección):**
  * El temporizador de 2.5s llega a 0.0s.
  * El armador se paraliza por el estrés, retira las manos por duda y desciende rígido (`anxiety_frozen`).
  * El balón cae libremente al suelo sin ser tocado jamás. Silbato arbitral agudo.
  * **Frame de Cierre Definitorio (Balón en el Suelo y la Inacción):**
    * Escena en estricta escala de grises con viñeta oscura profunda en los bordes.
    * Balón estático e inerte en el piso.
    * Armador congelado mirando fijamente sus manos vacías con gotas de sudor frío.
    * Sombra espectral ominosa que emerge detrás de él simbolizando el bloqueo emocional y la parálisis por presión.
    * Rótulo: `"24-25 PARÁLISIS POR ANSIEDAD: EL BALÓN EN EL SUELO"`.

### 3. Gestor de Audios y Sistema de Fallback Secundario
* Llamadas programadas a:
  * `audio_servicio_exito.mp3`
  * `audio_ego_refutacion.mp3`
  * `audio_paralisis_estres.mp3`
* **Verificación y Fallback:**
  * Si el archivo no existe o falla la carga, no interrumpe la simulación.
  * Despliega la **Tarjeta de Transcripción de Audio** en la interfaz con ecualizador animado, nombre del archivo y texto oratorio completo de LifeLab.
  * Emite un **tono armónico sintético** mediante Web Audio API:
    * Éxito: Arpegio triunfal en Do mayor.
    * Ego: Acorde menor/disonante tenso.
    * Parálisis: Tono sombrío continuo de baja frecuencia + silbato.
  * Botón opcional de **Síntesis Vocal (TTS)** mediante `speechSynthesis`.

### 4. Conexión con Dashboard LifeLab y Módulo Formativo de Autorregulación
* **Dashboard LifeLab:**
  * Gráfico de Radar de 5 factores generado dinámicamente en Canvas con estética neón:
    1. Control Inhibitorio (Freno Prefrontal)
    2. Visión Táctica (Zona 4)
    3. Vocación de Servicio Colectivo
    4. Conciencia Ética y Axiológica
    5. Resolución Bajo Presión
  * Final 1 (Servicio): Puntajes altos (Inhibición 95%, Visión 96%, Servicio 99%, Ética 98%, Resolución 92%) y felicitación destacada.
  * Final 2 (Ego) y Final 3 (Parálisis): Puntajes con alertas formativas (déficit inhibitorio o sobrecarga cognitiva).
* **Módulo Formativo de Autorregulación Socioemocional:**
  * Se abre automáticamente con auto-scroll suave hacia abajo del Canvas tras desencadenar Final 2 o Final 3.
  * **Tarjeta 1: Pausa Cognitiva (Freno Inhibitorio):** Freno prefrontal de 300ms sobre el impulso amigdalino.
  * **Tarjeta 2: Respiración Consciente en 4 Tiempos:** Widget interactivo de respiración cuadrada (*Box Breathing 4-4-4-4*) con animación visual circular en vivo y conteo de fases (Inhala -> Retén -> Exhala -> Retén).
  * **Tarjeta 3: Reencuadre Ético de la Jugada:** Transición axiológica del «yo» al «nosotros» y transferencia al proyecto de vida.
