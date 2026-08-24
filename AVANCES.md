# Avances – Sitio Web Grupo de Investigación en Lenguas, Territorio e Inteligencia Artificial

## Descripción del proyecto

Sitio web académico para el **Grupo de Investigación en Lenguas, Territorio e Inteligencia Artificial** (antes "Voz Maya") de CentroGeo, desarrollado con Hugo Blox (Academic). El grupo trabaja en tecnología de procesamiento de lenguaje natural para lenguas de bajos recursos (con foco inicial en la lengua maya yucateca). En inglés: **Languages, Territory and AI Research Group**.

- **URL final**: https://giltia.github.io/
- **Repositorio**: https://github.com/giltia/giltia.github.io
- **GitHub user**: giltia
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
- [x] Correo institucional de Manuel (`al.mmalmora@centrogeo.edu.mx`) agregado a ambos perfiles
- [x] Grupos de la página de equipo en inglés traducidos (antes salían en español): `Principal Investigators`, `Researchers`, `Collaborators`, `Alumni`; los perfiles EN usan ahora esos nombres en `user_groups`
- [x] Categoría "Estudiantes de Posgrado" eliminada en ambos idiomas; Manuel quedó en Investigadores/Researchers
- [x] Rol de Jaziel Carballo cambiado a "PhD Candidate in Geospatial Information Sciences" / "Candidato a Doctorado en Ciencias de Información Geoespacial" (antes "AI in Education Specialist")
- [x] Navbar brand cambiado a la abreviatura **GILTIA** (Grupo de Investigación en Lenguas, Territorio e IA) mediante override local del partial del tema (`layouts/partials/components/headers/navbar.html`, copiado del commit pinneado `661cadc` de blox-bootstrap) y el nuevo parámetro `header.navbar.brand_text` en `params.yaml`. Los títulos de pestaña y el SEO conservan el nombre completo del grupo

#### Sesión del 7 de agosto de 2026

- [x] **Migración a la nueva cuenta GitHub `giltia`**: repo público `giltia/giltia.github.io` con todo el historial de commits; el sitio ahora vive en la raíz `https://giltia.github.io/` (sitio de usuario, sin subruta). El repo viejo `jazielcarballo/vozmaya` sigue existiendo pero ya no se usa
- [x] Configuración migrada: `baseURL`, URL del repositorio en `params.yaml`, ruta del módulo en `go.mod` y datos de este documento
- [x] GitHub Pages habilitado en el repo nuevo (build vía Actions); el workflow `deploy.yml` funcionó sin cambios
- [x] Credenciales: `gh` quedó con dos cuentas (giltia activa, con scope `workflow`; jazielcarballo). Este repo usa `credential.helper` local apuntando a `gh auth git-credential`, así los push salen como giltia sin afectar otros repos
- [x] **Eduardo Mendoza Vargas agregado al equipo** con perfil bilingüe (`content/authors/emendoza/` y ES): Estudiante de Maestría en Geointeligencia Computacional (CentroGeo, 2027), Ingeniería de Datos (UPY, 2025), bio del usuario (EN íntegra, ES traducida), GitHub (Walotex) y LinkedIn (eduardomv24). Foto `Foto_EMV.jpg` → `avatar.jpg`. Datos del CV `Resume Eduardo Mendoza Vargas ESP.docx` (no versionado)
- [x] **Fátima Miranda Pestaña agregada al equipo** con perfil bilingüe (`content/authors/fmiranda/` y ES): Data Engineer / Ingeniera de Datos, Ingeniería de Datos (UPY, 2025), bio del perfil profesional de su CV (publicación WASET 2024 sobre detección de maya yucateco y 3er lugar en Datathón Yucatán i6), LinkedIn (`fatimamirandaa`, extraído del enlace embebido del PDF) y correo personal. Foto `IMG_20260709_130346.jpg` → `avatar.jpg`. CV `FatimaMiranda2025_RESUMEeng.pdf` (no versionado)
- [x] **Sección de equipo unificada en un solo grupo** `Researchers` / `Investigadores`: Jaziel y Alejandro dejaron "Principal Investigators / Investigadores Principales"; las páginas de equipo listan solo ese grupo y ya no muestran encabezados de subgrupos. El orden se mantiene por `weight` (Alejandro 1, Jaziel 2, resto 10)
- [x] Contacto actualizado en EN y ES: correo `giltiamexico@gmail.com` (antes `vozmaya@centrogeo.edu.mx`); los teléfonos fijos de CentroGeo se eliminaron (el celular +52 999 158 8558 se agregó y luego se quitó a petición del usuario, quedando la página sin teléfono)
- [x] Bloque markdown con imagen de fondo `contact.jpg` eliminado de las páginas de contacto (aparecía a pantalla completa después de los datos)
- [x] Foto de Alejandro Molina reemplazada por `IMG_9020.jpg` (commit `f74a662`)
- [x] Bloque de **bienvenida del Dr. Alejandro Molina** agregado a la portada en EN y ES (texto con foto circular `amolina-welcome.jpg`, firmado como líder del grupo); después se generalizó para hablar de "lenguas" en vez de solo maya yucateco (commits `1737a8a` y `2636d1e`)

#### Sesión del 10 de agosto de 2026

- [x] **Hero y SEO generalizados a lenguas de bajos recursos**: el texto del hero en la portada (EN y ES) y las descripciones meta/SEO (`languages.yaml` y `params.yaml`) ya no se limitan a la lengua maya yucateca; ahora dicen "low-resource languages" / "lenguas de bajos recursos" (commit `e4e21f9`)
- [x] Foto de perfil de Jaziel reemplazada por `perfilJC.png` → `avatar.png` en `content/authors/admin/` y `content/es/authors/admin/` (se eliminaron los `avatar.jpg` viejos; el tema acepta `avatar.*`) (commit `b0fe34a`)
- [x] Nombre completo corregido a **Jaziel A. Carballo Tadeo** en los perfiles de autor (`title`, `first_name`, `last_name`) y en las tres menciones de la noticia LxMLS 2026, en ambos idiomas (commit `5d087f3`)

#### Sesión del 24 de agosto de 2026

- [x] Ítem del menú principal cambiado de "Noticias"/"News" a **"Noticias | Prensa"** / **"News | Press"** en `menus.yaml`, `menus.es.yaml` y `menus.en.yaml` (commit `231d060`); el h1 de la página de listado (`content/post/_index.md` y `content/es/post/_index.md`, que decía "Latest News" en ambos idiomas) se corrigió igual a **"News | Press"** / **"Noticias | Prensa"** (commit `281b852`)
- [x] **Sección Noticias | Prensa poblada con 9 notas de prensa reales** sobre la cobertura mediática de la participación de Jaziel Carballo Tadeo en LxMLS 2026 (y una sobre T'aantsil de Alejandro Molina-Villegas), cada una como page bundle en `content/post/<slug>/` y `content/es/post/<slug>/`:
  1. Diario de Yucatán, "Traductor en maya" (17 ago 2026) — commit `23427d2`
  2. PuntoMedio, "Buscan que la IA reconozca y procese la lengua maya" (11 ago 2026)
  3. Telesur (@telesuryuc), post en redes sociales (~10 ago 2026)
  4. TV Azteca Yucatán, segmento #HechosMeridianoYucatán (14 ago 2026) — los tres anteriores en commit `adb8df1`
  5. TecNM Campus Mérida, publicación de Facebook **embebida con iframe** (16 ago 2026) — commit `11f5143`, imagen agregada después en `98630ac`
  6. CentroGeo, anuncio del corpus paralelo maya-español YUA-ES-CCC (1 jul 2026, con enlace interno a la publicación ya existente `/publication/yua-es-corpus/`) — commit `98630ac`
  7. Radio Fórmula Yucatán, "¡El maya yucateco llega a la inteligencia artificial!" (11 ago 2026) — commit `9ff6fcb`
  8. GeoInt Difusión (CentroGeo), "Se podría navegar en maya en la web" sobre la plataforma T'aantsil (abr 2024) — commit `6cc74f0`
  9. TeleYucatán, entrevista en vivo sobre LxMLS 2026 **embebida con el shortcode nativo `{{< youtube >}}`** saltando al minuto 35:23 (start=2123) (~14 ago 2026) — commit `2511b7c`, imagen corregida por la captura real del segmento en `ca2055a`

  Convención establecida: título con el medio antepuesto (`"<Medio>: <titular>"`), `external_link` a la fuente cuando se quiere que la tarjeta enlace directo afuera (con `target="_blank"`), imagen `featured.*` como respaldo visual (captura de la nota, thumbnail de YouTube, etc.) por si la fuente original se cae, y transcripción/resumen del texto en el cuerpo como respaldo adicional. Cuando se prefiere que el lector se quede en el sitio (contenido embebido: iframe de Facebook, video de YouTube), se omite `external_link` para que la tarjeta enlace a la página interna
- [x] Imágenes fuente de las notas (`press/*.png`, `press/*.jpg`) se mantienen locales sin versionar (igual que otros archivos originales del repo, p. ej. CVs y fotos crudas); solo las copias redimensionadas/usadas (`featured.*`) quedan en `content/`
- [x] **Miniaturas de la vista `compact`** (usada en Noticias | Prensa) agrandadas: el tema las limitaba a 150px de ancho (80px en móvil) sin importar la resolución de la imagen fuente. Se agregó `layouts/partials/views/compact.html` (override local del partial de `blox-bootstrap`, mismo patrón que el `card.html` ya existente) generando la imagen a 500px en vez de 150px, y en `assets/scss/template.scss` se subió el `max-width` del CSS a 280px/140px (commit `281b852`)
- [x] Pendiente: `press/secihti.png` quedó sin nota porque el usuario no dio el link de esa fuente

### Pendiente

- [ ] Decidir qué hacer con el repo viejo `jazielcarballo/vozmaya`: su GitHub Pages sigue publicando la versión anterior del sitio en `jazielcarballo.github.io/vozmaya`. Opciones: archivarlo o deshabilitar su Pages
- [ ] Agregar el GitHub de Fátima si tiene (no venía en su CV) y decidir si se mantiene su correo personal de Gmail en el sitio público
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
│   ├── authors/admin/      # Perfil de Jaziel A. Carballo Tadeo
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
| Inicio | `/` | `/es/` | Configurado |
| Noticias \| Prensa | `/post/` | `/es/post/` | 9 notas de prensa reales |
| Equipo | `/people/` | `/es/people/` | 5 miembros en un solo grupo |
| Publicaciones | `/publication/` | `/es/publication/` | 5 publicaciones reales |
| Eventos | `/event/` | `/es/event/` | LxMLS 2026 |
| Contacto | `/contact/` | `/es/contact/` | Configurado |

---

## Personalización pendiente (recomendada)

### Contenido a reemplazar
- **Noticias | Prensa**: hecho — 9 notas de prensa reales (24 de agosto de 2026); agregar nuevas conforme salgan (falta `press/secihti.png`, sin link dado)
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

Desde el 7 de agosto de 2026 hay un **solo grupo** (el `user_groups` del perfil debe coincidir con el de la página de equipo de su idioma):
- EN (`content/people/index.md`): `Researchers`
- ES (`content/es/people/index.md`): `Investigadores`

### Imagen de portada
Hecho: el hero usa `assets/media/imagenVozMaya.jpg`. `welcome.jpg` se conserva porque la página tour la usa de fondo.

### Correo de contacto
Hecho (7 de agosto de 2026): el contacto ahora es `giltiamexico@gmail.com` con celular +52 999 158 8558 (se quitaron los teléfonos fijos de CentroGeo) en:
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
