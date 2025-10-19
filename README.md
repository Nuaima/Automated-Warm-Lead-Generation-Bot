## Overview

This project is an **AI-powered bot** that monitors public online platforms (Twitter/X) for posts where someone is looking to hire for tech services such as web/app development, UI/UX, or automation. It automatically qualifies “warm leads” using Google Gemini AI and saves them to a Google Sheet.

This project was created as part of the **SOFINDEX AI Automation Engineer Skills Assessment (Project 1 — Mandatory).**

---

## Features

* Monitors Twitter/X for posts containing queries like:

  ```
  looking for developer OR hiring developer OR need web developer
  ```
* Uses **Google Gemini AI** (`models/gemini-2.0-flash`) to classify posts as warm leads.
* Filters out posts offering services, asking for school help, or general discussion.
* Stores qualified leads in a **Google Sheet** with columns:

  ```
  Timestamp | Lead Text | Source | URL | AI Summary | Confidence Score
  ```
* Prints real-time classification results to console for demo purposes.

---

## Tech Stack

* Python 3.12+
* `requests` (Twitter/X API)
* `google-generativeai` (Gemini AI)
* `gspread` & `google-auth` (Google Sheets)
* `datetime` (timestamping)

---

## Setup Instructions

### 1. Twitter API

* Obtain a **Twitter/X Bearer Token** from [developer.twitter.com](https://developer.twitter.com/).
* Replace the placeholder in `BEARER_TOKEN` in the script.

### 2. Google Gemini AI

* Obtain a **Google Generative AI API Key**.
* Replace the placeholder in `GENAI_API_KEY` in the script.

### 3. Google Sheets API

1. Create a Google Cloud project.
2. Enable **Google Sheets API** and **Google Drive API**.
3. Create a service account, download `credentials.json`, and share your Google Sheet with the service account email (Editor access).

### 4. Install Dependencies

```bash
pip install praw openai gspread google-auth oauth2client
pip install --upgrade google-generativeai
pip install requests
```

### 5. Google Sheet Setup

* Create a sheet named **"Warm Leads"**.
* Columns (in order):

  ```
  Timestamp | Lead Text | Source | URL | AI Summary | Confidence Score
  ```

---

## Usage

1. Place `credentials.json` in the same folder as the script.
2. Run:

```bash
python lead_gen_bot.py
```

3. Monitor console output for detected leads.
4. Qualified leads are automatically saved in the Google Sheet.

---

## Sample Output

```
✅ Lead Detected: Dibutuhkan Flutter Developer
Summary: Seeking a Flutter developer, indicating a hiring need.
Confidence: 9
Timestamp: 2025-10-19 13:21:54
```

---

## Notes

* Only posts classified as **warm leads** are stored.
* Maximum 10 recent tweets are fetched per run; adjustable in the script.
* Designed for demonstration and skills assessment purposes.

---


