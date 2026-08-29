# Quantum Architecture

## Purpose

Quantum is designed as a long-lived personal automation platform. The architecture must allow agents, AI providers, storage engines, integrations, and client applications to evolve independently.

## Core boundaries

```text
Clients
   |
   v
Core API / Events
   |
   +--> Agents
   +--> Orchestration
   +--> Memory
   +--> Tools
   +--> Security / Policy
```

### Core

Owns stable domain contracts, events, identifiers, configuration abstractions, and shared primitives. Core must not depend on concrete integrations or AI vendors.

### Agents

Agents are isolated capabilities with explicit inputs, outputs, tools, memory access, and permission requirements. An agent must never receive unrestricted infrastructure access by default.

### Memory

Provides a provider-independent interface for short-term context, long-term memory, semantic retrieval, and user-approved personal knowledge. Storage implementations remain replaceable.

### Orchestration

Coordinates events, schedules, workflows, retries, queues, and agent execution. n8n may be used as an implementation/integration component, but Quantum must not become architecturally dependent on it.

### Tools

Adapters for external systems such as GitHub, servers, databases, messaging platforms, calendars, and future services. Each tool exposes a narrow capability contract.

### Security

Centralizes authentication, authorization, capability policies, secrets handling, audit logs, approval gates, and risk classification.

### Clients

User-facing interfaces including Android, desktop, web, CLI, and future clients. Clients communicate through stable APIs/events rather than importing internal module implementations.

## Risk model

Actions are classified by impact. Read-only and reversible actions may be automated. Destructive, financial, security-sensitive, or externally consequential actions require explicit policy and, where configured, human approval.

## Design rule

No module may directly reach into another module's internal implementation. Communication happens through public contracts, events, or explicitly defined service interfaces.
