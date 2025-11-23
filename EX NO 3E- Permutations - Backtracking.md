# EX 3E Generate Permutations using Backtracking  Approach.
## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
For example:

## Algorithm:
1. Read the input array from the user. 
2. Initialize a list to store all permutations.
3. Use backtracking to build permutations by adding numbers not already in the current list.
4. When a permutation reaches the length of the array, add it to the result list. 
5. Print all generated permutations.  

## Program:
```
Developed by: NITHYA D
Register Number: 212223240110
```
```
import java.util.*;

public class Solution {

    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        backtrack(new ArrayList<>(), ans, nums);
        return ans;
    }

    public void backtrack(List<Integer> curr, List<List<Integer>> ans, int[] nums) {
        if (curr.size() == nums.length) {
            ans.add(new ArrayList<>(curr));
            return;
        }

        for (int num : nums) {
            if (!curr.contains(num)) {
                curr.add(num);
                backtrack(curr, ans, nums);
                curr.remove(curr.size() - 1);
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Accept input in the form: nums = [1,2,3]
        //System.out.print("Input: ");
        String inputLine = scanner.nextLine().trim();

        // Extract the array part from the string
        inputLine = inputLine.replaceAll(".*\\[|\\].*", ""); // get content inside brackets
        String[] parts = inputLine.split(",");

        int[] nums = new int[parts.length];
        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }

        // Generate permutations
        Solution solution = new Solution();
        List<List<Integer>> permutations = solution.permute(nums);

        // Print output
        System.out.println(permutations);
        scanner.close();
    }
}
```

## Output:
<img width="1267" height="184" alt="image" src="https://github.com/user-attachments/assets/0896f1b9-c7f8-45a2-971b-fadbe7fac1a0" />

## Result:
The program successfully implemented and the expected output is verified.
