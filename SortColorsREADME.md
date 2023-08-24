# leet-day41

# Sort Colors

Given an array `nums` with `n` objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers `0`, `1`, and `2` to represent the colors red, white, and blue, respectively.

## Example

**Input:**
```
nums = [2,0,2,1,1,0]
```
**Output:**
```
[0,0,1,1,2,2]
```

**Input:**
```
nums = [2,0,1]
```
**Output:**
```
[0,1,2]
```

## Constraints

- `n` is the length of `nums`
- `1 <= n <= 300`
- `nums[i]` is either 0, 1, or 2.

## Approach and Explanation

We can solve this problem in a one-pass algorithm using only constant extra space. The idea is to maintain three pointers: `left`, `right`, and `current`. The `left` pointer keeps track of the boundary between 0s and 1s, and the `right` pointer keeps track of the boundary between 1s and 2s. The `current` pointer iterates through the array.

- If `nums[current]` is 0, swap it with `nums[left]` and increment both `left` and `current` pointers. This effectively moves the 0 to the beginning of the array.
- If `nums[current]` is 2, swap it with `nums[right]` and decrement the `right` pointer. This effectively moves the 2 to the end of the array.
- If `nums[current]` is 1, just increment the `current` pointer. This means that the 1 is already in its correct position.

This approach ensures that 0s are moved to the beginning and 2s are moved to the end, leaving 1s in the middle.

## Complexity Analysis

- Time Complexity: O(n), where n is the size of the input array `nums`. We traverse the array once.
- Space Complexity: O(1), as we are using constant extra space.

## Summary

The "Sort Colors" problem can be efficiently solved using the Dutch National Flag algorithm, which sorts the array in one pass with constant extra space. This approach is based on maintaining pointers to divide the array into three segments: 0s, 1s, and 2s. By properly swapping elements, we can achieve the desired sorting.
