
# EX 2C Job Sequencing using Greedy Approach
## DATE: 01/08/26
## AIM:
To write a Java program to for given constraints.
Given an integer array nums and an integer k, return the number of pairs (i, j) where i < j such that |nums[i] - nums[j]| == k.

The value of |x| is defined as:

x if x >= 0.
-x if x < 0.You're given N jobs, each with:

A unique jobId

A deadline (by which it must be completed)

A profit (earned only if completed on or before the deadline)

Each job:

Takes exactly 1 unit of time

Only one job can be done at a time

Your goal is to maximize total profit while completing the maximum number of jobs possible within their deadlines.

## Algorithm
1. Start the program.  
2. Read the number of jobs `n`.  
3. For each job, read:  
   - Job ID  
   - Deadline  
   - Profit  
4. Sort all jobs in decreasing order of profit.  
5. Find the **maximum deadline** among all jobs.  
6. Create a slot array initialized with `-1` (indicating empty slots).  
7. For each job:  
   - Try to place it in the latest available slot before its deadline.  
   - If a slot is found:  
     - Schedule the job.  
     - Increase job count and total profit.  
8. Print the number of scheduled jobs and total profit.  
9. Stop the program.  

## Program:
```java
/*
Program to implement Job Scheduling
Developed by: MANIKANDAN T
Register Number: 212224110037
*/

import java.util.*;

public class JobScheduling {

    static class Job {
        int id, deadline, profit;

        Job(int id, int deadline, int profit) {
            this.id = id;
            this.deadline = deadline;
            this.profit = profit;
        }
    }

    public static int[] jobScheduling(Job[] jobs, int n) {
        // Step 1: Sort jobs by profit in descending order
        Arrays.sort(jobs, (a, b) -> b.profit - a.profit);

        // Step 2: Find the maximum deadline to size the schedule array
        int maxDeadline = 0;
        for (Job job : jobs) {
            maxDeadline = Math.max(maxDeadline, job.deadline);
        }

        // Step 3: Initialize time slots (-1 means empty slot)
        int[] slot = new int[maxDeadline + 1];
        Arrays.fill(slot, -1);

        int countJobs = 0;
        int totalProfit = 0;

        // Step 4: Schedule jobs greedily
        for (Job job : jobs) {
            for (int j = job.deadline; j > 0; j--) {
                if (slot[j] == -1) {
                    slot[j] = job.id;
                    countJobs++;
                    totalProfit += job.profit;
                    break;
                }
            }
        }

        return new int[] {countJobs, totalProfit};
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        Job[] jobs = new Job[n];

        for (int i = 0; i < n; i++) {
            int id = sc.nextInt();
            int deadline = sc.nextInt();
            int profit = sc.nextInt();
            jobs[i] = new Job(id, deadline, profit);
        }

        int[] result = jobScheduling(jobs, n);
        System.out.println(result[0] + " " + result[1]);
    }
}
```

## Output:
<img width="400" height="373" alt="image" src="https://github.com/user-attachments/assets/e5a5f138-04bd-4241-badb-c4f9fef97293" />

## Result:
The program successfully implemented and the expected output is verified.
