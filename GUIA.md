# Guía de construcción — Motobiker Xperiences

Bitácora cronológica de cómo se construyó esta web. Cada entrada documenta una acción concreta, su motivación y los archivos afectados.

## Stack y decisiones generales

- **HTML + CSS + JS puro** — sin frameworks, igual que Drizzt Design y Gausark. Máximo control, velocidad de carga y deploy trivial.
- **5 páginas:** index, viajes, experiencias, nosotros, contacto.
- **Paleta:** negro `#050505` + naranja `#FF5E14` (extraída del logo oficial Motobiker Xperiences).
- **Tipografías:** Bebas Neue (display monumental) + Space Grotesk (H2/H3) + Inter (body).
- **Premium baseline:** mesh orbs naranja, cursor dual con lag, glass cards 3D, page transitions, header 96px, scroll progress, word-reveal, count-up, footer monumental.
- **Scroll-video:** hero con `.scroll-video-wrapper { height: 175vh }` + `.hero { position: sticky }` — vídeo ligado al scroll, listo para activar cuando el cliente entregue los archivos.
- **Deploy previsto:** GitHub → Vercel auto-deploy en cada push a main.
- **Destinos actuales:** Marruecos, Colombia, Tailandia, Madagascar.

## 1. Decisiones iniciales

### 2026-04-26 — Crear proyecto Txonlan

**Qué:** Inicializada la carpeta `a:\txonlan\` con el kit de skills self-contained (deploy-github-vercel, guia-progresiva, scroll-video, seo-optimizer), `.gitignore`, repo git en branch main, y `assets/` vacía.
**Por qué:** Empezar nueva web siguiendo el patrón premium ya validado en Drizzt Design y Gausark.
**Cómo:** `cp` del `.claude/` de drizzt-design + `git init -b main`.
**Archivos:** .claude/, .gitignore, assets/, GUIA.md, CLAUDE.md

### 2026-04-26 — Definir brand: Motobiker Xperiences

**Qué:** La carpeta `txonlan` corresponde al proyecto público "Motobiker Xperiences" — agencia de viajes guiados en moto. Tagline oficial del logo: "Viajes en moto. Destinos que te transforman."
**Por qué:** El cliente aportó el logo (naranja/negro, moto trail, brújula) e indicó los destinos reales: Marruecos, Colombia, Tailandia, Madagascar. Paleta y tipografía derivadas del logo.
**Cómo:** Decisión del cliente en briefing inicial. Logo pegado en chat; pendiente el PNG real.
**Archivos:** CLAUDE.md (actualizado con brand, paleta, stack)

### 2026-04-26 — Seleccionar referencias de inspiración

**Qué:** Dos webs de referencia aprobadas por el cliente: motorbeachviajes.com (premium, fotografia cinematográfica, Marruecos/Atlas) y rakatanga-tour.com (tours aventura, grupos pequeños, mucho visual).
**Por qué:** Definen el tono aspiracional: viajes que venden emoción y confianza, no catálogos de precios.
**Cómo:** Briefing del cliente.
**Archivos:** — (decisión sin archivos tocados)

## 2. Setup del proyecto

## 3. Estructura y arquitectura

### 2026-04-26 — Definir estructura de 5 páginas

**Qué:** Arquitectura de 5 páginas: `index.html` (hero + preview destinos), `viajes.html` (calendario 2026), `experiencias.html` (4 modalidades), `nosotros.html` (historia + valores + destinos), `contacto.html` (formulario + FAQ).
**Por qué:** Kit crear-web-premium standard de 5 páginas. Cada página tiene propósito de conversión claro: index = enganche, viajes = calendario de oferta, experiencias = explicar el "cómo", nosotros = confianza, contacto = conversión.
**Cómo:** Derivado del patrón Drizzt Design + necesidades del sector moto-turismo.
**Archivos:** index.html, viajes.html, experiencias.html, nosotros.html, contacto.html

## 4. Diseño y UI

### 2026-04-26 — Adaptar premium baseline a paleta naranja/negro

**Qué:** Creados `assets/premium.css` y `assets/premium.js` adaptando el baseline de Drizzt Design (azul → naranja). Cambios: accent `#FF5E14`, accent-2 `#FFA94D`, orbs naranja, page transitions naranja, CTAs naranja, glow naranja.
**Por qué:** El baseline Drizzt usa azul `#60a5fa`. El logo de Motobiker Xperiences es negro/naranja. Cambio de paleta sistemático para que toda la capa premium sea coherente con la marca.
**Cómo:** Reescritura del CSS y JS de Drizzt Design con sustitución de todos los valores de color.
**Archivos:** assets/premium.css, assets/premium.js

### 2026-04-26 — Construir index.html con hero scroll-video

**Qué:** Página principal completa: hero con scroll-video placeholder, marquee de destinos, intro con stats, 4 modalidades, 4 pasos del proceso, 3 tarjetas de destinos preview, 3 testimonios, CTA final, footer monumental.
**Por qué:** Estructura de máximo impacto en el primer scroll: el hero vende el viaje, el marquee establece los destinos, las stats dan confianza, los pasos explican el proceso.
**Cómo:** HTML + CSS inline base + `<link rel="stylesheet" href="assets/premium.css">` + JS premium.
**Archivos:** index.html

### 2026-04-26 — Construir viajes.html con los 4 destinos reales

**Qué:** Página de calendario con 4 viajes reales (Marruecos Atlas Total, Colombia Andes & Café, Tailandia Norte Salvaje, Madagascar Pistas del Sur). Cada card incluye fechas, precio, descripción, stats (días, km, perfil, nivel) y filtros visuales por categoría.
**Por qué:** El cliente especificó los 4 destinos: Madagascar, Colombia, Tailandia, Marruecos. Las cards reemplazan los destinos ficticios del primer borrador (Pirineos, Albania, Dolomitas, etc.).
**Cómo:** HTML con viaje-card structure + filtros por JS.
**Archivos:** viajes.html

### 2026-04-26 — Construir experiencias.html (4 modalidades)

**Qué:** Página que explica las 4 formas de viajar: rutas guiadas, fly&ride, alquiler, eventos motoclub. Layout alternado izq/der con visual de color. Sección "lo que incluye" con 9 cards de servicios garantizados.
**Por qué:** La "capa de confianza" del site: el cliente necesita entender exactamente qué compra antes de reservar.
**Cómo:** HTML con `.servicio-bloque` alternado + `.incluye-grid` de 3 columnas.
**Archivos:** experiencias.html

### 2026-04-26 — Construir nosotros.html

**Qué:** Página de confianza: manifiesto (blockquote grande), 4 stats count-up, 6 valores con glass cards, tabla de destinos conocidos.
**Por qué:** El cliente potencial necesita confiar antes de dar el número de tarjeta. Esta página es la que convierte al curioso en cliente.
**Cómo:** HTML con secciones manifiesto + stats + valores + destinos.
**Archivos:** nosotros.html

### 2026-04-26 — Construir contacto.html

**Qué:** Formulario de reserva con 6 campos (nombre, email, teléfono, destino, formato, motos, mensaje), 4 tarjetas de contacto (email, teléfono, WhatsApp, Instagram), FAQ desplegable con 6 preguntas frecuentes.
**Por qué:** Página de conversión final. El FAQ reduce objeciones antes de que el cliente tenga que preguntar.
**Cómo:** HTML con `.contacto-grid` (info + form), `<details>` para FAQ, JS demo de envío.
**Archivos:** contacto.html

## 5. Contenido y datos

### 2026-04-26 — Destinos reales: Madagascar, Colombia, Tailandia, Marruecos

**Qué:** Sustituidos los destinos ficticios (Pirineos, Albania, Dolomitas, Sahara) por los 4 destinos reales del catálogo actual del cliente.
**Por qué:** El cliente los especificó en la segunda iteración: "los viajes son en Madagascar, Colombia, Tailandia, Marruecos".
**Cómo:** Edición de `index.html` (marquee + preview 3 tarjetas) y reescritura completa de `viajes.html` (4 cards con datos reales de cada destino).
**Archivos:** index.html, viajes.html

## 6. Integraciones externas

## 7. Funcionalidades

### 2026-04-26 — Integrar efecto scroll-video en el hero

**Qué:** El hero del index usa `.scroll-video-wrapper { height: 175vh }` con `.hero { position: sticky }`. El vídeo avanza/retrocede siguiendo el scroll via estrategia híbrida `playbackRate` dinámico + seek throttleado. En móvil: autoplay loop simple.
**Por qué:** El cliente pidió explícitamente "dejar un huevo para hacer el efecto scrolling". Se usó la skill `scroll-video` del proyecto que define la implementación correcta (playbackRate + seek > rAF puro, evita trompicones).
**Cómo:** Implementación según skill scroll-video. Wrapper renombrado a `.scroll-video-wrapper`. JS híbrido reemplaza el rAF lerp original.
**Archivos:** index.html, assets/hero-scrub.mp4, assets/hero-scrub-mobile.mp4, assets/hero.mp4, assets/hero-poster.jpg

### 2026-04-26 — Copiar vídeos hero desde Descargas y generar poster

**Qué:** Copiados los 3 MP4 generados por el cliente a `assets/` con los nombres estándar. Poster extraído con `ffmpeg` del primer frame del scrub desktop.
**Por qué:** El cliente indicó "tienes en descargas los tres últimos elementos para hacer el efecto del scrolling". Los 3 archivos son los vídeos de scrub desktop, móvil y referencia.
**Cómo:**
- `cp hf_20260426_193126_*.mp4 assets/hero-scrub.mp4` (desktop, 9.1MB)
- `cp hf_20260426_165735_*.mp4 assets/hero-scrub-mobile.mp4` (móvil, 7.1MB)
- `cp hf_20260424_193010_*.mp4 assets/hero.mp4` (referencia, 18MB)
- `ffmpeg -ss 2 -i assets/hero-scrub.mp4 -frames:v 1 -q:v 2 assets/hero-poster.jpg`
**Archivos:** assets/hero-scrub.mp4, assets/hero-scrub-mobile.mp4, assets/hero.mp4, assets/hero-poster.jpg

### 2026-04-26 — Filtros de categoría en viajes.html

**Qué:** Pills de filtro (Todos / Trail / Asfalto / Fly & Ride / Aventura) con toggle de clase `active` por JS. Actualmente solo visuales (toggle de estado), sin filtrado real de cards — se activará cuando haya más destinos o el cliente quiera filtrado real.
**Por qué:** El calendario tiene 4 destinos de categorías mixtas. Los filtros preparan la UX para cuando crezca el catálogo.
**Cómo:** JS vanilla con `querySelectorAll('.filter')` + toggle de clase.
**Archivos:** viajes.html

## 8. Performance y SEO

### 2026-04-26 — SEO completo en las 5 páginas

**Qué:** Cada página incluye: `<title>` único, `<meta name="description">`, canonical, Open Graph completo (og:type, og:title, og:description, og:url, og:image 1200×630), Twitter Card, JSON-LD (TravelAgency, ItemList, Service según página), robots, author.
**Por qué:** SEO desde el día uno — patrón estándar del kit premium.
**Cómo:** Meta tags inline en cada HTML + JSON-LD específico por tipo de página.
**Archivos:** index.html, viajes.html, experiencias.html, nosotros.html, contacto.html

### 2026-04-26 — Crear sitemap.xml y robots.txt

**Qué:** `sitemap.xml` con las 5 URLs, fechas y prioridades. `robots.txt` apuntando al sitemap.
**Por qué:** Requerimiento SEO mínimo para indexación correcta en Google Search Console.
**Cómo:** Creación manual de ambos archivos.
**Archivos:** sitemap.xml, robots.txt

### 2026-04-26 — Poster del hero extraído con FFmpeg

**Qué:** `hero-poster.jpg` generado desde frame 2s del vídeo scrub. Se usa como `poster` del `<video>` para evitar flash de pantalla negra mientras carga el vídeo.
**Por qué:** Sin poster, el hero aparece negro hasta que el browser puede decodificar el primer frame del MP4.
**Cómo:** `ffmpeg -ss 00:00:02 -i assets/hero-scrub.mp4 -frames:v 1 -q:v 2 assets/hero-poster.jpg`
**Archivos:** assets/hero-poster.jpg

## 9. Deploy e infraestructura

_(pendiente — primer deploy cuando el cliente confirme el dominio y los datos reales)_

### 2026-04-26 — Re-encodar vídeos hero con keyframe por frame (fluidez)

**Qué:** Re-encodados `hero-scrub.mp4` y `hero-scrub-mobile.mp4` con `x264opts keyint=1:min-keyint=1:no-scenecut`. Cada frame del vídeo es ahora un keyframe.
**Por qué:** El cliente reportó que el scroll-video iba a trompicones. La causa real es el encoding por defecto: el navegador, cuando el scroll va hacia atrás o salta, tiene que decodificar desde el keyframe anterior hasta el frame objetivo. Con keyframes solo cada 30 frames, eso son hasta 30 frames de decodificación por seek = stuttering. Con keyframe-por-frame el scrub es instantáneo en cualquier dirección.
**Cómo:**
- Desktop: `ffmpeg -i hero-scrub.mp4 -c:v libx264 -x264opts "keyint=1:min-keyint=1:no-scenecut" -crf 23 -preset slow -tune film -an -movflags +faststart -y hero-scrub-fluid.mp4`
- Mobile: igual + `-vf "scale=1280:-2"` y `-crf 24`
- Sustituidos los originales con los `-fluid` y eliminada la versión vieja.
**Archivos:** assets/hero-scrub.mp4, assets/hero-scrub-mobile.mp4

### 2026-04-26 — Añadir fotos de marca (hero-still + world-map)

**Qué:** Dos fotos integradas: `hero-still.jpg` (moto en carretera al amanecer entre montañas, perfecta para Marruecos/Atlas) y `world-map.jpg` (mapa mundi con rutas naranjas). Optimizadas a JPEG real (~250KB cada una desde PNGs de 2MB).
**Por qué:** El cliente pidió "añade fotos". Estas dos imágenes encajan con la voz de marca (cinematográficas, aspiracionales, paleta naranja-negro).
**Cómo:**
- Copiadas de Descargas con nombres canónicos.
- `ffmpeg -q:v 3` para convertir PNG→JPEG y reducir tamaño.
- `hero-still.jpg` reemplaza el `hero-poster.jpg` (era un frame extraído del scrub, menos potente que la foto cinematográfica).
- Usadas como `background-image` en: `.proyecto-card-bg` Marruecos del index, `.viaje-image-bg` Marruecos de viajes.html, `.page-hero-bg` (overlay sutil con blur) y `.destinos-map img` de nosotros.html.
**Archivos:** assets/hero-still.jpg, assets/world-map.jpg, assets/hero-poster.jpg, index.html, viajes.html, nosotros.html

### 2026-04-26 — Sustituir scroll-video JS por rAF lerp continuo

**Qué:** Reescrito el JS del scroll-video. Antes: estrategia híbrida con `playbackRate` forward + seek backward + snap-on-stop. Ahora: loop `requestAnimationFrame` que interpola continuamente `currentTime` hacia el target del scroll en cada frame.
**Por qué:** El cliente reportó saltos bruscos de frame a frame durante el scroll. La causa eran tres jolts del approach híbrido: (1) catch-up seek si `diff > 2s`, (2) snap final tras 150ms sin scroll, (3) seeks instantáneos en backward. Con keyframe-per-frame ya en sitio, asignar `currentTime` cuesta casi cero — eso desbloquea el lerp continuo, que sigue al scroll suavemente sin saltos.
**Cómo:**
- Eliminado `playbackRate`, `setTimeout`, catch-up seeks.
- Loop rAF con `current += diff * LERP` donde LERP=0.18 base.
- Lerp adaptativo: si `|diff| > 0.8s`, sube hasta 0.5 para alcanzar target en scroll rápido sin lags.
- Threshold de parada en `|diff| < 0.003s` para liberar el rAF cuando ya está pegado al target.
**Archivos:** index.html (script inline)

### 2026-04-26 — Logo limpio + favicon + og-image

**Qué:** Logo PNG del cliente colocado en `assets/logo.png`. Quitado el fondo blanco con flood-fill (Pillow). Generados `favicon.png` (192×192) y `og-image.jpg` (1200×630, foto cinematográfica + logo).
**Por qué:** El cliente entregó el logo como JPEG con fondo blanco — no servía sobre la web negra. El flood-fill desde las 4 esquinas elimina el fondo sin tocar las partes blancas interiores (letras del wordmark) porque están aisladas dentro de formas oscuras.
**Cómo:**
- `mv logo.png.jpeg logo.png` (Windows guardó con doble extensión)
- Pillow: `ImageDraw.floodfill(img, (corner), (255,255,255,0), thresh=20)` desde 4 esquinas → `getbbox()` para auto-trim
- Favicon: resize lanczos a 192×192 con padding centrado transparente
- og-image: hero-still recortado a 1200×630, `Brightness(0.55)` para oscurecer, logo 380px de alto centrado encima
- Reemplazado `Motobiker<span>X</span>periences` (texto) por `<img src="assets/logo.png">` en `.brand` (header) y `.footer-brand-logo` (footer) de las 5 páginas
- Estilos en `premium.css`: `.brand-logo { height: 64px }` (50px móvil), `.footer-brand-logo img { height: 110px }` (90px móvil)
**Archivos:** assets/logo.png, assets/favicon.png, assets/og-image.jpg, assets/premium.css, index.html, viajes.html, experiencias.html, nosotros.html, contacto.html

## 10. Mantenimiento y notas

### Pendiente del cliente (2026-04-26)

- Logo PNG real → `assets/logo.png` (el cliente pegó la imagen en el chat pero hay que pedirle el archivo)
- Datos reales de contacto (email, teléfono, WhatsApp, redes)
- Fotos reales de los 4 destinos → `assets/` (actualmente los viaje-card usan gradientes de color)
- Confirmar URL final del dominio para actualizar los canonicals y el sitemap
- Conectar el formulario de contacto a un backend real (Formspree, Google Apps Script, o similar)
- Si el vídeo va a trompicones en el scrub: re-encodar con keyframes en cada frame: `ffmpeg -i hero-scrub.mp4 -c:v libx264 -x264opts "keyint=1:min-keyint=1" -crf 30 -preset ultrafast hero-scrub-fixed.mp4`
