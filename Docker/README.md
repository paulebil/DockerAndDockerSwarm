### Docker Cheat Sheet


#### System

| Command | Description |
|:---|:---|
| `docker info` | Display system-wide information. |
| `docker version` | Show the Docker version information. |
| `docker login` | Log in to a Docker registry. |
| `docker logout` | Log out from a Docker registry. |
| `docker system prune` | Remove unused containers, images, and networks. |
| `docker system df` | Show Docker disk usage. |

***

#### Containers

| Command | Description |
|:---|:---|
| `docker run <image>` | Run a container from an image. |
| `docker run -d <image>` | Run a container in detached mode (in the background). |
| `docker ps` | List all running containers. |
| `docker ps -a` | List all containers, including stopped ones. |
| `docker ps -aq` | List all containers_ids. |
| `docker stop <container_id>` | Stop a running container. |
| `docker start <container_id>` | Start a stopped container. |
| `docker rm <container_id>` | Remove a container. |
| `docker exec -it <container_id> <command>` | Run a command inside a running container. |
| `docker logs <container_id>` | View the logs of a container. |

***

#### Volumes

| Command | Description |
|:---|:---|
| `docker volume create <volume_name>` | Create a new volume. |
| `docker volume ls` | List all volumes. |
| `docker volume inspect <volume_name>` | Display detailed information about a volume. |
| `docker volume rm <volume_name>` | Remove a volume. |
| `docker volume prune` | Remove all unused local volumes. |

***

#### Networks

| Command | Description |
|:---|:---|
| `docker network create <network_name>` | Create a new network. |
| `docker network ls` | List all networks. |
| `docker network inspect <network_name>` | Display detailed information about a network. |
| `docker network connect <network_name> <container_id>` | Connect a container to a network. |
| `docker network disconnect <network_name> <container_id>` | Disconnect a container from a network. |
| `docker network rm <network_name>` | Remove a network. |

***

#### Images

| Command | Description |
|:---|:---|
| `docker images` | List all local Docker images. |
| `docker build -t <tag> .` | Build an image from a Dockerfile in the current directory. |
| `docker pull <image_name>` | Pull an image from a registry. |
| `docker push <image_name>` | Push an image to a registry. |
| `docker rmi <image_id>` | Remove a Docker image. |
| `docker history <image_id>` | Show the history of an image. |
| `docker tag <source_image>:<tag> <target_image>:<tag>` | Create a tag `target_image` that refers to `source_image`. |

***

## Quick Guides
>Note: Be careful with these commands as some of them are dangerous and can remove every container on your system even when they're not in use leading to loss of data especially command 2, all of them  and command 8


#### 1. Stop and remove all Containers

```
docker rm -f $(docker ps -aq)
```

#### 2. Remove All Docker volumes
```
docker  volume rm $(docker volumes ls -q)

        or

docker system prune --volumes -f
```

#### 3. Remove all Docker Images
```
docker rmi -f $(docker images -q)
```

#### 4. Remove all Docker Networks forcefully
```
docker network prune -f
``` 

#### 5. Rebuild containers from strach
```
docker compose up --build --force-recreate
```

#### 6. Check Docker status
```
sytemctl status docker

```

#### 7. Start the docker service
```
sudo systemctl start docker
```

#### 8. Remove Everything (Full reset)
```
docker system prune -a --volumes -f
```