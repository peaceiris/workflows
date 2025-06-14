---
description: 'Create a pull request'
---

# Create Pull Request

Please follow the steps below to create a pull request:

## Steps

1. Check/Create Branch
   - If the current branch is main/master, create a new branch
   - Name the branch to concisely describe the changes
2. Stage and Commit Changes
   - Stage changed files with `git add`
   - Create a commit following the Conventional Commits convention
   - Include the Claude Code signature in the commit
3. Push and Create Pull Request
   - Push the branch to GitHub
   - Create a pull request with `gh pr create`

## PR Template

Use the following template for the pull request body:

```
## Overview

(List a summary of the changes in bullet points)

## References

(List related links)
```

## Commit Message Convention

Follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) and use the following format:

- `feat: add new feature` Only use when related to Go files
- `fix: bug fix` Only use when related to Go files
- `test: add or update tests` Only use when related to Go files
- `docs: documentation update`
- `style: code formatting`
- `refactor: code refactoring`
- `chore: other changes`
- `build: build-related changes`
- `ci: CI/CD changes`

## Example

```bash
# Create a new branch (if on main/master)
git checkout -b feat/add-new-endpoint

# Stage and commit changes
git add .
git commit -m "feat: add new API endpoint"

# Push and create PR
git push -u origin feat/add-new-endpoint
gh pr create --title "feat: add new API endpoint" --body "$(cat <<'EOF'## Overview

- Added a new API endpoint
- Implemented validation

## References

- Issue #123

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>
EOF
)"
```
