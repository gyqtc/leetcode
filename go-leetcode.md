# Leetcode go刷题记录

## 136 只出现一次的数字
- easy
- 考点：两个相同的数异或之后为0
- 最佳代码
```
func singleNumber(nums []int) int {
    result := 0
    for _, num := range nums {
        result ^= num
    }
    return result
}
```
- 哈希表
```

```

## 94 二叉树的中序遍历
- easy
- 考点：二叉树递归实现
- 递归实现
```
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func inorderTraversal(root *TreeNode) []int {
    var result []int
    inorder(root, &result)
    return result
}

func inorder(root *TreeNode, result *[]int) {
    if root == nil {
        return 
    } else {
        inorder(root.Left, result)
        *result = append(*result, root.Val)
        inorder(root.Right, result)
    }
}
```

## 104 二叉树的最大深度
- easy
- 考点：二叉树最大深度的递归实现
- 递归实现
```
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func max(a int, b int) int{
    if a > b {
        return a
    } 
    return b
}
func maxDepth(root *TreeNode) int {
    if root == nil {
        return 0
    } 
    return max(maxDepth(root.Left), maxDepth(root.Right)) + 1
}
```

## 144 二叉树的前序遍历
- easy
- 考点
- 递归实现
```
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func preorderTraversal(root *TreeNode) []int {
    var result []int
    preorder(root, &result)
    return result
}
func preorder(root *TreeNode, result *[]int) {
    if root == nil {
        return 
    }
    *result = append(*result, root.Val)
    preorder(root.Left, result)
    preorder(root.Right, result)
}
```

## 171 Excel表序号

- easy
- 考点
- 代码：进制转换
```
func titleToNumber(columnTitle string) int {
	n := len(columnTitle)
	ans := 0
	for i := n - 1; i >= 0; i-- {
		ans += int(columnTitle[i] - 'A' + 1) * int(math.Pow(float64(26), float64(n-i-1)))
	}
	return ans
}
```

## 344 反转字符串
- easy
- 考点：go语言特性
- 代码
```
func reverseString(s []byte)  {
    for i, j := 0, len(s)-1; i < j; i, j = i+1, j-1 {
		s[i], s[j] = s[j], s[i]
	}
}
```
## 4 寻找两个正序数组的中位数
- hard
- 考点：中位数
- 自己尝试，暴力解法，直接归并两个数组然后排序取中位数
```
func findMedianSortedArrays(nums1 []int, nums2 []int) float64 {
    for _, num2 := range nums2 {
        nums1 = append(nums1, num2)
    }
    sort.Ints(nums1)
    n := len(nums1)
    if n % 2 == 1 {
        return float64(nums1[(n - 1) / 2])
    } else {
        return float64((nums1[n / 2 - 1] + nums1[n / 2])) / 2
    }
}
```

