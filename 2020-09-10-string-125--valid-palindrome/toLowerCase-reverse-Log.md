#### Question [125. 验证回文串](https://leetcode-cn.com/problems/valid-palindrome/)/[Valid Palindrome](https://leetcode-cn.com/problems/valid-palindrome/)

tag#string#



#### Description

```
给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。

说明：本题中，我们将空字符串定义为有效的回文串。

示例 1:

输入: "A man, a plan, a canal: Panama"
输出: true
示例 2:

输入: "race a car"
输出: false

```





#### Analysis

题意分析:

首先了解 "回文符" 的定义:

> 回文串的定义:
>
> 从前往后读, 再从后往回读, 都是一样的字符串, 就是回文串.
>
> 短的回文串如 `aacaa` 回过来读也是 `aacaa`
>
> 长的回文串如 `A man, a plan, a canal: Panama` (只考虑字母和数字的话, 这里忽略 `:` 和 `P` 和 `p` 的差别) .

判断给定字符串属不属于回文字符串.

只不过这里的回文稍微不同的嗲放在于, **不区分大小写** , 其次, 如果不计入标点符号.

也就是说, 只要其中的字母和数字符合回文的要求, 就属于一个回文字符串.

解题分析:

首先将原字符串中非数字和字母的字符剔除, 这一步可以用只取出其中的字母数字字符.

接着将其反转和原字符串你比对是不是回文.

这一步可以用双指针法, 比对. 加上一个布尔值变量, 如遇异常情况则视为不符合要求.





#### Code

```java
class Solution {
    public boolean isPalindrome(String s) {
        // 本题中，我们将空字符串定义为有效的回文串。
        if (s == null) return true;
        //  1. 不区分大小写, 无论字符串大小写都属于同一字符, 统一变小写方便后面匹配
        s = s.toLowerCase();
        int l = s.length();
        //  2. 新建一个与目标字符串相同长度的 StringBuilder 对象
        StringBuilder str = new StringBuilder(l);
        //  3. 遇到数字或者(小写)字母的时候追加, 构建目标 StringBuilder (此处只需要判断小写字母)
        for (char c : s.toCharArray()) {
            if ((c >= '0' && c <= '9') || (c >= 'a' && c <= 'z')) {
                str.append(c);
            }
        }
        //  4. 问, StringBuilder 内的字符串与 reverse 后的字符串值相等不相等.
        return str.toString().equals(str.reverse().toString());
    }
}
```

分析:

两大步: 

1.构建字符串中由字母构成的 StringBuidler;

2.反转字符串判断是否值相等.

**因为忽略大小写, 所以那里面原大写的转对应的小写, 然后再当作小写字母之间的判等也没关系.**



##### commit 1

效果: **395 / 481** 个通过测试用例

```java
class Solution {
    public boolean isPalindrome(String s) {
        char[] org = new char[s.length()];
        org = s.toCharArray();
        List<String> list = new ArrayList<>();
        StringBuilder sb = new StringBuilder();
        //  遍历字符数组, 当数组项属于字母和数字范围内时, 加入 StringBuidler 对象
        for (int i = 0; i < org.length; i++) {
            if ( ((org[i] >= 48) && (org[i] <= 57)) || ((org[i] >= 65)&&(org[i]<=90)) ||
            ((org[i] >= 97) && (org[i] <= 122))) {
                sb.append(org[i]);
            }
        }        
        String x = sb.toString();
        
        char[] newArr = new char[x.length()];
        for (int i = 0; i < x.length(); i++) {
            newArr[i] = x.charAt(0);
        }
                
        boolean allSame = true;
        for (int i = 0; i <= newArr.length/2; i++) {
            for (int j = (newArr.length-1); j >= newArr.length/2+1; j--) {
                if (newArr[i] != newArr[j]) 
                    allSame = false;
            }
        }        
        return allSame;
    }
}
```



> 测试用例分析:
>
> ```
> 输入：
> "race a car"
> 输出：
> true
> 预期：
> false
> ```
>
> 中间的部分: 偶数位的比较.

