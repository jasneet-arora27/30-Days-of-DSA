# 🚀 Day 26: Advanced Topics - Basics 🚀

Today, we dive into two crucial advanced topics: **Bit Manipulation** and **Greedy Algorithms**. These topics are extremely important in solving a variety of complex problems efficiently. Let’s make this learning journey fun and engaging with emojis, examples, and a simple approach! 😊

<hr>

## 💡 1. Bit Manipulation

**Bit manipulation** involves using **bitwise operators** to solve problems. Computers store data in binary (0s and 1s), and by manipulating these bits, we can often solve problems much faster and with less space. Bit manipulation is efficient and widely used in algorithm design, especially for optimization and problem-solving challenges.

### 🧑‍💻 Common Bitwise Operators:

1. **AND (`&`):** Compares two bits; both must be 1 to return 1.
   - `1 & 1 = 1, 1 & 0 = 0`
2. **OR (`|`):** Compares two bits; if at least one is 1, it returns 1.
   - `1 | 0 = 1, 0 | 0 = 0`
3. **XOR (`^`):** Compares two bits; returns 1 if the bits are different.
   - `1 ^ 0 = 1, 1 ^ 1 = 0`
4. **NOT (`~`):** Inverts all bits.
   - `~1 = 0, ~0 = 1`
5. **Left Shift (`<<`):** Shifts bits to the left, multiplying by powers of 2.
   - `2 <<strong 1 = 4` (shifts the bits of 2 to the left, making it 4)
6. **Right Shift (`>>`):** Shifts bits to the right, dividing by powers of 2.
   - `4 >> 1 = 2`

### 🔍 Where is Bit Manipulation Used?

- **Optimizing space and speed:** Using bits instead of regular integers allows for faster and more memory-efficient algorithms.
- **Finding unique elements:** XOR (`^`) is particularly useful in finding the **only unique number** in an array where every other number occurs twice. This is used in problems like **Single Number** below 👇.
- **Checking if a number is a power of 2:** Numbers that are powers of 2 have only one bit set to 1.

### 🖥️ Real-Life Example:

Think of bit manipulation like working with switches in an electric panel. Each switch (bit) can be either ON (1) or OFF (0). We can manipulate these switches to create different combinations, just like using bitwise operations to solve problems!

### 🔑 Key Tricks:

- **XOR:** A number XOR-ed with itself is 0 (`a ^ a = 0`), and a number XOR-ed with 0 is the number itself (`a ^ 0 = a`). This property is often used to find the unique number in an array.
- **AND:** To check if a number is even or odd, use `num & 1`. If the result is 1, the number is odd; if it’s 0, the number is even.

<hr>

## 🏆 2. Greedy Algorithms

**Greedy algorithms** make **locally optimal choices** at each step with the hope of finding a global optimum. They are often used to solve **optimization problems** where we aim to maximize or minimize certain values.

### 🔧 How Greedy Algorithms Work:

1. At each step, choose the best option available **without considering future consequences**.
2. Once a choice is made, it cannot be changed.
3. Greedy algorithms don’t always guarantee the best solution but are efficient in many cases.

### 🌟 Common Use Cases:

- **Scheduling:** Where tasks need to be scheduled in the shortest amount of time (e.g., **Activity Selection Problem**).
- **Huffman Encoding:** For optimal data compression.
- **Minimum Spanning Tree:** Like **Kruskal’s Algorithm** or **Prim’s Algorithm** for connecting nodes in a graph with minimal total weight.

### 🖥️ Real-Life Example:

Imagine picking up coins 💰 along a path. A greedy approach would be to always pick the largest coin at every step without thinking about future steps. It might not always give us the best overall amount, but it’s a quick way to accumulate some value.

### 🔑 Key Characteristics:

- **Greedy choice property:** A global optimum can be arrived at by making a locally optimal choice.
- **Optimal substructure:** The problem can be broken down into subproblems, and solving those subproblems optimally leads to an optimal solution for the entire problem.

### 📝 Important Note:

<h4>Greedy algorithms don’t always guarantee the best solution. For example, in problems like the <strong>Traveling Salesman Problem (TSP)</strong>, a greedy algorithm might not always find the shortest path, but in some cases, greedy approaches work perfectly!</h4>

<hr>

## 🌟 Key Takeaways:

1. Bit Manipulation:
   - Mastering bitwise operators allows us to solve problems efficiently, especially in situations that involve **unique elements, masking, or binary representations**.
   - **XOR** is particularly useful in problems that involve pairs or duplicates.
2. Greedy Algorithms:
   - Greedy algorithms are fast and efficient for certain problems where local optimization leads to a global solution.
   - Always check if the problem has the greedy choice property and optimal substructure to ensure a greedy solution will work.

<hr>

## 🎯 Final Thoughts:

Advanced topics like **Bit Manipulation and Greedy Algorithms** might seem tricky at first, but with practice, one can see patterns in problems where these techniques apply. These strategies are like secret weapons 🛡️, enabling us to solve complex problems with elegance and speed!

Keep practicing, and you’ll see how powerful these concepts are in real-life coding scenarios! 💪

## 📚 What's Next?

Now that now that we've covered the concepts, try applying them to the following practice problems:

- **Easy:** [Single Number](https://leetcode.com/problems/single-number/)
- **Medium:** [Decode Ways](https://leetcode.com/problems/decode-ways/)
- **Hard:** [N-Queens II](https://leetcode.com/problems/n-queens-ii/)
