---
title: Comandos esenciales
summary: Los comandos más utilizados en Git para el día a día.
date: 2026-06-20
---

# :material-console: Comandos esenciales de Git

En esta sección aprenderás los comandos más usados de Git para tu día a día como desarrollador.

## :material-folder-plus: Iniciar un repositorio

### Crear un repositorio nuevo

```bash
# Inicializa un repositorio Git en el directorio actual
git init
```

### Clonar un repositorio existente

```bash
# Clona un repositorio desde una URL
git clone https://github.com/usuario/proyecto.git

# Clona en una carpeta específica
git clone https://github.com/usuario/proyecto.git mi-carpeta
```

## :material-format-list-checks: Comandos básicos

A continuación se muestra una tabla con los comandos más utilizados en Git:

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `git status` | Muestra el estado de los archivos | `git status` |
| `git add` | Añade archivos al staging area | `git add archivo.txt` |
| `git commit` | Confirma cambios en el repositorio | `git commit -m "mensaje"` |
| `git log` | Muestra el historial de commits | `git log --oneline` |
| `git diff` | Muestra los cambios sin guardar | `git diff archivo.txt` |
| `git push` | Envía cambios al remoto | `git push origin main` |
| `git pull` | Trae cambios del remoto | `git pull origin main` |
| `git branch` | Lista o crea ramas | `git branch nueva-rama` |
| `git checkout` | Cambia de rama o archivo | `git checkout main` |
| `git merge` | Fusiona ramas | `git merge feature` |

## :material-file-plus: Agregar y confirmar cambios

### Agregar archivos al staging

=== "Un archivo"

    ```bash
    git add archivo.txt
    ```

=== "Múltiples archivos"

    ```bash
    git add archivo1.txt archivo2.txt
    ```

=== "Todos los archivos"

    ```bash
    git add .
    ```

=== "Por patrón"

    ```bash
    git add *.md
    git add docs/
    ```

### Confirmar los cambios

```bash
# Commit con mensaje corto
git commit -m "Agrega funcionalidad de login"

# Commit con mensaje extendido (abre el editor)
git commit

# Commit añadiendo todo lo modificado
git commit -am "Corrige bugs menores"
```

!!! tip "Buenas prácticas para mensajes de commit"
    - Usa el modo imperativo: "Agrega", "Corrige", "Actualiza".
    - Sé breve pero descriptivo (máx. 72 caracteres en la primera línea).
    - Detalla el por qué del cambio en el cuerpo del mensaje.

## :material-history: Ver el historial

```bash
# Historial completo
git log

# Historial resumido (una línea por commit)
git log --oneline

# Historial gráfico de ramas
git log --graph --oneline --all

# Últimos 5 commits
git log -5
```

??? example "Ejemplo de salida de git log"
    ```
    commit a1b2c3d4 (HEAD -> main, origin/main)
    Author: Estudiante <estudiante@correo.com>
    Date:   Fri Jun 20 10:30:00 2026 -0500
    
        Agrega documentación con MkDocs
    
    commit e5f6g7h8
    Author: Estudiante <estudiante@correo.com>
    Date:   Thu Jun 19 14:20:00 2026 -0500
    
        Configuración inicial del proyecto
    ```

## :material-undo: Deshacer cambios

!!! warning "Precaución"
    Algunos de estos comandos pueden eliminar tu trabajo. Úsalos con cuidado.

=== "Descartar cambios locales"

    ```bash
    # Descarta cambios en un archivo
    git checkout -- archivo.txt
    
    # Descarta todos los cambios locales
    git checkout -- .
    ```

=== "Sacar del staging"

    ```bash
    # Quita un archivo del staging
    git reset HEAD archivo.txt
    
    # Quita todos los archivos del staging
    git reset HEAD
    ```

=== "Deshacer un commit"

    ```bash
    # Deshace el último commit, mantiene los cambios
    git reset --soft HEAD~1
    
    # Deshace el último commit, descarta los cambios
    git reset --hard HEAD~1
    ```

## :material-server-network: Trabajar con repositorios remotos

### Conectar con un remoto

```bash
# Agrega un repositorio remoto
git remote add origin https://github.com/usuario/proyecto.git

# Lista los remotos
git remote -v

# Cambia la URL del remoto
git remote set-url origin nueva-url
```

### Enviar y recibir cambios

```bash
# Envía la rama actual al remoto
git push

# Envía y establece upstream
git push -u origin main

# Trae cambios del remoto
git pull origin main

# Trae cambios sin fusionar
git fetch origin
```

## :material-tag: Etiquetas (tags)

Las etiquetas son útiles para marcar versiones específicas (ej: v1.0.0).

```bash
# Crear un tag
git tag v1.0.0

# Crear un tag con mensaje
git tag -a v1.0.0 -m "Primera versión estable"

# Listar tags
git tag

# Enviar tags al remoto
git push origin --tags
```

## :material-help-circle-outline: Comandos de ayuda

```bash
# Ayuda general
git help

# Ayuda de un comando específico
git help commit
git commit --help

# Versión de Git
git --version
```

## :material-lightbulb-on: Tabla de aliases útiles

Puedes crear aliases para comandos frecuentes:

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.lg "log --oneline --graph --all"
```

Ahora puedes usar `git st` en lugar de `git status`.

---

!!! success "¡Sigue avanzando!"
    Continúa con la sección de [Flujo de trabajo](flujo.md) para ver cómo combinar todos estos comandos en proyectos reales.

[:material-arrow-left: Volver a introducción](introduccion.md){ .md-button }
[Continuar al flujo de trabajo :material-arrow-right:](flujo.md){ .md-button .md-button--primary }
