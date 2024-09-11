# 🌳 Day 9: Trees - Advanced Techniques 🌳

Today, we're diving deeper into **Advanced Tree Traversal and Operations**. We will break things down in a simplified, structured, and interesting way—plus, we'll sprinkle in some emojis to keep things fun and engaging! 🎉

<hr>

## 🌟 Topics to Cover 🌟

### 1. Advanced Tree Traversal

- **Morris Traversal** (Inorder without recursion/stack)
- **Diagonal Traversal** (Used in many coding problems)
- **Boundary Traversal** (Get the boundary nodes of the tree)
- **Zigzag Traversal** (Level order traversal, but alternating between left-to-right and right-to-left)

### 2.Advanced Tree Operations

- **Lowest Common Ancestor (LCA):** Finding the common ancestor of two nodes 📍
- **Height Balanced Tree (AVL Trees):** Keeping the tree balanced for optimal performance 🌲
- **Threaded Binary Trees:** A tree where null pointers are replaced with pointers to the in-order predecessor/successor ➿

<hr>

## 📜 Advanced Tree Traversal Techniques 📜

### 1. Morris Traversal (Inorder without recursion/stack) 🌀

- **Problem:** Normal inorder traversal uses recursion or a stack, leading to extra memory usage.
- **Solution:** **Morris Traversal** reduces memory use by linking the current node to its predecessor, achieving inorder traversal in $O(1)$ space. However, it modifies the tree structure temporarily.
- **Real-Life Example:** Imagine going through a series of interconnected rooms (nodes) but without any map (stack/recursion). You leave a temporary marker at the doors (predecessors) so that you can retrace your steps without getting lost! 🏠

#### Here's how you can implement this in code:

- [C++](#cpp)
- [Java](#java)

### C++

```cpp
void morrisTraversal(Node* root) {
    Node* current = root;
    while (current != nullptr) {
        if (current->left == nullptr) {
            cout << current->data << " ";
            current = current->right;
        } else {
            Node* pre = current->left;
            while (pre->right != nullptr && pre->right != current)
                pre = pre->right;

            if (pre->right == nullptr) {
                pre->right = current;
                current = current->left;
            } else {
                pre->right = nullptr;
                cout << current->data << " ";
                current = current->right;
            }
        }
    }
}
```

### Java

```java
public void morrisTraversal(Node root) {
    Node current = root;
    while (current != null) {
        if (current.left == null) {
            System.out.print(current.data + " ");
            current = current.right;
        } else {
            Node pre = current.left;
            while (pre.right != null && pre.right != current)
                pre = pre.right;

            if (pre.right == null) {
                pre.right = current;
                current = current.left;
            } else {
                pre.right = null;
                System.out.print(current.data + " ");
                current = current.right;
            }
        }
    }
}

```

<hr>

### 2. Zigzag Traversal 🔀

- This traversal is like a level order traversal, but instead of processing all levels left-to-right, you alternate directions at each level. It's great for problems where you need to mimic a "zigzag" pattern.
- **Real-Life Example:** Think of playing hopscotch 🦘; sometimes you jump to the right, and other times to the left, back and forth!

#### Here's how you can implement this in code:

- [C++](#cpp)
- [Java](#java)

### C++

```cpp
void zigzagTraversal(Node* root) {
    if (root == nullptr) return;

    stack<Node*> currentLevel;
    stack<Node*> nextLevel;
    bool leftToRight = true;

    currentLevel.push(root);

    while (!currentLevel.empty()) {
        Node* temp = currentLevel.top();
        currentLevel.pop();

        if (temp) {
            cout << temp->data << " ";

            if (leftToRight) {
                if (temp->left) nextLevel.push(temp->left);
                if (temp->right) nextLevel.push(temp->right);
            } else {
                if (temp->right) nextLevel.push(temp->right);
                if (temp->left) nextLevel.push(temp->left);
            }
        }

        if (currentLevel.empty()) {
            leftToRight = !leftToRight;
            swap(currentLevel, nextLevel);
        }
    }
}
```

### Java

```java
public void zigzagTraversal(Node root) {
    if (root == null) return;

    Stack<Node> currentLevel = new Stack<>();
    Stack<Node> nextLevel = new Stack<>();
    boolean leftToRight = true;

    currentLevel.push(root);

    while (!currentLevel.isEmpty()) {
        Node temp = currentLevel.pop();

        if (temp != null) {
            System.out.print(temp.data + " ");

            if (leftToRight) {
                if (temp.left != null) nextLevel.push(temp.left);
                if (temp.right != null) nextLevel.push(temp.right);
            } else {
                if (temp.right != null) nextLevel.push(temp.right);
                if (temp.left != null) nextLevel.push(temp.left);
            }
        }

        if (currentLevel.isEmpty()) {
            leftToRight = !leftToRight;
            Stack<Node> swap = currentLevel;
            currentLevel = nextLevel;
            nextLevel = swap;
        }
    }
}
```

<hr>

### 3. Boundary Traversal 🚧

- This traversal helps you find the outer boundary of the tree, starting from the leftmost node, then the leaves, and ending with the rightmost node.
- **Real-Life Example:** Imagine walking around the boundary of a forest 🌲. You first walk along the left side, then across the outermost leaves 🍃, and finally back along the right side. It's like tracing the entire "outline" of the forest!

#### Here's how you can implement this in code:

- [C++](#cpp)
- [Java](#java)

### C++

```cpp
void boundaryTraversal(Node* root) {
    if (root == nullptr) return;

    cout << root->data << " ";

    printLeftBoundary(root->left);
    printLeaves(root->left);
    printLeaves(root->right);
    printRightBoundary(root->right);
}

void printLeftBoundary(Node* root) {
    if (root == nullptr) return;

    if (root->left) {
        cout << root->data << " ";
        printLeftBoundary(root->left);
    } else if (root->right) {
        cout << root->data << " ";
        printLeftBoundary(root->right);
    }
}

void printLeaves(Node* root) {
    if (root == nullptr) return;

    printLeaves(root->left);
    if (root->left == nullptr && root->right == nullptr)
        cout << root->data << " ";
    printLeaves(root->right);
}

void printRightBoundary(Node* root) {
    if (root == nullptr) return;

    if (root->right) {
        printRightBoundary(root->right);
        cout << root->data << " ";
    } else if (root->left) {
        printRightBoundary(root->left);
        cout << root->data << " ";
    }
}
```

### Java

```java
public void boundaryTraversal(Node root) {
    if (root == null) return;

    System.out.print(root.data + " ");

    printLeftBoundary(root.left);
    printLeaves(root.left);
    printLeaves(root.right);
    printRightBoundary(root.right);
}

public void printLeftBoundary(Node root) {
    if (root == null) return;

    if (root.left != null) {
        System.out.print(root.data + " ");
        printLeftBoundary(root.left);
    } else if (root.right != null) {
        System.out.print(root.data + " ");
        printLeftBoundary(root.right);
    }
}

public void printLeaves(Node root) {
    if (root == null) return;

    printLeaves(root.left);
    if (root.left == null && root.right == null)
        System.out.print(root.data + " ");
    printLeaves(root.right);
}

public void printRightBoundary(Node root) {
    if (root == null) return;

    if (root.right != null) {
        printRightBoundary(root.right);
        System.out.print(root.data + " ");
    } else if (root.left != null) {
        printRightBoundary(root.left);
        System.out.print(root.data + " ");
    }
}
```

<hr>

### 4. Diagonal Traversal 📐

- **Diagonal Traversal** divides the tree into diagonals and processes nodes from top-left to bottom-right.
- **Real-Life Example:** Think of diagonally crossing a matrix. Each diagonal contains nodes with the same slope from top to bottom.

#### Here's how you can implement this in code:

- [C++](#cpp)
- [Java](#java)

### C++

```cpp
void diagonalTraversal(Node* root) {
    if (root == nullptr) return;

    queue<Node*> q;
    q.push(root);

    while (!q.empty()) {
        Node* temp = q.front();
        q.pop();

        while (temp) {
            cout << temp->data << " ";
            if (temp->left)
                q.push(temp->left);
            temp = temp->right;
        }
    }
}
```

### Java

```java
public void diagonalTraversal(Node root) {
    if (root == null) return;

    Queue<Node> q = new LinkedList<>();
    q.add(root);

    while (!q.isEmpty()) {
        Node temp = q.remove();

        while (temp != null) {
            System.out.print(temp.data + " ");
            if (temp.left != null)
                q.add(temp.left);
            temp = temp.right;
        }
    }
}
```

<hr>

## ⚙️ Advanced Tree Operations ⚙️

### 1. Lowest Common Ancestor (LCA) 🧭

- The LCA is the deepest node that is an ancestor of both given nodes in a binary tree. It’s useful for finding relationships between nodes (like the "closest" common relative).
- **Real-Life Example:** Think of it like a family tree 👨‍👩‍👧‍👦. If you and a cousin both trace back your ancestry, the first common person you both are related to is your LCA! It's the "lowest" common ancestor in the hierarchy.

#### Here's how you can implement this in code:

- [C++](#cpp)
- [Java](#java)

### C++

```cpp
Node* findLCA(Node* root, int n1, int n2) {
    if (root == nullptr) return nullptr;

    if (root->data == n1 || root->data == n2)
        return root;

    Node* leftLCA = findLCA(root->left, n1, n2);
    Node* rightLCA = findLCA(root->right, n1, n2);

    if (leftLCA != nullptr && rightLCA != nullptr)
        return root;

    return (leftLCA != nullptr) ? leftLCA : rightLCA;
}
```

### Java

```java
public Node findLCA(Node root, int n1, int n2) {
    if (root == null) return null;

    if (root.data == n1 || root.data == n2)
        return root;

    Node leftLCA = findLCA(root.left, n1, n2);
    Node rightLCA = findLCA(root.right, n1, n2);

    if (leftLCA != null && rightLCA != null)
        return root;

    return (leftLCA != null) ? leftLCA : rightLCA;
}
```

<hr>

### 2. Height Balanced Trees (AVL Trees) 📏

- These trees automatically balance themselves as you perform insertions and deletions. This balance ensures operations like searching, insertion, and deletion stay efficient.
- **Real-Life Example:** Imagine stacking books 📚. You want to keep the stack even (balanced) so it doesn't tip over. Similarly, AVL trees adjust themselves to maintain balance.

#### Here's how you can implement this in code:

- [C++](#cpp)
- [Java](#java)

### C++

```cpp
class AVLNode {
public:
    int data;
    AVLNode* left;
    AVLNode* right;
    int height;

    AVLNode(int val) {
        data = val;
        left = right = nullptr;
        height = 1;
    }
};

int height(AVLNode* node) {
    if (node == nullptr) return 0;
    return node->height;
}

AVLNode* rightRotate(AVLNode* y) {
    AVLNode* x = y->left;
    AVLNode* T2 = x->right;

    x->right = y;
    y->left = T2;

    y->height = max(height(y->left), height(y->right)) + 1;
    x->height = max(height(x->left), height(x->right)) + 1;

    return x;
}

AVLNode* leftRotate(AVLNode* x) {
    AVLNode* y = x->right;
    AVLNode* T2 = y->left;

    y->left = x;
    x->right = T2;

    x->height = max(height(x->left), height(x->right)) + 1;
    y->height = max(height(y->left), height(y->right)) + 1;

    return y;
}

int getBalance(AVLNode* node) {
    if (node == nullptr) return 0;
    return height(node->left) - height(node->right);
}

AVLNode* insert(AVLNode* node, int data) {
    if (node == nullptr) return new AVLNode(data);

    if (data < node->data)
        node->left = insert(node->left, data);
    else if (data > node->data)
        node->right = insert(node->right, data);
    else
        return node;

    node->height = 1 + max(height(node->left), height(node->right));

    int balance = getBalance(node);

    if (balance > 1 && data < node->left->data)
        return rightRotate(node);

    if (balance < -1 && data > node->right->data)
        return leftRotate(node);

    if (balance > 1 && data > node->left->data) {
        node->left = leftRotate(node->left);
        return rightRotate(node);
    }

    if (balance < -1 && data < node->right->data) {
        node->right = rightRotate(node->right);
        return leftRotate(node);
    }

    return node;
}
```

### Java

```java
class AVLNode {
    int data, height;
    AVLNode left, right;

    AVLNode(int d) {
        data = d;
        height = 1;
    }
}

public class AVLTree {
    int height(AVLNode N) {
        if (N == null) return 0;
        return N.height;
    }

    AVLNode rightRotate(AVLNode y) {
        AVLNode x = y.left;
        AVLNode T2 = x.right;

        x.right = y;
        y.left = T2;

        y.height = Math.max(height(y.left), height(y.right)) + 1;
        x.height = Math.max(height(x.left), height(x.right)) + 1;

        return x;
    }

    AVLNode leftRotate(AVLNode x) {
        AVLNode y = x.right;
        AVLNode T2 = y.left;

        y.left = x;
        x.right = T2;

        x.height = Math.max(height(x.left), height(x.right)) + 1;
        y.height = Math.max(height(y.left), height(y.right)) + 1;

        return y;
    }

    int getBalance(AVLNode N) {
        if (N == null) return 0;
        return height(N.left) - height(N.right);
    }

    AVLNode insert(AVLNode node, int data) {
        if (node == null)
            return new AVLNode(data);

        if (data < node.data)
            node.left = insert(node.left, data);
        else if (data > node.data)
            node.right = insert(node.right, data);
        else
            return node;

        node.height = 1 + Math.max(height(node.left), height(node.right));

        int balance = getBalance(node);

        if (balance > 1 && data < node.left.data)
            return rightRotate(node);

        if (balance < -1 && data > node.right.data)
            return leftRotate(node);

        if (balance > 1 && data > node.left.data) {
            node.left = leftRotate(node.left);
            return rightRotate(node);
        }

        if (balance < -1 && data < node.right.data) {
            node.right = rightRotate(node.right);
            return leftRotate(node);
        }

        return node;
    }
}
```

<hr>

### 3. Threaded Binary Trees ➿

- This advanced tree type uses pointers in null nodes to point to in-order predecessors or successors. It improves traversal efficiency by reducing the need for recursion or a stack.
- **Real-Life Example:** Think of it as leaving a breadcrumb trail 🥖 as you move through the forest (tree) so you can return more efficiently without having to retrace your steps entirely!

#### Here's how you can implement this in code:

- [C++](#cpp)
- [Java](#java)

### C++

```cpp
struct Node {
    int data;
    Node* left, *right;
    bool rightThread;
};

Node* leftmost(Node* n) {
    if (n == nullptr) return nullptr;
    while (n->left != nullptr)
        n = n->left;
    return n;
}

void inOrder(Node* root) {
    Node* cur = leftmost(root);
    while (cur != nullptr) {
        cout << cur->data << " ";

        if (cur->rightThread)
            cur = cur->right;
        else
            cur = leftmost(cur->right);
    }
}
```

### Java

```java
class Node {
    int data;
    Node left, right;
    boolean rightThread;

    Node(int data) {
        this.data = data;
        left = right = null;
        rightThread = false;
    }
}

public class ThreadedBinaryTree {
    Node leftmost(Node n) {
        if (n == null) return null;
        while (n.left != null)
            n = n.left;
        return n;
    }

    public void inOrder(Node root) {
        Node cur = leftmost(root);
        while (cur != null) {
            System.out.print(cur.data + " ");

            if (cur.rightThread)
                cur = cur.right;
            else
                cur = leftmost(cur.right);
        }
    }
}
```

<hr>

## 🎯 Summary 🎯

Today's advanced tree techniques bring more efficiency and flexibility to how we process and manipulate trees:

- **Morris Traversal** minimizes memory usage during traversal by temporarily modifying the tree.
- **Zigzag and Diagonal Traversal** add variety to how we traverse trees for specific problem requirements.
- **Boundary Traversal** gives you a complete outline of the tree's nodes.
- **LCA and Height-Balanced Trees** improve search performance and balance tree operations.
- **Threaded Trees** optimize space usage during traversal.

These techniques open doors to tackling more complex problems with trees 🌳.

## 📚 What's Next?

Now that we've covered the concepts, try applying them to the following practice problems:

- **Easy:** [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)
- **Medium:** [Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)
- **Hard:** [Recover Binary Search Tree](https://leetcode.com/problems/recover-binary-search-tree/)