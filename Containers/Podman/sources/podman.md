---
created: 2025-09-02T23:29
updated: 2025-09-02T23:45
---
I have dreams of working in DevOps one day. And as a consultant. And Information Systems. And networking. 

Suffice it to say that I want to know and do it all, so I practice and read and build and try again until I learn something new or finally move on to the next. 

I'll probably never master a coding language, though I do have languages which I prefer based on software I've used for one reason or another. Python, Zig, Rust, Go, Ruby, HTML, CSS, and the many iterations of Javascript and Node that are available to us. 

Truth be told, and for reasons still unknown to me, I enjoy working with containers and virtual machines the most. By containers I mean anything but Docker and by virtual machines I mean Linux distro after distro after distro. If I had to guess, my passion for containerization stems from the challenge of learning whatever system is in use, which crossover and work together, and which can fulfill multiple roles across multiple platforms. For the Linux machines, there are simply too many that I want to try. The challenge comes with attempting to install them correctly either bare metal or through an ISO. Maybe it's more about the intricate details of it all as opposed to the actual challenge. 

I now wish to welcome you on my journey of learning Podman Desktop on an M 3 MacBook Pro. Why Podman instead of Colima or K 8 s or Rancher or Docker? The latter two are just to massive in size, K 8 s annoys me to no end at times, and Colima I feel just desperately needs a GUI of some sort. To be fair, I've used Docker the most of them all simply because of it's the easiest to learn. Orbstack is a personal favorite of mine but I want to learn something that's compliant with multiple platforms. 

Enough about me - lets begin! I like to start with compiling a listing of commands to be used for whichever software or service I'm currently learning. Here's what we'll be working with for Podman:

--- 

Common Podman commands grouped by their general functionality:
### Container Management
- `podman run` — Run a command in a new container.
- `podman ps` — List running containers.
- `podman ps -a` — List all containers (running and stopped).
- `podman start` — Start one or more existing containers.
- `podman stop` — Stop one or more running containers.
- `podman restart` — Restart one or more containers.
- `podman rm` — Remove one or more containers.
- `podman kill` — Send a signal to one or more containers, commonly to terminate.
- `podman exec` — Execute a command in a running container.
- `podman logs` — Fetch logs of a container.
- `podman attach` — Attach your terminal to a running container.
- `podman cp` — Copy files/folders between a container and the host.

### Image Management
- `podman pull` — Pull an image from a registry.
- `podman images` — List images in local storage.
- `podman build` — Build an image from a Containerfile/Dockerfile.
- `podman push` — Push an image to a container registry.
- `podman rmi` — Remove one or more images.
- `podman commit` — Create a new image from a container's changes.
- `podman save` — Save an image to a tar archive.
- `podman load` — Load an image from a tar archive.
- `podman search` — Search images on a registry.

### Pod Management (Groups of Containers)
- `podman pod create` — Create a new pod.
- `podman pod ls` — List pods.
- `podman pod ps` — List pods (alias).
- `podman pod start` — Start one or more pods.
- `podman pod stop` — Stop one or more pods.
- `podman pod rm` — Remove one or more pods.
- `podman pod kill` — Kill the main process in containers within a pod.
- `podman pod logs` — Show logs from all containers in a pod.

### Network and Volume
- `podman network ls` — List networks.
- `podman network inspect` — Inspect network configurations.
- `podman volume ls` — List volumes.
- `podman volume create` — Create a new volume.
- `podman volume rm` — Remove volumes.

### System and Miscellaneous
- `podman info` — Display system information.
- `podman system df` — Show disk usage.
- `podman wait` — Wait for container (s) to stop and return exit codes.
- `podman inspect` — Show detailed information about containers, images, pods, volumes, or networks.
- `podman generate kube` — Generate Kubernetes YAML from containers or pods.
- `podman kube play` — Create pods from Kubernetes YAML.

---

