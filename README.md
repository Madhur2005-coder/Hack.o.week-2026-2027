# 📚 Student Library Management System
![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-0.139-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-Auth-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
A full-stack **Student Library Management System** built as a college project. It features a secure **REST API backend** (Python + FastAPI + SQLite) and a **premium dark-mode web frontend** (HTML/CSS/JS) — all served from a single server.
---
## ✨ Features
### 👨‍🎓 For Students
- Register & login securely (JWT-based sessions)
- Browse & search the book catalog (by title, author, genre)
- Borrow books (max 3 active at once)
- Return books with automatic fine calculation
- View complete borrowing history & pending fines
### 🛡️ For Admins (Librarians)
- Add, update, and delete books from the catalog
- View all active borrowings across all students
- Browse the registered student directory
- Delete books (blocked if actively borrowed)
### 🔐 Security
- Passwords hashed with **PBKDF2-HMAC-SHA256** (never stored in plain text)
- **JWT tokens** for stateless, secure session authentication
- **Role-Based Access Control** (Admin vs. Student)
---
## 🖥️ Tech Stack
|
 Layer 
|
 Technology 
|
|
---
|
---
|
|
 Backend Framework 
|
 Python 3.8+ · FastAPI 
|
|
 Database 
|
 SQLite (via built-in 
`sqlite3`
) 
|
|
 Authentication 
|
 JWT (
`PyJWT`
) 
|
|
 Password Security 
|
 PBKDF2-HMAC-SHA256 (Python 
`hashlib`
) 
|
|
 Frontend 
|
 HTML5 · Vanilla CSS · Vanilla JavaScript 
|
|
 ASGI Server 
|
 Uvicorn 
|
|
 API Docs 
|
 Swagger UI (auto-generated at 
`/docs`
) 
|
---
## 📁 Project Structure
```
student-library-backend/
│
├── app/
│   ├── __init__.py
│   ├── config.py            # JWT config, business rules (fine rate, borrow limits)
│   ├── database.py          # SQLite init, table schemas, data seeding
│   ├── dependencies.py      # JWT decode, role guard dependencies
│   ├── schemas.py           # Pydantic request/response validation models
│   ├── utils.py             # Password hashing & verification helpers
│   ├── main.py              # FastAPI app init, static files, CORS, routers
│   └── routers/
│       ├── __init__.py
│       ├── auth.py          # POST /register, POST /login
│       ├── books.py         # GET/POST/PUT/DELETE /books
│       ├── borrow.py        # Borrow/Return/History endpoints
│       └── users.py         # User profile & student directory
│
├── static/
│   ├── index.html           # Single Page Application layout
│   ├── style.css            # Dark glassmorphism design system
│   └── app.js               # API client, DOM rendering, session management
│
├── .env.example             # Environment variable template
├── .gitignore               # Git exclusions (DB files, secrets, pycache)
├── requirements.txt         # Python dependencies
├── test_api.py              # Automated integration test suite
└── README.md
```
---
## 🚀 Getting Started
### Prerequisites
- **Python 3.8+** installed on your machine
- `pip` package manager
### 1. Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/student-library-backend.git
cd student-library-backend
```
### 2. Set Up Environment (Optional)
```bash
# Create a virtual environment (recommended)
python -m venv venv
# Activate it:
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
```
### 3. Install Dependencies
```bash
pip install -r requirements.txt
```
### 4. Configure Environment Variables (Optional)
```bash
# Copy the example file
copy .env.example .env       # Windows
cp .env.example .env         # macOS/Linux
# Edit .env and set your own JWT_SECRET
```
### 5. Run the Server
```bash
python -m uvicorn app.main:app --reload
```
The server will start at **http://127.0.0.1:8000**
> **Note:** The database (`library.db`) is automatically created and seeded with sample data on first launch.
---
## 🔑 Default Test Accounts
The database is pre-seeded with these accounts on first run:
|
 Role 
|
 Email 
|
 Password 
|
|
------
|
-------
|
----------
|
|
 👑 Admin / Librarian 
|
`admin@library.com`
|
`admin123`
|
|
 🎓 Student 
|
`student@library.com`
|
`student123`
|
---
## 📖 API Documentation
Once running, visit the **interactive Swagger UI**:
👉 **http://127.0.0.1:8000/docs**
Or the ReDoc alternative:
👉 **http://127.0.0.1:8000/redoc**
### Endpoint Summary
#### 🔐 Authentication
|
 Method 
|
 Endpoint 
|
 Access 
|
 Description 
|
|
--------
|
----------
|
--------
|
-------------
|
|
`POST`
|
`/api/auth/register`
|
 Public 
|
 Register new user 
|
|
`POST`
|
`/api/auth/login`
|
 Public 
|
 Login & get JWT token 
|
#### 📚 Books
|
 Method 
|
 Endpoint 
|
 Access 
|
 Description 
|
|
--------
|
----------
|
--------
|
-------------
|
|
`GET`
|
`/api/books/`
|
 Public 
|
 List/search books (paginated) 
|
|
`GET`
|
`/api/books/{id}`
|
 Public 
|
 Get single book 
|
|
`POST`
|
`/api/books/`
|
 Admin 
|
 Add new book 
|
|
`PUT`
|
`/api/books/{id}`
|
 Admin 
|
 Update book 
|
|
`DELETE`
|
`/api/books/{id}`
|
 Admin 
|
 Delete book 
|
#### 🔖 Borrowing
|
 Method 
|
 Endpoint 
|
 Access 
|
 Description 
|
|
--------
|
----------
|
--------
|
-------------
|
|
`POST`
|
`/api/borrow/borrow`
|
 Authenticated 
|
 Borrow a book 
|
|
`POST`
|
`/api/borrow/return`
|
 Authenticated 
|
 Return a book 
|
|
`GET`
|
`/api/borrow/current`
|
 Authenticated 
|
 Active borrows 
|
|
`GET`
|
`/api/borrow/history`
|
 Authenticated 
|
 Full borrow history 
|
|
`GET`
|
`/api/borrow/admin/active`
|
 Admin 
|
 All library active loans 
|
#### 👤 Users
|
 Method 
|
 Endpoint 
|
 Access 
|
 Description 
|
|
--------
|
----------
|
--------
|
-------------
|
|
`GET`
|
`/api/users/profile`
|
 Authenticated 
|
 My profile 
|
|
`GET`
|
`/api/users/`
|
 Admin 
|
 All students 
|
---
## 📋 Business Rules
|
 Rule 
|
 Value 
|
|
------
|
-------
|
|
 Max concurrent borrows per student 
|
**
3 books
**
|
|
 Default borrowing period 
|
**
14 days
**
|
|
 Overdue fine rate 
|
**
$1.00 per day
**
|
|
 Minimum password length 
|
**
6 characters
**
|
---
## 🧪 Running Tests
An automated integration test suite validates all endpoints:
```bash
python test_api.py
```
**Test coverage includes:**
- ✅ Registration & login (including duplicate prevention)
- ✅ Book CRUD (admin-only enforcement, duplicate ISBN blocking)
- ✅ Borrowing (stock checks, duplicate borrow prevention, limit enforcement)
- ✅ Return (fine calculation, inventory restoration)
- ✅ Admin-only route protection
- ✅ User profile & student directory
---
## 🗄️ Database Schema
```sql
-- Users
CREATE TABLE users (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    email TEXT UNIQUE NOT NULL,
    password TEXT NOT NULL,      -- PBKDF2 hashed
    role TEXT NOT NULL,          -- 'student' or 'admin'
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);
-- Books
CREATE TABLE books (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    title TEXT NOT NULL,
    author TEXT NOT NULL,
    isbn TEXT UNIQUE NOT NULL,
    copies_available INTEGER NOT NULL DEFAULT 1,
    total_copies INTEGER NOT NULL DEFAULT 1,
    genre TEXT,
    published_year INTEGER
);
-- Borrowings
CREATE TABLE borrowings (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    user_id INTEGER NOT NULL REFERENCES users(id),
    book_id INTEGER NOT NULL REFERENCES books(id),
    borrow_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    due_date DATETIME NOT NULL,
    return_date DATETIME,        -- NULL if not returned yet
    fine_amount REAL DEFAULT 0.0
);
```
---
## 📄 License
This project is licensed under the **MIT License** — feel free to use, modify, and distribute it.
---
## 👨‍💻 Author
Madhur Wanjari
