# n8n Integration Plan

## Product Name

Elite IA Workflow Assistant

## Purpose

This document defines the integration plan for n8n in the MVP.

n8n will be used as the automation engine that connects the client request form, Google Sheets, notifications and future AI processing.

## Integration Objective

The objective of the n8n integration is to automate the first operational workflow:

Client submits a form  
↓  
n8n detects the new request  
↓  
n8n processes the data  
↓  
n8n updates Google Sheets  
↓  
n8n sends an internal notification  

## Current System Status

The project currently has:

- Google Form created
- Google Sheets connected to form responses
- Internal workflow columns added
- Sample client request tested
- GitHub documentation created

## Main Tools

The integration will use:

- Google Forms
- Google Sheets
- n8n
- Email notification
- AI / LLM API in future versions

## Google Sheets Input Columns

These columns come from the form:

- Timestamp
- Name
- Email
- Phone number
- Service requested
- Problem description
- Urgency level
- Budget range
- Additional notes

## Google Sheets Internal Columns

These columns will support automation:

- Request ID
- Status
- AI Category
- AI Priority
- AI Summary
- Suggested Response
- Internal Notes

## MVP Workflow

The first n8n workflow will focus on basic automation.

### Step 1: Detect new form response

n8n should detect when a new row is added to Google Sheets.

Trigger:

```text
New row in Google Sheets
