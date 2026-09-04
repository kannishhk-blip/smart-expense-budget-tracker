# Smart Expense & Budget Tracker

**“Track your money. Understand your spending. Reach your goals.”**

A production-quality, full-stack personal finance web application built to help college students, employees, freelancers, and families track income and expenses, monitor monthly category budgets, manage savings goals, analyze spending habits using interactive charts, receive budget overflow alerts, and export financial reports.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Problem Statement](#problem-statement)
3. [Proposed Solution](#proposed-solution)
4. [Key Features](#key-features)
5. [Technology Stack](#technology-stack)
6. [System Architecture](#system-architecture)
7. [Database Schema](#database-schema)
8. [Project Structure](#project-structure)
9. [Installation & Setup](#installation--setup)
10. [Environment Variables](#environment-variables)
11. [Database Setup & Seeding](#database-setup--seeding)
12. [Running the Application](#running-the-application)
13. [API Documentation](#api-documentation)
14. [Testing & Verification](#testing--verification)
15. [Deployment Guide](#deployment-guide)
16. [Future Improvements](#future-improvements)

---

## 1. Project Overview

People often spend money every day without knowing exactly where their money goes. Without systematic expense logging and budget monitoring, users risk overspending and struggle to achieve savings targets.

**Smart Expense & Budget Tracker** provides a centralized financial dashboard with real-time analytics, overspending warnings, savings goal progress, budget monitoring, and downloadable CSV transaction reports.

---

## 2. Problem Statement

* **Lack of Visibility:** Users may be unaware of cumulative daily expenses such as food delivery, transportation, and shopping.
* **Budget Exceedance:** Difficulty maintaining category-based spending limits throughout the month.
* **Complex Tools:** Many existing financial tools do not provide simple, unified category analytics and customizable savings goals.
* **Saving Obstacles:** Difficulty visualizing progress toward important savings milestones.

---

## 3. Proposed Solution

The application provides:

* Secure JWT authentication with session management.
* Interactive financial analytics using Recharts, including pie charts and monthly income-versus-expense trends.
* Complete transaction CRUD with search, filters, date ranges, amount ranges, and multi-field sorting.
* Monthly category budgets with dynamic warning badges at 80% usage and alert notifications when budgets are exceeded.
* Savings goals with target amounts, progress tracking, and deposit functionality.
* Financial insights including top spending category, highest expense, average daily spending, and month-over-month comparisons.
* Downloadable CSV transaction exports.
* Persistent dark mode and customizable currency support, including INR ₹, USD, EUR, and GBP.

---

## 4. Key Features

### 🏠 Landing Page

* Modern hero section
* Features overview
* How-it-works section
* Call-to-action buttons

### 🔐 Authentication

* User registration and login
* Logout functionality
* Protected routes
* Bcrypt password hashing
* JWT-based authorization
* Quick demo credentials fill

### 📊 Dashboard

* Income summary
* Expense summary
* Balance overview
* Savings summary
* Interactive Recharts visualizations
* Recent transactions

### 💳 Transactions

* Create, read, update, and delete transactions
* Income and expense tracking
* Instant search
* Type and category filters
* Date-range filtering
* Minimum and maximum amount filtering
* Multi-field sorting
* Responsive transaction table
* Mobile-friendly card layout
* CSV transaction export

### 💰 Budgets

* Monthly category budgets
* Budget progress bars
* Warning indicators
* Budget overflow alerts
* Budget usage monitoring

### 🎯 Savings Goals

* Create savings goals
* Target amount tracking
* Current savings progress
* Deposit funds
* Progress bars
* Goal completion badges

### 📈 Financial Insights

* Top spending category
* Highest expense
* Average daily spending
* Month-over-month spending comparison
* Spending analysis

### 📅 Monthly Reports

* Month and year selection
* Financial performance summaries
* Key performance indicators

### 🔔 Notifications

* Unread notification counter
* Budget warning notifications
* Budget exceeded notifications
* Goal achievement notifications
* Mark notifications as read
* Clear notifications

### ⚙️ Profile & Settings

* Profile management
* Avatar selection
* Password change
* Dark mode
* Currency selection
* Notification preferences
* Budget alert preferences
* Monthly report preferences

---

## 5. Technology Stack

### Frontend

* **React 18**
* **TypeScript**
* **Vite**
* **Tailwind CSS**
* **Lucide React**
* **Recharts**
* **React Router v6**
* **React Hot Toast**

### Backend

* **Node.js**
* **Express.js**
* **TypeScript**
* **Prisma ORM**
* **JWT (jsonwebtoken)**
* **Bcryptjs**
* **Zod**
* **Express Middleware**

### Database

* **SQLite** for local development
* **PostgreSQL** supported through Prisma configuration

---

## 6. System Architecture

```text
┌───────────────────────────────────────────────┐
│              React + Vite Frontend            │
│     TypeScript • Tailwind • Recharts         │
│       React Router • Lucide • Toast           │
└───────────────────────┬───────────────────────┘
                        │
                        │ REST API (JSON)
                        ▼
┌───────────────────────────────────────────────┐
│          Node.js + Express Backend            │
│      TypeScript • JWT • Bcryptjs • Zod        │
└───────────────────────┬───────────────────────┘
                        │
                        │ Prisma ORM
                        ▼
┌───────────────────────────────────────────────┐
│             Database Layer                    │
│             SQLite / PostgreSQL               │
└───────────────────────────────────────────────┘
```

---

## 7. Database Schema

The application uses Prisma ORM with the following main models:

* **User:** `id`, `name`, `email`, `passwordHash`, `profileImage`, `createdAt`, `updatedAt`
* **Transaction:** `id`, `userId`, `type`, `amount`, `category`, `description`, `paymentMethod`, `transactionDate`, `notes`, `receiptUrl`
* **Budget:** `id`, `userId`, `category`, `amount`, `month`, `year`
* **SavingsGoal:** `id`, `userId`, `name`, `targetAmount`, `currentAmount`, `targetDate`, `description`, `status`
* **Notification:** `id`, `userId`, `type`, `message`, `isRead`
* **UserSettings:** `id`, `userId`, `currency`, `darkMode`, `notificationsEnabled`, `budgetAlertsEnabled`, `monthlyReportsEnabled`

---

## 8. Project Structure

```text
expense/
├── prisma/
│   └── ...                       # Prisma database configuration
│
├── public/                       # Static assets and favicon
│
├── src/
│   ├── components/               # Reusable UI components
│   ├── context/                  # Authentication, theme and currency contexts
│   ├── layouts/                  # Application layouts
│   ├── pages/                    # Application pages
│   ├── services/                 # API and service functions
│   ├── types/                    # TypeScript interfaces and types
│   ├── utils/                    # Utility functions and CSV exporter
│   ├── App.tsx
│   └── main.tsx
│
├── PROJECT_DOCUMENTATION.md
├── README.md
├── index.html
├── package.json
├── package-lock.json
├── postcss.config.js
├── tailwind.config.js
├── tsconfig.json
└── vite.config.ts
```

---

## 9. Installation & Setup

### Prerequisites

* **Node.js:** v18.x or higher
* **npm:** v9.x or higher

### Step 1: Clone the Repository

```bash
git clone https://github.com/kannishhk-blip/smart-expense-budget-tracker.git
cd smart-expense-budget-tracker
```

### Step 2: Install Dependencies

```bash
npm install
```

---

## 10. Environment Variables

Create a `.env` file according to the application's configuration.

Example:

```env
PORT=5000
DATABASE_URL="file:./dev.db"
JWT_SECRET="your_secure_jwt_secret_here"
NODE_ENV="development"
```

> **Important:** Never commit real passwords, API keys, database credentials, or JWT secrets to GitHub.

---

## 11. Database Setup & Seeding

If Prisma is configured for the project, run:

```bash
npx prisma db push
npx prisma generate
```

To seed the database with demo data:

```bash
npx ts-node prisma/seed.ts
```

### Demo Credentials

**Email:** `demo@example.com`
**Password:** `Demo@12345`

> The demo credentials should only be used for a dedicated demo account and should not contain sensitive personal information.

---

## 12. Running the Application

Start the development server using:

```bash
npm run dev
```

The application will normally be available at:

```text
http://localhost:5173
```

If the backend runs as a separate service, configure and start it according to the backend scripts and environment variables in the project.

---

## 13. API Documentation

### Authentication

* `POST /api/auth/register` - Create a user account
* `POST /api/auth/login` - Authenticate a user and return JWT
* `POST /api/auth/logout` - Log out the current user
* `GET /api/auth/me` - Fetch authenticated user profile

### Transactions

* `GET /api/transactions` - Fetch transactions with search, filters, sorting and pagination
* `POST /api/transactions` - Create an income or expense transaction
* `GET /api/transactions/:id` - Fetch transaction details
* `PUT /api/transactions/:id` - Update a transaction
* `DELETE /api/transactions/:id` - Delete a transaction
* `GET /api/transactions/export` - Export transactions as CSV

### Budgets & Savings

* `GET /api/budgets` - Fetch category budgets and alert statuses
* `POST /api/budgets` - Create or update a category budget
* `DELETE /api/budgets/:id` - Delete a budget
* `GET /api/savings-goals` - List savings goals
* `POST /api/savings-goals` - Create a savings goal
* `POST /api/savings-goals/:id/add-funds` - Add funds to a savings goal

### Analytics & Reports

* `GET /api/dashboard/summary` - Fetch dashboard summary data
* `GET /api/dashboard/category-breakdown` - Fetch category expense distribution
* `GET /api/dashboard/monthly-trends` - Fetch monthly income and expense trends
* `GET /api/insights` - Fetch calculated financial insights
* `GET /api/reports/monthly` - Fetch detailed monthly performance reports

---

## 14. Testing & Verification

### TypeScript Type Checking

```bash
npx tsc --noEmit
```

### Production Build

```bash
npm run build
```

### End-to-End Verification

Test the following user flows:

* Register and log in with a user account.
* Add income and expense transactions.
* Verify dashboard totals and charts update correctly.
* Search and filter transactions.
* Create a category budget.
* Exceed a budget and verify the warning/notification behavior.
* Create a savings goal.
* Deposit funds into a savings goal.
* Verify goal progress and completion status.
* Export transactions as CSV and open the file in Excel.

---

## 15. Deployment Guide

### Frontend

The React/Vite application can be deployed using platforms such as:

* Vercel
* Netlify

Configure the required API base URL and environment variables for the production environment.

### Backend

The Node.js/Express backend can be deployed using platforms such as:

* Render
* Railway
* Heroku

For production deployments, configure the appropriate hosted PostgreSQL database and secure environment variables.

---

## 16. Future Improvements

* Bank account aggregation and Open Banking API integration
* AI-driven spending recommendations
* Recurring bill detection
* Receipt OCR scanning with automatic transaction extraction
* Multi-user shared family budgets
* Advanced financial forecasting
* More detailed spending analytics
* Mobile application support

---

## License

This project is intended for educational and portfolio purposes.
