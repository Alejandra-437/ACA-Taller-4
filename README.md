# Manual de Git y GitHub - Documentación con MkDocs

Sitio de documentación técnica creado con **MkDocs** y el tema **Material for MkDocs** como parte del taller de **Aplicacion de Código Abierto (ACA)**.

## :rocket: Vista rápida

El sitio es un manual completo sobre Git y GitHub que cubre desde conceptos básicos hasta flujos de trabajo colaborativos avanzados.

## :open_file_folder: Estructura del proyecto

```text
.
├── mkdocs.yml              # Configuración de MkDocs y navegación
├── README.md               # Este archivo
├── .gitignore              # Archivos ignorados por Git
├── docs/                   # Contenido del sitio
│   ├── index.md            # Página de inicio
│   ├── about.md            # Acerca de
│   ├── img/                # Imágenes del sitio
│   ├── guia/               # Sección "Guía Básica"
│   │   ├── introduccion.md
│   │   ├── comandos.md
│   │   └── flujo.md
│   └── avanzado/           # Sección "Temas Avanzados"
│       ├── ramas.md
│       └── colaboracion.md
└── site/                   # Generado por mkdocs build
```

## :wrench: Comandos principales

```bash
# Servidor de desarrollo (auto-refresh)
mkdocs serve

# Generar sitio estático en /site
mkdocs build

# Publicar en GitHub Pages
mkdocs gh-deploy
```

## :clipboard: Requisitos cubiertos por el taller

| Requisito | Ubicación |
|-----------|-----------|
| Tabla | Múltiples (index.md, comandos.md, flujo.md, etc.) |
| Bloque de código con pestañas (tabs) | index.md, introduccion.md, comandos.md |
| Enlace interno entre páginas | Toda la navegación en `mkdocs.yml` |
| Imagen en `docs/img/` | `docs/img/git.png`, `docs/img/gitflow-branches.png` |
| Bloque de admonición (tip/warning/note) | Distribuidos en todas las páginas |

## :globe_with_meridians: Publicación en GitHub Pages

### 1. Crear el repositorio en GitHub

1. Ve a [github.com/new](https://github.com/new).
2. Nombre del repositorio: `manual-git-github` (o el que prefieras).
3. Marca como **público**.
4. **No** inicialices con README (lo haremos localmente).

### 2. Conectar el proyecto local con GitHub

```bash
# Inicializa el repositorio (si no lo habías hecho)
git init

# Agrega todos los archivos
git add .

# Primer commit
git commit -m "Sitio de documentación con MkDocs"

# Renombra la rama principal a main
git branch -M main

# Conecta con tu repositorio
git remote add origin https://github.com/TU_USUARIO/manual-git-github.git

# Sube los cambios
git push -u origin main
```

### 3. Desplegar el sitio

```bash
# Construye y publica automáticamente
mkdocs gh-deploy
```

Este comando:

1. Construye el sitio en la carpeta `site/`.
2. Crea (o actualiza) la rama `gh-pages`.
3. Sube el contenido a GitHub.

### 4. Habilitar GitHub Pages

1. Ve a tu repositorio en GitHub.
2. **Settings** → **Pages**.
3. En **Source**, selecciona la rama `gh-pages` y la carpeta `/ (root)`.
4. Haz clic en **Save**.

Después de unos minutos, tu sitio estará disponible en:

```text
https://TU_USUARIO.github.io/manual-git-github/
```

### 5. Personalizar la URL en `mkdocs.yml`

Edita el campo `site_url` en `mkdocs.yml`:

```yaml
site_url: https://TU_USUARIO.github.io/manual-git-github/
```

## :art: Personalización aplicada

- **Tema Material** con paleta de colores personalizada (indigo + pink).
- **Modo claro y oscuro** automático según preferencia del usuario.
- **Iconos Material Design** en títulos y navegación.
- **Búsqueda** con resaltado y sugerencias.
- **Tabs de navegación** en la parte superior.
- **Código con tabs** (Linux, Windows, Git Bash, etc.).
- **Diagramas Mermaid** en flujo.md.
- **Admoniciones** (note, tip, warning, info, success, danger).
- **Botones** de navegación entre páginas.
- **Fecha de última modificación** por página.
- **Tablas de contenido** plegables con anclas.

## :test_tube: Vista previa local

```bash
mkdocs serve
```

Abre en tu navegador: [http://127.0.0.1:8000](http://127.0.0.1:8000)

## :memo: Licencia

MIT - Material educativo de uso libre.

---

**Autor**: Alejandra Vanessa Serrano Cordova
**Fecha**: Junio 2026
**Curso**: Aplicacion de Código Abierto
