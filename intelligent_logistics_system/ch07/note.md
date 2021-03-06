# Ortools求解器：
* 线性规划，默认使用GLOP
* 整数规划，默认使用CBC（Coin-or branch and cut），还包括SCIP、GLPK、Gurobi等
* 开源求解器，在计算性能和规模上弱于商业求解器，适用于中小企业及普通问题

# 旅行商问题（TSP）：
Travelling Salesman Problem，一个旅行商想去拜访若干城市，然后回到他的出发地，给定各个城市之间所需的旅行时间后，怎样计划他的路线，使得他能对每个城市恰好进行一次访问，而且总时间最短


# VRP(Vehicle Routing Problem):
车辆路径问题，可以看成旅行商问题的推广

有N辆车，都从原点出发，每辆车访问一些点后回到原点，要求所有的点都要被访问到，求最短的车辆行驶距离或最少需要的车辆数

# summary：

运筹学求解思路简单，但要找到满意的结果却很难
* 现在的求解思路类似暴力穷举，而求解的空间又是非常巨大的 => 不能在约束的时间内得到较好结果
* 针对凸优化问题（比如线性规划）可直接得到最优解
* 如果是非凸优化，无法判定是全局最优解还是局部最优解，在业界一般使用启发式算法，比如遗传算法
* 分支定界法，启发式算法核心原理是暴力穷举的改进，尽可能减少搜索空间，更快得到可行解
