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

**Sub-module structure** — functional sub-modules live in subdirectories (e.g. `regional/`, `dns/`, `nat/`). Each subdirectory has its own `helpers.tofu` invoking `pt-arche-core-helpers//child`.

**Module tests** — tests live in `tests/*.tftest.hcl` and run via `tofu test` in the `test.yml` GitHub Actions workflow on pull requests. Tests use mocked providers — no real infrastructure or credentials needed.

## Creating Releases

Tags follow [Semantic Versioning](https://semver.org/): `MAJOR.MINOR.PATCH` — increment MAJOR for breaking changes, MINOR for backwards-compatible additions, PATCH for backwards-compatible fixes.

To release a new version, simply push a new tag to the repository. The tag should be in the format `vX.Y.Z` where `X`, `Y`, and `Z` are integers.

```none
git tag vX.Y.Z
git push origin vX.Y.Z
```
