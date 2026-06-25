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
  status: ""
  approved_by: []
  approved_date: ""

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
| `approval.status` | `pending`, `provisional`, `approved` o `rejected` |
| `approval.approved_by` | Lista de aprobadores. Obligatorio si `status` es `provisional` o `approved`. Puede ser `[]` si `status: pending`. |
| `approval.approved_date` | Fecha `YYYY-MM-DD`. Obligatorio si `status` es `provisional` o `approved`. Puede ser `""` si `status: pending`. |

### Campos opcionales (pueden eliminarse si no aplican)

| Campo | Instrucción |
|-------|-------------|
| `document_subtype` | Subtipo según categoría (ver LTA-GOV-001 §7.2). Si no se usa, eliminar la línea. |
| `tags` | Lista de etiquetas. Si no se usa, dejar `[]` o eliminar. |
| `related_documents` | Referencias a otros documentos. Si no se usa, dejar `[]` o eliminar. |
| `translation_of` | Identificador del documento original normativo si este documento es una traducción. Si no aplica, eliminar la línea. |

### Valores controlados

Los campos `document_type`, `document_subtype`, `status`, `approval.status`, `review_cycle` y `classification` solo aceptan los valores definidos en LTA-GOV-001 §5.4. Los valores son sensibles a mayúsculas. Ejemplo: `"GOV"` válido, `"gov"` inválido. El campo `language` debe utilizar un código ISO 639-1 válido (ver LTA-GOV-001 §5.4).

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

| Versión | Fecha | Descripción |
| ------- | ----- | ----------- |
| 0.1.0   |       | Versión inicial |
