#### Question

tag##



#### Description



#### Analysis

题意分析: 

```
我们假设有一个函数 f(s)，其中 s 是一个非空字符串；该函数可以统计 s  中（按字典序比较）最小字母的出现频次。

例如，若 s = "dcce"，按字典序序其中最小的字母是 "c", 而它出现的频次是 2，所以 f(s) = 2。

若 s = "cbd", 按字典序序其中最小的字母是 "b", 而它出现的频次是 1，所以 f(s) = 1。

现在，给你两个字符串数组待查表 queries 和词汇表 words，请你找出其中 f(queries[i]) 的频数. 并比较 f(W), 找出其中 f(queries[i]) < f(W) 的词的数目，W 是词汇表 words 中的词。
返回一个整数数组 answer 作为答案, 依次表示出词汇表中比待查表中的最小字母出现频数更大的频数的次数.

示例 1：

输入：queries = ["cbd"], words = ["zaaaz"]
输出：[1]
解释：查询 "cbd" 中最小字母为 "b", f("cbd") = 1，而 "zaaaz"中最小字母为 "a", f("zaaz") = 3, f("cbd") < f("zaaaz"), 所以返回。



```



今天题意分析到此结束.

#### Code







