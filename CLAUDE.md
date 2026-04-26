# CLAUDE.md — Motobiker Xperiences (carpeta `txonlan`)

## Marca

**Motobiker Xperiences** — Agencia de viajes guiados en moto (rutas trail/aventura, fly&ride, alquiler, eventos motoclub).
Tagline oficial: _"Viajes en moto. Destinos que te transforman."_

## Stack y convenciones

- HTML + CSS + JS puro (sin frameworks).
- Mobile-first.
- 5 páginas: `index`, `viajes`, `experiencias`, `nosotros`, `contacto`.
- Capa visual premium compartida en `assets/premium.css` + `assets/premium.js` (mesh orbs, cursor dual, glass cards, page transitions, header 96px, scroll-video ready).
- Paleta:
  - `--color-bg: #050505` (negro principal)
  - `--color-bg-2: #0d0d0f`
  - `--color-accent: #FF5E14` (naranja vibrante del logo)
  - `--color-accent-2: #FFA94D` (naranja cálido secundario para gradients)
  - `--color-accent-hover: #E04A05`
- Tipografía: `Bebas Neue` (display monumental) + `Space Grotesk` (H2/H3) + `Inter` (body).
- SEO completo desde el día uno (meta + OG + JSON-LD + sitemap + robots).

## Hero scroll-video

El index reserva el "huevo" para el efecto scroll-video del kit (`<!-- SCROLL-VIDEO-SECTION -->` ya marcado, `.hero-wrapper { height: 175vh }`, `.hero { position: sticky }`). Mientras no haya vídeo real, se renderiza un placeholder con orbs naranja + foto poster. Archivos esperados cuando los entregue el cliente:
- `assets/hero.mp4` (autoplay loop mobile)
- `assets/hero-scrub.mp4` (desktop scroll-driven)
- `assets/hero-scrub-mobile.mp4` (mobile fallback)
- `assets/hero-poster.jpg`

## Producción

_(se rellena tras el primer deploy)_

- 🌐 _(URL Vercel pendiente)_
- 📦 _(URL GitHub pendiente)_
- Auto-deploy: cada `git push origin main` despliega solo.

## Para desplegar cambios

```bash
bash .claude/scripts/deploy.sh "mensaje commit"
# o desde Claude Code:
/deploy "mensaje commit"
```

Primer deploy: ejecutar antes `bash .claude/scripts/setup-deploy.sh` para crear repo en GitHub y enlazar Vercel.

## Pendiente del cliente

- [ ] Logo (PNG real) → `assets/logo.png` (el cliente lo pegó como imagen en chat — pedirle el archivo)
- [ ] Lista real de destinos/rutas con fotos, fechas y precios
- [ ] Vídeos hero (`assets/hero.mp4`, `hero-scrub.mp4`, `hero-scrub-mobile.mp4`, `hero-poster.jpg`)
- [ ] Datos reales de contacto (email, teléfono, WhatsApp, redes)
- [ ] Fotos reales de viajes anteriores → `assets/`
