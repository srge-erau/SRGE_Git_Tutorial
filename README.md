<p align="center">
  <a href="https://github.com/srge-erau"><img src="assets/srge-logo.png" alt="SRGE — Space Robotics and Generative Estimation Laboratory" width="180"></a>
</p>

# SRGE Git Tutorial — organize and document research repositories

![Tutorial version](https://img.shields.io/badge/tutorial-v1.0.0-blue)
[![SRGE](https://img.shields.io/badge/GitHub-srge--erau-00599C?logo=github)](https://github.com/srge-erau)
![Format](https://img.shields.io/badge/format-Markdown-lightgrey?logo=markdown)

A practical guide for members of the **Space Robotics and Generative Estimation Laboratory (SRGE)** to create, organize, and maintain GitHub repositories. It includes a Git workflow, research file conventions, and a reusable README template with the SRGE logo and version badges. These are suggested conventions; follow project-specific requirements from your maintainer.

## Highlights

- Create an SRGE repository and clone it locally.
- Organize source code, experiments, configuration, data, and results.
- Choose which file types to track, ignore, or store outside Git.
- Collaborate through branches, commits, and pull requests.
- Copy a README template and configure accurate version badges.
- Record reproducible experiments and release versions.

## Learning path

| Step | Guide | Outcome |
| --- | --- | --- |
| 1 | [Git and GitHub workflow](docs/01-git-workflow.md) | Create a repository and submit a pull request |
| 2 | [Repository organization](docs/02-repository-organization.md) | Give each folder a clear purpose |
| 3 | [File types and data](docs/03-file-types.md) | Decide what belongs in Git |
| 4 | [README, badges, and versions](docs/04-readme-and-versioning.md) | Document and version your project |

## Requirements

- A GitHub account with access to the target SRGE repository. Creating a repository under the organization requires appropriate organization permissions.
- Git installed locally; check with `git --version`.
- A text editor such as VS Code. The examples use a terminal.

## Quick start

```bash
git clone https://github.com/srge-erau/SRGE_Git_Tutorial.git
cd SRGE_Git_Tutorial
```

Start with [the Git workflow](docs/01-git-workflow.md). For an existing project, copy [templates/README-template.md](templates/README-template.md) into its root as `README.md`, and copy `assets/srge-logo.png` into its `assets/` folder. Replace every `REPLACE_*` marker, choose the relevant sections, and verify setup commands on a fresh clone.

The [starter .gitignore](templates/gitignore-template.txt) covers common Python, MATLAB, C++, and research outputs. Review its patterns before copying it into your project as `.gitignore`.

## Project layout

```text
SRGE_Git_Tutorial/
├── README.md
├── VERSION                         # Tutorial documentation version
├── CHANGELOG.md                    # Changes to the tutorial
├── .gitignore
├── assets/
│   ├── srge-logo.png
│   └── README.md                   # Logo source
├── docs/
│   ├── 01-git-workflow.md
│   ├── 02-repository-organization.md
│   ├── 03-file-types.md
│   └── 04-readme-and-versioning.md
└── templates/
    ├── README-template.md
    └── gitignore-template.txt
```

## References

- [SRGE GitHub organization](https://github.com/srge-erau)
- [GitHub repository best practices](https://docs.github.com/en/repositories/creating-and-managing-repositories/best-practices-for-repositories)
- [GitHub Skills: interactive lessons](https://skills.github.com/)

## License

No project license has been selected. The repository owner should add a `LICENSE` file before offering reuse under an explicit license. The SRGE logo is a branding asset; its inclusion does not grant additional branding rights.
