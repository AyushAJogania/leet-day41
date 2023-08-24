# leet-day41

# Problem: All Possible Full Binary Trees

## Description

Given an integer `n`, you are required to return a list of all possible full binary trees with `n` nodes. Each node of each tree in the answer must have `Node.val` equal to 0. Each element of the answer is the root node of one possible tree. You may return the final list of trees in any order.

A full binary tree is a binary tree where each node has exactly 0 or 2 children.

## Example

Input: `n = 7`
Output: Multiple possible output trees, for example:
```
[
 [0,0,0,null,null,0,0,null,null,0,0],
 [0,0,0,null,null,0,0,0,0],
 [0,0,0,0,0,0,0],
 [0,0,0,0,0,null,null,null,null,0,0],
 [0,0,0,0,0,null,null,0,0]
]
```

Input: `n = 3`
Output: `[0,0,0]`

## Approach

The given solution uses a recursive approach to generate all possible full binary trees with the required properties. The `solve` function is recursively called to generate trees for different numbers of nodes. The base cases are when `n` is 1 (a single node with value 0) or when `n` is even (no valid full binary tree can be formed with an even number of nodes).

For odd `n`, the solution recursively generates left and right subtrees for different numbers of nodes and combines them in all possible ways to form the full binary trees.

The algorithm uses memoization to store already computed results to avoid redundant computations and improve efficiency.

## Complexity Analysis

The time complexity of this approach is exponential since the number of possible full binary trees grows exponentially with `n`. The space complexity is also high due to the recursive nature of the solution and memoization.

## Implementation

The solution is implemented in C++ and utilizes the `TreeNode` struct provided in the problem description. The `solve` function generates all possible full binary trees for a given number of nodes. The `allPossibleFBT` function initializes the memoization table and calls the `solve` function to generate the trees.

```cpp
class Solution {
public:
    vector<vector<TreeNode*>> dp;
    
    vector<TreeNode*> solve(int n) {
        // Base cases
        if (n % 2 == 0) return {}; // Even n
        if (dp[n].size() != 0) return dp[n]; // Memoization
        if (n == 1) {
            TreeNode* new_node = new TreeNode(0);
            return {new_node};
        }
        
        vector<TreeNode*> res;
        
        for (int i = 1; i < n; i += 2) {
            vector<TreeNode*> left = solve(i);
            vector<TreeNode*> right = solve(n - i - 1);
            
            for (TreeNode* l : left) {
                for (TreeNode* r : right) {
                    TreeNode* root = new TreeNode(0);
                    root->left = l;
                    root->right = r;
                    res.push_back(root);
                }
            }
        }
        
        return dp[n] = res;
    }
    
    vector<TreeNode*> allPossibleFBT(int n) {
        dp.resize(n + 1);
        return solve(n);
    }
};
```

## Conclusion

This README file provides an explanation of the problem statement, approach, complexity analysis, and C++ implementation for solving the "All Possible Full Binary Trees" problem.
