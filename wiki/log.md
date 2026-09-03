# Registro de cambios de Atlas-Wiki

Este archivo conserva la historia material de la base de conocimiento: qué cambió,
por qué cambió, qué evidencia o instrucción lo motivó y qué páginas resultaron
afectadas. Complementa el historial de versiones del repositorio; no lo sustituye.

El registro está dirigido tanto a personas como a agentes. Debe permitir reconstruir
la evolución de Atlas-Wiki sin convertirlo en una lista de cada edición menor.

## Qué debe registrarse

Se registra un cambio cuando altera materialmente el conocimiento, su estructura o
las reglas con las que se mantiene. Esto incluye:

- ingreso, reemplazo, rechazo o pérdida de disponibilidad de una fuente;
- ingreso de evidencia en `raw/documents/`, `raw/conversations/`, `raw/media/`,
  `raw/datasets/` o `raw/other/`;
- ingestión o reemplazo de un pack en `raw/sub_wiki/`;
- creación, retiro, traslado o cambio de nombre de una página;
- actualización sustancial de afirmaciones, relaciones, alcance o estado;
- aparición, modificación o resolución de una contradicción;
- creación o reemplazo de una síntesis;
- cambio en `AGENTS.md`, `wiki/index.md` o cualquier archivo de `schemas/`;
- reorganización de directorios o convenciones de navegación;
- corrección de un error que haya afectado la interpretación del conocimiento.

No es necesario registrar:

- correcciones ortográficas o gramaticales sin cambio de significado;
- ajustes de formato que no alteren estructura ni navegación;
- reparación de un enlace cuando su destino y significado no cambiaron;
- ediciones transitorias realizadas y revertidas dentro de la misma tarea.

Si existe duda razonable sobre el impacto, se prefiere registrar una entrada breve.

## Orden y granularidad

- Las entradas se ordenan en cronología inversa: la más reciente aparece primero.
- Una tarea coherente produce una sola entrada, aunque afecte varios archivos.
- Los cambios independientes deben registrarse por separado aunque ocurran el mismo
  día.
- No se debe generar una entrada por archivo cuando todos forman parte del mismo
  cambio conceptual.
- Las fechas usan la zona horaria de trabajo de Atlas, actualmente
  `America/Bogota`.

## Identificador de entrada

Cada entrada usa un identificador estable con este formato:

```text
LOG-YYYYMMDD-NN
```

`NN` es una secuencia de dos dígitos dentro del día, comenzando en `01`. Si una
entrada se añade entre otras ya existentes, recibe el siguiente número disponible;
los identificadores anteriores nunca se renumeran.

Ejemplo: `LOG-20260824-02`.

## Tipos de cambio

Cada entrada declara uno o varios valores de esta lista:

| Tipo | Uso |
| --- | --- |
| `governance` | Reglas de operación, autoridad o comportamiento de agentes. |
| `schema` | Creación o modificación de contratos de conocimiento. |
| `source` | Cambios en el catálogo o estado de fuentes. |
| `knowledge` | Creación o actualización material de páginas de conocimiento. |
| `synthesis` | Creación o revisión de conocimiento integrado. |
| `navigation` | Cambios en índice, rutas o estructura navegable. |
| `conflict` | Aparición o tratamiento de evidencia contradictoria. |
| `correction` | Reparación de un error semántico previamente publicado. |

Los tipos describen el cambio, no el directorio donde ocurrió.

## Formato obligatorio

Cada entrada conserva esta estructura:

```markdown
## LOG-YYYYMMDD-NN — <Resumen breve>

- **Fecha:** YYYY-MM-DD
- **Tipos:** `<tipo>`, `<tipo>`
- **Responsable:** <persona, agente o `no documentado`>
- **Motivo:** <instrucción, fuente, decisión o necesidad que originó el cambio>
- **Archivos afectados:**
  - [`ruta/archivo.md`](ruta/archivo.md)

### Cambio

<Qué se añadió, modificó, reemplazó o retiró.>

### Impacto

<Cómo cambia la navegación, interpretación o mantenimiento de la wiki. Usar
`Sin impacto adicional identificado.` cuando corresponda.>

### Trazabilidad

- <enlace a la fuente, decisión, requisito o instrucción registrada; si no existe
  una página enlazable, describir el origen sin inventar una referencia>
```

Las rutas de **Archivos afectados** son relativas a `wiki/log.md`. Para archivos
dentro de `wiki/`, comienzan sin `wiki/`; para archivos en la raíz o `schemas/`,
comienzan con `../`.

## Reglas de redacción

- Describir hechos realizados, no intenciones futuras.
- Ser concreto: indicar qué cambió y su efecto, sin copiar el contenido completo de
  los archivos.
- Enlazar todos los archivos materialmente afectados.
- No atribuir un cambio a una persona o fuente sin evidencia.
- No incluir razonamiento interno, conversaciones completas, credenciales, secretos
  ni datos personales innecesarios.
- Distinguir la causa del cambio de quien lo ejecutó.
- Si una ingestión crea o actualiza conocimiento, enlazar tanto la página de fuente
  como las páginas derivadas relevantes.
- Si una decisión reemplaza conocimiento anterior, enlazar ambas versiones o
  decisiones y describir qué permanece históricamente válido.

## Correcciones y reversión

Las entradas publicadas no deben borrarse ni reescribirse para ocultar un error.

- Un error meramente tipográfico en la propia entrada puede corregirse directamente.
- Un error en fecha, alcance, autoría, causa o impacto requiere una nueva entrada de
  tipo `correction` que enlace el identificador corregido.
- La reversión de un cambio material recibe una entrada nueva. Debe explicar qué se
  revirtió, por qué y qué conocimiento vuelve a estar vigente.
- Si una entrada fue creada por completo por equivocación, se conserva y se marca
  al inicio de **Cambio** como `Anulada por LOG-YYYYMMDD-NN`, enlazando o nombrando la
  entrada correctiva.

## Mantenimiento

Antes de finalizar una tarea material, el agente debe:

1. determinar si el cambio cumple los criterios de registro;
2. buscar la secuencia disponible para la fecha;
3. añadir una entrada completa al inicio de **Entradas**;
4. comprobar enlaces y archivos afectados;
5. confirmar que el registro describe el estado guardado, no trabajo pendiente.

Cuando el archivo crezca, las entradas antiguas pueden trasladarse a archivos
anuales como `logs/2026.md`, pero solo con autorización explícita y manteniendo en
este archivo enlaces claros hacia el archivo histórico. Los identificadores no se
modifican durante el traslado.

## Entradas

## LOG-20260902-02 — Carpetas de evidencia suelta en `raw/`

- **Fecha:** 2026-09-02
- **Tipos:** `governance`, `navigation`
- **Responsable:** Agente, bajo dirección de la persona usuaria
- **Motivo:** Hacía falta distinguir documentos, conversaciones y demás evidencia
  suelta de las wikis completas en `raw/sub_wiki/`.
- **Archivos afectados:**
  - [`../AGENTS.md`](../AGENTS.md)
  - [`../schemas/source.md`](../schemas/source.md)
  - [`index.md`](index.md)
  - [`log.md`](log.md)

### Cambio

Se documentaron y crearon `raw/documents/`, `raw/conversations/`, `raw/media/`,
`raw/datasets/` y `raw/other/`. La ingestión ordinaria copia ahí; `@subir_wiki`
sigue usando solo `raw/sub_wiki/`.

### Impacto

Las fuentes que no son un pack tienen carpeta propia. No se añadió conocimiento
de dominio.

### Trazabilidad

- Instrucción de agregar los directorios de `raw/` para documentos normales,
  conversaciones y evidencia análoga.

## LOG-20260902-01 — Fundación de super_wiki con ingestión `@subir_wiki`

- **Fecha:** 2026-09-02
- **Tipos:** `governance`, `navigation`, `schema`
- **Responsable:** Agente, bajo dirección de la persona usuaria
- **Motivo:** Construcción inicial de Atlas-Wiki en el repositorio `super_wiki`,
  con soporte para ingerir y consultar wikis completas mediante `@subir_wiki`.
- **Archivos afectados:**
  - [`../AGENTS.md`](../AGENTS.md)
  - [`index.md`](index.md)
  - [`../schemas/source.md`](../schemas/source.md)
  - [`../schemas/project.md`](../schemas/project.md)
  - [`../schemas/person.md`](../schemas/person.md)
  - [`../schemas/organization.md`](../schemas/organization.md)
  - [`../schemas/decision.md`](../schemas/decision.md)
  - [`../schemas/requirement.md`](../schemas/requirement.md)
  - [`../schemas/concept.md`](../schemas/concept.md)
  - [`../schemas/process.md`](../schemas/process.md)
  - [`../schemas/synthesis.md`](../schemas/synthesis.md)
  - [`log.md`](log.md)

### Cambio

Se estableció el contrato operativo, el mapa navegable, los nueve tipos de
página y este registro. `source_kind` incluye `wiki-pack`. `@subir_wiki` copia
un árbol a `raw/sub_wiki/<slug>/` y, si esa ruta ya existe, la elimina y carga
de nuevo el pack. El agente puede consultar el pack y su `raw/` interno cuando
`wiki/` no alcanza.

### Impacto

El repositorio puede recibir fuentes sueltas y wikis completas con el mismo
modelo de trazabilidad, sin un tipo de página extra ni un segundo contrato. No
se incorporó conocimiento de dominio.

### Trazabilidad

- Instrucción de crear `super_wiki` como wiki inicial, sin fuentes ni páginas de
  conocimiento.
