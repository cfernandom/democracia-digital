---
title: "Política de Issues y Seguimiento de Trabajo"

document_id: "LTA-GOV-004"
version: "0.1.0"
status: "draft"
document_type: "GOV"
document_subtype: "process"
classification: "public"
language: "es"

authors:
  - "Equipo fundador"

owner: "Gestión de Proyectos"

created: "2026-06-25"
updated: "2026-06-25"

review_cycle: "annual"

tags:
  - issues
  - project-management
  - tracking

license: "CC BY 4.0"

approval:
  status: "pending"

related_documents:
  - id: "LTA-GOV-001"
    relation: "references"
  - id: "LTA-GOV-002"
    relation: "references"
  - id: "LTA-GOV-003"
    relation: "references"
---

# Política de Issues y Seguimiento de Trabajo

## 1. Propósito

Establecer el uso de Issues como mecanismo oficial para registrar, discutir y gestionar actividades del proyecto.

---

## 2. Principios

Los Issues representan:

* problemas identificados.
* propuestas.
* investigaciones.
* tareas.
* decisiones pendientes.

No deben utilizarse como conversaciones informales sin objetivo definido.

---

## 3. Tipos de Issue

| Tipo          | Uso                 |
| ------------- | ------------------- |
| bug           | Error técnico       |
| feature       | Nueva capacidad     |
| research      | Investigación       |
| policy        | Propuesta normativa |
| documentation | Mejora documental   |
| discussion    | Debate estratégico  |

> **Nota**: Los tipos de commit `test` y `refactor` (definidos en LTA-GOV-002 §3) no tienen un tipo de Issue correspondiente. Estos trabajos típicamente ocurren dentro del alcance de un Issue existente (`type/feature`, `type/bug`, `type/documentation`) y no requieren un Issue independiente.

---

## 4. Estructura mínima

Todo Issue deberá contener:

```markdown
## Objetivo

Descripción clara del propósito.

## Contexto

Antecedentes relevantes.

## Alcance

Qué incluye y qué no incluye.

## Criterios de aceptación

Cómo saber que está terminado.
```

---

## 5. Etiquetas

Las etiquetas (labels) implementan la clasificación de Issues en GitHub. Siguen una convención de prefijos que las agrupa en tres categorías.

### 5.1 Categorías

| Categoría   | Prefijo      | Propósito                                      |
| ----------- | ------------ | ---------------------------------------------- |
| Área        | `area/*`     | Dominio organizacional afectado                |
| Prioridad   | `priority/*` | Nivel de urgencia y atención requerida         |
| Tipo        | `type/*`     | Naturaleza del trabajo                         |

Cada Issue debe tener **al menos una etiqueta de cada categoría** para que sea clasificable y filtrable.

### 5.2 Áreas (`area/*`)

| Etiqueta           | Descripción                                  |
| ------------------ | -------------------------------------------- |
| `area/governance`  | Gobernanza institucional y procesos          |
| `area/research`    | Investigaciones, estudios y publicaciones    |
| `area/legal`       | Análisis jurídico, normativa y regulación    |
| `area/policy`      | Propuestas de política pública y posición     |
| `area/technical`   | Software, arquitectura e infraestructura     |
| `area/data`        | Datos, modelos y pipelines                   |
| `area/community`   | Comunidad, difusión y participación          |

### 5.3 Prioridades (`priority/*`)

| Etiqueta             | Descripción                                  |
| -------------------- | -------------------------------------------- |
| `priority/critical`  | Atención inmediata — bloquea trabajo esencial|
| `priority/high`      | Prioridad alta — atender en el ciclo actual  |
| `priority/medium`    | Prioridad media — planificar próximos ciclos |
| `priority/low`       | Prioridad baja — backlog sin urgencia        |

### 5.4 Tipos (`type/*`)

| Etiqueta               | Descripción                                  |
| ---------------------- | -------------------------------------------- |
| `type/bug`             | Error técnico o comportamiento incorrecto    |
| `type/feature`         | Nueva funcionalidad o capacidad              |
| `type/research`        | Investigación, análisis o estudio            |
| `type/policy`          | Propuesta normativa o de política            |
| `type/documentation`   | Creación o mejora de documentación           |
| `type/discussion`      | Debate estratégico o decisión abierta        |

### 5.5 Etiquetas comunitarias

Dos etiquetas se mantienen sin prefijo por ser estándar de GitHub y facilitar el descubrimiento por colaboradores externos:

| Etiqueta            | Descripción                                  |
| ------------------- | -------------------------------------------- |
| `good first issue`  | Ideal para quienes contribuyen por primera vez|
| `help wanted`       | Se busca colaboración externa                |

### 5.6 Combinación de etiquetas

Cada Issue debe combinar una etiqueta de cada categoría. Ejemplo para un Issue de investigación con prioridad alta en el área legal:

```
area/legal   priority/high   type/research
```

La configuración declarativa de las etiquetas se mantiene en `.github/labels.yml` como referencia canónica. La aplicación de estas etiquetas al repositorio puede realizarse manualmente mediante la interfaz de GitHub o la API. La automatización de este proceso queda fuera del alcance actual.

---

## 6. Ciclo de vida

Los estados del trabajo se gestionan mediante los mecanismos nativos de GitHub, sin etiquetas de estado adicionales:

* **Apertura y cierre**: Issues abiertos (`Open`) y cerrados (`Closed`).
* **Asignación**: `Assignees` indican quién está a cargo del trabajo.
* **Seguimiento activo**: `Projects` y `Milestones` reflejan el trabajo planificado o en curso.
* **Revisión**: `Pull Requests` vinculados muestran el avance hacia la implementación.

Este enfoque mantiene el flujo simple y evita la duplicación con el estado nativo del Issue.

---

## 7. Relación con Pull Requests

Todo cambio implementado mediante PR deberá vincularse con un Issue cuando corresponda.

Ejemplo:

```
Closes #34
```

Esto permite mantener trazabilidad:

```
Problema
   ↓
Discusión
   ↓
Implementación
   ↓
Aprobación
```

---

## Historial de cambios

| Versión | Fecha      | Descripción      |
| ------- | ---------- | ---------------- |
| 0.1.0   | 2026-06-25 | Creación inicial                       |

---
