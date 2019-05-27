Leetcode是程序员刷算法题的大本营，难度也很友好的分了高级、中级及初级，目前在全球范围内已经有了上百万名用户，并且拥有超过了1000道题目资源和公司面试真题。 
我在刷题的过程中，会复习曾经学过的数据结构知识来解决题目，然后在看别人优秀的解决方案时，还是学习到新的思路，以及一些tricks，觉得记录一下会很有意思。这系列主要会翻译题目，然后使用python来解题，并且会穿插一些python的用法技巧，希望大家可以一起加油~ 

目前答题是“pick one”，顺序随机，这次先从最简单的走起。

## Two Sum
Q：Given an array of integers, return indices of the two numbers such that they add up to a specific target.
You may assume that each input would have exactly one solution, and you may not use the sameelement twice.

两数之和
给一个整数数组nums和一个目标值target，请你在该数组中找到和为目标值的那两个整数，并返回它们的数组下标。
你可以假设每种输入只会对应一个答案，但是你不能重复利用这个数组中同样的元素。

```
Example:
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```


解题思路：
这个题最暴力的解法当然是两个for循环遍历数组，这样计算复杂度为O(n²)
比较巧妙的解法是引入python dict，而在python中字典是基于hash table(哈希表，也叫散列表)做的，所以我们这次介绍下哈希表。

哈希函数大概就是value = hash(key)，我们希望key和value之间是唯一的映射关系。哈希表是根据关键码值（key value）而直接进行访问的数据结构，通过把关键码值映射到表中的一个位置来访问记录，以加快查找的记录。
哈希表的查找时间为常数，即O(n)。

下面就是用字典解题的代码了，善用数据结构，可以让我们的思路更加开阔，程序性能也会提升。
```
class Solution:
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        
        d = dict()
        for index, value in enumerate(nums):
            if target - value in d:
                return [d[target-value], index]
            else:
                d[value] = index
        return None
```