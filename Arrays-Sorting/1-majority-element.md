# Majority Element ⭐
You can access the problem using the following link: [Problem Link](https://leetcode.com/problems/majority-element/description/)

## Problem Statement
Given an array `nums` of size `n`, return the majority element.

The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

### Example 1:
#### Input: `nums = [3,2,3]`
#### Output: `3`

### Example 2:
#### Input: `nums = [2,2,1,1,1,2,2]`
#### Output: `2`
 
### Constraints:
* $n == nums.length$
* $1 <= n <= 5 * 10^4$
* $-10^9 <= nums[i] <= 10^9$

## Solution Approach

### Intuition:

If an element appears more than `n/2` times, it must occupy the middle position (and potentially other positions as well) of the sorted array.  Think about it: if it's more than half the elements, there's no way it can not be in the middle after sorting.

### Approach:

1. **Sort the array**: We can use any efficient sorting algorithm (like the standard library's sort function, which is often an optimized quicksort or merge sort implementation). Sorting brings all identical elements together.

2. **Return the middle element**: After sorting, the element at the middle index `(n/2)` will be the majority element.  Since the majority element occurs more than `n/2` times, it's guaranteed to be present at this middle position.

#### Example:

Let's say `nums = [2, 2, 1, 1, 2, 2, 2]`.

1. **Sort**: After sorting, nums becomes [1, 1, 2, 2, 2, 2, 2].

2. **Middle element**: n = 7, so n/2 = 3.  nums[3] is 2, which is the majority element.

### Why this works:

The core idea is based on the pigeonhole principle. If you have more than `n/2` pigeons and `n` pigeonholes, at least one pigeonhole must contain more than one pigeon.  In our case, the elements are the pigeons, and the distinct values are the pigeonholes. Since the majority element appears more than half the times, it has to occupy the middle position after sorting.

## Code Implementation (C++)
```C++
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        sort(nums.begin(), nums.end()); // Sort the input vector
        int n = nums.size();             // Get the size of the vector
        return nums[n/2];              // Return the element at the middle index
    }
};
```
- `sort(nums.begin(), nums.end());` sorts the vector `nums` in ascending order.
- `int n = nums.size();` stores the size of the vector in `n`.
- `return nums[n/2];` returns the element at the middle index `n/2`. Integer division ensures we get the correct middle index even if `n` is odd.

## Complexity Analysis
- **Time Complexity:** `O(n log n)` due to the sorting step.
- **Space Complexity:** `O(1)` if the sorting is done in-place.  Some sorting algorithms might use `O(log n)` space in certain cases.









