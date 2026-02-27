# Skill Setup Implementation Plan

**Goal:** Enable all `.agent/skills` by installing dependencies and configuring necessary credentials.

## Summary of Findings

The current workspace is missing several critical components required for the skills in `.agent/skills` to function correctly:

- **Missing Python Packages**: `gspread`, `google-auth-oauthlib`, `python-dotenv`, `anthropic`, `apify`, `pandas`, `fpdf2`, `beautifulsoup4`, `duckduckgo-search`, etc.
- **Missing Credentials**:
  - `credentials.json` (Google OAuth Client ID) for Gmail and Google Sheets skills.
  - `APIFY_API_TOKEN` for lead scraping.
  - `ANYMAILFINDER_API_KEY` for email enrichment.
  - `UNSPLASH_ACCESS_KEY` for website design mockups (optional).
- **Unpopulated Resources**: Brand identity files in `.agent/skills/enforcing-brand-identity/resources/` need to be filled.

## Proposed Changes

### [Environment Setup]

#### [MODIFY] .env
Create a `.env` file in the workspace root with placeholders for all required keys.

```bash
# Apify (for lead scraping)
APIFY_API_TOKEN=your_apify_token_here

# Anthropic (may be provided by environment, but required by scripts)
ANTHROPIC_API_KEY=your_anthropic_key_here

# AnyMailFinder (for email enrichment)
ANYMAILFINDER_API_KEY=your_anymailfinder_key_here

# Unsplash (optional, for design-website skill)
UNSPLASH_ACCESS_KEY=your_unsplash_key_here

# Google Credentials Path
GOOGLE_APPLICATION_CREDENTIALS=credentials.json
```

### [Dependency Installation]

#### [RUN] Dependency install command
I will install all required Python packages using `pip`.

```bash
pip install gspread google-auth-oauthlib python-dotenv anthropic apify gspread-formatting requests pandas fpdf2 beautifulsoup4 duckduckgo-search google-auth-httplib2 google-api-python-client google-auth-oauthlib
```

### [Google OAuth Setup]

> [!IMPORTANT]
> You need to provide a `credentials.json` file in the workspace root (`c:\Users\topaa\Documents\code_projects`).
> 1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
> 2. Create a project and enable the **Gmail API**, **Google Sheets API**, and **Google Drive API**.
> 3. Go to **APIs & Services > Credentials**.
> 4. Create an **OAuth 2.0 Client ID** (Desktop app).
> 5. Download the JSON and save it as `credentials.json` in the root folder.

## Verification Plan

### Automated Tests
- Run a simple import test for all libraries:
  `python -c "import gspread, apify, anthropic, dotenv, pandas, bs4, fpdf2, duckduckgo_search; print('Dependencies OK')"`
- Run `python .agent/skills/generate-report/scripts/fetch_weather.py --output .tmp/test.json` (requires No API key) to verify basic script execution.

### Manual Verification
- After you provide `credentials.json`, I will run the authentication script for one of the Gmail tools to ensure OAuth flow works.
- Verify that a test lead scrape works (requires `APIFY_API_TOKEN`).
