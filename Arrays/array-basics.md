# Arrays — Basic Problems

These notes cover the array problems discussed in this session. Solutions use Java.

## 1. Divisors of a Number

**Problem:** Return all positive divisors of `n` in sorted order.

**Intuition:** Check each integer from `1` through `n`. If `n % i == 0`, then `i` is a divisor. Since we check in increasing order, the result is already sorted.

```java
import java.util.*;

class Solution {
    public int[] divisors(int n) {
        ArrayList<Integer> list = new ArrayList<>();

        for (int i = 1; i <= n; i++) {
            if (n % i == 0) {
                list.add(i);
            }
        }

        return list.stream().mapToInt(Integer::intValue).toArray();
    }
}
```

- **Time:** O(n)
- **Auxiliary space:** O(k), where k is the number of divisors.
- **Key concept:** ArrayList to primitive array conversion. `stream()` creates a stream; `mapToInt(Integer::intValue)` converts Integer elements to primitive ints; `toArray()` returns an `int[]`.
- **Alternative:** Copy values with a loop into `new int[list.size()]`.
- **Pitfall:** Use `Integer`, not `Integers`, as the generic type.

## 2. Sum of Array Elements

**Problem:** Return the sum of the first `n` array elements.

**Approach:** Initialize a running total to zero, traverse the array, and add each element.

```java
class Solution {
    public int sum(int[] arr, int n) {
        int sum = 0;

        for (int i = 0; i < n; i++) {
            sum += arr[i];
        }

        return sum;
    }
}
```

- **Time:** O(n)
- **Auxiliary space:** O(1)
- **Pattern:** Array traversal + accumulation.

## 3. LeetCode 1480 — Running Sum of 1d Array

**Link:** https://leetcode.com/problems/running-sum-of-1d-array/

**Problem:** Return an array where each position contains the sum of all input elements from index 0 through that position.

**Approach:** Maintain a cumulative sum and store it at each index.

```java
class Solution {
    public int[] runningSum(int[] nums) {
        int[] result = new int[nums.length];
        int sum = 0;

        for (int i = 0; i < nums.length; i++) {
            sum += nums[i];
            result[i] = sum;
        }

        return result;
    }
}
```

- **Time:** O(n)
- **Auxiliary space:** O(n) for the returned array.
- **Pattern:** Prefix sum.
- **Further improvement:** The input array can be modified in place to achieve O(1) auxiliary space (excluding the returned/input array).

## 4. LeetCode 1523 — Count Odd Numbers in an Interval Range

**Link:** https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/

**Problem:** Count odd integers in the inclusive range `[low, high]`.

**Brute-force idea:** Check every integer and count those for which `i % 2 != 0`. Avoid storing odd values in an ArrayList when only the count is needed.

**Improvement:** Start at the first odd number in the range and increment by 2. This takes O((high - low) / 2) time and O(1) space.

**Optimal O(1) formula:**

```java
class Solution {
    public int countOdds(int low, int high) {
        return (high + 1) / 2 - low / 2;
    }
}
```

- **Time:** O(1)
- **Space:** O(1)
- **Key observation:** The number of odd integers from 1 through x is `(x + 1) / 2` using integer division. Subtract the count before `low` from the count through `high`.

## 5. Check if the Array Is Sorted (Non-decreasing)

**Problem:** Return true if every element is greater than or equal to the previous element.

```java
class Solution {
    boolean arraySortedOrNot(int[] arr, int n) {
        for (int i = 1; i < n; i++) {
            if (arr[i] < arr[i - 1]) {
                return false;
            }
        }

        return true;
    }
}
```

- **Time:** O(n)
- **Auxiliary space:** O(1)
- **Key observation:** A non-decreasing array allows equal adjacent values. It is unsorted only when `arr[i] < arr[i - 1]`.
- **Mistakes to avoid:** Start at index 1, stop at `i < n`, and compare adjacent array elements rather than comparing the size `n`.

## Revision points from this session

- Use `i < n` when traversing an array of length `n`; the last valid index is `n - 1`.
- For odd/even checks, use `value % 2 != 0` for odd and `value % 2 == 0` for even.
- If only a count is required, use a counter instead of storing matching elements.
- Prefix sum means maintaining a cumulative total while traversing.
- For non-decreasing order, duplicates are allowed.
- Prefer O(1) mathematical formulas when they are clear and safe; for counting odds in an interval, use `(high + 1) / 2 - low / 2`.
- Your submitted approaches in this session correctly used accumulation for array sum and running sum. For the divisors task, the divisor-checking logic was correct; the initial code needed array/list declaration, type, increment, and return-type fixes. For the sorted-array task, the adjacent-comparison idea was right; the condition and loop boundary needed correction.
