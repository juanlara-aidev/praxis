# Atribuciones — Praxis

Praxis es un sistema Agent-First construido sobre conceptos publicos y ampliamente adoptados del ecosistema de desarrollo asistido por IA. Este archivo lista las fuentes intelectuales sobre las que se apoya el payload.

---

## Conceptos y frameworks

### PRPs — Product Requirements Prompts

- **Autor:** Rasmus Widing (Wirasm)
- **Repositorio:** https://github.com/Wirasm/PRPs-agentic-eng
- **Uso en Praxis:** `.claude/PRPs/prp-base.md` es un template adaptado del framework PRPs-agentic-eng. La skill `prp` genera PRPs siguiendo esta spec. Un PRP es un prompt ejecutable, no un documento de producto tradicional.

### Bucle-agentico (agentic loop)

- **Origen:** bucle de ejecucion nativo de Anthropic Claude Code.
- **Docs oficiales:** https://docs.anthropic.com/en/docs/claude-code
- **Uso en Praxis:** la skill `bucle-agentico` encapsula el patron de ejecucion por fases con mapeo de contexto recomendado por Anthropic para tareas multi-paso.

### Agent Skills Specification

- **Autor:** Anthropic.
- **Docs oficiales:** https://docs.anthropic.com/en/docs/agents/skills
- **Uso en Praxis:** todas las skills en `.claude/skills/` siguen el formato oficial (frontmatter YAML + instrucciones en prosa + carga perezosa de recursos). La skill `skill-creator` ayuda a crear skills que cumplen la spec.

### Feature-First (modular monolith)

- **Origen:** patron derivado de Domain-Driven Design (Eric Evans, 2003) y popularizado como "modular monolith" por varios autores del ecosistema (Kamil Grzybek, Simon Brown, entre otros).
- **Uso en Praxis:** el scaffold de `src/features/<feature>/` agrupa components, hooks, services, state y types en una sola carpeta para que un agente pueda razonar sobre la superficie completa sin navegar entre directorios.

### Spec-Driven Development

- **Origen:** metodologia de industria. Anthropic, Martin Fowler, GitHub, Addy Osmani y otros han publicado sobre el patron de "escribir la spec antes del codigo" en el contexto de desarrollo con LLMs.
- **Uso en Praxis:** el pipeline `brief -> prp -> bucle-agentico` es una implementacion de Spec-Driven Development para Claude Code.

### Context Engineering

- **Popularizador:** Cole Medin.
- **Uso en Praxis:** el mapeo de contexto por fase (propio del bucle-agentico) es una practica de context engineering — el agente lee solo lo necesario justo antes de ejecutar cada fase.

---

## Stack tecnico

| Tecnologia | Fuente |
|-----------|--------|
| Next.js 16 + React 19 | Vercel, Meta |
| Tailwind CSS 3.4 | Tailwind Labs |
| shadcn/ui | shadcn (ui.shadcn.com) |
| Supabase (Postgres + Auth + RLS) | Supabase |
| Vercel AI SDK v5 | Vercel |
| OpenRouter | OpenRouter.ai |
| Zod | Colin McDonnell |
| Zustand | Poimandres |
| Playwright | Microsoft |
| TypeScript | Microsoft |

Los bloques del `ai-sdk-kit` adaptan ejemplos de la documentacion oficial de Vercel AI SDK y del libro de patrones de agentes publicado por Anthropic.

---

## Elementos propios de Praxis

Lo siguiente es contribucion original del payload Praxis (no derivado de fuentes externas):

- La metafora **Jefe de Planta** de la skill `build-with-agent-team` para orquestar agentes.
- El framework de compatibilidad **MATCH / EXTEND / PARTIAL / REPLACE_FRONT / REPLACE** usado en las recetas de `brief`.
- La **Directiva de Stack** (KEEP / ADD / REPLACE / REMOVE / CONFIG) como contrato entre `brief` y `prp`.
- La separacion **Brief master** (proyecto nuevo completo) vs. **Brief single** (feature acotada) con auto-deteccion desde la idea + el workspace.
- El empaquetado del payload completo como **extension de VS Code** que inyecta el Trust Stack con un click (alternativas a `cp -r` o a scripts shell).
- La **inyeccion selectiva por skill** con catalogo de skills + MCPs gestionable desde el sidebar.

---

## Licencia

Praxis se distribuye bajo los terminos declarados en el repositorio de la extension. El uso de los conceptos citados arriba respeta las licencias y la comunidad de cada fuente original.

---

