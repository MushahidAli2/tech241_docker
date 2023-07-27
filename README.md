# Docker Documentation

## What is Docker?

Docker is an open-source platform that enables you to automate the deployment, scaling, and management of applications using containerization. Containerization is a lightweight approach to virtualization that packages applications along with their dependencies and configurations into containers, ensuring consistent and reproducible execution across different environments.

## Why is Docker Useful?

- **Consistency**: Docker ensures that your application runs consistently in any environment, reducing the "works on my machine" problem and minimizing environment-related issues.

- **Isolation**: Containers provide a secure and isolated environment for applications, preventing conflicts between applications and their dependencies.

- **Resource Efficiency**: Docker containers share the host OS kernel, making them lightweight and efficient in terms of resource usage compared to traditional virtual machines.

- **Rapid Deployment**: Docker allows you to package your application and its dependencies into a single container, making deployment quick and straightforward.

- **Scalability**: Docker containers can be easily scaled up or down to meet changing demands without significant overhead.

- **Version Control**: Docker images can be versioned and stored in repositories, allowing you to track changes and roll back to previous versions when needed.

- **Easy Collaboration**: Docker simplifies collaboration among developers by providing a consistent development environment and facilitating the sharing of containerized applications.

## How Containerization Works on Docker?

Containerization in Docker is achieved through the use of container images. An image is a lightweight, stand-alone, and executable software package that includes everything needed to run a piece of software, including the code, runtime, libraries, environment variables, and system tools.

Here's how containerization works on Docker:

1. **Dockerfile**: Developers create a Dockerfile, which is a text file that defines the instructions to build the Docker image. The Dockerfile specifies the base image, sets up the application environment, copies files into the container, and defines the commands to run the application.

2. **Build Image**: Using the Dockerfile, developers build a Docker image. The Docker image is a snapshot of the application along with its dependencies and configurations.

3. **Docker Image Registry**: The Docker image can be stored in a registry like Docker Hub or a private registry. Registries allow you to share and distribute Docker images with others.

4. **Create Container**: To run the application, a Docker container is created from the Docker image. Containers are instances of Docker images that run in isolation from the host system and other containers.

5. **Runtime Isolation**: Containers use namespaces and control groups (cgroups) to isolate the application's view of the operating system, file system, network, and other resources.

6. **Container Lifecycle**: Containers can be started, stopped, and removed as needed. When a container is stopped, any changes made to its file system are discarded, providing a clean and consistent environment for each run.

## How to Install Docker on Ubuntu Linux?

1. Update package lists:
```bash
sudo apt update
```
2. Update package lists:
```bash
sudo apt update
```
3. Install prerequisites to allow apt to use repositories over HTTPS:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
4. Add Docker's official GPG key:

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
5. Add Docker repository to apt sources:

```bash
echo "deb [signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list
```
6. Update package lists again:

```bash
sudo apt update
```
7. Install Docker:

```bash
sudo apt install docker-ce
```
8. Start and enable Docker service:

```bash
sudo systemctl start docker
sudo systemctl enable docker
```
9. Verify Docker installation:

```bash
sudo docker --version
sudo docker info
```
## Useful Docker Commands:
- Check Docker service status:

```bash
sudo systemctl status docker
```
- Add your user to the 'docker' group to run Docker commands without using sudo. Replace "your_username" with your actual username:

```bash
sudo usermod -aG docker your_username
```
- Pull and run the "hello-world" image to verify Docker installation:

```bash
sudo docker run hello-world
```
- List running containers:

```bash
sudo docker ps
```
- List all containers (including stopped ones):

```bash
sudo docker ps -a
```
- Run the "nginx" image in detached mode (-d) and map port 80 of the host to port 80 of the container:

```bash
sudo docker run -d -p 80:80 nginx
```
- Stop and start a container using its container ID or name:

```bash
sudo docker stop <container_id_or_name>
sudo docker start <container_id_or_name>
```
- Access a shell (interactive terminal) inside a running container:

```bash
sudo docker exec -it <container_id_or_name> sh
```
- Run the "ahskhan/tech221-nginx:v1" image in detached mode (-d) and map port 80 of the host to port 90 of the container:

```bash
sudo docker run -d -p 90:80 ahskhan/tech221-nginx:v1
```
- Commit changes to a running container and save them as a new Docker image:

```bash
sudo docker commit <container_id_or_name> <new_image_name>
```
- Tag a Docker image to prepare it for pushing to a registry. Replace "<new_image_name>" with the desired image name:

```bash
sudo docker tag <old_image_name> <new_image_name>
```
- Push a tagged Docker image to a container registry (e.g., Docker Hub). Replace "<yourusername>" and "<your_repository>" with your Docker Hub username and repository name, respectively, and "<tag>" with the desired version or tag:

```bash
sudo docker push <yourusername>/<your_repository>:tag
```
- Login to Docker Hub:

```bash
sudo docker login
```
- Run a previously pushed Docker image in detached mode (-d) and map port 8080 of the host to port 80 of the container:
```bash
sudo docker run -d -p 8080:80 <yourusername>/<your_repository>:tag
```