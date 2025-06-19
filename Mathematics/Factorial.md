# 🔢 Factorial of a Number
### 📘 Definition
> The factorial of a number n (denoted as n!) is the product of all positive integers less than or equal to n.

- Defined only for n ≥ 0.

### 🧮 Examples:
0! = 1  
1! = 1  
4! = 1 × 2 × 3 × 4 = 24  
6! = 1 × 2 × 3 × 4 × 5 × 6 = 720

### ✅ Iterative Approach
**💡 Idea:**
Initialize result = 1

Multiply all numbers from 2 to n in a loop.

### 🔁 Example for n = 5
ini
result = 1  
i = 2 → result = 1 × 2 = 2  
i = 3 → result = 2 × 3 = 6  
i = 4 → result = 6 × 4 = 24  
i = 5 → result = 24 × 5 = 120

🧑‍💻 Code (C++/Java style)
```
int factorial(int n) {
    int result = 1;
    for (int i = 2; i <= n; i++) {
        result *= i;
    }
    return result;
}
```

### ⏱️ Time and Space Complexity
Time: Θ(n)

Auxiliary Space: Θ(1) (constant extra space)

### 🔁 Recursive Approach
**💡 Idea:**
Use the mathematical property:

n! = n × (n - 1)!
🧑‍💻 Code (C++/Java style)
```
int factorial(int n) {
    if (n == 0) return 1;
    return n * factorial(n - 1);
}
```

### 🧠 Recursion Stack for factorial(5)
```
factorial(5)
→ 5 × factorial(4)
→ 5 × (4 × factorial(3))
→ 5 × (4 × (3 × factorial(2)))
→ 5 × (4 × (3 × (2 × factorial(1))))
→ 5 × (4 × (3 × (2 × (1 × factorial(0)))))
→ 5 × 4 × 3 × 2 × 1 × 1 = 120
```

### ⏱️ Time and Space Complexity
Time: Θ(n)

Auxiliary Space: Θ(n) due to call stack

Less efficient due to recursion overhead

### ⚖️ Comparison
| Method    | Time Complexity | Space Complexity | Pros                 | Cons                              |
| --------- | --------------- | ---------------- | -------------------- | --------------------------------- |
| Iterative | Θ(n)            | Θ(1)             | Efficient, simple    | Slightly less elegant             |
| Recursive | Θ(n)            | Θ(n)             | Elegant, clean logic | Stack overflow risk for large `n` |


Let me know if you'd like:

- Python version of both implementations

- Visualization using call stack diagram

- Practice problems related to factorials (like trailing zeroes, large factorial, etc.)
