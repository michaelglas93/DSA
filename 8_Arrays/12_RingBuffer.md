# RingBuffer

A **RingBuffer** (or circular buffer) can be thought of as an ArrayList with a twist: instead of using index `0` as the head and `length` as the tail, both the head and tail are maintained as indices within the range `0` to `N - 1`.

## Key Concepts

- **Index-Based Head and Tail:**  
  - The head and tail pointers indicate positions in the buffer.  
  - All operations use these indices, ensuring they wrap around when reaching the end of the array.

- **Efficient Operations:**  
  - **Push, Pop, Shift, Unshift:**  
    - All these operations can be performed in \(O(1)\) time.
  - **Remove from Front:**  
    - Simply increment the head pointer by one (i.e., `head = (head + 1) % N`).
  - **Insertion at the Tail:**  
    - Similarly, adding a new element at the tail is done by placing it at the current tail index and then updating the tail (i.e., `tail = (tail + 1) % N`).

## Handling the Wrap-Around

- **Wrap-Around Behavior:**  
  - When the tail reaches the end of the buffer (i.e., `tail + 1` equals the buffer length), it wraps around to the beginning.  
  - This is achieved using the modulo operation: `new_index = (current_index + 1) % capacity`.

## Resizing the RingBuffer

- **When to Resize:**  
  - If the buffer becomes full (i.e., the tail catches up to the head in a way that indicates no more free space), a resize operation is necessary.
- **Resizing Process:**  
  - Start from the current head and traverse the entire buffer to copy the elements into a new array with a larger capacity.
  - Update the head to `0` and set the tail to the former length.

## Practical Use Case

- **Logging Systems:**  
  - RingBuffers are ideal for scenarios like log writing, where logs need to stay in order and new logs must continuously be added.
  - They ensure that the most recent logs are available, and older logs are overwritten or moved when the buffer reaches capacity.

This implementation ensures that all basic operations are efficient, while also managing the complexity of dynamic resizing only when necessary.
