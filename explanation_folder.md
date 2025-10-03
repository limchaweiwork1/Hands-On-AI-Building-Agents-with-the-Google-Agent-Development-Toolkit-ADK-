# Explanation of Repository Configuration Folders

This document explains the purpose of the configuration files found in the `.devcontainer`, `.github`, and `.vscode` directories. These files are used to set up the development environment, define workflows, and configure the code editor for this project.

---

## `.devcontainer`

This folder contains the configuration for the development container, which allows for a consistent and reproducible development environment using technologies like GitHub Codespaces or VS Code Remote - Containers.

- **`devcontainer.json`**: This is the main configuration file.
    - **`customizations`**: Specifies settings and extensions for the development environment. For example, it pre-installs a list of recommended VS Code extensions (`prettier-vscode`, `linkedinlearning.linkedinlearning-vscode-theme`, etc.) to ensure a consistent coding experience for all contributors.
    - **`onCreateCommand` / `postAttachCommand`**: These are shell commands that run at different points in the container's lifecycle. They are used here to customize the terminal prompt and ensure the local git repository is up-to-date.

---

## `.github`

This folder contains configurations related to the project's management on GitHub, including issue templates, pull request guidelines, and automated workflows.

- **`CODEOWNERS`**: A file that defines individuals or teams that are responsible for the code in the repository. It's used to automatically request reviews on pull requests.
- **`ISSUE_TEMPLATE.md`**: Provides a template that users see when they create a new issue. It encourages them to provide structured and detailed information, such as steps to reproduce, expected behavior, and environment details.
- **`PULL_REQUEST_TEMPLATE.md`**: Provides a template for pull requests. In this repository, it clearly states that pull requests are not accepted, directing contributors to the `CONTRIBUTING.md` file for more information.
- **`workflows/main.yml`**: This file defines a GitHub Actions workflow. The "Copy To Branches" workflow in this file is designed to automatically copy content from the `main` branch to other branches, likely used to manage the different stages of the course content.

---

## `.vscode`

This folder contains workspace-specific settings for the Visual Studio Code editor, ensuring a consistent coding style and environment for anyone who clones the repository.

- **`settings.json`**: This file overrides default VS Code user settings with project-specific configurations. It defines settings such as:
    - Editor appearance (font size, theme, bracket colorization).
    - Formatting rules (format on save, tab size).
    - Behavior of extensions like Live Server and Prettier.