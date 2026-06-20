---
title: Trabajo colaborativo
summary: Pull requests, forks, code review y trabajo en equipo con GitHub.
date: 2026-06-20
---

# :material-account-group: Trabajo colaborativo con GitHub

GitHub facilita la colaboración entre desarrolladores a través de Pull Requests, Issues, code review y otras herramientas.

## :material-account-multiple-plus: Fork: contribuir a proyectos

Un **fork** es una copia de un repositorio en tu cuenta. Te permite experimentar sin afectar al proyecto original.

### Cuándo hacer un fork

!!! example "Casos de uso"
    - Contribuir a proyectos open source.
    - Probar cambios sin afectar el original.
    - Usar como base para un nuevo proyecto.

### Sincronizar un fork con el original

```bash
# Agregar el repositorio original como remoto
git remote add upstream https://github.com/original/proyecto.git

# Ver los remotos
git remote -v

# Traer cambios del original
git fetch upstream

# Fusionar cambios a tu main
git checkout main
git merge upstream/main

# Subir a tu fork
git push origin main
```

## :material-source-pull: Pull Requests

Un **Pull Request (PR)** es una solicitud para fusionar tus cambios en otra rama o repositorio.

### Crear un PR desde la línea de comandos

```bash
# 1. Crea una rama
git checkout -b feature/mejora-busqueda

# 2. Realiza tus cambios
git add .
git commit -m "Mejora algoritmo de búsqueda"

# 3. Sube la rama al remoto
git push -u origin feature/mejora-busqueda

# 4. Ve a GitHub y abre el Pull Request desde la web
```

### Buenas prácticas para un PR

=== "Título"

    - Claro y conciso.
    - Describe el cambio realizado.
    - Ejemplo: "Implementa autenticación con OAuth"

=== "Descripción"

    - Contexto del cambio.
    - Problema que resuelve.
    - Capturas de pantalla si aplica.
    - Referencias a issues (`#123`).

=== "Commits"

    - Commits pequeños y enfocados.
    - Mensajes claros.
    - Un PR puede tener varios commits relacionados.

### Plantilla de PR ejemplo

```markdown
## Descripción
Este PR implementa la autenticación de usuarios usando OAuth 2.0.

## Cambios realizados
- [x] Nuevo endpoint de autenticación
- [x] Integración con proveedor OAuth
- [x] Tests unitarios
- [ ] Documentación (pendiente)

## Cómo probar
1. Configurar las variables de entorno
2. Ejecutar `npm test`
3. Probar el endpoint `/auth/login`

## Issues relacionados
Closes #42
```

## :material-eye-outline: Code Review

El **code review** es la revisión del código antes de fusionarlo.

### Para el autor

!!! tip "Antes de pedir review"
    - :material-check: El código funciona localmente.
    - :material-check: Pasa los tests.
    - :material-check: Sigue las convenciones del equipo.
    - :material-check: Es autoexplicativo o está documentado.
    - :material-check: No incluye archivos innecesarios.

### Para el revisor

!!! tip "Aspectos a revisar"
    - :material-check: **Funcionalidad**: ¿Resuelve el problema?
    - :material-check: **Calidad**: ¿Es legible y mantenible?
    - :material-check: **Performance**: ¿Hay problemas de rendimiento?
    - :material-check: **Seguridad**: ¿Hay vulnerabilidades potenciales?
    - :material-check: **Tests**: ¿Está adecuadamente probado?

### Comentarios constructivos

=== "Comentario útil"

    "Considera extraer esta lógica a una función separada para mejorar la legibilidad. ¿Qué te parece?"

=== "Comentario a evitar"

    "Esto está mal."

!!! success "Recuerda"
    El objetivo del code review es mejorar la calidad del código y compartir conocimiento, no criticar.

## :material-bug-outline: Issues

Las **issues** son tickets para reportar bugs, sugerir mejoras o discutir tareas.

### Plantilla de issue para bugs

```markdown
## Descripción del bug
Descripción clara y concisa del problema.

## Pasos para reproducir
1. Ir a '...'
2. Hacer clic en '...'
3. Ver el error

## Comportamiento esperado
Lo que esperabas que ocurriera.

## Capturas de pantalla
Si aplica, agrega capturas.

## Entorno
- OS: [Windows 11]
- Navegador: [Chrome 120]
- Versión: [2.1.0]

## Información adicional
Cualquier contexto adicional.
```

### Etiquetas comunes

| Etiqueta | Uso | Color |
|----------|-----|-------|
| `bug` | Reporte de error | :red_circle: |
| `enhancement` | Mejora o nueva funcionalidad | :blue_circle: |
| `documentation` | Cambios en documentación | :large_blue_diamond: |
| `good first issue` | Ideal para nuevos contribuidores | :purple_circle: |
| `help wanted` | Se necesita ayuda | :green_circle: |
| `question` | Pregunta o duda | :large_orange_diamond: |

## :material-bell-outline: Notificaciones y menciones

```markdown
# Mencionar a un usuario
@usuario

# Mencionar a un equipo
@equipo/desarrollo

# Referenciar un issue
#123

# Referenciar un PR
PR#456

# Cerrar issue automáticamente con un commit o PR
Closes #123
Fixes #456
Resolves #789
```

## :material-shield-key-outline: Protección de ramas

En GitHub puedes proteger ramas importantes (como `main`):

| Configuración | Descripción |
|---------------|-------------|
| **Require pull request reviews** | Requiere aprobaciones antes de fusionar |
| **Require status checks** | Requiere que los tests pasen |
| **Require signed commits** | Requiere commits firmados |
| **Include administrators** | Aplica las reglas también a admins |
| **Restrict who can push** | Limita quién puede hacer push directo |

!!! example "Configuración recomendada para main"
    - :material-check: Requiere 1-2 aprobaciones
    - :material-check: Requiere que los CI checks pasen
    - :material-check: Bloquea force push
    - :material-check: Bloquea eliminación

## :material-account-multiple-outline: Equipos y permisos

### Roles en un repositorio

| Rol | Permisos |
|-----|----------|
| **Owner** | Control total, transferir propiedad |
| **Maintainer** | Gestionar issues, PRs, releases |
| **Developer** | Push directo a ramas asignadas |
| **Contributor** | Abrir issues y PRs |

### Configurar acceso en equipo

```bash
# Ejemplo de CODEOWNERS
# Todos los miembros del equipo @equipo/dev son revisores
* @equipo/dev

# Solo @alice es dueña de la documentación
/docs/* @alice

# El equipo de seguridad revisa archivos críticos
/auth/* @equipo/security
```

## :material-source-branch-sync: GitHub Actions básico

GitHub Actions permite automatizar workflows con archivos YAML en `.github/workflows/`.

### Ejemplo: tests automáticos

```yaml
name: Tests

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout código
      uses: actions/checkout@v3
    
    - name: Configurar Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.11'
    
    - name: Instalar dependencias
      run: |
        pip install -r requirements.txt
    
    - name: Ejecutar tests
      run: |
        pytest
```

!!! tip "Aprende más"
    La documentación oficial de GitHub Actions es excelente: [docs.github.com/actions](https://docs.github.com/es/actions)

## :material-tools: Herramientas útiles

| Herramienta | Función | Costo |
|-------------|---------|-------|
| [GitHub Desktop](https://desktop.github.com/) | Cliente gráfico para Git | Gratis |
| [GitKraken](https://www.gitkraken.com/) | Cliente gráfico avanzado | Freemium |
| [Sourcetree](https://www.sourcetreeapp.com/) | Cliente gráfico gratuito | Gratis |
| [gh CLI](https://cli.github.com/) | Línea de comandos de GitHub | Gratis |
| [VS Code](https://code.visualstudio.com/) | Editor con integración Git | Gratis |

## :material-chart-line: Métricas y actividad

GitHub proporciona información útil en el perfil:

- :material-check: **Contributions graph**: actividad del último año.
- :material-check: **Pull requests**: PRs abiertos y mergeados.
- :material-check: **Issues**: participación en discusiones.
- :material-check: **Stars**: proyectos destacados.
- :material-check: **README profile**: presentación personal.

## :material-checkbox-marked-outline: Checklist del colaborador

Antes de contribuir a un proyecto:

- :material-check: Lee el `README.md` y el `CONTRIBUTING.md`.
- :material-check: Revisa las issues abiertas y los PRs en curso.
- :material-check: Busca issues marcadas como `good first issue`.
- :material-check: Discute cambios grandes antes de implementar.
- :material-check: Sigue las convenciones del proyecto.
- :material-check: Sé paciente y respetuoso en las discusiones.

---

!!! quote "Filosofía de colaboración"
    *"La mejor forma de aprender es contribuir. La mejor forma de contribuir es colaborar."*

[Ver información del manual :material-arrow-right:](../about.md){ .md-button .md-button--primary }
