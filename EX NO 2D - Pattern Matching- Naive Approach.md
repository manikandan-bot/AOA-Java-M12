
# EX 2D Pattern Matching using Naive Approach.
## DATE: 03/08/26
## AIM:
To write a Java program to for given constraints.
Given text string with length n and a pattern with length m, the task is to prints all occurrences of pattern in text.
Note: You may assume that n > m.

Examples: 

Input:  text = "THIS IS A TEST TEXT", pattern = "TEST"
Output: Pattern found at index 10

Input:  text =  "AABAACAADAABAABA", pattern = "AABA"
Output: Pattern found at index 0, Pattern found at index 9, Pattern found at index 12
## Algorithm
1. Start the program.  
2. Read the input text.  
3. Read the pattern to search.  
4. Loop through the text from index `0` to `n - m`.  
5. For each index, check if the next `m` characters match the pattern.  
6. If all characters match, print the index.  
7. Stop.  

## Program:
```java
/*
Program to implement Naive Pattern Search
Developed by: MANIKANDAN T
Register Number: 212224110037
*/
import java.util.Scanner;

public class NaivePatternSearch {
    static void search(String text, String pattern){
        int n = text.length();
        int m = pattern.length();
        for(int i = 0; i <= n - m; i++){
            int j;
            for(j = 0; j < m; j++){
                if(text.charAt(i + j) != pattern.charAt(j)){
                    break;
                }
            }
            if(j == m){
                System.out.println("Pattern found at index " + i);
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String text = scanner.nextLine();
        String pattern = scanner.nextLine();

        search(text, pattern);

        scanner.close();
    }
}
```

## Output:
<img width="728" height="239" alt="image" src="https://github.com/user-attachments/assets/c38213c2-57b2-44ae-8cae-b37987f567db" />


## Result:
The program successfully implemented and the expected output is verified.
