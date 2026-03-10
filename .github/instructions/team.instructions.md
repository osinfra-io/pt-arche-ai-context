---
applyTo: "**/pt-arche-*/**"
---

# Arche Team Instructions

## Child Module Conventions

All arche repos are reusable OpenTofu child modules. Key patterns that differ from root modules:

**Source path** — child modules use the `//child` path suffix:

```hcl
module "helpers" {
  source = "github.com/osinfra-io/pt-arche-core-helpers//child?ref=<commit_sha>"  # v1.2.3
}
```

**File structure** — the same standard file layout applies (main.tofu, variables.tofu, outputs.tofu, locals.tofu, helpers.tofu, providers.tofu, backend.tofu). Each submodule directory (e.g. `regional/`, `dns/`) is also a complete module with its own full file layout.

**Lifecycle rules** — child modules must not declare `prevent_destroy` or other lifecycle rules. Root modules that consume a child module control resource destruction.

**Sub-module structure** — functional sub-modules live in subdirectories (e.g. `regional/`, `dns/`, `nat/`). Each subdirectory has its own `helpers.tofu` invoking `pt-arche-core-helpers//child`.

**Module tests** — tests live in `tests/*.tftest.hcl` and run via `tofu test` in the `test.yml` GitHub Actions workflow on pull requests. Tests use mocked providers — no real infrastructure or credentials needed.

## README Badges

In addition to the Dependabot badge (see platform instructions), all Arche child modules include an OpenTofu Tests badge immediately after the title, before the Dependabot badge:

```markdown
[![OpenTofu Tests](https://img.shields.io/github/actions/workflow/status/osinfra-io/<repo>/test.yml?style=for-the-badge&logo=opentofu&color=FEDA15&label=OpenTofu%20Tests)](https://github.com/osinfra-io/<repo>/actions/workflows/test.yml) [![Dependabot](https://img.shields.io/github/actions/workflow/status/osinfra-io/<repo>/dependabot.yml?style=for-the-badge&logo=github&color=2088FF&label=Dependabot)](https://github.com/osinfra-io/<repo>/actions/workflows/dependabot.yml)
```
