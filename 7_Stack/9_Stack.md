# Stack

A stack is similar to a queue, but operates in reverse. It can be visualized as:

$$
A \leftarrow B \leftarrow C \leftarrow D
$$

with the **tail** on the left and the **head** on the right.

Imagine a stack of plates (like a stacktrace in programming). In a stack, you only add (push) and remove (pop) from the head.

---

## Pushing to the Stack

When you add a new element (say, **E**) to the stack:

1. **Point E to the current head.**
2. **Update the head to E.**

After adding, the stack becomes:

$$
A \leftarrow B \leftarrow C \leftarrow D \leftarrow E
$$

---

## Popping from the Stack

When you remove the head:

1. **Save the current head (E).**
2. **Update the head to `E.next` (or `E.prev`, depending on your implementation).**
3. **Return E.**

After removal, the stack reverts to:

$$
A \leftarrow B \leftarrow C \leftarrow D
$$

---

## Additional Notes

- When discussing recursion, it is easier to think of a stack of function calls.
- The peek operation (viewing the top element) is analogous to that of a queue.
- The constraint of only pushing and pulling from the head makes the stack very efficient.

---

## Implementation

📂 **[Stack.ts](../kata-machine/src/day1/Stack.ts)**
