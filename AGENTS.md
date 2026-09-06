# AGENTS.md

**Tradeoff:** These guidelines prioritize sound architecture, verification, and code quality over raw speed. Do not rush when clarification would materially improve the result.

## 1. The Pragmatic Ladder

**Do not assume. Ask when it elevates quality.**

Before writing code, understand the problem, trace the relevant execution flow end to end, and evaluate the request against this ladder. Stop at the first rung that satisfies the current requirement:

1. **Does this need to be built?** Challenge speculative requirements and follow YAGNI.
2. **Does it already exist?** Reuse existing helpers, utilities, abstractions, and project patterns.
3. **Does the standard library cover it?** Prefer native platform capabilities when they solve the problem safely and clearly.
4. **Does an installed dependency solve it?** Prefer an existing suitable dependency over adding or rebuilding one.
5. **Can it be implemented directly?** Write the smallest clear solution without unnecessary abstraction.

Use the `minimal-code` skill for implementation work when it is available. The objective is the smallest clear solution, not the fewest lines.

### Scalability and Complexity

Choose algorithms, data structures, and concurrency patterns that naturally scale when the current problem requires them.

Do not confuse scalability with speculative abstraction. Avoid premature factories, single-use interfaces, unnecessary configuration, or extension points without a demonstrated requirement.

### Design Patterns

If a recognized design pattern would resolve a structural problem, meaningfully decouple brittle logic, or substantially improve maintainability, propose it before implementation. Explain both the present benefit and the added complexity. Do not introduce the pattern silently.

### Comments

Unless explicitly requested or required by project convention, do not add comments that merely restate the code. Prefer clear structure and naming.

When a deliberately temporary architectural ceiling must be recorded, use a single-line comment in this form:

```text
// tradeoff: [current limitation] -> [upgrade path]
```

Do not use `tradeoff:` comments to excuse avoidable technical debt.

## 2. Surgical Changes and Root Causes

**Touch only what is necessary. Fix the source, not the symptom.**

- Trace reported behavior to its origin. If a shared function is broken, fix it there and assess affected callers rather than patching one execution path.
- Match the existing style. Do not polish adjacent code, formatting, or comments unless the requested change requires it.
- Remove imports, variables, functions, or files made obsolete by the current change. Leave unrelated pre-existing dead code alone unless it blocks the work.
- Preserve unrelated user changes in a working tree. Do not overwrite or revert them.

## 3. Defensive Programming and Edge Cases

**The happy path is not enough. Anticipate relevant failure modes.**

Before implementation, consider edge cases that apply to the actual execution path, such as:

- null or missing values,
- empty collections,
- malformed input or type mismatches,
- network failures and timeouts,
- concurrency and race conditions, and
- partial failures.

Fail safely. Do not swallow errors silently. Handle them or propagate them with enough context to diagnose the failure.

If an unresolved edge case materially changes architecture, compatibility, security, or scope, clarify it before implementation.

## 4. Goal-Driven Execution and Verification

Define observable success criteria before non-trivial implementation. For multi-step work, state a brief plan in this form:

```text
1. [implementation] -> verify: [observable result]
2. [implementation] -> verify: [observable result]
```

Non-trivial changes must be verified on the primary path and at least one important edge case or failure path. Prefer existing tests and the narrowest relevant checks. Create a persistent new check only when it provides ongoing value.

Never weaken or rewrite an existing test solely to make a failure pass. Change a test only when requirements changed or the test is demonstrably incorrect.

Use the `verification` skill for the detailed workflow when it is available.

## 5. Memory Bank

For non-trivial projects, maintain concise durable context in a project-local `.memory/` directory. Use it for architectural decisions, completed milestones, important constraints, verification results, and paused complex work.

Read relevant memory before continuing existing work. Treat the current codebase and current user request as authoritative when memory is stale or contradictory.

Do not ask for permission to initialize or update the memory bank. If the project is a Git repository, ensure `.memory/` is ignored and never committed unless the user explicitly requests otherwise.

Use the `memory-bank` skill for the detailed workflow when it is available.

## 6. External Verification

Do not guess about uncertain, version-sensitive, deprecated, or recently changed technical behavior.

When external verification is needed, use the active harness's available web-search, documentation-retrieval, repository-inspection, or package-source capabilities. Prefer authoritative sources and verify that guidance matches the project's installed version.

Use the `technical-research` skill for the detailed workflow when it is available.

## 7. Clarification and Architectural Choices

Ask rather than guess when an unresolved requirement materially affects:

- correctness,
- architecture or data modeling,
- public interfaces,
- security or privacy,
- concurrency,
- compatibility, or
- implementation complexity.

Do not ask questions whose answers can be reliably determined from the repository, installed dependencies, memory bank, authoritative documentation, or established project conventions.

When clarification is necessary, present a small set of concrete engineering choices:

- provide two to four distinct options,
- put the recommended option first,
- explain the relevant tradeoff of each option briefly,
- default to one selection unless combining options is structurally valid, and
- avoid choices that do not materially affect the result.

If the active harness provides a structured question or user-input capability, prefer it. Otherwise, ask the same question directly in normal conversation.

Do not block progress on trivial preferences or decisions that can be made safely from existing evidence.
