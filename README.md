# power-automate-employee-data-to-sharepoint
## What This Flow Does
An automated Power Automate flow that reads a CSV file received via email and populates a SharePoint list with the data. Every time a new email arrives with a CSV attachment, the flow clears the existing SharePoint list and repopulates it with fresh data from the CSV.
## Features
- Triggers when email with CSV attachment is received
- Filters non-CSV attachments automatically
- Clears existing SharePoint list before repopulating
- Handles 400+ rows efficiently with concurrency
## Prerequisites
- Microsoft Power Automate account (standard license)
- Microsoft SharePoint site with a list set up
- Microsoft OneDrive for Business account
- Outlook email account connected to Power Automate
- A CSV file with consistent column headers
- ## Flow Structure
```
Trigger: When a new email arrives (V3)
    ↓
Initialize Variable (Rows - Array)
    ↓
Get items (fetch all existing SharePoint items)
    ↓
Condition (is list empty?)
    ├── True  → Apply to each → Delete item (Concurrency: 50)
    └── False → Skip
    ↓
For each (loop through email attachments)
    ↓
    Condition 1 (does attachment end with .csv?)
        └── True
            ├── Get Attachment (V2)
            ├── Create file (save to OneDrive)
            ├── Get file content (read from OneDrive)
            ├── Compose (convert to text)
            ├── Set Variable (split CSV into rows)
            └── Apply to each (loop through rows, Concurrency: 50)
                    └── Condition (skip header row)
                            ├── True  → Do nothing
                            └── False → Create item (SharePoint)
            └── Delete file (clean up OneDrive)
```
---
