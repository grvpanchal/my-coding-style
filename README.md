# Code Style Implementation Guide

A minimal Node.js starter that combines:

1. **ESLint + airbnb-base** for code style enforcement.
2. **[agent-skills](https://github.com/addyosmani/agent-skills)** for an AI-assisted development flow in [Claude Code](https://claude.com/claude-code).

## Setup

```sh
npm install
```

Install the [ESLint VS Code extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) for inline diagnostics.

## The Flow

Five slash commands, run in order, cover the full lifecycle:

```
/spec  →  /plan  →  /build  →  /review  →  /ship
 define    plan      build      review     ship
```

| Command   | What it does                                                                     |
| --------- | -------------------------------------------------------------------------------- |
| `/spec`   | Turn a vague idea into a structured `SPEC.md` (objective, features, boundaries). |
| `/plan`   | Decompose the spec into vertical-slice tasks with acceptance criteria.           |
| `/build`  | Implement the next task incrementally with TDD; debug if anything fails.         |
| `/review` | Five-axis review: correctness, readability, architecture, security, performance. |
| `/ship`   | Parallel fan-out to code-reviewer, security-auditor, test-engineer for go/no-go. |

Skills auto-trigger from natural-language requests too — just describe what you want.

## What's Included

```
.claude/
├── skills/        # 7 lifecycle skills
├── commands/      # 5 slash commands
└── agents/        # 3 specialist personas (used by /ship)
CLAUDE.md          # Project conventions for Claude
index.html         # Static showcase page (open in any browser)
.editorconfig      # Editor defaults
.eslintrc.js       # airbnb-base config
```

The skills, commands, and personas are sourced from <https://github.com/addyosmani/agent-skills> (MIT). To pull a wider set later, see that repo's catalogue.

## Code Style

`airbnb-base` with these project overrides (`.eslintrc.js`):

```js
module.exports = {
  extends: 'airbnb-base',
  rules: {
    'no-undef': 'off',
    'no-alert': 'off',
    'quote-props': 'off',
    'brace-style': 2,
    'object-shorthand': 'off',
    'no-console': 'off',
  },
};
```

EditorConfig (`.editorconfig`) enforces 2-space indent, UTF-8, trimmed trailing whitespace, and final newlines.

## Run

```sh
npm start          # node ./
npx eslint .       # lint
```
