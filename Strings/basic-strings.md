# Basic Strings

## 1. LeetCode 242 — Valid Anagram

**Link:** https://leetcode.com/problems/valid-anagram/

**Problem:** Given two strings, determine whether one string is an anagram of the other. Anagrams contain exactly the same characters with the same frequencies, possibly in a different order.

**Approach chosen:** Frequency counting.

**Reasoning:**
1. First compare the string lengths. If they differ, they cannot be anagrams.
2. Count the characters in the first string.
3. Traverse the second string and decrease the matching character count.
4. If a required character is missing or its count becomes negative, the strings are not anagrams.
5. If all counts balance, they are anagrams.

**Hints we discussed:** Check lengths before counting; while processing the second string, decrease the stored frequency.

- **Status:** You chose the frequency approach and worked through hints. You said you would implement it while solving the code, so a final Java submission is not recorded here.
- **Pattern:** Frequency counting.
- **Assumption to check:** A fixed-size array such as `int[26]` works only when the input is restricted to lowercase English letters. For a broader character set, choose a suitable map or character-count representation.
