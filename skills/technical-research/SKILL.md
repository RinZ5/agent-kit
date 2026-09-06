---
name: technical-research
description: Resolve uncertain or version-sensitive implementation questions using authoritative documentation, installed code, and focused external research.
---

# Technical Research

Use research when implementation depends on uncertain, version-sensitive, deprecated, security-sensitive, or recently changed technical behavior. Research only enough to make the current decision reliably.

## Establish Local Context

Before searching externally, inspect the project when possible to determine:

- the installed library or framework version,
- relevant configuration and lockfiles,
- existing usage patterns, and
- available package source, generated types, or local documentation.

Do not apply documentation for an unknown or mismatched version.

## Retrieve Evidence

Use whatever web-search, documentation-retrieval, repository-inspection, or package-source capabilities the active harness provides. Refer to capabilities generically; do not assume a specific tool name or provider exists.

Prefer evidence in this order when applicable:

1. official documentation for the installed version,
2. official API or language reference,
3. installed package source or type definitions,
4. the official source repository,
5. maintainer release notes or migration guides, and
6. reputable secondary sources when primary sources are insufficient.

Avoid relying on tutorials, snippets, or forum answers when authoritative material resolves the question.

## Verify Applicability

Confirm that findings match the project's version, runtime, platform, and configuration. Check release or migration notes when behavior differs across versions.

When sources conflict, prefer the source closest to the installed implementation. Inspect source or types and perform a focused experiment if documentation remains ambiguous.

## Apply and Stop

Use the findings to choose the smallest correct implementation that fits project conventions.

Stop once sufficient authoritative evidence resolves the implementation uncertainty. Do not expand a focused task into unrelated library comparisons or speculative redesign.

If research shows the requested approach is unsafe, deprecated, incompatible, or impossible, explain the evidence before taking a materially different approach. State any meaningful remaining uncertainty.

