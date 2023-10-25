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
