# 1 - Build an image using Dockerfile

```sh
docker build . -t myfirstimage:1
```

NOTE: See Dockerfile in fast-track-course directory
building a new Docker image from a Dockerfile and a "context". A context is typically the set of files located in the specified path in your command, in this case, ".", which represents the current directory.

(a) 'docker build' tells Docker to build a new image.

(b) '.' indicates that the current directory is the build context. Docker will look for the Dockerfile in this location and use the files located here for the build.

(c) '-t myfirstimage:1' specifies the name and tag for the new image. The name of the image is "myfirstimage", and "1" is the tag, which is useful for versioning.

# 2 - Run a container off the image created above

```sh
docker container run myfirstimage:1
```

# 3 - RUN vs CMD vs ENTRYPOINT

- RUN exectues when building the image
- CMD and ENTRYPOINT execute when the container starts
- ENTRYPOINT determines the main thing you want to run
- CMD provides additional parameters we can pass into the entry point and they can be overriden

# 4 Different Ways Of Running Docker Files

### Docker File In a Different Path

- To run a docker image from a different path, do the following:

Get the full pathname of current working directory:

```sh
pwd
```

- Copy the path up to the part where the docker file exist and append it with the docker filename. For example currently in port directory and i want to use the dockerfile in the rce directory:

-port
---Dockerfile

-rce
---Dockerfile

pwd returns this in terminal:

/Users/michaelmena/Documents/purple.nosync/docker/fast-track-course/port

Now copy all except for 'port' and append it with rce directory where its docker file resides:

```sh
docker build /Users/michaelmena/Documents/purple.nosync/docker/fast-track-course/rce -t rce:1
```

### Docker File With Custom Name

-- In custom directory, we have a docker file named 'Dockerfile.prod'

```sh
docker build -f Dockerfile.prod . -t custom:1
```

-- You may see a completely different naming of a Docker file like the one in custom direcotry called 'mydockerfile'

```sh
docker build --file="mydockerfile" . -t custom:2
```

### Docker File in a github repo

<!-- https://github.com/madflojo/automatron -->

-- Clone the HTTPS url from the github repo. https://github.com/madflojo/automatron.git

```sh
docker build https://github.com/madflojo/automatron.git  -t automatron:1
```

### Docker Housekeeping - Images

Lists the Docker images that are locally stored on your machine:

```sh
docker image ls
```

Delete an image from your machine:

```sh
docker image rm [IMAGE ID]
```

Delete all image from your machine:

```sh
docker image rm $(docker image ls -aq)
```

Force delete all image from your machine:

```sh
docker image rm -f $(docker image ls -aq)
```

### Docker Housekeeping - Containers

Lists the Docker containers that are locally stored on your machine:

```sh
docker container ls
```

Stop all containers from your machine:

```sh
docker container stop $(docker container ls -aq)
```

Run a container and pass a name 'mywebserv'.

docker container run: This command tells Docker to run a new container.

-d: This flag runs the container in detached mode, which means it runs in the background and doesn't tie up your terminal.

-p 8080:80: This is a port mapping. It maps port 8080 on the host to port 80 on the container. This means if you access http://localhost:8080 on the host machine, you are essentially accessing the application running on port 80 inside the container.

--name=mywebserv: This names the container mywebserv for easier reference. Without this, Docker would assign a random name.

challenge:2: This is the image you're using to create the container. It's named challenge and tagged with 2.

```sh
docker container run -d -p 8080:80 --name=mywebserv challenge:2
```
