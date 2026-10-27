# CLAUDE.md

Guidance for Claude Code (claude.ai/code) in this repository. Work as a principal-level engineer with deep expertise in GitHub Actions workflows.

## 📝 CLAUDE.MD EVOLUTION

If the user gives the same correction or instruction in more than one conversation, ask whether to add it to this file.

## 🏗️ PROJECT ARCHITECTURE

### Socket Workflows Repository
This repository (`SocketDev/workflows`) holds GitHub Actions workflows for the SocketDev organization.

### Core Structure
- `.github/workflows/audit-gha-workflows.yml` - runs zizmor (`--min-severity medium`) over `.github/` on pull requests, merge queue, and pushes to `main`/`master`
- `.github/dependabot.yml` - weekly Dependabot updates for GitHub Actions

## ⚡ COMMANDS & SCRIPTS

- **Audit workflows**: `zizmor .github --min-severity medium` (the check `audit-gha-workflows.yml` runs in CI)

## 🔒 WORKFLOW CONVENTIONS

Follow the pattern in `audit-gha-workflows.yml`: a top-level `permissions:` block scoped to the minimum (`contents: read`), third-party actions pinned to a full commit SHA with a `# vX.Y.Z` comment, `persist-credentials: false` on checkout, a `timeout-minutes` on each job, and pinned tool versions. New or changed workflows must pass zizmor at medium severity.

## 🔧 GIT & WORKFLOW

### Git Commit Guidelines
- **🚨 FORBIDDEN**: NEVER add Claude co-authorship or Claude signatures to commits
- **🚨 FORBIDDEN**: Do NOT include "Generated with Claude Code" or similar AI attribution in commit messages
- **Commit messages**: Should be written as if by a human developer, focusing on the what and why of changes
- **Professional commits**: Write clear, concise commit messages that describe the actual changes made
- **Pithy messages**: Keep commit messages concise and to the point - avoid lengthy explanations

### Git Workflow Rules
- **DO NOT commit automatically** - let the user review changes first
- Use `--no-verify` flag only when explicitly requested
- Always provide clear, descriptive commit messages