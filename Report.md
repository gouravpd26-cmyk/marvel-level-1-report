## 1. Working with Git and GitHub Basics

### Task Overview
Successfully completed the foundational Git and GitHub task. This task provided practical, hands-on experience in version control, managing distributed repositories, and executing standard collaborative workflows.

### Key Implementations
* **Version Control:** Cloned repositories, created isolated feature branches, and managed staging environments.
* **Advanced Git Operations:** Successfully resolved upstream commit history mismatches utilizing `git fetch`, `git reset --mixed`, and force pushing to align local branches with the main repository.
* **Open Source Contribution:** Actively claimed and resolved an open issue (Issue #3) on the `consilium` repository.

![Docker file](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-1(1).png?raw=true)

### Contribution Details
* **Infrastructure as Code:** Built a `Dockerfile` for a Python FastAPI server and configured a `docker-compose.yml` to orchestrate the API alongside an Ollama LLM container.
* **Documentation:** Updated the project's `README.md` with clear, containerized deployment instructions.
* **Outcome:** Successfully submitted a Pull Request (PR) to the upstream repository.

![Git commands](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-1(2).png?raw=true)

![Pull request](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-1(3).png?raw=true)

---
## 2. Exploring Docker Fundamentals

### Objective
---
Successfully completed the task on Docker fundamentals, establishing a solid understanding of containerized environments crucial for cloud architecture and secure deployments.

### Containers vs. Virtual Machines
---
The primary theoretical outcome involved differentiating between legacy and modern infrastructure paradigms:
* **Virtual Machines (VMs):** VMs operate on top of a hypervisor and require a complete, isolated Guest Operating System for every single application. This architecture makes them heavily resource-intensive, consuming substantial memory and resulting in slower boot times.
* **Containers:** Containers bypass the need for a Guest OS by directly sharing the host machine's operating system kernel. This modern approach renders them exceptionally lightweight, highly portable, and capable of booting in milliseconds, ensuring consistent performance from development to production.

### Docker CLI & Lifecycle Management
---
Practical execution involved utilizing the Docker CLI to manage an `nginx` web server through its complete lifecycle:
* **Image Retrieval:** Executed `docker pull nginx` to securely fetch the standalone, executable software blueprint from the Docker Hub registry.
* **Deployment & Execution:** Utilized `docker run -d -p 8080:80 --name my_web_server nginx` to initialize the container in detached mode, actively mapping local machine ports to expose the web service.
* **Inspection & Monitoring:** Employed `docker ps` to inspect active container states, verifying uptime and port configurations. Used `docker logs my_web_server` to monitor internal HTTP traffic and verify process health.
* **Lifecycle Teardown:** Maintained local system hygiene by executing `docker stop` to gracefully halt the running process, followed immediately by `docker rm` to permanently delete the container instance.

