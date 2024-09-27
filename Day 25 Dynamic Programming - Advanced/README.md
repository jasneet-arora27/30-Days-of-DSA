# 🚀Day 25: Dynamic Programming - Advanced🚀

Today we’re advancing further into the powerful world of **Dynamic Programming (DP)**, covering two classic DP problems: **Knapsack** and **Longest Common Subsequence (LCS)**. These problems frequently show up in coding interviews and competitive programming. So, let's break them down step by step! 🚀

<hr>

## 🧠 What is Advanced Dynamic Programming?

**Advanced Dynamic Programming** focuses on solving problems where we need to make optimal choices under certain constraints. These problems often involve combining solutions from smaller subproblems to build up to the final solution.

Two of the most famous DP problems are:

1. **Knapsack Problem 🎒**
2. **Longest Common Subsequence (LCS) 🔗**

These problems challenge our ability to apply dynamic programming effectively. Let’s dive deeper!

<hr>

## 🎒 1. Knapsack Problem

The Knapsack Problem is one of the most classic DP problems. The idea is simple: we are given a set of items, each with a weight and a value. Our task is to maximize the value of the items we carry in a knapsack with a limited weight capacity.

**Problem Types:**

- **0/1 Knapsack:** We can either take an item or leave it.
- **Fractional Knapsack:** We can take fractions of an item (solved using greedy algorithms, not DP).

For DP, we focus on the **0/1 Knapsack** problem.

### 🔧 How it Works:

1. We have an array of items, each with a weight and a value.
2. We need to decide whether to take or skip each item to maximize the value of items without exceeding the knapsack's weight capacity.

### 🖥️ Example:

Imagine we’re packing for a hiking trip 🏞️. We have limited space in our backpack, but we want to bring items like food, water, and gear. Each item has a weight and a value (how much we need it). We can’t carry everything, so we must decide which items to bring to maximize our survival chances while keeping our backpack light.

**DP Table:**

- Rows: represent the items.
- Columns: represent the weight capacity of the knapsack.
- Entry at `dp[i][w]` means the maximum value obtainable with `i` items and a knapsack of capacity `w`.

<hr>

## 🔗 2. Longest Common Subsequence (LCS)

The **Longest Common Subsequence (LCS)** problem is about finding the longest sequence that appears in the same order in both given sequences. This is different from finding the Longest Common Substring, as the characters in the subsequence don’t need to be contiguous.

### 🔧 How it Works:

1. We have two sequences (or strings), and we need to find the longest subsequence that is common to both.
2. The key here is to compare the characters of both sequences and keep track of the length of the common subsequence.

### 🖥️ Example:

Imagine we're comparing DNA sequences 🧬. The goal is to find the **longest sequence of genes** that is common to both DNA strands. This helps in studying similarities between species or individuals.

**DP Table:**

- **Rows**: represent the characters of the first string.
- **Columns**: represent the characters of the second string.
- **Entry** at `dp[i][j]` represents the length of the LCS up to characters `i` of the first string and `j` of the second string.

<hr>

## ⚔️ Common Dynamic Programming Patterns

Let’s explore two famous patterns for solving dynamic programming problems, which often come up in interviews.

<hr>

## 🛠️ 1. Knapsack Problem Pattern

This pattern is useful when dealing with problems where we need to make decisions about selecting items under certain constraints (usually related to maximizing value while staying within a weight or capacity limit).

Here are some common problem variants based on this pattern:

- **0/1 Knapsack:** Choose items to maximize value without exceeding a weight limit.
- **Subset Sum Problem:** Find a subset of numbers that sum up to a specific target.
- **Partition Problem:** Can the array be divided into two subsets with equal sum? (Like **Partition Equal Subset Sum** below 👇)

<hr>

## 🧑‍🔧 2. Longest Common Subsequence (LCS) Pattern

This pattern is common in problems where we need to compare **two sequences** and make decisions based on matching or mismatching elements. The goal is to find the **optimal alignment** or commonality between the sequences.

Common problems that use this pattern:

- **Longest Palindromic Subsequence:** Find the longest subsequence that is also a palindrome.
- **Edit Distance:** Minimize the number of edits to convert one string into another.
- **Wildcard Matching:** Match a pattern with **wildcards** to a string (like below 👇).

<hr>

## 💡 Key Insights:

- Dynamic Programming is a powerful technique that helps solve optimization problems by breaking them down into smaller subproblems.
- Two major categories of DP problems are knapsack-like problems, where we decide whether to include/exclude items, and sequence alignment problems, where we compare two sequences to find optimal alignments.
- Problems like **Knapsack** and **LCS** lay the foundation for solving more complex DP challenges.

<hr>

## Final Thoughts:

As we dive deeper into DP, it’s crucial to recognize the problem patterns and apply the right DP approach, whether it’s memoization (top-down) or tabulation (bottom-up). The more problems we practice, the more intuitive these patterns will become. Keep pushing forward! 🌟

## 📚 What's Next?

Now that we've covered the concepts, try applying them to the following practice problems:

- **Easy:** [Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)
- **Medium:** [Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/)
- **Hard:** [Wildcard Matching](https://leetcode.com/problems/wildcard-matching/)
