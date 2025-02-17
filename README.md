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

- **Add Books**: Add a book to the library with its title, author, and availability status.
- **Issue Books**: Mark a book as issued if it's available.
- **Return Books**: Mark a book as returned, making it available again.
- **Display Book Details**: Show all details of the book.

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

- **Calculate Circle Area**: This feature allows the user to calculate the area of any circle by providing the radius.
- **Calculate Rectangle Area**: This feature enables the user to input the dimensions of a rectangle and get the corresponding area.
- **Calculate Triangle Area**: The feature calculates the area based on the three sides of the triangle.
   
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
# Day 4: Student Grade Management System(C++)

**Problem Statement:**
Design a program to calculate and display student details, including total marks and grades. The system should allow:
- Adding a student's name and marks for three subjects.
- Calculating the total marks.
- Assigning grades based on total marks:
   - A: 90–100
   - B: 75–89
   - C: 50–74
   - F: Below 50
---

## Features

- **Add Student Details**: Input the name and marks for three subjects of a student.
- **Calculate Total Marks**: Automatically compute the total marks by summing up marks of all subjects.
- **Assign Grades**: Assign grades `(A, B, C, F)` based on the total marks using predefined criteria.
   
---

## Code

```cpp
#include <iostream>
#include <vector>
#include <string>
using namespace std;

class Student {
private:
    string name;
    int marks[3]; 
    int totalMarks;
    char grade;
    void calculateGrade() {
        if (totalMarks >= 90) grade = 'A';
        else if (totalMarks >= 75) grade = 'B';
        else if (totalMarks >= 50) grade = 'C';
        else grade = 'F';
    }
public:
    Student(string studentName, int subject1, int subject2, int subject3) {
        name = studentName;
        marks[0] = subject1;
        marks[1] = subject2;
        marks[2] = subject3;
        totalMarks = marks[0] + marks[1] + marks[2];
        calculateGrade();
    }
    void displayDetails() const {
        cout << "Name: " << name << endl;
        cout << "Marks: " << marks[0] << ", " << marks[1] << ", " << marks[2] << endl;
        cout << "Total Marks: " << totalMarks << endl;
        cout << "Grade: " << grade << endl;
        cout << "-----------------------------" << endl;
    }
};

int main() {
    vector<Student> students;
    students.emplace_back("Rishabh", 95, 88, 92);
    students.emplace_back("Ayush", 78, 82, 74);
    students.emplace_back("Neelesh", 45, 52, 49);

    cout << "Student Details:\n";
    cout << "-----------------------------" << endl;
    for (const auto& student : students) {
        student.displayDetails();
    }
    return 0;
}

```

# Day 5: Employee Payroll System(C++)

**Problem Statement:**
Design a payroll system for employees in a company. The system should:

- Add employees with details like name, designation, and base salary.
- Allow different types of employees, such as full-time and part-time, with unique salary calculations.
   - Full-time: `baseSalary + allowances`
   - Part-time: `hourlyRate * hoursWorked`
---

## Features

- **Add Employee Details**: Store name, designation, and salary-related information.
- **Calculate Salary**: Compute salary using different methods for full-time and part-time employees.
- **Display Employee Details**: Show name, designation, and salary in a structured format.
   
---

## Code

```cpp
#include <iostream>
using namespace std;

class Employee {
protected:
    string name;
public:
    Employee(string empName) : name(empName) {}
    virtual double calculateSalary() const = 0; // Pure virtual function
    virtual void displayDetails() const {
        cout << "Name: " << name << endl;
    }
    virtual ~Employee() {}
};
class FullTimeEmployee : public Employee {
private:
    double baseSalary;
public:
    FullTimeEmployee(string empName, double salary)
        : Employee(empName), baseSalary(salary) {}

    double calculateSalary() const override {
        return baseSalary;
    }
    void displayDetails() const override {
        Employee::displayDetails();
        cout << "Salary: $" << calculateSalary() << endl;
    }
};
class PartTimeEmployee : public Employee {
private:
    double hourlyRate;
    int hoursWorked;
public:
    PartTimeEmployee(string empName, double rate, int hours)
        : Employee(empName), hourlyRate(rate), hoursWorked(hours) {}

    double calculateSalary() const override {
        return hourlyRate * hoursWorked;
    }
    void displayDetails() const override {
        Employee::displayDetails();
        cout << "Salary: $" << calculateSalary() << endl;
    }
};

int main() {
    FullTimeEmployee emp1("Rishabh", 5000);
    PartTimeEmployee emp2("Aman", 20, 80);

    cout << "Employee Payroll Details:\n------------------------" << endl;
    emp1.displayDetails();
    cout << "------------------------" << endl;
    emp2.displayDetails();
    
    return 0;
}

```

# Day 6: Bank Loan Eligibility System(C++)

**Problem Statement:**
Create a system to check loan eligibility for bank customers. The system should:

Allow adding customers with details like `name`, `income`, and `credit score`.
Check eligibility based on:
- Income >= 50,000
- Credit score >= 700
- Display eligible customers.
---

## Features

- **Add Customer Details**: Store customer name, income, and credit score.
- **Check Loan Eligibility**: Evaluate if income >= 50,000 and credit score >= 700.
- **Display Results**: Show customer details along with eligibility status.
   
---

## Code

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Customer {
private:
    string name;
    double income;
    int creditScore;

public:
    Customer(string custName, double custIncome, int custCreditScore)
        : name(custName), income(custIncome), creditScore(custCreditScore) {}

    bool isEligible() const {
        return (income >= 50000 && creditScore >= 700);
    }

    void displayDetails() const {
        cout << "Name: " << name << ", Income: $" << income << ", Credit Score: " << creditScore;
        if (isEligible())
            cout << " - Eligible for Loan" << endl;
        else
            cout << " - Not Eligible for Loan" << endl;
    }
};

int main() {
    vector<Customer> customers = {
        Customer("Rishabh", 60000, 750),
        Customer("Aryan", 40000, 680),
        Customer("Siddharth", 55000, 710)
    };

    cout << "Loan Eligibility Results:\n------------------------" << endl;
    for (const auto& customer : customers) {
        customer.displayDetails();
    }

    return 0;
}

```

# Day 7: Vehicle Rental System(C++)

**Problem Statement:**
Design a Vehicle Rental System that allows customers to rent different types of vehicles. The system should:

- Allow adding vehicles with details like `type`, `brand`, and `rental price`.
- Use inheritance to categorize vehicles as `Car` and `Bike` with unique rental calculations.
- Implement a method to calculate rental cost based on `days rented`.
---

## Features

- **Store Vehicle Details**: Maintain type, brand, and rental price information.
- **Calculate Rental Cost**: Compute total cost based on vehicle type and rental duration.
- **Display Rental Summary**: Show vehicle details and rental amount.
     
---

## Code
```cpp
#include <iostream>
using namespace std;

// Base class
class Vehicle {
protected:
    string brand;
    double rentalPricePerDay;
public:
    Vehicle(string vBrand, double price) : brand(vBrand), rentalPricePerDay(price) {}

    virtual double calculateRentalCost(int days) const = 0; // Pure virtual function

    virtual void displayDetails(int days) const {
        cout << "Brand: " << brand << ", Rental Cost for " << days << " days: $"
             << calculateRentalCost(days) << endl;
    }

    virtual ~Vehicle() {}
};

// Derived class for Cars
class Car : public Vehicle {
public:
    Car(string vBrand, double price) : Vehicle(vBrand, price) {}

    double calculateRentalCost(int days) const override {
        return days * rentalPricePerDay;
    }
};

// Derived class for Bikes
class Bike : public Vehicle {
public:
    Bike(string vBrand, double price) : Vehicle(vBrand, price) {}

    double calculateRentalCost(int days) const override {
        return days * rentalPricePerDay * 0.8; // 20% discount for bikes
    }
};

int main() {
    Car car("Toyota", 50);
    Bike bike("Yamaha", 30);

    cout << "Vehicle Rental Summary:\n------------------------" << endl;
    car.displayDetails(5); 
    bike.displayDetails(5); 

    return 0;
```

# Day 8: Smart Home Automation System(C++)

**Problem Statement:**
Design a Smart Home Automation System that manages multiple home devices. The system should:

- Support different types of devices like `Lights`, `Fans`, and `ACs`.
- Allow turning devices ON/OFF dynamically.
- Display the status of all connected devices.
---

## Features

- **Device Control**: Turn devices ON/OFF with a function call.
- **Device Status**: Display the state (ON/OFF) of all home devices.
- **Scalability**: Easily extendable to add more device types.
   
---

## Code
```cpp
#include <iostream>
#include <vector>
using namespace std;

class Device {
protected:
    string name;
    bool isOn;
public:
    Device(string dName) : name(dName), isOn(false) {}
    virtual void turnOn() {
        isOn = true;
        cout << name << " is now ON." << endl;
    }

    virtual void turnOff() {
        isOn = false;
        cout << name << " is now OFF." << endl;
    }

    virtual void displayStatus() const {
        cout << name << " Status: " << (isOn ? "ON" : "OFF") << endl;
    }

    virtual ~Device() {}
};

class Light : public Device {
public:
    Light(string dName) : Device(dName) {}
};

class Fan : public Device {
public:
    Fan(string dName) : Device(dName) {}
};

class AC : public Device {
public:
    AC(string dName) : Device(dName) {}
};

class SmartHome {
private:
    vector<Device*> devices;
public:
    void addDevice(Device* device) {
        devices.push_back(device);
    }

    void showStatus() {
        cout << "\nDevice Status:\n";
        for (const auto& device : devices) {
            device->displayStatus();
        }
    }

    ~SmartHome() {
        for (auto device : devices) {
            delete device;
        }
    }
};

int main() {
    SmartHome home;

    Device* light = new Light("Living Room Light");
    Device* fan = new Fan("Bedroom Fan");
    Device* ac = new AC("Office AC");

    home.addDevice(light);
    home.addDevice(fan);
    home.addDevice(ac);

    light->turnOn();
    fan->turnOff();
    ac->turnOn();

    home.showStatus();

    return 0;
}

```

# Day 9: Virtual Zoo Management System(C++)

**Problem Statement:**
Design a Virtual Zoo Management System that manages different types of animals. The system should:

- Support various animals like `Mammals`, `Birds`, and `Reptiles`.
- Allow animals to make sounds, eat, and display their habitat information.
- Keep track of all animals in the zoo and their unique behaviors.
---

## Features

- **Animal Interaction**: Each animal has a unique sound and eating habit.
- **Habitat Information**: Displays the natural habitat of each animal.
- **Extensibility**: Easily add more animal types in the future.
   
---

## Code 
```cpp
#include <iostream>
#include <vector>
using namespace std;

class Animal {
protected:
    string name;
    string habitat;
public:
    Animal(string n, string h) : name(n), habitat(h) {}

    virtual void makeSound() const = 0; // Pure virtual function
    virtual void eat() const = 0;

    void displayHabitat() const {
        cout << name << " lives in " << habitat << ".\n";
    }

    virtual ~Animal() {}
};

class Mammal : public Animal {
public:
    Mammal(string n) : Animal(n, "Land") {}

    void makeSound() const override {
        cout << name << " makes a growling sound!\n";
    }

    void eat() const override {
        cout << name << " eats plants and meat. \n";
    }
};

class Bird : public Animal {
public:
    Bird(string n) : Animal(n, "Sky and Trees") {}

    void makeSound() const override {
        cout << name << " chirps melodiously! \n";
    }

    void eat() const override {
        cout << name << " eats seeds and worms. \n";
    }
};

class Reptile : public Animal {
public:
    Reptile(string n) : Animal(n, "Swamps and Deserts") {}

    void makeSound() const override {
        cout << name << " hisses loudly! \n";
    }

    void eat() const override {
        cout << name << " eats insects and small animals. \n";
    }
};

class Zoo {
private:
    vector<Animal*> animals;
public:
    void addAnimal(Animal* animal) {
        animals.push_back(animal);
    }

    void showAllAnimals() const {
        cout << "\nAnimals in the Zoo:\n";
        for (const auto& animal : animals) {
            animal->displayHabitat();
            animal->makeSound();
            animal->eat();
            cout << "-----------------\n";
        }
    }

    ~Zoo() {
        for (auto animal : animals) {
            delete animal;
        }
    }
};

int main() {
    Zoo myZoo;

    Mammal* lion = new Mammal("Lion");
    Bird* parrot = new Bird("Parrot");
    Reptile* snake = new Reptile("Snake");

    myZoo.addAnimal(lion);
    myZoo.addAnimal(parrot);
    myZoo.addAnimal(snake);

    myZoo.showAllAnimals();

    return 0;
}

```

# Day 10: Online Quiz System(C++)

**Problem Statement:**
Design an Online Quiz System where users can take quizzes on different topics. The system should:

- Allow adding multiple questions with a question text and answer choices.
- Enable users to attempt a quiz and select answers.
- Evaluate and display the score at the end of the quiz.
---

## Features

- **Question Bank**: Store multiple quiz questions with options.
- **User Interaction**: Allow users to select answers and complete the quiz.
- **Automatic Scoring**: Evaluate responses and display the final score.
   
---

## Code
```cpp
#include <iostream>
#include <vector>
using namespace std;

class Question {
private:
    string text;
    vector<string> options;
    int correctAnswer;
public:
    Question(string txt, vector<string> opts, int correct) 
        : text(txt), options(opts), correctAnswer(correct) {}

    void display() const {
        cout << text << "\n";
        for (size_t i = 0; i < options.size(); ++i) {
            cout << i + 1 << ". " << options[i] << "\n";
        }
    }

    bool checkAnswer(int userAnswer) const {
        return userAnswer == correctAnswer;
    }
};

class Quiz {
private:
    vector<Question> questions;
    int score;
public:
    Quiz() : score(0) {}

    void addQuestion(const Question& q) {
        questions.push_back(q);
    }

    void start() {
        int userChoice;
        for (const auto& q : questions) {
            q.display();
            cout << "Your answer (1-" << q.options.size() << "): ";
            cin >> userChoice;
            if (q.checkAnswer(userChoice)) {
                cout << "Correct!\n";
                score++;
            } else {
                cout << "Wrong answer.\n";
            }
            cout << "---------------------\n";
        }
        cout << "Quiz Completed! Your Score: " << score << "/" << questions.size() << "\n";
    }
};

int main() {
    Quiz myQuiz;

    myQuiz.addQuestion(Question("What is the capital of France?", {"Paris", "London", "Rome", "Berlin"}, 1));
    myQuiz.addQuestion(Question("Who developed C++?", {"Dennis Ritchie", "Bjarne Stroustrup", "James Gosling", "Guido van Rossum"}, 2));
    myQuiz.addQuestion(Question("What is the value of Sin90°?", {"0", "undefined", "1", "1/2"}, 3));

    myQuiz.start();
```

# Day 11: Smart Parking System(C++)

**Problem Statement:**
Design a Smart Parking System that helps manage vehicle parking in a parking lot. The system should:

- Allow vehicles to enter and exit while tracking occupied spaces.
- Maintain vehicle details such as license plate and parking slot.
- Display available slots and a list of parked vehicles.
---

## Features

- **Vehicle Entry & Exit**: Register vehicles when they park and remove them upon exit.
- **Parking Slot Management**: Keep track of available and occupied slots.
- **Display Parked Vehicles**: Show vehicle details currently in the lot.
   
---

## Code
```cpp
#include <iostream>
#include <vector>
using namespace std;

class Vehicle {
private:
    string licensePlate;
    int slotNumber;
public:
    Vehicle(string plate, int slot) : licensePlate(plate), slotNumber(slot) {}

    void displayDetails() const {
        cout << "Vehicle License: " << licensePlate << ", Slot: " << slotNumber << "\n";
    }

    int getSlotNumber() const { return slotNumber; }
};

class ParkingLot {
private:
    vector<Vehicle> parkedVehicles;
    int totalSlots;
public:
    ParkingLot(int slots) : totalSlots(slots) {}

    void parkVehicle(string plate, int slot) {
        if (slot > totalSlots || slot < 1) {
            cout << "Invalid slot number!\n";
            return;
        }
        for (const auto& v : parkedVehicles) {
            if (v.getSlotNumber() == slot) {
                cout << "Slot " << slot << " is already occupied!\n";
                return;
            }
        }
        parkedVehicles.push_back(Vehicle(plate, slot));
        cout << "Vehicle with license " << plate << " parked at Slot " << slot << ".\n";
    }

    void removeVehicle(int slot) {
        for (auto it = parkedVehicles.begin(); it != parkedVehicles.end(); ++it) {
            if (it->getSlotNumber() == slot) {
                cout << "Vehicle at Slot " << slot << " removed.\n";
                parkedVehicles.erase(it);
                return;
            }
        }
        cout << "No vehicle found at Slot " << slot << ".\n";
    }

    void displayParkedVehicles() const {
        cout << "\nCurrently Parked Vehicles:\n";
        for (const auto& v : parkedVehicles) {
            v.displayDetails();
        }
    }
};

int main() {
    ParkingLot lot(5); // Creating a parking lot with 5 slots

    lot.parkVehicle("ABC123", 1);
    lot.parkVehicle("XYZ789", 3);
    lot.parkVehicle("LMN456", 5);

    lot.displayParkedVehicles();

    lot.removeVehicle(3);
    lot.displayParkedVehicles();

    return 0;
}

```

# Day 12: Online Food Ordering System(C++)

**Problem Statement:**
Design an Online Food Ordering System that allows customers to order food from a restaurant. The system should:

- Allow users to add food items to their cart.
- Calculate the total bill after order placement.
- Display order details, including items and cost.
---

## Features

- **Add Items**: Customers can add food items to their cart.
- **Bill Calculation**: Computes the total price of the order.
- **Order Summary**: Displays ordered items with total cost.
   
---

## Code
```cpp
#include <iostream>
#include <vector>
using namespace std;

class FoodItem {
private:
    string name;
    double price;
public:
    FoodItem(string n, double p) : name(n), price(p) {}

    string getName() const { return name; }
    double getPrice() const { return price; }

    void displayItem() const {
        cout << name << " - $" << price << endl;
    }
};

class Order {
private:
    vector<FoodItem> items;
public:
    void addItem(const FoodItem& item) {
        items.push_back(item);
        cout << item.getName() << " added to your order!\n";
    }

    void displayOrder() const {
        if (items.empty()) {
            cout << "Your cart is empty!\n";
            return;
        }
        cout << "\nOrder Summary:\n";
        double total = 0;
        for (const auto& item : items) {
            item.displayItem();
            total += item.getPrice();
        }
        cout << "Total Bill: $" << total << "\n";
    }
};

int main() {
    Order myOrder;

    FoodItem burger("Cheese Burger", 5.99);
    FoodItem pizza("Margherita Pizza", 8.49);
    FoodItem drink("Coke", 1.99);

    myOrder.addItem(burger);
    myOrder.addItem(pizza);
    myOrder.addItem(drink);

    myOrder.displayOrder();

    return 0;
}

```

# Day 13: Ride Sharing System(C++)

**Problem Statement:**
Design a Ride Sharing System that allows users to book rides with available drivers. The system should:

- Allow users to request a ride with their location.
- Assign an available driver to the user.
- Display ride details, including driver name and estimated fare.
---

## Features

- **Ride Booking**: Users can request rides.
- **Driver Assignment**: Matches users with available drivers.
- **Fare Calculation**: Computes ride fare based on distance.
   
---

## Code
```cpp
#include <iostream>
#include <vector>
using namespace std;

class Driver {
private:
    string name;
    bool available;
    double ratePerKm;
public:
    Driver(string n, double rate) : name(n), ratePerKm(rate), available(true) {}

    bool isAvailable() const { return available; }
    string getName() const { return name; }
    double getRate() const { return ratePerKm; }

    void assignRide() { available = false; }
    void completeRide() { available = true; }

    void displayDriver() const {
        cout << "Driver: " << name << " | Rate: $" << ratePerKm << " per km\n";
    }
};

class Ride {
private:
    double distance;
    Driver* assignedDriver;
public:
    Ride(double dist, Driver* driver) : distance(dist), assignedDriver(driver) {
        if (assignedDriver) assignedDriver->assignRide();
    }

    void completeRide() {
        if (assignedDriver) assignedDriver->completeRide();
    }

    void displayRideDetails() const {
        if (!assignedDriver) {
            cout << "No available driver for this ride.\n";
            return;
        }
        cout << "\nRide Details:\n";
        cout << "Driver: " << assignedDriver->getName() << "\n";
        cout << "Distance: " << distance << " km\n";
        cout << "Total Fare: $" << (distance * assignedDriver->getRate()) << "\n";
    }
};

class RideSharingApp {
private:
    vector<Driver> drivers;
public:
    void addDriver(const Driver& driver) {
        drivers.push_back(driver);
    }

    Driver* findAvailableDriver() {
        for (auto& driver : drivers) {
            if (driver.isAvailable()) return &driver;
        }
        return nullptr;
    }

    void requestRide(double distance) {
        Driver* driver = findAvailableDriver();
        Ride ride(distance, driver);
        ride.displayRideDetails();
        ride.completeRide();
    }

    void displayDrivers() const {
        cout << "\nAvailable Drivers:\n";
        for (const auto& driver : drivers) {
            if (driver.isAvailable()) driver.displayDriver();
        }
    }
};

int main() {
    RideSharingApp app;

    app.addDriver(Driver("John Doe", 2.5));
    app.addDriver(Driver("Emma Smith", 3.0));
    app.addDriver(Driver("Mike Johnson", 2.8));

    app.displayDrivers();

    app.requestRide(10.5); 

    app.displayDrivers();

    return 0;
}

```

# Day 14: Scientific Calculator(C++)

**Problem Statement:**
Create a program that performs different mathematical operations using OOP. The calculator should:

- Support basic operations like addition, subtraction, multiplication, and division.
- Include advanced operations like exponentiation and square root.
- Allow calculations on different data types (integers, floating-point numbers).
---

## Features

- **Basic operations**: Addition, subtraction, multiplication, and division.
- **Advanced functions**: Power and square root calculations.
- **Handles different data types**: Works with integers and floating-point numbers.
   
---

## Code
```cpp
#include <iostream>
#include <cmath>
using namespace std;

class Calculator {
protected:
    double num1, num2;
public:
    Calculator(double a, double b = 0) : num1(a), num2(b) {}
    virtual double compute() const = 0; // Pure virtual function
};

class Addition : public Calculator {
public:
    Addition(double a, double b) : Calculator(a, b) {}
    double compute() const override {
        return num1 + num2;
    }
};

class Subtraction : public Calculator {
public:
    Subtraction(double a, double b) : Calculator(a, b) {}
    double compute() const override {
        return num1 - num2;
    }
};

class Multiplication : public Calculator {
public:
    Multiplication(double a, double b) : Calculator(a, b) {}
    double compute() const override {
        return num1 * num2;
    }
};

class Division : public Calculator {
public:
    Division(double a, double b) : Calculator(a, b) {}
    double compute() const override {
        if (num2 == 0) {
            cout << "Error: Division by zero!\n";
            return 0;
        }
        return num1 / num2;
    }
};

class Power : public Calculator {
public:
    Power(double base, double exp) : Calculator(base, exp) {}
    double compute() const override {
        return pow(num1, num2);
    }
};

class SquareRoot : public Calculator {
public:
    SquareRoot(double a) : Calculator(a) {}
    double compute() const override {
        if (num1 < 0) {
            cout << "Error: Square root of negative number!\n";
            return 0;
        }
        return sqrt(num1);
    }
};

int main() {
    Addition add(10, 5);
    Subtraction sub(10, 5);
    Multiplication mul(10, 5);
    Division div(10, 5);
    Power powCalc(2, 3);
    SquareRoot sqrtCalc(16);

    cout << "Addition: " << add.compute() << endl;
    cout << "Subtraction: " << sub.compute() << endl;
    cout << "Multiplication: " << mul.compute() << endl;
    cout << "Division: " << div.compute() << endl;
    cout << "Power: " << powCalc.compute() << endl;
    cout << "Square Root: " << sqrtCalc.compute() << endl;

    return 0;
}

```

# Day 15: Digital Wallet System(C++)

**Problem Statement:**
Design a Digital Wallet System that allows users to manage their funds securely. The system should:

- Allow users to add money to their wallet.
- Enable making payments while ensuring sufficient balance.
- Display the current wallet balance.
---

## Features

- **Secure Transactions**: Ensures balance doesn't go negative.
- **Fund Management**: Add money and track spending.
- **Balance Display**: Shows available funds in real time.
   
---

## Code
```cpp 
#include <iostream>
using namespace std;

class DigitalWallet {
private:
    string owner;
    double balance;
public:
    DigitalWallet(string name, double initialBalance = 0) : owner(name), balance(initialBalance) {}

    void addMoney(double amount) {
        if (amount > 0) {
            balance += amount;
            cout << owner << " added $" << amount << " to the wallet.\n";
        } else {
            cout << "Invalid amount!\n";
        }
    }

    void makePayment(double amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
            cout << owner << " made a payment of $" << amount << ".\n";
        } else {
            cout << "Insufficient balance or invalid amount!\n";
        }
    }

    void showBalance() const {
        cout << owner << "'s Wallet Balance: $" << balance << endl;
    }
};

int main() {
    DigitalWallet wallet("Alice", 100);

    wallet.showBalance();
    wallet.addMoney(50);
    wallet.makePayment(30);
    wallet.showBalance();
    wallet.makePayment(150); // Should show insufficient balance

    return 0;
}

```

# Day 16: Movie Ticket Booking System(C++)

**Problem Statement:**
Design an Online Movie Ticket Booking System that allows users to book tickets for different movies. The system should:

- Allow users to select a movie and book tickets.
- Ensure seat availability before confirming a booking.
- Display booking details including movie name and number of seats booked.
---

## Features

- **Seat Management**: Ensures tickets are available before booking.
- **User-Friendly Booking**: Allows users to select a movie and number of seats.
- **Booking Confirmation**: Displays the movie name and seats booked.
   
---

## Code
```cpp
#include <iostream>
#include <vector>
using namespace std;

class Movie {
private:
    string name;
    int availableSeats;
public:
    Movie(string n, int seats) : name(n), availableSeats(seats) {}

    bool bookTickets(int seats) {
        if (seats > 0 && seats <= availableSeats) {
            availableSeats -= seats;
            cout << "Booking successful! " << seats << " tickets booked for " << name << ".\n";
            return true;
        } else {
            cout << "Insufficient seats available for " << name << ".\n";
            return false;
        }
    }
    void showDetails() const {
        cout << "Movie: " << name << " | Available Seats: " << availableSeats << endl;
    }
};

int main() {
 
    Movie movie1("Avengers: Endgame", 50);
    Movie movie2("Inception", 30);

    movie1.showDetails();
    movie2.showDetails();

    movie1.bookTickets(5);
    movie2.bookTickets(35); 

    movie1.showDetails();
    movie2.showDetails();

    return 0;
}

```

# Day 17: Virtual Pet Simulation(C++)

**Problem Statement:**
Create a Virtual Pet Simulation where a pet can eat, sleep, play, and show happiness levels. The system should:

- Allow users to feed, play, and rest with their pet.
- Track the hunger, energy, and happiness levels dynamically.
- Display the pet’s current mood based on interactions.
---

## Features

- **Interactive Actions**: Feed, play, and rest to maintain pet health.
- **Dynamic Mood Tracking**: Happiness changes based on user interaction.
- **Life Simulation**: Pet behavior updates in real-time.
   
---

## Code
```cpp
#include <iostream>
using namespace std;

class VirtualPet {
private:
    string name;
    int hunger;
    int energy;
    int happiness;

public:
    VirtualPet(string petName) : name(petName), hunger(50), energy(50), happiness(50) {}

    void feed() {
        hunger -= 10;
        happiness += 5;
        if (hunger < 0) hunger = 0;
        cout << name << " is eating... Hunger decreased!\n";
    }

    void play() {
        if (energy > 10) {
            happiness += 10;
            energy -= 15;
            cout << name << " is playing! Happiness increased!\n";
        } else {
            cout << name << " is too tired to play. Try resting.\n";
        }
    }

    void rest() {
        energy += 20;
        hunger += 10;
        if (energy > 100) energy = 100;
        cout << name << " is resting... Energy restored!\n";
    }

    void showStatus() const {
        cout << "\n--- " << name << "'s Status ---\n";
        cout << "Hunger: " << hunger << "/100\n";
        cout << "Energy: " << energy << "/100\n";
        cout << "Happiness: " << happiness << "/100\n";
    }
};

int main() {
    VirtualPet pet("Buddy");

    pet.showStatus();
    pet.feed();
    pet.play();
    pet.rest();
    pet.showStatus();

    return 0;
}

```
