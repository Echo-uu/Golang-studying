### 决策树

常见算法：ID3, C4.5, C5.0, CART(Classification And Regression Tree)

最佳划分的度量问题（如何选择最佳划分属性，使节点的不纯度(impurity)最低）

记不纯度的降低程度为$ \Delta$
$$
\Delta_I = I_{(parent)} - \sum_{j=1}^k\frac{N(j)}{N}I(j)
$$
$I_{(parent)}$ 是父结点的不纯度度量，$k$ 是划分属性取值的个数。$N$ 是父亲结点上样本的总数，$N(j)$ 是第 j 个儿子结点上样本的数目，$I(j)$ 是第 j 个儿子结点的不纯度度量

不纯度度量

* 熵 Entropy

$$
Entropy(t) = -\sum_{i=1}^{c}{p(i)log_2p(i)}

$$

* 基尼指数 Gini ：从数据集中随机抽取两个样本，其类别标记不一致的概率

$$
Gini(t) = 1-\sum_{i=1}^{c}{p(i)}^2
$$

* 误分类率 Error

$$
Error(t)=1-max_ip(i)
$$

$c$ 为类别数目

#### ID3

由增熵(Entropy) 原理来决定哪个作为父节点，哪个节点需要分裂（熵越小，分类效果越好）

* 熵 

$$
Entropy(t) = - \sum_j{p(j|t)log_2p(j|t)}\ \ \ \ \  \ p(j|t) 表示在节点 t 上数据属于类 j 的概率
$$

* 信息增益 
  $$
  gain(A) = Entropy(D) - Entropy_A(D)
  $$

* 缺点：Overfitting

<img src="https://upload-images.jianshu.io/upload_images/10758717-2de8925cda56cad1.png?imageMogr2/auto-orient/strip|imageView2/2/w/996/format/webp" alt="img" style="zoom:50%;" />

#### C4.5

优化项要除以分割太细的代价，这个比值为 信息增益率。分割太细则分母增大，信息增益率降低

$$
GainRATIO_{split} = \frac{GAIN_{Split}}{SplitINFO}
\\ 
SplitINFO = -\sum_{i=1}^{k}{\frac{n_i}{n}log\frac{n_i}{n}}
\\
SplitINFO(S,A)：数据集S关于属性A的熵，值越大表示S在A上分布越均匀
$$

* Q: 若当前划分属性在当前结点几乎都是相同的值则$SplitINFO\rightarrow 0，GainRATIO\rightarrow \infty$，**启发式方法**：先计算每个属性的信息增益及平均值，然后**仅对信息增益高于平均值的属性应用增益率度量**。

* AverGain 平均增益度量

$$
AverGain = \frac{\Delta_{Info}}{k}
\ \ \ \ \ \ \ \ \ \ \ \ \ 
k是划分属性取值的个数
$$





