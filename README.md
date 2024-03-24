# Simple Python Docker App with Volume Mounting via Docker Compose

Simple Python Docker app which prints a message to console. The app is run in a Docker container with the current directory mounted to the container.

## Open a Terminal in the Docker Container and Mount the Current Directory There

```bash
flynntknapp@DELL-GAME-DESK:~/Programming/python-simple-script-compose$ docker run -it -v $(pwd):/app -w /app python:3 bash
Unable to find image 'python:3' locally
3: Pulling from library/python
71215d55680c: Pull complete 
3cb8f9c23302: Pull complete 
5f899db30843: Pull complete 
567db630df8d: Pull complete 
d68cd2123173: Pull complete 
63941d09e532: Pull complete 
097431623722: Pull complete 
09527fa4de8d: Pull complete 
Digest: sha256:336461f63f4eb1100e178d5acbfea3d1a5b2a53dea88aa0f9b8482d4d02e981c
Status: Downloaded newer image for python:3
root@3fee8ca119bb:/app# pip list
Package    Version
---------- -------
pip        24.0
setuptools 69.1.1
wheel      0.43.0
root@3fee8ca119bb:/app# cat goodbuy.py 
def main():
    print(f"Goodbuy, World! Enjoy the sails and bar guns!")


if __name__ == "__main__":
    main()
root@3fee8ca119bb:/app# python goodbuy.py 
Goodbuy, World! Enjoy the sails and bar guns!
root@3fee8ca119bb:/app# exit
exit
flynntknapp@DELL-GAME-DESK:~/Programming/python-simple-script-compose$
```

1. `docker run -it -v $(pwd):/app -w /app python:3 bash`
    - `docker` is the command to interact with the Docker daemon.
    - `run` is the command to run a command in a new container.
    - `-it` is the flag to run the container in interactive mode and allocate a pseudo-TTY.
    - `-v $(pwd):/app` is the flag to mount the current directory to the `/app` directory in the container.
    - `-w /app` is the flag to set the working directory to `/app` in the container.
    - `python:3` is the name of the Docker image to use for the container.
    - `bash` is the command to run in the container.
1. `python goodbuy.py`
    - `python` is the command to run the Python interpreter.
    - `goodbuy.py` is the Python script to run.
1. `pip list`
    - `pip` is the command to interact with the Python package manager.
    - `list` is the command to list the installed Python packages.

## Run the Application

1. `docker compose -f docker-compose.yml up --build`
    - `docker` is the command to interact with the Docker daemon.
    - `compose` is the command to interact with Docker Compose.
    - `-f` specifies the file to use for the Docker Compose configuration.
    - `docker-compose.yml` is the file to use for the Docker Compose configuration.
    - `up` is the command to start the services defined in the Docker Compose configuration.
    - `--build` is the flag to build the Docker images before starting the services.

```powershell
flynntknapp@DELL-GAME-DESK:~/Programming/python-simple-script-compose$ docker compose -f docker-compose.yml up --build
[+] Building 1.7s (9/9) FINISHED                                                              docker:default
 => [goodbuy-app internal] load build definition from Dockerfile                                        0.0s
 => => transferring dockerfile: 390B                                                                    0.0s
 => [goodbuy-app internal] load metadata for docker.io/library/python:3.9-alpine                        1.0s
 => [goodbuy-app internal] load .dockerignore                                                           0.0s
 => => transferring context: 2B                                                                         0.0s
 => [goodbuy-app 1/4] FROM docker.io/library/python:3.9-alpine@sha256:9c67be172ccdb634540db2dc90d44429  0.0s
 => [goodbuy-app internal] load build context                                                           0.0s
 => => transferring context: 7.66kB                                                                     0.0s
 => CACHED [goodbuy-app 2/4] WORKDIR /usr/src/app                                                       0.0s
 => [goodbuy-app 3/4] COPY . .                                                                          0.1s
 => [goodbuy-app 4/4] RUN chmod +x goodbuy.py                                                           0.3s
 => [goodbuy-app] exporting to image                                                                    0.1s
 => => exporting layers                                                                                 0.1s
 => => writing image sha256:512a8b1c9eaf6e6cea8ab8a4c7bdb3070777a74b7c88818b0c6ab911a2b50684            0.0s
 => => naming to docker.io/library/python-simple-script-compose-goodbuy-app                             0.0s
[+] Running 2/1
 ✔ Network python-simple-script-compose_default          Created                                        0.1s 
 ✔ Container python-simple-script-compose-goodbuy-app-1  Created                                        0.1s 
Attaching to goodbuy-app-1
goodbuy-app-1  | Goodbuy, World! Enjoy the sails and bar guns!
goodbuy-app-1 exited with code 0
flynntknapp@DELL-GAME-DESK:~/Programming/python-simple-script-compose$
```

1. `docker compose -f docker-compose.yml down --remove-orphans`
    - `docker` is the command to interact with the Docker daemon.
    - `compose` is the command to interact with Docker Compose.
    - `-f` specifies the file to use for the Docker Compose configuration.
    - `docker-compose.yml` is the file to use for the Docker Compose configuration.
    - `down` is the command to stop the services defined in the Docker Compose configuration.
    - `--remove-orphans` is the flag to remove any orphaned services that are not defined in the Docker Compose configuration.

```powershell
flynntknapp@DELL-GAME-DESK:~/Programming/python-simple-script-compose$ docker compose -f docker-compose.yml down --remove-orphans
[+] Running 2/2
 ✔ Container python-simple-script-compose-goodbuy-app-1  Removed                                        0.0s 
 ✔ Network python-simple-script-compose_default          Removed                                        0.2s 
flynntknapp@DELL-GAME-DESK:~/Programming/python-simple-script-compose$
```
