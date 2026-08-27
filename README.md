# Bank Guarantee (BG) Request & Approval Portal

A secure, enterprise-level web portal built with **Flask** and **Supabase (PostgreSQL)** to automate the submission, tracking, and approval lifecycle of Bank Guarantees.

---

## 🚀 Key Features

* **Role-Based Access Control (RBAC):** Separate user roles for **Requesters** and **Admins/Approvers**.
* **Draft & Submit Workflow:** Requesters can create drafts, upload files, and submit requests once ready.
* **Dynamic Approval Limits:** 
  * Requests with amounts **≤ ₹15,00,000** require Managing Director (MD) approval.
  * Requests with amounts **> ₹15,00,000** require Board approval.
* **Smart File Validation:** Automatically checks for mandatory document uploads based on approval levels (e.g., vetted draft, MD/Board approval files).
* **Secure Document Hosting:** Integrates with cloud storage using signed URLs for secure document access.
* **Activity & Audit Logging:** Tracks status transitions and decision-making trails with timestamped history and remarks.

---

## 🛠️ Tech Stack

* **Backend:** Python, Flask, Werkzeug, python-dotenv
* **Frontend:** HTML5, CSS3, Jinja2 Templates, JavaScript
* **Database & Security:** Supabase (PostgreSQL), Row Level Security (RLS) policies
* **Deployment Ready:** Gunicorn

---

## 📂 Project Structure

```text
├── bg_portal/              # Main application package
│   ├── routes/             # Authentication, Admin, Request, and Setting routes
│   ├── templates/          # HTML Templates (Jinja2)
│   ├── utils/              # Helper functions (Approval limits, File uploads)
│   ├── app.py              # Flask app factory initialization
│   ├── extensions.py       # DB / Supabase Client configuration
│   └── config.py           # Configuration classes
├── app.py                  # Server entry point
├── schema.sql              # Database schema & RLS policies
├── requirements.txt        # Python dependency list
└── .env.example            # Template for environment variables
```

---

## ⚙️ Setup and Installation

### 1. Clone the Repository
```bash
git clone <your-repository-url>
cd Internship-Project
```

### 2. Configure Environment Variables
Create a `.env` file in the root directory and add your configurations (refer to `.env.example`):
```ini
SECRET_KEY=your-secret-key
SUPABASE_URL=https://your-project-ref.supabase.co
SUPABASE_KEY=your-supabase-anon-key
MD_APPROVAL_LIMIT=1500000
```

### 3. Setup Virtual Environment & Install Dependencies
```bash
# Create virtual environment
python3 -m venv venv

# Activate virtual environment
source venv/bin/activate  # On Windows use: venv\Scripts\activate

# Install requirements
pip install -r requirements.txt
```

### 4. Run the Application
```bash
python app.py
```
The server will start running at **[http://127.0.0.1:5000](http://127.0.0.1:5000)**.

---

## 🔒 Security & RLS Policies
The database is configured with PostgreSQL **Row Level Security (RLS)** to protect user data:
* **Requesters** can only view and modify their own requests.
* **Admins/Approvers** are granted broad access to view all requests to make informed decisions.
