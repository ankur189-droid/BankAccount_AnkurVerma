# BankAccount_AnkurVerma

import java.util.Scanner;

class Array_BankAccount {
    double balance;
    String[] accountArr = new String[5];

    double deposit(double amount){
        if(amount<0){
            System.out.println("Invalid input");
            return balance;
        }
        balance+=amount;
        return balance;
    }

    double withdraw(double amount){
        if(amount>balance){
            System.out.println("Insufficient Funds");
            return balance;
        }
        balance-=amount;
        return balance;
    }

    void displayAccountDetails(){
        System.out.println("Account Number: " + accountArr[4]);
        System.out.println("Account Holder Name: " + accountArr[0]);
        System.out.println("Email: " + accountArr[2]);
        System.out.println("Phone NUmber: " + accountArr[3]);
    }

    String updateContactDetails(String email, String phoneNumber){
        accountArr[2]=email;
        accountArr[3]=phoneNumber;
        return "Contact Updated";
    }
}


class Array_UserInterface extends Array_BankAccount{
    Scanner sc = new Scanner(System.in);

    void createAccount(){
        System.out.println("Enter account holder name: ");
        accountArr[0] = sc.nextLine();

        System.out.println("Enter initial deposit amount: ");
        accountArr[1] = sc.nextLine();

        System.out.println("Enter email address: ");
        accountArr[2] = sc.nextLine();

        System.out.println("Enter phone number");
        accountArr[3] = sc.nextLine();

        accountArr[4] = "100";
        System.out.println("Account created successfully! Account Number: " + accountArr[4]);
        accountArr[4]+=1;

    }

    void performDeposit(){
        System.out.println("Enter amount to deposit: ");
        double amount = sc.nextDouble();
        sc.nextLine();
        super.deposit(amount);
        System.out.println("Amount deposit successful");
        System.out.println("Available Balance: " + balance);
    }

    void performWithdrawal(){
        System.out.println("Enter amount to withdraw");
        double amount = sc.nextDouble();
        sc.nextLine();
        super.withdraw(amount);
        System.out.println("Amount withdrawal successful");
        System.out.println("Available balance: " + balance);
    }

    void showAccountDetails(){
        super.displayAccountDetails();
    }

    void updateContact(){
        System.out.println("Enter new email: ");
        String email = sc.nextLine();
        System.out.println("Enter new Phone Number: ");
        String phoneNumber = sc.nextLine();
        super.updateContactDetails(email,phoneNumber);
    }

    void mainMenu(){
        while(true){
            System.out.println("Welcome to the Banking Application :) ");
            System.out.println("1. Create a new account");
            System.out.println("2. Deposit Money");
            System.out.println("3. Withdraw Money");
            System.out.println("4. View Account Details");
            System.out.println("5. Update Contact Details");
            System.out.println("6. Exit");
            System.out.print("Enter your choice: ");
            int n = sc.nextInt();
            sc.nextLine();

            if(n==1){
                createAccount();
            }
            else if(n==2){
                performDeposit();
            }
            else if(n==3){
                performWithdrawal();
            }
            else if(n==4){
                showAccountDetails();
            }
            else if(n==5){
                updateContact();
            }
            else if(n==6){
                System.out.println("The End");
                break;
            }
            else{
                System.out.println("Invalid Choice");
            }
        }
    }
}

class Array_Account{
    public static void main(String[] args) {
        Array_UserInterface obj = new Array_UserInterface();
        obj.mainMenu();
    }
}
