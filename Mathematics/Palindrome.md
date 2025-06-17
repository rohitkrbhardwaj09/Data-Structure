# 🔁 Palindrome Number Check
### 🧠 Problem Statement

- **Input:** A non-negative integer n.

- **Task:** Check whether n is a palindrome.

- A palindrome number reads the same forward and backward.

- **Examples:**

  - ✅ 78987 → Palindrome

  - ✅ 8668 → Palindrome

  - ✅ 7 → Palindrome (single-digit)

  - ❌ 21 → Not a palindrome

  - ❌ 367 → Not a palindrome
 
---

### ✅ Approach: Reverse the Number
- Reverse the digits of n.

- Compare reversed number with original:

  - If same → return true

  - Else → return false
 
---

### 🔁 How to Reverse a Number
1. Initialize reverse = 0.

2. Copy n into a temporary variable temp (to preserve original n).

3. Loop until temp > 0:

4. Get last digit: lastDigit = temp % 10

5. Update reverse: reverse = reverse * 10 + lastDigit

6. Remove last digit: temp = temp / 10 (integer division)

---

### 🔢 Example: n = 4533
- Initial values: reverse = 0, temp = 4533
| Iteration | `lastDigit` | `reverse`             | `temp` |
| --------- | ----------- | --------------------- | ------ |
| 1         | 3           | `0 * 10 + 3 = 3`      | `453`  |
| 2         | 3           | `3 * 10 + 3 = 33`     | `45`   |
| 3         | 5           | `33 * 10 + 5 = 335`   | `4`    |
| 4         | 4           | `335 * 10 + 4 = 3354` | `0`    |

- Compare: n = 4533 vs. reverse = 3354 → ❌ Not a palindrome

---

### 🧑‍💻 Code Skeleton
```java
package dsa.mathematics;

import java.util.Scanner;

public class Palindrome {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter number to check Palindrome: ");
		int num = sc.nextInt();
		
		
		boolean b = isPalindrome(num);
		
		if(b) {
			System.out.println(num+" is a palindrome number");
		}else {
			System.out.println(num+" is not a palindrome number");
		}
		
		sc.close();

	}

	private static boolean isPalindrome(int num) {
		
		int temp = num;
		int reverse = 0;
		
		while(num>0) {
			int reminder = num % 10;
			reverse = reverse * 10 + reminder;
			num = num / 10;
		}
			
		if(reverse==temp) {
			return true;
		}else {
			return false;
		}
	}
}
```

--- 

### ⏱️ Time Complexity
- Each digit is processed once.

- Let d be the number of digits in n.

- **Time Complexity: Θ(d)**

