# antigravity-agent-kit

A minimal, opinionated starter kit for building reliable coding agents in Google Antigravity IDE.

Includes production-tested templates for `GEMINI.md`, `AGENTS.md`, and `project.md`
that enforce low-interference iteration, modular architecture, and skill-based task routing.

---

## What's Included

| File | Purpose |
|------|---------|
| `GEMINI.md` | Global rules for Antigravity — loaded automatically at IDE startup |
| `AGENTS.md` | Per-project agent roles, operating rules, and collaboration protocol |
| `project.md` | Feature/migration spec template with ordered build steps and acceptance criteria |
| `docs/PAIN_POINTS.md` | Documented common Antigravity failure modes with fixes baked into the config |

---

## Quick Start

1. Copy `GEMINI.md` to `~/.gemini/GEMINI.md` (or append if one exists)
2. Copy `AGENTS.md` and `project.md` into the root of any new project repo
3. Fill in the bracketed fields in `project.md` for your specific feature/migration
4. Open the repo in Antigravity — the agent will load the rules and follow the spec automatically

---

## Design Principles

- **Low interference**: agent works through a checklist step-by-step without asking unnecessary questions
- **Spec-driven**: all goals, constraints, and acceptance criteria live in `project.md`, not in chat
- **Skill-aware**: GEMINI.md points the agent to your local skills directory for self-directed tool selection
- **Fail fast**: hard rules for env validation, path safety, encoding, and Docker config are enforced globally

---

## Skill Bundle Routing

This kit assumes you have [antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills)
installed locally. GEMINI.md instructs the agent to:

1. Read `BUNDLES.md` from your skills directory
2. Select the most relevant bundle(s) for the current task
3. Invoke only 3-5 skills at a time to prevent context dilution

Update the skills path in `GEMINI.md` to match your machine.

---

## Known Antigravity Pain Points (Pre-Resolved)

These issues are documented and guarded against in the included config files:

- Agent context drift in long sessions
- MCP tool hangups and silent terminal failures
- Gemini over-planning instead of acting
- Model/gateway version mismatches
- Context bloat in large repos

See `docs/PAIN_POINTS.md` for the full breakdown and exact fix applied per issue.

---

## Contributing

Open source. PRs welcome for:
- New GEMINI.md rule snippets with documented rationale
- Additional `project.md` templates for specific project types (APIs, CLI tools, automation pipelines, etc.)
- Validated pain point fixes from your own Antigravity sessions

---

## License

MIT
