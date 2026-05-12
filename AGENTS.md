# AGENTS

This repository implements a VS Code extension for analyzing and improving AI prompt customization files.

## What this project is

- A VS Code extension named `vscode-chat-customizations-evaluations`.
- It provides LLM-powered analysis for prompt files, agent files, skill instructions, and other customization documents.
- The extension integrates with GitHub Copilot via the `vscode.lm` API and exposes diagnostics in the Problems panel.

## Key areas

- `src/` — language server and analyzer logic
  - `src/server.ts` — server entry point
  - `src/analyzers/llm.ts` — LLM-powered semantic analysis implementation
  - `src/types.ts` — shared interfaces, enums, protocol types, diagnostics, and agent metadata definitions used across the extension
  - `src/__tests__/` — unit tests for analyzer behavior
- `client/` — VS Code extension client
  - `client/src/extension.ts` — extension activation and command wiring
  - `client/package.json` — client dependencies and scripts
- `skills/` — extension-provided chat skill(s)
  - `skills/fix-customization-evaluation-diagnostics/SKILL.md`
- `docs/` — published project documentation
  - `docs/WAZA-USER-GUIDE.md`
- `CONTRIBUTING.md` — development setup, architecture, build/test workflow, and contribution guidance

## Important conventions

- TypeScript strict mode is used across the project.
- The core logic is split between the server (`src/`) and client (`client/src/`).
- Tests live under `src/__tests__/` and use Vitest.
- `package.json` defines primary scripts and extension metadata.

## Useful commands

- `npm install` — install dependencies
- `npm run build` — compile the server and client
- `npm test` — run tests
- `npm run lint` — run ESLint on server and client sources
- `npm run watch` — watch server sources for changes
- `cd client && npm run watch` — watch client sources for changes
- `npm run package` — bundle and package the extension

## What agents should know

- This repo is about building a VS Code extension, not about the contents of prompts themselves.
- When changing analyzer behavior, update `src/analyzers/llm.ts` and add tests in `src/__tests__/`.
- The extension supports diagnostics and commands for prompt and customization files.
- Use `docs/WAZA-USER-GUIDE.md` for the extension’s evaluation workflow and `CONTRIBUTING.md` for development setup.

## Notes

- There is no existing `.github/copilot-instructions.md` or `AGENTS.md`; this file is the primary agent guidance.
- Keep changes aligned with the existing client/server split and extension manifest declarations.
