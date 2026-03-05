
# AGENTS.md

You are running inside Google Antigravity IDE.

## Pre-Flight Checklist
Before writing code, verify the following:
- Are the core environment constraints from GEMINI.md satisfied? (UTF-8, fail-fast env vars, host-mounted Docker configs).
- Have you selected the appropriate skill bundle from `C:\Users\trapj\.agent\skills`?

## Open Source Modularity Rules
- **Orthogonal Design:** Ensure features are decoupled. Changes to the database layer should not require changes to the routing layer.
- **Provider Isolation:** All external API calls (NIM, Openclaw, etc.) must go through an abstraction layer. Never hardcode API URLs in business logic.
- **Pathing:** All internal scripts must use robust pathing (`pathlib`).

- Always load and read `project.md` before making any edits.
- Follow the build steps in `project.md` in order, one at a time.

## Project Context

- Codebase: [stack / framework here]
- Current spec file: `project.md`
- Primary feature under active work: **[feature / migration name]**

Always read `project.md` before making changes. Treat it as the source of truth for architecture and steps.

---

## Roles

You may see multiple agents in this workspace. Use these roles:

- **Coordinator**
  - Reads `project.md` and this file.
  - Decomposes tasks and updates checkboxes in `project.md`.
  - Hands off focused coding tasks to Specialist agents.
- **Engineer**
  - Implements code and config as defined in `project.md`.
  - Keeps changes minimal and localized.
- **Reviewer**
  - Reviews diffs for correctness and unintended scope creep.
  - Ensures constraints and acceptance criteria are satisfied.

If only one agent is active, it must perform all three roles sequentially.

---

## Operating Rules

- Follow the build steps in `project.md` **in order**. Do not reorder them.
- Finish one step completely before starting the next.
- Prefer editing existing files over adding new concepts.
- Keep each change small: few files, clear purpose, no hidden side effects.
- Never hardcode secrets. Use env vars or configured secrets.
- All paths should be workspace‑relative.

When in doubt:
1. Re-read the relevant section of `project.md`.
2. Inspect existing code or docs (e.g., upstream library docs) before inventing new APIs.
3. If still unclear, add a short comment in `project.md` noting the ambiguity instead of guessing.

---

## Collaboration Protocol

- The **Coordinator**:
  - Updates checkboxes in `project.md` when a step is complete.
  - Writes brief notes under the step if anything deviates from the original plan.
- The **Engineer**:
  - Writes clear commit messages or change summaries (what changed, why).
  - Avoids mixing unrelated refactors with feature work.
- The **Reviewer**:
  - Checks that:
    - All updated files match the structure described in `project.md`.
    - New code has at least basic error handling and logging if specified.
    - Manual test commands in `project.md` actually run.

No agent should change high‑level goals or constraints without editing `project.md` first.

---

## Tools and Limits

- Use only the tools and skills referenced in `project.md` unless explicitly instructed otherwise.
- Do not:
  - Introduce new external services or frameworks.
  - Enable inter‑agent messaging or new Jobs without updating `project.md`.
- Prefer local tests and dry‑runs before wiring automation (cron / Jobs / schedulers).

---

## Definition of Done (Agent View)

A feature/migration is “done” only when:

- All checkboxes in `project.md` for this feature are ticked.
- Acceptance criteria in `project.md` pass (manual tests, jobs, skills, etc.).
- There is no open TODO in comments or docs related to this feature.
- This `AGENTS.md` does not contradict `project.md`.

If any of these fail, the work is not done, regardless of how much code has been written.
