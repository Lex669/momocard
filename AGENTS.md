# Repository Guidelines

## Project Structure & Module Organization

This repository is a Claude/Qoder plugin that turns study material into Markji (墨墨记忆卡) card text. It contains documentation and plugin configuration, not application source code.

- `.claude-plugin/plugin.json` — Claude/Qoder plugin manifest and metadata.
- `.codex-plugin/plugin.json` — Codex-compatible plugin manifest and presentation metadata.
- `commands/momocard.md` — `/momocard` slash-command entry point.
- `skills/momocard/SKILL.md` — main card-generation workflow.
- `skills/momocard/references/markji-syntax.md` — authoritative Markji syntax rules and the 12-item output checklist.
- `skills/momocard/references/card-design.md` — blank selection, card types, and visual conventions.
- `skills/momocard/examples/example-cards.md` — complete input/output examples used as the quality baseline.
- `README.md` — user-facing installation and usage documentation.

Keep new references and examples in their existing directories. Use lowercase, hyphenated Markdown filenames such as `formula-examples.md`.

## Build, Test, and Development Commands

There is no build system or automated test suite. Validate the repository by reviewing the Markdown and checking generated cards against `skills/momocard/references/markji-syntax.md`. To package the plugin while preserving hidden files and relative paths:

```powershell
tar -a -c -f momocard.zip .claude-plugin .codex-plugin commands skills README.md
```

## Coding Style & Naming Conventions

All content is Markdown. Keep headings descriptive, use two-space indentation for nested lists, and write concise, direct instructions. Preserve Chinese source wording in card material; only permitted reordering and `[F#n#...]` blanks may change presentation. Markji tag names and parameters are case-sensitive (`T`, `P`, `F`, `Choice`, `E`); use six-digit lowercase hexadecimal colors.

## Testing Guidelines

When changing card-generation behavior, add or update an example in `skills/momocard/examples/example-cards.md`. Generate at least one small sample and apply the 12-item checklist in `markji-syntax.md`; cover blanks, choices, and formulas when those features change. Verify chapter markers (`###章节名`) and card separators (`===`) remain valid.

## Commit & Pull Request Guidelines

Git history is not included in this checkout. Use concise imperative commit subjects, one concern per commit, such as `Add math formula examples`. Pull requests should state what changed and why, link an issue when applicable, and include sample input/output for behavior changes. Add screenshots only for rendered or pasted-card UI changes.

## Security & Configuration Tips

Never invent image, audio, mask, or linked-card IDs. Preserve `${CLAUDE_PLUGIN_ROOT}` references in command files, keep `plugin.json` valid JSON, and do not copy private study notes into examples.
