# Ruby Example

A simple **Ruby** application published as a **sample deployment project for [Nife.io](https://nife.io)**.

This repository demonstrates how to run a lightweight Ruby application locally, package it with Docker, and deploy it on [Nife.io](https://nife.io). It is intended as a practical sample for testing Ruby deployment workflows and showcasing a straightforward Ruby deployment path.

---

## Overview

This project is a basic Ruby application with a standard project structure and backend logic. It is designed to be small enough for learning and deployment experiments while still reflecting the conventions of a real Ruby application.[3]

If you want a simple backend-oriented sample to test deployment on [Nife.io](https://nife.io), this repository is a good starting point.

---

## Features

| Feature | Description |
| --- | --- |
| Ruby app | Built with standard Ruby application structure |
| Modular architecture | Uses classes, modules, and organized code structure |
| Gem-based dependencies | Supports Ruby gems through Bundler for dependency management |
| Docker support | Includes a `Dockerfile` for containerized execution |
| Deployment-ready setup | Can be deployed using Git-based or Docker-based workflows |
| Nife.io sample use case | Suitable as a reference project for [Nife.io](https://nife.io) deployments |

---

## Tech Stack

| Technology | Purpose |
| --- | --- |
| Ruby | Runtime environment |
| Bundler | Dependency management |
| Sinatra/Rack | Web framework (optional, depending on configuration) |
| Docker | Container packaging |
| Nife.io | Deployment platform |

---

## Prerequisites

Before running the project locally, make sure the following are installed.

| Requirement | Notes |
| --- | --- |
| Ruby | Use the version specified in `.ruby-version` |
| Bundler | Required to install Ruby gems |
| Git | Required to clone the repository |

---

## Getting Started

### Clone the repository

```bash
git clone https://github.com/nifetency/ruby-example.git
cd ruby-example
```

### Install dependencies

```bash
bundle install
```

### Start the application

```bash
ruby server.rb
```

Then open the application at `http://localhost:8080`.

## Run with Docker

This project includes a Dockerfile for container-based execution.

### Build the image

```bash
docker build -t ruby-example .
```

### Run the container

```bash
docker run -p 8080:8080 ruby-example
```

After the container starts, open the app at `http://localhost:8080`.

## Deploy on Nife.io

You can deploy this application on [Nife.io](https://nife.io) using either a Docker image, the source repository, or the CLI.[1] [2]

### Option 1: Deploy from a Docker image

First, build and push the image to your preferred container registry.

```bash
docker build -t ruby-example .
docker tag ruby-example <username>/ruby-example:latest
docker push <username>/ruby-example:latest
```

Then configure a new application in Nife.io with the following settings.

| Setting | Value |
| --- | --- |
| Source | Docker Image |
| Registry | Docker Hub or another supported registry |
| Image | `<username>/ruby-example:latest` |
| Internal Port | `8080` |
| External Port | `80` |
| Suggested Replicas | `1` |

### Option 2: Deploy from the Git repository

You can also deploy the project directly from GitHub.

| Setting | Value |
| --- | --- |
| Source | Git Repository |
| Provider | GitHub |
| Branch | `main` |
| Internal Port | `8080` |
| External Port | `80` |
| Build Mode | Auto-Dockerize with runtime |

### Option 3: Deploy with `nifectl`

If you prefer the command line, use the following workflow.

```bash
nifectl auth login
nifectl init
nifectl deploy
```

For step-by-step instructions, see the [Nife.io Quick Deploy documentation](https://docs.nife.io/overview/quick-deploy) and the [nifectl quick start guide](https://docs.nife.io/Quick-Start/Nifectl).

## Environment Variables

The following variables are commonly relevant for deployment.

| Variable | Description | Example |
| --- | --- | --- |
| `RACK_ENV` | Ruby/Rack execution environment | `production` |
| `PORT` | Application port, if overridden by environment | `8080` |

## Repository Structure

| Path | Purpose |
| --- | --- |
| `lib/` | Main Ruby application code |
| `config/` | Framework and environment configuration |
| `test/` | Test files |
| `public/` | Static public assets |
| `Dockerfile` | Container build instructions |
| `Gemfile` | Ruby gem dependencies |
| `config.ru` | Rack configuration entry point |

## Troubleshooting

| Issue | Suggested fix |
| --- | --- |
| Bundler install fails | Verify your Ruby version and rerun `bundle install` |
| Port `8080` is already in use | Stop the conflicting process or remap the port |
| Docker build fails | Recheck the Dockerfile and local Ruby environment |
| Deployment fails on Nife.io | Verify ports, environment variables, and build settings |
| Application is unreachable | Check routing, service exposure, and deployment logs |

---

## Acknowledgements

This repository is maintained by **Nifetency** as a sample deployment project for [Nife.io](https://nife.io).

If this repository is derived from an earlier template or upstream example, it is good practice to retain visible credit to the original author or source repository.

## License

This project is licensed under the MIT License.

## References

1. [Nife.io](https://nife.io)
2. [Nife Docs Overview](https://docs.nife.io/overview/)
3. [Nife Quick Start](https://docs.nife.io/Quick-Start)

