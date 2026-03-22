# Personal Assistant

This folder contains an n8n workflow called `Agent Lisa`, a Telegram-based personal assistant that turns voice notes into structured logs and simple analytics.

## File Included

- `Agent Lisa (1).json` - n8n workflow for Telegram voice input, Gemini-based intent extraction, Google Sheets logging, and analytics replies

## What This Workflow Does

The workflow listens for Telegram voice messages, downloads the audio, sends it to Gemini, and converts the result into structured JSON.

Based on the detected intent, it can:

- log daily activity into date-based sheets
- add planned tasks
- record expenses
- create reminders
- log calories and food entries
- answer analytics questions from stored data

## Supported Intents

The workflow classifies each voice message into one of these intents:

- `activity_log`
- `task_log`
- `finance_log`
- `reminder_set`
- `reminder_review`
- `calorie_log`
- `analytics_query`

## Data Storage

This assistant writes to Google Sheets using different tabs depending on the intent.

### Sheets used

- `Expense` - stores amount, note, and date
- `Remainder` - stores reminder task, date, time, and status
- `Calories` - stores food item, quantity, calories, and date
- `Tasks` - stores task, time required, and category
- `YYYY-MM-DD` date-based sheets - store activity logs in 15-minute time blocks

## How Activity Logging Works

Activity entries are normalized into strict 15-minute slots.

Examples:

- `06.15 AM - 06.30 AM`
- `11.45 AM - 12.00 PM`

If the user says "past 15 minutes", the workflow uses the last fully completed 15-minute block instead of a sliding time range.

## Task Categories

Task logs are restricted to these categories:

- `Personal`
- `Financial Growth and Stability`
- `Cognizant`
- `InnovateIT Labs`
- `Family and Friends`
- `Others`

## Analytics Mode

The workflow also supports analytics queries. It uses an AI agent plus a Google Sheets tool to read the relevant sheet and return a structured summary.

Supported analytics domains:

- `activity`
- `task`
- `finance`
- `calorie`
- `reminder`

Examples of analytics use cases:

- how much money was spent
- how many calories were consumed
- how the day was spent
- pending task counts
- reminder reviews

## User Experience

The assistant sends Telegram confirmation messages after logging entries and edits the original status message with the final result.

Typical confirmations include:

- expense added successfully
- reminder saved
- calorie entry logged
- analytics summary returned

## Required Credentials

Before using this workflow in n8n, connect:

- Telegram Bot credentials
- Google Sheets credentials
- Google Gemini / PaLM API credentials

## Setup Notes

1. Import `Agent Lisa (1).json` into n8n.
2. Connect the Telegram bot used by the trigger and reply nodes.
3. Connect Google Sheets and point the workflow to your personal tracking spreadsheet.
4. Confirm the required sheet tabs exist:
   - `Expense`
   - `Remainder`
   - `Calories`
   - `Tasks`
   - date-based activity sheets such as `2026-03-22`
5. Test each intent with short Telegram voice notes before activating it for regular use.

## Important Note

This workflow contains account-specific configuration such as Telegram bot references, chat IDs, Google Sheets references, and Gemini credential mappings. If you plan to share it publicly, sanitize those values first.
