# Prebuilt mountebank Docker image

Includes:

- [mountebank](http://www.mbtest.org/)
- Node.js 14
- Alpine Linux

## Run

To build a new image based on `Dockerfile` and run it:

    mountebank

Pass variable `BUILD_ARGS` to add additional `docker build` arguments.

Pass variable `RUN_ARGS` to add additional `docker run` arguments.

## Build

To build a new base image:

    docker/build_and_test_image

Pass variable `BUILD_DIR` to override the directory path where `Dockerfile` is.

## Push

Remember to `docker login` first.

Push the image to a private Docker registry:

    REGISTRY_URL=https://your.private.registry/username \
      docker/tag_and_push_image

Push the image to [Docker Hub](https://hub.docker.com):

    REGISTRY_URL=username \
      docker/tag_and_push_image
