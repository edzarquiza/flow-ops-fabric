# FlowOps Fabric — Project Context

This file is the authoritative context for the Microsoft Fabric analytics/data-platform work built around the FlowOps application. Read it before creating, modifying, or reviewing any documentation in this repo.

Detailed implementation docs for architecture, ingestion, Bronze, data quality, Silver, Gold, semantic model, Power BI, orchestration, and visuals live in separate documents (see Phases below) and will supersede/extend this file as they're written. **Do not infer implementation details that aren't documented or verified.**

## Project Identity

- **Project name:** FlowOps Service Operations Analytics Platform
- **Underlying application:** FlowOps — Operations & Delivery Management Platform (an IT Support / Service Desk operational product)

The Fabric project is an analytics/data-platform layer built around the operational data FlowOps produces and stores. FlowOps and Fabric are related but distinct parts of the overall portfolio.

## Core Relationship

```
FlowOps Application
        ↓
Operational PostgreSQL Data
        ↓
Microsoft Fabric Data Platform
        ↓
Analytical Model
        ↓
Power BI Analytics
```

- FlowOps is the operational system.
- Microsoft Fabric is the analytical/data-engineering platform.
- Power BI is the analytics/reporting consumption layer.

Do not describe FlowOps itself as a Fabric application. Do not describe the Fabric work as "just another Power BI dashboard." The Fabric project shows how operational application data can move through a modern analytical pipeline into analytics-ready information.

## What FlowOps Is

FlowOps is an Operations & Delivery Management Platform built around: **WORK → WORKFLOW → INTELLIGENCE → ACTION**.

Primary persona: **IT Support / Service Desk**.

Operational questions the application addresses:
- What needs my attention right now?
- What work is approaching or breaching SLA?
- What is unassigned?
- What work is aging or stalled?
- What work is being reassigned?
- What work has been reopened?
- How is workload distributed across the team?
- How quickly is work being resolved?

Core domain concepts: Tickets, Teams, Categories, Projects, Users, Ticket events, SLA tracking, Assignment changes, Reopen activity, Workload, Operational status.

The existing FlowOps application documentation remains authoritative for the application itself. **Do not rewrite or reinterpret the FlowOps domain model when documenting the Fabric layer.**

## Why the Fabric Project Was Built

To demonstrate practical, end-to-end experience with a modern data platform, extending a portfolio that already covers Power BI, Tableau, Python automation, PostgreSQL, SQL, software engineering, and AI/automation.

Progression demonstrated:
```
Operational Application → Operational Database → Data Ingestion →
Data Validation → Data Transformation → Analytical Storage →
Semantic Modeling → Business Analytics
```

The goal is broader than producing visualizations — it's the ability to move data through the entire analytical lifecycle.

## Primary Portfolio Message

> FlowOps demonstrates how an operational PostgreSQL-based application can be connected to Microsoft Fabric and transformed into a governed analytical data platform, using layered storage, automated data quality validation, Spark-based transformation, a dimensional warehouse, a Direct Lake semantic model, and Power BI analytics.

The documentation should show two connected capability sets, not isolated technologies:

**Data Engineering:** ingestion, incremental data movement, orchestration, data quality, transformation, layered architecture, analytical storage, dimensional modeling.

**Analytics:** semantic modeling, DAX measures, operational KPIs, team performance analysis, ticket analysis, SLA analysis, workload analysis.

## What This Project Should Demonstrate

Practical familiarity with: Fabric Workspace, OneLake, Lakehouse architecture, Bronze/Silver layers, Fabric Data Factory, Copy Jobs, pipeline orchestration, incremental ingestion, PySpark/Spark notebooks, automated data quality validation, Fabric Warehouse, dimensional modeling, semantic models, Direct Lake, Power BI.

**Only describe a technology as implemented when the actual project implementation supports it.** Don't add technologies just because they're commonly associated with Fabric.

## Project Scope

```
Operational Source → Data Ingestion → Raw/Bronze Data → Data Quality →
Silver Transformation → Gold Analytical Warehouse → Semantic Model → Power BI
```

This is a focused portfolio implementation demonstrating the complete analytical lifecycle on a realistic operational application — not an attempt to build a full enterprise data platform.

## What the Project Is NOT

Do not claim implementation of features that were discussed but not actually built. In particular, do **NOT** claim:
- Fabric AI Functions
- AI Ticket Intelligence / AI-generated ticket summaries
- Machine-learning models
- Eventhouse / KQL / Real-Time Intelligence
- Streaming/event-driven ingestion
- Fabric Data Activator
- Fabric deployment pipelines
- Fabric Git integration

...unless subsequently implemented and verified. Ideas discussed during development are not equivalent to implemented functionality. Only implemented and verified functionality belongs in claims about the finished project.

## Relationship to the Existing FlowOps Engineering Project

The FlowOps application remains an important, separate part of the portfolio. The Fabric project must not replace or diminish the existing software-engineering story — present them as connected layers:

```
                 FLOWOPS
        Operations Platform
                 │
                 ▼
        PostgreSQL Database
                 │
                 ▼
       Microsoft Fabric Platform
                 │
        ┌────────┴────────┐
        ▼                 ▼
   Data Platform       Analytics
        │                 │
        ▼                 ▼
   Warehouse        Semantic Model
                          │
                          ▼
                       Power BI
```

This combination — building the operational app *and* building the analytical platform around its data — is important portfolio value.

## Documentation Philosophy

GitHub documentation should read as an engineering/data-platform case study, not a collection of screenshots. It should answer:

1. What problem does this solve?
2. What is the source system?
3. How does data move through the platform?
4. Why are Bronze, Silver, and Gold layers used?
5. How is data quality validated?
6. How is the analytical model structured?
7. How is Power BI connected to the analytical layer?
8. What was actually implemented?
9. How was the implementation validated?
10. What does this demonstrate technically?

Priority order: **Architecture → Process → Data → Validation → Analytics** — not Screenshots → Features → Screenshots. Screenshots are evidence; diagrams and writing communicate the architecture.

## Documentation Style

Aim for a clean, modern, structured, technically credible, concise, easy-to-scan, visually consistent portfolio piece, understandable to both technical and non-technical hiring professionals.

Avoid: excessive marketing language, exaggerated claims, unnecessary jargon, generic Fabric descriptions, long explanations of basic concepts, decorative low-information diagrams, unexplained screenshots, unverifiable claims.

## Evidence-Based Documentation Rule

Use the actual implementation as the source of truth:

1. Inspect the repository.
2. Inspect the existing FlowOps documentation.
3. Inspect the Fabric project structure when available.
4. Use screenshots supplied by the project owner as implementation evidence.
5. Use verified row counts and configuration details.
6. Clearly distinguish implemented functionality from proposed/future functionality.

**Never invent:** row counts, pipeline activities, transformations, relationships, measures, technologies, architecture components, performance metrics, business outcomes. If something can't be verified, don't state it as fact — ask the project owner.

## Documentation Phases

- **Phase 2 — Fabric Implementation:** Workspace, Data Factory, Copy Jobs, Bronze Lakehouse, Silver Lakehouse, Notebooks, Warehouse, stored procedures, semantic model, Power BI report.
- **Phase 3 — Data Pipeline:** source ingestion, reference-data ingestion, incremental ingestion, watermarking, merge behavior, Bronze storage, Data Quality, Silver transformation, Gold refresh, orchestration dependencies.
- **Phase 4 — Data Model & Analytics:** Silver tables, Gold tables, fact/dimension structure, relationships, semantic model, DAX measures, Power BI report pages, analytical questions answered.
- **Phase 5 — Visual Documentation:** end-to-end architecture, pipeline flow, data lifecycle, Bronze→Silver→Gold, data quality flow, semantic model diagrams. Diagrams explain architecture; screenshots prove implementation.
- **Phase 6 — GitHub README:** the final public-facing README, written only after the preceding phases are complete, telling the story:

```
Project Overview → Why It Was Built → Architecture → Pipeline Flow →
Data Lifecycle → Data Quality → Data Model → Power BI Analytics →
Technology Stack → Validation → Engineering Decisions → Future Enhancements
```

## Instructions for Claude Code

- Read this document before modifying Fabric documentation.
- Read the existing FlowOps CLAUDE.md before describing the underlying application.
- Inspect the repository before making assumptions.
- Preserve existing FlowOps engineering documentation — don't replace the existing FlowOps story with the Fabric story.
- Treat the Fabric platform as an analytical extension of the FlowOps application.
- Keep implemented functionality separate from future ideas.
- Do not invent missing implementation details.
- Ask for clarification when a significant architectural fact can't be verified.
- Prefer factual technical documentation over marketing language.
- Keep diagrams consistent with the actual implementation.
- Use screenshots supplied by the project owner as evidence.
- Do not expose credentials, passwords, API keys, connection strings, or other secrets in documentation.

**Ultimate objective:** produce documentation that lets a hiring manager understand, in a few minutes, that this project demonstrates an end-to-end Microsoft Fabric data platform built around a realistic operational application.

---

# PHASE 2 — Fabric Implementation Context

This section is the authoritative reference for the **currently implemented** Microsoft Fabric environment.

**IMPORTANT:**
- Treat these details as the current implemented state.
- Do not rename components in documentation unless explicitly instructed.
- Do not invent additional Fabric components.
- Do not assume that a discussed/proposed feature was implemented.
- If repository files, screenshots, and this document conflict, inspect the actual implementation and flag the discrepancy rather than silently inventing a resolution.
- Preserve the exact names of Fabric objects when documenting the implementation.
- Do not expose credentials, passwords, connection strings, API keys, or secrets.

## 2.1 Fabric Workspace

**Workspace:** `FlowOps Analytics`

```
FlowOps Analytics
│
├── CopyJob_FlowOps_Incremental      (Copy Job)
├── CopyJob_FlowOps_Reference        (Copy Job)
├── LH_FlowOps_Bronze                (Lakehouse)
├── LH_FlowOps_Silver                (Lakehouse)
├── NB_FlowOps_DataQuality           (Notebook)
├── NB_FlowOps_Transform             (Notebook)
├── PL_FlowOps_Ingestion             (Pipeline)
├── WH_FlowOps_Analytics             (Warehouse)
├── SM_FlowOps_Analytics             (Semantic Model)
└── FlowOps Operations Analytics     (Power BI Report)
```

There is also an older/duplicate workspace item displayed as `PL_FlowOps_Ingestion` with type **Copy Job** — this is **not** the active orchestration pipeline. The actual orchestration artifact is `PL_FlowOps_Ingestion` with type **Pipeline**. When documenting the architecture, distinguish the two.

## 2.2 Source System

The source system is the operational FlowOps PostgreSQL database hosted on **Neon**.

```
FlowOps Application
        ↓
PostgreSQL / Neon
        ↓
Microsoft Fabric
```

The Fabric implementation does not replace the operational database — it creates an analytical data path from the operational database into Fabric. Do not expose the PostgreSQL production password or complete connection string in documentation.

## 2.3 Fabric Architecture (Implemented)

```
FlowOps PostgreSQL / Neon
            │
            ▼
    Fabric Data Factory
            │
            ▼
     Bronze Lakehouse (LH_FlowOps_Bronze)
            │
            ▼
    Data Quality Validation (NB_FlowOps_DataQuality)
            │
            ▼
     Silver Lakehouse (LH_FlowOps_Silver)
            │
            ▼
   Silver Transformation (NB_FlowOps_Transform)
            │
            ▼
    Gold Fabric Warehouse (WH_FlowOps_Analytics)
            │
            ▼
 Direct Lake Semantic Model (SM_FlowOps_Analytics)
            │
            ▼
        Power BI (FlowOps Operations Analytics)
```

This is the authoritative high-level architecture.

## 2.4 Bronze Lakehouse

**Lakehouse:** `LH_FlowOps_Bronze`

Purpose: stores raw operational data extracted from the FlowOps PostgreSQL source. Intentionally close to source structure; raw tables use the `_raw` suffix.

Current Bronze raw tables: `categories_raw`, `organizations_raw`, `projects_raw`, `sla_configurations_raw`, `team_members_raw`, `teams_raw`, `ticket_comments_raw`, `ticket_events_raw`, `users_raw`, `tickets_raw`.

Do not describe Bronze as a fully cleaned or business-ready layer — its purpose is raw/landing storage.

## 2.5 Reference Data Ingestion

**Copy Job:** `CopyJob_FlowOps_Reference`

Source tables → Bronze destination:
| Source | Destination |
|---|---|
| `AspNetUsers` | `users_raw` |
| `categories` | `categories_raw` |
| `organizations` | `organizations_raw` |
| `projects` | `projects_raw` |
| `sla_configurations` | `sla_configurations_raw` |
| `team_members` | `team_members_raw` |
| `teams` | `teams_raw` |

This represents the reference-data ingestion path. Do not claim it is scheduled unless scheduling is explicitly verified elsewhere.

## 2.6 Incremental Data Ingestion

**Copy Job:** `CopyJob_FlowOps_Incremental` — handles operational ticket-related tables: `tickets`, `ticket_events`, `ticket_comments` → `tickets_raw`, `ticket_events_raw`, `ticket_comments_raw`.

| Table | Watermark | Merge Key | Write Behavior |
|---|---|---|---|
| tickets | `updated_at` | `id` | Merge |
| ticket_events | `id` | `id` | Merge |
| ticket_comments | `id` | `id` | Merge |

Supports both initial/full loading and subsequent incremental loading. The first run loaded existing data; a subsequent no-change run detected zero new/changed records; a later test update to an existing ticket generated new ticket events and an updated ticket record, successfully detected and propagated. This is evidence the incremental path was actually **tested**, not merely configured.

This is **incremental batch ingestion** — do not describe it as real-time streaming.

## 2.7 Initial Ingestion Validation

Initial incremental Copy Job run:
- tickets: 635
- ticket_events: 3,382
- ticket_comments: 1,105

Subsequent no-change incremental run: 0 / 0 / 0.

Later controlled test (single ticket update) detected: tickets: 1, ticket_events: 4, ticket_comments: 0. Resulting ticket event count increased from 3,382 → 3,386.

Describe this as a controlled validation of incremental ingestion. Do not imply these numbers represent live production business activity.

## 2.8 Silver Lakehouse

**Lakehouse:** `LH_FlowOps_Silver`

Purpose: transformed, analytics-oriented tables derived from Bronze raw data, produced by `NB_FlowOps_Transform`.

Current Silver tables and verified row counts (at time of writing — update this section rather than presenting outdated counts as current):

| Table | Rows |
|---|---|
| dim_ticket | 635 |
| fact_ticket_events | 3,386 |
| dim_user | 32 |
| dim_team | 8 |
| dim_category | 13 |
| dim_project | 11 |
| dim_organization | 6 |
| dim_date | 104 |

## 2.9 Silver Transformation

**Notebook:** `NB_FlowOps_Transform` — reads Bronze via the Fabric Lakehouse namespace, writes to Silver. Produces: `dim_ticket` (ticket-level descriptive/operational attributes), `dim_user` (analytics-relevant user info — auth/security fields excluded), `dim_team`, `dim_category`, `dim_project`, `dim_organization`, `fact_ticket_events` (ticket activity/event records), `dim_date` (date dimension for downstream warehouse/semantic model).

## 2.10 Gold Warehouse

**Warehouse:** `WH_FlowOps_Analytics`

Tables: `dbo.DimTicket`, `dbo.DimUser`, `dbo.DimTeam`, `dbo.DimCategory`, `dbo.DimProject`, `dbo.DimOrganization`, `dbo.FactTicket`, `dbo.FactTicketEvent`, `dbo.DimDate`.

Separates descriptive dimensions from ticket/event facts — this is the primary analytical serving layer consumed by the semantic model.

## 2.11 Gold Warehouse Model

**DimTicket** — ticket-level descriptive/status info: `TicketID`, `TicketReference`, `TicketTitle`, `WorkType`, `Priority`, `Status`, `RequesterID`, `AssigneeID`, `TeamID`, `ProjectID`, `CategoryID`, `CreatedAt`, `UpdatedAt`, `DueDate`, `SLATargetMinutes`, `SLAMet`, `ResolvedAt`, `ClosedAt`, `ResolutionCode`, `ReopenCount`, `AssignmentChangeCount`, `PendingReason`, `SprintBacklog`, `SprintID`.

**FactTicket** — ticket-level analytical facts/timestamps: `TicketID`, `TeamID`, `ProjectID`, `CategoryID`, `RequesterID`, `AssigneeID`, `CreatedAt`, `UpdatedAt`, `DueDate`, `SLATargetMinutes`, `SLAStartedAt`, `SLADueAt`, `SLAPausedMinutes`, `SLAMet`, `ResolvedAt`, `ClosedAt`, `ReopenCount`, `AssignmentChangeCount`, `SprintBacklog`, `SprintID`, `CreatedDate` (derived from `CreatedAt`, used for the date relationship).

**FactTicketEvent** — ticket activity history: `EventID`, `TicketID`, `EventType`, `ActorUserID`, `OccurredAt`, `ChangedField`, `OldValue`, `NewValue`, `EventNote`.

**Dimension tables:** `DimUser`, `DimTeam`, `DimCategory`, `DimProject`, `DimOrganization`, `DimDate` — descriptive context for analytical slicing/filtering.

## 2.12 Gold Refresh Procedure

**Stored procedure:** `dbo.usp_RefreshFlowOpsGold` — refreshes Gold analytical tables from Silver. Covers: `DimOrganization`, `DimTeam`, `DimCategory`, `DimProject`, `DimUser`, `DimTicket`, `FactTicketEvent`, `FactTicket`, `DimDate`. Executed successfully as part of the Fabric workflow.

Do not describe this as an incremental Warehouse merge — its current purpose is a full refresh of Gold from Silver.

## 2.13 Semantic Model

**Semantic model:** `SM_FlowOps_Analytics` — storage mode: **Direct Lake on OneLake**. Built on the Fabric Warehouse analytical model; uses dimensional relationships rather than a flat table source.

## 2.14 Semantic Model Relationships

```
DimProject[ProjectID]      1 ──── * FactTicket[ProjectID]
DimCategory[CategoryID]    1 ──── * FactTicket[CategoryID]
DimTeam[TeamID]            1 ──── * FactTicket[TeamID]
DimTicket[TicketID]        1 ──── 1 FactTicket[TicketID]
DimTicket[TicketID]        1 ──── * FactTicketEvent[TicketID]
DimUser[UserID]            1 ──── * FactTicket[AssigneeID]
DimOrganization[OrgID]     1 ──── * DimTeam[OrganizationID]
DimDate[Date]              1 ──── * FactTicket[CreatedDate]
```

All listed relationships are active, single-direction filtering. `RequesterID` was **not** configured as an additional active DimUser relationship. Do not invent additional relationships.

## 2.15 Power BI Report

**Report:** `FlowOps Operations Analytics` — three pages: Operations Overview, Team Performance, Ticket Details. Built on `SM_FlowOps_Analytics`. Demonstrates operational analytics, not a reproduction of the application UI.

## 2.16 Operations Overview (page)

Purpose: high-level view of ticket volume, operational status, SLA performance, team-level performance.

Visuals: Total Tickets, Open Tickets, In Progress Tickets, SLA Compliance %, Average Resolution Time, ticket volume trend, ticket volume by status, ticket volume by team, SLA compliance by team.

## 2.17 Team Performance (page)

Purpose: operational pressure, workload, SLA risk, reopen behavior, assignment activity, priority distribution across teams.

Metrics/visuals: Overdue Tickets, Reopened Tickets, Reopen Rate, Assignment Changes, Average Events per Ticket, Overdue Tickets by Team, Reopen Rate by Team, Assignment Changes by Team, Tickets by Priority.

Slicers: Date Range, Team, Status, Priority, Category, Display Name.

## 2.18 Ticket Details (page)

Purpose: granular ticket and workload analysis.

Metrics/visuals: Total Tickets, Resolved Tickets, Closed Tickets, Assigned Tickets, Unassigned Tickets, Tickets by Work Type, Resolution Time by Priority, SLA Compliance by Category, Assignment Changes by Team, Workload by Work Type.

Detail table fields: `TicketReference`, `TicketTitle`, `Priority`, `Status`, `TeamName`, `CategoryName`, `DisplayName`, `CreatedAt`, `ResolvedAt`, Average Resolution Hours.

## 2.19 DAX / Analytical Measures

- **Ticket volume/status:** Total Tickets, Open Tickets, In Progress Tickets, Pending Tickets, Resolved Tickets, Closed Tickets
- **SLA:** SLA Met Tickets, SLA Compliance %, Overdue Tickets
- **Resolution:** Average Resolution Hours, Average Resolution Days
- **Reopen analysis:** Reopened Tickets, Reopen Rate %
- **Assignment/workload:** Assigned Tickets, Unassigned Tickets, Assignment Changes, Average Assignment Changes, Average Events per Ticket

Document these as analytical calculations built on the semantic model — not application-side business rules.

## 2.20 Important Modeling Principle

The Fabric model intentionally separates **Dimensions** (`DimDate`, `DimUser`, `DimTeam`, `DimCategory`, `DimProject`, `DimOrganization`, `DimTicket`) from **Facts** (`FactTicket`, `FactTicketEvent`). Describe the model as a dimensional analytical model, not a direct replica of the PostgreSQL transactional schema.

## 2.21 Data Quality

Automated validation via `NB_FlowOps_DataQuality`: **19 checks, 0 issues detected.**

- **Completeness** — 8 checks covering required ticket fields.
- **Uniqueness** — 2 checks: ticket ID, ticket reference.
- **Domain validation** — 3 checks: status, priority, work type.
- **Temporal consistency** — 1 check: updated timestamp must not precede created timestamp.
- **Referential integrity** — 5 checks: team ID → teams, project ID → projects, category ID → categories, assignee ID → users, requester ID → users.

Result: **DQ Overall Status: PASS, Total Issues: 0.** Results persisted in `LH_FlowOps_Silver.dbo.dq_results` recording `RunTimestamp`, `CheckType`, `Check`, `IssueCount`, `Status`.

Do not claim the DQ system validates fields/rules beyond those listed above.

## 2.22 Data Quality as a Pipeline Gate

Data quality is part of the orchestrated Fabric workflow, not a standalone notebook:

```
Incremental Ingestion → Data Quality Validation → Silver Transformation → Gold Refresh
```

The pipeline validates incoming data before continuing through downstream layers. Full orchestration detail belongs in Phase 3.

## 2.23 Pipeline Artifact

**Pipeline:** `PL_FlowOps_Ingestion` — four activities in sequence:

```
Run_Incremental_Ingestion → Run_Data_Quality → Run_Silver_Transform → Run_Gold_Refresh
```

| Activity | Runs | Purpose |
|---|---|---|
| Run_Incremental_Ingestion | `CopyJob_FlowOps_Incremental` | Load new/changed operational ticket data into Bronze |
| Run_Data_Quality | `NB_FlowOps_DataQuality` | Validate Bronze data before downstream transformation |
| Run_Silver_Transform | `NB_FlowOps_Transform` | Transform Bronze data into analytical Silver tables |
| Run_Gold_Refresh | `dbo.usp_RefreshFlowOpsGold` | Refresh Gold Warehouse tables from Silver |

The pipeline has been successfully validated and executed end-to-end.

## 2.24 Pipeline Execution Evidence

A successful run, all four activities succeeded:

| Activity | Duration |
|---|---|
| Run_Incremental_Ingestion | 1 min 15 sec |
| Run_Data_Quality | 1 min 41 sec |
| Run_Silver_Transform | 4 min 12 sec |
| Run_Gold_Refresh | 23 sec |

Overall result: **Succeeded.** Present these durations as evidence from one captured run — not as guaranteed or average performance benchmarks.

## 2.25 Fabric Workspace Identity

**Workspace:** `FlowOps Analytics`
- Identity ID: `b45a314c-65f0-4ed7-a9e5-98cac90096c8`
- App ID: `7577238c-a988-49e3-b0d0-2c9102307957`

The workspace identity was added to workspace access as a **Contributor**. Notebook connection `Notebook_FlowOps_Fabric EdwardJonArquiza` uses Authentication: **Workspace identity**, Data gateway: **None**, Privacy level: **None**.

Do not expose credentials or secrets. These IDs may be documented for technical context but are not necessary in the public-facing README unless there's a specific reason to include them.

## 2.26 Current End-to-End State

```
FlowOps PostgreSQL → Incremental Copy Job → Bronze Lakehouse →
Automated Data Quality → Silver PySpark Transformation → Gold Fabric Warehouse →
Direct Lake Semantic Model → Power BI Report
```

The pipeline has been successfully executed end-to-end. Current verified DQ result: 19 checks, 0 issues, PASS. Current verified analytical data: 635 tickets, 3,386 ticket events, 32 users, 8 teams, 13 categories, 11 projects, 6 organizations, 104 dates.

These numbers describe the current verified Fabric analytical dataset and may change if source data is subsequently updated.

## 2.27 Documentation Rules for This Implementation

**DO:**
- Use the exact Fabric object names.
- Explain the purpose of each layer.
- Show how data moves from PostgreSQL to Power BI.
- Explain why Bronze/Silver/Gold layers exist.
- Explain the distinction between operational and analytical schemas.
- Show incremental ingestion as implemented batch processing.
- Show Data Quality as part of the pipeline.
- Show the dimensional Gold model.
- Show Direct Lake as the semantic-model storage mode.
- Use actual screenshots as implementation evidence.
- Use diagrams to explain architecture and flow.
- Distinguish verified results from design intent.
- Keep technical claims evidence-based.

**DO NOT:**
- Invent additional Fabric services.
- Claim real-time streaming.
- Claim AI functionality that was not implemented.
- Claim machine learning.
- Claim production-scale business outcomes.
- Claim performance benchmarks from a single pipeline run.
- Expose secrets.
- Present future enhancements as current features.
- Describe the Power BI report as the entire project.
- Replace the existing FlowOps application architecture with the Fabric architecture.

## 2.28 Visual Documentation Requirements (for Phase 5)

Eventual GitHub documentation should contain explanatory visuals for at least: end-to-end Fabric architecture, pipeline orchestration, data lifecycle, Bronze → Silver → Gold flow, data quality validation, and the analytical/star-schema model — all generated from the implementation documented in this file.

- **Diagrams** explain the architecture and process.
- **Screenshots** (provided by the project owner) prove the implementation exists.

Do not create diagrams containing architecture components not present in the implementation. Diagrams should be clean, modern, minimal, professional, technically accurate, and visually consistent with the FlowOps portfolio, prioritizing information hierarchy over decoration.

## 2.29 Phase 2 Completion Criteria

Phase 2 is complete when Claude Code understands: what the Fabric workspace contains; what the PostgreSQL source is; what the Bronze layer contains; what the Silver layer contains; what the Gold Warehouse contains; how the semantic model is structured; what the Power BI report contains; what DAX measures exist; what data-quality checks exist; what the orchestration pipeline contains; how incremental ingestion works; what has actually been tested; and which features are explicitly **not** implemented.

Phase 3 will document the detailed pipeline behavior, execution logic, data lifecycle, and engineering rationale. **Do not generate the final README yet. Do not generate the final architecture diagrams yet.** First complete and verify the project context.

---

# PHASE 3 — Data Pipeline, Orchestration & Data Lifecycle Context

This section documents **how data actually moves** through the implemented FlowOps Fabric platform. It is an implementation description, not a generic explanation of Microsoft Fabric.

Establishes the authoritative: ingestion flow, incremental processing behavior, Bronze lifecycle, Data Quality process, Silver transformation, Gold refresh, semantic serving path, pipeline orchestration, validation process, and end-to-end data lifecycle. Use this when creating architecture diagrams, pipeline flow diagrams, lifecycle diagrams, README explanations, or technical case-study documentation. **Do not introduce processing stages that do not exist.**

## 3.1 End-to-End Data Flow

```
FlowOps Application
        ↓
PostgreSQL / Neon
        ↓
Incremental Ingestion
        ↓
Bronze Lakehouse
        ↓
Data Quality Validation
        ↓
Silver Transformation
        ↓
Silver Lakehouse
        ↓
Gold Warehouse Refresh
        ↓
Fabric Warehouse
        ↓
Direct Lake Semantic Model
        ↓
Power BI
```

The operational application remains separate from the analytical platform. PostgreSQL is the operational source; Fabric performs analytical ingestion, validation, transformation, storage, and serving; Power BI consumes the resulting analytical model.

## 3.2 Pipeline Orchestration

Central orchestration artifact: `PL_FlowOps_Ingestion`, coordinating four stages in order (each depends on the successful completion of the previous one):

```
Run_Incremental_Ingestion → Run_Data_Quality → Run_Silver_Transform → Run_Gold_Refresh
```

Conceptually: **INGEST → VALIDATE → TRANSFORM → SERVE**. The semantic model and Power BI report consume the resulting Gold data only after the pipeline completes.

## 3.3 Stage 1 — Incremental Ingestion

Activity `Run_Incremental_Ingestion` runs `CopyJob_FlowOps_Incremental` to bring new/changed operational ticket data from PostgreSQL into Bronze:

```
PostgreSQL (tickets, ticket_events, ticket_comments)
        ↓
Bronze Lakehouse (tickets_raw, ticket_events_raw, ticket_comments_raw)
```

Uses watermark-based incremental detection.

## 3.4 Incremental Ingestion Logic

| Table | Source | Watermark | Merge Key | Write Method |
|---|---|---|---|---|
| tickets | `tickets` | `updated_at` | `id` | Merge |
| ticket_events | `ticket_events` | `id` | `id` | Merge |
| ticket_comments | `ticket_comments` | `id` | `id` | Merge |

`updated_at` lets changes to existing tickets be detected; `id` watermarks let new event/comment records be detected.

## 3.5 Why Incremental Ingestion Is Used

Purpose: avoid treating every pipeline execution as a complete reload of transactional data — instead identify data new or changed since the previous load.

```
Previous Source State → Watermark → New/Changed Records → Merge into Bronze
```

Relevant because FlowOps tickets/events keep changing after creation: status changes, updates, new events, new comments, assignment changes, resolution activity. The pipeline models the source as changing operational data, not a static dataset.

## 3.6 Incremental Ingestion Validation

- Initial load: tickets 635, ticket_events 3,382, ticket_comments 1,105.
- No-change run: 0 / 0 / 0 — confirms the process doesn't blindly reload all records.
- Controlled update to an existing ticket → incremental run detected: tickets 1, ticket_events 4, ticket_comments 0. Event count increased 3,382 → 3,386.

This is a controlled end-to-end validation that source changes propagate through incremental ingestion. Document as an **incremental-ingestion validation test** — this is **incremental batch processing**, not real-time ingestion.

## 3.7 Stage 2 — Bronze Storage

Raw data lands in `LH_FlowOps_Bronze`: `tickets_raw`, `ticket_events_raw`, `ticket_comments_raw`, `users_raw`, `teams_raw`, `categories_raw`, `projects_raw`, `organizations_raw`, `team_members_raw`, `sla_configurations_raw`.

```
Operational PostgreSQL → Bronze → Raw source-aligned data
```

Bronze is not the final analytical model.

## 3.8 Reference Data vs. Transactional Data

- **Reference/dimension-oriented**, loaded by `CopyJob_FlowOps_Reference`: `AspNetUsers`, `categories`, `organizations`, `projects`, `sla_configurations`, `team_members`, `teams`.
- **Transactional/operational activity**, loaded by `CopyJob_FlowOps_Incremental`: `tickets`, `ticket_events`, `ticket_comments`.

This split lets relatively stable reference data be handled separately from continuously changing ticket/activity data — a practical ingestion design choice worth calling out in documentation.

## 3.9 Stage 3 — Data Quality Validation

Activity `Run_Data_Quality` runs `NB_FlowOps_DataQuality` to validate ingested Bronze ticket data before it continues into transformation. Current implementation: **19 automated checks, 0 issues detected. DQ Overall Status: PASS.**

## 3.10 Data Quality Categories

| Category | # Checks | Covers |
|---|---|---|
| Completeness | 8 | Required ticket fields populated |
| Uniqueness | 2 | Ticket ID uniqueness, ticket reference uniqueness |
| Domain validation | 3 | Valid values for status, priority, work type |
| Temporal consistency | 1 | `updated_at >= created_at` |
| Referential integrity | 5 | `team_id`→teams, `project_id`→projects, `category_id`→categories, `assignee_id`→users, `requester_id`→users |

Total: 8+2+3+1+5 = **19 checks**.

## 3.11 Data Quality Result Storage

Results persist to `LH_FlowOps_Silver.dbo.dq_results`: `RunTimestamp`, `CheckType`, `Check`, `IssueCount`, `Status` — not just a transient notebook output. Current verified result: 19 checks, 0 issues, PASS.

Do not claim historical trend monitoring — the current notebook establishes the persistent DQ result table but currently **overwrites** the baseline result rather than maintaining an append-only run history.

## 3.12 Data Quality as a Pipeline Gate

```
Incremental Ingestion → Data Quality → Silver Transformation
```

The platform does not move directly from raw ingestion to the analytical layer — it explicitly introduces a validation stage as an engineering control, to catch structural/data-integrity problems before downstream processing. Do not claim a complex automated rollback mechanism exists — the documented capability is validation within the orchestrated flow.

## 3.13 Stage 4 — Silver Transformation

Activity `Run_Silver_Transform` runs `NB_FlowOps_Transform`, transforming Bronze source-oriented data into cleaner analytical structures in `LH_FlowOps_Silver`: `dim_ticket`, `dim_user`, `dim_team`, `dim_category`, `dim_project`, `dim_organization`, `fact_ticket_events`, `dim_date`.

```
Bronze (raw / source-aligned) → Silver (structured / analytics-oriented)
```

## 3.14 Silver Modeling Approach

Silver begins separating **Dimensions** (`dim_ticket`, `dim_user`, `dim_team`, `dim_category`, `dim_project`, `dim_organization`, `dim_date`) from **Facts** (`fact_ticket_events`). The final Gold model further splits ticket-level facts (`FactTicket`) from event-level activity (`FactTicketEvent`). Silver is the transformation/preparation stage for the final warehouse model.

## 3.15 Silver / Data Quality Relationship

```
Bronze → Data Quality → Silver Transformation
```

Clear separation of responsibilities: Bronze preserves ingested source data; Data Quality checks whether incoming data satisfies validation rules; Silver transforms and organizes validated data for analytical consumption. Reflect this separation in diagrams.

## 3.16 Stage 5 — Gold Warehouse Refresh

Activity `Run_Gold_Refresh` runs `dbo.usp_RefreshFlowOpsGold` against `WH_FlowOps_Analytics`, populating Gold from Silver: `DimOrganization`, `DimTeam`, `DimCategory`, `DimProject`, `DimUser`, `DimTicket`, `FactTicketEvent`, `FactTicket`, `DimDate`.

```
Silver Lakehouse → Gold Refresh Procedure → Fabric Warehouse
```

## 3.17 Gold Layer Purpose

Gold provides a stable analytical structure for downstream semantic modeling/reporting, separating **Dimensions** (`DimDate`, `DimUser`, `DimTeam`, `DimCategory`, `DimProject`, `DimOrganization`, `DimTicket`) from **Facts** (`FactTicket`, `FactTicketEvent`) — a dimensional structure suitable for Power BI. Present Gold as **analytics-ready/reporting-ready data**, not another raw ingestion layer.

## 3.18 Stage 6 — Semantic Modeling

After Gold refresh, data is exposed through `SM_FlowOps_Analytics` (Direct Lake on OneLake) — the business-facing analytical layer.

```
Gold Warehouse → Direct Lake Semantic Model → Power BI
```

Present the semantic model as the layer translating the Gold data model into reusable analytical concepts for Power BI.

## 3.19 Stage 7 — Power BI Analytics

Final consumption: `FlowOps Operations Analytics` (Operations Overview, Team Performance, Ticket Details pages), built on the semantic model — **not** connected directly to raw PostgreSQL.

```
PostgreSQL → Fabric Data Platform → Gold Warehouse → Semantic Model → Power BI
```

This separation is an important part of the architecture.

## 3.20 Complete Pipeline Flow (for diagramming)

```
FlowOps PostgreSQL / Neon
        ↓
Incremental Ingestion — CopyJob_FlowOps_Incremental
        ↓
Bronze Lakehouse — LH_FlowOps_Bronze
        ↓
Data Quality — 19 checks / 0 issues
        ↓
Silver Transformation — NB_FlowOps_Transform
        ↓
Silver Lakehouse — LH_FlowOps_Silver
        ↓
Gold Warehouse Refresh — usp_RefreshFlowOpsGold
        ↓
Fabric Warehouse — WH_FlowOps_Analytics
        ↓
Direct Lake Semantic Model — SM_FlowOps_Analytics
        ↓
Power BI — FlowOps Operations Analytics
```

This is the primary conceptual pipeline that should later become a polished visual diagram (Phase 5).

## 3.21 Data Lifecycle

```
SOURCE → INGEST → LAND → VALIDATE → TRANSFORM → SERVE → MODEL → ANALYZE
```

Mapped to actual components:

| Lifecycle Stage | Component |
|---|---|
| SOURCE | FlowOps PostgreSQL / Neon |
| INGEST | CopyJob_FlowOps_Incremental |
| LAND | LH_FlowOps_Bronze |
| VALIDATE | NB_FlowOps_DataQuality |
| TRANSFORM | NB_FlowOps_Transform |
| SERVE | WH_FlowOps_Analytics |
| MODEL | SM_FlowOps_Analytics |
| ANALYZE | FlowOps Operations Analytics |

This lifecycle should become a separate visual from the detailed pipeline architecture.

## 3.22 Bronze → Silver → Gold Story

- **Bronze — Raw:** capture source data in raw, source-aligned form (PostgreSQL → Bronze).
- **Silver — Refined:** transform and organize into cleaner analytical structures (Bronze → Silver).
- **Gold — Curated:** provide a dimensional analytical structure for semantic modeling/reporting (Silver → Gold Warehouse).

Story: **RAW → REFINED → CURATED**. Do not use generic enterprise-data terminology implying functionality not implemented.

## 3.23 Separation of Responsibilities

| Stage | Responsibility |
|---|---|
| PostgreSQL | Operational application data |
| Data Factory / Copy Job | Data movement |
| Bronze Lakehouse | Raw landing/storage |
| Data Quality Notebook | Validation |
| Silver Notebook | Transformation |
| Silver Lakehouse | Refined analytical data |
| Gold Warehouse | Curated analytical serving |
| Stored Procedure | Gold refresh |
| Semantic Model | Analytical relationships and measures |
| Power BI | Visualization and decision support |

This table can be adapted for the final README.

## 3.24 End-to-End Validation

Verified pipeline execution — all four activities SUCCESS, overall **Pipeline Succeeded**. Observed execution times from the captured successful run:

| Activity | Duration |
|---|---|
| Incremental Ingestion | 1m 15s |
| Data Quality | 1m 41s |
| Silver Transform | 4m 12s |
| Gold Refresh | 23s |

These are observations from one successful execution — not performance guarantees or benchmarks.

## 3.25 Controlled Incremental Test

```
Initial Load (635 tickets, 3,382 events)
        ↓
No-change incremental run (0 new/changed)
        ↓
Controlled ticket update
        ↓
Incremental ingestion (1 ticket, 4 events detected)
        ↓
Silver transformation → Gold refresh
        ↓
3,386 ticket events
```

Demonstrates the pipeline was tested across more than a single full load — both **initial ingestion** and **change detection/incremental ingestion** are proven. Worth emphasizing in the case study.

## 3.26 What the Pipeline Demonstrates

- **Data ingestion** — operational PostgreSQL data can be brought into Fabric.
- **Incremental processing** — new/changed transactional records detected via watermarks and merge keys.
- **Layered data architecture** — Bronze → Silver → Gold.
- **Automated validation** — data quality checks executed as part of the pipeline.
- **Transformation** — PySpark used to create analytical structures.
- **Analytical serving** — a Fabric Warehouse provides a curated analytical layer.
- **Semantic modeling** — a Direct Lake semantic model exposes reusable relationships/measures.
- **BI consumption** — Power BI consumes the semantic model for operational analysis.

Present these as a connected end-to-end workflow.

## 3.27 What the Pipeline Does NOT Demonstrate

Do not imply: streaming ingestion, real-time analytics, machine learning, AI enrichment, predictive modeling, automated anomaly detection, event-driven architecture, historical DQ trend tracking, automated rollback, enterprise-scale SLA guarantees, or production-scale workload benchmarking. These are outside the verified implementation — list only as clearly labeled future work if mentioned at all.

## 3.28 Engineering Narrative

> FlowOps generates operational data through its PostgreSQL-backed service-management application. Microsoft Fabric provides a dedicated analytical path for that data. Incremental Copy Jobs move changing operational records into a Bronze Lakehouse, where automated data-quality checks validate structural and referential integrity. Validated data is transformed with PySpark into Silver analytical structures, then promoted into a curated Gold Warehouse through a controlled refresh procedure. A Direct Lake semantic model exposes the analytical model to Power BI, where operational performance, SLA compliance, workload, ticket status, and team-level behavior can be analyzed.

This can be refined for the final README but must stay faithful to the implemented architecture.

## 3.29 Documentation Visuals Derived From This Phase (for Phase 5)

- **Visual 1 — End-to-End Architecture:** PostgreSQL → Fabric Data Factory → Bronze → Silver → Gold → Direct Lake Semantic Model → Power BI. Communicates the overall platform.
- **Visual 2 — Pipeline Flow:** the actual orchestration (`Run_Incremental_Ingestion` → `Run_Data_Quality` → `Run_Silver_Transform` → `Run_Gold_Refresh`) with each stage's purpose. Communicates process, not just architecture.
- **Visual 3 — Data Lifecycle:** SOURCE → INGEST → BRONZE → VALIDATE → SILVER → GOLD → MODEL → ANALYZE. Visually distinct from the pipeline diagram.
- **Visual 4 — Bronze/Silver/Gold:** RAW → REFINED → CURATED, with actual lakehouse/Warehouse names.
- **Visual 5 — Data Quality:** Bronze Data → 19 Automated Checks (Completeness, Uniqueness, Domain, Temporal, Referential Integrity) → PASS/Issues Detected → Silver Transformation.
- **Visual 6 — Analytical Model:** the Gold dimensional model — `DimDate`, `DimTeam`, `DimProject`, `DimCategory`, `DimUser`, `DimOrganization` around `FactTicket`; `DimTicket` → `FactTicketEvent`. Must be based on the actual semantic-model relationships in §2.14 — do not invent relationships.

## 3.30 Visual Design Direction

- **Style:** clean, modern, professional, minimal, technical, portfolio-quality.
- **Layout:** strong visual hierarchy; flow should read left-to-right or top-to-bottom immediately.
- **Color:** use the existing FlowOps visual identity where appropriate; restrained accent colors — not a colorful infographic poster.
- **Typography:** modern, clean sans-serif; labels readable at GitHub README scale.
- **Information density:** enough technical detail to demonstrate competence without becoming a system dump — the diagram should explain the architecture in seconds.

## 3.31 Screenshot Strategy

Project owner will supply screenshots of: Fabric workspace, Bronze Lakehouse, Silver Lakehouse, Warehouse, semantic model, pipeline canvas, pipeline run history, Data Quality results, Power BI report pages.

Recommended pattern:
```
[Explanatory Diagram]
Short explanation of what the architecture does.
[Actual Fabric Screenshot]
Evidence of the implemented component.
```

Do not use screenshots as substitutes for architecture diagrams. Do not create fake UI screenshots. Do not modify screenshots in a way that changes technical evidence.

## 3.32 Phase 3 Completion Criteria

Phase 3 is complete when Claude Code understands: the complete data lifecycle; the actual pipeline sequence; incremental ingestion behavior; watermark and merge behavior; Bronze responsibilities; reference vs. transactional ingestion; Data Quality's position in the pipeline; all 19 DQ checks; Silver transformation responsibilities; Gold refresh responsibilities; the semantic-model serving path; the Power BI consumption path; controlled incremental testing; successful end-to-end execution; what the pipeline does **not** implement; and what each future documentation visual needs to communicate.

**Do not generate the final README yet. Do not create the final diagrams yet. Do not invent screenshots.** Phase 4 will provide the actual screenshot inventory and establish how screenshots and explanatory visuals should be assembled into the final GitHub documentation.

---

# PHASE 4 — Screenshot Evidence & Visual Documentation Context

This section defines how the actual Fabric screenshots are used in the FlowOps Fabric portfolio documentation. Screenshots are **implementation evidence** — they do not replace architecture diagrams. Documentation combines: Explanatory Visuals + Written Technical Explanation + Actual Fabric Screenshots.

**Screenshot source directory:** `D:\CLAUDE Projects\Flow_Ops_Fabric\FlowOps_Fabric_Screenshots` — currently contains `Bronze_Lakehouse.PNG`, `Fabric_workspace.PNG`, `Measures.PNG`, `Page_1_Operations.PNG`, `Page_2_Team_Performance.PNG`, `Page_3_Ticket_Details.PNG`, `Pipeline_Run.PNG`, `Semantic_Model.PNG`, `Silver_Lakehouse.PNG`.

Every screenshot must be opened and visually inspected — never documented from its filename alone. Do not invent information not visible in the image or elsewhere verified in this file.

## 4.1 Verified Screenshot Inventory

All 9 screenshots have been inspected. Verified findings:

| Screenshot | Confirmed Contents | Matches Phase 1–3 Docs? |
|---|---|---|
| `Fabric_workspace.PNG` | Workspace `FlowOps Analytics`, listing: `CopyJob_FlowOps_Incremental`, `CopyJob_FlowOps_Reference`, `FlowOps Operations Analytics` (Report), `LH_FlowOps_Bronze` (Lakehouse + its SQL analytics endpoint), `LH_FlowOps_Silver` (Lakehouse + its SQL analytics endpoint), `NB_FlowOps_DataQuality`, `NB_FlowOps_Transform`, `PL_FlowOps_Ingestion` (Pipeline), `SM_FlowOps_Analytics` (Semantic model), `WH_FlowOps_Analytics` (Warehouse) | ⚠️ Only **one** `PL_FlowOps_Ingestion` item is visible, typed Pipeline. The older/duplicate Copy Job artifact of the same name (documented in §2.1) is **not visible** in this capture — see discrepancy note below. |
| `Bronze_Lakehouse.PNG` | Explorer shows `LH_FlowOps_Bronze` → `dbo` → Tables: `dim_category`, `dim_organization`, `dim_project`, `dim_team`, `dim_ticket`, `dim_user`, `fact_ticket_events` (plus Views/Functions/Stored Procedures folders) | ❌ **Discrepancy** — §2.4 documents Bronze as containing raw `_raw`-suffixed tables. This screenshot instead shows dimensional/fact-named tables. See discrepancy note below — **not silently resolved.** |
| `Silver_Lakehouse.PNG` | Explorer shows `LH_FlowOps_Silver` → Tables: `dim_category`, `dim_date`, `dim_organization`, `dim_project`, `dim_team`, `dim_ticket`, `dim_user`, `dq_results`, `fact_ticket_events` | ✅ Matches §2.8 and §3.11 exactly, including the `dq_results` table. `dq_results` grid visible: **19 rows**, all `Status = PASS`, `IssueCount = 0`, categories `Completeness` (7 visible: reference, title, work_type, created_at, status, priority, updated_at — 7 not 8, see note), `Uniqueness` (2: id, reference), `Domain` (3: status, priority, work_type), `Temporal` (1: updated_at >= created_at), `Referential Integrity` (5: team_id→teams, project_id→projects, category_id→categories, assignee_id→users, requester_id→users). |
| `Pipeline_Run.PNG` | Pipeline canvas: Copy job `Run_Incremental_Ingestion` → Notebook `Run_Data_Quality` → Notebook `Run_Silver_Transform` → Stored procedure `Run_Gold_Refresh`, all green/succeeded. Output grid confirms **Pipeline status: Succeeded**, run start 9/29/2026 3:38:28 PM–3:45:38 PM, durations: Run_Incremental_Ingestion 1m 15s, Run_Data_Quality 1m 41s, Run_Silver_Transform 4m 12s, Run_Gold_Refresh 23s | ✅ Exact match to §2.24/§3.24 durations. |
| `Semantic_Model.PNG` | Model view: `DimDate`, `DimProject`, `DimCategory`, `DimTeam`, `DimOrganization`, `DimUser`, `DimTicket`, `FactTicket`, `FactTicketEvent` with visible relationship lines matching §2.14 (DimProject/DimCategory/DimTeam/DimUser/DimDate → FactTicket; DimTicket → FactTicket and → FactTicketEvent; DimOrganization → DimTeam) | ✅ Matches documented relationships. |
| `Measures.PNG` | `MyMeasures` folder: Assigned Tickets, Assignment Changes, Average Assignment Changes, Average Events per Ticket, Average Resolution Days, Average Resolution Hours, Closed Tickets, **Column**, In Progress Tickets, Open Tickets, Overdue Tickets, Pending Tickets, **Reopen Rate %**, **Reopen Rate Debug**, Reopened Tickets, Resolved Tickets, SLA Compliance %, SLA Met Tickets, **Ticket Volume**, **Ticket Volume by Date**, Total Tickets, Unassigned Tickets | ⚠️ Mostly matches §2.19. Two items not previously documented: a plain `Column` entry (appears to be a leftover/implicit calculated column artifact, not a true measure) and `Reopen Rate Debug` (an internal/debug measure alongside the real `Reopen Rate %`). Do not present either as a polished analytical measure in the README without owner confirmation. |
| `Page_1_Operations.PNG` | Operations Overview page, filtered to **Date Range: Last 90 Days**: Total Tickets 567, Open Tickets 57, In Progress Tickets 89, SLA Compliance 48.50%, Avg Resolution Time 0.99 hrs, ticket status trend line, status pie (Resolved 194/34.22%, Closed 145/25.57%, InProgress 89/15.7%, Assigned 61/10.76%, Open 57/10.05%), ticket volume by team bar (Service Desk 266 … Street 1), SLA compliance by team bar (Business Operations 53.19% … Team Support 33.33%) | ⚠️ Total Tickets here is **567**, not the 635 documented in §2.7/§2.26. The page's Date Range slicer is set to "Last 90 Days" — 567 is very likely the **filtered** count, not the full table's row count. Treat these as two different, non-contradictory numbers (filtered report view vs. full Silver/Gold table count) and say so explicitly in the README; do not present 567 as "the dataset size." |
| `Page_2_Team_Performance.PNG` | Team Performance page (same 90-day filter): Overdue Tickets 292, Reopened Tickets 3, Reopen Rate 0.5%, Assignment Changes 9, Avg Events/Ticket 5.38; Overdue by Team, Reopen Rate by Team (Service Desk 1.1%, only team shown with reopens), Assignment Changes by Team (Service Desk 9, all others 0), Tickets by Priority (Medium 235, Low 165, High 110, Critical 57) | ✅ Matches described page purpose/visuals in §2.17. Team names visible across pages: Service Desk, IT Infrastructure, Platform Engineering, Business Operations, Application Support, Team Support, Team Agriculture, Street — 8 teams, consistent with the verified `dim_team` count of 8 (§2.8). Note "Team Agriculture" and "Street" read as sample/test data team names — fine to keep, but don't editorialize on it in the public README. |
| `Page_3_Ticket_Details.PNG` | Ticket Details page (same 90-day filter): Total Tickets 567, Resolved 194, Closed 145, Assigned 510, Unassigned 57; Tickets by Work Type (ServiceRequest 277, Incident 286, Task 3, Problem 1), Resolution Time by Priority, SLA Compliance by Category, Assignment Changes by Team, Workload by Work Type donut (567 total), and a detail table with columns `TicketReference`, `TicketTitle`, `Priority`, `Status`, `TeamName`, `CategoryName`, `DisplayName`, `CreatedAt`, `ResolvedAt`, `Average Resolution Hours` | ✅ Matches §2.18 described metrics/columns exactly. |

## 4.2 Open Discrepancies Requiring Clarification

Per the evidence-integrity rule (§2.27, §3.31): these are **flagged, not silently resolved**. Ask the project owner before writing the final README:

1. **Bronze Lakehouse table names.** `Bronze_Lakehouse.PNG` shows dimensional/fact table names (`dim_ticket`, `fact_ticket_events`, etc.) inside `LH_FlowOps_Bronze`, not the `_raw`-suffixed tables documented in §2.4/§2.7. Possible explanations: the screenshot file may be mislabeled (e.g., an earlier capture of Silver before `dim_date`/`dq_results` existed), or the actual Bronze layer's contents differ from what was described. Needs the project owner to confirm which is accurate.
2. **Duplicate `PL_FlowOps_Ingestion` artifact.** §2.1 documents an older/duplicate Copy Job item of this name alongside the real Pipeline. `Fabric_workspace.PNG` shows only one `PL_FlowOps_Ingestion` (type Pipeline) — the duplicate isn't visible in this capture. May simply mean it was already cleaned up, or the workspace view is filtered/scrolled. Confirm before claiming in the README that a duplicate no longer exists.
3. **Report ticket totals (567 vs. 635).** Likely explained by the Power BI pages defaulting to a "Last 90 Days" filter versus the full underlying table count — but confirm before stating both numbers in the same document, to avoid an apparent contradiction.

## 4.3 Screenshot Documentation Placement

| Screenshot | Recommended README Section | Supporting Diagram |
|---|---|---|
| `Fabric_workspace.PNG` | Fabric Architecture | Visual 1 (End-to-End Architecture) |
| `Bronze_Lakehouse.PNG` | Architecture / Bronze-Silver-Gold | Visual 4 (Bronze/Silver/Gold) — hold until discrepancy #1 is resolved |
| `Silver_Lakehouse.PNG` | Bronze → Silver → Gold | Visual 4 |
| `Pipeline_Run.PNG` | Pipeline Orchestration | Visual 2 (Pipeline Flow) |
| `Semantic_Model.PNG` | Data Model | Visual 6 (Analytical Model) |
| `Measures.PNG` | Semantic Model / Analytics | Visual 6 |
| `Page_1_Operations.PNG` | Power BI Analytics → Operations Overview | — |
| `Page_2_Team_Performance.PNG` | Power BI Analytics → Team Performance | — |
| `Page_3_Ticket_Details.PNG` | Power BI Analytics → Ticket Details | — |

Every screenshot needs a short caption answering "what is this evidence showing?" — never just the filename repeated. Example: *"Figure — Direct Lake semantic model showing the dimensional relationships used by the Power BI report."*

## 4.4 Screenshot vs. Diagram Strategy

- **Screenshots** prove the implementation exists — use the 9 files above as-is, unmodified.
- **Diagrams** explain the architecture and process — six polished explanatory visuals to be created in Phase 5:
  1. End-to-End Architecture (source → Fabric Data Factory → Bronze → Silver → Gold → Semantic Model → Power BI, distinguishing Source / Data Platform / Semantic Layer / Consumption zones)
  2. Pipeline Flow (`CopyJob_FlowOps_Incremental` → `NB_FlowOps_DataQuality` → `NB_FlowOps_Transform` → `dbo.usp_RefreshFlowOpsGold`, answering "what happens to the data?" as distinct from the architecture diagram's "where does data go?")
  3. Data Lifecycle (SOURCE → INGEST → BRONZE → VALIDATE → SILVER → GOLD → MODEL → ANALYZE, visually distinct from the pipeline diagram)
  4. Bronze / Silver / Gold (RAW → REFINED → CURATED, with actual lakehouse/warehouse names — pending discrepancy #1)
  5. Data Quality Flow (Bronze Data → 19 Automated Checks across the 5 categories → PASS → Silver Transformation — no fake branching/remediation workflow)
  6. Analytical Model (the Gold dimensional model per the verified relationships in §2.14 and confirmed against `Semantic_Model.PNG` — do not invent relationships, do not add a `RequesterID` relationship that isn't implemented)

Diagrams must never pretend to be Fabric screenshots.

## 4.5 Visual Design Direction

Clean, modern, minimal, professional, technical, restrained, highly readable, suitable for GitHub, consistent with FlowOps branding. Avoid: overly colorful infographic styles, 3D effects, unnecessary icons, decorative illustrations, excessive gradients, giant text, visual clutter. Use subtle color coding for Source / Data Platform / Analytical Layer / Consumption zones — never decoratively.

## 4.6 Diagram & Screenshot Output Location

Before creating or moving any files, inspect the existing repository structure — do not assume `docs/fabric/` exists or copy/move the screenshots until that's confirmed. Preferred structure once confirmed appropriate:

```
docs/
└── fabric/
    ├── diagrams/
    │   ├── flowops-fabric-architecture.*
    │   ├── flowops-pipeline-flow.*
    │   ├── flowops-data-lifecycle.*
    │   ├── flowops-bronze-silver-gold.*
    │   ├── flowops-data-quality.*
    │   └── flowops-data-model.*
    └── screenshots/
        └── (the 9 files currently in FlowOps_Fabric_Screenshots/)
```

Where practical, keep editable diagram sources (e.g., Mermaid `.mmd`) alongside rendered images — don't create documentation visuals that can't reasonably be maintained later.

## 4.7 Visual Evidence Hierarchy

1. Architecture diagram — explains the system.
2. Pipeline diagram — explains the processing flow.
3. Actual Fabric screenshots — prove the implementation.
4. Power BI screenshots — show the analytical output.

A reader should understand the project before looking closely at every screenshot.

## 4.8 Screenshot Integrity Rule

Never fabricate UI elements, edit technical values, replace labels, alter counts, change pipeline states, remove failed runs if relevant, or make a screenshot appear to show functionality that doesn't exist. Any conflict between a screenshot and the documented implementation gets flagged (see §4.2) — never silently resolved, and never edited away.

## 4.9 Phase 4 Completion Criteria

Phase 4 is complete now that all 9 screenshots have been inspected, an evidence inventory built (§4.1), placement decided (§4.3), the six required diagrams specified (§4.4), and discrepancies flagged rather than silently resolved (§4.2). **The 3 open discrepancies in §4.2 should be resolved with the project owner before the final README or diagrams are produced.** Do not finalize the README until they are. Phase 5 will define the final GitHub README structure, case-study narrative, and portfolio presentation strategy.

---

# PHASE 5 — GitHub README, Case Study & Portfolio Documentation

This is the final documentation phase: turning Phases 1–4 into a polished, professional GitHub repository and technical case study.

**IMPORTANT:** The project owner has an existing portfolio website/project that presents their portfolio projects. **Before finalizing the FlowOps README, inspect that existing portfolio project** — it is the source of truth for presentation style, naming conventions, case-study structure, terminology, tone, visual hierarchy, and portfolio positioning. Do not invent a different presentation style. The FlowOps GitHub documentation should feel like a deeper technical companion to the existing portfolio project — not a stylistic departure from it.

## 5.1 First Step — Inspect the Existing Portfolio Project

Before touching the FlowOps README, inspect the existing portfolio project for: project cards, project descriptions, case-study pages, project detail structures, typography, visual hierarchy, section naming, technology presentation, project outcomes, architecture presentation, screenshots, existing GitHub links, and existing documentation patterns.

Goal: understand *how this portfolio already tells the story of a project*, then follow that language and philosophy for FlowOps. Reuse conventions — don't copy another project's content.

## 5.2 Relationship Between Portfolio and GitHub

| | Portfolio | GitHub |
|---|---|---|
| Provides | Concise overview, business/technical problem, key capabilities, visual impact, selected screenshots, technologies, high-level architecture, outcome | Deeper technical context, architecture, implementation detail, pipeline flow, data lifecycle, data quality, data model, semantic model, Power BI implementation, validation, technical decisions, project structure |
| Answers | "What did you build and why should I care?" | "How did you build it and how does it work?" |

The two complement each other — they should not duplicate the same content.

## 5.3 Final README Objective

Within the first few minutes, a technical/hiring reader should understand: (1) what FlowOps is, (2) what the Fabric project adds, (3) where the data comes from, (4) how data moves through Fabric, (5) why Bronze/Silver/Gold layers exist, (6) how data quality is handled, (7) how the analytical model is structured, (8) how Power BI consumes the model, (9) what was actually implemented, (10) how it was validated.

The README should communicate **end-to-end ownership of an analytical data platform**, not "Power BI dashboard development."

## 5.4 Recommended README Structure

Starting point — adapt to the existing portfolio's conventions after inspecting it, and prioritize readability/narrative flow over rigidly following this list:

```
# FlowOps Service Operations Analytics Platform
Project introduction
Key highlights
Architecture
Pipeline Flow
Data Lifecycle
Data Quality
Data Model
Power BI Analytics
Technology Stack
Implementation Details
Validation & Results
Engineering Decisions
Project Structure
Future Enhancements
Portfolio / Project Links
```

## 5.5 README Opening Section

Establish the FlowOps ↔ Fabric relationship immediately:

```
FlowOps (Operational Application) → PostgreSQL (Operational Data) →
Microsoft Fabric (Analytical Data Platform) → Power BI (Operational Analytics)
```

Avoid generic statements like "Microsoft Fabric is a comprehensive analytics platform…" — that describes Fabric, not this project. Describe what was actually built.

## 5.6 Project Overview

Explain FlowOps as an Operations & Delivery Management Platform centered on IT Support/Service Desk workflows, then the Fabric extension: an analytical data platform built around FlowOps' operational PostgreSQL data, moving through PostgreSQL → Bronze → Data Quality → Silver → Gold Warehouse → Direct Lake Semantic Model → Power BI. Keep this concise — detailed architecture comes later.

## 5.7 Why This Project

Frame the motivation as connecting **Operational Application + Data Engineering + Analytics**, demonstrating practical experience with ingestion, incremental processing, orchestration, Lakehouse architecture, data quality, PySpark transformation, Warehouse modeling, semantic modeling, Direct Lake, and Power BI. Present it as an applied implementation, not a Fabric learning exercise.

## 5.8 Architecture Section

Use the Phase 4 architecture diagram (Visual 1).

```
## Architecture
Short explanation.
[Architecture Diagram]
### Architecture Layers
Source / Data Platform / Analytical Layer / Consumption
```

Explain each layer's role in *this* project, not a textbook explanation of Fabric.

## 5.9 Pipeline Flow Section

Use the Phase 4 pipeline diagram (Visual 2): Incremental Ingestion → Data Quality → Silver Transformation → Gold Refresh, with the actual `Pipeline_Run.PNG` screenshot as implementation evidence.

```
## Pipeline Flow
[Pipeline Diagram]
### Orchestration
Explanation.
[Pipeline Screenshot]
```

Reader should come away understanding both what the pipeline is designed to do and that it demonstrably ran successfully.

## 5.10 Data Lifecycle Section

Use the Phase 4 lifecycle diagram (Visual 3): SOURCE → INGEST → BRONZE → VALIDATE → SILVER → GOLD → MODEL → ANALYZE. Emphasize movement/refinement of data over individual Fabric products.

## 5.11 Bronze / Silver / Gold Section

Bronze (raw/source-aligned, `LH_FlowOps_Bronze`) → Silver (refined analytical structures, `LH_FlowOps_Silver`) → Gold (curated analytical Warehouse, `WH_FlowOps_Analytics`). Use the layered diagram (Visual 4) plus the Bronze/Silver screenshots where useful — **note: Visual 4 and the Bronze screenshot are on hold pending discrepancy #1 in §4.2.** Emphasize RAW → REFINED → CURATED.

## 5.12 Data Quality Section

Give this real weight — it's one of the strongest engineering aspects of the case study. Explain why validation exists, where it sits in the pipeline, what categories are checked, and the current result: **19 automated checks, 0 issues detected, PASS**, across Completeness / Uniqueness / Domain / Temporal / Referential Integrity. Use the Data Quality diagram (Visual 5) and the `dq_results` evidence from `Silver_Lakehouse.PNG`. Do not imply historical DQ trend reporting — it isn't implemented (§3.11).

## 5.13 Incremental Ingestion Section

Document because it distinguishes this from a one-time ETL demo:

```
tickets         — watermark: updated_at, merge key: id
ticket_events   — watermark: id, merge key: id
ticket_comments — watermark: id, merge key: id
```

Then the controlled validation sequence: Initial load (635 tickets, 3,382 events) → no-change run (0/0) → controlled update → incremental detection (1 ticket, 4 events) → downstream transformation → Gold refresh → 3,386 ticket events. Label clearly as a **controlled implementation test** — do not imply production-scale throughput.

## 5.14 Data Model Section

Explain the analytical model, not the full PostgreSQL transactional schema. Show the semantic model diagram/screenshot (`Semantic_Model.PNG`). Distinguish Dimensions (`DimDate`, `DimUser`, `DimTeam`, `DimCategory`, `DimProject`, `DimOrganization`, `DimTicket`) from Facts (`FactTicket`, `FactTicketEvent`).

## 5.15 Semantic Model Section

`SM_FlowOps_Analytics`, storage mode Direct Lake on OneLake — the analytical layer between Gold Warehouse and Power BI, providing relationships, reusable measures, analytical filtering, business-facing metrics. Include the Measures screenshot where useful (excluding the internal `Reopen Rate Debug` / `Column` artifacts noted in §4.1 unless the owner wants them shown). Focus on how the semantic model supports the analytical product — not a DAX tutorial.

## 5.16 Power BI Analytics Section

Report `FlowOps Operations Analytics`, three pages:
- **Operations Overview** — high-level operational status, ticket volume, SLA performance, team analysis.
- **Team Performance** — operational pressure, overdue work, reopen activity, assignment changes, priorities, team-level analysis.
- **Ticket Details** — granular ticket, workload, resolution, SLA, category, priority, assignment analysis.

Use `Page_1_Operations.PNG`, `Page_2_Team_Performance.PNG`, `Page_3_Ticket_Details.PNG`. For each page, answer "what operational question does this page help answer?" rather than listing chart types.

## 5.17 Technology Stack

Concise table, implemented technologies only — verify against the repo/project context before finalizing:

| Technology | Role |
|---|---|
| PostgreSQL / Neon | Operational data source |
| Microsoft Fabric Data Factory | Data ingestion/orchestration |
| Fabric Lakehouse | Bronze/Silver storage |
| PySpark / Spark Notebooks | Data transformation |
| Fabric Warehouse | Gold analytical storage |
| T-SQL / Stored Procedure | Gold refresh |
| Direct Lake | Semantic model storage mode |
| Power BI | Analytics and visualization |
| DAX | Analytical measures |

Don't add technologies just because they're commonly associated with Fabric.

## 5.18 Validation & Results

Concise section with verified evidence: DQ (19 checks, 0 issues, PASS), Pipeline (all 4 activities succeeded), Incremental ingestion (initial load → no-change validation → controlled-update validation), and current analytical data (635 tickets, 3,386 ticket events, 32 users, 8 teams, 13 categories, 11 projects, 6 organizations, 104 dates). State these represent the current verified dataset and may change if the source database changes.

## 5.19 Observed Pipeline Execution

If included: Incremental Ingestion 1m 15s, Data Quality 1m 41s, Silver Transform 4m 12s, Gold Refresh 23s — label as **observed durations from one successful pipeline execution**. Never call them benchmarks, SLAs, average execution times, or guaranteed performance.

## 5.20 Engineering Decisions

Concise section on implementation decisions actually supported by the documented context, e.g.: why incremental ingestion over full reload; why Bronze/Silver/Gold separation; why Data Quality runs before transformation; why the Warehouse serves as the final analytical layer; why Direct Lake for the Power BI consumption layer. Do not invent ADRs that don't exist.

## 5.21 Project Structure

Inspect the actual repository before documenting structure — don't invent a directory tree. A possible shape (verify against reality):

```
docs/
└── fabric/
    ├── diagrams/
    ├── screenshots/
    └── FABRIC_PROJECT_CONTEXT.md
```

## 5.22 Future Enhancements

Keep clearly separated from implemented functionality. Potential areas (only if clearly labeled as future work): AI-assisted ticket intelligence, richer historical data-quality monitoring, additional analytical dimensions, deployment automation, expanded Fabric governance. Never imply Fabric AI Ticket Intelligence was implemented.

## 5.23 Portfolio Link

Include a link to the existing portfolio project only if the URL can be verified from the repo or the portfolio project itself — never invent a URL. The GitHub README functions as the deeper technical documentation behind the portfolio project.

## 5.24 Tone and Writing Style

Follow the tone established by the existing portfolio project (identify whether it's concise / technical / business-oriented / case-study-oriented / engineering-oriented, then match it). Stay professional, factual, confident, technically specific, easy to scan. Avoid excessive self-promotion, exaggerated claims, generic "enterprise-grade" language, unsupported business outcomes, filler, and unnecessary explanations of Microsoft terminology. Let the architecture and evidence demonstrate the capability.

## 5.25 Visual Consistency With Existing Portfolio

Inspect the portfolio before finalizing visual assets — use it as a reference for colors, typography, terminology, visual hierarchy, naming, and tone. GitHub documentation should feel related to the portfolio without duplicating its UI, and stay optimized for GitHub readability — don't force website UI design into technical diagrams if it reduces clarity.

## 5.26 README Narrative Principle

```
WHAT → WHY → ARCHITECTURE → HOW DATA MOVES → HOW DATA IS VALIDATED →
HOW DATA IS TRANSFORMED → HOW DATA IS MODELED → HOW DATA IS ANALYZED →
HOW IT WAS VALIDATED
```

This is the core case-study story.

## 5.27 Do Not Overdocument

Detailed enough to demonstrate competence, not a complete internal engineering spec. Use this CLAUDE.md for implementation facts; use the README for the most important technical story, linking to supporting documentation for deeper detail rather than dumping everything into the main README.

## 5.28 Final Documentation Quality Standard

Evaluate as a first-time hiring-manager reader: within 30 seconds — can they tell what this project is? Within 1 minute — the architecture? Within 2 minutes — how data moves through Fabric? Within 3 minutes — evidence the implementation exists? After deeper reading — ingestion, data quality, transformation, warehouse, semantic modeling, Power BI all understood? If not, revise.

## 5.29 Final Accuracy Review

Before committing, verify every major claim against: (1) existing FlowOps repository, (2) Phase 1 context, (3) Phase 2 Fabric implementation context, (4) Phase 3 pipeline context, (5) Phase 4 screenshots, (6) existing portfolio project. Check specifically for: incorrect component names, outdated row counts, invented features, incorrect relationships, incorrect DAX claims, incorrect pipeline behavior, unsupported performance claims, AI features accidentally presented as implemented, real-time claims, exposed credentials, screenshots that don't match their captions. **Flag discrepancies rather than silently inventing a resolution** — the three items in §4.2 are still open and should be resolved first.

## 5.30 Final Deliverables

- **Primary:** `README.md`
- **Documentation context:** `docs/fabric/FABRIC_PROJECT_CONTEXT.md` (or this `CLAUDE.md`, depending on final repo structure — verify before assuming)
- **Architecture visuals (minimum):** End-to-End Architecture, Pipeline Flow, Data Lifecycle, Bronze/Silver/Gold, Data Quality, Analytical Model
- **Evidence:** organized copies/references of the actual Fabric screenshots
- **Supporting documentation:** only where it materially improves the repository — don't create files just to pad the project's apparent size

## 5.31 Final Portfolio Positioning

```
FlowOps (Operational Application) → PostgreSQL (Operational Data) →
Microsoft Fabric (Data Platform) → Bronze → Silver → Gold (Data Engineering) →
Direct Lake (Semantic Layer) → Power BI (Operational Analytics)
```

Final message: **"This project demonstrates the ability to take operational application data and build an end-to-end analytical data platform around it."** Not: "This project is a Power BI dashboard." The Power BI report is the final consumption layer — the data platform is the project.

## 5.32 Final Instruction to Claude Code

Before making changes: (1) inspect the existing FlowOps repository, (2) inspect the existing FlowOps README, (3) inspect the existing portfolio project, (4) re-inspect all screenshots in `FlowOps_Fabric_Screenshots`, (5) read all Phase 1–4 context in this file, (6) compare proposed documentation against the actual implementation, (7) identify contradictions or missing evidence, (8) resolve only what can be verified, (9) ask for clarification only where a material technical fact can't be established. Then: (10) build the documentation visuals, (11) organize the screenshots, (12) construct the GitHub README, (13) ensure links/image references work, (14) review as a first-time technical reader, (15) perform a final factual/technical accuracy pass.

**Do NOT** modify the FlowOps application itself, add new Fabric functionality, redesign the Power BI report, invent features, or expose credentials. The objective is documentation and presentation of the completed implementation.

## 5.33 Definition of Done

- [ ] Existing portfolio project inspected
- [ ] Existing FlowOps README inspected
- [ ] Phase 1–4 context incorporated
- [ ] All Fabric screenshots inspected
- [ ] Screenshot evidence mapped to documentation sections
- [ ] Architecture diagram complete
- [ ] Pipeline Flow diagram complete
- [ ] Data Lifecycle diagram complete
- [ ] Bronze/Silver/Gold diagram complete
- [ ] Data Quality diagram complete
- [ ] Analytical Model diagram complete
- [ ] README complete
- [ ] README matches the existing portfolio's terminology and positioning
- [ ] README explains the project without requiring the reader to inspect the code
- [ ] Technical implementation claims are evidence-based
- [ ] Screenshots correctly captioned
- [ ] GitHub image paths work
- [ ] No credentials or secrets present
- [ ] No unimplemented features presented as current functionality
- [ ] Final documentation presents the project as an end-to-end Microsoft Fabric data platform, not just a Power BI dashboard

The final result should feel like a polished technical case study that supports the existing portfolio project.
