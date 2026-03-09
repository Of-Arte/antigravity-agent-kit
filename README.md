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

---

## Requirements

Before using this kit, you should have:
- Google Antigravity IDE installed.
- A local clone of [antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills) OR another skills collection you plan to route to.

---

## Setup Prerequisites

1. **Install Antigravity and Gemini CLI**
   - Follow the official Antigravity / Gemini setup guides for your OS.
2. **Clone Skills Repository**
   - Clone `antigravity-awesome-skills` somewhere on your machine.
   - Note the absolute path to its `skills` directory (you’ll paste this into `GEMINI.md`).

3. **Create or Update Global GEMINI.md**
   - Ensure `~/.gemini/GEMINI.md` exists.
   - Copy the kit’s `GEMINI.md` content into it, then replace `PROVIDE PATH TO AWESOME SKILL INSTALLATION` with your actual skills path.

4. **Prepare a Project Repo**
   - Create or open a project on GitHub.
   - Add `AGENTS.md` and `project.md` from this kit to the repo root.
   - Use an LLM to fill in the blanks in `project.md` based on your project idea, then commit it as the spec.

Once these are done, opening the repo in Antigravity will load the global rules plus the project-specific templates automatically.

---

## Quick Start

1. Copy `GEMINI.md` to `~/.gemini/GEMINI.md` (or append if one exists)
2. Open `GEMINI.md` and update the skills path placeholder:
   ```
   ## Skill Self Discovery System
   You have access to a massive library of specialized skills located at:
   `PROVIDE PATH TO AWESOME SKILL INSTALLATION`
   ```
   Replace with the absolute path to your local [antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills) installation. Example:
   - Windows: `C:\Users\yourname\.agent\skills`
   - macOS/Linux: `/home/yourname/.agent/skills`

3. Copy `AGENTS.md` and `project.md` into the root of any new project repo
4. **Fill in `project.md` using an LLM:**
   - Paste the template into your preferred LLM (ChatGPT, Gemini, Claude, etc.)
   - Give it a brief description of your project idea or feature goal
   - Ask it to fill in all `[bracketed fields]` based on your context
   - Review the output, then commit it to your repo as the agent's source of truth
5. Open the repo in Antigravity — the agent will load the rules and follow the spec automatically

---

## Design Principles

- **Low interference**: agent works through a checklist step by step without asking unnecessary questions
- **Spec driven**: all goals, constraints, and acceptance criteria live in `project.md`, not in chat
- **Skill aware**: GEMINI.md points the agent to your local skills directory for self directed tool selection
- **Fail fast**: hard rules for env validation, path safety, encoding, and Docker config are enforced globally

---

## Skill Bundle Routing

This kit assumes you have [antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills)
installed locally. GEMINI.md instructs the agent to:

1. Read `BUNDLES.md` from your configured skills directory
2. Select the most relevant bundle(s) for the current task
3. Invoke only 3–5 skills at a time to prevent context dilution

**You must set your local skills path in `GEMINI.md` before this works.** See Quick Start step 2.

---

## Known Antigravity Pain Points (Pre-Resolved)

These issues are documented and guarded against in the included config files:

- Agent context drift in long sessions
- MCP tool hangups and silent terminal failures
- Gemini over planning instead of acting
- Model/gateway version mismatches
- Context bloat in large repos

---

## Contributing

Open source. PRs welcome for:
- New GEMINI.md rule snippets with documented rationale
- Additional `project.md` templates for specific project types (APIs, CLI tools, automation pipelines, etc.)
- Validated pain point fixes from your own Antigravity sessions

---

## License

MIT
