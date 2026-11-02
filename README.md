# Plantilla NoExpertise · Albañil y pequeñas obras

Web para albañiles autónomos: llamada y WhatsApp a mano, trabajos con fotos, zonas y presupuesto corto.

- Sectores: albanil, albanileria, obras, alicatado, tejados, muros. Estilo: sólido. Plan mínimo: gratis.
- Secciones: hero, servicios, trabajos, garantias, proceso, zonas, cifras, opiniones, preguntas, presupuesto, contacto (+ `texto` genérico).
- Campos propios: `hero.items[]` (titulo, icono), `servicios.items[]` (titulo, texto, icono), `trabajos[]` (titulo, lugar, duracion, texto, imagen), `garantias.items[]`, `proceso.items[]`, `zonas.items[]` (titulo) e `imagen`, `cifras.items[]`, `opiniones.testimonios[]` (texto, autor, nota), `presupuesto` (items, nota, boton_formulario, cta).
- Pensada para un autónomo: primera persona, botón de WhatsApp en la cabecera, barra fija «Llamar / WhatsApp» en móvil, teléfono gigante y formulario de tres campos.
- Diseño a ancho completo: gris cemento + naranja obra; hero partido con foto a sangre y canto diagonal, pared de bloques, fotos de trabajos de borde a borde, escalera de pasos, cortes y franjas diagonales. Brief en `DISEÑO.md`.
- SEO de base incluido (`src/lib/seo.ts`): canónica, og:image, JSON-LD del negocio (`GeneralContractor`, con `areaServed` desde las zonas) y de las preguntas frecuentes, `robots.txt`, `sitemap.xml` y `llms.txt`; `noindex` si `seo.indexable: false`.
- Contenido editable en `site.yaml`; metadatos y guion del asistente en `template.yaml`; reglas para el agente en `CLAUDE.md`; fotos a generar en `fotos.json`.

```
npm ci
npm run dev      # desarrollo
npm run build    # web estática en dist/
```

Basada en [AstroWind](https://github.com/onwidget/astrowind) © onWidget, licencia MIT (`LICENSE-ASTROWIND.md`). Imágenes de relleno (`public/placeholders/`) dibujadas para esta plantilla, sin licencias de terceros.
