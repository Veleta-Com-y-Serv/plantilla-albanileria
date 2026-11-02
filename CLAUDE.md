# Plantilla «Albañil y pequeñas obras» (NoExpertise)

Web estática Astro 5 + Tailwind 4, derivada de AstroWind (MIT, ver `LICENSE-ASTROWIND.md`). Estilo: **sólido de
autónomo** (gris cemento + naranja obra + blanco; bandas a sangre de borde a borde con rayado de sección y cortes en
diagonal; títulos pesados en mayúsculas; etiquetas inclinadas como cinta de obra; esquinas vivas). Brief completo en
`DISEÑO.md`. Todo en castellano de España, frases cortas, sin jerga y **en primera persona** («Voy yo a verlo»): es la
web de un albañil autónomo, no de una empresa.

## Dónde está cada cosa
- **Textos, contacto, menú, SEO y secciones**: `site.yaml` (raíz). Es la única fuente de contenido. `src/data/site.ts` lo carga y lo tipa (lista propia `trabajos` y `testimonios` con `nota`, normalizadas con `lista<T>()`); no pongas textos fijos en los componentes.
- **Colores**: `site.yaml → colores` (primario = gris cemento, acento = naranja obra, fondo, texto). `src/layouts/Base.astro` los convierte en variables CSS (`--c-primario`…). Los derivados (`--c-cemento`, `--c-cemento-2`, `--c-carbon`, `--c-carbon-2`, `--c-acento-texto`, `--c-tenue`, `--c-borde`, `--c-sobre-acento`, `--c-sobre-primario`) se calculan con `color-mix` y `oklch(from …)` en `src/styles/global.css`.
- **Tipografías y aspecto general**: `src/styles/global.css` (`--fuente-titulos` Segoe UI Black / system-ui 900 en mayúsculas, `--fuente-texto` del sistema; bandas `.banda-carbon`, `.banda-cemento`, `.banda-acento`; texturas `.rayado`, `.rayado-claro`, `.franjas`; cortes `.corte-arriba`, `.corte-arriba-inv`; `.etiqueta`, `.icono-bloque`; botones `.btn-acento`, `.btn-oscuro`, `.btn`, `.btn-sec`, `.enlace-flecha`; cabecera `.cabecera--tabique`, pie `.pie--tabique`, barra móvil `.barra-movil`). Fuentes del sistema: no añadas fuentes externas.
- **Cabecera**: `src/components/Header.astro`. Blanca, fija, a todo el ancho; teléfono (pantallas grandes), botón de WhatsApp siempre visible y `boton_cabecera`.
- **Pie**: `src/components/Footer.astro`. Columnas de servicios y zonas (salen de esas secciones), contacto, cinta naranja y la barra fija inferior «Llamar / WhatsApp» en móvil (solo si hay teléfono o WhatsApp).
- **Imágenes**: en `public/`. Fotos en `public/fotos/` (las genera el coordinador desde `fotos.json`); respaldo en `public/placeholders/` (`hero.svg`, `obra.svg`, `persona.svg`). En `site.yaml` se referencian con ruta absoluta (`/fotos/trabajo-solado.jpg`). Si una foto falta, `Imagen.astro` muestra su SVG de respaldo. Fotos de trabajos sin caras.
- **Logo**: `site.yaml → logo` (ruta en `public/`); vacío = inicial en bloque naranja inclinado + nombre en texto.
- **Pie «Web creada con NoExpertise»**: `site.yaml → marca_pie` (se oculta solo con `false`).

## Secciones
Cada sección es un componente que solo se pinta si `site.yaml → secciones.<id>.activa` es `true`, en el orden de `site.yaml`. Todas son bandas a todo el ancho.
- `hero` → `secciones/hero.astro` · partido a sangre: cemento claro con título enorme, botones «Llamar» y «WhatsApp» (de `contacto`) y compromisos (`items`); foto a la derecha con canto diagonal.
- `servicios` → `secciones/servicios.astro` · pared de bloques con junta de mortero (3 / 2 / 1 columnas).
- `trabajos` → `secciones/trabajos.astro` · fotos grandes de borde a borde con la duración en cinta naranja.
- `garantias` → `secciones/garantias.astro` · banda naranja con franjas diagonales (sin items no se pinta).
- `proceso` → `secciones/proceso.astro` · escalera de bloques; el último peldaño en naranja.
- `zonas` → `secciones/zonas.astro` · muro de pueblos en mayúsculas + foto a sangre (`imagen` opcional).
- `cifras` → `secciones/cifras.astro` · cifras enormes en naranja sobre carbón (sin cifras no se pinta).
- `opiniones` → `secciones/opiniones.astro` · una opinión enorme y el resto apiladas (sin opiniones no se pinta).
- `preguntas` → `secciones/preguntas.astro` · acordeón `details/summary` (sin preguntas no se pinta).
- `presupuesto` → `secciones/presupuesto.astro` · 50/50 a sangre: pasos, nota y botón `cta` en naranja; formulario corto en carbón.
- `contacto` → `secciones/contacto.astro` · teléfono gigante, WhatsApp y datos; formulario solo si no hay `presupuesto` activa.
- `texto` → `secciones/texto.astro` · apartado genérico para secciones nuevas (`tipo: texto`); con imagen, fila 50/50 a sangre.

## Campos propios de esta plantilla (además del esquema común)
- `hero.items[]`: compromisos bajo los botones `{ titulo, icono }`. `hero.cta` y `hero.cta_secundario` son enlaces si hay teléfono o WhatsApp, y botones si no los hay.
- `servicios.items[]`: `{ titulo, texto, icono }`; `servicios.cta` opcional (enlace bajo el texto).
- `trabajos.trabajos[]`: `{ titulo, lugar, duracion, texto, imagen }`, todo cadenas (`duracion`: «3 días», «1 semana»). `trabajos.cta` opcional.
- `garantias.items[]`: `{ titulo, texto, icono }`.
- `proceso.items[]`: `{ titulo, texto }`; `proceso.cta` opcional.
- `zonas.items[]`: `{ titulo }` (pueblos y comarcas; el primero sale en naranja); `zonas.imagen` opcional.
- `cifras.items[]`: `{ titulo = la cifra, texto }`. Nunca inventes cifras.
- `opiniones.testimonios[]`: `{ texto, autor, nota }` (`nota` = trabajo y sitio). Nunca inventes opiniones.
- `presupuesto`: `items[]` `{ titulo, texto }` (pasos), `nota` («Sin compromiso»), `boton_formulario`, `cta` (WhatsApp o formulario).
- `contacto.cta.texto`: texto del botón del formulario cuando sale en contacto.
- Sin precios en esta plantilla. Si el cliente quiere enseñar uno, va en el texto del servicio y siempre como cadena.
- Iconos disponibles: ver `src/components/ui/Icono.astro` (ladrillos, superficie, nivel, casa, herramienta, casco, euro, calendario, documento, check…).

## Reglas para órdenes
1. **Activar o quitar una sección**: cambia `activa: true|false` en `site.yaml`. No borres componentes.
2. **Reordenar secciones**: mueve el bloque dentro de `secciones:` en `site.yaml`.
3. **Cambiar textos, teléfonos, horarios, fotos, trabajos o zonas**: solo en `site.yaml`. Si un texto contiene comas o «: » dentro de `{ … }`, ponlo entre comillas.
4. **Listas planas**: ningún elemento de lista puede llevar otra lista dentro. Máximo 24 elementos por lista. Precios siempre entre comillas.
5. **Página nueva**: crea `src/pages/<slug>.astro` usando `import Base from '../layouts/Base.astro'` y `<Base titulo="…" descripcion="…">…</Base>`; enlázala en `site.yaml → menu`. Ejemplo: `src/pages/aviso-legal.astro`.
6. **Sección nueva**: mejor con `tipo:` (`tipo: texto`, `tipo: servicios`, `tipo: trabajos`…) y un id propio en `site.yaml`. Si hace falta un diseño nuevo, crea `src/components/secciones/<id>.astro` copiando la estructura de una existente (`seccion(Astro.props.id)`, `Titular`, banda a todo el ancho con `.contenedor` dentro). `src/pages/index.astro` la recoge sola.
7. **No tocar** `src/layouts/Base.astro`, `src/pages/index.astro`, `tailwind.config.mjs` ni `src/styles/comun.css` salvo orden explícita de diseño. Los ids `hero` y `contacto` no se cambian. Tampoco `src/lib/seo.ts` ni `src/pages/robots.txt.ts`, `sitemap.xml.ts` y `llms.txt.ts`: son el SEO de base (canónica, og:image, `noindex` si `seo.indexable: false`, JSON-LD del negocio y de las preguntas, robots, sitemap y llms.txt), salen solos de `site.yaml` y el fichero es el mismo en todas las plantillas. `seo.url` y `seo.indexable` los pone la plataforma: no los cambies.
8. Mantén: `lang="es-ES"`, imágenes con `Imagen.astro` (carga diferida), sin JavaScript nuevo salvo necesidad real (solo hay uno mínimo: cierre del menú móvil), 16 px de margen lateral del texto en móvil (`.contenedor` o `px-4`), fotos y fondos a sangre, sin scroll horizontal en móvil, barra «Llamar / WhatsApp» en móvil. Imágenes de contenido con `alt` sacado del contenido (`altHero`, `altSeccion` de `src/lib/seo.ts`, o el `titulo` de la ficha); las decorativas, `alt=""`.
9. El formulario no tiene servidor: abre el correo (`mailto`) con el email de `site.yaml`. Tiene tres campos (nombre, teléfono y qué necesitas): no le añadas subida de fotos.

## Construir
```
npm ci && npm run build      # resultado en dist/
npx astro preview            # ver dist/ en http://localhost:4321
```
Antes de dar una orden por buena: `npm run build` sin errores.

## Páginas propias (fichas por elemento y páginas por zona)
- Listas con página propia (espejo de `fichas:` de template.yaml en `src/data/fichas.ts`): `secciones.servicios.items` → `/servicios/<slug>/` (servicio).
  **Solo los elementos con `detalle`** (texto largo, párrafos separados por una línea en blanco, ≤ 3000 caracteres, sin HTML) tienen página;
  los demás siguen como hasta ahora. Campos opcionales del elemento: `slug` (si falta, sale del nombre; no lo pongas sin motivo)
  e `imagenes` («/fotos/a.jpg; /fotos/b.jpg», galería de la ficha; la foto principal es `imagen` o, si no hay, la primera de `imagenes`).
  El resto de campos (precio, duración…) salen en la tabla de datos de la ficha.
- Zonas: cada elemento de `secciones.zonas.items` **con `texto`** (60-150 palabras: qué trabajos se hacen allí, pueblos cercanos)
  tiene su página en `/zonas/<slug>/`. En la sección: `titulo_pagina` («Reformas en {zona}») y `texto_pagina` (entrada, con {zona} y {negocio}).
- Una orden «añade una página para X» = escribir su `detalle` (o el `texto` de la zona) en site.yaml. Nunca crees a mano páginas en
  `src/pages/servicios/` ni en `src/pages/zonas/`: salen solas de `src/pages/[coleccion]/[slug].astro` y `src/pages/zonas/[slug].astro`.
- No tocar `src/lib/paginas.ts`, `src/lib/slug.ts` ni `src/lib/seo.ts` (comunes a todas las plantillas). Las páginas propias entran solas en
  `sitemap.xml` y `llms.txt`, con su JSON-LD (migas y servicio/producto con precio si lo hay; zonas con `areaServed`).
