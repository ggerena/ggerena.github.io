# Plan: Rediseñar ggerena.cl como "Markdown-style"

## Context
Gery quiere que su sitio personal se vea como un documento Markdown renderizado (estilo GitHub README), manteniendo los mismos links sociales. Bonus: que AIs/crawlers puedan consumir Markdown real.

## Approach

### 1. Reescribir `index.html` con estilo Markdown
- HTML ultra-semántico y limpio: `<h1>`, `<p>`, `<ul>` con links
- CSS inline mínimo estilo **raw/monospace** (como código en terminal):
  - Font: `"Courier New", Courier, monospace` o similar
  - Max-width ~800px centrado, padding generoso
  - Links en azul simple, listas con bullets/guiones
  - Fondo claro, texto oscuro, minimalista
- Eliminar referencias a Bootstrap, Font Awesome, WOW.js, Animate.css del HTML
- **No borrar** los archivos de assets viejos (quedan en el repo por ahora)
- Mantener meta tags de SEO/OG actualizados
- **Mantener avatar** como imagen estilo Markdown: `![Gery Gerena](url)`

### 2. Estructura visual del contenido
```
# Gery Gerena

Software Developer

## Links

- [Twitter](https://twitter.com/ggerena)
- [Instagram](https://www.instagram.com/gery.gerena)
- [LinkedIn](https://www.linkedin.com/in/ggerena/)
- [Facebook](https://facebook.com/ggerena/)
- [GitHub](https://github.com/ggerena)
- [Medium](https://medium.com/@ggerena)

---
Gery Gerena © 2025
```

### 3. AI/Markdown consumption
- Crear `index.md` con el contenido real en Markdown puro
- En el `<head>` del HTML, agregar: `<link rel="alternate" type="text/markdown" href="/index.md">`
- Los crawlers inteligentes y AIs que respeten `rel=alternate` podrán descubrir y consumir el `.md`
- El HTML será tan semántico que incluso sin el `.md`, un AI parseando el HTML obtendrá contenido limpio

### 4. Archivos a modificar/crear
- **Modificar**: `index.html` — reescritura completa pero simple
- **Crear**: `index.md` — versión Markdown pura del contenido
- **Sin cambios**: `CNAME`, `404.html`, assets viejos (se dejan en el repo)

## Verification
- Abrir `index.html` en browser → debe verse como un README de GitHub
- `curl` o fetch de `index.md` → debe devolver Markdown limpio
- Verificar que todos los links sociales funcionen
