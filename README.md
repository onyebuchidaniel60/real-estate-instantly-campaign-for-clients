# Real Estate Instantly Campaign Automation

This n8n workflow automates the transition from lead discovery to active outreach. It is designed to pull raw lead data from Google Sheets, validate contact information, and sync it with Instantly.ai for automated cold email campaigns.

## 🚀 Features

- **Scheduled Execution:** Uses a **Schedule Trigger** to automatically process new leads at set intervals.
- **Google Sheets Integration:** - Pulls raw lead data from the "real estate client outreach with gmail" sheet.
    - Logs processed lead data to a separate "kornel cold outreach campaign" sheet for tracking.
- **Email Verification:** Integrates with the **verify-email.app API** to ensure leads have valid email addresses before sending, protecting your sender reputation.
- **Intelligent Name Parsing:** Features a **Custom JavaScript node** that automatically extracts First and Last names from social media titles or handles while filtering out invalid formats (like those starting with numbers).
- **Automated Outreach:** Directly syncs verified leads into **Instantly.ai** ("Kornel's Campaign").
- **Safe Rate Limiting:** Includes multiple **Wait nodes** and batching (15 leads per batch) to prevent API rate limits and ensure smooth execution.

## 🛠️ Prerequisites

To use this workflow, you will need:
- An **n8n** instance.
- **Google Sheets OAuth2** credentials.
- **Verify-Email.app API Key**.
- **Instantly.ai API Key**.

## ⚙️ How It Works

1.  **Lead Retrieval:** The workflow triggers on a schedule and pulls lead rows from a designated Google Sheet.
2.  **Verification:** Each email is sent to an external verification service. Only leads marked as "valid" proceed.
3.  **Data Cleaning:** A JavaScript snippet cleans the profile titles to extract usable names for personalization.
4.  **Syncing:** Verified and cleaned leads are added to the Instantly.ai campaign and logged in a "clean" Google Sheet for the client.
5.  **Looping:** The workflow loops through batches of 15-30 leads with built-in delays to maintain stability.

## 📦 Installation

1. Download the `real estate instantly campaign for client.json` file.
2. Open your n8n dashboard and click on **Import from File**.
3. Configure the following credentials:
   - **Google Sheets OAuth2 API** (update the Document ID to your specific sheet).
   - **HTTP Request** (add your `X-API-Key` for email verification).
   - **Instantly API**.
4. Set the **Schedule Trigger** to your preferred frequency.
