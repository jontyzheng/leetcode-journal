#### Question  [替换所有的问号](https://leetcode-cn.com/problems/replace-all-s-to-avoid-consecutive-repeating-characters/)

tag#string#



#### Description

```
给你一个仅包含小写英文字母和 '?' 字符的字符串 s，请你将所有的 '?' 转换为若干小写字母，使最终的字符串不包含任何 连续重复 的字符。

注意：你不能修改非 '?' 字符。

题目测试用例保证除 '?' 字符之外，不存在连续重复的字符。

在完成所有转换（可能无需转换）后返回最终的字符串。如果有多个解决方案，请返回其中任何一个。可以证明，在给定的约束条件下，答案总是存在的。

 

示例 1：

输入：s = "?zs"
输出："azs"
解释：该示例共有 25 种解决方案，从 "azs" 到 "yzs" 都是符合题目要求的。只有 "z" 是无效的修改，因为字符串 "zzs" 中有连续重复的两个 'z' 。
示例 2：

输入：s = "ubv?w"
输出："ubvaw"
解释：该示例共有 24 种解决方案，只有替换成 "v" 和 "w" 不符合题目要求。因为 "ubvvw" 和 "ubvww" 都包含连续重复的字符。
示例 3：

输入：s = "j?qg??b"
输出："jaqgacb"
示例 4：

输入：s = "??yw?ipkj?"
输出："acywaipkja"
 

提示：

1 <= s.length <= 100

s 仅包含小写英文字母和 '?' 字符
```





#### Analysis

题意分析: 题目默认的是字符串中最多含有两种字符, 小写字母和 ?. 

要求只能修改其中的 ? 用别的小写字母替换, 替换后又不会和前后的重复.

只能修改其中的 ? 说明原来的字符已经是不重复的, 不需要修改.

解题分析: ? 出现的情况有两种, 一种是前面有字母的, 不能和前面的重复, 如果和前面的重复, 就要变到不一样. 一种是后面有字母的, 不能和后面的重复, 如果和后面的重复, 就不能是一样的.

两种情况都不能有.

前提: 遇到 ? 的字符.



#### Code

```java
class Solution {
    public String modifyString(String s) {
        int len = s.length();
        char[] sb = s.toCharArray();
        for (int i=0; i<len; i++) {
            if (sb[i] == '?') {
                char temp = 'a';		//	temp 是待会假设要替换掉 ? 的字符.
                if ((i>0 && sb[i] == temp) || (i<(len-1) && sb[i+1] == temp)) {
                    temp++;				
                }
                sb[i] = temp;
            }
        }
        return new String(sb)l
    }
}
```



规避两种可能情况:

```java
if (() || ())
```

先假设为 `a`, 再 **while 反面条件对 temp 的值进行修改** , **直到不再反面条件**.

```java
char temp = 'a';		//	temp 是待会假设要替换掉 ? 的字符.
if ((i>0 && sb[i] == temp) || (i<(len-1) && sb[i+1] == temp)) {
    temp++;				
}
```

`++` **也是一种运算**.



运行效果:

执行用时：2 ms, 在所有 Java 提交中击败了31.07%的用户





实际上需要考虑的情况也只有前面是字母后面是 ?, 后面是字母, 前面是 ? 两种情况.

```java
(i>0 && sb[i] == temp) || (i<(len-1) && sb[i+1] == temp)
```

包括了从 0 开始的情况.

第一个为 ?, 不能和后一个字符重复 当前位置为 ?, 不能和后一个字符相重复 是同一类情况.



从 0 走到 len-1, 每一个当前字符都会经过这样前后的匹配程序, 连续出现 ? 也包括在内了.