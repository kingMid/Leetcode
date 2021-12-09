给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

说明：

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

示例 1:

输入: [2,2,1]
输出: 1
示例 2:

输入: [4,1,2,1,2]
输出: 4


链接：https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/x21ib6/
来源：力扣（LeetCode）
---
方法一：双指针（时间复杂度 O(n)）

思路：先排序,相同的一定相邻，先排除第一个就是独狼和只有一个值两种情况，如果nums[0]不等于nums[1],一定是nums[0]是独狼（前提是排序完的数组），
接着遍历，如果相邻相等则不做处理，如果相邻不相等，判断后一个值于它下一个相邻的值是否相等，如果不相等，则它就是独狼，直到剩下最后个值还没找到就是最后一个值。

```
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    const arr = nums.sort((a, b) => a - b);
    let len = nums.length;
    let i = 0;
    if(len === 1){
        return arr[0];
    } else if(arr[0] !== arr[1]){
       return arr[0]
    } else{
        for(let j = 1; j<len-1; j++){
            if( arr[i] === arr[j]){
                i++;
            } else {
                if(arr[j] !== arr[j+1]){
                    return arr[j]
                } else {
                    i ++;
                }
            }
        }
        return arr[len-1]
    }
};
```
---
第二种：异或运算（降维打击）

思路：异或运算，两数异或，相同为0，不同为1，0^任何数=任何数，而且异或满足交换律：a^b^a^b^c = a^a^b^b^c=0^0^C = C，nice!

```
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
 let res = 0;
 for(let i = 0; i < nums.length; i++){res ^= nums[i]}
 return res;
};
```
