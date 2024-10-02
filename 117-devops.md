Questions:
1. What is configuration management?
Answer:
Configuration management is the process of maintaining and handling the desired state of systems and software across an organization's IT infrastructure. It involves ensuring consistency, tracking changes, and automating the deployment of configurations.

2. Why Ansible over the other configuration management tools?
Answer:
Ansible is chosen over other tools because it is agentless, uses a simple YAML syntax, and is easier to set up and learn. It works through SSH, reducing the need for additional software installation on client machines. Ansible also has a large ecosystem with modules for various platforms.

3. Can you explain any Ansible Playbook that you wrote and found to be effective?
Answer:
I wrote a playbook to deploy an NGINX web server across multiple Linux servers. The playbook handled installation, configuration, and service restarts. It was effective because it used roles to modularize tasks, making it reusable and easy to maintain.

4. How has Ansible helped your organization?
Answer:
Ansible has streamlined configuration management, reducing manual interventions and errors. By automating server configurations and software deployments, we were able to reduce time spent on repetitive tasks and improve system consistency.

5. Scenario: Let's assume you are not aware of the Ansible Servers that would be created in the future but still want to manage them. How can you achieve that?
Answer:
This can be managed through dynamic inventory. Ansible can integrate with cloud providers like AWS, using their APIs to automatically detect new servers and manage them as they are created.

6. What is Ansible Tower and have you used it? If yes, why?
Answer:
Ansible Tower is an enterprise-level web-based solution for managing Ansible automation. It provides a user-friendly interface, scheduling, RBAC, and reporting features. I have used it to provide more control over large-scale automation processes and to centralize playbook execution.

7. How do you manage the RBAC of users for Ansible Tower?
Answer:
In Ansible Tower, Role-Based Access Control (RBAC) is managed by assigning roles such as Admin, Operator, and User. These roles define the actions a user can perform, from viewing jobs to executing playbooks.

8. What is Ansible Galaxy command and why is it used for?
Answer:
ansible-galaxy is a command-line tool used to install, manage, and share Ansible roles. It is primarily used for downloading roles from the Ansible Galaxy repository to speed up development by reusing community-created content.

9. Can you explain the structure of an Ansible Playbook using Roles?
Answer:
A playbook using roles is structured as follows:

roles/: Directory containing roles. Each role has subdirectories for tasks, handlers, vars, defaults, files, and templates.
site.yml: Main playbook that calls the roles.
Each role encapsulates a part of the configuration (e.g., web server setup).
10. What are handlers in Ansible and why are they used?
Answer:
Handlers are special tasks that run only when triggered by another task using the notify directive. They are used for operations that need to happen after a state change, such as restarting a service after a configuration file is modified.

11. I would like to run a specific set of tasks only on Windows VMs and not Linux VMs. Is it possible?
Answer:
Yes, you can use conditionals in the playbook to check the ansible_os_family or ansible_system variable and run tasks only on Windows VMs.

12. Does Ansible support parallel execution of tasks?
Answer:
Yes, Ansible supports parallel execution by controlling the forks parameter, which defines how many hosts to execute tasks on simultaneously.

13. What is the protocol that Ansible uses to connect to Windows VMs?
Answer:
Ansible uses WinRM (Windows Remote Management) protocol to connect to Windows VMs.

14. Can you explain the variable precedence in Ansible?
Answer:
Ansible variable precedence (from lowest to highest) includes:

Role defaults
Inventory file variables
Playbook group_vars and host_vars
Playbook variables
Role vars
Extra vars passed from the command line.
15. How do you handle secrets in Ansible?
Answer:
Secrets in Ansible are handled using Ansible Vault, which encrypts sensitive data such as passwords and API keys.

16. Can Ansible be used for IaC (Infrastructure as Code)?
Answer:
Yes, Ansible can be used for IaC by automating the provisioning of infrastructure resources like EC2 instances, databases, and networking components.

17. Write an Ansible Playbook to Install and start httpd service on an existing EC2 instance.
Answer:

yaml
Copy code
- name: Install and start httpd
  hosts: webservers
  become: yes
  tasks:
    - name: Install httpd
      yum:
        name: httpd
        state: present

    - name: Start and enable httpd service
      service:
        name: httpd
        state: started
        enabled: true
18. Finally, What do you think that Ansible can improve?
Answer:
Ansible could improve its performance when handling large-scale environments. Additionally, better out-of-the-box support for Windows and simplified error messaging could enhance user experience.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questions:
1. What is IaC? Why Terraform?
Answer:
IaC (Infrastructure as Code) is a method of managing and provisioning infrastructure using code rather than manual processes. Terraform is preferred because it is cloud-agnostic, supports modular configurations, and has state management for tracking infrastructure changes.

2. What are modules in Terraform?
Answer:
Modules in Terraform are reusable blocks of infrastructure code that help in organizing and standardizing configurations. They promote code reuse, improve maintainability, and make complex infrastructure more manageable.

3. What is a state file in Terraform?
Answer:
A state file in Terraform stores the current state of the infrastructure managed by Terraform. It helps Terraform determine which resources need to be created, updated, or deleted.

4. What are some of the most common Terraform CLI commands that you use every day?
Answer:
Common commands include:

terraform init: Initializes the working directory.
terraform plan: Shows the execution plan.
terraform apply: Applies the changes to the infrastructure.
terraform destroy: Destroys the resources managed by Terraform.
5. What is Terraform backend?
Answer:
Terraform backend is the configuration that defines where Terraform's state file is stored. It can be local or remote, and different backends support additional features like locking and versioning.

6. What is Terraform Remote Backend?
Answer:
A remote backend allows Terraform to store its state file in a remote location, such as S3 or a Terraform Cloud workspace. This ensures that multiple users or teams can collaborate by using the same state file.

7. How do you handle secrets in Terraform?
Answer:
Secrets in Terraform can be managed by using environment variables, third-party vault systems like HashiCorp Vault, or AWS Secrets Manager. Sensitive data should not be hardcoded in Terraform configuration files.

8. What is Resource Graph in Terraform?
Answer:
Resource Graph is the internal dependency graph Terraform builds to understand the relationships between resources. It helps Terraform determine the order in which resources should be provisioned or destroyed.

9. What is Terraform State Locking?
Answer:
Terraform State Locking prevents multiple users from modifying the state file concurrently. It ensures that one operation completes before another can begin.

10. What is a Tainted Terraform resource?
Answer:
A resource becomes tainted when it is marked for destruction and recreation in the next apply command. This is usually done when a resource is found to be inconsistent or corrupted.

11. What is Terraform State Rollback?
Answer:
Terraform State Rollback is the process of reverting to a previous state file in case of errors or unwanted changes. This allows you to restore your infrastructure to a known good state.


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Git Interview Q&A

Questions:

Is Git a Distributed or Centralized version control system? What is the difference between them? Answer: Git is a distributed version control system. In a centralized system, there is a single central repository, and developers directly interact with it. In a distributed system, every developer has a local copy of the entire repository, allowing offline work and easier branching/merging.

What are the Git commands that you use to commit changes to your remote repository? Answer: Common commands include:

git add . to stage changes.
git commit -m "commit message" to commit staged changes.
git push origin <branch> to push commits to the remote repository.
What is the difference between git fetch and git push? Answer: git fetch retrieves updates from a remote repository without modifying your local branches, whereas git push sends your local changes to the remote repository.

What is the difference between git merge and git rebase? Answer: git merge integrates changes from one branch into another, preserving the history of both branches. git rebase re-applies changes from one branch onto another, rewriting history to create a linear sequence of commits.

What is git and gitignore? Answer: Git is a distributed version control system for tracking changes in source code. .gitignore is a file that specifies which files or directories Git should ignore, preventing them from being added to the repository.

What are pre-commit hooks and post-commit hooks? Answer: Pre-commit hooks run scripts before a commit is finalized, often used for linting or running tests. Post-commit hooks run after a commit, useful for tasks like sending notifications or updating external tools.

What is a webhook? Answer: A webhook is an automated callback triggered by events in a system, like pushing code to a repository, to notify external services or trigger actions like CI/CD pipelines.

How to pull and push changes to git? Answer: Use git pull to fetch and merge changes from the remote repository. Use git push to upload local commits to the remote repository.

How do you resolve a merge conflict in git? Answer: To resolve a merge conflict:

Identify conflicting files using git status.
Edit the conflicting files to resolve the conflict.
Stage the resolved files with git add.
Complete the merge with git commit.
What is git stash and talk about its use cases? Answer: git stash temporarily saves changes that are not ready for a commit, allowing you to switch branches or work on something else. Use cases include pausing work or preparing a clean working directory for another task.

What is the difference between git clone and git fork? Answer: git clone creates a local copy of a repository, while git fork creates a copy of the repository under your account (typically used on platforms like GitHub), allowing independent development.

How to amend a commit in git? Answer: Use git commit --amend to modify the most recent commit, which can be used to update the commit message or include additional changes.

What is cherry-pick in git? Answer: git cherry-pick applies a specific commit from one branch onto another, useful for selectively bringing changes without merging entire branches.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Docker and Kubernetes Q&A

Questions:

What is the difference between Docker and Kubernetes? Answer: Docker is a platform for building, running, and managing containers. Kubernetes is an orchestration tool that manages and scales containerized applications across clusters, automating deployment, scaling, and maintenance of containerized apps.

What are the main components of Kubernetes architecture? Answer: The key components include:

Master Node: Contains the API server, scheduler, and controller manager.
Worker Nodes: Run the application pods and contain kubelet and kube-proxy.
Etcd: Stores cluster configuration data.
Controller: Maintains the desired state of objects in the cluster.
What are the main differences between Docker Swarm and Kubernetes? Answer:
Docker Swarm: Native Docker orchestration, simpler setup, tightly integrated with Docker CLI.
Kubernetes: More feature-rich, supports larger-scale deployments, has advanced networking, scaling, and monitoring capabilities.
What is the difference between Docker container and Kubernetes pod? Answer: A Docker container is an isolated instance of an application. A Kubernetes pod is a higher-level abstraction that can run one or more containers, allowing them to share resources like storage and networking.

What is the difference between Kubernetes deployment, statefulset, and daemonset? Answer:

Deployment: Manages stateless applications.
StatefulSet: Manages stateful applications, ensuring the same pods are re-deployed with persistent storage.
DaemonSet: Ensures that a pod runs on all or specific nodes in a cluster.
What is a namespace in Kubernetes? Answer: A namespace is a virtual cluster within a Kubernetes cluster, used to separate resources for different teams, projects, or environments.

What is the role of kube-proxy? Answer: Kube-proxy handles networking for Kubernetes services, managing network rules and load balancing across service endpoints.

What are the different types of services within Kubernetes? Answer:

ClusterIP: Exposes services only within the cluster.
NodePort: Exposes services on each node’s IP at a static port.
LoadBalancer: Exposes services externally using a cloud provider’s load balancer.
ExternalName: Maps a service to an external DNS name.
What is the difference between NodePort and LoadBalancer type service? Answer: NodePort exposes a service on a specific port on each node in the cluster, while LoadBalancer creates an external load balancer to expose the service outside the cluster.

What is Ingress in Kubernetes? Answer: Ingress is a resource that manages external access to services, typically HTTP and HTTPS, and can provide load balancing, SSL termination, and path-based routing.

What is the role of Kubelet? Answer: Kubelet is an agent that runs on each node, ensuring that containers are running in the correct state as defined by Kubernetes configuration. It communicates with the API server to manage container lifecycle.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Docker Q&A

Questions:

What is Docker? Answer: Docker is a platform that allows developers to automate the deployment, scaling, and management of applications inside lightweight, portable containers. Containers package an application and its dependencies, ensuring it runs consistently across different environments.

What is a Docker container and how is it different from a Virtual Machine? Answer: A Docker container is a lightweight, standalone executable package that includes everything needed to run a piece of software. Unlike virtual machines, containers share the host operating system's kernel and are more resource-efficient, allowing faster startup times and less overhead.

What is a DockerFile? Answer: A Dockerfile is a text file containing a set of instructions that are used to build a Docker image. It defines the environment in which the application runs, including the base image, dependencies, configuration settings, and commands to execute.

What are Docker Images? Answer: Docker images are read-only templates used to create Docker containers. They contain the application code, runtime, libraries, and dependencies required to run the application.

What are the different Docker components? Answer: The main Docker components are:

Docker Engine: Core software to create and run containers.
Docker Images: Templates to create containers.
Docker Containers: Instances of Docker images.
Dockerfile: Instructions to build Docker images.
Docker Hub: Public repository for sharing Docker images.
Docker Compose: Tool to define and run multi-container applications.
Docker Swarm: Native clustering and orchestration tool for Docker.
What is a Docker Registry and which registry are you using in your current organisation? Answer: A Docker registry is a storage and distribution system for Docker images. The most popular public registry is Docker Hub. Organizations often use private registries like Amazon ECR, Google Container Registry, or self-hosted registries. (The specific registry can vary depending on the organization).

What is the difference between docker COPY and docker ADD? Answer:

COPY: Copies files or directories from the local filesystem into the container.
ADD: Similar to COPY but can also fetch remote URLs and automatically unpack compressed files.
What is the difference between CMD and Entrypoint in Docker? Answer:
CMD: Specifies the default command to run when the container starts, but it can be overridden by passing arguments.
Entrypoint: Defines the command that always runs when the container starts and cannot be overridden, but additional parameters can be passed.
How can you transfer a file from one docker container to another? Answer: You can transfer files between containers using shared volumes, or by copying files between containers using the docker cp command to first move files to the host and then from the host to another container.

What is the difference between docker, docker compose, and docker swarm? Answer:

Docker: Basic tool to create and run containers.
Docker Compose: Used to define and manage multi-container Docker applications with a YAML file.
Docker Swarm: Native Docker orchestration tool to manage clusters of Docker containers.
What is multi-stage build in Docker? Answer: Multi-stage builds allow creating Docker images more efficiently by using multiple FROM statements in a Dockerfile. This method helps reduce the final image size by copying only the necessary artifacts from the intermediate build stages to the final image.

What are distroless images in Docker? Answer: Distroless images are minimal Docker images that contain only the application and its dependencies, without including a package manager or shell. These images are more secure and smaller in size, reducing the attack surface.









