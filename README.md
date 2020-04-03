# grocy-docker

ERP beyond your fridge - now containerized!

This repository includes container build infrastructure for [grocy](https://github.com/grocy/grocy).

[![Docker Pulls](https://img.shields.io/docker/pulls/grocy/grocy.svg)](https://hub.docker.com/r/grocy/grocy/)
[![Docker Stars](https://img.shields.io/docker/stars/grocy/grocy.svg)](https://hub.docker.com/r/grocy/grocy/)

## Prerequisites

Follow [these instructions](https://docs.docker.com/install/) to get Docker running on your server.

## Quickstart

To get started using pre-built [Docker Hub grocy images](https://hub.docker.com/u/grocy), run the following commands:

```sh
docker-compose pull
docker-compose up
```

The grocy application should now be accessible locally to the server:

 - [http://localhost](http://localhost)
 - [https://localhost](https://localhost)

Since the images contain self-signed certificates, your browser may display a warning when visiting the HTTPS URL.

### Configuration

The grocy application reads configuration settings from environment variables prefixed by `GROCY_`.

Some key settings are included in [grocy.env](grocy.env). The included version of this file sets `GROCY_MODE=demo`; this disables authentication and creates sample database content.

#### Demo Mode

To run the container in demo mode, override the `GROCY_MODE` environment variable at application run-time:

```sh
GROCY_MODE=demo docker-compose up
```

### Build

#### Docker Images

```sh
docker-compose build
```

Note: if you experience build failures as a result of GitHub API [rate limiting](https://developer.github.com/v3/#rate-limiting), you may optionally provide a GitHub API key (preferably restricted to `read:packages` scope) at build-time:

```sh
GITHUB_API_TOKEN='your-token-here' docker-compose build
```

#### OCI Images

Optional support for building [opencontainer](https://www.opencontainers.org/) images is available via the [Makefile](Makefile) provided.
