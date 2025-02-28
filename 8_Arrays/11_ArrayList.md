# ArrayList

## Initial Setup

Consider an array with indices from `0` to `3`. Suppose the array holds elements like `[2,]` with:
- **Length:** 1 (number of elements actually stored)
- **Capacity:** 3 (total allocated space)

## Operations

### Get Operation

- **Operation:** `get(idx)`
- **Behavior:** 
  - If `idx >= length`, throw an error.
  - Otherwise, return the element at that index.
- **Time Complexity:** \(O(1)\)

### Push Operation

- **Operation:** `push(val: T)`
- **Behavior:**
  - Write the new value at the index given by `length`.
  - Increment `length` by 1.
- **Time Complexity:** \(O(1)\) on average.

### Pop Operation

- **Operation:** `pop() : T | undefined`
- **Behavior:**
  - Retrieve the value at `length - 1`.
  - Decrement `length`.
  - Return the retrieved value.
- **Time Complexity:** \(O(1)\)

### Handling Capacity Overflow

- When a `push` operation is attempted and the array's length equals its capacity:
  - A new array with a larger capacity (commonly double the current capacity) is created.
  - The existing elements are copied to this new array.
  - The `length` remains unchanged (only capacity increases).

## Queue Operations and Data Structure Choice

### ArrayList as a Queue

When using an ArrayList (dynamic array) as a queue without additional techniques:
- **Naive Enqueue/Dequeue:**
  - **Enqueue (Insertion at the Head):**
    - If you choose to insert at the beginning (head) of the array, all existing elements must be shifted one position to the right.
    - **Time Complexity:** \(O(n)\)
  - **Dequeue (Removal from the Head):**
    - Removing the element from the head similarly requires shifting all remaining elements one position to the left.
    - **Time Complexity:** \(O(n)\)

### LinkedList as a Queue

- **Linked List Queue:**
  - **Enqueue (Insertion at the Tail):**
    - Add a new node at the tail. With a tail pointer, this is an \(O(1)\) operation.
  - **Dequeue (Removal from the Head):**
    - Remove the node from the head. With direct access, this is an \(O(1)\) operation.
- **Advantages:**
  - Linked lists naturally support efficient insertions and deletions at both ends without the need for shifting elements.
  - They are well-suited for dynamic queue operations when a circular array is not used.


## Interview Tip

When discussing data structure choices in interviews, it's beneficial to explain that **"IT DEPENDS"**:
- **ArrayList (Dynamic Array):**
  - Use when frequent push/pop operations at the end are required (e.g., implementing a stack) or when random access is needed.
- **LinkedList:**
  - Use when the application demands frequent insertions and deletions at the beginning or in the middle, or when implementing a queue (if not using a circular buffer with an array).


