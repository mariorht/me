# Sitio personal de Mario Roos

Web estática escrita a mano con HTML, CSS y un poco de JavaScript. No hay generador de sitios, dependencias, compilación ni `npm install`: los archivos del repositorio son exactamente los que se publican.

## Estructura

```
.
├── index.html                  # Portada
├── about/index.html            # Sobre mí
├── experience/index.html       # Experiencia y formación
├── publications/index.html     # Publicaciones
├── blog/
│   ├── index.html              # Listado del blog
│   └── leonardo-aerial-screw/  # Una entrada del blog
│       └── index.html
├── 404.html                    # Página de error
├── assets/
│   ├── css/styles.css          # Todos los estilos
│   ├── js/main.js              # Menú móvil y cabecera con scroll
│   ├── fonts/                  # Roboto y Playfair Display
│   └── images/                 # Imágenes del sitio
├── CNAME                       # Dominio de GitHub Pages
├── .nojekyll                   # Publicar archivos tal cual, sin procesarlos
├── sitemap.xml
└── robots.txt
```

Cada página es un `index.html` dentro de su carpeta, así las URLs quedan limpias (`/about/`, `/blog/`, etc.). Los archivos `about.html`, `experience.html`, `blog.html`, etc. de la raíz son redirecciones para no romper enlaces antiguos.

## Ver el sitio en local

No hace falta instalar nada. Desde la raíz del repositorio:

```bash
python3 -m http.server 8000
```

Abre <http://localhost:8000>. Es importante usar un servidor: abrir `index.html` directamente con `file://` no resuelve bien las rutas absolutas (`/assets/...`).

## Editar contenido

- **Estilos**: todo está en `assets/css/styles.css`, con variables al principio para colores, tipografías y sombras.
- **Portada**: `index.html`. Las secciones están separadas por comentarios y tienen sus propios bloques.
- **Textos de páginas**: edita directamente el HTML de cada carpeta.
- **Curriculum**: la experiencia y la formación están en `experience/index.html`. En la portada hay un resumen de la experiencia y de los estudios; si cambias algo importante, actualiza también ese resumen.
- **Publicaciones**: `publications/index.html`.
- **Email y redes**: el pie de página se repite en cada HTML. El email está en el `footer` y los iconos de GitHub/LinkedIn enlazan a los perfiles.

## Añadir una entrada al blog

1. Crea una carpeta con un nombre corto y sin espacios, por ejemplo `blog/mi-proyecto/`.
2. Copia `blog/leonardo-aerial-screw/index.html` dentro y cambia el título, la fecha, la imagen y el contenido.
3. Añade la tarjeta de la entrada en `blog/index.html` y, si quieres que aparezca en la portada, en la sección `#blog` de `index.html`.
4. Añade la URL a `sitemap.xml`.

## Imágenes

Las fotos del blog están en WebP y limitadas a 1600 px de ancho. Para mantener el sitio rápido, conviene respetar ese tamaño:

```bash
python3 -c "from PIL import Image; im = Image.open('foto.png'); im.thumbnail((1600, 1600)); im.save('foto.webp', 'WEBP', quality=84)"
```

## Publicación

El sitio se publica con GitHub Pages desde la rama `main`:

1. El dominio está en `CNAME`.
2. `.nojekyll` indica a GitHub Pages que sirva los archivos tal cual.
3. No hay que ejecutar ningún build: al hacer push, los cambios están publicados.

## Fuentes

Roboto y Playfair Display se sirven desde `assets/fonts/` (subconjunto latino, licencia SIL Open Font License), así que la web no depende de Google Fonts.
