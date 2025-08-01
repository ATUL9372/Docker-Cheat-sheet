# Advanced Docker Commands

1. **Check Running Docker Compose Projects**:
   ```bash
   docker ps --format "{{.Names}}" | xargs -I {} docker inspect {} --format '{{index .Config.Labels "com.docker.compose.project.working_dir"}}'

2 **Check Compose File Path Using Labels**:
   ```bash
   docker inspect <ENTER-YOUR-CONTAINER-NAME> --format '{{index .Config.Labels "com.docker.compose.project.config_files"}}'
   ```
3 **Delete All Docker Images That Start With a Specific Name**:
   ```bash
   docker images --format "{{.Repository}}:{{.Tag}}" | grep '^ENTER_YOUR_IMAGE_NAME' | xargs -r docker rmi -f
   ```

# Docker Cheatsheet

## Basic Docker Commands

| Command                             | Description                                      |
|-------------------------------------|--------------------------------------------------|
| `docker version`                    | Show Docker version information.                 |
| `docker info`                       | Display system-wide information about Docker.    |
| `docker help`                       | List available Docker commands.                  |

## Images

| Command                             | Description                                      |
|-------------------------------------|--------------------------------------------------|
| `docker images`                     | List all Docker images on your system.           |
| `docker search <image>`             | Search for an image on Docker Hub.               |
| `docker pull <image>`               | Download an image from a repository.             |
| `docker rmi <image>`                | Remove a Docker image.                           |
| `docker image prune`                | Remove unused images.                            |
| `docker tag <image> <new_tag>`      | Add a tag to an image.                           |

## Containers

| Command                             | Description                                      |
|-------------------------------------|--------------------------------------------------|
| `docker ps`                         | List running containers.                         |
| `docker ps -a`                      | List all containers (including stopped ones).    |
| `docker run <image>`                | Run a container from an image.                   |
| `docker run -it <image>`            | Run a container in interactive mode (with shell).|
| `docker run -d <image>`             | Run a container in detached mode.                |
| `docker run --name <name> <image>`  | Run a container with a custom name.              |
| `docker start <container>`          | Start a stopped container.                       |
| `docker stop <container>`           | Stop a running container.                        |
| `docker restart <container>`        | Restart a container.                             |
| `docker rm <container>`             | Remove a container.                              |
| `docker container prune`            | Remove all stopped containers.                   |
| `docker exec -it <container> <cmd>` | Execute a command inside a running container.    |
| `docker logs <container>`           | View the logs of a container.                    |
| `docker inspect <container>`        | Get detailed information about a container.      |

## Networks

| Command                                    | Description                                    |
|--------------------------------------------|------------------------------------------------|
| `docker network ls`                        | List all Docker networks.                      |
| `docker network create <network>`          | Create a new network.                          |
| `docker network rm <network>`              | Remove a network.                              |
| `docker network connect <network> <cont>`  | Connect a container to a network.              |
| `docker network disconnect <network> <cont>` | Disconnect a container from a network.        |

## Volumes

| Command                                     | Description                                    |
|---------------------------------------------|------------------------------------------------|
| `docker volume ls`                          | List all Docker volumes.                       |
| `docker volume create <volume>`             | Create a new volume.                           |
| `docker volume rm <volume>`                 | Remove a volume.                               |
| `docker volume inspect <volume>`            | View detailed information about a volume.      |
| `docker run -v <volume>:/path <image>`      | Mount a volume in a container.                 |
| `docker volume prune`                       | Remove all unused volumes.                     |

## Images Building and Management

| Command                                  | Description                                    |
|------------------------------------------|------------------------------------------------|
| `docker build -t <tag> <path>`           | Build an image from a Dockerfile.              |
| `docker commit <container> <new_image>`  | Create a new image from a container’s changes. |
| `docker history <image>`                 | Show the history of an image.                  |
| `docker save -o <file>.tar <image>`      | Save an image to a tar file.                   |
| `docker load -i <file>.tar`              | Load an image from a tar file.                 |
| `docker push <repo>:<tag>`               | Push an image to a Docker registry.            |
| `docker pull <repo>:<tag>`               | Pull an image from a Docker registry.          |

## Dockerfile Directives

| Instruction                   | Description                                      |
|-------------------------------|--------------------------------------------------|
| `FROM <image>`                 | Base image to use.                              |
| `COPY <src> <dest>`            | Copy files from host to container.              |
| `ADD <src> <dest>`             | Copy files and unpack archives.                 |
| `RUN <command>`                | Execute command inside the image.               |
| `CMD <command>`                | Command to run when container starts.           |
| `ENTRYPOINT <command>`         | Set the entry point for the container.          |
| `ENV <key> <value>`            | Set environment variables.                      |
| `EXPOSE <port>`                | Specify ports to expose.                        |
| `WORKDIR <path>`               | Set working directory inside the container.     |
| `USER <user>`                  | Set the user for running commands.              |

## Docker Compose

| Command                                    | Description                                    |
|--------------------------------------------|------------------------------------------------|
| `docker-compose up`                        | Start services defined in `docker-compose.yml`. |
| `docker-compose down`                      | Stop and remove containers, networks, etc.     |
| `docker-compose build`                     | Build images defined in `docker-compose.yml`.   |
| `docker-compose up -d`                     | Start services in detached mode.               |
| `docker-compose stop`                      | Stop running services.                         |
| `docker-compose start`                     | Start stopped services.                        |
| `docker-compose restart`                   | Restart services.                              |
| `docker-compose logs`                      | View logs for all services.                    |
| `docker-compose ps`                        | List containers managed by Docker Compose.     |
| `docker-compose exec <service> <cmd>`      | Execute a command in a running service.        |
| `docker-compose run <service> <cmd>`       | Run a one-off command in a service.            |

## Docker Swarm (for Orchestration)

| Command                             | Description                                      |
|-------------------------------------|--------------------------------------------------|
| `docker swarm init`                 | Initialize a new swarm.                          |
| `docker swarm join`                 | Join an existing swarm as a node.                |
| `docker swarm leave`                | Leave a swarm.                                   |
| `docker service create`             | Create a new service in the swarm.               |
| `docker service ls`                 | List all services in the swarm.                  |
| `docker service scale <service>=N`  | Scale a service to N replicas.                   |
| `docker node ls`                    | List all nodes in the swarm.                     |
| `docker stack deploy -c <file>`     | Deploy a stack using a Compose file.             |
| `docker stack rm <name>`            | Remove a stack.                                  |

## Debugging & Monitoring

| Command                                 | Description                                      |
|-----------------------------------------|--------------------------------------------------|
| `docker stats`                          | Display a live stream of container resource usage.|
| `docker top <container>`                | Display running processes inside a container.    |
| `docker events`                         | Get real-time events from the Docker daemon.     |
| `docker diff <container>`               | Inspect changes to files or directories.         |

## Tips & Tricks

0. **Check Running Docker Compose Projects**:
   ```bash
   docker ps --format "{{.Names}}" | xargs -I {} docker inspect {} --format '{{index .Config.Labels "com.docker.compose.project.working_dir"}}'

0.0 **Check Compose File Path Using Labels**:
   ```bash
   docker inspect <ENTER-YOUR-CONTAINER-NAME> --format '{{index .Config.Labels "com.docker.compose.project.config_files"}}'
   ```

   
1. **Stop all running containers**:
   ```bash
   docker stop $(docker ps -q)
   ```

2. **Remove all containers**:
   ```bash
   docker rm $(docker ps -aq)
   ```

3. **Remove all images**:
   ```bash
   docker rmi $(docker images -q)
   ```

4. **Remove all volumes**:
   ```bash
   docker volume rm $(docker volume ls -q)
   ```

5. **Remove dangling/unused images**:
   ```bash
   docker image prune -f
   ```

6. **Log in to Docker Hub**:
   ```bash
   docker login
   ```
   
