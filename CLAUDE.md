# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repository contains a collection of composite run steps GitHub Actions. Each directory contains actions for setting up specific development environments.

## Development Commands

### Testing
```bash
npm run test:renovate  # Validate Renovate configuration
```

### Dependencies
```bash
npm install  # Install dependencies
```

## Architecture

### Action Structure
- Each action is organized in its own directory (e.g., `setup-go/`, `setup-node/`)
- Each directory contains an `action.yml` file defining the action
- Implemented as composite actions that bundle multiple steps into a single action

### Key Actions
- `setup-go/`: Go development environment setup (includes mage, goreleaser)
- `setup-node/`: Node.js development environment setup (npm, yarn, pnpm cache support)
- `setup-python/`: Python development environment setup (includes pipenv)
- `setup-rust/`: Rust development environment setup (with caching)
- `setup-docker/`: Docker environment setup (compose v2, buildx)
- `create-release-npm/`: GitHub release creation for npm packages

### Configuration Files
- `renovate.json`: Automated dependency updates (timezone: Asia/Tokyo)
- `.github/workflows/`: Reusable workflows (hadolint, actionlint, merger)
- `package.json`: Node.js dependencies for renovate config validation

### Versioning
- Uses semantic versioning (e.g., v0.21.1)
- GitHub Actions are SHA-pinned with hash comments
- README sample code is also updated by Renovate