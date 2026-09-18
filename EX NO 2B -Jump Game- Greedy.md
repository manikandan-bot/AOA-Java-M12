
# EX 2B Jump Game using Greedy Algorithm.
## DATE: 31.07.26
## AIM:
To write a Java program to for given constraints.
You are given an array of integers. Each number represents the maximum number of steps you can jump forward from that position.

You start from the first element (index 0). 
Write a program to find the minimum number of jumps required to reach the last index of the array.

If it is not possible to reach the end, return -1.
## Algorithm
1. Start the program.  
2. Read the number of elements `n`.  
3. Read the elements of array `nums[]`.  
4. If array length is `1`, return `0`.  
5. If the first element is `0`, return `-1` (cannot move anywhere).  
6. Initialize `jump = 0`, `currEnd = 0`, `farthest = 0`.  
7. Traverse the array:  
   - Update `farthest = max(farthest, i + nums[i])`.  
   - If `i == currEnd`, increment jump and set `currEnd = farthest`.  
   - If `currEnd >= n - 1`, break (destination reachable).  
   - If no progress can be made, return `-1`.  
8. Print the number of jumps.  
9. End the program.
   
## Program:
```java
/*
Program to implement Jump Game
Developed by: MANIKANDAN T
Register Number: 212224110037
*/
import java.util.Scanner;

public class MinJumpToEnd {

    // Function to return minimum jumps to reach end
    public static int minimumJumps(int[] nums) {
        if(nums.length <= 1) return 0;
        if(nums[0] == 0) return -1;

        int jump = 0;
        int currEnd = 0;
        int farthest = 0;

        for(int i = 0; i < nums.length; i++) {
            farthest = Math.max(farthest, i + nums[i]);

            if(i == currEnd) {
                jump++;
                currEnd = farthest;
            }

            if(currEnd >= nums.length - 1) {
                break;
            }

            if(currEnd == i) return -1;
        }
        return currEnd >= nums.length - 1 ? jump : -1;
    }

    // Main method to handle input and output
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(); // Number of elements
        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        System.out.println("Minimum jumps to reach last index: " + minimumJumps(nums));
    }
}
```

## Output:
<img width="864" height="274" alt="image" src="https://github.com/user-attachments/assets/907dd4ea-f7a6-4a4c-9830-8c6f7e887aa2" />

## Result:
The program successfully computes and prints the minimum number of jumps required to reach the last index using a greedy approach.

## Result:
The program successfully implemented and the expected output is verified.
