# ATM
This program simulates the user experience of an ATM.
#include <iostream>
#include <string>
using namespace std;

int unique_acct = 12345; // this is the account number given to the user by the bank.

int unique_pin = 54321; // this is the PIN associated with the given account number.

int acct, pin; // acct stands for account number, PIN is the unique numbers associated with the account which is entered by the user

int choice, amount;// this holds the menu, and the user's monetary input

int acct_bal = 96580;// the user's account balance

int opinion;

int counter = 0;// counter for the bool authenticateUser

bool flag; // condition to control the authenticateUser()

bool authenticateUser();// function to check credentials

int showMenu();

void viewbalance(); // function for account balance

void withdrawCash(); // function for withdrawal

void depositCash();  // funtion for deposit

int main()
{
	
	while (counter < 3 && flag==false)// control loop to multiple trails of account info
	{
		cout << "\t Welcome to TigerOne Bank" << endl;
		cout << "\tPlease enter your account number: " << flush;
		cin >> acct;
		cout << "\tPlease enter your PIN: " << flush;
		cin >> pin;
		cout << endl;

		authenticateUser();
	}

	if (flag == false)
	{
		cout << "\nYou have entered the incorrect information too many times. System Timeout\n";
	}

	while (flag == true)
	{
		while (choice!=4)
		{
			showMenu();

			switch (choice)
			{
			case 1:
				viewbalance();
				break;
			case 2:
				withdrawCash();
				break;
			case 3:
				depositCash();
				break;
			case 4:
				cout << "Thank you for Banking with us. Goodbye!\n";
				break;
			default:
				cout << "Invalid selection, please try again...!\n";
			}
		} 
		
	}

	
	system("pause");
	return 0;
}

bool authenticateUser()
{
	

		if (acct == unique_acct && pin == unique_pin)
		{
			flag = true;
			return true;
			
		}
		else if (acct != unique_acct || pin != unique_pin)
		{
			cout << "The account number and PIN does not match any account in our system. Please try again\n";
			counter++;
		}
		else if (counter == 3)
		{

			flag = false;
			return false;

		}
		
	
}

int showMenu()
{
	cout << "\n\t1- View account balance\n";
	cout << "\t2- Withdrawal\n";
	cout << "\t3- Deposit\n";
	cout << "\t4- Exit\n";
	cout << "\nPlease enter your choice:\n";
	cin >> choice;
	cout << endl;

			
	return choice;

}

void viewbalance()
{
	
	cout << "You Selected View Balance\n";
}

void withdrawCash()
{
	cout << "You Selected Withdraw Cash\n";
}

void depositCash()
{
	cout << "You Selected Deposit Cash\n";
}
