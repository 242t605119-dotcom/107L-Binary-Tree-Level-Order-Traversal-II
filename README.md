# LeetCode 107 - Binary Tree Level Order Traversal II

## Problem

Given the root of a binary tree, return the **bottom-up level order traversal** of its nodes' values.

In normal level order traversal, we visit the tree from the root level downwards. In this problem, the levels must be returned in **reverse order**, starting from the bottom level and ending with the root.

## Example 1

### Input

```text
root = [3,9,20,null,null,15,7]
```

### Output

```text
[[15,7],[9,20],[3]]
```

### Explanation

The tree is:

```text
        3
       / \
      9   20
         /  \
        15   7
```

Normal level order:

```text
[3]
[9,20]
[15,7]
```

After reversing the levels:

```text
[[15,7],[9,20],[3]]
```

## Example 2

### Input

```text
root = [1]
```

### Output

```text
[[1]]
```

## Example 3

### Input

```text
root = []
```

### Output

```text
[]
```

## Approach

We use **Breadth-First Search (BFS)** with a queue.

First, we perform a normal level order traversal and store each level in the result list. After processing the complete tree, we reverse the result so that the bottom level comes first.

## Algorithm

1. If the root is `None`, return an empty list.
2. Create a queue and add the root.
3. While the queue is not empty:

   * Find the number of nodes in the current level.
   * Process all nodes of that level.
   * Store their values.
   * Add their children to the queue.
4. Store every level in the result.
5. Reverse the result.
6. Return the reversed result.

## Code

```python
from collections import deque

class Solution:
    def levelOrderBottom(self, root):
        if not root:
            return []

        queue = deque([root])
        result = []

        while queue:
            level = []

            for _ in range(len(queue)):
                node = queue.popleft()
                level.append(node.val)

                if node.left:
                    queue.append(node.left)

                if node.right:
                    queue.append(node.right)

            result.append(level)

        return result[::-1]
```

## Complexity

* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(n)`

Each node is visited exactly once. The queue and result list require space proportional to the number of nodes.

## LeetCode Details

**Problem Number:** 107
**Problem Name:** Binary Tree Level Order Traversal II
**Difficulty:** Medium
**Topics:** Binary Tree, Breadth-First Search, Queue

## Language

Python 3

## Author

T.Nandhini
