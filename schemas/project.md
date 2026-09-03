# Esquema de proyecto

## Propósito y ubicación

Una página de proyecto describe una iniciativa temporal o evolutiva con un
propósito, alcance, responsables y resultados esperados. Es el punto de conexión
entre personas, organizaciones, requisitos, decisiones, procesos, conceptos y
fuentes.

- Directorio: `wiki/projects/`
- Ruta: `wiki/projects/<slug>.md`
- Nombre: estable, descriptivo y en `kebab-case`

No debe crearse un proyecto para una actividad aislada sin objetivo propio. Si el
contenido describe una forma recurrente de trabajar, corresponde a un proceso.

## Metadatos

Toda página comienza con YAML. Los campos no definidos aquí requieren una revisión
previa de este esquema.

### Obligatorios

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `type` | texto | Siempre `project`. |
| `title` | texto | Nombre oficial o reconocido. |
| `status` | texto controlado | Estado actual del proyecto. |
| `owners` | lista de enlaces o textos | Responsables; `unknown` si no se conocen. |
| `organizations` | lista de enlaces o textos | Organizaciones vinculadas; puede ser `[]`. |
| `started` | fecha, fecha parcial, `unknown` o `not-started` | Inicio real. |
| `created` | fecha | Creación de la página (`YYYY-MM-DD`). |
| `updated` | fecha | Último cambio material (`YYYY-MM-DD`). |

### Opcionales

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `target_end` | fecha, fecha parcial o `unknown` | Finalización prevista. |
| `ended` | fecha o fecha parcial | Finalización real. |
| `parent_project` | enlace | Proyecto del cual depende o forma parte. |
| `aliases` | lista de textos | Nombres anteriores o alternativos. |
| `confidentiality` | `public`, `internal` o `restricted` | Restricción de acceso. |

`status` admite:

- `proposed`: existe una propuesta, todavía no aprobada;
- `planned`: aprobado y preparado, aún sin ejecución;
- `active`: en ejecución;
- `paused`: detenido temporalmente;
- `completed`: alcanzó su condición de cierre;
- `cancelled`: terminó sin completar su objetivo;
- `archived`: se conserva como referencia histórica.

El estado debe reflejar evidencia, no una expectativa del agente.

## Cuerpo obligatorio

### `## Resumen`

Explica qué es el proyecto, por qué existe y cuál es su estado actual.

### `## Objetivo`

Describe el resultado que define el éxito. Debe diferenciarse de las actividades o
entregables usados para alcanzarlo.

### `## Alcance`

Debe contener:

```markdown
### Incluye

- <elemento dentro del alcance>

### No incluye

- <límite explícito o `No documentado todavía.`>
```

### `## Estado actual`

Resume avances, bloqueos y siguiente hito con fecha de vigencia. No reemplaza un
sistema de gestión de tareas.

### `## Relaciones`

Incluye, según existan:

- responsables y participantes;
- organizaciones;
- requisitos;
- decisiones;
- procesos;
- proyectos relacionados;
- conceptos relevantes.

Debe usarse `Ninguna documentada todavía.` cuando una relación obligatoria aún no
exista, sin crear enlaces ficticios.

### `## Fuentes`

Lista páginas de `wiki/sources/` que respaldan propósito, alcance, estado o
relaciones. Las afirmaciones sensibles al tiempo deben indicar fecha.

## Secciones opcionales

- `## Entregables`: resultados concretos producidos por el proyecto.
- `## Hitos`: eventos verificables con fecha, estado y fuente.
- `## Riesgos y dependencias`: condiciones que podrían afectar el resultado.
- `## Historia`: cambios materiales de nombre, alcance, estado o dirección.
- `## Preguntas abiertas`: asuntos documentados que aún requieren respuesta.

## Reglas

- Actualizar una página existente antes de crear otra para el mismo proyecto.
- No presentar una propuesta como proyecto aprobado.
- Conservar estados y decisiones históricas relevantes en **Historia** o mediante
  enlaces a decisiones.
- No duplicar el detalle mantenido por requisitos, decisiones o procesos; resumirlo
  y enlazar su página principal.
- Usar fechas o periodos de vigencia para información cambiante.
- No incluir credenciales, información personal innecesaria ni detalles
  restringidos en páginas de mayor visibilidad.

## Plantilla

```markdown
---
type: project
title: "<Nombre del proyecto>"
status: <valor-controlado>
owners:
  - <enlace-persona-o-unknown>
organizations: []
started: <YYYY-MM-DD-fecha-parcial-unknown-o-not-started>
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
---

# <Nombre del proyecto>

## Resumen

<Propósito y situación actual.>

## Objetivo

<Resultado que define el éxito.>

## Alcance

### Incluye

- <elemento>

### No incluye

- No documentado todavía.

## Estado actual

<Estado a fecha de YYYY-MM-DD.>

## Relaciones

### Responsables y participantes

- <enlace-o-unknown>

### Requisitos y decisiones

- Ninguna documentada todavía.

### Procesos y proyectos relacionados

- Ninguno documentado todavía.

## Fuentes

- <enlace-a-fuente-y-evidencia>
```

## Validación

- [ ] El proyecto no duplica una página existente.
- [ ] Objetivo, alcance y estado están diferenciados.
- [ ] El estado usa un valor permitido y está respaldado.
- [ ] Las relaciones importantes usan enlaces relativos válidos.
- [ ] La información temporal incluye fecha de vigencia.
- [ ] Las afirmaciones materiales tienen fuentes.
- [ ] `created` y `updated` son coherentes.
- [ ] El índice y el log se actualizaron si corresponde.
