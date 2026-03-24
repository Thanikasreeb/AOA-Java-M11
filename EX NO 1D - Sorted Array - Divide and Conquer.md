
# EX 1D Sorted Array using Divide and Conquer Approach.

## AIM:
To write a Java program to for given constraints.
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).

## Algorithm
1. Start the program and import the Scanner class to take user input.
2.Read the sizes of the two sorted arrays and store their elements in nums1 and nums2.
3.Calculate the total length of both arrays combined.
4.Use the getMin() method to sequentially retrieve the smallest elements from both arrays until reaching the median position.
5.Display the median value of the merged sorted arrays as the final output.

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

public class Solution {
    private int p1 = 0, p2 = 0;
    private int getMin(int[] nums1, int[] nums2) {
        if (p1 < nums1.length && p2 < nums2.length) {
            return nums1[p1] < nums2[p2] ? nums1[p1++] : nums2[p2++];
        } else if (p1 < nums1.length) {
            return nums1[p1++];
        } else if (p2 < nums2.length) {
            return nums2[p2++];
        }
        return -1; // Should not reach here if input is valid
    }

    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int total=nums1.length+nums2.length;
        int mid=total/2;
        int pre=0,cur=0;
        for (int i=0;i<=mid;i++)
        {
            pre=cur;
            cur=getMin(nums1,nums2);
        }
        if (total%2==0)
        {
            return (pre+cur)/2.0;
        }
        else
        {
            return cur;
        }
    }

    // Main method with user input
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        // Input for nums1
        int m = sc.nextInt();
        int[] nums1 = new int[m];
        for (int i = 0; i < m; i++) {
            nums1[i] = sc.nextInt();
        }

        // Input for nums2
        int n = sc.nextInt();
        int[] nums2 = new int[n];
        for (int i = 0; i < n; i++) {
            nums2[i] = sc.nextInt();
        }

        // Find and display the median
        double median = sol.findMedianSortedArrays(nums1, nums2);
        System.out.println("Median of the two sorted arrays = " + median);
        
        sc.close();
    }
}
```

## Output:
<img width="971" height="344" alt="image" src="https://github.com/user-attachments/assets/4eca018f-b409-4a5e-8d91-a8518515cbb3" />



## Result:
The program successfully implemented and the expected output is verified.
