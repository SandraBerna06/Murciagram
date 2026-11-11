# MurciaGram · El Pinterest de la Región de Murcia

Galería de inspiración visual (HTML5 + CSS3, sin JavaScript) para promocionar el patrimonio histórico, natural, cultural y gastronómico de los municipios de la Región de Murcia. Práctica obligatoria de CSS3.

🔗 **Demo:** `https://TU-USUARIO.github.io/murciagram/` _(sustituye `TU-USUARIO` por tu usuario de GitHub antes de publicar)._

![Vista del proyecto](assets/img/lorca-desktop.jpg)

## Qué incluye

- **Diseño editorial y responsive** con paleta mediterránea (terracota, verde profundo y dorado), cabecera sticky con efecto glass, hero con imagen destacada y tarjetas tipo Pinterest.
- **HTML5 semántico:** `header`, `nav`, `aside`, `main`, `footer`, `section`, `article`, `figure`, `figcaption` y `menu`. No hay `div` genéricos.
- **SEO:** viewport, `robots` index/follow, descripción, canonical, Open Graph, Twitter Cards y datos estructurados JSON-LD.
- **Mobile-first puro:** el CSS base define el móvil (< 600 px) en una columna Flexbox.
  - Tableta `(width >= 600px) and (width <= 800px)`: Flexbox multidireccional de 2 columnas.
  - Escritorio `(width > 800px)`: CSS Grid (cabecera, aside fijo de 260 px, galería Flexbox fluida y pie).
  - Solo se usa la sintaxis de rangos; no hay `min-width` ni `max-width` en las media queries.
- **`@media print`:** oculta el menú lateral y los botones de interacción, fuerza fondo blanco y optimiza la tipografía para papel.
- **Tarjetas:** borde sutil, esquinas redondeadas, sombras difuminadas y transiciones con curvas `cubic-bezier` personalizadas.
- **Efecto permanente:** el botón "Guardar en mi ruta" es un `label` de un checkbox; al marcarlo, `:checked` + `:has()` cambian por completo el color de la tarjeta y muestran una insignia.
- **Overlay estilo Pinterest:** al hacer hover o foco, la imagen se oscurece, aparece la descripción, el icono de "Me gusta" y el enlace a la web oficial del municipio.
- **Imágenes adaptables:** cada tarjeta usa `<picture>` con una versión móvil de 400 × 300 px y una de escritorio de 1000 × 750 px. Las imágenes fuera del primer viewport usan `loading="lazy"`; el hero usa `fetchpriority="high"`.
- **Accesibilidad:** foco visible, `aria-label`, `aria-pressed`, texto alternativo, `prefers-reduced-motion` y navegación por teclado.

## Estructura

```text
murciagram/
├─ index.html
├─ styles.css
├─ README.md
├─ .vscode/
│  └─ tasks.json
├─ scripts/
│  ├─ optimize-images.ps1
│  └─ optimize-images.sh
└─ assets/
   ├─ favicon.svg
   ├─ raw/          ← fotos originales
   └─ img/          ← versiones -mobile.jpg y -desktop.jpg
```

## Imágenes y licencias

Las fotografías proceden de Wikimedia Commons y se han recortado a 4:3 para las tarjetas:

| Municipio | Archivo original | Autoría | Licencia |
| --- | --- | --- | --- |
| Lorca | [Fortaleza del Sol (Lorca)](<https://commons.wikimedia.org/wiki/File:Lorca_-_2011-12-17_Fortaleza_del_Sol_(Lorca)_001.jpg>) | Luiyo | CC BY-SA 2.0 |
| Cartagena | [Teatro romano de Cartagena](https://commons.wikimedia.org/wiki/File:Teatro_romano_de_Cartagena,_Espa%C3%B1a,_2022-07-16,_DD_02.jpg) | Diego Delso | CC BY-SA 4.0 |
| Caravaca de la Cruz | [Vista de Caravaca de la Cruz](https://commons.wikimedia.org/wiki/File:Lots_of_buildings_with_mission_tile_roofs_in_Caravaca_de_la_Cruz,_Noroeste,_Murcia,_Spain,_2025_February.jpg) | Ximonic (Simo Räsänen) | CC BY-SA 4.0 |
| Murcia | [Sábado Santo en Murcia](https://commons.wikimedia.org/wiki/File:S%C3%A1bado_Santo_en_Murcia_19-04-2014_edited.jpg) | nesimo | CC BY-SA 2.0 |
| Águilas | [Tormenta sobre Águilas](<https://commons.wikimedia.org/wiki/File:Storm_over_Aguilas_(Spain)_-_panoramio.jpg>) | HunTeR | CC BY-SA 3.0 |
| Mazarrón | [Gredas de Bolnuevo](https://commons.wikimedia.org/wiki/File:Enchanted_City_of_Bolnuevo.jpg) | Martinvl | CC BY-SA 4.0 |
| Cieza | [Cieza desde la Sierra de Ascoy](https://commons.wikimedia.org/wiki/File:Cieza_desde_la_Sierra_de_Ascoy.jpg) | Ramón Cutanda López | CC BY 2.0 |
| Jumilla | [Plaza de Arriba de Jumilla](https://commons.wikimedia.org/wiki/File:Jumilla._Plaza_de_Arriba.JPG) | Enrique Íñiguez Rodríguez (Qoan) | CC BY-SA 3.0 |

> Para cambiar una foto, sustituye el archivo en `assets/raw/` manteniendo el nombre (por ejemplo, `lorca.jpg`) y ejecuta la tarea de optimización.

## Preparación de las imágenes con ImageMagick

Las fotos originales viven en `assets/raw/`. Cada una genera dos variantes en `assets/img/`:

```bash
magick assets/raw/lorca.jpg -auto-orient -resize '400x300^' -gravity center -extent 400x300 -strip -quality 82 assets/img/lorca-mobile.jpg
magick assets/raw/lorca.jpg -auto-orient -resize '1000x750^' -gravity center -extent 1000x750 -strip -quality 85 assets/img/lorca-desktop.jpg
```

Instalación de ImageMagick en Windows:

```powershell
winget install --id ImageMagick.ImageMagick
```

En macOS: `brew install imagemagick`. En Debian/Ubuntu: `sudo apt install imagemagick`.

### Automatización en VS Code

`.vscode/tasks.json` define la tarea **"Optimizar imágenes (ImageMagick)"**, que recorre `assets/raw/*` y exporta en bloque las dos versiones a `assets/img/`.

1. Abre la carpeta del proyecto en VS Code.
2. Pulsa `Ctrl + Shift + B` (o *Terminal → Ejecutar tarea…*).
3. La tarea detecta `magick` en el PATH; si no lo encuentra, busca la instalación en `Program Files`/`LocalAppData` y, en Linux/macOS, usa `convert` (ImageMagick 6) como alternativa.

La lógica está en `scripts/optimize-images.ps1` (Windows) y `scripts/optimize-images.sh` (Linux/macOS). Se puede ejecutar también desde terminal:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/optimize-images.ps1
```

```bash
bash scripts/optimize-images.sh
```

## Preparado para la fase JavaScript

- Cada tarjeta tiene `data-municipio` y un botón `.like[data-like]` con `aria-pressed`.
- `.like[aria-pressed="true"]` ya rellena el corazón.
- `.card.is-liked { order: -1 }` hará que la tarjeta suba al principio de la galería Flexbox.
- La tarjeta guardada ya cambia de estado visual con `:has(.toggle:checked)`, sin necesidad de JavaScript.

## Despliegue en GitHub Pages

1. Crea un repositorio público llamado `murciagram`.
2. Sube el proyecto:

   ```bash
   git init
   git add .
   git commit -m "MurciaGram: galería visual de la Región de Murcia"
   git branch -M main
   git remote add origin https://github.com/TU-USUARIO/murciagram.git
   git push -u origin main
   ```

3. En GitHub: *Settings → Pages → Deploy from a branch → `main` / root*.
4. Sustituye `TU-USUARIO` en `index.html` (canonical, Open Graph, JSON-LD) y en este README por tu usuario real.

## Checklist del enunciado

| Requisito | Estado |
| --- | --- |
| HTML5 semántico sin contenedores genéricos | ✅ |
| `viewport` con escala correcta y zoom controlado | ✅ |
| `robots` index/follow, descripción y Open Graph | ✅ |
| CSS base = móvil (< 600 px), una columna Flexbox | ✅ |
| Sintaxis de rangos `>=` / `<=`, sin `min-width` ni `max-width` | ✅ |
| Tableta 600–800 px con 2 columnas | ✅ |
| Escritorio > 800 px con CSS Grid y galería Flexbox | ✅ |
| `@media print` con fondo blanco y sin menú/botones | ✅ |
| Tarjetas con borde, `border-radius` y `box-shadow` | ✅ |
| Hover/foco con `transform` y `cubic-bezier` | ✅ |
| Efecto permanente con selectores de estado | ✅ |
| Overlay Pinterest con texto, "Me gusta" y enlace externo | ✅ |
| `<picture>` con versión móvil y de escritorio | ✅ |
| `loading="lazy"` en imágenes fuera del viewport | ✅ |
| ImageMagick + variantes de imagen | ✅ |
| Automatización en VS Code | ✅ (+1 punto) |
| Preparación para la fase JavaScript | ✅ |
| README documentado | ✅ |
| Repositorio público y despliegue online | ⏳ Pendiente de publicar con tu cuenta de GitHub |

## Nota sobre accesibilidad

El enunciado pide inhabilitar el zoom (`maximum-scale=1.0, user-scalable=no`). Se ha implementado así de forma intencionada para cumplir la práctica, aunque en un proyecto real de accesibilidad se recomendaría permitir el zoom del usuario.
