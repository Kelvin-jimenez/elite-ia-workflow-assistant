# Minimum Viable Product

## Product Name

Elite IA Workflow Assistant

## MVP Objective

The objective of the MVP is to create a simple but useful workflow system that can receive client requests, store them, notify the responsible person and prepare the foundation for AI-based classification and response generation.

The MVP should prove that the core idea is valuable before adding more advanced features such as RAG, dashboards or autonomous agents.

## Main User

The main user of this MVP is a freelancer, small business owner or digital service provider who receives client requests and wants to organize them better.

## Problem to Solve

Many small businesses receive requests through different channels such as WhatsApp, email, marketplaces or social media.

This creates several problems:

- Client information is not centralized
- Requests can be forgotten
- Responses are slow
- Manual work is repeated
- There is no clear follow-up process

## MVP Scope

The first version will include:

- A client request form
- Automatic storage of form responses
- A Google Sheets database
- Basic notification when a new request arrives
- Initial request status tracking
- Documentation in GitHub

## MVP Features

### Feature 1: Client Request Form

The system will include a form where a client can submit a request.

The form should collect:

- Name
- Email
- Phone number
- Type of service requested
- Description of the problem
- Urgency level
- Approximate budget

### Feature 2: Data Storage

Each request will be stored automatically in Google Sheets.

The sheet should include:

- Date
- Name
- Email
- Phone number
- Service requested
- Problem description
- Urgency
- Status
- Notes

### Feature 3: Basic Workflow Automation

A basic n8n workflow will receive the form submission and send the data to Google Sheets.

The first workflow will be:

Client submits form  
↓  
n8n receives data  
↓  
n8n stores data in Google Sheets  
↓  
Responsible person receives a notification  

### Feature 4: Notification

When a new client request arrives, the responsible person should receive a notification.

Possible notification channels:

- Email
- Telegram
- WhatsApp in future versions

### Feature 5: Status Tracking

Each request should have a status.

Initial statuses:

- New
- Reviewed
- Pending response
- Responded
- Budget sent
- Accepted
- Rejected
- Completed

## Out of Scope for MVP

The MVP will not include:

- Automatic email sending without human review
- Advanced RAG
- Autonomous agents
- Payment integration
- Client login
- Dashboard
- CRM system
- Legal contract generation
- Real client data during testing

## Success Criteria

The MVP will be considered successful if:

- A client can submit a request through a form
- The request is stored automatically in Google Sheets
- The responsible person receives a notification
- The information is organized and easy to review
- The project is documented clearly in GitHub

## Future Improvements

After the MVP, future versions may include:

- AI request classification
- AI summary generation
- Suggested client response
- RAG with business documentation
- Dashboard or CRM view
- Telegram integration
- Email draft creation
- Human approval workflow
- Better security and privacy controls

## MVP Status

Status: In progress
