# 502 Example Project

## Descripción
Proyecto de desarrollo de software con estándares profesionales de control de versiones y colaboración.

## Tabla de Contenidos
- [Instalación](#instalación)
- [Uso](#uso)
- [Estándares de Commits](#estándares-de-commits)
- [Estrategia de Branching](#estrategia-de-branching)
- [Contribución](#contribución)

## Instalación

```bash
# Clonar el repositorio
git clone <repository-url>
cd 502-example

# Instalar dependencias (ajustar según el proyecto)
npm install
```

## Uso

```bash
# Instrucciones para ejecutar el proyecto
npm start
```

## Estándares de Commits

Este proyecto sigue la especificación [Conventional Commits](https://www.conventionalcommits.org/).

### Formato

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Types

- **feat**: Nueva funcionalidad
- **fix**: Corrección de bugs
- **docs**: Cambios en documentación
- **style**: Cambios de formato (espacios, puntos y coma, etc.)
- **refactor**: Refactorización de código (no añade features ni corrige bugs)
- **perf**: Mejoras de rendimiento
- **test**: Añadir o modificar tests
- **build**: Cambios en el sistema de build o dependencias
- **ci**: Cambios en configuración de CI/CD
- **chore**: Otras tareas de mantenimiento

### Ejemplos

```bash
# Feature simple
git commit -m "feat: add user authentication"

# Fix con scope
git commit -m "fix(api): resolve null pointer exception in user service"

# Con body y breaking change
git commit -m "feat!: redesign database schema

BREAKING CHANGE: users table now requires email field"

# Refactorización
git commit -m "refactor(utils): simplify date formatting logic"

# Documentación
git commit -m "docs: update API documentation"
```

### Reglas

1. Los commits deben estar en tiempo presente imperativo
2. La descripción debe ser concisa (máx. 72 caracteres)
3. El body debe explicar el "qué" y el "por qué", no el "cómo"
4. Breaking changes deben indicarse con `!` o `BREAKING CHANGE:` en el footer

## Estrategia de Branching

Este proyecto utiliza **Git Flow** como estrategia de branching.

### Branches Principales

- **`main`**: Producción. Código estable y desplegable
- **`develop`**: Integración. Última versión en desarrollo

### Branches de Soporte

#### Feature Branches
- **Naming**: `feature/<feature-name>`
- **Branch desde**: `develop`
- **Merge a**: `develop`
- **Propósito**: Desarrollo de nuevas funcionalidades

```bash
# Crear feature branch
git checkout develop
git checkout -b feature/user-login

# Finalizar feature
git checkout develop
git merge feature/user-login
git branch -d feature/user-login
```

#### Release Branches
- **Naming**: `release/<version>`
- **Branch desde**: `develop`
- **Merge a**: `main` y `develop`
- **Propósito**: Preparación de nueva versión

```bash
# Crear release branch
git checkout develop
git checkout -b release/1.0.0

# Finalizar release
git checkout main
git merge release/1.0.0
git tag -a v1.0.0 -m "Release version 1.0.0"
git checkout develop
git merge release/1.0.0
git branch -d release/1.0.0
```

#### Hotfix Branches
- **Naming**: `hotfix/<issue-name>`
- **Branch desde**: `main`
- **Merge a**: `main` y `develop`
- **Propósito**: Correcciones urgentes en producción

```bash
# Crear hotfix branch
git checkout main
git checkout -b hotfix/critical-bug

# Finalizar hotfix
git checkout main
git merge hotfix/critical-bug
git tag -a v1.0.1 -m "Hotfix version 1.0.1"
git checkout develop
git merge hotfix/critical-bug
git branch -d hotfix/critical-bug
```

#### Bugfix Branches
- **Naming**: `bugfix/<bug-name>`
- **Branch desde**: `develop`
- **Merge a**: `develop`
- **Propósito**: Corrección de bugs en desarrollo

```bash
git checkout develop
git checkout -b bugfix/fix-validation-error
```

### Reglas de Branching

1. Nunca hacer commit directo a `main` o `develop`
2. Usar Pull Requests para todos los merges
3. Eliminar branches después del merge
4. Mantener `develop` siempre funcional
5. Tagear todas las releases en `main`

### Workflow Típico

```bash
# 1. Actualizar develop
git checkout develop
git pull origin develop

# 2. Crear feature branch
git checkout -b feature/new-feature

# 3. Hacer commits siguiendo Conventional Commits
git add .
git commit -m "feat: add new feature"

# 4. Push y crear Pull Request
git push origin feature/new-feature

# 5. Después del code review y aprobación, merge a develop
# 6. Eliminar feature branch
```

## Contribución

1. Fork el proyecto
2. Crear feature branch (`git checkout -b feature/amazing-feature`)
3. Commit cambios siguiendo Conventional Commits
4. Push al branch (`git push origin feature/amazing-feature`)
5. Abrir Pull Request

## Licencia

[Especificar licencia]

## Contacto

[Información de contacto del equipo]
