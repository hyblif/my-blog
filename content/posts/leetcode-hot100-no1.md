---
title: "LeetCode Hot 100: 两数之和"
date: 2026-03-28
tags: ["LeetCode", "算法", "哈希表"]
categories: ["题解"]
showToc: true
draft : false
---

## 题目描述
给定一个整数数组 `nums` 和一个整数目标值 `target`，请你在该数组中找出 和为目标值 `target`  的那 两个 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案，并且你不能使用两次相同的元素。

你可以按任意顺序返回答案。

## 思路复盘
使用哈希表来存储已经遍历过的数字及其索引，时间复杂度  $ O(n) $。

## 代码实现
### python 实现
```python
def twoSum(nums, target):
    hashmap = {}
    for i, num in enumerate(nums):
        if target - num in hashmap:
            return [hashmap[target - num], i]
        hashmap[num] = i
```
### C++实现
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int,int> hash; // hash 表格
        for(int i = 0;i < nums.size();i++){
            if(hash.count(target - nums[i])){
                return {i, hash[target - nums[i]]};
            }
            hash[nums[i]] = i;
        }
        return {};
    }
};
```