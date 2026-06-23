# Estándar de Documentación Institucional

**Documento ID:** LTA-GOV-001
**Versión:** 0.1.0
**Estado:** Draft
**Tipo:** Governance
**Clasificación:** Public
**Fecha de creación:** 2026-06-22

---

# 1. Propósito

Este documento define los estándares de estructura, metadatos, versionamiento, trazabilidad y gobernanza documental utilizados por el Laboratorio de Transparencia Algorítmica (LTA).

Su objetivo es garantizar que toda documentación institucional, técnica, investigativa y normativa sea consistente, auditable y mantenible a largo plazo.

---

# 2. Alcance

Este estándar aplica a:

* Documentos institucionales.
* Investigaciones.
* Propuestas regulatorias.
* Especificaciones técnicas.
* Procedimientos internos.
* Informes públicos.
* Documentación de proyectos.

Todo documento oficial deberá cumplir este estándar salvo aprobación explícita de una excepción.

---

# 3. Principios

## Transparencia

Toda información pública debe poder ser auditada por terceros.

## Trazabilidad

Toda modificación relevante debe quedar registrada.

## Reproducibilidad

Las investigaciones y análisis deberán incluir metodología y fuentes.

## Responsabilidad

Todo documento tendrá un responsable claramente identificado.

## Versionamiento

Los cambios deberán documentarse mediante un esquema formal de versiones.

---

# 4. Formato de almacenamiento

La documentación institucional deberá almacenarse preferiblemente en formato Markdown (`.md`).

Los documentos podrán complementarse con:

* PDF
* CSV
* JSON
* Imágenes
* Diagramas

La versión fuente siempre será la versión Markdown.

---

# 5. Metadatos obligatorios

Todos los documentos deberán incluir un bloque YAML Front Matter al inicio.

Ejemplo:

```yaml
---
title: "Visión Institucional"
document_id: "LTA-VISION-001"
version: "1.0.0"
status: "approved"
document_type: "charter"
classification: "public"

authors:
  - "Nombre Apellido"

owner: "Dirección Estratégica"

created: "2026-06-22"
updated: "2026-06-22"

review_cycle: "annual"

tags:
  - vision
  - strategy

license: "CC BY 4.0"

approval:
  approved_by: "Consejo Directivo"
  approved_date: "2026-07-01"

related_documents:
  - "LTA-PRINCIPLES-001"

supersedes: null
---
```

---

# 6. Identificadores documentales

Cada documento deberá poseer un identificador único.

Formato:

```
LTA-[CATEGORIA]-[NUMERO]
```

Ejemplos:

```
LTA-VISION-001
LTA-PRINCIPLES-001
LTA-GOV-001
LTA-RES-001
LTA-POLICY-001
LTA-TECH-001
```

---

# 7. Categorías documentales

## Charter

Documentos fundacionales.

Ejemplos:

* Visión
* Misión
* Principios

---

## Governance

Gobernanza institucional.

Ejemplos:

* Estatutos
* Procesos de decisión
* Normas internas

---

## Research

Investigaciones y estudios.

---

## Policy

Propuestas regulatorias o normativas.

---

## Technical

Arquitectura, software y especificaciones técnicas.

---

## Operational

Procedimientos y manuales internos.

---

## Position

Posiciones institucionales públicas.

---

# 8. Estados documentales

Todo documento deberá encontrarse en uno de los siguientes estados:

| Estado     | Descripción                           |
| ---------- | ------------------------------------- |
| draft      | Borrador en construcción              |
| review     | En revisión                           |
| approved   | Aprobado oficialmente                 |
| superseded | Reemplazado por una versión posterior |
| archived   | Archivado                             |

---

# 9. Clasificación de información

## Public

Información abierta al público.

## Internal

Uso interno de colaboradores.

## Confidential

Acceso restringido.

---

# 10. Versionamiento

Se utilizará Semantic Versioning.

Formato:

```
MAJOR.MINOR.PATCH
```

Ejemplos:

```
1.0.0
1.1.0
1.1.1
2.0.0
```

### MAJOR

Cambios incompatibles o redefiniciones importantes.

### MINOR

Nuevas secciones o ampliaciones.

### PATCH

Correcciones menores.

---

# 11. Historial de cambios

Todos los documentos deberán mantener una sección de cambios relevantes.

Ejemplo:

| Versión | Fecha      | Descripción                            |
| ------- | ---------- | -------------------------------------- |
| 0.1.0   | 2026-06-22 | Creación inicial                       |
| 0.2.0   | 2026-07-05 | Inclusión de política de clasificación |
| 1.0.0   | 2026-07-20 | Aprobación institucional               |

---

# 12. Documentación de investigaciones

Los documentos clasificados como Research deberán incluir:

* Objetivo.
* Metodología.
* Fuentes de datos.
* Limitaciones.
* Resultados.
* Referencias.

Cuando sea posible:

* Código fuente.
* Dataset.
* Scripts de reproducción.

---

# 13. Aprobación institucional

Los documentos considerados oficiales requerirán:

1. Revisión.
2. Registro de observaciones.
3. Aprobación formal.
4. Publicación.

La aprobación deberá quedar registrada en los metadatos.

---

# 14. Revisión periódica

Cada documento deberá definir una periodicidad de revisión.

Ejemplos:

* annual
* biennial
* every_6_months
* none

---

# 15. Vigencia

Este estándar permanecerá vigente hasta que sea reemplazado por una versión posterior aprobada conforme a los mecanismos de gobernanza institucional.

---

# Historial de cambios

| Versión | Fecha      | Descripción       |
| ------- | ---------- | ----------------- |
| 0.1.0   | 2026-06-22 | Documento inicial |
|         |            |                   |
