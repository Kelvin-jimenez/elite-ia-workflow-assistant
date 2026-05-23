# n8n Workflow V3 AI Classification Plan

## Product Name

Elite IA Workflow Assistant

## Purpose

This document describes the planned third version of the n8n workflow for the Elite IA Workflow Assistant MVP.

Workflow V1 created the first working automation.

Workflow V2 improved the internal Gmail notification by including full client request details.

Workflow V3 will introduce AI classification to analyze each client request and prepare structured information for human review.

## Current Workflow V2

The current workflow does the following:

```text
Google Sheets Trigger
        |
        v
IF condition
        |
        v
Update row in Google Sheets
        |
        v
Send Gmail notification
```

## Workflow V2 Status

Workflow V2 is working.

Current behavior:

- New form responses are saved in Google Sheets
- n8n detects new or updated rows
- The IF condition prevents repeated processing
- The workflow updates Request ID, Status and Internal Notes
- Gmail sends an internal notification with full request details

## Workflow V3 Objective

The objective of Workflow V3 is to use AI to analyze each client request.

The AI should generate:

- AI Category
- AI Priority
- AI Summary
- Suggested Response

These results will be stored in Google Sheets and included in the internal Gmail notification.

## AI Fields

Workflow V3 will use the following Google Sheets fields:

- AI Category
- AI Priority
- AI Summary
- Suggested Response

## Input Fields for AI

The AI will analyze the following client request fields:

- Name
- Email
- Phone number
- Service requested
- Problem description
- Urgency level
- Budget range
- Additional notes

## Expected AI Output

The AI should return structured information like this:

```text
AI Category: Technical Support
AI Priority: High
AI Summary: The client needs urgent help with a computer problem that is affecting their ability to work.
Suggested Response: Hello, thank you for contacting us. We have received your request and will review the issue before suggesting the best solution.
```

## Planned Workflow V3 Structure

The planned Workflow V3 structure is:

```text
Google Sheets Trigger
        |
        v
IF condition
        |
        v
AI classification
        |
        v
Update row in Google Sheets
        |
        v
Send Gmail notification with AI results
```

## AI Classification Rules

The AI should classify requests using simple and practical business logic.

Possible AI categories:

- Technical Support
- Automation
- Data Analysis
- AI / Machine Learning
- Cybersecurity
- General Inquiry
- Other

Possible AI priority levels:

- Low
- Medium
- High
- Urgent

Priority criteria:

- Urgent: The client mentions immediate impact, business interruption, data loss, security risk or urgent deadlines.
- High: The problem is important and should be handled soon.
- Medium: The request is relevant but not critical.
- Low: The request is general, exploratory or not time-sensitive.

## Suggested Response Rules

The suggested response should:

- Be professional
- Be clear and simple
- Confirm that the request was received
- Avoid promising a final solution without human review
- Avoid giving technical instructions that have not been validated
- Keep the message suitable for manual review before sending

## Human Approval Rule

Workflow V3 will not send automatic responses to clients.

The AI will only generate a suggested response.

A human must review and approve the response before contacting the client.

## Security and Privacy Rules

The workflow should follow these rules:

- Do not expose private client data publicly
- Do not publish real client information on GitHub
- Do not send automatic client responses without review
- Do not store API keys or credentials in the repository
- Keep sensitive data inside Google Sheets, n8n and authorized tools only

## Success Criteria

Workflow V3 will be considered successful if:

- A new form response triggers the workflow
- n8n processes only rows where Request ID is empty
- AI generates category, priority, summary and suggested response
- Google Sheets is updated with the AI results
- Gmail sends an internal notification that includes both client details and AI analysis
- Already processed rows are not notified again
- No automatic email is sent to the client

## Future Improvements After V3

After Workflow V3, future versions may include:

- Human approval workflow
- Draft email generation in Gmail
- Telegram or WhatsApp internal notification
- Dashboard or CRM view
- RAG using business documentation
- Better error handling
- Multi-language response generation
- Lead scoring
- Client follow-up tracking

## Workflow Version

Version: V3 Plan  
Status: Planned
