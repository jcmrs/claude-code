# Git Workflow Protocol for Claude Code Projects

This protocol defines how you (and Claude) use Git to manage all aspects of the project.

## 1. Branching & Session Isolation

- For each new prompt experiment or major change, create a new branch:
  ```
  git checkout -b prompt-<feature>-YYYYMMDD
  ```
- Use worktrees for true parallel development if needed.

## 2. Committing Changes

- Write atomic commits: each commit should focus on a single logical change.
- Use commit messages like:
  ```
  prompt: add new summarization experiment
  config: update model temp for test
  refactor: clean up prompt formatting
  ```
- Always commit after successful test or experiment runs.

## 3. Merging & Rollback

- Merge experimental branches only if results are positive.
- Use `git revert` or `git checkout` to roll back prompt/config changes if something fails.

## 4. Automation

- Pushing to `main` triggers workflows in `.github/workflows/` (tests, prompt checks, etc.).
- Keep workflow files up to date as automation evolves.

## 5. Cleanup

- Regularly prune old or merged branches.
- Archive unused logs to keep the repo lean.

---

_Claude, always follow this protocol when making or suggesting changes to project structure, prompts, or configs._