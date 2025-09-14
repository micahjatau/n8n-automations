# n8n Automations

A collection of automation workflows built with [n8n](https://n8n.io).  
Each folder contains a self-contained project with:

- Exported `workflow.json` (ready to import into n8n)
- Setup instructions
- Screenshots and/or demo GIFs

## Projects

- [Telegram AI Bot](./telegram-ai-bot) – Chatbot that connects Telegram with OpenAI GPT
- [Quote Request Automation](./quote-request) – Capture, store, and auto-respond to client quote requests
- [Payment Automation](./payment-automation) – Crypto payment processing and settlement bot
- [WhatsApp Chatbot](./whatsapp-chatbot) - A simple chatbot that connects to your whatsapp account
- [Invoice automation workflow](./invoice-automation-workflow) - A workflow that extracts data from uploaded files using OCR + AI, saves it to Google Sheets & Airtable, and sends a notification based on the upload source. 

---

### How to Use
1. Clone this repo
2. Open n8n > Import from File > select `workflow.json` from a project folder
3. Configure your own credentials (Telegram API, OpenAI key, etc.)
