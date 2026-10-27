# writing-adrs

> Dejar por escrito por qué se decidió algo, no solo qué.

**Escribir ADR** · Skill para agentes de código de la comunidad [nvvdev](https://github.com/nvv-dev). Funciona en Claude Code como plugin o como skill suelta, y en cualquier agente compatible con el formato abierto [`SKILL.md`](https://agentskills.io).

*English summary at the end.*

## Qué hace

Redacta Architecture Decision Records cortos en docs/adr/: contexto, opciones consideradas, decisión y consecuencias honestas, con estados (propuesto, aceptado, reemplazado). Dice cuándo vale la pena escribir uno y cuándo no.

## Objetivo

Que nadie reabra una decisión sin información nueva, ni la siga a ciegas cuando el contexto cambió.

## Cuándo usarla

- Elegir base de datos, framework, hosting, modelo de autenticación o de datos
- Una pregunta técnica que se repite

## Cuándo no

- Decisiones locales y fáciles de revertir

## Ejemplo

```text
Escribe un ADR para usar PostgreSQL con esquemas por cliente en vez de bases separadas.
```

## Cómo se activa

Esta skill **se activa sola**: Claude Code lee su descripción y la carga cuando la tarea coincide. También puedes pedirla por nombre ("usa la skill writing-adrs") o invocarla con `/writing-adrs:writing-adrs` (plugin) o `/writing-adrs` (copiada a `.claude/skills/`).

## Instalación

### Opción 1: Claude Code, como plugin (recomendada)

Dentro de Claude Code:

```text
/plugin marketplace add nvv-dev/claude-plugins
/plugin install writing-adrs@nvvdev
```

La primera línea agrega el catálogo de nvvdev una sola vez; la segunda instala esta skill. Si prefieres el paquete completo, instala `dev-workflow@nvvdev` en su lugar (incluye esta skill y las demás de [dev-workflow](https://github.com/nvv-dev/dev-workflow)); no instales los dos a la vez.

### Opción 2: Claude Code, copiando la skill

Para un solo proyecto (se comparte con tu equipo por git):

```bash
git clone --depth 1 https://github.com/nvv-dev/writing-adrs.git /tmp/writing-adrs
mkdir -p .claude/skills
cp -R /tmp/writing-adrs/skills/writing-adrs .claude/skills/
```

Para todos tus proyectos, cópiala en `~/.claude/skills/` en lugar de `.claude/skills/`.

### Opción 3: otros agentes

Copia la carpeta `skills/writing-adrs/` en la carpeta de skills de tu agente (cada agente documenta la suya). Con la CLI [skills](https://github.com/vercel-labs/skills) de Vercel Labs:

```bash
DISABLE_TELEMETRY=1 npx skills add nvv-dev/writing-adrs
```

### Verificar

Abre una sesión nueva y pregunta "¿qué skills tienes disponibles?"; `writing-adrs` debe aparecer. Con el plugin, `/plugin` la muestra como instalada.

### Actualizar o desinstalar

- Plugin: `/plugin marketplace update nvvdev` para actualizar; `/plugin uninstall writing-adrs@nvvdev` para quitarla.
- Copia manual: repite la copia para actualizar, o borra la carpeta `.claude/skills/writing-adrs`.

Antes de instalar cualquier skill, incluida esta, conviene leerla: es un solo archivo, [`skills/writing-adrs/SKILL.md`](skills/writing-adrs/SKILL.md). Ver [vetting-external-skills](https://github.com/nvv-dev/vetting-external-skills).

## Contenido

| Ruta | Qué es |
|---|---|
| `skills/writing-adrs/SKILL.md` | La skill: instrucciones en inglés para que los escáneres de seguridad las analicen completas; el agente responde en tu idioma |
| `.claude-plugin/plugin.json` | Manifiesto para instalarla como plugin |
| `.github/workflows/` | Validación de estructura y escaneo con SkillSpector en cada cambio |

## Contribuir

Este repo se **genera** desde [nvv-dev/dev-workflow](https://github.com/nvv-dev/dev-workflow), donde vive la versión canónica. Abre issues y PRs allí. La mejor contribución es un caso real en la sección *Known failures* de la skill, con la regla que lo evita.

## Origen

Escrita desde cero por nvvdev. Inspirada en: Michael Nygard's ADR format; [mattpocock/skills](https://github.com/mattpocock/skills) (glossary + ADR vocabulary).

## Licencia

MIT.

---

## English

**writing-adrs** — Short ADRs in docs/adr/ with context, options, decision and honest consequences.

Install in Claude Code with `/plugin marketplace add nvv-dev/claude-plugins` and `/plugin install writing-adrs@nvvdev`, or copy `skills/writing-adrs/` into `.claude/skills/` (project) or `~/.claude/skills/` (personal). Other agents: copy the folder into their skills directory, or run `DISABLE_TELEMETRY=1 npx skills add nvv-dev/writing-adrs`. Loads automatically when the task matches its description. Canonical source: [nvv-dev/dev-workflow](https://github.com/nvv-dev/dev-workflow). License: MIT.
