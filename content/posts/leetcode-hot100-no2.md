---
title : 'Leetcode Hot 100: 字符串排序'
date : '2026-04-14T15:39:36+08:00'
tags : ["数组","哈希表","字符串","排序"]
categories : ["题解"]
showToc: true
draft : false
---
## 题目描述
给你一个字符串数组，请你将 字母异位词 组合在一起。可以按任意顺序返回结果列表。

## 思路复盘
建立一个哈希表，依次遍历数组中的元素，按照字母序排序后加入对应的哈希值数组中。最后依次解压出来返回答案

## 代码
### C++实现
```c++
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string, vector<string>> mp;
        for(auto& str : strs){
            string sorted_str = str;
            ranges::sort(sorted_str);
            mp[sorted_str].push_back(str);
        }
        vector<vector<string>> ans;
        for(auto& [_, value] : mp){
            ans.push_back(value);
        }
        return ans;
    }
};
```