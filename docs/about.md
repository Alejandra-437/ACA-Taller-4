---
title: Acerca de
summary: Información sobre este manual y referencias.
date: 2026-06-20
---

# :material-information: Acerca de este manual

## :material-bookshelf: Sobre el proyecto

Este manual fue creado como parte del **Taller de MkDocs** del curso de **Aplicación De Código Abierto (ACA)**.

El objetivo es demostrar las capacidades de **MkDocs** con el tema **Material for MkDocs** para crear documentación técnica de alta calidad.

## :material-target: Objetivos de aprendizaje

Al completar este taller, se cubren los siguientes objetivos:

| Objetivo | Estado |
|----------|--------|
| Crear un proyecto MkDocs desde cero | :material-check: |
| Configurar el tema Material for MkDocs | :material-check: |
| Personalizar paleta de colores y tipografía | :material-check: |
| Crear múltiples páginas con navegación | :material-check: |
| Usar extensiones de Markdown (admoniciones, tabs, etc.) | :material-check: |
| Configurar plugins (search, git-revision-date) | :material-check: |
| Incluir imágenes, tablas y bloques de código | :material-check: |
| Publicar en GitHub Pages | :material-check: |

## :material-tools: Tecnologías utilizadas

- :material-language-python: **Python 3.13.0** - Lenguaje de programación
- :material-book-open-page-variant: **MkDocs 1.6.1** - Generador de sitios estáticos
- :material-palette: **Material for MkDocs** - Tema visual
- :material-puzzle: **PyMdown Extensions** - Extensiones de Markdown
- :material-source-repository: **Git** - Control de versiones
- :fontawesome-brands-github: **GitHub Pages** - Hosting del sitio

## :material-file-document-multiple: Estructura del proyecto

```text
manual-git-github/
├── mkdocs.yml              # Configuración del sitio
├── docs/
│   ├── index.md            # Página principal
│   ├── about.md            # Esta página
│   ├── img/                # Imágenes
│   │   ├── git.png
│   │   └── gitflow-branches.png
│   ├── guia/               # Sección de guía básica
│   │   ├── introduccion.md
│   │   ├── comandos.md
│   │   └── flujo.md
│   └── avanzado/           # Sección avanzada
│       ├── ramas.md
│       └── colaboracion.md
└── site/                   # Generado por mkdocs build
```

## :material-format-list-checks: Requisitos cubiertos

Este manual cumple con todos los requisitos del taller:

- :material-check: **Tabla**: Presente en cada página principal.
- :material-check: **Bloque de código con pestañas (tabs)**: Múltiples ejemplos con `=== "Lenguaje"`.
- :material-check: **Enlace interno entre páginas**: Navegación completa con `nav:`.
- :material-check: **Imagen almacenada en docs/img/**: Logo de Git en la página principal.
- :material-check: **Bloque de admonición**: Notas, tips, warnings en cada página.

## :material-account-circle: Autor

| Campo | Valor |
|-------|-------|
| **Estudiante** | Estudiante ACA |
| **Curso** | Aplicación De Código Abierto |
| **Taller** | Documentación técnica con MkDocs |
| **Fecha** | Junio 2026 |

## :material-link-variant: Referencias y recursos

### Documentación oficial

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [PyMdown Extensions](https://facelessuser.github.io/pymdown-extensions/)

### Git y GitHub

- [Pro Git Book (español)](https://git-scm.com/book/es/v2)
- [GitHub Docs](https://docs.github.com/)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)

### Tutoriales recomendados

- [Learn Git Branching](https://learngitbranching.js.org/) - Interactivo
- [Oh My Git!](https://ohmygit.org/) - Juego para aprender Git
- [Git Immersion](https://gitimmersion.com/) - Tutorial paso a paso

## :material-creation: Cómo contribuir

Si encuentras errores o quieres mejorar este manual:

1. Haz un fork del repositorio
2. Crea una rama con tu cambio (`git checkout -b mejora/seccion`)
3. Realiza los cambios y haz commit
4. Sube la rama y abre un Pull Request

## :material-license: Licencia

Este material se distribuye con fines educativos bajo licencia MIT.

---

!!! quote "Mensaje final"
    *"La documentación es un superpoder. Si sabes cómo hacerlo, el siguiente paso es enseñarlo."*

[:material-home: Volver al inicio](index.md){ .md-button }
