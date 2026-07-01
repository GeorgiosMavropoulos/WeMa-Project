# AI-Driven Project Execution Platform

## Vision

This product is an AI-driven project execution platform for Agile teams that transforms natural language into structured work and automates the coordination layer of software development. It removes the need for manual task management, fragmented tool switching, and repetitive reporting by turning communication directly into actionable workflows.

Planning, tracking, and reporting are continuously automated and synchronized with actual engineering activity.

## Target Users

- CEOs
- Project Managers
- HR
- Small software development teams
- Game development, design, or marketing agencies

## Core Problems Solved

- Time-consuming manual Kanban task creation and maintenance
- Fragmented tool usage across Kanban boards, Git, and communication tools
- Lack of real-time visibility into development progress
- Manual, subjective reporting overhead
- Lack of standardized task complexity estimation
- Disconnected Git workflow from project management
- Manual task breakdown left entirely to developers
- Delayed communication of changing requirements
- Time wasted on standup meetings

## Project Philosophy

- Workflow first.
- AI assists.
- Humans decide.
- The workflow database, workflow state, and event history are the single source of truth.
- AI outputs, notifications, and reports are derived artifacts — they never override workflow state.
- The system must never report an action as successful unless it was safely persisted.

## Architecture Overview

The MVP uses a **centralized, customer/team-controlled shared server deployment**. Users access the platform through a browser. The internal architecture stays modular even though the MVP deployment is all-in-one:

- Web UI
- Backend API
- Workflow Engine
- Rule Handler
- AI Service
- GitHub Integration (later)
- Notification Service
- Database

AI requests are handled asynchronously through a job queue, with configurable concurrency, per-job-type timeouts, and deterministic rule-based validation before any AI output is stored. AI failures never block core workflow operations.

## Scalability Target (MVP)

- Small Agile team: ~10–15 total users (1–2 PMs, 5–10 developers, 1 admin)
- ~3–5 concurrent active users
- Not targeting enterprise scale, multi-tenant SaaS, or high AI concurrency

## Feature Areas

1. **Core Platform Features** — auth, roles, dashboards, project/team management, Kanban board, task management, notifications, activity history
2. **Integration Features (Git layer)** — *Later*: GitHub integration, PR tracking, branch↔task linking, commit tracking
3. **AI Agent Features** — chat agent, natural language/voice task creation, task decomposition, requirement clarification, standup summarization, AI-generated reports
4. **Workflow Automation Features** — auto status transitions, workflow suggestions, human-in-the-loop approval, auto Kanban card creation
5. **Analytics Features** — task completion rate, cycle time, PR review time, team productivity insights, bottleneck detection

> GitHub/Git-layer integration is deferred to a later phase. The core workflow platform must remain fully functional without it.

## Architecture Decision Records (ADRs)

| ADR | Title | Status |
|---|---|---|
| ADR-001 | Deployment Model | Proposed / Under Team Review |
| ADR-002 | AI Service Architecture | Draft |
| ADR-003 | Source of Truth | Accepted — MVP Scope |
| ADR-004 | Failure Philosophy | Proposed / Under Team Review |
| ADR-005 | Scalability Target | Proposed / Under Team Review |

## Deployment & Operational Notes

- Deployment: Docker-based, on customer/team-managed infrastructure
- Remote access: via customer-managed VPN/tunneling (no public internet exposure required for MVP)
- Data ownership: the customer
- Responsibility split: the team is responsible for application robustness, software bugs, upgrades, and AI model updates; the customer is responsible for infrastructure

## Status

This project is currently in the pre-requirements phase: finalizing architectural decisions (ADRs) before breaking platform features into epics and user stories.