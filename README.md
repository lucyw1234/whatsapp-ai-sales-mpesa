WhatsApp AI Sales Engine (with Automated M-Pesa Checkout)
Overview
This project is an autonomous, AI-powered WhatsApp sales engine designed for retail and e-commerce businesses. It handles end-to-end customer conversion, from initial inquiry and stock verification to generating dynamic M-Pesa STK push prompts for immediate payment.

Built for speed and execution, this architecture eliminates manual data entry, prevents lost sales from slow response times, and directly increases revenue through 24/7 intelligent automation.

Core Architecture
Front-End Interface: WhatsApp Business API

Operations & Logic Engine: n8n (Workflow Automation)

AI Brain: Mixtral 8x7b via Groq API (Agentic Intent Recognition & Tool Calling)

Database & Inventory: Google Sheets

Payment Gateway: Safaricom Daraja API (M-Pesa STK Push)

Key Features
Agentic Tool Execution: The AI is not a standard chatbot. It autonomously queries a live Google Sheet to verify stock levels and calculate dynamic pricing before confirming orders.

Defensive Data Sanitization: Hardwired JavaScript/RegEx sanitization layers intercept AI outputs to ensure clean, API-compliant phone numbers and integer amounts before hitting the payment gateway.

Global Error Handling: A dedicated catch-all workflow monitors the entire workspace. If an external API times out, it triggers an instant Telegram alert to the system admin with diagnostic data.

Escalation Protocol (Human-In-The-Loop): The AI is constrained by strict prompt rules. If a customer requests wholesale pricing, complains, or hits an edge case, the system freezes the AI, sends a polite hold message, and instantly notifies the business owner to take over the chat.

Workflow Execution Flow
Trigger: Customer sends a WhatsApp message.

Processing: n8n routes the message to the AI Agent.

Memory: Window Buffer Memory provides conversation context.

Tool Access: * Check_Stock: Reads inventory and pricing.

Initiate_Payment: Sub-workflow that formats data and pushes the M-Pesa STK prompt to the user's handset.

Fulfillment: Asynchronous webhook listener waits for Safaricom's bank receipt, logs the transaction, and sends final WhatsApp confirmation.

Business Value
Reduces Operational Cost: Eliminates the need for a dedicated 24/7 human sales rep for routine transactions.

Increases Conversion: Instantaneous checkout links capitalize on buyer intent without delay.

Zero Downtime: Intelligent error handling ensures the customer experience remains conversational even during backend API outages.
