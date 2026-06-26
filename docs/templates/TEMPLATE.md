---
title: ""
document_id: ""
version: "0.1.0"
status: "draft"
document_type: ""
document_subtype: ""
classification: "public"
language: "es"

authors:
  - ""

owner: ""

created: ""
updated: ""

review_cycle: "annual"

tags:
  - ""

license: "CC BY 4.0"

approval:
  status: "pending"
  # approved_by: []      # obligatorio solo si approval.status es provisional o approved
  # approved_date: ""    # obligatorio solo si approval.status es provisional o approved

related_documents: []
---

# [Título del documento]

> **Nota**: Completar los campos del bloque YAML superior antes de redactar el contenido. Eliminar esta nota al publicar.

### Campos requeridos (no pueden quedar vacíos)

| Campo | Instrucción |
|-------|-------------|
| `title` | Título del documento |
| `document_id` | Formato `LTA-{CATEGORIA}-{NNN}` (ver LTA-GOV-001 §6) |
| `document_type` | Código de categoría: `CHR`, `GOV`, `RES`, `POL`, `TEC`, `OPS`, `POS` (ver LTA-GOV-001 §5.4) |
| `classification` | `public`, `internal` o `confidential` |
| `language` | Código ISO 639-1 (ej. `es`, `en`, `pt`). Cualquier código válido es aceptable. |
| `authors` | Al menos un autor |
| `owner` | Área responsable |
| `created` | Fecha `YYYY-MM-DD` |
| `updated` | Fecha `YYYY-MM-DD` |
| `approval.status` | `pending`, `provisional` o `approved`. La combinación con `status` debe ajustarse a la matriz LTA-GOV-001 §8.3. Para `status: draft`, usar siempre `approval.status: pending`. Un documento rechazado en revisión no usa `rejected` en `approval.status`; transita a `draft` (devolución) o `archived` (descarte) conforme a LTA-GOV-001 §8.1. |
| `approval.approved_by` | Lista de aprobadores. Obligatorio si `approval.status` es `provisional` o `approved`. Omitir el campo si `approval.status: pending` (no usar `[]` como sustituto de ausencia). |
| `approval.approved_date` | Fecha `YYYY-MM-DD` válida. Obligatorio si `approval.status` es `provisional` o `approved`. Omitir el campo si `approval.status: pending` (no usar `""` como sustituto de ausencia). |

### Campos opcionales (pueden eliminarse si no aplican)

| Campo | Instrucción |
|-------|-------------|
| `document_subtype` | Subtipo según categoría (ver LTA-GOV-001 §7.2). Si no se usa, eliminar la línea. |
| `tags` | Lista de etiquetas. Si no se usa, dejar `[]` o eliminar. |
| `related_documents` | Referencias a otros documentos. Si no se usa, dejar `[]` o eliminar. |
| `translation_of` | Marca la instancia idiomática como traducción. El valor es el mismo `document_id` del documento; no identifica un documento distinto. Si no aplica, eliminar la línea. (Ver LTA-GOV-001 §10.2) |

### Valores controlados

Los campos `document_type`, `document_subtype`, `status`, `approval.status`, `review_cycle`, `classification` y las relaciones de `related_documents` constituyen **conjuntos cerrados**: solo aceptan los valores definidos en LTA-GOV-001 §5.4 y §5.3. Cualquier incorporación, eliminación o renombrado requiere modificación formal del estándar (ver LTA-GOV-001 §11.2). Los valores son sensibles a mayúsculas. Ejemplo: `"GOV"` válido, `"gov"` inválido. El campo `language` es **conjunto abierto** y debe utilizar un código ISO 639-1 válido (ver LTA-GOV-001 §5.4).

## 1. Propósito

<!-- Describir el objetivo del documento en uno o dos párrafos. Responder: ¿qué problema resuelve o qué decisión fundamenta? -->

## 2. Alcance

<!-- Definir qué cubre este documento. Opcional: indicar explícitamente qué NO cubre. -->

## 3. Contenido principal

<!-- Desarrollar el contenido según la categoría y tipo de documento.
     Para documentos Research, incluir las secciones obligatorias definidas en LTA-GOV-001:
     Objetivo, Metodología, Fuentes de datos, Limitaciones, Resultados, Referencias. -->

---

## Historial de cambios

> **Nota**: opcional mientras el documento esté en `draft`. Obligatorio a partir de la primera publicación (`review` o `approved`). Ver LTA-GOV-001 §12.

| Versión | Fecha | Descripción |
| ------- | ----- | ----------- |
| 0.1.0   |       | Versión inicial |
