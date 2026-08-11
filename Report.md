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
## Task 4: Launch and manage an AWS EC2 Instance

### Objective Overview
* Provision and manage a live AWS EC2 virtual machine to transition from local development to cloud infrastructure.
* Configure secure remote access and deploy a lightweight web server (Nginx) accessible via a public IP.

### Implementation Summary
* **AWS Setup:** Resolved initial billing e-mandate loops to successfully activate the AWS Free Tier console.
* **Provisioning:** Launched a `t3.micro` instance running the Amazon Linux operating system.
* **Security & Access:** Configured the AWS Security Group to explicitly allow inbound traffic on Ports 22 (SSH) and 80 (HTTP).
* **Troubleshooting Permissions:** Overcame Windows NTFS and OneDrive permission conflicts by disabling file inheritance and strictly limiting `.pem` read access to a single user profile.
* **Deployment:** Connected securely via SSH using the `ec2-user` profile, installed the Nginx web server via the `dnf` package manager, and successfully verified public web access.
* **Cleanup:** Terminated the instance and its attached storage volumes to ensure zero ongoing costs.

![Img-1](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/ec2-task4-marvel.png?raw=true)

### Concepts Mastered
* **IaaS Fundamentals:** Gained practical, hands-on experience provisioning and configuring raw cloud compute resources.
* **Compute Mechanics:** Understood the `t3.micro` burstable CPU credit system and its fixed memory constraints.
* **Network Security:** Mastered using AWS Security Groups as stateful, virtual firewalls to enforce the principle of least privilege.
* **Cryptographic Authentication:** Transitioned from traditional password-based logins to highly secure asymmetric key-pair (`.pem`) remote access.

![Img-2](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/ec2-task4-2.png?raw=true)

![Img-3](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/ec2-task4-3.png?raw=true)

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

## Task 6: Manage AWS S3 and IAM with CLI

### Task Objective
To configure the AWS Command Line Interface (CLI), implement secure Identity and Access Management (IAM) practices, and manage Amazon S3 object storage directly from the terminal.

### IAM Security & Authentication
* **User Creation:** Created a dedicated IAM User specifically for programmatic access, ensuring the root AWS account remains secure.
* **Policy Management:** Assigned necessary S3 access policies to the IAM user to authorize specific cloud operations.
* **CLI Configuration:** Generated an Access Key ID and Secret Access Key, and used `aws configure` to authenticate the Kali Linux terminal with AWS.

### S3 Bucket Provisioning
* **Global Naming Constraints:** Navigated S3's global namespace requirements by resolving a `BucketAlreadyExists` error to secure a unique bucket identifier.
* **Bucket Creation:** Successfully utilized the `aws s3 mb` command to provision a new storage bucket hosted in the `ap-south-1` region.

### Object Operations & Data Lifecycle
* **Uploading:** Created a local test file and pushed it to the cloud container using `aws s3 cp`.
* **Verification:** Queried the cloud environment using `aws s3 ls` to confirm the object was successfully stored.
* **Retrieval & Cleanup:** Downloaded the object back to the local filesystem, followed by securely deleting the cloud copy using `aws s3 rm`.

### Key Takeaways
Successfully bridged local command-line operations with AWS infrastructure, gaining practical experience in automated cloud storage management and programmatic identity verification.

![Img-1](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-6(1).png?raw=true)

![Img-2](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-6(2).png?raw=true)


---

## Task 7: Deploy a Containerized Application on Kubernetes

### Overview
This report details the deployment of a containerized Nginx application to a Kubernetes cluster using YAML manifests. The application was exposed both internally and externally, and dynamic scaling was verified.

### 1. Deployment Creation
I created a Kubernetes `Deployment` manifest (`deployment.yaml`) to manage application. 
- **Image used**: `nginx:latest`
- **Replicas**: Initially set to 3 to ensure high availability.
- **Result**: The deployment successfully pulled the Docker image and spun up 3 identical Pods running the application.

### 2. Exposing the Application
To make the application accessible, I created a `Service` manifest (`service.yaml`). 
- **Service Type**: `NodePort`. This type of service inherently satisfies two networking requirements:
  1. **ClusterIP**: It creates an internal IP address so other resources inside the Kubernetes cluster can communicate with the app.
  2. **NodePort**: It maps an external port (`30080`) on the node directly to the internal pods, allowing to access the application via a web browser from our local machine.
- **Validation**: The Nginx welcome page was successfully accessed via the exposed NodePort URL.

### 3. Scaling Operations
 Interacted with the Kubernetes control plane using `kubectl` to dynamically scale the application without downtime.
- **Scaling Up**: Scaled the deployment to 5 replicas (`kubectl scale deployment/my-nginx-app --replicas=5`). Kubernetes instantly scheduled and started 2 additional pods.
- **Scaling Down**: Scaled the deployment back down to 2 replicas (`kubectl scale deployment/my-nginx-app --replicas=2`). Kubernetes gracefully terminated 3 of the pods.

### Conclusion
The application was successfully containerized, deployed, networked, and scaled using declarative YAML manifests and `kubectl` commands, fulfilling all expected task outcomes.

![Img-1](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-7(1).png?raw=true)

![Img-2](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-7(2).png?raw=true)

---

## Task 8: Use Kubernetes Secrets and Environment Variables

### Overview
This report documents the successful implementation of configuration management and sensitive data handling in a Kubernetes cluster using ConfigMaps and Secrets. I verified the secure injection of these resources into a running container as environment variables.

### 1. ConfigMaps vs. Secrets 
A core outcome of this task was understanding when to use which resource:
- **ConfigMap**: Used for non-sensitive data, such as application settings, URLs, or environment tags (e.g., `APP_MODE=production`).
- **Secret**: Used specifically for sensitive data, such as passwords, API tokens, and AWS credentials. Kubernetes stores this data securely (Base64 encoded) and can be configured for encryption at rest to prevent accidental exposure.

### 2. Configuration Management (ConfigMap)
I created a ConfigMap named `app-config` using literal values to store general application settings.
- **Injected Variables**: `APP_MODE=production` and `APP_REGION=us-east-1`
- **Purpose**: To decouple the application's configuration from its container image, making the app portable across different environments.

### 3. Secure Credential Storage (Secret)
I created a generic Secret named `aws-credentials` to securely store AWS authentication keys.
- **Injected Variables**: `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`
- **Outcome**: By using a Secret, Avoided hardcoding sensitive AWS credentials directly into our Deployment YAML or Docker image, aligning with security best practices.

### 4. Deployment and Verification
Created a Deployment (`aws-app-deployment`) that utilized both resources:
- Using `envFrom`, we injected all key-value pairs from the `app-config` ConfigMap directly into the container's environment.
- Using `valueFrom.secretKeyRef`, we selectively mapped the AWS credentials from our Secret to the exact environment variables expected by the AWS SDK.
- **Verification**: Successfully used `kubectl exec` to enter the running Pod and execute the `env` command. The output confirmed that both the standard configuration (`APP_MODE`, `APP_REGION`) and the sensitive AWS credentials were successfully loaded into the container's environment, ready for the application to use.

### Conclusion
The application deployment was successfully configured to securely consume both non-sensitive settings and sensitive AWS credentials using Kubernetes native resources.

![Img-1](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-8(1).png?raw=true)

![Img-2](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-8(2).png?raw=true)

![Img-3](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-8(3).png?raw=true)

---

## Task 9: Deploy an App to Push Files from Kubernetes to S3

### Overview
This report details the successful development and deployment of a custom file-upload application on a Kubernetes cluster. The application securely pushes user-uploaded files directly to an AWS S3 bucket, integrating core concepts across Docker, Kubernetes, AWS IAM, and Kubernetes Secrets.

### 1. Application Development and Containerization
I developed a lightweight Python application using the Flask framework. The application provides a simple web interface for users to upload files and handles the backend logic of transmitting those files to S3.
- To ensure portability, I containerized the application by writing a `Dockerfile` that packages the Python environment, dependencies, and application code.
- I built the Docker image (`s3-uploader-app:v1`) directly inside the Minikube Docker environment to streamline the local deployment process.

### 2. Secure Credential Management
Security was a primary focus for this deployment. Rather than hardcoding sensitive AWS credentials into the application code or Docker image, I utilized Kubernetes native Secrets.
- I created a Secret manifest to securely store the `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`.
- I provisioned a dedicated IAM User in the AWS Console with an S3 access policy to strictly control access to the storage resources.

### 3. Kubernetes Deployment and Configuration
I authored a comprehensive Kubernetes Deployment and Service manifest to manage the application lifecycle and networking.
- **Environment Injection**: The Deployment was configured to securely inject the AWS credentials from the Kubernetes Secret into the Pod's environment variables. I also passed the target `S3_BUCKET_NAME` as a standard environment variable.
- **Networking**: I exposed the application to my local machine using a `NodePort` Service, allowing me to access the web UI seamlessly via the browser.

### 4. Validation and Outcomes
The pipeline was successfully validated end-to-end:
1. I accessed the web application interface running on the Minikube cluster.
2. I uploaded a file through the application's UI.
3. I verified in the AWS S3 Console that the file was successfully transmitted and stored in the target bucket.

### Conclusion
This task successfully demonstrated a complete, end-to-end cloud-native pipeline. I was able to build a custom application, package it with Docker, deploy it to Kubernetes, securely manage secrets, and interact with external cloud resources (AWS S3) dynamically.

![Img-1](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-9(1).png?raw=true)

![Img-2](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-9(2).png?raw=true)

![Img-3](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-9(3).png?raw=true)

![Img-4](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-9(4).png?raw=true)

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

![Image-1](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-cy-7(1).png?raw=true)

![Image-2](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-cy-7(2).png?raw=true)

![Image-3](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/M-1-T-cy-7(3).png?raw=true)

[Worksheet](https://github.com/gouravpd26-cmyk/marvel-level-1-report/blob/main/DNSLiveLabWorksheet-Completed.docx)

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

## Task 10: Protocols: HTTP (s)
Task 10 explores the fundamental web protocols: HTTP and HTTPS. While HTTP facilitates standard client-server communication for delivering web resources, HTTPS enhances this by employing SSL/TLS encryption. This secure layer prevents data interception and verifies server authenticity. I successfully observed these differences by accessing example.com over both protocols.

---

## Task 11: Protocols: Other Important models

Task 11 explains the OSI model, a theoretical framework dividing network communication into seven layers: Physical, Data Link, Network, Transport, Session, Presentation, and Application. While real-world implementations like TCP/IP condense these layers, the OSI model remains an essential educational tool for understanding network operations and describing networking equipment.

---

## Task 12: Windows: Introduction 

Task 12 introduces the Microsoft Windows operating system, focusing on file navigation and system management. It highlights the hierarchical folder structure in File Explorer for organizing data. Furthermore, it emphasizes essential maintenance habits, including regular Windows updates, secure application management, and utilizing Task Manager to monitor real-time system performance.

---

## Task 13: Windows: Powershell

Task 13 details PowerShell, a powerful, cross-platform automation tool and scripting language by Microsoft. Unlike traditional text-based shells, PowerShell is built on the .NET framework and utilizes object-oriented data processing. This structural advantage allows administrators to easily automate complex system configurations and manage interconnected environments with high efficiency.

---

## Task 14:  Windows: Powershell vs CMD

 Task 14 compares Windows Command Prompt and PowerShell. CMD is a legacy, text-based shell suitable for basic, local automation tasks. Conversely, PowerShell is a modern, object-oriented framework designed for advanced, remote system administration. Ultimately, PowerShell offers greater flexibility and capabilities, though CMD aliases ease the transition for traditional users.

 ---

 ## Task 15: Windows: System32

Task 15 explains the Windows directory, typically located at `C:\Windows`, which houses essential operating system files. It emphasizes the critical System32 subfolder, containing vital tools and utilities. Modifying or deleting System32 files can severely break Windows. Environment variables like `%windir%` dynamically help the system locate this core directory reliably.

---

## Task 16: Windows: User Accounts & UAC 

Task 16 covers Windows user accounts, highlighting Administrators and Standard Users. Administrators hold full privileges to modify system settings and user groups, while Standard Users only manage personal files. It also explains managing profiles located in `C:\Users` and utilizing local groups to streamline permission management across multiple users effectively.

---

## Task 17: Windows: Security 
Task 17 details built-in Windows Security features designed to protect against threats. It covers Virus & threat protection for malware scanning, App & browser control, and Device security. Additionally, it highlights the Windows Firewall, which controls inbound and outbound network access across Domain, Private, and untrusted Public networks securely.

---

## Task 18: Linux: Introduction
 
Task 18 introduces Linux, an open-source, highly efficient, and flexible operating system. Widely utilized in web servers, critical infrastructure, and retail systems, Linux offers stability and lightweight performance. It explains that Linux encompasses multiple distributions, like Ubuntu and Debian, which are customizable for varied server and desktop computing needs.

---

## Task 19: Linux: File Systems
Task 19 covers essential Linux file management commands. Key utilities include touch for creating files, mkdir for directories, cp for copying, mv for moving or renaming, and rm for permanent deletion. It also introduces the file command to accurately identify file types, as Linux doesn't rely strictly on extensions.

---

## Task 20: Others: Cryptography - Part 1

Task 20 introduces cryptography, the cornerstone of digital privacy and security. It ensures confidentiality and integrity by transforming readable plaintext into unreadable ciphertext using mathematical ciphers and secret keys. Decryption reverses this process. Cryptography safely underpins everyday activities, from secure web browsing to maintaining essential regulatory data compliance.

---

## Task 21:  Others: Cyptography - Part 2

Task 21 contrasts symmetric and asymmetric encryption. Symmetric encryption, like AES, uses a single shared key for both encryption and decryption, demanding secure key exchange. Asymmetric encryption, like RSA, solves this distribution problem by using a public key to encrypt and a private key to decrypt, though it is slower.

---

## Task 23: Principles of CyberSecurity: CIA 

Task 23 introduces the CIA triad, the foundational pillar of cybersecurity. This framework focuses on preserving Confidentiality (keeping data private), Integrity (preventing unauthorized modifications), and Availability (ensuring systems remain accessible). Understanding these core principles helps security professionals identify real-world vulnerabilities and make informed decisions to protect digital environments from attacks.

---

## Task 24: Principles of CyberSecurity: CIA - Explanantion 

Task 24 details the CIA Triad, cybersecurity's core foundation. Confidentiality ensures sensitive data remains accessible only to authorized individuals, preventing privacy breaches. Integrity guarantees data remains accurate and unaltered by unauthorized parties. Finally, Availability ensures critical services and data are reliably accessible to authorized users exactly when needed.

---

## Task 25: Path 1 - Red Teaming

Task 25 introduces offensive security, focusing on actively testing systems to uncover weaknesses before real attackers exploit them. It emphasizes viewing networks from an attacker's perspective by questioning exposed resources and system assumptions. Additionally, it defines penetration testing as a legal, ethical process used to strengthen organizational security.

---

## Task 26: Red Teaming Continuation

Task 26 introduces a practical ethical hacking exercise, defining core offensive security terms like Red Teaming, Vulnerability, Exploit, and Scope. Highlighting the critical requirement of explicit permission, the task demonstrates how attackers discover hidden web application pages manually through URL manipulation and automatically using enumeration tools like Gobuster.

---