# Ponytail for AAPI

This fork keeps Ponytail's original minimalism and adds an AAPI-specific architecture guard.

## What changes for AAPI

Ponytail still prefers YAGNI, reuse, standard library, native platform features, installed dependencies, and the smallest correct diff.

When working in AAPI, it additionally prefers:

`Existing Core → Existing Capability → Extension → Manifest/Composition → Existing Layer growth → New architecture last`

It must not simplify away AAPI contracts, security/trust boundaries, authority boundaries, evidence, traceability, or regression/conformance checks.

## Recommended mode

Use **full** for normal AAPI development.

- `lite`: exploratory work; builds the request and points out a simpler option.
- `full`: recommended; reuse-first and minimum-correct-diff rules are enforced.
- `ultra`: use manually for focused cleanup or over-engineering experiments. Do not use it as the default for architecture work.

## Install from this fork

From Codex CLI:

```bash
codex plugin marketplace add spring-kr/ponytail
```

Then open Codex and install Ponytail from the Ponytail marketplace. Review and trust the lifecycle hooks in `/hooks`, then start a new thread.

Node.js should be available on `PATH` for automatic lifecycle-hook activation. The skills can still be invoked without the hooks.

## Use in Codex

Start normal AAPI work with:

```text
@ponytail full
```

Then give the task normally. Example:

```text
@ponytail full
Implement this RFC using existing AAPI Core/Capability/Extension/Composition paths first.
Preserve security, authority, evidence, traceability, and existing regression contracts.
Do not add a new Core or Layer unless the existing architecture is demonstrably insufficient.
```

For a complexity-only review after implementation:

```text
@ponytail-review
```

For a repository-wide over-engineering audit:

```text
@ponytail-audit
```

Ponytail review/audit are complexity reviews, not replacements for correctness, architecture, security, ADS, test, or evidence gates.

## Recommended AAPI workflow

1. RFC / requirement is the source of intent.
2. Activate `@ponytail full`.
3. Reuse existing architecture before creating anything new.
4. Implement the smallest correct change.
5. Run focused tests, then the required regression/conformance gates.
6. Optionally run `@ponytail-review` to find accidental complexity.
7. Produce/update evidence and traceability.

A Ponytail win in AAPI is not simply fewer lines. It is fewer unnecessary lines **without weakening an architectural invariant**.
