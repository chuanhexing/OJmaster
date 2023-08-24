给你二叉树的根节点 `root` ，返回其节点值的 **层序遍历** 。 （即逐层地，从左到右访问所有节点）。

 

**示例 1：**

![img](https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg)

输入：root = [3,9,20,null,null,15,7]
输出：[[3],[9,20],[15,7]]
示例 2：

输入：root = [1]
输出：[[1]]
示例 3：

输入：root = []
输出：[]


提示：

树中节点数目在范围 [0, 2000] 内
-1000 <= Node.val <= 1000

来源：力扣（LeetCode）
链接：https://leetcode.cn/problems/binary-tree-level-order-traversal
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```c++
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
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> ans;
        if (!root) return ans;
        TreeNode* p;
        queue<TreeNode*> qu;//定义一个数据类型是二叉树指针的队列
        qu.push(root);//根结点r进队
        
        while (!qu.empty()) {
            int count = qu.size();
            vector<int> arr;

            while(count > 0) {
                p = qu.front();
                qu.pop();
                arr.push_back(p -> val);
                if(p -> left != NULL)
                    qu.push(p -> left);
                if(p -> right != NULL)
                    qu.push(p -> right);
                count --;
            }
            ans.push_back(arr);
        }
        return ans;
    }
};
```



```c++
//如果不加count就会出现下面的结果
输入
[3,9,20,null,null,15,7]
输出
[[3],[9],[20],[15],[7]]
预期结果
[[3],[9,20],[15,7]]
```

