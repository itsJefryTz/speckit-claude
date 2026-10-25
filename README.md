# speckit-claude

Plantilla de [Spec Kit](https://github.com/github/spec-kit) lista para Claude Desktop (pestaña
Code) y Claude Code: el ciclo de especificación completo, sin el CLI de speckit y con una regla de
trabajo ya puesta.

La regla, en una línea: **el agente ejecuta la fase, se detiene y te entrega una tarjeta de
decisión; tú apruebas.** Los documentos siguen existiendo en `specs/`, pero no tienes que leerlos
para aprobar.

## Qué incluye

| Pieza | Para qué |
|---|---|
| `.claude/skills/speckit-*/` | Las diez fases, como skills invocables |
| `.specify/templates/` | Plantillas de spec, plan, tasks, checklist y constitución |
| `.specify/scripts/bash/` | El motor que las skills invocan (numeración, rutas, setup) |
| `.specify/memory/constitution.md` | El Principio I ya ratificado |
| `CLAUDE.md` | El protocolo: preguntar antes de escribir, tarjeta del gate |
| `specs/` | Vacío, listo para la primera feature |

No incluye el CLI de speckit, los manifests de integraciones ni el motor de workflows: nada de eso
lo leen las skills. Tampoco trae features de ejemplo, para que el primer `specify` sea el tuyo.

## Requisitos

- Claude Desktop (pestaña Code) o Claude Code, con las skills de `.claude/skills/`.
- `bash` y `git`.
- Opcional: `jq` o `python3` — los scripts los usan si están para leer JSON; si no, caen a `awk`.

## Cómo arrancar

1. Copia esta carpeta, o usa *Use this template* en GitHub.
2. Ábrela en Claude Desktop.
3. Pide una feature en una frase: «Corre speckit-specify con: …».
4. Responde las preguntas que te lleguen y aprueba la tarjeta.

## El ciclo

```
  TÚ                          AGENTE                          QUEDA EN
  ─────────────────────────────────────────────────────────────────────────
  «quiero X» en una línea ──► create-new-feature ──► specs/NNN-x/
                              speckit-specify
                              speckit-clarify   (obligatorio)
                                                        └─► GATE  spec.md

  «sigue» ──────────────────► speckit-plan
                              speckit-tasks
                              speckit-analyze ──► corrige ──► analyze
                                                        └─► GATE  plan.md
                                                                   tasks.md

  «a código» ───────────────► speckit-implement
                              speckit-converge ──► corrige ──► converge
                                                        └─► GATE  diff + tests

  «haz el git» ─────────────► commit
```

`clarify`, `analyze` y `converge` no son una pasada: se repiten después de cada corrección hasta
que no queden hallazgos críticos ni altos. Lo que sobreviva se acepta en la tarjeta, no se silencia.

En cada gate la tarjeta tiene la misma forma:

```
SPEC 004 — lista para plan
  Decidido   · …
  Necesito   · …
  Riesgo     · …
  → «sigue» / «cambia X» / «muéstrame Y»
```

## Estructura

```
.
├── CLAUDE.md                  protocolo del agente
├── .claude/skills/            10 skills (speckit-*)
├── .specify/
│   ├── memory/constitution.md
│   ├── templates/
│   ├── scripts/bash/
│   └── init-options.json      numeración secuencial, script sh
└── specs/                     una carpeta por feature
```

## Personalizar

- **Principios del proyecto:** ejecuta `speckit-constitution` con lo que sea vinculante —stack,
  idioma, producto, marca—. El Principio I no se toca; el resto del archivo es tuyo.
- **Reglas del agente:** `CLAUDE.md`, sección «Reglas propias del proyecto».
- **Numeración:** `feature_numbering` en `.specify/init-options.json` (`sequential` por defecto).
