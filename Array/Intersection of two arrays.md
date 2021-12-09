给你两个整数数组 nums1 和 nums2 ，请你以数组形式返回两数组的交集。返回结果中每个元素出现的次数，应与元素在两个数组中都出现的次数一致（如果出现次数不一致，则考虑取较小值）。可以不考虑输出结果的顺序。

 

示例 1：

输入：nums1 = [1,2,2,1], nums2 = [2,2]
输出：[2,2]
示例 2:

输入：nums1 = [4,9,5], nums2 = [9,4,9,8,4]
输出：[4,9]


提示：

1 <= nums1.length, nums2.length <= 1000
0 <= nums1[i], nums2[i] <= 1000


进阶：

如果给定的数组已经排好序呢？你将如何优化你的算法？
如果 nums1 的大小比 nums2 小，哪种方法更优？
如果 nums2 的元素存储在磁盘上，内存是有限的，并且你不能一次加载所有的元素到内存中，你该怎么办？

链接：https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/x2y0c2/
来源：力扣（LeetCode）

---
方法一：遍历查找

思路：遍历数组nums1,拿到每个值去查找nums2包不包括这个值，包括就插入结果数组，并删除nums2中的这个值，避免多次计算该值。

```
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
    let len1 = nums1.length;
    let arr = []
    for(let i= 0; i < len1; i++){
        if( nums2.includes(nums1[i])){
            nums2.splice(nums2.indexOf(nums1[i]), 1)
            arr.push(nums1[i])
        }
    }
    return arr;
};
```
---
方法二：双指针法

思路：先把两个数组统一一种次序排序，两个指针分别指向两个数组的起始位置，开始遍历比较两个指针的值是否相同，相同则取该值加入到结果数组，不同，则判断谁小，谁的指针前移，再比较，直到一方指针到终点，结束遍历。

```
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
    let len1 = nums1.length;
    let len2 = nums2.length;
    let arr = [];
    let arr1 = nums1.sort((a, b) => a - b);
    let arr2 = nums2.sort((a, b) => a - b);
    let i = 0, j = 0; 
    while(i < len1 && j< len2){
        if(arr1[i] === arr2[j]){
            arr.push(arr2[j]);
            i++;
            j++;
        }else if(arr1[i] < arr2[j]){
            i++;
        } else {
            j++;
        }
    }
    return arr;
};
```
