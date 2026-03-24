
# EX 1E Integer Multiplication using Divide and Conquer Approach(Strassen’s algorithm).
## AIM:
To write a Java program to for given constraints.
You are given two square matrices A and B of size n × n (where n is a power of 2). Your task is to compute their matrix product using Strassen’s Matrix Multiplication algorithm and return the resulting matrix.

Unlike traditional matrix multiplication which takes O(n3)O(n^3)O(n3) time, Strassen’s algorithm improves this by reducing the number of recursive multiplications from 8 to 7, achieving approximately O(n2.81)O(n^{2.81})O(n2.81) complexity.
## Algorithm
1. Start the program and import the Scanner class to take user input.
2.Read the matrix size n and input the two square matrices A and B.
3.Divide both matrices into four equal submatrices recursively.
4.Use Strassen’s algorithm to compute the seven matrix products and combine them to form the resulting matrix.
5.Display the final multiplied matrix as the output.   

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

public class StrassenMatrix {

    // Add two matrices
    static int[][] add(int[][] A, int[][] B) {
        int n = A.length;
        int[][] C = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                C[i][j] = A[i][j] + B[i][j];
        return C;
    }

    // Subtract matrix B from A
    static int[][] subtract(int[][] A, int[][] B) {
        int n = A.length;
        int[][] C = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                C[i][j] = A[i][j] - B[i][j];
        return C;
    }

    // Strassen recursive multiplication
    static int[][] strassen(int[][] A, int[][] B) {
        int n = A.length;
        int[][] c = new int[n][n];
        if(n==1)
        {
            c[0][0]=A[0][0]*B[0][0];
            return c;
        }
        int newsize = n/2;
        int[][] A11 = new int[newsize][newsize];
        int[][] A12 = new int[newsize][newsize];
        int[][] A21 = new int[newsize][newsize];
        int[][] A22 = new int[newsize][newsize];
        int[][] B11 = new int[newsize][newsize];
        int[][] B12 = new int[newsize][newsize];
        int[][] B21 = new int[newsize][newsize];
        int[][] B22 = new int[newsize][newsize];
        
        for(int i=0;i<newsize;i++)
        {
            for (int j=0;j<newsize;j++)
            {
                A11[i][j]=A[i][j];
                A12[i][j]=A[i][j+newsize];
                A21[i][j]=A[i+newsize][j];
                A22[i][j]=A[i+newsize][j+newsize];
                B11[i][j]=B[i][j];
                B12[i][j]=B[i][j+newsize];
                B21[i][j]=B[i+newsize][j];
                B22[i][j]=B[i+newsize][j+newsize];
            }
        }
        int[][] m1 = strassen(add(A11,A22),add(B11,B22));
        int[][] m2 = strassen(add(A21,A22),B11);
        int[][] m3 = strassen(A11,subtract(B12,B22));
        int[][] m4 = strassen(A22,subtract(B21,B11));
        int[][] m5 = strassen(add(A11,A12),B22);
        int[][] m6 = strassen(subtract(A21,A11),add(B11,B12));
        int[][] m7 = strassen(subtract(A12,A22),add(B21,B22));
        
        int[][] c11 = add(subtract(add(m1,m4),m5),m7);
        int[][] c12 = add(m3,m5);
        int[][] c21 = add(m2,m4);
        int[][] c22 = add(subtract(add(m1,m3),m2),m6);
        
        for(int i=0;i<newsize;i++)
        {
            for(int j=0;j<newsize;j++)
            {
                c[i][j]=c11[i][j];
                c[i][j+newsize]=c12[i][j];
                c[i+newsize][j]=c21[i][j];
                c[i+newsize][j+newsize]=c22[i][j];
            }
        }
        return c;
        }

    // Function to print matrix
    static void printMatrix(int[][] matrix) {
        for (int[] row : matrix) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    // Main method to get input and run Strassen multiplication
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read size of matrix
        //System.out.print("Enter matrix size (power of 2): ");
        int n = sc.nextInt();

        int[][] A = new int[n][n];
        int[][] B = new int[n][n];

        // Input Matrix A
        //System.out.println("Enter elements of matrix A:");
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                A[i][j] = sc.nextInt();

        // Input Matrix B
        //System.out.println("Enter elements of matrix B:");
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                B[i][j] = sc.nextInt();

        // Multiply using Strassen
        int[][] result = strassen(A, B);

        // Output the result matrix
        System.out.println("Result of Strassen Matrix Multiplication:");
        printMatrix(result);
    }
}
```

## Output:

<img width="965" height="865" alt="image" src="https://github.com/user-attachments/assets/287a3eb9-fb00-4b5a-b39f-0b5a7a4dc325" />


## Result:
The program successfully implemented and the expected output is verified.
