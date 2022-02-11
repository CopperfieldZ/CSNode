## ```Arrays.sort()```比较器写法

```java
Arrays.sort(intervals, new Comparator<int[]>() {
    		//把所有int[] 换成T即可
            @Override
            public int compare(int[] o1, int[] o2) {
                if (o1[0] == o2[0]) return o1[1] - o2[1];
                return o1[0] - o2[0];
            }
        });
```



## 双指针法

如：盛最多水的容器

<img src="D:\Learning_CS\CSNote\leetcode刷题笔记.assets\image-20220104092041631.png" alt="image-20220104092041631" style="zoom: 67%;" />

## 优先排序法

对于某些要求不重复答案，或者答案为有序排列的情况，一般可以采用优先对整体进行排序再进行求解，因为这样能够减少去重时间，从而降低时间复杂度。对于很多情况，排序之后再解决问题会使问题变得简单很多。

如三数之和为零题目：解法为优先排序+双指针法（这里的双指针为基于排序才能实现的，因为排序之后左指针向右两数之和变大，右指针向左两数之和变小）

<img src="D:\Learning_CS\CSNote\leetcode刷题笔记.assets\image-20220104102412633.png" alt="image-20220104102412633" style="zoom: 67%;" />

## 二分查找法

对于已排序队列一般都会使用二分查找法注意二分查找法不需要使用递归，一般用==循环==就能实现！！！

下图中lower为true查找大于等于target的第一个下标，lower为false查找大于target的第一个下标。（图中的大于号将寻找大于和大于等于的情况都设置为一样的，都为向左边寻找）

![image-20220108144134789](D:\Learning_CS\CSNote\leetcode刷题笔记.assets\image-20220108144134789.png)

## 滑动窗口法

如：最长不重复子序列

## 中心扩展法

如：最长回文子序列的解法二

## 动态规划

方法过于复杂，可见算法导论笔记

### 思路障碍：



## 链表

对于链表操作一般会设置一个哨兵头结点，最终返回哨兵头dummy结点的next。

## 树相关

### 树的递归/子问题拆分思想：

以根节点为目标，左右子树为一个新的子问题进行递归或者拆分的思想。在动态规划与递归中常常用到

<img src="D:\Learning_CS\CSNote\leetcode刷题笔记.assets\image-20220202110757206.png" alt="image-20220202110757206" style="zoom:67%;" />

如图所示，整棵树的所有种数等于（假设左边节点为j，右边节点数为k，则总种数为左子树j的子问题答案乘以右边子问题的答案）

### 深度优先搜索（==回溯法==）：==对于一类寻找可行解的题（或一类可行集合的题）==，都可以尝试用[搜索回溯]的方法来求解，即深度优先搜索。

```java
void DFS(tree T){
    if(到节点){
        //注意递归算法中一定要将边界条件写到最前面！！！
    }
    
}
```

#### 代码中的空指针重复判断问题

如下代码中被注释的部分对左右节点进行了非空判断，然而调用的递归函数中以经对其进行了非空判断，此处无需判断，==只要没有进行```left.xxx```就不需要对left进行非空判断==！！只有用·的时候才进行判断，赋值的时候可不判断。

```java
public TreeNode buildMaxvalTree(TreeNode root){
        if(root==null)
            return null;
        TreeNode maxRoot = new TreeNode();
        maxRoot.val = root.val;
        maxRoot.left = buildMaxvalTree(root.left);
        maxRoot.right = buildMaxvalTree(root.right);
        if(maxRoot.left!=null)
            maxRoot.val = Math.max(maxRoot.val,maxRoot.left.val);
        if(maxRoot.right!=null)
            maxRoot.val = Math.max(maxRoot.val,maxRoot.right.val);
        return maxRoot;
//        if(root.left==null&&root.right==null)
//            maxRoot.val = root.val;
//        else if(root.left!=null){
//            TreeNode left = buildMaxvalTree(root.left);
//            maxRoot.val = Math.max(root.val,left.val);
//            maxRoot.left = left;
//        }
//        else if(root.right!=null){
//            TreeNode right = buildMaxvalTree(root.right);
//            maxRoot.val = Math.max(root.val,right.val);
//            maxRoot.right = right;
//        }
        //return root;

    }
```



#### 回溯法不适用的情况

<img src="D:\Learning_CS\CSNote\leetcode刷题笔记.assets\image-20220122161531981.png" alt="image-20220122161531981" style="zoom:67%;" />

上题中要求我们寻找可能的集合，由之前对回溯法使用情况的总结，第一反应想到的是使用回溯法，然而在此情况下，这些可能的集合并不是一条==路径==，路径一般都是从顶点开始单方向延伸，然而此题能多多方共同延伸，所以不适用于回溯法。![image-20220211093605609](leetcode刷题笔记.assets/image-20220211093605609.png)

### 广度优先算法（一般基于队列来实现，比较麻烦，不像回溯可以基于递归）

### 树的各类迭代遍历算法(LeeCode144)

#### test：

![image-20220211093613970](leetcode刷题笔记.assets/image-20220211093613970.png)

## 附录

- ```Integer.MAX```、```Long.MAX_VALUE```
- ```Arrays.copyOfRange()```:数组截取拷贝
- ```HashSet```：用HashMap实现的Set集合
