# Basic Maths — Number Theory

> Notes from the learning session. Problem order here reflects the topics discussed; verify against the official Striver A2Z sheet before treating it as the canonical sheet order.

## 1. Check for Perfect Number — Striver 745
- **Task:** Check whether a positive integer equals the sum of its positive proper divisors (excluding itself).
- **Key observation:** `n <= 1` is not a perfect number.
- **Basic approach:** Start the sum at 1 and test divisors from 2 to n - 1, adding each divisor of n. Time: O(n).
- **Optimization discussed:** Check divisor pairs only up to the square root. When `i` divides `n`, add `i` and `n / i`; avoid adding the same divisor twice when `i == n / i`.
- **LeetCode:** [507. Perfect Number](https://leetcode.com/problems/perfect-number/)
- **Pitfalls:** The first attempt missed n = 1. The O(n) loop can be slow for large inputs. Optimized implementation was discussed but successful submission was not confirmed.

## 2. Check for Prime Number
- **Task:** Determine whether n is prime.
- **Key observation:** A prime number is greater than 1 and has no divisor other than 1 and itself.
- **Algorithm:** Return false for `n <= 1`. Test divisors from 2 while `i <= n / i`. If `n % i == 0`, return false; otherwise return true after the loop.
- **Complexity:** O(sqrt(n)) time, O(1) space.
- **Related LeetCode:** [204. Count Primes](https://leetcode.com/problems/count-primes/) is related, but counts primes rather than checking one number.
- **Pitfall:** Check divisibility of the candidate number. The condition `i <= n / i` avoids overflow from `i * i`.

## 3. Count of Prime Numbers till N — Striver 790
- **Task:** Count prime numbers in the inclusive range [1, n].
- **Approach learned:** Outer loop selects each candidate `j` from 2 through n. Inner loop checks divisors from 2 while `i <= j / i`. If `j % i == 0`, increment a local divisor counter and break. If the counter remains zero, increment the total count.
- **Complexity:** O(n * sqrt(n)) time, O(1) extra space.
- **LeetCode:** [204. Count Primes](https://leetcode.com/problems/count-primes/) counts primes strictly less than n, unlike this inclusive range.
- **Debugging notes:** The inner loop must check `j`, not `n`; start divisor checking at 2; increment the total only after the candidate has no divisor. Use `c++` or `c += 1`, not `c = +1`. Use `j <= n` for the inclusive range. The Sieve of Eratosthenes has not yet been learned, so this straightforward approach may time out for large n.

## 4. GCD of Two Numbers — Striver 693
- **Task:** Find the greatest positive integer that divides both numbers.
- **Algorithm:** Euclidean algorithm. While `b != 0`, calculate `rem = a % b`, then update `a = b` and `b = rem`. Return `a` when b becomes zero.
- **Example:** GCD(48, 18): remainders are 12, 6, 0; answer = 6.
- **Complexity:** O(log(min(a, b))) time, O(1) space.
- **Related LeetCode:** [1979. Find Greatest Common Divisor of Array](https://leetcode.com/problems/find-greatest-common-divisor-of-array/) applies the GCD idea to an array.

## 5. LCM of Two Numbers — Striver 792
- **Task:** Find the smallest positive number divisible by both inputs.
- **Formula:** `LCM(a, b) = (a * b) / GCD(a, b)`.
- **Algorithm:** Find GCD using the Euclidean algorithm, then divide the product of the two numbers by the GCD.
- **Complexity:** O(log(min(a, b))) time, O(1) space.
- **Pitfall:** `a * b` can overflow an int for large inputs. Use a wider type or divide one factor by the GCD before multiplying, subject to the required return type.
- **LeetCode:** No exact two-number LCM equivalent was identified in this session.

## Quick Java patterns

### Prime check
```java
if (n <= 1) return false;

for (int i = 2; i <= n / i; i++) {
    if (n % i == 0) return false;
}
return true;
```

### Euclidean GCD
```java
while (b != 0) {
    int rem = a % b;
    a = b;
    b = rem;
}
return a;
```
