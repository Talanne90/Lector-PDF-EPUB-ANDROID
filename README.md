# 📚 Novela Audio Reader

<div align="center">

![Android](https://img.shields.io/badge/Platform-Android%207.0%2B%20(API%2024%2B)-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Format](https://img.shields.io/badge/Formats-PDF%20%7C%20EPUB%20%7C%20TXT-FF7043?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Zero--Ads-100%25%20Offline-success?style=for-the-badge)

**Lector auditivo y visual de novelas ligeras, libros y textos largos con síntesis de voz (TTS) ininterrumpida en segundo plano y pantalla apagada.**

[Descargar APK](#-descarga-e-instalación) • [Características](#-características-principales) • [Capturas de Pantalla](#-capturas-de-pantalla) • [Arquitectura](#-arquitectura-técnica)

</div>

---

## 🌟 ¿Qué es Novela Audio Reader?

**Novela Audio Reader** es un reproductor y lector offline diseñado específicamente para lectores voraces de novelas ligeras, webnovels y literatura en formatos **PDF**, **EPUB** y **TXT**. 

A diferencia de los lectores convencionales saturados de publicidad o que pausan la voz al bloquear el dispositivo, Novela Audio Reader funciona como un reproductor de música: mantén el teléfono en el bolsillo o escucha con la pantalla apagada mientras el motor de voz nativo avanza de párrafo en párrafo de forma continua y fluida.

---

## ✨ Características Principales

### 🎧 Lectura Auditiva Continua (Segundo Plano y Pantalla Apagada)
- **Foreground Service con WakeLock:** Reproduce ininterrumpidamente durante horas sin ser cerrado por el optimizador de batería del sistema.
- **Pre-encolado Inteligente de Fragmentos (Zero-Silence):** El siguiente fragmento se sintetiza antes de que termine el actual, eliminando baches o silencios entre oraciones.
- **Controles Multimedia Nativos:** Controla la reproducción (Play/Pausa, anterior, siguiente) desde la barra de notificaciones, pantalla de bloqueo o tus auriculares Bluetooth.

### 📖 Soporte Multiformato Seguro y Rápido
- **PDF:** Extracción vectorial ligera por páginas sin desbordar la memoria RAM.
- **EPUB:** Motor nativo basado en streaming con `ZipFile` y parsing XML. Limpieza de artefactos XHTML y eliminación de caracteres comodín `[OBJ]` de ilustraciones.
- **TXT:** Detección automática UTF-8 y codificaciones alternativas en español (ISO-8859-1 / Windows-1252) para conservar tildes y la letra `ñ`.
- **Segmentación Sintáctica:** Divide el texto en fragmentos óptimos de ~300 caracteres respetando los signos de puntuación y las rayas de diálogo en español (`—`).

### 🖼️ Riel de Biblioteca con Portadas Automáticas
- **Detección inteligente de volúmenes:** Ordenamiento automático alfabético y numérico (`Volumen 01`, `02`, `1.5`, etc.).
- **Extracción de portadas en alta resolución:** Decodificación submuestreada (*2-pass inSampleSize*) que genera miniaturas nítidas sin saturar la GPU ni la memoria del sistema.

### 👁️ Modo Baja Visión y Accesibilidad
- **Tipografía Escalable:** Ajuste rápido de tamaño de fuente desde 12sp hasta **44sp** con pasos precisos de `±2sp`.
- **Resaltado de Lectura de Alto Contraste:** El párrafo activo se ilumina con acento cyan mientras el resto mantiene un contraste relajante para la vista.
- **Botón Flotante "Volver a la voz":** Si navegas manualmente por el libro, un botón contextual te regresa al párrafo que está sonando en un toque.
- **Anti-Toques Accidentales:** Salto manual de audio únicamente mediante **doble toque** con respuesta háptica sutil.

### ⏱️ Temporizador de Apagado (Sleep Timer)
- Escucha tus novelas antes de dormir: configura el apagado a los **15, 30, 45 o 60 minutos**, o define detenerte tras **X fragmentos**. Detención suave con notificación visual en vivo.

### 🚫 Privacidad Absoluta y Zero-Bloat
- **Sin anuncios, sin registros, sin telemetría ni conexión a internet obligatoria.**
- Todos tus libros, portadas y cachés permanecen exclusivamente en tu dispositivo.

---

## 📸 Capturas de Pantalla

<div align="center">

| Riel de Biblioteca y Portadas | Lector con Resaltado y Modo Baja Visión | Reproductor Persistente y Sleep Timer |
| :---: | :---: | :---: |
| *(Agrega captura de biblioteca en `screenshots/01_biblioteca.png`)* | *(Agrega captura del lector en `screenshots/02_lector.png`)* | *(Agrega captura de controles en `screenshots/03_player.png`)* |

</div>

---

## 📥 Descarga e Instalación

Puedes descargar la aplicación directamente desde este repositorio:

- 📦 **Descarga directa:** [**`NovelaAudioReader.apk`**](./NovelaAudioReader.apk?raw=true) *(13.3 MB, versión Release compilada y optimizada)*
- 🚀 **O desde la pestaña de [Releases](../../releases):** Donde encontrarás las notas de versión y el instalador listo.

### Pasos de instalación:
1. Descarga el archivo **`NovelaAudioReader.apk`** en tu dispositivo Android.
2. Abre el archivo y concédele permiso para instalar aplicaciones desde fuentes desconocidas si el sistema lo solicita.
3. Inicia **Novela Audio Reader**, pulsa en *"Detectar Carpeta de Novelas"* y selecciona el directorio raíz de tus libros (PDF, EPUB o TXT).
4. Elige tu novela favorita en el riel de portadas y ¡disfruta de la lectura auditiva!

---

## 🛠️ Tecnologías y Arquitectura

- **Lenguaje:** Java 17 puro para Android (Android SDK 24 a 35).
- **Audio Engine:** `android.speech.tts.TextToSpeech` + `MediaSessionCompat`.
- **Procesamiento de Documentos:** `PdfRenderer`, `java.util.zip.ZipFile`, `XmlPullParser`, streaming JSON con `android.util.JsonReader`.
- **UI & Diseño:** Material Components Android, `RecyclerView` optimizado con `PagerSnapHelper`, arquitectura Anti-Descuadre y Zero-GC en hilos secundarios.

---

## 📄 Licencia

Distribuido bajo la Licencia **MIT**. Consulta el archivo `LICENSE` para más información.
