Docker Interview Questions
Question: What is a Dockerfile?
Answer: A Dockerfile is a text file that contains a series of commands used to build a Docker image. It automates the process of setting up an application’s environment inside a container by specifying OS dependencies, configurations, and other setup instructions.

Question: What is multi-stage in Docker?
Answer: Multi-stage builds allow you to use multiple FROM statements in one Dockerfile. This helps in reducing the final image size by copying only the necessary artifacts from one stage to another, avoiding unnecessary dependencies.

Question: What is a Docker volume and how do you use it?
Answer: A Docker volume is a mechanism for persisting data generated or used by Docker containers. It can be mounted into containers to store data that should not be lost when a container is stopped or removed. You use it by declaring VOLUME in Dockerfile or via -v flag in docker run.

Question: How can we pass an argument to Dockerfile?
Answer: Arguments can be passed to a Dockerfile using the ARG instruction. You can set a default value or pass it at build time using the --build-arg flag.

Question: Dockerfile runs as which user?
Answer: By default, the Dockerfile runs as the root user unless explicitly changed using the USER instruction.

Question: How do you push the image to Docker Hub?
Answer: You push an image to Docker Hub by tagging the image with your Docker Hub repository name and using the command docker push <image_name> after authenticating with docker login.

Question: Write a Dockerfile for a Java-based application.
Answer:

dockerfile
Copy code
FROM openjdk:11-jre-slim
COPY ./app.jar /usr/app/app.jar
WORKDIR /usr/app
ENTRYPOINT ["java", "-jar", "app.jar"]
Question: What is Docker Compose?
Answer: Docker Compose is a tool used for defining and running multi-container Docker applications. It uses a YAML file (docker-compose.yml) to define services, networks, and volumes, allowing you to run a complete application with one command.

Question: How is Docker integrated in Jenkins?
Answer: Docker can be integrated with Jenkins to build and run containers during the build process. Jenkins can use Docker agents as slaves for running the build, and Docker plugins in Jenkins help manage containers and images during the CI/CD pipeline.

Question: Please explain Docker networking.
Answer: Docker networking allows containers to communicate with each other and the outside world. Docker provides various network drivers like bridge, host, and overlay to manage container communication across different environments.

Question: Can you use multiple FROM statements in a Dockerfile?
Answer: Yes, using multiple FROM statements is possible, especially in multi-stage builds. Each FROM creates a new stage, allowing you to use artifacts from one stage in another.

Question: What is the difference between RUN and CMD?
Answer: RUN executes a command during the image build process, while CMD specifies the default command to run when a container starts. RUN instructions are used to create layers, whereas CMD instructions are for the runtime configuration.

Question: Write a Dockerfile for an Nginx application.
Answer:

dockerfile
Copy code
FROM nginx:latest
COPY ./html /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
Question: What is the difference between Docker images and Docker containers?
Answer: A Docker image is a lightweight, standalone, and immutable package that includes the code, runtime, and dependencies needed to run an application. A Docker container is a runtime instance of an image, which means a container is the actual running environment.

Question: What are the benefits and use cases of using multi-stage builds in Docker?
Answer: Multi-stage builds reduce the final image size, improve security by only including necessary artifacts, and optimize build time by separating the build and runtime environments.

Question: How does Docker handle resource limitations and isolation, such as CPU, memory, and I/O?
Answer: Docker uses Linux cgroups to control and limit resources like CPU, memory, and I/O. You can specify resource limits with flags like --memory, --cpus, and --blkio-weight when running a container.

Question: Docker command: COPY vs ADD.
Answer: COPY simply copies files from the host to the container, while ADD has additional features like extracting local tar files and downloading files from URLs.

Question: ENTRYPOINT vs CMD in Dockerfile.
Answer: ENTRYPOINT sets the default application that will run, and any arguments passed will be appended to it, whereas CMD sets the default command and can be overridden by passing arguments during docker run. ENTRYPOINT is preferred when you always want the container to run the same application.

Question: Tell us something about Docker Compose.
Answer: Docker Compose allows developers to define, run, and manage multi-container Docker applications. Using a docker-compose.yml file, developers can specify all necessary services and dependencies, making it easy to orchestrate complex applications.

Kubernetes Interview Questions
Question: If I want to run a specific container in a pod in Kubernetes, how do I run it?
Answer: You can run a specific container in a pod using the kubectl exec -it <pod_name> -c <container_name> -- <command> command.

Question: ENTRYPOINT vs CMD.
Answer: Same as in Docker. ENTRYPOINT is used for defining a fixed command that always runs, while CMD is for defining default arguments or commands that can be overridden.

Question: How are the pods communicating with each other?
Answer: Pods communicate with each other through a flat, cluster-wide network, where every pod gets its unique IP address. Kubernetes uses services or DNS to enable communication between pods.

Question: What will you do to make your application more secure?
Answer: To secure an application in Kubernetes, you can use network policies, role-based access control (RBAC), secrets management, pod security policies, and ensuring images are scanned for vulnerabilities.

Question: What is a namespace in Kubernetes?
Answer: A namespace is a way to divide cluster resources between multiple users or teams. It provides a scope for resources, helping to organize and isolate groups of resources within a cluster.

Question: What is a pod security policy?
Answer: A pod security policy is a Kubernetes resource that defines a set of conditions pods must meet to be allowed to run, ensuring security best practices, like restricting privileged containers.

Question: How will you implement security for a running container if you find a vulnerability?
Answer: If a vulnerability is found, patch the base image, update the container image with the fix, and redeploy the container. You can also use Kubernetes security mechanisms like network policies, pod security policies, and ensuring minimal privileges are used.

Question: What are the various things that can be done to increase Kubernetes security?
Answer: Kubernetes security can be enhanced through the use of network policies, RBAC, encryption of secrets, image scanning, audit logs, and controlling access to the API server.

Question: What problems have you faced?
Answer: Answer varies by individual experience. It could include issues with scaling, networking, etc.

Question: How often do you release the product?
Answer: Answer varies by individual experience. Could be weekly, monthly, or based on CI/CD pipeline policies.

Question: What Kubernetes issues have you encountered in production?
Answer: Common issues include pod evictions, CrashLoopBackOff errors, and scaling problems due to improper resource allocation or network failures.

Question: What is the architecture of Kubernetes?
Answer: Kubernetes architecture consists of a master node and worker nodes. The master node manages the cluster and its components like the API server, etcd, and controllers. Worker nodes run the actual applications in containers.

Question: How is the pod health check done in Kubernetes?
Answer: Kubernetes uses liveness and readiness probes to check the health of pods. Liveness probes restart a pod if it becomes unresponsive, while readiness probes ensure that traffic is only routed to healthy pods.

Question: How do you use Helm charts?
Answer: Helm charts are used to define, install, and upgrade Kubernetes applications. Helm makes it easy to deploy complex applications by packaging Kubernetes resources and enabling version control.

Question: What is the Blue/Green Deployment Pattern?
Answer: Blue/Green deployment involves running two versions of an application (blue for old, green for new) and switching traffic from the old version to the new one once it is ready. It minimizes downtime and ensures smooth updates.

Question: Can you explain the concept of auto-healing in Kubernetes and give examples of how it works?
Answer: Auto-healing in Kubernetes refers to its ability to automatically restart failed containers and replace unhealthy pods. This is achieved through controllers like the ReplicationController and ReplicaSet.

Question: What is a label and selector in Kubernetes?
Answer: Labels are key-value pairs attached to Kubernetes objects for identification. Selectors are used to group objects based on these labels for purposes like service discovery and replication.

Question: What is the CrashLoopBackOff state in a pod?
Answer: CrashLoopBackOff indicates that a pod is repeatedly failing and Kubernetes is backing off from restarting it. This can be due to application misconfigurations or runtime errors.

Question: What is Kubernetes Ingress?
Answer: Ingress is an API object in Kubernetes that manages external access to services, typically HTTP/HTTPS traffic, and provides load balancing, SSL termination, and name-based virtual hosting.

Question: What are Kubernetes ConfigMaps and Secrets?
Answer: ConfigMaps store non-sensitive configuration data, while Secrets store sensitive data such as passwords or tokens. Both are used to configure applications without embedding data into images.

Question: How do microservices work?
Answer: Microservices break down a large application into smaller, loosely coupled services that can be developed, deployed, and scaled independently, communicating over APIs.

Question: How do you debug your existing container?
Answer: You can debug a container by running kubectl exec to interact with the container, checking logs using kubectl logs, or inspecting events with kubectl describe.

Question: What is a DaemonSet?
Answer: A DaemonSet ensures that a copy of a pod is running on each node in the Kubernetes cluster. It's typically used for tasks like log collection and node monitoring.

Question: How do you upgrade the database and cluster in Kubernetes?
Answer: For upgrading, you can create backup snapshots, scale down services, perform rolling updates, and upgrade the database using automated Helm charts or custom scripts.

Question: How do you design your pods to be highly available?
Answer: High availability in pods is achieved by using replicas in deployments, distributing them across multiple nodes, and using services with load balancers to ensure continuous access.

Question: What is the Kubernetes version you are using?
Answer: Answer varies depending on the version of Kubernetes being used in your environment (e.g., v1.24).

Question: What is the difference between StatefulSets and Deployments in Kubernetes?
Answer: Deployments are used for stateless applications, while StatefulSets are used for stateful applications that require stable network identities and persistent storage.

Question: Have you done the backup of etcd?
Answer: Yes, etcd backups can be performed using etcdctl snapshot save to store cluster state and configuration data for recovery in case of failure.

