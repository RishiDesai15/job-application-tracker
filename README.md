# 📋 Job Hunt — Application Tracker

A clean, dark-themed, interactive job application tracker that lives entirely in your browser. No backend, no sign-up — just open the file and start tracking.

---

## ✨ Features

- **Add / Edit / Delete** applications with a smooth modal UI
- **Color-coded status badges** — Interview, Rejected, Waiting, Intro Call, Offer, Withdrawn, Pending
- **Filter by status** with one-click pill buttons
- **Search** across company, position, notes, and contact info
- **Sort** by company, position, or applied date
- **Contact emails** render as clickable `mailto:` links
- **Live stat counters** in the header (total, interviews, rejected, offers)
- **Export to CSV** — download a snapshot at any time
- **Persistent storage** via `localStorage` — your data survives page refreshes
- Pre-loaded with sample data so you can explore right away

---

## 📁 File Structure

```
job-tracker/
├── index.html      # App shell + table + modals
├── styles.css      # Dark theme, badges, layout
├── app.js          # All logic: CRUD, filtering, sorting, CSV export
└── README.md       # This file
```

---

## 🚀 Hosting on GitHub Pages (Free, in ~3 minutes)

### Step 1 — Create a GitHub Repository

1. Go to [github.com](https://github.com) and log in (or create a free account)
2. Click the **+** icon → **New repository**
3. Name it something like `job-tracker` or `job-hunt`
4. Set it to **Public** (required for free GitHub Pages)
5. Click **Create repository**

### Step 2 — Upload Your Files

**Option A — Drag & Drop (easiest)**
1. On your new repo page, click **uploading an existing file**
2. Drag all three files into the upload box: `index.html`, `styles.css`, `app.js`
3. Scroll down and click **Commit changes**

**Option B — Git CLI**
```bash
git init
git add .
git commit -m "Initial commit: job tracker"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/job-tracker.git
git push -u origin main
```

### Step 3 — Enable GitHub Pages

1. In your repo, click **Settings** (top nav)
2. Click **Pages** in the left sidebar
3. Under **Source**, select **Deploy from a branch**
4. Set branch to `main` and folder to `/ (root)`
5. Click **Save**

### Step 4 — Get Your URL 🎉

After 1–2 minutes, your site will be live at:

```
https://YOUR_USERNAME.github.io/job-tracker/
```

GitHub will show you this URL in the Pages settings once it's ready.

> **Tip:** Bookmark this URL. Any time you push changes to the repo, GitHub Pages will automatically redeploy.

---

## 💾 Data & Privacy

All data is stored in your browser's `localStorage`. It **never leaves your device** — there's no server, no database, no analytics. To move your data to another browser or device, use the **CSV export** button and re-import manually.

---

## 🎨 Status Colors Reference

| Status     | Color         |
|------------|---------------|
| Interview  | 🟢 Green      |
| Intro Call | 🔵 Blue       |
| Waiting    | 🟡 Yellow     |
| Rejected   | 🔴 Red        |
| Offer      | 🟣 Purple     |
| Withdrawn  | 🟠 Orange     |
| Pending    | ⚪ Grey       |

---

## 🛠 Customization Tips

- **Add more status options**: Edit the `<select id="fResponse">` in `index.html` and add corresponding badge/row classes in `styles.css`
- **Change the color theme**: All colors are CSS variables at the top of `styles.css` under `:root`
- **Remove sample data**: In `app.js`, clear out the `SAMPLE_DATA` array
- **Add more columns**: Add a `<th>` in `index.html`, a `td` in the `rowHTML()` function in `app.js`, and a matching field in the form

---

## 🤖 GitHub Copilot Prompt

> See the bottom of this README for the Copilot onboarding prompt.

---

## 📌 Copilot Onboarding Prompt

Use this to bring GitHub Copilot (or any AI assistant) up to speed on this project:

---

```
This project is a single-page, client-side job application tracker built with
vanilla HTML, CSS, and JavaScript — no frameworks, no backend, no build step.

FILE OVERVIEW:
- index.html  — App shell. Contains the header with stats, a filter/search bar,
                the main <table> (columns: Company, Position, Status, Notes,
                Applied Date, Result, Contacts, Actions), an Add/Edit modal,
                and a Delete confirmation modal.
- styles.css  — Dark theme using CSS variables (all defined in :root). Uses
                Google Fonts (Syne, IBM Plex Mono, DM Sans). Status-specific
                colors are named --green, --red, --yellow, --blue, --purple,
                --orange and used in .badge-* and .row-* classes.
- app.js      — All application logic. Key sections:
                  • SAMPLE_DATA array — pre-loaded entries (matches the user's
                    real spreadsheet data)
                  • State variables: applications[], currentFilter, searchQuery,
                    sortCol, sortDir, pendingDeleteId
                  • init()       — loads from localStorage or seeds SAMPLE_DATA
                  • save()       — persists to localStorage
                  • render()     — filters, searches, sorts, then re-renders <tbody>
                  • rowHTML(app) — returns a <tr> string for one application
                  • renderStats()— updates header chip counters
                  • openAdd() / openEdit(id) — controls the modal
                  • handleSubmit(e) — creates or updates an application
                  • exportCSV()  — downloads all data as a .csv file
                  • toast(msg, type) — shows a temporary notification

DATA MODEL — each application object:
{
  id:          string   // uid() = timestamp + random chars
  company:     string
  position:    string
  response:    string   // '' | 'Interview' | 'Rejected' | 'Waiting' |
                        //    'Intro Call' | 'Offer' | 'Withdrawn'
  appliedDate: string   // 'YYYY-MM-DD'
  notes:       string
  result:      string
  emails:      string   // newline-separated "Name: email@domain.com" entries
}

CONVENTIONS:
- Status badge CSS classes follow the pattern .badge-{status lowercase}
- Row highlight classes follow .row-{status lowercase}
- The app uses NO external JS libraries — everything is vanilla DOM
- Data persists in localStorage under the key 'jobtracker_apps'
- Modal open/close is handled by toggling the .open class on .modal-overlay
- The app is hosted as a static site on GitHub Pages
```

---

*Built to track the grind. Good luck out there. 🚀*
