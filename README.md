**📚 Library Management System – PLP Academy SQL Project**

##  Project Description

This project is a **Library Management System** built entirely using **MySQL**. 
It models key components of a real-world library including books, authors, members, loans, and staff. 
The database is designed to store and manage data about book lending, membership, and staff roles with proper relational integrity.

###  Core Entities:
- **Authors** – Stores author details.
- **Books** – Stores book records, each linked to an author.
- **Members** – Registered library users who borrow books.
- **Loans** – Tracks borrowing activity.
- **Staff** – Library personnel data.

The schema supports one-to-many relationships like:
- One author writes many books.
- One member can have many loans.
- One book can be loaned many times.

##  Run / Set Up

1. **Download MySQL** (if not installed):
   - [MySQL Downloads](https://dev.mysql.com/downloads/)

2. **Import the SQL file:**

   - Using MySQL Workbench:
     - Open MySQL Workbench.
     - Create a new schema (e.g., `library_db`).
     - Click *File > Open SQL Script* and select `library_management_system.sql`.
     - Run the script to create the tables.

   - Or via terminal:

     mysql -u _your_username_ -p library_db < library_management_system.sql


3. # Explore the tables and run queries!

# 🗂️ Files Included

- **`library_management_system.sql`** – Contains all `CREATE TABLE` statements with constraints and relationships.
- **`README.md`** – Project documentation.
- `ERD.png` – Visual ERD showing the structure and relationships (optional).


Or you can generate it live at [dbdiagram.io](https://dbdiagram.io) using the code below.

  Table Authors {
  AuthorID int [pk, increment]
  Name varchar
  Bio text
}

Table Books {
  BookID int [pk, increment]
  Title varchar
  ISBN varchar [unique]
  Genre varchar
  AuthorID int [ref: > Authors.AuthorID]
}

Table Members {
  MemberID int [pk, increment]
  Name varchar
  Email varchar [unique]
  JoinDate date
}

Table Staff {
  StaffID int [pk, increment]
  Name varchar
  Role varchar
  Email varchar [unique]
}

Table Loans {
  LoanID int [pk, increment]
  BookID int [ref: > Books.BookID]
  MemberID int [ref: > Members.MemberID]
  IssueDate date
  DueDate date
  ReturnDate date
}

