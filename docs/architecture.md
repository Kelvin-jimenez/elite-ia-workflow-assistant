# System Architecture

## Product Name

Elite IA Workflow Assistant

## Architecture Objective

The objective of this document is to describe how the main components of the system will work together.

Elite IA Workflow Assistant will use a simple automation architecture to receive client requests, store information, trigger workflows, use AI services and support human decision-making.

## High-Level Architecture

The system will follow this basic flow:

Client Request Form  
↓  
n8n Workflow  
↓  
Google Sheets Database  
↓  
AI / LLM Processing  
↓  
Notification  
↓  
Human Review  

## Main Components

### 1. Client Request Form

The form is the entry point of the system.

Its purpose is to collect structured information from a potential client.

The form will collect:

- Name
- Email
- Phone number
- Type of service requested
- Problem description
- Urgency level
- Approximate budget

Possible tools:

- Google Forms
- Tally
- Typeform

For the first MVP, Google Forms or Tally will be enough.

---

### 2. n8n Workflow

n8n will be the automation engine of the system.

Its role is to receive the form submission and trigger the next actions.

Initial workflow:

Form submitted  
↓  
n8n receives the data  
↓  
n8n stores the data in Google Sheets  
↓  
n8n sends a notification  

Future workflow:

Form submitted  
↓  
n8n receives the data  
↓  
AI classifies the request  
↓  
AI creates a summary  
↓  
AI suggests a response  
↓  
Data is stored in Google Sheets  
↓  
Notification is sent  
↓  
Human reviews the response  

---

### 3. Google Sheets Database

Google Sheets will be used as the first database for the MVP.

It will store all client requests in a structured way.

Initial columns:

- Date
- Name
- Email
- Phone number
- Service requested
- Problem description
- Urgency
- Status
- Notes

Future columns:

- AI category
- AI priority
- AI summary
- Suggested response
- Assigned owner
- Follow-up date
- Final decision

---

### 4. AI / LLM Processing

The AI layer will help analyze the client request.

The AI will be used to:

- Classify the request
- Detect the type of service needed
- Generate a short summary
- Suggest a first response
- Support decision-making

Possible AI providers:

- OpenAI
- Claude
- Gemini
- Local LLMs in future versions

For the first AI version, the system will not send messages automatically. It will only generate suggestions for human review.

---

### 5. Notification System

The notification system will alert the responsible person when a new client request arrives.

Possible notification channels:

- Email
- Telegram
- WhatsApp in future versions

For the MVP, email notification is enough.

Telegram can be added later as an improvement.

---

### 6. Human Review

Human review is required before sending any response to the client.

This is important to:

- Avoid incorrect answers
- Protect client communication
- Review prices and conditions
- Keep control over the business process
- Reduce risks caused by AI mistakes

The system will assist the human, not replace the human.

---

## MVP Architecture

The first MVP architecture will be:

Client fills form  
↓  
Form sends data to n8n  
↓  
n8n stores data in Google Sheets  
↓  
n8n sends email notification  
↓  
Human reviews the request  

## MVP Architecture Diagram

```text
[Client]
   |
   v
[Google Form / Tally Form]
   |
   v
[n8n Workflow]
   |
   v
[Google Sheets]
   |
   v
[Email Notification]
   |
   v
[Human Review]
```

## Future AI Architecture

```text
[Client]
   |
   v
[Form]
   |
   v
[n8n Workflow]
   |
   v
[AI / LLM]
   |
   |-- Classify request
   |-- Generate summary
   |-- Suggest response
   |
   v
[Google Sheets]
   |
   v
[Notification]
   |
   v
[Human Review]
```

## Future RAG Architecture

In future versions, the system may use RAG.

RAG means Retrieval Augmented Generation.

This means the AI will be able to answer using business documents such as:

- Service descriptions
- Prices
- FAQs
- Conditions
- Internal procedures
- Response templates

Future RAG flow:

Client request  
↓  
n8n receives request  
↓  
AI searches business documentation  
↓  
AI generates a grounded response  
↓  
Human reviews before sending  

## Security Principles

The system must follow basic security rules:

- Do not upload API keys to GitHub
- Do not use real client data during testing
- Use example data only
- Keep human approval before sending messages
- Limit permissions for each tool
- Document all sensitive integrations
- Store secrets in environment variables

## Out of Scope for the First Version

The first version will not include:

- Autonomous agents with system access
- Automatic email sending without review
- Payment processing
- Client login
- Advanced CRM
- Full RAG implementation
- Local LLM deployment
- Production database

## Architecture Status

Status: In progress
