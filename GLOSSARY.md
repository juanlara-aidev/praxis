# Glosario — Praxis

Taxonomia de los terminos usados en el payload de Praxis. Incluye terminos propios del proyecto y terminos del ecosistema con atribucion.

---

## Terminos propios de Praxis

### Trust Stack
Stack tecnico preconfigurado por Praxis (Next.js 16, Supabase, Tailwind, Vercel AI SDK, Zod, Zustand, Playwright). El nombre refleja que la eleccion es opinada, no dogmatica: si un proyecto exige otra tecnologia, la skill `brief` documenta la compatibilidad.

### Registro de Aprendizajes
Seccion en PRPs y en `CLAUDE.md` donde se documentan errores y sus fixes. Cada aprendizaje se consolida para que el mismo error no vuelva a ocurrir.

### Directiva de Stack
Contrato emitido por la skill `brief` para la siguiente skill. Formato: bloques `KEEP / ADD / REPLACE / REMOVE / CONFIG` + archivos a borrar + archivos a crear + toolchain externo.

### Compatibilidad Praxis
Clasificacion que emite la skill `brief` sobre que tan compatible es el Trust Stack con el tipo de proyecto. Cinco niveles:

| Nivel | Significado |
|-------|-------------|
| `MATCH` | El Trust Stack es la eleccion correcta. Nada que cambiar. |
| `EXTEND` | El Trust Stack es base, hay que sumar libs o SDKs. |
| `PARTIAL` | Parte del Trust Stack sirve, parte se reemplaza (ej: solo frontend, solo BD). |
| `REPLACE_FRONT` | Frontend se reemplaza (ej: Expo/Electron), backend Supabase se conserva. |
| `REPLACE` | Stack totalmente distinto (ej: CLI en Rust, desktop nativo). |

### Brief master / Brief single
Dos modos de la skill `brief`. **Master** genera un brief maestro para un proyecto nuevo completo (multifase, con phases de construccion). **Single** genera un brief acotado para una feature especifica en un proyecto existente. El modo se auto-detecta por contexto, no se elige.

### Jefe de Planta
Rol orquestador de la skill `build-with-agent-team`. Coordina agentes especializados (database, backend, frontend, qa), aprueba sus PRPs, y supervisa la ejecucion por fases.

### Trust Stack inyectable
Lo que Praxis deposita en un proyecto nuevo: `src/` con Next.js + `core/` + `features/`, `.claude/` con skills + PRPs + design-systems, `.mcp.json` inicial.

---

## Terminos del ecosistema (con atribucion)

### PRP — Product Requirements Prompt
Framework de **Rasmus Widing / Wirasm** (github.com/Wirasm/PRPs-agentic-eng). Un PRP es un prompt ejecutable que define objetivo, contexto, plan y validacion antes de escribir codigo. Praxis adapta el template en `.claude/PRPs/prp-base.md` y la skill `prp` lo genera.

### Bucle-agentico
Bucle de ejecucion nativo de **Anthropic Claude Code**. Docs: https://docs.anthropic.com/en/docs/claude-code. Praxis lo envuelve en la skill `bucle-agentico` para ejecutar PRPs por fases con mapeo de contexto.

### Agent Skills Specification
Formato oficial de **Anthropic** para skills. Docs: https://docs.anthropic.com/en/docs/agents/skills. Todas las skills de Praxis siguen esta spec.

### Progressive Disclosure
Patron recomendado por Anthropic en la Agent Skills Specification: cargar metadata primero, `SKILL.md` al activar la skill, references solo bajo demanda.

### Feature-First
Convencion de organizacion modular derivada de Domain-Driven Design (**Eric Evans**, 2003) y popularizada como "modular monolith" por varios autores del ecosistema. Praxis la aplica en `src/features/<feature>/`.

### Spec-Driven Development
Metodologia de industria (Anthropic, Martin Fowler, GitHub, Addy Osmani). Principio: escribir la spec antes del codigo. Praxis la implementa con el pipeline `brief -> prp -> bucle-agentico`.

### Context Engineering
Popularizado por **Cole Medin**. Principio: el agente solo necesita el contexto suficiente para la siguiente accion, no todo de golpe. Praxis lo aplica en el mapeo de contexto por fase del bucle-agentico y en la carga perezosa de recursos en skills multi-archivo.

---

## Nomenclatura de archivos

| Tipo | Convencion |
|------|------------|
| PRPs | `PRP-[numero]-[descripcion-kebab].md` |
| Estados PRP | `PENDIENTE` -> `APROBADO` -> `EN PROGRESO` -> `COMPLETADO` |
| Skills | `.claude/skills/<dominio>/<id>/SKILL.md` |
| Briefs | `BRIEF-MASTER-<nombre>.md` o `BRIEF-<nombre>.md` (single) |

---

