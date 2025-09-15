# Mini_Atm_java
import java.util.Scanner;


class PIN {
    private int atmpin = 1911;


    public boolean verifyPin(int enteredPin) {
        return atmpin == enteredPin;
    }
}


public class Atm {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        double balance = 5000.00;
        int option;
        double amount;


        PIN pinObj = new PIN();

        System.out.print("Enter Your PIN: ");
        int pin = sc.nextInt();

        
        if (pinObj.verifyPin(pin)) {
            System.out.println("------ Welcome to Mini ATM ----------");

            do {
                System.out.println("1. Check Balance");
                System.out.println("2. Deposit Cash");
                System.out.println("3. Withdraw Cash");
                System.out.print("Enter the option: ");
                option = sc.nextInt();

                switch (option) {
                    case 1:
                        System.out.println("Account Balance is: " + balance);
                        break;

                    case 2:
                        System.out.print("Enter the amount to deposit: ");
                        amount = sc.nextDouble();
                        if (amount > 0) {
                            balance += amount;
                            System.out.println(amount + " deposited successfully.");
                        } else {
                            System.out.println("Invalid amount.");
                        }
                        break;

                    case 3:
                        System.out.print("Enter the amount to withdraw: ");
                        amount = sc.nextDouble();
                        if (amount > 0 && amount <= balance) {
                            balance -= amount;
                            System.out.println(amount + " withdrawn successfully.");
                        } else {
                            System.out.println("Insufficient balance or invalid amount.");
                        }
                        break;

                    default:
                        System.out.println("Invalid option. Please try again.");
                }

            } while (option != 3);

        } else {
            System.out.println("Incorrect PIN.");
        }        sc.close();
    }
}
