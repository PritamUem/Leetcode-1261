# Leetcode-1261

# C++

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class FindElements {
public:
    map<int,int>mp;
    void modify(TreeNode *r)
    {
        if(!r)
            return;
         mp[r->val]=1;
        if(r->left!=NULL)
            r->left->val=2*(r->val)+1;
         if(r->right!=NULL)
            r->right->val=2*(r->val)+2;
        modify(r->left);
        modify(r->right);
    }
    FindElements(TreeNode* root) {
        if(!root)
       return ;
        root->val=0;
        modify(root);
    }
    
    bool find(int target) {
        return mp[target];
    }
};

/**
 * Your FindElements object will be instantiated and called as such:
 * FindElements* obj = new FindElements(root);
 * bool param_1 = obj->find(target);

 */

 # Python

 # Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class FindElements:
    def __init__(self, root):
        self.mp = set()
        if root:
            root.val = 0
            self.modify(root)

    def modify(self, root):
        if not root:
            return
        self.mp.add(root.val)
        if root.left:
            root.left.val = 2 * root.val + 1
            self.modify(root.left)
        if root.right:
            root.right.val = 2 * root.val + 2
            self.modify(root.right)

    def find(self, target):
        return target in self.mp

        


# Your FindElements object will be instantiated and called as such:
# obj = FindElements(root)
# param_1 = obj.find(target)

# Java

/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
import java.util.HashSet;
import java.util.Set;

class FindElements {
    private Set<Integer> set;

    public FindElements(TreeNode root) {
        set = new HashSet<>();
        if (root != null) {
            root.val = 0;
            modify(root);
        }
    }

    private void modify(TreeNode root) {
        if (root == null) return;
        set.add(root.val);
        if (root.left != null) {
            root.left.val = 2 * root.val + 1;
            modify(root.left);
        }
        if (root.right != null) {
            root.right.val = 2 * root.val + 2;
            modify(root.right);
        }
    }

    public boolean find(int target) {
        return set.contains(target);
    }
}


/**
 * Your FindElements object will be instantiated and called as such:
 * FindElements obj = new FindElements(root);
 * boolean param_1 = obj.find(target);
 */
