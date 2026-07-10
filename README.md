# AI Product Operations Research Agent

An AI-powered research pipeline that evaluates software applications for agent integration readiness.

Built for the Composio AI Product Ops Intern take-home assignment.

---

## Overview

Composio enables AI agents to interact with applications through tools.

Before building a toolkit for an application, several factors need to be researched:

- Authentication methods
- Developer access availability
- API surface
- MCP availability
- Integration complexity
- Potential blockers

Researching hundreds of applications manually does not scale.

This project builds an AI-assisted Product Operations research agent that automates application research and produces structured integration intelligence.

---

# Problem Statement

Given a list of applications, determine:

- What the application does
- Authentication methods supported
- Whether developers can self-serve credentials
- Available APIs and developer interfaces
- Existing MCP support
- Whether the application is ready for agent integration
- Evidence supporting each decision

---

# Solution Architecture

```
Application List (100 Apps)

          ↓

AI Research Agent
(Gemini + Structured Prompt)

          ↓

Official Source Research

Priority:
1. Official Developer Documentation
2. API Documentation
3. Official GitHub Repository
4. MCP Documentation

          ↓

Structured JSON Extraction

          ↓

Validation Pipeline

          ↓

Human Verification Loop

          ↓

Final Dataset + Insights
```

---

# Technology Stack

| Component | Technology |
|---|---|
| AI Model | Gemini |
| Agent Environment | Google AI Studio |
| Data Format | JSON |
| Validation | Schema validation |
| Analysis | AI-assisted pattern analysis |
| Sources | Official docs, APIs, GitHub, MCP repositories |

---

# Research Agent Workflow

## 1. Input

The agent receives application metadata:

```json
{
  "app_name": "Salesforce",
  "category": "CRM and Sales",
  "hint": "salesforce.com"
}
```

---

## 2. Research Process

The agent researches each application using:

### Official Documentation Priority

1. Developer documentation
2. API documentation
3. Official GitHub repositories
4. MCP documentation

Third-party sources are avoided unless official sources are unavailable.

---

## 3. Information Extracted

### Application Information

- Category
- Product description

### Authentication

Normalized into:

- OAuth2
- API Key
- Basic Auth
- Token
- JWT
- Session Cookie
- Other

### Developer Access

Classified as:

- Self-Serve
- Paid
- Admin Approval
- Partnership Required
- Contact Sales

### API Surface

Detected:

- REST
- GraphQL
- SDK
- Webhooks
- CLI
- MCP

### Integration Readiness

Classified as:

| Verdict | Meaning |
|---|---|
| Ready | Can be integrated today |
| Near Ready | Minor blockers exist |
| Blocked | Significant restrictions exist |

---

# Output Schema

Each application is converted into structured integration intelligence.

Example:

```json
{
  "app_name": "Salesforce",
  "category": "CRM and Sales",

  "raw_auth_methods": [
    "OAuth 2.0 with PKCE",
    "JWT Bearer Flow",
    "Session ID"
  ],

  "normalized_auth_methods": [
    "OAuth2",
    "JWT",
    "Token"
  ],

  "self_serve_or_gated": "Self-Serve",

  "api_types": [
    "REST",
    "GraphQL",
    "SDK",
    "Webhooks",
    "MCP"
  ],

  "api_breadth": "Broad",

  "mcp_exists": "Yes",
  "mcp_type": "Official",

  "buildability_verdict": "Ready",

  "blocker": "None",

  "evidence_urls": [
    "official documentation URLs"
  ],

  "confidence_score": 100,

  "human_intervention_required": false,

  "verification_status": "Reviewed",

  "verification_notes": "Manually verified against official documentation."
}

# Validation Pipeline

After generating the dataset, automated checks were performed.

## Automated Validation

Checked:

- Exactly 100 applications exist
- Duplicate application names
- Schema completeness
- Enum consistency
- Missing fields
- Low-confidence records
- Human intervention flags

---

# Human Verification Loop

AI-generated research was validated using official sources.

Workflow:

```
AI Research Output

        ↓

Random Sample Selection

        ↓

Official Documentation Review

        ↓

Corrections Applied

        ↓

Final Dataset
```

---

# Verification Results

## Sample Review

Reviewed:

**11 / 100 applications**

Verified:

- Authentication methods
- MCP availability
- API documentation
- Access model

---

## Findings

| Metric | Result |
|---|---:|
| Applications reviewed | 11 |
| MCP classification issues found | 5 |
| Major corrections applied | 5 |

---

# MCP Corrections Identified

During manual verification:

| Application | Correction |
|---|---|
| Pylon | MCP exists (official) |
| Klaviyo | Official MCP available |
| Meta Ads | Official MCP available |
| Grain | MCP available |
| Mermaid CLI | Official MCP available |

---

# Human Intervention Required

The agent flagged 8 applications requiring deeper investigation:

| Application | Reason |
|---|---|
| DealCloud | Enterprise API provisioning |
| Gladly | Limited public access |
| Waterfall.io | Difficult API verification |
| Paygent Connect | Environment-specific access |
| PitchBook | Commercial API access |
| NotebookLM | Product/API separation |
| Consensus | Application-based access |
| Devin | Restricted availability |

---

# Repository Structure

```
ai-product-ops-research-agent/

│
├── README.md
│
├── data/
│   ├── input_apps.json
│   └── results.json
│
├── prompts/
│   └── research_agent_prompt.md
│
├── schemas/
│   └── output_schema.json
│
├── analysis/
│   └── insights.md
│
└── html/
    └── index.html
```

---

# Running the Project

## Step 1: Prepare Input

Add applications to:

```
data/input_apps.json
```

Example:

```json
[
  {
    "app_name": "Salesforce",
    "category": "CRM and Sales",
    "hint": "salesforce.com"
  }
]
```

---

## Step 2: Run Research Agent

Provide the application list and research prompt to the AI agent.

The output is:

```
results.json
```

containing structured application intelligence.

---

## Step 3: Validate Results

Run validation checks:

- Schema validation
- Duplicate detection
- Missing fields
- Confidence review

---

## Step 4: Human Verification

Verify samples against:

- Official developer documentation
- API references
- MCP repositories

---

# Key Insights

## 1. MCP Availability Is a Strong Readiness Signal

Applications with MCP support generally have clearer paths toward agent integration.

---

## 2. Authentication Standardization Matters

OAuth2 and API Keys cover the majority of integration requirements.

---

## 3. AI Research Requires Verification Loops

Documentation changes frequently, especially MCP availability.

A reliable workflow requires:

```
AI Discovery
      ↓
Validation
      ↓
Human Review
      ↓
Improved Accuracy
```

---

# Future Improvements

Potential improvements:

- Automated browser verification
- MCP registry monitoring
- Documentation freshness tracking
- Multi-agent verification
- Automated confidence recalculation

---

# Deliverables

This repository contains:

- AI research workflow
- Structured application dataset
- Validation approach
- Analysis outputs
- HTML case study
