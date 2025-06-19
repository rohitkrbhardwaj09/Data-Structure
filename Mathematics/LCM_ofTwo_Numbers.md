# Greatest Common Divisor (GCD) and Least Common Multiple (LCM) Notes

---

> **FORMULA** : (a x b) = gcd(a,b) x lcm(a,b) => lcm(a,b) = (a x b) / gcd(a,b);

## ✅ Problem Statement

We are given two integers `a` and `b`. Our task is to:

* Find the **GCD** (Greatest Common Divisor)
* Find the **LCM** (Least Common Multiple)

---

## 🧮 What is GCD?

The **GCD** of two numbers is the largest number that divides both `a` and `b`.

### 🔹 Examples:

* GCD(4, 6) = 2
* GCD(100, 200) = 100
* GCD(15, 30) = 15
* GCD(9, 10) = 1 (no common factor except 1)

### 🧠 Real-life Analogy:

If you have a rectangle of size `a × b`, GCD is the largest square tile that can tile the rectangle without cutting.

---

## 🐌 Naive Approach (GCD)

* Start from min(a, b)
* Decrease one-by-one until a number is found that divides both a and b

```java
int gcd(int a, int b) {
    int res = Math.min(a, b);
    while (res > 0) {
        if (a % res == 0 && b % res == 0) {
            break;
        }
        res--;
    }
    return res;
}
```

### Time Complexity:

* O(min(a, b))

---

## ⚡ Euclidean Algorithm (GCD)

**Concept**: `gcd(a, b) = gcd(b, a % b)`

```java
int gcd(int a, int b) {
    if (b == 0) return a;
    return gcd(b, a % b);
}
```

### Time Complexity:

* O(log(min(a, b)))

---

## 🌟 LCM - Least Common Multiple

The **LCM** of two numbers is the smallest number divisible by both `a` and `b`.

### 🔹 Examples:

* LCM(4, 6) = 12
* LCM(12, 15) = 60
* LCM(2, 8) = 8 (one divides the other)
* LCM(9, 10) = 90 (coprime case)

---

## 🐌 Naive Approach (LCM)

Start from max(a, b) and keep increasing by 1 until you find a number divisible by both `a` and `b`.

```java
int lcm(int a, int b) {
    int res = Math.max(a, b);
    while (true) {
        if (res % a == 0 && res % b == 0) {
            break;
        }
        res++;
    }
    return res;
}
```

### Time Complexity:

* O(a × b - max(a, b)) → Worst-case

---

## ⚡ Efficient LCM using GCD

**Formula**: `LCM(a, b) = (a × b) / GCD(a, b)`

```java
int gcd(int a, int b) {
    if (b == 0) return a;
    return gcd(b, a % b);
}

int lcm(int a, int b) {
    return (a * b) / gcd(a, b);
}
```

### Time Complexity:

* O(log(min(a, b))) → due to GCD

---

Let me know if you want examples, dry run or this explanation translated in Hindi/Hinglish format.
