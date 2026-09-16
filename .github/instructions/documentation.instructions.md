---
description: 'Commenting and documentation standards for the Tailspin Toys codebase'
applyTo: '**/*.{ts,astro,css}'
---

# Commenting and Documentation Standards

## Comment intent, not mechanics

- Explain **why** code exists, including business rules, invariants, accessibility decisions, and non-obvious trade-offs.
- Do not add comments that merely restate a name, condition, loop, or CSS utility that is already clear from the code.
- Keep comments concise and close to the decision they explain.
- Treat stale comments as bugs: update or remove a comment whenever the related code changes.
- Use TSDoc (`/** ... */`) for API documentation and ordinary comments (`//` or `/* ... */`) only for local reasoning.

## Data-layer API documentation

Every exported function in `db/` and `src/lib/` must have a TSDoc comment that:

- States the function's purpose and any important ordering, determinism, or error behavior.
- Documents every parameter with `@param`, including the injectable `db` argument used by data-access helpers.
- Documents the result with `@returns`.

Keep the public API typed with explicit parameter and return types. Private implementation details do not need TSDoc unless their behavior is non-obvious.

## Astro component contracts

Every reusable `.astro` component must define and document its `Props` interface in frontmatter. Add a short TSDoc property description for each prop whose purpose, accepted values, default, or interaction with other props is not obvious from its name and type. Page-only components may keep an internal `Props` interface when Astro props are used.
