# Thinking1 都有哪些模型具有特征可解释性？
* 线性回归
* 逻辑回归
* 决策树
* 支持向量机
* K最近邻

等

# Thinking2 评分卡模型中的A卡、B卡、C卡分别指的是什么？
按照不同的业务阶段，可以划分为三种:
* 贷前：申请评分卡（Application score card），称为A卡
* 贷中：行为评分卡（Behavior score card），称为B卡
* 贷后：催收评分卡（Collection score card），称为C卡

评分机制的区别在于：

* 使用的时间不同。分别侧重贷前、贷中、贷后
* 数据要求不同。A卡一般可做贷款0-1年的信用分析，B卡则是在申请人有了一定行为后，有了较大数据进行的分析，一般为3-5年，C卡则对数据要求更大，需加入催收后客户反应等属性数据
* 每种评分卡的模型会不一样。在A卡中常用的有逻辑回归，AHP等，而在后面两种卡中，常使用多因素逻辑回归，精度等方面更好

# Thinking3 评分卡模型的开发流程是怎样的？

评分卡模型开发步骤：
* Step1，数据获取，包括获取存量客户及潜在客户的数据
  * 存量客户，已开展融资业务的客户，包括个人客户和机构客户；
  * 潜在客户，将要开展业务的客户
* Step2，EDA，获取样本整体情况，进行直方图、箱形图可视化
* Step3，数据预处理，包括数据清洗、缺失值处理、异常值处理
* Step4，变量筛选，通过统计学的方法，筛选出对违约状态影响最显著的指标。主要有单变量特征选择和基于机器学习的方法
* Step5，模型开发，包括变量分段、变量的WOE（证据权重）变换和逻辑回归估算三个部分
* Step6，模型评估，评估模型的区分能力、预测能力、稳定性，并形成模型评估报告，得出模型是否可以使用的结论
* Step7，生成评分卡（信用评分），根据逻辑回归的系数和WOE等确定信用评分的方法，将Logistic模型转换为标准评分的形式
* Step8，建立评分系统（布置上线），根据生成的评分卡，建立自动信用评分系统

# Thinking4 变量分箱都有哪些方法？

* 等频分箱，把自变量从小到大排序，根据自变量的个数等分为k部分，每部分作为一个分箱
* 等距分箱，把自变量从小到大排序，将自变量的取值范围分为k个等距的区间，每个区间作为一个分箱
* 聚类分箱，用k-means聚类法将自变量聚为k类，但在聚类过程中需要保证分箱的有序性
