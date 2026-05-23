# n8n Workflow V2 Plan

## Product Name

Elite IA Workflow Assistant

## Purpose

This document describes the planned improvements for the second version of the n8n workflow.

Workflow V1 is already working and published. It detects new client requests, updates the request status and sends a basic internal Gmail notification.

Workflow V2 will improve the internal notification by including the full client request details in the email.

## Current Workflow V1

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
