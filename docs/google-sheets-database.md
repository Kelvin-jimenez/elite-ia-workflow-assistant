# Google Sheets Database

## Product Name

Elite IA Workflow Assistant

## Purpose

This document describes the Google Sheets database used in the MVP.

Google Sheets is used as the first database to store client requests submitted through the form.

## Database Objective

The goal of this database is to keep all client requests organized in one place.

It allows the responsible person to review requests, track their status and prepare future automation with n8n and AI.

## Data Source

The first data source is the client request form.

Each time a client submits the form, a new row is created automatically in Google Sheets.

## Form Columns

These columns are created from the Google Form:

- Timestamp
- Name
- Email
- Phone number
- Service requested
- Problem description
- Urgency level
- Budget range
- Additional notes

## Internal System Columns

These columns are added manually to support the workflow:

- Request ID
- Status
- AI Category
- AI Priority
- AI Summary
- Suggested Response
- Internal Notes

## Column Description

### Timestamp

Automatically created by Google Forms.

It shows when the request was submitted.

### Name

Client name.

### Email

Client email address.

### Phone number

Client phone number.

### Service requested

The type of service requested by the client.

Possible values:

- IT Support
- Workflow Automation
- Data Analysis
- AI Assistance
- Cybersecurity
- Other

### Problem description

The client explanation of the problem or request.

This field is important because the AI will use it to classify and summarize the request.

### Urgency level

The urgency selected by the client.

Possible values:

- Low
- Medium
- High
- Urgent

### Budget range

The approximate budget selected by the client.

Possible values:

- Less than 100 EUR
- 100-300 EUR
- 300-500 EUR
- More than 500 EUR
- Not sure yet

### Additional notes

Extra information provided by the client.

This field is optional.

### Request ID

Internal request identifier.

Example:

```text
REQ-001
REQ-002
REQ-003
