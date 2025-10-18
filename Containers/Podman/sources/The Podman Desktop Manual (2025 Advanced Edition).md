
The Podman Desktop Manual (2025 Edition)

This guide provides a comprehensive walkthrough of Podman and Podman Desktop, designed for developers familiar with virtualization and container concepts.

Table of Contents

1.  Introduction to Podman & Podman Desktop
◦    What is Podman?
◦    What is Podman Desktop?
◦    Key Features
2.  Installation and Setup
◦    macOS
◦    Windows
◦    Linux
◦    Initializing the Podman Machine
3.  Podman Desktop UI Tour
◦    Dashboard & Main UI Components
◦    Managing Containers
◦    Managing Images, Pods, Volumes
4.  Core Workflows with Podman Desktop
◦    Running a Container
◦    Building an Image
◦    Working with Pods
5.  Migrating from Docker
◦    CLI Compatibility
◦    Using Docker Compose
6.  Working with Kubernetes
◦    Managing Local Kubernetes Clusters (Kind, Lima)
◦    Deploying Containers to Kubernetes
7.  Podman CLI Essentials
◦    Docker Command Equivalents
◦    Podman Machine Management
8.  Troubleshooting
◦    Accessing Logs
◦    Common Issues

---


9. Introduction to Podman & Podman Desktop

What is Podman?

Podman is a powerful, daemonless container engine for developing, managing, and running OCI-compliant containers and pods. Unlike Docker, it doesn't require a persistent background daemon, which enhances security and simplifies architecture. On macOS and Windows, Podman utilizes a lightweight Linux VM (the "Podman machine") to run containers.

What is Podman Desktop?

Podman Desktop is a graphical user interface for the Podman engine. It provides an intuitive, visual way to manage containers, images, pods, and even local Kubernetes clusters, serving as a powerful open-source alternative to Docker Desktop.

Key Features

•    Visual Management: Create, run, and manage containers and pods without touching the command line.
•    Kubernetes Integration: Set up and manage local Kubernetes clusters with providers like Kind and Lima.
•    Multi-Platform: Works seamlessly on macOS, Windows, and Linux.
•    Docker Compatibility: Use familiar Docker commands and run your existing Docker Compose files.
•    Extensibility: Add new features and integrations through an extension mechanism.


2. Installation and Setup

macOS

1.  Install Podman CLI (via Homebrew):

2.  Install Podman Desktop:
◦    Download the macOS installer from the official website.
◦    Open the downloaded .dmg or .pkg file and follow the installation prompts.

Windows

1.  Install Podman CLI: Podman Desktop for Windows comes bundled with a Podman installer. When you first launch Podman Desktop, it will prompt you to install Podman if it's not already present.
2.  Install Podman Desktop:
◦    Download the Windows .exe installer from the official website.
◦    Run the installer and follow the setup wizard.

Linux

1.  Install Podman CLI: Use your distribution's package manager (e.g., sudo dnf install podman on Fedora or sudo apt install podman on Debian/Ubuntu).
2.  Install Podman Desktop: The recommended method is via Flatpak to ensure all dependencies are met.

Initializing the Podman Machine

After installing both the CLI and the desktop application, you need to create and start the virtual machine that will run your containers.

1.  From the Command Line:

2.  From Podman Desktop:
◦    Launch Podman Desktop.
◦    The UI will indicate that the machine is not running. Click the "Create" or "Start" button to initialize and start it for you.

3. Podman Desktop UI Tour

Dashboard & Main UI Components

The main interface gives you a complete overview of your container environment.

•    Left Sidebar: Navigate between major sections: Containers, Pods, Images, Volumes, and Settings.
•    Status Bar (Bottom): See the status of the Podman machine and any connected Kubernetes clusters.
•    Main Pane: Displays the content for the currently selected section.

Managing Containers

In the Containers view, you can:
•    View Logs: Select a container and click the Logs tab.
•    Inspect: The Inspect tab shows detailed information about the container's configuration and state.
•    Terminal Access: The Terminal tab provides a shell session directly inside the running container.
•    Start/Stop/Delete: Use the buttons next to each container for quick actions.

Managing Images, Pods, Volumes

•    Images: Pull images from remote registries, build new images from a Dockerfile, and push images to a registry.
•    Pods: Group and manage related containers together as a single unit (a core concept from Kubernetes).
•    Volumes: Create and manage persistent data volumes for your containers.

4. Core Workflows with Podman Desktop

Running a Container

1.  Navigate to the Containers section.
2.  Click the Play kube button. This lets you run a pod from a Kubernetes YAML file. For simpler container runs, it is often easier to use the command line.

Building an Image

1.  Go to the Images section.
2.  Click Build Image.
3.  Point the builder to your Dockerfile path and provide a name for the new image.
4.  Click Build. Podman Desktop will stream the build logs to the UI.

Working with Pods

Create a pod to run multiple containers together:
1.  Go to the Pods section.
2.  Click Create Pod.
3.  Define the pod's name and port mappings. The containers within the pod can now communicate with each other over localhost.

4. Migrating from Docker

CLI Compatibility

For most commands, you can simply use podman as a drop-in replacement for docker.

| Docker Command | Podman Equivalent | Description |
| :--- | :--- | :--- |
| docker run | podman run | Run a container |
| docker ps | podman ps | List running containers |
| docker build | podman build | Build an image from a Dockerfile |
| docker pull | podman pull | Pull a container image |
| docker stop | podman stop | Stop a running container |

Using Docker Compose

Podman Desktop includes built-in support for Compose. Navigate to the Compose section in the UI to bring up your docker-compose.yml or compose.yml files.

6. Working with Kubernetes

Podman Desktop simplifies running containers in a local Kubernetes environment.

Managing Local Kubernetes Clusters

1.  Go to Settings > Kubernetes.
2.  Click Create new.
3.  Choose a provider like Kind or Lima to create a single-node Kubernetes cluster. Podman Desktop will handle the installation and configuration.

Deploying Containers to Kubernetes

Once your Kubernetes cluster is running, you can use the Deploy to Kubernetes action on any container or pod to generate a Kubernetes manifest and apply it to your local cluster.

7. Podman CLI Essentials

While the desktop app is powerful, the CLI remains essential.

Podman Machine Management

•    podman machine init: Creates the Linux VM for containers.
•    podman machine start: Starts the Linux VM.
•    podman machine stop: Stops the VM.
•    podman machine list: Lists all available Podman machines.

8. Troubleshooting

Accessing Logs

If you encounter issues, the first place to look is the logs. In Podman Desktop, go to Settings > Podman > View logs to see detailed logs from the Podman machine and the desktop application itself.

Common Issues

•    Machine Fails to Start: This can be due to networking conflicts or resource constraints. Try running podman machine stop followed by podman machine start. If that fails, podman machine rm -f && podman machine init will recreate the machine from scratch.
•    Cannot Pull Image: Check your network connection and ensure that you can access the registry from your host machine.