# Guía de Contribución

¡Gracias por tu interés en contribuir a este proyecto! Esta guía te ayudará a entender nuestros estándares y procesos.

## Tabla de Contenidos

- [Código de Conducta](#código-de-conducta)
- [¿Cómo puedo contribuir?](#cómo-puedo-contribuir)
- [Estándares de Commits](#estándares-de-commits)
- [Estrategia de Branching](#estrategia-de-branching)
- [Pull Requests](#pull-requests)
- [Estándares de Código](#estándares-de-código)

## Código de Conducta

Este proyecto se adhiere a un código de conducta. Al participar, se espera que mantengas un ambiente respetuoso y colaborativo.

## ¿Cómo puedo contribuir?

### Reportar Bugs

- Usa el issue tracker de GitHub
- Describe el bug detalladamente
- Incluye pasos para reproducirlo
- Menciona el entorno (OS, versión, etc.)

### Sugerir Mejoras

- Abre un issue describiendo la mejora
- Explica el caso de uso
- Discute alternativas si es posible

### Contribuir Código

1. Fork el repositorio
2. Crea tu branch siguiendo nuestros estándares
3. Realiza tus cambios
4. Asegúrate que los tests pasen
5. Crea un Pull Request

## Estándares de Commits

Este proyecto sigue la especificación **[Conventional Commits](https://www.conventionalcommits.org/)**.

### Formato

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Types

| Type | Descripción | Ejemplo |
|------|-------------|---------|
| `feat` | Nueva funcionalidad | `feat: add user authentication` |
| `fix` | Corrección de bugs | `fix: resolve null pointer exception` |
| `docs` | Cambios en documentación | `docs: update API documentation` |
| `style` | Formato (espacios, puntos y coma) | `style: format code with prettier` |
| `refactor` | Refactorización sin cambiar funcionalidad | `refactor: simplify validation logic` |
| `perf` | Mejoras de rendimiento | `perf: optimize database queries` |
| `test` | Añadir o modificar tests | `test: add unit tests for auth service` |
| `build` | Sistema de build o dependencias | `build: update webpack configuration` |
| `ci` | Configuración de CI/CD | `ci: add github actions workflow` |
| `chore` | Tareas de mantenimiento | `chore: update dependencies` |

### Scope (Opcional)

El scope especifica el área del código afectada:

```bash
feat(auth): add OAuth2 support
fix(api): handle timeout errors
docs(readme): update installation steps
```

### Breaking Changes

Indica cambios que rompen compatibilidad:

```bash
feat!: redesign API endpoints

BREAKING CHANGE: /api/users endpoint now requires authentication
```

### Ejemplos Completos

```bash
# Feature simple
git commit -m "feat: add password reset functionality"

# Fix con scope
git commit -m "fix(validation): prevent SQL injection in login form"

# Con body explicativo
git commit -m "refactor: restructure user service

- Extract validation logic to separate module
- Improve error handling
- Add comprehensive logging"

# Breaking change
git commit -m "feat!: migrate to API v2

BREAKING CHANGE: Authentication now uses JWT tokens instead of session cookies.
Update your client code to include Authorization header."
```

### Reglas

✅ **Hacer:**
- Usar tiempo presente imperativo ("add" no "added")
- Descripción concisa (máx. 72 caracteres)
- Commits atómicos (un concepto por commit)
- Body explicando "qué" y "por qué", no "cómo"

❌ **No hacer:**
- Commits genéricos ("fix stuff", "updates")
- Mezclar múltiples cambios no relacionados
- Commits con errores de sintaxis o typos

## Estrategia de Branching

Este proyecto utiliza **Git Flow** como estrategia de branching.

### Branches Principales

#### `main`
- Código en producción
- Siempre estable y desplegable
- Solo recibe merges de `release` y `hotfix`
- Cada merge debe tener un tag de versión

#### `develop`
- Branch de integración
- Refleja el estado actual de desarrollo
- Recibe merges de `feature`, `bugfix` y `release`

### Branches de Soporte

#### Feature Branches

**Naming:** `feature/<feature-name>`

```bash
# Crear feature
git checkout develop
git checkout -b feature/user-notifications

# Trabajar en la feature
git add .
git commit -m "feat: add notification system"

# Actualizar con develop
git checkout develop
git pull origin develop
git checkout feature/user-notifications
git merge develop

# Finalizar (via Pull Request)
git push origin feature/user-notifications
```

**Reglas:**
- Branch desde: `develop`
- Merge a: `develop`
- Naming: descriptivo y en kebab-case
- Eliminar después del merge

#### Bugfix Branches

**Naming:** `bugfix/<bug-name>`

```bash
git checkout develop
git checkout -b bugfix/fix-login-validation
```

**Reglas:**
- Branch desde: `develop`
- Merge a: `develop`
- Para bugs encontrados en desarrollo

#### Release Branches

**Naming:** `release/<version>`

```bash
# Crear release
git checkout develop
git checkout -b release/1.2.0

# Bug fixes menores si son necesarios
git commit -m "fix: minor adjustments for release"

# Finalizar release
git checkout main
git merge release/1.2.0
git tag -a v1.2.0 -m "Release version 1.2.0"

git checkout develop
git merge release/1.2.0

git branch -d release/1.2.0
```

**Reglas:**
- Branch desde: `develop`
- Merge a: `main` y `develop`
- Solo bug fixes menores
- Actualizar versión y changelog

#### Hotfix Branches

**Naming:** `hotfix/<issue-name>`

```bash
# Crear hotfix
git checkout main
git checkout -b hotfix/critical-security-fix

# Hacer el fix
git commit -m "fix: patch security vulnerability"

# Merge a main
git checkout main
git merge hotfix/critical-security-fix
git tag -a v1.2.1 -m "Hotfix version 1.2.1"

# Merge a develop
git checkout develop
git merge hotfix/critical-security-fix

git branch -d hotfix/critical-security-fix
```

**Reglas:**
- Branch desde: `main`
- Merge a: `main` y `develop`
- Solo para fixes críticos en producción
- Incrementar patch version

### Naming Conventions

| Branch Type | Pattern | Ejemplo |
|-------------|---------|---------|
| Feature | `feature/<name>` | `feature/add-payment-gateway` |
| Bugfix | `bugfix/<name>` | `bugfix/fix-memory-leak` |
| Hotfix | `hotfix/<name>` | `hotfix/security-patch` |
| Release | `release/<version>` | `release/2.0.0` |

**Reglas generales:**
- Usar kebab-case (lowercase con guiones)
- Nombres descriptivos y concisos
- Sin caracteres especiales excepto guiones

### Workflow Típico

```bash
# 1. Sincronizar develop
git checkout develop
git pull origin develop

# 2. Crear branch
git checkout -b feature/my-new-feature

# 3. Desarrollar y hacer commits
git add .
git commit -m "feat: implement new feature"

# 4. Mantener actualizado con develop
git fetch origin
git merge origin/develop

# 5. Push del branch
git push origin feature/my-new-feature

# 6. Crear Pull Request en GitHub

# 7. Después de code review y aprobación, merge a develop

# 8. Eliminar branch local y remoto
git branch -d feature/my-new-feature
git push origin --delete feature/my-new-feature
```

## Pull Requests

### Antes de Crear un PR

- [ ] Todos los tests pasan
- [ ] Código sigue los estándares del proyecto
- [ ] Documentación actualizada
- [ ] Branch actualizado con base (develop/main)
- [ ] Commits siguen Conventional Commits

### Crear un PR

1. Push tu branch al repositorio remoto
2. Ve a GitHub y crea un Pull Request
3. Completa la plantilla del PR
4. Asigna reviewers apropiados
5. Vincula issues relacionados

### Durante el Review

- Responde a comentarios constructivamente
- Realiza cambios solicitados en commits separados
- No forces push después del review inicial
- Mantén la conversación profesional

### Después del Merge

- Elimina el branch remoto (GitHub puede hacerlo automáticamente)
- Elimina el branch local: `git branch -d <branch-name>`
- Sincroniza tu repositorio local

## Estándares de Código

### General

- Código limpio y legible
- Nombres descriptivos de variables y funciones
- Comentarios solo cuando sea necesario explicar "por qué"
- Evitar código duplicado (DRY principle)
- Funciones pequeñas y con una sola responsabilidad

### Testing

- Escribir tests para nueva funcionalidad
- Mantener cobertura de tests > 80%
- Tests deben ser independientes y reproducibles
- Usar nombres descriptivos para tests

### Documentation

- Documentar APIs públicas
- README actualizado con cambios relevantes
- Comentarios JSDoc/docstrings para funciones complejas

## Versionado

Este proyecto sigue [Semantic Versioning](https://semver.org/):

- **MAJOR** (X.0.0): Cambios incompatibles con versiones anteriores
- **MINOR** (0.X.0): Nueva funcionalidad compatible con versiones anteriores
- **PATCH** (0.0.X): Bug fixes compatibles

## Preguntas

Si tienes preguntas, puedes:
- Abrir un issue con la etiqueta "question"
- Contactar al equipo de mantenimiento
- Revisar la documentación existente

---

¡Gracias por contribuir! 🚀
