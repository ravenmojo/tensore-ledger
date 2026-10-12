# TENSORE Lab Cleaning Fund Ledger

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen.svg)](https://ravenmojo.github.io/tensore-ledger/)
[![GitHub Pages](https://img.shields.io/badge/hosted_on-GitHub%20Pages-blue.svg)](https://pages.github.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **Live Website:** [https://ravenmojo.github.io/tensore-ledger/](https://ravenmojo.github.io/tensore-ledger/)  
> Automated, transparent, and serverless financial ledger for the **TENSORE Lab, IIT Kharagpur**.

---

## 🌟 Overview

The **TENSORE Lab Cleaning Fund** web application tracks member contributions (credits) and service payments (debits) in real time. Built as a lightweight, single-page application hosted on **GitHub Pages** with a **Google Sheets + Apps Script** serverless backend, it requires zero maintenance, incurs zero hosting cost, and provides complete auditability.

---

## ✨ Key Features

### 1. 💰 Contribution Submission (UPI & Cash)
- **📱 UPI Payments**: Upload a payment screenshot and client-side OCR automatically extracts the **amount** and **transaction date**.
- **💵 Cash Contributions**: Direct entry mode for in-person cash contributions (amount and date mandatory, no screenshot required).
- **Client-Side Privacy**: OCR runs entirely in the contributor's browser using [Tesseract.js](https://tesseract.projectnaptha.com/) — fast and private.

### 2. 🔒 On-Page Admin Panel & Inline Editing
- **PIN-Protected Access**: Secure admin gate authenticated server-side via Google Apps Script.
- **Pending Submissions Queue**: Real-time list of pending contributions awaiting verification.
- **📎 Screenshot Inspector**: Full-screen modal overlay to verify uploaded UPI receipts.
- **✏️ Inline Edit Mode**: Admins can inspect the receipt and correct any misread OCR amounts, dates, or names before approving.
- **One-Click Approval/Rejection**: Approving an entry automatically writes to the **Pending** sheet, appends to the **Main Ledger**, and updates the live balance.

### 3. 📊 Interactive Live Ledger
- **Direct Access**: Clicking **View Ledger** immediately displays historical transactions.
- **Latest-to-Oldest Ordering**: Recent transactions appear at the top so users immediately see recent entries.
- **25-Row Paginated Infinite Scroll**: Renders 25 entries initially and seamlessly loads older batches as the user scrolls.
- **Navigation Controls**: Includes an **↑ Top (Latest)** floating button and a **🔄 Refresh** button to fetch updated data without reloading the browser.

### 4. 🎨 Modern Aesthetics
- Custom responsive design with warm, curated palette.
- **🌓 Dark / Light Mode** toggle with system preference detection and `localStorage` persistence.
- Glassmorphism, smooth micro-animations, and mobile-friendly layouts.

---

## 🛠️ Architecture & Tech Stack

| Component | Technology | Description |
|---|---|---|
| **Frontend** | HTML5, CSS3, JavaScript (ES6+) | Vanilla implementation, zero heavy frameworks |
| **Hosting** | GitHub Pages | Static hosting with automatic SSL |
| **OCR Engine** | Tesseract.js v5 | In-browser text recognition for UPI receipts |
| **CSV Parser** | PapaParse v5 | High-speed client-side CSV parsing |
| **Backend** | Google Apps Script (GAS) | Serverless REST API (`doPost`, `doGet`) |
| **Database** | Google Sheets | Dual-sheet architecture (`Pending` + `Main Ledger`) |
| **Storage** | Google Drive API | Secure screenshot storage for UPI transactions |

---

## 📂 Google Sheets Structure

The backend Google Sheet consists of two tabs:

### 1. `Pending` Sheet
Stores incoming submissions awaiting admin approval:
- **Column A**: Timestamp
- **Column B**: Submitter Name
- **Column C**: Transaction Date
- **Column D**: Amount (₹)
- **Column E**: Checkbox (`✓`)
- **Column F**: Status (`PENDING`, `Approved`, `Rejected`)
- **Column G**: Screenshot URL (Drive link or `"Cash"`)

### 2. `Main Ledger` Sheet
Public ledger displayed on the website:
- **Column A**: Name / Description
- **Column B**: Date
- **Column C**: Debit (Expenses)
- **Column D**: Credit (Contributions)
- **Column E**: Balance

---

## 🚀 Setup & Local Development

### 1. Clone Repository
```bash
git clone https://github.com/ravenmojo/tensore-ledger.git
cd tensore-ledger
```

### 2. Run Locally
Because Google Sheets blocks cross-origin requests from the `file:///` protocol, run a local web server:

**Using Python:**
```bash
python -m http.server 8000
```
Open [http://localhost:8000](http://localhost:8000) in your browser.

**Using Node.js:**
```bash
npx serve .
```

---

## 👨‍💻 Author & Attribution

- **Developed by:** [Souradeep Satpathy](https://ravenmojo.github.io/)
- **Organization:** [TENSORE Lab, IIT Kharagpur](https://sites.google.com/view/tensore/home)
- **License:** [MIT](LICENSE)
