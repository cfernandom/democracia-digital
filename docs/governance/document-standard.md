---
title: "Estándar de Documentación Institucional"

document_id: "LTA-GOV-001"
version: "0.2.0"
status: "draft"
document_type: "GOV"
document_subtype: "standard"
classification: "public"
language: "es"

authors:
  - "Equipo fundador"

owner: "Gobernanza Institucional"

created: "2026-06-22"
updated: "2026-06-25"

review_cycle: "annual"

tags:
  - documentation
  - governance
  - standards
  - metadata

license: "CC BY 4.0"

approval:
  status: "provisional"
  approved_by:
    - "Equipo fundador"
  approved_date: "2026-06-25"

related_documents:
  - id: "LTA-CHR-002"
    relation: "references"
---

# Estándar de Documentación Institucional

## 1. Propósito

Este documento define los estándares de estructura, metadatos, versionamiento, trazabilidad y gobernanza documental utilizados por el Laboratorio de Transparencia Algorítmica (LTA).

Su objetivo es garantizar que toda documentación institucional, técnica, investigativa y normativa sea consistente, auditable y mantenible a largo plazo.

---

## 2. Alcance

Este estándar aplica a:

* Documentos institucionales.
* Investigaciones.
* Propuestas regulatorias.
* Especificaciones técnicas.
* Procedimientos internos.
* Informes públicos.
* Documentación de proyectos.

Todo documento oficial deberá cumplir este estándar salvo aprobación explícita de una excepción.

### Nota de bootstrap institucional

Este documento constituye el estándar inicial de documentación del proyecto.
Durante la fase fundacional, su aprobación se considera provisional mediante
aceptación del equipo fundador y deberá ser ratificada mediante el mecanismo
formal de gobernanza cuando este sea establecido.

---

## 3. Principios

### Transparencia

Toda información pública debe poder ser auditada por terceros.

### Trazabilidad

Toda modificación relevante debe quedar registrada.

### Reproducibilidad

Las investigaciones y análisis deberán incluir metodología y fuentes.

### Responsabilidad

Todo documento tendrá un responsable claramente identificado.

### Versionamiento

Los cambios deberán documentarse mediante un esquema formal de versiones.

---

## 4. Formato de almacenamiento

La documentación institucional deberá almacenarse preferiblemente en formato Markdown (`.md`).

Los documentos podrán complementarse con:

* PDF
* CSV
* JSON
* Imágenes
* Diagramas

La versión fuente siempre será la versión Markdown.

---

## 5. Metadatos obligatorios

Todos los documentos deberán incluir un bloque YAML Front Matter al inicio.

Ejemplo:

```yaml
---
title: "Visión Institucional"
document_id: "LTA-CHR-001"
version: "1.0.0"
status: "approved"
document_type: "CHR"
document_subtype: "vision"
classification: "public"
language: "es"

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
  status: "approved"
  approved_by: "Consejo Directivo"
  approved_date: "2026-07-01"

related_documents:
  - id: "LTA-CHR-002"
    relation: "references"
---
```

### 5.1 Campos requeridos

| Campo              | Requerido | Descripción                                      |
| ------------------ | --------- | ------------------------------------------------ |
| title              | Sí        | Título del documento                             |
| document_id        | Sí        | Identificador único (ver sección 6)              |
| version            | Sí        | Versión semántica (ver sección 11)              |
| status             | Sí        | Estado documental (ver sección 8)                |
| document_type      | Sí        | Categoría documental (ver sección 7)             |
| document_subtype   | No        | Subtipo dentro de la categoría. Cardinalidad 0..1: un documento puede tener como máximo un subtipo. Ver sección 7.2. |
| classification     | Sí        | Nivel de acceso (ver sección 9)                  |
| language           | Sí        | Idioma principal del documento (ver sección 10)  |
| authors            | Sí        | Lista de autores                                 |
| owner              | Sí        | Área responsable del documento                   |
| created            | Sí        | Fecha de creación (YYYY-MM-DD)                   |
| updated            | Sí        | Fecha de última modificación (YYYY-MM-DD)        |
| review_cycle       | Sí        | Periodicidad de revisión (ver sección 15)        |
| tags               | No        | Etiquetas para clasificación temática            |
| license            | Sí        | Licencia del documento                           |
| approval           | Sí        | Estado de aprobación (ver sección 5.4)           |
| related_documents  | No        | Documentos relacionados (ver sección 5.3)        |
| translation_of     | No        | Identificador único del documento original normativo. Valor único (string), cardinalidad 0..1. Ver sección 10.2. |

Los campos controlados de metadata utilizan valores exactos definidos por este estándar. Los valores son sensibles a mayúsculas y deben emplear exclusivamente los códigos establecidos en la sección 5.4.

Ejemplo válido:

```yaml
document_type: "GOV"
```

Ejemplo inválido:

```yaml
document_type: "gov"
```

### 5.2 Subtipo documental (`document_subtype`)

El campo `document_subtype` permite precisar la naturaleza de un documento dentro de su categoría.

Reglas:

- Un documento pertenece a una única categoría (`document_type`).
- Un documento puede tener a lo sumo un subtipo (`document_subtype`).
- Los subtipos válidos están definidos por cada categoría en la sección 7.2 y constituyen el conjunto oficial de subtipos permitidos. La incorporación de nuevos subtipos requiere actualización del presente estándar.
- El campo es opcional pero recomendado cuando una categoría agrupa varios tipos de documento.

Ejemplos:

```yaml
document_type: "GOV"
document_subtype: "standard"
```

```yaml
document_type: "CHR"
document_subtype: "vision"
```

| Código | Subtipos válidos                             |
| ------ | -------------------------------------------- |
| CHR    | vision, mission, principles                  |
| GOV    | statute, process, internal-rule, standard    |
| RES    | study, report, analysis, dataset             |
| POL    | regulatory-proposal, position-paper, comment |
| TEC    | architecture, api-spec, runbook, adr         |
| OPS    | procedure, manual, checklist, runbook        |
| POS    | statement, communiqué, open-letter           |

### 5.3 Referencias entre documentos (`related_documents`)

Las referencias entre documentos utilizan un formato estructurado que define el identificador del documento referenciado y el tipo de relación.

Formato:

```yaml
related_documents:
  - id: "LTA-CHR-002"
    relation: "references"
```

Relaciones permitidas:

| Relación     | Significado                                              |
| ------------ | -------------------------------------------------------- |
| references   | El documento referencia o cita al documento indicado     |
| depends_on   | El documento requiere del documento indicado             |
| implements   | El documento implementa lo definido en el documento indicado |
| supersedes   | El documento reemplaza al documento indicado             |

**Reglas para `supersedes`**:

- Un documento solo puede declarar `relation: supersedes` como máximo una vez en `related_documents`.
- El documento reemplazado debe cambiar su `status` a `superseded`.
- Para referencias no sustitutivas al documento anterior, usar `relation: references`.

---

### 5.4 Valores controlados de metadata

Los siguientes campos de metadata aceptan exclusivamente los valores definidos en esta sección. Los valores son sensibles a mayúsculas.

#### `status`

| Valor      | Descripción                           |
| ---------- | ------------------------------------- |
| draft      | Borrador en construcción              |
| review     | En revisión                           |
| approved   | Aprobado oficialmente                 |
| superseded | Reemplazado por una versión posterior |
| archived   | Archivado                             |

#### `approval.status`

Estado del proceso de aprobación institucional.

| Valor       | Descripción                                              |
| ----------- | -------------------------------------------------------- |
| pending     | Sin aprobación registrada                                |
| provisional | Aprobación válida durante fase fundacional               |
| approved    | Aprobación institucional formal                          |
| rejected    | Documento rechazado                                      |

#### `approval.approved_by`

Lista de personas o entidades que otorgaron la aprobación. Campo obligatorio cuando `approval.status` es `provisional` o `approved`.

#### `approval.approved_date`

Fecha en que se otorgó la aprobación, en formato ISO 8601 (YYYY-MM-DD). Campo obligatorio cuando `approval.status` es `provisional` o `approved`.

#### `review_cycle`

| Valor     | Descripción            |
| --------- | ---------------------- |
| monthly   | Revisión mensual       |
| quarterly | Revisión trimestral    |
| biannual  | Revisión semestral     |
| annual    | Revisión anual         |
| none      | Sin revisión periódica |

#### `classification`

| Valor        | Descripción                  |
| ------------ | ---------------------------- |
| public       | Información abierta al público |
| internal     | Uso interno de colaboradores |
| confidential | Acceso restringido           |

#### `language`

Debe utilizarse un código ISO 639-1 de dos letras válido. No existe un conjunto cerrado de idiomas permitidos; cualquier código ISO 639-1 es aceptable.

Ejemplos de códigos frecuentes:

| Código | Idioma    |
| ------ | --------- |
| es     | Español   |
| en     | Inglés    |
| pt     | Portugués |
| fr     | Francés   |

---

## 6. Identificadores documentales

Cada documento deberá poseer un identificador único.

### 6.1 Formato

```
LTA-[CATEGORIA]-[NUMERO]
```

Donde `[CATEGORIA]` es el código de tres letras de la categoría documental (ver sección 7.1).

Ejemplos válidos:

```
LTA-CHR-001
LTA-GOV-001
LTA-RES-001
LTA-POL-001
LTA-TEC-001
LTA-OPS-001
LTA-POS-001
```

### 6.2 Reglas de validación

| Regla                    | Descripción                                                    |
| ------------------------ | -------------------------------------------------------------- |
| Prefijo obligatorio      | Todo identificador comienza con `LTA`                          |
| Separador                | Los componentes se separan mediante guiones (`-`)              |
| Categoría                | Código de tres letras en mayúsculas (ver tabla en sección 7.1) |
| Caracteres de categoría  | Solo caracteres alfabéticos ASCII (A-Z)                        |
| Número                   | Número entero positivo                                         |
| Numeración               | Secuencial por categoría, sin reutilización                    |
| Longitud del número      | Entero positivo con un mínimo obligatorio de tres dígitos. La numeración puede expandirse naturalmente cuando el número de documentos supere dicho rango. |

Ejemplos inválidos:

| Identificador      | Motivo                                |
| ------------------ | ------------------------------------- |
| `LTA-foo-001`      | Categoría no definida                 |
| `LTA-VISION-001`   | Categoría en formato obsoleto         |
| `lta-gov-001`      | Prefijo en minúsculas                 |
| `LTA_GOV_001`      | Separador incorrecto                  |
| `LTA-GOV-🍕`       | Caracteres no ASCII                   |
| `LTA-GOV-1`        | Número sin ancho fijo                 |
| `LTA-GOV-0`        | Número no positivo                   |

---

## 7. Categorías documentales

### 7.1 Códigos de categoría

Cada categoría documental se identifica mediante un código de tres letras utilizado en el `document_id`.

| Código | Categoría   |
| ------ | ----------- |
| CHR    | Charter     |
| GOV    | Governance  |
| RES    | Research    |
| POL    | Policy      |
| TEC    | Technical   |
| OPS    | Operational |
| POS    | Position    |

### 7.2 Categorías vs subtipos

Una categoría documental agrupa varios tipos de documento. El campo `document_subtype` (ver sección 5.2) permite precisar el tipo específico sin crear nuevas categorías.

Subtipos permitidos por categoría:

| Código | Subtipos permitidos                          |
| ------ | -------------------------------------------- |
| CHR    | vision, mission, principles                  |
| GOV    | statute, process, internal-rule, standard    |
| RES    | study, report, analysis, dataset             |
| POL    | regulatory-proposal, position-paper, comment |
| TEC    | architecture, api-spec, runbook, adr         |
| OPS    | procedure, manual, checklist, runbook        |
| POS    | statement, communiqué, open-letter           |

### 7.3 Descripciones por categoría

#### Charter (CHR)

Documentos fundacionales que definen la identidad, propósito y principios de la institución.

Ejemplos:

* Visión
* Misión
* Principios

#### Governance (GOV)

Normas de gobernanza institucional que regulan el funcionamiento interno.

Ejemplos:

* Estatutos
* Procesos de decisión
* Normas internas
* Estándares documentales

#### Research (RES)

Investigaciones, estudios y análisis realizados por la institución.

#### Policy (POL)

Propuestas regulatorias, normativas o de política pública.

#### Technical (TEC)

Documentación técnica sobre arquitectura, software, infraestructura y especificaciones.

#### Operational (OPS)

Procedimientos operativos, manuales internos y guías de trabajo.

#### Position (POS)

Posiciones institucionales públicas, comunicados y declaraciones.

---

## 8. Estados documentales

Los estados documentales corresponden a los valores definidos para el campo `status` en la sección 5.4.

---

## 9. Clasificación de información

Los niveles de clasificación y sus valores permitidos están definidos en la sección 5.4.

---

## 10. Idioma institucional

### 10.1 Idioma principal

El idioma institucional principal del LTA es el español. Todo documento oficial deberá redactarse en español, salvo que su propósito o audiencia requieran otro idioma.

### 10.2 Traducciones

Las traducciones de documentos oficiales a otros idiomas se identifican mediante el campo `language` en los metadatos.

Una traducción:

- Mantiene el mismo `document_id` conceptual que el documento original.
- Declara el idioma correspondiente en el campo `language` (ej. `"en"`, `"pt"`).
- Referencia al documento original mediante el campo `translation_of`.

Ejemplo de metadatos de una traducción al inglés:

```yaml
document_id: "LTA-GOV-001"
language: "en"
translation_of: "LTA-GOV-001"
```

**Solo la versión en el idioma original aprobado tiene carácter normativo.** Las traducciones tienen carácter informativo, salvo que el proceso de aprobación institucional les otorgue expresamente carácter oficial. La versión normativa debe estar explícitamente identificada mediante el campo `language` del documento original aprobado.

### 10.3 Códigos de idioma

Se utilizarán códigos ISO 639-1 de dos letras.

| Código | Idioma    |
| ------ | --------- |
| es     | Español   |
| en     | Inglés    |
| pt     | Portugués |

---

## 11. Versionamiento

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

#### PATCH

Correcciones menores. Ejemplos aplicados a documentación:

- Correcciones de redacción.
- Correcciones de metadata.
- Aclaraciones que no modifican reglas.

Ejemplo:

```
0.2.1
Corrección de validación documental.
```

#### MINOR

Nuevas secciones o ampliaciones compatibles. Ejemplos aplicados a documentación:

- Nuevas secciones.
- Nuevas reglas compatibles con las existentes.
- Nuevos campos opcionales.

Ejemplo:

```
0.3.0
Incorporación de política de idiomas.
```

#### MAJOR

Cambios incompatibles o redefiniciones importantes. Ejemplos aplicados a documentación:

- Cambios incompatibles en la estructura documental.
- Cambios del modelo de gobernanza.
- Modificación de reglas que invalidan versiones anteriores.

Ejemplo:

```
1.0.0 → 2.0.0
Cambio del sistema de aprobación institucional.
```

---

## 12. Convenciones de historial de cambios

Todos los documentos deberán mantener una sección de cambios relevantes.

Ejemplo:

| Versión | Fecha      | Descripción                            |
| ------- | ---------- | -------------------------------------- |
| 0.1.0   | 2026-06-22 | Creación inicial                       |
| 0.2.0   | 2026-06-28 | Incorporación de política de clasificación |
| 1.0.0   | 2026-07-15 | Aprobación institucional                   |

---

## 13. Documentación de investigaciones

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

## 14. Aprobación institucional

Los documentos considerados oficiales requerirán:

1. Revisión.
2. Registro de observaciones.
3. Aprobación formal.
4. Publicación.

La aprobación deberá quedar registrada en el campo `approval` de los metadatos, conforme a los estados definidos en la sección 5.4.

Durante la fase fundacional, la aprobación provisional mediante aceptación del equipo fundador es válida con `approval.status: "provisional"`. Una vez establecido el mecanismo formal de gobernanza, toda aprobación provisional deberá ser ratificada o reemplazada por una aprobación formal.

---

## 15. Revisión periódica

Cada documento deberá definir una periodicidad de revisión en el campo `review_cycle`. Los valores permitidos están definidos en la sección 5.4.

---

## 16. Vigencia

Este estándar permanecerá vigente hasta que sea reemplazado por una versión posterior aprobada conforme a los mecanismos de gobernanza institucional.

---

## Historial de cambios

| Versión | Fecha      | Descripción       |
| ------- | ---------- | ----------------- |
| 0.1.0   | 2026-06-22 | Documento inicial |
| 0.1.1   | 2026-06-23 | Inclusión de metadata obligatoria conforme al estándar definido |
| 0.1.2   | 2026-06-25 | Corrección de inconsistencias internas y normalización documental |
| 0.2.0   | 2026-06-25 | Normalización de taxonomía documental con códigos, formalización de subtipos, modelo de aprobación con estados, valores controlados de metadata, política de traducciones con translation_of, SemVer documental con ejemplos aplicados |

---
