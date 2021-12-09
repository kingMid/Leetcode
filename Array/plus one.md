### 加一
给定一个由 整数 组成的 非空 数组所表示的非负整数，在该数的基础上加一。

最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。

你可以假设除了整数 0 之外，这个整数不会以零开头。

 

示例 1：

输入：digits = [1,2,3]
输出：[1,2,4]
解释：输入数组表示数字 123。
示例 2：

输入：digits = [4,3,2,1]
输出：[4,3,2,2]
解释：输入数组表示数字 4321。
示例 3：

输入：digits = [0]
输出：[1]


提示：

1 <= digits.length <= 100
0 <= digits[i] <= 9


链接：https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/x2cv1c/
来源：力扣（LeetCode）
---
方法一：字符串转化法
思路：将数组转化成字符串，再隐式转化成number类型进行计算，这里要注意到js最大整数只能表示2<sup>53</sup>-1，所用使用BigInt类型
计算完成，再转化成数组即可。

```
/**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function(digits) {
    return (BigInt(digits.join("")) + 1n).toString().split("");
};
```
---
方法二：模拟十进制对数组进行计算

思路：逢十进一，题目只加一，所有位数上是9的情况才会有进位计算可能，没遇到直接+1返回,如果遇到全是9的，只需要判断最高位是否为0的，为0则手动再数组最前面添加1

```
 /**
 * @param {number[]} digits
 * @return {number[]}
 */
 /**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function(digits) {
  let i = digits.length - 1;
  for(; i >= 0; i--){
    if(digits[i] !== 9){
        digits[i]++;
        return digits;
    } else {
        digits[i] = 0;
    }
  }
  if(digits[0] === 0){
    return [1,...digits]
  }
}; 
```
