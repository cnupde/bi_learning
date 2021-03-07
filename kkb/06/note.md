
# 心得笔记



Policy Gradients方法训练策略网络。模型通过学习Action在Environment获得反馈，用梯度更新模型参数。训练过程，模型接触到好Action及高期价值，和差Action及低期望价值。通过样本学习，模型逐渐增加选择好Action概率，降低选择坏Action概率，完成策略学习。直接学习当前环境应该采取策略，如选择Actionc概率，或Action具体数值。策略网络是End-to-End(端对端)方法，直接产生最终策略。

Policy-Based比Value-Based，收敛性更好，通常可以保证收敛到局部最优，且不会发散。对高维、连续值Action，训练、输出结果都更高效。能学习出带有随机性的策略。

## MCTS

MCTS，即蒙特卡罗树搜索，是一类搜索算法树的统称，可以较为有效地解决一些搜索空间巨大的问题。

如一个8*8的棋盘，第一步棋有64种着法，那么第二步则有63种，依次类推，假如我们把第一步棋作为根节点，那么其子节点就有63个，再往下的子节点就有62个……

如果不加干预，树结构将会繁杂，MCTS采用策略来对获胜性较小的着法不予考虑，如第二步的63种着法中有10种是不可能胜利的，那么这十个子节点不予再次分配子节点。

MCTS的主要步骤分为四个：

1， 选择（Selection）

即找一个最好的值得探索的结点，通常是先选择没有探索过的结点，如果都探索过了，再选择UCB值最大的进行选择（UCB是由一系列算法计算得到的值，这里先不详细讲，可以简单视为value）

2， 扩展（Expansion）

已经选择好了需要进行扩展的结点，那么就对其进行扩展，即对其一个子节点最为下一步棋的假设，一般为随机取一个可选的节点进行扩展。

3， 模拟（Simulation）

扩展出了子节点，就可以根据该子节点继续进行模拟了，我们随机选择一个可选的位置作为模拟下一步的落子，将其作为子节点，然后依据该子节点，继续寻找可选的位置作为子节点，依次类推，直到博弈已经判断出了胜负，将胜负信息作为最终得分。

4， 回溯更新（Backpropagation）

将最终的得分累加到父节点，不断从下向上累加更新。