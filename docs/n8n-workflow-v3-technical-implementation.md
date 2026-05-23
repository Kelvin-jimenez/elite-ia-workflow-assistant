# n8n Workflow V3 Technical Implementation

## Product Name

Elite IA Workflow Assistant

## Purpose

This document describes the technical implementation of Workflow V3 for the Elite IA Workflow Assistant MVP.

Workflow V3 adds AI classification to the automation system.

The workflow receives a client request from Google Forms, stores it in Google Sheets, processes it with n8n, uses AI to analyze the request, updates the Google Sheets database and sends an internal Gmail notification with both client details and AI analysis.

## Workflow Version

Version: V3  
Status: Working in production

## Workflow Objective

The objective of Workflow V3 is to automate the first analysis of a new client request.

The workflow must:

- Detect new client requests
- Prevent duplicated processing
- Generate a Request ID
- Set the request status
- Analyze the request with AI
- Store AI results in Google Sheets
- Send an internal Gmail notification
- Keep human approval before contacting the client

## Workflow Structure

```text
Google Sheets Trigger
        |
        v
IF condition
        |
        v
Message a model
        |
        v
Code in JavaScript
        |
        v
Update row in Google Sheets
        |
        v
Send Gmail notification
```

## Tools Used

Workflow V3 uses the following tools:

- Google Forms
- Google Sheets
- n8n
- OpenAI
- JavaScript Code node
- Gmail
- GitHub

## Data Source

The workflow starts when a new form response is added to Google Sheets.

The Google Form collects the following client information:

- Name
- Email
- Phone number
- Service requested
- Problem description
- Urgency level
- Budget range
- Additional notes

## Google Sheets Database Fields

The Google Sheets database contains both client fields and internal workflow fields.

Client request fields:

- Marca temporal
- Name
- Email
- Phone number
- Service requested
- Problem description
- Urgency level
- Budget range
- Additional notes

Internal workflow fields:

- Request ID
- Status
- AI Category
- AI Priority
- AI Summary
- Suggested Response
- Internal Notes

## Node 1: Google Sheets Trigger

The first node is:

```text
Google Sheets Trigger
```

Purpose:

This node listens for new or updated rows in the Google Sheets database.

Trigger behavior:

- Detects new form responses
- Sends row data to the next node
- Provides all client request fields to the workflow

Main data used from this node:

- Name
- Email
- Phone number
- Service requested
- Problem description
- Urgency level
- Budget range
- Additional notes
- Request ID

## Node 2: IF Condition

The second node is:

```text
IF condition
```

Purpose:

This node prevents duplicated processing.

Condition:

```text
Request ID is empty
```

Logic:

```text
If Request ID is empty:
    Continue workflow

If Request ID already exists:
    Stop workflow
```

Why this is important:

Without this condition, updated rows could trigger the workflow again and send duplicated emails.

## Node 3: Message a Model

The third node is:

```text
Message a model
```

Purpose:

This node sends the client request information to OpenAI for analysis.

The AI receives the following input fields:

- Name
- Email
- Phone number
- Service requested
- Problem description
- Urgency level
- Budget range
- Additional notes

The AI must return structured JSON with:

- ai_category
- ai_priority
- ai_summary
- suggested_response

Expected JSON output:

```json
{
  "ai_category": "Data Analysis",
  "ai_priority": "High",
  "ai_summary": "The client is requesting help with data analysis and needs support soon.",
  "suggested_response": "Hello, thank you for contacting us. We have received your request and will review the details before suggesting the best solution."
}
```

Important rule:

The AI must return only valid JSON.

No markdown, no comments and no extra text should be included outside the JSON.

## Node 4: Code in JavaScript

The fourth node is:

```text
Code in JavaScript
```

Purpose:

This node converts the AI text response into structured fields that n8n can use in the next nodes.

The AI returns JSON as text.

The Code node parses that text and creates usable fields.

JavaScript code used:

```javascript
const aiText = $json.output[0].content[0].text;

const aiData = JSON.parse(aiText);

const originalData = $("Google Sheets Trigger").item.json;

return [
  {
    json: {
      ...originalData,
      ai_category: aiData.ai_category,
      ai_priority: aiData.ai_priority,
      ai_summary: aiData.ai_summary,
      suggested_response: aiData.suggested_response
    }
  }
];
```

What this code does:

- Reads the AI response text
- Converts the text into JSON
- Keeps the original Google Sheets Trigger data
- Adds the AI results as structured fields
- Sends all data to the next node

Output fields created:

- ai_category
- ai_priority
- ai_summary
- suggested_response

## Node 5: Update Row in Google Sheets

The fifth node is:

```text
Update row in Google Sheets
```

Purpose:

This node updates the original Google Sheets row with internal workflow data and AI results.

The workflow updates:

- Request ID
- Status
- AI Category
- AI Priority
- AI Summary
- Suggested Response
- Internal Notes

Field mapping:

```text
Request ID:
REQ-{{ $now.toFormat("yyyyLLddHHmmss") }}-{{ $itemIndex + 1 }}

Status:
New

Internal Notes:
Automatically processed by n8n.

AI Category:
{{ $json["ai_category"] }}

AI Priority:
{{ $json["ai_priority"] }}

AI Summary:
{{ $json["ai_summary"] }}

Suggested Response:
{{ $json["suggested_response"] }}
```

Match column:

```text
Email
```

The Email field is used to identify the row that must be updated.

## Node 6: Send Gmail Notification

The final node is:

```text
Send Gmail notification
```

Purpose:

This node sends an internal email notification to the responsible person.

The email includes:

- Request ID
- Status
- Client details
- Request details
- Problem description
- Additional notes
- AI Category
- AI Priority
- AI Summary
- Suggested Response
- Internal Notes

The email is internal only.

No automatic email is sent to the client.

## Gmail Notification Structure

The internal Gmail notification includes:

```text
New client request received

Request ID
Status

Client details:
Name
Email
Phone number

Request details:
Service requested
Urgency level
Budget range

Problem description

Additional notes

AI Analysis:
AI Category
AI Priority
AI Summary
Suggested Response

Internal Notes

Please review the Google Sheets database before contacting the client.
```

## Human Approval Rule

Workflow V3 does not contact clients automatically.

The AI only generates a suggested response.

A human must review the request and approve the response before contacting the client.

This rule is important because:

- AI can make mistakes
- Client communication must be reviewed
- Technical advice should be validated
- Business decisions should remain under human control

## Security Rules

Workflow V3 follows these security rules:

- Do not publish real client data on GitHub
- Do not expose API keys or credentials
- Do not send automatic responses to clients
- Keep sensitive data inside Google Sheets, n8n and authorized tools
- Use fake data for public screenshots or portfolio examples
- Review AI-generated responses before sending them

## Production Behavior

Workflow V3 has been tested successfully in production.

Current production behavior:

- New form responses are detected by n8n
- Only rows without Request ID are processed
- OpenAI analyzes the request
- JavaScript parses the AI JSON response
- Google Sheets is updated with AI fields
- Gmail sends an internal notification with AI analysis
- Already processed rows are ignored
- No automatic client response is sent

## Success Criteria

Workflow V3 is considered successful because:

- The workflow runs from a real Google Form submission
- The correct Google Sheets row is updated
- Request ID is generated
- Status is set to New
- Internal Notes are added
- AI Category is generated
- AI Priority is generated
- AI Summary is generated
- Suggested Response is generated
- Gmail notification includes full client details
- Gmail notification includes AI analysis
- Human approval is preserved

## Known Limitations

Current limitations:

- The workflow uses Email as the matching column
- The AI response depends on prompt quality
- The suggested response still requires human review
- Error handling is basic
- There is no dashboard yet
- There is no client approval interface yet
- There is no automatic draft creation in Gmail yet

## Future Improvements

Future improvements may include:

- Use row ID or row number instead of Email as match field
- Add error handling for invalid AI JSON
- Add Gmail draft generation
- Add human approval workflow
- Add Telegram notification
- Add dashboard or CRM view
- Add RAG with business documentation
- Add multi-language response support
- Add lead scoring
- Add follow-up tracking

## Final Status

Workflow V3 is working in production.

The system can now receive a client request, analyze it with AI, update the database and notify the responsible person with a complete internal email.

Status: Working
