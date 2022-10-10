# 计量经济学


## 0 假设检验 
[本节首先考虑最简单的假设检验，即对单个系数进行检验。需要检验的"原假设"（mullhypothesis，也称为"零假设"）为H。∶A=β，，其中B为给定的常数。通常B=0，此时即检验是否变量x的系数显著地不等于0。假设检验的实质是一种概率意义上的反证法，即首先假设原假设成立，然后看在原假设成立的前提下，是否导致不太可能发生的"小概率事件"在一次抽样中出现。如果小概率事件竟然在一次抽样实验中被观测到，则说明原假设不可信，应该拒绝原假设，接受"替代假设"（alternative hypothesis，也称为"备择假设"）H，∶BA≠β。](obsidian://booknote?type=annotation&book=%E5%AE%9E%E8%AF%81/Book/%E9%AB%98%E7%BA%A7%E8%AE%A1%E9%87%8F%E7%BB%8F%E6%B5%8E%E5%AD%A6%E5%8F%8AStata%E5%BA%94%E7%94%A8++%E7%AC%AC2%E7%89%88_%E9%99%88%E5%BC%BA%E7%BC%96%E8%91%97_13526050(OCR).pdf&id=5d2c1dcb-d5c7-71d1-629e-65e8bc316c40&page=35&rect=28,89.930,470.000,182.756)
t检验的步骤：
![[40-Booknote/books-data/实证/Book/(annots)高级计量经济学及Stata应用++第2版_陈强编著_13526050(OCR).pdf/p37r18.130,196.533,477.550,570.383z2i(8d456ecf-e38b-a275-144a-ad7515a066e7).png#center|766]]
p值：
![[40-Booknote/books-data/实证/Book/(annots)高级计量经济学及Stata应用++第2版_陈强编著_13526050(OCR).pdf/p37r19.990,60.293,477.550,195.603z2i(e50af3a1-23b9-e81a-b7c8-e7e752194029).png#center|763]]
**p值越小越倾向于拒绝原假设（零假设）**
## 1. 交互效应

^66ccdb

[【计量地图】交互效应|进来唠唠机制分析中的“交互效应” - 吴晶晶的文章 - 知乎 ](https://zhuanlan.zhihu.com/p/120310111)
![思维导图](https://gmc-1258067706.cos.ap-chengdu.myqcloud.com/20220219154623.png)



## 2. 知名会议
 https://www.cistconf.org/
http://www.wiseconf.org/
https://icis2021.aisconferences.org/
http://www.scecr.org/
http://2021.cswimworkshop.org/program/
https://ide.mit.edu/events/2021-conference-on-digital-experimentation-mit-codemit/#:~:text=The%20purpose%20of%20the%20Conference,computer%20science%20and%20sociology%2C%20in

## 3 零膨胀泊松回归（ZIP）& 零膨胀负二项回归（ZINB）
**二者使用分布不同，ZINB多了一个离散参数**
**ZINB比ZIP更适用于存在过离散特征的数据**


## 4 缩尾/截尾
使用命令`winsor2`
缩尾与截尾是处理离群值的方法，区别是缩尾是将离群值替换为1%和99%的值，而截尾是直接把离群值丢掉
```stata
//缩尾
winsor2 variable ,replace cut(1 99)
```
```stata
//截尾
winsor2 variable ,replace cut(1 99) trim
```


## 5 中介效应和调节效应

## 6 面板logit模型
![[Pasted image 20220328204620.png|500]]
Stata的输出结果中，包含了对原假设"$H_0: \rho =0$"的LR检验结果（Stata将$\rho$记为"rho"）。如果拒绝"$H_0: \rho =0$"，则认为应采用随机效应模型;反之，则支持混合回归。上表最后一行可知，LR 检验的强烈拒绝原假设，认为应使用面板随机效应模型，不宜进行混合回归。
选择re还是fe可以用 hausman检验

## 7 聚类稳健标准误
[另外，无论OIM、OPC法，还是（胡贝尔-怀特）稳健标准误都假设样本数据为id。**如果样本数据可分为若干组，而同一组内的观测值存在自相关，则应使用"聚类稳健标准误"（cluster-robust standard erors），在Stata中由选择项"vce（cluster clustvar）"来实现，其中"clustvar"为聚类变量（详见第8章8.4节）**。总之，对于线性回归模型，通常建议总是使用稳健标准误。而对于非线性模型，可以分为以下四种情况来考虑。（i）如果对模型设定较有信心或模型拟合得较好，则可以不用稳健标准误。（ii）如果对模型设定缺乏信心，而且QMLE为一致估计，则应使用稳健标准误。（）如果对模型设定缺乏信心，但QMLE也不一致，则应首先担心QMLE估计量的一致性，仅仅使用稳健标准误进行校正是无济于事的。（iv）对于聚类样本，应使用聚类稳健的标准误。](obsidian://booknote?type=annotation&book=%E5%AE%9E%E8%AF%81/Book/%E9%AB%98%E7%BA%A7%E8%AE%A1%E9%87%8F%E7%BB%8F%E6%B5%8E%E5%AD%A6%E5%8F%8AStata%E5%BA%94%E7%94%A8++%E7%AC%AC2%E7%89%88_%E9%99%88%E5%BC%BA%E7%BC%96%E8%91%97_13526050(OCR).pdf&id=2deebfe9-eb7b-61af-ea42-072ccb8a4082&page=94&rect=29,96.184,477.000,265.110)

## 8 固定效应 or 随机效应
采用hausman检验，如果prob很小，选择固定效应，否则随机效应

## 9 wald chi2
回归结果中wald chi2的 prob如果很小说明模型有效果


zhelihenzhongyao
[Balanced order batching problem (BOBP) arises from the processof warehouse picking in Cainiao, the largest logistics platform inChina. Batching orders together in the picking process to forma single picking route, reduces travel distance. The reason for itsimportance is that order picking is a labor intensiv](obsidian://booknote?type=annotation&book=null&id=4f78907c-9e5a-e9ac-c8cc-c2051bd8be3e&page=1&rect=53.798,566.228,294.047,619.894)


$x_i$

$$
x_i$$
```theory
att
```
