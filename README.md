# power-automate-employee-data-to-sharepoint
## What This Flow Does
Automatically reads a CSV file received via email 
and populates a SharePoint list with the data.Power Automate solution for extracting employee data from an email attachment and updating a SharePoint list.
## Features
- Triggers when email with CSV attachment is received
- Filters non-CSV attachments automatically
- Clears existing SharePoint list before repopulating
- Handles 400+ rows efficiently with concurrency
## Prerequisites
- Microsoft Power Automate license
- SharePoint list with matching columns
- OneDrive folder: /Power Automate Flow
- ## Flow Structure
1. Trigger: New email with attachment
2. Delete existing SharePoint items
3. Process CSV attachment
4. Populate SharePoint list
