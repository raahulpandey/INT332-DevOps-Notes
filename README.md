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
