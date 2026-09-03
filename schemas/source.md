# Esquema de fuente

## 1. Propósito

Una página de fuente representa una unidad de evidencia utilizada por Atlas-Wiki.
Su función es identificar el material original, conservar su procedencia, resumir
su contenido y conectar las afirmaciones extraídas con las páginas de conocimiento
que las utilizan.

La página de fuente no reemplaza el material original ni constituye por sí misma
una validación de todo lo que este afirma. Es una ficha de trazabilidad mantenida
en `wiki/sources/`.

Una wiki completa ingerida con `@subir_wiki` es también una fuente, con
`source_kind: wiki-pack`. No existe un tipo de página adicional para ese caso.

## 2. Ubicación y nombre

- Directorio: `wiki/sources/`
- Formato: Markdown (`.md`)
- Nombre: `kebab-case`
- Ruta esperada: `wiki/sources/<slug>.md`

El nombre debe ser estable y suficientemente distintivo. Se recomienda formarlo a
partir del autor u organización, un título abreviado y, cuando ayude a distinguir
versiones, el año.

Para un `wiki-pack`, el `<slug>` de la ficha coincide con el de
`raw/sub_wiki/<slug>/`.

Ejemplos:

- `manual-operativo-atlas-2026.md`
- `entrevista-ana-perez-arquitectura.md`
- `repositorio-equipo-plataforma.md`

No debe usarse como nombre un identificador temporal, una fecha de descarga aislada
o expresiones genéricas como `documento-1.md`.

## 3. Relación con el material original

El material original debe estar en `raw/` o en una ubicación externa autorizada.
La página de fuente debe apuntar a él de forma inequívoca:

- Para fuentes locales, usar una ruta relativa desde la página hasta el archivo
  o carpeta en `raw/`, según la tabla de `AGENTS.md` §3:
  `documents/`, `conversations/`, `media/`, `datasets/`, `other/` o
  `sub_wiki/<slug>/`.
- Para un `wiki-pack`, `origin` apunta al directorio
  `../../raw/sub_wiki/<slug>/`. No usar las otras carpetas de `raw/` para un pack.
- Para fuentes externas, conservar la URL canónica y la fecha de acceso.
- Para comunicaciones o fuentes no públicas, registrar un localizador autorizado
  que no exponga información sensible.
- Si el original deja de estar disponible, conservar su localizador y marcar la
  disponibilidad; no eliminar la ficha ni presentar el resumen como sustituto
  exacto del original.

Los agentes no deben modificar el material existente en `raw/` durante la creación
o actualización de una página de fuente, salvo el reemplazo de
`raw/sub_wiki/<slug>/` autorizado por `@subir_wiki` en `AGENTS.md` §16.

## 4. Metadatos

Toda página comienza con un bloque YAML. Los campos no definidos aquí no deben
añadirse sin actualizar previamente este esquema.

### Campos obligatorios

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `type` | texto | Siempre `source`. |
| `title` | texto | Título humano y reconocible de la fuente. |
| `source_kind` | texto controlado | Naturaleza del material original. |
| `origin` | texto | Ruta local, URL o localizador autorizado del original. |
| `authors` | lista de textos o enlaces | Personas u organizaciones responsables; usar `unknown` si no se conocen. |
| `published` | fecha, fecha parcial o `unknown` | Fecha atribuida a la publicación o producción original. |
| `accessed` | fecha o `not-applicable` | Fecha de obtención o consulta en formato `YYYY-MM-DD`. |
| `language` | texto | Código BCP 47, por ejemplo `es`, `en` o `es-CO`. |
| `status` | texto controlado | Estado del procesamiento dentro de Atlas-Wiki. |
| `created` | fecha | Creación de la ficha, en formato `YYYY-MM-DD`. |
| `updated` | fecha | Última modificación material, en formato `YYYY-MM-DD`. |

### Campos opcionales

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `version` | texto | Versión, edición, revisión o identificador publicado. |
| `publisher` | texto o enlace | Entidad que publicó o distribuyó el material. |
| `archived_at` | URL | Copia archivada autorizada, si existe. |
| `content_hash` | texto | Algoritmo y huella del archivo local para verificar identidad. |
| `confidentiality` | texto controlado | Restricción de acceso cuando no sea `public`. |
| `supersedes` | enlace | Fuente anterior reemplazada explícitamente por esta. |
| `superseded_by` | enlace | Fuente posterior que reemplaza explícitamente a esta. |
| `layout_kind` | texto controlado | Solo si `source_kind` es `wiki-pack`. |

### Valores controlados

`source_kind` admite:

- `article`
- `book`
- `dataset`
- `document`
- `email`
- `image`
- `interview`
- `meeting`
- `message`
- `paper`
- `presentation`
- `repository`
- `transcript`
- `video`
- `webpage`
- `wiki-pack`
- `other`

Si se usa `other`, la sección **Procedencia** debe explicar la naturaleza del
material.

`layout_kind`, cuando se declare, admite:

- `atlas-wiki`: el pack incluye `AGENTS.md` y `wiki/` o `schemas/`;
- `markdown-tree`: árbol Markdown u otra wiki sin ese contrato;
- `other`: explicar en **Procedencia**.

`status` admite:

- `registered`: la fuente está identificada, pero aún no fue examinada por completo;
- `reviewed`: fue revisada y su ficha contiene un resumen suficiente;
- `integrated`: su conocimiento relevante fue conectado con otras páginas;
- `superseded`: existe una versión posterior que la reemplaza;
- `unavailable`: el original ya no puede consultarse;
- `rejected`: se conserva la trazabilidad, pero no se usa como evidencia.

`confidentiality`, cuando se declare, admite:

- `public`
- `internal`
- `restricted`

La clasificación describe acceso, no credibilidad. Una fuente interna o restringida
no debe reproducirse en una página pública sin autorización.

## 5. Cuerpo obligatorio

Después de los metadatos, la página debe contener estas secciones y conservar sus
títulos.

### `## Resumen`

Descripción neutral y concisa del contenido y propósito de la fuente. Debe poder
entenderse sin abrir el original, pero no debe intentar sustituirlo.

### `## Procedencia`

Explica quién produjo el material, en qué contexto, cómo llegó a Atlas-Wiki y qué
representa el localizador de `origin`. También registra transformaciones previas
relevantes, como transcripción, traducción, exportación o conversión de formato.
En un `wiki-pack`, indica que el ingreso fue `@subir_wiki` y si se reemplazó un
árbol anterior del mismo slug.

### `## Inventario`

Obligatoria solo si `source_kind` es `wiki-pack`. Resume el árbol copiado: raíces
relevantes, recuento aproximado, índices detectados. No enumerar cada archivo
irrelevante. No sustituye a **Relaciones**.

### `## Evidencia relevante`

Lista las afirmaciones, datos o fragmentos conceptuales utilizados por la wiki.
Cada elemento debe:

- expresar una sola idea verificable;
- incluir página, sección, marca de tiempo, línea u otro localizador cuando el
  formato lo permita;
- distinguir una afirmación explícita de una inferencia del agente;
- evitar citas extensas cuando una paráfrasis fiel sea suficiente.

Formato recomendado:

```markdown
- **E1 — Afirmación:** Paráfrasis fiel de la evidencia.
  - Localizador: sección 2.1, p. 8
  - Uso: [Página derivada](../concepts/pagina-derivada.md)
```

Los identificadores `E1`, `E2`, etc. son locales a la página de fuente. Deben
mantenerse estables para no romper referencias hechas desde otras páginas.

### `## Alcance y limitaciones`

Indica qué permite sostener la fuente y qué queda fuera de su alcance. Aquí se
registran sesgos conocidos, información incompleta, contexto temporal, posibles
conflictos de interés, problemas de disponibilidad o incertidumbres de
interpretación.

No debe asignarse una puntuación universal de confiabilidad. La utilidad de una
fuente depende de la afirmación concreta para la que se utiliza.

### `## Relaciones`

Contiene dos listas:

```markdown
### Páginas derivadas

- Ninguna todavía.

### Fuentes relacionadas

- Ninguna todavía.
```

Las páginas derivadas son páginas de la wiki que usan esta fuente. Las fuentes
relacionadas pueden confirmarla, ampliarla, contradecirla o reemplazarla; la
naturaleza de la relación debe indicarse en el texto del elemento.

## 6. Secciones opcionales

Solo se incluyen cuando aportan información real.

### `## Cronología`

Para fuentes cuya creación, publicación, revisión o reemplazo requiera distinguir
varios momentos.

### `## Notas de procesamiento`

Documenta decisiones técnicas que afecten la interpretación: OCR incompleto,
segmentos inaudibles, hojas omitidas, traducción automática o extracción parcial.

### `## Contradicciones`

Enumera desacuerdos concretos con otras fuentes. Debe enlazar cada fuente implicada
y describir el desacuerdo sin resolverlo artificialmente.

## 7. Reglas de redacción

- Redactar en español, salvo nombres propios, términos técnicos o citas que deban
  conservar su idioma.
- Preferir paráfrasis fieles y concisas.
- Marcar cualquier traducción como traducción del agente si no proviene de una
  versión oficial.
- No atribuir intenciones, causalidad ni conclusiones que la fuente no exprese.
- No incluir secretos, credenciales ni datos personales innecesarios.
- No usar `reviewed` o `integrated` si solo se inspeccionó una parte no representativa.
- No confundir actualidad con autoridad: una fuente reciente puede describir un
  cambio, mientras una fuente anterior sigue siendo evidencia histórica válida.

## 8. Duplicados, versiones y reemplazos

Antes de crear una ficha, debe buscarse una fuente equivalente por título, autor,
URL, ruta, versión y, si existe, `content_hash`.

- Copias idénticas del mismo material comparten una sola ficha.
- Ediciones con cambios sustantivos reciben fichas separadas y se enlazan.
- Una exportación o conversión puramente técnica no crea una nueva fuente si el
  contenido permanece igual; se documenta en **Procedencia**.
- Un nuevo `@subir_wiki` del mismo `<slug>` actualiza la ficha existente: se
  conserva `created` y los identificadores de evidencia aún vigentes; se actualizan
  inventario, procedencia, `accessed` y `updated`.
- `supersedes` y `superseded_by` solo se usan cuando el reemplazo es explícito o
  está claramente documentado.
- Una fuente reemplazada no se elimina y puede seguir respaldando hechos históricos.

## 9. Actualización de la ficha

Actualizar `updated` cuando cambien el resumen, la procedencia, la evidencia, las
limitaciones, el estado o las relaciones. No es necesario cambiarlo por correcciones
puramente ortográficas.

Al integrar conocimiento nuevo:

1. conservar identificadores de evidencia existentes;
2. agregar nuevos identificadores al final de la secuencia;
3. actualizar **Páginas derivadas**;
4. reflejar contradicciones o reemplazos sin borrar el historial útil;
5. cambiar `status` solo cuando se cumpla su definición;
6. registrar el cambio en `wiki/log.md` cuando sea material.

## 10. Plantilla

```markdown
---
type: source
title: "<Título de la fuente>"
source_kind: <valor-controlado>
origin: "<ruta-relativa-url-o-localizador>"
authors:
  - <persona-organización-o-unknown>
published: <YYYY-MM-DD-YYYY-MM-o-unknown>
accessed: <YYYY-MM-DD-o-not-applicable>
language: <código-bcp-47>
status: registered
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
---

# <Título de la fuente>

## Resumen

<Descripción neutral del contenido y propósito.>

## Procedencia

<Autoría, contexto, forma de obtención y transformaciones relevantes.>

## Evidencia relevante

- **E1 — Afirmación:** <Paráfrasis fiel de una idea verificable.>
  - Localizador: <página-sección-marca-de-tiempo-o-no-disponible>
  - Uso: <enlace-a-página-derivada-o-pendiente>

## Alcance y limitaciones

<Qué respalda la fuente y qué no permite concluir.>

## Relaciones

### Páginas derivadas

- Ninguna todavía.

### Fuentes relacionadas

- Ninguna todavía.
```

Si `source_kind` es `wiki-pack`, usar además `layout_kind` en el YAML e insertar
`## Inventario` entre **Procedencia** y **Evidencia relevante**.

## 11. Validación

Antes de guardar una página de fuente, comprobar:

- [ ] El original existe o su indisponibilidad está declarada.
- [ ] `origin` identifica el material sin ambigüedad.
- [ ] No existe una ficha equivalente.
- [ ] Los metadatos obligatorios están presentes y usan valores válidos.
- [ ] Si `source_kind` es `wiki-pack`, existen `layout_kind` e **Inventario**.
- [ ] El resumen es neutral y no sustituye artificialmente el original.
- [ ] Cada evidencia tiene un identificador y un localizador cuando es posible.
- [ ] Las inferencias están separadas de afirmaciones explícitas.
- [ ] Las limitaciones y contradicciones relevantes son visibles.
- [ ] Las páginas derivadas enlazan de vuelta a esta fuente.
- [ ] Los enlaces relativos funcionan.
- [ ] No se modificó el material en `raw/`, salvo el reemplazo de
      `raw/sub_wiki/<slug>/` en una tarea `@subir_wiki`.
- [ ] Se actualizó `wiki/index.md` o `wiki/log.md` si corresponde.
