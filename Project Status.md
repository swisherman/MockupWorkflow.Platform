# MockupWorkflow.Platform

## Purpose

Create a flagship software portfolio project that demonstrates how Robert's Photoshop automation, C#/.NET services, Blazor experience, APIs, and Docker workflows can operate as one coherent platform.

## Desired Outcome

Build a portfolio-quality system that can coordinate an end-to-end product-mockup workflow:

- Receive or identify source artwork.
- Organize project files and folders.
- Prepare or convert image assets.
- Coordinate Photoshop batch-mockup generation.
- Track workflow jobs and results.
- Provide a Blazor administration interface.
- Expose reusable API services.
- Run the supporting components through Docker.
- Demonstrate realistic business-process automation.

The platform should become a strong example for Fiverr, contract work, and part-time software-engineering opportunities.

## Status

- **State:** Active
- **Priority:** Low
- **Health:** On Track
- **Work Status:** Ready
- **Last Meaningful Attention:** September 13, 2026
- **Review Frequency:** Monthly
- **Source Folder:** `E:\repos\MockupWorkflow.Platform`
- **Related Projects:** Photoshop UXP Batch Mockup Plugin, Fiverr.ServiceKits, Customer Workflow Demo, C# Development Practice

## Current Outcome

Maintain MockupWorkflow.Platform as a portfolio-quality automation platform and architectural hub that demonstrates the integration of Photoshop automation, .NET services, workflow orchestration, asset preparation, Docker, and administrative tooling.

## Current Milestone

Consolidate the platform's reusable production assets and documentation around the implemented workflow architecture. Recent work has focused on the printable wall-art template library, including validated 2:3 mockup templates, lifestyle templates, listing-information PSD templates, artwork-showcase templates, and listing-template refinements.

## Next Action

Review the current platform repository after the September template work and determine the next bounded portfolio-development task.

Confirm:

- Whether the printable wall-art template library is complete for its current scope.
- Whether the README and architecture documentation accurately reflect the implemented platform.
- Whether any remaining component or workflow needs documentation before further feature development.
- Whether the next work should improve the portfolio presentation or add another production capability.

Do not begin a broad platform expansion until that review identifies a specific next task.

## Proposed Components

### Photoshop UXP Plugin

Role:

- Interact with Photoshop.
- Replace artwork in mockup templates.
- Run batch mockup operations.
- Export completed mockup images.

Existing foundation:

- Photoshop UXP Batch Mockup Plugin

### Workflow API

Role:

- Create and manage workflow jobs.
- Track processing state.
- Coordinate the platform's services.
- Store job metadata and results.

Likely technology:

- ASP.NET Core Web API

### PNG or Image API

Role:

- Inspect image files.
- Validate image dimensions or formats.
- Convert or prepare image assets.
- Produce standardized output where needed.

The exact scope should be defined before implementation.

### Folder Creator API

Role:

- Create expected project-folder structures.
- Apply naming conventions.
- Organize inputs, templates, and outputs.
- Reduce manual setup.

The project should first determine whether this needs to be a separate API or merely a shared service.

### Shared Library

Role:

- Hold common models and validation rules.
- Prevent duplicated logic.
- Standardize job, file, and result structures.

### Blazor Administration Application

Role:

- Submit or monitor jobs.
- Show workflow status.
- Display validation failures.
- Provide access to completed output.
- Demonstrate Robert's Blazor experience.

### Docker Orchestration

Role:

- Run compatible services together.
- Provide repeatable development setup.
- Demonstrate deployment and service-integration skills.

Photoshop itself may require desktop interaction and should not be assumed to run inside the same containerized environment.

## Candidate Minimum Viable Platform

A possible first version could:

1. Accept a mockup-job request.
2. Validate the artwork and project information.
3. Create the required folder structure.
4. Record the job.
5. Prepare a Photoshop processing manifest.
6. Allow the Photoshop plugin to process the manifest.
7. Record the completed outputs.
8. Display job status in a Blazor interface.

The project brief should confirm or revise this flow before development begins.

## Skills Demonstrated

The platform could provide portfolio evidence for:

- C# and .NET
- ASP.NET Core Web API
- Blazor
- JavaScript and Adobe UXP
- MongoDB or another suitable data store
- API design
- Background workflow processing
- File automation
- Testing
- Docker
- Documentation
- System integration
- Practical business-process automation

Technology should be included because the workflow needs it, not merely to increase the number of technologies listed.

## Milestones

| Milestone | Target | Type | Status |
|---|---|---|---|
| Identify platform concept | July 2026 | Target Window | Completed |
| Identify candidate components | July 2026 | Target Window | Completed |
| Confirm source-folder status | Flexible | Review Date | Not Started |
| Write one-page project brief | Flexible | Target Window | Not Started |
| Define minimum viable workflow | Flexible | Target Window | Not Started |
| Decide whether to activate or pause the project | After Project Brief | Review Condition | Not Started |
| Create architecture and repository structure | After Activation | Target Condition | Not Started |
| Implement first end-to-end workflow | After Activation | Target Condition | Not Started |
| Prepare portfolio demonstration | After MVP | Target Condition | Not Started |

## Activation Conditions

The project should become Active only when:

- Higher-priority retirement obligations are under control.
- Current customer orders are not at risk.
- Robert has a regular development-time allowance.
- The project brief is complete.
- The minimum viable scope is small enough to finish.
- The work supports a current job-search, Fiverr, or portfolio objective.

Until those conditions are met, the project should remain Planned.

## Deadlines and Important Dates

MockupWorkflow.Platform currently has no external hard deadline.

| Date or Condition | Item | Type | Status |
|---|---|---|---|
| Monthly portfolio review | Reconsider project state | Review Date | Planned |
| Before implementation | Complete project brief | Target Condition | Not Started |
| Before implementation | Define minimum viable workflow | Target Condition | Not Started |

## Scope Controls

The first version should avoid:

- Building every proposed API immediately.
- Creating separate services where a shared component would suffice.
- Adding infrastructure with no demonstrated need.
- Rebuilding the existing Photoshop plugin.
- Attempting production-scale deployment before the workflow works locally.
- Expanding into a generic workflow platform before the mockup use case is complete.

## Blockers and Uncertainties

- The minimum viable scope has not been defined.
- The source repository or local folder status needs confirmation.
- The boundary between separate APIs and shared services is unclear.
- Photoshop desktop integration may affect orchestration choices.
- The project could become too large for a focused portfolio demonstration.
- It currently competes with retirement work, business operations, C# practice, and existing project commitments.

## Important Decisions

- The platform is intended to be a flagship portfolio project.
- It should integrate existing useful work rather than replace it.
- The Photoshop UXP plugin remains a separate working project.
- The first release must demonstrate one complete workflow.
- Full implementation should not begin before scope is deliberately constrained.
- Architecture should follow the business workflow.
- The project may remain Planned without being considered neglected.
- A smaller completed platform is more valuable than an ambitious unfinished system.

## Recent Progress

### July 2026

- Identified MockupWorkflow.Platform as a possible next flagship project.
- Proposed integration of the Photoshop UXP plugin, Workflow API, PNG API, Folder Creator API, shared library, Blazor administration application, and Docker orchestration.
- Recognized its value as a portfolio demonstration.

## Review Questions

During each monthly review, ask:

1. Is there a current portfolio, Fiverr, or job-search reason to activate this project?
2. Are higher-priority obligations sufficiently controlled?
3. Can the first useful version be completed within a limited scope?
4. Which components are truly required for the first workflow?
5. Can any proposed API begin as a shared service instead?
6. Does the project reuse the existing Photoshop plugin?
7. Is the platform demonstrating skills Robert wants employers or customers to see?
8. Should the project remain Planned, become Active, or be Paused?