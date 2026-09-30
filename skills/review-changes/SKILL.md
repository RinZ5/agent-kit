---
name: review-changes
description: Review non-trivial implementation changes for correctness, design quality, repository conventions, maintainability, and questionable decisions. Use after implementation work or when the user asks for a code review.
---

# Review Changes

Review the implementation before considering the task complete. Use this skill after non-trivial implementation work or when the user explicitly asks for a code review. Skip it for trivial edits unless the user requests it.

This review is separate from tests, linting, formatting, and build verification. Those checks establish whether the code runs; this review determines whether the implementation is sensible and appropriate for the existing codebase.

## Review As Another Developer

Read the relevant diff and enough surrounding code to understand the existing design. Treat the changed code as if it were submitted by another developer. Prefer repository conventions and established architecture over generic best practices.

Review only the task's changes and directly affected code. Do not rewrite unrelated user changes or broaden the scope without a concrete reason.

## Review

Check for:

- incorrect or questionable algorithms
- unnecessary complexity or abstractions
- duplicated logic
- hidden assumptions or surprising side effects
- poor naming or unclear intent
- inappropriate data structures
- avoidable allocations or expensive operations
- incorrect ownership or lifetime decisions
- weak error handling
- violations of existing architecture or design patterns
- inconsistencies with nearby code
- code that works but is unnecessarily difficult to maintain

Apply YAGNI. Do not recommend abstractions, optimizations, or extensibility without a concrete present need. If a simpler implementation satisfies the same requirements without harming the existing design, prefer it.

## Explain Non-Obvious Code

Explain non-obvious algorithms, data structures, abstractions, optimizations, concurrency mechanisms, ownership strategies, and architectural decisions:

1. How the code works.
2. Why this approach was chosen.
3. Important assumptions or tradeoffs.
4. Relevant alternatives when the choice is not obvious.

Do not explain trivial code or add source comments merely to satisfy this requirement. Add comments only when future maintainers need an invariant, constraint, workaround, or other non-obvious behavior documented in the code.

## Findings

Classify meaningful findings as:

- **Must fix** — likely incorrect, unsafe, or violates an important project constraint.
- **Should fix** — questionable design or maintainability issue with a clear better alternative.
- **Consider** — legitimate tradeoff worth bringing to the developer's attention.

Do not invent findings just to populate the review. If the implementation is appropriate, say so explicitly.

## Fix Findings

In build mode, fix clear **Must fix** issues before completing the task. Fix straightforward **Should fix** issues when they are within scope. Do not automatically act on subjective **Consider** findings; explain the tradeoff instead.

In read-only or review-only mode, report findings without editing the implementation.

After making a significant correction, review the affected code again. Run verification separately according to the project's verification workflow.

## Report

Finish with a concise review containing:

### What Changed

Summarize the implementation and its execution or data flow.

### Why This Approach

Explain the important implementation and design decisions.

### Findings

Report meaningful Must fix, Should fix, and Consider findings with file and line references where applicable. Omit empty categories.

### Important Details

Explain any non-obvious algorithms, assumptions, complexity, ownership, data structures, or other behavior the developer should understand.

Keep the report proportional to the change. A simple change may require only a few sentences; a complex algorithm or architectural change deserves a deeper explanation.
