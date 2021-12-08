### There are duplicate elements
给定一个整数数组，判断是否存在重复元素。

如果存在一值在数组中出现至少两次，函数返回 true 。如果数组中每个元素都不相同，则返回 false 。

 

示例 1:

输入: [1,2,3,1]
输出: true
示例 2:

输入: [1,2,3,4]
输出: false
示例 3:

输入: [1,1,1,3,3,4,3,2,4,2]
输出: true


链接：https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/x248f5/
来源：力扣（LeetCode）
---
方法一:暴力双层循环大法( 时间复杂度T(n)=O( n<sup>2</sup>) )

思路:遍历所有元素一一比较是否有相同的值，有返回true,直到遍历而结束没有相同值返回false

```
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
  let len = nums.length;
  for(let i = 0; i < len; i++){
    for(let j = i + 1; j < len; j++){
        if(nums[i] === nums[j]){
            return true;
        }
    }
  }
  return false;
};
```
方法二：排序双指针法（时间复杂度T(n)=O(n)）

思路：先把数组排序那么相同的值一定是相邻的，只要遍历一次比较两两相邻的数是否相等即可；
```
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
  let arr = nums.sort((a,b)=>a-b);
  let len = nums.length;
  let i =0;
  for(let j = 1; j < len; j++){
    if(arr[i] !== arr[j]){
        i++;
    } else{
        return true;
    }
  }
  return false;
};
```
方法三：Set方法

思路：使用Set方法去重再和原数组比较长度，一样长返回false,不一样长返回true

```
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
  if([... new Set(nums)].length === nums.length){
    return false;
  } else{
    return true;
  }
};
```

