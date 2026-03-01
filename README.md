<div align="center">

# bash-repo-template

**Shared boilerplate for Bash script projects**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

</div>

CI, linting, release automation, and project scaffolding extracted from [chawan](https://github.com/wasabi0522/chawan), [yunomi](https://github.com/wasabi0522/yunomi), and [obon](https://github.com/wasabi0522/obon).

## Included Files

| File | Description |
|------|-------------|
| [`Makefile`](Makefile) | `test` / `lint` / `fmt` / `coverage` / `setup` targets. Change `BASH_FILES` at the top to match your project |
| [`.github/workflows/ci.yml`](.github/workflows/ci.yml) | 3-job CI: **lint** (ShellCheck + shfmt with cache), **test** (bats-core with bats-support/assert), **coverage** (bashcov + GitHub Step Summary) |
| [`.github/workflows/tagpr.yml`](.github/workflows/tagpr.yml) | Automated release PR via [tagpr](https://github.com/Songmu/tagpr) |
| [`.github/dependabot.yml`](.github/dependabot.yml) | Weekly GitHub Actions version updates |
| [`.github/release.yml`](.github/release.yml) | Exclude tagpr label from auto-generated release notes |
| [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) | PR template with Why / What / checklist |
| [`.gitignore`](.gitignore) | `coverage/`, `tests/libs/`, editor swap files |
| [`.tagpr`](.tagpr) | tagpr config (`vPrefix=true`, `releaseBranch=main`) |
| [`LICENSE`](LICENSE) | MIT License |

## Usage

1. Copy the files into your new repository
2. Edit `Makefile` — change the first line to match your project:
   ```makefile
   BASH_FILES := scripts/*.sh your-project.tmux
   ```
3. If your project doesn't use bashcov, remove the `coverage` target from `Makefile` and the `coverage` job from `.github/workflows/ci.yml`

## Pinned Versions

All GitHub Actions are pinned to commit SHAs for reproducibility.

| Tool | Version | Pinned in |
|------|---------|-----------|
| `actions/checkout` | v6.0.2 | `ci.yml`, `tagpr.yml` |
| `actions/cache` | v5.0.3 | `ci.yml` |
| `mfinelli/setup-shfmt` | v4.0.1 | `ci.yml` |
| `bats-core/bats-action` | 4.0.0 | `ci.yml` |
| `Songmu/tagpr` | v1.17.1 | `tagpr.yml` |
| ShellCheck | 0.11.0 | `ci.yml` (`SHELLCHECK_VERSION` env) |
| shfmt | 3.12.0 | `ci.yml` (`shfmt-version` input) |
| bashcov | 3.3.0 | `ci.yml` (`gem install` arg) |

## License

[MIT](LICENSE)
