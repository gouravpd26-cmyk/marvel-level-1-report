# CL domain

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

![img-1](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-3(1).png?raw=true)

![img-2](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-3(2).png?raw=true)

![img-3](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-3(3).png?raw=true)

---

## Task 5: Kubernetes Basics and Writing Pod Specs  

### 1. Objective Overview
The goal of this task was to understand core Kubernetes concepts, configure a local Minikube environment, write a YAML manifest to deploy an Nginx container, and interact with the cluster using `kubectl` commands.

### 2. Core Concepts Mastered
*   **Cluster:** The overarching system of machines running Kubernetes.
*   **Control Plane:** The management layer that orchestrates the cluster, dictates container placement, and monitors overall health.
*   **Nodes:** The virtual or physical worker machines that execute the workloads.
*   **Pods:** The smallest deployable unit in Kubernetes, acting as an environment wrapper around one or more containers (e.g., an Nginx web server).

### 3. Writing the Pod Specification
Created a declarative manifest file (`nginx-pod.yaml`) to define the desired state of the Pod:
*   **`apiVersion` & `kind`:** Specified that the resource to be created is a `Pod`.
*   **`metadata`:** Assigned the identifiable name `my-first-nginx` and applied organizational labels.
*   **`spec`:** Defined the container configuration, instructing the cluster to pull the official `nginx:latest` image and expose `containerPort: 80`.

### 4. Key Commands Executed
*   `minikube start`: Initialized the local single-node cluster.
*   `kubectl apply -f nginx-pod.yaml`: Deployed the Pod directly into the cluster.
*   `kubectl get pods`: Monitored the real-time status of active Pods.
*   `kubectl describe pod my-first-nginx`: Inspected the Pod's lifecycle events, image pulling status, and internal configuration details.
*   `kubectl logs my-first-nginx`: Accessed the container's output logs for diagnostic purposes.
*   `kubectl delete pod my-first-nginx` & `minikube stop`: Cleaned up the deployed resources and safely powered down the local cluster to free system memory.

![img-1](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-5(1).png?raw=true)

![img-2](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-5(2).png?raw=true)

![img-3](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-5(3).png?raw=true)

---

# CY domain

## Task 1: Fundamentals of Computer Networking: Introduction

A network is a collection of connected things. Just like a friend group or a city’s transit system, a computer network links devices—from laptops to traffic lights—to share data. 

Networks scale from two devices to the global internet. Because they power everything from power grids to social media, securing these connections is the foundation of cybersecurity.

---

## Task 2: Fundamentals of Computer Networking: Internet

The Internet started in the late 1960s with ARPANET, later becoming a global information library in 1989 when Tim Berners-Lee created the World Wide Web. 

Essentially a "network of networks," it connects small private groups into a massive public network. To communicate across this global web, every device uses a unique address—acting like a name tag—to ensure data reaches the right destination.

---

## Task 3: Fundamentals of Computer Networking: IP Address

Devices use IP and MAC addresses to identify each other. An **IP address** is like a temporary name (e.g., 192.168.1.10) that can change. It can be private for local networks or public for the internet. Because IPv4 addresses ran out, IPv6 was created to offer virtually unlimited space. 

Conversely, a **MAC address** is a permanent physical fingerprint built into hardware. However, attackers can bypass security using "MAC spoofing," making it unsafe to rely on MAC addresses alone.

---

## Task 4: Fundamentals of Computer Networking: Ports

Ports are numbered communication channels (from 0 to 65535) where data enters and leaves a device, acting like specialized harbor docks for specific traffic. 

Standardized "well-known ports" (0–1024) ensure applications communicate consistently; for example, HTTP uses Port 80, while HTTPS uses Port 443. While these defaults are standard practice to keep browsing seamless, they can be customized—requiring users to specify the custom port manually in the network address. 

---

## Task 5: Fundamentals of Computer Networking: Packets and Frames

Data travels across networks by breaking large files into smaller units called packets and frames. A **packet** (Layer 3) contains the data and IP addresses, while a **frame** (Layer 2) encapsulates the packet with MAC addresses for local delivery—much like putting a letter inside an envelope.

Packets include critical header fields like the Source/Destination IPs, a Checksum for corruption checks, and a Time To Live (TTL) value to prevent eternal network congestion.

---
## Task 6: Fundamentals of Computer Networking: Networking Devices

Network devices use physical memory and logical operating systems to connect hardware, direct traffic, and enforce security across the OSI model layers.

### Core Connectivity Devices
* **Hub (Layer 1):** A basic device that blindly broadcasts incoming data to all ports, causing traffic collisions and inefficiencies.
* **Switch (Layer 2):** Connects local devices (LAN) intelligently, using MAC addresses to forward data packets only to the intended recipient.
* **Access Point (Layer 2/1):** Bridges wired and wireless networks, extending LAN connectivity to Wi-Fi devices.
* **Router (Layer 3):** Connects entirely different networks. It uses IP addresses to find efficient paths, manages traffic via NAT/DHCP, and secures boundaries.
* **Multilayer Switch (Layers 2 & 3):** Combines the rapid local switching of Layer 2 with the hardware-based routing of Layer 3 to handle inter-VLAN traffic seamlessly.

### Security and Defense Devices
* **Firewall:** Acts as a barrier between trusted and untrusted networks, filtering traffic based on security rules. Next-Gen Firewalls (NGFW) use Deep Packet Inspection to catch hidden malware.
* **IDPS:** **IDS** passively monitors and alerts administrators about suspicious traffic (like an alarm). **IPS** sits inline to actively detect and block threats in real time.
* **VPN:** Creates an encrypted tunnel over the public internet to provide secure remote access (Site-to-Site or Remote Access), ensuring data confidentiality.

---
## Task 7: Protocols: DNS

The **Domain Name System (DNS)** serves as the phonebook of the Internet. Because computers communicate using numbers while humans prefer names, DNS translates human-readable domain names (like `google.com`) into machine-readable IP addresses (like `142.250.195.78`). 

Without DNS, users would have to memorize complex strings of numbers for every website they want to visit.

---
## Task 8: Protocols: DHCP

**Dynamic Host Configuration Protocol (DHCP)** is an application-layer protocol (using UDP ports 67/68) that automatically configures network settings—like IP addresses, subnet masks, default gateways, and DNS servers—for connecting devices. While servers require static, manual IP setups, everyday mobile devices rely on DHCP to avoid configuration hassle and IP address conflicts.

### The DORA Process
When connecting to a network, a device initially uses broadcast addresses (`0.0.0.0` and MAC `ff:ff:ff:ff:ff:ff`) to run through four quick steps:

1. **Discover:** The client broadcasts a request to locate available DHCP servers.
2. **Offer:** The server suggests an available IP address and network details.
3. **Request:** The client asks to officially lease that specific IP address.
4. **Acknowledge:** The server confirms the setup, officially putting the device online.

---
## Task 9: Protocols: ICMP

The **Internet Control Message Protocol (ICMP)** is used for network diagnostics and error reporting, helping devices communicate connectivity issues. Two essential tools rely on it:

### 1. Ping
Acts like digital ping-pong to test if a target system is reachable. 
* **Process:** Your device sends an **Echo Request (Type 8)**, and the target answers with an **Echo Reply (Type 0)**. 
* **Output:** It measures Round-Trip Time (RTT) and packet loss. Missing replies mean the target is offline or a firewall is blocking ICMP.

### 2. Traceroute
Maps the exact path (hops) data takes to a destination by manipulating the packet's **Time-To-Live (TTL)** value. Each router drops the TTL by 1; when TTL hits 0, the router drops the packet and sends back an **ICMP Time Exceeded (Type 11)** message, revealing its IP address and delay.

---