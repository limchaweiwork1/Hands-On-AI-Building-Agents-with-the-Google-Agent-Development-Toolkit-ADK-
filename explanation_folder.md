# Explanation of Repository Configuration Folders

This document explains the purpose of the configuration files found in the `.devcontainer`, `.github`, and `.vscode` directories. These files are used to set up the development environment, define workflows, and configure the code editor for this project.

---

## `.devcontainer`

This folder contains the configuration for the development container, which allows for a consistent and reproducible development environment using technologies like GitHub Codespaces or VS Code Remote - Containers.

- **`devcontainer.json`**: This is the main configuration file.
    - **`customizations`**: Specifies settings and extensions for the development environment. For example, it pre-installs a list of recommended VS Code extensions (`prettier-vscode`, `linkedinlearning.linkedinlearning-vscode-theme`, etc.) to ensure a consistent coding experience for all contributors.
    - **`onCreateCommand` / `postAttachCommand`**: These are shell commands that run at different points in the container's lifecycle. They are used here to customize the terminal prompt and ensure the local git repository is up-to-date.
    - **Relationship to Notebooks**: This file is crucial for the `.ipynb` files as it defines the environment where they are intended to be run. It ensures that any developer working on the notebooks has the necessary VS Code extensions (for Python, Jupyter, etc.) and settings for a seamless experience.

---

## `.github`

This folder contains configurations related to the project's management on GitHub, including issue templates, pull request guidelines, and automated workflows.

- **`CODEOWNERS`**: A file that defines individuals or teams that are responsible for the code in the repository. It's used to automatically request reviews on pull requests.
    - **Relationship to Notebooks**: This file specifies who is responsible for reviewing any changes made to the `.ipynb` files, ensuring quality and consistency.

- **`ISSUE_TEMPLATE.md`**: Provides a template that users see when they create a new issue. It encourages them to provide structured and detailed information, such as steps to reproduce, expected behavior, and environment details.
    - **Relationship to Notebooks**: This template is what a user would fill out if they encounter a bug or have an issue with the code or content within any of the `.ipynb` notebooks.

- **`PULL_REQUEST_TEMPLATE.md`**: Provides a template for pull requests. In this repository, it clearly states that pull requests are not accepted, directing contributors to the `CONTRIBUTING.md` file for more information.
    - **Relationship to Notebooks**: This file defines the contribution policy regarding changes to the notebooks, making it clear that direct pull requests to modify them will not be accepted.

- **`workflows/main.yml`**: This file defines a GitHub Actions workflow. The "Copy To Branches" workflow in this file is designed to automatically copy content from the `main` branch to other branches, likely used to manage the different stages of the course content.
    - **Relationship to Notebooks**: This workflow automates the distribution of the `.ipynb` files from the main branch to other branches, which might represent different states of the course (e.g., a starting state and a solution state).

---

## `.vscode`

This folder contains workspace-specific settings for the Visual Studio Code editor, ensuring a consistent coding style and environment for anyone who clones the repository.

- **`settings.json`**: This file overrides default VS Code user settings with project-specific configurations. It defines settings such as:
    - Editor appearance (font size, theme, bracket colorization).
    - Formatting rules (format on save, tab size).
    - Behavior of extensions like Live Server and Prettier.
    - **Relationship to Notebooks**: These settings ensure that when any of the `.ipynb` notebooks are edited in VS Code, the developer has a consistent and standardized coding environment, from the visual theme to automatic code formatting. This helps maintain a uniform style across all files.