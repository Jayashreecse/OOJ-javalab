import java.util.Scanner;

class Account {
    private String customerName;
    private String accountNumber;
    protected double balance;

    public Account(String customerName, String accountNumber) {
        this.customerName = customerName;
        this.accountNumber = accountNumber;
        this.balance = 0.0;
    }

    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposited amount: " + amount);
    }

    public void displayBalance() {
        System.out.println("Balance amount: " + balance);
    }

    public void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
            System.out.println("Withdraw amount: " + amount);
        } else {
            System.out.println("Insufficient balance for withdrawal!");
        }
    }

    protected double getBalance() {
        return balance;
    }
}

class SavAcct extends Account {
    private double interestRate;

    public SavAcct(String customerName, String accountNumber, double interestRate) {
        super(customerName, accountNumber);
        this.interestRate = interestRate;
    }

    public void computeAndDepositInterest() {
        double currentBalance = getBalance();
        double interest = currentBalance * interestRate / 100;
        deposit(interest);
        System.out.println("Interest deposited: " + interest);
    }
}

class CurAcct extends Account {
    private double minimumBalance;
    private double serviceCharge;

    public CurAcct(String customerName, String accountNumber, double minimumBalance, double serviceCharge) {
        super(customerName, accountNumber);
        this.minimumBalance = minimumBalance;
        this.serviceCharge = serviceCharge;
    }

    public void withdraw(double amount) {
        if (getBalance() - amount < minimumBalance) {
            System.out.println("Service charge imposed: " + serviceCharge);
            deposit(-serviceCharge);
            System.out.println("Insufficient balance.");
        } else {
            super.withdraw(amount);
        }
    }
}

public class Bank {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

   
        System.out.println("Enter customer name for Savings Account:");
        String savingsCustomerName = scanner.nextLine();
        System.out.println("Enter account number for Savings Account:");
        String savingsAccountNumber = scanner.nextLine();
        System.out.println("Enter interest rate for Savings Account:");
        double interestRate = scanner.nextDouble();

        SavAcct savingsAccount = new SavAcct(savingsCustomerName, savingsAccountNumber, interestRate);
        savingsAccount.deposit(1000);
        savingsAccount.computeAndDepositInterest();
        savingsAccount.displayBalance();

       
        System.out.println("Enter amount to withdraw from Savings Account:");
        double withdrawAmount = scanner.nextDouble();
        savingsAccount.withdraw(withdrawAmount);
        savingsAccount.displayBalance();


        scanner.nextLine();
        System.out.println("Enter customer name for Current Account:");
        String currentCustomerName = scanner.nextLine();
        System.out.println("Enter account number for Current Account:");
        String currentAccountNumber = scanner.nextLine();
        System.out.println("Enter minimum balance for Current Account:");
        double minimumBalance = scanner.nextDouble();
        System.out.println("Enter service charge for Current Account:");
        double serviceCharge = scanner.nextDouble();

        CurAcct currentAccount = new CurAcct(currentCustomerName, currentAccountNumber, minimumBalance, serviceCharge);
        currentAccount.deposit(2000);
        currentAccount.displayBalance();
       
        System.out.println("Enter amount to withdraw from Current Account:");
        double currentWithdrawAmount = scanner.nextDouble();
        currentAccount.withdraw(currentWithdrawAmount);
        currentAccount.displayBalance();

       
        System.out.println("Enter amount to withdraw from Current Account (may incur service charge):");
        currentWithdrawAmount = scanner.nextDouble();
        currentAccount.withdraw(currentWithdrawAmount);
        currentAccount.displayBalance();

        scanner.close();
    }
}
if want to use normal method to call methods
public class Bank {
    public static void main(String[] args) {
        // Creating a Savings Account with hardcoded values
        String savingsCustomerName = "Alice";
        String savingsAccountNumber = "S12345";
        double interestRate = 5.0;  // 5% interest rate

        // Create a Savings Account
        SavAcct savingsAccount = new SavAcct(savingsCustomerName, savingsAccountNumber, interestRate);

        // Deposit money into Savings Account
        savingsAccount.deposit(1000);  // Deposit 1000 into Savings Account
        savingsAccount.computeAndDepositInterest();  // Compute and deposit interest
        savingsAccount.displayBalance();  // Display balance after interest

        // Withdraw money from Savings Account
        double withdrawAmount = 500;
        savingsAccount.withdraw(withdrawAmount);  // Withdraw 500 from Savings Account
        savingsAccount.displayBalance();  // Display remaining balance

        // Creating a Current Account with hardcoded values
        String currentCustomerName = "Bob";
        String currentAccountNumber = "C67890";
        double minimumBalance = 1000.0;
        double serviceCharge = 50.0;

        // Create a Current Account
        CurAcct currentAccount = new CurAcct(currentCustomerName, currentAccountNumber, minimumBalance, serviceCharge);

        // Deposit money into Current Account
        currentAccount.deposit(2000);  // Deposit 2000 into Current Account
        currentAccount.displayBalance();  // Display balance after deposit

        // Withdraw money from Current Account (should be allowed)
        double currentWithdrawAmount = 1500;
        currentAccount.withdraw(currentWithdrawAmount);  // Withdraw 1500 from Current Account
        currentAccount.displayBalance();  // Display remaining balance

        // Withdraw money from Current Account that triggers service charge (balance below minimum)
        currentWithdrawAmount = 700;
        currentAccount.withdraw(currentWithdrawAmount);  // Withdraw 700 from Current Account (below minimum balance)
        currentAccount.displayBalance();  // Display remaining balance
    }
}
