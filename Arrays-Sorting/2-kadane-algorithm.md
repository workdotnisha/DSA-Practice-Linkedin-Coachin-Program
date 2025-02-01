# Maximum Subarray ⭐
You can access the problem using the following link: [Problem Link](https://leetcode.com/problems/maximum-subarray/description/)

## Problem Statement
Given an integer array nums, find the subarray with the largest sum, and return its sum.

### Example 1:
#### Input: `nums = [-2,1,-3,4,-1,2,1,-5,4]`
#### Output: `6`
#### Explanation: `The subarray [4,-1,2,1] has the largest sum 6.`

### Example 2:
#### Input: `nums = [1]`
#### Output: `1`
#### Explanation: `The subarray [1] has the largest sum 1.`
 
### Constraints:
* $1 <= nums.length <= 10^5$
* $-10^4 <= nums[i] <= 10^4$

## Solution Approach

### Intuition:

The key idea is to keep track of the `currentSum` of the subarray we're currently considering.  If `currentSum` becomes negative, it's no longer beneficial to include it in the sum, because adding a negative number will only decrease the overall sum. In such a case, we reset `currentSum` to 0 and start considering a new subarray from the next element.  We also maintain a `maxSum` variable to store the maximum sum encountered so far.

### Approach (Kadane's Algorithm):

1. **Initialize**:
   - **maxSum**: Initialize this to the smallest possible integer (INT_MIN in C++) to handle cases where all numbers are negative. This will store the final result.
   - **currentSum**: Initialize this to 0. This will store the sum of the current subarray being considered.
2. **Iterate**: Loop through the array from left to right.
3. **Update currentSum**: In each iteration, add the current element nums[i] to currentSum.
4. **Update maxSum**: If currentSum is greater than maxSum, update maxSum with the value of currentSum. This step ensures that we are always storing the largest sum found so far.
5. **Reset currentSum**: If currentSum becomes negative, reset it to 0. This is the crucial step.  A negative currentSum would only reduce the sum of any subsequent elements. So, we start considering a new subarray from the next element.
6. **Return maxSum**: After iterating through the entire array, maxSum will hold the maximum subarray sum.

#### Example:

Let's say `nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]`.

| i	| nums[i]	| currentSum |	maxSum |	Explanation                                                 |
| - | --------- | ---------- |  ------ | -------------------------------------------------------------- |
| 0	| -2	    |   -2	     |  -2	   |   currentSum becomes -2, which is greater than initial maxSum. |
| 1	| 1	        |   -1	     |  -2	   | currentSum becomes -1.                                         |
| 2	| -3	    |   -4	     |  -2	   | currentSum becomes -4.                                         |
| 3	| 4	        |    4	     |   4	   | currentSum becomes 4, which is greater than maxSum.            |
| 4	| -1	    |    3	     |   4	   | currentSum becomes 3.                                          |
| 5	| 2	        |    5	     |   5	   | currentSum becomes 5, which is greater than maxSum.            |
| 6	| 1	        |    6	     |   6	   | currentSum becomes 6, which is greater than maxSum.            |
| 7	| -5	    |    1	     |   6	   | currentSum becomes 1.                                          |
| 8	| 4	        |    5	     |   6	   | currentSum becomes 5.                                          |

The maximum subarray sum is 6.

## Code Implementation (C++)
```C++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int n = nums.size();
        int maxSum = INT_MIN;  // Initialize maxSum to the smallest possible integer
        int currentSum = 0;   // Initialize currentSum to 0

        for (int i = 0; i < n; i++) {
            currentSum += nums[i]; // Add the current element to currentSum

            if (currentSum > maxSum) {
                maxSum = currentSum; // Update maxSum if currentSum is greater
            }

            if (currentSum < 0) {
                currentSum = 0;   // Reset currentSum if it becomes negative
            }
        }

        return maxSum; // Return the maximum subarray sum
    }
};
```

## Complexity Analysis
- **Time Complexity:** `O(n)` - We iterate through the array only once.
- **Space Complexity:** `O(1)` - We use only constant extra space.


