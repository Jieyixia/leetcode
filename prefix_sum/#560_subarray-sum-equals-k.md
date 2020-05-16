给定一个整数数组和一个整数 k，你需要找到该数组中和为 k 的连续的子数组的个数。用到哈希表降低时间复杂度。
```python
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        n = len(nums)

        count = 0
        dic = {0:1}
        prefixSum = 0
        for i in range(n):
            prefixSum += nums[i]
            if prefixSum - k in dic:
                count += dic[prefixSum - k]
            if prefixSum in dic:
                dic[prefixSum] += 1
            else:
                dic[prefixSum] = 1
        return count
```
