# Solo Developer & Claude Code Onboarding

Welcome! This project uses **Git** as the foundational tool for all version control, session management, and automation.  
Claude is expected to learn and follow these best practices.

## Key Practices

- All work (code, prompts, configs) is tracked in Git.
- Each major experiment, session, or feature starts on its own Git branch or worktree.
- Prompt and config changes are committed with clear, descriptive messages.
- Automation (tests, deployments, prompt checks) runs via `.github/workflows/`.
- All conventions and protocols are documented here and in `protocols/`.

## Folder Structure

- `src/` — main code
- `prompts/` — all prompt files (versioned)
- `logs/` — outputs, transcripts (can be large; regularly pruned)
- `configs/` — config files (YAML, TOML, .env etc.)
- `scripts/` — helper scripts and utilities
- `.github/workflows/` — automation

## Git Tips

- Use `git branch` for every new experiment/session.
- Use `git commit -m "<prompt name>: <what changed>"` for prompt/config edits.
- For major changes, merge or rebase cleanly to main.
- Use `git tag` for important milestones (e.g., working prompt versions).

_Claude, always reference this doc before workflow or structure changes!_