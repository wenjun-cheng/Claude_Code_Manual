# CLAUDE.md

## Workflow Orchestration

### Plan Mode Default
- Enter plan mode for ANY non-trivial task (3+ steps or architectural decisions). Use plan mode for verification steps, not just building. Write detailed specs upfront to reduce ambiguity.
- If something goes sideways, STOP and re-plan immediately, don't keep pushing blindly.
- Stongly prefer best practices. Quick hacks are not acceptable.

### Subagent Strategy
- Use subagents liberally to keep the main context window clean.
- Offload research, exploration, and parallel analysis to subagents.
- Spawn multiple agents to work on isolatable tasks and use `git worktree` as appropriate.
- One task per subagent for focused execution.

### Autonomous Bug Fixing
- When given a bug report: just fix it. Don't ask for hand-holding.
- Point at logs, errors, failing tests — then resolve them. Require zero context switching from the user.
- Go fix failing CI tests without being told how.

### Elegance
- For non-trivial changes: pause and ask "is there a more elegant way?" (Skip this for simple, obvious fixes -- don't over-engineer).
- If a fix feels hacky: "Knowing everything I know now, implement the elegant solution".

### Verification
- Keep useful logs and visualizations to help understanding the situation better.
- Never mark a task complete without proving it works. Run tests, check logs, demonstrate correctness.
- Ask yourself: "Would a staff engineer approve this?"

### Self-Improvement
- After ANY correction from the user: update `tasks/lessons.md` with the pattern.
- Write rules for yourself that prevent the same mistake, ruthlessly iterate on these lessons until mistake rate drops.
- Review lessons at session start for relevant project.

### Task Management
- **Plan First:** Write plan to tasks/todo.md with checkable items
- **Verify Plan:** Check in before starting implementation
- **Track Progress:** Mark items complete as you go
- **Explain Changes:** High-level summary at each step
- **Document Results:** Add review section to tasks/todo.md
- **Capture Lessons:** Update tasks/lessons.md after corrections


## Development Standards

### Core Principles
- **Simplicity First:** Make every change as simple as possible. Impact minimal code.
- **No Laziness:** Find root causes. No temporary fixes. Senior developer standards.
- **Minimal Impact:** Only touch what's necessary. No side effects with new bugs.

### SOLID Principles
- **Single Responsibility (SRP):** Each class/module owns exactly one concern. Keep files small(<800 lines); split if they grow too large.
- **Open/Closed (OCP)**: Extend behavior through interfaces, not by modifying existing code.
- **Liskov Substitution (LSP)**: Any implementation of an interface must be swappable without breaking callers.
- **Interface Segregation (ISP)**: Prefer narrow, focused interfaces over large ones.
- **Dependency Inversion (DIP):** Depend on abstractions, not concrete implementations.

### DRY (Don't Repeat Yourself)
- Extract shared logic into reusable components.
- Avoid copy-pasting code between modules — create shared utilities instead.

### KISS (Keep It Simple, Stupid)
- Prefer the simplest solution that meets current requirements.
- Do not implement features "just in case" — follow YAGNI (You Aren't Gonna Need It).
- Three similar lines of code is better than a premature abstraction.

### Architecture Maintenance
- **Frequently update architecture documentation** when structural changes occur, especially:
  - Flowcharts (data flow, control flow)
  - File/class diagrams and their dependencies

### Testing
- Design tests carefully before implementing features.
- Unit tests must be environment-agnostic.
- Verify after every structural change that existing tests still pass.

### Config
- Prefer YAML config files over command-line arguments for long config settings. One `--config path/to/config.yaml` is ideal.

### Module Boundaries
- Communication between modules must use well-defined contracts to prepare for/maintain message-bus patterns.

### Others
- **Type Hints:** Use strict Python Type Hints (\typing` module) for all function signatures, class properties, and complex variables.
