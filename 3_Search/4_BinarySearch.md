# Binary Search

## **Introduction**

Binary Search is a fundamental algorithm and a **classic off-by-one problem**.

### **First Question: Is the Array Ordered?**

If the array is **ordered**, we can optimize searching by:
1. Starting at the **middle**.
2. Checking if the target value is **bigger or smaller**.
3. Jumping to the **half** that might contain the target.
4. Repeating until:
   - The value is found.
   - No more halves are left.

### **Big-O Complexity Analysis**
At each step, we divide the array size in half:

\[ N \to \frac{1}{2}N \to \frac{1}{4}N \to \frac{1}{8}N \to ... \]

Until:

\[ \frac{N}{2^k} = 1 \Rightarrow N = 2^k \Rightarrow k = \log_2 N \]

Thus, **Binary Search runs in** \(O(\log N)\).

#### **Trick for Identifying Logarithmic Complexity**
If the problem involves **halving at each step**, it is likely:
- **O(log N)** (for simple halving like Binary Search)
- **O(N log N)** (for sorting algorithms like Merge Sort)

---

## **Binary Search PseudoCode**

### **Indexing Rules**
- `lo` (lower bound) is **inclusive**.
- `hi` (upper bound) is **exclusive** (this ensures correctness and prevents infinite loops).

```pseudo
function search(arr, lo, hi, target):
    while lo < hi:
        midpoint = floor(lo + (hi - lo) / 2)
        value = arr[midpoint]
        
        if value == target:
            return true
        else if value > target:
            hi = midpoint  # Keep hi exclusive
        else:
            lo = midpoint + 1  # Move lo forward
    
    return false
```

---

## **Implementation**
📂 **[BinarySearchList.ts](../kata-machine/src/day1/BinarySearchList.ts)**


