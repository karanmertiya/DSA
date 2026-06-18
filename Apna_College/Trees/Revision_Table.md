# Trees Revision Table

<table border="1">
  <thead>
    <tr>
      <th rowspan="2" style="width: 5%;">S.No</th>
      <th rowspan="2" style="width: 15%;">Problem Name</th>
      <th rowspan="2" style="width: 25%;">Example & Constraints</th>
      <th rowspan="2" style="width: 10%;">Complexity</th>
      <th colspan="2" style="width: 20%;">Conditions & Edge Cases</th>
      <th rowspan="2" style="width: 25%;">Logic</th>
    </tr>
    <tr>
      <th>Dependencies / Setup</th>
      <th>Edge Case Handling</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="1">1</td>
      <td rowspan="1">Tree 01 Binary Tree Inorder Traversal<br><br></b> <a href='https://leetcode.com/problems/binary-tree-inorder-traversal/' target='_blank'>LeetCode 94</a></td>
      <td rowspan="1"><b>Example 1:</b> Input: root = [1,null,2,3], Output: [1,3,2]<br><br><b>Note (Constraint):</b> Inorder -> Left, Root, Right.</td>
      <td><b>Time:</b> O(N) (Constraint)<br><b>Space:</b> O(N) (Constraint)</td>
      <td>-</td>
      <td><b>Recursion Depth:</b> In the worst-case (skewed tree), the recursion stack takes `O(N)` space. For balanced trees, it takes `O(log N)`.</td>
      <td><b>Explanation:</b> Recursive approach. Traverse the left subtree, process the current node, then traverse the right subtree.<br><br><details><summary><b>View C++</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-cpp">/*&#10;struct TreeNode {&#10;    int val;&#10;    TreeNode *left;&#10;    TreeNode *right;&#10;    TreeNode(int x) : val(x), left(NULL), right(NULL) {}&#10;};&#10;*/&#10;#include &lt;vector&gt;&#10;&#10;void inorder(TreeNode* root, std::vector&lt;int&gt;&amp; ans) {&#10;    if (root == nullptr) return;&#10;    inorder(root-&gt;left, ans);&#10;    ans.push_back(root-&gt;val);&#10;    inorder(root-&gt;right, ans);&#10;}&#10;&#10;std::vector&lt;int&gt; inorderTraversal(TreeNode* root) {&#10;    std::vector&lt;int&gt; ans;&#10;    inorder(root, ans);&#10;    return ans;&#10;}</code></pre></details><br><details><summary><b>View Python</b></summary><pre style="white-space: pre-wrap; word-wrap: break-word;"><code class="language-python"># class TreeNode:&#10;#     def __init__(self, val=0, left=None, right=None):&#10;#         self.val = val&#10;#         self.left = left&#10;#         self.right = right&#10;&#10;def inorder_traversal(root: TreeNode) -&gt; list[int]:&#10;    ans = []&#10;    def inorder(node):&#10;        if not node: return&#10;        inorder(node.left)&#10;        ans.append(node.val)&#10;        inorder(node.right)&#10;    inorder(root)&#10;    return ans</code></pre></details></td>
    </tr>
  </tbody>
</table>
