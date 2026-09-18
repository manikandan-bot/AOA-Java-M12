
# EX 2E Pattern Matching using KMP Algorithm.
## DATE:  05.08.26
## AIM:
To write a Java program for the following constraints.
Longest Palindromic Substring
Given a string s, return the longest palindromic substring in s.
using Manacher's Algorithm

## Algorithm
1. Start the program.  
2. Read the input string.  
3. Transform the string by inserting `#` between characters.  
4. Initialize the `center`, `radius`, and radii array.  
5. For each position:
   - Find its mirror index.
   - Use the mirror's radius to minimize expansion.
   - Expand outward while characters match.
   - Update the center and radius if the palindrome extends further.  
6. After filling the radii array, find the index with maximum radius.  
7. Convert the index in `sPrime` back to the original string position.  
8. Print the longest palindromic substring.  
9. End the program. 

## Program:
```
/*
Program to find the Longest Palindromic Substring using Manacher's Algorithm
Developed by: MANIKANDAN T
Register Number: 212224110037
*/
import java.util.Scanner;

public class Solution {
    public String longestPalindrome(String s) {
        // Step 1: Transform the string (insert '#')
        StringBuilder sPrime = new StringBuilder("#");
        for (char c : s.toCharArray()) {
            sPrime.append(c).append("#");
        }

        int n = sPrime.length();
        int[] palindromeRadii = new int[n];
        int center = 0;
        int radius = 0;

        // Step 2: Manacher's Algorithm to calculate radii
        for (int i = 0; i < n; i++) {
            int mirror = 2 * center - i;

            if (i < radius) {
                palindromeRadii[i] = Math.min(radius - i, palindromeRadii[mirror]);
            }

            while (
                i + 1 + palindromeRadii[i] < n &&
                i - 1 - palindromeRadii[i] >= 0 &&
                sPrime.charAt(i + 1 + palindromeRadii[i]) == sPrime.charAt(i - 1 - palindromeRadii[i])
            ) {
                palindromeRadii[i]++;
            }

            if (i + palindromeRadii[i] > radius) {
                center = i;
                radius = i + palindromeRadii[i];
            }
        }

        // Step 3: Find the longest palindrome
        int maxLength = 0;
        int centerIndex = 0;
        for (int i = 0; i < n; i++) {
            if (palindromeRadii[i] > maxLength) {
                maxLength = palindromeRadii[i];
                centerIndex = i;
            }
        }

        int startIndex = (centerIndex - maxLength) / 2;
        return s.substring(startIndex, startIndex + maxLength);
    }

    // Main method for user input
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String input = scanner.nextLine();

        Solution sol = new Solution();
        String result = sol.longestPalindrome(input);

        System.out.println("Longest Palindromic Substring: " + result);
        scanner.close();
    }
}
```

## Output:
<img width="770" height="191" alt="image" src="https://github.com/user-attachments/assets/1bb49832-6998-4cd8-8c72-082153c5ceee" />



## Result:
The program successfully implemented and the expected output is verified.
