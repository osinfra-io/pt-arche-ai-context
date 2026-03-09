# Platform Team: Arche AI Context

Arche team-level Copilot instructions for the [osinfra-io](https://github.com/osinfra-io) platform teams workspace.

## Overview

This repository is the **arche team level** of a three-level GitHub Copilot instruction hierarchy. Instructions here apply to all `pt-arche-*` repositories.

```none
Platform   pt-ai-context                   ← universal conventions for all pt-* repos
  └── Team   pt-arche-ai-context           ← this repo (applies to all pt-arche-* repos)
        └── Repo   .github/copilot-instructions.md   ← in every repo (repo-specific only)
```

## Setup

`COPILOT_CUSTOM_INSTRUCTIONS_DIRS` tells the GitHub Copilot CLI which directories to load custom instructions from at startup. Always include `pt-ai-context` (platform-level) alongside this repo (team-level).

```bash
# ~/.zshrc
export COPILOT_CUSTOM_INSTRUCTIONS_DIRS="\
$HOME/repositories/osinfra-io/platform-teams/pt-ai-context,\
$HOME/repositories/osinfra-io/platform-teams/arche/pt-arche-ai-context"
```

After editing your shell profile, reload it with `source ~/.zshrc`. See the `pt-ai-context` repo for multi-team setup and full path reference.
