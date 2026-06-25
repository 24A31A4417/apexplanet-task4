# ApexPlanet Internship – Task 4

## User Authentication, Session Management & Input Validation in PHP CRUD Blog

## 📌 Task Overview

This project is developed as part of the **ApexPlanet Internship – Task 4**.
The objective of this task is to enhance the existing **PHP CRUD Blog Application** by implementing:

* **User Authentication**
* **Session Management**
* **Form Validation**
* **Secure CRUD Operations**
* **Role-based session handling**
* **Improved UI for login, registration, and post management**

Task 4 builds on the previous CRUD Blog project and focuses on making the application more secure, user-friendly, and structured.

---

## 🚀 Features Implemented

### 1. User Registration

* New users can create an account.
* Registration form includes:

  * Username
  * Email
  * Password
  * Confirm Password
* Validations added:

  * All fields are required
  * Valid email format
  * Password must be at least 6 characters
  * Password and confirm password must match
  * Duplicate email check
* Passwords are securely stored using **`password_hash()`**

---

### 2. User Login

* Existing users can log in with email and password.
* Validations added:

  * Required field check
  * Email format validation
  * Password verification using **`password_verify()`**
* On successful login:

  * Session is created
  * User ID, username, and role are stored in session
* On failure:

  * Error messages are displayed properly

---

### 3. Session Management

* Protected pages require authentication.
* If a user is not logged in, they are redirected to the login page.
* Session variables used:

  * `user_id`
  * `username`
  * `role`
* Logout functionality destroys the session and redirects the user to login page.

---

### 4. Secure CRUD Operations

Users can perform CRUD operations only after logging in.

#### Create Post

* Logged-in users can create blog posts.
* Input validation added:

  * Title required
  * Content required
  * Minimum title length validation

#### View Posts

* Users can view only **their own posts**
* Search functionality implemented
* Pagination implemented for better UI/UX

#### Edit Post

* Users can edit only their own posts
* Validation added before updating post

#### Delete Post

* Users can delete only their own posts
* Delete operation is protected using user-based conditions

---

### 5. Prepared Statements for Security

To improve security and prevent SQL Injection, prepared statements are used in:

* Registration
* Login
* Create Post
* Edit Post
* Delete Post

---

### 6. Role-based Session Handling

* User role is stored in session after login
* Navigation bar supports role-based link rendering
* Admin link can be shown when the logged-in user role is `admin`

---

### 7. Improved UI

Bootstrap-based UI enhancements were added for:

* Login form
* Registration form
* Create Post page
* Edit Post page
* View Posts page
* Navbar and Dashboard

---

## 🛠️ Tech Stack

* **Frontend:** HTML, CSS, Bootstrap 5
* **Backend:** PHP
* **Database:** MySQL
* **Server:** XAMPP / Apache
* **Version Control:** Git & GitHub

---

## 📂 Project Structure

```bash
crud_blog/
│
├── auth/
│   ├── login.php
│   ├── register.php
│   └── logout.php
│
├── config/
│   └── database.php
│
├── includes/
│   ├── header.php
│   ├── footer.php
│   └── navbar.php
│
├── posts/
│   ├── create.php
│   ├── edit.php
│   ├── delete.php
│   └── view.php
│
├── assets/
│   ├── css/
│   └── images/
│
├── index.php
└── README.md
```

---

## ⚙️ Database Requirements

### Database Name

```sql
blog
```

### Required Tables

You should have the following tables:

#### `users` table

```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    role VARCHAR(20) DEFAULT 'editor',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### `posts` table

```sql
CREATE TABLE posts (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);
```

---

## ▶️ How to Run the Project

### 1. Start XAMPP

Start:

* Apache
* MySQL

### 2. Move project into htdocs

Place the project folder inside:

```bash
C:\xampp\htdocs\
```

or your XAMPP project directory.

### 3. Create Database

Open **phpMyAdmin** and create a database named:

```bash
blog
```

### 4. Import/Create Tables

Create the `users` and `posts` tables.

### 5. Configure Database Connection

Open:

```bash
config/database.php
```

Set your database credentials:

```php
$host = "localhost";
$username = "root";
$password = "";
$database = "blog";
```

### 6. Open in Browser

Run:

```bash
http://localhost/crud_blog/
```

---

## 🔐 Security Improvements in Task 4

* Password hashing with `password_hash()`
* Password verification with `password_verify()`
* Prepared statements for safer queries
* Session-based route protection
* Input validation on forms
* Ownership-based access for posts

---

## 📸 Suggested Screenshots for Submission

1. Registration Page
2. Login Page
3. Dashboard after login
4. Create Post page
5. My Posts page with search/pagination
6. Edit Post page
7. Logout / redirected login page
8. GitHub repository with Task 4 files

---

## 📚 Learning Outcomes

Through this task, I practiced:

* PHP authentication system
* Session management in PHP
* Password hashing and verification
* Form validation
* Prepared statements in MySQLi
* Secure CRUD development
* Git and GitHub workflow management

---

## 👨‍💻 Internship Task Details

**Internship:** ApexPlanet
**Task:** Task 4 – User Authentication, Session Management & Input Validation
**Project:** PHP CRUD Blog Application

---

## ✅ Status

**Task 4 Completed Successfully**

