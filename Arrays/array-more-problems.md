# Arrays — More Problems Discussed

This file continues the array notes in [array-basics.md](array-basics.md). It records the problems discussed after the initial array basics.

## 1. Reverse an Array

**Problem:** Reverse the elements of an array in place.

**LeetCode reference:** [344. Reverse String](https://leetcode.com/problems/reverse-string/) uses the same two-pointer swapping idea, but its input is a character array. The integer-array problem discussed here is not exactly the same LeetCode signature.

**Approach — two pointers:**
1. Set `i = 0` and `j = n - 1`.
2. While `i < j`, swap `arr[i]` and `arr[j]`.
3. Move `i` forward and `j` backward.
4. Stop when the pointers meet or cross.

```java
class Solution {
    public void reverse(int[] arr, int n) {
        int i = 0;
        int j = n - 1;

        while (i < j) {
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;

            i++;
            j--;
        }
    }
}
```

- **Time:** O(n).
- **Auxiliary space:** O(1).
- **Pattern:** Two pointers from opposite ends.
- **Status:** Your submitted code used the correct two-pointer structure. The discussion did not confirm an accepted submission.

## 2. Second Highest Occurring Element

**Problem:** Find the element with the second-highest frequency in an array.

**Approach discussed:** Count the frequency of each distinct value, then identify the highest and second-highest frequencies.

**Important details to verify in the original problem statement:**
- Whether “second highest” means the second distinct frequency.
- What to return when multiple values share a frequency.
- What to return when no second distinct frequency exists.

These tie and edge-case rules matter for hidden tests.

- **Status:** We discussed the logic and a dry run. You reported that the final code failed hidden test cases, so this problem is **not marked complete**. Revisit the exact statement and edge cases before finalizing code.
- **Revision reminder:** Do not assume the second element in a sorted list of frequencies is the answer; first clarify distinct-frequency and tie rules.

## 3. Sum of Highest and Lowest Frequency

**Problem:** Find the sum of the maximum frequency and minimum frequency among the distinct values in the array.

**Approach:**
1. Count the frequency of every distinct value.
2. Traverse the frequency counts.
3. Track the maximum and minimum frequency.
4. Return `maxFreq + minFreq`.

- **Status:** The problem was introduced, but a final implementation and accepted test result were not confirmed.
- **Pitfall:** The minimum is the smallest frequency among values that actually occur, not zero for values absent from the array.
