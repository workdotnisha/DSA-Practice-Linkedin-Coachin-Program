# Sort 0s, 1s and 2s ⭐
You can access the problem using the following link:[Problem Link](https://www.geeksforgeeks.org/problems/sort-an-array-of-0s-1s-and-2s4231/1?itm_source=geeksforgeeks&itm_medium=article&itm_campaign=practice_card)

## Problem Statement
Given an array `arr[]` containing only 0s, 1s, and 2s. Sort the array in ascending order.

You need to solve this problem without utilizing the built-in sort function.

### Example 1:
#### Input: `arr[] = [0, 1, 2, 0, 1, 2]`
#### Output: `[0, 0, 1, 1, 2, 2]`
#### Explanation: `0s 1s and 2s are segregated into ascending order.`

### Example 2:
#### Input: `arr[] = [0, 1, 1, 0, 1, 2, 1, 2, 0, 0, 0, 1]`
#### Output: `[0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 2, 2]`
#### Explanation: `0s 1s and 2s are segregated into ascending order.`
 
### Constraints:
* $1 <= arr.size() <= 10^6$
* $0 <= arr[i] <= 2$

## Solution Approach

### Intuition:

The core idea is to partition the array into three sections:
- 0s: All 0s are placed at the beginning of the array.
- 1s: All 1s are placed in the middle section.
- 2s: All 2s are placed at the end of the array.
  
We use three pointers to achieve this partitioning:
- `lo`: Points to the beginning of the array and keeps track of the boundary between 0s and 1s.
- `mid`: Points to the current element being considered.
- `hi`: Points to the end of the array and keeps track of the boundary between 1s and 2s.

### Approach (Dutch National Flag Algorithm):

1. **Initialize**:
   - `lo = 0`
   -`mid = 0`
   - `hi = n - 1` (where `n` is the size of the array)
2. **Iterate**: `While mid <= hi`:
   - **Case 1**: `arr[mid] == 0`:
        - Swap `arr[lo]` and `arr[mid]`.
        - Increment both `lo` and `mid`. We've placed a 0 in its correct position, so we move both pointers forward.
   - **Case 2**: `arr[mid] == 1`:
        - Increment mid. The element is already in its correct position.
   - **Case 3**: `arr[mid] == 2`:
       - Swap `arr[mid]` and `arr[hi]`.
       - Decrement `hi`. We've placed a 2 in its correct position, but we don't increment `mid` yet because the swapped element at `arr[mid]` might be a 0 or a 1, which still needs to be processed.
3. **Termination**: The loop continues until mid crosses `hi`. At this point, all 0s are at the beginning, all 1s are in the middle, and all 2s are at the end.

#### Example:

Let's say `arr = [2, 0, 2, 1, 1, 0]`.

| lo | mid	|hi	|arr	            |Explanation|
| -- | ---- |-- |------------------ | -------------------- |
| 0	 | 0	|5	|[2, 0, 2, 1, 1, 0]	|arr[mid] == 2, swap arr[mid] and arr[hi], hi--|
| 0	 | 0	|4	|[0, 0, 2, 1, 1, 2]	|arr[mid] == 0, swap arr[lo] and arr[mid], lo++, mid++|
| 1	 | 1	|4	|[0, 0, 2, 1, 1, 2]	|arr[mid] == 0, swap arr[lo] and arr[mid], lo++, mid++|
| 2	 | 2	|4	|[0, 0, 2, 1, 1, 2]	|arr[mid] == 2, swap arr[mid] and arr[hi], hi--|
| 2	 | 2	|3	|[0, 0, 1, 1, 2, 2]	|arr[mid] == 1, mid++|
| 2	 | 3	|3	|[0, 0, 1, 1, 2, 2]	|arr[mid] == 1, mid++|
| 2	 | 4	|3	|[0, 0, 1, 1, 2, 2]	|mid > hi, loop terminates.|


## Code Implementation (C++)
```C++
class Solution {
public:
    void sort012(vector<int>& arr) {
        int n = arr.size();
        int lo = 0;
        int hi = n - 1;
        int mid = 0;

        while (mid <= hi) {
            if (arr[mid] == 0) {
                swap(arr[lo++], arr[mid++]);
            } else if (arr[mid] == 1) {
                mid++;
            } else {
                swap(arr[mid], arr[hi--]);
            }
        }
    }
};
```

## Complexity Analysis
- **Time Complexity:** `O(n)` - We iterate through the array at most once.
- **Space Complexity:** `O(1)` - We use only constant extra space for the pointers.



