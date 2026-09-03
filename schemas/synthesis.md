# Esquema de síntesis

## Propósito y ubicación

Una página de síntesis integra evidencia procedente de varias fuentes o páginas
para responder una pregunta, comparar perspectivas, explicar un estado de situación
o producir una visión de conjunto. Su valor está en relacionar conocimiento, no en
repetir resúmenes individuales.

- Directorio: `wiki/syntheses/`
- Ruta: `wiki/syntheses/<slug>.md`
- Nombre: tema o pregunta abreviada en `kebab-case`

Una síntesis es conocimiento derivado y revisable; nunca debe presentarse como
fuente primaria. Si solo existe una fuente y no hay integración o análisis, el
contenido corresponde normalmente a su página de fuente o a una página temática.

## Metadatos

### Obligatorios

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `type` | texto | Siempre `synthesis`. |
| `title` | texto | Título orientado al asunto o resultado. |
| `synthesis_kind` | texto controlado | Forma principal de integración. |
| `status` | texto controlado | Madurez y vigencia. |
| `question` | texto | Pregunta o propósito analítico que delimita la síntesis. |
| `sources` | lista de enlaces | Páginas de fuente utilizadas. |
| `as_of` | fecha | Corte temporal del análisis (`YYYY-MM-DD`). |
| `created` | fecha | Creación de la página (`YYYY-MM-DD`). |
| `updated` | fecha | Último cambio material (`YYYY-MM-DD`). |

### Opcionales

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `scope` | lista de enlaces | Proyectos, organizaciones, procesos o conceptos cubiertos. |
| `time_range` | texto | Periodo estudiado cuando difiere de `as_of`. |
| `authors` | lista de enlaces o textos | Personas o agentes responsables de la síntesis. |
| `supersedes` | enlace | Síntesis anterior reemplazada explícitamente. |
| `review_on` | fecha | Revisión prevista para asuntos cambiantes. |

`synthesis_kind` admite:

- `overview`: visión de conjunto de un dominio;
- `analysis`: explicación razonada de evidencia y relaciones;
- `comparison`: contraste explícito entre alternativas o perspectivas;
- `brief`: respuesta concisa orientada a una necesidad concreta;
- `timeline`: integración cronológica de hechos y cambios;
- `state-of-knowledge`: qué se sabe, qué se discute y qué falta por conocer.

`status` admite:

- `draft`: integración incompleta o pendiente de revisión;
- `current`: representa adecuadamente la evidencia disponible al corte;
- `contested`: existen interpretaciones incompatibles no resueltas;
- `stale`: nueva evidencia o el paso del tiempo exige revisión;
- `superseded`: otra síntesis la reemplaza.

## Cuerpo obligatorio

### `## Pregunta y alcance`

Formula la pregunta, audiencia o propósito, límites temáticos, periodo cubierto y
exclusiones. Debe permitir determinar qué evidencia es pertinente.

### `## Respuesta breve`

Ofrece la conclusión principal en pocos párrafos. Debe expresar incertidumbre y no
ser más concluyente que la evidencia presentada después.

### `## Hallazgos`

Presenta las conclusiones parciales que sostienen la respuesta. Cada hallazgo debe:

- expresar una afirmación concreta;
- enlazar las fuentes y, cuando sea posible, sus identificadores de evidencia;
- distinguir observación, consenso entre fuentes e inferencia;
- indicar fecha o periodo si puede cambiar con el tiempo.

Formato recomendado:

```markdown
### H1 — <Hallazgo>

<Explicación y alcance del hallazgo.>

- Evidencia: [Fuente A](../sources/fuente-a.md#evidencia-relevante),
  [Fuente B](../sources/fuente-b.md#evidencia-relevante)
- Tipo: <hecho-documentado-consenso-inferencia>
```

Los identificadores `H1`, `H2`, etc. son locales y deben mantenerse estables cuando
otras páginas los referencien.

### `## Análisis`

Explica cómo se relacionan los hallazgos, qué patrones aparecen y qué razonamiento
conduce a la respuesta. Las inferencias deben señalarse de forma explícita y
mostrar la evidencia que las sustenta.

### `## Evidencia en conflicto`

Describe contradicciones, desacuerdos de interpretación o diferencias de alcance y
fecha. Si no se encontraron, usar `No se identificó evidencia material en conflicto
en las fuentes consultadas.` Esto no implica que exista consenso universal.

### `## Limitaciones y preguntas abiertas`

Expone vacíos de fuentes, sesgos de selección, calidad o actualidad insuficiente,
supuestos y preguntas que la evidencia no permite responder.

### `## Relaciones`

Enlaza páginas de proyectos, personas, organizaciones, decisiones, requisitos,
conceptos, procesos y otras síntesis relacionadas. No duplica el catálogo ya
declarado en `sources`.

## Secciones opcionales

- `## Método`: estrategia de selección, comparación o análisis cuando afecte la
  interpretación.
- `## Cronología`: eventos integrados en orden temporal.
- `## Comparación`: criterios y alternativas en una tabla o estructura uniforme.
- `## Implicaciones`: consecuencias razonadas para proyectos o decisiones, marcadas
  como análisis y no como decisiones aprobadas.
- `## Recomendaciones`: propuestas explícitas que requieren evaluación humana; no
  deben presentarse como decisiones existentes.

## Reglas de evidencia y razonamiento

- Toda conclusión material debe enlazar evidencia identificable.
- La cantidad de fuentes no sustituye su pertinencia, independencia o calidad para
  la afirmación concreta.
- No usar una síntesis como único respaldo de otra síntesis cuando las fuentes
  primarias o sus fichas estén disponibles.
- Diferenciar claramente hechos documentados, interpretación, inferencia,
  recomendación y decisión.
- No ocultar fuentes contrarias ni resolver contradicciones mediante redacción
  ambigua.
- Declarar el corte `as_of`; `current` significa vigente a ese corte, no verdadero
  indefinidamente.
- Una síntesis puede citar páginas temáticas para contexto, pero `sources` debe
  contener las fichas de evidencia utilizadas.
- No copiar extensamente las fuentes. Integrar mediante paráfrasis y atribución.

## Actualización y reemplazo

Una síntesis debe revisarse cuando aparece evidencia que cambia un hallazgo,
resuelve o introduce una contradicción, amplía materialmente el alcance o vuelve
obsoleto el corte temporal.

Al actualizar:

1. revisar la pregunta y mantener el alcance original, salvo cambio explícito;
2. conservar identificadores de hallazgos aún vigentes;
3. añadir nuevos hallazgos al final de la secuencia;
4. marcar hallazgos superados y explicar por qué, en vez de borrarlos si conservan
   valor histórico;
5. actualizar `sources`, `as_of`, `updated`, conflictos y limitaciones;
6. usar `superseded` y crear una nueva síntesis cuando cambien sustancialmente la
   pregunta, el método o el alcance.

## Plantilla

```markdown
---
type: synthesis
title: "<Título de la síntesis>"
synthesis_kind: <valor-controlado>
status: draft
question: "<Pregunta o propósito analítico>"
sources:
  - <enlace-a-fuente>
as_of: <YYYY-MM-DD>
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
---

# <Título de la síntesis>

## Pregunta y alcance

<Pregunta, propósito, periodo, inclusión y exclusiones.>

## Respuesta breve

<Conclusión principal calibrada a la evidencia.>

## Hallazgos

### H1 — <Hallazgo>

<Explicación y alcance.>

- Evidencia: <enlaces-a-fuentes-y-evidencias>
- Tipo: <hecho-documentado-consenso-o-inferencia>

## Análisis

<Relaciones y razonamiento que conectan los hallazgos.>

## Evidencia en conflicto

<Contradicciones atribuidas o declaración limitada de que no se identificaron.>

## Limitaciones y preguntas abiertas

- <limitación, supuesto o pregunta>

## Relaciones

- <enlace y naturaleza de la relación>
```

## Validación

- [ ] Integra varias evidencias o páginas y no duplica una ficha de fuente.
- [ ] La pregunta, el alcance y el corte temporal están definidos.
- [ ] La respuesta breve coincide con los hallazgos.
- [ ] Cada hallazgo material tiene fuentes identificables.
- [ ] Hechos, consenso, inferencias y recomendaciones están diferenciados.
- [ ] Las contradicciones y fuentes contrarias son visibles.
- [ ] Limitaciones y preguntas abiertas están declaradas.
- [ ] Estado, fechas e identificadores son coherentes.
- [ ] Los enlaces relativos funcionan.
- [ ] El índice y el log se actualizaron si corresponde.
