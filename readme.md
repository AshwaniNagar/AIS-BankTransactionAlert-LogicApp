# Bank Transaction Alert - Azure Logic App

A reusable Azure Logic App that monitors incoming bank transaction data via HTTP, logs the data to Excel (OneDrive/SharePoint), and sends an alert email if a transaction meets suspicious criteria (e.g., high amount or non INR transaction).

## Features

- Triggered via HTTP POST with transaction payload
- Logs each transaction to an Excel table (OneDrive/SharePoint)
- Sends alert email for flagged transactions
- Error handling with failure notification and explicit termination
- Parameterized and reusable with ARM template + parameter file

---

## Technology Stack

- **Azure Logic Apps**
- **Excel Online connector**
- **Gmail connector** 
- **ARM Templates** for deployment

---

## Folder Structure
├── LogicApp-bankTransactionAlert-template.json # ARM Template defining Logic App and workflow
├── LogicApp-bankTransactionAlert-parameters.json # Parameters file (environment-specific)
└── README.md # Project documentation

---

## Error Handling
 - On failure, the Logic App sends an error email with details.
 - It explicitly terminates with a Failed status for observability.

 ---

 ## Future Enhancements
 - Add adaptive card in Teams for flagged transactions
 - Connect to Azure Service Bus for downstream processing
 - Add retry policies and logic to auto-handle transient failures

 ---

 ## Sample Payload
Send a POST request with the following JSON structure to the Logic App's HTTP endpoint:
{
  "transactionId": "TXN123456",
  "user": "Ashwani Nagar",
  "amount": 12000,
  "currency": "INR",
  "location": "Delhi",
  "description": "iPhone 15 Purchase",
  "timestamp": "2025-07-26T10:30:00Z"
}


