---
title: '[Leetcode总结]生成一个String所有partitioning'
date: 2022-01-09 16:52:32
tags: Leetcode, Algorithms
---

# 前言

这是我在刷今天的leetcode题目 [131.Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/) 学到的技巧，在这里记录一下。

# 问题

给与一个String, 我们要产出他的所有的partitioning。

**Example 1**

```
Input: "ac"

Output: [["a","c],  ["ac"]]
```


**Example 2**

```
Input: "abc"

Output: [["a","b","c], ["a","bc"], ["ab", "c"], ["abc"]]
```

# 思路

我们可以使用递归来解决这个问题，对于partitioning这个问题，我们可以很容易的辨别出很多更小规模的问题。比如对于整个String，我们可以求整个String的全部的partitioning，也可以求从这个String的一个subString的全部的partitioning。在分辨出了sub problem之后，我们就可以寻找不同规模问题之间的互通之处。我们选择了top down的方式来解决，从最大规模的问题层层递归到最小规模，最后求解。

对于每个String，我们先取它从头开始的每一种substring，对于一下的例子来说就是 ["a", "ab", "abc"]，然后对于剩下的String 递归套用一样的方法。最后的结果就会是全部的partitioning。


![alt](pic.jpg)


# 代码实现

``` java
public List<List<String>> allPartitioning (String s){
    List<List<String>> ans = new ArrayList<>();

    dfs(ans, new ArrayList<String>(), 0, s);

    return ans;
}

public void dfs (List<List<String>> ans, List<String> currList, int start, String s){
    if(start >= s.length()){
        ans.add(new ArrayList<String>(currList));
    } else {
        for(int end = start; end < s.length(); end++){
            currList.add(s.subString(start,end+1));
            dfs(ans,currList, start + 1, s);
            // backtrack and remove the substring we just added.
            currList.remove(currList.size()-1); 
        }
    }
} 
```