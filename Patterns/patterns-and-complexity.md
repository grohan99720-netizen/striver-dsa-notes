# DSA Patterns and Complexity — Quick Revision

Use this file as a compact revision reference. Add a pattern here when it is encountered in a problem; keep problem-specific explanations in their topic files.

## 1. Array Traversal

**When to use:** Visit every element once to calculate a sum, count items, find a value, or validate a condition.

**Algorithm:**
1. Initialize the required answer or state.
2. Loop from index `0` while `i < n`.
3. Process `arr[i]`.
4. Return the answer.

```java
int sum = 0;
for (int i = 0; i < arr.length; i++) {
    sum += arr[i];
}
```

- **Time:** O(n).
- **Auxiliary space:** O(1), if only a few variables are used.

## 2. Two Pointers — Opposite Ends

**When to use:** Reverse an array or compare/swap elements from both ends.

**Algorithm:**
1. Initialize `i = 0` and `j = n - 1`.
2. Continue while `i < j`.
3. Process or swap the two pointed elements.
4. Move `i++` and `j--`.

- **Time:** O(n), because the pointers move toward each other.
- **Auxiliary space:** O(1) for in-place swapping.

## 3. Prefix Sum / Running Sum

**When to use:** A result at each index depends on the sum of all elements up to that index.

**Algorithm:**
1. Initialize `sum = 0`.
2. Traverse from left to right.
3. Add the current element to `sum`.
4. Store `sum` as the result for the current index.

- **Time:** O(n).
- **Auxiliary space:** O(n) if a separate result array is created; O(1) extra space if modifying the input array is allowed.

## 4. Frequency Counting

**When to use:** Count occurrences, compare character composition, or find values with highest/lowest frequency.

**Algorithm:**
1. Create a frequency structure, such as a `HashMap` or a fixed-size count array when the value range is known.
2. Traverse the input and increment the count for each value.
3. Process the counts to answer the question.

- **Time:** Usually O(n) expected with a hash map, or O(n + k) when processing k distinct values.
- **Auxiliary space:** O(k), where k is the number of distinct values. A fixed-size count array uses O(1) relative to input size when its size is fixed.

**Remember:** For anagrams, compare lengths first, increment counts from one string, and decrement counts using the other string.

## 5. Euclidean Algorithm — GCD

**When to use:** Find the greatest common divisor of two integers.

**Algorithm:**
1. While `b != 0`, calculate `r = a % b`.
2. Set `a = b` and `b = r`.
3. When `b == 0`, return `a`.

- **Time:** O(log(min(a, b))) for positive inputs.
- **Auxiliary space:** O(1) in the iterative version.

## 6. LCM Using GCD

**Formula:** `LCM(a, b) = (a / GCD(a, b)) * b` for nonzero inputs; use an absolute value if negative inputs are allowed.

- **Time:** O(log(min(a, b))) because of GCD.
- **Auxiliary space:** O(1) with an iterative GCD.
- **Overflow reminder:** Divide before multiplying.

## 7. Basic Prime Checking

**Beginner algorithm:** For `n > 1`, try divisors from `2` through `n - 1`. If any divides evenly, it is not prime; otherwise it is prime.

- **Time:** O(n) for one candidate using this basic version.
- **Auxiliary space:** O(1).
- **Later optimization:** Checking only up to the square root reduces the time. Learn and use it when comfortable.

---

# General Time Complexity

Time complexity describes how the number of operations grows as input size `n` grows. It is not the exact time in seconds.

| Complexity | Common name | Typical example |
|---|---|---|
| O(1) | Constant | Array index access |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | One traversal |
| O(n log n) | Linearithmic | Efficient comparison sorting |
| O(n²) | Quadratic | Two nested loops over n |
| O(n³) | Cubic | Three nested loops over n |
| O(2ⁿ) | Exponential | Some subset/backtracking algorithms |
| O(n!) | Factorial | Generating all permutations |

## How to estimate time complexity

- One loop over n elements is usually O(n).
- Two independent consecutive loops are O(n + n) = O(n).
- A loop inside another loop, each running n times, is usually O(n²).
- If the input is repeatedly divided by 2, the number of steps is usually O(log n).
- Consecutive parts are added; nested parts are multiplied.
- Ignore constant factors and lower-order terms: O(3n + 5) becomes O(n).
- Always inspect loop bounds and input changes; nested loops are not automatically O(n²).

# General Space Complexity

Space complexity describes extra memory growth as input size increases.

| Complexity | Typical example |
|---|---|
| O(1) | A fixed number of variables |
| O(n) | A new array or list holding n values |
| O(k) | A map storing k distinct values |
| O(n²) | A two-dimensional n by n table |

## Auxiliary space reminders

- Auxiliary space means extra working memory; clarify whether the returned output is counted.
- A few variables such as `i`, `j`, and `temp` use O(1) auxiliary space.
- A separate result array of n elements uses O(n) space.
- A frequency map can use O(k) space for k distinct values.
- Recursive calls use stack space; for recursion depth n, stack space can be O(n).
- In-place means the input is modified instead of creating another full-size data structure; it usually reduces auxiliary space.

## Quick checklist before submitting

1. Is the loop boundary correct? For an array of length n, valid indices are 0 through n - 1.
2. Are empty and single-element inputs handled?
3. Are duplicates and ties handled according to the statement?
4. Is the required range inclusive or exclusive?
5. Am I storing values when only a count is needed?
6. Can the answer overflow an `int`?
7. Have I stated time and auxiliary space separately?
