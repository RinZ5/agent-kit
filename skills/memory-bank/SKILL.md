---
name: memory-bank
description: Maintain concise project-local context for non-trivial work, architectural decisions, milestones, verification results, and paused tasks.
---

# Memory Bank

Maintain durable project context outside the conversation window. Record facts that help future work resume accurately without turning the memory bank into a transcript.

## Initialize

1. Locate the project root.
2. Create `.memory/` only if it does not exist.
3. If the project is a Git repository, inspect `.gitignore` and add `.memory/` only when it is not already ignored.
4. Do not commit memory files unless the user explicitly requests it.

Perform routine initialization and updates without asking permission.

## Recall

Before continuing non-trivial existing work:

1. Inspect `.memory/`.
2. Read only files relevant to the current task.
3. Reconstruct architectural decisions, current implementation state, unresolved issues, constraints, and prior verification results.

Memory is supporting context, not the source of truth. When memory conflicts with the current codebase or current user request, follow the current evidence and update the stale entry.

## Update

Update the memory bank when:

- an architectural decision is made,
- a milestone is completed,
- an important constraint is discovered,
- verification produces durable information, or
- complex work is paused.

Use focused files when useful, for example:

```text
.memory/
|-- architecture.md
|-- current_task_state.md
|-- decisions.md
`-- verification.md
```

Create only files with useful content. Do not generate empty templates.

## Write Durable Facts

Record decisions, rationale, constraints, implementation state, and verified results. Avoid chat transcripts, vague statements, unverified speculation, secrets, credentials, and sensitive personal data.

Keep entries concise and scannable. Include dates only when chronology matters.

## Maintain

Update existing entries instead of appending contradictions. Replace or remove stale information when the implementation changes. At a pause, record the exact remaining work and the next useful verification step.
