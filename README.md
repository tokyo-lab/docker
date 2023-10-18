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

## Stop Container

The docker stop command is used to stop one or more running containers. CONTAINER can be the container ID or name.

```sh
docker stop [OPTIONS] CONTAINER [CONTAINER...]
```

## Other common commands for containers

list the containers that are currently running on your system

```sh
docker ps
```

displays the running processes within a specific container

```sh
docker top CONTAINER [ps OPTIONS]

```

```

```
