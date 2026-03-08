# pt-arche-ai-context

Arche team-level Copilot instructions for the [osinfra-io](https://github.com/osinfra-io) platform teams workspace.

## Overview

This repository is the **arche team level** of a three-level GitHub Copilot instruction hierarchy. Instructions here apply to all `pt-arche-*` repositories.

```none
Platform   pt-ai-context                   ← universal conventions for all pt-* repos
  └── Team   pt-arche-ai-context           ← this repo (applies to all pt-arche-* repos)
        └── Repo   .github/copilot-instructions.md   ← in every repo (repo-specific only)
```

## What's in this repo

`.github/instructions/team.instructions.md` — loaded via `COPILOT_CUSTOM_INSTRUCTIONS_DIRS`. Contains conventions shared across all arche child module repositories:

- Repository overview and child module patterns
- Module structure (root module, sub-modules, `shared/helpers.tofu`)
- GitHub Actions workflows (`test.yml` on PRs, `release.yml` on version tags)
- Release process and semantic versioning

## Setup

Add this repo alongside `pt-ai-context` in your `COPILOT_CUSTOM_INSTRUCTIONS_DIRS`:

```bash
# ~/.zshrc or ~/.bashrc
export COPILOT_CUSTOM_INSTRUCTIONS_DIRS="\
$HOME/repositories/osinfra-io/platform-teams/pt-ai-context,\
$HOME/repositories/osinfra-io/platform-teams/arche/pt-arche-ai-context"
```
