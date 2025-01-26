# Day 1: Bank Account Management System (C++)

**Problem Statement:**
Create a C++ program using OOP to manage a bank account. Implement the following functionalities:
Deposit money into the account.
Withdraw money from the account (ensure the balance doesn't go negative).
Display the account balance.
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
