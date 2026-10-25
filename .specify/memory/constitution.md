<!--
Sync Impact Report
==================
Cambio de versión: — → 1.0.0
Tipo de bump: ratificación inicial.

Cambios:
  * Se ratifica el Principio I, portable a cualquier proyecto: el agente ejecuta el ciclo speckit y
    el dueño aprueba cada fase.

Principios añadidos: I.
Principios eliminados: ninguno.
Secciones eliminadas: ninguna.
Plantillas dependientes: ninguna (las plantillas leen la constitución en tiempo de ejecución).
TODOs diferidos: los principios propios del proyecto se añaden con `speckit-constitution`.
-->

# Constitución del proyecto

## Principios Fundamentales

### I. El agente ejecuta el ciclo speckit; el dueño aprueba cada fase (NO NEGOCIABLE)

El agente ejecuta las fases del ciclo —`speckit-specify`, `speckit-clarify`, `speckit-plan`,
`speckit-tasks`, `speckit-analyze`, `speckit-checklist`, `speckit-implement`, `speckit-converge`,
`speckit-taskstoissues`— cuando el dueño lo pide o lo autoriza para una feature.

El agente corre una fase, se detiene y entrega una tarjeta de decisión: qué quedó decidido, qué
necesita del dueño y qué riesgo hay si se sigue. No encadena dos fases sin aprobación. El dueño
puede leer los `.md` si quiere, pero la aprobación se toma sobre la tarjeta.

Antes de escribir cualquier artefacto, el agente pregunta las decisiones abiertas —con opciones y
una recomendación— y escribe con las respuestas dentro. No escribe suposiciones propias para
enseñarlas después de haberlas fijado. Lo que solo el dueño puede decidir se pregunta, no se rellena.

**Razón:** el dueño conduce el ciclo por decisiones, no leyendo documentos de cientos de líneas. El
gate conserva lo que importa —que ninguna fase avanza sin aprobación— y cambia su unidad: la
decisión, no el artefacto. Preguntar antes de escribir evita que una suposición del agente quede
grabada como requisito aprobado.

### II. Principios propios del proyecto

Este apartado está vacío a propósito. Los principios vinculantes del proyecto —stack, idioma,
producto, marca, lo que sea— los escribe el dueño ejecutando `speckit-constitution`.

El Principio I no se toca: es lo que hace que el ciclo funcione.

## Restricciones de Tecnología

Sin definir. Se añaden cuando el stack esté decidido.

## Flujo de Desarrollo

- Una fase del ciclo a la vez, con aprobación del dueño entre fases.
- Nada se implementa sin una spec aprobada.
- El agente no hace commit ni push hasta que el dueño lo pida explícitamente.

## Gobierno

Esta constitución manda sobre cualquier otra práctica del proyecto.

- **Enmiendas:** toda enmienda se propone al dueño, se explica por qué y queda registrada con su
  fecha. Ninguna enmienda entra sin aprobación explícita.
- **Versionado:** semántico. MAJOR si se elimina o redefine un principio o una regla de gobierno de
  forma incompatible; MINOR si se añade un principio o se amplía materialmente la guía existente;
  PATCH si es una aclaración o corrección de redacción que no cambia el significado.
- **Resolución de conflictos:** si una decisión de una feature entra en conflicto con un principio,
  el conflicto se resuelve antes de implementar, no después.
- **Cumplimiento:** la revisión de cada feature verifica estos principios antes de la aprobación.

**Versión**: 1.0.0 | **Ratificada**: 2026-10-24 | **Última enmienda**: 2026-10-24
