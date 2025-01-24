# Containers

**Containers** are a package containing an application, its dependencies, and the underlying system libraries required for it to run. They are lightweight and efficiently utilize resources from the host system. Multiple containers can share the resources of the host machine, such as the operating system kernel, while remaining isolated from one another.

# Docker

**Docker** is a containerization platform that provides an easy way to containerize(package) our application into a light weight images, run the images to create the containers for running the application, and also push the image to different registries such as Dockerhub AWS ECR, etc.


# Terminologies

### Docker Daemon
**Docker Daemon(Dockerd)** is a heart of docker. When we install docker in out host system, we are technically installing the docker daemon. Docker demon accepts the commands provided via docker client(Docker CLI) and acts upon the command respectively.

### Docker client
**Docker client** is basically a platform or medium via which a user can communicate with docker daemon. Docker client provides a platform where user can type the docker commands and send the intruction to the docker daemon which in response executes the command and performs the requested action. Docker CLI is an example of docker client.# Containers

### Docker Desktop
**Docker Desktop** is an easy to use GUI application that helps to perform all the docker actions such as running images, list the containers, build the docker image, etc. It's a bit equivalent to installing docker from terminal, but Docker Desktop provdes more flexibility and more complex worflow as compared to installing docker from terminal.
Moreover, Docker Desktop is more suited for Windows or MAC operating systems since command line is more native to Linux environments.

### Docker Registries
**Docker Registries** are nothing but a repository for docker images. Like GitHub is a repository where we can push and store our application code, Docker registries is a repository where we can push our images and store. Examples can be, DockerHub, AWS ECR, etc.

### Dockerfile
**Dockerfile** is a mechanism to create a docker image. It contains a set of instructions on how the docker image should be created. Dockerfiles are essential for containerizing applications, ensuring consistency across different environments, and enabling easy deployment.

### Image
**Image** is like a blueprint or template for creating containers. It contains everything an application needs to run, including:
   - The application code.
   - System tools and libraries.
   - Dependencies.

We can think of it as a read-only package that defines the environment and instructions to run our application. When we run a image, it becomes a container, which is a running instance of the image.

### .dockerignore
The concept of dockerignore in docker is same as gitignore in git. As in git the files and folders listed in gitignore is not pushed to the repository, likewise the files and folders listed in docker ignore is not included in the docker image. For example, Dockerfile itself is not needed in the docker image, so we can put the Dockerfile in the dockerinore file.









