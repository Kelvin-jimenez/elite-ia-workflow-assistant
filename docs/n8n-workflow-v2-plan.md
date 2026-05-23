# n8n Workflow V2 Plan

## Product Name

Elite IA Workflow Assistant

## Purpose

This document describes the second version of the n8n workflow for the Elite IA Workflow Assistant MVP.

Workflow V1 was already working and published. It detected new client requests, updated the request status and sent a basic internal Gmail notification.

Workflow V2 improves the internal notification by including the full client request details in the email.

## Current Workflow V1

The previous workflow did the following:

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

## Workflow V1 Limitation

The first Gmail notification included only:

- Request ID
- Status
- Email
- Internal Notes

This was useful, but incomplete.

The responsible person still needed to open Google Sheets to view the full client request.

## Workflow V2 Objective

The objective of Workflow V2 is to send a more complete internal email notification.

The improved email includes:

- Request ID
- Status
- Name
- Email
- Phone number
- Service requested
- Problem description
- Urgency level
- Budget range
- Additional notes
- Internal Notes

## Workflow V2 Structure

The current Workflow V2 structure is:

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

## Improved Gmail Notification

Workflow V2 sends an internal Gmail notification with full client request details.

The email includes:

```text
New client request received

Request ID: REQ-...
Status: New

Client details:
Name: ...
Email: ...
Phone number: ...

Request details:
Service requested: ...
Urgency level: ...
Budget range: ...

Problem description:
...

Additional notes:
...

Internal Notes:
Automatically processed by n8n.

Please review the Google Sheets database before contacting the client.
```

## Google Sheets Fields Used

The workflow uses the following Google Sheets fields:

- Name
- Email
- Phone number
- Service requested
- Problem description
- Urgency level
- Budget range
- Additional notes
- Request ID
- Status
- Internal Notes

## Important Rule

Column names must match exactly between Google Sheets and n8n.

System columns should remain in English:

- Request ID
- Status
- AI Category
- AI Priority
- AI Summary
- Suggested Response
- Internal Notes

This prevents errors caused by translated or mismatched column names.

## Human Approval Rule

Workflow V2 does not send automatic responses to clients.

The email is only an internal notification.

All client communication must be reviewed by a human before sending.

## Success Criteria

Workflow V2 is considered successful because:

- A new form response triggers the workflow
- n8n updates Request ID, Status and Internal Notes
- Gmail sends one internal email notification
- The email includes full client request details
- Already processed rows are not notified again

## Production Status

Workflow V2 has been tested successfully.

The improved Gmail notification now includes full client request details.

Production behavior:

- The workflow listens for new or updated rows in Google Sheets
- New requests are processed only if Request ID is empty
- Processed requests receive a Request ID, Status and Internal Notes
- One internal Gmail notification is sent per new request
- The internal email includes the main client and request details

Status: Working

## Future Improvements After V2

After Workflow V2, future versions may include:

- AI category classification
- AI priority detection
- AI summary generation
- Suggested response generation
- Better error handling
- Telegram notification
- Dashboard or CRM view

## Workflow Version

Version: V2  
Status: Working
