# Esquema de organización

## Propósito y ubicación

Una página de organización describe una entidad colectiva relevante para el
conocimiento de Atlas: empresa, institución, equipo, comunidad, proveedor, cliente
u otra unidad organizada. Explica su identidad, función y relaciones documentadas
sin convertirse en un directorio corporativo exhaustivo.

- Directorio: `wiki/organizations/`
- Ruta: `wiki/organizations/<slug>.md`
- Nombre: denominación reconocible en `kebab-case`

Los equipos con identidad, responsabilidades y continuidad propias pueden tener
una página. Los grupos temporales ligados a un único resultado suelen documentarse
dentro de su proyecto.

## Metadatos

### Obligatorios

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `type` | texto | Siempre `organization`. |
| `title` | texto | Nombre oficial o reconocido. |
| `organization_kind` | texto controlado | Naturaleza de la entidad. |
| `status` | texto controlado | Estado documentado de la organización. |
| `created` | fecha | Creación de la página (`YYYY-MM-DD`). |
| `updated` | fecha | Último cambio material (`YYYY-MM-DD`). |

### Opcionales

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `aliases` | lista de textos | Siglas, nombres anteriores o variantes. |
| `parent_organization` | enlace | Entidad matriz o contenedora documentada. |
| `website` | URL | Sitio oficial. |
| `founded` | fecha, fecha parcial o `unknown` | Inicio documentado. |
| `ended` | fecha o fecha parcial | Finalización documentada. |

`organization_kind` admite:

- `company`
- `institution`
- `government`
- `nonprofit`
- `community`
- `team`
- `client`
- `partner`
- `vendor`
- `other`

`status` admite `active`, `inactive`, `merged`, `dissolved` y `unknown`. Para
`merged`, debe enlazarse la organización resultante en el cuerpo.

## Cuerpo obligatorio

### `## Resumen`

Identifica la organización, explica su función relevante y delimita el contexto al
que se refiere la página.

### `## Propósito y responsabilidades`

Describe el propósito declarado y las responsabilidades relacionadas con Atlas.
No presentar mensajes promocionales como hechos independientes.

### `## Relación con Atlas`

Enlaza proyectos, requisitos, decisiones, procesos o fuentes que expliquen la
relación. Debe indicar el periodo y la naturaleza de vínculos como propiedad,
colaboración, provisión, contratación o dependencia.

### `## Personas relacionadas`

Lista únicamente personas cuya relación profesional relevante esté documentada,
con rol y periodo cuando se conozcan.

### `## Fuentes`

Enlaza evidencia sobre identidad, estado, responsabilidades y relaciones.

## Secciones opcionales

- `## Estructura`: unidades internas necesarias para comprender responsabilidades.
- `## Historia relevante`: cambios de nombre, fusión, división o cierre.
- `## Productos y servicios`: solo los pertinentes para la wiki.
- `## Acuerdos y dependencias`: relaciones formales respaldadas.

## Reglas

- No confundir una marca, producto o proyecto con una organización.
- No asumir que una persona continúa vinculada por aparecer en una fuente antigua.
- Fechar estructura, responsables y relaciones que puedan cambiar.
- Distinguir nombre legal, nombre comercial y alias cuando sea relevante.
- No registrar información confidencial, contractual o personal más allá de lo
  autorizado y necesario.
- Las afirmaciones de la propia organización deben atribuirse cuando no exista
  corroboración independiente y esta diferencia sea importante.

## Plantilla

```markdown
---
type: organization
title: "<Nombre de la organización>"
organization_kind: <valor-controlado>
status: <valor-controlado>
aliases: []
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
---

# <Nombre de la organización>

## Resumen

<Identidad, función y contexto relevante.>

## Propósito y responsabilidades

<Propósito declarado y responsabilidades documentadas.>

## Relación con Atlas

- <naturaleza, periodo y enlace relacionado>

## Personas relacionadas

- <persona, rol y periodo o `Ninguna documentada todavía.`>

## Fuentes

- <enlace-a-fuente-y-evidencia>
```

## Validación

- [ ] La entidad es realmente una organización según este esquema.
- [ ] No existe una página equivalente o bajo un alias.
- [ ] Tipo y estado usan valores permitidos.
- [ ] Relaciones, roles y periodos están respaldados.
- [ ] Las afirmaciones institucionales están correctamente atribuidas.
- [ ] No hay información sensible innecesaria.
- [ ] Los enlaces relativos funcionan.
- [ ] El índice y el log se actualizaron si corresponde.
