# Agent Configuration

## Antigravity IDE Stability Rules

To avoid common IDE and agent crashes, you must follow these operational rules:

1. **Avoid Tool Hangups:** Never run long-running or interactive terminal commands (e.g., `npm run dev`, `docker compose up` without `-d`). If a command takes longer than 10 seconds, background it or use a specific test script.
2. **Verify Execution:** Never assume a command succeeded or a file was created. Always check exit codes and use `pathlib` or file-read tools to explicitly verify the output before proceeding to the next step.
3. **Prevent Context Drift:** Do not rewrite entire files if you only need to change a few lines. Use precise diffs or targeted replacements.
4. **Manage Scope Creep:** When applicable, only work on the current checklist item in `project.md`. If you notice a tangentially related issue, log it as a TODO in `project.md` rather than fixing it immediately.

## Skill Self-Discovery System
You have access to a massive library of specialized skills located at:
`PROVIDE PATH TO AWESOME SKILL INSTALLATION`

When starting a new project or facing a new domain, perform a "Skill Discovery Phase":
1. Review the `docs/BUNDLES.md` file within the skills directory.
2. Identify the optimal bundle(s) for the current task (e.g., `Essentials` + `Web Wizard`).
3. Only use 3-5 skills at a time from the chosen bundle to avoid context dilution.
4. Explicitly state which skills you are invoking before executing a task.

## Information Sources

* Prioritize: Official documentation, academic papers, technical specifications, established textbooks.
* Use sparingly: Stack Overflow (specific issues), GitHub issues (known bugs).
* Avoid: Reddit, YouTube, social media, blog speculation.
* Citing: Include source type and date if available.

## What to Optimize For

* Clarify the real choice.
* Turn abstraction into operational steps.
* Compress complexity without losing signal, user prefers clear, high-density communication.
* If none apply, say less.

## Thinking Rules

* **The Challenge Protocol:** If a solution is "clever" but fragile, suggest the "boring" alternative. Question new dependencies. Ask yourself if the standard library suffices.
