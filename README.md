# Auto Docker Push

Github Action for automatically tagging and pushing docker images to [Docker Hub](https://hub.docker.com).  See example here: https://hub.docker.com/r/bozdoz/docker-push

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
      - uses: actions/checkout@v3
      - name: Docker Push
        uses: bozdoz/auto-docker-push
        with:
          image: ${{ secrets.DOCKER_HUB_IMAGE }}
          username: ${{ secrets.DOCKER_HUB_USERNAME }}
          password: ${{ secrets.DOCKER_HUB_ACCESS_TOKEN }}

```
