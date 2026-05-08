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

![CLI](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-2(4).png?raw=true)

![CLI-2](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-2(5).png?raw=true)

![Port](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-2(3).png?raw=true)

---

## 3. Dockerize a Simple Application

### 1. Task Objective
The goal of this task was to learn Dockerfile basics, containerize a simple Node.js API application, build the Docker image, run it as a container locally, and verify successful deployment via the browser.

### 2. Writing the Dockerfile
To containerize the application, a `Dockerfile` was created at the root of the project. A lightweight base image, `node:18-alpine`, was selected. The file sets the working directory to `/app`, copies the `package.json` file, and runs `npm install` to install dependencies. Afterwards, the remaining application files (`index.js`) were copied into the container. The `Dockerfile` exposes port 3000 and defines the startup command using `CMD ["npm", "start"]`. 

### 3. Building the Docker Image and Understanding Layers
The Docker image was built using the command `docker build -t my-simple-app .`. During the build process, the concept of image layers became evident. Each instruction in the `Dockerfile` (like `FROM`, `WORKDIR`, `COPY`, and `RUN`) created a discrete, read-only layer. By copying `package.json` and running `npm install` *before* copying the rest of the application code, Docker caches the dependency layer. This optimization ensures that subsequent builds are significantly faster if only the application code changes.

### 4. Running the Container and Port Mapping
The container was executed in detached mode using `docker run -d -p 8080:3000 --name running-app my-simple-app`. A crucial part of this step was mapping the ports. The `-p 8080:3000` flag mapped port 8080 on the host machine to port 3000 inside the isolated container, establishing a bridge for external traffic to reach the application.

### 5. Verification
The deployment was verified by navigating to `http://localhost:8080` in a web browser, successfully displaying the starter code's API response: "Task 3 Complete! Hello from Docker inside my container!". The application is fully containerized and operational.

