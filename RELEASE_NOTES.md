# 🚀 Novela Audio Reader v2.0.0 — Motor TTS Neuronal ONNX Offline (Claudia & Aldo México)

¡Bienvenido al lanzamiento de **Novela Audio Reader v2.0**! Una actualización mayor que transforma la experiencia auditiva incorporando voces neuronales de alta fidelidad **100% offline y privadas** sin depender de los motores robóticos del sistema.

---

### 📦 Archivos del Release
- **Instalador APK:** `NovelaAudioReader.apk` (o `NovelaAudioReader-v2.0.apk`) (~164 MB, incluye modelos ONNX y diccionarios fonéticos)
- **SHA-256:** `c40518938d52e4f98b5704cb5d216b1f2b9c6df53f68aaa1a7187d1c52e0caeb`
- **Compatibilidad:** Android 8.0 (Oreo, API 26) hasta Android 14/15/16 (API 34+). Arquitectura `arm64-v8a` pura.

---

### 🌟 Novedades de la Versión 2.0

#### 🧠 Motor Dual TTS Neuronal ONNX Offline (Piper VITS + sherpa-onnx)
- **Voces Mexicanas de Estudio Integradas:**
  * **✨ Claudia (Femenina):** Narración fluida, expresiva y natural en Español de México (`es_MX-claude-high`). Activa por defecto.
  * **✨ Aldo (Masculina):** Tono sobrio, balanceado y claro (`es_MX-ald-medium`).
- **Respaldo Híbrido:** Si lo deseas, puedes alternar en cualquier momento hacia las voces de tu motor nativo del sistema Android (`TextToSpeech`).

#### ⚡ Arquitectura Productor-Consumidor "Zero-Silence" con Pausa Inmediata
- **Doble Buffer en Memoria:** Mientras el fragmento actual suena en el consumidor `AudioTrack` (PCM 16-bit a 22.05 kHz), el hilo productor sintetiza por anticipado el párrafo siguiente. Cero vacíos ni baches sonoros entre oraciones.
- **Pausa y Salto Sub-milisegundo:** Al pulsar pausa o cambiar de fragmento, el buffer de hardware se vacía al instante (`pause()` + `flush()`) sin colas residuales ni latencias molestas.

#### 🔋 Ahorro de Recursos: Smart 30-Minute Auto-Kill en Pausa
- Al dejar la lectura en pausa por más de 30 minutos, la app salva atómicamente el progreso exacto, libera completamente la memoria nativa de los modelos ONNX (`release()`), apaga el `ForegroundService` y se auto-cierra para cuidar la batería y la RAM de tu teléfono.

#### 🛡️ Blindaje de Progreso Atómico
- Cada avance de fragmento, salto manual o pausa guarda instantáneamente la posición tanto en la sesión activa como en el índice persistente de la biblioteca para cada libro individual.

---

### 🛠️ Características Clásicas Mantenidas
- **Lectura con Pantalla Apagada:** Reproducción continua en segundo plano con `WakeLock` parcial y controles multimedia en pantalla de bloqueo y barra de notificaciones (`MediaSessionCompat`).
- **Multiformato:** Soporte para PDF, EPUB y TXT con extracción nativa ultra ligera.
- **Modo Baja Visión:** Tipografía escalable hasta 44sp con alto contraste cyan y anti-toques involuntarios (doble toque para saltar).
- **Temporizador de Apagado (Sleep Timer):** 15, 30, 45, 60 minutos o conteo de fragmentos.
- **Privacidad Total:** 100% offline, sin publicidad, sin telemetría ni rastreadores.
