# Dynamic Task Management & Reporting System (Trello API → Excel)

## Overview
This project is a Python-based automation pipeline that extracts task-level data from Trello using its REST API and generates a structured Excel report for tracking and reporting. It is designed to help teams consolidate Trello activity into a single spreadsheet that can be shared with stakeholders, used for audits, or analysed for progress tracking.

The script retrieves board lists and cards, extracts key metadata (such as due dates, last activity, labels, and list status), and exports everything into an Excel workbook in a clean tabular format.

## Problem Statement
Teams often manage requirements, bugs, and activity tracking inside Trello boards. While Trello is excellent for day-to-day execution, it becomes difficult to:
- Create consistent weekly/monthly status reports
- Track due dates and activity across multiple lists in one view
- Share structured updates with stakeholders who prefer Excel
- Analyse trends such as delayed tasks, inactivity, or workload distribution

Manual reporting from Trello is time-consuming and inconsistent, especially when boards contain many lists and cards.

## Solution
This project automates the reporting workflow by connecting to Trello via API and exporting all relevant task information into Excel.

### High-Level Workflow
1. Connect to Trello API and fetch all lists under a board
2. For each list, fetch all cards in that list
3. Extract key fields from each card:
   - Card URL (traceability)
   - Card Name
   - Due Date (if available)
   - Last Activity Date (if available)
   - Label (if available)
   - List Name (acts as task status/category)
4. Consolidate all cards across lists into a single dataset
5. Export the dataset into a structured Excel file for reporting

### Key Implementation Details
- Uses the Trello REST API endpoint to pull lists from a board:
  - `/1/boards/{board_id}/lists`
- Uses the list-level endpoint to fetch cards:
  - `/1/lists/{list_id}/cards`
- Handles missing fields safely:
  - If a card has no label, due date, or activity date, the script assigns `None` instead of failing
- Writes results to Excel using Pandas `to_excel()` for structured export

## Tech Stack
- Python
- REST API Integration (Trello API)
- requests (HTTP calls)
- json (response parsing)
- pandas (tabular transformation and export)
- Microsoft Excel output (`.xlsx`)

## Output
The script generates an Excel report containing one row per Trello card, with the following columns:
- URL
- Name
- Due Date
- Last Activity Date
- Label
- List Name

This creates an analytics-ready dataset that can be filtered, sorted, and analysed in Excel or imported into BI tools.

## Use Cases
- Weekly/monthly project reporting from Trello
- Requirement and activity tracking for delivery teams
- Bug/issue reporting consolidation for stakeholders
- Audit-friendly documentation of task status and activity
- Building dashboards in Power BI using exported Excel as a source

## Potential Enhancements
- Export additional Trello fields (members, descriptions, checklists, comments)
- Support multiple boards and consolidated reporting
- Automate scheduling (cron/Azure Functions) for daily refresh
- Load output into SQL database for historical tracking
- Build a Power BI dashboard on top of the exported dataset
- Add error handling for API failures (rate limits, network retries)

## Notes
This project was built as a practical automation solution to convert Trello activity into a structured reporting format without manual effort. It demonstrates API integration, data transformation, and automated reporting — common tasks in analytics and data engineering roles.
