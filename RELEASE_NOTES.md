# 🚀 Novela Audio Reader v1.0.0 — Lanzamiento Inicial

¡Bienvenido al lanzamiento oficial de **Novela Audio Reader**! Un reproductor y lector de novelas ligeras y libros offline diseñado para escuchar tus historias sin interrupciones con la pantalla apagada.

---

### 📦 Archivos del Release
- **Instalador APK:** `NovelaAudioReader.apk` (13.3 MB)
- **SHA-256:** `d942c884f6a28b08ca63cb7dcb945365ce9bd1e455c2a7b71ec8964aed497915`
- **Compatibilidad:** Android 7.0 (Nougat, API 24) en adelante.

---

### 🌟 Novedades y Características

#### 🎧 Reproducción y TTS Continuo
- **Pantalla apagada y segundo plano:** Foreground Service nativo con `WakeLock` parcial y controles multimedia integrados en la pantalla de bloqueo y barra de notificaciones (`MediaSessionCompat`).
- **Pre-encolado inteligente (Zero-Silence):** El motor sintetiza el fragmento siguiente antes de que culmine el actual, eliminando vacíos de audio entre párrafos.
- **Selector de velocidad en vivo:** Cambios de velocidad (0.75x a 2.0x) reflejados al instante.

#### 📖 Compatibilidad Multiformato
- **PDF:** Renderizado vectorial y extracción rápida sin desbordar memoria.
- **EPUB:** Extractor nativo por streaming con `ZipFile`, eliminación de artefactos XHTML y limpieza de `[OBJ]` en ilustraciones. Subsampling en portadas para proteger la memoria ante imágenes de alta resolución.
- **TXT:** Detección automática UTF-8 / Windows-1252 / ISO-8859-1 para preservar acentos y la letra `ñ`.
- **Preservación de diálogos:** Respeta las rayas de diálogo en español (`—` y `–`) para mantener la entonación literaria.

#### 👁️ Accesibilidad y Modo Baja Visión
- **Tipografía escalable:** Desde 12sp hasta **44sp** con pasos de `±2sp`.
- **Resaltado de párrafo activo:** Contraste cyan sobre fondo oscuro.
- **Botón flotante "Volver a la voz":** Regreso instantáneo al párrafo que está sonando si te desplazas manualmente.
- **Anti-toques accidentales:** Salto manual de audio únicamente mediante **doble toque** con respuesta háptica.

#### ⏱️ Temporizador de Apagado (Sleep Timer)
- Apagado automático configurable: **15, 30, 45 o 60 minutos**, o por conteo de fragmentos leídos. Notificación en vivo en el reproductor.

#### 🖼️ Riel de Portadas
- Detección automática en almacenamiento local con ordenamiento alfabético y por volúmenes (`Volumen 01`, `02`, `1.5`, etc.).
- 100% offline, sin publicidad, sin rastreadores y sin compras integradas.
