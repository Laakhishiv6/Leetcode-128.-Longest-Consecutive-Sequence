# Leetcode-128.-Longest-Consecutive-Sequence
# Description
Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.
# Solution
In the given question we have been given an array nums in which we have to find the length of the longest consecutive sequence .

The longest consecutive elements sequence [100,4,200,1,3,2] is [1, 2, 3, 4]. Therefore its length is 4.

Example 1:

Input: nums = [100,4,200,1,3,2]

Output: 4

Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.

Example 2:

Input: nums = [0,3,7,2,5,8,4,6,0,1]

Output: 9

Example 3:

Input: nums = [1,0,1,2]

Output: 3

We can create a set to store the non duplicate values of each of the numbers.

We can solve this question by finding out from where the sequence starts first . A sequence will be starting from the number which doesnt have any left neighbours . 

For example in [100,4,200,1,3,2] 1 doesnt have any left neighbour but 2 , 3 ,4 has left neighbours as 1,2,3 . In a similar way 100 and 200 are part of different sequences.

Once we find out the starting point we have to check whether there is its right neighbour in the set or not.

# Algorithm
1. Create a set numsSet which stores nums.
2. Create a variable longest , which returns the longest length of the consecutive seq.
3. Loop through each number in numsSet.
4. Check if there exists any left neighbour(n-1) for the given number , if it doesn't then calculate the length of the sequence it follows.
5. Check if there exists right neighbours of the consecutive sequences .
6. Return the longest length found.
# Code
class Solution:

    def longestConsecutive(self, nums: List[int]) -> int:
        
        numsSet=set(nums)
        longest=0

        for n in numsSet:
            if n-1 not in numsSet:
                length=0
                while (n+length) in numsSet:
                    length+=1
                longest=max(longest,length)
        return longest
# Complexity
Time: O(n)

Each number is checked at most twice (once in if, once in while).

Space: O(n)

For storing numbers in the set.
