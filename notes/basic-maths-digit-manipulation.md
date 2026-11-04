# Basic Maths — Digit Manipulation

> Problems covered in our learning-session discussion order. This is not a claim that the order has been verified against the official A2Z sheet.

## 1. Count Digits of a Number
- **Task:** Count the number of digits in an integer.
- **Idea:** Repeatedly divide the number by 10 and count each division. Handle zero separately because it has one digit.
- **Complexity:** (O(\log_{10} n)) time, (O(1)) space.
- **Pitfall:** The loop `while (n > 0)` returns zero for input zero; account for it.

## 2. Count Odd Digits
- **Task:** Count digits whose value is odd.
- **Idea:** Extract the last digit with `n % 10`, test `digit % 2 != 0`, then remove it with `n /= 10`.
- **Complexity:** (O(\log_{10} n)) time, (O(1)) space.
- **Pitfall:** Count the digit, not whether the whole number is odd.

## 3. Reverse a Number
- **Task:** Reverse the decimal digits of an integer.
- **Idea:** Build the answer as `rev = rev * 10 + digit`, extracting each digit with modulo 10.
- **Complexity:** (O(\log_{10} n)) time, (O(1)) space.
- **LeetCode:** [7. Reverse Integer](https://leetcode.com/problems/reverse-integer/)
- **Pitfall:** LeetCode requires returning 0 if the reversed value overflows a signed 32-bit integer. Check before multiplying/adding, or use a wider type and validate the range.

## 4. Palindrome Number
- **Task:** Check whether a number reads the same forward and backward.
- **Idea:** Reverse the digits and compare the reversed number with the original. Negative numbers are not palindromes under the usual definition.
- **Complexity:** (O(\log_{10} n)) time, (O(1)) space.
- **LeetCode:** [9. Palindrome Number](https://leetcode.com/problems/palindrome-number/)
- **Pitfall:** Preserve the original number before modifying a working copy.

## 5. Largest Digit in a Number
- **Task:** Find the maximum digit.
- **Idea:** Extract each digit and update a maximum variable, initially 0 for non-negative input.
- **Complexity:** (O(\log_{10} n)) time, (O(1)) space.
- **Pitfall:** Include zero as a valid digit; define handling for negative input according to the problem statement.

## 6. Count the Digits That Divide a Number
- **Task:** Count digits of a positive number that divide the original number exactly.
- **Idea:** For each extracted digit, count it when it is non-zero and `n % digit == 0`.
- **Complexity:** (O(\log_{10} n)) time, (O(1)) space.
- **LeetCode:** [2520. Count the Digits That Divide a Number](https://leetcode.com/problems/count-the-digits-that-divide-a-number/)
- **Pitfall:** Skip zero; modulo or division by zero is invalid. Keep the original number unchanged for divisibility checks.

## 7. Factorial of a Number
- **Task:** Calculate (n! = 1 \times 2 \times \cdots \times n), with (0! = 1).
- **Idea:** Start the result at 1 and multiply by every integer from 2 through n.
- **Complexity:** (O(n)) time, (O(1)) extra space.
- **Related LeetCode:** [172. Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/) is related, but it asks for trailing zeroes—not the factorial itself.
- **Pitfall:** Java `int` and `long` overflow quickly; check the constraints and required return type.

## 8. Armstrong Number
- **Task:** Check whether a number equals the sum of each digit raised to the number of digits.
- **Idea:** Count the digits, then sum each digit raised to that count and compare with the original number.
- **Complexity:** (O(d)) digit-processing steps, where (d) is the number of digits; exponentiation cost depends on implementation. (O(1)) extra space.
- **Pitfall:** Use the number of digits as the exponent (not always 3), and preserve the original value.

---

## Java patterns used

```java
int digit = n % 10;
n /= 10;
```

- `% 10` extracts the last decimal digit.
- `/ 10` removes the last decimal digit.
- Repeated extraction processes digits from right to left.
- Save the original number if the algorithm needs to compare against it later.
