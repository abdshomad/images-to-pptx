# Agent Instructions & Workflow Protocol

> **Core Directive**: Follow the standards defined in [`autonomous-coding-agents/AGENTS.md`](./autonomous-coding-agents/AGENTS.md) and [`autonomous-coding-agents/README.md`](./autonomous-coding-agents/README.md).
>
> [!CAUTION]
> **Submodule Immutability**: The `autonomous-coding-agents/` submodule is strictly **100% READ-ONLY**. Do not modify submodule files directly. Place parent overlays/diffs in `patches/autonomous-coding-agents/` and custom runners in `scripts/`. Keep submodule `git status` clean at all times.

---

## ⚡ Infinite Evolution Flywheel (`i` → `n, n, n... ♾️`)

The workspace adopts the **`inex`** autonomous agent execution method:

| Command | Action | Directive | Reference Skill / Doc |
|:---|:---|:---|:---|
| **`i` / `init`** | **Define** | Ingest research/grill into `docs/deep-research/`; author PRD in `docs/prd/`; scaffold baseline. | [`skills/spec-driven-development/`](./autonomous-coding-agents/skills/spec-driven-development/) |
| **`n` / `next`** | **Build & Evolve** | Implement top `[TODO]`. Auto-runs `e` when plan empty. Enforces quality gates (`t` → `f` → `c` → `r`). | [`skills/test-driven-development/`](./autonomous-coding-agents/skills/test-driven-development/) |
| **`n{x}`** (e.g. `n3`) | **Batch Build** | Run `{x}` enhancement cycles sequentially in 1 turn. | [`autonomous-coding-agents/AGENTS.md`](./autonomous-coding-agents/AGENTS.md) |
| **`e` / `enhance`** | **Plan** | Decompose PRD into 3 tasks/module in `plans/next-enhancements.md`. | [`skills/task-decomposition/`](./autonomous-coding-agents/skills/task-decomposition/) |
| **`focus: <dir>`** | **Steer** | 1-batch focus override. Auto-returns to PRD roadmap when done. | [`plans/focus.md`](./plans/focus.md) |
| **`focus: reset`** | **Clear** | Cancel focus; restore PRD roadmap. | [`plans/focus.md`](./plans/focus.md) |
| **`t` / `f`** | **Verify & Fix** | Run test suites (`t`); fix failures (`f`) or log to `issues/`. | [`skills/debugging-and-recovery/`](./autonomous-coding-agents/skills/debugging-and-recovery/) |
| **`c` / `r`** | **Review & Audit** | Enforce ≤256 LOC per file (`c`); audit PRD & architecture compliance (`r`). | [`skills/code-audit-and-refactor/`](./autonomous-coding-agents/skills/code-audit-and-refactor/) |
| **`d` / `m`** | **Ship & Release** | Milestone check (`m`) & deployment/changelog (`d`). | [`skills/milestone-and-release/`](./autonomous-coding-agents/skills/milestone-and-release/) |

---

## 📂 Repository & Project Structure

```text
.
├── AGENTS.md                          # Root workflow contract (this file)
├── autonomous-coding-agents/          # Submodule (100% READ-ONLY)
│   ├── AGENTS.md                      # Core agent rules & lifecycle contract
│   ├── README.md                      # Framework documentation
│   ├── docs/                          # Guides and integration references
│   ├── plans/                         # Templates & plans
│   └── skills/                        # Engineering skills
├── docs/                              # Project documentation & PRDs
│   ├── deep-research/                 # Codebase analysis & research notes
│   └── prd/                           # Product Requirement Documents
├── plans/                             # Execution tracking
│   ├── focus.md                       # Priority steering & active focus
│   └── next-enhancements.md           # Task queue & backlog
├── issues/                            # Issue tracking (00X-<topic>.md)
├── screenshots/                       # Step captures & visual proof
├── patches/autonomous-coding-agents/  # Submodule patch overrides
└── scripts/                           # Project automation scripts
```

---

## 🧭 Core Guidelines & Anti-Rationalization

1. **Submodule Safety**: Never edit `autonomous-coding-agents/` directly. Keep `git status` clean.
2. **Extreme Concision**: Maximize token density; eliminate fluff, greetings, and filler text.
3. **Relative Paths**: Always use relative paths across code, docs, and plans.
4. **Quality Verification**: Verify test suites (`t`) and generate visual proofs before marking any task `[DONE]`.
5. **LOC Limit**: Enforce ≤256 lines of code per file; modularize when exceeded.
6. **Task Completion Contract**: Every turn ends with:
   ```text
   [DONE] <Task ID/Action>: <Brief summary>. Tests: <green result>.
   👉 Next: Type 'n' (or 'focus: <direction>' to steer)
   ```

---

## 🔗 Key Links

- [Submodule GitHub Repository](https://github.com/abdshomad/autonomous-coding-agents.git)
- Submodule Core Instructions: [`autonomous-coding-agents/AGENTS.md`](./autonomous-coding-agents/AGENTS.md)
- Submodule Integration Docs: [`autonomous-coding-agents/docs/integrations/submodule.md`](./autonomous-coding-agents/docs/integrations/submodule.md)
- Submodule Skills Directory: [`autonomous-coding-agents/skills/`](./autonomous-coding-agents/skills/)
