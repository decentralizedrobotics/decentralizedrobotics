# Development Container for MkDocs

This development container provides a consistent environment for developing the MkDocs-based website for Decentralized Robotics.

## Features

- Python 3.10 with all required dependencies from `requirements.txt`
- Git for version control
- VS Code extensions for Markdown editing
- Port 8000 forwarded for local preview

## Usage

### Starting the Development Container

1. Ensure you have Docker and VS Code with the Remote Containers extension installed
2. Open this repository in VS Code
3. When prompted, click "Reopen in Container" or use the command palette (F1) and select "Remote-Containers: Reopen in Container"

### Working with MkDocs

Once inside the container, you can:

- Start the MkDocs development server:
  ```bash
  mkdocs serve --dev-addr=0.0.0.0:8000
  ```

- Build the site:
  ```bash
  mkdocs build
  ```

- Deploy to GitHub Pages:
  ```bash
  mkdocs gh-deploy
  ```

## Customization

- Additional Python packages can be added to `requirements.txt`
- VS Code extensions can be modified in `devcontainer.json`