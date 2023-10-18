# docker

Sample docker configs and other explorations

# Source Code

https://github.com/BretFisher/udemy-docker-mastery

Useful Information:

https://docs.docker.com/

# Docker Containers

## Create a container

The docker command below downloads image 'nginx' from Docker Hub. It starts a new container from that image. Opens port 8000 on the host IP. Routes that traffic to the container IP, port 80.

```sh
docker container run --publish 8000:80 nginx
```

## Create a container in the background

To run the container in the background,add th detach keyword:

Start an nginx:

```sh
docker container run --publish 8000:80 --detach nginx
```

Start a mongo database. Lets call it mongoand its detached:

```sh
docker run --name mongo -d mongo
```

Start a mysql database and pass enviornment variable for root password:

```sh
docker container run --name mysql --publish 3306:3306 -d mysql -e MYSQL_RANDOM_ROOT_PASSWORD=yes
```

## List running containers:

```sh
docker container ls
```

OR

```sh
docker ps
```

## Stop Container

The docker stop command is used to stop one or more running containers. CONTAINER can be the container ID or name.

```sh
docker stop [OPTIONS] CONTAINER [CONTAINER...]
```

## Other common commands for containers

list the containers that are currently running on your system:

```sh
docker ps
```

displays the running processes within a specific container:

```sh
docker top CONTAINER [ps OPTIONS]

```

The command docker container top displays the running processes inside a specific container.CONTAINER can be the container ID or name:

```sh
docker container top CONTAINER

```

The docker container inspect command provides detailed information on your container configuration, including the network settings, volume mappings, restart policies, resource limits, and more:

```sh
docker container inspect CONTAINER

```

This command is particularly useful when you're trying to understand the resource footprint of your running containers, or when you're diagnosing performance issues:

```sh
docker container stats CONTAINER

```

The docker container run command is used to create and run a container based on a specified image. The -it flag is actually two flags, -i and -t, used together.

-i or --interactive: This flag keeps STDIN open even if not attached, which allows you to interact with the container.
-t or --tty: This flag allocates a pseudo-TTY or terminal inside the new container.

```sh
docker container run -it IMAGE COMMAND [ARG...]

i.e. docker container run -it ubuntu bash
```

The docker container exec command is used to execute a command inside an already running container. The -it flag is a combination of two flags:

-i or --interactive: Keeps STDIN open even if not attached. This means you can interact with the command line interface of the running container.
-t or --tty: Allocates a pseudo-TTY or terminal. This is what allows you to send commands to the container and receive output like you're interacting with a normal terminal.

```sh
docker container exec -it IMAGE COMMAND [ARG...]

i.e. docker container exec -it ubuntu bash
```

## Networks for Containers

Start a container:

```sh
docker container run -p 8000:80 --name webhost -d nginx
```

View a specific container port:

```sh
docker container port webhost
```

View all networks created:

```sh
docker network ls
```

The docker network inspect command provides detailed information about a Docker network. Docker has a concept of networks to allow different containers to communicate and isolate traffic in a controlled way. The "bridge" network is a default network that Docker sets up on installation and which containers connect to by default if no network is specified.

Here's how you use the command to inspect the "bridge" network:

```sh
docker network inspect bridge

```

The docker network create command is used to create a new network. This is useful when you want to establish communication between containers while providing network isolation. When you create a new network, it allows you to have more control over how the containers communicate with each other and with the outside world.

Here's how you use the command to create a new network named "my_app_net":

```sh
docker network create my_app_net


```

Run a new container in detached mode using the official "nginx" image, names the container "new_nginx", and connects it to the "my_app_net" network:

```sh
docker container run -d --name new_nginx --network my_app_net nginx
```
