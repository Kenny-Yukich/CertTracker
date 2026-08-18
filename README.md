# Certificate Tracker

## Overview

Certificate Tracker is an automated equipment certification tracking and notification system built with Microsoft 365 tools. The solution helps organizations monitor employee equipment certifications, calculate expiration dates, and notify responsible leaders before certifications expire or become overdue.

This project is designed to reduce manual tracking, improve compliance visibility, and provide a centralized source of truth for certification records.

## Problem Statement

Organizations often track certifications manually using spreadsheets, email reminders, or disconnected records. Manual tracking can lead to missed expirations, compliance gaps, duplicated work, and limited reporting visibility.

Certificate Tracker solves this by combining structured certification records with automated daily checks and notification workflows.

## Key Features

- Centralized certification record tracking
- Department and equipment lookup lists
- Automatic expiration date calculation
- Days remaining calculation
- Daily compliance review workflow
- 30-day expiration warning notifications
- Overdue certification alerts
- List views for filtering and reporting
- Export to Excel for audits and reporting

## Technology Stack

| Component | Purpose |
|---|---|
| SharePoint Online | Hosts the project site and list experience |
| Microsoft Lists | Stores certification, department, and equipment data |
| Power Automate | Runs scheduled checks and sends notifications |
| SharePoint Pages | Provides the user-facing dashboard and documentation page |
| Excel Export | Supports offline review, reporting, and audits |

## Data Model

### Main List: CertTracker

The main list stores one record per employee certification.

| Field | Description |
|---|---|
| Employee Name | Name of the certified employee |
| Department | Department associated with the employee |
| Equipment | Equipment or machine certification type |
| Certification Date | Date the certification was completed |
| Valid Years | Number of years the certification remains valid |
| Expiration Date | Calculated certification expiration date |
| Days Remaining | Number of days until expiration |
| Department Lead | Responsible department contact or supervisor |
| Lead Email | Email address used for notifications |

### Supporting List: Department Lookup

Stores department-level ownership information.

| Field | Description |
|---|---|
| Department Name | Name of the department |
| Department Lead | Person responsible for department certification oversight |
| Lead Email | Notification email address for the department lead |

### Supporting List: Equipment Lookup

Stores equipment certification reference data.

| Field | Description |
|---|---|
| Equipment Name | Name of the equipment or certification type |
| Default Valid Years | Standard certification duration |
| Renewal Notes | Optional renewal or compliance notes |

## Automation Logic

A scheduled Power Automate flow runs every morning and reviews all certification records.

### Daily Workflow

1. Get all certification records from the main list.
2. Calculate each certification expiration date.
3. Calculate the number of days remaining.
4. Update the certification record with current values.
5. Identify certifications that are within the warning window.
6. Send warning notifications to the responsible lead.
7. Identify certifications that are past due.
8. Send overdue alerts when the overdue threshold is met.

## Notification Rules

### Expiration Warning

A warning notification is sent when a certification is 30 days from expiration.

The notification can include:

- Employee name
- Department
- Equipment certification
- Certification date
- Expiration date
- Days remaining

### Overdue Alert

An overdue alert is sent when a certification is 7 days past expiration.

The alert can include:

- Employee name
- Department
- Equipment certification
- Expiration date
- Number of days overdue
- Responsible department lead

## Example Workflow

```text
Certification record created or updated
        ↓
Expiration date calculated
        ↓
Daily scheduled automation runs
        ↓
Days remaining calculated
        ↓
30-day warning needed?
        ↓
Warning email sent
        ↓
Certification overdue by 7 days?
        ↓
Overdue alert sent
```

## Recommended SharePoint Views

Useful list views may include:

- All Certifications
- Expiring in 30 Days
- Overdue Certifications
- By Department
- By Equipment Type
- Recently Renewed
- Compliance Review

## Permissions Model

Recommended access levels:

| Role | Access Level |
|---|---|
| Site Owners | Full Control |
| Administrators | Edit and manage all records |
| Department Leads | View and update department records |
| Employees | Read access, if appropriate |
| Auditors or Reviewers | Read-only access |

## Benefits

- Reduces manual tracking effort
- Improves certification compliance
- Provides early visibility into upcoming expirations
- Helps prevent overdue certifications
- Centralizes records in Microsoft 365
- Supports audits and management reporting
- Creates a repeatable notification process

## Future Enhancements

Potential improvements include:

- Power BI compliance dashboard
- Microsoft Teams notifications
- Certificate attachment storage
- Employee self-service renewal requests
- Multi-level escalation workflow
- Automated renewal task creation
- Historical certification archive
- Mobile-friendly dashboard experience

## Repository Contents

Suggested repository structure:

```text
certificate-tracker/
├── README.md
├── docs/
│   ├── setup-guide.md
│   ├── data-model.md
│   └── automation-flow.md
├── screenshots/
│   └── dashboard-example.png
└── power-automate/
    └── flow-overview.md
```

## Getting Started

1. Create a SharePoint site for the project.
2. Create the main certification tracking list.
3. Create supporting lookup lists for departments and equipment.
4. Configure lookup columns in the main list.
5. Create calculated or automation-managed fields for expiration tracking.
6. Build the scheduled Power Automate flow.
7. Configure warning and overdue email notifications.
8. Test with sample certification records.
9. Create filtered SharePoint views for reporting.
10. Publish project documentation for users and administrators.

## Notes

This README intentionally avoids organization-specific names, internal URLs, employee records, email addresses, and proprietary data so the project can be safely shared in a public GitHub repository.


