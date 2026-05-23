# Elite IA Workflow Assistant

Elite IA Workflow Assistant is a project focused on automating client request management using AI, workflows and business process automation.

## Objective

The goal is to build a system that can receive client requests, classify them with AI, store the information and generate an initial response proposal.

## Problem

Many small businesses manage client requests manually through WhatsApp, email, marketplaces and spreadsheets. This creates disorder, delays and repetitive work.

This project aims to reduce that manual work by creating a simple AI-powered workflow system.

## MVP

The first version will:

- Receive client requests through a form
- Store the information in Google Sheets
- Notify the responsible person
- Classify the request using AI
- Generate a suggested response
- Keep human approval before sending anything

## Tech Stack

- n8n
- Google Forms or Tally
- Google Sheets
- AI / LLM APIs
- GitHub
- Markdown

## Project Status

In progress.

## Repository Structure

```text
elite-ia-workflow-assistant/
│
├── docs/
│   ├── product-vision.md
│   ├── backlog.md
│   ├── mvp.md
│   ├── architecture.md
│   ├── security.md
│   ├── how-it-works.md
│   ├── google-sheets-database.md
│   ├── n8n-integration-plan.md
│   ├── n8n-workflow-v1.md
│   ├── n8n-workflow-v2-plan.md
│   └── linkedin-post-draft.md
│
├── examples/
│   └── sample-client-request.json
│
├── prompts/
│   └── service-classifier-prompt.md
│
├── workflows/
│   └── basic-client-request-workflow.md
│
├── .gitignore
└── README.md
```

## Current Progress

- Product vision documented
- Initial product backlog created
- MVP scope defined
- System architecture documented
- Security and privacy guidelines created
- Fake client request example added
- Initial AI service classifier prompt created
- Basic client request workflow documented
- How it works documentation added
- LinkedIn post draft created
- Git ignore file added for security
- Google Sheets database documented
- n8n integration plan documented
- First n8n workflow V1 documented
- n8n workflow V2 improvement plan documented

## Roadmap

### Phase 1: Product Definition

- Define product vision
- Define MVP
- Create product backlog
- Create GitHub documentation

### Phase 2: Basic Automation

- Create client request form
- Connect form with Google Sheets
- Create first n8n workflow
- Send internal notification

### Phase 3: AI Integration

- Classify requests with AI
- Generate request summary
- Suggest client response

### Phase 4: Advanced Features

- Add RAG with business documentation
- Create better response templates
- Add dashboard or CRM view
- Improve security and privacy controls
