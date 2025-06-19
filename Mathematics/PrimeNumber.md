# Prime Numbers – Comprehensive Notes

---

## 1️⃣ Definition

An integer **n > 1** is **prime** if its only positive divisors are **1** and **n** itself.

* `2` is the **only even prime**; all other even numbers are composite.
* `1` is **neither** prime **nor** composite.

---

## 2️⃣ Quick Facts & Properties

| Property                   | Detail                                                |
| -------------------------- | ----------------------------------------------------- |
| Smallest prime             | 2                                                     |
| Only even prime            | 2                                                     |
| Prime density              | Roughly `n / ln(n)` primes ≤ n (Prime Number Theorem) |
| Coprime (Relatively prime) | Two numbers with GCD = 1                              |
| Twin primes                | Primes that differ by 2 (e.g. 11, 13)                 |
| Mersenne primes            | Primes of the form `2^p − 1` where `p` is prime       |
| Goldbach Conjecture        | Every even number > 2 is sum of two primes (unproven) |

### First 25 Primes

```
2, 3, 5, 7, 11, 13, 17, 19, 23, 29,
31, 37, 41, 43, 47, 53, 59, 61, 67, 71,
73, 79, 83, 89, 97
```

---

## 3️⃣ Classification of Natural Numbers

```
>1  →  Prime  │  Composite
 1  →  Neither prime nor composite
≤0  →  Not in “natural” prime discussion
```

---

## 4️⃣ Algorithms to Test Primality

### 4.1 🐌 Naive Trial Division (Up to n − 1)

```java
boolean isPrimeNaive(int n) {
    if (n <= 1) return false;
    for (int i = 2; i < n; i++)
        if (n % i == 0) return false;
    return true;
}
```

* **Time**: O(n)
* **Space**: O(1)

### 4.2 ⚡ Improved – Check Up to √n

```java
boolean isPrimeSqrt(int n) {
    if (n <= 1) return false;
    for (int i = 2; i * i <= n; i++)
        if (n % i == 0) return false;
    return true;
}
```

* **Time**: O(√n)
* **Space**: O(1)

### 4.3 🚀 6k ± 1 Optimization (Skip Multiples of 2 & 3)

```java
boolean isPrimeFast(int n) {
    if (n <= 1) return false;
    if (n <= 3) return true;           // 2 & 3 are prime
    if (n % 2 == 0 || n % 3 == 0) return false;

    for (int i = 5; i * i <= n; i += 6) {
        if (n % i == 0 || n % (i + 2) == 0)
            return false;
    }
    return true;
}
```

* **Idea**: All primes ≥ 5 are of the form **6k ± 1**.
* **Time**: ≈⅓ × √n (3× faster than plain √n loop)

### 4.4 🏎️ Sieve of Eratosthenes (Generate All Primes ≤ N)

```java
List<Integer> sieve(int N) {
    boolean[] isPrime = new boolean[N + 1];
    Arrays.fill(isPrime, true);
    isPrime[0] = isPrime[1] = false;

    for (int p = 2; p * p <= N; p++) {
        if (isPrime[p]) {
            for (int mult = p * p; mult <= N; mult += p)
                isPrime[mult] = false;
        }
    }
    List<Integer> primes = new ArrayList<>();
    for (int i = 2; i <= N; i++) if (isPrime[i]) primes.add(i);
    return primes;
}
```

* **Time**: O(N log log N)
* **Space**: O(N)
* **Use‑case**: Need all primes up to big N (e.g., competitive programming).

### 4.5 🔒 Deterministic Miller–Rabin (Large 64‑bit n)

For 64‑bit signed integers, a fixed set of bases `{2, 3, 5, 7, 11, 13, 17}` is sufficient for a deterministic result.

* **Time**: O(k · log³ n) (where k = #bases)
* **Space**: O(1)
* **Use‑case**: Cryptography & very large numbers.

---

## 5️⃣ Complexity Comparison

| Method                | Time           | Space | When to Use                 |
| --------------------- | -------------- | ----- | --------------------------- |
| Trial up to n‑1       | O(n)           | O(1)  | Educational, very small n   |
| Up to √n              | O(√n)          | O(1)  | Simple & decent for n ≤ 1e9 |
| 6k ± 1                | ≈⅓·√n          | O(1)  | Faster single checks        |
| Sieve of Eratosthenes | O(N log log N) | O(N)  | All primes up to N (≤ 10⁷)  |
| Miller–Rabin          | O(k·log³ n)    | O(1)  | Very large n (≥ 10¹²)       |

---

## 6️⃣ Code Snippet – Unified Primality Tester

```java
public class Primality {
    /** Returns true if n is prime (32‑bit range) */
    public static boolean isPrime(int n) {
        if (n <= 1) return false;
        if (n <= 3) return true;
        if (n % 2 == 0 || n % 3 == 0) return false;
        for (int i = 5; i * i <= n; i += 6) {
            if (n % i == 0 || n % (i + 2) == 0) return false;
        }
        return true;
    }

    public static void main(String[] args) {
        int[] nums = {13, 14, 101, 121};
        for (int n : nums)
            System.out.println(n + " → " + isPrime(n));
    }
}
```

---

## 7️⃣ Practical Tips

1. **First filter** by small primes (2, 3, 5, 7) before heavy tests.
2. Pre‑compute primes with a sieve for multiple queries.
3. Use **long** / **BigInteger** where overflow is possible.
4. For cryptographic sizes (> 10¹⁵), use probabilistic tests (Miller–Rabin, Baillie–PSW).

---
