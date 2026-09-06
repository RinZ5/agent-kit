---
name: verification
description: Verify non-trivial implementation work with observable success criteria, focused checks, and relevant failure-path coverage.
---

# Verification

Use this workflow for non-trivial implementation work. Scale the effort to the risk and size of the change.

## Define Success

Translate the request into observable milestones before implementation:

```text
1. [implementation] -> verify: [observable result]
2. [implementation] -> verify: [observable result]
```

Identify relevant failure modes before coding. Consider null or missing values, empty collections, malformed input, type mismatches, timeouts, races, and partial failures only when they apply to the execution path.

## Protect Test Integrity

Fix implementation defects rather than weakening tests. Do not modify an existing test solely to make a failing build pass.

A test may change when requirements explicitly changed or the test is demonstrably incorrect. State that reason when it is not obvious from the change.

## Run Focused Checks

Run the narrowest relevant existing check first, then broader affected checks when the risk warrants them.

For non-trivial new logic, verify:

1. the primary happy path, and
2. at least one important edge case or failure mode.

Prefer the project's existing test infrastructure. Do not introduce a test framework for a small check. Create a persistent new test only when it provides ongoing regression value; otherwise use an appropriate temporary or existing runnable check.

## Resolve Failures

When verification fails:

1. identify the root cause,
2. fix the implementation,
3. rerun the narrowest relevant check, and
4. repeat until the success criteria pass or a genuine blocker is established.

Do not hide skipped checks or claim success without evidence. Report what passed, what failed, and any verification that could not be run.

