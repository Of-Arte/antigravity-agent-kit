### Project Plan

# [Project Name]: [One-line description]

## Context

<!--
What exists today. What is broken, missing, or being replaced.
One paragraph max.
-->

- **Current state:** [what exists now]
- **Target state:** [what we're building]
- **Scope boundary:** [what is explicitly out of scope for this spec]

---

## Architecture

<!--
ASCII or text diagram showing data/control flow.
Keep it under 20 lines.
-->

```
[Entry point]
  └─► [Layer 1]
        └─► [Layer 2]
              └─► [Output / side effect]
```

---

## Repo Structure

<!--
Only list files that the agent needs to create or edit.
Do not list unchanged files.
-->

```
project/
├── src/[module]/
│   ├── [file].py        # [one-line purpose]
│   └── [file].py        # [one-line purpose]
├── config/
│   └── [config].json    # [one-line purpose]
├── [skill or job dir]/
│   └── [file]           # [one-line purpose]
└── ENVIRONMENT.md        # required env vars
```

---

## Build Steps

<!--
Ordered. Each step is independently completable.
Agent checks off each before moving to the next.
Keep each step to 3-5 bullets max.
-->

### [ ] 1. Environment
- [ ] Add dependencies to `requirements.txt` or `pyproject.toml`
- [ ] Create `ENVIRONMENT.md` listing all required env vars with descriptions
- [ ] Verify core imports work without launching UI or side effects

### [ ] 2. [Core module / wrapper]
- [ ] Implement `[function](config: dict) -> dict`
- [ ] Input schema: `[key, key, key]`
- [ ] Output schema: `{ [key]: ..., [key]: ..., [key]: ... }`
- [ ] Raise explicit errors; never return silently empty results

### [ ] 3. [Config / registry]
- [ ] Create `config/[file].json` with schema:
  ```json
  {
    "[field]": "[type and purpose]",
    "[field]": "[type and purpose]"
  }
  ```
- [ ] Implement selector / loader that reads this file

### [ ] 4. [Dispatcher / router]
- [ ] Route `[input_type]` to correct handler
- [ ] Unimplemented variants raise `NotImplementedError` explicitly

### [ ] 5. [Skill / interface definition]
- [ ] Define tool `[tool_name]` with input and output schema
- [ ] Behavior: [what it does in plain terms]

### [ ] 6. [Job / schedule definition]
- [ ] Schedule: `[cron expression]`
- [ ] Action: call `[skill].[tool]` with `[fixed params]`
- [ ] On success: write to `[output path]`
- [ ] On failure: log structured error, do not crash

### [ ] 7. Manual test path
- [ ] `python -m [module].manual_test [--flags]`
- [ ] Prints result JSON and output artifact path to stdout

---

## Constraints

<!--
Hard rules the agent must not violate.
Keep to ≤7 items.
-->

- [ ] No hardcoded secrets; use env vars or secrets manager
- [ ] All file paths are workspace-relative
- [ ] New files match the structure defined in **Repo Structure** above
- [ ] Do not introduce new dependencies unless a build step explicitly requires one
- [ ] [Project-specific constraint]
- [ ] [Project-specific constraint]

---

## Acceptance Criteria

<!--
Binary pass/fail checks. If all pass, the spec is done.
-->

- [ ] `manual_test` runs end-to-end and produces expected output artifact
- [ ] [Skill/tool] loads and returns valid JSON for a happy-path call
- [ ] [Job/schedule] fires and writes output to correct path
- [ ] Two consecutive runs behave correctly under [cooldown / dedup / idempotency rule]
- [ ] A failed run logs a structured error and does not block the next run
