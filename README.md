# Mockup Workflow Platform

![.NET 10](https://img.shields.io/badge/.NET-10-purple)
![ASP.NET Core](https://img.shields.io/badge/ASP.NET%20Core-Web%20API-blue)
![Adobe UXP](https://img.shields.io/badge/Adobe-UXP-red)
![Blazor](https://img.shields.io/badge/Blazor-Server-512BD4)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-47A248)
![Docker](https://img.shields.io/badge/Docker-Enabled-2496ED)
![Status](https://img.shields.io/badge/Status-Active_Development-success)

The Mockup Workflow Platform is an end-to-end automation platform for high-volume creative production. It integrates Adobe Photoshop UXP, ASP.NET Core services, MongoDB, Docker, and Blazor into configurable workflows for asset generation, mockup production, and digital publishing.

## Platform Architecture

![Platform Architecture](docs/images/architecture-overview.svg)

## Documentation

For additional information, see:

## Documentation

- [Architecture Overview](docs/Architecture.md)
- [Deployment Guide](docs/Deployment.md)

## Project Status

**Status:** Active Development (Portfolio Release)

The Mockup Workflow Platform is under active development and serves as the foundation for automated mockup generation and digital publishing workflows.

Current capabilities include:

- Batch workflow orchestration
- Photoshop UXP automation
- Dockerized microservices
- Administrative dashboard
- Asset management APIs
- Workflow monitoring

## Quick Start

The Mockup Workflow Platform is orchestrated through Docker Compose.

See:

- `docs/Deployment.md`

for complete setup instructions, including:

- environment configuration
- Docker startup
- service verification
- troubleshooting

## Explore the Platform

The Mockup Workflow Platform is distributed across several focused repositories. Start with the component that best matches what you want to explore.

### Start with the Architecture

This repository provides the system-level overview, architecture documentation, workflow description, and links to the individual platform components.

### Explore the Photoshop Automation

[Photoshop UXP Batch Mockup Plugin](https://github.com/swisherman/photoshop-uxp-batch-mockup-plugin)

See how the platform executes configurable Photoshop workflows, processes PSD templates, replaces artwork, generates mockups, and reports processing results.

### Explore the Workflow API

[PhotoshopAutomation.Api](https://github.com/swisherman/PhotoshopAutomation.Api)

Review the ASP.NET Core API responsible for workflow records, batch processing, queue state, completion tracking, and communication with the Photoshop plug-in.

### Explore the Operations Dashboard

[MockupWorkflow.Admin](https://github.com/swisherman/MockupWorkflow.Admin)

Explore the Blazor Server administration dashboard used to import production batches, monitor workflow execution, review processing status, and manage automated Photoshop production workflows.

### Explore Folder Preparation

[FolderCreator.API](https://github.com/swisherman/FolderCreator.API)

See how standardized batch and product folder structures are created from structured requests before creative processing begins.

### Explore Asset Uploads

[MockupWorkflow.BuildUploader](https://github.com/swisherman/MockupWorkflow.BuildUploader)

Review the .NET command-line utility used to upload prepared input and mockup folders while preserving the platform’s expected directory structure.

### Recommended Review Path

For a complete tour of the system:

1. Review the architecture diagram in this repository.
2. Explore `PhotoshopAutomation.Api` to understand workflow state and orchestration.
3. Explore `MockupWorkflow.Admin` to see how operators manage production batches and monitor workflow execution.
4. Explore the Photoshop UXP plug-in to see workflow execution inside Adobe Photoshop.
5. Review `FolderCreator.API` and `MockupWorkflow.BuildUploader` to understand asset preparation and movement.
6. Review the end-to-end workflow below to see how the components operate together.

## Overview

Mockup Workflow Platform is a modular automation platform designed around reusable workflow concepts rather than product-specific logic.

The platform separates:

- Workflow orchestration
- Photoshop automation
- Asset management
- Administrative monitoring
- Shared business models
- File management

This architecture allows multiple products and content pipelines to share the same workflow engine.

## What This Demonstrates

This project showcases experience designing and building a distributed workflow automation platform from the ground up, including:

- Distributed system architecture
- Adobe Photoshop UXP development
- ASP.NET Core Web APIs
- Blazor Server applications
- MongoDB data modeling
- Docker containerization
- Workflow engine design
- Batch processing pipelines
- Service-oriented architecture
- End-to-end production automation

## Why It Exists

Creative production often requires repeating the same Photoshop operations hundreds or thousands of times.

The Mockup Workflow Platform automates those repetitive tasks through configurable workflows, allowing new product pipelines to be added without redesigning the core system.

## Architecture 

The Mockup Workflow Platform is built around a configurable workflow engine rather than product-specific automation.

Workflows are composed of ordered processing steps executed by registered processors, allowing new products and production pipelines to be added without redesigning the core platform.

## Technology 

### Languages
- C#
- JavaScript

### Frameworks
- ASP.NET Core
- Blazor Server
- Adobe Photoshop UXP

### Infrastructure
- Docker
- MongoDB

### Architecture

- REST APIs
- Service-Oriented Architecture
- Workflow Engine

---

## Workflow

The Mockup Workflow Platform automates creative production through a configurable, multi-stage processing pipeline. Each component has a well-defined responsibility, allowing the platform to scale as new product types and workflow steps are added.

### End-to-End Workflow

```text
Source Artwork
        |
        v
MockupWorkflow.BuildUploader
        |
        v
PhotoshopAutomation.Api
        |
        v
MongoDB Workflow Queue
        |
        v
Photoshop UXP Plugin
        |
        v
Workflow Engine
        |
        +--> Step 10 - Artwork Generation
        |
        +--> Step 20 - Mockup Generation
        |
        +--> Future Workflow Steps...
        |
        v
Generated Mockups
        |
        v
PNGAPI
        |
        v
MockupWorkflow.Admin
```

### Workflow Summary

1. **BuildUploader** prepares and uploads production assets.
2. **PhotoshopAutomation.Api** registers workflow batches and exposes REST endpoints.
3. **MongoDB** stores workflow definitions, batch status, and processing state.
4. **Photoshop UXP Plugin** retrieves pending batches and executes the workflow.
5. **Workflow Engine** processes each configured workflow step in sequence.
6. **PNGAPI** stores the generated mockups.
7. **MockupWorkflow.Admin** provides real-time monitoring and batch management.

## Design Principles

- Modular services
- Workflow-driven architecture
- Product-independent processing
- Shared domain models
- Docker-based deployment
- Extensible processor pipeline

## Roadmap

### Near Term

- Additional workflow processors
- Workflow configuration editor
- Additional product pipelines
- Public release of additional platform components

### Future

- Cloud storage providers
- Marketplace publishing integration
- Distributed worker processing
- Workflow designer and visual editor
- Additional creative production pipelines

## Example Consumers

The platform is designed to support multiple applications.

Current consumer:

- Mosswick.World

Future consumers may include:

- Additional digital art publishing systems
- Marketplace automation tools
- Product generation pipelines

## Key Features

- Configurable multi-step workflow engine
- Photoshop UXP automation
- Dockerized microservice architecture
- REST-based service communication
- MongoDB-backed workflow persistence
- Blazor administrative dashboard
- Batch processing and monitoring
- Shared domain model across services

## Repository Purpose

This repository serves as the architectural overview of the Mockup Workflow Platform.

Individual repositories contain the implementation of each service, while this repository documents how they integrate into a scalable workflow automation platform for creative production and digital publishing.

