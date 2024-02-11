# Simple Python Docker App with Volume Mounting via Docker Compose

Python simple CLI app in Docker container with `docker-compose.yml`.

1. `docker run -it -v $(pwd):/app -w /app python:3 bash`
    - `docker` is the command to interact with the Docker daemon.
    - `run` is the command to run a command in a new container.
    - `-it` is the flag to run the container in interactive mode and allocate a pseudo-TTY.
    - `-v $(pwd):/app` is the flag to mount the current directory to the `/app` directory in the container.
    - `-w /app` is the flag to set the working directory to `/app` in the container.
    - `python:3` is the name of the Docker image to use for the container.
    - `bash` is the command to run in the container.



## Run the Application

1. `docker compose -f docker-compose.yml up --build`
    - `docker` is the command to interact with the Docker daemon.
    - `compose` is the command to interact with Docker Compose.
    - `-f` specifies the file to use for the Docker Compose configuration.
    - `docker-compose.yml` is the file to use for the Docker Compose configuration.
    - `up` is the command to start the services defined in the Docker Compose configuration.
    - `--build` is the flag to build the Docker images before starting the services.
1. `docker compose -f docker-compose.yml down --remove-orphans`
    - `docker` is the command to interact with the Docker daemon.
    - `compose` is the command to interact with Docker Compose.
    - `-f` specifies the file to use for the Docker Compose configuration.
    - `docker-compose.yml` is the file to use for the Docker Compose configuration.
    - `down` is the command to stop the services defined in the Docker Compose configuration.
    - `--remove-orphans` is the flag to remove any orphaned services that are not defined in the Docker Compose configuration.
