title: 'LeetCode: Verify Preorder Sequence in Binary Search Tree'
date: 2015-08-16 17:05:29
---
 Given an array of numbers, verify whether it is the correct preorder traversal sequence of a binary search tree.

You may assume each number in the sequence is unique.


Reference Link: http://www.tangjikai.com/algorithms/leetcode-255-verify-preorder-sequence-in-binary-search-tree

```java
public class Solution {
    public boolean verifyPreorder(int[] preorder) {
        if (preorder == null || preorder.length < 3) {
            return true;
        }

        Stack<Integer> stack = new Stack<>();
        List<Integer> list = new ArrayList<>();

        for (int i : preorder) {
            if (!list.isEmpty() && i < list.get(list.size() - 1)) {
                return false;
            }

            while (!stack.isEmpty() && i > stack.peek()) {
                list.add(stack.pop());
            }
            stack.add(i);
        }

        return true;
    }
}
```