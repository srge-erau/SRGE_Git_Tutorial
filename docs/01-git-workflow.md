# Git and GitHub workflow

[← Tutorial home](../README.md)

**Git** tracks versions on your computer. **GitHub** hosts repositories and provides issues, pull requests, and reviews. A **commit** records changes; a **branch** lets you develop changes independently; a **pull request (PR)** proposes merging one branch into another.

## 1. Create a repository

1. Sign in to GitHub and create a new repository.
2. Select `srge-erau` as owner if your organization permissions allow it. Otherwise, ask a maintainer to create it or provide access.
3. Use a descriptive name, such as `lunar-rover-localization`, and a one-sentence description.
4. Choose the visibility appropriate to the project with your maintainer.
5. Initialize with a README. Select a language-specific `.gitignore` if useful; agree on a license with the project owner before selecting one.
6. Create the repository and copy its HTTPS clone URL.

The examples use `REPLACE_REPO_NAME`. Replace it with your repository name before running commands. They assume the default branch is `main`; substitute the actual default branch if needed.

## 2. Configure Git and clone

Set the identity recorded in commits. Use an email associated with your GitHub account, or its GitHub-provided no-reply address.

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
git clone https://github.com/srge-erau/REPLACE_REPO_NAME.git
cd REPLACE_REPO_NAME
git remote -v
```

The global settings apply to all local repositories. Omit `--global` and run inside a repository to set an identity just for that project. Authenticate through your configured Git credential manager or SSH setup when required; a GitHub account password is not used for Git HTTPS authentication.

## 3. Make a focused change

Start from an up-to-date default branch with a clean working directory. `git status` shows pending changes; commit or otherwise preserve them before switching branches.

```bash
git status
git switch main
git pull --ff-only origin main
git switch -c docs/improve-readme
```

Edit `README.md`, then inspect and commit that file:

```bash
git diff -- README.md
git add README.md
git diff --staged
git commit -m "docs: clarify setup instructions"
git push -u origin docs/improve-readme
```

Stage specific files so unrelated changes do not accidentally enter the commit. Suggested branch prefixes include `docs/`, `feat/`, and `fix/`. Commit messages should explain the change, such as `fix: correct timestamp units`.

## 4. Open and review a pull request

On GitHub, open a PR from your branch to the repository's default branch. Describe the problem, the change, and how you checked it. Include relevant issue numbers and example outputs, then request a reviewer according to the project's process.

Respond to feedback by editing, committing, and pushing to the same branch. Merge once required reviews and checks pass. A draft PR is also useful for discussing work in progress.

## 5. Update after merging

```bash
git switch main
git pull --ff-only origin main
```

Optionally delete the local feature branch with `git branch -d docs/improve-readme`. If Git refuses after a squash merge, leave it until you verify that all work is preserved.

## Handle conflicts

If your branch needs changes from `main`, first commit your work, then run:

```bash
git fetch origin
git merge origin/main
```

If Git reports a conflict, resolve the `<<<<<<<`, `=======`, and `>>>>>>>` sections in each affected file into the intended content. Remove the markers, run relevant checks, stage the resolved files, and commit. Push to update the PR. Use `git merge --abort` to cancel an in-progress merge if you need to reconsider the resolution.

## Practice exercise

In a practice repository, create `docs/first-contribution.md`, describe your research project, and submit it through a feature branch and PR. Ask a teammate to review whether the instructions are clear.

## References

- [GitHub Hello World guide](https://docs.github.com/en/get-started/start-your-journey/hello-world)
- [Git reference](https://git-scm.com/docs)
- [GitHub authentication](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github)
