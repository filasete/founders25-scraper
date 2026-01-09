# Estrategia de Versionado Semántico

## Formato: MAJOR.MINOR.PATCH

### Definiciones

**MAJOR (X.0.0):** Cambios incompatibles / breaking changes
- Ejemplo: Cambiar estructura de datos que rompe scripts existentes
- Cambiar API de funciones principales

**MINOR (0.X.0):** Nuevas funcionalidades compatibles
- Ejemplo: Agregar nuevo tipo de scraper
- Agregar soporte para nuevo sitio web
- Nuevas opciones de configuración

**PATCH (0.0.X):** Correcciones de bugs
- Ejemplo: Arreglar error en parsing HTML
- Mejorar rendimiento sin cambiar API
- Actualizar dependencias (sin breaking changes)

---

## Ejemplos Concretos

### PATCH: v0.1.1
```
- Fix: Corregir bug en parseo de URLs con caracteres especiales
- Fix: Actualizar beautifulsoup4 a 4.12.3
- Improvement: Optimizar velocidad de descargas
```

### MINOR: v0.2.0
```
- Feature: Agregar soporte para scraping con Selenium
- Feature: Nuevo método de autenticación
- Feature: Exportar datos a Excel (.xlsx)
- Improvement: Interface más amigable
```

### MAJOR: v1.0.0
```
- BREAKING: Cambiar estructura de config.json
- BREAKING: Nueva API de funciones
- BREAKING: Cambiar nombres de métodos principales
```

---

## Política de Releases

### 1. Draft Release (Prerelease)
```
Tag: v0.1.0-beta.1
Estado: Draft en GitHub
Descripción: Pre-release para testing
```

### 2. Release Oficial
```
Tag: v0.1.0
Estado: Release completo
Descripción: Lista para producción
```

---

## Naming Convention para Tags

```
v0.1.0          # Release estable
v0.1.0-beta.1   # Beta/prerelease
v0.1.0-rc.1     # Release candidate
v0.1.0-alpha.1  # Alpha testing
```

---

## Generación de CHANGELOG a partir de Commits

### Formato de Commits Semánticos

```
feat(scraper): agregar soporte para Facebook
fix(parser): corregir bug en URLs especiales
docs: actualizar README
style: formatear código
refactor: reorganizar estructura
perf: optimizar búsquedas
test: agregar tests unitarios
chore: actualizar dependencias
```

### Estructura CHANGELOG.md

```markdown
## [0.2.0] - 2026-02-15

### Added
- feat(scraper): Soporte para LinkedIn
- feat(config): Nueva opción proxy support

### Fixed
- fix(parser): Bug en caracteres Unicode
- fix(api): Error en conexiones concurrentes

### Changed
- refactor: Reorganizar estructura de carpetas

### Removed
- Eliminado soporte para Python 3.7

### Security
- Actualizar requests a versión segura

### Known Issues
- Performance lenta en proxies HTTP
```

---

## Criterios de Release Notes

### 1. Resumen Ejecutivo (2-3 líneas)
```
Versión con soporte para múltiples plataformas.
Mejoras significativas en rendimiento y estabilidad.
```

### 2. Breaking Changes (si aplica)
```
⚠️ BREAKING CHANGES:
- config.json cambió de estructura JSON a YAML
- Función scrape() ahora retorna dict en lugar de list
```

### 3. Nuevas Funcionalidades
```
✨ Features:
- Scraping simultáneo (multithreading)
- Exportar a Excel
- Autenticación OAuth2
```

### 4. Correcciones
```
🐛 Bug Fixes:
- Corregido timeout en conexiones lenta
- Unicode en caracteres especiales
```

### 5. Mejoras
```
⚡ Improvements:
- +50% velocidad en parsing
- Reducción uso memoria
```

### 6. Dependencias
```
📦 Dependencies:
- beautifulsoup4: 4.12.0 → 4.12.3
- requests: 2.31.0 → 2.32.0
```

### 7. Riesgos Conocidos
```
⚠️ Known Issues & Risks:
- Puede fallar con proxies HTTP
- Requiere Python 3.8+
- No soporta Windows XP
```

### 8. Agradecimientos
```
👏 Gracias a:
- @usuario1 por reportar bug #45
- Comunidad por feedback
```

---

## Flujo de Release

```
1. Desarrollo en rama feature
2. Merge a master cuando está listo
3. Crear tag: git tag v0.2.0
4. Push tag: git push origin v0.2.0
5. GitHub crea Draft Release automáticamente
6. Editar Draft con Release Notes
7. Publicar como Release oficial
```

---

## Ejemplos de Decisión

| Cambio | Tipo | Razón |
|--------|------|-------|
| Arreglar bug URL | PATCH | Corrección sin API change |
| Nuevo método scrape_linkedin() | MINOR | Nueva funcionalidad compatible |
| Cambiar config.json a .yaml | MAJOR | Breaking change |
| Actualizar beautifulsoup4 | PATCH | Dependencia sin breaking changes |
| Soporte para async/await | MINOR | Nueva forma de uso opcional |
| Eliminar método antiguo | MAJOR | Breaking change |

---

# 📋 RELEASE CHECKLIST OPERATIVO

## PRE-TAG (Antes de crear el tag)

### Code Quality
- [ ] Todos los tests pasan
- [ ] Sin errores de linting
- [ ] Código revisado
- [ ] No hay warnings

### Documentation
- [ ] README.md actualizado
- [ ] CHANGELOG.md completado
- [ ] Docstrings en funciones nuevas

### Dependencies
- [ ] requirements.txt actualizado
- [ ] Sin vulnerabilidades

### Version Update
- [ ] Versión actualizada en archivos relevantes
- [ ] Versión coincide en CHANGELOG.md

### Final Check
- [ ] Branch master limpio
- [ ] Último commit es el definitivo
- [ ] Todos los tests pasaron

---

## TAG (Crear y pushear tag)

### Crear Tag
```bash
# Tag anotado (recomendado)
git tag -a v0.1.0 -m "Release version 0.1.0"
```

### Verificar Tag
```bash
git show v0.1.0
```

### Pushear a GitHub
```bash
git push origin v0.1.0
```

### Verificar en GitHub
- [ ] Tag visible en GitHub
- [ ] Tag apunta al commit correcto

---

## POST-RELEASE (Después de publicar)

### GitHub Release
- [ ] Draft Release creado automáticamente
- [ ] Release Notes completadas:
  - [ ] Resumen ejecutivo
  - [ ] Breaking changes
  - [ ] Nuevas features
  - [ ] Bug fixes
  - [ ] Known issues
- [ ] Release publicada como oficial
- [ ] Marcada como "Latest release"

### Monitoreo
- [ ] Monitor errores en primeras 24h
- [ ] Responder issues relacionados
- [ ] Si hay bugs críticos: hotfix release

---

## Comandos Útiles

```bash
# Ver todos los tags
git tag

# Información del tag
git show v0.1.0

# Borrar tag local
git tag -d v0.1.0

# Borrar tag remoto
git push origin --delete v0.1.0

# Cambiar tag a otro commit
git tag -f v0.1.0 <commit-hash>
git push origin v0.1.0 -f
```
