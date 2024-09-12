# 🚀 Day 10: Heaps - Basics🚀

Today’s topic is **Heaps**, a particularly intriguing data structure that is crucial in various algorithms. Let's dive in and explore this structure in an exciting and engaging way! 🎉

<hr>

## 🌳 What is a Heap?

A heap is a binary tree that satisfies the heap property. It's typically used to implement priority queues.

**There are two types of heaps:**

- **Min-Heap 📉**
- **Max-Heap 📈**

<hr>

## 🔍 Types of Heaps:

### 1. Min-Heap 📉

- In a **min-heap**, the value of each node is **greater than or equal to** the value of its parent.

- The **smallest element** is at the root.

  **Use Case:** Useful when you need to quickly access the minimum element, such as in scheduling or simulation problems.

**Example:**

```
    1
   / \
  3   5
 / \
4   8
```

### 2. Max-Heap 📈

- In a **max-heap**, the value of each node is **less than** or equal to the value of its parent.

- The **largest element** is at the root.

  **Use Case:** Useful for problems where you need to quickly access the largest element, like priority queues for task scheduling.

Example:

```
    9
   / \
  7   6
 / \
4   3
```

<hr>

## ⚙️ Heap Operations

Heaps support the following primary operations efficiently:

### 1. Insert 🛠️

- Add an element to the heap and maintain the heap property.
- Time complexity: **$O(log n)$**

### 2. Delete (Remove the root) 🚮

- Remove the root node (the minimum or maximum value) and reheapify the structure.
- Time complexity: **$O(log n)$**

### 3. Peek (Access the root) 👀

- Access the root element without removing it.
- Time complexity: **$O(1)$**

<hr>

## 🛠️ Building a Heap (Heapify)

Building a heap from an unsorted array is known as heapifying. The process involves adjusting the positions of elements to satisfy the heap property.

- **Heapify** involves comparing a node with its children and swapping it with the smaller (in a min-heap) or larger (in a max-heap) child to maintain the structure.
- **Heapify an array**: Time complexity is $O(n)$.

<hr>

## 🌟 Applications of Heaps

### 1. Priority Queues ⏳

- Heaps are often used to implement priority queues where the highest (or lowest) priority element can be accessed quickly.

### 2. Sorting (Heap Sort) 📊

- You can use heaps to implement a sorting algorithm known as heap sort. It has a time complexity of O(n log n).

### 3. Finding Kth Largest/Smallest Element 🏆

- Heaps are great for problems like finding the Kth largest or smallest element in an array (which you’ll practice today!).

### 4. Efficient Merging 🛠️

- Heaps are used in algorithms to efficiently merge multiple sorted lists or arrays, such as in the merge step of merge sort.

<hr>

## Here how you can implement your own Heap and it's operations 💻

**_The implementation of a Max-Heap is nearly identical to a Min-Heap. The only difference is in the comparison: for Max-Heap, we ensure the parent node is greater than its children, while for Min-Heap, the parent node is smaller.In this examples we have implemented the Min-Heap and try the Max-Heap by your own_**

- [C++](#cpp)
- [Java](#java)

### C++

```cpp
    #include <iostream>
    #include <vector>

    using namespace std;

    class MinHeap {
        vector<int> heap;

        void heapifyUp(int index) {
            int parent = (index - 1) / 2;
            if (index && heap[parent] > heap[index]) {
                swap(heap[index], heap[parent]);
                heapifyUp(parent);
            }
        }

        void heapifyDown(int index) {
            int left = 2 * index + 1;
            int right = 2 * index + 2;
            int smallest = index;

            if (left < heap.size() && heap[left] < heap[smallest])
                smallest = left;
            if (right < heap.size() && heap[right] < heap[smallest])
                smallest = right;

            if (smallest != index) {
                swap(heap[index], heap[smallest]);
                heapifyDown(smallest);
            }
        }

    public:
        void insert(int value) {
            heap.push_back(value);
            heapifyUp(heap.size() - 1);
        }

        void deleteRoot() {
            if (heap.size()) {
                heap[0] = heap.back();
                heap.pop_back();
                heapifyDown(0);
            }
        }

        int peek() {
            if (heap.size())
                return heap[0];
            return -1; // Return -1 if heap is empty
        }

        void printHeap() {
            for (int i : heap)
                cout << i << " ";
            cout << endl;
        }
    };

    int main() {
        MinHeap h;
        h.insert(3);
        h.insert(1);
        h.insert(5);
        h.insert(4);
        h.insert(8);

        cout << "Heap: ";
        h.printHeap();

        cout << "Peek: " << h.peek() << endl;

        h.deleteRoot();
        cout << "Heap after deleting root: ";
        h.printHeap();

        return 0;
    }

```

### Java

```java
    import java.util.ArrayList;

    class MinHeap {
        private ArrayList<Integer> heap;

        public MinHeap() {
            this.heap = new ArrayList<>();
        }

        private void heapifyUp(int index) {
            int parent = (index - 1) / 2;
            if (index > 0 && heap.get(parent) > heap.get(index)) {
                int temp = heap.get(index);
                heap.set(index, heap.get(parent));
                heap.set(parent, temp);
                heapifyUp(parent);
            }
        }

        private void heapifyDown(int index) {
            int left = 2 * index + 1;
            int right = 2 * index + 2;
            int smallest = index;

            if (left < heap.size() && heap.get(left) < heap.get(smallest)) {
                smallest = left;
            }
            if (right < heap.size() && heap.get(right) < heap.get(smallest)) {
                smallest = right;
            }

            if (smallest != index) {
                int temp = heap.get(index);
                heap.set(index, heap.get(smallest));
                heap.set(smallest, temp);
                heapifyDown(smallest);
            }
        }

        public void insert(int value) {
            heap.add(value);
            heapifyUp(heap.size() - 1);
        }

        public void deleteRoot() {
            if (!heap.isEmpty()) {
                heap.set(0, heap.remove(heap.size() - 1));
                heapifyDown(0);
            }
        }

        public int peek() {
            if (!heap.isEmpty()) {
                return heap.get(0);
            }
            return -1;
        }

        public void printHeap() {
            System.out.println(heap);
        }
    }

    public class Main {
        public static void main(String[] args) {
            MinHeap h = new MinHeap();
            h.insert(3);
            h.insert(1);
            h.insert(5);
            h.insert(4);
            h.insert(8);

            h.printHeap();
            System.out.println("Peek: " + h.peek());

            h.deleteRoot();
            h.printHeap();
        }
    }

```

<hr>

## 📚 What's Next?

Now that we've covered the concepts, try applying them to the following practice problems:

- **Easy:** [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)
- **Medium:** [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
- **Hard:** [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)
