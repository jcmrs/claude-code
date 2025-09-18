# CLAUDE.md — Onboarding & Best Practices for Claude Code

---

## 0. Configuration Check (Start Here)

Before proceeding, always check if this project is properly configured and initialized:

- **Is this folder a Git repository?**
  - If NO:  
    1. Run `git init` to initialize version control.
    2. Create and commit `.gitignore`, `README.md`, `CLAUDE.md`, and the recommended folder structure.
    3. (Optional) Link to a remote repository for backup/collaboration:  
       `git remote add origin https://github.com/<user>/<repo>.git`
    4. Reference: [GitHub Getting Started Guide](https://docs.github.com/en/get-started/quickstart/create-a-repo)

- **Are all key folders present?** (`src/`, `prompts/`, `logs/`, `configs/`, etc.)
  - If NO:  
    1. Create missing folders.
    2. Reference: See “Project Folder Structure” section below.

- **Is initial onboarding documentation present?** (`CLAUDE.md`, `ONBOARDING.md`)
  - If NO:  
    1. Create from this template or copy from a known good project.

- **Is Claude Code configured with project-specific context?**
  - If NO:  
    1. Read this file in full.
    2. Confirm all best practices and protocols are loaded into your session.
    3. If using a local MCP or Claude server, ensure it is pointed at this folder and has loaded `CLAUDE.md`.

**If ANY of the above checks fail:**  
- **STOP.**  
- Complete the missing configuration steps before engaging in project work or Claude Code sessions.

**If YES to all:**  
- Proceed with your task as described in this document.

---

## 1. Project Purpose

This project uses Claude Code to automate, develop, and maintain high-quality code, prompts, and workflows.  
You will assist in all aspects of coding, prompt engineering, automation, and documentation.

---

## 2. Core Principles

- **Version Control:**  
  All changes (code, prompts, configs) must be tracked in Git.
- **Modularity:**  
  Keep project organized using dedicated folders for code, prompts, logs, configs, and scripts.
- **Session/Task Isolation:**  
  Use Git branches or worktrees for each new experiment, session, or major task.
- **Documentation:**  
  Keep this file (`CLAUDE.md`) and `README.md` updated with new conventions, protocols, and project decisions.
- **Automation:**  
  Support and maintain `.github/workflows/` for CI/CD and automated checks.
- **Clarity & Reproducibility:**  
  All steps, changes, and decisions must be clear, well-documented, and reproducible.

---

## 3. Project Folder Structure

Follow this layout at all times:

```
project-root/
├── CLAUDE.md              # This file: context, etiquette, protocols
├── README.md              # General project overview
├── .gitignore             # Files/folders to exclude from Git
├── src/                   # All source code
├── prompts/               # Prompt templates, variants, and history
├── logs/                  # Output logs and transcripts
├── configs/               # Configuration files (YAML, TOML, .env)
├── scripts/               # Helper scripts and automation utilities
├── .github/
│   └── workflows/         # CI/CD and automation workflows
├── tests/                 # Unit and integration tests
├── tasks/                 # (Optional) Per-session/task folders
├── .prompt_versions/      # (Optional) Prompt/config versioning
└── knowledge_base/        # (Optional) Decision records, references
```

---

## 4. Git & Workflow Protocols

- **Branching:**  
  For every new task or experiment, create a new Git branch:  
  `git checkout -b <feature-or-session-name>-YYYYMMDD`
- **Committing:**  
  Make frequent, atomic commits with clear, descriptive messages (e.g., `prompt: add summarization v2`).
- **Merging:**  
  Only merge branches when experiments/tests are successful.
- **Rollback:**  
  Use Git to revert changes if needed.
- **Prompt/Config Versioning:**  
  Track all prompt and config changes via Git; use `.prompt_versions/` for snapshots if required.
- **CI/CD:**  
  Pushing to `main` triggers automation defined in `.github/workflows/`.

---

## 5. Prompt & Config Management

- Store all prompt files in `prompts/`, using clear names and dated/numbered variants if experimenting.
- Annotate all prompts with comments describing purpose, expected outcome, and revision history.
- Store all config files in `configs/`, and version-control them.
- Never mix prompts, logs, or configs in the same folder.

---

## 6. Logging & Housekeeping

- Store logs in `logs/`, organized by date or task.
- Prune/clean up logs and unused branches regularly.
- Archive deprecated prompts/configs in `.prompt_versions/` or `archive/`.

---

## 7. Documentation

- Update `CLAUDE.md` with every new convention, protocol, or important decision—this is your persistent memory!
- Keep `README.md` current for human users.
- Add/maintain `ONBOARDING.md` for quick start and context.

---

## 8. Automation

- Use scripts in `scripts/` for setup, testing, or batch jobs.
- CI/CD workflows in `.github/workflows/` should lint, test, and validate code and prompts automatically.

---

## 9. Etiquette & Behavior

- Follow all documented best practices without deviation unless explicitly instructed.
- When in doubt, consult this `CLAUDE.md` or escalate for human clarification.
- Strive for transparency, clarity, and reproducibility in every action and suggestion.

---

## 10. First Steps (Claude Checklist)

1. **Read this file in full before taking any action.**
2. **Clone the repository and confirm the folder structure matches the template above.**
3. **When starting any new experiment, feature, or prompt:**
   - Create a new branch.
   - Document your rationale and process in commits and, if needed, in `CLAUDE.md`.
4. **Always update this file with new protocols, conventions, or lessons learned (see Section 11 for instructions).**

---

## 11. How to Update This File (`CLAUDE.md`)

**Purpose:**  
Keep this file as a living, authoritative record of all project protocols, conventions, and lessons learned.  
Update it promptly after any relevant change, experiment, or insight.

### Where to Add Updates

- **New Protocols or Conventions:**  
  - If it is a new major protocol, create a new numbered section in `CLAUDE.md` (e.g., "12. Experimentation Protocols").
  - For minor changes, add as a sub-point or bullet under the most relevant existing section.

- **Lessons Learned or Retrospectives:**  
  - Add a subsection to the end of the relevant section, titled “Lessons Learned” or “Notes.”
  - Alternatively, maintain a dedicated “Lessons Learned” section at the end of the file (e.g., section 99).

### Structure & Format

- Use clear markdown headings (`##`, `###`, `####`) for sections and subsections.
- Use bullet points or numbered lists for clarity.
- For protocols, always include:
    - **Purpose**
    - **Step-by-step instructions**
    - **Rationale or context** (if applicable)
- For lessons learned, include:
    - **Date**
    - **Description of the event or change**
    - **Action taken or protocol updated**

### Update Method (Step-by-step)

1. **Locate** the most relevant section or decide if a new section is needed.
2. **Edit** the file in your preferred editor or via Claude Code.
3. **Add** the new protocol, change, or lesson using the structure above.
4. **Save** the file, then immediately **commit** the change in Git with a descriptive message, e.g.:
   ```
   docs: update CLAUDE.md with new prompt versioning protocol (section 12)
   ```
5. **Push** to remote if using a remote repository.

### Example Update

```
## 12. Prompt Versioning Protocol (added 2025-09-17)

**Purpose:**  
Ensure all prompt changes are tracked and reversible.

**Protocol:**  
- Every new prompt experiment gets a unique, dated filename in `prompts/`.
- Commits affecting prompts must reference the prompt filename and experiment purpose.
- Archive superseded prompts in `.prompt_versions/`.

**Lessons Learned:**  
- *2025-09-17*: Lost track of prompt effectiveness when not using dated filenames. Now required.
```

---

_Always ensure updates are clear, dated, and well-structured to support future maintainability and ease of onboarding for both humans and Claude._