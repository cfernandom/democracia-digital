---
title: "Convenciones de Commits"

document_id: "LTA-GOV-002"
version: "0.1.0"
status: "draft"
document_type: "GOV"
document_subtype: "standard"
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
  - commits
  - version-control
  - engineering

license: "CC BY 4.0"

approval:
  status: "pending"

related_documents:
  - id: "LTA-GOV-001"
    relation: "references"
---

# Convenciones de Commits

## 1. Propósito

Este documento establece las convenciones para la creación de commits dentro del repositorio del Laboratorio de Transparencia Algorítmica (LTA).

El objetivo es mantener un historial de cambios claro, trazable y comprensible para colaboradores técnicos y no técnicos.

---

## 2. Formato de commit

Todos los commits deberán seguir la estructura:

```
<type>(<scope>): <description>
```

Ejemplo:

```
docs(governance): add document metadata requirements
```

---

## 3. Tipos permitidos

| Tipo     | Uso                                   |
| -------- | ------------------------------------- |
| feat     | Nueva capacidad funcional o documental |
| fix      | Corrección de errores                 |
| docs     | Creación o modificación de documentación |
| test     | Adición o modificación de pruebas     |
| refactor | Reestructuración sin cambio de comportamiento |
| chore    | Mantenimiento, tooling, configuración |

---

## 4. Scopes permitidos

Los scopes representan el área o dominio afectado por el cambio. Un mismo scope puede recibir cambios de distinto tipo.

Cada scope se corresponde con una etiqueta de área (`area/*`) en el sistema de Issues definido en LTA-GOV-004:

| Scope        | Label correspondiente |
| ------------ | --------------------- |
| governance   | `area/governance`     |
| research     | `area/research`       |
| legal        | `area/legal`          |
| policy       | `area/policy`         |
| technical    | `area/technical`      |
| data         | `area/data`           |
| community    | `area/community`      |

Esta correspondencia permite vincular los cambios en el historial de commits con el trabajo planificado en Issues, manteniendo trazabilidad de extremo a extremo.

### governance

Gobernanza institucional, procesos, estándares y normas internas.

Ejemplo:

```
docs(governance): update approval process
```

---

### research

Investigaciones, publicaciones, estudios y revisiones de literatura.

Ejemplo:

```
docs(research): add misinformation dataset review
```

---

### legal

Análisis jurídico, revisión normativa y dictámenes legales.

Ejemplo:

```
docs(legal): update digital advertising regulation review
```

---

### policy

Propuestas de política pública, recomendaciones regulatorias y documentos de posición.

Ejemplo:

```
docs(policy): draft digital transparency framework
```

---

### technical

Software, arquitectura, infraestructura y especificaciones técnicas.

Ejemplo:

```
feat(technical): implement claim extraction pipeline
```

---

### data

Datos, modelos, pipelines de procesamiento y esquemas.

Ejemplo:

```
fix(data): correct dataset metadata schema
```

---

### community

Lineamientos comunitarios, código de conducta, guías de contribución y outreach.

Ejemplo:

```
docs(community): add contribution guide
```

---

La lista de scopes puede expandirse conforme el proyecto crezca. Para proponer un nuevo scope, debe documentarse en este mismo documento mediante un Pull Request.

## 5. Reglas de descripción

Las descripciones deberán:

* iniciar con verbo en infinitivo.
* ser breves.
* evitar información redundante.

Correcto:

```
docs(governance): add metadata validation rules
```

Incorrecto:

```
docs(governance): changes made to metadata because the document needed more fields
```

---

## 6. Cambios incompatibles (BREAKING CHANGE)

Un commit que rompe compatibilidad con versiones anteriores debe señalizarse explícitamente.

Dos formas equivalentes:

**Notación `!` en el subject:**

```
<type>(<scope>)!: <description>
```

**Footer `BREAKING CHANGE`:**

```
<type>(<scope>): <description>

BREAKING CHANGE: descripción del cambio incompatible
```

En documentos institucionales, un BREAKING CHANGE implica un incremento MAJOR de Semantic Versioning (ver LTA-GOV-001, sección 11).

Ejemplo en documento:

```
docs(governance)!: restructure approval model

BREAKING CHANGE: el proceso de aprobación anterior queda obsoleto.
La versión del documento debe pasar de 1.x.x a 2.0.0.
```

Ejemplo en código:

```
feat(technical)!: change API authentication method

BREAKING CHANGE: se elimina autenticación por token simple.
Los consumidores deben migrar a OAuth 2.0.
```

---

## 7. Commits atómicos

Un commit debe representar un cambio lógico único.

Evitar:

```
feat(technical): create API, modify documents, update legal analysis
```

Preferir:

```
feat(technical): create API structure

docs(governance): update technical documentation

docs(legal): add regulatory references
```

Los commits atómicos cumplen dos propósitos incluso cuando el repositorio utiliza squash merge (ver LTA-GOV-003 §8):

* **Revisión incremental**: cada commit aislado permite al revisor entender el cambio paso a paso, verificando que cada unidad lógica es correcta por sí misma.
* **Trazabilidad durante el desarrollo**: el historial de la rama de trabajo documenta la evolución del cambio, facilitando la colaboración entre autores y revisores antes del merge.

El squash merge consolida estos commits atómicos en un único commit en la rama principal, preservando un historial limpio sin perder la trazabilidad interna del Pull Request.

---

## 8. Versionamiento

Los commits que modifiquen documentos oficiales deberán actualizar la versión correspondiente siguiendo Semantic Versioning.

| Cambio                     | Versión          | Tipo de commit asociado          |
| -------------------------- | ---------------- | -------------------------------- |
| Corrección o ajuste menor  | PATCH (`x.x.1`)  | `fix`, `docs` (corrección)       |
| Nueva capacidad o sección  | MINOR (`x.1.x`)  | `feat`, `docs` (contenido nuevo) |
| Cambio incompatible        | MAJOR (`1.x.x`)  | `!` o `BREAKING CHANGE`          |

Ejemplos:

```
fix(data): correct schema typo
→ 0.1.0 → 0.1.1
```

```
docs(research): add election integrity section
→ 0.1.0 → 0.2.0
```

```
docs(governance)!: restructure approval model
→ 0.2.0 → 1.0.0
```

---

## 9. Relación con Tipos de Issue

Los tipos de Issue definidos en LTA-GOV-004 §3 y los tipos de commit definidos en §3 de este documento operan en niveles distintos: los Issues representan la planificación del trabajo, los commits representan la implementación concreta. No existe una correspondencia obligatoria entre ambos, pero la siguiente tabla ofrece una guía orientativa.

| Tipo de Issue         | Tipo(s) de commit sugerido(s) | Ejemplo                                                                 |
| --------------------- | ----------------------------- | ----------------------------------------------------------------------- |
| `type/research`       | `docs`, `feat`                | `docs(research): add literature review` o `feat(data): collect disinformation samples` |
| `type/policy`         | `docs`                        | `docs(policy): draft transparency guidelines`                           |
| `type/bug`            | `fix`                         | `fix(technical): correct API auth header`                               |
| `type/feature`        | `feat`, `docs`, `test`        | `feat(technical): add claim extraction endpoint`                        |
| `type/documentation`  | `docs`                        | `docs(governance): update review process`                               |
| `type/discussion`     | `docs`                        | `docs(governance): summarize decision on data retention`                |

Esta tabla es orientativa. Un Issue de tipo `type/research` puede generar tanto documentos (`docs`) como nuevas capacidades técnicas (`feat`). Un Issue `type/feature` típicamente se implementa con `feat`, pero también puede incluir commits `docs` para su documentación y `test` para sus pruebas. Lo importante es que cada commit cumpla con el formato definido en §2 y represente un cambio atómico según §7.

---

## Historial de cambios

| Versión | Fecha      | Descripción                                         |
| ------- | ---------- | --------------------------------------------------- |
| 0.1.0   | 2026-06-25 | Creación inicial                                    |

---
