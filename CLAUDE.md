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

### El ciclo no cierra a la primera

Las fases que producen artefactos se verifican, y la verificación se repite después de cada
corrección. Una sola pasada no vale: es una foto del estado anterior.

- **`clarify` se corre siempre** después de `specify`, aunque parezca que no queda nada por
  preguntar: su barrido estructurado encuentra ambigüedades que la conversación previa no vio. Si no
  hay nada que preguntar, la salida es «sin preguntas» y se anota. Se vuelve a correr cada vez que
  `analyze` detecte una ambigüedad. Las de producto —fórmulas, límites, denominadores, reglas de
  negocio— se preguntan al dueño; no se resuelven con una recomendación del agente.
- **`analyze` es obligatorio** después de `tasks` y **se vuelve a correr tras cada tanda de
  correcciones**. No se pasa a `implement` con hallazgos críticos o altos abiertos.
- **La condición de salida no es «cero hallazgos»** —`analyze` siempre encuentra algo—, sino:
  cero críticos y cero altos, y los medios y bajos que queden escritos en la tarjeta para que el
  dueño los acepte. Un hallazgo aceptado es deuda conocida; uno silenciado no existe.
- **`converge` hace lo mismo después de `implement`**: compara el código con la spec, añade a
  `tasks.md` lo que falte y se repite hasta que no quede trabajo sin construir.

```
specify → clarify → GATE
plan → tasks → analyze → corrige → analyze → GATE
implement → converge → corrige → converge → GATE
```

Sin commit ni push hasta que el dueño lo pida.

## Reglas propias del proyecto

Este apartado está vacío. Añade aquí lo que aplique —idioma del código, estilo, stack— o mejor,
ponlo en la constitución, que es donde se versiona.
