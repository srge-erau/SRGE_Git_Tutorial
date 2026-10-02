# README, badges, and versions

[← Tutorial home](../README.md)

A README should let a new member understand the project, install dependencies, run a small example, and interpret the output.

## Use the template

1. Copy [README-template.md](../templates/README-template.md) to the project root as `README.md`.
2. Copy [the SRGE logo](../assets/srge-logo.png) to its `assets/srge-logo.png`.
3. Replace every `REPLACE_*` marker with verified information. Remove sections and badges that do not apply.
4. Match the layout to actual files and check setup commands on a fresh clone.
5. Add the chosen license as `LICENSE` and link it once it exists.

The template image path is written for a root README. Its preview inside `templates/` will not resolve the image until copied into place.

## Badges

Use a few badges and describe their values accurately.

| Badge | Image URL | Meaning |
| --- | --- | --- |
| Static version | `https://img.shields.io/badge/version-v1.0.0-blue` | Manually maintained label |
| GitHub release | `https://img.shields.io/github/v/release/srge-erau/REPLACE_REPO_NAME` | Latest published GitHub release |
| Python version | `https://img.shields.io/badge/Python-3.11-blue?logo=python&logoColor=white` | Example runtime; replace with the tested version |
| MATLAB release | `https://img.shields.io/badge/MATLAB-R2025b-orange` | Example release; replace with the tested release |

Use the static badge until a published release exists. The release badge can show an error when there is no release or the repository is inaccessible. A tag alone is not a published GitHub release. Static runtime badges do not verify compatibility: run and document your checks.

Link a release badge to the releases page:

```markdown
[![Latest release](https://img.shields.io/github/v/release/srge-erau/REPLACE_REPO_NAME)](https://github.com/srge-erau/REPLACE_REPO_NAME/releases)
```

Add a CI status badge only after its workflow exists, and a license badge only after the license is selected and present.

## Version numbers

For software with a defined public interface, semantic versions use `MAJOR.MINOR.PATCH`:

- **MAJOR:** a breaking change to the public interface.
- **MINOR:** new functionality that remains compatible.
- **PATCH:** compatible fixes.

Use `0.x.y` during early development when interfaces are still changing. Define compatibility for your project: function signatures, configuration schemas, command-line options, or output formats. Documentation projects can use a stated editorial convention instead.

This tutorial starts at documentation version `1.0.0`, recorded in `VERSION`, its static badge, and `CHANGELOG.md`. No release or tag is implied. Major versions reorganize the learning path, minor versions add guides or templates, and patch versions correct instructions.

## Publish a version

After review, merge release changes, update the authoritative project version and changelog, and test the exact commit to be released. Keep static badges in sync. For a project whose next version is `1.0.0`, a maintainer can run:

```bash
git switch main
git pull --ff-only origin main
git status
git tag -a v1.0.0 -m "Release v1.0.0"
git push origin v1.0.0
```

Use the actual default branch and intended version. Confirm the working directory is clean and the tag is unused before tagging. In GitHub's Releases section, create a release from that tag with changes, setup notes, and known limitations. Do not move an already published tag to a different commit.

## References

- [GitHub README documentation](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes)
- [Shields badges](https://shields.io/)
- [Semantic Versioning](https://semver.org/)
- [Managing GitHub releases](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository)
