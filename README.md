# Aprendé a Construir con IA — CURSO COMPLETO

Landing estática con el plan de estudios del curso *Aprendé a Construir con IA (Construí y Vendé)*, de Mauri & Axel.

**11 partes · 81 lecciones · ~7,5 horas**, más el Kit de Producción del Fundador (12 recursos).

## Cómo correrlo

No hay build ni dependencias. Es HTML + CSS plano, sin JavaScript.

```bash
npx http-server -p 8080 .
# o simplemente abrir index.html en el navegador
```

## Estructura

```
index.html      Toda la página: markup + CSS inline (fuentes, tema y layout)
css/style.css   Variable auxiliar de imagen
fonts/          Inter + JetBrains Mono (woff2)
images/         Logos de herramientas, foto de portada y avatares
```

El diseño es dark, con un color propio por parte (`--p1` … `--p11`) inyectado vía
`style="--c:var(--pN)"` en cada `<section class=part>`. Los carruseles de marcas y de
testimonios son CSS puro (`@keyframes scroll`), por eso los items están duplicados en el
markup: es lo que hace que el loop sea continuo.

## Pendientes

- **Link de Skool.** Los dos CTA (`.unlock-cta` y `.skool-cta`) están marcados con
  `data-cta="skool-pendiente"` y sin `href`. Buscá los comentarios `TODO` en `index.html`
  y reponé `href="URL" target=_blank rel=noopener` cuando esté la URL definitiva.
- **Dominio.** Falta el `<link rel=canonical>` con el dominio real de producción. Las
  etiquetas `og:image` / `twitter:image` usan ruta relativa; conviene pasarlas a URL
  absoluta una vez fijado el dominio.
