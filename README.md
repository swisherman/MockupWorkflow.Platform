# Mockup Workflow Platform

![.NET 10](https://img.shields.io/badge/.NET-10-purple)
![ASP.NET Core](https://img.shields.io/badge/ASP.NET%20Core-Web%20API-blue)
![Adobe UXP](https://img.shields.io/badge/Adobe-UXP-red)
![Blazor](https://img.shields.io/badge/Blazor-Server-512BD4)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-47A248)
![Docker](https://img.shields.io/badge/Docker-Enabled-2496ED)
![Status](https://img.shields.io/badge/Status-Active_Development-success)

A modular workflow automation platform for building configurable creative production pipelines.

The platform combines Adobe Photoshop UXP, ASP.NET Core microservices, Docker, MongoDB, and Blazor to automate high-volume asset generation, mockup production, and digital publishing workflows.
---
## Project Status

**Status:** Active Development

The Mockup Workflow Platform is under active development and serves as the foundation for automated mockup generation and digital publishing workflows.

Current capabilities include:

- Batch workflow orchestration
- Photoshop UXP automation
- Dockerized microservices
- Administrative dashboard
- Asset management APIs
- Workflow monitoring
---
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

---
## Why It Exists

Creative production often requires repeating the same Photoshop operations hundreds or thousands of times.

The Mockup Workflow Platform automates those repetitive tasks through configurable workflows, allowing new product pipelines to be added without redesigning the core system.
---

## Architecture 

The Mockup Workflow Platform is built around a configurable workflow engine rather than product-specific automation.

Workflows are composed of ordered processing steps executed by registered processors, allowing new products and production pipelines to be added without redesigning the core platform.
---
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
- Distributed Services
- Workflow Engine

---
## Platform Architecture

``` 
                 Mockup Workflow Platform

                     BuildUploader
                           │
                           ▼
               MockupWorkflow.Admin
                           │
                           ▼
              PhotoshopAutomation.Api
            ┌─────────┼──────────┐
            ▼         ▼          ▼
    FolderCreator   PNGAPI   MongoDB
                           │
                           ▼
                Photoshop UXP Plugin
                           │
                           ▼
                  Adobe Photoshop
                           │
                           ▼
                  Generated Assets
```

---

## Platform Components

### Component Repositories

| Repository | Purpose |
|------------|---------|
| Photoshop UXP Plugin | Photoshop client |
| MockupWorkflow.Admin | Administrative dashboard |
| PhotoshopAutomation.Api | Workflow API |
| FolderCreatorApi | Folder management |
| PNGAPI | Asset service |
| MockupWorkflow.Shared | Shared models |
---

## Photoshop UXP Plugin

The Photoshop client responsible for:

- Loading workflow batches
- Opening PSD templates
- Executing workflow processors
- Replacing Smart Objects
- Exporting generated artwork
- Reporting workflow status

---

## PhotoshopAutomationApi

Coordinates workflow execution.

Responsibilities include:

- Batch management
- Processing state
- Workflow endpoints
- Queue management
- Completion reporting

---

## MockupWorkflow.Admin

Blazor Server application providing:

- Batch monitoring
- Workflow status
- Import tools
- Processing history
- Administrative dashboards

---

## FolderCreatorApi

Responsible for:

- Folder generation
- Build folder preparation
- Safe path creation
- Input/output directory management

---

## PNGAPI

Provides image asset services.

Responsibilities include:

- PNG upload
- PNG download
- Generated asset storage
- Shared Docker volume access

---

## MockupWorkflow.Shared

Shared library containing:

- Domain models
- Repository abstractions
- DTOs
- Shared constants
- Common workflow logic

---

## MockupWorkflow.BuildUploader

Imports new build artifacts into the workflow.

Responsibilities include:

- Build registration
- Incoming asset preparation
- Workflow initialization

---

# Workflow

```
Artwork
    │
    ▼
BuildUploader
    │
    ▼
Batch Registration
    │
    ▼
Photoshop UXP Plugin
    │
    ▼
Workflow Engine
    │
    ▼
Photoshop Processing
    │
    ▼
Generated Assets
    │
    ▼
Workflow Complete
```

---

# Design Principles

- Modular services
- Workflow-driven architecture
- Product-independent processing
- Shared domain models
- Docker-based deployment
- Extensible processor pipeline

---

## Roadmap

- Additional workflow processors
- Workflow configuration editor
- Additional product pipelines
- Cloud storage providers
- Marketplace publishing integration

# Example Consumers

The platform is designed to support multiple applications.

Current consumer:

- Mosswick.World

Future consumers may include:

- Additional digital art publishing systems
- Marketplace automation tools
- Product generation pipelines

---
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

