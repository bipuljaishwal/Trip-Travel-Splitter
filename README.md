# ✈️ Travel Splitter

**Travel Splitter** is a robust, offline-first single-page application (SPA) designed to manage, track, and split group travel expenses. It eliminates the mathematical complexity of group trips by automatically calculating who owes whom, visualizing spending habits, and generating enterprise-grade PDF reports.

Built with **Vanilla JavaScript**, it requires no backend server, respects user privacy by storing data in `localStorage`, and features an optional synchronization engine for Google Sheets.

---

## 🚀 Key Features

* **Smart Settlement Algorithm:** Minimizes the number of transactions required to settle debts among the group.
* **Money Keeper (Banker) Mode:** Handles complex scenarios where one person holds a cash pool (advances) for the group.
* **Enterprise PDF Reports:** Generates professional, branded PDF summaries with vector icons, financial formatting, and transaction history.
* **Interactive Dashboard:** Real-time data visualization using Chart.js (Category breakdown & Per-person spending).
* **Google Sheet Sync:** Seamlessly import data from Google Forms/Sheets for collaborative tracking.
* **Offline First:** All data is persisted locally in the browser; works without an internet connection.
* **Data Portability:** Export and Import trip data as JSON backups.

---

## 🛠️ Technical Stack

* **Core:** HTML5, CSS3 (CSS Variables, Flexbox/Grid), Vanilla JavaScript (ES6+).
* **State Management:** LocalStorage API.
* **Libraries (via CDN):**
    * `Chart.js` - For data visualization.
    * `jsPDF` & `jspdf-autotable` - For client-side PDF generation.
    * `PapaParse` - For CSV parsing (Google Sheets integration).
    * `RemixIcon` - For UI iconography.

---

## 📋 Prerequisites

Since this is a client-side application, there are **no server-side prerequisites** (like Node.js, Python, or PHP).

* A modern web browser (Chrome, Firefox, Edge, Safari).
* (Optional) An internet connection is required only to load the CDN libraries initially and for Google Sheet Sync.

---

## 📦 Installation & Setup

### Option 1: Run Locally
1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/yourusername/travel-splitter.git](https://github.com/yourusername/travel-splitter.git)
    ```
2.  **Navigate to the folder:**
    ```bash
    cd travel-splitter
    ```
3.  **Open the App:**
    Simply double-click `index.html` to open it in your default browser.

### Option 2: Deploy (Static Hosting)
You can host this immediately on GitHub Pages, Netlify, or Vercel.
1.  Upload the `index.html` file (and any assets).
2.  Point your host to the file.
3.  Done!

---

## 📖 Usage Guide

### 1. Setup Phase
* **Trip Details:** Enter your trip name (e.g., "Summer 2026").
* **Add Travelers:** Enter names manually in the "Travelers" section.
* **Assign Banker (Optional):** If one person is collecting cash from everyone to pay for things, designate them as the "Money Keeper."

### 2. Recording Transactions
* **Expense:** When someone pays for a group activity (e.g., "John pays $50 for Dinner").
* **Advance:** When someone gives cash to the Banker (e.g., "Alice gives $100 to the Money Keeper").
    * *Note: You must select a Money Keeper in Setup before recording Advances.*

### 3. Google Sheet Sync (Advanced)
To sync data from a Google Sheet (linked to a Google Form):
1.  Create a Google Form with fields: `Name`, `Description`, `Amount`, `Date`.
2.  Link it to a Google Sheet.
3.  **Important:** Make the Google Sheet **Public** (Share -> Anyone with the link -> Viewer).
4.  Copy the URL and paste it into the **Server Data Sync** section in the app.
5.  Click **Sync Data Now**.
    * *The app intelligently matches column names like "Amount", "INR", "Timestamp", etc.*

### 4. Generating Reports
* Go to the dashboard or click the **Download Report** button in the header.
* The app will generate a high-quality PDF containing:
    * Financial Dashboard (Total Cost, Per Person Share).
    * Settlement Plan (Who pays whom).
    * Net Balance Table.
    * Detailed Transaction History.

---

## 🧠 Settlement Logic Explained

The application uses a **Net Balance** approach rather than splitting every single transaction individually.

1.  **Calculate Total & Share:**
    `Total Expenses / Number of Travelers = Fair Share`
2.  **Determine Net Balances:**
    `Paid Amount - Fair Share = Net Balance`
    * *Positive Balance (+):* Person is owed money.
    * *Negative Balance (-):* Person owes money.
3.  **Settlement Algorithm:**
    The app sorts debtors and creditors by amount. It then matches the highest debtor with the highest creditor to minimize the total number of transfers required to clear all debts.

---

## 📂 Project Structure

```text
travel-splitter/
│
├── index.html       # Contains all HTML, CSS, and Logic (Single File)
└── README.md        # Documentation
