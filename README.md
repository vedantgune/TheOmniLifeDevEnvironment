# TheOmniLifeDevEnvironment

## Overview
The **TheOmniLifeDevEnvironment** repository provides a multi-container development setup using **DevContainers** and **Docker Compose**. This environment enables seamless development for personal nutrition project that require multiple services such as a frontend (Angular), backend (.NET), and automation (Python Django). It can allow developers to work within isolated containers while maintaining efficient workflow and debugging capabilities.

## Features
- **Multi-container setup**: Supports frontend, backend, and automation containers.
- **VS Code DevContainers integration**: Open and work inside individual containers with full VS Code support.
- **Pre-configured environment**: Each container runs predefined commands to streamline development.
- **Flexible repository cloning**: Clone and work on specific repositories inside containers.
- **Shared network and dependencies**: Ensures smooth inter-container communication.
- **Reverse Proxy Setup**: Uses **Caddy** as a reverse proxy to serve applications on `https://pnut.localhost`.

## Prerequisites
Before you begin, ensure you have the following installed:
- [Docker](https://docs.docker.com/get-docker/) (with Docker Compose)
- [Visual Studio Code](https://code.visualstudio.com/)
- [VS Code Remote - Containers Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Directory Structure
```bash
.
├── Caddyfile                 # Configuration for reverse proxy
├── common-compose.yml        # Docker Compose configuration for all containers
├── .devcontainer/            # DevContainer configurations for different environments
│   ├── automation/
│   │   ├── devcontainer.json
│   │   ├── Dockerfile-Automation
│   ├── backend/
│   │   ├── devcontainer.json
│   │   ├── Dockerfile-Backend
│   ├── frontend/
│       ├── devcontainer.json
│       ├── Dockerfile-Frontend
├── .env                      # Environment variables
├── sql_install.sh            # SQL installation script (if needed)
├── .gitignore                # Git ignore file
```
*NOTE:* Make sure to add .env file with proper environment variables, otherwise containers won't start.

## Getting Started
### 1. Clone the Repository

```bash
git clone https://github.com/in/TheOmniLifeDevEnvironment.git
cd TheOmniLifeDevEnvironment
```

### 2. Open in VS Code with Dev Containers

1.  Open **VS Code**.
2.  Select **Open Folder** and choose the `TheOmniLifeDevEnvironment` directory.
3. Install **Dev Containers** VSCode Extension if not installed yet.
4.  Click on the **Remote Explorer** (or Command Palette: `Ctrl+Shift+P` > "Dev Containers: Open Folder in Container").
5.  A pop-up will appear with **three options**:
    -   **Frontend** (Angular container)
    -   **Backend** (.NET container)
    -   **Automation** (Scripts and automation tools container)
6.  Select the container where you want to use as a devcontainer.

### 3. Cloning a Specific Project Inside the Container

Once inside a selected container, the workspace will be empty initially. To start working on a specific project, clone the required repository:

#### Example (Cloning Angular Frontend Repository)

```bash
git clone <github-repo-https-or-ssh-link> .

```
(The `.` at the end ensures cloning into the current directory.)


### 4. Running the Application

Each container is preconfigured to run necessary commands:
(Assuming that container is opened in Frontend(Angular) Dev Environment)
-   **Frontend (Angular)**: Runs development server.
-   **Backend (.NET)**: Runs `dotnet watch run` for hot-reloading.
-   **Automation**: Runs predefined scripts (ex: `python manage.py runserver`).

Once cloned, use appropriate commands to start development:

#### Example (Starting Angular Development Server)

```bash
npm install
npm start
```

#### Example (Starting .NET Backend)

```bash
dotnet watch run
```

#### Example (Starting Python Automation)

```bash
python manage.py runserver 0.0.0.0:8000
```

### 5. Accessing the Application

The reverse proxy is configured to serve the application on:

```
https://pnut.localhost
```

Make sure your `/etc/hosts` file includes `127.0.0.1 pnut.localhost` for local resolution.

## Notes

-   The containers share a **Docker network**, ensuring smooth interaction.
-   Use **VS Code debugging tools** within the selected DevContainer.
-   The `.env` file can be modified to customize environment variables.

## Troubleshooting

-   **DevContainer not opening?** Ensure you have **Docker** and **VS Code Remote Containers extension** installed.
-   **Network issues?** Restart Docker and reopen VS Code.
-   **Containers not starting?** Run `docker-compose up -d` inside the project folder.
