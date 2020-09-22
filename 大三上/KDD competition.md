<img src="C:\Users\Echo-\AppData\Roaming\Typora\typora-user-images\image-20200921181919299.png" alt="image-20200921181919299" style="zoom:50%;" />

* 时间特征
  * 日期变量    时间差    时序相关特征
  * 周期性
  * 趋势性
  * 强相关
  * 异常点

<img src="C:\Users\Echo-\AppData\Roaming\Typora\typora-user-images\image-20200921184741584.png" alt="image-20200921184741584" style="zoom:50%;" />

<img src="C:\Users\Echo-\AppData\Roaming\Typora\typora-user-images\image-20200921185022374.png" alt="image-20200921185022374" style="zoom:50%;" />

<img src="C:\Users\Echo-\AppData\Roaming\Typora\typora-user-images\image-20200921185220214.png" alt="image-20200921185220214" style="zoom: 33%;" />

stacking



![image-20200921204258995](C:\Users\Echo-\AppData\Roaming\Typora\typora-user-images\image-20200921204258995.png)

![image-20200921204859034](C:\Users\Echo-\AppData\Roaming\Typora\typora-user-images\image-20200921204859034.png)









1、混淆矩阵（Confuse Matrix）

- （1）若一个实例是正类，并且被预测为正类，即为真正类TP(True Positive )
- （2）若一个实例是正类，但是被预测为负类，即为假负类FN(False Negative )
- （3）若一个实例是负类，但是被预测为正类，即为假正类FP(False Positive )
- （4）若一个实例是负类，并且被预测为负类，即为真负类TN(True Negative )

2、准确率（Accuracy） 准确率是常用的一个评价指标，但是不适合样本不均衡的情况。 
$$
Accuracy = \frac{TP + TN}{TP + TN + FP + FN}
$$
3、精确率（Precision） 又称查准率，正确预测为正样本（TP）占预测为正样本(TP+FP)的百分比。 
$$
Precision = \frac{TP}{TP + FP}
$$
4、召回率（Recall） 又称为查全率，正确预测为正样本（TP）占正样本(TP+FN)的百分比。
$$
Recall = \frac{TP}{TP + FN}
$$
5、F1 Score 精确率和召回率是相互影响的，精确率升高则召回率下降，召回率升高则精确率下降，如果需要兼顾二者，就需要精确率、召回率的结合F1 Score。
$$
F1-Score = \frac{2}{\frac{1}{Precision} + \frac{1}{Recall}}
$$
6、P-R曲线（Precision-Recall Curve） P-R曲线是描述精确率和召回率变化的曲线

<img src="https://camo.githubusercontent.com/25688baabbff569136e19f04c812ed80af778351/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303931333031303232363132352e706e67" alt="p-r" style="zoom: 50%;" />



7、ROC（Receiver Operating Characteristic）

- ROC空间将假正例率（FPR）定义为 X 轴，真正例率（TPR）定义为 Y 轴。

TPR：在所有实际为正例的样本中，被正确地判断为正例之比率。 $$TPR = \frac{TP}{TP + FN}$$ FPR：在所有实际为负例的样本中，被错误地判断为正例之比率。 $$FPR = \frac{FP}{FP + TN}$$

![roc.png](https://camo.githubusercontent.com/2dfea351fa5eac42caab9e716aa76a20553e4103/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303931333031303232363132342e706e67)

8、AUC(Area Under Curve) AUC（Area Under Curve）被定义为 ROC曲线 下与坐标轴围成的面积，显然这个面积的数值不会大于1。又由于ROC曲线一般都处于y=x这条直线的上方，所以AUC的取值范围在0.5和1之间。AUC越接近1.0，检测方法真实性越高;等于0.5时，则真实性最低，无应用价值。

##### 对于金融风控预测类常见的评估指标如下:

1、KS(Kolmogorov-Smirnov) KS统计量由两位苏联数学家A.N. Kolmogorov和N.V. Smirnov提出。在风控中，KS常用于评估模型区分度。区分度越大，说明模型的风险排序能力（ranking ability）越强。 K-S曲线与ROC曲线类似，不同在于

- ROC曲线将真正例率和假正例率作为横纵轴

- K-S曲线将真正例率和假正例率都作为纵轴，横轴则由选定的阈值来充当。 公式如下

- $$
  KS=max(TPR-FPR)
  $$

-  KS不同代表的不同情况，一般情况KS值越大，模型的区分能力越强，但是也不是越大模型效果就越好，如果KS过大，模型可能存在异常，所以当KS值过高可能需要检查模型是否过拟合。以下为KS值对应的模型情况，但此对应不是唯一的，只代表大致趋势。

| KS（%） | 好坏区分能力         |
| ------- | -------------------- |
| 20以下  | 不建议采用           |
| 20-40   | 较好                 |
| 41-50   | 良好                 |
| 51-60   | 很强                 |
| 61-75   | 非常强               |
| 75以上  | 过于高，疑似存在问题 |

2、ROC

3、AUC