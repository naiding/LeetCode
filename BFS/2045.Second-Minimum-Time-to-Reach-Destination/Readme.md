### 2045.Second-Minimum-Time-to-Reach-Destination

Dijkstra算用可以用来求最短路径，自然也可以用来求第二短路径。我们只要在算法中略作改动：第一次从pq里弹出某节点node时对应的路径是最短路径arrival1[node]，此时我们一切照旧进行BFS；直到该节点被第二次从pq里弹出并且能更新为arrival2[node]之后，我们才禁止在pq里再加入node。

另外根据题意，假设当前cur被到达的时刻是t，那么有两种可能：t落在了绿灯时段，那么我们就可以在t+time时候到达nxt。如果t落在了红灯时段，那么我们必须在下一个绿灯时段开始后time再到达nxt。判断是否落在绿灯时段，就看t/change是否是偶数。判断何时是下一个绿灯时段的开始，我们就以```2*change```为一个周期，计算t落在了哪个周期```k=(t-1)/(2*change)+1```，那么```k*2*change```就是该周期结束、新周期开始的时刻。