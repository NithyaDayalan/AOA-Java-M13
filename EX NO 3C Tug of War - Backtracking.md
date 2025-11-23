# EX 3C Tug of War problem - Backtracking.

## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm:
1. Read the array of numbers from the user.
2. Calculate the total sum of the array and check if it is even; if odd, return false.
3. Set the target subset sum as total sum divided by 2.
4. Use a boolean array to track achievable subset sums using dynamic programming. 
5. Return true if the target subset sum is achievable; otherwise, return false.   

## Program:
```
Developed by: NITHYA D
Register Number: 212223240110
```
```
import java.util.Scanner;
public class Solution {
    public boolean canPartition(int[] nums) {
        if (nums.length == 0)
            return false;
        int totalSum = 0;
        for (int num : nums) {
            totalSum += num;
        }
        if (totalSum % 2 != 0)
            return false;
        int subSetSum = totalSum / 2;
        boolean[] dp = new boolean[subSetSum + 1];
        dp[0] = true;
        for (int curr : nums) {
            for (int j = subSetSum; j >= curr; j--) {
                dp[j] |= dp[j - curr];
            }
        }
        return dp[subSetSum];
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
    }
}

```

## Output:
<img width="441" height="229" alt="image" src="https://github.com/user-attachments/assets/c7029d72-e33b-41a4-899e-bec8a72b8b3f" />

## Result:
The program successfully implemented and the expected output is verified.
