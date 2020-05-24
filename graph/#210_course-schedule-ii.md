现在你总共有 n 门课需要选，记为 0 到 n-1。在选修某些课程之前需要一些先修课程。
例如，想要学习课程 0 ，你需要先完成课程 1 ，我们用一个匹配来表示他们: [0,1]。
给定课程总量以及它们的先决条件，返回你为了学完所有课程所安排的学习顺序。
可能会有多个正确的顺序，你只要返回一种就可以了。如果不可能完成所有课程，返回一个空数组。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/course-schedule-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

拓扑排序问题，可以对图进行深度优先搜索或广度优先搜索。
我采用的是广度优先搜索。首先找到入度为0的节点，删除以这些节点为起始的边，再找到新的入度为0的节点。重复该过程。

```python
class Solution:
    def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
        prev = collections.defaultdict(list)
        indegree = [0] * numCourses
        for c, p in prerequisites:
            prev[p].append(c)
            indegree[c] += 1

        result = []
        queue = [i for i in range(numCourses) if not indegree[i]]
        while queue:
            node = queue.pop(0)
            result.append(node)
            numCourses -= 1
            
            for cur in prev[node]:
                indegree[cur] -= 1
                if indegree[cur] == 0:
                    queue.append(cur)
        if numCourses > 0:
            result = list()
        return result           
```
需要注意的细节：不要对邻接表进行删除操作，这样消耗的时间长。
