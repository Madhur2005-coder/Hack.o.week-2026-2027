1. Project Overview (What It Is)
"I built a Student Library Management System as my college project. It is a full-stack web application that allows students to browse and borrow books, and allows a librarian/admin to manage the entire library catalog digitally."

2. Problem Statement (Why It's Needed)
"Traditional library systems rely on paper registers which are error-prone, slow, and hard to track. My system digitizes the entire process — from book registration to borrowing and return tracking — with automatic fine calculation for overdue books."

3. Technologies Used (Tech Stack)
Explain it layer by layer:

Layer	Technology	Why I Used It
Backend / API	Python + FastAPI	Modern, fast framework. Generates API docs automatically
Database	SQLite	Lightweight relational database, zero setup needed
Authentication	JWT (JSON Web Tokens)	Stateless, secure login sessions
Password Security	PBKDF2-HMAC-SHA256	Industry-standard cryptographic hashing
Frontend	HTML + CSS + JavaScript	Single-page app served directly by the backend
API Documentation	Swagger UI (built into FastAPI)	Auto-generated, interactive API sandbox
"I chose Python because it is widely used in industry, and FastAPI is one of the fastest growing frameworks for building REST APIs."

4. Key Features (What It Does)
For Students:
Register/Login securely with hashed passwords
Browse and search the book catalog (by title, author, genre)
Borrow books (up to 3 at a time)
Return books and view their borrowing history
See overdue fines automatically calculated
For Admin (Librarian):
Add, update, and delete books from the catalog
View all active borrowings across all students
View the full registered student directory
Manage book stock inventory
5. System Architecture (How It Works)
Draw or describe this flow:


Browser (Frontend)
      ↓  HTTP Request
FastAPI Server (Backend)
      ↓  SQL Query
SQLite Database
"The frontend (HTML/CSS/JS) makes HTTP requests to the FastAPI backend. The backend validates the request, checks the JWT token to confirm who is logged in and what their role is, then queries the SQLite database and sends back a JSON response."

6. Database Design (3 Tables)
"My database has 3 related tables that follow proper relational design principles:"


users                    books                    borrowings
─────────────────        ─────────────────        ──────────────────────
id (PK)                  id (PK)                  id (PK)
name                     title                    user_id (FK → users)
email (unique)           author                   book_id (FK → books)
password (hashed)        isbn (unique)            borrow_date
role (student/admin)     copies_available         due_date
created_at               total_copies             return_date
                         genre                    fine_amount
                         published_year
"The borrowings table acts as a join table linking students to books with additional metadata like dates and fines."

7. Security & Business Logic
"I implemented proper security and real-world business rules:"

JWT Authentication — Every protected API request must carry a valid token
Role-Based Access Control — Admins get extra privileges (adding/deleting books), students cannot access admin routes
Password Hashing — No passwords are stored in plain text. I use PBKDF2-HMAC-SHA256 with a random salt
Borrow Limit — Students cannot borrow more than 3 books at a time
Duplicate Prevention — Can't borrow the same book twice simultaneously
Fine Calculation — $1.00 per day automatically added if a book is returned after the 14-day due date
Deletion Guard — Admin cannot delete a book that is currently checked out by a student
8. REST API Endpoints (What I Built)
"I built a total of 12 REST API endpoints following industry-standard design patterns:"

Method	Endpoint	Description
POST	/api/auth/register	Create new account
POST	/api/auth/login	Login and get token
GET	/api/books/	Search/browse all books
POST	/api/books/	Add book (admin only)
PUT	/api/books/{id}	Edit book (admin only)
DELETE	/api/books/{id}	Delete book (admin only)
POST	/api/borrow/borrow	Borrow a book
POST	/api/borrow/return	Return a book
GET	/api/borrow/current	My active borrowings
GET	/api/borrow/history	My full history
GET	/api/borrow/admin/active	All library loans (admin)
GET	/api/users/profile	My profile
9. What I Learned
"Through this project I learned:"

How to design a relational database schema with foreign keys
How REST APIs work and how to build them with proper HTTP methods
How JWT authentication and role-based access control work
How to hash passwords securely using cryptographic algorithms
How to build and connect a frontend SPA to a backend API using fetch()
How to write automated integration tests to verify system correctness
How to use FastAPI's auto-documentation (Swagger UI) which is widely used in industry
