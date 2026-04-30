# my-coding-style

A minimal Node.js template wired with [agent-skills](https://github.com/addyosmani/agent-skills) for AI-assisted development. The code style is enforced by ESLint (`airbnb-base`) and EditorConfig.

## Project Structure

```
.editorconfig          → Editor defaults (utf-8, 2-space indent, LF)
.eslintrc.js           → ESLint config extending airbnb-base
index.js               → Entry point (run with `npm start`)
package.json           → Dependencies and scripts
.claude/
  skills/              → 7 lifecycle skills (SKILL.md per directory)
  commands/            → 5 slash commands: /spec /plan /build /review /ship
  agents/              → 3 personas used by /ship: code-reviewer, security-auditor, test-engineer
```

## The Flow

Five slash commands cover the lifecycle. Run them in order; skip what doesn't apply.

| Command   | Phase   | Skills invoked                                                                |
| --------- | ------- | ----------------------------------------------------------------------------- |
| `/spec`   | Define  | spec-driven-development                                                       |
| `/plan`   | Plan    | planning-and-task-breakdown                                                   |
| `/build`  | Build   | incremental-implementation, test-driven-development, debugging-and-error-recovery |
| `/review` | Review  | code-review-and-quality                                                       |
| `/ship`   | Ship    | shipping-and-launch (parallel fan-out to the three personas)                  |

Skills auto-trigger from their frontmatter `description` when their conditions are met, so you can also just describe the work and let Claude pick the right skill.

## Code Style

- Extends `airbnb-base` via ESLint
- 2-space indent, LF line endings, UTF-8, trim trailing whitespace, final newline (enforced by `.editorconfig`)
- Project-specific overrides live in `.eslintrc.js` (`no-undef`, `no-alert`, `quote-props`, `object-shorthand`, `no-console` off; `brace-style` error)

## Commands

- `npm start` — run `index.js`
- `npx eslint .` — lint the project (no script alias yet — add one if needed)

## Boundaries

- Always: run ESLint before committing; keep changes small and incremental (see `incremental-implementation`)
- Always: write a failing test first when fixing bugs (Prove-It pattern, see `test-driven-development`)
- Never: bypass ESLint with blanket `// eslint-disable` — disable specific rules with a justification
- Never: commit without running the full lint + test suite locally
