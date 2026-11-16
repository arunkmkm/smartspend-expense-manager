
# SmartSpend - Database Design

## 1. Overview

SmartSpend is a personal finance management application.
MySQL is used to store user accounts, expense records,
categories, and monthly budgets.

## 2. Database Name

smartspend_db

## 3. Tables

### Users
Stores registered user information.

- id: Primary Key
- name: User's name
- email: Unique email address
- password_hash: Hashed password
- created_at: Account creation timestamp
- updated_at: Last update timestamp

### Categories
Stores expense categories.

- id: Primary Key
- name: Unique category name
- created_at: Creation timestamp

Default categories:
Food, Travel, Shopping, Bills, Entertainment,
Healthcare, Education, Other.

### Expenses
Stores individual user expenses.

- id: Primary Key
- user_id: Foreign Key referencing users(id)
- category_id: Foreign Key referencing categories(id)
- amount: Expense amount
- description: Expense description
- expense_date: Date of expense
- created_at: Record creation timestamp

### Budgets
Stores monthly category-wise spending limits.

- id: Primary Key
- user_id: Foreign Key referencing users(id)
- category_id: Foreign Key referencing categories(id)
- monthly_limit: Monthly spending limit
- budget_month: Budget month (1-12)
- budget_year: Budget year
- created_at: Record creation timestamp

A unique constraint prevents duplicate budgets
for the same user, category, month, and year.

## 4. Relationships

- One user can have many expenses.
- One category can have many expenses.
- One user can have many budgets.
- One category can have many budgets.

## 5. Data Integrity

- Primary keys uniquely identify records.
- Foreign keys maintain valid relationships.
- Unique constraints prevent duplicate emails,
  category names, and monthly budgets.
- Check constraints ensure positive expense amounts
  and budget limits, and valid budget months.

## 6. Technology

- Database: MySQL
- Backend: Java Spring Boot
- Frontend: React.js
