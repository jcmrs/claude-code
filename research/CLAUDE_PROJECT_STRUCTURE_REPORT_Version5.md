# Claude Code Local Project Structure – Synthesis Report & Actionable Template

## 1. Executive Summary

This report synthesizes best practices from:
- Official Anthropic/Claude documentation and blog posts,
- Leading Claude Code public repositories,
- AI/prompt engineering community resources.

The goal is to deliver a robust, modular, and adaptable project structure template for local Claude Code or Anthropic LLM development, supporting clarity, automation, and maintainability.

---

## 2. Key Principles

- **Modularity:** Clearly separate code, prompts, logs, configuration, and documentation.
- **Task/Session Isolation:** Use folders or branches for concurrent/parallel tasks—minimizes clutter and focus drift.
- **Automation-Ready:** Integrate GitHub Actions or scripts via standard `.github` and `/scripts` directories.
- **Polyglot Support:** Structure easily adapts to single-language or multi-language projects.
- **Documentation Clarity:** Project root contains concise onboarding and Claude-specific guides.

---

## 3. Recommended Folder Structure

```
claude-project-root/
│
├── README.md               # Project overview, setup, onboarding
├── CLAUDE.md               # Claude/Anthropic-specific usage and protocols
├── LICENSE                 # Licensing
├── .gitignore
├── .gitmessage             # Commit message template (optional)
├── .github/                # GitHub Actions/workflow automation
│   └── workflows/
│
├── src/                    # Primary source code (or main language directory, e.g., python/, node/, etc.)
│
├── prompts/                # Prompt templates, instructions, few-shot examples, Claude session inputs
│
├── logs/                   # Session logs, outputs, transcripts
│
├── configs/                # Claude, LLM, or tool configuration files (YAML, JSON, TOML, etc.)
│
├── scripts/                # Automation utilities, local workflow scripts
│
├── tasks/                  # (Optional) Isolated subfolders for major, parallel, or archived tasks/sessions
│
└── archive/                # (Optional) Deprecated, experimental, or legacy assets
```

---

## 4. Folder/Asset Descriptions

- **README.md:**  
  Project intro, setup steps, contributor/onboarding info.

- **CLAUDE.md:**  
  Claude-specific workflows, prompt engineering tips, session conventions, automation protocols.

- **.github/workflows/:**  
  CI/CD, deployment, automation for Claude or LLM pipelines.

- **src/:**  
  Main codebase (renameable for single-language repos; use top-level folders for polyglot).

- **prompts/:**  
  All prompt templates, instructions, and input files for Claude or related LLMs.

- **logs/:**  
  Claude session outputs, transcripts, and debugging logs (ensure .gitignore for sensitive or large files).

- **configs/:**  
  Project-level configs (model parameters, session settings, tool configs).

- **scripts/:**  
  Helper scripts—runbook automation, local utilities, data prep.

- **tasks/:**  
  (Optional) Per-task or per-session folders for parallel development, experiments, or isolated workflows.

- **archive/:**  
  (Optional) Deprecated, superseded, or legacy files for historical reference.

---

## 5. Customization by Project Type

- **Single-Language:**  
  Use `src/` as main code directory.
- **Multi-Language:**  
  Create `python/`, `node/`, etc. at root, each with its own `/prompts`, `/logs`, as needed.
- **Research/Prototyping:**  
  Emphasize `/tasks` and `/archive` for fast iteration.

---

## 6. Operational Recommendations

- **Session/Task Isolation:**  
  Use `tasks/` or branches (or Git worktrees) for major, parallel Claude sessions.
- **Documentation:**  
  Keep `CLAUDE.md` up to date with any workflow changes or protocol updates.
- **Automation:**  
  Store reusable scripts in `/scripts` and automate common workflows with `.github/workflows`.

---

## 7. Example Template (Starter Files)

```
claude-project-root/
├── README.md
├── CLAUDE.md
├── LICENSE
├── .gitignore
├── .github/
│   └── workflows/ci.yml
├── src/
├── prompts/
├── logs/
├── configs/
├── scripts/
└── tasks/
```

---

## 8. References

- [Anthropic Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)
- [Claude Code Best Practices (GitHub)](https://github.com/awattar/claude-code-best-practices)
- [AIXplore: Claude Code Practices](https://publish.obsidian.md/aixplore/AI+Development+%26+Agents/claude-code-best-practices)
- [AIBase: Anthropic Guide Summary](https://www.aibase.com/news/17387)

---

## 9. Next Steps

- Fork or clone this template for new Claude Code projects.
- Adapt folder names and structure to match project complexity and language stack.
- Maintain a living CLAUDE.md for all Claude/LLM-specific protocols and workflows.
- Periodically review and update structure as best practices evolve.

---

_This report and template are living documents. Update as your workflow, tools, or community best practices change._