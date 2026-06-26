---
title: "Estándar de Documentación Institucional"

document_id: "LTA-GOV-001"
version: "0.3.0"
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
  status: "pending"

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

### 2.1 Repositorio institucional oficial

Se denomina **repositorio institucional oficial** al sistema o conjunto de sistemas oficialmente designados por el LTA para almacenar la versión autorizada de sus documentos. Esta designación puede recaer en uno o varios repositorios y puede trasladarse a otra plataforma mediante migración, sin que ello afecte al régimen documental definido por este estándar. Cada repositorio institucional oficial debe garantizar la recuperabilidad del estado actual y del histórico de cada documento, conforme a §3.1 y §12. La tecnología o plataforma concreta del repositorio queda fuera del alcance de este estándar.

### 2.2 Definición de documento oficial

Se denomina **documento oficial** a todo documento que cumple simultáneamente:

1. posee un `document_id` asignado conforme a §6;
2. está incorporado al repositorio institucional oficial;
3. se encuentra bajo el régimen documental definido por este estándar.

Quedan fuera del alcance de este estándar y no constituyen documentos oficiales: notas personales, borradores locales, copias temporales, material de trabajo anecdótico y cualquier contenido no incorporado al repositorio institucional oficial. La ausencia de `document_id` o la pertenencia a un repositorio personal no confiere rango oficial.

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

### 3.1 Documento, instancia idiomática y versión

Se distinguen tres conceptos:

- **Documento:** identidad permanente identificada por `document_id` (ver §6). El documento es una obra institucional conceptual, independiente de sus versiones e idiomas.
- **Instancia idiomática:** materialización del documento en un `language` dado (ver §10.2). Cada instancia idiomática existe como archivo físico en el repositorio institucional y se identifica unívocamente por el par (`document_id`, `language`) conforme a §6.3.
- **Versión:** estado del contenido en un momento dado, registrada en el campo `version` (ver §11). La versión es un atributo de la instancia idiomática presente en el repositorio.

**Modelo de persistencia.** Para cada instancia idiomática existe un único archivo vigente en el repositorio. Las versiones históricas se preservan exclusivamente mediante el sistema de control de versiones del repositorio (historial de commits) y el historial de cambios del documento (ver §12). El estándar no contempla la coexistencia de archivos independientes por versión.

`document_id` es inmutable durante toda la vida del documento. `language` es inmutable para una instancia idiomática. `version` cambia con cada modificación publicada conforme a §11.1.

`version` no constituye un documento ni una instancia documental independiente; es únicamente un atributo de una instancia idiomática. Las versiones no se registran como entidades separadas, sino como estados sucesivos del archivo de la instancia idiomática (ver §3.3).

### 3.2 Fuerza normativa de los verbos modales

Los verbos modales del presente estándar se interpretan conforme a RFC 2119:

- **debe**: requisito obligatorio.
- **no debe**: prohibición absoluta.
- **debería**: recomendación.
- **puede**: habilitación opcional.

La interpretación semántica sigue RFC 2119. El presente estándar utiliza exclusivamente las formas en español; no introduce las formas en inglés (MUST, MUST NOT, SHOULD, MAY).

### 3.3 Modelo conceptual

```
                        Documento
                     (document_id, §6)
                            │
            ┌───────────────┼───────────────┐
            │               │               │
   Instancia idiom.    Instancia idiom.   ...
   (language=es)       (language=en)
    │                       │
    └──── metadata ────────┘
            version (§11)
            status (§8)
            approval (§14)
            classification (§9)
            translation_of (§10.2)

   related_documents (§5.3): vincula Documentos,
   no instancias idiomáticas ni versiones.
```

Cada documento posee una identidad `document_id` y se materializa en una o varias instancias idiomáticas identificadas por `language`. Cada instancia idiomática expone su propia metadata: `version`, `status`, `approval`, `classification` y, si corresponde, `translation_of`.

`related_documents` vincula Documentos entre sí (no instancias idiomáticas ni versiones) mediante relaciones controladas (§5.3).

Las versiones históricas no son entidades físicas coexistentes: se preservan mediante el historial del sistema de control de versiones del repositorio y el historial de cambios del documento (§12).

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

Los archivos complementarios (datasets, PDF, diagramas) no reciben `document_id` propio y no son sujetos de versionamiento autónomo. Si futuramente se requiere un régimen formal de anexos y material suplementario, se incorporará como extensión de este estándar.

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
| translation_of     | No        | Marca que la instancia idiomática actual es una traducción. El valor es el `document_id` de la obra (el mismo del documento actual); no identifica un documento distinto. Cardinalidad 0..1. Ver sección 10.2. |

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

**Reglas para `supersedes`**: ver sección 5.3.1.

### 5.3.1 Política de reemplazo de documentos

Un documento `A` reemplaza a un documento `B` cuando:

- `B` se encuentra en estado `approved`; y
- `A` introduce un cambio sustantivo que modifica, deroga o reemplaza normativamente el contenido de `B`; y
- `A` declara `relation: supersedes` hacia `B` en `related_documents`.

Al publicarse `A` con `status: approved`:

1. `B` cambia su `status` de `approved` a `superseded` de forma obligatoria.
2. El documento reemplazado se conserva íntegramente para garantizar la trazabilidad histórica. Su retirada del estado vigente no está permitida; el documento debe permanecer recuperable conforme a §8.4.
3. De `B` se conservan inmutables su identidad (`document_id`) y los metadatos permanentes (`version`, `language`, `created`, `authors`, `owner`). Únicamente se actualizan los metadatos gestionados por el ciclo de vida (`status`, que pasa a `superseded`, y `updated`, con la fecha del cambio). El resto de la metadata registrada al momento de la aprobación previa (incluido `approval`) permanece como quedó en esa aprobación y no se sobrescribe.
4. `A` debe conservar la relación declarada durante toda su vigencia.
5. Un documento solo puede declarar `relation: supersedes` como máximo una vez en `related_documents`.

Para referencias no sustitutivas al documento anterior (citas, dependencias
técnicas), usar `relation: references` o `relation: depends_on`.

---

### 5.4 Valores controlados de metadata

Los siguientes campos constituyen **conjuntos cerrados**: solo aceptan los valores aquí enumerados y son sensibles a mayúsculas. Cualquier incorporación, eliminación o renombrado requiere modificación formal de este estándar (ver §11.2).

Conjuntos cerrados:

- `status`
- `approval.status`
- `review_cycle`
- `classification`
- `document_type` (ver §7.1)
- `document_subtype` (ver §7.2)
- relaciones de `related_documents` (ver §5.3)

Excepción: `language` es **conjunto abierto** y acepta cualquier código ISO 639-1 válido (ver §5.4 `language`).

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

El valor `rejected` no forma parte del conjunto controlado. Un documento cuya revisión fue desfavorable se maneja mediante transiciones del ciclo de vida (ver §8.1): `review → draft` (devolución con observaciones) o `review → archived` (descarte). Duplicar el rechazo en `approval.status` sería redundante respecto del campo `status`.

#### `approval.approved_by`

Lista de personas o entidades que otorgaron la aprobación. Campo obligatorio cuando `approval.status` es `provisional` o `approved`.

#### `approval.approved_date`

Fecha en que se otorgó la aprobación, en formato ISO 8601 (YYYY-MM-DD). Campo obligatorio cuando `approval.status` es `provisional` o `approved`.

Campos de fecha y listas de metadata no deben declararse con valores vacíos (`""` o `[]`) como sustituto de ausencia. Cuando un campo condicional no aplica debe omitirse de los metadatos en lugar de rellenarse con un valor nulo o vacío.

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

### 6.3 Asignación de identificadores

La asignación de `document_id` es responsabilidad del órgano de gobernanza
documental del LTA. Durante la fase fundacional, esta responsabilidad recae en
el equipo fundador hasta que un órgano formal sea establecido.

Reglas:

1. **Unicidad.** Ningún `document_id` puede asignarse a dos documentos distintos. La unicidad se entiende a nivel de par (`document_id`, `language`): no pueden existir dos documentos con el mismo `document_id` y el mismo `language` (ver sección 10.2 para el régimen de traducciones).
2. **No reutilización.** Un `document_id` asignado a un documento posteriormente `superseded` o `archived` no puede reasignarse a un nuevo documento. La numeración es estrictamente creciente por categoría.
3. **Asignación centralizada.** Todo nuevo documento debe solicitar la asignación de su `document_id` al órgano responsable antes de su publicación.
4. **Registro.** El órgano responsable mantiene un registro de identificadores emitidos que incluye como mínimo `document_id`, título, fecha de asignación y área solicitante.

La ausencia temporal de un órgano formal no suspende estas reglas: el equipo fundador actúa como autoridad transitoria bajo el mismo régimen.

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

### 7.4 Carácter normativo e informativo (interpretación)

El presente estándar no introduce un campo explícito para distinguir fuerza normativa. El carácter se infiere de la combinación de `document_subtype` y
`status`:

- Documentos `GOV/*`, `POL/regulatory-proposal`, `CHR/*` en `status: approved` tienen presunción **normativa** dentro del LTA.
- Documentos `RES/*`, `POS/*`, `TEC/*` y similares tienen presunción **informativa** o **descriptiva**, incluso en `status: approved`.
- Documentos en `status: draft` o `review` nunca tienen fuerza normativa, independientemente de su categoría.

La distinción idioma-original vs traducción (sección 10.2) opera en una dimensión ortogonal: determina cuál instancia idiomática es la fuente normativa, no si toda ella lo es.

### 7.5 Extensibilidad del modelo

Cualquier modificación a:

- categorías documentales (§7.1);
- subtipos permitidos (§7.2);
- campos obligatorios (§5.1);
- conjuntos cerrados de valores controlados (§5.4);

requiere actualización formal del presente estándar mediante incremento de versión conforme a §11 y, según el caso, §11.2.

No se permite la incorporación de nuevos valores controlados mediante extensión local; todo nuevo valor debe registrarse en este documento.

---

## 8. Estados documentales

Los estados documentales corresponden a los valores definidos para el campo `status` en la sección 5.4. Las transiciones entre estados siguen el ciclo de vida definido en esta sección.

### 8.1 Ciclo de vida y transiciones permitidas

```
draft
  ↓
review
  ↓
approved
  ├──→ superseded
  └──→ archived
```

`superseded` y `archived` son estados terminales independientes. Ningún documento puede retornar a `draft`, `review` o `approved` desde ellos.

Transiciones permitidas:

| Origen     | Destinos permitidos       |
| ---------- | ------------------------- |
| draft      | review, archived          |
| review     | draft, approved, archived |
| approved   | superseded, archived      |
| superseded | (terminal)                |
| archived   | (terminal)                |

Reglas:

- `draft` → `review`: el documento entra en proceso de aprobación.
- `review` → `draft`: requiere devolución con observaciones registradas.
- `review` → `approved`: implica la actualización simultánea de `approval` conforme a la sección 14.
- `approved` → `superseded`: se produce exclusivamente por la publicación de un documento que declara `relation: supersedes` (ver sección 5.3.1).
- `approved` → `archived`: corresponde al retiro por obsolescencia sin reemplazo normativo (ver sección 8.2).
- `draft` → `archived` y `review` → `archived`: retiro anticipado de un documento que no llegó a aprobación y no se continuará.

### 8.2 Distinción entre `superseded` y `archived`

Ambos son estados terminales, pero responden a circunstancias distintas:

| Criterio | `superseded` | `archived` |
| -------- | ------------ | ---------- |
| Causa | Existe un documento nuevo que lo reemplaza normativamente | Retiro por obsolescencia o pérdida de relevancia sin reemplazo |
| Reemplazo | Sí, identificado en `related_documents` con `relation: supersedes` | No |
| Trazabilidad | Requiere vínculo explícito al sucesor | No requiere sucesor |

**Regla de decisión:**

- Si se publica un nuevo documento `A` que reemplaza normativamente a `B` → `B` pasa a `superseded` (ver 5.3.1).
- Si se retira `B` por obsolescencia (proceso suprimido, política abandonada, período cerrado) sin documento que lo reemplace → `B` pasa a `archived`.

**Ejemplos:**

- `LTA-GOV-001` v1.0.0 reemplazado por `LTA-GOV-002` v1.0.0 → `LTA-GOV-001` pasa a `superseded`; `LTA-GOV-002` declara `relation: supersedes`.
- `LTA-OPS-003` "Manual de procedimiento X" para un proceso descontinuado, sin reemplazo → pasa a `archived`.

Un documento nunca puede ser `archived` si existe su reemplazo declarado; debe ser `superseded`. Inversamente, un documento sin reemplazo no puede ser
`superseded` (no hay `relation: supersedes` que declarar).

### 8.3 Consistencia con `approval.status`

La combinación entre `status` y `approval.status` debe ajustarse a la siguiente matriz. Cualquier otra combinación es inválida.

| `status`     | `approval.status` permitidos            |
| ------------ | --------------------------------------- |
| draft        | pending                                 |
| review       | pending                                 |
| approved     | provisional, approved                   |
| superseded   | provisional, approved                   |
| archived     | provisional, approved                   |

Un documento en estado `review` no puede considerarse simultáneamente aprobado. La transición `review → approved` (ver §8.1) implica la actualización simultánea de `approval` conforme a §14. Un documento en `review` con revisión desfavorable transita a `draft` (devolución con observaciones) o a `archived` (descarte); no introduce estado paralelo en `approval`.

Notas:

- Un documento `status: approved` debe haber registrado `approved_by` y `approved_date` (ver §5.4).
- Un documento `status: draft` debe tener `approval.status: pending`; no puede pretender aprobación simultánea.

### 8.4 Conservación documental

Ningún documento cuyo `status` sea `approved`, `superseded` o `archived` debe dejar de ser recuperable en el repositorio institucional oficial.

Los documentos en `draft` o `review` pueden retirarse mientras no hayan sido publicados. Una vez publicados, su conservación es obligatoria: el documento debe permanecer recuperable en el repositorio institucional oficial, incluido su contenido histórico y sus versiones previas.

La forma concreta en que el repositorio institucional oficial garantiza la recuperabilidad (árbol vigente, historial de control de versiones, archivo de largo plazo u otro mecanismo equivalente) queda fuera del alcance de este estándar y se rige por las políticas del repositorio correspondiente.

Para retiro normativo sin pérdida de trazabilidad, usar los estados terminales `superseded` (ver §5.3.1) o `archived` (ver §8.2), no la eliminación del documento.

---

## 9. Clasificación de información

Los niveles de clasificación y sus valores permitidos están definidos en la sección 5.4.

---

## 10. Idioma institucional

### 10.1 Idioma principal

El idioma institucional principal del LTA es el español. Todo documento oficial deberá redactarse en español, salvo que su propósito o audiencia requieran otro idioma.

### 10.2 Traducciones

Un mismo `document_id` identifica una obra institucional conceptual. Cada traducción constituye una **instancia idiomática** distinta de esa obra. La unicidad del `document_id` (ver sección 6.3) se entiende a nivel de **par(`document_id`, `language`)**: no pueden existir dos documentos con el mismo `document_id` y el mismo `language`.

Las traducciones de documentos oficiales a otros idiomas se identifican mediante el campo `language` en los metadatos.

Una traducción:

- Comparte `document_id` con el documento original; no es un nuevo documento.
- Declara el idioma correspondiente en el campo `language` (ej. `"en"`, `"pt"`).
- Se marca como traducción mediante el campo `translation_of`, cuyo valor coincide con su propio `document_id`. Su única función es distinguir la instancia idiomática original de las traducidas; no referencia otro `document_id`.

Ejemplo de metadatos de una traducción al inglés:

```yaml
document_id: "LTA-GOV-001"
language: "en"
translation_of: "LTA-GOV-001"
```

**Solo la versión en el idioma original aprobado tiene carácter normativo.** Las traducciones tienen carácter informativo, salvo que el proceso de aprobación institucional les otorgue expresamente carácter oficial. La versión normativa debe estar explícitamente identificada mediante el campo `language` del documento original aprobado.

**Nota sobre `translation_of`:** el valor de `translation_of` coincide por construcción con el `document_id` del propio documento cuando este es una traducción. El campo no es redundante: su **presencia/ausencia** es el marcador explícito que distingue instancia idiomática original de instancia traducida. No se deriva de `document_id` + `language` sin conocer el idioma original, que no es un campo del modelo.

**Independencia de versionado entre idiomas.** Cada instancia idiomática evoluciona de forma autónoma. Las versiones no están obligadas a sincronizarse entre idiomas: puede existir, por ejemplo, una versión `2.0.0` en español y `1.8.0` en inglés de un mismo `document_id`. Esa asincronía constituye un estado temporal aceptable. El idioma original aprobado conserva carácter normativo según el párrafo anterior, sin perjuicio de la versión vigente de cada traducción.

El presente estándar no modela el grado de sincronización entre traducciones, no presupone equivalencia entre los números de versión de distintos idiomas y no exige que las traducciones evolucionen simultáneamente. La equivalencia de contenido entre instancias idiomáticas es responsabilidad del proceso de traducción, no del modelo documental aquí definido.

### 10.3 Códigos de idioma

Se utilizarán códigos ISO 639-1 de dos letras.

| Código | Idioma    |
| ------ | --------- |
| es     | Español   |
| en     | Inglés    |
| pt     | Portugués |

---

## 11. Versionamiento

El presente estándar adopta Semantic Versioning 2.0.0 como convención para el versionamiento documental. SemVer se adapta aquí al ámbito documental: los componentes MAJOR, MINOR y PATCH se interpretan según los criterios definidos en esta sección y en §11.2, prevaleciendo las reglas del presente documento sobre el uso tradicional de SemVer en software cuando existan diferencias.

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

### 11.1 Obligaciones de modificación

Toda modificación publicada de un documento debe:

1. incrementar `version` conforme a la semántica de §11;
2. actualizar `updated` con la fecha de la modificación;
3. registrar una entrada en el historial de cambios (ver §12).

A los efectos de esta sección, se considera modificación cualquier cambio del contenido del documento o de cualquier campo de metadata, incluidos `approval`, `classification`, `owner`, `review_cycle` y `language`. Un cambio exclusivamente de metadata obliga al incremento de `version` en la misma medida que un cambio de contenido.

No deben coexistir en el repositorio dos revisiones de un mismo documento con el mismo `document_id` y `language` que declaren la misma `version`.

Para cambios no publicados en ramas de trabajo, esta regla aplica al momento de integrar la versión al repositorio oficial.

### 11.2 Cambios incompatibles

Constituyen cambios incompatibles y requieren incremento MAJOR:

- eliminación de un campo obligatorio;
- renombrado de un campo obligatorio o de un valor controlado;
- eliminación o renombrado de un valor controlado en un conjunto cerrado;
- modificación del formato de `document_id` (ver §6.1);
- modificación de las transiciones permitidas entre estados (ver §8.1);
- eliminación o cambio de una categoría documental (ver §7.1);
- modificación de la semántica de un campo que invalide documentos previamente válidos.

No constituyen cambio incompatible:

- añadir un campo opcional (incremento MINOR);
- añadir un nuevo valor controlado a un conjunto cerrado (MINOR);
- corregir redacción o metadata sin alterar la semántica (PATCH).

---

## 12. Convenciones de historial de cambios

Todo documento debe mantener una sección de historial de cambios a partir de su primera publicación, definida como:

- paso a `review` por primera vez, o
- paso a `approved` o `provisional`.

Antes de la primera publicación (estado `draft`), el historial es **opcional**.

El historial debe contener al menos:

- versión;
- fecha (YYYY-MM-DD);
- descripción sumaria del cambio.

Para documentos ya publicados, cada nueva versión debe registrar una entrada conforme a §11.1.

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

## 17. Convenciones de nombres de archivo

Las siguientes son recomendaciones institucionales para nombrar archivos de documentos oficiales. No son reglas de validación del `document_id` (ver
sección 6) y no forman parte del identificador documental.

Principios:

1. El `document_id` declarado en el front matter es la única fuente de verdad sobre la identidad del documento.
2. El nombre físico del archivo no forma parte del identificador documental.
3. Cambiar el nombre físico del archivo no modifica la identidad ni la trazabilidad del documento, siempre que el `document_id` se mantenga.

Recomendaciones de estilo:

1. Usar el `document_id` en minúsculas como prefijo del nombre.
2. Separar componentes con guiones (`-`), sin espacios ni guiones bajos.
3. Usar el `document_subtype` o un descriptor corto en minúsculas y sin acentos como componente descriptivo.
4. Para traducciones, incluir el código ISO 639-1 del idioma como sufijo antes de la extensión.
5. La extensión oficial de la fuente es `.md`.

Formato sugerido:

```
[lta-categoría-número]-[descriptor].md
[lta-categoría-número]-[descriptor].[lang].md   (traducción)
```

Ejemplos:

| Archivo                                   | document_id  | language |
| ----------------------------------------- | ------------ | -------- |
| `lta-gov-001-document-standard.md`        | LTA-GOV-001  | es       |
| `lta-gov-001-document-standard.en.md`     | LTA-GOV-001  | en       |
| `lta-chr-001-vision.md`                   | LTA-CHR-001  | es       |

---

## 18. Referencias normativas e informativas

### 18.1 Referencias normativas

Las siguientes especificaciones son parte normativa del presente estándar: su cumplimiento es obligatorio para todo documento bajo este régimen.

- Semantic Versioning 2.0.0
- YAML 1.2
- CommonMark
- ISO 8601
- ISO 639-1
- RFC 2119 (interpretación de los verbos modales del presente estándar, ver §3.2)

### 18.2 Referencias informativas

Las siguientes referencias se citan con fines contextuales y no son de cumplimiento obligatorio:

- Creative Commons Attribution 4.0 (CC BY 4.0)

La adopción de CC BY 4.0 como licencia por defecto es una decisión institucional, no una dependencia técnica del formato documental.

### 18.3 Referencias internas

Las referencias internas entre secciones de un mismo documento deben utilizar la numeración oficial (formato `§X` o `§X.Y`).

No deben emplearse referencias relativas como «arriba», «más adelante», «la sección anterior».

Excepción: referencias al historial de cambios o a secciones no numeradas pueden ser nominales.

El formulario `§X.Y` es preferido cuando se cita una subsección concreta.

---

## Historial de cambios

| Versión | Fecha      | Descripción       |
| ------- | ---------- | ----------------- |
| 0.1.0   | 2026-06-22 | Documento inicial |
| 0.1.1   | 2026-06-23 | Inclusión de metadata obligatoria conforme al estándar definido |
| 0.1.2   | 2026-06-25 | Corrección de inconsistencias internas y normalización documental |
| 0.2.0   | 2026-06-25 | Normalización de taxonomía documental con códigos, formalización de subtipos, modelo de aprobación con estados, valores controlados de metadata, política de traducciones con translation_of, SemVer documental con ejemplos aplicados |
| 0.3.0   | 2026-06-25 | Modelo conceptual documento/instancia/versión (§3.1-§3.3), verbos modales RFC 2119 (§3.2), definición de documento oficial y repositorio institucional (§2.1-§2.2), política de reemplazo de documentos (§5.3.1), conjuntos cerrados de metadata (§5.4), asignación de identificadores (§6.3), carácter normativo vs informativo (§7.4), extensibilidad del modelo (§7.5), ciclo de vida documental con transiciones permitidas (§8.1-§8.4), eliminación de `rejected` en approval.status, modelo de traducciones con independencia de versionado (§10.2), obligaciones de modificación y cambios incompatibles (§11.1-§11.2), formalización del historial de cambios (§12), convenciones de nombres de archivo (§17), referencias normativas e informativas (§18) |
---
