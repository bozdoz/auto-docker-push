# Auto Docker Push

Github Action for automatically tagging and pushing docker images to [Docker Hub](https://hub.docker.com).  See example here: https://hub.docker.com/r/bozdoz/docker-push

**Roughly**, it translates a git tag of `v1.2.3` to a docker tag push of both `1.2.3`, and `latest`.

### Getting Started

Follow the template from this very repository:

```yml
name: ReleaseWorkflow

on:
  push:
    tags:
      - "*"

jobs:
  push:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Docker Push
        uses: bozdoz/auto-docker-push
        with:
          image: ${{ secrets.DOCKER_HUB_IMAGE }}
          username: ${{ secrets.DOCKER_HUB_USERNAME }}
          password: ${{ secrets.DOCKER_HUB_ACCESS_TOKEN }}

```

Now, anytime you publish a new tag, it will generate a docker image using that tag. 

For example: if you publish `v1.0`, then your image will be pushed under the tags `1.0` and `latest` (note: it strips the leading `v`).

For extra verbose images, if you publish `v1.0.1-2023-04-15`, then your image will be pushed with tags: `1.0.1-2023-04-15`, `1.0.1`, and `latest`.
