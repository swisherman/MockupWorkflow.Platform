# Deployment Guide

## Overview

This guide describes how to deploy and run the Mockup Workflow Platform for local development.

The platform is orchestrated through Docker Compose and consists of multiple services that work together to process production batches for Photoshop automation.

---

# Prerequisites

Before starting the platform, install:

* Docker Desktop
* .NET SDK (for local development)
* Adobe Photoshop (for Photoshop workflow execution)
* Git

Ensure Docker Desktop is running before starting the platform.

---

# Repository Layout

The platform repository contains the Docker orchestration and deployment configuration.

```text
MockupWorkflow.Platform/
    docker/
        docker-compose.yml
        .env.example
        config/
```

Application source code is maintained in the individual repositories referenced by the Docker Compose file.

---

# Configuration

## Platform Environment

Copy:

```text
docker/.env.example
```

to:

```text
docker/.env
```

Update:

```env
INCOMING_ROOT=E:/Products/Generations/Incoming
```

to match the location where incoming production batches are stored.

---

## Service Configuration

Each service has an example configuration file.

Copy every:

```text
*.env.example
```

to:

```text
*.env
```

inside:

```text
docker/config/
```

Update values as needed for your local environment.

---

# Starting the Platform

From the repository root:

```powershell
docker compose `
    --env-file .\docker\.env `
    -f .\docker\docker-compose.yml `
    up -d --build
```

Docker will build the services (if necessary) and start the platform.

---

# Stopping the Platform

```powershell
docker compose `
    --env-file .\docker\.env `
    -f .\docker\docker-compose.yml `
    down
```

To preserve build data, do not use the `-v` option unless you intentionally want to remove Docker volumes.

---

# Verifying the Deployment

Check that all containers are running:

```powershell
docker compose `
    --env-file .\docker\.env `
    -f .\docker\docker-compose.yml `
    ps
```

Expected services:

* MockupWorkflow.Admin
* PhotoshopAutomation.Api
* FolderCreator.API
* PNGAPI
* MongoDB

---

# Service Endpoints

| Service                 | URL                    |
| ----------------------- | ---------------------- |
| MockupWorkflow.Admin    | http://localhost:27031 |
| PhotoshopAutomation.Api | http://localhost:5767  |
| FolderCreator.API       | http://localhost:27020 |
| PNGAPI                  | http://localhost:27021 |

---

# Storage Layout

The platform separates external input from internal production storage.

## Incoming batches

Incoming source material is provided through:

```text
INCOMING_ROOT
```

and is mounted inside Docker as:

```text
/incoming
```

## Production storage

Generated production assets are stored in the Docker-managed volume:

```text
build-directories
```

which is mounted as:

```text
/data/builds
```

This avoids reliance on host-specific output folders while allowing incoming content to remain on the host.

---

# Troubleshooting

## INCOMING_ROOT must be set

Ensure:

```text
docker/.env
```

exists and contains a valid `INCOMING_ROOT` value.

---

## Containers fail to build

Rebuild the platform:

```powershell
docker compose `
    --env-file .\docker\.env `
    -f .\docker\docker-compose.yml `
    up -d --build
```

---

## Verify configuration

Validate the Compose configuration without starting containers:

```powershell
docker compose `
    --env-file .\docker\.env `
    -f .\docker\docker-compose.yml `
    config
```

A successful validation confirms that the Docker configuration and environment files are correctly configured.
