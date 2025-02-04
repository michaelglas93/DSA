# Two Crystal Balls Problem

## Problem Statement
You are given **two crystal balls** that will break if dropped from a high enough distance. The challenge is to determine the **exact floor** at which they will break, using the most optimized approach.

The problem can be visualized as an **array of boolean values**, where `false` represents a floor where the ball does not break, and `true` represents a floor where the ball does break. The array starts with `false` values and at some point transitions to `true` values permanently.

Our goal is to find the first `true` in the most efficient way possible.

## Possible Approaches
### 1. **Linear Search (O(n))**
A simple approach is to drop a ball from each floor, one by one, until it breaks. Once it breaks, we know the exact floor.

**Worst-case scenario:** We have to check every floor, resulting in an **O(n) time complexity**.

### 2. **Binary Search (O(log n))**
Since the array is sorted (`false -> false -> true -> true`), a **binary search** might seem like a good idea. However, the issue is that once a ball breaks, we cannot continue searching with it. After the first ball breaks, we would need to switch to a **linear search**, leading to a **worst-case time complexity of O(n)**.

### 3. **Optimized Approach (O(√n))**
A more efficient strategy is to take advantage of the two crystal balls by using a **square root jump strategy**:

1. Jump in increments of **√n** floors using the first ball.
2. If the first ball breaks, we know the breaking floor is within the last jump interval.
3. Use the second ball to perform a **linear search** in the last jump interval to pinpoint the exact floor.

#### **Why is this approach better?**
- The worst case is **O(√n)** instead of O(n).
- Instead of checking every floor, we reduce the search space significantly with each jump.
- Once the first ball breaks, we only have to check at most **√n** additional floors.

## Implementation

📂 **[TwoCrystalBalls.ts](../kata-machine/src/day1/TwoCrystalBalls.ts)**


## Complexity Analysis
- **Jumping in steps of √n**: O(√n)
- **Linear search within the last interval**: O(√n) (at most)
- **Total worst-case time complexity**: **O(√n)**

## Summary
| Approach         | Time Complexity | Explanation |
|-----------------|----------------|-------------|
| **Linear Search** | O(n)            | Drop the ball one floor at a time until it breaks |
| **Binary Search** | O(n) worst case | Once the first ball breaks, a linear search is required |
| **√n Jump Search** | **O(√n)**       | Jump in steps of √n, then perform a linear search |

By leveraging **two crystal balls**, the **O(√n) strategy** significantly optimizes the search process, making it the best solution for this problem.

