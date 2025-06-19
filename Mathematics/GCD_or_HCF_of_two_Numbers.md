# GCD (Greatest Common Divisor) - Notes

## Problem Statement

Given two integers **A** and **B**, find the **greatest number that divides both** of them.

---

## Examples

* GCD(4, 6) = 2
* GCD(100, 200) = 100
* GCD(15, 30) = 15
* GCD(9, 10) = 1 *(Only 1 common factor, but both are not prime)*

---

## Real-Life Analogy

* If you make a rectangle of size `A x B`, the GCD is the size of **largest square tile** that can tile the rectangle perfectly.

---

## Naive Approach

1. Start from `min(A, B)` and iterate downwards.
2. Check if the number divides both A and B.
3. First such number is the GCD.

### Time Complexity

* Worst case: O(min(A, B))

---

## Euclidean Algorithm (Efficient)

### Basic Idea

If A > B, then:

```
GCD(A, B) = GCD(A - B, B)
```

Keep subtracting the smaller from the larger until both are equal.

### Optimized Idea (Modulo Version)

```
GCD(a, b):
    if b == 0:
        return a
    else:
        return GCD(b, a % b)
```

* This is based on the fact that the GCD does not change when the larger number is replaced by the remainder of dividing the larger by the smaller.

### Dry Run

```
GCD(12, 15)
=> GCD(15, 12)  // swap if needed
=> GCD(12, 3)   // 15 % 12 = 3
=> GCD(3, 0)    // 12 % 3 = 0
=> return 3
```

---

## Java Implementation

```java
public class GCD {
    static int gcd(int a, int b) {
        if (b == 0)
            return a;
        return gcd(b, a % b);
    }

    public static void main(String[] args) {
        int a = 12, b = 15;
        System.out.println("GCD of " + a + " and " + b + " is " + gcd(a, b));
    }
}
```

---

## Time & Space Complexity

* **Time Complexity**: O(log(min(a, b)))
* **Space Complexity**:

  * Recursive: O(log(min(a, b))) due to call stack
  * Iterative (if implemented): O(1)

---

## Summary

* GCD helps in number theory, simplifying fractions, and solving problems involving tiling or synchronization.
* Euclid's Algorithm is the most efficient way to compute GCD.
* Modulo-based version is better than repeated subtraction.
