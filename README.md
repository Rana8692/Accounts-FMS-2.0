Accounts FMS 2.0
Version: 2.0.0
Last Updated: May 22, 2025

Table of Contents
Introduction

Features

System Overview

Dashboard Header

Main Action Buttons

Scorecards

Entries Table

Workflow & Usage

Adding a New Entry

Viewing Entry Details

Processing Entries Through Stages

Responsibilities

Accessing Backend Data

Syncing Data

Technical Setup

Frontend

Backend API Endpoints

Troubleshooting

Future Enhancements (Suggestions)

1. Introduction
The Accounts Follow-up Management System (FMS) 2.0 is a web application designed to track and manage financial entries through a two-stage approval process. It provides a clear dashboard for an overview of entries, their current status, and facilitates actions based on defined responsibilities. The system aims to improve the efficiency of the accounts approval workflow.

2. Features
Sticky Dashboard Header: Displays "Accounts FMS 2.0", current date/time, a data synchronization button, and a user profile icon.

Entrance Animation: Shows a loading spinner and text ("Loading Accounts FMS 2.0...") on a blurred background during initial data load.

Responsive Design: Adapts to various screen sizes for usability on desktop, tablet, and mobile devices.

Modal-driven Interface: Utilizes macOS-style animated popups for viewing details and informational messages.

Google Form Integration for Entry: The "Add Entry" button redirects to an external Google Form for data submission.

Direct Backend Data Access: A "Backend Data" button provides a direct link to the underlying Google Sheet.

Dynamic Data Fetching & Modification:

Reads data using a Google Apps Script endpoint (VIEW_ENTRIES_URL).

Updates entry stages and details using a SheetDB API endpoint (MODIFY_ENTRIES_URL).

Client-Side Data Management:

Search functionality for entries in the main table.

Sortable table columns with visual indicators.

Pagination for handling large datasets.

Two-Stage Workflow (S1 & S2):

S1: "Updating Status to MD and Submitting" by the Accounts Team.

S2: "Check Necessary Documents And Approve the same" by the MD.

Status Visualization:

Color-coded status badges (e.g., "Pending: Updating Status to MD and Submitting", "Approved: Check Necessary Documents And Approve the same").

"Next Planned On" column in the table, highlighting overdue tasks.

Scorecards: Display key metrics like Total Entries, Pending S1, Pending S2, Approved, and Rejected counts.

Action Buttons in Entry Details:

"Take Action" buttons for progressing entries through S1 and S2.

Conditional logic for S1 and S2 actions, including handling external form links if provided in the data for "Take Action (S1)" or "Take Action (S2)" fields.

Informational Modals:

"Responsibilities" modal detailing roles for each process step, styled for readability.

"How to Use" modal providing a system guide, updated with current workflow.

Timestamp Management: Records and displays planned and actual timestamps for S1 and S2, calculating delays.

3. System Overview
Dashboard Header
System Title: "Accounts FMS 2.0".

Dynamic Date & Time: Current date and time.

Sync Button (🔄): Manually refreshes data from the backend.

User Profile Button (👤): Placeholder.

Main Action Buttons
Responsibilities: Opens a modal detailing who is responsible for each stage (Add Entry, S1 Action, S2 Action).

Backend Data: Opens the linked Google Sheet in a new tab.

How to Use: Opens a modal with instructions.

Add Entry: Opens an external Google Form in a new tab for submitting new entries.

Scorecards
Provides a quick overview of:

Total Entries

Pending: Updating Status to MD and Submitting

Pending: Check Necessary Documents And Approve the same

Approved: Check Necessary Documents And Approve the same

Rejected: Check Necessary Documents And Approve the same

Entries Table
Displays entries with sortable columns:

UID

Timestamp

Party Name

Payment Amounts

Status (descriptive and color-coded)

Next Planned On (highlights overdue tasks)

Comments (Initial)

Actions (View Details button)

4. Workflow & Usage
Adding a New Entry
Click the "Add Entry" button.

This will open the designated Google Form (https://docs.google.com/forms/d/e/1FAIpQLSfmJlLiNSs_pAf03EM06jBUR6Me0zFQJcDzkcsuEoZ2eU5mnw/viewform) in a new browser tab.

Fill out the Google Form with all required details (Party Name, Payment Amounts, Mobile Number, Comments, etc.).

Submit the Google Form.

The new entry will appear in the Accounts FMS 2.0 table after the next data sync (click the 🔄 icon in the header).

Viewing Entry Details
In the "All Recorded Entries" table, click the Eye icon (👁️) in the "Actions" column for the desired entry.

The "Entry Details" modal will open, showing comprehensive information including main details and the stage processing timeline.

Processing Entries Through Stages
Open Entry Details for an entry.

The "Stage Processing" section will display two main stages:

Updating Status to MD and Submitting (corresponds to S1 fields in the data)

Check Necessary Documents And Approve the same (corresponds to S2 fields in the data)

Stage 1: Updating Status to MD and Submitting:

If the entry's status is "Pending: Updating Status to MD and Submitting":

A "Take Action" button will be visible.

If the Take Action (S1) field in your Google Sheet for this entry contains a URL, clicking the button will open that URL in a new tab (for external action).

If Take Action (S1) is empty, clicking the button will allow internal processing (confirming S1 completion, setting actual timestamp, and updating status to "Pending: Check Necessary Documents And Approve the same").

Stage 2: Check Necessary Documents And Approve the same:

If the entry's status is "Pending: Check Necessary Documents And Approve the same":

A "Take Action" button will be visible.

If the Take Action (S2) field in your Google Sheet for this entry contains a URL, clicking the button will open that URL in a new tab.

Otherwise, clicking allows internal processing (e.g., adding S2 comments), changing status to "Awaiting Approval: Check Necessary Documents And Approve the same".

If the status is "Awaiting Approval: Check Necessary Documents And Approve the same":

Two "Take Action" buttons will appear (styled as Approve/Reject).

Clicking one will update the Approve/Reject (S2) field and set the final status (Approved or Rejected).

All updates are sent to the SheetDB API. The UI refreshes to reflect changes.

Responsibilities
Click the "Responsibilities" button.

A modal will display the tasks, who is responsible, how it's done, and when.

Add Entry: MD / Accounts Team, via Google Form, Anytime.

Updating Status to MD and Submitting: Accounts Team, via FMS/External Form, Within Two days.

Check Necessary Documents And Approve the same: MD, via FMS/External Form, Within Two days.

Accessing Backend Data
Click the "Backend Data" button.

This will open the linked Google Sheet (https://docs.google.com/spreadsheets/d/18mEHFdmuXYzgCZYKP_2Fr-6zr8R2XqpxWgLouX5Rc5c/edit?gid=1061979610#gid=1061979610) in a new browser tab.

Syncing Data
Click the Sync icon (🔄) in the dashboard header.

The icon animates, and the system re-fetches data from the VIEW_ENTRIES_URL.

5. Technical Setup
Frontend
HTML, CSS (Tailwind CSS), and vanilla JavaScript.

Backend API Endpoints
VIEW_ENTRIES_URL: https://script.google.com/macros/s/AKfycbzjN1DHyHyfLJUx7ttPlx73tfftKpUaKAd3chWpVoLbhG8OJkz796BrRRO7rsuDDZ3W2A/exec

Used for GET requests to fetch all entry data.

Expected to be a Google Apps Script Web App URL.

MODIFY_ENTRIES_URL: https://sheetdb.io/api/v1/nydthm8eqg4w4

Used for PUT (update) operations.

Updates are made by targeting the UID (e.g., .../UID/:entryUID).

Google Sheet Column Structure:
The system expects the Google Sheet (read by VIEW_ENTRIES_URL and written to by SheetDB via MODIFY_ENTRIES_URL and the Google Form) to have the following columns (case-sensitive):
Timestamp, Party Name, Payment Amounts, Mobile Number, Comments, UID, Take Action (S1), Planned (S1), Actual (S1), Time Delay (S1), Take Action (S2), Planned (S2), Actual (S2), Approve/Reject (S2), Comments (S2), Time Delay (S2).
An id column might also be present/used by SheetDB internally for row identification if UID is not configured as its primary key for updates.

6. Troubleshooting
"Failed to fetch" / "Network error":

Verify VIEW_ENTRIES_URL and MODIFY_ENTRIES_URL are correct.

For Google Apps Script (VIEW_ENTRIES_URL): Ensure correct deployment ("Anyone" access, "New version"). Check Apps Script "Executions" log.

For SheetDB (MODIFY_ENTRIES_URL): Ensure API URL is correct and permissions allow PUT operations based on the UID column. Check SheetDB dashboard for errors.

Check browser's Developer Console (Network and Console tabs).

Data not updating correctly:

Verify column headers in your Google Sheet match the expected names exactly (case-sensitive).

Ensure SheetDB is configured to use UID as the search key for updates.

7. Future Enhancements (Suggestions)
User Authentication: Secure the application.

Direct Editing in Table: For quick modifications.

Enhanced Filtering/Reporting: More advanced data analysis tools.

Notifications: For pending actions or overdue items.
