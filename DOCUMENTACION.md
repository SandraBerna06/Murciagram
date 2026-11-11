<img src="assets/banner.svg" alt="MurciaGram · El Pinterest de la Región de Murcia" width="100%">

# MurciaGram

**Galería de inspiración visual de la Región de Murcia.** Un proyecto académico de HTML5 y CSS3, sin JavaScript de interacción, que presenta ocho municipios murcianos con fotografías reales, tarjetas estilo Pinterest y un diseño *mobile-first* completamente responsive.

[![HTML5](https://img.shields.io/badge/HTML5-sem%C3%A1ntico-e34f26?logo=html5&logoColor=white)](https://developer.mozilla.org/es/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-moderno-1572b6?logo=css3&logoColor=white)](https://developer.mozilla.org/es/docs/Web/CSS)
[![Responsive](https://img.shields.io/badge/dise%C3%B1o-mobile--first-0f5f5c)](#diseño-responsive)
[![Sin JavaScript](https://img.shields.io/badge/JavaScript-0%20l%C3%ADneas-f7df1e?logo=javascript&logoColor=black)](#preparado-para-la-fase-javascript)

> [!NOTE]
> **Demo:** `https://sandraberna06.github.io/Murciagram/`
> Sustituye `sandraberna06` por tu usuario de GitHub antes de publicar. El proyecto está listo para GitHub Pages.

---

## Índice

- [Sobre el proyecto](#sobre-el-proyecto)
- [Características](#características)
- [Diseño responsive](#diseño-responsive)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Empezar a usarlo](#empezar-a-usarlo)
- [Imágenes con ImageMagick](#imágenes-con-imagemagick)
- [Accesibilidad y rendimiento](#accesibilidad-y-rendimiento)
- [Preparado para la fase JavaScript](#preparado-para-la-fase-javascript)
- [Créditos de las imágenes](#créditos-de-las-imágenes)
- [Despliegue en GitHub Pages](#despliegue-en-github-pages)
- [Checklist del enunciado](#checklist-del-enunciado)
- [Licencia](#licencia)

---

## Sobre el proyecto

**MurciaGram** es una práctica de CSS3 que simula una plataforma de descubrimiento visual, en la línea de Pinterest, centrada en la Región de Murcia. La página reúne **ocho municipios** —Lorca, Cartagena, Caravaca de la Cruz, Murcia, Águilas, Mazarrón, Cieza y Jumilla— y combina patrimonio, costa, naturaleza y gastronomía en una interfaz editorial.

El objetivo del ejercicio era demostrar dominio de:

- HTML5 semántico, sin `div` genéricos de maquetación.
- CSS moderno: Flexbox, CSS Grid, media queries con sintaxis de rangos, `:has()`, `:checked`, custom properties y transiciones con `cubic-bezier`.
- Diseño *mobile-first* real, con la versión móvil como base y mejoras progresivas.
- Estilos de impresión y preparación para una futura capa de JavaScript.

El resultado es una web **estática, sin dependencias y sin framework**: solo HTML y CSS.

---

## Características

### Diseño y composición

- Paleta mediterránea: terracota, verde profundo, dorado y crema.
- Cabecera *sticky* con efecto *glass* (`backdrop-filter`).
- Hero editorial con imagen destacada, estadísticas y llamadas a la acción.
- Tarjetas con borde sutil, esquinas redondeadas, sombras difuminadas y animación al pasar el ratón o al enfocar con el teclado.
- Tipografía editorial: serif para títulos y sans-serif para el cuerpo, usando pilas de fuentes del sistema (sin peticiones externas).

### Interacción sin JavaScript

- **Overlay tipo Pinterest:** al hacer hover o foco, la imagen se oscurece, aparece una descripción, un botón de *me gusta* y un enlace a la web oficial del municipio.
- **Estado guardado permanente:** el botón “Guardar en mi ruta” es un `label` asociado a un checkbox oculto. Gracias a `:checked` y `:has()`, la tarjeta entera cambia de color y muestra la insignia “✓ Guardado”.
- **Foco visible** en todos los elementos interactivos y navegación completa por teclado.
- **`prefers-reduced-motion`:** reduce animaciones si el sistema lo solicita.

### Rendimiento y SEO

- `<picture>` con variantes de **400 × 300 px** para móvil y **1000 × 750 px** para escritorio.
- `loading="lazy"` en las imágenes de la galería y `fetchpriority="high"` en la imagen principal.
- `width` y `height` explícitos para evitar saltos de maquetación (CLS).
- Metadatos `description`, `robots`, `canonical`, Open Graph, Twitter Cards y JSON-LD.
- Favicon SVG propio.

---

## Diseño responsive

La base del CSS está pensada para móvil y se amplía con dos breakpoints. **No se usan `min-width` ni `max-width`** en las media queries: solo la sintaxis moderna de rangos.

| Rango de ancho | Técnica principal | Columnas de galería |
| --- | --- | --- |
| `< 600 px` | Flexbox en columna, navegación en varias filas | 1 |
| `600 px – 800 px` | `@media (width >= 600px) and (width <= 800px)`, Flexbox con `flex-wrap` | 2 |
| `> 800 px` | `@media (width > 800px)`, CSS Grid con sidebar fija + galería Flexbox fluida | fluida |

En escritorio, el `body` se organiza con `grid-template-areas`:

```css
grid-template-areas:
  "header header"
  "aside  main"
  "footer footer";
```

La barra lateral permanece *sticky* mientras se recorre la galería y el pie queda por encima de ella al llegar al final de la página.

### Impresión

`@media print` oculta la barra lateral, la navegación y los botones de interacción; fuerza fondo blanco, tipografía serif y tarjetas sin sombras, con `break-inside: avoid` para que no se corten.

---

## Estructura del proyecto

```text
murciagram/
├── index.html                 # Página completa (semántica, metadatos, tarjetas)
├── styles.css                 # Todo el diseño: base móvil, tablet, escritorio e impresión
├── README.md
├── .vscode/
│   └── tasks.json             # Tarea "Optimizar imágenes (ImageMagick)"
├── scripts/
│   ├── optimize-images.ps1    # Automatización en Windows
│   └── optimize-images.sh     # Automatización en Linux/macOS
└── assets/
    ├── banner.svg             # Cabecera del README
    ├── favicon.svg
    ├── raw/                   # Fotografías originales (no necesarias para publicar)
    └── img/                   # Versiones optimizadas -mobile.jpg y -desktop.jpg
```

> [!TIP]
> Para publicar solo necesitas `index.html`, `styles.css` y la carpeta `assets/img/`. La carpeta `assets/raw/` y los scripts son para regenerar las imágenes.

---

## Empezar a usarlo

### Opción A · Live Server (recomendado en VS Code)

1. Descarga o clona el repositorio.
2. Abre la carpeta completa en VS Code: **Archivo → Abrir carpeta…**
3. Instala la extensión **Live Server** de Ritwick Dey.
4. Haz clic derecho sobre `index.html` y elige **Open with Live Server**.

### Opción B · Servidor local con Node

```bash
npx serve .
```

### Opción C · Abrir el archivo directamente

También funciona con doble clic sobre `index.html`, aunque un servidor local evita problemas de caché.

> [!IMPORTANT]
> `index.html`, `styles.css` y `assets/` deben estar en el mismo nivel. No renombres las imágenes: el HTML las referencia como `assets/img/lorca-desktop.jpg`, etc.

---

## Imágenes con ImageMagick

Las fotos originales viven en `assets/raw/`. Cada una genera dos variantes recortadas a 4:3 en `assets/img/`:

```bash
magick assets/raw/lorca.jpg -auto-orient -resize '400x300^' -gravity center -extent 400x300 -strip -quality 82 assets/img/lorca-mobile.jpg
magick assets/raw/lorca.jpg -auto-orient -resize '1000x750^' -gravity center -extent 1000x750 -strip -quality 85 assets/img/lorca-desktop.jpg
```

### Instalación de ImageMagick

| Sistema | Comando |
| --- | --- |
| Windows | `winget install --id ImageMagick.ImageMagick` |
| macOS | `brew install imagemagick` |
| Debian / Ubuntu | `sudo apt install imagemagick` |

### Automatización en VS Code

`.vscode/tasks.json` define la tarea **“Optimizar imágenes (ImageMagick)”**:

1. Abre la carpeta del proyecto en VS Code.
2. Pulsa `Ctrl + Shift + B` o ve a **Terminal → Ejecutar tarea…**.
3. La tarea recorre `assets/raw/*` y genera las dos versiones en `assets/img/`.

Los scripts detectan `magick` en el `PATH`; si no lo encuentran, buscan la instalación en `Program Files` / `LocalAppData` y, en Linux/macOS, usan `convert` (ImageMagick 6) como alternativa.

También se pueden ejecutar a mano:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File scripts/optimize-images.ps1
```

```bash
bash scripts/optimize-images.sh
```

---

## Accesibilidad y rendimiento

- HTML semántico con `header`, `nav`, `main`, `aside`, `footer`, `section`, `article`, `figure`, `figcaption` y `menu`.
- Texto alternativo descriptivo en las ocho fotografías.
- `aria-label`, `aria-labelledby`, `aria-pressed` y `aria-hidden` donde aportan contexto.
- Foco visible con `outline` dorado y navegación completa por teclado.
- Contraste de texto secundario corregido para superar **WCAG AA (4,5:1)**.
- Imágenes con dimensiones explícitas, `lazy` y variantes responsive.
- **Lighthouse:** Buenas prácticas 100, SEO 100, Accesibilidad 94. El único aviso es el zoom desactivado, requerido por el enunciado.

> [!NOTE]
> El enunciado pide `maximum-scale=1.0, user-scalable=no`. Se mantiene de forma intencionada para cumplir la práctica, aunque en un proyecto real de accesibilidad se recomendaría permitir el zoom del usuario.

---

## Preparado para la fase JavaScript

El HTML y el CSS ya incluyen los ganchos necesarios para una futura capa de interacción:

- Cada tarjeta tiene `data-municipio` y un botón `.like[data-like]` con `aria-pressed`.
- `.like[aria-pressed="true"]` ya rellena el corazón.
- `.card.is-liked { order: -1 }` permite subir la tarjeta al principio de la galería Flexbox.
- El estado guardado ya funciona sin JavaScript mediante `:has(.toggle:checked)`.
- Las tarjetas y los botones tienen clases estables y `id` únicos por municipio.

---

## Créditos de las imágenes

Las fotografías proceden de **Wikimedia Commons** y se han recortado y optimizado para el proyecto. Cada imagen conserva su licencia original.

| Municipio | Fotografía original | Autoría | Licencia |
| --- | --- | --- | --- |
| Lorca | [Fortaleza del Sol (Lorca)](<https://commons.wikimedia.org/wiki/File:Lorca_-_2011-12-17_Fortaleza_del_Sol_(Lorca)_001.jpg>) | Luiyo | CC BY-SA 2.0 |
| Cartagena | [Teatro romano de Cartagena](https://commons.wikimedia.org/wiki/File:Teatro_romano_de_Cartagena,_Espa%C3%B1a,_2022-07-16,_DD_02.jpg) | Diego Delso | CC BY-SA 4.0 |
| Caravaca de la Cruz | [Vista de Caravaca de la Cruz](https://commons.wikimedia.org/wiki/File:Lots_of_buildings_with_mission_tile_roofs_in_Caravaca_de_la_Cruz,_Noroeste,_Murcia,_Spain,_2025_February.jpg) | Ximonic (Simo Räsänen) | CC BY-SA 4.0 |
| Murcia | [Sábado Santo en Murcia](https://commons.wikimedia.org/wiki/File:S%C3%A1bado_Santo_en_Murcia_19-04-2014_edited.jpg) | nesimo | CC BY-SA 2.0 |
| Águilas | [Tormenta sobre Águilas](<https://commons.wikimedia.org/wiki/File:Storm_over_Aguilas_(Spain)_-_panoramio.jpg>) | HunTeR | CC BY-SA 3.0 |
| Mazarrón | [Gredas de Bolnuevo](https://commons.wikimedia.org/wiki/File:Enchanted_City_of_Bolnuevo.jpg) | Martinvl | CC BY-SA 4.0 |
| Cieza | [Cieza desde la Sierra de Ascoy](https://commons.wikimedia.org/wiki/File:Cieza_desde_la_Sierra_de_Ascoy.jpg) | Ramón Cutanda López | CC BY 2.0 |
| Jumilla | [Plaza de Arriba de Jumilla](https://commons.wikimedia.org/wiki/File:Jumilla._Plaza_de_Arriba.JPG) | Enrique Íñiguez Rodríguez (Qoan) | CC BY-SA 3.0 |

> Para cambiar una foto, sustituye el archivo en `assets/raw/` manteniendo el nombre y ejecuta la tarea de optimización.

---

## Despliegue en GitHub Pages

1. Crea un repositorio **público** llamado `murciagram`.
2. Sube el proyecto:

   ```bash
   git init
   git add .
   git commit -m "MurciaGram: galería visual de la Región de Murcia"
   git branch -M main
   git remote add origin https://github.com/sandraberna06/Murciagram.git
   git push -u origin main
   ```

3. En GitHub: **Settings → Pages → Deploy from a branch → `main` / (root)**.
4. Espera un par de minutos y abre `https://sandraberna06.github.io/Murciagram/`.

### Antes de publicar, sustituye `sandraberna06`

| Archivo | Dónde |
| --- | --- |
| `index.html` | `canonical`, `og:url`, `og:image`, `twitter:image` y JSON-LD |
| `README.md` | Enlace de demo y comandos de clonado/despliegue |

---

## Checklist del enunciado

| Requisito | Estado |
| --- | --- |
| HTML5 semántico sin contenedores genéricos | ✅ |
| `viewport` con escala y zoom controlado | ✅ |
| `robots` index/follow, descripción y Open Graph | ✅ |
| CSS base = móvil (< 600 px), una columna Flexbox | ✅ |
| Sintaxis de rangos `>=` / `<=`, sin `min-width` ni `max-width` | ✅ |
| Tableta 600–800 px con 2 columnas | ✅ |
| Escritorio > 800 px con CSS Grid y galería Flexbox | ✅ |
| `@media print` con fondo blanco y sin menú/botones | ✅ |
| Tarjetas con borde, `border-radius` y `box-shadow` | ✅ |
| Hover/foco con `transform` y `cubic-bezier` | ✅ |
| Efecto permanente con selectores de estado | ✅ |
| Overlay Pinterest con texto, “Me gusta” y enlace externo | ✅ |
| `<picture>` con versión móvil y de escritorio | ✅ |
| `loading="lazy"` en imágenes fuera del viewport | ✅ |
| ImageMagick + variantes de imagen | ✅ |
| Automatización en VS Code | ✅ |
| Preparación para la fase JavaScript | ✅ |
| README documentado | ✅ |
| Repositorio público y despliegue online | ⏳ Pendiente de publicar |

---

## Licencia

- **Código** (`index.html`, `styles.css`, scripts): proyecto académico. Puede reutilizarse con fines educativos citando la autoría del proyecto.
- **Fotografías**: cada imagen mantiene la licencia indicada en la tabla anterior (CC BY 2.0, CC BY-SA 2.0, 3.0 o 4.0). Si reutilizas una foto, conserva la atribución y la licencia correspondiente.
- **Tipografías**: pilas de fuentes del sistema, sin archivos ni licencias externas.

---

<p align="center">
  Hecho con HTML y CSS para la <strong>Región de Murcia</strong> · 2026
</p>
