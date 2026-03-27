# 📘 INT332: DevOps, Virtualization and Configuration Management

## 🧱 Unit I: Basics of DevOps Infrastructure

---

# 1️⃣ Conceptual Overview

| Concept                  | Description                                                            | Key Benefit              |
| ------------------------ | ---------------------------------------------------------------------- | ------------------------ |
| **Origin of Containers** | Solves the **"Matrix of Hell"** (incompatibility between apps and OS). | Environment Consistency  |
| **Evolution**            | Bare Metal → Virtual Machines → Containers                             | Efficiency & Portability |
| **Virtualization**       | OS-level virtualization using **Docker Engine**                        | Low resource overhead    |

---

# 2️⃣ Core Linux Kernel Mechanisms (Isolation Engine)

| Mechanism      | Type      | Responsibility                                               |
| -------------- | --------- | ------------------------------------------------------------ |
| **Namespaces** | Isolation | Separates resources like Network, Processes, and Filesystems |

### Namespace Types

| Namespace         | Responsibility                                           |
| ----------------- | -------------------------------------------------------- |
| **MNT Namespace** | Provides a private mount point / filesystem              |
| **PID Namespace** | Isolates process IDs; container can't see host processes |
| **NET Namespace** | Provides a private network stack (IP, Routing, Ports)    |

### Resource Management

| Mechanism   | Responsibility                                       |
| ----------- | ---------------------------------------------------- |
| **cgroups** | Limits CPU, Memory, and Disk I/O usage per container |

---

# 3️⃣ Docker Architecture & Objects

| Component            | Function                                                 |
| -------------------- | -------------------------------------------------------- |
| **Docker Client**    | CLI tool where user enters commands (e.g., `docker run`) |
| **Docker Daemon**    | Background service (`dockerd`) that manages containers   |
| **Docker Registry**  | Central library for images (Docker Hub, GHCR)            |
| **Docker Image**     | Read-only template with application code and libraries   |
| **Docker Container** | Runnable instance of an image with a writable layer      |

---

# 4️⃣ Filesystem & Layering

| Feature           | Technical Detail                                             |
| ----------------- | ------------------------------------------------------------ |
| **UnionFS**       | Combines multiple layers into a single cohesive filesystem   |
| **Layering**      | Each instruction in Dockerfile creates a new read-only layer |
| **Copy-on-Write** | Files copied to writable layer only when modified            |
| **Storage**       | Uses Volumes and Bind Mounts for data persistence            |

---

# 5️⃣ Practical Command Reference

```bash
docker version        # Check Docker Client & Server info
docker pull <image>   # Download image from Docker Hub
docker run -it <image> # Run container in interactive mode
docker ps -a          # List all containers
docker images         # List all images
docker inspect <id>   # View detailed metadata
docker rm <id>        # Remove container
docker rmi <id>       # Remove image
```

---

# 📌 Learning Flow

```text
Bare Metal
     ↓
Virtual Machines
     ↓
Containers
     ↓
Docker
```

---

# 🚀 Key Advantages of Containers

* Lightweight and fast
* Portable across systems
* Efficient resource usage
* Better scalability
* Faster deployment

---
---

# 📌 Advanced Docker Concepts (Quick Reference Table)

| Section | Topic | Description | Example Command / Flow |
|--------|------|-------------|------------------------|
| **6️⃣** | Docker Image Lifecycle | Docker image ek template hoti hai jisse containers bante hain. | Dockerfile → Build → Image → Run → Container |
|  | Create Dockerfile | Instructions define karti hain ki image kaise banegi. | `FROM ubuntu:latest`<br>`RUN apt update`<br>`CMD ["echo","Hello Docker"]` |
|  | Build Image | Dockerfile se image create hoti hai. | `docker build -t myimage .` |
|  | Run Container | Image se container start hota hai. | `docker run myimage` |
| **7️⃣** | Docker Container Lifecycle | Container ka lifecycle multiple stages se guzarta hai. | Create → Start → Run → Stop → Remove |
|  | Container Commands | Container lifecycle manage karne ke commands. | `docker create nginx`<br>`docker start nginx`<br>`docker stop nginx`<br>`docker rm nginx` |
| **8️⃣** | Docker Networking Basics | Containers network ke through communicate karte hain. | `docker network ls` |
|  | Bridge Network | Default Docker network. | Container-to-container communication |
|  | Host Network | Host network use karta hai. | Direct host networking |
|  | None Network | Network disabled hota hai. | No connectivity |
| **9️⃣** | Docker Storage Basics | Permanent data storage ke liye volumes use hote hain. | `docker volume create myvolume` |
|  | Volume Commands | Available volumes list karne ke liye. | `docker volume ls` |
|  | Volume Benefits | Data persistent rehta hai even after container deletion. | Backup & Data Safety |
| **🔟** | Basic Docker Workflow | Docker ka simple workflow example. | `docker pull nginx`<br>`docker run -d -p 8080:80 nginx`<br>`docker ps` |
|  | Browser Access | Running container ko browser me access karna. | `http://localhost:8080` |
| **🧪** | Practical Commands | Common commands jo daily use hote hain. | `docker version`<br>`docker images`<br>`docker ps`<br>`docker network ls`<br>`docker volume ls` |

---

# 📌 Practical Output Section



```bash
docker version
docker images
docker ps
docker network ls
docker volume ls