LeetCode Java Solutions – Searching, Sorting & Two Pointers
 Overview:

This repository contains 7 LeetCode solutions implemented in Java. The problems focus on important Data Structures and Algorithm concepts such as Binary Search, Two Pointers, Sorting, Binary Search on Answer, and Greedy validation.

The purpose of this collection is to improve problem-solving skills, understand efficient algorithms, analyze time and space complexity, and maintain a structured record of LeetCode practice.

| Solution    | LeetCode | Problem                          | Difficulty | Main Concept                 |
| ----------- | -------: | -------------------------------- | ---------- | ---------------------------- |
| Solution-01 |      367 | Valid Perfect Square             | Easy       | Binary Search                |
| Solution-02 |      374 | Guess Number Higher or Lower     | Easy       | Binary Search                |
| Solution-03 |       75 | Sort Colors                      | Medium     | Two Pointers                 |
| Solution-04 |      410 | Split Array Largest Sum          | Hard       | Binary Search on Answer      |
| Solution-05 |      704 | Binary Search                    | Easy       | Binary Search                |
| Solution-06 |      719 | Find K-th Smallest Pair Distance | Hard       | Binary Search + Two Pointers |
| Solution-07 |      977 | Squares of a Sorted Array        | Easy       | Two Pointers                 |

🔹 Solution 01 – LeetCode 367
Valid Perfect Square
Problem Description

Given a positive integer num, determine whether num is a perfect square.

A perfect square is an integer that can be represented as the product of an integer with itself.

Examples:

16 = 4 × 4
25 = 5 × 5
36 = 6 × 6
49 = 7 x 7

The solution should determine the result without directly using a square-root function.

Approach

Binary Search is used to find whether there exists an integer mid such that:

mid × mid = num

The search range starts from 1 and continues up to num.

For every middle value:

If mid * mid == num, the number is a perfect square.
If mid * mid < num, search the right half.
If mid * mid > num, search the left half.
Algorithm
Set left = 1.
Set right = num.
Calculate the middle value.
Compare mid * mid with num.
Adjust the search range.
Return true if an exact square is found.
Otherwise return false.
Example
Input:
num = 16

Search:
1 → 8 → 4

4 × 4 = 16

Output:
true
Complexity
Time Complexity: O(log n)
Space Complexity: O(1)
File
Solution-01-367.java
🔹 Solution 02 – LeetCode 374
Guess Number Higher or Lower
Problem Description

A number is selected from the range:

1 to n

The goal is to find the selected number using the provided guess() function.

The function provides three possible results:

-1 → guessed number is higher than the target
 1 → guessed number is lower than the target
 0 → guessed number is correct
Approach:

Binary Search is used because the possible numbers form a sorted search space.

Instead of checking every number sequentially, the search space is divided into two parts at every step.

Algorithm
Set left = 1.
Set right = n.
Calculate the middle number.
Call guess(mid).
If the result is 0, return mid.
If the result indicates that the guess is too high, move right.
Otherwise move left.
Continue until the number is found.
Example
Input:
n = 10
Target = 6

Possible search:
1 2 3 4 5 6 7 8 9 10

mid = 5
Target is higher

Search right side

mid = 8
Target is lower

Search left side

mid = 6
Found
Complexity
Time Complexity: O(log n)
Space Complexity: O(1)
File
Solution-02-374.java
🔹 Solution 03 – LeetCode 75
Sort Colors
Problem Description

Given an array containing only:

0, 1, 2

sort the array in-place so that the same colors are grouped together.

The required order is:

0 → 1 → 2
Approach

The Dutch National Flag Algorithm is used.

Three pointers are maintained:

low
mid
high

Their purpose is:

low  → position where 0 should be placed
mid  → current element
high → position where 2 should be placed
Algorithm

Initialize:

low = 0
mid = 0
high = n - 1
While mid <= high:
If the current value is 0, swap it with low.
If the current value is 1, move mid.
If the current value is 2, swap it with high.
Continue until all elements are processed.
Example
Input:
[2,0,2,1,1,0]

Output:
[0,0,1,1,2,2]
Complexity
Time Complexity: O(n)
Space Complexity: O(1)
File
Solution-03-75.java
🔹 Solution 04 – LeetCode 410
Split Array Largest Sum
Problem Description

Given an integer array nums and an integer k, split the array into k non-empty continuous subarrays.

The objective is to minimize the largest sum among the resulting subarrays.

Approach

This problem is solved using Binary Search on Answer.

The answer cannot be smaller than the largest element:

minimum answer = max(nums)

The answer cannot be greater than the total sum:

maximum answer = sum(nums)

Therefore, binary search can be performed between these two values.

Example
Input:
nums = [7,2,5,10,8]
k = 2

One possible split:

[7,2] [5,10,8]

Sums:
9
23


The largest sum is:

18

The algorithm searches for the smallest possible maximum sum.

Validation

For every possible maximum sum, check whether the array can be divided into at most k subarrays.

If it can:

Try a smaller maximum sum

If it cannot:

Try a larger maximum sum
Algorithm
Find the maximum element.
Find the total sum.

Set:

left = maximum element
right = total sum

Calculate:

mid = left + (right - left) / 2
Check how many subarrays are required if mid is the maximum allowed sum.
If the number of required subarrays is within k, move right.
Otherwise move left.
Return the minimum valid value.
Complexity
Time Complexity: O(n log(sum))
Space Complexity: O(1)
File
Solution-04-410.java
🔹 Solution 05 – LeetCode 704
Binary Search
Problem Description

Given a sorted array of integers and a target value, find the index of the target.

If the target does not exist, return:

-1
Approach

Binary Search is used because the array is sorted.

Instead of checking every element, the algorithm repeatedly removes half of the remaining search space.

Algorithm

Set:

left = 0
right = nums.length - 1

Calculate:

mid = left + (right - left) / 2

If:

nums[mid] == target

return mid.

If:

nums[mid] < target

search the right half.

Otherwise search the left half.
Return -1 if the target is not found.
Example
Input:
nums = [-1,0,3,5,7,12]
target = 7

Output:
4

complexity:
Time Complexity: O(log n)
Space Complexity: O(1)
File
Solution-05-704.java
🔹 Solution 06 – LeetCode 719
Find K-th Smallest Pair Distance
Problem Description

Given an integer array, consider every possible pair of elements.

The distance between two elements is:

|nums[i] - nums[j]|

The goal is to find the k-th smallest pair distance.

Approach

The solution combines:

Sorting
+
Binary Search
+
Two Pointers

First, sort the array.

Then binary search the possible distance.

The smallest possible distance is:

0

The largest possible distance is:

max(nums) - min(nums)

For each candidate distance, count how many pairs have a distance less than or equal to it.

Pair Counting

After sorting, use two pointers.

For every right pointer:

Move the left pointer until the distance becomes valid.
All elements between left and right form valid pairs.

The number of valid pairs is:

right - left
Algorithm
Sort the array.

Set:

left = 0
right = nums[n-1] - nums[0]
Find the middle distance.
Count pairs whose distance is less than or equal to mid.
If the count is at least k:
Search for a smaller distance.
Otherwise:
Search for a larger distance.
Return the smallest valid distance.
Example
Input:
nums = [1,3,1]
k = 1

Possible pair distances:

|1 - 3| = 2
|1 - 1| = 0
|3 - 1| = 2

Sorted distances:

[0,2,2]

The 1st smallest distance is:

0
Complexity
Sorting: O(n log n)

Binary Search + Pair Counting:
O(n log D)

Overall:
O(n log n + n log D)

Where:

D = maximum possible pair distance

Extra space depends on the sorting implementation.

File
Solution-06-719.java
🔹 Solution 07 – LeetCode 977
Squares of a Sorted Array
Problem Description

Given an integer array sorted in non-decreasing order, return an array containing the squares of all elements, also sorted in non-decreasing order.

The original array may contain negative numbers.

Approach

Use the Two Pointer Technique.

One pointer starts at the beginning:

left = 0

Another pointer starts at the end:

right = n - 1

The largest square will always come from either:

nums[left]

or

nums[right]

Therefore, compare their absolute values and place the larger square at the end of the result array.

Algorithm
Initialize left = 0.
Initialize right = n - 1.
Create a result array.
Start filling the result array from the last position.

Compare:

abs(nums[left])

and

abs(nums[right])
Place the larger square into the current result position.
Move the corresponding pointer.
Continue until all elements are processed.
Example
Input:
[-4,-1,0,3,10]

Squares:
[16,1,0,9,100]

Output:
[0,1,9,16,100]
Complexity
Time Complexity: O(n)
Space Complexity: O(n)
File
Solution-07-977.java


Concepts Learned
1. Binary Search

Binary Search reduces the search space by half at every iteration.

It is useful when:

The data is sorted.
The search space has a monotonic property.
The answer can be determined by checking a condition.

Problems:

367
374
704
2. Binary Search on Answer

Instead of searching directly through an array, Binary Search can be applied to the possible answer range.

Problem:

410

The same concept is also used in:

719
3. Two Pointer Technique

Two pointers allow an array to be processed efficiently without repeatedly scanning the same elements.

Problems:

75
719
977
4. In-Place Array Processing

LeetCode 75 demonstrates how an array can be rearranged without creating another array.

This reduces extra memory usage.

5. Greedy Validation

LeetCode 410 uses a validation procedure to determine whether a candidate maximum sum is possible.

This validation allows Binary Search on the answer.
