
# EX 1B Power of 2

## AIM:
To write a Java program to for given constraints.Given an integer n, return true if it is a power of two. Otherwise, return false.

An integer n is a power of two, if there exists an integer x such that n == 2x.

## Algorithm
1. Start the program.
2.Import the Scanner class.
3.Read an integer n from the user.
4.If n <= 0, print false.
5.Check (n & (n - 1)) == 0.
6.If true, print true, else print false.
7.Stop the program.

## Program:
```
/*
Program to implement Reverse a String
Developed by: Thanika Sree B 
Register Number: 212222100055 
*/
```
```
import java.util.Scanner;

public class Main {

    public static boolean isPowerOfTwo(int n) {
        if (n <= 0) {
            return false;
        }
        return (n & (n - 1)) == 0;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        boolean result = isPowerOfTwo(n);
        System.out.println(result);

        scanner.close();
    }
}
```
## Output:
<img width="399" height="215" alt="image" src="https://github.com/user-attachments/assets/9df68518-8b79-4928-9129-6055ba847f86" />

## Result:
The program successfully implemented and the expected output is verified.

## Result:
The program successfully implemented and the expected output is verified.
