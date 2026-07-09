# Avances – Sitio Web Grupo de Investigación Voz Maya

## Descripción del proyecto

Sitio web académico para el **Grupo de Investigación Voz Maya** de CentroGeo, desarrollado con Hugo Blox (Academic). El grupo trabaja en tecnología de procesamiento de lenguaje natural para la lengua maya yucateca.

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

### Pendiente

- [ ] Agregar correo de contacto público de Alejandro Molina Villegas (no se encontró uno público; el de su perfil en CentroGeo está protegido contra spam)

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
| Noticias | `/vozmaya/post/` | `/vozmaya/es/post/` | Ejemplos del template |
| Equipo | `/vozmaya/people/` | `/vozmaya/es/people/` | Configurado |
| Publicaciones | `/vozmaya/publication/` | `/vozmaya/es/publication/` | Ejemplos del template |
| Eventos | `/vozmaya/event/` | `/vozmaya/es/event/` | Ejemplo del template |
| Contacto | `/vozmaya/contact/` | `/vozmaya/es/contact/` | Configurado |

---

## Personalización pendiente (recomendada)

### Contenido a reemplazar
- **Noticias** (`content/post/` y `content/es/post/`): reemplazar los posts de ejemplo con noticias reales del proyecto
- **Publicaciones** (`content/publication/` y `content/es/publication/`): agregar artículos, tesis y otros trabajos del grupo
- **Eventos** (`content/event/` y `content/es/event/`): agregar conferencias, talleres y presentaciones
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
Reemplazar `assets/media/welcome.jpg` con una imagen representativa del proyecto Voz Maya.

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
