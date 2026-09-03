# Esquema de persona

## Propósito y ubicación

Una página de persona registra únicamente el contexto profesional o intelectual
necesario para comprender su relación con Atlas-Wiki. No es un perfil biográfico
exhaustivo ni un expediente personal.

- Directorio: `wiki/people/`
- Ruta: `wiki/people/<slug>.md`
- Nombre: nombre reconocible en `kebab-case`; añadir un calificador solo para
  resolver homónimos.

Debe existir evidencia de una relación relevante antes de crear la página. Una
mención aislada no basta.

## Metadatos

### Obligatorios

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `type` | texto | Siempre `person`. |
| `title` | texto | Nombre público o profesional. |
| `status` | texto controlado | Vigencia de su relación documentada. |
| `created` | fecha | Creación de la página (`YYYY-MM-DD`). |
| `updated` | fecha | Último cambio material (`YYYY-MM-DD`). |

### Opcionales

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `preferred_name` | texto | Nombre usado por la persona, si está documentado. |
| `aliases` | lista de textos | Variantes necesarias para búsqueda o desambiguación. |
| `organizations` | lista de enlaces | Organizaciones relevantes. |
| `roles` | lista de textos | Roles documentados; el periodo se explica en el cuerpo. |
| `public_profiles` | lista de URL | Perfiles profesionales publicados por la persona. |

`status` admite:

- `active`: mantiene una relación vigente con al menos un contexto descrito;
- `historical`: su relación documentada pertenece al pasado;
- `unknown`: la vigencia no puede determinarse.

El estado se refiere a la relación con el contexto de la wiki, no a la condición de
la persona.

## Cuerpo obligatorio

### `## Resumen`

Identifica a la persona y explica por qué es relevante para Atlas-Wiki. Evita
valoraciones no atribuidas.

### `## Roles y responsabilidades`

Registra cada rol con organización o proyecto, periodo conocido y fuente. Los
títulos informales deben marcarse como tales.

### `## Participación y aportes`

Enlaza proyectos, decisiones, procesos, conceptos, fuentes o síntesis donde su
participación esté documentada. Diferencia autoría, responsabilidad, consulta,
aprobación y simple mención.

### `## Relaciones`

Lista organizaciones, proyectos y otras personas cuando la relación sea pertinente
y esté respaldada. No inferir jerarquías, afiliaciones ni relaciones personales.

### `## Fuentes`

Enlaza las fichas de fuente que respaldan la identidad, roles y aportes descritos.

## Secciones opcionales

- `## Trayectoria relevante`: cronología limitada al alcance de la wiki.
- `## Ideas y posiciones`: posturas explícitas, fechadas y atribuidas.
- `## Obras o recursos`: trabajos públicos relevantes.
- `## Desambiguación`: diferencias frente a personas homónimas.

## Privacidad y seguridad

- Incluir solo información necesaria, pertinente y respaldada.
- No registrar domicilios, teléfonos, identificadores gubernamentales, credenciales,
  datos familiares, información médica ni otros datos personales sensibles.
- No convertir datos públicos en un perfil invasivo por acumulación.
- No inferir atributos sensibles, intenciones, desempeño o relaciones privadas.
- Respetar la confidencialidad de las fuentes y resumir únicamente lo autorizado.
- Corregir información de identidad con cuidado y conservar la trazabilidad del
  cambio cuando sea material.

## Plantilla

```markdown
---
type: person
title: "<Nombre público o profesional>"
status: <active-historical-o-unknown>
organizations: []
roles: []
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
---

# <Nombre>

## Resumen

<Identificación y relevancia dentro del alcance de Atlas-Wiki.>

## Roles y responsabilidades

- <Rol> — <organización-o-proyecto>, <periodo> ([fuente](../sources/fuente.md))

## Participación y aportes

- <tipo de participación>: <enlace y descripción respaldada>

## Relaciones

- <relación relevante o `Ninguna documentada todavía.`>

## Fuentes

- <enlace-a-fuente-y-evidencia>
```

## Validación

- [ ] La persona es relevante más allá de una mención aislada.
- [ ] No existe otra página para la misma persona.
- [ ] Roles, periodos y relaciones están atribuidos.
- [ ] No se infieren intenciones, jerarquías ni atributos sensibles.
- [ ] No hay datos personales innecesarios.
- [ ] Los enlaces y fuentes funcionan.
- [ ] El estado describe la vigencia contextual correctamente.
- [ ] El índice y el log se actualizaron si corresponde.
