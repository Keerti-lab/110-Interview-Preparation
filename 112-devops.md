Basic Scenarios
You have a simple web application. How would you Dockerize it?

Create a Dockerfile that defines the application’s environment (base image, dependencies, etc.).
Build the Docker image with docker build -t <image-name> ..
Run the container with docker run -d -p 8080:80 <image-name> to map the container's port to the host.
How do you build a Docker image from a Dockerfile?

Use the command docker build -t <image-name> ., where . refers to the current directory containing the Dockerfile.
What's the difference between docker run and docker start?

docker run: Creates a new container from an image and starts it.
docker start: Starts an existing, stopped container.
Explain how to mount a local directory into a Docker container.

Use the -v option with docker run, e.g., docker run -v /host/path:/container/path <image>, where /host/path is the local directory.
You get an "Image not found" error. What are the possible causes?

The image name might be incorrect.
The image might not exist locally, and Docker Hub may not have the image.
Network issues could prevent pulling the image.
How do you view logs of a running container?

Use docker logs <container-id> to view the container's logs.
What's the purpose of Docker Compose?

Docker Compose allows you to define and run multi-container Docker applications with a YAML file, simplifying orchestration and scaling.
Describe how to network two containers together.

Use a custom network (docker network create <network-name>), then run containers with --network <network-name>.
What is the difference between a Docker image and a container?

A Docker image is a blueprint for containers. A container is a running instance of an image.
How would you remove all stopped containers?

Run the command docker container prune to remove all stopped containers.
Intermediate Scenarios
You have a multi-container application. How do you orchestrate it with Docker Compose?

Define the services in a docker-compose.yml file and run docker-compose up to start all containers as defined.
How do you build a minimal Docker image for production?

Use a lightweight base image like alpine and multi-stage builds to minimize unnecessary files and layers.
Explain how to use environment variables in a Dockerfile.

Use the ENV instruction in the Dockerfile or pass variables at runtime with docker run --env VAR_NAME=value.
Your container keeps crashing. How do you troubleshoot it?

Check logs with docker logs <container-id>.
Inspect the container's exit status and restart policy.
Check for issues in the application, memory, or disk space.
What's the difference between COPY and ADD in a Dockerfile?

COPY: Copies files and directories from the host to the container.
ADD: Like COPY, but also supports URL downloads and tarball extraction.
Describe how to publish a Docker image to Docker Hub.

Tag the image with docker tag <image> <username/repo:tag>.
Log in with docker login and push with docker push <username/repo:tag>.
How do you manage persistent data in Docker containers?

Use Docker volumes (docker volume create and docker run -v) to persist data outside the container's lifecycle.
You want to run a database in a container. What are the best practices?

Use volumes for data persistence.
Use environment variables for configuration.
Expose only necessary ports and secure them properly.
How do you connect a Docker container to a local network?

Use --network host for host networking or docker network connect to connect a container to an existing network.
What are Docker volumes, and why are they useful?

Volumes store persistent data outside the container’s lifecycle. They enable data sharing between containers and allow data to persist after the container is deleted.
Advanced Scenarios
You have a microservices architecture. How would you deploy it with Docker Swarm?

Initialize a Swarm cluster with docker swarm init, then define the services in a docker-compose.yml file and deploy with docker stack deploy.
Explain how to use Docker secrets for sensitive data.

Create secrets using docker secret create, and use docker service or Docker Compose to mount them into containers securely.
Your application needs to scale horizontally. How do you achieve this with Docker?

Use Docker Compose or Docker Swarm to define and scale services with docker-compose scale <service>=<replicas> or docker service scale <service>=<replicas>.
How do you set up health checks for your Docker containers?

Define HEALTHCHECK in the Dockerfile to run a command inside the container that determines if it’s healthy.
Describe how to use Docker multi-stage builds for optimized images.

In a Dockerfile, use multiple FROM statements to create different stages, copying only the final build artifacts into the production image to reduce size.
You're facing performance issues in your Docker containers. What can you check?

Check resource limits (CPU, memory) with docker stats.
Optimize the Dockerfile for reduced layers.
Investigate network or storage bottlenecks.
How do you create a custom Docker network bridge?

Use docker network create -d bridge <network-name> to create a bridge network.
What's the role of Docker Swarm in container orchestration?

Docker Swarm is a native clustering tool for Docker, providing container orchestration, service discovery, load balancing, and scaling.
How do you back up and restore Docker volumes?

To back up: docker run --rm -v <volume-name>:/data -v $(pwd):/backup busybox tar cvf /backup/backup.tar /data.
To restore: docker run --rm -v <volume-name>:/data -v $(pwd):/backup busybox tar xvf /backup/backup.tar -C /data.
How do you handle rolling updates for your Dockerized application?

In Docker Swarm, use docker service update --update-parallelism <n> --update-delay <time> <service> to update containers one by one.

Security Scenarios
How do you ensure the security of your Docker images?

Use official and trusted base images from Docker Hub.
Regularly update your images to include the latest security patches.
Limit the number of layers in your Dockerfile to reduce the attack surface.
Use Docker Content Trust to sign images.
Scan your images for vulnerabilities using tools like Trivy, Clair, or Anchore.
Explain how to scan Docker images for vulnerabilities using Trivy.

Install Trivy and run trivy image <image-name> to scan the Docker image for known vulnerabilities.
Trivy will report CVEs, their severity, and potential fixes or workarounds.
What are some common Docker security risks?

Using outdated or insecure images.
Running containers with root privileges.
Exposing sensitive data (e.g., credentials) via environment variables or unencrypted networks.
Insecure container-to-container or host-to-container communication.
How do you restrict container capabilities for better security?

Use the --cap-drop option when running containers to remove unnecessary capabilities (e.g., docker run --cap-drop=NET_RAW).
Use the --security-opt flag to apply security profiles like AppArmor or SELinux.
What are the best practices for securing Docker Swarm?

Enable mutual TLS for node communication (--tls).
Rotate Swarm manager and worker node certificates regularly.
Encrypt network traffic between containers using overlay networks with encryption (--opt encrypted).
Secure sensitive data using Docker secrets and avoid storing them in environment variables.
Troubleshooting Scenarios
Your Docker build fails. How do you analyze the error logs?

Check the build output for specific error messages.
Rebuild the image with docker build --no-cache to ensure it doesn’t use cached layers.
Use docker build --progress=plain to get detailed logs during the build process.
You can't access a running container's port. What are the possible reasons?

The container might not be exposing the correct port (docker run -p <host-port>:<container-port>).
The service inside the container might not be running.
Firewall rules on the host may be blocking access.
Network issues between the host and the container.
Your Docker containers are consuming too much memory. What can you do?

Use the docker stats command to check memory usage.
Set memory limits on containers using --memory and --memory-swap options.
Investigate the application inside the container for memory leaks or inefficiencies.
How do you recover a deleted Docker image?

If the image is deleted locally but still available on Docker Hub or a registry, pull it again using docker pull <image-name>.
If it's completely deleted, you will need to rebuild the image from the Dockerfile.
Your Docker Swarm nodes are not communicating. How do you troubleshoot?

Ensure that the necessary ports for Swarm communication (2377 for cluster management, 7946 for node communication, and 4789 for overlay networking) are open.
Check logs using docker logs on each node for error messages.
Verify that the nodes are using the same Swarm token and that there is no clock drift between them.
Real-World Scenarios
You're migrating a legacy application to Docker. What's your approach?

Break down the application into its components (web, database, etc.).
Create a Dockerfile for each component, specifying the necessary dependencies and configurations.
Use Docker Compose to orchestrate the application for local development and testing.
Ensure that data persistence and environment variables are handled securely.
Test the Dockerized application in a staging environment before moving to production.
You're designing a CI/CD pipeline with Docker. What are the key steps?

Build Docker images as part of the pipeline, typically triggered by code pushes.
Run unit and integration tests within Docker containers for a consistent environment.
Push the Docker image to a registry (Docker Hub, ECR, etc.) once the tests pass.
Deploy the Docker image to a staging environment for final testing.
Once approved, deploy to production using orchestrators like Docker Swarm, Kubernetes, or Compose.
How would you use Docker for local development environments?

Create a docker-compose.yml file to define services for the application and its dependencies (databases, caches, etc.).
Use volumes to map local directories to the container for real-time code changes without rebuilding the image.
Use Docker networks to simulate production-like interactions between containers.
Set up environment variables and configuration files to match production settings as closely as possible.
You're setting up a staging environment with Docker. How do you ensure it mirrors production?

Use the same Docker images and Compose or Kubernetes configurations that are used in production.
Mirror production environment variables, databases, and services in the staging environment.
Use Docker Compose or a Swarm stack to deploy the application in the same manner as in production.
Ensure that sensitive information (e.g., credentials) is secured in the same way (using secrets or encrypted volumes).
Your team is adopting Docker. What training do you recommend?

Start with basic Docker concepts (images, containers, Dockerfiles, and networking).
Progress to Docker Compose and Swarm for multi-container and distributed applications.
Train on Docker security best practices (restricting privileges, scanning for vulnerabilities, etc.).
Introduce container orchestration tools (Docker Swarm or Kubernetes) for production deployments.
Encourage hands-on workshops and exercises where the team builds, runs, and troubleshoots Docker containers.