# Reddit Scrapping and Lead Scoring

This folder contains a two-step n8n automation for finding potential leads on Reddit and scoring them for outreach.

## Files Included

- `Reddit Scrapping.json` - searches Reddit for buying-intent keywords and appends matching posts to Google Sheets
- `Lead Scoring for reddit.json` - reads the scraped rows, classifies them with Gemini, extracts contact details, and updates the sheet

## How It Works

### 1. Reddit Scrapping

This workflow:

- runs on a schedule
- searches Reddit with a predefined keyword list
- formats the post content
- stores each result in Google Sheets

The scraped rows include these fields:

- `Time Scrapped`
- `Post URL`
- `Post Data`
- `Label`
- `Phone`
- `Email`

The keyword list is focused on people looking for developers, app builders, website help, and marketing support.

### 2. Lead Scoring for reddit

This workflow:

- runs repeatedly on a schedule
- reads rows from the sheet for the current date
- limits processing to 50 rows per run
- sends post text to Gemini for classification
- updates the same sheet with:
  - `Label`
  - `Phone`
  - `Email`

The scoring logic classifies posts into:

- `requirement`
- `in_house_hiring`
- `offering`
- `irrelevant`

## Required Credentials

Before using these workflows in n8n, connect:

- Reddit OAuth2 credentials
- Google Sheets credentials
- Google Gemini / PaLM API credentials

## Setup Notes

1. Import both JSON workflows into n8n.
2. Review the schedule triggers and adjust them for your timezone.
3. Update the keyword list inside `Reddit Scrapping.json` if you want to target different lead types.
4. Confirm the Google Sheet structure contains the columns listed above.
5. Make sure both workflows point to the same spreadsheet if you want scoring to update the scraped results.

## Important Caveat

The current JSON files reference different spreadsheet IDs in different places. Before activating the workflows, verify that:

- the scraping workflow appends to the intended sheet
- the scoring workflow reads from and updates that same sheet

If those IDs do not match, the second workflow will not score the rows created by the first one.

Placeholder IDs currently used in the shared version:

- `1AbCDeFgHiJkLmNoPqRsTuVwXyZ1234567890Fake`
- `1ZyXwVuTsRqPoNmLkJiHgFeDcBa0987654321Demo`
