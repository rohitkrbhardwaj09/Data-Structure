# 🔢 Trailing Zeros in Factorial (n!)

## 📘 Problem Statement
Aapko ek number `n` diya gaya hai. Aapko `n!` (factorial of n) ke **end mein kitne zeros** hain — yeh count karna hai.

---

## ❓ Trailing Zero Kya Hota Hai?

**Trailing zero** matlab:
- Factorial ke end mein kitne **0** lage hain.
- Example:
  - 5! = 1×2×3×4×5 = 120 → 1 trailing zero
  - 10! = 3628800 → 2 trailing zeros
  - 100! → 24 trailing zeros
 
---

## 🧠 Concept Simplified

Zero tab aata hai jab number **10 ka multiple** ho.

- 10 = 2 × 5
- Factorial mein `2` bahut hoti hain.
- Lekin `5` limited hoti hai.

🟢 Isliye:
```
Trailing Zeros = Kitni baar 5 aayi hai in n!
```
---

## ✅ Formula (Efficient Approach)

Har `5`, `25`, `125`, ... number ek extra `5` contribute karta hai.

```txt
Zeros = n / 5 + n / 25 + n / 125 + ...
```

👉 Jab tak n / powerOf5 > 0, tab tak add karte jao.

#### Example: n = 100
```
100 / 5   = 20
100 / 25  = 4
100 / 125 = 0 ❌

Total = 20 + 4 = 24 trailing zeros ✅
```

### 💻 Java Code (Iterative)
```
public class TrailingZeros {
    public static int countTrailingZeros(int n) {
        int count = 0;
        for (int i = 5; i <= n; i *= 5) {
            count += n / i;
        }
        return count;
    }

    public static void main(String[] args) {
        int n = 100;
        System.out.println("Trailing zeros in " + n + "! = " + countTrailingZeros(n));
    }
}
```

### ⏱️ Time & Space Complexity
| Type          | Complexity   |
| ------------- | ------------ |
| Time          | Θ(log₅ n)    |
| Space         | Θ(1)         |
| Overflow Risk | ❌ Nahi hai   |
| Efficiency    | ✅ Bahut Fast |

--- 

### 📌 Points to Remember
- Trailing zero = 2 × 5, lekin 2 toh hamesha zyada hoti hain.

- Sirf 5 count karni hoti hai.

- n / 5 + n / 25 + n / 125 + ... use karke fast answer milta hai.

- Kabhi bhi n! calculate mat karo (overflow aa sakta hai).
📌 Points to Remember
