# Library System - Software Engineering
## Overview
This project is a **C++ console-based library management system** developed as part of a **software engineering coursework project**. Thy system design for **librarian/staff use only**, not for custumers, and focuses on managing members and book-lending operations through a command-line interface.

The application loads book data from a **CSV file**, stores library members and books in memory, and allows the librarian to perform core task such as:
- adding a new member
- issuing a book
- returning a book
- displaying books borrowed by a member
- calculating overdue fines

The coursework brief defies a **3-day borrowing period** and a fine of **1£ per day overdue**, and the implementation follows that approach by assigning a due date three days from the issue time and calculating the delay on return.

---
## Key Purpose
The purpose of this project is to demonstrate how a **small real-world management system** can be design using core **software engineering and object-oriented programming principles** in C++.

The project models the main entities in a library domain, separates responsibility across classes, and uses file-based data input to simulate a real library catalogue. It also shows how to approach a problem from a requirements brief, where the written problem description is translated into a working implementation.

---
## Problem Explained

Libraries need a simple and effective way to manage:
- available books
- registered members
- borrowing and returning operations
- overdue penalties

This project simulates a small library system where the books are loaded from a dataset, members can be registered, books can be issued and returned, and fines are calculated for late returns.

This project includes a simple data set file, **`library_books.csv`**, which is used for the implementation and testing purposes.

---

## Project Explained

When the program startsm it ask the librarian to enter a file name for the book dataset**(in our scenario is hardcoded)**. It then opens that CSV file, reads the records, extracts the book information, and creates in-memory book objects.

After that, it prompts for librarian verification and displays a menu for the main actions.

The systems supports the following functionality:

- **Add a member**
- **Issue a book to a member**
- **Return a book**
- **Display all borrowed books for a member**
- **Exit the program**

The system also enforces the coursework borrowing rules:

- books are borrowed for **3 days**
- overdue books are charged at **1£ per day**

---
## Key Methods and Techinques

### Object-Oriented Design

The project is structured using multiple classes, each with a clear responsibility:

- `Person` stores shared personal details such as name, addres, and email
- `Member` inherits from `Person` and adds a member ID and borrowed book list
- `Book` stores book details, due date, and borrowed information
- `Librarian` inherits from `Person` and manages the main library operations

This class-based structure demonstrates:

- inheritance
- encapsulation
- modular design
- separation of concerns

---
### Input Validation with RegEX

The code uses **regular expressions** to validate different kinds of usre input, including:

- librarian/staff ID
- librarian/staff name
- member name
- adrress
- email

This helps prevent invalid or badly formated input from being stored in the system.

---
### Borrowing and Returning Logic

When a book is issued:

- the book is linked to a specific member
- a due date is assigned as **3 days from the issue date**
- the borrowed book is added to the member's list

When a book is returned:

- the borrower is removed from the book
- the book is removed from the member's borrowed list
- the system checks whether the book is overdue
- a fine is calculated if necessary

---
### Fine Calculation

The fine calculation is based on the difference between the current data and the stored due date.

If book is overdue, the system applies the corsework rule: 

```
1£ per day overdue
```

Those are ones of the main business rules implemented in the project.
