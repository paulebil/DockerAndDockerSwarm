### Docker Compose Cheat Sheet

#### Basic Commands

| Command | Description |
|:---|:---|
| `docker compose up` | Build, create, and start containers defined in `docker-compose.yml`. |
| `docker compose up -d` | Run containers in detached mode (in the background). |
| `docker compose down` | Stop and remove containers, networks, and volumes created by `up`. |
| `docker compose start` | Start existing containers for a service. |
| `docker compose stop` | Stop running containers without removing them. |
| `docker compose ps` | List containers and their current state for the current project. |
| `docker compose logs` | View the output logs from services. |
| `docker compose build` | Build or rebuild services. |
| `docker compose pull` | Pull service images. |
| `docker compose exec <SERVICE> <COMMAND>` | Run a command in a running container. |
| `docker compose exec <SERVICE> <COMMAND> bash` | Enter inside the container bash terminal. |

***

#### Common `docker-compose.yml` Directives

| Directive | Description |
|:---|:---|
| `image` | Specify the image to use for the service. |
| `build` | Define the path to a Dockerfile for building the image. |
| `ports` | Expose ports from the container to the host. |
| `volumes` | Mount host paths or named volumes into the container. |
| `networks` | Attach the service to specific networks. |
| `environment` | Set environment variables in the container. |
| `depends_on` | Specify a dependency on another service. |
| `restart` | Define a restart policy (`no`, `always`, `on-failure`, `unless-stopped`). |
| `container_name` | Assign a custom name to the container. |
| `command` | Override the default command defined in the Dockerfile. |

#### Example compose file

```
version: '3.8'
services:
  web:
    image: nginx:latest
    container_name: my-nginx-web
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
    restart: always

  db:
    image: postgres:13
    environment:
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=password
      - POSTGRES_DB=mydb
    volumes:
      - db_data:/var/lib/postgresql/data
    restart: unless-stopped

volumes:
  db_data:
```