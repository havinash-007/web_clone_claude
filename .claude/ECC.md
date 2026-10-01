# ECC — curated install

Source: https://github.com/affaan-m/ECC @ `c70874f` (v2.2.2), MIT (`.claude/ECC-LICENSE`).
Vendored into the repo (not the `ecc@ecc` plugin) so it works in every session, local or cloud, with zero setup.

## Installed

| Type | Items |
|---|---|
| Agents (11) | planner, typescript-reviewer, react-reviewer, build-error-resolver, react-build-resolver, security-reviewer, performance-optimizer, a11y-architect, e2e-runner, refactor-cleaner, silent-failure-hunter |
| Skills (14) | nextjs-turbopack, react-patterns, react-performance, frontend-patterns, frontend-a11y, browser-qa, make-interfaces-feel-better, motion-foundations, motion-patterns, design-system, verification-loop, search-first, e2e-testing, seo |
| Rules (11) | typescript/{coding-style,patterns,security}, react/{coding-style,hooks,patterns,security}, web/{coding-style,patterns,performance,security} — all path-scoped |

## Deliberately left out

- **Hook runtime** — 250 lines of hooks that need ECC's Node runtime installed in `~/.claude`; would break or no-op in cloud sessions and slows every tool call.
- **`rules/common/*`** — always-loaded and mandates TDD + 80% coverage and `ecc:`-prefixed agents; this repo has no test suite.
- **`rules/web/design-quality.md`** — tells the agent to impose its own style ("no template-looking UI"), which directly contradicts pixel-perfect cloning.
- **`*/testing.md`, `*/hooks.md` rules** — no test infra; hook advice is config-only noise.
- **ECC `security-review` / `code-review` skills** — would shadow Claude Code's built-in `/security-review` and `/code-review`.
- **The other ~270 skills / 57 agents** — other languages and domains (Go, Rust, Django, healthcare, trading…). Pure context bloat here.

## Local tweaks

- `rules/ecc/react/coding-style.md` — kebab-case files + named exports (repo convention).
- `skills/verification-loop` — maps to `npm run check`; skips the coverage phase.
- Dangling links to ECC `common/` rules replaced with plain text.

## Updating

Re-clone ECC, diff these folders against upstream, and re-apply the tweaks above. Want the full thing instead? Delete these files and run `/plugin marketplace add https://github.com/affaan-m/ECC` + `/plugin install ecc@ecc` — but don't do both.
