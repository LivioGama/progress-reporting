---
trigger: always_on
---

# Progress Reporting

For non-trivial work, give honest `Progress: NN/100` updates at meaningful milestones and roughly every 30 seconds while active.

The percentage is a current estimate of user-visible completion, not a plan item, commitment, or substitute for verification.

Each progress update should briefly say what is done, what is happening now, and what remains or blocks completion.

## Subagents

When you are a **subagent** working on a delegated task, apply the same rule scoped to your own assignment:

- Report `Progress: NN/100` against **your** delegated task, not the overall request.
- Tag your updates so the parent can attribute them, e.g. `Subagent [auth-lane]: Progress: 40/100`.
- State your status: `queued` → `running` → `done`, or `blocked` (with the reason).
- Report a blocker or completion **immediately** so the parent can relay it without polling.
- Keep the honest-estimate rules: your percentage is your view of your task, never a commitment. The parent reconciles lane estimates into the user-visible whole; do not try to express the overall request unless you are the coordinator.

## Coordinating Agent Reporting on Subagents

When you are the **main agent** and have delegated work to subagents (including parallel / fanned-out lanes), report on their progress, not just your own:

- **Track each subagent**: name/id, assigned task, progress %, and status (`queued`, `running`, `done`, `blocked`).
- **Aggregate**: combine your own work with subagent work into one overall `Progress: NN/100` for the user-visible request.
- **Per-subagent breakdown**: when multiple subagents run in parallel, show each one:

  ```
  Progress: 55/100  (coordinator)
  - auth-lane:   Progress: 60/100 · running
  - ui-lane:     Progress: 30/100 · running
  - tests-lane:  Progress: 100/100 · done
  Blocks: ui-lane waiting for API keys
  ```

- **Relay immediately**: re-emit the aggregate whenever any subagent finishes, blocks, changes progress, or a new subagent starts, so the user hears about it without polling.
- **Attribute honestly**: present each figure as that lane's estimate; never present a subagent's percentage as your own completion.

## Example Usage (coordinator with subagents)

```
Progress: 70/100
Done: Core refactor, database schema; docs-lane finished
Now: 2 of 3 lanes still running (auth, ui); integrating auth-lane output
Remains: UI polish, end-to-end testing
Sub-agents: auth (75/100 · running), ui (40/100 · running), docs (100/100 · done)
```

Apply the main rule's frequency and content-quality guidance to subagent, coordinator, and aggregate updates alike.
