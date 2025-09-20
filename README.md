# Agents and MCPs: Supercharging Performance Testing and Beyond

> **STARWEST 2025 Conference Demo** | AI-Driven Performance Testing Pipeline

### Talk Abstract

#### Agents and MCPs: Supercharging Performance Testing and Beyond

Performance testing pipelines have traditionally relied on static scripts and manual orchestration, but as architectures become more dynamic, and microservices proliferate, these traditional approaches often buckle under rapid change. AI agents promise autonomous orchestration if they can seamlessly access the right data and workflows. Enter the Model Context Protocol (MCP), a universal spec that lets agents discover and invoke external tools and sources with a single, standardized interface.

In this talk, Kaushal will demonstrate how MCP-enabled agents, combined with low-code workflows and visual orchestration, can empower teams to build self-healing, context-aware performance testing pipelines. Kaushal will explain and show Langraph-powered agents, MCP servers, and orchestrations, showcasing the future of AI-driven performance testing as he uncovers patterns and practices for supercharging your performance pipelines and beyond.


## 🏗️ Complete Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                        Claude Desktop                            │
│                   (Single Interface for All Tools)               │
└────────────────────────────┬─────────────────────────────────────┘
                             │ MCP Protocol
        ┌────────────────────┼────────────────────┐
        │                    │                    │
┌───────▼────────┐   ┌───────▼────────┐   ┌───────▼────────┐
│  Atlassian MCP │   │   GitHub MCP   │   │   Slack MCP    │
│ JIRA/Confluence│   │  Code Analysis │   │  Notifications │
└────────────────┘   └────────────────┘   └────────────────┘
        │                    │                    │
        └────────────────────┼────────────────────┘
                             │
                    ┌────────▼────────┐
                    │    K6 MCP       │
                    │ Test Execution  │
                    └────────┬────────┘
                             │ HTTP
                    ┌────────▼────────┐
                    │  K6 App Server  │
                    │   (Port 3001)   │
                    └────────┬────────┘
                             │
                ┌────────────┼────────────┐
                │            │            │
        ┌───────▼────┐   ┌───▼───┐   ┌────▼─────┐
        │ Demo API   │   │ Redis │   │PostgreSQL│
        │ (Port 3000)│   │       │   │ Metrics  │
        └────────────┘   └───────┘   └──────────┘
```

## 📂 Repository Structure

This talk demonstration consists of three main repositories:

### 1. [Demo API](https://github.com/kaushald/talk-ai-perf-demo-api)
The target application for performance testing - a sample API server running on port 3000 with Redis and PostgreSQL backends.

### 2. [K6 App Server](https://github.com/kaushald/talk-ai-perf-k6-app-server)
HTTP server (port 3001) that orchestrates K6 test execution and manages performance test workflows.

### 3. [K6 MCP Server](https://github.com/kaushald/talk-ai-perf-k6-mcp-server)
Model Context Protocol server that enables Claude Desktop to interact with K6 for autonomous performance testing.
