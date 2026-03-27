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


---

## 5. Docker Image Lifecycle

A Docker Image is a read-only template used to create containers.  
The lifecycle of an image involves creating, building, and running containers from it.

### Image Lifecycle Flow

Dockerfile → Build → Image → Run → Container

### Steps Involved

**1. Create Dockerfile**

A Dockerfile contains instructions to build a Docker image.

Example:

```dockerfile
FROM ubuntu:latest
RUN apt update
CMD ["echo", "Hello Docker"]

2. Build Image

Build image from Dockerfile:

docker build -t myimage .

3. Run Container

Run container from image:

docker run myimage
6. Docker Container Lifecycle

A Docker container passes through several stages during its lifecycle.

Container Lifecycle Flow

Create → Start → Run → Pause → Stop → Remove

Lifecycle Commands

Create a container:

docker create nginx

Start container:

docker start nginx

Pause container:

docker pause nginx

Stop container:

docker stop nginx

Remove container:

docker rm nginx
7. Docker Networking Basics

Docker provides networking support to allow containers to communicate with each other and external systems.

Types of Docker Networks

Bridge Network

Default network type
Used for container-to-container communication
docker network ls

Host Network

Uses host machine network directly
No network isolation

Example:

docker run --network host nginx

None Network

No networking access
Fully isolated container

Example:

docker run --network none nginx
8. Docker Storage & Volumes

Docker volumes are used to store persistent data.

Containers normally lose data when deleted, but volumes preserve data.

Volume Commands

Create volume:

docker volume create myvolume

List volumes:

docker volume ls

Remove volume:

docker volume rm myvolume
Advantages of Volumes
Persistent storage
Data backup support
Share data between containers
Improves performance
9. Docker Basic Workflow

A simple workflow for running a container from Docker Hub.

Workflow Steps

Pull image from Docker Hub:

docker pull nginx

Run container:

docker run -d -p 8080:80 nginx

Check running containers:

docker ps

Access container in browser:

http://localhost:8080
10. Advantages of Containerization

Containerization provides several benefits over traditional deployment methods.

Key Advantages
Lightweight and fast startup
Portable across different systems
Efficient resource utilization
Faster deployment and scaling
Improved application isolation
Simplified dependency management
11. Comparison: Virtual Machines vs Containers
Feature	Virtual Machines	Containers
Virtualization	Hardware-level	OS-level
Startup Time	Slow	Fast
Resource Usage	Heavy	Lightweight
Isolation	Strong	Moderate
Performance	Lower	Higher
OS Requirement	Separate OS	Shared OS
12. Summary of Unit I

In this unit, we learned:

Introduction to Containers
Linux Kernel Features (Namespaces & cgroups)
Docker Architecture
Docker Images & Containers
Docker Networking
Docker Volumes
Container Lifecycle
Virtual Machines vs Containers

This unit builds the foundation for advanced Dockerfile creation and container orchestration in later units.


---


- ✔ Image Lifecycle  
- ✔ Container Lifecycle  
- ✔ Networking  
- ✔ Volumes  
- ✔ Workflow  
- ✔ VM vs Container  
- ✔ Summary  



---


