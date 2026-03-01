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

## Tool Versions

All GitHub Actions are pinned to commit SHAs for reproducibility. Versions at the time of extraction:

| Tool | Version |
|------|---------|
| ShellCheck | 0.10.0 |
| shfmt | latest (via `mfinelli/setup-shfmt`) |
| bats-core | 4.0.0 (via `bats-core/bats-action`) |
| bashcov | 3.3.0 |
| tagpr | 1.17.0 |

## License

[MIT](LICENSE)
