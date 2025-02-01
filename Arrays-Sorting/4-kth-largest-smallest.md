# Kth Largest Element in an Array ⭐
You can access the problem using the following link: [Problem Link](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)

## Problem Statement
Given an integer array `nums` and an integer `k`, return the `kt`h largest element in the array.

Note that it is the `kth` largest element in the sorted order, not the `kth` distinct element.

### Example 1:
#### Input: `nums = [3,2,1,5,6,4], k = 2`
#### Output: `5`

### Example 2:
#### Input: `nums = [3,2,3,1,2,4,5,5,6], k = 4`
#### Output: `4`
 
### Constraints:
* $1 <= k <= nums.length <= 10^5$
* $-10^4 <= nums[i] <= 10^4$

## Solution Approach

### Intuition:

The most straightforward approach is to simply sort the array. Once the array is sorted, the `k-th` largest element will be located at the `n - k` index (remember that arrays are 0-indexed), where `n` is the size of the array.

### Approach:

1. **Sort the array**: Use any efficient sorting algorithm (like the standard library's sort function, which is often an optimized quicksort or merge sort). This arranges the elements in ascending order.

2. **Return the element at the correct index**: After sorting, the k-th largest element will be at index n - k.  Return the element at this index.

#### Example:

Let's say `nums = [3, 2, 1, 5, 6, 4]` and `k = 2`.

1. **Sort**: After sorting, nums becomes [1, 2, 3, 4, 5, 6].

2. **Middle element**:`n = 6`, so `n - k = 6 - 2 = 4`.  `nums[4]` is `5`, which is the 2nd largest element.

### Why this works:

Sorting arranges the elements in increasing order.  The largest element will be at the last index `(n - 1)`, the second largest at the second to last index `(n - 2)`, and so on.  Therefore, the `k-th` largest element will be at index `n - k`.

## Code Implementation (C++)
```C++
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        int n = nums.size();
        sort(nums.begin(), nums.end()); // Sort the input vector
        return nums[n - k];          // Return the element at the (n - k)th index
    }
};
```
- `sort(nums.begin(), nums.end());` sorts the vector `nums` in ascending order.
- `int n = nums.size();` stores the size of the vector in `n`.
- `return nums[n - k];` returns the element at the index `n - k`.

## Complexity Analysis
- **Time Complexity:** `O(n log n)` due to the sorting step.
- **Space Complexity:** `O(1)` if the sorting is done in-place. Some sorting algorithms might use `O(log n)` space in certain cases.