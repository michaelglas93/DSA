# Bubble Sort: Step-by-Step Explanation and Time Complexity Analysis

## Introduction
Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. This process continues until the array is fully sorted. 

## Step-by-Step Execution
Consider an unsorted array:

```
[1, 3, 7, 4, 2]
```

Bubble Sort follows these steps:

1. Start at the 0th position and iterate through the array.
2. Compare each element with the next one.
3. If the next element is smaller, swap them.
4. After the first full pass, the largest element is placed at the last position.
5. Repeat the process for the remaining elements (excluding the last sorted one) until only one element is left unsorted.

### Example Walkthrough

#### **Pass 1:**
```
[1, 3, 7, 4, 2]  → Compare 1 and 3 (no swap)
[1, 3, 7, 4, 2]  → Compare 3 and 7 (no swap)
[1, 3, 4, 7, 2]  → Compare 7 and 4 (swap)
[1, 3, 4, 2, 7]  → Compare 7 and 2 (swap)
```
**Largest element 7 is now sorted at the last position.**

#### **Pass 2:** (Ignoring last element)
```
[1, 3, 4, 2, 7]  → Compare 1 and 3 (no swap)
[1, 3, 4, 2, 7]  → Compare 3 and 4 (no swap)
[1, 3, 2, 4, 7]  → Compare 4 and 2 (swap)
```
**Second largest element 4 is now sorted.**

#### **Pass 3:**
```
[1, 3, 2, 4, 7]  → Compare 1 and 3 (no swap)
[1, 2, 3, 4, 7]  → Compare 3 and 2 (swap)
```
**Third largest element 3 is now sorted.**

#### **Pass 4:**
```
[1, 2, 3, 4, 7]  → Compare 1 and 2 (no swap)
```
**Sorting is complete!**

## Time Complexity Analysis

Bubble Sort performs **N-1** comparisons in the first iteration, **N-2** in the second, and so on, until only one element remains. The total number of comparisons is:

$$N + (N-1) + (N-2) + \dots + 1$$

Using the formula for the sum of the first N natural numbers:

$$\frac{N(N+1)}{2}$$

For Big-O notation, we drop constants and lower order terms:

$$O(N^2)$$

Thus, Bubble Sort has a worst-case and average-case time complexity of **O(N^2)**, making it inefficient for large datasets.

## Conclusion
Bubble Sort is easy to understand but inefficient compared to other sorting algorithms like Merge Sort or Quick Sort. It is primarily useful for educational purposes or when working with small datasets.

## Implementation

📂 **[BubbleSort.ts](../kata-machine/src/day1/BubbleSort.ts)**