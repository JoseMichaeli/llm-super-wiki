# Esquema de concepto

## Propósito y ubicación

Una página de concepto define una idea, término, distinción o modelo mental
reutilizable dentro de Atlas-Wiki. Su objetivo es mantener un significado claro,
mostrar límites de uso y conectar el concepto con evidencia y aplicaciones.

- Directorio: `wiki/concepts/`
- Ruta: `wiki/concepts/<slug>.md`
- Nombre: término preferido en `kebab-case`

No debe crearse una página para una palabra de uso común que no necesite una
definición propia ni para una mención sin aplicación en la wiki.

## Metadatos

### Obligatorios

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `type` | texto | Siempre `concept`. |
| `title` | texto | Término preferido. |
| `status` | texto controlado | Madurez de la definición. |
| `created` | fecha | Creación de la página (`YYYY-MM-DD`). |
| `updated` | fecha | Último cambio material (`YYYY-MM-DD`). |

### Opcionales

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `aliases` | lista de textos | Sinónimos, siglas o variantes de búsqueda. |
| `broader_concepts` | lista de enlaces | Conceptos más generales. |
| `related_concepts` | lista de enlaces | Conceptos vinculados sin jerarquía directa. |
| `domains` | lista de textos o enlaces | Ámbitos donde se usa la definición. |

`status` admite:

- `draft`: definición inicial con evidencia o alcance incompletos;
- `established`: significado suficientemente respaldado y usado de forma estable;
- `contested`: existen definiciones incompatibles o debate material;
- `deprecated`: el término ya no se recomienda y apunta a su reemplazo.

## Cuerpo obligatorio

### `## Definición`

Ofrece una definición breve y autosuficiente. Debe indicar el sentido utilizado en
Atlas cuando el término tenga varios significados.

### `## Alcance y límites`

Explica qué casos incluye, cuáles excluye y en qué contexto deja de ser útil. Una
definición operacional debe declarar las condiciones bajo las cuales aplica.

### `## Explicación`

Desarrolla componentes, mecanismo o intuición sin repetir la definición. Puede
incluir ejemplos respaldados y contraejemplos aclaratorios.

### `## Relaciones`

Enlaza conceptos más amplios, específicos, relacionados, opuestos o frecuentemente
confundidos. Cada enlace debe explicar la relación.

### `## Aplicaciones en Atlas`

Enlaza proyectos, decisiones, requisitos, procesos o síntesis que utilicen el
concepto. Si todavía no hay una aplicación real, debe reconsiderarse la necesidad
de crear la página.

### `## Fuentes`

Enlaza las fichas de fuente que respaldan definición, terminología, límites y
variantes. Si Atlas adopta una definición propia, debe declararse como convención y
explicar en qué evidencia se basa.

## Secciones opcionales

- `## Ejemplos y contraejemplos`: casos que aclaran límites.
- `## Interpretaciones`: definiciones alternativas atribuidas.
- `## Historia del término`: evolución relevante y fechada.
- `## Preguntas abiertas`: aspectos aún no resueltos.

## Reglas

- Una página mantiene un concepto principal. Los sentidos sustancialmente distintos
  reciben páginas separadas y se desambiguan.
- Los alias ayudan a encontrar el concepto, pero no sustituyen la definición.
- No presentar una definición estipulada por Atlas como consenso externo.
- En estado `contested`, representar las principales interpretaciones con sus
  fuentes y no fabricar una conciliación.
- No duplicar teoría extensa de una fuente; sintetizarla y enlazar la evidencia.
- Los cambios que alteren el significado central deben conservarse en una sección
  histórica o documentarse en el log.

## Plantilla

```markdown
---
type: concept
title: "<Término preferido>"
status: <draft-established-contested-o-deprecated>
aliases: []
broader_concepts: []
related_concepts: []
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
---

# <Término preferido>

## Definición

<Definición breve en el sentido usado por Atlas.>

## Alcance y límites

<Qué incluye, qué excluye y dónde aplica.>

## Explicación

<Componentes, mecanismo o intuición.>

## Relaciones

- <concepto>: <naturaleza de la relación>

## Aplicaciones en Atlas

- <enlace y forma de aplicación>

## Fuentes

- <enlace-a-fuente-y-evidencia>
```

## Validación

- [ ] El concepto necesita una definición propia y tiene aplicación real.
- [ ] No duplica otro término o alias existente.
- [ ] La definición es breve, contextualizada y respaldada.
- [ ] Alcance, exclusiones y ambigüedades son visibles.
- [ ] Interpretaciones en conflicto están atribuidas.
- [ ] Las relaciones explican su naturaleza.
- [ ] Los enlaces relativos funcionan.
- [ ] El índice y el log se actualizaron si corresponde.
