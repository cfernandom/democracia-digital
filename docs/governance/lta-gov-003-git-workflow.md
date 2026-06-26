---
title: "Flujo de Contribuciones y Pull Requests"

document_id: "LTA-GOV-003"
version: "0.1.0"
status: "draft"
document_type: "GOV"
document_subtype: "process"
classification: "public"
language: "es"

authors:
  - "Equipo fundador"

owner: "Gobernanza Técnica"

created: "2026-06-25"
updated: "2026-06-25"

review_cycle: "annual"

tags:
  - git
  - github
  - pull-request
  - collaboration

license: "CC BY 4.0"

approval:
  status: "pending"

related_documents:
  - id: "LTA-GOV-001"
    relation: "references"
  - id: "LTA-GOV-002"
    relation: "references"
  - id: "LTA-GOV-004"
    relation: "references"
---

# Flujo de Contribuciones y Pull Requests

## 1. Propósito

Definir el proceso mediante el cual colaboradores internos y externos pueden proponer cambios al repositorio.

---

## 2. Principios

Todo cambio debe cumplir:

* trazabilidad.
* revisión.
* documentación.
* responsabilidad.

Ningún cambio significativo deberá incorporarse directamente a ramas protegidas.

---

## 3. Flujo general

1. Issue
2. Branch
3. Commits
4. Pull Request
5. Review
6. Merge

---

## 4. Creación de ramas

Formato:

```
<scope>/<descripcion>
```

El componente `<scope>` representa el dominio o área del trabajo, y debe coincidir con uno de los scopes definidos en LTA-GOV-002 §4.

Scopes válidos para ramas:

| Scope        | Uso                                         |
| ------------ | ------------------------------------------- |
| governance   | Gobernanza institucional y procesos         |
| research     | Investigaciones, estudios y publicaciones   |
| legal        | Análisis jurídico y normativa               |
| policy       | Propuestas de política pública              |
| technical    | Software, arquitectura e infraestructura    |
| data         | Datos, modelos y pipelines                  |
| community    | Comunidad, difusión y participación         |

La rama representa el **contexto del trabajo**. Los commits dentro de esa rama representan la **naturaleza del cambio** y deben seguir LTA-GOV-002 para tipo y descripción.

Ejemplos:

```
research/disinformation-analysis

technical/claim-verifier-api

governance/update-document-standard

legal/regulatory-analysis
```

---

## 5. Pull Request

Todo PR deberá incluir:

* descripción del cambio.
* relación con Issue.
* impacto esperado.
* pruebas realizadas.
* documentación actualizada.

Ejemplo:

```
Closes #25
```

---

## 6. Revisión requerida

### Documentación

Mínimo:

* 1 revisor.

### Investigación pública

Mínimo:

* 2 revisores.

Debe incluir revisión metodológica.

### Código crítico

Mínimo:

* 2 revisores técnicos.

---

## 7. Criterios de rechazo

Un PR podrá rechazarse cuando:

* no tenga documentación.
* no tenga evidencia suficiente.
* introduzca riesgos legales.
* incumpla principios institucionales.

---

## 8. Estrategia de Integración de Cambios

### Estrategia seleccionada

El repositorio utiliza **Squash Merge** como estrategia de integración para todos los Pull Requests.

```
main ← squash merge ← feature branch
```

### Justificación

La estrategia squash merge fue seleccionada por las siguientes razones:

* **Historial limpio**: la rama principal (`main`) contiene únicamente commits que representan cambios completos y atómicos, sin ruido de iteraciones intermedias.
* **Trazabilidad**: cada commit en `main` corresponde exactamente a un Pull Request, facilitando la auditoría y navegación del historial.
* **Reversibilidad**: un cambio puede revertirse con un único commit, sin necesidad de rastrear múltiples commits intermedios.
* **Enfoque documental**: el repositorio prioriza la evolución de documentos institucionales; los commits intermedios reflejan iteraciones de trabajo, no decisiones finales.
* **Cumplimiento con LTA-GOV-002**: el commit resultante sigue las convenciones definidas, representando la totalidad del cambio aprobado.

### Efecto sobre el historial

Los Pull Requests aprobados generan **un único commit** en la rama `main`. Los commits individuales de la rama de trabajo se comprimen (squash) en ese commit final.

#### Antes del merge

```
main
 |
 PR #15
 |
 ├── fix(docs): correct typo in section 3
 ├── docs(governance): add reviewer requirements table
 └── docs(governance): update related documents list
```

#### Después del merge

```
main
 |
 └── docs(governance): update contribution workflow
```

El commit final en `main` consolida el propósito completo del Pull Request. Los commits intermedios permanecen visibles en la rama de origen y en el Pull Request cerrado, pero no forman parte del historial principal.

### Reglas

1. Todo Pull Request aprobado será integrado mediante **squash merge**.
2. El mensaje del commit resultante deberá cumplir **LTA-GOV-002** (Convenciones de Commits).
3. El mensaje del commit final debe representar el cambio completo realizado, no una iteración individual.
4. Los commits intermedios del Pull Request no se consideran parte del historial principal de `main`.
5. El autor del Pull Request es responsable de que el mensaje del commit squash refleje fielmente el cambio aprobado.
6. Quien realiza el merge es responsable de verificar que el mensaje cumpla las convenciones antes de confirmar la integración.

### Responsabilidades durante la integración

| Rol                    | Responsabilidad                                                                 |
| ---------------------- | -------------------------------------------------------------------------------- |
| Autor del PR           | Proponer un mensaje de commit squash que cumpla LTA-GOV-002 y describa el cambio |
| Revisor                | Verificar que el mensaje propuesto representa adecuadamente el cambio aprobado   |
| Responsable del merge  | Ejecutar el squash merge confirmando el mensaje final                           |

---

## Historial de cambios

| Versión | Fecha      | Descripción      |
| ------- | ---------- | ---------------- |
| 0.1.0   | 2026-06-25 | Creación inicial |

---
