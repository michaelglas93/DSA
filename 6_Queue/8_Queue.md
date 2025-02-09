# Queue Data Structure

## Overview
A **Queue** is one of the most common data structures implemented in many programming languages. It follows the **FIFO (First In, First Out)** principle, meaning that the first element added is the first one to be removed.

A **queue** is essentially a specific implementation of a **linked list**.

### Structure
A typical queue maintains a reference to both the **head** and the **tail**:

```
A -> B -> C -> D
head            tail
```

### Operations
1. **Enqueue (Insertion at the tail)**
   - We insert a new element at the tail.
   - `tail.next = E`, then `this.tail = E`.
   - **Time Complexity:** $O(1)$

2. **Dequeue (Removal from the head)**
   - We remove the element from the head.
   - `h = head`
   - `head = head.next`
   - `h.next = null`
   - Sometimes return `h.val`.
   - **Time Complexity:** $O(1)$

3. **Peek (Viewing the first element)**
   - Returns the value of `head` without removing it.
   - **Time Complexity:** $O(1)$

## Queue Implementation
The queue can be implemented using a linked list or an array, but a linked list provides better performance for dynamic queue operations.

### Example (TypeScript)
📂 **[Queue.ts](../kata-machine/src/day1/Queue.ts)**


## Time Complexity Summary
| Operation | Complexity |
|-----------|------------|
| Enqueue   | $O(1)$     |
| Dequeue   | $O(1)$     |
| Peek      | $O(1)$     |

## Use Cases
- **Scheduling tasks** (e.g., CPU scheduling, print queue)
- **Breadth-First Search (BFS)** in graphs
- **Handling requests in web servers**
- **Messaging services** (e.g., Kafka, RabbitMQ)

---
This implementation ensures **efficient** queue operations with constant time complexity. 🚀

