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
