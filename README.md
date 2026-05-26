# Tareabox HyperFrames Registry

> ⚠️ **Catálogo experimental — leer antes de usar**
>
> Este NO es un repositorio oficial de HyperFrames ni de Heygen. Es mi espacio personal donde guardo los bloques que me funcionan a medida que aprendo y experimento con HyperFrames.
>
> **Importante:**
> - Algunos bloques están mejor codificados que otros — los voy puliendo con el tiempo.
> - Lo publico "tal como está", sin garantías de que funcione en tu entorno.
> - **No me hago responsable** si algo no anda como esperás, rompe tu proyecto, o causa pérdidas de cualquier tipo (ver [LICENSE](LICENSE)).
> - No tengo obligación de dar soporte, arreglar bugs, o aceptar PRs (aunque me encanta cuando lo hacen 💜).
> - Sugerencias y feedback son super bienvenidos; demandas y reclamos legales no.
>
> **"HyperFrames" es marca de Heygen Inc.** Soy **aficionada, no afiliada** 😄 — este catálogo es un proyecto independiente, NO está patrocinado ni respaldado por Heygen. Solo es compatible con su framework porque me re gusta lo que están haciendo.

Registry de bloques de video para [HyperFrames](https://hyperframes.heygen.com).
**+100 bloques de video** y creciendo — un catálogo vivo de bloques HyperFrames listos para instalar con `hyperframes add`.

Este repo es mi laboratorio público: a medida que experimento con HyperFrames, los bloques que realmente me gustan los subo acá.

<!-- AUTO-STATS-START -->
**127 bloques** (65 verticales 9:16 + 62 horizontales 16:9)

Por categoría:
- `conversationapp`: 24
- `data`: 4
- `layout`: 31
- `text`: 46
- `visual`: 22
<!-- AUTO-STATS-END -->

## Sobre el creador

Este catálogo es parte de **[Tareabox](https://tareabox.com)** — producto creado por **Natalie Digital** (Natalie Abadie).

### Tareabox (el producto, multiidioma)
- 🌐 [tareabox.com](https://tareabox.com) — ES / EN / FR / PT / DE / JA / NL
- 🎥 YouTube: [@tareabox](https://www.youtube.com/@tareabox)
- 📷 Instagram: [@tareabox](https://www.instagram.com/tareabox/)
- 📘 Facebook: [tareabox](https://www.facebook.com/tareabox)

### Natalie Digital (la creadora, contenido en español)
- 🌐 [nataliedigital.com](https://nataliedigital.com)
- 🎥 YouTube: [@Natalie.digital](https://www.youtube.com/@Natalie.digital)
- 📷 Instagram: [@natalie.digital](https://www.instagram.com/natalie.digital/)
- 🔗 LinkedIn: [nataliedigital](https://www.linkedin.com/in/nataliedigital/)

**Copyright legal:** Natalie Abadie (ver [LICENSE](LICENSE))

---

## Estructura

```
registry/
├─ registry.json          ← manifiesto: lista los 127 bloques
└─ blocks/
   └─ <nombre-del-bloque>/
      ├─ <nombre>.html         ← el efecto (formato bloque de registry)
      ├─ registry-item.json    ← metadata del bloque
      └─ tb-media/             ← assets que usa el bloque, si tiene
```

## Categorías de bloques

- **text** (46) — typewriter, warp, neon, kinetic, glitch, chapter, headline...
- **layout** (31) — YouTube setups, video hero/pip/hook, split-screen, tutoriales
- **conversationapp** (24) — iMessage, WhatsApp, Slack, Discord, Instagram DM, Twitter, notifs iOS/Android
- **visual** (22) — GIF stickers, callouts, indicadores (zoom, timestamp, progress, keyboard)
- **data** (4) — checklist, metric flip

La lista completa de los 127 está en `registry/registry.json`.

## Install rápido con Claude Code (sin código)

Si usás **Claude Code**, hay una skill que automatiza todo: instala HyperFrames + configura el registry + te guía a montar el video sin que toques nada.

```bash
git clone https://github.com/Tareabox/tareabox-video-edit-skill ~/.claude/skills/tareabox-video-edit
```

Después en Claude Code decile algo como *"haceme un video con tareabox"* y la skill toma el control.

**Skill repo:** [Tareabox/tareabox-video-edit-skill](https://github.com/Tareabox/tareabox-video-edit-skill) (MIT)

---

## Cómo instalar un bloque (manual)

Hay dos formas:

### Opción A — Custom registry (un solo comando)

Solo funciona con este repo público. En tu `hyperframes.json` apuntás al registry:

```json
{ "registry": "https://raw.githubusercontent.com/Tareabox/tareabox-catalog-free/main/registry" }
```

Después:

```bash
npx hyperframes add text-chapter-reveal-21-tb-v
```

Trae el `.html` + assets a tu proyecto.

### Opción B — Git clone manual

```bash
git clone https://github.com/Tareabox/tareabox-catalog-free
cp -R tareabox-catalog-free/registry/blocks/text-chapter-reveal-21-tb-v \
   my-project/compositions/
```

### Montar el bloque en tu composición

```html
<div class="clip"
     data-composition-id="text-chapter-reveal-21-tb-v"
     data-composition-src="compositions/text-chapter-reveal-21-tb-v.html"
     data-start="0" data-duration="3" data-track-index="1"
     data-width="1080" data-height="1920"></div>
```

### Personalizar

Editá el bloque `🎨 CUSTOMIZE HERE` dentro del `.html` instalado (es tu copia).


## Preview de todos los bloques

Ver los 127 bloques renderizados en grilla: **https://tareabox.com/hf-catalog-free/**

Para previewar local desde el repo clonado:

```bash
git clone https://github.com/Tareabox/tareabox-catalog-free
# El catálogo trae los MP4 + PNG de cada bloque listos para servir
# (Si no, levantá tu propio HyperFrames preview con `npx hyperframes preview`)
```

## Formato de los bloques

Cada bloque sigue el formato oficial de bloque de registry de HyperFrames:
`<style>` dentro del `<div>` de la composición y CSS scopeado con
`[data-composition-id="..."]`. Así renderiza correctamente al montarse como
sub-composición.

---

## Asset Folder Convention (English)

Each block ships its bundled assets in one of two folders. The folder name tells
you whether to keep the asset or replace it.

### `tb-media/` — part of the effect, keep as-is (or swap if you prefer)

These assets are intentional design elements of the block. Use them as shipped,
or swap them for your own equivalents if you want a different look.

| File | Where it appears | Optional replacement |
|---|---|---|
| `tb-tareabox-logo.png` | conversation app blocks (avatar slot) | Your own logo or brand mark |
| `tb-natalie-digital-avatar.png` | tweet / DM blocks (profile picture slot) | Your own profile picture |
| `tb-react-clap.mp4`, `tb-react-mind-blown.mp4`, `tb-react-omg.mp4` (and `-2`, `-3` variants) | GIF burst / sticker / meme blocks | Any reaction MP4 that fits your content (HyperFrames seeks MP4 deterministically, GIFs don't animate in render) |
| `tb-luisa-audio.m4a` | `text-popup-words` block | Your own audio clip |

Backgrounds, patterns, particle loops, sound effects, and other design-integral
files added in the future will also live here. **You can ship a final video with
these assets in place.**

### External demo videos (Pexels CDN)

For blocks that need video footage, the bundled HTML streams the demo from the [Pexels CDN](https://www.pexels.com/license/) via HTTPS — **no video file is downloaded into your project**.

All `<video src="https://videos.pexels.com/...">` references in the blocks point to original Pexels-hosted MP4s. Pexels license allows commercial use; attribution is **not required** but appreciated. To see the author of any specific demo, open the `pexels.com/video/{id}/` URL embedded in the block's HTML.

The block's CSS uses `object-fit: cover`, so the same source adapts cleanly to both horizontal and vertical blocks (center-cropped, no letterboxing). To swap any demo for your own footage, see [How to swap a video asset](#how-to-swap-a-video-asset) below.

## How to swap a video asset

Each block's HTML has an `ASSET` comment above its `<video>` tag explaining how
to replace the demo with your own footage. Two ways:

### Option 1 — Use an external URL (HTTPS)

Change the `src` to any HTTPS URL hosting an `.mp4` or `.webm`. The host must
allow CORS (`Access-Control-Allow-Origin: *`), which is standard on Pexels,
Cloudflare R2, S3, Vimeo CDN, etc.

```html
<video src="https://yourdomain.com/your-video.mp4"
       crossorigin="anonymous" data-tb-asset="vertical"
       data-start="0" data-duration="5.5" data-track-index="0"
       muted playsinline></video>
```

### Option 2 — Use a local file in your project

Drop your file into your project's `assets/` folder and reference it with a
relative path. The block HTML lives inside `compositions/`, so `..` walks one
folder up to the project root:

```
your-project/
├─ compositions/
│   └─ text-freeze-pop-24-tb-v.html   ← the block HTML
└─ assets/
    └─ tb-media/
        └─ your-video.mp4              ← your file
```

```html
<video src="../assets/tb-media/your-video.mp4"
       data-tb-asset="vertical"
       data-start="0" data-duration="5.5" data-track-index="0"
       muted playsinline></video>
```

The `data-tb-asset` attribute is just a hint that tells you which orientation
the block was designed for (`vertical` or `horizontal`). The actual dimensions
of your source video can vary — `object-fit: cover` will center-crop it to fit
the block's frame.

## Dynamic text fitting

Blocks with editable text (variables like `text`, `word`, `headline`) use the
official HyperFrames API to fit any user-provided text to the available width
without overflow. This is the HyperFrames-recommended pattern for variable copy
length.

**Source:** [`hyperframes/dist/skills/hyperframes/SKILL.md`](https://github.com/heygen-com/hyperframes) — Typography and Assets section:

> *"For dynamic text overflow, use `window.__hyperframes.fitTextFontSize(text, { maxWidth, fontFamily, fontWeight })`"*

And again in the Visual Inspect section:

> *"Fix [text spilling out] by ... using `window.__hyperframes.fitTextFontSize(...)` for dynamic copy."*

**Pattern applied in our blocks:**

```js
const FRAME_W = 1080, INNER_PCT = 0.88;          // 6% padding each side
const MAX_W = FRAME_W * INNER_PCT;
if (window.__hyperframes && window.__hyperframes.fitTextFontSize) {
  const fitted = window.__hyperframes.fitTextFontSize(el.textContent, {
    maxWidth: MAX_W,
    fontFamily: "Geist",
    fontWeight: 900,
  });
  el.style.fontSize = fitted + "px";
}
// else: the CSS `clamp(...)` defined in the stylesheet is the fallback
```

This guarantees that even very long words (e.g. `"TRANSFORMATION"`,
`"DEVELOPMENT"`) shrink to fit, while short words keep their full display size.
Tested on the `text-morph-06-*` blocks; the same pattern applies to any other
block whose font size depends on user-provided text length.

---

(c) 2026 **Natalie Digital** (canal/marca) · Copyright legal **Natalie Abadie** — ver [LICENSE](LICENSE) · [tareabox.com](https://tareabox.com)
