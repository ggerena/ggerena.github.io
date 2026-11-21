# AGENTS.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static personal portfolio site for Gery Gerena (ggerena.cl), hosted on GitHub Pages. Redesigned as a terminal-style Markdown page — no frameworks, no build step, no package manager.

For the full redesign rationale and decisions, see [PLAN.md](./PLAN.md).

## Development

**No build commands.** Edit HTML/CSS/JS directly and push to `master` to deploy via GitHub Pages.

To preview locally, open `index.html` in a browser or use any static file server (e.g., `python -m http.server`).

## Architecture

- **index.html** — Single-page landing styled as Markdown rendered in a terminal (profile for recruiters: summary, skills, experience, education, languages, contact). Monospace font, no visible images, no external dependencies. Styles live in `styles.css` (shared with `404.html`). Includes JSON-LD (`WebSite`, `ProfilePage`, `Person` with `image` and `sameAs`) and a small inline script that switches visible text to Spanish via `data-i18n` keys.
- **index.md** — Pure Markdown version of the site content for AI/crawler consumption. Linked from the HTML via `<link rel="alternate" type="text/markdown">`.
- **llms.txt** — Profile summary for AI assistants (GEO). Keep its content consistent with `index.html` and `index.md`.
- **404.html** — Custom error page.
- **CNAME** — Custom domain `ggerena.cl`.
- **assets/images/avatar/gery-gerena.jpg** — Official profile photo (400×400, no EXIF/GPS), used in JSON-LD `image`, `llms.txt` and as a Markdown link line on the page. The rest of `assets/` are legacy files from the previous Jekyll theme.

## Key Details

- Asset URLs in HTML use root-relative paths (`/assets/...`), so local preview works with any static file server.
- No external CDN dependencies. Only JavaScript: the inline i18n script.
- Layout scales with the screen (`clamp` font size, column in `ch`), dark and light themes via `prefers-color-scheme`.

## Decisiones de Gery (21-11-2026)

- Mostrar poca información personal: sin teléfono, correo, segundo apellido ni colegio; contacto solo por LinkedIn. Instagram y Facebook se listan, pero no van en `sameAs` ni llevan `rel="me"`.
- Mantener la estética de documento Markdown: no mostrar imágenes en la página; la foto aparece como línea `![Profile photo](…)` con enlace.
- Cada imagen nueva se publica sin metadatos EXIF (la foto original `yo.jpg` exponía coordenadas GPS; se borró del sitio, pero sigue en el historial del repo).
- Antes de cambiar el diseño, cargar la skill `frontend-ui-engineering` y verificar accesibilidad (contraste 4,5:1, foco visible, lector de pantalla, sin desborde de 320 a 1440 px).
- Las páginas se regeneraron con un script temporal que no quedó en el repo; editar el HTML a mano manteniendo los números de línea correlativos y las claves `data-i18n` iguales en `es` y `en`.

## Publicación del sitio personal desde Codex

Gery confirmó el 2026-09-07 que las reglas personales de respaldo obligatorio mediante PR y autorización adicional de merge no aplican a este sitio personal; corresponden al trabajo con Gear3 o Remora. Un pedido de publicar aquí autoriza subir el cambio verificado directamente a master para GitHub Pages. Comprobar el diff y excluir datos privados antes de publicar. Esta excepción se limita a este repositorio.
