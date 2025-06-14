---
description: 'Commit changes'
---

# Create a Commit

Please commit your changes using the following steps:

## Steps

1. Check changes
   - Check changed files with `git status`
   - Review changes with `git diff`
2. Staging
   - Stage relevant files with `git add`
   - Stage partially as needed
3. Create a commit
   - Write a commit message following the Conventional Commits specification
   - Include the Claude Code signature in the commit

## Commit Message Convention

Follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) and use the following formats:

- `feat: Add new feature` (Use only if related to Go files)
- `fix: Bug fix` (Use only if related to Go files)
- `test: Add or update tests` (Use only if related to Go files)
- `docs: Update documentation`
- `style: Code formatting`
- `refactor: Refactoring`
- `chore: Other changes`
- `build: Build-related changes`
- `ci: CI/CD changes`

## Commit Template

```
<type>: <description>

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

## Example

```bash
# Check changes
git status
git diff

# Stage files
git add src/main.go
git add docs/README.md

# Create a commit
git commit -m "$(cat <<'EOF'
feat: add new API endpoint

🤖 Generated with [Claude Code](https://claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>
EOF
)"
```

## Notes

- The commit message should concisely describe the changes
- If there are multiple types of changes, use the type that best represents the main change
- Always include the Claude Code signature
- Never commit confidential information
