# Avances – Sitio Web Grupo de Investigación en Lenguas, Territorio e Inteligencia Artificial

## Descripción del proyecto

Sitio web académico para el **Grupo de Investigación en Lenguas, Territorio e Inteligencia Artificial** (antes "Voz Maya") de CentroGeo, desarrollado con Hugo Blox (Academic). El grupo trabaja en tecnología de procesamiento de lenguaje natural para la lengua maya yucateca. En inglés: **Languages, Territory and AI Research Group**.

- **URL final**: https://jazielcarballo.github.io/vozmaya/
- **Repositorio**: https://github.com/jazielcarballo/vozmaya
- **GitHub user**: jazielcarballo
- **Idiomas**: Inglés (principal) + Español

---

## Estado actual

### Completado

- [x] Instalación de Hugo Extended (v0.147.9) en `~/.local/bin`
- [x] Instalación de Go (v1.22.4) en `~/.local/go`
- [x] Clonación y adaptación del template Hugo Blox Research Group
- [x] Configuración bilingüe ES/EN
- [x] Contenido de la página principal en español e inglés
- [x] Página de contacto con dirección de CentroGeo (ES/EN)
- [x] Página de equipo con grupos en español
- [x] Perfil del investigador principal (Jaziel Carballo)
- [x] Workflow GitHub Actions para deploy automático a GitHub Pages
- [x] Commit inicial en rama `main`
- [x] Sitio verificado: compila sin errores (53 páginas ES + 18 páginas EN)
- [x] Repositorio publicado en GitHub y desplegado vía GitHub Actions
- [x] Perfil de Alejandro Molina Villegas (líder del grupo) agregado al equipo
- [x] Inglés establecido como idioma por defecto (URL raíz `/vozmaya/`); español disponible en `/vozmaya/es/`
- [x] Secciones News/Events/Publications completas en ambos idiomas (antes solo existían en ES)
- [x] Perfiles del equipo traducidos y disponibles en ambos idiomas
- [x] Sección de noticias eliminada del home en ambos idiomas (la página `/post/` sigue accesible desde el menú)
- [x] Página de contacto actualizada con la ubicación real: CentroGeo Yucatán (Laboratorio Nacional de Geointeligencia, Parque Científico Tecnológico Yucatán, Mérida, CP 97302), teléfonos (9996) 88-53-00 y 42, (9994) 06-00-22 y 25, y mapa apuntando a 21.13087, -89.78084 (coordenadas de OpenStreetMap)

#### Sesión del 9 de julio de 2026

- [x] Publicación técnica sobre el notebook de Colab Whisper-LM (corrección de transcripciones ASR de maya yucateco con Gemini + léxico de 2,988 entradas), en EN y ES, con sección final para solicitar el notebook por correo. El `.ipynb` local NO se versiona (contiene una API key de Gemini; está en `.gitignore`)
- [x] Tres publicaciones de Alejandro Molina agregadas (EN y ES): benchmark de similitud de palabras para maya yucateco (*Inteligencia Artificial*, 2025), Mayasoundex (LatinX in AI @ NAACL 2024) y Findings del shared task AmericasNLP 2024
- [x] Eliminadas las publicaciones de ejemplo del tema (preprint, journal article, conference paper)
- [x] Eliminadas las dos noticias de ejemplo del tema
- [x] Evento de ejemplo reemplazado por LxMLS 2026 (16.ª Lisbon Machine Learning School, 20–25 de julio de 2026, IST Lisboa; Jaziel Carballo aceptado como participante)
- [x] Imagen de portada reemplazada: `imagenVozMaya.jpg` en el bloque hero (original PNG de 8.2 MB redimensionado a 1600px y convertido a JPEG de 327 KB)
- [x] Favicon reemplazado por el logo de GitHub (octocat) en `assets/media/icon.png`
- [x] Logotipos de CentroGeo y SECIHTI quitados de la portada (los SVG siguen en `assets/media/logos/`)
- [x] Grupo renombrado en todo el sitio: portada, título, SEO, footer, contacto, perfil de Alejandro Molina y evento LxMLS

#### Sesión del 13 de julio de 2026

- [x] Manuel Morales Almora agregado al equipo como Estudiante de Posgrado, con perfil bilingüe (`content/authors/mmorales/` y `content/es/authors/mmorales/`): rol, bio, intereses, formación (Maestría en Ciencias de Información Geoespacial en CentroGeo 2025–2027; Licenciatura en Estadística, Universidad Veracruzana 2024), GitHub y LinkedIn. Datos tomados de su CV (Google Doc) y bio proporcionada por el usuario
- [x] Avatar de Manuel generado desde `Foto - ManuelMoralesAlmora.png` (1072×1072 PNG de 1.5 MB → JPEG 800×800 de 80 KB); el PNG original quedó en `.gitignore` para no repetir el error del commit `5c2234b`

### Pendiente

- [ ] Agregar correo de contacto público de Alejandro Molina Villegas (no se encontró uno público; el de su perfil en CentroGeo está protegido contra spam)
- [ ] Eliminar el autor de ejemplo del tema (`content/es/authors/吳恩達/`)
- [ ] Decidir si se limpia el historial de git: en el commit `5c2234b` se subieron por error archivos locales (PNG original de 8 MB, `qr-lexiconmaya.png` y 4 fotos de `team/`); se quitaron del repo en `34859e4` pero siguen visibles en el historial público. Quitarlos del todo requiere reescribir historial y push forzado
- [ ] Si el notebook de Colab se quiere publicar, quitar primero la API key de Gemini (y de preferencia rotarla en Google AI Studio)

### Nota técnica importante: por qué `content/` ahora es inglés

Hugo Blox (con esta versión de Hugo, 0.147.9) tiene un problema cuando el **idioma por defecto** usa un `contentDir` distinto de `content` (p. ej. `content/en`): las páginas de sección (news, people, events, publications) del *otro* idioma dejan de generarse (quedan en 404), aunque el idioma no-default con `contentDir` alterno sí funciona sin problema.

Por eso, al cambiar el idioma por defecto a inglés, se intercambiaron físicamente los directorios:
- `content/` → ahora contiene el contenido en **inglés** (antes vivía en `content/en/`)
- `content/es/` → ahora contiene el contenido en **español** (antes vivía en `content/`)

Si en el futuro se quiere volver a español por defecto, hay que repetir el mismo intercambio (mover `content/es/*` a `content/` y viceversa) en vez de solo cambiar `defaultContentLanguage` en `hugo.yaml`.

---

## Estructura del sitio

```
vozmaya/
├── .github/workflows/
│   └── deploy.yml          # CI/CD para GitHub Pages
├── config/_default/
│   ├── hugo.yaml           # Configuración principal (baseURL, idioma)
│   ├── languages.yaml      # EN (content/, por defecto) y ES (content/es/)
│   ├── menus.es.yaml       # Navegación en español
│   ├── menus.en.yaml       # Navegación en inglés
│   └── params.yaml         # Apariencia, SEO, footer (fallback; se sobreescribe por idioma en languages.yaml)
├── content/                # Contenido en inglés (idioma principal)
│   ├── _index.md           # Página principal EN
│   ├── contact/            # Contacto EN
│   ├── people/             # Equipo EN
│   ├── post/                # Noticias (ejemplos del template)
│   ├── publication/        # Publicaciones (ejemplos del template)
│   ├── event/               # Eventos (ejemplos del template)
│   ├── authors/admin/      # Perfil de Jaziel Carballo
│   ├── authors/amolina/    # Perfil de Alejandro Molina Villegas
│   └── es/                 # Contenido en español
│       ├── _index.md       # Página principal ES
│       ├── contact/        # Contacto ES
│       ├── people/         # Equipo ES
│       └── authors/        # Perfiles del equipo ES
└── assets/media/           # Imágenes del sitio
```

---

## Secciones disponibles

| Sección | URL EN (por defecto) | URL ES | Estado |
|---|---|---|---|
| Inicio | `/vozmaya/` | `/vozmaya/es/` | Configurado |
| Noticias | `/vozmaya/post/` | `/vozmaya/es/post/` | Vacía (ejemplos eliminados) |
| Equipo | `/vozmaya/people/` | `/vozmaya/es/people/` | Configurado |
| Publicaciones | `/vozmaya/publication/` | `/vozmaya/es/publication/` | 5 publicaciones reales |
| Eventos | `/vozmaya/event/` | `/vozmaya/es/event/` | LxMLS 2026 |
| Contacto | `/vozmaya/contact/` | `/vozmaya/es/contact/` | Configurado |

---

## Personalización pendiente (recomendada)

### Contenido a reemplazar
- **Noticias** (`content/post/` y `content/es/post/`): agregar noticias reales del proyecto (la sección quedó vacía)
- **Publicaciones**: hecho — hay 5 reales; agregar nuevas conforme salgan
- **Eventos**: hecho — LxMLS 2026; agregar conferencias, talleres y presentaciones futuras
- **Equipo** (`content/authors/` y `content/es/authors/`): agregar perfiles de cada investigador del grupo

### Agregar investigadores
Como el sitio es bilingüe con directorios de contenido separados, hay que crear el perfil **en ambos idiomas**:
- `content/authors/<nombre>/_index.md` (perfil en inglés)
- `content/es/authors/<nombre>/_index.md` (perfil en español)

Cada uno con:
- `_index.md` (perfil con nombre, rol, intereses, redes)
- `avatar.jpg` o `avatar.png` (foto de perfil, puede ser la misma en ambos idiomas)

Grupos disponibles en `content/people/index.md`:
- `Investigadores Principales`
- `Investigadores`
- `Estudiantes de Posgrado`
- `Colaboradores`
- `Alumni`

### Imagen de portada
Hecho: el hero usa `assets/media/imagenVozMaya.jpg`. `welcome.jpg` se conserva porque la página tour la usa de fondo.

### Correo de contacto
Actualizar `vozmaya@centrogeo.edu.mx` en:
- `content/contact/index.md`
- `content/es/contact/index.md`

---

## Entorno de desarrollo

Desde julio 2026 el desarrollo se hace en Windows, con el repo clonado en `C:\Users\Jaziel Carballo\Documents\Claude\web\vozmaya`. En esta máquina **no están instalados Hugo ni Go**, así que no hay vista previa local; los cambios se verifican tras el deploy automático de GitHub Actions.

Comandos del entorno Linux original (por si se retoma ahí):

```bash
# Exportar PATH para usar Hugo y Go
export PATH="$HOME/.local/bin:$HOME/.local/go/bin:$PATH"

# Servidor local de desarrollo (vista previa en http://localhost:1313/vozmaya/)
cd /home/jaz/Documents/opencode/web/centrogeo/vozmaya
hugo server

# Compilar el sitio
hugo --gc --minify
```

---

## Notas técnicas

- Hugo Extended es requerido por el tema (procesa SCSS)
- El módulo Go descarga el tema automáticamente en el primer build
- El deploy se activa automáticamente con cada `git push` a `main`
- El selector de idioma aparece en la barra de navegación (activado en `params.yaml`)
