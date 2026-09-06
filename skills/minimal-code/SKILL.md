---
name: minimal-code
description: Implement coding changes with the smallest clear solution that satisfies current requirements, following YAGNI without sacrificing correctness or readability.
---

# Minimal Code

Implement the smallest clear solution that completely satisfies the current requirement. Minimize unnecessary code, abstractions, dependencies, and indirection—not line count.

## Use the Smallest Sufficient Rung

Prefer, in order:

1. no code when no change is needed,
2. existing project code or configuration,
3. a standard-library or native platform operation,
4. an already-installed suitable dependency,
5. a direct expression or small local function, and
6. a new abstraction only when the current problem requires one.

Stop as soon as the requirement is clearly and safely satisfied.

## Follow YAGNI

Do not add functionality for hypothetical future requirements. Avoid speculative configuration, extension points, generic helpers, single-implementation interfaces, single-path factories, wrappers around stable APIs, plugin systems, compatibility layers, and future-proofing abstractions.

Add structure when a present requirement creates a concrete benefit.

## Keep Code Direct

Keep behavior local when it is used in one place and remains easy to understand. Extract an abstraction when it solves a current problem such as meaningful duplication, multiple implementations, independently testable complex behavior, an unstable dependency boundary, or a genuinely distinct responsibility.

Similarity alone does not require a shared abstraction.

## Prefer Clarity Over Brevity

A one-liner is good only when it is also the clearest representation of the operation. Do not compress code into nested expressions, dense chains, or clever syntax merely to reduce line count.

A straightforward five-line implementation is better than an opaque one-liner. Both are better than a multi-class design with no present need.

## Use Dependencies Deliberately

Do not add a dependency for behavior that can be implemented clearly and safely with a small amount of native code. Use an existing dependency when it already solves the problem well.

Do not reimplement substantial, security-sensitive, or standardized functionality merely to avoid a justified dependency.

## Limit Refactoring

Do not refactor surrounding code unless the requested change requires it. When existing structure makes a simple change unnecessarily difficult, make the smallest structural improvement needed to remove that obstacle.

Do not redesign the system for hypothetical future changes.

## Decision Test

Before adding code or structure, ask:

1. Does the current requirement need this?
2. Does something already solve it?
3. Does this abstraction remove complexity now?
4. Would the simpler implementation be harder to understand, verify, or maintain?

If the extra structure has no concrete present benefit, do not add it.

A solution is appropriately minimal when it is correct, readable, verified in proportion to risk, free of speculative functionality, and cannot lose more code without losing clarity or required behavior.

