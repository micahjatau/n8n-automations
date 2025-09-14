🧾 Invoice Automation Workflow

Built with: n8n, Mistral OCR, Google Sheets, Telegram, Gmail
Role: Automation Engineer / Workflow Developer
Client: Internal Portfolio Project (Adaptable to SMBs, finance teams, and startups)
Status: Completed ✅

🔍 Problem Overview

Manual invoice processing is tedious, error-prone, and inefficient.
Finance teams and small businesses often spend 5–15 minutes per invoice reviewing files, extracting key data (like vendor name, amount, date, and category), and entering them into spreadsheets or databases.

For companies that receive dozens of invoices per week, this amounts to hours of lost productivity and increased risk of data entry errors — especially when dealing with multiple file formats (PDFs, scanned images, forwarded emails, and chat submissions).

🎯 Goal

Build a unified invoice intake system that can:

Accept invoices from Telegram, Gmail, or form uploads

Extract structured data (vendor, amount, date, tax, etc.)

Handle PDFs and image-based invoices (via OCR)

Auto-classify and validate data

Append clean records to a Google Sheet

Flag low-confidence extractions for review

⚙️ Solution Architecture
🔧 Tools Used
Tool	Purpose
n8n	Workflow orchestration
Telegram Bot	Accept chat uploads
Gmail Trigger	Process email attachments
Form Uploads/Webhook	Allow API or web form ingestion
Mistral OCR	Extract text from PDFs/images
JavaScript Nodes	Regex fallback, error handling, validation
Google Sheets	Centralized data storage
🧠 Smart Workflow Features
✅ Multi-Source Input Handling

Telegram: Detects if file is image or PDF → routes accordingly

Gmail: Auto-downloads attachments from new emails

Form submissions: Accepts API/webhook payloads directly

📄 OCR + AI Extraction

Uses Mistral OCR (or Tesseract fallback) to extract raw text

AI model transforms messy text into a structured JSON:

{
  "vendor": "XYZ Company",
  "amount": 275,
  "date": "2028-09-07",
  "invoice_number": "#INV-2023-001"
}

🔐 Validation & Enrichment

If critical fields (like vendor/amount) are missing → fallback logic kicks in

Adds metadata: user source, transaction ID, confidence score, overdue status

🧾 Output Storage

Every successful invoice is appended to a Google Sheet

Fields tracked include:

Vendor, Amount, Date, Tax, Currency, Category, Type

Transaction ID, Source (e.g., Telegram), User, Confidence Score

📊 Outcomes
Metric	Before	After
Time per invoice	5–15 mins	~30 seconds
Data errors	Common (manual entry)	<2% (with AI + fallback)
Human effort	High	Zero-touch after upload
Confidence scoring	❌	✅ High/Med/Low tagging
Multi-source support	❌	✅ Telegram, Email, API
🔍 Sample Output (Google Sheet)
Date	Vendor	Amount	Tax	Category	Confidence
2028-09-07	XYZ Company	$275.00	$25.00	Services	High
💡 Why This Matters for Clients

If you:

Collect invoices from WhatsApp, Telegram, or Email

Have a team still doing manual data entry

Want to standardize formats across vendors

Then this solution gives you:

24/7 automation

Near real-time entry into your accounting system

Pluggable AI/LLM support for improving accuracy over time

🚀 Want a Custom Invoice Bot?

Whether you're a startup, freelancer, or agency — I can help you:

Build custom document pipelines

Create Google Sheet dashboards

Send auto-alerts for rejected/flagged files

Connect this to Notion, Airtable, or your CRM

📬 DM me or connect on LinkedIn
 — let's automate your back office.
