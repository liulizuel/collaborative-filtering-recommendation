# collaborative-filtering-recommendation
> collaborative filtering recommendation description and implementaion

## 基于用户的协同过滤推荐算法
	
### 基本思路：

    选取某个用户A的具有相似品味的邻居用户集合, 从邻居用户集合的历史评分以及用户A的历史评分综合考虑预测用户A给其未评价过的项目的评分结果, 选取预测分大于指标的项目推荐给用户A.
### 基本问题：

#### 1.选择的查找相似用户用到的算法：

	 k近邻算法、皮尔森相关系数法：
	
	（1）皮尔逊相关系数是余弦相似度在维度值缺失情况下的一种改进：
	https://www.cnblogs.com/charlesblc/p/8336765.html
	（2）k近邻选择时，用到推排序，选取相似度最高的前k个

> 
>  【1】k近邻（knn)和k-means聚类，有什么区别，哪一个比较适合用于协同过滤推荐系统？【我的思考是，如果存在大量0，或者某些用户评分次数较少，这个时候可以用基于模型的推荐算法，或者对用户多个特征或者物品做一个聚类，基于内容等，给类似的用户推荐】
>  
>  【2】需要做svd吗？【矩阵存在大量0的时候适用，属于基于模型的推荐算法中的矩阵分解方法】
>  

#### 2.预测评分的策略是：【我自己对这个地方有点疑问，这种预测方式是否可行？】

	计算相似用户对该项目的评分的加权平均分加上用户的历史平均分

#### 3.推荐结果选取的策略是：【是否有更好的方式？】

	选取预测分数大于用户历史平均分的项目作为推荐结果

#### 4.评价指标是：【是否还需要其他评价指标，如果有多个评价指标，如何选取较优方案】

	计算系统平均绝对误差 = sum(每个用户的平均绝对误差)/用户总数

#### 5.引入用户特征：

	重新对相似度取用户特征、皮尔森相关系数各自一个权重作为最终的相似的值
	
### Tips:

1.数据集：

	movieLens，从训练集中得出相似用户，去预测测试集中的评分，
	再与实际评分作对比

2.环境：

	（1）语言：python 3.8, 用到的库:【几乎没用到什么库】;

	（2）IDE：pycharm;

	（3）系统：Windows 7;

