# Albañil y pequeñas obras: brief de diseño

Plantilla `albanileria` creada el 02/11/2026 a partir de `construccion-promotora` con `php artisan plantillas:nueva`
(tanda 4, plantillas para autónomos) y rediseñada entera: de la base solo queda la estructura técnica (`index.astro`,
`Base.astro`, `seo.ts`, los tres endpoints, `Imagen.astro`, `Icono.astro`). Este fichero se queda en el repo: es lo
que lee quien (persona o agente) rediseñe la plantilla.

## Brief

- **Para quién**: albañiles autónomos y equipos muy pequeños de obra menor: tabiques, solados, alicatados, tejados,
  muros y arreglos (`sectores`: albanil, albanileria, obras, alicatado, tejados, muros). El cliente es un particular,
  una comunidad o un pequeño negocio de su pueblo o comarca que busca «albañil en <pueblo>» desde el móvil.
- **Qué tiene que conseguir la web**: que le llamen o le escriban por WhatsApp. El teléfono y WhatsApp mandan:
  barra fija inferior en móvil «Llamar / WhatsApp», botón de WhatsApp siempre visible en la cabecera, botones de
  llamada y WhatsApp en la portada, teléfono gigante en contacto y un presupuesto corto (nombre, teléfono y qué
  necesitas, solo texto).
- **Voz**: primera persona del singular, cercana («Soy Julián, albañil en Talavera desde 2008», «Voy yo a verlo»).
  Nada de «nuestra empresa».
- **Tono y estilo** (`estilo: solido`): obra pequeña, honrada y limpia. Referencia que sí: losmartesnohayluna.com
  (bandas a sangre alternas, títulos gigantes); los planos de albañilería (el rayado a 45° de la fábrica de ladrillo),
  la cinta de obra y una pared de bloques con su junta de mortero. Que no: la caja centrada estrecha con tarjetas
  blancas; el hero oscuro con velo, las mayúsculas condensadas y la banda de seguridad negra y naranja de
  `taller-mecanico`; el hormigón con berenjenos, la monoespaciada y el azul acero de `construccion-promotora`; el
  amarillo y el formulario en la portada de `reformas-oficios`.
- **Paleta de ejemplo**: primario `#585d62` (gris cemento), acento `#f26a1b` (naranja obra), fondo `#ffffff`, texto
  `#1f2123`. Derivados en `global.css`: `--c-cemento` (cemento claro: portada, zonas, preguntas), `--c-cemento-2`
  (junta de mortero, cantos), `--c-carbon` / `--c-carbon-2` (bandas oscuras, pie, botones oscuros),
  `--c-acento-texto` (naranja oscurecido legible sobre claro), `--c-sobre-acento` y `--c-sobre-primario` (blanco o
  negro según la luz del color, con `oklch(from …)`). El diseño aguanta que el cliente cambie los cuatro.
- **Tipografía** (del sistema, sin descargas): títulos pesados en MAYÚSCULAS (`Segoe UI Black` / `system-ui` 900,
  interletrado −0,012 em, interlineado 0,9-0,94: ancho, no condensado); etiquetas, menú, botones y datos en la misma
  negra en mayúsculas espaciadas; texto en `system-ui`.
- **Motivos**: etiqueta inclinada (antetítulo) como un trozo de cinta naranja (`skewX(-12deg)`); bloques de icono y
  marcas inclinados; rayado de sección a 45° en las bandas de cemento (`.rayado`, `.rayado-claro`); franjas
  diagonales anchas tono sobre tono en el naranja (`.franjas`); cortes en diagonal entre bandas (`.corte-arriba`,
  `.corte-arriba-inv`, la banda se monta sobre la anterior); fotos con el canto en diagonal; botones macizos con el
  canto inferior más oscuro. Esquinas vivas en todo.
- **Ritmo de bandas** (todas de borde a borde; contenido a 90 rem como mucho, 16 px de margen del texto en móvil):
  1. `hero` — partido a sangre (1,1 fr / 1 fr, 86 svh): cemento claro con rayado, etiqueta, título de 6 rem (2,6 en
     móvil), texto, botones «Llamar al …» y «WhatsApp» (sin ellos, `cta` y `cta_secundario`; con ellos, esos dos van
     como enlaces subrayados) y los compromisos (`items`) con marca naranja; foto a la derecha hasta el borde con el
     canto izquierdo en diagonal y una cinta naranja paralela. En móvil, foto arriba con corte diagonal abajo.
  2. `servicios` — blanco; titular partido; «pared» de bloques blancos con junta de mortero (el fondo asoma entre
     ellos) a 3 columnas (2 en tableta), número hueco y bloque de icono; al pasar, el bloque se pone naranja.
  3. `trabajos` — carbón con rayado claro y corte diagonal; fotos grandes de borde a borde sin márgenes (3 / 2 / 1,
     la última fila se estira), cinta naranja con la duración, lugar, título y texto sobre degradado.
  4. `garantias` — naranja con franjas diagonales y corte diagonal; titular + compromisos a 2 columnas con marca
     carbón inclinada y filete grueso.
  5. `proceso` — blanco; escalera de bloques que sube (columnas cada vez más altas sobre un suelo carbón; en móvil,
     bloques que se sangran hacia la derecha); el último peldaño en naranja.
  6. `zonas` — cemento claro con rayado; 50/50: muro de pueblos en mayúsculas separados por barras naranjas + foto a
     sangre hasta el borde con canto diagonal.
  7. `cifras` — carbón con corte diagonal; cifras enormes naranjas con barra inclinada (2 / 4 columnas).
  8. `opiniones` — blanco; la primera opinión enorme en mayúsculas con comillas naranjas gigantes, el resto apiladas
     entre filetes gruesos.
  9. `preguntas` — cemento claro; titular fijo y acordeón con preguntas en mayúsculas y bloque «+» inclinado.
  10. `presupuesto` — 50/50 a sangre: naranja con franjas (titular, pasos numerados, nota en sello, botón `cta` a
      WhatsApp) + carbón con el formulario corto.
  11. `contacto` — blanco; teléfono gigante entre filetes gruesos con el botón de WhatsApp y los datos a 4 columnas.
      Si no hay `presupuesto` activa, añade el formulario corto en una banda carbón.
  Pie carbón a 4 columnas (marca y redes, servicios, zonas, contacto) con cinta naranja de franjas diagonales y, en
  móvil, la barra fija «Llamar / WhatsApp».
- **Fotos** (`fotos.json`, 8): tabique de ladrillo a medio levantar con paleta y nivel (hero 16:9), seis trabajos
  (tabique enlucido, solado de cocina, alicatado de baño, retejado, muro de cerramiento, escalera de piedra) y tejados
  de un pueblo de la comarca (zonas). Sin texto legible, sin logotipos ni personas.
- **Qué no hacer**: tarjetas blancas con sombra en rejilla estrecha; esquinas redondeadas; fuentes condensadas;
  hero oscuro con velo; inventar precios, cifras o plazos en los componentes (todo sale del `site.yaml`; sin dato no
  se pinta: sin cifras no hay banda de cifras, sin garantías no hay banda naranja, sin opiniones no hay opiniones).

## Hecho

- [x] `site.yaml` de ejemplo: Obras Julián Robles (Talavera de la Reina), todo activo, al menos un elemento por lista,
  listas planas, sin precios.
- [x] Secciones: `hero`, `servicios`, `trabajos`, `garantias`, `proceso`, `zonas`, `cifras`, `opiniones`,
  `preguntas`, `presupuesto`, `contacto` y `texto` genérico. Fuera las de la base (`promociones`, `equipo`, `cta`).
- [x] `template.yaml` (sectores con nombre, secciones, plan mínimo gratis, orden 600, guion del asistente de 11
  pasos), `fotos.json`, `CLAUDE.md`, `README.md`, placeholders y favicon propios, `aviso-legal` y `404` con el diseño.
- [ ] Fotos generadas y previews definitivas (paso de fotos; las de ahora son provisionales con placeholders).
- [ ] Repo `Veleta-Com-y-Serv/plantilla-albanileria` con la etiqueta `v1.0.0`; en la plataforma,
  `config/plantillas.php` (`repos` y `refs`) y `php artisan plantillas:sync --demos`.
