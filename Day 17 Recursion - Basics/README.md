# 🌟 Day 17: Recursion - Basics 🌟

Today we will be diving into the fundamentals of **Recursion**, which is a powerful technique that allows a function to call itself and solve problems in a more elegant and compact way.

<hr>

## 🔄 What is Recursion?

**Recursion** is when a function calls **itself** to break down complex problems into smaller, more manageable pieces. Each recursive call solves a smaller version of the original problem, and once the smallest version is solved, the results propagate back up the call chain.

It’s like "**Russian nesting dolls**" 🪆 — each doll contains a smaller doll inside until you reach the tiniest one.

<hr>

## 🚩 Key Components of Recursion:

### 1. Base Case (Exit Condition) 🛑:

- This is the condition where the recursion stops. Without a base case, the function would call itself infinitely, leading to a stack overflow.
- For example, in a factorial calculation, when `n == 0`, the recursion stops.

### 2. Recursive Case 🔄:

- This is where the function calls itself with a smaller input, gradually working toward the base case.
- For example, in a factorial calculation, the recursive case would call `factorial(n-1)` until `n == 0`.

<hr>

## 🛠️ How Recursion Works (Simple Example: Factorial)

Factorial of a number `n` i.e. `(n!)` is defined as:

- `n! = n * (n-1) * (n-2) * ... * 1`
- Example: `5! = 5 * 4 * 3 * 2 * 1`

Let's see how we would write this using recursion in different programming languages:

- [C++](#cpp)
- [Java](#java)

#### C++

```cpp
    int factorial(int n) {
        // Base case: if n is 0, return 1
        if (n == 0) {
            return 1;
        }
        // Recursive case: multiply n by factorial of n-1
        return n * factorial(n - 1);
    }
```

#### Java

```java
    public class Factorial {
        public static int factorial(int n) {
            // Base case: if n is 0, return 1
            if (n == 0) {
                return 1;
            }
            // Recursive case: multiply n by factorial of n-1
            return n * factorial(n - 1);
        }

        public static void main(String[] args) {
            System.out.println(factorial(5));  // Output: 120
        }
    }

```

- Step-by-step execution:
  - `factorial(5)` calls `factorial(4)`
  - `factorial(4)` calls `factorial(3)`
  - `factorial(3)` calls `factorial(2)`
  - `factorial(2)` calls `factorial(1)`
  - `factorial(1)` calls `factorial(0)` which returns `1` (base case)
  - Then, the results propagate back:
    - `factorial(1) = 1 * 1 = 1`
    - `factorial(2) = 2 * 1 = 2`
    - `factorial(3) = 3 * 2 = 6`
    - `factorial(4) = 4 * 6 = 24`
    - `factorial(5) = 5 * 24 = 120`

This concept can be used to solve many complex problems by breaking them into smaller, solvable parts!

<hr>

## 🌀 Tail Recursion - What’s Different?

**Tail recursion** is a special type of recursion where **the recursive call is the last** thing the function does. There are no pending operations after the recursive call, which allows the compiler to optimize and avoid stack overflow.

- **Real-life analogy:** Imagine you are cleaning dishes 🧼. If you finish cleaning one dish and immediately start cleaning the next, you don’t need to remember anything about the previous dishes.

In contrast, regular recursion has to remember the steps and intermediate calculations.

## ⚡ Example of Tail Recursion (Sum of N Numbers)

Here’s how a function that calculates the sum of the first n natural numbers can be written using tail recursion:

- [C++](#cpp)
- [Java](#java)

#### C++

```cpp
    int sumTail(int n, int result = 0) {
        if (n == 0) {
            return result; // Base case
        }
        return sumTail(n - 1, result + n); // Recursive case
    }
```

#### Java

```java
    public class TailRecursionSum {
        public static int sumTail(int n, int result) {
            if (n == 0) {
                return result;  // Base case
            }
            return sumTail(n - 1, result + n);  // Recursive case
        }

        public static void main(String[] args) {
            System.out.println(sumTail(5, 0));  // Output: 15
        }
    }

```

- Execution steps for `sumTail(5)`:
  - Call: `sumTail(5, 0)` → `sumTail(4, 5)`
  - Call: `sumTail(4, 5)` → `sumTail(3, 9)`
  - Call: `sumTail(3, 9)` → `sumTail(2, 12)`
  - Call: `sumTail(2, 12)` → `sumTail(1, 14)`
  - Call: `sumTail(1, 14)` → `sumTail(0, 15)`
  - Base case reached, returns `15`.

<hr>

## ✨ Why Recursion is Powerful:

- **Simplifies complex problems:** Problems like **tree traversals**, **graph algorithms**, and **backtracking** (like solving Sudoku or the N-Queens problem) become easier to understand.
- **Elegant code:** The code is often shorter and more readable.
- **Real-world analogy:** Think of a **to-do list** 📝 where each task depends on another. You start solving tasks in order, one after the other, like how recursion breaks problems into smaller tasks.

<hr>

## 🎯 Key Points to Remember:

1. **Base case** is essential to stop the recursion.
2. Be mindful of **stack overflow** when recursion depth is too deep.
3. Try converting regular recursion into tail recursion for optimization.
4. Recursion can be tricky at first but becomes intuitive with practice.

<hr>

## 📚 What's Next?

Now that we've covered the concepts, try applying them to the following practice problems:

- **Medium:**
  - [Permutations](https://leetcode.com/problems/permutations/)
  - [Combination Sum](https://leetcode.com/problems/combination-sum/)