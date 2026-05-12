# AGENTS

This repository implements the VS Code extension `vscode-chat-customizations-evaluations`.
It analyzes and improves chat customization files in VS Code using GitHub Copilot via the `vscode.lm` API.

## Purpose

- Provide diagnostics and fixes for prompt, agent, instructions, and skill files.
- Analyze `.prompt.md`, `.agent.md`, `.instructions.md`, `SKILL.md`, and related customization files.
- Support `waza` evaluation workflows via commands and docs.

## Key areas

- `src/` — language server and analysis logic
  - `src/server.ts` — server entry point
  - `src/analyzers/llm.ts` — LLM-powered semantic analysis logic
  - `src/types.ts` — shared interfaces and protocol types
  - `src/__tests__/` — Vitest unit tests for analyzer behavior
- `client/` — extension client and manifest
  - `client/src/extension.ts` — activation and command wiring
  - `client/package.json` — client dependencies and scripts
- `skills/` — extension-provided chat skills
  - `skills/fix-customization-evaluation-diagnostics/SKILL.md`
- `docs/WAZA-USER-GUIDE.md` — waza integration and evaluation workflow
- `CONTRIBUTING.md` — development setup, build/test workflow, and local extension debugging

## Important conventions

- TypeScript strict mode is enabled across the repo.
- The extension is split between a server (`src/`) and a client (`client/src/`).
- Analyzer changes usually belong in `src/analyzers/llm.ts` and require tests in `src/__tests__/`.
- Commands and menus are declared in `package.json` under `contributes`.

## Useful commands

- `npm install` — install dependencies (includes client install via `preinstall`)
- `npm run build` — compile server and client
- `npm run compile` — build server only
- `npm test` — run Vitest tests
- `npm run lint` — run ESLint on server and client
- `npm run watch` — watch server changes
- `cd client && npm run watch` — watch client changes
- `npm run package` — bundle and package the extension

## Agent guidance

- Use this file as the primary repo-specific instruction set.
- Do not create `.github/copilot-instructions.md`; `AGENTS.md` is already the canonical guidance file.
- Prefer linking to `docs/WAZA-USER-GUIDE.md` and `CONTRIBUTING.md` rather than duplicating detailed setup instructions.
- Keep changes focused on the extension and its prompt-analysis workflow, not on generic prompt engineering.
- If you change analyzer behavior, update tests in `src/__tests__/` to cover the new behavior.
