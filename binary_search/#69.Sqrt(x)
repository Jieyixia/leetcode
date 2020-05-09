题目：实现 int sqrt(int x) 函数。计算并返回 x 的平方根，其中 x 是非负整数。返回类型是整数，结果只保留整数的部分，小数部分将被舍去。
解答：


```python
class Solution:
    def mySqrt(self, x: int) -> int:
        
        l, r = 0, x
        
        while l <= r:
            mid = l + (r - l) // 2
            if mid ** 2 == x:
                return mid
            
            if mid ** 2 > x:
                r = mid - 1
                
            else:
                l = mid + 1
        
        return r
            

```
