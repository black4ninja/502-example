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

Este proyecto sigue [Conventional Commits](https://www.conventionalcommits.org/).

Para detalles completos, consulta [CONTRIBUTING.md](CONTRIBUTING.md#estándares-de-commits).

**Formato básico:**
```
<type>[optional scope]: <description>
```

**Tipos principales:** `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

**Ejemplos:**
```bash
git commit -m "feat: add user authentication"
git commit -m "fix(api): resolve timeout error"
git commit -m "docs: update installation guide"
```

## Estrategia de Branching

Este proyecto utiliza **Git Flow**.

Para detalles completos, consulta [CONTRIBUTING.md](CONTRIBUTING.md#estrategia-de-branching).

**Branches principales:**
- `main` - Producción
- `develop` - Integración

**Branches de soporte:**
- `feature/<name>` - Nuevas funcionalidades
- `bugfix/<name>` - Corrección de bugs
- `hotfix/<name>` - Fixes urgentes en producción
- `release/<version>` - Preparación de releases

**Workflow básico:**
```bash
git checkout develop
git checkout -b feature/my-feature
git commit -m "feat: implement my feature"
git push origin feature/my-feature
# Crear Pull Request
```

## Contribución

¿Quieres contribuir? ¡Genial! Lee nuestra [Guía de Contribución](CONTRIBUTING.md) para conocer:

- Cómo reportar bugs
- Estándares de código y commits
- Proceso de Pull Requests
- Estrategia de branching completa

**Quick start:**
1. Fork el proyecto
2. Crear branch (`git checkout -b feature/amazing-feature`)
3. Commit cambios siguiendo [Conventional Commits](CONTRIBUTING.md#estándares-de-commits)
4. Push (`git push origin feature/amazing-feature`)
5. Abrir [Pull Request](.github/pull_request_template.md)

## Licencia

[Especificar licencia]

## Contacto

[Información de contacto del equipo]
