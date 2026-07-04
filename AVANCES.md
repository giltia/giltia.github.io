# Avances – Sitio Web Grupo de Investigación Voz Maya

## Descripción del proyecto

Sitio web académico para el **Grupo de Investigación Voz Maya** de CentroGeo, desarrollado con Hugo Blox (Academic). El grupo trabaja en tecnología de procesamiento de lenguaje natural para la lengua maya yucateca.

- **URL final**: https://jazielcarballo.github.io/vozmaya/
- **Repositorio**: https://github.com/jazielcarballo/vozmaya
- **GitHub user**: jazielcarballo
- **Idiomas**: Español (principal) + Inglés

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

### Pendiente – pasos del usuario

- [ ] Crear repositorio `vozmaya` en GitHub (público, sin inicializar)
- [ ] Subir el código:
  ```bash
  cd /home/jaz/Documents/opencode/web/centrogeo/vozmaya
  git remote add origin https://github.com/jazielcarballo/vozmaya.git
  git push -u origin main
  ```
- [ ] En GitHub: `Settings → Pages → Source → GitHub Actions`

---

## Estructura del sitio

```
vozmaya/
├── .github/workflows/
│   └── deploy.yml          # CI/CD para GitHub Pages
├── config/_default/
│   ├── hugo.yaml           # Configuración principal (baseURL, idioma)
│   ├── languages.yaml      # ES (content/) y EN (content/en/)
│   ├── menus.es.yaml       # Navegación en español
│   ├── menus.en.yaml       # Navegación en inglés
│   └── params.yaml         # Apariencia, SEO, footer
├── content/                # Contenido en español (idioma principal)
│   ├── _index.md           # Página principal ES
│   ├── contact/            # Contacto ES
│   ├── people/             # Equipo ES
│   ├── post/               # Noticias (ejemplos del template)
│   ├── publication/        # Publicaciones (ejemplos del template)
│   ├── event/              # Eventos (ejemplos del template)
│   ├── authors/admin/      # Perfil de Jaziel Carballo
│   └── en/                 # Contenido en inglés
│       ├── _index.md       # Página principal EN
│       ├── contact/        # Contacto EN
│       └── people/         # Equipo EN
└── assets/media/           # Imágenes del sitio
```

---

## Secciones disponibles

| Sección | URL ES | URL EN | Estado |
|---|---|---|---|
| Inicio | `/vozmaya/` | `/vozmaya/en/` | Configurado |
| Noticias | `/vozmaya/post/` | `/vozmaya/en/post/` | Ejemplos del template |
| Equipo | `/vozmaya/people/` | `/vozmaya/en/people/` | Configurado |
| Publicaciones | `/vozmaya/publication/` | `/vozmaya/en/publication/` | Ejemplos del template |
| Eventos | `/vozmaya/event/` | `/vozmaya/en/event/` | Ejemplo del template |
| Contacto | `/vozmaya/contact/` | `/vozmaya/en/contact/` | Configurado |

---

## Personalización pendiente (recomendada)

### Contenido a reemplazar
- **Noticias** (`content/post/`): reemplazar los posts de ejemplo con noticias reales del proyecto
- **Publicaciones** (`content/publication/`): agregar artículos, tesis y otros trabajos del grupo
- **Eventos** (`content/event/`): agregar conferencias, talleres y presentaciones
- **Equipo** (`content/authors/`): agregar perfiles de cada investigador del grupo

### Agregar investigadores
Crear una carpeta por persona en `content/authors/<nombre>/` con:
- `_index.md` (perfil con nombre, rol, intereses, redes)
- `avatar.jpg` (foto de perfil)

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
- `content/en/contact/index.md`

---

## Comandos útiles

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
