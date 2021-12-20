### 有效的字母异位词
给定两个字符串 s 和 t ，编写一个函数来判断 t 是否是 s 的字母异位词。

注意：若 s 和 t 中每个字符出现的次数都相同，则称 s 和 t 互为字母异位词。

 

示例 1:

输入: s = "anagram", t = "nagaram"
输出: true
示例 2:

输入: s = "rat", t = "car"
输出: false
 

提示:

1 <= s.length, t.length <= 5 * 104
s 和 t 仅包含小写字母
 

进阶: 如果输入字符串包含 unicode 字符怎么办？你能否调整你的解法来应对这种情况？


链接：https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/xn96us/

来源：力扣（LeetCode）

---
方法一：排序比较

思路：若 s 和 t 中每个字符出现的次数都相同，则称 s 和 t 互为字母异位词，那么按照一定排序，为同一个字母序列组合。

```
var isAnagram = function(s, t) {
    var arrs = [...s].sort().toString();
    var arrt = [...t].sort().toString();
    if(arrs === arrt){ return true } else { return false }  
};
```
方法二：替换置空

思路：先判断字符串长度，遍历拿出s每个字符去替换置空t的相同的字符串
```
var isAnagram = function(s, t) {
    const sLen = s.length;
    const tLen = t.length;

    if(sLen !== tLen) return false;

    for(let i = 0;i < sLen; i++){
        t = t.replace(s[i], '')
    }

    return !t.length
};
```