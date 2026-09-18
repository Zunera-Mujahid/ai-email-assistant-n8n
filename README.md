# AI Email Assistant (n8n + Google Gemini)

An automated email assistant built with n8n that reads incoming Gmail messages, classifies them by intent, and generates a tailored draft reply using Google's Gemini API — so replies are ready to review and send instead of being written from scratch.

## Overview

This workflow demonstrates a practical, no-code AI automation pipeline: connecting Gmail, an LLM classification step, and generative reply logic into a single automated system.

## How It Works

1. **Gmail Trigger** — listens for new incoming emails
2. **AI Text Classifier** — categorizes each email into one of four intent categories using an LLM classification node
3. **Contextual Reply Generation** — a Gemini-powered model reads the email and writes a reply tailored to that category's tone and purpose
4. **Structured Output Parsing** — the AI's JSON response (subject + body) is parsed into clean, usable fields
5. **Draft Creation** — the reply is saved as a Gmail draft, not sent automatically, so it can always be reviewed first

## Email Categories

| Category | Description | Reply Behavior |
|---|---|---|
| `action_required` | Needs a response, decision, confirmation, or contains a request/meeting/task | Acknowledges the request and states the next step |
| `question` | Sender is asking something and expects an answer | Answers directly, or asks for clarification if info is missing |
| `urgent` | Time-sensitive or marked as an emergency/ASAP | Opens by acknowledging urgency, reassures a quick response |
| `informational` | A notification, update, receipt, or announcement | Sends a short acknowledgment only, if appropriate |

## Tech Stack

- **n8n** — workflow automation and orchestration
- **Google Gemini API** (`gemini-3.6-flash-lite`) — email classification and reply generation
- **Gmail API** — trigger and draft creation

## Setup

To use this workflow yourself:

1. Import the `.json` file into your own n8n instance
2. Connect your own Gmail account (OAuth2) to the Gmail Trigger and Draft nodes
3. Generate a free Google Gemini API key at [Google AI Studio](https://aistudio.google.com/apikey) and connect it as a credential
4. Adjust the category descriptions or reply prompts as needed for your use case

No credentials or API keys are included in this repository — all connections must be configured with your own accounts.

## Notes

- This is a portfolio/demo project. The workflow is kept **inactive** in n8n and was only run manually for testing — it is not connected live to a personal inbox.
  
## Demo

[Watch the demo video](https://youtu.be/0a0Z5_Z4FCk?si=6cQ8wCtZ2xfQRRrH)

