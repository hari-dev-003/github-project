# GitHub Best Practices

## Table of Contents

- [Branching Strategy](#branching-strategy)
  - [The `main` Branch](#the-main-branch)
  - [The `dev` Branch](#the-dev-branch)
  - [Feature Branches](#feature-branches)
- [Pull Requests (PRs)](#pull-requests-prs)
- [Gitignore](#gitignore)
- [Commit Messages](#commit-messages)
- [General Best Practices](#general-best-practices)

## Branching Strategy

We use a branching model based on GitFlow, but simplified for our needs. The primary branches are `main`, `dev`, and feature branches.

### The `main` Branch

- The `main` branch is the most stable branch and represents the production-ready code.
- Direct commits to `main` are strictly forbidden.
- All changes to `main` must come from the `dev` branch through a pull request.
- Each commit on `main` should be a tagged release.

### The `dev` Branch

- The `dev` branch is the primary development branch. It contains the latest development changes and is the integration branch for all feature branches.
- All feature branches are created from the `dev` branch.
- When a feature is complete, it is merged back into `dev` through a pull request.
- The `dev` branch should always be in a state that can be deployed to a staging or testing environment.

### Feature Branches

- Feature branches are used to develop new features or fix bugs.
- They are created from the `dev` branch.
- The naming convention for feature branches is `feature/<feature-name>` (e.g., `feature/user-authentication`) or `fix/<bug-name>` (e.g., `fix/login-button-bug`).
- Once a feature is complete, a pull request is created to merge the feature branch into `dev`.
- Feature branches should be short-lived and focused on a single feature or fix.

## Pull Requests (PRs)

- All changes to the `dev` and `main` branches must be made through a pull request.
- Before creating a PR, ensure your feature branch is up to date with the `dev` branch by rebasing or merging.
- Provide a clear and descriptive title for your PR.
- The PR description should include:
    - A summary of the changes.
    - The "why" behind the changes.
    - A link to the relevant issue, if applicable.
- At least one other developer must review and approve the PR before it can be merged.
- All CI/CD checks must pass before a PR can be merged.

## Gitignore

- The `.gitignore` file is used to specify which files and directories should be ignored by Git.
- This includes:
    - Dependencies (e.g., `node_modules/`, `vendor/`)
    - Build artifacts (e.g., `dist/`, `build/`)
    - Environment variables (e.g., `.env`)
    - IDE and editor files (e.g., `.idea/`, `.vscode/`)
    - Operating system files (e.g., `.DS_Store`, `Thumbs.db`)
- A good `.gitignore` file helps keep the repository clean and prevents unnecessary files from being committed. You can find templates for `.gitignore` files at [github.com/github/gitignore](https://github.com/github/gitignore).

## Commit Messages

- Write clear and concise commit messages.
- Follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification.
- The commit message should be structured as follows:
    ```
    <type>[optional scope]: <description>

    [optional body]

    [optional footer]
    ```
- Example:
    ```
    feat: add user authentication endpoint

    This commit introduces a new endpoint for user authentication.
    It includes the necessary logic for handling user login and registration.

    Fixes #123
    ```

## General Best Practices

- **Keep your local `dev` branch up to date:** Before starting a new feature, pull the latest changes from the remote `dev` branch.
- **Rebase your feature branch:** Before creating a PR, rebase your feature branch on top of the latest `dev` branch to maintain a linear history.
- **Delete merged branches:** After your PR is merged, delete the feature branch to keep the repository clean.
- **Use issues:** Create an issue for any bug or feature request. This helps track work and provides a place for discussion.
- **Code reviews:** Participate in code reviews to ensure code quality and share knowledge.
