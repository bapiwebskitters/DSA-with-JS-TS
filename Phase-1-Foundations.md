# Time and Space Complexity (Big O Notation)

**I assume you already know the basics(Variables, Data Types, Operators,Loops and Conditionals etc.), lt’s now master Time and Space Complexity (Big O Notation) step-by-step — it’s the core language of efficiency in DSA.**

## 🎯 Goal

Understand how to measure the efficiency of your code — both in terms of time (speed) and space (memory usage).

### 1. What Is Big O Notation?

Big O describes how the runtime or memory usage grows as the input size **n** increases.
It doesn’t give the exact time, but the rate of growth.

***Example:***

If an algorithm takes **n** steps → **O(n)**
If it takes **n²** steps → **O(n²)**
If it takes log **n** steps → **O(log n)**

Think of it as a mathematical way to express performance.

### 2. Why It Matters

Let’s say you’re building a feature that processes 1 million users.

O(n) algorithm → ~1,000,000 steps

O(n²) algorithm → ~1,000,000,000,000 steps (that’s 1 trillion 😱)

👉 Even if your code “works,” it can become too slow as data grows.

### 3. Common Big O Complexities (from Fast → Slow)

***Big O Name Example:***

1. O(1) Constant Accessing an array element (arr[i])
2. O(log n) Logarithmic Binary search
3. O(n) Linear Loop through an array
4. O(n log n) Line-arithmic Merge sort, Quick sort
5. O(n²) Quadratic Nested loops (like bubble sort)
6. O(2ⁿ) Exponential Recursive Fibonacci
7. O(n!) Factorial Solving permutations (N-Queens)

### 4. Time Complexity Examples

🟢 O(1) → Constant Time

```js
function getFirstElement(arr: number[]) {
  return arr[0];
}
```

***Always takes 1 step, no matter how big arr is.***

🟡 O(n) → Linear Time

```js
function printAll(arr: number[]) {
  for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
  }
}
```

***If array length = 1000, loop runs 1000 times → O(n)***

🔵 O(n²) → Quadratic Time

```js
function printPairs(arr: number[]) {
  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr.length; j++) {
      console.log(arr[i], arr[j]);
    }
  }
}
```

***For n elements, total iterations = n × n = n²***

🔴 O(log n) → Logarithmic Time

```js
function binarySearch(arr: number[], target: number) {
  let low = 0, high = arr.length - 1;
  while (low <= high) {
    const mid = Math.floor((low + high) / 2);
    if (arr[mid] === target) return mid;
    if (arr[mid] < target) low = mid + 1;
    else high = mid - 1;
  }
  return -1;
}
```

***Every iteration cuts the array in half → O(log n)***

🟠 O(2ⁿ) → Exponential Time

```js
function fibonacci(n: number): number {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}
```

***Each call spawns two more calls → grows exponentially***

### 5. Space Complexity example

Space complexity measures how much extra memory (RAM) an algorithm uses.
For example:

🟢 O(1) Space

```js
function sum(arr: number[]): number {
  let total = 0; // only one variable
  for (let i = 0; i < arr.length; i++) total += arr[i];
  return total;
}
```

🟡 O(n) Space

```js
function cloneArray(arr: number[]) {
  return [...arr]; // creates a new array of size n
}
```

### 6. Big O Simplification Rules

#### Ignore constants

- O(2n) → O(n)
- O(3n² + 5n) → O(n²)

#### Use the dominant term

- O(n² + n) → O(n²)

#### Nested loops multiply

- Two nested loops → O(n × n) = O(n²)

#### Sequential code adds

- Two separate loops → O(n) + O(n) = O(2n) → O(n)

### 7. Practice Exercises

Try to identify the Big O for each:

1️⃣ Q.

```js
function printOnce(arr: number[]) {
  console.log(arr[0]);
}
```

🧩 Answers: O(1)

2️⃣ Q.

```js
function printTwice(arr: number[]) {
  for (let i = 0; i < arr.length; i++) console.log(arr[i]);
  for (let j = 0; j < arr.length; j++) console.log(arr[j]);
}
```

🧩 Answers: O(n)

3️⃣ Q.

```js
function printNested(arr: number[]) {
  for (let i = 0; i < arr.length; i++)
    for (let j = 0; j < arr.length; j++)
      console.log(arr[i], arr[j]);
}
```

🧩 Answers: O(n²)

4️⃣ Q.

```js
function printHalf(arr: number[]) {
  for (let i = 0; i < arr.length / 2; i++) console.log(arr[i]);
}
```

🧩 Answers: O(n)

## 📘 Summary chart of Big O notation complexities

| **Notation**   | **Pronunciation**      | **Description**                                      | **Examples**                           |
| -------------- | ---------------------- | ---------------------------------------------------- | -------------------------------------- |
| **O(1)**       | *O one*                | Constant time – runtime doesn’t depend on input size | Accessing an array element             |
| **O(log n)**   | *O log n*              | Logarithmic time – input size is divided each step   | Binary search                          |
| **O(n)**       | *O n*                  | Linear time – runtime grows directly with input size | Iterating through an array             |
| **O(n log n)** | *O n log n*            | Line arithmic time – slightly slower than linear      | Merge sort, Quick sort (average case) |
| **O(n²)**      | *O n squared*          | Quadratic time – nested loops                        | Bubble sort, Insertion sort            |
| **O(n³)**      | *O n cubed*            | Cubic time – three nested loops                      | Matrix multiplication                  |
| **O(2ⁿ)**      | *O two to the power n* | Exponential time – doubles each step                 | Recursive subset generation            |
| **O(n!)**      | *O n factorial*        | Factorial time – grows extremely fast                | Traveling salesman (brute force)       |

### Quick Takeaways

- O(1) → Best possible efficiency (constant operations).
- O(log n) → Excellent (logarithmic growth).
- O(n) → Acceptable for most real-world use.
- O(n log n) → Optimal for sorting algorithms.
- O(n²) and worse → Avoid if input size can be large.

## 🧩 DSA Interview Question Bank – Big O Notation (Time & Space Complexity)

### 🟢 Level 1 — Basic Understanding

(Know how to identify Big O from code snippets)

#### 1. Q: What is the time complexity of accessing an element in an array by index?

**A:** O(1) – Constant time.
**Explanation:**
Array indices map directly to memory addresses. Accessing `arr[i]` doesn’t depend on array size.

```js
const arr = [10, 20, 30, 40];
console.log(arr[2]); // O(1)
```

### 2. Q: What is the time complexity of inserting at the end of an array?

**A:** O(1) – Amortized constant time.
**Explanation:**
Inserting at the end does not require shifting elements. However, if the array is dynamically resized, occasional resizing can take longer — hence “amortized” O(1).

```js
arr.push(50); // O(1)
```

### 3.Q: What is the time complexity of inserting at the beginning of an array?

**A:** O(n) – Linear time.
**Explanation:**
All existing elements must be shifted one index forward.

```js
arr.unshift(0); // O(n)
```

### 4. Q: What is the time complexity of searching for an element in an unsorted array?

**A:** O(n) – Linear time.
**Explanation:**
You must check each element until you find the target or reach the end.

```js
for (let i = 0; i < arr.length; i++) {
  if (arr[i] === target) return i;
} // O(n)
```

### 5. Q: What is the time complexity of searching for an element in a sorted array using binary search?

**A:** O(log n) – Logarithmic time.
**Explanation:**
Each comparison cuts the search space in half.

```js
function binarySearch(arr, target) {
  let l = 0, r = arr.length - 1;
  while (l <= r) {
    const mid = Math.floor((l + r) / 2);
    if (arr[mid] === target) return mid;
    else if (arr[mid] < target) l = mid + 1;
    else r = mid - 1;
  }
  return -1;
} // O(log n)
```

### 6.Q: What is the difference between O(1) and O(n) time?

**A:**

- **O(1):** Constant — time doesn’t depend on input size.
- **O(n):** Linear — time grows proportionally to input size.

**Example:**

- Accessing `arr[2]` → O(1)
- Looping through entire array → O(n)

### 7. What is the space complexity of an algorithm that uses only a few variables?

**A:** O(1) – Constant space.
**Explanation:**
The memory usage doesn’t grow with input size.

### 8. Why ignore constants and lower terms in Big O notation?

**A:** Big O describes growth rate as input size increases.
Constants and smaller terms become insignificant for large inputs.

**Example:**
`O(2n + 10)` → simplified to **O(n)**

---

### 9. Which is faster — O(log n) or O(n)?

**A:** O(log n) is faster.
**Explanation:**
Logarithmic growth increases much slower than linear.
For example, when `n = 1,000,000`:

- `log₂(n)` ≈ 20
- `n` = 1,000,000

### 10. Q: What is the meaning of worst-case, best-case, and average-case complexity?

**A:**

- **Worst-case:** Maximum time/space algorithm may take (used most often).
- **Best-case:** Minimum time (rare in real use).
- **Average-case:** Expected time over many inputs.

**Example:** Linear search in array of size `n`:

- Best-case → O(1) (first element matches)  
- Worst-case → O(n) (last element or not found)
- Average-case → O(n/2) ≈ O(n)

### ✅ Summary Table

| Operation                    | Time Complexity | Notes                        |
| ---------------------------- | --------------- | ---------------------------- |
| Array access by index        | O(1)            | Direct memory access         |
| Insert end of array          | O(1)*           | Amortized for dynamic arrays |
| Insert beginning of array    | O(n)            | Shifting needed              |
| Search in unsorted array     | O(n)            | Linear scan                  |
| Binary search (sorted array) | O(log n)        | Divide by 2 each step        |
| Constant variables           | O(1)            | Constant space               |
| Loop over array              | O(n)            | Linear growth                |
| Nested loops                 | O(n²)           | Quadratic growth             |

### 🟡 Level 2 — Code-Based Identification(Q 11-17)

***(You’ll often get snippets and must identify their complexity.)***

#### 11

```js
for (let i = 0; i < n; i++) console.log(i);
```

➡️**Time Complexity:** **O(n)**
**Explanation:**
The loop runs once for each value of `i` from 0 to n − 1 → n iterations.
Each iteration is O(1), so total = n × O(1) = **O(n)**.
**Space:** O(1)

#### 12

```js
for (let i = 0; i < n; i++)
  for (let j = 0; j < n; j++)
    console.log(i, j);
```

➡️ **Time Complexity:** **O(n²)**
**Explanation:**
Outer loop → n times
Inner loop → n times per outer iteration
Total = n × n = **n²** operations.
**Space:** O(1)

#### 13

```js
for (let i = 0; i < n; i++)
  for (let j = 0; j < n * n; j++)
    console.log(i, j);
```

➡️ **Time Complexity:** **O(n³)**
**Explanation:**
Outer loop: n times
Inner loop: n² times
Total = n × n² = **n³** operations.
**Space:** O(1)

#### 14

```js
for (let i = 1; i < n; i *= 2)
  console.log(i);
```

➡️ **Time Complexity:** **O(log n)**
**Explanation:**
`i` doubles each time (1, 2, 4, 8, 16, …) until ≥ n.
The number of iterations ≈ log₂(n).
**Space:** O(1)

#### 15

```js
for (let i = 0; i < n; i++)
  for (let j = 0; j < i; j++)
    console.log(i, j);
```

➡️ **Time Complexity:** **O(n²)**
**Explanation:**
The inner loop runs i times per outer i.
Total work = 1 + 2 + 3 + … + (n − 1) = n(n − 1)/2 ≈ **O(n²)**.
**Space:** O(1)

#### 16

```js
function fun(n) {
  if (n <= 1) return;
  fun(n - 1);
}
```

➡️ **Time Complexity:** **O(n)**
**Explanation:**
Recursive call reduces n by 1 each time → n levels deep.
**Space Complexity:** O(n) (due to call stack)

#### 17

```js
function fun(n) {
  if (n <= 1) return;
  fun(n - 1);
  fun(n - 1);
}
```

➡️ **Time Complexity:** **O(2ⁿ)**
**Explanation:**
Each call spawns two subcalls, forming a binary recursion tree.
Total ≈ 2ⁿ calls.
**Space Complexity:** O(n) (maximum recursion depth)

✅ **Summary Table**

| #Q  | Code Type            | Time Complexity | Space Complexity | Notes                  |
| --- | -------------------- | --------------- | ---------------- | ---------------------- |
| 11  | Single loop          | O(n)            | O(1)             | Linear growth          |
| 12  | Nested loop          | O(n²)           | O(1)             | Quadratic              |
| 13  | Nested with n² inner | O(n³)           | O(1)             | Cubic                  |
| 14  | Doubling loop        | O(log n)        | O(1)             | Logarithmic            |
| 15  | Triangular nested    | O(n²)           | O(1)             | ½ n² pattern           |
| 16  | Simple recursion     | O(n)            | O(n)             | Linear recursive depth |
| 17  | Binary recursion     | O(2ⁿ)           | O(n)             | Exponential growth     |

### 🟠 Level 3 — Comparative & Conceptual

***(These check your reasoning about growth rates.)***

#### 18. Between O(n) and O(n log n), which is faster for large n?

**A:** O(n) is faster.
**Explanation:**
Although O(n log n) grows only slightly faster, the log n factor increases total operations as n becomes large.
However, for small n, the difference might be negligible — constant factors can make O(n log n) algorithms competitive.

#### 19. Why is O(log n) often better than O(1) in real life?

*(Hint: caching, I/O)*
**A:**
Theoretically O(1) is faster, but in real-world systems:
O(1) operations may involve disk access, network calls, or cache misses, which are slow.
O(log n) algorithms (like balanced trees or binary search) often use sequential, cache-friendly memory access, making them faster in practice.

**Example:**
A binary search (O(log n)) on sorted data in memory may outperform a poorly designed hash lookup (O(1)) with collisions or disk I/O.

#### 20. When can O(n²) still be acceptable?

**A:**
When n is small or the algorithm runs rarely.
If n ≤ 1000, an O(n²) algorithm may finish in milliseconds.
Also acceptable when:

- Simpler to implement.
- Run infrequently (e.g., admin task).
- Input size guaranteed small (e.g., fixed UI dataset).

#### 21. Compare Merge Sort (O(n log n)) vs Bubble Sort (O(n²))

**A:**

| Aspect                 | Merge Sort              | Bubble Sort          |
| ---------------------- | ----------------------- | -------------------- |
| Time Complexity        | O(n log n)              | O(n²)                |
| Space                  | O(n)                    | O(1)                 |
| Approach               | Divide & Conquer        | Repeated swaps       |
| Stability              | Stable                  | Stable               |
| Real-world performance | Much faster for large n | Too slow for large n |

*Conclusion: Merge Sort scales far better for large datasets.*

#### 22. Is it possible for an algorithm to be O(1) time but O(n) space? Give an example

**A:** Yes ✅

**Example:**
Creating an array of size n filled with zeros.

```js
const arr = new Array(n).fill(0);
```

Time: O(1) — just allocate memory reference.
Space: O(n) — stores n elements.

Another example: allocating a large matrix without iterating to fill it.

#### 23. What does it mean if a function has O(∞)?

**A:**
This is invalid — Big O notation only describes finite growth rates as `n → ∞`.
`O(∞)` doesn’t exist; it means the algorithm never terminates or its complexity is undefined (infinite loop or error).

#### 24. Why does Big O only measure asymptotic behavior (not exact runtime)?

**A:**
Because Big O abstracts away:

- Hardware differences
- Compiler optimizations
- Constant factors

*It focuses on how runtime scales with input size `n`, not exact milliseconds.*
*Big O is a mathematical upper bound, showing performance trends as `n → ∞`.*

✅ **Summary Table**

| #   | Concept                   | Answer Summary                                      |
| --- | ------------------------- | --------------------------------------------------- |
| 18  | O(n) vs O(n log n)        | O(n) is faster for large n                          |
| 19  | O(log n) vs O(1)          | O(log n) may be faster in real-world due to caching |
| 20  | O(n²) acceptable when     | n is small / runs infrequently                      |
| 21  | Merge Sort vs Bubble Sort | Merge Sort more efficient for large data            |
| 22  | O(1) time but O(n) space  | Array initialization example                        |
| 23  | O(∞) meaning              | Invalid / undefined                                 |
| 24  | Why asymptotic only       | Focuses on growth, not hardware/runtime             |

### 🔵 Level 4 — Real-World and Advanced

***(Application-based problems you can explain or derive complexity for.)***
25. What is the time complexity of inserting into a HashMap?
26. What is the time complexity of searching in a Binary Search Tree (BST)?
27. What is the worst-case time complexity of searching in a Skewed BST?
28. What is the average-case complexity of Quick Sort and its worst case?
29. What is the time complexity of Merge Sort and its space complexity?
30. What is the complexity of Heap Sort?
31. What is the time complexity of traversing a graph using BFS/DFS?
32. What is the space complexity of recursive DFS?
33. What is the time complexity of Dijkstra’s Algorithm using a min-heap?
34. What is the time complexity of finding all subsets of a set of size n?
35. What is the time complexity of generating all permutations of a string?
36. What is the time complexity of checking if a string is a palindrome?
37. What is the space complexity of a recursive factorial function?
38. What is the time complexity of computing the nth Fibonacci number recursively vs iteratively?

### 🔴 Level 5 — Tricky & Edge Questions

***(Used to test conceptual depth and problem-solving.)***
39. Can an algorithm have different time complexities for different inputs? Example?
40. Can an algorithm have different time and space complexities?
41. If a function runs in O(n) and another in O(log n), and they run sequentially — what is the total complexity?
42. If two functions run nested (O(n) × O(log n)), what’s the total complexity?
43. What’s the complexity of binary search in an unsorted array?
44. What’s the complexity of finding the maximum element in an array?
45. Why is recursion often considered less space-efficient?
46. What’s the difference between amortized and average time complexity?
47. What’s the amortized complexity of push/pop in a dynamic array (like JS Array)?
48. How does the hash collision affect the time complexity of a HashMap lookup?
49. What’s the time complexity of sorting when all elements are already sorted (for Merge Sort vs Quick Sort)?
50. Can you think of a real-world example where space optimization is more important than time optimization?

### 🧠 Bonus Practice Challenges (with Implementation)

***Try writing functions and analyzing their complexities:***

- Reverse a string
- Find duplicates in an array
- Find all pairs in an array that sum to k
- Find the intersection of two arrays
- Calculate factorial recursively
- Merge two sorted arrays
- Implement binary search
- Implement linear search
- Implement bubble sort and analyze time + space
- Implement merge sort and quick sort

### 📚 Recommended Practice Resources

- LeetCode “Big O” tagged problems → easy + conceptual
- freeCodeCamp: Big O explained with visuals
- GeeksforGeeks: Time & Space Complexity practice questions
- InterviewBit: Complexity Analysis quiz
