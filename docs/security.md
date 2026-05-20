# Security and Privacy Guidelines

## Product Name

Elite IA Workflow Assistant

## Purpose

This document defines the basic security and privacy rules for the project.

Elite IA Workflow Assistant will work with workflows, forms, client requests, AI services and external tools. Because of this, the project must follow clear rules to avoid exposing sensitive information.

## Main Security Principles

The project must follow these principles:

- Do not upload passwords to GitHub
- Do not upload API keys to GitHub
- Do not upload tokens to GitHub
- Do not use real client data during testing
- Use example data only
- Keep human approval before sending messages
- Limit access permissions for each tool
- Document all external integrations
- Review AI-generated responses before using them
- Avoid storing unnecessary personal information

## Sensitive Information

The following information must never be uploaded to GitHub:

- API keys
- Passwords
- Access tokens
- Private emails
- Client phone numbers
- Real client names
- Payment information
- Personal documents
- Authentication credentials
- Environment files containing secrets

## Environment Variables

Secrets must be stored in environment variables, not inside the public repository.

Examples of secrets:

- OpenAI API key
- Claude API key
- Google API credentials
- Telegram bot token
- n8n credentials
- Database credentials

A file called `.env.example` may be added in the future to show which variables are needed without exposing real values.

Example:

```text
OPENAI_API_KEY=your_api_key_here
TELEGRAM_BOT_TOKEN=your_token_here
GOOGLE_SHEETS_ID=your_sheet_id_here
```

The real `.env` file must not be uploaded to GitHub.

## Test Data

During development, the project will only use fake client data.

Example test client:

```text
Name: John Doe
Email: john.doe@example.com
Phone: +34 600 000 000
Service requested: Workflow automation
Problem description: I want to automate client request tracking.
Urgency: Medium
Budget: 100-300 EUR
```

Fake data helps test the system without exposing private information.

## Human Approval

The system must not send automatic responses to clients without human approval during the first versions.

AI-generated responses must be reviewed before being sent.

This is important because AI can:

- Make mistakes
- Misunderstand client requests
- Suggest incorrect prices
- Generate incomplete answers
- Create legal or business risks

The system should assist the human, not replace the human.

## GitHub Rules

Before every commit, check that the repository does not contain:

- Real credentials
- Real client data
- Private files
- Local configuration files
- Personal notes
- Sensitive screenshots

Recommended files to avoid uploading:

```text
.env
credentials.json
token.json
private_notes.md
client_data_real.xlsx
```

## n8n Security Rules

When using n8n:

- Use limited permissions
- Do not expose credentials publicly
- Avoid sharing workflow screenshots with visible tokens
- Use test accounts when possible
- Review each workflow before activating it
- Keep logs clean from sensitive data

## AI Security Rules

When using AI services:

- Do not send real sensitive client data during testing
- Avoid including unnecessary personal information in prompts
- Review AI responses before using them
- Keep prompts documented
- Do not give AI tools unrestricted access to files or systems

## Future Security Improvements

Future versions may include:

- `.gitignore` configuration
- `.env.example` file
- Basic data retention policy
- Access control documentation
- Safer workflow logs
- Approval workflow before sending emails
- Clear data deletion process
- Local testing environment

## Security Status

Status: In progress
