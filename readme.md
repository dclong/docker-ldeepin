# [dclong/ldeepin](https://hub.docker.com/r/dclong/deepin/)

## Prerequisite
You need to [install Docker](http://www.legendu.net/en/blog/docker-installation/) before you use this Docker image.


## Usage in Linux/Unix

Please refer to the Section
[Usage](http://www.legendu.net/en/blog/my-docker-images/#usage)
of the post [My Docker Images](http://www.legendu.net/en/blog/my-docker-images/) 
for detailed instruction on how to use the Docker image.

The following command starts a container 
and mounts the current working directory and `/home` on the host machine 
to `/workdir` and `/home_host` in the container respectively.
```
docker run -d \
    --name deepin \
    --log-opt max-size=50m \
    -p 4000:4000 \
    -e DOCKER_USER=$(id -un) \
    -e DOCKER_USER_ID=$(id -u) \
    -e DOCKER_PASSWORD=$(id -un) \
    -e DOCKER_GROUP_ID=$(id -g) \
    -v $(pwd):/workdir \
    -v $(dirname $HOME):/home_host \
    --cap-add=SYS_PTRACE \
    dclong/deepin
```
The following command does the same as the above one 
except that it limits the use of CPU and memory.
```
docker run -d \
    --name deepin \
    --log-opt max-size=50m \
    --memory=$(($(head -n 1 /proc/meminfo | awk '{print $2}') * 4 / 5))k \
    --cpus=$(($(nproc) - 1)) \
    -p 4000:4000 \
    -e DOCKER_USER=$(id -un) \
    -e DOCKER_USER_ID=$(id -u) \
    -e DOCKER_PASSWORD=$(id -un) \
    -e DOCKER_GROUP_ID=$(id -g) \
    -v $(pwd):/workdir \
    -v $(dirname $HOME):/home_host \
    --cap-add=SYS_PTRACE \
    dclong/deepin
```
A default user `dclong` with password `dclong` is used if not specified when running the docker image.

## Remote Connect to Desktop in the Container

Please refer to the section 
[Remote Connect to Desktop in the Container](http://www.legendu.net/en/blog/my-docker-images/#remote-connect-to-desktop-in-the-container)
of the post [My Docker Images](http://www.legendu.net/en/blog/my-docker-images/) 
for detailed instruction on how to use the desktop environment in the Docker image.

## [Detailed Information](http://www.legendu.net/en/blog/my-docker-images/#list-of-images-and-detailed-information) 

## [Use the JupyterHub Server](http://www.legendu.net/en/blog/my-docker-images/#use-the-jupyterhub-server)

## [Add a New User to the JupyterHub Server](http://www.legendu.net/en/blog/my-docker-images/#add-a-new-user-to-the-jupyterhub-server)

## [Known Issues](http://www.legendu.net/en/blog/my-docker-images/#known-issues)

## [About the Author](http://www.legendu.net/pages/about)
