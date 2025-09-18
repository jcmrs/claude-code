# Claude Code / Anthropic Project Structure — Comprehensive Synthesis & Evaluation

---

## 1. Introduction

This synthesis merges findings from:
- The Perplexity AI research report (detailed, source-rich, with community and official input)
- Copilot's own independent research using GitHub repositories, Anthropic documentation, and best-practice guides

The goal: deliver a robust, direct, and actionable guide for structuring local Claude Code, Anthropic, and prompt-engineering projects, focused on clarity, maintainability, and workflow automation.

---

## 2. Perplexity AI Research Report: Key Takeaways

**A. Project Structure Patterns**
- Modular, root-level documentation (`CLAUDE.md`, `README.md`)
- Segregated folders for:
    - `src/` (source code)
    - `prompts/` (prompt files, variants, history)
    - `logs/` (outputs, transcripts, by date/task)
    - `configs/` (YAML, TOML, JSON, .env configs)
    - `scripts/` (automation, local utilities)
    - `.github/workflows/` (CI/CD, automation)
    - `tests/` (unit/integration tests)
    - `.claude/commands/` (custom commands)
    - `docs/` (extended documentation, diagrams, ADRs)
    - `knowledge_base/` (optional: project-specific background, decisions)
- Session/task isolation via branches, worktrees, or subfolders
- Prompt & config versioning (`.prompt_versions/` or similar)
- Polyglot support: language-specific subfolders (`src/python/`, etc.)

**B. Documentation & Prompt Management**
- Maintain up-to-date `CLAUDE.md` for Claude's context
- Document prompt conventions, versioning, session etiquette, and protocols
- Use annotated, version-controlled prompts and configs

**C. Automation & Environment**
- Use `.github/workflows/` for CI/CD or Claude workflows
- Scripts for setup, testing, prompt evaluation, and environment management (tools like Rye, Team-GPT, Activepieces, MCP)
- Keep logs, test outputs, and experimental files clearly separated

---

## 3. Copilot’s Independent Findings

- Confirms nearly all Perplexity conclusions, with additional emphasis on:
    - Minimal root clutter: keep only top-level folders and vital files at the root
    - Clear separation between Claude/Anthropic-specific assets and generic project code
    - Per-task/session isolation recommended for heavy parallel or research workflows
    - **No evidence for profile/role-based multi-folder segregation** in public best-practice sources (Perplexity agrees)
    - Living documentation: `CLAUDE.md` and project docs should evolve with workflow

---

## 4. Synthesis: Unified Best Practice Template

### Folder Structure (Tree)

```
claude-project-root/
│
├── CLAUDE.md              # Claude/Anthropic context, etiquette, onboarding
├── README.md              # Human-facing project intro
├── LICENSE
├── .gitignore
├── .github/
│   └── workflows/         # CI/CD, automation
├── src/                   # Primary source code (language folders as needed)
├── prompts/               # Prompt templates, variants, histories
├── logs/                  # Session logs, outputs (by date/task)
├── configs/               # Config files (YAML, TOML, .env)
├── scripts/               # Helper/setup/testing scripts
├── tests/                 # Unit/integration tests
├── docs/                  # Deep documentation, diagrams, ADRs
├── knowledge_base/        # (Optional) Roadmap, decisions, references
├── .claude/commands/      # (Optional) Custom Claude commands
├── .prompt_versions/      # (Optional) Prompt/config version control
└── tasks/                 # (Optional) Per-session/task isolation
```

### Key Practices

- **Documentation:** Maintain `CLAUDE.md` and `README.md`, update with workflow/evolution.
- **Isolation:** Use `tasks/` or branches/worktrees for parallel sessions.
- **Versioning:** Track prompts/configs for rollback and A/B testing.
- **Automation:** Keep scripts and CI/CD logic modular and in their own folders.
- **Logs:** Organize by date/task, prune as needed.
- **No profile/role segregation:** Structure is function- and workflow-centric, not persona-based.
- **Adapt for polyglot:** Use language-specific subfolders if needed.
- **Maintainability:** Regularly review and update docs, configs, and folder structure as project evolves.

---

## 5. Evaluation

- **Alignment:** Perplexity and Copilot’s findings are highly aligned.
- **Comprehensiveness:** Both sources cover not only structure but also documentation, automation, and versioning best practices.
- **Community Validation:** Patterns are backed by official Anthropic docs, top GitHub repos, and community guides.
- **No superfluous complexity:** The synthesized template avoids unnecessary depth, sticking to evidence-based, widely adopted conventions.

---

## 6. Final Recommendations

- Adopt the unified folder structure template above for all Claude Code, Anthropic, and prompt-engineering projects.
- Maintain living documentation (`CLAUDE.md`) as workflows evolve.
- Use session/task isolation for heavy parallel or research workflows.
- Leverage automation and versioning processes as standard, not optional.
- Periodically audit and prune folders/logs/configs for clarity and maintainability.
- Keep structure flexible: adapt as project scope, team, or stack changes.

---

## 7. References

- Anthropic Claude Code Best Practices: https://www.anthropic.com/engineering/claude-code-best-practices
- Awesome Claude Code: https://github.com/hesreallyhim/awesome-claude-code
- Perplexity AI Research Synthesis (thread above)
- AIXplore: https://publish.obsidian.md/aixplore/AI+Development+%26+Agents/claude-code-best-practices
- AIBase: https://www.aibase.com/news/17387
- Next.js Claude Best Practices: https://github.com/romualdtats/claude-code-best-practices

---

_This synthesis is directly actionable for new or existing Claude Code/Anthropic projects, and is designed to remain robust as best practices evolve._