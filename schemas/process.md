# Esquema de proceso

## Propósito y ubicación

Una página de proceso describe una forma repetible de alcanzar un resultado:
propósito, alcance, entradas, responsables, pasos, salidas y controles. Debe
permitir ejecutar o evaluar el proceso sin convertir la wiki en un gestor de tareas.

- Directorio: `wiki/processes/`
- Ruta: `wiki/processes/<slug>.md`
- Nombre: acción o resultado reconocible en `kebab-case`

Una secuencia realizada una sola vez pertenece normalmente a un proyecto. Un
principio sin pasos ejecutables corresponde normalmente a un concepto.

## Metadatos

### Obligatorios

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `type` | texto | Siempre `process`. |
| `title` | texto | Nombre del proceso. |
| `status` | texto controlado | Estado de vigencia. |
| `owners` | lista de enlaces o textos | Responsables de mantenerlo; `unknown` si no constan. |
| `version` | texto | Versión documental, por ejemplo `1.0` o `draft-1`. |
| `created` | fecha | Creación de la página (`YYYY-MM-DD`). |
| `updated` | fecha | Último cambio material (`YYYY-MM-DD`). |

### Opcionales

| Campo | Tipo | Descripción |
| --- | --- | --- |
| `effective` | fecha | Inicio de vigencia de esta versión. |
| `review_on` | fecha | Próxima revisión prevista. |
| `organizations` | lista de enlaces | Entidades donde aplica. |
| `supersedes` | enlace | Versión o proceso reemplazado. |
| `frequency` | texto | Cadencia cuando sea inherente al proceso. |

`status` admite:

- `draft`: en elaboración, no aprobado para uso normal;
- `active`: vigente;
- `paused`: suspendido temporalmente;
- `deprecated`: desaconsejado durante una transición;
- `retired`: fuera de uso y conservado como historia.

## Cuerpo obligatorio

### `## Propósito`

Explica qué resultado produce el proceso y qué necesidad satisface.

### `## Alcance`

Define cuándo comienza y termina, dónde aplica, quién participa y qué casos quedan
fuera.

### `## Entradas y condiciones previas`

Lista información, materiales, permisos, estados o eventos necesarios para iniciar.

### `## Roles y responsabilidades`

Define roles del proceso y su responsabilidad. Enlaza personas solo cuando la
asignación nominal aporte valor; el proceso debe seguir siendo comprensible aunque
cambien sus ocupantes.

### `## Procedimiento`

Usa una lista numerada. Cada paso debe indicar acción, responsable, entrada o
condición relevante y resultado esperado. Las decisiones dentro del flujo deben
mostrar sus ramas.

### `## Salidas y condición de finalización`

Describe entregables, registros o estados resultantes y cómo saber que el proceso
terminó correctamente.

### `## Controles y excepciones`

Incluye validaciones, aprobaciones, criterios de escalamiento, fallos previsibles y
forma segura de tratarlos. No ocultar excepciones conocidas bajo el flujo ideal.

### `## Relaciones`

Enlaza proyectos, requisitos, decisiones, conceptos, organizaciones y otros
procesos que activan, restringen o reciben sus resultados.

### `## Fuentes`

Enlaza evidencia de la versión, autoridad, pasos, controles y cambios.

## Secciones opcionales

- `## Métricas`: medidas con definición, unidad, fuente y frecuencia.
- `## Herramientas`: sistemas necesarios sin incluir secretos ni credenciales.
- `## Ejemplo`: una ejecución representativa claramente marcada.
- `## Historia de versiones`: cambios materiales, fecha, autoría y motivo.
- `## Preguntas abiertas`: aspectos aún no resueltos.

## Reglas

- Documentar el proceso vigente; conservar versiones anteriores cuando sean
  necesarias para trazabilidad.
- No mezclar instrucciones aspiracionales con el flujo real. Señalar diferencias
  entre proceso actual y proceso propuesto.
- Usar roles, no nombres personales, para responsabilidades estructurales.
- No inventar pasos faltantes; marcarlos como pendientes o como variación conocida.
- Un cambio que altere propósito, alcance, autoridad, controles o secuencia crítica
  requiere incrementar la versión y registrar su motivo.
- Nunca almacenar credenciales, tokens o instrucciones que eludan controles de
  seguridad.

## Plantilla

```markdown
---
type: process
title: "<Nombre del proceso>"
status: <draft-active-paused-deprecated-o-retired>
owners:
  - <enlace-o-unknown>
version: "<versión>"
created: <YYYY-MM-DD>
updated: <YYYY-MM-DD>
---

# <Nombre del proceso>

## Propósito

<Resultado y necesidad atendida.>

## Alcance

<Inicio, fin, aplicación, participantes y exclusiones.>

## Entradas y condiciones previas

- <entrada o condición>

## Roles y responsabilidades

| Rol | Responsabilidad |
| --- | --- |
| <rol> | <responsabilidad> |

## Procedimiento

1. **<Rol>:** <acción y resultado esperado>.
2. **<Rol>:** <acción y resultado esperado>.

## Salidas y condición de finalización

- <salida y criterio de terminación>

## Controles y excepciones

- <control, excepción o escalamiento>

## Relaciones

- <enlace y naturaleza de la relación>

## Fuentes

- <enlace-a-fuente-y-evidencia>
```

## Validación

- [ ] El contenido describe una actividad repetible, no un proyecto puntual.
- [ ] Propósito, alcance, entradas y salidas están definidos.
- [ ] Cada paso tiene una acción y responsabilidad comprensibles.
- [ ] Ramas, controles y excepciones relevantes están visibles.
- [ ] Estado y versión son coherentes con la evidencia.
- [ ] No contiene credenciales ni instrucciones inseguras.
- [ ] Los enlaces relativos funcionan.
- [ ] El índice y el log se actualizaron si corresponde.
