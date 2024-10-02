## 1. Day-to-Day Life Scenario of a DevOps Engineer
Explain Roles and Responsibilities

## 2. Architecture of Your Project
When explaining the architecture of a project, start with the high-level overview. For example, you could describe a microservices-based architecture hosted on cloud platforms like AWS or Azure. Explain how each microservice is containerized using Docker and orchestrated with Kubernetes. Describe the use of CI/CD pipelines to automate the build, test, and deployment processes, and how tools like Jenkins or GitLab CI are integrated. Mention the use of infrastructure as code (IaC) for managing the underlying infrastructure, ensuring consistency and scalability. For example, Terraform is used to provision resources, while Ansible is used for configuration management. Discuss how monitoring and logging are implemented using Prometheus, Grafana, and ELK Stack to ensure the system's health and performance.

## 3. Clusters in Production Environment
In a typical production environment, you might use multiple Kubernetes clusters to manage different services or environments (e.g., staging, production). The number of clusters depends on the complexity and scale of the application. For example, in a production environment, you might have 3 clusters: one for the core application, one for databases, and another for auxiliary services like monitoring and logging. Each cluster could be configured with autoscaling, with nodes having a CPU size of 4 vCPUs and 16GB RAM, ensuring enough resources to handle peak traffic. Autoscaling ensures that the cluster scales up or down based on load, optimizing resource usage and cost.

## 4. Integrating ELB and Auto Scaling
Elastic Load Balancing (ELB) and Auto Scaling are key components of an AWS architecture. To integrate them, you first set up an ELB to distribute incoming traffic across multiple EC2 instances. The ELB ensures high availability by routing traffic only to healthy instances. Next, you configure an Auto Scaling group to manage the EC2 instances. You define scaling policies based on metrics like CPU utilization. When the load increases, Auto Scaling automatically launches additional instances and adds them to the ELB, ensuring that the application can handle the increased traffic. When the load decreases, it terminates the excess instances to reduce costs. Health checks are configured to ensure that only healthy instances receive traffic.

## 5. Configuring VPC
To configure a Virtual Private Cloud (VPC) in AWS, start by defining the CIDR block for the VPC, which determines the range of IP addresses. Next, create subnets within the VPC, typically divided into public and private subnets. Public subnets are associated with a route table that directs internet-bound traffic to an internet gateway, while private subnets route traffic through a NAT gateway for outbound connections. Security groups and network ACLs are configured to control inbound and outbound traffic at the instance and subnet levels, respectively. The VPC is also connected to other networks (on-premises or other VPCs) using VPNs or VPC peering, ensuring secure communication.

## 6. Handling Disaster Recovery
Disaster recovery in a DevOps environment involves preparing for potential failures and ensuring that systems can recover quickly. A common strategy includes setting up a multi-region or multi-availability zone deployment where the application is replicated across different geographic locations. In case of a failure in one region, traffic is automatically redirected to a healthy region. Regular backups of critical data are taken and stored in different locations, and databases are configured with cross-region replication. Disaster recovery plans also include automated failover mechanisms, regular DR drills, and clearly defined RTO (Recovery Time Objective) and RPO (Recovery Point Objective) to minimize downtime and data loss.

## 7. Git Commands: Stash, Squash, Cherry-pick
Stash: The git stash command is used to temporarily save changes that are not yet ready to be committed. It allows you to switch branches without committing your work. You can later apply the stashed changes using git stash apply.
Squash: git squash is not a direct command, but the process of squashing is typically done during a rebase. git rebase -i allows you to combine multiple commits into a single commit, which can be useful for cleaning up a messy commit history before merging.
Cherry-pick: git cherry-pick allows you to apply the changes from a specific commit to your current branch. This is useful when you want to apply a bug fix from one branch to another without merging the entire branch.

## 8. Explain Dockerfile and Building a Simple Image
A Dockerfile is a script that contains a series of instructions for building a Docker image. Each instruction in a Dockerfile creates a layer in the image. A simple Dockerfile might start with a base image (e.g., FROM python:3.8), followed by commands to copy the application code into the container (COPY . /app), install dependencies (RUN pip install -r requirements.txt), and specify the command to run the application (CMD ["python", "app.py"]). To build an image from this Dockerfile, you use the command docker build -t my-app ., which creates an image tagged my-app that can be run as a container.

## 9. Demo of an Internal Project
When asked to demo an internal project, you can walk through the project's repository in Git, explaining the structure and key components. Show the CI/CD pipeline setup, explaining how code is automatically built, tested, and deployed. You can also share screenshots or even live access (if possible) to the frontend or other parts of the application, explaining how different microservices interact, how monitoring is set up, and any unique challenges you faced and overcame.

## 10. Application Deployment Process
Application deployment can be explained as the process of moving code from development to a production environment. In a typical CI/CD pipeline, after the code is committed to a repository, automated tests are run. If the tests pass, the application is built into a Docker image and pushed to a container registry. From there, the deployment process begins, which might involve pulling the latest image into a Kubernetes cluster, where it is deployed using Helm charts or Kubernetes manifests. The process includes rolling updates to ensure zero downtime, with monitoring and logging tools in place to track the deployment’s success.

## 11. Detailed Explanation of an Internal Project
Explain the purpose of the project, the technologies used, and your role. Discuss the architecture, how you implemented CI/CD, how you handled configuration management, and how you ensured security and scalability. If the project involved collaboration, mention how you worked with other teams. Highlight any challenges and how you addressed them, focusing on the impact your work had on the project’s success.

## 12. Linux-Related Concepts
Zombie Process: A zombie process is a process that has completed execution but still has an entry in the process table, meaning its parent process has not yet read its exit status. It doesn’t consume resources but can indicate issues in process management.
Inode: An inode is a data structure on a filesystem that stores information about a file or directory, like its size, ownership, and location on disk. Each file has a unique inode number.
Hardlink: A hardlink is a directory entry that points to the same inode as another file. Multiple hardlinks to the same inode share the same data.
Kill: The kill command is used to send signals to processes, most commonly to terminate them. For example, kill -9 sends a SIGKILL signal to forcefully terminate a process.
Get Process IDs: You can get process IDs using the ps command or pgrep followed by the process name. For example, ps aux | grep process_name or pgrep process_name.
Root User Benefits: The root user has unrestricted access to all commands and files on a Linux system, making it essential for administrative tasks. However, it's also a security risk if not managed properly.
Other Users: Other users on the system have restricted permissions based on their roles. Users can be part of groups that grant specific permissions, and sudoers can perform root-level tasks without being root.

## 13. Determining if a Subnet is Private or Public:

Private Subnet: A subnet is considered private if it does not have a route to the internet. In AWS, this is typically achieved by not associating the subnet with an internet gateway. Instead, it might have routes to a Virtual Private Gateway (for VPN connections) or other private networks.
Public Subnet: A subnet is considered public if it has a route to an internet gateway, allowing resources in that subnet to communicate directly with the internet. This is usually done by associating a route table with the subnet that includes a route to an internet gateway.

## 14. Difference Between EBS and EFS:
EBS (Elastic Block Store): EBS provides block-level storage that is attached to EC2 instances. It is like a virtual hard drive for an EC2 instance, and the storage is persistent and can be detached and attached to other instances. EBS volumes are useful for single-instance applications where data persistence is needed.
EFS (Elastic File System): EFS provides scalable file storage that can be mounted on multiple EC2 instances simultaneously. It is a shared file system, meaning multiple instances can access the same files, making it suitable for applications that require shared access to data across multiple instances.

## 15. Difference Between ALB and NLB:
ALB (Application Load Balancer): Operates at the application layer (Layer 7) of the OSI model. It is designed to handle HTTP/HTTPS traffic and can perform advanced routing based on URL paths, host headers, and more. It is used for web applications and microservices.
NLB (Network Load Balancer): Operates at the transport layer (Layer 4) of the OSI model. It is designed to handle TCP/UDP traffic and is optimized for high performance and low latency. NLB is suitable for applications that require extreme performance and static IP addresses.

## 15. Running a Specific Container in a Pod in Kubernetes:
To run a specific container in a Kubernetes pod, you define the container in the pod specification within a YAML file. You can specify the container's image, commands, ports, and other configuration details. Once the pod is created, Kubernetes will ensure the container runs according to the defined configuration. For example:

apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: my-container
    image: my-container-image
    ports:
    - containerPort: 80

## 16 .State in Terraform:
The Terraform state file (terraform.tfstate) is a critical component that maintains the mapping between your configuration files and the actual resources in your infrastructure. It keeps track of resource IDs and metadata, allowing Terraform to perform updates, deletions, and create changes efficiently.

## 17.Remote State in Terraform:
Remote state refers to storing the Terraform state file in a remote backend (such as AWS S3, Azure Blob Storage, or Terraform Cloud) rather than locally. This allows multiple team members to work on the same infrastructure and provides centralized state management and locking mechanisms to prevent concurrent changes.

## 18. Pipeline Stages in Your Organization:
Pipeline stages typically include:
Source: Code is pulled from a version control system.
Build: Code is compiled and artifacts are created.
Test: Automated tests are run to ensure code quality.
Deploy: Artifacts are deployed to a staging or production environment.
Release: The application is made available to users.
Monitor: The application’s performance and health are monitored.

## 19. Terraform Data Block vs. Resource Block:
Data Block: Used to retrieve information from the infrastructure that Terraform can use. Data blocks do not create or manage resources; they only query existing resources.

data "aws_ami" "latest_amazon_linux" {
  owners = ["amazon"]
  most_recent = true
  filters {
    name = "name"
    values = ["amzn2-ami-hvm-*-x86_64-gp2"]
  }
}
Resource Block: Used to create, update, or delete resources. Resources define the infrastructure components you want to manage.

resource "aws_instance" "example" {
  ami           = data.aws_ami.latest_amazon_linux.id
  instance_type = "t2.micro"
}

## 20. Entry Point vs CMD in Docker:
ENTRYPOINT: Defines the default executable to run when a container starts. It is used to set the main command and is not overridden by arguments passed to docker run.

ENTRYPOINT ["python", "app.py"]
CMD: Provides default arguments to the ENTRYPOINT command or, if ENTRYPOINT is not set, defines the command to run. CMD can be overridden by arguments passed to docker run.

CMD ["--port", "80"]
What is a Dockerfile?

A Dockerfile is a text file containing instructions to build a Docker image. It defines the base image, sets up the environment, copies files, installs dependencies, and specifies the command to run when the container starts. Example:

FROM python:3.8
WORKDIR /app
COPY . /app
RUN pip install -r requirements.txt
CMD ["python", "app.py"]
How Pods Communicate with Each Other in Kubernetes:

Pods in the same Kubernetes cluster can communicate with each other using their IP addresses and DNS names. Kubernetes provides a flat network model where every pod gets its own IP address, and services are used to expose and manage communication between pods.
What is a VPC Endpoint?

A VPC Endpoint allows you to connect to AWS services from within your VPC without traversing the internet. It provides a private connection between your VPC and supported AWS services, enhancing security and performance.
Similarities Between SSL and TLS:

Both SSL (Secure Sockets Layer) and TLS (Transport Layer Security) are cryptographic protocols designed to provide secure communication over a network. TLS is the successor to SSL, offering improved security and efficiency. They both use encryption to protect data in transit and authentication to verify the identities of communicating parties.
Making an Application More Secure:

Implement secure coding practices, use encryption for data at rest and in transit, perform regular security audits and vulnerability scans, use firewalls and network security groups, apply least privilege access control, and ensure timely updates and patches.
Architecture of Your Application CI/CD Deployment:

This typically involves source code management (e.g., Git), a CI/CD tool (e.g., Jenkins, GitLab CI), build automation (e.g., Maven, Gradle), automated testing, deployment automation (e.g., Ansible, Terraform), and monitoring/feedback systems.
What is Multi-stage in Docker?

Multi-stage builds in Docker allow you to use multiple FROM statements in a single Dockerfile to create smaller and more efficient images. You can use intermediate stages for building and compiling and then copy only the necessary artifacts into the final image.

# Stage 1: Build
FROM node:14 AS build
WORKDIR /app
COPY . .
RUN npm install && npm run build

# Stage 2: Final image
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
Namespace in Kubernetes:

Namespaces are virtual clusters within a Kubernetes cluster that provide isolation between resources. They allow multiple teams or applications to share the same physical cluster while keeping their resources separated.
Tags in Ansible:

Tags in Ansible allow you to selectively execute parts of a playbook. By assigning tags to tasks or roles, you can run only those tasks that match a given tag, which is useful for testing or partial deployment.

tasks:
  - name: Install package
    apt: name=nginx state=present
    tags: [install, web]
Pod Security Policy:

A Pod Security Policy (PSP) is a Kubernetes resource that defines a set of conditions that a pod must meet to be accepted into the cluster. It controls aspects such as privilege escalation, volume types, and user namespaces to enhance security.
AMI and Snapshot Difference:

AMI (Amazon Machine Image): A snapshot of an EC2 instance’s root volume and any attached EBS volumes, used to launch new instances with the same configuration.
Snapshot: A backup of an EBS volume at a specific point in time, which can be used to restore the volume or create new volumes.
Upgrade Master Node:

To upgrade a master node in a Kubernetes cluster, you typically follow these steps:
Upgrade the control plane components (kube-apiserver, kube-scheduler, kube-controller-manager).
Upgrade kubelet and kubectl on the master node.
Validate the cluster functionality and apply any necessary configuration changes.
Securing a Running Container with a Vulnerability:

To secure a running container with a vulnerability:
Isolate the container to prevent further impact.
Update the container image to a version without the vulnerability.
Redeploy the updated container.
Apply additional security measures such as network segmentation and runtime security monitoring.
Increasing Kubernetes Security:

Use network policies, enable RBAC (Role-Based Access Control), apply Pod Security Policies, use image scanning and signing, enforce security contexts, and implement logging and monitoring.
Problem Faced:

Describe a specific problem you encountered, such as scaling issues, deployment failures, or integration challenges, and explain how you identified the problem, the steps you took to resolve it, and the outcome.
What is S3?

Amazon S3 (Simple Storage Service) is a scalable object storage service for storing and retrieving any amount of data. It is commonly used for backup, archiving, and as a data lake for analytics.
Issues Faced in Jenkins Non-Prod to Prod:

Common issues include configuration differences between environments, permission problems, dependency mismatches, and data migration issues. Solutions involve aligning configurations, managing credentials securely, and ensuring consistent environment setup.
Issues Faced in Web Application from Pre-Pod to Pod:

Issues might include application not starting due to misconfiguration, network connectivity problems, or resource constraints. Debugging involves checking logs, configuration files, and resource usage.
Git Conflict:

A Git conflict occurs when changes in different branches cannot be automatically merged. To resolve it, manually edit the conflicting files, mark them as resolved using git add, and complete the merge with git commit.
Branching Strategy:

Common branching strategies include:
Git Flow: Uses feature, develop, and release branches.
GitHub Flow: Uses a single main branch and feature branches.
GitLab Flow: Combines feature branching with environment branches.
How Often Do You Release the Product:

This depends on the organization’s release cycle. It could be weekly, bi-weekly, monthly, or continuous deployment, depending on the project requirements and team practices.
Your Role in the Project:

Discuss your specific responsibilities, such as managing CI/CD pipelines, infrastructure automation, application deployment, or monitoring and troubleshooting.
Day-to-Day Activities:

Typical activities include monitoring systems, managing deployments, troubleshooting issues, updating documentation, and collaborating with development and operations teams.
Handling Production Issues:

Follow a structured approach: identify the issue, assess its impact, use logs and monitoring tools to diagnose, apply a fix, test the solution, and communicate with stakeholders.
Pipeline Issues in Jenkins:

Common issues include failing builds, plugin errors, and misconfigurations. Troubleshooting involves checking Jenkins logs, validating pipeline scripts, and reviewing plugin versions.
Production Pipeline Issues in Jenkins:

Similar to general pipeline issues but with added complexity due to the production environment. Focus on issues affecting live systems, such as downtime or deployment failures.
Kubernetes Issues in Production:

Issues might include pod crashes, resource limitations, and networking problems. Use Kubernetes logs, metrics, and diagnostic tools to identify and resolve problems.
Collaborating with Various Teams:

Effective collaboration involves regular meetings, clear communication channels, using shared documentation, and coordinating with development, operations, and security teams.
Build Issues Faced in Your Project:

Discuss specific build issues such as dependency problems, compilation errors, or environment inconsistencies, and how you resolved them.
Deployment Strategies:

Common strategies include Blue/Green Deployment, Canary Releases, Rolling Updates, and Feature Toggles. Each has its advantages and use cases depending on the application and risk tolerance.
Architecture of Kubernetes:

Kubernetes architecture includes the Master Node (containing the API server, scheduler, and controller manager) and Worker Nodes (running kubelet and kube-proxy). It uses etcd for storage and provides a robust platform for container orchestration.
Booting Process in Linux:

The booting process includes:
BIOS/UEFI: Initializes hardware and loads the bootloader.
Bootloader (GRUB): Loads the kernel.
Kernel: Initializes system components and mounts the root filesystem.
Init System (e.g., systemd): Starts system services and user processes.
What is an Inode in Linux?

An inode is a data structure on a filesystem that stores information about a file or directory, such as its size, permissions, and location on the disk.
Various Plugins in Jenkins Pipeline:

Examples include:
Git Plugin: For version control integration.
Maven Plugin: For building Java applications.
Docker Plugin: For building and deploying Docker containers.
Tool Integration with Jenkins:

Tools are integrated with Jenkins via plugins, which need to be installed and configured to interact with the specific tools and services, such as SCM systems, build tools, or deployment platforms.
Resolving Merge Conflicts:

Manually resolve conflicts in the affected files, then mark the conflicts as resolved using git add, and complete the merge with git commit.
What is VPC and Its Components:

A VPC (Virtual Private Cloud) is a logically isolated network within a cloud provider. Components include subnets, route tables, internet gateways, NAT gateways, and security groups.
Difference Between NACL and Security Groups:

NACL (Network Access Control List): Stateless and applies rules at the subnet level. It controls inbound and outbound traffic.
Security Groups: Stateful and applies rules at the instance level. It controls inbound and outbound traffic specific to instances.
Difference Between Network and Application Load Balancer:

Network Load Balancer (NLB): Operates at Layer 4 (TCP/UDP), suitable for high-performance applications.
Application Load Balancer (ALB): Operates at Layer 7 (HTTP/HTTPS), suitable for web applications and advanced routing.
Different Dashboards Created in Grafana:

Grafana dashboards can display various metrics and visualizations, such as system performance, application health, and network traffic, using data from sources like Prometheus, InfluxDB, or Elasticsearch.
What is Ansible Playbook?

An Ansible playbook is a YAML file that defines a set of tasks to be executed on managed hosts. It describes the desired state of the system and automates configuration management and deployment.
Handlers in Ansible Playbook:

Handlers are special tasks in Ansible that run only when notified by other tasks. They are typically used for actions that need to be performed only when a change occurs, such as restarting a service.
Various Modules Used in Ansible:

Examples include:
ansible.builtin.yum: For managing packages on RPM-based systems.
ansible.builtin.file: For managing file properties.
ansible.builtin.service: For managing services.
Ansible Ad Hoc Command:

Ad hoc commands are used for quick, one-off tasks. They allow you to execute a single command on your managed hosts without writing a playbook.

ansible all -m ping
Pod Health Check in Kubernetes:

Kubernetes uses liveness probes and readiness probes to check the health of pods. Liveness probes ensure the container is running, while readiness probes check if the container is ready to serve traffic.
Route 53 Types:

Simple Routing: Route traffic based on a single resource record.
Weighted Routing: Distribute traffic based on weights assigned to different records.
Latency-Based Routing: Route traffic based on lowest latency.
Failover Routing: Route traffic to a secondary resource if the primary fails.
Geolocation Routing: Route traffic based on the geographic location of the requester.
Helm Charts Usage:

Helm charts are packages of pre-configured Kubernetes resources that make it easier to deploy and manage applications. Charts define Kubernetes manifests and configuration in a reusable and version-controlled format.
Terraform Modules:

Modules in Terraform are reusable components that encapsulate a set of resources. They allow you to define infrastructure as a module once and reuse it across different configurations.

module "vpc" {
  source = "./modules/vpc"
  vpc_cidr_block = "10.0.0.0/16"
}
Docker Volume:

Docker volumes are used to persist data outside of containers. They are stored on the host filesystem and can be shared between containers. Volumes are managed by Docker and provide a way to persist data across container restarts.

docker run -v my_volume:/data my_image
Network ACL to Block Particular IP:

You can configure a Network ACL (NACL) to block traffic from specific IP addresses by adding inbound or outbound rules with the action set to "deny" for the desired IP range.
Blue/Green Deployment Pattern:

This deployment pattern involves running two environments, Blue and Green. The Blue environment represents the current production version, while the Green environment is the new version. Once the Green environment is tested and validated, traffic is switched from Blue to Green.
Route Table in Amazon VPC:

A route table contains rules, called routes, that determine where network traffic is directed within the VPC. Each subnet in a VPC must be associated with a route table.
IAM Role:

An IAM role is an AWS identity with specific permissions that can be assumed by entities like users, applications, or services to access AWS resources. It does not have credentials associated with it.
IAM Policy:

An IAM policy defines permissions and access levels granted to IAM roles or users. It specifies what actions are allowed or denied on AWS resources.
Merge vs. Rebase:

Merge: Combines changes from different branches and creates a merge commit.
Rebase: Applies changes from one branch onto another, rewriting history to create a linear sequence of commits.
Interactive Rebase in Git:

Interactive rebase allows you to edit, reorder, squash, or drop commits in a branch. It provides a way to clean up commit history before merging.


git rebase -i HEAD-n
Squash in Git:

Squashing combines multiple commits into a single commit. It is useful for consolidating changes and maintaining a clean commit history.


git rebase -i HEAD-n
Fast-Forward Merge in Git:

A fast-forward merge occurs when the target branch is directly ahead of the source branch, allowing Git to simply move the branch pointer forward without creating a new merge commit.
Cherry Pick in Git:

Cherry-picking allows you to apply specific commits from one branch to another. It is useful for applying bug fixes or features without merging the entire branch.


git cherry-pick <commit-hash>
Jenkins Error:

Errors in Jenkins could be due to plugin failures, build script issues, or configuration problems. Diagnose by checking Jenkins logs, reviewing build configuration, and verifying plugin compatibility.
Provider in Terraform:

A provider in Terraform is a plugin that allows Terraform to interact with cloud providers or other APIs. Providers define the available resources and how to manage them.

provider "aws" {
  region = "us-east-1"
}
Services Handled in AWS:

Examples include EC2 (virtual servers), S3 (object storage), RDS (managed databases), Lambda (serverless computing), and CloudFormation (infrastructure as code).
Exposure in Compute:

Exposure in compute refers to experience with cloud-based compute services like AWS EC2, Google Compute Engine, or Azure VMs, including provisioning, scaling, and managing instances.
Creating Clusters in EKS:

Creating clusters in Amazon EKS involves configuring the cluster, setting up node groups, and deploying workloads. This can be done using the AWS Management Console, AWS CLI, or Terraform.
Managed vs. Non-Managed Clusters in EKS:

Managed Clusters: EKS manages the Kubernetes control plane.
Non-Managed Clusters: The user manages the Kubernetes control plane, usually in a self-managed environment.
Creating Cluster with Terraform or Manually:

Discuss whether you created the cluster using Terraform for infrastructure as code benefits or manually through the AWS console for more hands-on control.
Kubernetes Cluster Communication:

Kubernetes clusters communicate using internal networking, typically through services and DNS. Resources like Pods communicate with each other via cluster IPs and services.
HPA vs. VPA in Kubernetes:

HPA (Horizontal Pod Autoscaler): Scales the number of pods based on resource usage or custom metrics.
VPA (Vertical Pod Autoscaler): Adjusts resource requests and limits for pods based on usage.
Exposure to Helm with Kubernetes:

Helm is a package manager for Kubernetes that simplifies deploying and managing applications. Experience might include creating, customizing, and deploying Helm charts.
Connecting Master Node with Worker Node:

Communication is established through the Kubernetes API server, which worker nodes connect to for managing and scheduling pods.
Discriminating Master and Worker Nodes:

Master nodes control the cluster and manage scheduling, while worker nodes run the application workloads. They are identified by their roles and responsibilities within the cluster.
Endpoints in VPC:

VPC endpoints are virtual devices that allow private connections between VPCs and supported AWS services without needing public IP addresses.
Types of Endpoints:

Interface Endpoints: Use private IP addresses for communication.
Gateway Endpoints: Support S3 and DynamoDB with a gateway to the VPC.
VPC Peering:

VPC peering allows you to connect two VPCs so that resources in each can communicate with each other as if they are in the same network.
How VPC Peering Works:

VPC peering establishes a private connection between VPCs, allowing traffic to flow using private IPs and without traversing the internet.
Types of Elastic Load Balancers:

Application Load Balancer (ALB)
Network Load Balancer (NLB)
Gateway Load Balancer (GLB)
Difference Between ALB and NLB and Which is Best:

ALB: Best for HTTP/HTTPS traffic and advanced routing.
NLB: Best for TCP/UDP traffic and high performance.
The choice depends on your application needs.
Launch Configuration:

A launch configuration defines instance settings for Auto Scaling Groups, including the AMI, instance type, and configuration details.
Terraform Taint Command:

The terraform taint command marks a resource for recreation on the next apply, useful for forcing a resource to be rebuilt.
Terraform State File Storage:

State files can be stored locally or remotely. Remote storage options include AWS S3, Azure Blob Storage, or Terraform Cloud.
State File Missing:

If a state file is missing, you might need to recreate it manually or use Terraform’s state recovery commands. Ensuring regular backups can prevent data loss.
CI/CD Used:

Discuss the CI/CD tools and processes used in your organization, such as Jenkins, GitLab CI, or GitHub Actions, and how they fit into your development workflow.
Declarative Pipeline:

Declarative pipelines in Jenkins use a pipeline DSL (Domain-Specific Language) to define the pipeline structure and stages in a Jenkinsfile.
Declarative vs. Scripted Pipeline in Jenkins:

Declarative Pipeline: Uses a simplified syntax for defining pipelines with a focus on readability and structure.
Scripted Pipeline: Uses Groovy scripting for more flexibility but can be more complex.
Pipeline Type Used in Jenkins:

Discuss the type of pipeline used, such as declarative or scripted, and how it aligns with your project requirements.
Branching Strategy for Multibranch Pipeline:

Strategies include feature branching, GitFlow, or GitHub Flow, which help manage and organize multiple branches in a multibranch pipeline setup.
Handling Secrets in Jenkins Pipeline:

Use Jenkins credentials and environment variables to securely manage secrets. Ensure secrets are not exposed in logs or UI.
Multistaging in Docker:

Multistage builds allow you to create multiple intermediate images within a single Dockerfile to optimize the final image size and build efficiency.
/dev/run in Shell Script:

/dev/run is a virtual filesystem used for runtime data and temporary files in Linux. It is used by system services and applications to store runtime information.
Mounting Disks:

Steps include creating a filesystem, mounting the disk to a directory, updating /etc/fstab for persistent mounting, and verifying the mount.
Git Rebase: - Rebase is a Git command used to apply commits from one branch onto another. It rewrites commit history to create a linear sequence of commits.

Git Rebase vs. Merge: - Rebase: Applies commits from one branch onto another, creating a linear history. - Merge: Combines branches with a merge commit, preserving the branch history.

Exposure to ArgoCD: - ArgoCD is a declarative, GitOps continuous delivery tool for Kubernetes. Experience might include setting up and managing application deployments and syncing configurations with Git repositories.

What is ArgoCD?
ArgoCD is a declarative, GitOps continuous delivery tool for Kubernetes. It automates the deployment and management of applications on Kubernetes clusters by leveraging Git repositories as the source of truth for application configurations.

Key Features
Declarative Configuration:

ArgoCD uses a declarative approach where the desired state of applications is defined in Git repositories. This approach ensures that the actual state of applications in the cluster matches the desired state described in Git.
GitOps Workflow:

ArgoCD aligns with the GitOps principles by using Git as the single source of truth. Changes to application configurations are made in Git, and ArgoCD synchronizes these changes with the Kubernetes cluster.
Application Deployment:

Supports various deployment strategies including blue-green and canary deployments. It manages deployments using Kubernetes manifests, Helm charts, and Kustomize configurations.
Sync and Drift Detection:

Continuously monitors the cluster to detect and correct any deviations from the desired state defined in Git. It can automatically sync the cluster state or alert you to manual intervention.
Multi-Cluster Support:

Can manage and deploy applications across multiple Kubernetes clusters from a single ArgoCD instance, providing centralized control and visibility.
Web-Based UI and CLI:

Provides a web-based user interface for managing applications, viewing logs, and performing operations like rollouts and rollbacks. Also offers a CLI for command-line interactions.
Integration with Other Tools:

Integrates seamlessly with tools like Helm, Kustomize, and Jsonnet for application configuration management. Supports various authentication methods and RBAC policies.
Basic Workflow
Define Application Configurations:

Store your Kubernetes manifests, Helm charts, or Kustomize configurations in a Git repository. This repository serves as the source of truth for your application’s desired state.
Create ArgoCD Applications:

In ArgoCD, create an application resource that specifies the Git repository, the path to the configuration files, and the target Kubernetes cluster and namespace.
Sync Application:

ArgoCD syncs the application's state in the cluster with the state defined in the Git repository. It deploys new changes, updates resources, or rolls back to previous versions as needed.
Monitor and Manage:

Use the ArgoCD UI or CLI to monitor the health and status of applications, view detailed logs, and manage deployments. You can initiate syncs, rollbacks, and other operations directly from the interface.
Use Cases
Continuous Deployment:

Automates the deployment process, ensuring that changes in Git are automatically reflected in the Kubernetes cluster.
Application Rollback:

Provides mechanisms for rolling back to previous versions of applications if issues are detected, using Git history.
Multi-Cluster Management:

Enables centralized management of deployments across multiple Kubernetes clusters, simplifying operations and enhancing scalability.
Advantages
Consistency and Reliability:

Ensures that the state of applications in the cluster is always consistent with the state defined in Git.
Auditability:

Provides a complete audit trail of changes made to application configurations through Git commits.
Reduced Manual Intervention:

Minimizes the need for manual deployments and updates, reducing the risk of human errors.
Visibility:

Offers visibility into the deployment process and application status through its web-based UI.
By understanding these aspects of ArgoCD, you can effectively explain its role and benefits in a DevOps environment during an interview. If you need more specific details or examples, just let me know!

1.ls: List directory contents
2. cd: Change directory
3. pwd: Print working directory
4. mkdir: Create a directory
5. touch: Create a file
6. cp: Copy files and directories
7. mv: Move or rename files and directories
8. rm: Remove files and directories
9. find: Search for files and directories
10. grep: Search for patterns in files
11. cat: Concatenate and display files
12. less: View file contents page by page
13.head: Display the first lines of a file
14. tail: Display the last lines of a file
15. vi/vim: Text editor
16. nano: Text editor
17. tar: Archive and compress files
18. gzip: Compress files
19. gunzip: Decompress files
20. wget: Download files from the web
21. curl: Transfer data to or from a server
22. ssh: Secure shell remote login
23. scp: Securely copy files between hosts
24. chmod: Change file permissions
25. chown: Change file ownership
26. chgrp: Change group ownership
27. ps: Display running processes
28. top: Monitor system resources and processes
29. kill: Terminate processes
30. df: Display disk space usage
31. du: Estimate file and directory space usage
32. free: Display memory usage
33. uname: Print system information
34. ifconfig: Configure network interfaces
35. ping: Test network connectivity
36. netstat: Network statistics
37. iptables: Firewall administration
38. systemctl: Manage system services
39. journalctl: Query the system journal
40. crontab: Schedule cron jobs
41. useradd: Create a user account
42. passwd: Change user password
43. su: Switch user
44. sudo: Execute a command as another user
45. usermod: Modify user account
46. groupadd: Create a group
47. groupmod: Modify a group
48. id: Print user and group information
49. ssh-keygen: Generate SSH key pairs
50. rsync: Synchronize files and directories
51. diff: Compare files line by line
52. patch: Apply a patch to files
53. tar: Extract files from an archive
54. curl: Perform HTTP requests
55. nc: Netcat - networking utility
56. wget: Download files from the web
57. whois: Lookup domain registration details
58. dig: DNS lookup utility
59. sed: Stream editor for text manipulation
60. awk: Pattern scanning and processing language
61. sort: Sort lines in a text file
62. cut: Extract sections from lines of files
63. wc: Word, line, character, and byte count
64. tee: Redirect output to multiple files or commands
65. history: Command history
66. source: Execute commands from a file in the current shell
67. alias: Create command aliases
68. ln: Create links between files
69. uname: Print system information
70. lsof: List open files and processes
71. mkfs: Create a file system
72. mount: Mount a file system
73. umount: Unmount a file system
74. ssh-agent: Manage SSH keys in memory
75. grep: Search for patterns in files
76. tr: Translate characters
77. cut: Select portions of lines from files
78. paste: Merge lines of files
79. uniq: Report or omit repeated lines

1. How to Configure an Alarm in CloudWatch
Step-by-Step Process:

Create a CloudWatch Alarm:

Navigate to the CloudWatch console.
Go to the "Alarms" section and click "Create Alarm."
Choose a metric to base the alarm on (e.g., CPU utilization, error rates).
Select Metric and Conditions:

Select the namespace, metric name, and dimension.
Define the conditions (thresholds) that trigger the alarm (e.g., CPU usage > 80%).
Configure Actions:

Set up actions such as sending notifications (e.g., via SNS) or auto-scaling actions.
Configure the actions to occur when the alarm state is triggered.
Add a Name and Description:

Give your alarm a meaningful name and optional description.
Review and Create:

Review all settings and click "Create alarm" to finalize.
Use Case Example:

Setting an alarm to monitor high CPU usage on an EC2 instance to trigger an auto-scaling action or alert the team if the threshold is breached.
2. Writing a Terraform File to Create an EC2 Instance
Terraform Configuration Example:


provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  tags = {
    Name = "example-instance"
  }

  # Optional: User data to configure instance at launch
  user_data = <<-EOF
              #!/bin/bash
              echo "Hello, World!" > /home/ec2-user/hello.txt
              EOF
}
Explanation:

provider: Defines the AWS region.
resource "aws_instance": Creates an EC2 instance with specified AMI and instance type.
tags: Adds a name tag to the instance.
user_data: Optional script executed on instance launch.
3. What S3 Buckets Do
S3 Buckets:

Storage: Provide scalable object storage for any type of data.
Access Control: Allows setting permissions to control who can access the data.
Durability and Availability: S3 offers high durability (99.999999999%) and availability.
Versioning and Lifecycle Policies: Supports versioning and lifecycle management to manage data retention.
Use Case Example:

Storing application logs, backups, or static website assets.
4. What CloudTrail Does
AWS CloudTrail:

Logging: Records AWS API calls made on your account.
Monitoring: Provides visibility into user activity and API usage.
Compliance: Helps in auditing and compliance by tracking changes and access patterns.
Integration: Can be integrated with CloudWatch for alarms and notifications based on API activity.
5. How to Open Logs
CloudWatch Logs:

Navigate to the CloudWatch console.
Go to "Logs" to view log groups and streams.
Select the desired log group and stream to view the logs.
Example:

Accessing logs from an EC2 instance or Lambda function to troubleshoot issues.
6. Checking Build Issues in Jenkins
Steps:

Access Jenkins Console: Go to Jenkins dashboard and select the job.
View Build Logs: Click on the build number to view the build log for errors or issues.
Check Console Output: Look for error messages or failed steps in the console output.
Example:

Identifying issues related to missing dependencies or build script errors.
7. Checking Errors in Jenkins Pipeline
Steps:

Access Pipeline Logs: From Jenkins dashboard, go to the pipeline job and click on the failed build.
Review Stage Logs: Click on each stage to view detailed logs and errors.
Analyze Stack Traces: Look for stack traces or error messages to diagnose the issue.
Example:

Debugging issues in a Jenkins pipeline script or configuration.
8. How Terraform Knows Whether to Update or Create a Resource
Mechanism:

State File: Terraform maintains a state file that records the current state of resources.
Plan Execution: During terraform plan, Terraform compares the desired configuration (from HCL files) with the current state and identifies changes.
Actions: Terraform decides to create, update, or delete resources based on this comparison.
Example:

Modifying an EC2 instance type in the configuration results in Terraform updating the instance.
9. Can I Overwrite the State Log and Still Apply?
State File Management:

Direct Overwriting: Overwriting the state file directly is risky and generally not recommended. It can lead to inconsistencies.
Safe Approach: Use terraform import to bring existing resources under Terraform management or restore from backups.
10. Difference Between .tfvars and auto.tfvars
.tfvars: Custom variable files that can be used to set variables. Must be specified using the -var-file option in the terraform apply command.
auto.tfvars: Automatically loaded by Terraform if present in the working directory. Useful for default variable values.
11. Running Commands After Resource Creation
Using Provisioners:

local-exec: Executes commands locally on the machine running Terraform.
remote-exec: Executes commands on the resource after it is created, e.g., via SSH.
Example:


resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"

  provisioner "remote-exec" {
    inline = [
      "sudo apt-get update",
      "sudo apt-get install -y nginx"
    ]
  }
}
12. Different Types of Provisioners and Where Used
Types:

local-exec: Runs a command on the local machine.
remote-exec: Runs commands on the remote resource (e.g., SSH into an instance).
Usage Example:

local-exec: Running scripts or commands on your local machine, like generating files.
remote-exec: Installing software or configuring applications on a provisioned instance.
13. What if remote-exec Command Fails?
Behavior:

Resource State: If a remote-exec command fails, the resource itself is created, but the provisioning might be incomplete. Terraform will report the error, and the resource may be in a partially configured state.
Example:

If an nginx installation fails, the EC2 instance will be created but without nginx.
14. What Happens When remote-exec Command Runs Internally?
Mechanism:

SSH Connection: Terraform establishes an SSH connection to the resource.
Command Execution: Executes the commands as specified in the remote-exec block.
Output Handling: Captures the output and error messages.
15. Creating Multiple Resources of the Same Kind
Using Count or For_each:

Example with count:


resource "aws_instance" "example" {
  count = 3
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}
Example with for_each:


resource "aws_instance" "example" {
  for_each = var.instances

  ami           = each.value.ami
  instance_type = each.value.instance_type
}
16. Running Terraform in CI/CD
Integration Steps:

CI/CD Pipeline: Integrate Terraform commands into your CI/CD pipeline using tools like Jenkins, GitLab CI, or GitHub Actions.
Commands: Typically include terraform init, terraform plan, and terraform apply.
Example:


# Example GitHub Actions workflow
name: Terraform CI/CD

on:
  push:
    branches:
      - main

jobs:
  terraform:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3

      - name: Set Up Terraform
        uses: hashicorp/setup-terraform@v2

      - name: Terraform Init
        run: terraform init

      - name: Terraform Plan
        run: terraform plan

      - name: Terraform Apply
        run: terraform apply -auto-approve
17. Automatically Approve Terraform Changes
Command:


terraform apply -auto-approve
Explanation:

-auto-approve: Skips the confirmation prompt, applying changes immediately.
18. What is Heap Memory?
Heap Memory:

Definition: A type of memory used for dynamic memory allocation where variables are allocated and freed as needed.
Sharing: Generally, heap memory is not shared between processes. Each process has its own heap space.
19. Stages in Git
Stages:

Working Directory: Where you make changes to files.
Staging Area: Where you prepare files for the next commit.
Repository: Where commits are stored.
Commands:

git add: Moves changes to the staging area.
git commit: Moves changes from the staging area to the repository.
20. Undo Changes in Git
Commands:

git checkout -- <file>: Discards changes in the working directory.
git reset HEAD <file>: Unstages changes in the staging area.
git revert <commit>: Creates a new commit that undoes changes from a previous commit.
21. Checking if a File is Tracked
Command:

sh
Copy code
git ls-files --error-unmatch <file>
Explanation:

Tracked: If the file is listed, it is tracked by Git.
22. Difference Between git revert and git reset
git revert:

Purpose: Creates a new commit that undoes changes from a previous commit.
git reset:

Purpose: Moves the current branch to a specified state, optionally modifying the staging area and working directory.
23. How git revert and git reset Work After Commit
git revert:

Operation: Creates a new commit that reverses changes made by a previous commit.
git reset:

Operation: Moves the HEAD pointer to a specified commit and modifies the staging area and working directory depending on the reset mode (--soft, --mixed, --hard).
24. Committing Only Specific Files
Command:


git add <file1> <file2>
git commit -m "Commit message"
Explanation:

Selective Commit: Use git add to stage specific files before committing.
25. Switching Branches with Uncommitted Changes
Problem:

Uncommitted Changes: Git prevents switching branches if there are uncommitted changes that conflict with the target branch.
Solution:

Stash Changes: Use git stash to save changes temporarily and then switch branches.
26. Jenkins Connection to Worker Nodes
Mechanism:

Jenkins Master: Manages jobs and distributes tasks.
Worker Nodes: Connect to the Jenkins master via agents (either via SSH or JNLP).
Configuration:

Manage Nodes: Configure nodes in Jenkins under "Manage Jenkins" -> "Manage Nodes and Clouds."
27. Troubleshooting Command Not Found in Jenkins Pipeline
Steps:

Check Path: Ensure the command is installed and available in the PATH.
Install Dependencies: Ensure all necessary dependencies are installed on the Jenkins worker.
Pipeline Configuration: Verify that the pipeline configuration is correct and points to the right environment.
28. Container Not Visible After Running Docker
Troubleshooting Steps:

Check Containers: Run docker ps -a to list all containers, including stopped ones.
Logs: Check container logs using docker logs <container_id>.
Start Container: Ensure the container is running with docker start <container_id> if it was stopped.
29. Too Many Requests Errors for Docker Container
Troubleshooting Steps:

Rate Limits: Check if you’re hitting rate limits on Docker Hub or other registries.
Retry Mechanism: Implement retry logic or check your usage patterns.
Network Issues: Verify network connectivity and proxy settings.
30. Creating a Docker Image with No Internet Connectivity
Steps:

Pre-download Dependencies: Download all required dependencies before the image build.
Use Local Cache: Ensure all necessary files are included in the build context or use a local repository.
31. Authenticating to Docker Hub
Command:


docker login
Explanation:

Interactive Login: Prompts for Docker Hub credentials.
Alternative: Use environment variables for automated scripts (DOCKER_USERNAME and DOCKER_PASSWORD).
32. No Internet Inside Docker Container
Troubleshooting Steps:

Network Configuration: Check Docker network settings and container network mode.
DNS Settings: Verify DNS settings within the container.
33. Pod Stuck in Pending State
Troubleshooting Steps:

Check Events: Use kubectl describe pod <pod_name> to view events and reasons for the pending state.
Resource Requests: Ensure sufficient resources (CPU/memory) are available.
Node Conditions: Verify node status and availability.
34. Commands to Check Pod Status
Commands:

kubectl get pods: Lists all pods and their statuses.
kubectl describe pod <pod_name>: Provides detailed information about a specific pod.
kubectl logs <pod_name>: Shows logs for a specific pod.
35. Pod Lifecycle
Stages:

Pending: Pod is being scheduled.
Running: Pod is running and containers are operational.
Succeeded: Pod has completed successfully.
Failed: Pod has failed.
Unknown: State cannot be determined.
36. Kubernetes Architecture
Components:

Master Node: Manages the cluster and includes the API server, scheduler, controller manager, and etcd.
Worker Nodes: Run the applications and contain the kubelet, kube-proxy, and container runtime.
37. Readiness and Liveness Probes
Readiness Probe:

Purpose: Checks if the application is ready to accept traffic.
Impact: A pod will not receive traffic until the readiness probe succeeds.
Liveness Probe:

Purpose: Checks if the application is alive and running.
Impact: If the liveness probe fails, Kubernetes will restart the container.
38. Types of Secrets in Kubernetes
Types:

Opaque: Default secret type for arbitrary user-defined data.
docker-registry: Used for storing Docker registry credentials.
Differences:

Opaque Secrets: Can store any key-value data.
docker-registry Secrets: Specifically for Docker registry credentials.
39. Example of Digging into a Complex Problem
Example:

Scenario: Debugging a complex deployment issue in a multi-tier application.
Approach: Analyzed logs, reviewed deployment scripts, and consulted team members to identify and resolve a misconfiguration causing deployment failures.
40. Data from Grafana
Data Types:

Metrics: Performance and operational metrics from various data sources.
Logs: Aggregated logs visualized in dashboards.
Alerts: Alert conditions based on metrics or log data.
41. Separating Infra for Different Environments
Approach:

Use Separate Accounts or VPCs: For isolation between environments like development, test, and production.
Terraform Workspaces: Manage different environments within the same configuration.
Environment-Specific Configurations: Use variable files or modules to differentiate resources based on the environment.
Protection Measures:

Access Controls: Implement strict access policies and permissions.
Network Segmentation: Use VPCs and security groups to control access.

Linux Questions
What is LVM Linux and Why Use LVM?

LVM (Logical Volume Manager):

Definition: A system of managing logical volumes or filesystems in Linux, providing flexibility in disk management.
Benefits:
Dynamic Volume Management: Allows resizing of logical volumes without unmounting.
Snapshot Support: Enables taking snapshots of volumes for backup or testing.
Volume Grouping: Aggregates multiple physical volumes into a single logical volume group.
/data Directory Full on LVM: How to Resolve This?

Steps:

Check Current Usage:
sh
Copy code
df -h /data
Extend Logical Volume:
sh
Copy code
lvextend -L +<size> /dev/<vg_name>/<lv_name>
Resize Filesystem:
sh
Copy code
resize2fs /dev/<vg_name>/<lv_name>
Verify:
sh
Copy code
df -h /data
Difference Between mkfs and resize2fs:

mkfs: Used to create a filesystem on a partition or volume.
sh
Copy code
mkfs.ext4 /dev/<device>
resize2fs: Used to resize an ext2/ext3/ext4 filesystem to match the size of its partition or logical volume.
sh
Copy code
resize2fs /dev/<device>
PV Failing or Faulty Issue Resolution:

Steps:

Check PV Status:
sh
Copy code
pvs
Examine Details:
sh
Copy code
pvdisplay /dev/<device>
Repair or Replace PV: Depending on the issue, you might need to replace the faulty PV and recreate or restore the volume group from backups.
Creating VG Directly on Linux OS:

Answer: Yes, you can create a Volume Group (VG) directly using LVM tools. Example:

sh
Copy code
vgcreate <vg_name> /dev/<pv_device>
Find Files Starting with Prefix in /data Directory:

Command:

sh
Copy code
ls /data/ample.*
Difference Between du and df Commands:

du (Disk Usage): Shows the disk space used by files and directories.
sh
Copy code
du -sh /path/to/dir
df (Disk Free): Shows available disk space on filesystems.
sh
Copy code
df -h
*Find All Errors in Log Files with .log Extension:

Command:

sh
Copy code
grep -i error /path/to/logs/*.log
Booting Sequence of a Linux Operating System:

Sequence:

BIOS/UEFI: Initializes hardware and performs POST.
Bootloader: Loads the kernel (e.g., GRUB).
Kernel Initialization: Loads the Linux kernel and initializes the system.
Init/Systemd: Starts system services and initializes user-space processes.
Login Prompt: Provides a login interface for users.
Purpose of the Kernel:

Answer: The kernel is the core part of the operating system that manages hardware resources, provides system calls, and facilitates communication between hardware and software.

What is initrd:

Answer: initrd (Initial RAM Disk) is a temporary root filesystem used during the boot process to load necessary drivers and modules before the real root filesystem is mounted.

PID of init:

Answer: The PID of init is typically 1. It's the first process started by the kernel.

Sticky Bit (t and T):

t: Indicates a sticky bit is set, meaning only the file owner or root can delete or rename the file.
T: Sticky bit is set but the file is not writable by anyone.
Usage: Commonly used on directories like /tmp to prevent users from deleting files owned by others.
w Command:

Command:

sh
Copy code
w
jcpu: Total CPU time used by all processes in the current user's terminal.
pcpu: CPU time used by the current process.
Mount Directory Device Busy Error:

Troubleshooting Steps:

Check for Open Files: Use lsof to list open files in the mount point.
sh
Copy code
lsof +D /mount/point
Check for Active Processes: Ensure no processes are using the mount point.
sh
Copy code
fuser -m /mount/point
Permission Denied in /data Directory:

Possible Reasons:

Filesystem Permissions: Check ownership and permissions of the /data directory.
sh
Copy code
ls -ld /data
SELinux/AppArmor: Verify if security modules are blocking access.
What is an Inode in Linux Operating System?

Answer: An inode is a data structure on a filesystem that stores metadata about a file or directory (e.g., size, permissions, and location on disk).

Inode Number for Soft Link:

Answer: The inode number for a soft link is different from the inode of the target file. The soft link has its own inode.

Creating a Soft Link in Linux:

Command:

sh
Copy code
ln -s /path/to/original /path/to/softlink
How to Roll Back a Package:

Using Package Managers:

For RPM-based Systems (e.g., CentOS, RHEL):
sh
Copy code
yum history rollback <transaction_id>
For Debian-based Systems (e.g., Ubuntu):
sh
Copy code
apt-get install <package>=<version>
DevOps Questions
What is Git Rebase?

Answer: Git rebase is a command used to integrate changes from one branch onto another. It rewrites commit history to apply changes from the current branch on top of another branch, creating a linear history.

Command:

sh
Copy code
git rebase <branch>
Components of a Dockerfile:

FROM: Specifies the base image.
RUN: Executes commands to build the image.
COPY / ADD: Copies files or directories into the image.
CMD: Sets the default command to run when the container starts.
ENTRYPOINT: Configures the container to run as an executable.
EXPOSE: Declares ports to be exposed.
ENV: Sets environment variables.
Difference Between ENTRYPOINT and CMD:

ENTRYPOINT: Defines the main executable for the container. It is always executed.
CMD: Provides default arguments for the ENTRYPOINT. If ENTRYPOINT is not set, CMD will be executed as the main command.
Difference Between ADD and COPY Commands:

COPY: Copies files or directories from the build context to the image. It is simpler and preferred for copying files.
ADD: Similar to COPY but can also handle URLs and extract tar archives. Use ADD only when you need these additional features.
Implementing Networking in Docker:

Types of Networks:

Bridge Network: Default network for containers.
Host Network: Shares the host's network stack.
Overlay Network: Used for multi-host networking (requires Docker Swarm).
Macvlan Network: Assigns a MAC address to a container for direct network access.
Command to Create a Network:

sh
Copy code
docker network create <network_name>
Ensuring Security of Pods in Kubernetes:

Use RBAC: Define roles and permissions for access control.
Network Policies: Restrict communication between pods.
Pod Security Policies: Enforce security constraints.
Image Scanning: Regularly scan images for vulnerabilities.
What is a Multistage Pipeline in Jenkins?

Answer: A multistage pipeline in Jenkins is a pipeline with multiple stages defined in the Jenkinsfile. Each stage can perform different tasks (e.g., build, test, deploy) and helps in organizing and managing complex workflows.

Example:

groovy
Copy code
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Build steps
            }
        }
        stage('Test') {
            steps {
                // Test steps
            }
        }
        stage('Deploy') {
            steps {
                // Deploy steps
            }
        }
    }
}
How to Delete an Untagged Docker Image?

Command:

sh
Copy code
docker image prune
Explanation: This command removes all dangling (untagged) images.

1. Migration from On-Premises/Cloud to Cloud
Steps for Migration:

Assessment:

Inventory: Catalog all applications, data, and dependencies.
Assessment Tools: Use cloud provider tools or third-party solutions to assess compatibility and estimate costs.
Planning:

Strategy: Choose a migration strategy (lift-and-shift, replatforming, refactoring).
Timeline: Develop a timeline with milestones.
Resources: Allocate necessary resources (team, tools, budget).
Design:

Architecture: Design the target architecture in the cloud.
Security: Plan for security and compliance requirements.
Networking: Design network layout and connectivity.
Testing:

Proof of Concept: Test migration with a small subset of data and applications.
Performance Testing: Ensure performance meets expectations.
Migration:

Data Transfer: Use tools like AWS Data Migration Service or Azure Data Box for data transfer.
Application Migration: Migrate applications, either manually or using automated tools.
Validation:

Testing: Validate functionality and performance.
Monitoring: Set up monitoring and alerting.
Optimization:

Cost Optimization: Review and optimize cloud costs.
Performance Tuning: Adjust resources based on performance metrics.
2. Disaster Recovery Strategies
High Availability and Reliability:

Redundancy:

Multiple Data Centers: Use multiple availability zones or regions.
Load Balancing: Distribute traffic across multiple instances.
Backup:

Regular Backups: Schedule automated backups of critical data and configurations.
Backup Testing: Regularly test backups to ensure they are valid and restorable.
Failover:

Automated Failover: Use tools and services that support automatic failover (e.g., AWS Route 53, Azure Traffic Manager).
Manual Failover Procedures: Document and test manual failover procedures.
Monitoring and Alerts:

Continuous Monitoring: Implement robust monitoring to detect issues early.
Alerts: Set up alerts for critical events and anomalies.
Disaster Recovery Plan:

Documented Plan: Create a comprehensive disaster recovery plan outlining steps to recover from various types of failures.
Regular Drills: Conduct regular disaster recovery drills to ensure readiness.
Planning for 99.99% Availability:

SLA Requirements: Understand and align with the Service Level Agreements (SLAs) of your cloud providers.
High-Availability Architectures: Implement architectures that support high availability and fault tolerance.
3. Building an Application with Frontend, Kubernetes, and Databases
Steps:

Frontend Application:

Develop/Deploy: Build the web application and deploy it to a hosting environment (e.g., Azure App Service, AWS S3 with CloudFront).
Kubernetes Backend:

Cluster Setup: Set up a Kubernetes cluster (e.g., using EKS on AWS or AKS on Azure).
Deployment: Deploy backend services and APIs using Kubernetes Deployments.
Service Exposure: Use Kubernetes Services to expose the backend services.
Database Setup:

Azure SQL or Amazon RDS: Set up and configure your database.
Connectivity: Ensure secure connectivity between your Kubernetes cluster and the database.
API Gateway/Load Balancer:

API Gateway: Configure API Gateway for managing APIs (e.g., AWS API Gateway, Azure API Management).
Load Balancer: Set up a Load Balancer to distribute traffic to the Kubernetes cluster.
Networking:

VPC/Network Configuration: Configure networking to ensure proper communication between frontend, backend, and database.
Security Groups/Firewalls: Implement security groups or firewall rules to secure network traffic.
Troubleshooting:

Logs and Monitoring: Use logging and monitoring tools to troubleshoot issues.
Network Tools: Use tools like kubectl, curl, and traceroute for network troubleshooting.
4. Adapter Service vs. Normal Services in Kubernetes
Adapter Service:

Purpose: Adapter services act as intermediaries or adaptors between different systems or services.
Use Case: Used for integrating with external systems or translating between different service interfaces.
Normal Services:

Purpose: Provide access to a set of Pods within a Kubernetes cluster.
Use Case: Load balance traffic to Pods, expose application endpoints.
5. Mitigating S3 Bucket Vulnerabilities
Strategies:

Access Control:

Bucket Policies: Implement fine-grained bucket policies to control access.
IAM Roles: Use IAM roles and policies to restrict access.
Encryption:

Server-Side Encryption: Enable server-side encryption with S3 (e.g., SSE-S3, SSE-KMS).
Client-Side Encryption: Encrypt data before uploading to S3.
Backup and Replication:

Versioning: Enable versioning to protect against accidental deletions.
Replication: Use cross-region replication (CRR) or same-region replication (SRR) for redundancy.
Monitoring and Auditing:

CloudTrail: Use AWS CloudTrail to monitor and log access requests.
S3 Access Logs: Enable access logging for bucket activity.
6. Zero Touch CI/CD Automation
Concept:

Automated Pipelines: Fully automated CI/CD pipelines that require minimal manual intervention.
Infrastructure as Code: Use tools like Terraform or CloudFormation to provision and manage infrastructure.
Automated Testing: Integrate automated tests into the pipeline to ensure quality.
Steps:

Version Control Integration: Integrate with version control systems (e.g., Git).
Build Automation: Automate builds using CI tools (e.g., Jenkins, GitLab CI).
Automated Testing: Run tests automatically on each build.
Deployment Automation: Automate deployments to various environments.
Monitoring and Feedback: Implement monitoring and feedback loops to detect issues and improve the process.
7. Ansible: Templates, Roles, Handlers
Templates:

Purpose: Used to create configuration files from a template with dynamic content.
Example:
yaml
Copy code
- name: Template a file
  template:
    src: template.j2
    dest: /etc/myconfig.conf
Roles:

Purpose: Encapsulate tasks, handlers, and variables into reusable units.
Structure:
markdown
Copy code
roles/
  myrole/
    tasks/
    handlers/
    templates/
    vars/
Usage:
yaml
Copy code
- name: Include role
  include_role:
    name: myrole
Handlers:

Purpose: Define actions that are triggered by other tasks.
Example:
yaml
Copy code
- name: Restart service
  service:
    name: myservice
    state: restarted
  listen: "Restart myservice"
8. Terraform Concepts
Workspaces:

Purpose: Allow multiple states to be managed concurrently.
Command:
sh
Copy code
terraform workspace new <workspace_name>
Data Sources:

Purpose: Fetch data from external sources to use in configurations.
Example:
hcl
Copy code
data "aws_ami" "latest" {
  most_recent = true
  owners = ["amazon"]
}
Functions:

Purpose: Perform operations in configuration files.
Example:
hcl
Copy code
output "instance_ip" {
  value = aws_instance.example.private_ip
}
Modules:

Purpose: Encapsulate configurations into reusable units.
Usage:
hcl
Copy code
module "network" {
  source = "./modules/network"
}
tfstate File Corruption and Repair:

Steps:
Backup State: Always keep a backup.
Check for Corruption: Use terraform validate and terraform plan.
Repair: Restore from backup or manually edit the state file.
Migration from AWS to GCP/Azure:

Export Configuration: Use Terraform state files and export configurations.
Recreate Infrastructure: Apply configurations to the target cloud provider using appropriate Terraform modules and resources.
9. Python or Shell Automation Questions
Common Topics:

Python:

Scripting: Writing scripts to automate tasks (e.g., file operations, API interactions).
Libraries: Using libraries like requests, pandas, or boto3.
Shell Scripting:

Basic Commands: Using commands like awk, sed, grep, and find.
Automation: Writing scripts to automate routine tasks.
Example Python Script:

python
Copy code
import boto3

s3 = boto3.client('s3')
response = s3.list_buckets()
print("Buckets:")
for bucket in response['Buckets']:
    print(f'

GitHub commands.

1. 𝗴𝗶𝘁 𝗶𝗻𝗶𝘁: Initializes a new Git repository in the current directory.
2. 𝗴𝗶𝘁 𝗰𝗹𝗼𝗻𝗲 [𝘂𝗿𝗹]: Clones a repository into a new directory.
3. 𝗴𝗶𝘁 𝗮𝗱𝗱 [𝗳𝗶𝗹𝗲]: Adds a file or changes in a file to the staging area.
4. 𝗴𝗶𝘁 𝗰𝗼𝗺𝗺𝗶𝘁 -𝗺 "[𝗺𝗲𝘀𝘀𝗮𝗴𝗲]": Records changes to the repository with a descriptive message.
5. 𝗴𝗶𝘁 𝗽𝘂𝘀𝗵: Uploads local repository content to a remote repository.
6. 𝗴𝗶𝘁 𝗽𝘂𝗹𝗹: Fetches changes from the remote repository and merges them into the local branch.
7. 𝗴𝗶𝘁 𝘀𝘁𝗮𝘁𝘂𝘀: Displays the status of the working directory and staging area.
8. 𝗴𝗶𝘁 𝗯𝗿𝗮𝗻𝗰𝗵: Lists all local branches in the current repository.
9. 𝗴𝗶𝘁 𝗰𝗵𝗲𝗰𝗸𝗼𝘂𝘁 [𝗯𝗿𝗮𝗻𝗰𝗵]: Switches to the specified branch.
10. 𝗴𝗶𝘁 𝗺𝗲𝗿𝗴𝗲 [𝗯𝗿𝗮𝗻𝗰𝗵]: Merges the specified branch's history into the current branch.
11. 𝗴𝗶𝘁 𝗿𝗲𝗺𝗼𝘁𝗲 -𝘃: Lists the remote repositories along with their URLs.
12. 𝗴𝗶𝘁 𝗹𝗼𝗴: Displays commit logs.
13. 𝗴𝗶𝘁 𝗿𝗲𝘀𝗲𝘁 [𝗳𝗶𝗹𝗲]: Unstages the file, but preserves its contents.
14. 𝗴𝗶𝘁 𝗿𝗺 [𝗳𝗶𝗹𝗲]: Deletes the file from the working directory and stages the deletion.
15. 𝗴𝗶𝘁 𝘀𝘁𝗮𝘀𝗵: Temporarily shelves (or stashes) changes that haven't been committed.
16. 𝗴𝗶𝘁 𝘁𝗮𝗴 [𝘁𝗮𝗴𝗻𝗮𝗺𝗲]: Creates a lightweight tag pointing to the current commit.
17. 𝗴𝗶𝘁 𝗳𝗲𝘁𝗰𝗵 [𝗿𝗲𝗺𝗼𝘁𝗲]: Downloads objects and refs from another repository.
18. 𝗴𝗶𝘁 𝗺𝗲𝗿𝗴𝗲 --𝗮𝗯𝗼𝗿𝘁: Aborts the current conflict resolution process, and tries to reconstruct the pre-merge state.
19. 𝗴𝗶𝘁 𝗿𝗲𝗯𝗮𝘀𝗲 [𝗯𝗿𝗮𝗻𝗰𝗵]: Reapplies commits on top of another base tip, often used to integrate changes from one branch onto another cleanly.
20. 𝗴𝗶𝘁 𝗰𝗼𝗻𝗳𝗶𝗴 --𝗴𝗹𝗼𝗯𝗮𝗹 𝘂𝘀𝗲𝗿.𝗻𝗮𝗺𝗲 "[𝗻𝗮𝗺𝗲]" 𝗮𝗻𝗱 𝗴𝗶𝘁 𝗰𝗼𝗻𝗳𝗶𝗴 --𝗴𝗹𝗼𝗯𝗮𝗹 𝘂𝘀𝗲𝗿.𝗲𝗺𝗮𝗶𝗹 "[𝗲𝗺𝗮𝗶𝗹]": Sets the name and email to be used with your commits.
21. 𝗴𝗶𝘁 𝗱𝗶𝗳𝗳: Shows changes between commits, commit and working tree, etc.
22. 𝗴𝗶𝘁 𝗿𝗲𝗺𝗼𝘁𝗲 𝗮𝗱𝗱 [𝗻𝗮𝗺𝗲] [𝘂𝗿𝗹]: Adds a new remote repository.
23. 𝗴𝗶𝘁 𝗿𝗲𝗺𝗼𝘁𝗲 𝗿𝗲𝗺𝗼𝘃𝗲 [𝗻𝗮𝗺𝗲]: Removes a remote repository.
24. 𝗴𝗶𝘁 𝗰𝗵𝗲𝗰𝗸𝗼𝘂𝘁 -𝗯 [𝗯𝗿𝗮𝗻𝗰𝗵]: Creates a new branch and switches to it.
25. 𝗴𝗶𝘁 𝗯𝗿𝗮𝗻𝗰𝗵 -𝗱 [𝗯𝗿𝗮𝗻𝗰𝗵]: Deletes the specified branch.
26. 𝗴𝗶𝘁 𝗽𝘂𝘀𝗵 --𝘁𝗮𝗴𝘀: Pushes all tags to the remote repository.
27. 𝗴𝗶𝘁 𝗰𝗵𝗲𝗿𝗿𝘆-𝗽𝗶𝗰𝗸 [𝗰𝗼𝗺𝗺𝗶𝘁]: Picks a commit from another branch and applies it to the current branch.
28. 𝗴𝗶𝘁 𝗳𝗲𝘁𝗰𝗵 --𝗽𝗿𝘂𝗻𝗲: Prunes remote tracking branches no longer on the remote.
29. 𝗴𝗶𝘁 𝗰𝗹𝗲𝗮𝗻 -𝗱𝗳: Removes untracked files and directories from the working directory.
30. 𝗴𝗶𝘁 𝘀𝘂𝗯𝗺𝗼𝗱𝘂𝗹𝗲 𝘂𝗽𝗱𝗮𝘁𝗲 --𝗶𝗻𝗶𝘁 --𝗿𝗲𝗰𝘂𝗿𝘀𝗶𝘃𝗲: Initializes and updates submodules recursively.


1. GIT Stash
What is GIT Stash?

Definition: Git stash is a command used to temporarily save changes in your working directory that are not yet ready to be committed. It allows you to switch branches or pull changes without committing incomplete work.
Usage: git stash saves your local modifications, while git stash pop or git stash apply restores them.
2. Branching Strategy
What is a Branching Strategy?

Definition: A branching strategy is a set of rules or guidelines used to manage and organize branches in a version control system like Git.
Common Strategies:
Git Flow: Features, releases, and hotfix branches.
GitHub Flow: Main branch and feature branches.
GitLab Flow: Merges features directly into master or production.
3. Discarding Changes in Working Directory
What is the command to discard changes in the working directory?

Command: git checkout -- <file> to discard changes in a specific file or git reset --hard to discard all changes and reset the working directory to the last commit.
4. Debugging Exited Containers
How do you debug an exited container?

Steps:
Check Logs: Use docker logs <container_id> to view the logs of the exited container.
Inspect Container: Use docker inspect <container_id> to check container configuration and errors.
Re-run Container: If needed, re-run the container interactively to debug issues.
5. Executing Jobs in Jenkins in Parallel
How do you execute jobs parallelly in Jenkins?

Method: Use the Pipeline plugin to define parallel stages within a Jenkinsfile. Example:
groovy
Copy code
pipeline {
    stages {
        stage('Build') {
            parallel {
                stage('Job 1') {
                    steps {
                        echo 'Running Job 1'
                    }
                }
                stage('Job 2') {
                    steps {
                        echo 'Running Job 2'
                    }
                }
            }
        }
    }
}
6. Maven Lifecycle
What is the Maven Lifecycle?

Definition: Maven defines a standard lifecycle with a set of phases to build and manage projects.
Phases:
default: compile, test, package, verify, install, deploy
clean: pre-clean, clean, post-clean
site: pre-site, site, post-site, site-deploy
7. Upgrading Jenkins
How do you upgrade Jenkins?

Method:
Backup Jenkins: Backup the Jenkins home directory.
Update Jenkins: Download the latest Jenkins WAR file from the official website.
Restart Jenkins: Replace the old WAR file with the new one and restart Jenkins.
8. Parameterized Job in Jenkins
What is a Parameterized Job in Jenkins?

Definition: A parameterized job allows users to pass parameters to a Jenkins job, enabling dynamic builds. Parameters can be string, boolean, or choice types.
9. Docker Swarm
What is Docker Swarm?

Definition: Docker Swarm is Docker's native clustering and orchestration tool that allows you to manage a cluster of Docker nodes as a single virtual system.
10. Handling Code in Nexus
How do you handle code in Nexus?

Method:
Repository Management: Store and manage artifacts such as Maven, npm, and Docker images.
Access Control: Configure access controls and permissions.
Cleanup Policies: Implement policies to manage artifact retention.
11. Managing Space Issues in Jenkins Server
How do you manage space issues in the Jenkins server?

Methods:
Delete Old Builds: Remove old build artifacts and logs.
Cleanup Plugins: Use plugins like Disk Cleanup or workspace cleanup.
Increase Disk Space: Add more storage if necessary.
12. Multibranch Project in Jenkins
What is a Multibranch Project in Jenkins?

Definition: A Multibranch Pipeline project automatically creates a Jenkins job for each branch in your repository, allowing Jenkins to build branches as they are created or updated.
13. Securing the Jenkins Server
How do you secure the Jenkins server?

Methods:
Authentication: Use strong authentication mechanisms.
Authorization: Implement role-based access control.
SSL: Use HTTPS for secure communication.
Regular Updates: Keep Jenkins and plugins up to date.
14. Managing GitHub Roles
How do you manage GitHub roles?

Method:
Collaborators: Add collaborators with specific access levels (read, write, admin).
Teams: Use GitHub teams for managing permissions across multiple repositories.
15. NULL Resource in Terraform
What is a NULL resource in Terraform?

Definition: A NULL resource is a placeholder used to execute actions that don't fit into other resource types, often used with provisioners for custom scripts.
16. Terraform fmt
What is Terraform fmt?

Definition: terraform fmt is a command that formats Terraform configuration files to a canonical format and style.
17. Snowball
What is Snowball?

Definition: AWS Snowball is a data transfer service that uses secure appliances to transfer large amounts of data into and out of AWS.
18. Managing Credentials in Terraform
How do you manage credentials in Terraform?

Method:
Environment Variables: Use environment variables to pass credentials.
Terraform Vault Provider: Store and manage sensitive data using HashiCorp Vault.
19. Code Deploy in AWS
What is CodeDeploy in AWS?

Definition: AWS CodeDeploy is a service that automates the deployment of applications to EC2 instances, Lambda functions, and on-premises servers.
20. Attaching EBS Volume to Multiple EC2 Instances
Can you attach a single EBS volume to multiple EC2 instances at the same time?

Answer: No, EBS volumes can only be attached to a single EC2 instance at a time. Use EFS for shared file storage.
21. Multiple FROM in Dockerfile
Can you use Multiple FROM in Dockerfile?

Answer: Yes, you can use multiple FROM statements in a Dockerfile to create multi-stage builds, optimizing images by reducing their size.
22. Dockerfile User
Dockerfile runs as which user?

Answer: By default, Dockerfile commands run as the root user. You can specify a different user using the USER directive.
23. Passing Arguments to Dockerfile
How can we pass an argument to Dockerfile?

Method:
ARG Directive: Define arguments in the Dockerfile and pass them during build.
dockerfile
Copy code
ARG MY_ARG
RUN echo $MY_ARG
24. Deployment Strategies
What are deployment strategies?

Types:
Blue-Green Deployment: Switch traffic between two environments.
Canary Deployment: Gradually release changes to a small subset of users.
Rolling Update: Update instances incrementally.
25. Application Load Balancer
What is an Application Load Balancer?

Definition: An Application Load Balancer (ALB) distributes incoming application traffic across multiple targets, such as EC2 instances, based on content.
26. Kubernetes Architecture
What is Kubernetes architecture?

Components:
Master Node: Manages the Kubernetes cluster.
Worker Nodes: Run containerized applications.
Components: API server, etcd, scheduler, controller manager, kubelet, kube-proxy.
27. Fargate Service in AWS
What is Fargate service in AWS?

Definition: AWS Fargate is a serverless compute engine for containers that allows you to run containers without managing the underlying infrastructure.
28. Register Targets in Ansible
What are Register targets in Ansible?

Definition: register is used to store the result of a task in a variable, which can be used in later tasks.
yaml
Copy code
- name: Run a command
  command: /bin/echo hello
  register: command_result
29. Pulling Artifacts from Nexus
How do you pull artifacts from Nexus?

Method:
Using CLI: Use tools like curl or wget with Nexus REST API.
Maven: Configure your Maven settings.xml to point to the Nexus repository.
30. Accessing S3 Bucket Privately
How to access the S3 bucket privately?

Method:
VPC Endpoints: Use VPC endpoints to access S3 within a VPC.
IAM Policies: Ensure proper IAM policies are in place.
31. NAT Instance vs. NAT Gateway
What is the difference between a NAT instance and a NAT gateway?

NAT Instance:

Management: User-managed instance.
Scalability: Requires manual scaling and management.
NAT Gateway:

Management: Fully managed by AWS.
Scalability: Automatically scales and highly available.
32. Restricting IPs Accessing EC2 Instances
How can you restrict particular IPs accessing EC2 instances?

Method:
Security Groups: Configure inbound rules in security groups to allow specific IP addresses.
Network ACLs: Use network ACLs for broader network access control.
33. VPC Peering
What is VPC Peering?

Definition: VPC Peering allows you to connect two VPCs in the same or different AWS accounts, enabling them to communicate as if they are within the same network.
34. Transit Gateway
What is a Transit Gateway?

Definition: AWS Transit Gateway is a network transit hub that connects VPCs and on-premises networks through a central gateway.
35. Types of Autoscaling
What are the types of autoscaling?

Types:
EC2 Auto Scaling: Automatically adjust the number of EC2 instances.
Application Auto Scaling: Scale other AWS resources like ECS services, DynamoDB tables, etc.
36. Load Balancer for DDOS Protection
To prevent DDOS attacks, which load balancer is used?

Answer: AWS Shield provides DDOS protection, and AWS Global Accelerator or Application Load Balancer (ALB) can help with traffic distribution and resilience.
37. Sticky Session
What is a sticky session?

Definition: Sticky sessions (or session affinity) ensure that requests from a user are always routed to the same instance in a load-balanced environment.
38. Lambda
What is Lambda?

Definition: AWS Lambda is a serverless computing service that runs code in response to events and automatically manages the compute resources for you.
39. Managing tfstate File in Terraform
How do you manage tfstate file in Terraform?

Methods:
Remote Backend: Store the state file in a remote backend like S3 with state locking using DynamoDB.
Backup: Regularly back up the state file to prevent data loss.
40. Creating Multiple EC2 Instances in Terraform
How do you create multiple EC2 instances in Terraform?

Example:
hcl
Copy code
resource "aws_instance" "example" {
  count = 3
  ami = "ami-123456"
  instance_type = "t2.micro"
}
41. Terraform Behavior with New AWS Service
AWS has released a new service, how does Terraform behave?

Answer: Terraform may not immediately support new AWS services. You can check the Terraform AWS Provider documentation for updates or contribute to the provider’s development.
42. Uncommit Changes in GitHub
How do you uncommit changes that have already been pushed to GitHub?

Method: Use git revert to create a new commit that undoes the changes. For more drastic measures, use git reset and force-push (with caution).
43. Difference Between git pull and git fetch
What is the difference between git pull and git fetch?

git fetch: Downloads changes from the remote repository but doesn’t merge them into your local branch.
git pull: Downloads changes and merges them into your current branch.
44. Jenkins File
What is a Jenkins File?

Definition: A Jenkinsfile is a text file that contains the definition of a Jenkins pipeline. It is used to define the build, test, and deployment processes.
45. Shared Libraries in Jenkins
What are Shared Libraries in Jenkins?

Definition: Shared Libraries are reusable components stored in a separate repository that can be used across multiple Jenkins pipelines to promote code reuse.
46. Docker Networking
What is Docker Networking?

Definition: Docker networking allows containers to communicate with each other and with the outside world. Docker supports several network drivers like bridge, host, and overlay.
47. Trust Relationship in AWS
What is a Trust Relationship in AWS?

Definition: A trust relationship defines which entities (e.g., IAM users, roles) are allowed to assume a role. It is configured in the role’s trust policy.
48. Public Subnet vs. Private Subnet
What is the difference between Public Subnet and Private Subnet?

Public Subnet: Subnets with routes to the internet, allowing direct access to/from the internet.
Private Subnet: Subnets without direct internet access, used for internal resources.
49. Establishing Connection Between EC2 Instances
How do you establish a connection between EC2 instances?

Method:
Security Groups: Configure security group rules to allow traffic between instances.
VPC: Ensure instances are in the same VPC or have appropriate VPC peering.
50. Realm Command
What is the realm command?

Definition: The realm command is used to manage and configure identity management domains and services in Linux, often related to Active Directory and Kerberos integration.
51. Differentiating Environments in AWS Account
How do you differentiate within an AWS account dev env, test env, and prod env?

Method:
Naming Conventions: Use consistent naming conventions for resources.
Tags: Tag resources with environment-specific labels.
Separate Accounts or VPCs: Use different accounts or VPCs for isolation.
52. Types of EC2 Instances
What are the types of EC2 instances?

Types:
General Purpose: t2, t3, m5
Compute Optimized: c5, c6g
Memory Optimized: r5, x1
Storage Optimized: i3, d2
53. Encrypting Already Created Unencrypted EBS
How can you encrypt the already created unencrypted EBS without creating a fresh EC2 instance?

Method:
Create a Snapshot: Create a snapshot of the unencrypted volume.
Copy Snapshot: Copy the snapshot and enable encryption during the copy process.
Create New Volume: Create a new encrypted volume from the encrypted snapshot.
Attach New Volume: Attach the new volume to the EC2 instance and migrate data.
54. Installing Nginx in Ansible Playbook
How do you install Nginx in the Ansible playbook?

Example Playbook:
yaml
Copy code
- name: Install Nginx
  hosts: webservers
  become: yes
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
    - name: Ensure Nginx is running
      service:
        name: nginx
        state: started
        enabled: yes
55. Recovering Deleted Object in S3
How do you recover a deleted object in S3?

Method:
Versioning: If versioning is enabled, you can restore the object by retrieving its previous version.
S3 Object Lock: Use object lock to prevent objects from being deleted or overwritten.

Day-to-Day Activities
What are the day-to-day activities?
Monitoring: Checking system health, logs, and alerts to ensure everything is running smoothly.
Incident Management: Responding to issues, troubleshooting, and resolving incidents.
Deployment: Managing and deploying updates to applications and infrastructure.
Automation: Writing and maintaining scripts and automation tools for continuous integration and continuous deployment (CI/CD).
Configuration Management: Using tools like Ansible or Puppet to manage and automate configurations.
Collaboration: Working with development and operations teams to understand requirements and address issues.
Documentation: Maintaining documentation for processes, configurations, and procedures.
Sending Files Between Servers
How do you send a file from one server to another?
Using SCP (Secure Copy Protocol):
bash
Copy code
scp /path/to/local/file user@remote:/path/to/remote/destination
Using SFTP (Secure File Transfer Protocol):
bash
Copy code
sftp user@remote
put /path/to/local/file /path/to/remote/destination
Using rsync:
bash
Copy code
rsync -avz /path/to/local/file user@remote:/path/to/remote/destination
Web and Application Servers
Which web server and application server are you using in your project?
Web Server: Apache HTTP Server, Nginx
Application Server: Tomcat, JBoss, or any other relevant server used in your project.
Deploying Applications to Tomcat
How do you deploy an application on a Tomcat server?
Manually:
Build Application: Package the application as a WAR file.
Deploy WAR File: Copy the WAR file to the Tomcat webapps directory.
Restart Tomcat: Restart Tomcat to deploy the application.
Using Jenkins:
Configure Jenkins Job: Set up a Jenkins job to build and deploy the WAR file.
Use Tomcat Deployment Plugin: Use plugins like Deploy to container to deploy the WAR file to Tomcat.
Git Commands
What git commands do you know?
Basic Commands: git init, git clone, git add, git commit, git push, git pull, git fetch, git status
Branching: git branch, git checkout, git merge, git rebase
History: git log, git diff, git blame
Remote: git remote, git tag, git cherry-pick
Sending JAR File to Nexus
How do you send a JAR file from the server to Nexus?
Using Maven Deploy Plugin:
xml
Copy code
<distributionManagement>
  <repository>
    <id>nexus</id>
    <url>http://nexus.example.com/repository/maven-releases/</url>
  </repository>
</distributionManagement>
Run: mvn deploy
Using CURL or HTTP Post:
bash
Copy code
curl -u user:password --upload-file /path/to/file.jar http://nexus.example.com/repository/maven-releases/com/example/file.jar
Creating Jenkins Pipeline
What process do you follow to create a Jenkins pipeline?
Define Pipeline: Create a Jenkinsfile that defines the pipeline stages (e.g., build, test, deploy).
Set Up Jenkins Job: Create a new pipeline job in Jenkins.
Configure SCM: Connect the Jenkins job to your source code repository where the Jenkinsfile is located.
Pipeline Script: Paste or link the Jenkinsfile to define the pipeline logic.
Test and Monitor: Run the pipeline, monitor the build process, and adjust as necessary.
Creating Ingress
How to create an Ingress in Kubernetes?
Define an Ingress Resource:
yaml
Copy code
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
    - host: example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: example-service
                port:
                  number: 80
Apply the Ingress Resource:
bash
Copy code
kubectl apply -f ingress.yaml
Troubleshooting Ingress Issues
The pods are running successfully, but Ingress is not working. What might be the issue?
Check Ingress Controller: Ensure the Ingress controller (e.g., Nginx) is properly installed and running.
DNS Configuration: Verify DNS records are correctly pointing to the Ingress controller's IP.
Ingress Rules: Check if the Ingress resource rules match the service and paths correctly.
Network Policies: Ensure there are no network policies or security group rules blocking access.
Logs: Review the logs of the Ingress controller for errors.
Additional DevOps Questions
What are your day-to-day activities as a DevOps engineer?

Similar to the first question above; detail your routine tasks in monitoring, deployment, and collaboration.
What kind of automations have you done?

Examples: Automated deployments using Jenkins, CI/CD pipelines, infrastructure provisioning with Terraform, configuration management with Ansible.
Will you support on-call if given an opportunity?

Response: Yes, if it aligns with your career goals and if you are comfortable handling critical incidents.
Tell some issues you have faced in production and how have you solved them?

Example: Addressed a memory leak in production by identifying and fixing the root cause in the application code.
Have you performed RCA (Root Cause Analysis) of any production issues?

Response: Yes, and describe an instance where you analyzed the root cause of an issue and implemented solutions.
Explain the entire process of CI/CD.

CI/CD Pipeline: Code commit → Automated build → Automated tests → Deployment to staging → Manual/Automated approval → Deployment to production.
Explain some steps where you have mitigated the cost of your applications.

Examples: Implemented auto-scaling to reduce unnecessary resource costs, optimized storage usage, used reserved instances.
Have you enabled any monitoring metrics in your project?

Examples: Configured monitoring with tools like Prometheus, Grafana, AWS CloudWatch, set up alerts for system health and application performance.
Explain the complete architecture of your project.

Response: Provide a high-level overview of the architecture, including components such as web servers, application servers, databases, load balancers, and how they interact.
What are the best security measures implemented in your project?

Examples: Implemented IAM roles and policies, used encryption for data at rest and in transit, configured security groups and network ACLs, enabled multi-factor authentication.

What happens in the backend when you type amazon.com (Explain DNS Process):

When you type amazon.com into your browser, the following DNS (Domain Name System) process occurs:
DNS Lookup: The browser checks its local cache to see if it already has the IP address for amazon.com. If not, it queries the DNS resolver (usually provided by your ISP).
DNS Resolver: The DNS resolver starts by querying the root DNS servers to find out which authoritative DNS servers are responsible for the .com domain.
TLD DNS Server: The resolver then queries the .com TLD (Top-Level Domain) DNS server to get the authoritative DNS server for amazon.com.
Authoritative DNS Server: The resolver queries the authoritative DNS server for amazon.com to obtain the IP address.
Response: The resolver returns the IP address to your browser, which then uses it to connect to the web server hosting amazon.com.
Explain different types of DNS Queries:

Recursive Query: The DNS resolver performs the entire DNS lookup process on behalf of the client, returning the final IP address or an error if it can't resolve the name.
Iterative Query: The DNS resolver returns the best answer it can immediately (such as a referral to another DNS server) but does not perform the entire lookup itself.
Authoritative Query: The DNS server being queried has information about the domain and provides the final answer.
Iterative and Recursive DNS Queries:

Recursive Query: The DNS resolver will fully resolve the domain name and return the IP address to the client. If it does not have the answer, it will query other DNS servers until it finds the answer or determines it cannot be found.
Iterative Query: The DNS resolver will return the best possible answer it has (which may be a referral to another DNS server) and leaves the resolution process to the client or another server.
Explain after the browser has got the IP address how it loads the website (on protocol basis):

DNS Resolution: The browser uses the IP address obtained from DNS resolution.
TCP Handshake: The browser initiates a TCP connection to the server using a 3-way handshake (SYN, SYN-ACK, ACK).
HTTP/HTTPS Request: The browser sends an HTTP or HTTPS request to the server.
Server Response: The server processes the request and sends back the response, including HTML, CSS, JavaScript, and other resources.
Rendering: The browser renders the web page by processing the received HTML and associated resources.
3-Way TCP Handshake Process:

SYN: The client sends a SYN (synchronize) packet to the server to initiate a connection.
SYN-ACK: The server responds with a SYN-ACK (synchronize-acknowledge) packet to acknowledge the receipt of the SYN.
ACK: The client sends an ACK (acknowledge) packet back to the server, completing the handshake and establishing the connection.
Can you tell me how sequence numbers work in TCP handshake:

Initial Sequence Numbers: During the TCP handshake, both the client and server choose an initial sequence number. This number is used to keep track of the data packets.
SYN: The client sends a SYN packet with its initial sequence number.
SYN-ACK: The server responds with a SYN-ACK packet that includes its own sequence number and acknowledges the client's sequence number.
ACK: The client sends an ACK packet that acknowledges the server's sequence number.
What is HTTPS, and how is it different from HTTP:

HTTP (Hypertext Transfer Protocol): A protocol used for transmitting data over the web. It is not encrypted, so data sent between the client and server can be intercepted.
HTTPS (Hypertext Transfer Protocol Secure): HTTP over SSL/TLS. It encrypts data exchanged between the client and server, providing confidentiality and integrity.
Explain SSL/TLS Handshake Process:

Client Hello: The client sends a "Client Hello" message with supported cryptographic algorithms and a randomly generated number.
Server Hello: The server responds with a "Server Hello" message, selecting the cryptographic algorithms and sending its own random number and digital certificate.
Key Exchange: Both parties exchange keys to establish a secure session.
Finished: Both parties send a "Finished" message to confirm that the handshake was successful and encryption is now in place.
You have set up your website with HTTPS, but after too many redirects errors are happening, what would cause this?

Redirect Loops: Incorrectly configured redirects causing the browser to loop between URLs.
Mixed Content: A mix of HTTP and HTTPS content on the same page causing issues.
Configuration Errors: Incorrectly set up HTTPS rules or redirection rules in the server configuration.
The website is working fine, but now it's running slow, how to troubleshoot:

Check Server Performance: Monitor CPU, memory, and disk usage.
Network Latency: Use tools like ping and traceroute to identify network issues.
Application Performance: Review application logs and performance metrics.
Browser Performance: Use developer tools to identify slow-loading resources.
Caching: Ensure proper caching is configured and working.
CDN (Content Delivery Networks), how it works, and how it ensures the website is not slow:

How It Works: CDNs distribute content across multiple geographically dispersed servers. When a user requests content, the CDN serves it from the closest server.
Speed Enhancement: Reduces latency by decreasing the distance between the user and the content, and offloads traffic from the origin server.
Trace route to amazon.com and explain the fields that come up in the output:

Hop Number: Sequence number of the hop.
Round-Trip Time: Time it takes for packets to travel to the hop and back.
Hostname/IP Address: The address of the hop.
Which protocol is used in traceroute:

ICMP (Internet Control Message Protocol) or UDP (User Datagram Protocol), depending on the implementation.
Suppose a website is loading slow, is there anything which can be checked with the browser:

Network Tab: Analyze resource loading times.
Performance Tab: Measure page load and runtime performance.
Console: Look for any JavaScript errors or warnings.
Suppose I have a server not using any CDN, is there any way the servers can control the amount of the content cached by the browser:

HTTP Headers: Use headers like Cache-Control, Expires, and ETag to control caching.
Suppose your laptop is in a private network, any way it can connect to the internet? (NAT process):

NAT (Network Address Translation): Private IP addresses are translated to a public IP address by a NAT router or firewall, allowing access to the internet.
Explain types of NAT:

Static NAT: Maps a single private IP address to a single public IP address.
Dynamic NAT: Maps private IP addresses to a pool of public IP addresses.
PAT (Port Address Translation): Maps multiple private IP addresses to a single public IP address with different ports.
How can one server serve HTTPS requests for two domains:

Virtual Hosts: Configure the server to use virtual hosts with separate SSL certificates for each domain.
SNI (Server Name Indication): Allows multiple SSL certificates on a single IP address by specifying the domain name during the SSL handshake.
Can you tell me how does my laptop, when it is connected to an IP, and when I go to the office and it gets a different IP, how does a laptop connect to a new network? (DHCP DORA process):

Discovery: The laptop broadcasts a DHCP Discover message to find DHCP servers.
Offer: DHCP servers respond with a DHCP Offer message containing an IP address and other configuration details.
Request: The laptop sends a DHCP Request message to accept the offer.
Acknowledgment: The DHCP server sends a DHCP Acknowledgment message confirming the IP address assignment.
Can you explain how machines in a switch network communicate:

MAC Addresses: Machines communicate using MAC (Media Access Control) addresses. The switch uses a MAC address table to forward packets to the correct port.
Broadcasting: When a device sends a broadcast, the switch forwards it to all connected devices.
Can you explain the difference between dynamic and static web content:

Static Content: Fixed content that does not change (e.g., HTML files, images).
Dynamic Content: Content generated in real-time based on user interactions or other data (e.g., database queries).

22. Suppose I have multiple servers serving content, now I want to make sure a particular server does not get overloaded with requests, is there any software which can be used?
Load Balancer: Use a load balancer (e.g., HAProxy, NGINX, AWS ELB) to distribute incoming traffic across multiple servers, ensuring no single server gets overloaded.
Traffic Management Software: Tools like Kubernetes Ingress or service meshes (e.g., Istio) can help manage traffic and prevent overloading.
23. I have created a DNS record, but the value is not resolving as expected. What could be the possible reasons?
Propagation Delay: DNS changes can take time to propagate across the internet.
Caching: DNS caches (local or on intermediate servers) might still have old information.
Incorrect Configuration: Verify that the DNS records are correctly configured (e.g., A records, CNAMEs).
DNS Server Issues: The authoritative DNS server might be misconfigured or not responding.
TTL Settings: Check the TTL (Time to Live) values for outdated cached records.
24. How ARP works?
Address Resolution Protocol (ARP) is used to map a known IP address to a MAC address within a local network.
ARP Request: A device broadcasts an ARP request packet on the network asking, "Who has IP address X.X.X.X? Please send your MAC address."
ARP Reply: The device with the IP address X.X.X.X responds with an ARP reply packet containing its MAC address.
Caching: The requesting device caches this information for future use.
25. Tell me about a situation in your current role where you had to dive deep:
Example Answer: "In my current role, we faced an issue with intermittent application crashes that were difficult to diagnose. I took a deep dive into the application's logs and used performance monitoring tools to track down memory leaks. I also analyzed the application's codebase to identify inefficient algorithms contributing to high memory usage. By isolating the problematic code and optimizing it, we significantly improved application stability."
2nd Round: Amazon
Tell me about yourself, brief introduction:

Prepare a concise summary of your background, relevant experience, and key skills. Highlight your DevOps expertise, key projects, and why you're interested in the role at Amazon.
Tell me about a time where you solved something complex using a simple solution:

Example Answer: "We faced a problem with a deployment pipeline that had become overly complex and prone to errors. I simplified the pipeline by consolidating scripts and automating redundant tasks. This reduced errors, improved deployment speed, and made the pipeline easier to maintain."
SSH into an EC2 Instance is not working, getting permission denied error, How will you troubleshoot it?

Check Permissions: Ensure that the correct permissions are set for the PEM file (chmod 400 key.pem).
Correct Key: Verify that the correct private key is being used.
Authorized Keys: Confirm that the public key is correctly added to the -/.ssh/authorized_keys file on the EC2 instance.
Security Groups: Ensure that the security group associated with the EC2 instance allows inbound SSH traffic on port 22.
Instance State: Ensure that the EC2 instance is running and reachable.
How does SSH Authentication work?

Public Key Authentication: SSH authentication uses a pair of keys: a private key stored securely on the client and a public key stored on the server.
Process: The client sends a request to the server, the server challenges the client to prove possession of the private key, and the client responds with a proof that it has the corresponding private key. If successful, access is granted.
Public Key, Private Key, Authorized Keys, PEM file - Study on these topics:

Public Key: Used to encrypt data. It is shared with anyone who needs to send encrypted messages to the key holder.
Private Key: Used to decrypt data encrypted with the public key. It is kept secret and secure.
Authorized Keys: A file on the server that contains public keys of clients allowed to connect via SSH.
PEM File: A file format for storing cryptographic keys and certificates, commonly used for SSH keys.
Not able to modify file permissions using chmod, what could be the issue?

File Ownership: Ensure you have the appropriate ownership or permissions to modify the file.
File System: The file system might be mounted as read-only.
Sudo Access: You might need to use sudo to change permissions if you lack sufficient privileges.
What processes happen in the background when the OS loads up a program/application? Before it actually starts executing it:

Loading: The OS loads the program's executable file into memory.
Memory Allocation: The OS allocates memory for the program's code, data, and stack.
Page Table Setup: The OS sets up page tables to manage virtual memory.
Process Creation: The OS creates a process control block (PCB) to track the process's state and resources.
Initialization: The OS initializes the program's execution context and prepares for execution.
How to check disk usage?

df -h: Displays disk space usage of file systems.
du -sh /path/to/directory: Shows the disk usage of a specific directory.
Where is the Page Table stored?

In RAM: Page tables are stored in RAM as part of the process's memory management structures.
When a program is started, are all pages loaded into the RAM at the start?

No: Modern OSes use demand paging, which means only the necessary pages are loaded into RAM initially, and additional pages are loaded as needed.
Study paging, segmentation, demand paging, page fault, swap memory concepts for these:

Paging: Memory management scheme that eliminates the need for contiguous allocation of physical memory and thus eliminates the problems of fitting varying sized memory chunks onto the backing store.
Segmentation: Memory management technique that divides the memory into segments based on logical units (e.g., functions or data structures).
Demand Paging: Only loads pages into RAM when they are needed, rather than loading the entire program.
Page Fault: Occurs when a program tries to access a page that is not currently in RAM, causing the OS to load the page from disk.
Swap Memory: A space on a disk used to extend the physical memory of a computer by storing pages that are not currently in use.
From RAM where do the processes go?

Swap Space: Processes or pages that are not currently needed may be moved from RAM to swap space on disk to free up RAM.
How OS achieves running of multiple applications - Multitasking, Multiprocessing:

Multitasking: OS switches between multiple tasks or applications, giving the illusion of simultaneous execution.
Multiprocessing: OS uses multiple processors or cores to execute processes or threads simultaneously.
How context switching works, what is PCB?

Context Switching: The OS saves the state (context) of the currently running process and loads the state of the next process to be executed.
PCB (Process Control Block): A data structure that contains information about a process, including its state, program counter, CPU registers, and memory management information.
What interrupt signal is sent by CPU when it needs to switch from one process to another?

Timer Interrupt: A signal from a hardware timer that triggers the OS to perform a context switch and schedule the next process.
What is a scheduling algorithm?

Scheduling Algorithm: A method used by the OS to determine which process or thread to execute next. Examples include First-Come-First-Serve (FCFS), Round-Robin, and Shortest Job Next (SJN).
My system is running very slow, how will you troubleshoot?

CPU Usage: Use commands like top or htop to check for high CPU usage.
Memory Usage: Check for high memory usage with free -m or vmstat.
Disk Space: Use df -h to ensure there's enough disk space.
Network Issues: Use ping and traceroute to diagnose network problems.
Software Issues: Look at system logs (/var/log/) for errors or warnings.
Hard disk space is 600GB and 200GB is free, I am trying to upload a single file of 65GB to the hard disk, but I am getting an error stating that disk is full, what could be the issue?

File System Limitations: Some file systems have a maximum file size limit (e.g., FAT32 has a 4GB limit). Check if the file system supports large files.
Difference between File Storage, Block Storage, Object Storage:

File Storage: Stores data as files in a hierarchical structure (e.g., NFS, SMB). Best for shared file access.
Block Storage: Stores data in fixed-size blocks. It is used for high-performance applications and databases (e.g., AWS EBS, SAN).
Object Storage: Stores data as objects with metadata and unique identifiers. Best for unstructured data and scalability (e.g., AWS S3, Google Cloud Storage).
Why do you want to join Amazon?

Tailor your answer to reflect your passion for Amazon’s culture, its innovative projects, and how your skills and experiences align with the company's goals. Mention any specific aspects of Amazon’s work or values that resonate with you.

In NGINX, proxy_pass is a directive used within the location block to define a proxy server that NGINX will forward client requests to. This is useful when you want NGINX to act as a reverse proxy, forwarding requests to another server or service.

How proxy_pass Works:
Client Request: A client sends a request to NGINX.
Matching Location Block: NGINX looks for a matching location block in its configuration.
Forwarding Request: If the location block contains a proxy_pass directive, NGINX forwards the request to the specified upstream server.
Example Configuration:
Here’s a basic example of how proxy_pass might be used in an NGINX configuration file:

nginx
Copy code
server {
    listen 80;
    server_name example.com;

    location /api/ {
        proxy_pass http://backendserver.com/api/;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
Explanation:
proxy_pass http://backendserver.com/api/;: This tells NGINX to forward requests that match the /api/ location to http://backendserver.com/api/.
proxy_set_header directives: These set additional headers to pass along with the request:
Host: Sets the Host header to the original request's host.
X-Real-IP: Sets the X-Real-IP header to the client's IP address.
X-Forwarded-For: Appends the client's IP address to the X-Forwarded-For header, which is used to keep track of the client's IP through proxy layers.
X-Forwarded-Proto: Sets the X-Forwarded-Proto header to the original protocol (HTTP or HTTPS).
Use Cases:
Reverse Proxy: Directs incoming requests to a backend server or service.
Load Balancing: Forwards requests to multiple backend servers to distribute load.
API Gateway: Routes requests to different microservices based on URL paths.
Advanced Options:
proxy_redirect: Adjusts the Location header in responses from the backend server.
proxy_set_header: Customizes headers sent to the backend server.
proxy_buffering: Controls whether NGINX buffers responses from the backend server.
By using proxy_pass, NGINX can efficiently route traffic, handle load balancing, and act as a gateway between clients and backend services.







