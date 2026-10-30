# 🎓 Student Management System (SMS) - Python Django

A complete, responsive, full-stack **Student Management System** developed with **Python**, **Django**, **SQLite**, and modern **HTML5, CSS3, & JavaScript**.

Designed specifically for college projects, viva presentations, and internship submissions.

---

## 🌟 Features Overview

- 🔐 **Authentication & Security:** Built-in Django authentication for administrator login and secure logout. Unauthorized access to student data is prevented.
- 📊 **Dynamic Dashboard:** Real-time statistics including total student count, gender breakdown, active department distribution, quick actions, and the latest student registrations.
- 👨‍🎓 **CRUD Operations:**
  - **Create:** Add new students with ID, full name, email, phone number, gender, date of birth, department, course, year of study, and address.
  - **Read:** Comprehensive student directory table with pagination and individual detailed profile view cards.
  - **Update:** Edit existing student details with pre-populated form fields and uniqueness validations.
  - **Delete:** Delete student records with safety confirmation prompts to prevent accidental loss.
- 🔍 **Search & Filters:** Instantly search students by name, registration ID, or department, plus filter by department and course.
- 🛡️ **Validation:** Client-side JavaScript validation (email format, digit checks, date ranges) and server-side Django Form validations (duplicate ID/email checks, minimum age requirements).
- 📱 **Responsive Design:** Clean, modern blue-and-white theme that adapts smoothly to mobile devices, tablets, and desktop screens with a mobile sliding sidebar.
- 💬 **Flash Notifications:** Django message alerts (success, error, warning, info) with auto-dismiss timers.

---

## 📁 Project Structure

```text
student management system/
│
├── manage.py                          # Django management script
├── requirements.txt                   # Project dependencies
├── README.md                          # Documentation & execution guide
├── db.sqlite3                         # SQLite database (auto-generated)
│
├── student_management/                # Project Configuration
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py                    # App settings, DB, static paths
│   ├── urls.py                        # Root URL routing
│   └── wsgi.py
│
└── students/                          # Core Application
    ├── __init__.py
    ├── admin.py                       # Django Admin customization
    ├── apps.py
    ├── forms.py                       # StudentForm & AdminLoginForm
    ├── models.py                      # Student database model
    ├── urls.py                        # Student routes (CRUD + Auth)
    ├── views.py                       # Business logic & views
    │
    ├── migrations/                    # Database migrations
    │   ├── __init__.py
    │   └── 0001_initial.py
    │
    ├── static/                        # Static Assets
    │   ├── css/
    │   │   └── style.css              # Custom blue & white responsive theme
    │   └── js/
    │       └── script.js              # Client validation & UI controls
    │
    ├── templates/students/            # Django HTML Templates
    │   ├── base.html                  # Main layout with sidebar & topbar
    │   ├── login.html                 # Administrator login page
    │   ├── dashboard.html             # Summary metrics & recent activity
    │   ├── student_list.html          # Student directory, search & table
    │   ├── student_form.html          # Add & Edit student form
    │   ├── student_detail.html        # Detailed profile card
    │   └── student_confirm_delete.html # Deletion confirmation dialog
    │
    └── management/commands/
        ├── __init__.py
        └── seed_students.py           # Optional command to load demo students
```

---

## 🚀 Step-by-Step Setup & Execution Guide

### Step 1: Install Python
Ensure Python (version 3.9 or higher) is installed on your computer:
1. Download Python from the official website: [python.org/downloads](https://www.python.org/downloads/)
2. **Important for Windows users:** When running the Python installer, check the box:  
   ☑️ **"Add Python to PATH"** (or **"Add python.exe to PATH"**).
3. Verify your installation by opening a terminal (Command Prompt or PowerShell) and typing:
   ```bash
   python --version
   ```
   *(or `py --version`)*

---

### Step 2: Open the Project Directory
Open your terminal or PowerShell and navigate to the project folder:
```bash
cd "c:\Users\pujan\OneDrive\Desktop\student management system"
```

---

### Step 3: (Recommended) Create and Activate a Virtual Environment
A virtual environment keeps the project dependencies isolated:

**On Windows (PowerShell or Command Prompt):**
```powershell
python -m venv venv
venv\Scripts\activate
```

*(On macOS / Linux):*
```bash
python3 -m venv venv
source venv/bin/activate
```

---

### Step 4: Install Dependencies
Install Django using the provided `requirements.txt`:
```bash
pip install -r requirements.txt
```

---

### Step 5: Run Database Migrations
Create the SQLite database tables for users, sessions, and the `Student` model:
```bash
python manage.py makemigrations
python manage.py migrate
```

---

### Step 6: Create an Administrator Account
Create your superuser account to log in to the Student Management System:
```bash
python manage.py createsuperuser
```
Follow the prompts in your terminal:
- **Username:** `admin` (or your preferred name)
- **Email:** `admin@example.com`
- **Password:** Enter a secure password (note: characters will not show while typing for security)
- **Password (again):** Re-enter your password

---

### Step 7: (Optional) Seed Sample Demo Data
To immediately populate the system with sample students across various departments:
```bash
python manage.py seed_students
```

---

### Step 8: Start the Development Server
Run the local Django development server:
```bash
python manage.py runserver
```

You should see output similar to:
```text
System check identified no issues (0 silenced).
Django version 5.x.x, using settings 'student_management.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK / CTRL-C.
```

---

### Step 9: Open the Application in Your Browser
1. Open Google Chrome, Firefox, Edge, or any web browser.
2. Navigate to:  
   👉 **`http://127.0.0.1:8000/`**
3. If not logged in, you will be redirected to the **Login Page** (`http://127.0.0.1:8000/login/`).
4. Enter the administrator username and password you created in **Step 6**.
5. Click **Sign In to Dashboard**.

---

## 🧪 Testing System Operations

| Action | URL Route | Description |
|---|---|---|
| **Login** | `/login/` | Log in with the admin superuser account. |
| **Dashboard** | `/` | View total student count, department distribution chart, and quick shortcuts. |
| **Add Student** | `/students/add/` | Fill in the student form (Student ID, Full Name, Email, Phone, Gender, DOB, Department, Course, Year, Address) and submit. |
| **View All** | `/students/` | View the student table with pagination and contact details. |
| **Search & Filter** | `/students/?q=John` | Type a query in the search bar or select a department from the dropdown to filter records. |
| **View Profile** | `/students/<id>/` | View the complete profile card of an individual student. |
| **Update** | `/students/<id>/edit/` | Modify fields (e.g. course or phone) and save changes. |
| **Delete** | `/students/<id>/delete/` | Confirm and permanently delete a student record. |
| **Logout** | `/logout/` | Sign out securely. |
| **Django Admin** | `/admin/` | Standard Django admin backend interface for database audits. |

---

## 💡 Technologies & Concepts Demonstrated

- **Architecture:** Django MTV (Model-Template-View) Pattern
- **Database:** Relational SQLite with ORM queries, foreign key capability, and aggregate calculations (`Count`, `Q` filters)
- **Security:** CSRF Protection tokens, hashed passwords (PBKDF2/SHA256), session management, SQL injection defense via Django ORM
- **Frontend:** Responsive CSS Grid & Flexbox, CSS Variables, Mobile Drawer navigation, DOM manipulation for client validation

