# Linked List

Our first **real** data structure! Arrays are more like primitives since they are available in almost every language—except for JavaScript (haha).

## Why Not Arrays?

Arrays have some major downsides:
- **Deletion** is expensive.
- **Insertion** is expensive.
- **Fixed size** (ungrowable in low-level implementations).

## Introduction to Linked Lists

A **linked list** is a node-based data structure. Unlike arrays, linked lists provide dynamic memory allocation and efficient insertions/deletions.

### Singly Linked List

A singly linked list consists of nodes where each node contains a value and a reference to the next node.

```
A (head) -> B -> C -> D
```

#### Node Structure:
```ts
class Node<T> {
    val: T;
    next?: Node<T>;
    constructor(val: T) {
        this.val = val;
        this.next = undefined;
    }
}
```

### Doubly Linked List

A doubly linked list contains nodes that have references to both the next and previous nodes.

```
A <-> B <-> C <-> D
```

#### Node Structure:
```ts
class DoublyNode<T> {
    val: T;
    next?: DoublyNode<T>;
    prev?: DoublyNode<T>;
    constructor(val: T) {
        this.val = val;
        this.next = undefined;
        this.prev = undefined;
    }
}
```

## Insertion

Insertion in a linked list is **fast** (O(1)) compared to an array.

Example: **Inserting `F` after `A`**

1. `A -> F`
2. `F -> B`
3. `F <- B`
4. `A <- F`

```ts
A.next = F;
F.next = B;
B.prev = F;
F.prev = A;
```

## Deletion

Example: **Deleting `C`** (from a doubly linked list)

```
Before:
A <-> B <-> C <-> D

After:
A <-> B <-> D
```

**Steps:**
1. `B -> D` (i.e., `B.next = C.next`)
2. `B <- D` (i.e., `D.prev = C.prev`)
3. Set `C.next = null` and `C.prev = null` to completely detach.
4. Return `C.val` (optional).

```ts
B.next = C.next; // B -> D
D.prev = C.prev; // B <- D
C.next = C.prev = null; // Remove C completely
return C.val;
```

✅ **Time Complexity:** O(1) (constant operations, independent of list size).

> Note: Always check for edge cases (e.g., `null` checks, empty list handling) in real implementations.

## Complexity Analysis

| Operation          | Time Complexity | Notes |
|-------------------|---------------|-------|
| **Traversal**       | `O(n)`          | Not recommended; better data structures exist for fast lookups |
| **Get Head/Tail**   | `O(1)`          | Constant time retrieval |
| **Delete Middle**   | `O(1)`          | Requires direct reference to node |
| **Delete Head/Tail**| `O(1)`          | Constant operations |
| **Insert Middle**   | `O(1)`          | Requires direct reference to insertion point |
| **Prepend/Append**  | `O(1)`          | Direct updates |

## Implementation in TypeScript

Here’s a complete implementation of a doubly linked list in TypeScript:

```ts
class DoublyLinkedList<T> {
    head?: DoublyNode<T>;
    tail?: DoublyNode<T>;

    append(val: T): void {
        const newNode = new DoublyNode(val);
        if (!this.head) {
            this.head = this.tail = newNode;
        } else {
            this.tail!.next = newNode;
            newNode.prev = this.tail;
            this.tail = newNode;
        }
    }

    prepend(val: T): void {
        const newNode = new DoublyNode(val);
        if (!this.head) {
            this.head = this.tail = newNode;
        } else {
            newNode.next = this.head;
            this.head.prev = newNode;
            this.head = newNode;
        }
    }

    delete(val: T): void {
        let curr = this.head;
        while (curr) {
            if (curr.val === val) {
                if (curr.prev) curr.prev.next = curr.next;
                if (curr.next) curr.next.prev = curr.prev;
                if (curr === this.head) this.head = curr.next;
                if (curr === this.tail) this.tail = curr.prev;
                curr.next = curr.prev = undefined;
                return;
            }
            curr = curr.next;
        }
    }
}
```

This implementation provides basic append, prepend, and delete operations efficiently.

---

### Final Thoughts

Linked lists are great when **insertions and deletions** are frequent. However, for general-purpose use, other data structures (like **dynamic arrays**, **hash tables**, or **binary trees**) may be better depending on your needs.

If traversal or random access is a frequent operation, a **linked list is NOT ideal**—consider an array or a hash table instead!

