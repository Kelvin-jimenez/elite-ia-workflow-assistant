# n8n Workflow V1

## Product Name

Elite IA Workflow Assistant

## Purpose

This document describes the first working n8n workflow for the Elite IA Workflow Assistant MVP.

The workflow automates the first operational process:

Client form submission  
↓  
Google Sheets registration  
↓  
n8n processing  
↓  
Request status update  
↓  
Internal email notification  

## Workflow Objective

The objective of this workflow is to detect new client requests, mark them as processed and notify the responsible person by email.

This workflow does not send any automatic response to the client.

Human review is required before contacting the client.

## Workflow Status

Status: Working MVP version

## Workflow Tools

This workflow uses:

- Google Forms
- Google Sheets
- n8n
- Gmail

## Workflow Structure

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
