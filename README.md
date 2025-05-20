# 📚 Library Management System (MySQL Workbench)

This project is a database-driven Library Management System developed using **MySQL Workbench**. It focuses on managing books, users, and borrowing activities within a library setting.

---

## ✅ Features

- Add, update, and delete book records
- Manage student and staff user accounts
- Track book borrowing and return transactions
- View overdue books
- Search for books by title or author

---

## 🛠️ Tools Used

- **Database Tool:** MySQL Workbench
- **Language:** SQL

---

## 🗃️ Database Tables

- **books**
  - `book_id` (INT, PRIMARY KEY)
  - `title` (VARCHAR)
  - `author` (VARCHAR)
  - `genre` (VARCHAR)
  - `availability_status` (ENUM: 'Available', 'Borrowed')

- **users**
  - `user_id` (INT, PRIMARY KEY)
  - `name` (VARCHAR)
  - `email` (VARCHAR)
  - `user_type` (ENUM: 'Student', 'Staff')

- **borrow_records**
  - `record_id` (INT, PRIMARY KEY)
  - `user_id` (FK)
  - `book_id` (FK)
  - `borrow_date` (DATE)
  - `return_date` (DATE)
  - `status` (ENUM: 'Borrowed', 'Returned')

---

## 🔧 How to Run

1. Open **MySQL Workbench**
2. Create a new schema or use an existing one
3. Open and run the SQL script (`library_system.sql`) to create tables
4. Use SQL queries to insert data and manage records

---

## 💡 Sample SQL Queries

```sql
-- View all available books
SELECT * FROM books WHERE availability_status = 'Available';

-- Insert a new book
INSERT INTO books (book_id, title, author, genre, availability_status)
VALUES (1, 'The Great Gatsby', 'F. Scott Fitzgerald', 'Fiction', 'Available');

-- Borrow a book (update status)
UPDATE books SET availability_status = 'Borrowed' WHERE book_id = 1;

-- View overdue books
SELECT * FROM borrow_records 
WHERE return_date < CURDATE() AND status = 'Borrowed';
