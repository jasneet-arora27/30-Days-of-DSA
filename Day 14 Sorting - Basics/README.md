# 🚀 Day 14: Sorting - Basics 🚀

Today, we dive into the fundamental **sorting algorithms**: **Bubble Sort** and **Insertion Sort**. These algorithms are crucial for understanding more complex sorting methods and provide a solid foundation in sorting techniques. Let's get into it! 🌟

<hr>

## 🧩 Bubble Sort

### Concept:

Bubble Sort is a straightforward comparison-based sorting algorithm. It works by repeatedly stepping through the list, comparing adjacent elements, and swapping them if they are in the wrong order. This process "bubbles" the largest unsorted element to its correct position in each iteration.

### How It Works:

1. Start with the first element of the array.
2. Compare it with the next element.
3. Swap them if the first element is greater than the second.
4. Repeat this process for each pair of adjacent elements.
5. Continue this until the end of the array.
6. Repeat the entire process for the remaining unsorted elements.

**Visual Example:**

Imagine you have a row of books sorted by height, but they are out of order. Bubble Sort would involve comparing each pair of books and swapping them if necessary until all books are in the correct order.

### Steps:

1. Compare adjacent books.
2. Swap if the first book is taller.
3. Move to the next pair.
4. Repeat until all books are sorted.

### Pros:

- Simple to understand and implement. 🧩

### Cons:

- Inefficient for large datasets with a time complexity of $O(n^2)$. 🐢

## Here's how you can implement Bubble Sort

- [C++](#cpp)
- [Java](#java)

#### C++

```cpp
    #include <iostream>
    using namespace std;

    void bubbleSort(int arr[], int n) {
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    // Swap arr[j] and arr[j + 1]
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }

    void printArray(int arr[], int size) {
        for (int i = 0; i < size; i++)
            cout << arr[i] << " ";
        cout << endl;
    }

    int main() {
        int arr[] = {64, 34, 25, 12, 22, 11, 90};
        int n = sizeof(arr) / sizeof(arr[0]);
        bubbleSort(arr, n);
        cout << "Sorted array: \n";
        printArray(arr, n);
        return 0;
    }

```

#### Java

```java
    public class BubbleSort {
        public static void bubbleSort(int[] arr) {
            int n = arr.length;
            for (int i = 0; i < n - 1; i++) {
                for (int j = 0; j < n - i - 1; j++) {
                    if (arr[j] > arr[j + 1]) {
                        // Swap arr[j] and arr[j + 1]
                        int temp = arr[j];
                        arr[j] = arr[j + 1];
                        arr[j + 1] = temp;
                    }
                }
            }
        }

        public static void printArray(int[] arr) {
            for (int i : arr) {
                System.out.print(i + " ");
            }
            System.out.println();
        }

        public static void main(String[] args) {
            int[] arr = {64, 34, 25, 12, 22, 11, 90};
            bubbleSort(arr);
            System.out.println("Sorted array:");
            printArray(arr);
        }
    }

```

<hr>

## 🧩 Insertion Sort

### Concept:

Insertion Sort builds the final sorted array one item at a time. It picks elements from the unsorted portion and inserts them into their correct position in the sorted portion. This algorithm is efficient for small datasets or nearly sorted data.

### How It Works:

1. Start with the second element (assuming the first element is already sorted).
2. Compare it with the elements before it.
3. Insert it into the correct position in the sorted portion.
4. Repeat for each subsequent element.

**Visual Example:**

Think of sorting a hand of playing cards. You take one card at a time and insert it into the correct position among the cards already in your hand.

### Steps:

1. Pick the next card.
2. Compare with the cards in hand.
3. Insert it into the correct position.
4. Repeat with the next card.

### Pros:

- Simple and efficient for small or nearly sorted datasets. 🃏

### Cons:

- Inefficient for large datasets with a time complexity of $O(n^2)$. 🐢

## Here's how you can implement Bubble Sort

- [C++](#cpp)
- [Java](#java)

#### C++

```cpp
    #include <iostream>
    using namespace std;

    void insertionSort(int arr[], int n) {
        for (int i = 1; i < n; i++) {
            int key = arr[i];
            int j = i - 1;

            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j--;
            }
            arr[j + 1] = key;
        }
    }

    void printArray(int arr[], int size) {
        for (int i = 0; i < size; i++)
            cout << arr[i] << " ";
        cout << endl;
    }

    int main() {
        int arr[] = {64, 34, 25, 12, 22, 11, 90};
        int n = sizeof(arr) / sizeof(arr[0]);
        insertionSort(arr, n);
        cout << "Sorted array: \n";
        printArray(arr, n);
        return 0;
    }

```

#### Java

```java
    public class InsertionSort {
        public static void insertionSort(int[] arr) {
            int n = arr.length;
            for (int i = 1; i < n; i++) {
                int key = arr[i];
                int j = i - 1;
                while (j >= 0 && arr[j] > key) {
                    arr[j + 1] = arr[j];
                    j--;
                }
                arr[j + 1] = key;
            }
        }

        public static void printArray(int[] arr) {
            for (int i : arr) {
                System.out.print(i + " ");
            }
            System.out.println();
        }

        public static void main(String[] args) {
            int[] arr = {64, 34, 25, 12, 22, 11, 90};
            insertionSort(arr);
            System.out.println("Sorted array:");
            printArray(arr);
        }
    }

```

## 📚 What's Next?

Now that we've covered the concepts, try applying them to the following practice problems:

- **Easy:** [Merge Intervals](https://leetcode.com/problems/merge-intervals/)
- **Medium:** [Sort Colors](https://leetcode.com/problems/sort-colors/)
- **Hard:** [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)
