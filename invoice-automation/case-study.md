# 🧾 Invoice Automation Workflow

**Built with:** n8n, Mistral OCR, Google Sheets, Telegram, Gmail  
**Role:** Automation Engineer / Workflow Developer  
**Client:** Internal Portfolio Project *(Adaptable to SMBs, finance teams, and startups)*  
**Status:** Completed ✅  

---

## 🔍 Problem Overview

Manual invoice processing is tedious, error-prone, and inefficient.  
Finance teams and small businesses often spend **5–15 minutes per invoice** reviewing files, extracting key data (like vendor name, amount, date, and category), and entering them into spreadsheets or databases.

For companies that receive dozens of invoices per week, this amounts to **hours of lost productivity** and increased risk of data entry errors — especially when dealing with multiple file formats (PDFs, scanned images, forwarded emails, and chat submissions).

---

## 🎯 Goal

Build a **unified invoice intake system** that can:

- Accept invoices from **Telegram**, **Gmail**, or **form uploads**
- Extract structured data (vendor, amount, date, tax, etc.)
- Handle **PDFs and image-based** invoices (via OCR)
- Auto-classify and validate data
- Append clean records to a **Google Sheet**
- Flag low-confidence extractions for review

---

## ⚙️ Solution Architecture

### 🔧 Tools Used

| Tool           | Purpose                          |
|----------------|----------------------------------|
| **n8n**        | Workflow orchestration           |
| **Telegram Bot** | Accept chat uploads             |
| **Gmail Trigger** | Process email attachments      |
| **Webhook/API** | Accept external form submissions |
| **Mistral OCR** | Extract text from PDFs/images   |
| **JavaScript Nodes** | Validation, error handling |
| **Google Sheets** | Centralized data storage      |

---

## 🧠 Smart Workflow Features

### ✅ Multi-Source Input Handling

- **Telegram**: Detects if file is image or PDF → routes accordingly  
- **Gmail**: Auto-downloads attachments from new emails  
- **Webhook**: Accepts API/form payloads (e.g., mobile scanner apps)  

---

### 📄 OCR + AI Extraction

- Uses **Mistral OCR** (or fallback) to extract raw text  
- AI transforms messy text into a **structured JSON**:

```json
{
  "vendor": "XYZ Company",
  "amount": 275,
  "date": "2028-09-07",
  "invoice_number": "#INV-2023-001"
}
