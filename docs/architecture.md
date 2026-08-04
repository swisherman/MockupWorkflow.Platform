# Architecture

## 1. Purpose

The Mockup Workflow Platform coordinates multiple independent services to automate production workflows for digital products. It does not own business-specific logic (such as Mosswick); instead, it provides reusable infrastructure for importing production batches, processing artwork, executing Photoshop workflows, and managing generated assets.

## 2. Platform Overview

                 MockupWorkflow.Platform
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
        ▼                 ▼                 ▼
MockupWorkflow.Admin  PhotoshopAutomation.Api  FolderCreator.API
        │                 │
        └────────────┬────┘
                     ▼
                  MongoDB
                     │
                     ▼
           Photoshop UXP Plugin
                     │
                     ▼
             Generated Mockups

## 3. Repository Responsibilities

| Repository              | Responsibility               |
| ----------------------- | ---------------------------- |
| MockupWorkflow.Platform | Deployment and orchestration |
| MockupWorkflow.Admin    | Operations dashboard         |
| PhotoshopAutomation.Api | Workflow execution           |
| FolderCreator.API       | Folder preparation           |
| PNGAPI                  | Asset storage                |
| Photoshop UXP Plugin    | Photoshop automation         |
| Mosswick                | Content producer             |


## 4. Runtime Components

The Mockup Workflow Platform is composed of several independently deployable services. Each component has a focused responsibility and communicates with the rest of the platform through APIs, shared storage, or workflow records.

| Component                     | Runtime responsibility                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **MockupWorkflow.Admin**      | Provides the administrative interface for importing production manifests, creating batches, reviewing batch contents, monitoring processing status, and managing workflow operations.                                    |
| **PhotoshopAutomation.Api**   | Manages workflow records, batch state, processing status, and the coordination data used by the Photoshop automation client.                                                                                             |
| **FolderCreator.API**         | Creates the standardized directory structures required for input assets, generated mockups, and product-specific production files.                                                                                       |
| **PNGAPI**                    | Stores, retrieves, and exposes production image assets through HTTP endpoints. It provides a shared asset-access layer for the Admin application, APIs, and Photoshop plugin.                                            |
| **MongoDB**                   | Persists batch records, workflow items, processing state, errors, and other operational data used throughout the production lifecycle.                                                                                   |
| **Photoshop UXP Plugin**      | Runs inside Adobe Photoshop and executes product-specific PSD workflows. It retrieves pending records, loads source assets, updates templates, exports mockups, and reports success or failure back to the workflow API. |
| **Docker Compose**            | Starts and connects the platform services, configures service networking, mounts shared storage, and supplies environment-specific configuration.                                                                        |
| **Shared production storage** | Provides a common Docker-managed location for source assets, generated mockups, and other production files used by multiple services.                                                                                    |
| **Incoming host storage**     | Provides the external staging location from which production batches and source assets are imported into the platform.                                                                                                   |

### Component Interaction

The runtime components cooperate through three primary mechanisms:

1. **REST APIs**
   Services exchange workflow records, batch information, file requests, and processing updates through HTTP endpoints.

2. **Shared production storage**
   Services access the same production files through the Docker-managed `/data/builds` volume.

3. **Persistent workflow state**
   MongoDB stores the operational state needed to coordinate imports, processing, retries, failures, and completion.

The platform deliberately separates orchestration, business logic, and execution responsibilities.

The Admin application coordinates production work, the APIs provide specialized services, and the Photoshop UXP plugin performs the Photoshop-specific automation.

## 5. Data Flow

The platform processes production work as a sequence of well-defined stages. Each stage has a specific responsibility and hands its output to the next stage in the pipeline.

```text
External Producer
        │
        ▼
Production Manifest
        │
        ▼
MockupWorkflow.Admin
        │
        ▼
Production Batch Creation
        │
        ▼
FolderCreator.API
        │
        ▼
PNGAPI (Production Asset Storage)
        │
        ▼
Photoshop UXP Plugin
        │
        ▼
Generated Mockups
        │
        ▼
Workflow Status Updates
        │
        ▼
Completed Production Batch
```

### Processing Stages

1. **External Producer**

   An external system, such as Mosswick, generates a production manifest describing the assets that should be processed.

2. **Production Manifest**

   The production manifest acts as the integration contract between external producers and the Mockup Workflow Platform.

3. **Batch Creation**

   MockupWorkflow.Admin imports the manifest, creates a production batch, and stores workflow records in MongoDB.

4. **Folder Preparation**

   FolderCreator.API creates the standardized folder structure required for production processing.

5. **Asset Storage**

   Source assets are uploaded into the shared production storage managed by PNGAPI.

6. **Photoshop Processing**

   The Photoshop UXP plugin retrieves pending workflow records, loads the required PSD templates and source assets, performs product-specific processing, and exports the finished mockups.

7. **Workflow Completion**

   Processing results are reported back to the platform, allowing batches to be monitored, retried if necessary, and marked complete once all workflow steps have finished.

## 6. Production Workflow

The Mockup Workflow Platform processes production batches through a structured lifecycle that separates preparation, execution, and completion. Each stage has a clearly defined responsibility, allowing the platform to support multiple product types and external content producers while maintaining a consistent processing pipeline.

### 1. Import

A production manifest is imported through MockupWorkflow.Admin. The platform validates the input, creates a production batch, and stores the workflow records required for downstream processing.

### 2. Preparation

The platform prepares the batch for processing by creating the required folder structure and transferring source assets into shared production storage. At the completion of this stage, every workflow item has a standardized location for its input and output files.

### 3. Processing

The Photoshop UXP Plugin retrieves pending workflow records from PhotoshopAutomation.Api and executes the appropriate product-specific workflow.

Typical processing tasks include:

* Opening PSD templates
* Loading source assets
* Replacing Smart Objects
* Updating text layers
* Applying product-specific transformations
* Exporting finished mockups

The workflow architecture allows multiple product types to share the same processing pipeline while providing specialized implementations where required.

### 4. Completion

After processing finishes, workflow status is updated and the generated mockups become available for downstream publishing workflows. Failed items remain available for review and retry without interrupting the processing of the remaining batch.

This staged approach allows each phase of production to evolve independently while maintaining a consistent end-to-end workflow.

## 7. Design Principles

The Mockup Workflow Platform is designed around a small set of architectural principles that promote separation of concerns, extensibility, and reusable production workflows. These principles guide both new feature development and the integration of external producers.

- **Single Responsibility**  
  Each service has a focused responsibility and communicates through well-defined interfaces.

- **Application-Agnostic Platform**  
  The platform does not contain business-specific logic. External systems communicate through production manifests and shared contracts.

- **Manifest-Driven Integration**  
  External producers integrate by generating production manifests rather than calling internal services directly.

- **Separation of Orchestration and Execution**  
  Administrative coordination, business services, and Photoshop execution are implemented as separate components.

- **Shared Production Storage**  
  Runtime services share production assets through Docker-managed storage while keeping incoming source material external to the platform.

- **Extensible Workflow Architecture**  
  Product-specific workflows can be added without changing the overall processing pipeline.

- **Service Communication Through APIs**  
  Runtime services communicate through REST APIs instead of direct dependencies whenever practical.

- **Incremental Processing**  
  Workflow items can be retried independently, allowing failed items to be reprocessed without restarting an entire batch.

## 8. Future Extension Points

New producers can integrate with the platform by generating production manifests that conform to the platform's shared contracts. This allows domain-specific applications to remain independent while reusing the same production pipeline, Photoshop automation, asset storage, and operational tooling.

                External Producers

      Mosswick     Shopify     Website
            │          │          │
            └──────────┼──────────┘
                       │
               Manual Import
                       │
                       ▼
          MockupWorkflow.Admin
                       │
                       ▼
         Shared Production Pipeline
                       │
                       ▼
          Photoshop Automation