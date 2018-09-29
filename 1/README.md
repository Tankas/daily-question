# 两数之和
给定一个整数数组和一个目标值，找出数组中和为目标值的两个数。
你可以假设每个输入只对应一种答案，且同样的元素不能被重复利用。
示例:

给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

## code 


    /**
    * @param {number[]} nums
    * @param {number} target
    * @return {number[]}
    */
    var twoSum = function(nums, target) {
        var obj = {};
        for(var i=0;i<nums.length;i++){
            obj[nums[i]] = i;
        }
        for(var i=0;i<nums.length;i++){
            var com = target - nums[i];
            if(obj[com] && obj[com] != i){
                return [i , obj[com]];
            }
        }
    };

##解题思路 
最简单的方法 , 两层循环 , 时间复杂度o(n2);</br>
这里用了哈希表 , 空间换时间 , 时间复杂度o(n);</br>
*解题关键点 , 理解哈希表, 查找速度o(1);
