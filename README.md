# 💸Expense Tracker

![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)
![Express.js](https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Sequelize](https://img.shields.io/badge/Sequelize-52B0E7?style=for-the-badge&logo=sequelize&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)
![License](https://img.shields.io/badge/License-ISC-lightgrey?style=for-the-badge)

---

## 📖 Project Description

**Final Expense Tracker** is a full-stack web application that helps users log, manage, and monitor their personal expenses with ease. Built on a clean **MVC (Model-View-Controller)** architecture using **Node.js**, **Express.js**, and **MySQL** via **Sequelize ORM**, the app provides a complete user lifecycle — from registration and login to expense management and secure password recovery.

Users can categorise spending, view running totals, and manage their financial history through a responsive, server-rendered interface. The project follows industry-standard patterns: layered routing, service-based business logic, JWT-based authentication, and dedicated middleware for security and validation — making it an excellent demonstration of production-ready backend engineering.

---

## ✨ Features

- 📝 **Expense Management** — Add, view, update, and delete personal expense entries
- 🔐 **User Authentication** — Secure registration and login with hashed passwords and JWT sessions
- 🔑 **Forgot Password Flow** — End-to-end password reset via email with token validation
- 🗂️ **Expense Categories** — Organise expenses by category for clearer financial insights
- 📊 **Spending Summary** — View total expenditure and per-category breakdowns
- 🛡️ **Protected Routes** — Middleware-enforced authentication guards all expense endpoints
- 🌐 **Server-Rendered UI** — Dedicated frontend views for Login, Signup, Forgot Password, and the Expense Dashboard
- 📁 **MVC Architecture** — Clean separation of concerns across controllers, models, services, routes, and utilities
- 🗄️ **Relational Database** — MySQL with Sequelize ORM for reliable schema management and querying

---

## 🛠️ Tech Stack

### Programming Language

| Language | Usage |
|---|---|
| JavaScript (Node.js) | Backend server, routing, and business logic |
| HTML5 | Frontend templates and page structure |
| CSS3 | Styling and responsive layout |

### Libraries / Frameworks

| Library / Framework | Purpose |
|---|---|
| Express.js | HTTP server, routing, and middleware pipeline |
| Sequelize ORM | MySQL database access, model definitions, and associations |
| MySQL2 | MySQL database driver for Node.js |
| bcryptjs | Secure password hashing and comparison |
| jsonwebtoken (JWT) | Stateless session tokens for authenticated routes |
| Nodemailer | Sending password-reset emails to users |
| dotenv | Environment variable management |
| express-validator | Request body validation middleware |

---

## 📁 Project Structure

```
Final-Expense-Tracker-Project/
│
├── app.js                      # Express app entry point — middleware, routes, server
│
├── controllers/                # Request handlers (HTTP layer)
│   ├── authController.js       # Login, signup, logout logic
│   ├── expenseController.js    # CRUD operations for expenses
│   └── passwordController.js  # Forgot/reset password handlers
│
├── models/                     # Sequelize model definitions
│   ├── user.js                 # User schema (id, name, email, password)
│   ├── expense.js              # Expense schema (amount, category, description, date)
│   └── index.js                # Sequelize initialisation and associations
│
├── routes/                     # Express route definitions
│   ├── authRoutes.js           # /login, /signup, /logout endpoints
│   ├── expenseRoutes.js        # /expenses CRUD endpoints
│   └── passwordRoutes.js       # /forgot-password, /reset-password endpoints
│
├── middleware/                 # Custom Express middleware
│   ├── authenticate.js         # JWT verification — protects private routes
│   └── validate.js             # Input validation rules
│
├── services/                   # Business logic layer
│   ├── userService.js          # User creation and lookup
│   ├── expenseService.js       # Expense aggregation and queries
│   └── emailService.js         # Nodemailer email dispatch
│
├── util/                       # Utility/helper functions
│   └── tokenHelper.js          # JWT sign and verify helpers
│
├── login/                      # Login page (HTML + JS)
│   └── index.html
│
├── signup/                     # Signup page (HTML + JS)
│   └── index.html
│
├── ForgotPassword/             # Forgot/reset password page (HTML + JS)
│   └── index.html
│
├── ExpenseTracker/             # Main expense dashboard (HTML + JS)
│   └── index.html
│
├── public/
│   └── css/                    # Global stylesheets
│
└── .env.example                # Environment variable template
```

---

## ⚙️ Installation Steps

### Prerequisites

Ensure the following are installed on your machine:

- [Node.js](https://nodejs.org/) v16 or higher
- [npm](https://www.npmjs.com/) v8 or higher
- [MySQL](https://www.mysql.com/) v8 or higher (local or cloud)
- A running MySQL server with a database created

### 1. Clone the Repository

```bash
git clone https://github.com/sroy3333/Final-Expense-Tracker-Project.git
cd Final-Expense-Tracker-Project
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Create the MySQL Database

Open your MySQL client (Workbench, CLI, or DBeaver) and run:

```sql
CREATE DATABASE expense_tracker;
```

### 4. Configure Environment Variables

Create a `.env` file in the root directory:

```bash
cp .env.example .env
```

Fill in your values:

```env
# Server
PORT=3000

# MySQL Database
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_NAME=expense_tracker

# Authentication
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRES_IN=1d

# Email (Nodemailer — for password reset)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_app_password

# App URL (used in reset-password emails)
APP_URL=http://localhost:3000
```

### 5. Run Database Migrations

Sequelize will sync models and create tables automatically on first run. Alternatively, run migrations if configured:

```bash
npx sequelize-cli db:migrate
```

---

## ▶️ How to Run the Project Locally

### Development Mode

```bash
node app.js
```

Or with auto-restart using nodemon:

```bash
npm install -g nodemon
nodemon app.js
```

The server starts at **`http://localhost:3000`**

### Navigate to the App

| Page | URL |
|---|---|
| Signup | `http://localhost:3000/signup` |
| Login | `http://localhost:3000/login` |
| Forgot Password | `http://localhost:3000/forgot-password` |
| Expense Dashboard | `http://localhost:3000/expense-tracker` |

### API Endpoints (Quick Reference)

| Method | Endpoint | Description | Auth Required |
|---|---|---|---|
| POST | `/user/signup` | Register a new user | ❌ |
| POST | `/user/login` | Login and receive JWT | ❌ |
| POST | `/password/forgot` | Send password-reset email | ❌ |
| POST | `/password/reset` | Reset password via token | ❌ |
| GET | `/expense` | Fetch all user expenses | ✅ |
| POST | `/expense` | Add a new expense | ✅ |
| PUT | `/expense/:id` | Update an expense | ✅ |
| DELETE | `/expense/:id` | Delete an expense | ✅ |

---

## 🔒 Authentication Flow

```
User Registers → Password hashed with bcrypt → Stored in MySQL
       ↓
User Logs In → Credentials verified → JWT issued
       ↓
JWT attached to requests → authenticate middleware validates token
       ↓
Expense routes accessible → Data scoped to logged-in user
```

**Forgot Password Flow:**

```
User submits email → Token generated → Reset link emailed via Nodemailer
       ↓
User clicks link → Token validated → New password hashed and saved
```

---

## 🗄️ Database Schema (Overview)

**Users Table**

| Column | Type | Description |
|---|---|---|
| id | INT (PK) | Auto-increment primary key |
| name | VARCHAR | Full name |
| email | VARCHAR (UNIQUE) | Login email |
| password | VARCHAR | bcrypt-hashed password |
| resetToken | VARCHAR | Password reset token |
| tokenExpiry | DATETIME | Token expiration timestamp |
| createdAt | DATETIME | Auto-managed by Sequelize |

**Expenses Table**

| Column | Type | Description |
|---|---|---|
| id | INT (PK) | Auto-increment primary key |
| amount | DECIMAL | Expense amount |
| description | VARCHAR | Short description |
| category | VARCHAR | Category label (e.g. Food, Travel) |
| date | DATE | Date of expense |
| UserId | INT (FK) | Foreign key → Users.id |
| createdAt | DATETIME | Auto-managed by Sequelize |

---

<div align="center">
  <p>
    <a href="https://github.com/sroy3333/Final-Expense-Tracker-Project/issues">Report a Bug</a> ·
    <a href="https://github.com/sroy3333/Final-Expense-Tracker-Project/issues">Request a Feature</a> ·
    <a href="https://github.com/sroy3333/Final-Expense-Tracker-Project">View Repository</a>
  </p>
</div>
