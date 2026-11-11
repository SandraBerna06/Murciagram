<img src="assets/banner.svg" alt="MurciaGram · El Pinterest de la Región de Murcia" width="100%">

# MurciaGram

**Descubre la Región de Murcia, un municipio a la vez.**

Una galería visual, libre y sencilla, para conocer ocho lugares de la Región de Murcia a través de sus fotografías, su historia y su gastronomía.

<p align="center">
  <a href="https://sandraberna06.github.io/Murciagram/">
    <img src="https://img.shields.io/badge/Abrir_MurciaGram-ver_la_web-0f5f5c?style=for-the-badge&logo=githubpages&logoColor=white" alt="Abrir MurciaGram">
  </a>
</p>

> **Enlace directo:** **https://sandraberna06.github.io/Murciagram/**
> No hace falta instalar nada: se abre en el navegador del móvil, la tablet o el ordenador.

---

## ¿Qué es MurciaGram?

MurciaGram es una **galería de inspiración visual** inspirada en Pinterest. Reúne en una sola página ocho municipios de la Región de Murcia y muestra, para cada uno, una fotografía, una descripción breve y un enlace a su web oficial.

Nació como un **proyecto académico de HTML5 y CSS3**, pero está pensado para que cualquiera pueda consultarlo: turistas, estudiantes, vecinos o curiosos que quieran hacerse una idea rápida de lo que ofrece la región.

No hay cuentas, no hay anuncios y no se recogen datos. Es una web estática: solo HTML y CSS.

---

## Qué puedes hacer

- **Explorar los ocho municipios** en una galería de tarjetas.
- **Pasar el ratón o tocar una tarjeta** para ver su descripción, el botón de *me gusta* y el acceso a la web oficial del ayuntamiento.
- **Guardar tu ruta:** pulsa “Guardar en mi ruta” y la tarjeta cambia de color para que la recuerdes.
- **Consultar desde cualquier dispositivo:** móvil, tablet u ordenador, con un diseño que se adapta.
- **Imprimir la página** y llevarte una versión limpia en papel, sin menús ni botones.

> Los botones de *me gusta* y de guardar son **visuales**: funcionan con CSS, sin JavaScript, y no se guardan al cerrar la página. La idea es que sirvan de base para una futura versión interactiva.

---

## Los ocho municipios

| Municipio | Categoría | Qué no te puedes perder |
| --- | --- | --- |
| **Lorca** | Cultura · Interior | La Fortaleza del Sol y su Semana Santa |
| **Cartagena** | Cultura · Costa | El teatro romano y el puerto milenario |
| **Caravaca de la Cruz** | Cultura · Noroeste | El Real Alcázar-Santuario y los Caballos del Vino |
| **Murcia** | Gastronomía · Huerta | La Catedral y la huerta murciana |
| **Águilas** | Costa · Mediterráneo | Sus calas turquesa y el carnaval |
| **Mazarrón** | Costa · Bahía | Las Gredas de Bolnuevo y sus playas |
| **Cieza** | Naturaleza · Vega Alta | La floración del valle del Segura |
| **Jumilla** | Gastronomía · Altiplano | Sus viñedos y el vino Monastrell |

---

## Cómo navegar

| Dispositivo | Qué encontrarás |
| --- | --- |
| **Móvil** | Una columna de tarjetas a pantalla completa y un menú de municipios al principio. |
| **Tablet** | Dos columnas para comparar destinos de un vistazo. |
| **Ordenador** | Una barra lateral fija con los municipios y una galería fluida a la derecha. |

Consejos rápidos:

1. Entra en **https://sandraberna06.github.io/Murciagram/**.
2. Desplázate por la galería o usa los enlaces de municipios.
3. Pasa el ratón por una foto (o tócala en el móvil) para leer su descripción.
4. Pulsa el corazón si quieres marcarla y el enlace para visitar la web oficial.

También puedes recorrer toda la página **solo con el teclado**: la tecla `Tab` va resaltando cada enlace y botón con un contorno dorado.

---

## Accesibilidad

El proyecto cuida detalles que facilitan el uso a todo el mundo:

- Textos alternativos descriptivos en todas las fotografías.
- Contraste de color revisado para cumplir **WCAG AA**.
- Foco visible y navegación completa por teclado.
- Respeto por la opción del sistema **“reducir movimiento”**.
- Versión de impresión sin elementos decorativos.

> El zoom del navegador está desactivado porque así lo pedía el enunciado académico. En una web real se recomendaría permitirlo.

---

## Un proyecto académico

MurciaGram se ha construido sin frameworks y sin JavaScript de interacción, con estos ingredientes:

- **HTML5 semántico**: `header`, `nav`, `main`, `aside`, `footer`, `article`, `figure` y `figcaption`, sin `div` de maquetación.
- **CSS3 moderno**: Flexbox, CSS Grid, variables, `:has()`, `:checked`, transiciones con `cubic-bezier` y media queries con sintaxis de rangos.
- **Diseño mobile-first**: la versión móvil es la base; tablet y escritorio se añaden con mejoras progresivas.
- **Imágenes responsive** con `<picture>`, versiones de 400 px y 1000 px, y carga diferida.
- **Estilos de impresión** para obtener una página limpia en papel.
- **ImageMagick** para recortar y optimizar las fotografías, con una tarea automatizada en VS Code.

Si te interesa el detalle técnico —estructura del CSS, breakpoints, flujo de imágenes o despliegue— consulta **[DOCUMENTACION.md](DOCUMENTACION.md)**.

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

Si reutilizas una fotografía, conserva la atribución y la licencia indicadas.

---

## Ver el proyecto en local

No es necesario para consultar la web, pero si quieres abrirlo en tu ordenador:

```bash
git clone https://github.com/sandraberna06/Murciagram.git
cd Murciagram
```

Después, en VS Code, abre la carpeta y usa **Live Server** sobre `index.html`. También puedes ejecutar:

```bash
npx serve .
```

---

## Licencia

- **Código** (`index.html`, `styles.css`, scripts): proyecto académico; puede reutilizarse con fines educativos citando la autoría.
- **Fotografías**: cada una mantiene su licencia de Wikimedia Commons (CC BY o CC BY-SA, según la tabla).
- **Tipografías**: fuentes del sistema, sin archivos externos.

---

<p align="center">
  Proyecto de <a href="https://github.com/sandraberna06">@sandraberna06</a> · Región de Murcia · 2026
  <br>
  <a href="https://sandraberna06.github.io/Murciagram/">sandraberna06.github.io/Murciagram</a>
</p>
