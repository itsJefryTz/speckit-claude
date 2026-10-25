# CLAUDE.md — protocolo de trabajo

Este archivo lo lee el agente en cada sesión. La autoridad del proyecto es
`.specify/memory/constitution.md`; aquí va el detalle operativo.

## Ciclo speckit

El agente ejecuta las fases del ciclo —`specify`, `clarify`, `plan`, `tasks`, `analyze`, `checklist`,
`implement`, `converge`, `taskstoissues`— cuando el dueño lo pide, y se detiene al final de cada una
(Principio I de la constitución). Nunca encadena dos fases sin aprobación.

### Antes de escribir: preguntar

1. **Pre-pase.** Leer la spec existente, el código y la constitución. Sacar la lista de decisiones
   abiertas, separando las que bloquean de las que solo son forma.
2. **Preguntar.** Mandar las preguntas al dueño con el selector: máximo cuatro por tanda, cada una
   con dos a cuatro opciones y la recomendación marcada. Si hay más, van en tandas; no se recortan
   para que quepan.
3. **Escribir.** Redactar el artefacto con las respuestas dentro.

Nunca se escribe una suposición propia para enseñarla después de haberla fijado. Si al redactar
aparece una ambigüedad nueva, se pregunta en ese momento. Si el dueño responde «elige tú», la
elección se lista al final bajo **Elegí por ti** —como mucho tres puntos—, no se diluye en el texto.

Lo que solo el dueño puede decidir —precios, canales de pago, datos de clientes, cualquier hecho de
negocio— se pregunta como decisión; no se rellena.

### La tarjeta del gate

Cada fase termina con una tarjeta y una pregunta, no con el documento volcado:

```
SPEC 004 — lista para plan
  Decidido   · …
  Necesito   · …
  Riesgo     · …
  → «sigue» / «cambia X» / «muéstrame Y»
```

El `.md` sigue siendo la fuente de verdad y queda en `specs/`; la tarjeta es la interfaz con el
dueño. Si pide detalle, se le entrega solo la sección pedida, no el archivo entero.

Sin commit ni push hasta que el dueño lo pida.

## Reglas propias del proyecto

Este apartado está vacío. Añade aquí lo que aplique —idioma del código, estilo, stack— o mejor,
ponlo en la constitución, que es donde se versiona.
