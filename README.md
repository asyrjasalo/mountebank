# Prebuilt mountebank Docker image

Includes:

- Alpine Linux or Debian (slim)
- Node.js 14
- [mountebank](http://www.mbtest.org/) at [:2525](http://localhost:2525)
- [proxy to jsonplaceholder](https://jsonplaceholder.typicode.com/) at [:8080](http://localhost:8080)
- stateful response fakers for the proxy at [:8273](http://localhost:8273)

## Run

To build a new image based on `Dockerfile` and run it:

    ./mountebank

Pass variable `BUILD_ARGS` to add additional `docker build` arguments.

Pass variable `RUN_ARGS` to add additional `docker run` arguments.

## Build

Alpine Linux:

    docker/build_and_test_image

Debian Buster (slim):

    IMAGE_KIND="slimbuster" docker/build_and_test_image

Pass variable `BUILD_DIR` to override the directory path where `Dockerfile` is.

## Push

Remember to `docker login` first.

Push the image to the private Docker registry:

    REGISTRY_URL=https://your.azurecr.io \
      docker/tag_and_push_image

Tag and push the image as 'alpine' to [Docker Hub](https://hub.docker.com):

    REGISTRY_URL="$USER" \
      docker/tag_and_push_image

Tag and push the image as 'slimbuster' (note: build on Debian image first):

    REGISTRY_URL="$USER" \
    IMAGE_KIND=slimbuster \
      docker/tag_and_push_image
