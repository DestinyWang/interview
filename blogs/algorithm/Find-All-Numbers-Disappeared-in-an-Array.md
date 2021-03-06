# 1. 题目介绍

出自 Leetcode 第 448 题

Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements of [1, n] inclusive that do not appear in this array.

Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.

Example:

    Input:
    [4,3,2,7,8,2,3,1]
    
    Output:
    [5,6]
    
    
---
给定一个范围在  `1 ≤ a[i] ≤ n` ( n = 数组大小 ) 的 整型数组，数组中的元素一些出现了两次，另一些只出现一次。

找到所有在 [1, n] 范围之间没有出现在数组中的数字。

您能在不使用额外空间且时间复杂度为O(n)的情况下完成这个任务吗? 你可以假定返回的数组不算在额外空间内。

示例:

    输入:
    [4,3,2,7,8,2,3,1]
    
    输出:
    [5,6]
    
# 2. 分析

题目的描述比较简单, 寻找数组中没有出现的数字.

最容易想到的就是开辟一块额外的空间, 遍历原数组, 记录哪些数字没有出现过即可.

但题目规定:
> 除了返回的数组, 不能开辟新的额外空间, 且时间复杂度不能超过O(n).

意味着:
1. 必须在原数组进行操作
2. 对原数组的操作必须保持在常数级(即不能进行常规排序)
3. 题目中给出的重要条件 `1 ≤ a[i] ≤ n`

## 2.1 必须在原数组进行操作

用原题中的样例:

    [4,3,2,7,8,2,3,1]

数组长度为 8, 要找到 1 ~ 8 中缺失的整数, 最简单的方式就是排序, 如果能够完成排序:

    [1,2,2,3,3,4,7,8]
    
通过与下标进行对比, 一次遍历即可找到缺失的整数:

原数组:
元素 | 4 | 3 | 2 | 7 | 8 | 2 | 3 | 1 |
---|---|---|---|---|---|---|---|---
下标 | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |

排序后的数组:
元素 | 1 | 2 | 2 | 3 | 3 | 4 | 7 | 8 |
---|---|---|---|---|---|---|---|---
下标 | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |

```java
List<Integer> beingless = new ArrayList<>();
for (int i = 0; i < nums.length; ++ i) {
    if (nums[i] != (i + 1)) {
        beingless.add(nums[i]);
    }
}
```

## 2.2 对原数组的操作必须保持在常数级(即不能进行常规排序)
由第一个条件可知, 在不允许分配额外空间的情况下, 对原数组进行排序并比较下标是解决方案之一.

但该条件禁止了我们使用常规排序, 我们知道, 常见的排序在不借助额外空间的情况下, 时间复杂度都在 `O(nlogn)`

但是否完全堵死了排序这条路呢, 其实并没有.

仔细分析, 其实为了解决该题, 我们需要的排序有两个重要的特性:
1. 原数组是取值范围为 `[1, n]` 的 n 个数字
2. 我们并不需要将所有数字进行排序, 确切地说, 所有重复的数字其实并不需要真正排序, 只需要把不重复的数组排序即可


    [1,2,3,4,3,4,7,8]
    [1,2,3,4,4,3,7,8]
    
其实没有区别.

# 3. 解法

所以, 我们可以依据上面的结论进行定制化排序的设计:

```c
按接近小到大的顺序排序，如果该数字和对应数字 -1 所在索引不同，则交换位置，交换完 i--，继续判断交换后的数字
```

循环完成后判断数字是否和索引 +1 的值相等，不等则加入集合

```java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        List<Integer> beingless = new ArrayList<Integer>();
		int temp;
		for (int i = 0; i < nums.length; i++) {
			if(nums[i] != nums[nums[i] - 1]) {
			    // swap
				temp = nums[nums[i] - 1];
				nums[nums[i] - 1]=nums[i];
				nums[i]=temp;
				// 如果完成了交换, 需要重新处理该值
				i--;
			}
		}
		for (int i = 0; i < nums.length; i++) {
			if(nums[i] != i + 1) {
				beingless.add(i + 1);
			}
		}
		return beingless;
    }
}
```

数组交换过程:

```
[7, 3, 2, 4, 8, 2, 3, 1]
[3, 3, 2, 4, 8, 2, 7, 1]
[2, 3, 3, 4, 8, 2, 7, 1]
[3, 2, 3, 4, 8, 2, 7, 1]
[3, 2, 3, 4, 8, 2, 7, 1]
[3, 2, 3, 4, 8, 2, 7, 1]
[3, 2, 3, 4, 8, 2, 7, 1]
[3, 2, 3, 4, 8, 2, 7, 1]
[3, 2, 3, 4, 1, 2, 7, 8]
[1, 2, 3, 4, 3, 2, 7, 8]
[1, 2, 3, 4, 3, 2, 7, 8]
[1, 2, 3, 4, 3, 2, 7, 8]
[1, 2, 3, 4, 3, 2, 7, 8]
[1, 2, 3, 4, 3, 2, 7, 8]
```