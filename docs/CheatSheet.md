## Cheatsheet for Docker Commands
# Docker Command Cheatsheet

## Docker Images
Commands related to images, such as downloading, listing, or deleting images, fall under **docker image** commands. These commands deal with managing Docker images, which are like templates used to create containers.

- **List Images**:
  ```sh
  docker image ls
  ```
  Lists all available images on your system.

- **Pull an Image**:
  ```sh
  docker image pull [image_name]
  ```
  Downloads an image from the default Docker registry (Docker Hub).

- **Remove an Image**:
  ```sh
  docker image rm [image_name]
  ```
  Deletes the specified image from your system.

## Docker Containers
Commands related to running, managing, and interacting with containers fall under **docker container** commands. Containers are running instances of images and perform the tasks you specify.

- **Run a Container**:
  ```sh
  docker container run [image_name]
  ```
  Creates and starts a container from the specified image. You can add `-it` to run it interactively, or `-d` to run it in the background.

- **List Running Containers**:
  ```sh
  docker container ls
  ```
  Lists all running containers. Use the `-a` flag to list all containers, including stopped ones.

- **Start a Stopped Container**:
  ```sh
  docker container start [container_id]
  ```
  Restarts an existing container that has been stopped.

- **Run a Command Inside a Running Container**:
  ```sh
  docker exec -it [container_id] [command]
  ```
  Runs a specified command in a running container, e.g., `/bin/sh` to access a shell.

- **Stop a Container**:
  ```sh
  docker container stop [container_id]
  ```
  Stops a running container.

- **Remove a Container**:
  ```sh
  docker container rm [container_id]
  ```
  Deletes the specified container.

## Investigating Containers
These commands help you inspect and monitor containers.

- **View Processes in a Container**:
  ```sh
  docker exec -it [container_id] ps aux
  ```
  Views running processes in the container. You can use other Linux commands like `top` or `htop` if they are installed.

- **Inspect Container Details**:
  ```sh
  docker inspect [container_id]
  ```
  Provides detailed information about the container, such as network settings, volume mounts, and more.

- **View Resource Usage**:
  ```sh
  docker stats [container_id]
  ```
  Provides real-time resource usage statistics (CPU, memory, network) of running containers. Press `CTRL+c` to stop viewing.

## Additional Helpful Commands
- **Docker General Help**:
  ```sh
  docker --help
  ```
  Displays all available Docker commands. Use this to find which commands are available at each level (e.g., `docker image --help`).

- **Help for Specific Commands**:
  ```sh
  docker [command] --help
  ```
  Provides detailed help for a specific Docker command, such as usage examples and available flags.

## Common Scenarios
- **Running Commands in Containers**: When you need to execute a command in a container, use `docker exec`. For example, to open a shell interactively, use `docker exec -it [container_id] /bin/sh`.

- **Monitoring Container Resource Usage**: To check how much CPU or memory a container is using, run `docker stats`. This is helpful to understand performance and resource limitations.

- **Starting Containers in Background**: Use `docker container run -d [image_name]` to run a container in detached mode, which allows you to continue using your terminal while the container runs in the background.

---

This cheatsheet should help your students navigate Docker commands related to images, containers, and their operations. Let me know if you'd like to expand on any particular command or add more advanced Docker concepts!

