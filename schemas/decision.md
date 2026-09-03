# Esquema de decisión

## Propósito y ubicación

Una página de decisión conserva una elección relevante junto con su contexto,
alternativas, responsables, razones y consecuencias. Permite comprender por qué se
eligió un curso de acción y cómo evoluciona, sin reescribir la historia.

- Directorio: `wiki/decisions/`
- Ruta: `wiki/decisions/<slug>.md`
- Nombre recomendado: `<tema-o-eleccion>-<calificador-opcional>.md`

No debe crearse una decisión para una preferencia informal sin impacto ni para una
idea que todavía no ha sido elegida. Las propuestas pueden documentarse dentro del
proyecto hasta que exista una decisión o un proceso formal de evaluación.

## Metadatos

### Obligatorios

| Campo             | Tipo                                        | Descripción                                    |
| ----------------- | ------------------------------------------- | ---------------------------------------------- |
| `type`            | texto                                       | Siempre `decision`.                            |
| `title`           | texto                                       | Elección expresada de forma reconocible.       |
| `status`          | texto controlado                            | Estado de la decisión.                         |
| `decided`         | fecha, fecha parcial, `pending` o `unknown` | Momento de decisión.                           |
| `decision_makers` | lista de enlaces o textos                   | Autoridad responsable; `unknown` si no consta. |
| `projects`        | lista de enlaces                            | Proyectos afectados; puede ser `[]`.           |
| `created`         | fecha                                       | Creación de la página (`YYYY-MM-DD`).          |
| `updated`         | fecha                                       | Último cambio material (`YYYY-MM-DD`).         |

### Opcionales

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `effective` | fecha o fecha parcial | Inicio de vigencia. |
| `review_on` | fecha | Revisión prevista. |
| `supersedes` | lista de enlaces | Decisiones reemplazadas. |
| `superseded_by` | enlace | Decisión que la reemplaza. |
| `scope` | lista de enlaces | Organizaciones, procesos o requisitos afectados. |

`status` admite:

- `proposed`: decisión formalmente planteada, aún no resuelta;
- `accepted`: aprobada y vigente o pendiente de implementación;
- `rejected`: alternativa evaluada y descartada formalmente;
- `superseded`: reemplazada por otra decisión;
- `reversed`: revocada sin ser sustituida directamente;
- `expired`: perdió vigencia por una condición temporal documentada.

## Cuerpo obligatorio

### `## Decisión`

Declara con precisión qué se decidió. En estado `proposed`, formula qué se propone
decidir y deja explícito que aún no está aprobado.

### `## Contexto`

Describe el problema, restricciones, supuestos y fuerzas existentes al momento de
decidir. Debe ser suficiente para interpretar la elección en su contexto histórico.

### `## Opciones consideradas`

Enumera opciones reales, incluida la elegida. Para cada una, resume ventajas,
costos, riesgos y evidencia disponible en ese momento. No inventar alternativas
para completar la sección.

### `## Razones`

Explica por qué se tomó la decisión y qué criterios pesaron más. Distingue razones
documentadas de reconstrucciones posteriores.

### `## Consecuencias`

Registra efectos esperados, compromisos, costos y riesgos aceptados. Los resultados
observados posteriormente deben fecharse y diferenciarse de las expectativas.

### `## Relaciones`

Enlaza proyectos, requisitos, procesos, personas, organizaciones y decisiones
relacionadas, indicando el tipo de relación.

### `## Fuentes`

Enlaza la evidencia de la decisión, su autoridad, fecha, contexto y razones.

## Secciones opcionales

- `## Implementación`: acciones o cambios necesarios, enlazados en lugar de
  duplicar planes detallados.
- `## Resultados observados`: efectos medidos después de la decisión.
- `## Criterios de revisión`: condiciones para reconsiderarla.
- `## Historia`: cambios de estado y aclaraciones relevantes.

## Reglas

- Una decisión aceptada es inmutable en su significado histórico. Si cambia la
  elección, crear o enlazar la decisión que la reemplaza y actualizar estados.
- Corregir errores de forma es válido; alterar contexto, razones o alcance requiere
  documentar el cambio.
- No usar seguridad narrativa para ocultar desacuerdo o incertidumbre.
- No confundir quién documentó la decisión con quién tenía autoridad para tomarla.
- Cada opción, razón o consecuencia material debe estar respaldada o marcada como
  inferencia retrospectiva.
- Una decisión rechazada se documenta solo cuando conservar su evaluación aporta
  valor y existe evidencia formal.

## Plantilla

```markdown
---
type: decision
title: "<Elección o asunto decidido>"
status: <valor-controlado>
decided: <YYYY-MM-DD-fecha-parcial-pending-o-unknown>
decision_makers:
  - <enlace-o-unknown>
projects: []
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
---

# <Título de la decisión>

## Decisión

<Qué se decidió o qué está propuesto.>

## Contexto

<Problema, restricciones y supuestos del momento.>

## Opciones consideradas

### <Opción elegida>

- Ventajas: <...>
- Costos y riesgos: <...>

### <Otra opción>

- Ventajas: <...>
- Costos y riesgos: <...>

## Razones

<Criterios y motivos documentados.>

## Consecuencias

- <efecto, compromiso o riesgo aceptado>

## Relaciones

- <enlace y naturaleza de la relación>

## Fuentes

- <enlace-a-fuente-y-evidencia>
```

## Validación

- [ ] Existe una elección o propuesta formal que merece trazabilidad.
- [ ] Estado, fecha y autoridad están respaldados.
- [ ] La decisión está separada de su contexto y sus consecuencias.
- [ ] Las opciones corresponden a alternativas realmente consideradas.
- [ ] Las inferencias retrospectivas están marcadas.
- [ ] Reemplazos o reversiones conservan la historia.
- [ ] Los enlaces relativos funcionan.
- [ ] El índice y el log se actualizaron si corresponde.
