# GoHighLevel reporting and Google Docs automation

Exported n8n workflows for conversation archiving and marketing reporting. These are workflow definitions, not a standalone Python application.

## Workflows

- [talkinfrench_conversations.json](talkinfrench_conversations.json): scheduled conversation processing using HTTP requests, batching, waits, and Google Drive/Docs nodes. Creates documents and appends conversation content.
- [Weekly_Marketing_Report.json](Weekly_Marketing_Report.json): scheduled reporting with Mailchimp campaign metrics, YouTube statistics, Facebook/Instagram metrics, and Google Sheets updates.
- The PNG files show the original workflow layouts.

## Import and configure

1. Import a JSON file into an isolated n8n development instance. Keep the imported workflow inactive while reviewing it; these exports contain `active: true`.
2. Reconnect credentials in n8n for the services used by that workflow. Exported credential references do not provision working credentials.
3. Review every HTTP Request, Code, and Google service node. Replace account-specific URLs, identifiers, document/folder/sheet IDs, and any inline authentication values with your own configuration.
4. For conversation processing, use a test source and a separate Google Drive folder. For reporting, use a test spreadsheet and confirm the date range and row/index calculations.
5. Run one small manual execution and inspect each node's output before enabling schedules.

## Validation checklist

- Conversation documents contain the expected messages, ordering, and formatting.
- An empty source result is handled without creating an unintended document.
- A second run does not create unwanted duplicates.
- Marketing metrics match the source services for the same reporting period.
- Authentication failures, API rate limits, and retry behavior are checked with test accounts.

These are manual acceptance checks; the repository does not currently contain an automated workflow test suite. The export does not establish a tested n8n version, so verify node compatibility after import.

## Configuration and data handling

Treat exports and screenshots as account-specific artifacts. Review inline headers, Code node strings, pinned execution data, and credential references before reusing or sharing them. Keep tokens in n8n credentials and use synthetic contact/conversation data for demos. Any token exposed by a previous export must be rotated at its provider; removing it from a new file does not revoke it.

No license file is currently included. Confirm reuse permission before distributing a derivative workflow.
