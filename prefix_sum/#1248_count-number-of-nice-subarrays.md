给你一个整数数组 nums 和一个整数 k。
如果某个 连续 子数组中恰好有 k 个奇数数字，我们就认为这个子数组是「优美子数组」。
请返回这个数组中「优美子数组」的数目。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/count-number-of-nice-subarrays
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

和#560类似，前缀和中保存的不是子数组之和，而是子数组中奇数的个数。同样，使用哈希表降低时间复杂度。
```python
class Solution:
    def numberOfSubarrays(self, nums: List[int], k: int) -> int:
        dic = {0:1}
        odds = 0
        count = 0
        for i in range(len(nums)):
            odds += nums[i] % 2

            if odds - k in dic:
                count += dic[odds - k]
            
            if odds in dic:
                dic[odds] += 1
            else:
                dic[odds] = 1

        return count 
```
