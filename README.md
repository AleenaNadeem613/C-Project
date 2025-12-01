#include<iostream>
using namespace std;

void checkBalance(int balance) {
    cout << "\n----------------------------------\n";
    cout << "          Current Balance        \n";
    cout << "----------------------------------\n";
    cout << "     Your Balance: " << balance << " PKR\n";
    cout << "----------------------------------\n";
}

void withdrawMoney(int &balance)
{
    int amount;
    cout << "\n----------------------------------\n";
    cout << "          Withdraw Money         \n";
    cout << "----------------------------------\n";
    cout << "Enter amount: ";
    cin >> amount;

    if (amount > 0 && amount <= balance) {
        balance -= amount;
        cout << "\n Withdrawal Successful!\n";
        cout << "Remaining Balance: " << balance << " PKR\n";
    } else {
        cout << "\n Insufficient Amount!\n";
    }
}

void depositMoney(int &balance) {
    int amount;
    cout << "\n----------------------------------\n";
    cout << "            Deposit Money          \n";
    cout << "----------------------------------\n";
    cout << "Enter amount: ";
    cin >> amount;
    
    if (amount > 0) {
        balance += amount;
        cout << "\n Deposit Successful!\n";
        cout << "Updated Balance: " << balance << " PKR\n";
    } else {
        cout << "\n Invalid Amount!\n";
    }
}

int main() {
    int pin = 5642, Attempts = 0, EnteredPin, balance = 200000, choice;

    cout << "\n====================================\n";
    cout << "              WELCOME TO ATM          \n";
    cout << "====================================\n";

    while (Attempts < 3) {
        cout << "\nEnter PIN: ";
        cin >> EnteredPin;
        
        if (EnteredPin == pin) {
            cout << "\n Login Successful!\n";
            break;
        } else {
            Attempts++;
            cout << " Incorrect PIN! Attempts left: " << (3 - Attempts) << "\n";
        }
    }

    if (Attempts == 3) {
    cout << "\n====================================\n";
    cout << "   Too many attempts. CARD BLOCKED\n";
    cout << "====================================\n";

    string userAnswer;
    cout << "\nTo unblock your card, answer the security question.\n";
    cout << "Enter your date of birth (DDMMYYYY): ";
    cin >> userAnswer;

    if(userAnswer == "01061969") {  // your chosen answer
        cout << "\n Correct answer! Your card is unblocked.\n";
        Attempts = 0; // Reset attempts

        // Ask PIN again from start
        while (Attempts < 3) {
            int EnteredPin;
            cout << "\nEnter PIN: ";
            cin >> EnteredPin;

            if (EnteredPin == pin) {
                cout << "\nLogin Successful!\n";
                break;  // exit loop to ATM menu
            } else {
                Attempts++;
                cout << "Incorrect PIN! Attempts left: " << (3 - Attempts) << "\n";
            }
        }

        if (Attempts == 3) {
            cout << "\n Too many attempts again. Card remains blocked.\n";
            return 0;
        }

    } else {
        cout << "\n Wrong answer. Card remains blocked.\n";
        return 0;
    }
}

    do {
        cout << "\n\n---------- ATM MAIN MENU ----------\n";
        cout << "1.  Check Balance\n";
        cout << "2.  Withdraw Money\n";
        cout << "3.  Deposit Money\n";
        cout << "4.  Exit\n";
        cout << "-----------------------------------\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch(choice) {
            case 1: checkBalance(balance); break;
            case 2: withdrawMoney(balance); break;
            case 3: depositMoney(balance); break;
            case 4: Exit; break;
                cout << "\nThank you for using the ATM! \n\n";  
                break;
            default:
                cout << "\n Invalid Choice! Try Again.\n";
        }

    } while (choice != 4);

    return 0;
}



