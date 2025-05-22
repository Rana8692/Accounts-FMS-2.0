
# 📘 Accounts FMS 2.0 – README

## 📂 Project Overview

**Accounts FMS 2.0** is a web-based interface designed to manage financial entries related to payments and approvals within an organization. The system streamlines entry tracking, approval workflows, and accountability for finance team members and management.

This dashboard is built using **HTML**, **Tailwind CSS**, and **JavaScript**, and integrates with:
- **Google Forms** for entry submission
- **Google Sheets** via **Apps Script** and **SheetDB API** for data retrieval and modifications

---

## 🚀 Features

- 🎯 **Dashboard Summary**: Displays scorecards summarizing total entries, pending actions, approvals, and rejections.
- 📝 **Google Form Integration**: Enables adding new entries via an embedded Google Form.
- 📄 **Detailed Entry Viewer**: View and process individual entries in a modal with a stage-based timeline.
- 🛠️ **Workflow Stages**:
  - **S1**: Status Update to MD by Accounts Team
  - **S2**: Document Check & Final Approval by MD
- 🔍 **Search & Sort**: Real-time filtering and column-wise sorting of entries.
- 🧭 **Responsive UI**: Optimized for both desktop and mobile views.
- 🧾 **Role-based Guidance**: “Responsibilities” and “How to Use” modals for clarity and training.
- 🔁 **Manual Sync**: Sync button to refresh the dashboard with updated sheet data.

---

## 📁 File Structure

```
index.html          # Main HTML file with embedded JS, styles, and component structure
```

---

## 🔧 Technologies Used

- **HTML5**
- **Tailwind CSS**
- **JavaScript (ES6)**
- **Google Forms**
- **Google Apps Script API** for reading entries
- **SheetDB API** for updating backend data
- **Responsive design** principles

---

## 🔗 External Integrations

| Feature               | URL / API                                                                 |
|----------------------|---------------------------------------------------------------------------|
| Google Form (Add Entry) | [Embedded Google Form](https://docs.google.com/forms/d/e/1FAIpQLSfmJlLiNSs_pAf03EM06jBUR6Me0zFQJcDzkcsuEoZ2eU5mnw/viewform) |
| View Entries (GET)    | Google Apps Script Web App (Replace with actual endpoint if dynamic)     |
| Modify Entries (POST) | [SheetDB API](https://sheetdb.io/) endpoint                              |

---

## 🛠️ Setup & Deployment

1. **Host the HTML file** on any static web server (GitHub Pages, Firebase Hosting, Netlify, etc.)
2. **Ensure CORS is enabled** for Google Apps Script Web App.
3. **Set Google Sheet and Form access permissions** appropriately.
4. **Update API endpoints** in the `<script>` section of `index.html`:
   ```javascript
   const VIEW_ENTRIES_URL = '...';
   const MODIFY_ENTRIES_URL = '...';
   ```

---

## 📌 Usage Instructions

- Click **"Add Entry"** to submit new financial records.
- Use the **search bar** or **sortable headers** to filter/view entries.
- Click 👁️ to view and process entry stages.
- Sync data manually by clicking the 🔄 icon.
- Use the **“Responsibilities”** and **“How to Use”** buttons for operational guidance.

---

## 🙋 Support

For questions, bugs, or feature requests, please contact the Admin/Support Team listed in your organization.
