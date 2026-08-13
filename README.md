# Aprendé a Construir con IA — CURSO COMPLETO

Landing estática con el plan de estudios del curso *Aprendé a Construir con IA (Construí y Vendé)*, de Mauri & Axel.

**10 partes · 84 lecciones · ~8 horas**, más el Kit de Producción del Fundador (12 recursos).

Producción: <https://aprende-a-construir-con-ia-programa.vercel.app/>

## Cómo correrlo

No hay build ni dependencias.

```bash
python3 -m http.server 8080
# o simplemente abrir index.html en el navegador
```

## Estructura

```
index.html   Toda la página: markup, CSS y JS inline
fonts/       Inter + JetBrains Mono (woff2)
images/      Logos de herramientas, portada, avatares y favicon
```

Un solo archivo HTML: no hay hoja de estilos externa ni bundler. El único JavaScript
es el del modal de waitlist, que postea a un Google Form vía iframe oculto (evita CORS).

El diseño es dark, con un color propio por parte (`--p1` … `--p10`) inyectado vía
`style="--c:var(--pN)"` en cada `<section class=part>`. Los carruseles de marcas y de
testimonios son CSS puro (`@keyframes scroll`), por eso los items están duplicados en el
markup: es lo que hace que el loop sea continuo.

## Invariantes al editar el plan de estudios

Cosas que se rompen en silencio si no se respetan:

- **Los conteos declarados.** El `<strong>N lecciones</strong>` de cada bloque tiene que
  coincidir con la cantidad real de `.out-card`, y el total del header con la suma de los
  bloques.
- **Las 3 vueltas del Loop del MVP.** 1.1 promete que corre en prototipo, automatización
  y beta; las vueltas cierran los bloques 3, 6 y 9. Mover una de esas lecciones de bloque
  rompe la promesa sin que nada falle. La promesa se enuncia por contenido y no por
  semanas ni por número de bloque, justamente para que aguante cualquier repactado.
- **Sin referencias cruzadas por número.** Los bullets no citan otras lecciones por número
  (`7.3`, `1.9`): se referencian por contenido, así renumerar no deja texto mintiendo.
- **Los íconos son promesas.** Cada herramienta con ícono en la cabecera de un bloque
  tiene que aparecer en alguna de sus lecciones. Al revés está permitido.

La imagen de portada (`images/axelymaurinueva.jpg`, 1200×638) se usa en el hero, el CTA y
el modal, y además es el `og:image`. Si se reemplaza, mantener ancho 1200 y peso bajo:
la versión original sin optimizar pesaba 7,5 MB y tardaba ~12 s en 4G.
