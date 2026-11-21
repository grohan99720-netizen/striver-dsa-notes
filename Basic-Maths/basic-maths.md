# Basic Maths

Java notes for the Basic Maths problems discussed so far. A discussion or explanation does not automatically mean the problem is completed.

## 1. Check Whether a Number Is Prime

**Problem:** Determine whether an integer is prime. A prime number is greater than 1 and has exactly two positive factors: 1 and itself.

**Basic approach:** Numbers less than or equal to 1 are not prime. Try dividing the number by every integer from 2 up to `n - 1`. If any divides evenly, the number is not prime. If none does, it is prime.

```java
class Solution {
    public boolean isPrime(int n) {
        if (n <= 1) {
            return false;
        }

        for (int i = 2; i < n; i++) {
            if (n % i == 0) {
                return false;
            }
        }

        return true;
    }
}
```

- **Time:** O(n) for this beginner-friendly version.
- **Auxiliary space:** O(1).
- **Important:** Return false when a divisor is found. Do not count non-divisors as proof of primality.
- **Learning note:** We discussed the square-root optimization, but you preferred to first understand the basic approach.

## 2. Count Prime Numbers Till N

**Problem:** Count how many prime numbers occur in the requested range.

**Basic idea:** Check each candidate number and count it only if it is prime. Reuse the prime-checking logic above.

**Important range detail:** Read the statement carefully to determine whether the range is up to and including `N`, or strictly less than `N`. These are different definitions. LeetCode 204 uses primes strictly less than `n`: https://leetcode.com/problems/count-primes/

- **Status:** We discussed the problem and attempted code, but a correct final implementation and accepted test result were not confirmed.
- **Mistakes from the attempted code:** `c =+ 1` assigns positive one; it does not increment. Use `c++` or `c += 1`. Also, checking only whether `n % i != 0` does not establish that `n` is prime; a single divisor is enough to reject it.

## 3. GCD of Two Numbers

**Problem:** Find the greatest positive integer that divides both numbers exactly.

**Key idea — Euclidean algorithm:** Keep replacing the pair `(a, b)` with `(b, a % b)`. When the remainder becomes zero, the other number is the GCD.

```java
class Solution {
    public int gcd(int a, int b) {
        while (b != 0) {
            int r = a % b;
            a = b;
            b = r;
        }

        return a;
    }
}
```

**Dry run:** For `a = 48`, `b = 18`:

| a | b | a % b |
|---:|---:|---:|
| 48 | 18 | 12 |
| 18 | 12 | 6 |
| 12 | 6 | 0 |

When `b` becomes 0, the GCD is **6**.

- **Time:** O(log(min(a, b))) for positive inputs.
- **Auxiliary space:** O(1).
- **Your understanding:** You described the repeated-remainder process correctly.

## 4. LCM of Two Numbers

**Problem:** Find the smallest positive number divisible by both given numbers.

**Key formula:**

`LCM(a, b) = (a / GCD(a, b)) * b`

Divide before multiplying to reduce the chance of integer overflow.

```java
class Solution {
    public int lcm(int a, int b) {
        if (a == 0 || b == 0) {
            return 0;
        }

        int x = a;
        int y = b;

        while (y != 0) {
            int r = x % y;
            x = y;
            y = r;
        }

        return Math.abs((a / x) * b);
    }
}
```

- **Time:** O(log(min(a, b))) because the GCD calculation dominates.
- **Auxiliary space:** O(1).
- **Your learning note:** We discussed using GCD to calculate LCM. The formula is the main takeaway.

## Progress note

Prime checking, prime counting, GCD, and LCM were discussed. Do not treat all four as fully completed: prime counting still needs a corrected, tested solution, and independent final submissions for the others were not confirmed.
