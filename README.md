# Library Management System

## Description

This is a console-based Library Management System implemented in C++. It allows users to manage books and student records, handle book issuing and depositing, and perform various administrative tasks. The data is stored persistently in binary files (`book.dat` and `student.dat`).

## Features

The system offers the following features:

**Book Management:**

- Add new books with details like book number, name, and author.
- Display a list of all available books.
- Display details of a specific book by its number.
- Modify the details of an existing book.
- Delete books from the library records.
- Search for books by their title or author's name.

**Student Management:**

- Register new students with details like admission number and name.
- Display a list of all registered students.
- Display details of a specific student by their admission number.
- Modify the details of an existing student.
- Delete student records.

**Library Operations:**

- Issue books to students.
  - Checks if the student has already issued a book.
  - Updates student record with the issued book number.
- Deposit books returned by students.
  - Calculates a fine if a book is returned after 15 days (Rs. 1 per day).
  - Updates student record to reflect the book return.

**User Interface:**

- A console-based menu-driven interface.
- Separate menus for general library operations and administrator-specific tasks.
- Screen clearing (`clrscr()`) and cursor positioning (`gotoxy()`) for a cleaner console display (Windows-specific).

**Data Persistence:**

- Book records are stored in `book.dat`.
- Student records are stored in `student.dat`.
- Data is appended to files, and records are modified or deleted by reading, processing, and rewriting to temporary files, then renaming.

## Technologies Used

- **Programming Language:** C++
- **Core Libraries:**
  - `iostream` (for console input/output)
  - `fstream` (for file input/output operations)
  - `iomanip` (for I/O manipulators like `setw`)
  - `string.h` (for string manipulation functions like `strcmpi`, `strcpy`, `strstr`)
  - `stdlib.h` (for general utilities like `system`, `exit`)
  - `conio.h` (for console I/O functions like `getch`, `getche` - typically Windows-specific)
  - `windows.h` (for `gotoxy` implementation and `system("cls")` - Windows-specific)

## How to Compile and Run

### Prerequisites

- A C++ compiler that supports C++ standards used in the code (e.g., g++, MinGW for Windows, Visual Studio C++ Compiler).
- The code uses Windows-specific headers (`conio.h`, `windows.h`), so it's best compiled and run on a Windows environment or an environment that supports these (like MinGW).

### Compilation

Open a terminal or command prompt, navigate to the directory containing `lms.cpp`, and use a command similar to the following (using g++ as an example):

```sh
g++ lms.cpp -o lms
```

This will create an executable file named `lms.exe` (on Windows) or `lms` (on Linux/macOS if compatible).

### Running

Execute the compiled program from the terminal:

```sh
./lms
```

or, on Windows:

```sh
lms.exe
```

The program will start, and you can interact with it through the console menus. The data files (`book.dat` and `student.dat`) will be created in the same directory as the executable if they don't already exist.

## File Structure

- `lms.cpp`: The main C++ source code file containing all class definitions, function implementations, and the main program logic.
- `book.dat`: A binary file used to store records of all books in the library.
- `student.dat`: A binary file used to store records of all registered students.
- `temp.dat` / `Temp.dat`: Temporary binary files used during the deletion process for books and students. These files are renamed to `book.dat` or `student.dat` after the deletion operation.

## Core Classes

### `book` Class

Manages book-related data and operations.

- **Attributes:**
  - `bno[6]`: Character array to store the book number.
  - `bname[50]`: Character array to store the book name.
  - `aname[20]`: Character array to store the author's name.
- **Key Methods:**
  - `createbook()`: Prompts the user for book details and creates a new book record.
  - `showbook()`: Displays the details of a book.
  - `modifybook()`: Allows modification of an existing book's name and author.
  - `retbno()`: Returns the book number.
  - `retbname()`: Returns the book name.
  - `retaname()`: Returns the author's name.
  - `report()`: Displays book details in a formatted row for lists.

### `student` Class

Manages student-related data and operations.

- **Attributes:**
  - `admno[6]`: Character array to store the student's admission number.
  - `name[20]`: Character array to store the student's name.
  - `stbno[6]`: Character array to store the book number issued to the student.
  - `token`: An integer flag (0 if no book is issued, 1 if a book is issued).
- **Key Methods:**
  - `createstudent()`: Prompts the user for student details and creates a new student record.
  - `showstudent()`: Displays the details of a student, including any issued book.
  - `modifystudent()`: Allows modification of an existing student's name.
  - `retadmno()`: Returns the student's admission number.
  - `retstbno()`: Returns the book number issued to the student.
  - `rettoken()`: Returns the token status (book issued or not).
  - `addtoken()`: Sets the token to 1 (book issued).
  - `resettoken()`: Sets the token to 0 (book returned/not issued).
  - `getstbno(char t[])`: Sets the student's issued book number.
  - `report()`: Displays student details in a formatted row for lists.

## Menu Options

### Main Menu

1.  **BOOK ISSUE**: Allows issuing a book to a student.
2.  **BOOK DEPOSIT**: Allows depositing a book returned by a student.
3.  **ADMINISTRATOR MENU**: Navigates to the administrator-specific menu.
4.  **EXIT**: Terminates the application.

### Administrator Menu

1.  **CREATE STUDENT RECORD**: Add a new student.
2.  **DISPLAY ALL STUDENT RECORDS**: List all registered students.
3.  **DISPLAY SPECIFIC STUDENT RECORD**: Search and display a particular student.
4.  **MODIFY STUDENT RECORD**: Update a student's details.
5.  **DELETE STUDENT RECORD**: Remove a student from the records.
6.  **CREATE BOOK**: Add a new book.
7.  **DISPLAY ALL BOOKS**: List all books (Note: in-code menu text says "CREATE ALL BOOKS" which seems to be a typo and should be "DISPLAY ALL BOOKS" as per functionality).
8.  **DISPLAY SPECIFIC BOOK**: Search and display a particular book.
9.  **MODIFY BOOK RECORD**: Update a book's details.
10. **DELETE BOOK RECORD**: Remove a book from the records.
11. **SEARCH BOOKS**: Search for books by title or author.
12. **BACK TO MAIN MENU**: Returns to the main menu.


