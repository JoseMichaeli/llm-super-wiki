# Atlas-Wiki

Atlas-Wiki es el mapa vivo del conocimiento de Atlas. Reúne información
estructurada sobre fuentes, proyectos, personas, organizaciones, decisiones,
requisitos, conceptos, procesos y síntesis.

Este índice es la puerta de entrada a la wiki. Está diseñado para que una persona o
un agente pueda comprender qué conocimiento existe, dónde encontrarlo y cómo se
relaciona, sin tener que recorrer directamente el material original de `raw/`.

> **Estado actual:** estructura inicial. Las categorías de conocimiento están
> vacías. `raw/` ya tiene carpetas para documentos, conversaciones, media,
> datasets, other y wikis completas (`sub_wiki`).

## Cómo navegar la wiki

La navegación puede comenzar desde cuatro preguntas:

- **¿De dónde proviene una afirmación?** Consulta [Fuentes](#fuentes).
- **¿En qué contexto se está trabajando?** Consulta
  [Proyectos](#proyectos), [Personas](#personas) u
  [Organizaciones](#organizaciones).
- **¿Qué se decidió, se necesita o se hace?** Consulta
  [Decisiones](#decisiones), [Requisitos](#requisitos) o
  [Procesos](#procesos).
- **¿Qué significa algo o qué sabemos en conjunto?** Consulta
  [Conceptos](#conceptos) o [Síntesis](#síntesis).

Cada página debe enlazar sus fuentes y las páginas relacionadas. Cuando un tema
pueda abordarse desde varias categorías, debe comenzarse por la página más cercana
a la pregunta y seguir sus relaciones, en lugar de depender únicamente de este
índice.

Un pack subido con `@subir_wiki` se consulta primero por su ficha en
[Fuentes](#fuentes) (`source_kind: wiki-pack`) y por las páginas derivadas
que esa ficha enlaza. Si eso no basta, el agente puede leer el árbol en
`raw/sub_wiki/<slug>/`, incluido el `raw/` interno del pack, y citar esas
rutas. Ese árbol no sustituye a este índice.

## Mapa del conocimiento

### Fuentes

Catálogo del material que respalda el conocimiento de la wiki. Cada página de
fuente identifica su origen, procedencia, alcance y relación con el contenido
derivado.

- Directorio: [`sources/`](sources/)
- Esquema: [`../schemas/source.md`](../schemas/source.md)
- Páginas disponibles: ninguna todavía.

### Proyectos

Iniciativas con un propósito, alcance, responsables, estado y resultados
esperados. Una página de proyecto conecta personas, organizaciones, decisiones,
requisitos, procesos y fuentes relacionadas.

- Directorio: [`projects/`](projects/)
- Esquema: [`../schemas/project.md`](../schemas/project.md)
- Páginas disponibles: ninguna todavía.

### Personas

Personas relevantes para el conocimiento de Atlas, descritas según su contexto,
responsabilidades, aportes y relaciones documentadas. No es un directorio de datos
personales.

- Directorio: [`people/`](people/)
- Esquema: [`../schemas/person.md`](../schemas/person.md)
- Páginas disponibles: ninguna todavía.

### Organizaciones

Empresas, equipos, comunidades o instituciones relacionadas con los proyectos y el
conocimiento registrado.

- Directorio: [`organizations/`](organizations/)
- Esquema: [`../schemas/organization.md`](../schemas/organization.md)
- Páginas disponibles: ninguna todavía.

### Decisiones

Decisiones relevantes que requieren conservar contexto, alternativas, motivos,
consecuencias, estado y evidencia. Esta categoría permite entender no solo qué se
decidió, sino por qué.

- Directorio: [`decisions/`](decisions/)
- Esquema: [`../schemas/decision.md`](../schemas/decision.md)
- Páginas disponibles: ninguna todavía.

### Requisitos

Necesidades, restricciones o condiciones verificables que un proyecto, producto o
proceso debe satisfacer.

- Directorio: [`requirements/`](requirements/)
- Esquema: [`../schemas/requirement.md`](../schemas/requirement.md)
- Páginas disponibles: ninguna todavía.

### Conceptos

Definiciones y modelos mentales reutilizables. Una página de concepto explica qué
significa un término dentro de Atlas, sus límites y sus relaciones con otros
conceptos.

- Directorio: [`concepts/`](concepts/)
- Esquema: [`../schemas/concept.md`](../schemas/concept.md)
- Páginas disponibles: ninguna todavía.

### Procesos

Formas documentadas de ejecutar actividades recurrentes, incluidos su propósito,
entradas, pasos, responsables, resultados y controles.

- Directorio: [`processes/`](processes/)
- Esquema: [`../schemas/process.md`](../schemas/process.md)
- Páginas disponibles: ninguna todavía.

### Síntesis

Análisis que integran conocimiento procedente de varias fuentes o páginas para
responder una pregunta, comparar perspectivas o presentar una visión de conjunto.
Una síntesis debe distinguir claramente evidencia e interpretación.

- Directorio: [`syntheses/`](syntheses/)
- Esquema: [`../schemas/synthesis.md`](../schemas/synthesis.md)
- Páginas disponibles: ninguna todavía.

## Relaciones esperadas

Las categorías no son compartimentos aislados. La topología habitual es:

```text
fuentes ───────────────► conocimiento trazable
   │
   ├──► proyectos ─────► requisitos ─────► procesos
   │       │                 │                 │
   │       ├──► personas     └──► decisiones ◄┘
   │       └──► organizaciones       │
   │                                ▼
   └──────────────► conceptos ──► síntesis
```

El diagrama expresa rutas frecuentes, no restricciones. Cualquier página puede
enlazar otra cuando exista una relación significativa y respaldada.

## Convenciones de navegación

- Los archivos de conocimiento se nombran en `kebab-case` y usan la extensión
  `.md`.
- Los enlaces internos usan rutas Markdown relativas.
- El texto visible de un enlace debe describir su destino; se evitan enlaces como
  “aquí” o rutas sin contexto.
- Una página nueva debe incorporarse en la sección correspondiente de este índice
  cuando sea relevante para la navegación general.
- Este índice es curado: no necesita enumerar páginas auxiliares o de alcance muy
  específico si ya son accesibles desde una página principal.
- No se crean secciones temáticas vacías por anticipado. El mapa crece cuando
  aparece conocimiento real que lo justifica.
- Una misma página tiene una ubicación principal. Sus demás clasificaciones se
  representan mediante enlaces, no mediante copias.

## Criterios de incorporación al índice

Una página debe aparecer explícitamente en este mapa cuando cumpla al menos una de
estas condiciones:

- es una entrada principal para comprender Atlas;
- representa un proyecto, proceso, síntesis o `wiki-pack` de uso frecuente;
- conecta varias áreas de conocimiento;
- contiene una decisión o requisito con impacto amplio;
- sirve como punto de navegación hacia un conjunto significativo de páginas.

Crear una página no obliga automáticamente a destacarla aquí. Sin embargo, toda
página debe poder alcanzarse desde este índice a través de una cadena razonable de
enlaces.

## Estado y mantenimiento

Cuando cambie la estructura navegable, el agente responsable debe actualizar este
archivo en la misma tarea. Debe eliminar referencias obsoletas, conservar nombres
comprensibles y comprobar que las rutas existan.

Los cambios materiales realizados en la base de conocimiento se documentan en
[`log.md`](log.md). Las reglas generales de operación se encuentran en
[`../AGENTS.md`](../AGENTS.md).
