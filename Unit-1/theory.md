Unit I: Basics of DevOps Infrastructure & Containerization1. Introduction to ContainersOrigin: Traditional deployment faced the "Matrix of Hell" problem due to inconsistent environments across development, testing, and production. Containerization emerged to solve the "Works on my machine" syndrome by packaging code with all its dependencies.Evolution: Transitioned from Physical Servers (Bare Metal) $\rightarrow$ Virtual Machines (Hypervisor-based) $\rightarrow$ Containers (OS-level virtualization).2. Core Linux Kernel Features (The Engine of Isolation)Docker leverages the underlying Linux kernel features to provide isolation and resource management:Namespaces (Isolation Layer):MNT (Mount): Provides an isolated file system for the container.PID (Process ID): Isolates process trees; processes inside a container cannot see processes in the host or other containers.NET (Network): Provides a private network stack, including IP addresses, IP tables, and routing rules.UTS: Allows a container to have its own hostname and domain name.IPC: Isolates Inter-Process Communication resources.Control Groups (cgroups): * Responsible for Resource Limitation. It ensures a container doesn't exceed its allocated CPU, Memory, or Disk I/O, preventing a single container from crashing the entire Host System.3. Docker Architecture (Client-Server)Docker uses a Docker Engine which is a client-server application with three major components:Docker Client: The primary way users interact with Docker. When you run commands like docker run, the client sends these commands to the Docker Daemon.Docker Host (Daemon - dockerd): A background process that manages Docker objects such as images, containers, networks, and volumes. It listens for Docker API requests.Docker Registry: A stateless, highly scalable server-side application that stores and lets you distribute Docker images (e.g., Docker Hub, GitHub Container Registry).4. Docker Objects & FilesystemImages: Read-only templates used to create containers. Built using a layered approach.Containers: A runnable instance of an image. It adds a Thin Writable Layer on top of the read-only image layers using the Union File System (UnionFS).Copy-on-Write (CoW) Strategy: Optimizes disk space and performance by sharing layers between images and only copying files to the writable layer when they are modified.
# Verify Docker Installation
docker version

# Pulling and Running an Image from Docker Hub
docker pull hello-world
docker run hello-world

# Running an Interactive Ubuntu Container
docker run -it ubuntu /bin/bash

# Managing Containers and Images
docker ps -a       # List all containers
docker images      # List all local images
docker inspect <id> # Low-level information of Docker objects
