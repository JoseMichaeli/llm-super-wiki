# Esquema de requisito

## Propósito y ubicación

Una página de requisito describe una necesidad, capacidad, restricción o condición
verificable que un proyecto, producto, servicio o proceso debe satisfacer. Debe
permitir comprender su origen, alcance, prioridad y forma de verificación.

- Directorio: `wiki/requirements/`
- Ruta: `wiki/requirements/<slug>.md`
- Nombre: descriptivo y estable en `kebab-case`

No debe crearse un requisito para una tarea de implementación, una solución elegida
sin necesidad explícita o una aspiración imposible de verificar.

## Metadatos

### Obligatorios

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `type` | texto | Siempre `requirement`. |
| `title` | texto | Capacidad o condición requerida. |
| `requirement_kind` | texto controlado | Naturaleza del requisito. |
| `status` | texto controlado | Estado dentro de su ciclo de vida. |
| `priority` | texto controlado | Prioridad documentada. |
| `owners` | lista de enlaces o textos | Responsables de aclararlo y aceptarlo; `unknown` si no constan. |
| `projects` | lista de enlaces | Contextos donde aplica; puede ser `[]` solo si el alcance se explica. |
| `created` | fecha | Creación de la página (`YYYY-MM-DD`). |
| `updated` | fecha | Último cambio material (`YYYY-MM-DD`). |

### Opcionales

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `effective` | fecha | Inicio de vigencia. |
| `target` | fecha o fecha parcial | Fecha objetivo documentada. |
| `supersedes` | lista de enlaces | Requisitos reemplazados. |
| `superseded_by` | enlace | Requisito que lo reemplaza. |
| `parent_requirement` | enlace | Requisito más amplio del que depende. |

`requirement_kind` admite:

- `business`: resultado o necesidad de negocio;
- `user`: capacidad o resultado necesario para una persona usuaria;
- `functional`: comportamiento que debe ofrecer el sistema o proceso;
- `quality`: atributo medible como rendimiento, disponibilidad o usabilidad;
- `constraint`: límite técnico, legal, temporal, presupuestario u organizacional;
- `compliance`: obligación regulatoria, contractual o normativa.

`status` admite `proposed`, `accepted`, `in-progress`, `satisfied`, `deferred`,
`rejected`, `superseded` y `obsolete`.

`priority` admite `critical`, `high`, `medium`, `low` y `unassigned`. La prioridad
debe provenir de una decisión o autoridad documentada, no del juicio silencioso del
agente.

## Cuerpo obligatorio

### `## Enunciado`

Formula una sola necesidad o condición de manera clara y verificable. Debe evitar
mezclar varios requisitos unidos por expresiones como “y además”.

### `## Justificación`

Explica qué necesidad origina el requisito, quién se beneficia o qué riesgo evita.
No confundir la justificación con la solución propuesta.

### `## Alcance`

Indica dónde aplica, bajo qué condiciones y qué queda fuera. Define términos
ambiguos mediante enlaces a conceptos.

### `## Criterios de aceptación`

Lista condiciones observables que permiten concluir si el requisito está
satisfecho. Deben poder evaluarse sin depender de apreciaciones vagas.

### `## Verificación`

Describe el método y la evidencia esperada: prueba, inspección, demostración,
análisis, medición o revisión documental. Si aún no está definido, indicarlo.

### `## Dependencias y relaciones`

Enlaza proyectos, requisitos padres o relacionados, decisiones, procesos, personas
u organizaciones responsables. Señala conflictos conocidos.

### `## Fuentes`

Enlaza evidencia del origen, prioridad, aceptación y cambios del requisito.

## Secciones opcionales

- `## Supuestos`: condiciones tomadas como ciertas que afectan su interpretación.
- `## Riesgos`: consecuencias de incumplimiento o implementación incorrecta.
- `## Historia`: cambios materiales y razones.
- `## Evidencia de cumplimiento`: resultados fechados que respaldan `satisfied`.

## Reglas

- Describir la necesidad antes que una implementación concreta, salvo que la
  solución sea en sí una restricción autorizada.
- Usar métricas, umbrales, actores y condiciones cuando sean necesarios para hacer
  el enunciado verificable.
- No cambiar silenciosamente un requisito aceptado. Un cambio material debe quedar
  en **Historia** o producir un requisito sucesor cuando altere su identidad.
- `satisfied` exige evidencia y fecha; no equivale a “trabajo terminado”.
- Resolver duplicados y solapamientos mediante enlace, consolidación autorizada o
  relación padre-hijo.
- Requisitos en conflicto permanecen visibles hasta una decisión respaldada.

## Plantilla

```markdown
---
type: requirement
title: "<Capacidad o condición requerida>"
requirement_kind: <valor-controlado>
status: proposed
priority: unassigned
owners:
  - unknown
projects: []
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
---

# <Título del requisito>

## Enunciado

<Una necesidad o condición clara y verificable.>

## Justificación

<Origen, beneficiario o riesgo que explica la necesidad.>

## Alcance

<Dónde aplica, condiciones y exclusiones.>

## Criterios de aceptación

- [ ] <condición observable>

## Verificación

<Método y evidencia esperada o `Pendiente de definición.`>

## Dependencias y relaciones

- <enlace y naturaleza de la relación o `Ninguna documentada todavía.`>

## Fuentes

- <enlace-a-fuente-y-evidencia>
```

## Validación

- [ ] El enunciado contiene una sola necesidad o condición.
- [ ] La necesidad está separada de la solución.
- [ ] Tipo, estado y prioridad usan valores permitidos.
- [ ] Alcance y términos ambiguos están definidos.
- [ ] Los criterios de aceptación son observables.
- [ ] El método de verificación existe o está marcado como pendiente.
- [ ] Origen, prioridad y cumplimiento tienen evidencia.
- [ ] Los enlaces funcionan y los conflictos siguen visibles.
- [ ] El índice y el log se actualizaron si corresponde.
