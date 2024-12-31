# Finding the Maximum Number in a Circularly Shifted Array

## Overview
This project implements an algorithm to find the maximum number in a circularly shifted array in **O(log n)** time using a divide-and-conquer approach. A circularly shifted array is a sorted array that has been rotated by some positions to the right, such as:

- Example 1: `[35, 42, 5, 15, 27, 29]` (shifted 2 positions)
- Example 2: `[27, 29, 35, 42, 5, 15]` (shifted 4 positions)

---

## Algorithm Description

The divide-and-conquer approach works as follows:

1. **Base Case**: If the array size is 1, return the single element.
2. **Divide**: Find the middle index of the array.
3. **Rotation Point Check**:
   - If the middle element is greater than the next element, the middle element is the maximum.
   - If the middle element is smaller than the previous element, the previous element is the maximum.
4. **Search Direction**:
   - If the left half is sorted (the first element is smaller than the middle element), the maximum lies in the right half.
   - Otherwise, the maximum lies in the left half.
5. **Recursion**: Continue searching in the relevant half.

---

## Pseudocode

```cpp
Function findMax(arr, low, high)
    If low == high
        Return arr[low]

    mid = (low + high) / 2

    If mid < high and arr[mid] > arr[mid + 1]
        Return arr[mid]

    If mid > low and arr[mid] < arr[mid - 1]
        Return arr[mid - 1]

    If arr[low] <= arr[mid]
        Return findMax(arr, mid + 1, high)

    Else
        Return findMax(arr, low, mid - 1)
