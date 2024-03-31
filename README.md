# assignment1





import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner myObj = new Scanner(System.in);
        System.out.println("Choose the number of parameters to pass to SUM:");
        System.out.println("1. Single parameter\n2. Two parameters");
        int choice;
        boolean validChoice = false;
        while (!validChoice) {
            try {
                choice = myObj.nextInt();
                switch (choice) {
                    case 1:
                        System.out.println("Choose the data type of the parameter to pass to SUM:");
                        System.out.println("1. int\n2. double");
                        int select;
                        boolean validSelect = false;
                        while (!validSelect) {
                            try {
                                select = myObj.nextInt();
                                if (select == 1) {
                                    System.out.println("Please enter an integer:");
                                    int input;
                                    boolean validInput = false;
                                    while (!validInput) {
                                        try {
                                            input = myObj.nextInt();
                                            if (input >= 0) {
                                                int sumRes = sum(input);
                                                System.out.println("Sum result: " + sumRes);
                                                validInput = true;
                                            } else {
                                                System.out.println("Invalid input. Please enter a non-negative integer.");
                                            }
                                        } catch (Exception e) {
                                            System.out.println("Invalid input. Please enter a valid integer.");
                                            myObj.next(); 
                                        }
                                    }
                                    validSelect = true;
                                } else if (select == 2) {
                                    System.out.println("Please enter a double:");
                                    double input;
                                    boolean validInput = false;
                                    while (!validInput) {
                                        try {
                                            input = myObj.nextDouble();
                                            if (input >= 0) {
                                                int sumRes = sum((int) input);
                                                System.out.println("Sum result: " + sumRes);
                                                validInput = true;
                                            } else {
                                                System.out.println("Invalid input. Please enter a non-negative double.");
                                            }
                                        } catch (Exception e) {
                                            System.out.println("Invalid input. Please enter a valid double.");
                                            myObj.next(); // Clear the invalid input
                                        }
                                    }
                                    validSelect = true;
                                } else {
                                    System.out.println("Invalid Choice, please enter a valid choice 1 or 2");
                                }
                            } catch (Exception e) {
                                System.out.println("Invalid input. Please enter a valid choice.");
                                myObj.next(); // Clear the invalid input
                            }
                        }
                        validChoice = true;
                        break;
                    case 2:
                        System.out.println("Please enter the two integers to pass to SUM:");
                        int min, max;
                        boolean validInput = false;
                        while (!validInput) {
                            try {
                                min = myObj.nextInt();
                                max = myObj.nextInt();
                                if (max >= min) {
                                    int sumRes = sum(min, max);
                                    System.out.println("Sum result: " + sumRes);
                                    validInput = true;
                                } else {
                                    System.out.println("Invalid input. The second number should be greater than or equal to the first number.");
                                }
                            } catch (Exception e) {
                                System.out.println("Invalid input. Please enter valid integers.");
                                myObj.next(); // Clear the invalid input
                            }
                        }
                        validChoice = true;
                        break;
                    default:
                        System.out.println("Invalid choice, please enter a valid choice 1 or 2");
                }
            } catch (Exception e) {
                System.out.println("Invalid input. Please enter a valid choice.");
                myObj.next(); // Clear the invalid input
            }
        }
        myObj.close(); 
    }
    public static int sum(int k) {
        if (k > 0) {
            return k + sum(k - 1);
        } else {
            return 0;
        }
    }
    public static int sum(double k) {
        if (k > 0) {
            return (int) Math.round(k + sum(k - 1));
        } else {
            return 0;
        }
    }
    public static int sum(int start, int end) {
        if (end >= start) {
            int sum = 0;
            for (int i = start; i <= end; i++) {
                sum += i;
            }
            return sum;
        } else {
            return -1; 
        }
    }
}
