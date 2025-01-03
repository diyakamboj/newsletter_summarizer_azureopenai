# Newsltter Summarizer 📧🧠  
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Gmail API](https://img.shields.io/badge/Gmail%20API-Enabled-green)
![OpenAI](https://img.shields.io/badge/OpenAI-API-orange)
![Google Cloud](https://img.shields.io/badge/Google%20Cloud-Configured-yellow)

## Overview

**Newsltter Summarizer** is an AI-powered tool that automates the process of reading, understanding, and summarizing newsletters. With the increasing flood of emails, it can be challenging to stay updated without wasting hours scanning through content. This tool solves the problem by:

- Fetching unread emails from predefined newsletter senders.
- Using OpenAI's GPT-4 model to generate concise and meaningful summaries.
- Sending these summaries to your inbox or other preferred channels.

With **Newsltter Summarizer**, you can:
- Save time and improve productivity.
- Stay updated without feeling overwhelmed.
- Access summaries from multiple newsletters in one concise email.

## Setup Guide

### Prerequisites
- Python 3.8+
- Gmail account
- OpenAI account
- Google Cloud account

### Step 1: Clone Repository
```bash
git clone https://github.com/diyakamboj/newsletter_summarizer_azureopenai.git
cd newsletter_summarizer_azureopenai
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### Step 2: Google Cloud Setup
1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Create new project
   - Click top bar dropdown → "New Project"
   - Name: "Newsletter Summarizer"
   - Click "Create"

3. Enable Gmail API
   - Search "Gmail API" in top search bar
   - Click "Enable API"

4. Create OAuth Credentials
   - Go to "APIs & Services" → "Credentials"
   - Click "Create Credentials" → "OAuth client ID"
   - Configure consent screen:
     - User Type: External
     - App name: "Newsletter Summarizer"
     - User support email: Your email
     - Developer contact: Your email
   - Add test users:
     - Your Gmail address
   - Create OAuth Client ID:
     - Application type: Desktop app
     - Name: "Newsletter Client"
   - Download JSON
   - Rename to `credentials.json`
   - Move to project folder

### Step 3: OpenAI Setup
1. Visit [OpenAI Platform](https://platform.openai.com)
2. Create account/login
3. Click "API Keys" → "Create new secret key"
4. Copy key

### Step 4: Environment Setup
Create `.env` file:
```
OPENAI_API_KEY=your-openai-key
SUMMARY_EMAIL=your-email@example.com
```

### Step 5: Configure Newsletters
Update `NEWSLETTER_SENDERS` in newsletter_processor.py:
```python
NEWSLETTER_SENDERS = [
    'newsletter1@example.com',
    'newsletter2@example.com'
]
```

### Step 6: Run
```bash
python newsletter_processor.py
```
First run opens browser for Gmail authorization.

## Troubleshooting

### Common Issues
1. "Access Blocked" error
   - Check OAuth consent screen setup
   - Verify you're logged into correct Google account

2. "API Key Invalid" error
   - Check OPENAI_API_KEY in .env
   - Verify key on OpenAI platform

3. No emails processed
   - Verify newsletter sender addresses
   - Check for unread emails
