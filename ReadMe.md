# Git Cache

- [Requirements](#requirements)
  - [Local Runs](#local-runs)
  - [Docker Runs](#docker-runs)
  - [Development](#development)
- [Running](#running)
- [Configuration](#configuration)

## Requirements

### Local Runs

- .NET 8.0
- bash

### Docker Runs

- Docker

### Development

- Visual Studio 2022

## Running

Currently the implementation uses bash to execute commands, so it
runs fine on Linux or MacOS. For Windows, it is suggested to run
from a Docker container:

```batch
> docker compose up
Starting git-cache_git-cache-data_1 ... done
Starting git-cache_git-cache_1      ... done
Attaching to git-cache_git-cache_1, git-cache_git-cache-data_1
git-cache-data_1  | Data container for Git cache
git-cache_git-cache-data_1 exited with code 0
git-cache_1       | Hosting environment: Development
git-cache_1       | Content root path: /app
git-cache_1       | Now listening on: http://[::]:8085
git-cache_1       | Application started. Press Ctrl+C to shut down.
```

At this point should be able to clone using the cache:

```batch
> git clone http://localhost:8085/api/Git/github.com/{owner}/{repo}
```

> **Note:** If you try to start it using `docker-compose up` you'll now see the following error: `fatal: unable to access 'http://nu-ci-git-cache2:8085/api/Git/github.com/Monotype/DriverPDL/': Failed to connect to nu-ci-git-cache2 port 8085 after 21154 ms: Couldn't connect to server`

## Configuration

The default port on the host is `8085`. This can be controlled with
an environment variable `GIT_HTTP_PORT=8888` or with a `.env` file.