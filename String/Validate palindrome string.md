### 验证回文串
给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。

说明：本题中，我们将空字符串定义为有效的回文串。

 

示例 1:

输入: "A man, a plan, a canal: Panama"
输出: true
解释："amanaplanacanalpanama" 是回文串
示例 2:

输入: "race a car"
输出: false
解释："raceacar" 不是回文串


链接：https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/xne8id/

来源：力扣（LeetCode）
---

方法一：逆序比较

思路：先将大小写统一，去除非字母和数字，再逆序比较

```
var isPalindrome = function(s) {
    let arr = [...s.toLowerCase()];
    let res =[];
    let resver = [];
    for(let i = 0; i < arr.length; i++){
        if(/[a-z0-9]/.test(arr[i])){
            res.push(arr[i]);
            resver.unshift(arr[i]);
        }
    }
    if( res.toString() === resver.toString()){
        return true
    } else {
        return false
    }
};
```

方法二：对折比较

思路： 先将大小写统一，去除非字母和数字，再将字符串从中取半，循环比较是否相同

```
var isPalindrome = function(s) {
  let arr = [...s.toLowerCase().replace(/[^a-z0-9]/g,'')];
  console.log(arr)
  const arrLen = arr.length;
    let i = arrLen-1;
    for(let j = 0; j< parseInt(arrLen/2);j++){
        if(arr[j]==arr[i]){
            i--;
        }else{
            return false
        }
    }
    return true
};
```