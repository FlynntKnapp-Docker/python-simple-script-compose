# Simple Python Docker App with Volume Mounting via Docker Compose

Python simple CLI app in Docker container with `docker-compose.yml`.

1. `docker run -it -v $(pwd):/app -w /app python:3 bash`



## Run the Application

1. `docker compose -f docker-compose.yml up --build`
    - `docker` is the command to interact with the Docker daemon.
    - `compose` is the command to interact with Docker Compose.
    - `-f` specifies the file to use for the Docker Compose configuration.
    - `docker-compose.yml` is the file to use for the Docker Compose configuration.
    - `up` is the command to start the services defined in the Docker Compose configuration.
    - `--build` is the flag to build the Docker images before starting the services.
1. `docker compose -f docker-compose.yml down`
    - `down` is the command to stop the services defined in the Docker Compose configuration.
    - `docker compose -f docker-compose.yml down -v --remove-orphans`
        - `-v` is the flag to remove the volumes associated with the services defined in the Docker Compose configuration.
        - `--remove-orphans` is the flag to remove any orphaned services defined in the Docker Compose configuration.


[https://github.com/FlynntKnapp-Docker/python-simple-script](https://github.com/FlynntKnapp-Docker/python-simple-script)
