# Sparkify

**项目概述&目的**：这是一个虚拟的音乐服务数据集，拥有过千万用户，用户可以随时升级、降级、取消他们的套餐。用户的动态、意向可以直接影响到服务的盈利；而每次用户的操作都会被记录(即具体动作例如收藏、升级、降级、播放歌曲、添加歌单等)，这些数据对于服务商而言有着重要价值，可从该数据中发现某些用户的某些操作的共通点，来判断该用户接下来会进行什么样的操作， 本次任务的目标是寻找潜在客户，而潜在客户也分为潜在意向客户和流失客户，本次我们要利用机器学习找到那些流失(即将流失)的客户，寻找他们的共同特征，利用优惠、试用等手段控制损失。


### 项目分为两个文件，其中Sparkify-zh为SparkifyNotebook的子集，是一个小数据集，主要用来展示可视化(大数据文件所工作的AWS换境没有pandas)；SparkifyNotebook才是主要的文件，用于作对数据的具体分析；两个html文件也是如此。

#### 环境&依赖库
- Python
- PySpark 分布式机器学习库
- matplotlib 可视化库
- numpy 科学计算库

### 总结：
- 本次项目我们建立了一个模型来预测客户的流失。
- 在数据清洗过程中，我们把userId和sessionId为空的条目过滤掉。
- 在数据探索阶段，我们给数据集加上了标签，以便标记哪些是流失用户。
- 在可视化阶段，我们得知了男性用户的流失率较女性大。
- 在特征阶段，我们选取了**听歌平均时长、听歌总数、用户所关注的艺术家总数、行别、等级、地点、方法** 等字段作为输入特征。
- 最后发现线性回归是该项目最佳模型。

### 评价指标
Accuracy：准确率，该指标的高低能直接决定模型的完善程度，但需要结合训练集和测试集来下定论，如果训练集准确率太高，但训练集准确率过低，那模型就会过拟合；如果训练集和测试集的accuracy都太低，则说明欠拟合。

### 难点
过程中发现超参数调优是比较难的，而且由于数据集庞大，每次运行都要花飞好长时间，在AWS里面时间意味着美元；但完成了第一版项目以后觉得各个模型之间的优势劣势和侧重点依然不太清晰明了，以上三个模型都是在心里牢记的模型，至于哪一个更适用于本次项目，脑海里始终是"二元分类线性回归较好"，对概念还不是很明确，可能在以后的工作中才能慢慢熟悉。

### 代码的改进
一开始没有使用网格搜索导致完全使用参数默认值去判定模型的优劣，这是不准确的，后来经过多次搜索后慢慢掌握了网格搜索的用法(课程里面的恕在下愚笨)，才慢慢通过网格搜索来对超参数进行调优。

### 参考文献
[https://stackoverflow.com/questions/52498970/how-to-get-the-best-hyperparameter-value-after-crossvalidation-in-pyspark]
[https://spark.apache.org/docs/2.0.1/api/java/org/apache/spark/ml/evaluation/BinaryClassificationEvaluator.html]
[https://spark.apache.org/docs/latest/api/python/pyspark.mllib.html#pyspark.mllib.evaluation.BinaryClassificationMetrics]
[https://stackoverflow.com/questions/37707305/pyspark-multiple-conditions-in-when-clause]
