# 🔢 Count the Number of Digits in an Integer
### 🧠 Problem Statement
**Given a positive integer x, count how many digits it contains.**
**Examples:**

- x = 9235 → output: 4

- x = 38 → output: 2

- x = 7 → output: 1

> Constraint: x > 0

---

### ✅ Approach: Division by 10

- Continuously divide the number by 10 to remove the last digit.

- Keep a counter that increments with each division.

- Stop when x becomes 0.

--- 

### 🔁 Step-by-Step Process

- Initialize a counter variable result = 0.

- While x > 0:

- Do x = x / 10 (integer division).

- Increment result by 1.

- Return result.

---

### 🧮 Example Walkthrough

Given x = 789:

Iteration 1: x = 789 → 78, result = 1

Iteration 2: x = 78 → 7, result = 2

Iteration 3: x = 7 → 0, result = 3

Final output: 3

---

### 🧑‍💻 Code Skeleton 
```java
int countDigits(int x) {
    int result = 0;
    while (x > 0) {
        x = x / 10;
        result++;
    }
    return result;
}
```

---

### ⏱️ Time Complexity
- Let d be the number of digits in the input number.

- Loop runs d times.

- Time Complexity: Θ(d)
