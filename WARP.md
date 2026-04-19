# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## What this repo is
This repository is a **skill repo** implemented entirely as Markdown.

The runtime artifact for this repo lives at `hci-humanizer/SKILL.md`: Claude Code reads the YAML frontmatter (metadata + allowed tools) and the prompt/instructions that follow.

`README.md` is for humans: installation, usage, and a compact overview of the patterns.

## Key files (and how they relate)
- `hci-humanizer/SKILL.md`
  - The actual skill definition.
  - Starts with YAML frontmatter (`---` … `---`) containing `name`, `version`, `description`, and `allowed-tools`.
  - After the frontmatter is the editor prompt: the canonical, detailed pattern list with examples.
- `hci-humanizer/samples/`
  - Voice and glossary files loaded by the skill via paths relative to `hci-humanizer/SKILL.md`.
- `README.md`
  - Installation and usage instructions.
  - Contains a summarized “25 patterns” table and a short version history.

When changing behavior/content, treat `hci-humanizer/SKILL.md` as the source of truth, and update `README.md` to stay consistent.

## Common commands
### Install the skill into Claude Code
Recommended (copy the packaged skill directory):
```bash
mkdir -p ~/.claude/skills
cp -r hci-humanizer ~/.claude/skills/
```

If you need to clone the repo first:
```bash
git clone https://github.com/sarkrui/CCSwitchSkills.git
mkdir -p ~/.claude/skills
cp -r CCSwitchSkills/hci-humanizer ~/.claude/skills/
```

## How to “run” it (Claude Code)
Invoke the skill:
- `/hci-humanizer` then paste text

## Making changes safely
### Versioning (keep in sync)
- `hci-humanizer/SKILL.md` has a `version:` field in its YAML frontmatter.
- `README.md` has a “Version History” section.

If you bump the version, update both.

### Editing `hci-humanizer/SKILL.md`
- Preserve valid YAML frontmatter formatting and indentation.
- Keep the pattern numbering stable unless you’re intentionally re-numbering (since the README table and examples reference the same numbering).

### Documenting non-obvious fixes
If you change the prompt to handle a tricky failure mode (e.g., a repeated mis-edit or an unexpected tone shift), add a short note to `README.md`’s version history describing what was fixed and why.
