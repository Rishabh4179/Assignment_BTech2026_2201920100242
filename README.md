# Day 1: Bank Account Management System (C++)

**Problem Statement:**
Create a C++ program using OOP to manage a bank account. Implement the following functionalities:
1. Deposit money into the account.
2. Withdraw money from the account (ensure the balance doesn't go negative).
3. Display the account balance.
   
Use a class BankAccount to encapsulate the account details and methods.

---

## Features

- **Deposit Money**: Add funds to the account balance using the `deposit()` method.
- **Withdraw Money**: Deduct funds from the account using the `withdraw()` method (ensuring no overdrafts).
- **Display Balance**: Show the current balance and account holder details using the `displayBalance()` method.

---

## Code

```cpp
#include <iostream>
using namespace std;

class BankAccount {
private:
    string accountHolder;
    double balance;

public:
    BankAccount(string name, double initialBalance) : accountHolder(name), balance(initialBalance) {
        cout << "Account created for " << accountHolder << " with an initial balance of $" << initialBalance << endl;
    }
    void deposit(double amount) {
        balance += amount;
        cout << "Deposited: $" << amount << ". New Balance: $" << balance << endl;
    }
    void withdraw(double amount) {
        if (amount > balance) {
            cout << "Insufficient funds. Current Balance: $" << balance << endl;
        } else {
            balance -= amount;
            cout << "Withdrew: $" << amount << ". Remaining Balance: $" << balance << endl;
        }
    }
    void displayBalance() const {
        cout << "Account Holder: " << accountHolder << ", Balance: $" << balance << endl;
    }
};

int main() {
    BankAccount account("Rishabh Sharma", 1000.0);
    account.deposit(500.0);        
    account.withdraw(300.0);      
    account.displayBalance();     
    account.withdraw(1500.0);    
    account.deposit(1000.0);      
    account.displayBalance();    
    return 0;
}
``` 

# Day 2: Library Management System (C++)

**Problem Statement:**
Design a class-based Library Management System in C++ that allows users to perform the following actions:
1. Add a book to the library.
2. Search for a book by title.
3. Display all books available in the library.
   
Each book should have the following properties:

- A unique ID (integer)
- Title (string)
- Author (string)
- Price (float)

---

## Features

1. **Add Books**: Add a book to the library with its title, author, and availability status.
2. **Issue Books**: Mark a book as issued if it's available.
3. **Return Books**: Mark a book as returned, making it available again.
4. **Display Book Details**: Show all details of the book.

---

## Code

```cpp
#include <iostream>
#include <string>
using namespace std;

class Book {
private:
    string title;
    string author;
    bool isIssued;

public:
    Book(string bookTitle, string bookAuthor) : title(bookTitle), author(bookAuthor), isIssued(false) {
        cout << "Book added: " << title << " by " << author << endl;
    }
    void issueBook() {
        if (isIssued) {
            cout << "Book \"" << title << "\" is already issued." << endl;
        } else {
            isIssued = true;
            cout << "Book \"" << title << "\" has been issued." << endl;
        }
    }
    void returnBook() {
        if (!isIssued) {
            cout << "Book \"" << title << "\" is not issued, so it cannot be returned." << endl;
        } else {
            isIssued = false;
            cout << "Book \"" << title << "\" has been returned." << endl;
        }
    }
    void displayDetails() const {
        cout << "Title: " << title << ", Author: " << author << ", Status: " << (isIssued ? "Issued" : "Available") << endl;
    }
};

int main() {
    Book book1("The Great Gatsby", "F. Scott Fitzgerald");
    Book book2("1984", "George Orwell");
    Book book3("To Kill a Mockingbird", "Harper Lee");
    book1.displayDetails();
    book2.displayDetails();
    book1.issueBook();
    book1.issueBook();  
    book1.returnBook();
    book1.returnBook(); 
    book1.displayDetails();
    book2.issueBook();
    book3.issueBook();
    book2.displayDetails();
    book3.displayDetails();
    return 0;
}
```

# Day 3: Shape Area and Perimeter Calculator(C++)

**Problem Statement:**
Create a C++ program using Object-Oriented Programming (OOP) to calculate the area and perimeter of different shapes. The program should implement the following functionalities:
1. Circle: Calculate the area and perimeter using the radius.
2. Rectangle: Calculate the area and perimeter using the length and width.
3. Triangle: Calculate the area and perimeter using the lengths of the three sides.
   
Use a base class `Shape` and derived classes (`Circle`, `Rectangle`, `Triangle`) to encapsulate the details and methods for each shape.

---

## Features

1. **Calculate Circle Area**: This feature allows the user to calculate the area of any circle by providing the radius.
2. **Calculate Rectangle Area**: This feature enables the user to input the dimensions of a rectangle and get the corresponding area.
3. **Calculate Triangle Area**: The feature calculates the area based on the three sides of the triangle.
   
---

## Code

```cpp
#include <iostream>
#include <cmath>
using namespace std;

// Base class
class Shape {
public:
    virtual double calculateArea() const { return 0; }
    virtual double calculatePerimeter() const { return 0; }
    virtual ~Shape() {}
};

// Circle class
class Circle : public Shape {
private:
    double radius;
public:
    Circle(double r) : radius(r) {}
    double calculateArea() const override { return 3.14 * radius * radius; }
    double calculatePerimeter() const override { return 2 * 3.14 * radius; }
};

// Rectangle class
class Rectangle : public Shape {
private:
    double length, width;
public:
    Rectangle(double l, double w) : length(l), width(w) {}
    double calculateArea() const override { return length * width; }
    double calculatePerimeter() const override { return 2 * (length + width); }
};

// Triangle class
class Triangle : public Shape {
private:
    double side1, side2, side3;
public:
    Triangle(double a, double b, double c) : side1(a), side2(b), side3(c) {}
    double calculateArea() const override {
        double s = (side1 + side2 + side3) / 2;
        return sqrt(s * (s - side1) * (s - side2) * (s - side3));
    }
    double calculatePerimeter() const override {
        return side1 + side2 + side3;
    }
};

int main() {
    Circle circle(5.0);
    Rectangle rectangle(4.0, 6.0);
    Triangle triangle(3.0, 4.0, 5.0);

    cout << "Circle:\n";
    cout << "Area: " << circle.calculateArea() << endl;
    cout << "Perimeter: " << circle.calculatePerimeter() << endl;

    cout << "\nRectangle:\n";
    cout << "Area: " << rectangle.calculateArea() << endl;
    cout << "Perimeter: " << rectangle.calculatePerimeter() << endl;

    cout << "\nTriangle:\n";
    cout << "Area: " << triangle.calculateArea() << endl;
    cout << "Perimeter: " << triangle.calculatePerimeter() << endl;

    return 0;
}
```



















