---
title: Ramas y Merges
summary: Trabajo avanzado con ramas, merges y rebase.
date: 2026-06-20
---

# :material-source-branch: Ramas y Merges

Las ramas son una de las características más poderosas de Git. Permiten trabajar en funcionalidades de forma aislada sin afectar la línea principal de desarrollo.

## :material-creation: Crear y gestionar ramas

### Comandos básicos

```bash
# Listar todas las ramas locales
git branch

# Listar todas las ramas (locales y remotas)
git branch -a

# Crear una nueva rama
git branch nombre-rama

# Cambiar a una rama existente
git checkout nombre-rama

# Crear y cambiar a una nueva rama (atajo)
git checkout -b nombre-rama

# Renombrar la rama actual
git branch -m nuevo-nombre

# Eliminar una rama local
git branch -d nombre-rama

# Forzar eliminación de rama con cambios sin fusionar
git branch -D nombre-rama
```

### Convenciones de nombres

| Prefijo | Uso | Ejemplo |
|---------|-----|---------|
| `feature/` | Nueva funcionalidad | `feature/login-usuario` |
| `bugfix/` | Corrección de errores | `bugfix/error-404` |
| `hotfix/` | Corrección urgente | `hotfix/security-issue` |
| `release/` | Preparación de release | `release/v2.0.0` |
| `chore/` | Tareas de mantenimiento | `chore/update-deps` |
| `docs/` | Cambios en documentación | `docs/update-readme` |

!!! tip "Recomendación"
    Usa prefijos consistentes para identificar rápidamente el propósito de cada rama.

## :material-vector-combine: Merges

### Tipos de merge

=== "Fast-forward"

    Ocurre cuando la rama destino no tiene nuevos commits desde que se creó la rama a fusionar.
    
    ```bash
    # Estás en main y haces:
    git merge feature/login
    ```
    
    Git simplemente "avanza" el puntero a la rama feature/login.

=== "Three-way merge (Recursive)"

    Ocurre cuando ambas ramas han tenido nuevos commits divergentes.
    
    Git crea un nuevo commit de merge con dos padres.

=== "Squash"

    Combina todos los commits de la rama en uno solo.
    
    ```bash
    git merge --squash feature/login
    ```
    
    ??? info "¿Cuándo usar squash?"
        - Para limpiar el historial antes de mergear.
        - En features pequeñas con muchos commits intermedios.
        - Cuando no quieres preservar la historia de la rama.

## :material-compare-horizontal: Resolución de conflictos

### Escenario común

```bash
# Estás en main y quieres fusionar feature/login
git checkout main
git merge feature/login
```

### Si hay conflictos

Git mostrará un mensaje como:

```
Auto-merging archivo.txt
CONFLICT (content): Merge conflict in archivo.txt
Automatic merge failed; fix conflicts and then commit the result.
```

### Pasos para resolver

=== "Paso 1: Ver los conflictos"

    ```bash
    git status
    git diff
    ```

=== "Paso 2: Editar archivos"

    Abre los archivos marcados con `<<<<<<<` y resuelve manualmente.

=== "Paso 3: Marcar como resueltos"

    ```bash
    git add archivo-resuelto.txt
    ```

=== "Paso 4: Finalizar"

    ```bash
    git commit -m "Resuelve conflictos de merge"
    ```

### Herramientas de merge

```bash
# Usar una herramienta visual de merge
git mergetool
```

!!! warning "Cuidado"
    No uses `git commit` con mensaje de merge automático si has resuelto conflictos manualmente. Siempre verifica que el código funcione antes de hacer commit.

## :material-call-split: Rebase

**Rebase** es una alternativa al merge. Reaplica tus commits sobre la punta de otra rama, creando un historial lineal.

### Merge vs Rebase

=== "Merge"

    ```bash
    git checkout feature/login
    git merge main
    ```
    
    **Ventajas:**
    
    - Preserva el historial completo.
    - No reescribe commits.
    - Más seguro para ramas compartidas.
    
    **Desventajas:**
    
    - Historial más complejo.
    - Commits de merge adicionales.

=== "Rebase"

    ```bash
    git checkout feature/login
    git rebase main
    ```
    
    **Ventajas:**
    
    - Historial lineal más limpio.
    - Facilita la lectura del log.
    
    **Desventajas:**
    
    - Reescribe el historial.
    - ⚠️ Peligroso en ramas compartidas.

!!! danger "Regla de oro del rebase"
    **Nunca uses `git rebase` en ramas que ya están en el remoto y que otros están usando.** Esto causará problemas graves a tus compañeros.

### Cuándo usar rebase vs merge

| Situación | Recomendación |
|-----------|---------------|
| Rama local personal | Rebase |
| Antes de abrir PR | Rebase interactivo |
| Rama compartida | Merge |
| Release a main | Merge (no-ff) |

### Rebase interactivo

```bash
# Rebase interactivo de los últimos 3 commits
git rebase -i HEAD~3
```

Abre un editor donde puedes:

- `pick` - Mantener el commit
- `reword` - Cambiar el mensaje
- `edit` - Modificar el commit
- `squash` - Combinar con el anterior
- `drop` - Eliminar el commit

## :material-format-list-bulleted: Cherry-pick

**Cherry-pick** aplica un commit específico de otra rama a tu rama actual.

```bash
# Aplicar un commit por hash
git cherry-pick abc1234

# Aplicar varios commits
git cherry-pick abc1234 def5678

# Aplicar un rango de commits
git cherry-pick abc1234..def5678
```

!!! example "Caso de uso"
    Se corrigió un bug crítico en la rama `develop` y necesitas el mismo fix en `main` sin fusionar todas las nuevas funcionalidades. Usa cherry-pick.

## :material-tag-outline: Stash

`git stash` guarda temporalmente los cambios sin confirmar para trabajar en otra cosa.

```bash
# Guardar cambios actuales
git stash

# Guardar con mensaje
git stash save "Trabajo en progreso en login"

# Listar stashes
git stash list

# Recuperar el último stash
git stash pop

# Recuperar un stash específico
git stash apply stash@{2}

# Eliminar un stash
git stash drop stash@{0}
```

## :material-cog-play-outline: Workflow completo con ramas

```bash
# 1. Crear una rama para nueva funcionalidad
git checkout -b feature/login main

# 2. Hacer cambios y commits
git add .
git commit -m "Implementa formulario de login"

# 3. Mantener la rama actualizada con main
git fetch origin
git rebase origin/main

# 4. Subir la rama al remoto
git push -u origin feature/login

# 5. Abrir un Pull Request

# 6. Después de la aprobación, mergear y limpiar
git checkout main
git pull origin main
git branch -d feature/login
git push origin --delete feature/login
```

## :material-bug: Recuperarse de errores

!!! danger "Situación de emergencia"
    ¿Cometiste un error en un rebase o merge? No entres en pánico.

=== "Recuperar un commit perdido"

    ```bash
    # Ver todos los commits, incluso los "huérfanos"
    git reflog
    
    # Restaurar un commit específico
    git reset --hard abc1234
    ```

=== "Cancelar un rebase en curso"

    ```bash
    git rebase --abort
    ```

=== "Cancelar un merge en curso"

    ```bash
    git merge --abort
    ```

=== "Volver a un commit anterior"

    ```bash
    # Temporalmente
    git checkout abc1234
    
    # Permanentemente
    git reset --hard abc1234
    ```

---

!!! example "Practica lo aprendido"
    Elige un proyecto personal, crea una rama, haz algunos cambios, experimenta con merge y rebase. La práctica es la mejor forma de dominar las ramas.

[Continuar a colaboración :material-arrow-right:](colaboracion.md){ .md-button .md-button--primary }
