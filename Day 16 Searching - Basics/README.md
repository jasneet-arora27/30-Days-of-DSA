# 🌟 Day 17: Searching - Basics 🌟

Today, we dive into the world of **searching algorithms** 🧐, essential for efficiently finding elements in arrays or lists. Let's explore **linear search** and the more optimized **binary search**! These two algorithms form the foundation of searching techniques.

<hr>

## 🔍 Linear Search

**Linear search** is the simplest way to find an element in a collection. You go through each element, one by one, until you find what you're looking for 🎯.

### Steps:

1. Start from the first element.
2. Check each element.
3. If it matches, return its index. If not, continue until the end.
4. If the element isn't found, return `-1`.

### Efficiency:

- **🕒 Time complexity:** $O(n)$ — since we may need to search through every element.
- **❌ Drawback:** It's slow for large arrays because it checks every single element.

### 🎁 Here how you can implement Linear Search in code 🎁

- [C++](#cpp)
- [Java](#java)

#### C++

```cpp
#include <iostream>
using namespace std;

int linearSearch(int arr[], int n, int target) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == target) {
            return i;
        }
    }
    return -1;
}

int main() {
    int arr[] = {2, 4, 6, 8, 10};
    int n = sizeof(arr)/sizeof(arr[0]);
    int target = 6;

    int result = linearSearch(arr, n, target);
    if (result != -1)
        cout << "Element found at index " << result << endl;
    else
        cout << "Element not found" << endl;

    return 0;
}
```

#### Java

```java
public class LinearSearch {
    public static int linearSearch(int[] arr, int target) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {
                return i;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 10};
        int target = 6;
        int result = linearSearch(arr, target);
        if (result != -1) {
            System.out.println("Element found at index " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

<hr>

## ⚡ Binary Search

**Binary search** is much faster than linear search, but it requires the array to be sorted 📑.

### Steps:

1. Find the middle element.
2. Compare the target value with the middle element:
   - If the target is equal to the middle, return its index.
   - If the target is smaller, repeat the process on the left half.
   - If the target is larger, repeat the process on the right half.
3. Keep dividing the array until you find the element (or determine it's not present).

### Efficiency:

- **🕒 Time complexity:** $O(log n)$ — we halve the array size with each step, making it very efficient!

### Advantages:

- Super fast for large, sorted arrays.
- Saves a lot of time compared to linear search when dealing with thousands or millions of elements.

### 🎁 Here how you can implement Binary Search in code 🎁

- [C++](#cpp)
- [Java](#java)

#### C++

```cpp
#include <iostream>
using namespace std;

int binarySearch(int arr[], int low, int high, int target) {
    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (arr[mid] == target) {
            return mid;
        }
        if (arr[mid] < target) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return -1;
}

int main() {
    int arr[] = {2, 4, 6, 8, 10};
    int n = sizeof(arr) / sizeof(arr[0]);
    int target = 6;

    int result = binarySearch(arr, 0, n - 1, target);
    if (result != -1)
        cout << "Element found at index " << result << endl;
    else
        cout << "Element not found" << endl;

    return 0;
}
```

#### Java

```java
public class BinarySearch {
    public static int binarySearch(int[] arr, int target) {
        int low = 0, high = arr.length - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] == target) {
                return mid;
            }
            if (arr[mid] < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 10};
        int target = 6;
        int result = binarySearch(arr, target);
        if (result != -1) {
            System.out.println("Element found at index " + result);
        } else {
            System.out.println("Element not found");
        }
    }
}
```

<hr>

## 🚀 Key Differences Between Linear Search and Binary Search:

- **🛠️ Linear Search** works on unsorted data but is slower $(O(n))$.
- ⚙️ **Binary Search** requires sorted data but is much faster $(O(log n))$.

## 📚 What's Next?

Now that we've covered the concepts, try applying them to the following practice problems:

- **Easy:** [Binary Search](https://leetcode.com/problems/binary-search/)
- **Medium:** [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
- **Hard:** [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)