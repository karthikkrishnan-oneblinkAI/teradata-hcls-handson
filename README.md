# 🏥 Claire HCLS Workshop — Hands-On Lab

Build an AI agent that queries live healthcare data — from a raw model call to a production deployment — in four progressive notebooks.

## What You'll Build

```
Raw Bedrock call        →  "I can call a model"
  + MCP (Teradata)      →  "It can query real data"
    + Strands Agent     →  "It reasons and iterates"
      + Skills          →  "It handles different tasks"
        + AgentCore     →  "It runs in production"
```

## Notebooks

| # | Notebook | What You Do |
|---|----------|-------------|
| 1 | **Foundations** | First Bedrock API call → connect to Teradata via MCP → build a Strands agent that queries real PA data |
| 2 | **Skills & Deep Dive** | Add modular skills (dashboard, care pathway review, fraud check) with automatic routing |
| 3 | **Deploy to AgentCore** | Package the same agent code into a container and deploy to managed infrastructure |
| 4 | **Your Turn** | Open-ended challenges — build new agents, skills, or explore AgentCore features |

## Stack

- **Model** — Claude on [Amazon Bedrock](https://aws.amazon.com/bedrock/)
- **Data** — [Teradata](https://www.teradata.com/) HCLS database (claims, prior auth, providers, members)
- **Agent Framework** — [Strands Agents SDK](https://strandsagents.com)
- **Data Access** — [Teradata MCP Server](https://github.com/Teradata/teradata-mcp-server)
- **Deployment** — [Amazon Bedrock AgentCore](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/)

## HCLS Database Schema

Key tables available in the lab:

| Table | Description |
|-------|-------------|
| `prior_auth_request` | PA headers (member, provider, facility, status) |
| `member` | Members / patients |
| `provider` | Ordering providers (NPI, specialty, credentials) |
| `facility` | Facilities (name, type, location) |
| `auth_cpt_code` / `cpt_codes` | CPT procedure codes on a PA |
| `auth_icd_code` | ICD diagnosis codes on a PA |
| `auth_clinical_notes` | Clinical notes and prior test results |
| `auth_status` | Status lookup (approved, denied, pending) |
| `care_pathways` | Prerequisite rules (which CPTs require prior steps) |
| `WORKERS_COMP_HDR` / `WORKERS_COMP_DTL` | Claims history |
| `alerts` | Fraud / integrity alerts (keyed by provider NPI via `object_id`) |

## Getting Started

### Prerequisites

- AWS account with Bedrock access (Claude Sonnet)
- SageMaker notebook instance (IAM role handles auth — no API keys needed)
- Teradata HCLS database credentials (provided during the workshop)

### Setup

1. Clone this repo into your SageMaker notebook
2. Copy the provided `.env` file into the project root
3. Open `notebooks/01-foundations.ipynb` and start running cells

## Project Structure

```
├── notebooks/
│   ├── 01-foundations.ipynb          # Bedrock + MCP + first agent
│   ├── 02-claire-deep-dive.ipynb     # Skills and routing
│   ├── 03-agentcore-deploy.ipynb     # Container deploy to AgentCore
│   └── 04-production-patterns.ipynb  # Open challenges
├── .env                              # Teradata credentials (not committed)
└── README.md
```

## License

This project is provided for workshop / educational use.