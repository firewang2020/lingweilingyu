[TOC]



# 第一章 绪论

## 1.1 引言

​		机器学习是这样一门学科，它致力于研究如何通过计算的手段，利用经验来改善系统自身的性能,在计算机系统中，“经验”通常以“数据”形式存在，因此，机器学习所研究的主要内容，是关于在计算机上从数据中产生“模型” (model)的算法，即“学习算法” (learning algorithm)。有了学习算法，我们把经验数据提供给它，它就能基于这些数据产生模型；在面对新的情况时(例如看到一个没剖开的西瓜)，模型会给我们提供相应的判断(例如好瓜)。如果说计算机科学是研究关于“算法”的学问，那么类似的，可以说机器学习是研究关于“学习算法”的学问。

​		Mitchell 在1997给出了一个更形式化的定义：假设用 P 来评估计算机程序在某任务类 T 上的性能，若一个程序通过利用经验 E 在 T 中任务上获得了性能改善，则我们就说关于 T 和 P，该程序对 E 进行了学习。



## 1.2 基本术语

### 1.2.1 数据相关

* 示例/样本（instance / sample）

  例：（色泽=青绿；根蒂=蜷缩；敲声=浊响）

  一般以 $D={x_1,x_2, \dots , x_m}$ 表示包含 $m$ 个示例的数据集

* 数据集（data set）

  例：（色泽=青绿；根蒂=蜷缩；敲声=浊响），（色泽=乌黑；根蒂=稍蜷；敲声=沉闷），（色泽=浅白；根蒂=硬挺；敲声=清脆），……

* 属性/特征（attribute / feature）
  例：色泽、根蒂、敲声

  一个示例由 $d$ 个特征描述，如示例 $x_i=(x_{i1}；x_{i2}；\dots； x_{id})$ 
  
* 属性值（attribute value）
  例：青绿、乌黑、浅白

  如示例 $x_i=(x_{i1}；x_{i2}；\dots； x_{id})$ ，其中 $x_{id}$ 表示第 $i$ 个示例的第 $d$ 个特征的值
  
* 属性空间/样本空间/输入空间（attribute space / sample space）
  属性张成的空间称为“属性空间”（attribute space）、“样本空间”（sample space）或“输入空间”，例：我们把“色泽”、“根蒂”、“敲声”作为三个坐标轴，则它们张成一个用于描述西瓜的三维空间，每个西瓜都可在这个空间中找到自己的坐标位置。

* 特征向量（feature vector）
  在属性空间中的每个点对应一个坐标向量，因此我们也把一个示例 (instance/sample )称为一个“特征向量”（feature vector）


### 1.2.2 训练相关

* 学习/训练（learning / training）

  从数据中学得模型的过程称为“学习”（learning）或“训练”（training），这个过程通过执行某个学习算法来完成。

* 训练数据（training data）

  训练过程中使用的数据称为“训练数据”（training data）

* 训练样本（training sample）

  训练数据中每个样本称为一个“训练样本”（training sample）

* 训练集（training set）

  训练样本组成的集合称为“训练集”（training set）

* 假设与真相（hypothesis & ground-truth）

  + 假设：学得模型对应了关于数据的某种潜在的规律，因此亦称“假设”（hypothesis）

  + 真相：潜在规律自身，则称为“真相”或“真实”（ground-truth），学习过程就是为了找出或逼近真相
  + 两者区别：假设是我们认为的样本空间的真相，而样本空间的真相是客观存在的，我们认为的真相是否与真相本身相一致，需要后期的验证。

* 标记（label）

  训练样本的“结果”信息，例如“（色泽=青绿；根蒂=螺缩；敲声=浊响)，好瓜）”，这里关于示例结果的信息，例如“好瓜”，称为“标记”（label）

* 样例（example）

  拥有了标记信息的示例，称为“样例”（example）

* 标记空间/输出空间（label space）

  所有标记的集合，称为“标记空间”（label space）或“输出空间”

  

### 1.2.3 测试相关

* 分类（classification）

  若我们欲预测的是离散值，例如“好瓜”、“坏瓜”，此类学习任务称为“分类”（classification）

* 回归（regression）

  若欲预测的是连续值，例如西瓜成熟度0.95、0.37，此类学习任务称为“回归”（regression）

* 测试与测试样本（testing & testing sample）
  * 测试：学得模型后，使用其进行预测的过程称为“测试”（testing）
  * 测试样本：被预测的样本称为“测试样本”（testing sample）

* 簇&聚类（cluster & clustering）

  我们还可以对西瓜做“聚类”（clustering）：将训练集中的西瓜分成若干组，每组称为一个“簇”（cluster）；这些自动形成的簇可能对应一些潜在的概念划分，例如“浅色瓜”、“深色瓜”，甚至“本地瓜”、“外地瓜”。

  

  在聚类学习中，“浅色瓜”、“本地瓜”这样的概念我们事先是不知道的，而且学习过程中使用的训练样本通常不拥有标记信息。

* 监督学习与无监督学习的区别/分类
  + 监督学习（supervised learning）：训练数据有标记信息。如：分类、回归

  + 无监督学习（unsupervised learning）：训练数据无标记信息。如：聚类

    

### 1.2.4  泛化相关

* 泛化能力（generalization）

   学得模型适用于新样本的能力，称为“泛化”（generalization）能力

* 独立同分布（ i.i.d.）

  通常假设样本空间中全体样本服从一个未知“分布”（distribution）D，我们获得的每个样本都是独立地从这个分布上采样获得的，即“独立同分布”（independent and identically distributed，简称 i.i.d.），一般而言，训练样本越多，我们得到的关于 D 的信息越多，这样就越有可能通过学习获得具有强泛化能力的模型。

  > 中心极限定理：若样本的数据量足够大，样本均值近似服从正态分布。
  
  

## 1.3 假设空间

* 假设空间（hypothesis space）

  我们可以把学习过程看作一个在所有假设（hypothesis）组成的空间中进行搜索的过程，搜索目标是找到与训练集“匹配”（fit）的假设，即能够将训练集中的瓜判断正确的假设。

  

  假设的表示一旦确定，假设空间及其规模大小就确定了。

  

  附图
  
  ![img](https://github.com/firewang/lingweilingyu/raw/master/static/img/hypothesis_space.jpeg)

* 版本空间（version space）

  现实问题中我们常面临很大的假设空间，但学习过程是基于有限样本训练集进行的。因此，可能有多个假设与训练集一致，即存在着一个与训练集一致的“假设集合”，我们称之为“版本空间”（version space）。例如在西瓜问题中，与表1.1训练集所对应的版本空间如图1.2所示。

  
  
  附图
  
  ![img](https://github.com/firewang/lingweilingyu/raw/master/static/img/version_space.jpeg)

## 1.4 归纳偏好

* 归纳偏好（inductive bias）

   通过学习得到的模型对应了假设空间中的一个假设。机器学习算法在学习过程中对某种类型假设的偏好，称为“归纳偏好”（inductive bias），或简称为“偏好”。

  任何一个有效的机器学习算法必有其归纳偏好，否则它将被假设空间中看似在训练集上“等效”的假设所迷惑，而无法产生确定的学习结果。

  

* “奥卡姆剃刀”（Occam's razor）原则

  + 归纳偏好可看作学习算法自身在一个可能很庞大的假设空间中对假设进行选择的启发式或“价值观”，“奥卡姆剃刀”可以用来引导算法确立“正确的”偏好。
  + “奥卡姆剃刀”（Occam's razor）原则：若有多个假设与观察一致，则选最简单的那个

* 什么学习算法更好

  归纳偏好对应了学习算法本身所做出的关于“什么样的模型更好”的假设，在具体的现实问题中，这个假设是否成立，即算法的归纳偏好是否与问题本身匹配，大多数时候直接决定了算法能否取得好的性能。
  对于一个学习算法A，若它在某些问题上比学习算法B好，则必然存在另一些问题，在那里B比A好。**这个结论对任何算法均成立**

  + “没有免费的午餐”定理（NFL定理）

    无论学习算法A多聪明，学习算法B多笨拙，它们的期望性能相同。这就是“没有免费的午餐”定理（No Free Lunch Theorem，简称NFL定理）

    NFL定理有一个重要前提：所有“问题”出现的机会相同、或所有问题同等重要，但实际情形并不是这样。例如：“(根蒂=蝶缩;敲声=浊响)”的好瓜很常见，而“(根落二硬摄:敲声二清晚)”的好瓜罕见，甚至不存在。

    NFL定理最重要的寓意：脱离具体问题，空泛地谈论“什么学习算法更好”毫无意义。**要谈论算法的相对优劣，必须要针对具体的学习问题。**学习算法自身的归纳偏好与问题是否相配，往往会起到决定性的作用。

    

## 1.5 发展历程

​	略

##  1.6 应用现状

​	略

## 1.7 阅读材料

​	可以参考 [Roadmap](../Roadmap.md)中的相关资源

## 1.8 第1章习题

​	略

## 小故事：“机器学习”名称的由来

​    1952年，阿瑟·萨缪尔(Arthur Samuel， 1901-1990) 在IBM公司研制了一个西洋跳棋程序，这个程序具有自学习能力，可通过对大量棋局的分析逐渐辨识出当前局面下的“好棋”和“坏棋”，从而不断提高弈棋水平，并很快就赢了萨缪尔自己。 1956年，萨缪尔应约翰·麦卡锡(John McCarthy， “人工智能之父” ， 1971年图灵奖得主)之邀，在标志着人工智能学科诞生的达特茅斯会议上介绍这项工作，萨缪尔发明了“机器学习”这个词，将其定义为“不显式编程地赋予计算机能力的研究领域” 。他的文章"Some studies in machine learning using the game of checkers" 1959年在IBM Journal正式发表后，爱德华·费根鲍姆(Edward Feigenbaum，“知识工程之父” ，1994年图灵奖得主)为编写其巨著Computers and Thought，在1961年邀请萨缪尔提供一个该程序最好的对弈实例，于是，萨缪尔借机向康涅狄格州的跳棋冠军、当时全美排名第四的棋手发起了挑战，结果萨缪尔程序获胜，在当时引起表动。
​    事实上，萨缪尔跳棋程序不仅在人工智能领域产生了重大影响，还影响到整个计算机科学的发展，早期计算机科学研究认为，计算机不可能完成事先没有显式编程好的任务，而萨缪尔跳棋程序否证了这个假设，另外，这个程序是最早在计算机上执行非数值计算任务的程序之一，其逻辑指令设计思想极大地影响了IBM计算机的指令集，并很快被其他计算机的设计者采用。



# 第二章 模型评估与选择

## 2.1 经验误差与过拟合

### 2.1.1 概念解析

(1)  误差：学习器的实际预测输出与样本的真实输出之间的差异；其中学习器在训练集上的误差称为”**训练误差**“（training error）或“**经验误差**” （empirical error），在新样本上的误差称为”**泛化误差**“（generalization error）。值得一提的是，学习器就是在训练集上训练出来的，但实际上在回到训练集上对样本预测结果时，仍有误差。（即结果值与标记值不同）

(2)     错误率：分类错误的样本数占样本总数的比例，$E=\frac{a}{m}$（ $a$ 个样本错误，$m$ 个样本总数）

(3)     精度：与错误率的概念相反，$P=(1-E)\ast 100\%$ 

(4)     过拟合(overfitting)：学习器学习的”太好了“，把训练样本自身的特点当作了所有潜在样本都会有的一般性质。（注意：过拟合会造成泛化性能下降）

(5)     欠拟合(underfitting)：对训练样本的性质尚未学好



![过拟合和欠拟合图示](../static/img/underfitting_overfitting.jpeg)



### 2.1.2 注意事项

（1）泛化误差

我们一直希望得到泛化误差最小的学习器。但是我们实际能做的就是努力使经验误差最小化。注意：努力使经验误差最小化≠让经验误差达到最小值，即训练集的分类错误率为 0%。因为在训练集上表现很好的学习器，泛化能力却并不强。

（2）欠拟合与过拟合

欠拟合比较容易克服，往往因为学习器学习能力过强造成的过拟合较难处理，但是实际上过拟合是机器学习过程中必须面对的障碍。我们必须认识到过拟合我们无法彻底避免，我们只能尽可能”缓解“。从理论上讲，机器面临的问题通常是 NP 难或者更难，而有效的学习算法是在多项式时间内完成的，若可以彻底避免过拟合，则通过经验误差最小化就获得最优解，那么我们构造性的证明了 P=NP，但实际上 P≠NP，也就是说这是不可能完成的。

## 2.2 评估方法（数据集划分方法）

在现实任务中，我们往往有多种学习算法可供选择，甚至对同一个学习算法，当使用不同的参数配置时，也会产生不同的模型，那么，我们该选用哪一个学习算法、使用哪一种参数配置呢? 这就是机器学习中的“模型选择” (model selection)问题，理想的解决方案当然是对候选模型的泛化误差进行评估，然后选择泛化误差最小的那个模型，然而如上面所讨论的，我们无法直接获得泛化误差而训练误差又由于过拟合现象的存在而不适合作为标准。

因此，通常，我们需要通过实验测试来对学习器的泛化误差进行评估从而做出选择。此时，我们需要一个“测试集”来测试学习器对新样本的判别能力，然后以测试集上的“测试误差”作为泛化误差的近似。（假设测试样本独立同分布）我们知道一个 $m$ 个样例的数据集 $D={(x_1,y_1),(x_2,y_2),\dots,(x_m,y_m)}$ ,我们要对这个数据集既要训练又要测试，那么如何产生训练集 $S$ 和测试集 $T$ 是我们要面对的问题。

![数据集划分](../static/img/grid_search_workflow.png)



### 2.2.1 留出法 LOO
留出法 Leave-one-out：直接将数据集 $D$ 划分为两个互斥的集合，其中一个集合作为训练集 $S$ ，另一个作为测试集 $T$，即 $D=S\cup T$，$S\cap T= \emptyset$。

![留出法（非分层采样）](../static/img/leave_one_out.png)

如上图所示，两个同心圆。其中内圆红色部分为训练集，外环绿色部分为测试集，两部分是两个互斥的集合。

除此之外，留出法还要尽可能的保持数据分布的一致性，要保持样本类别比例相似，从采样的角度看待数据采集的划分过程，保留类别比例的采样方式通常称为“分层采样”。

就好比它真是一个西瓜，按甜度将其分为七块，采样时每一块都要按照相同的所占比例去采。这七类数据集的测试集与训练集的比值应是相等的。

![留出法（分层采样）](../static/img/leave_one_out(stratified).png)

注意：单次使用留出法所得到的估计结果往往不稳定可靠，在使用留出法时，一般采用若干次随机划分、重复实验取平均值。

留出法的特点：
1. 直接划分训练集与测试集；
2. 训练集和测试集采取分层采样；
3. 随机划分若干次，重复试验取平均值

### 2.2.2 交叉验证 CV
交叉验证法 cross-validation：先将数据集 $D$ 分为 $k$ 个大小相似的互斥子集，即 $D=D_1\cup D_2\cup \dots \cup D_k ；D_i \cap D_j = \emptyset（i \neq j）$。每个子集 $D_i$ 都尽可能保持数据分布的一致性，即每个子集仍然要进行分层采样。每次用 $k-1$ 个子集作为训练集，余下作测试集，这样可以获得 $k$ 组“训练/测试集”，最终返回的是 $k$ 个结果的均值。

![交叉验证示意图](../static/img/cross_validation_example.png)

与留出法类似，将数据集 $D$ 划分为 $K$ 个子集同样存在多种划分方式。为减少因样本划分不同而引入的差别，$k$ 折交叉验证通常也要重复 $p$ 次实验，最后取均值。

**交叉验证的特例：**

留一法（LOO）：$m$ 个样本划分成 $m$ 个子集，每个子集包含一个样本。留一法中被实际评估的模型与期望评估的用 $D$ 训练出来的模型很相似，因此，留一法的评估结果往往被认为比较准确。

留一法缺陷：当数据集过大时，计算开销、时间开销、空间开销都是难以忍受的（还未考虑算法调参）。

### 2.2.3 自助法 bootstrapping	
留出法与交叉验证法都会使训练集比 $D$ 小，这必然会引入一些因样本规模不同而导致的估计偏差。那么如何做到较少训练样本规模不同造成的影响，同时还高效地进行实验估计呢？

自助法 bootstrapping：对有 $m$ 个样本的数据集 $D$，按如下方式采样产生数据集 $D^\prime$：每次随机取一个样本拷贝进$D^\prime$，取 $m$ 次（有放回取 $m$ 次）。

按此方法，保证了 $D^\prime$ 和 $D$ 的规模一致。但 $D^\prime$ 虽然也有 $m$ 个样本，其中会出现重复的样本，$D$中会存在  $D^\prime$ 没有采到的样本，这些样本就留作测试集。

计算某样本在 $m$ 次采样中均不会被采到的概率是： $(1-\frac{1}{m})^m$ ，取极限可得
$$
\lim_{m\to \infty}(1-\frac{1}{m})^m \to \frac{1}{e} \approx 0.368
$$
由此可知，理论上有36.8%的样本没有出现在在$D^\prime$ 之中，我们把 $D \setminus D^\prime$ 作为测试集。

优点：训练集与数据集规模一致；数据集小、难以有效划分训练/测试集时效果显著；能产生多个不同的训练集；

缺点：改变了训练集的样本分布，引入估计偏差。

### 2.2.4 调参与最终模型

大多数学习算法都有些参数 (parameter) 需要设定，参数配置不同，学得模型的性能往往有显著差别，因此，在进行模型评估与选择时，除了要对适用学习算法进行选择，还需对算法参数进行设定，这就是通常所说的“参数调节”或简称“调参” (parameter tuning)。

因为学习算法的参数可能是在实数域，因此对每种参数配置都训练相应的模型成为了不可行方案，通常我们对每个参数选定一个**范围**和**变化步长**，显然，这样选定的参数值往往不是“最佳”值，但这是在计算开销和性能估计之间进行折中的结果，通过这个折中，学习过程才变得可行，

给定包含 $m$ 个样本的数据集 $D$，在模型评估与选择过程中由于需要留出一部分数据进行评估测试，事实上我们只使用了一部分数据训练模型，因此，在模型选择完成后，学习算法和参数配置已选定，此时应该用数据集 $D$ **重新训练模型**，这个模型在训练过程中使用了所有 $m$ 个样本，这才是我们最终提交给用户的模型。	

另外，需注意的是，我们通常把学得模型在实际使用中遇到的数据称为测试数据，为了加以区分，模型评估与选择中用于评估测试的数据集常称为“验证集” (validation set)。例如，在研究对比不同算法的泛化性能时，我们用测试集上的判别效果来估计模型在实际使用时的泛化能力，而把训练数据另外划分为训练集和验证集，基于验证集上的性能来进行模型选择和调参。

（1）概念详解
+ 调参 parameter tunning：对模型进行评估和选择时，对算法参数 parameter 进行标定。
+ 验证集 validation set：模型评估与选择中用于评估测试的数据集。

（2）参数的分类
- 算法的参数：亦称超参数，数目在十以内
- 模型的参数：数目众多。



## 2.3 性能度量

对学习器的泛化性能进行评估，不仅需要有效可行的实验估计方法，还需要**衡量模型泛化能力的评价标准**，即性能度量 performance measure。不同的性能度量，模型的好坏也不同，故模型的好坏是相对的。它取决于三个方面：

- 算法（算法类型+ 参数）
- 数据情况
- 任务需求
  - 原型设计阶段：离线评估 Offline evaluation
  - 应用阶段：在线评估 Online evaluation , 一般使用商业评价指标



>通常机器学习过程包括两个阶段,原型设计阶段和应用阶段

>原型设计阶段是使用历史数据训练一个适合解决目标任务的一个或多个机器学习模型，并对模型进行验证( Validation )与离线评估( Offline evaluation )，然后通过评估指标选择一个较好的模型。比如准确率( accuracy )、精确率-召回率( precision-recall)等

>应用阶段是当模型达到设定的指标值时便将模型上线,投入生产,使用新生成的数据来对该模型进行在线评估( Online evaluation ),以及使用新数据更新模型。在线评估中，一般使用一些商业评价指标,如用户生命周期价值( Customer Lifetime Value, CLV )、广告点击率(ClickThrough Rate, CTR)、用户流失率( Customer Churn Rate, CCR)等,这些指标才是模型使用者最终关心的一些指标。



预测任务中，给定样例数据集 $D={(x_1,y_1),(x_2,y_2),\dots,(x_m,y_m)}$ ，其中  $y_i$ 是示例 $x_i$ 的真实标记。 评估学习器 $f$ 的性能，需要将学习器的预测结果 $f(x)$ 同真实标记 $y$  进行比较。



本节内容，原书都以分类任务的常用性能度量为例。



### 2.3.1 错误率与精度

错误率 error rate：
$$
E(f ; D)=\frac{1}{m} \sum_{i=1}^{m} \mathbb{I}\left(f\left(\boldsymbol{x}_{i}\right) \neq y_{i}\right)
$$
其中 $\mathbb{I}(f(x_i)\neq y_i)$ 为指示函数 indicator function ，若表达式为真则取值为1，否则取值0

精度 accuracy：
$$
\begin{aligned} \operatorname{acc}(f ; D) &=\frac{1}{m} \sum_{i=1}^{m} \mathbb{I}\left(f\left(\boldsymbol{x}_{i}\right)=y_{i}\right) \\ &=1-E(f ; D) \end{aligned}
$$


更一般的，对于数据分布 $\mathcal{D}$ 和概率密度函数 $\mathcal{p}(\cdot)$ ，错误率和精度可分别描述为

[comment]: 后续需要补充说明

$$
E(f ; \mathcal{D})=\int_{\boldsymbol{x} \sim \mathcal{D}} \mathbb{I}(f(\boldsymbol{x}) \neq y) p(\boldsymbol{x}) \mathrm{d} \boldsymbol{x} \tag{2.6}
$$

$$
\begin{aligned} \operatorname{acc}(f ; \mathcal{D}) &=\int_{\boldsymbol{x} \sim \mathcal{D}} \mathbb{I}(f(\boldsymbol{x})=y) p(\boldsymbol{x}) \mathrm{d} \boldsymbol{x} \\ &=1-E(f ; \mathcal{D}) \end{aligned} \tag{2.7}
$$



### 2.3.2 查准率、查全率与F1（混淆矩阵）

当需要反映的不是判断正确与否的能力，而是正例、反例查出的准确率时，就不能用错误率和精度作为判断分类任务模型的性能度量了，查准率（准确率） precision 和查全率（召回率） recall 应运而生。（因为各个翻译版本的不同，下文都以英文表示）

为了说明 precision 和 recall，我们引入混淆矩阵 confusion matrix。可以说，confusion matrix 很直观地表示了各个指标的定义、来源以及作用意义。

以 [维基百科](https://en.wikipedia.org/wiki/Confusion_matrix) 给出的表格释义最为直观与全面

![confusion_matrix](../static/img/confusion_matrix.png)

其中，True condition 表示数据集中各数据样本的真实标记值，一般即为 $y$ ，Predicted condition 表示学习算法给出的预测值。

> True positive (TP)：真正例，即真实值为1，预测为1

> False positive (FP)：假正例，即真实值为0，预测为1

> False negtive (FN)：假反例，即真实值为1，预测为0

> True negtive (TN):  真反例，即真实值为0，预测为0

有了confusion matrix ，我们就可以很直观地知道其他指标的定义了

> precision(Positive predictive value,PPV) ：预测为正例的样本中真正例的比例
> $$
> \text{Precision} = \frac{\sum \text { True positive }}{\sum \text { Predicted condition positive }}=\frac{\text{真正例=TP}}{\text{预测为正例=TP+FP}}
> $$

> Recall(True positive rate, TPR, Sensitivity) ：真实值为正例中被预测为正例的比例
> $$
> \text{Recall}=\frac{\sum \text { True positive }}{\sum \text { Condition positive }} = \frac{\text {真正例=TP}}{\text {真实值为正例=TP+FN}}
> $$
> 



可以发现，**precision 反映准确性，recall 反映全面性，**他们是一对矛盾的存在。为了找到 P、R之间的平衡点，我们将以 precision 为纵轴，recall 为横轴，建立直角坐标系，就得到”P-R“图

![P-R图](../static/img/P_R.jpeg)

根据 P-R 曲线，我们就可以去评价学习器性能的优劣

* 当曲线没有交叉的时候：外侧曲线的学习器性能优于内侧；
* 当曲线有交叉的时候（此时无法根据 P-R 图得到哪个学习器更优，需要在具体情境下比较）：
  * 比较曲线下面积（值不容易计算）
  * 比较两条曲线的平衡点 Break-Even Point (BEP)，平衡点是“precision=recall”时的取值，在上图中表示为曲线和对角线的交点，平衡点在外侧的曲线的学习器性能优于内侧
  * $F1$ 度量和 $F_{\beta}$度量。$F1$ 是基于查准率与查全率的调和平均 harmonic mean ，$F_{\beta}$ 则是加权调和平均



> $$
> \frac{1}{F 1}=\frac{1}{2} \cdot\left(\frac{1}{P}+\frac{1}{R}\right) \Rightarrow F1=\frac{2\times P \times R}{P+R} = \frac{2\times TP}{\text{样例总数}+TP-TN}
> $$

> $$
> \frac{1}{F_{\beta}}=\frac{1}{1+\beta^{2}} \cdot\left(\frac{1}{P}+\frac{\beta^{2}}{R}\right) \Rightarrow F_{\beta} = \frac{(1+\beta ^{2})\times P \times R}{(\beta ^{2}\times P)+ R}
> $$

其中， $\beta \gt 0$ 度量了recall 对 precision 的相对重要性，$\beta = 1$ 时 $F_{\beta}$ 退化为标准 $F1$ ， $\beta \gt 1$ 时 recall 有更大影响，反之，precision 有更大影响。



对于我们有多个二分类混淆矩阵的情况，例如进行多次训练/测试，每次得到一个混淆矩阵；或是在多个数据集上进行训练/测试，希望估计学习算法的“全局”性能；甚或是执行多分类任务，每两两类别的组合都对应一个混淆矩阵……总之，我们希望在n个二分类混淆矩阵上综合考察查准率 precision 和查全率recall，于是就有了宏查准率 （macro-P）、 宏查全率（macro-R）、宏F1（macro-F1）以及微查准率 （micro-P）、 微查全率（micro-R）、微F1（micro-F1）



宏 macro ：在 n 个混淆矩阵中分别计算出 precision、recall，再计算均值，就得到“宏查准率, macro-P”、“宏查全率, macro-R ”和“宏F1, macro-F1”

> $$
> macro\mathbb{-}P=\frac{1}{n} \sum_{i=1}^{n} P_{i} \quad macro\mathbb{-}R=\frac{1}{n} \sum_{i=1}^{n} R_{i} \quad macro\mathbb{-}F1=\frac{2\times macro\mathbb{-}P \times macro\mathbb{-}R}{macro\mathbb{-} P + macro\mathbb{-} R}
> $$



微 micro ：先将n个混淆矩阵的对应元素 $TP,  FP, TN, FN$ 进行平均得到 $\overline{TP}, \overline{FP}, \overline{TN}, \overline{FN}$，再计算precison, recall 和 F1，就得到“微查准率，micro-P”、“微查全率，micro-R”和 “微F1，micro-F1”。
$$
micro\mathbb{-}P=\frac{\overline{TP}}{\overline{TP}+\overline{FP}} \quad micro\mathbb{-}R=\frac{\overline{TP}}{\overline{TP}+\overline{FN}} \quad micro\mathbb{-}F1=\frac{2\times micro\mathbb{-}P \times micro\mathbb{-}R}{micro\mathbb{-} P + micro\mathbb{-} R}
$$



[comment]:   macro-F1和micro-F1应用场景的区别？



### 2.3.3 ROC与AUC

很多学习器是为测试样本产生一个实值或概率预测，然后将这个预测值与一个分类阈值(threshold)进行比较，若大于阔值则分为正类，否则为反类。例如，神经网络在一般情形下是对每个测试样本预测出一个[0.0，1.0]之间的实值，然后将这个值与 0.5 进行比较，大于 0.5 则判为正例，否则为反例，这个实值或概率预测结果的好坏，直接决定了学习器的泛化能力，实际上，根据这个实值或概率预测结果，我们可将测试样本进行排序， “最可能”是正例的排在最前面，“最不可能”是正例的排在最后面，这样，分类过程就相当于在这个排序中以某个“截断点” (cut point)将样本分为两部分，前一部分判作正例，后一部分则判作反例

在不同的应用任务中，我们可根据任务需求来采用不同的截断点，例如若我们更重视precision，则可选择排序中靠前的位置进行截断；若更重视 recall，则可选择靠后的位置进行截断，因此，**排序本身的质量好坏**，体现了综合考虑学习器在不同任务下的**期望泛化性能**的好坏，或者说， “一般情况下”泛化性能的好坏。 ROC曲线（Receiver Operating Characteristic curve）则是从这个角度出发来研究学习器泛化性能的有力工具。

ROC 名为”受试者工作特征“曲线，源于二战中用于敌机检测的雷达信号分析技术。与之前的P-R曲线相似，需要对样例进行排序，然后按顺序逐个将样本作为正例进行预测。ROC曲线以真正例率（TPR，即Recall）为纵轴，假正例率（FPR）为横轴，ROC曲线下的面积为AUC（Area Under ROC Curve）

> $$
> TPR = Recall = \frac{\sum \text{True positive}}{\sum \text{Condition positive}}=\frac{TP}{TP+FN}
> $$

真正例率（TPR）：【真正例样本数】与【真实情况是正例的样本数】的比值。反映预测正类中实际正类越多

> $$
> FPR = \frac{\sum \text{False positive}}{\sum \text{Condition negtive}}=\frac{FP}{FP+TN}
> $$

假正例率（FPR）：【假正例样本数】与【真实情况是反例的样本数】的比值。反映预测正类中实际负类越多



![ROC-AUC](../static/img/ROC_AUC.jpeg)

如图，理想模型是真正例率为100%，假正例率为 0% 的一点（左上角）。随机猜测模型则是真正例率与假正例率持平的直线。对角线对应于“随机猜测”模型,而点(0, 1)则对应于将所有正例排在所有反例之前的“理想模型”。



然而，现实任务中通常是利用**有限个**测试样例来绘制 ROC 图，此时仅能获得有限个(真正例率，假正例率)坐标对，ROC曲线绘图过程很简单：给定m+ (即 Condition positive)个正例和 m- (即Condition negtive)个反例，根据学习器预测结果对样例进行排序，然后把分类阈值设为最大，即把所有样例均预测为反例，此时真正例率和假正例率均为0，在坐标 (0,0) 处标记一个点，然后，将分类阈值依次设为每个样例的预测值（从大到小）,即依次将每个样例划分为正例，设前一个标记点坐标为 $(x,y)$ 当前若为真正例，则对应标记点的坐标为 $(x, y+\frac{1}{m+} )$ 当前若为假正例，则对应标记点的坐标为$(x+\frac{1}{m-}, y)$ 然后用线段连接相邻点即得。



**利用ROC曲线比较学习器的性能优劣**

* 若一个学习器的ROC曲线被另一个学习器的曲线完全“包住” ，则可断言后者的性能优于前者
* 若两个学习器的ROC曲线发生交叉，则难以一般性地断言两者孰优孰劣，此时如果一定要进行比较，则较为合理的判据是比较ROC曲线下的面积，即AUC

从定义可知，AUC可通过对ROC曲线下各部分的面积求和而得，假定ROC曲线是由坐标为${(x_1,y_1), (x_2, y_2),\dots, (x_m,y_m)}$ 的点按序连接而形成 $(x_1=0, x_m=1)$ ，则AUC可估算为
$$
AUC=\frac{1}{2} \sum_{i=1}^{m-1}\left(x_{i+1}-x_{i}\right) \cdot\left(y_{i}+y_{i+1}\right)
$$
这里的估算方式实际上是使用了梯形公式（$(\text{上底+下底})\times \text{高} \times \frac{1}{2}$），其中 $x_{i+1}-x_i$ 为高，$y_i, y_{i+1}$ 分别为上底和下底，更详细的解析可以参考[南瓜书](https://datawhalechina.github.io/pumpkin-book/#/chapter2/chapter2)



AUC 指标用来评估分类器性能，可以兼顾**样本中类别不平衡**的情况（当测试集中的正负样本的分布变化的时候，ROC曲线能够保持不变），这一点上要比分类准确率更加具有参考价值。



**AUC的一般判断标准**
* 0.5 - 0.7：效果较低
* 0.7 - 0.85：效果一般
* 0.85 - 0.95：效果很好
* 0.95 - 1：效果非常好，但一般不太可能



整体而言，混淆矩阵给我们呈现了一个清晰可见的分类模型效果评估工具，而基于混淆矩阵的评估指标可以从不同侧面来评价分类器性性能，至于在实际操作中使用什么样的评估指标来进行评价，还要视具体的分析目标而定。



可参考的说明网站 [网站1](http://alexkong.net/2013/06/introduction-to-auc-and-roc/) , [网站2](https://www.cnblogs.com/dlml/p/4403482.html)

### 2.3.4 代价敏感错误率与代价曲线

从混淆矩阵中我们可以看到，存在两种错判的情况（FP 为 1型错误，FN为 2型错误），在前面介绍的性能度量标准下，它们都隐式地假设了均等代价（两种错判情况造成影响相等），然而，两种错误类型会造成的后果（错误代价）是不一致的。

例如在医疗诊断中，错误地把患者诊断为健康人与错误地把健康人诊断为患者，看起来都是犯了“一次错误” ，但后者的影响是增加了进一步检查的麻烦，前者的后果却可能是丧失了拯救生命的最佳时机；再如，门禁系统错误地把可通行人员拦在门外，将使得用户体验不佳，但错误地把陌生人放进门内，则会造成严重的安全事故。

为权衡不同类型错误所造成的不同损失，为错误赋予“非均等代价”（unequal cost）。在非均等代价下，目标不再是简单地最小化错误次数，而是最小化总体代价 total cost 。



实现方式是，可根据任务的领域知识设定代价矩阵 cost matrix

![代价矩阵cost matrix](../static/img/cost_matrix.png)

其中 $cost_{ij}$ 表示将第 $i$ 类样本预测为第 $j$ 类样本的代价。一般来说, $cost_{01}$ 就对应于第一类错误，$cost_{10}$ 就对应于第二类错误。如上图所示，第1类作为正类、第0类作为反类，令 $D+$ 与 $D-$ 分别代表样例集 $D$ 的正例子集和反例子集，则“代价敏感” (cost-sensitive)错误率为
$$
\begin{aligned} 
E(f ; D ; cost)=& \frac{1}{m}\left(\sum_{x_{i} \in D^{+}} \mathbb{I}\left(f\left(\boldsymbol{x}_{i}\right) \neq y_{i}\right) \times cos t_{01}\right.\\ &+\sum_{\boldsymbol{x}_{i} \in D^{-}} \mathbb{I}\left(f\left(\boldsymbol{x}_{i}\right) \neq y_{i}\right) \times cost_{10} ) \end{aligned}
$$


类似的，可给出基于分布定义的代价敏感错误率，以及其他一些性能度量如精度（precision）的代价敏感版本，若令 $cost_{ij}$ 中的 $i,  j$ 取值不限于0、1,则可定义出多分类任务的代价敏感性能度量。

在非均等代价下, ROC曲线不能直接反映出学习器的期望总体代价，而“代价曲线” (cost curve)则可达到该目的，代价曲线图的横轴是取值为 [0,1] 的正例概率代价， 纵轴是取值为 [0,1] 的归一化代价
$$
P(+)\text{cost}=\frac{p \times \text{cost}_{01}}{p \times \text{cost}_{01}+(1-p) \times \text{cost}_{10}}
$$

$$
\text{cost}_\text{norm}=\frac{FNR \times p \times \text{cost}_{01}+FPR \times(1-p) \times \text{cost}_{10}}{p \times \text{cost}_{01}+(1-p) \times \text{cost}_{10}}
$$

其中 FPR 是假正例率，FNR=1-TPR是假反例率，代价曲线的绘制很简单: ROC曲线上每一点对应了代价平面上的一条线段，设ROC曲线上点的坐标为(TPR, FPR)，则可相应计算出 FNR ，然后在代价平面上绘制一条从 (0, FPR) 到(1, FNR) 的线段，线段下的面积即表示了该条件下的期望总体代价；如此将ROC曲线上的每个点转化为代价平面上的一条线段，然后**取所有线段的下界**，围成的面积即为在所有条件下学习器的期望总体代价

![代价曲线cost_curve](../static/img/cost_curve.png)



### 2.3.5 sklearn中的分类算法性能度量实现

[comment]:  <后续补充>



## 2.4 比较检验

有了实验评估方法和性能度量，看起来就能对学习器的性能进行评估比较了：先使用某种实验评估方法测得学习器的某个性能度量结果，然后对这些结果进行比较，但怎么来做这个“比较”呢？是直接取得性能度量的值然后“比大小”吗？

实际上，机器学习中性能比较这件事要复杂得多。这里面涉及几个重要因素：

- 我们希望比较的是泛化性能，然而通过实验评估方法我们获得的是测试集上的性能，两者的对比结果可能未必相同；
- 测试集上的性能与测试集本身的选择有很大关系，且不论使用不同大小的测试集会得到不同的结果，即便用相同大小的测试集，若包含的测试样例不同，测试结果也会有不同；
- 很多机器学习算法本身有一定的随机性，即便用相同的参数设置在同一个测试集上多次运行，其结果也会有不同

统计假设检验(hypothesis test)为我们进行学习器性能比较提供了重要依据，基于假设检验结果我们可推断出，若在测试集上观察到学习器 A 比 B 好，则A的泛化性能是否在统计意义上优于B，以及这个结论的把握有多大。



[comment]: 后续再补充



## 2.5 偏差与方差

[comment ]: <后续补充>



# **第三章 线性模型**

## 3.1 基本形式

给定由 $d$ 个属性描述的示例 $x=(x_1;x_2;x_3\dots ;x_d)$，其中 $x_i$ 是 $x$ 的第 $i$ 个属性上的取值，线性模型试图学得一个通过属性的线性组合来进行预测函数，即 
$$
f(x) = w_1x_1+w_2x_2+\dots w_dx_d + b \tag{3.1}
$$
一般用向量形式
$$
f(x)=w^{T}x+b \tag{3.2}
$$
其中 $w=(w_1;w_2;\dots ;w_d)$  。 $w$ 和 $b$ 学得之后，模型就得以确定。

线性模型形式简单、易于建模，但却蕴涵着机器学习中一些重要的基本思想，许多功能更为强大的非线性模型(nonlinear model)可在线性模型的基础上通过引入**层级结构**或**高维映射**而得，此外，由于 $w$ 直观表达了各属性在预测中的重要性，因此线性模型有很好的可解释性(comprehensibility) / 可理解性 (understandability) 。

例：西瓜问题中学的 $“f_{\text{好瓜}}（x）= 0.2*x{\text{色泽}}+0.5*x_{\text{根蒂}}+0.3*x_{\text{敲声}}+1”$，则意味着可通过综合考虑色泽、根蒂和敲声来判断瓜好不好，其中根蒂最要紧，而敲声比色泽更重要。



## 3.2 线性回归

​	给定数据集 $D=\{(x_1,y_1),(x_2,y_2),\dots,(x_m,y_m)\}$ ，其中 $x_i = (x_{i 1};x_{i 2};\dots x_{i d}), y \in \mathbb{R}$ 。“线性回归”(linear regression)试图学得一个线性模型以尽可能准确地预测实值输出标记。

例如：通过历年的人口数据预测2020年人口数量。在这类问题中，往往我们会先得到一系列的有标记数据，例如：2000--13亿...2018--15亿，这时输入的属性只有一个，即年份；也有输入多属性的情形，假设我们预测一个人的收入，这时输入的属性值就不止一个了，例如：（学历，年龄，性别，颜值，身高，体重）-- 15 k。

有时这些输入的属性值并不能直接被我们的学习模型所用，需要进行相应的处理，对于连续数值型的特征，一般都可以被学习器所用，有时会根据具体的情形作相应的预处理，例如：归一化等；对于离散型的特征，针对其属性值间的特点，有不同的处理方式：

- 若属性值之间存在“序关系” （order），则可以将其转化为连续值，例如：身高属性分为{高，中等，矮}，可转化为数值：{1, 0.5, 0}。
- 若属性值之间不存在“序关系”，则通常将其转化为向量的形式，例如：瓜类的取值{西瓜，南瓜，黄瓜}，可转化为向量：{(1, 0, 0)，(0, 1, 0)，(0, 0, 1)}。

### 3.2.1 一元（简单）线性回归

（1）当输入特征只有一个的时候，就是最简单的情形。

线性回归试图学得
$$
f\left(x_{i}\right)=w x_{i}+b \approx y_i \tag{3.3}
$$

> $f(x_i) + \epsilon = y_i$  ，其中 $\epsilon$ 是误差项的随机变量，反映了自变量之外的随机因素对因变量的影响，它是不同由自变量 $x$ 和 因变量 $y$ 的线性关系所解释的变异性。

如何确定 $w, b$ ？通过计算出每个样本预测值与真实值之间的误差平方并求和，通过最小化均方误差 (mean-square error，MSE) / 平方损失 (square loss) 即可。均方误差有非常好的几何意义，它对应了常用的欧几里得距离或简称“欧氏距离” (Euclidean distance)。基于均方误差最小化来进行模型求解的方法称为“最小二乘法” (least square method)。在线性回归中，最小二乘法就是试图找到一条直线，使所有样本到直线上的欧氏距离之和最小。
$$
\begin{aligned}\left(w^{*}, b^{*}\right) &=\underset{(w, b)}{\arg \min } \sum_{i=1}^{m}\left(f\left(x_{i}\right)-y_{i}\right)^{2} \\ &=\underset{(w, b)}{\arg \min } \sum_{i=1}^{m}\left(y_{i}-w x_{i}-b\right)^{2} \end{aligned} \tag{3.4}
$$
其中，$\omega ^{*}, b^{*}$ 表示  $\omega, b$ 的解 ； $\arg$ 是变元(即自变量argument) ，$\arg \min$ 就是使函数值达到最小值时的变量的取值 $\arg \max$ 就是使函数值达到最大值时的变量的取值。 

求解 $\omega$ 和 $b$ 使  $E_{(w, b)}=\sum_{i=1}^{m}\left(y_{i}-w x_{i}-b\right)^{2}$ 最小化的过程，称为线性回归模型的最小二乘“参数估计” (parameter estimation)。这里 $E_{(w, b)}$ 是关于 $\omega$ 和 $b$ 的凸函数， 因此可以通过求导的方式得到最优解的闭式（closed-form）解

> 凸函数定义： 对区间 $[a,b]$ 上定义的函数 $f$ ，若它对区间中任意两点 $x_1,x_2$ 均有 $f\left(\frac{x_{1}+x_{2}}{2}\right) \leqslant \frac{f\left(x_{1}\right)+f\left(x_{2}\right)}{2}$ ，则称 $f$ 为区间 $[a,b]$ 上的凸函数。 $U$ 型曲线的函数如 $f(x)=x^2$ 通常是凸函数。

$$
\frac{\partial E_{(w, b)}}{\partial w}=2\left(w \sum_{i=1}^{m} x_{i}^{2}-\sum_{i=1}^{m}\left(y_{i}-b\right) x_{i}\right) \tag{3.5}
$$

$$
\frac{\partial E_{(w, b)}}{\partial b}=2\left(\sum_{i=1}^{m}b-\sum_{i=1}^{m}\left(y_{i}-w x_{i}\right)\right)=2\left(m b-\sum_{i=1}^{m}\left(y_{i}-w x_{i}\right)\right) \tag{3.6}
$$

令导数为 0 即可，这里先求解 3.6 式，因为其形式上更简单
$$
\frac{\partial E_{(w, b)}}{\partial b}=2\left(m b-\sum_{i=1}^{m}\left(y_{i}-w x_{i}\right)\right)=0 \Rightarrow b=\frac{1}{m}\sum_{i=1}^{m}\left(y_{i}-w x_{i}\right)\tag{3.8}
$$
继续化简 3.8 式，$ \cfrac{1}{m}\sum_{i=1}^{m}y_i=\bar{y} $，$ \cfrac{1}{m}\sum_{i=1}^{m}x_i=\bar{x} $，实际上就是均值，则 
$$
b=\bar{y}-w\bar{x} \tag{3.8.1}
$$
继续求解 3.5 式，
$$
\begin{array}{cl}
\frac{\partial E_{(w, b)}}{\partial w}=2\left(w \sum_{i=1}^{m} x_{i}^{2}-\sum_{i=1}^{m}\left(y_{i}-b\right) x_{i}\right)=0 
&\Rightarrow \omega \sum_{i=1}^{m} x_{i}^{2} = \sum_{i=1}^{m}\left(y_{i}-b\right) x_i
\\
& \Downarrow
\\
\omega \sum_{i=1}^{m} x_{i}^{2} = \sum_{i=1}^{m}\left(y_{i}-(\bar{y}-w\bar{x})\right) x_i &= \sum_{i=1}^{m}(y_{i}x_i) - \sum_{i=1}^{m}(\bar{y}x_i)+\sum_{i=1}^{m}w\bar{x}x_i
\\
& \Downarrow
\\
\omega (\sum_{i=1}^{m} x_{i}^{2} -\bar{x}\sum_{i=1}^{m}x_i) 
&= \sum_{i=1}^{m}(y_{i}x_i) - \sum_{i=1}^{m}(\bar{y}x_i)
\end{array}
$$
因为 $\sum_{i=1}^{m}(\bar{y}x_i) = \frac{1}{m}\sum_{i=1}^{m}(y_i x_i)=\sum_{i=1}^{m}(\bar{x}y_i)$ ,  $\bar{x} \sum_{i=1}^{m} x_{i}=\frac{1}{m} \sum_{i=1}^{m} x_{i} \sum_{i=1}^{m} x_{i}=\frac{1}{m}\left(\sum_{i=1}^{m} x_{i}\right)^{2}$

由此即可得到
$$
\begin{array}{cl}
\omega (\sum_{i=1}^{m} x_{i}^{2} -\bar{x}\sum_{i=1}^{m}x_i) 
= \sum_{i=1}^{m}(y_{i}x_i) - \sum_{i=1}^{m}(\bar{y}x_i)
\\
\Downarrow
\\
\omega =\frac{\sum_{i=1}^{m} y_{i}\left(x_{i}-\bar{x}\right)}
{\sum_{i=1}^{m} x_{i}^{2}-\frac{1}{m}\left(\sum_{i=1}^{m} x_{i}\right)^{2}}
\end{array}  \tag{3.7}
$$

### 3.2.2 多元线性回归

multivariate linear regression

（2）当输入特征有多个的时候，例如对于一个样本有 $d$ 个属性 $\{(x_{i1}；x_{i2}；\dots； x_{id}),y\}$，则可写成：
$$
f(\vec{x}_i) = w_1 x_{i 1}+w_2 x_{i 2}+ \dots +w_d x_{i d}+b = \vec{w}^{T}\vec{x}_i+b\approx y_i
$$
和一元的情况类似，依然使用最小二乘法来对 $\omega$ 和 $b$ 进行估计，但是对于多元问题，我们使用矩阵的形式来表示数据。为便于讨论，我们把  $\omega$ 和 $b$  吸收入向量形式  $\hat{\omega}=(\omega;b)$ ，相应的，把数据集 $D$ 表示为一个 $m\times (d+1)$ 大小的矩阵 $\mathbf{X}$ ，其中每行对应于一个示例，该行前 $d$ 个元素对应于示例的 $d$ 个属性值，最后一个元素置为1，即
$$
\hat{\omega}_{(d+1)\times 1} =(\omega;b) = \left(\begin{array}{c}{\omega_{1}} \\ {\omega_{2}} \\ {\vdots} \\ {\omega_{d}} \\ {b}\end{array}\right)
$$

$$
\mathbf{X}=\left(\begin{array}{ccccc}{x_{11}} & {x_{12}} & {\dots} & {x_{1 d}} & {1} \\ {x_{21}} & {x_{22}} & {\dots} & {x_{2 d}} & {1} \\ {\vdots} & {\vdots} & {\ddots} & {\vdots} & {\vdots} \\ {x_{m 1}} & {x_{m 2}} & {\dots} & {x_{m d}} & {1}\end{array}\right)=\left(\begin{array}{cc}{x_{1}^{T}} & {1} \\ {x_{2}^{T}} & {1} \\ {\vdots} & {\vdots} \\ {x_{m}^{T}} & {1}\end{array}\right)
$$

于是，矩阵形式的线性回归可以表示为
$$
X * \hat{\omega}
=\left(\begin{array}{ccccc}
{x_{11}} & {x_{12}} & {\dots} & {x_{1 d}} & {1} 
\\ 
{x_{21}} & {x_{22}} & {\dots} & {x_{2 d}} & {1} 
\\ 
{\vdots} & {\vdots} & {\ddots} & {\vdots} & {\vdots} 
\\ 
{x_{m 1}} & {x_{m 2}} & {\dots} & {x_{m d}} & {1}
\end{array}\right) 
*
\left(\begin{array}{c}{\omega_{1}} \\ {\omega_{2}} \\ {\vdots} \\ {\omega_{d}} \\ {b}\end{array}\right)
=
\left(\begin{array}{c}
{\omega_{1} x_{11}+\omega_{2} x_{12}+\ldots \omega_{d} x_{1 d}+b} \\ 
{\omega_{1} x_{21}+\omega_{2} x_{22}+\ldots \omega_{d} x_{2 d}+b} \\ 
{\vdots} \\
{\omega_{1} x_{m1}+\omega_{2} x_{m2}+\ldots \omega_{d} x_{m d}+b} \\ 
\end{array}\right)
=\left(\begin{array}{c}
{f\left(\mathrm{x}_{1}\right)} \\ 
{f\left(\mathrm{x}_{2}\right)} \\ 
{\vdots} \\ 
{f\left(\mathrm{x}_{m}\right)}
\end{array}\right)
$$
同时将因变量也写成向量形式 $\boldsymbol{y}=(y_1;y_2;\dots ;y_m)$ ，则可以将式 3.4 推广为
$$
\begin{array}{cl}
\hat{\omega}^{*} 
&= \underset{\hat{w}^{*}}{\arg \min } (f(x)-\boldsymbol{y})^2  \\
&= \underset{\hat{w}^{*}}{\arg \min } (\boldsymbol{y}-\mathbf{X}\hat{\omega})^{T}(\boldsymbol{y}-\mathbf{X}\hat{\omega})
\end{array} \tag{3.9}
$$
同样地进行求导求解，令 $E_{\hat{\boldsymbol{w}}}=(\boldsymbol{y}-\mathbf{X} \hat{\boldsymbol{w}})^{\mathrm{T}}(\boldsymbol{y}-\mathbf{X} \hat{\boldsymbol{w}})$ ，对 $\hat{\omega}$ 求导可得
$$
\frac{\partial E_{\hat{\boldsymbol{w}}}}{\partial \hat{\boldsymbol{w}}}
=2 \mathbf{X}^{\mathrm{T}}(\mathbf{X} \hat{\boldsymbol{w}}-\boldsymbol{y})
=2 \mathbf{X}^{\mathrm{T}}\mathbf{X} \hat{\boldsymbol{w}}-2 \mathbf{X}^{\mathrm{T}}\boldsymbol{y}
\tag{3.10}
$$
> 式3.10 涉及到矩阵求导，可以参考[维基百科矩阵运算](https://en.wikipedia.org/wiki/Matrix_calculus) ，[刘建平的解释](https://www.cnblogs.com/pinard/p/10750718.html)，在这里我们就知道一些基本的运算即可，
>
> ![向量或矩阵求导](../static/img/scalar_by_vector_identities.jpg)
>
> 这里对矩阵的求导还分为分子布局(**Numerator layout** , 对应上图结果左)和分母布局(**Denominator layout**，对应上图结果右) ，一般准则是对于向量或者矩阵**对**标量求导，则使用分子布局，对于标量**对**向量或者矩阵，则使用分母布局。

由此我们可以对式3.10 展开并得到各部分的求导结果
$$
\begin{array}{cl}
\frac{\partial E_{\hat{\boldsymbol{w}}}}{\partial \hat{\boldsymbol{w}}} 
&=(\boldsymbol{y}-\mathbf{X} \hat{\boldsymbol{w}})^{\mathrm{T}}(\boldsymbol{y}-\mathbf{X} \hat{\boldsymbol{w}}) \\
&=\frac{\partial \boldsymbol{y}^{T} \boldsymbol{y}}{\partial \hat{\boldsymbol{w}}}-\frac{\partial \boldsymbol{y}^{T} \mathbf{X} \hat{\boldsymbol{w}}}{\partial \hat{\boldsymbol{w}}}-\frac{\partial \hat{\boldsymbol{w}}^{T} \mathbf{X}^{T} \boldsymbol{y}}{\partial \hat{\boldsymbol{w}}}+\frac{\partial \hat{\boldsymbol{w}}^{T} \mathbf{X}^{T} \mathbf{X} \hat{\boldsymbol{w}}}{\partial \hat{\boldsymbol{w}}}\\
& =0- \mathbf{X}^{T} \boldsymbol{y}- \mathbf{X}^{T} \boldsymbol{y} + (\mathbf{X}^{T}\mathbf{X}+ (\mathbf{X}^{T}\mathbf{X})^{T})\hat{\omega} \\
&=2 \mathbf{X}^{\mathrm{T}}(\mathbf{X} \hat{\boldsymbol{w}}-\boldsymbol{y}) 
\end{array}
\tag{3.10.1}
$$
令式 3.10 为 0 即可得到最优解的闭式解。
$$
\hat{\boldsymbol{w}}^{*}=(\mathbf{X}^{\mathrm{T}}\mathbf{X} )^{-1}\mathbf{X}^{\mathrm{T}}\boldsymbol{y}  \tag{3.11}
$$
可以发现以矩阵的形式我们得到的闭式解很简洁，然而我们却无法忽略一个问题， $(\mathbf{X}^{\mathrm{T}}\mathbf{X} )^{-1}$ 是否存在？

对于 $\mathbf{X}^{\mathrm{T}}\mathbf{X}$ ，它是一个方阵，这是一个很好的性质，但是它却不一定满秩（比如音频，基因等，都可能特征数量大于（甚至远大于）样例数量），只有当其为满秩矩阵( full-rank matrix) 或正定矩阵(positive definite matrix)时，我们才能得到式3.11 。

现我们假设该方阵是满秩的情况，令 $\boldsymbol{\hat{x_i}}=(\boldsymbol{x_i};1)$ 则多元线性回归模型可以表示为
$$
f\left(\hat{\boldsymbol{x}}_{i}\right)=\hat{\boldsymbol{x}}_{i}^{\mathrm{T}}\left(\mathbf{X}^{\mathrm{T}} \mathbf{X}\right)^{-1} \mathbf{X}^{\mathrm{T}} \boldsymbol{y}  \tag{3.12}
$$

对于现实任务中 $\mathbf{X}^{\mathrm{T}}\mathbf{X}$ 不是满秩矩阵的情况，此时可解出多个 $\hat{\omega}^{*}$，它们都能使均方误差最小化，选择哪一个解作为输出，将由学习算法的归纳偏好决定，常见的做法是引入正则化(regularization)项。



### 3.2.3 广义线性模型

generalized linear model 

线性模型虽然简单，但却有丰富的变化。对于样例 $(\mathbf{x},y), y\in \mathbb{R}$ ，当我们希望线性模型（3.2）的预测值逼近真实标记 $y$ 时，就得到了线性回归模型，我们将模型简写为
$$
y = \mathbf{\omega}^{T} \mathbf{x} + b \tag{3.13}
$$
有时像上面这种原始的线性回归可能并不能满足需求，例如：$y$ 值并不是线性变化，而是在指数尺度上变化。这时我们可以采用线性模型来逼近 $y$ 的衍生物，例如 $\ln y$，这时衍生的线性模型如下所示，实际上就是相当于将指数曲线投影在一条直线上，如下图所示：
$$
\ln y = \mathbb{\omega}^{T} \mathbb{x} +b \tag{3.14}
$$
![generalized_linear_model](../static/img/generalized_linear_model.png)

式3.14在形式上仍然式线性回归，但实质上已经式在求输入空间到输出空间的非线性函数映射。



一般地，考虑所有 $y$ 的衍生物的情形，就得到了“广义的线性模型”（generalized linear model）
$$
y = g^{-1}(\mathbb{\omega}^{T}\mathbb{x}+b) \tag{3.15}
$$
其中，$g(\cdot)$ 单调可微（即连续且充分光滑），称为联系函数（link function）。



## 3.3 对数几率回归

线性模型可以应用于回归学习问题，利用上述广义线性模型的特征，是否可以通过一个联系函数，将预测值转化为离散值从而进行分类任务的学习呢？

考虑二分类任务，其输出标记 $y\in \{0,1\}$ ，而线性回归模型产生的预测值 $z=\mathbf{\omega}^{T} \mathbf{x} + b$ 是实值，于是我们需要将其转化为 0/1，最理想的是"单位阶跃函数" (unit-step function)
$$
y=\left\{
\begin{array}{cl}
{0,} & {z<0} \\ 
{0.5,} & {z=0} \\ 
{1,} & {z>0}
\end{array}\right. \tag{3.16}
$$
![unit_step_function](../static/img/unit_step_function.png)

由上图可知单位阶跃函数不连续，因此不能作为广义线性模型中的联系函数，于是我们希望找到能在一定程度上近似单位阶跃函数的”替代函数“ (surrogate function)，并且它可以作为联系函数（单调可微），对数几率函数（logistic function）正是替代函数之一，可将预测值投影到 0-1之间，从而将线性回归问题转化为二分类问题。
$$
y=\frac{1}{1+e^{-z}} \tag{3.17}
$$
对数几率函数也是一种”Sigmoid 函数“ （即形似 S 的函数）。

将式 3.17 代入式 3.15 即可得到
$$
y=\frac{1}{1+e^{-\left(\boldsymbol{w}^{\mathrm{T}} \boldsymbol{x}+b\right)}} \tag{3.18}
$$
基于式 3.14的变换方式，可得到
$$
\ln \frac{y}{1-y}=\boldsymbol{w}^{\mathrm{T}} \boldsymbol{x}+b \tag{3.19}
$$
若将 $y$ 看做样本为正例的概率，$1-y$ 则为反例的概率，两者比值称为”几率“ (odds), 反映了样本作为正例的相对可能性。对几率取对数则得到”对数几率“ （log odds，亦称 logit）
$$
\frac{y}{1-y} \tag{3.20}
$$

$$
\ln \frac{y}{1-y} \tag{3.21}
$$



由此可看出，式3.18 实际上是在用线性回归模型的预测结果取逼近真实标记的对数几率，因此这个模型称为“对数几率回归”（logistic regression，或 logit regression），即“逻辑回归”。它的优点在于直接对分类可能性进行建模，无需事先假设数据分布，这样就避免了假设分布不准确所带来的问题；不仅可以预测类别，也可得到近似概率预测；对数几率函数是任意阶可导的凸函数，现有的许多数值优化算法都可直接用于求取最优解。

逻辑回归（对数几率回归）带有2个主要假设：

**（1）假设数据服从伯努利分布**

**（2）假设模型的输出值是样本为正例的概率**

若将式3.18中的 $y$ 视为类后验概率估计 $p(y=1|x)$ ，则式3.19可重写为
$$
\ln \frac{p(y=1 | \boldsymbol{x})}{p(y=0 | \boldsymbol{x})}=\boldsymbol{w}^{\mathrm{T}} \boldsymbol{x}+b  \tag{3.22}
$$
因为 $p(y=1|x)+p(y=0|x)=1$ ，于是我们可以得到
$$
p(y=1 | \boldsymbol{x})=\frac{e^{\boldsymbol{w}^{\top} \boldsymbol{x}+b}}{1+e^{\boldsymbol{w}^{\top} \boldsymbol{x}+b}} \tag{3.23}
$$

$$
p(y=0 | \boldsymbol{x})=\frac{1}{1+e^{\boldsymbol{w}^{\top} \boldsymbol{x}+b}} \tag{3.24}
$$



于是，可以使用极大似然估计的方法（maximum likelihood estimation, MLE）来计算出 $\omega $ 和 $b$ 两个参数

对于给定的训练数据集 $D=\{(x_i,y_i)\}_{i=1}^{m}$ ，该数据集出现的概率（即似然函数）为
$$
\ell(\boldsymbol{\omega},b) = P(D) = \prod p(y_i | \boldsymbol{x_i} ; \boldsymbol{\omega},b)
$$
对似然函数取对数得到“对数似然”(log-likelihood)
$$
LL(\boldsymbol{w}, b)=\ln \ell(\boldsymbol{w}, b)=\sum_{i=1}^{m} \ln p\left(y_{i} | \boldsymbol{x}_{i} ; \boldsymbol{w}, b\right) \tag{3.25}
$$
极大似然最简单的理解就是：样本所展现的状态便是所有可能状态中出现概率最大的状态。即令每个样本属于其真实标记的概率越大越好。为便于讨论，令 $\boldsymbol{\beta} = (\boldsymbol{\omega},b), \boldsymbol{\hat{x}}=(\boldsymbol{x};1)$ ，则 $\boldsymbol{w}^{\mathrm{T}} \boldsymbol{x}+b = \boldsymbol{\beta}^{T} \boldsymbol{\hat{x}}$ ,  令 $p_1(\boldsymbol{\hat{x}};\boldsymbol{\beta}) = p(y=1|\boldsymbol{\hat{x}};\boldsymbol{\beta})$ , $p_0(\boldsymbol{\hat{x}};\boldsymbol{\beta}) = p(y=0|\boldsymbol{\hat{x}};\boldsymbol{\beta})=1-p_1(\boldsymbol{\hat{x}};\boldsymbol{\beta}) $ ， 于是似然项可以重写为
$$
p\left(y_{i} | \boldsymbol{x}_{i} ; \boldsymbol{w}, b\right)=y_{i} p_{1}\left(\hat{\boldsymbol{x}}_{i} ; \boldsymbol{\beta}\right)+\left(1-y_{i}\right) p_{0}\left(\hat{\boldsymbol{x}}_{i} ; \boldsymbol{\beta}\right) \tag{3.26}
$$
将式3.26，3.23，3.24带入式3.25，则可以转化式3.25为
$$
\begin{array}{cl}LL(\boldsymbol{\beta})&=\sum_{i=1}^{m} \ln(y_{i} p_{1}\left(\hat{\boldsymbol{x}}_{i} ; \boldsymbol{\beta}\right)+\left(1-y_{i}\right) p_{0}\left(\hat{\boldsymbol{x}}_{i} ; \boldsymbol{\beta}\right)) \\&=\sum_{i=1}^{m} \ln (y_i\frac{e^{\boldsymbol{\beta}^{T} \boldsymbol{\hat{x_i}}}}{1+e^{\boldsymbol{\beta}^{T} \boldsymbol{\hat{x_i}}}} + (1-y_i)\frac{1}{1+e^{\boldsymbol{\beta}^{T} \boldsymbol{\hat{x_i}}}} ) \\&=\sum_{i=1}^{m} \left(\ln (y_i e^{\boldsymbol{\beta}^{T} \boldsymbol{\hat{x_i}}}+1-y_i) - \ln(1+e^{\boldsymbol{\beta}^{T} \boldsymbol{\hat{x_i}}}) \right)\end{array}  \tag{3.26.1}
$$
将 $y_i \in \{0,1\}$ 代入得到
$$
LL(\boldsymbol{\beta}) = \left\{\begin{array}{ll}{\sum_{i=1}^{m}\left(-\ln \left(1+e^{\beta^{T} \hat{x_i}}\right)\right),} & {y_{i}=0} \\ {\sum_{i=1}^{m}\left(\boldsymbol{\beta}^{T} \hat{\boldsymbol{x}}_{i}-\ln \left(1+e^{\boldsymbol{\beta}^{T} \hat{x_i}}\right)\right),} & {y_{i}=1}\end{array}\right.  \tag{3.26.2}
$$
综合上式即可得到
$$
LL(\boldsymbol{\beta})=\sum_{i=1}^{m}\left(y_{i} \boldsymbol{\beta}^{T} \hat{\boldsymbol{x_i}}-\ln \left(1+e^{\boldsymbol{\beta}^{T} \hat{x_i}}\right)\right) \tag{3.27}
$$
而损失函数即为对数似然函数的相反数，对于对数似然函数（高阶可导连续凸函数）求最大值，即是求其相反数的最小值，即损失函数的最小值。根据凸优化理论，经典的数值优化算法如梯度下降法(gradient descent method)、牛顿法(Newton method)等都可求得其最优解，于是就得到
$$
\boldsymbol{\beta}^{*} = \underset{\beta}{\arg \min} \left(-LL(\beta)\right) \tag{3.28}
$$

注: 逻辑回归的损失函数“对数似然函数(的相反数)”，在模型GBDT分类情况下也会用到，又叫作**“交叉熵”**（cross-entropy，描述两组不同概率数据分布的相似程度，越小越相似）。

用一句话来描述逻辑回归的过程：逻辑回归假设数据服从伯努利分布，通过极大化似然函数的方法，运用梯度下降来求解参数得出分类概率，通过阈值过滤来达到将数据二分类的目的。

## 3.4 线性判别分析

[comment ]: <后续补充>

## 3.5 多分类学习

[comment ]: <后续补充>


## 3.6 类别不平衡问题

前面介绍的分类学习方法都有一个共同的基本假设，即不同类别的训练样例数目相当，如果不同类别的训练样例数目稍有差别，通常影响不大，但若差别很大，则会对学习过程造成困扰，例如有998个反例，但正例只有2个，那么学习方法只需返回一个永远将新样本预测为反例的学习器，就能达到99.8%的精度，然而这样的学习器往往没有价值，因为它不能预测出任何正例。

类别不平衡（class-imbanlance）就是指分类问题中不同类别的训练样本相差悬殊的情况，常见的做法有三种：

1. 在训练样本较多的类别中进行“欠采样”（under-sampling / down-sampling），即去除一些样本，比如从反例中采出100个，常见的算法有：EasyEnsemble，其利用集成学习机制，将反例划分为若干个集合供不同学习器使用，这样对每个学习器来看都进行了欠采样，但在全局来看不会丢失重要信息。
2. 在训练样本较少的类别中进行“过采样”（oversampling / up-sampling），例如通过对正例中的数据进行插值，来产生额外的正例，常见的算法有SMOTE（Synthetic minority over-sampling technique）。
3. 直接基于原数据集进行学习，对预测值进行“再缩放”(rescaling / re-balance)处理。其中再缩放也是代价敏感学习的基础。

前两种方法都关注于对于数据样本进行均衡，而第三种方法则是关注于对预测结果进行均衡，称为“阈值移动” (threshold-moving)。

以逻辑回归应用在二分类问题为例，当我们在用 $y=\omega^{T}x +b $ 对新样本进行预测的时候，事实上是在用预测出的 $y$ 值与阈值进行比较，对于逻辑回归而言，因为联系函数的分段点在 $y=0.5$ 的位置，即在几率大于 1 时判定为正例，反之为反例。
$$
\frac{y}{1-y} > 1 \quad,  \text{预测为正例}  \tag{3.46}
$$
但是当训练集中正/反例的数目不同时，令 $m^{+}$ 表示正例数目，$m^{-}$ 表示反例数目，则观测几率是 $\frac{m^{+}}{m^{-}}$ ，由于我们通常假设训练集是真实样本总体的无偏采样，因此观测几率就代表了真实几率，于是，只要分类器的预测几率高于观测几率就应判定为正例，即
$$
\frac{y}{1-y} > \frac{m^{+}}{m^{-}} \quad, \text{预测为正例}  \tag{3.47}
$$
由于分类器是基于式3.46 进行决策，因此需要对其结果进行调整，使其执行式3.47，于是我们只需要令
$$
\frac{y^{\prime}}{1-y^{\prime}}=\frac{y}{1-y} \times \frac{m^{-}}{m^{+}} \tag{3.48}
$$
这就是在决策过程中进行了再缩放。



## 3.7 阅读材料

“稀疏表示” (sparse representation) 近年来很受关注（详细见第十一章），但即便对多元线性回归这样简单的模型，获得具有最优“稀疏性” (sparsity)的解也并不容易。稀疏性问题本质上对应了 $L_0$ 范数的优化，这在通常条件下是NP难问题。 LASSO通过 $L_1$ 范数来近似 $L_{0}$ 范数，是求取稀疏解的重要技术。

可以证明，OvO和 OvR 都是ECOC的特例[Allwein et al., 2000])，人们以往希望设计通用的编码法, [Crammer and Singer, 2002]提出要考虑问题本身的特点，设计“问题依赖”的编码法，并证明寻找最优的离散编码矩阵是一个NP完全问题，此后，有多种问题依赖的 ECOC编码法被提出，通常是通过找出具有代表性的二分类问题来进行编码，[Escalera et al., 2010]开发了一个开源ECOC库.

MvM除了ECOC还可有其他实现方式，例如DAG (Directed Acyclic Graph)拆分法将类别划分表达成树形结构，每个结点对应于一个二类分类器，还有一些工作是致力于直接求解多分类问题，例如多类支持向量机方面的一些研究[Crammer and Singer, 2001; Lee et al, 2004])

代价敏感学习中研究得最多的是基于类别的“误分类代价” (misclassification cost)， 代价矩阵如表2.2所示，在提及代价敏感学习时，默认指此类情形，已经证明，对二分类任务可通过“再缩放”获得理论最优解[Elkan,2001]，但对多分类任务，仅在某些特殊情形下存在闭式解[Zhouand Liu, 2006]。非均等代价和类别不平衡性虽然都可借助“再缩放”技术，但两者本质不同[Zhou and Liu, 2006b]。需注意的是，类别不平衡学习中通常是较小类的代价更高，否则无需进行特殊处理。

多分类学习中虽然有多个类别，但每个样本仅属于一个类别，如果希望为一个样本同时预测出多个类别标记，例如一幅图像可同时标注为“蓝天”、“白云”、“羊群”、“自然场景” ，这样的任务就不再是多分类学习，而是“多标记学习” (multi-label learning)，这是机器学习中近年来相当活跃的一个研究领域。



# 第四章 决策树

## 4.1 决策树基本流程

决策树(decision tree，亦称为判定树)是一类常见的机器学习方法。

以二分类任务为例，我们希望从给定训练数据集学得一个模型用以对新实例进行分类，这个把样本分类的任务，可看作对“当前样本属于正类吗?"这个问题的“决策”或“判定”过程，顾名思义，决策树是基于树结构来进行决策的，这恰是人类在面临决策问题时一种很自然的处理机制。

例如，我们要对“这是好瓜吗?"这样的问题进行决策时，通常会进行一系列的判断或“子决策"：我们先看“它是什么颜色?"，如果是“青绿色”，则我们再看“它的根蒂是什么形态?" ，如果是“蜷缩" ，我们再判断“它敲起来是什么声音?" ，最后，我们得出最终决策:这是个好瓜。决策过程如图4.1所示：



![4.1 decision_tree_4.1](../static/img/decision_tree_4.1.png)

显然，决策过程的最终结论对应了我们所希望的判定结果，例如“是”或“不是”好瓜；决策过程中提出的每个判定问题都是对某个属性的“测试” ，例如“色泽=?" “根蒂=?" ；每个测试的结果或是导出最终结论，或是导出进一步的判定问题，其考虑范围是在上次决策结果的限定范围之内，例如若在“色泽=青绿”之后再判断“根蒂=?" ，则仅在考虑青绿色瓜的根蒂。

一般一颗决策树包含：一个根节点、若干个内部节点和若干个叶子节点，易知：

```
* 每个叶节点存放一个类别，对应于决策结果。
* 每个非叶节点表示一个特征/属性测试。
* 每个节点包含的样本集合通过属性测试被划分到子节点中，每个分支代表这个特征/属性在某个值域上的输出。
* 根节点包含样本全集。
* 从根节点到每个叶节点的路径对应了一个判定测试序列（决策序列）。
```



决策树学习的目的是为了产生一颗泛化能力强，即处理未见实例（样本）能力强的决策树（判定规则），其基本流程遵循简单且直观的“分而治之”（divide-and-conquer）策略，如图4.2所示

![4.2 desicion_tree_algorithm](../static/img/desicion_tree_algorithm.png)

显然，决策树的生成是一个递归过程，在决策树基本算法中，有三种情形会导致递归返回:

- (1) 当前结点包含的样本全属于同一类别，无需划分； 
- (2) 当前属性集为空，或是所有样本在所有属性上取值相同，无法划分； 
- (3) 当前结点包含的样本集合为空，不能划分。

在第(2)种情形下，我们把当前结点标记为叶结点，并将其类别设定为该结点所含样本最多的类别；在第(3)种情形下，同样把当前结点标记为叶结点，但将其类别设定为其父结点所含样本最多的类别。

注意这两种情形的处理实质不同：情形(2)是在利用当前结点的**后验分布**，而情形(3)则是把父结点的样本分布作为当前结点的**先验分布**。

一句话总结，对于决策树这种树形结构，可以认为是 if-then（如果...那么...） 规则的集合，是以实例为基础的归纳学习。基本思想是自顶向下，以信息增益（或信息增益比，基尼系数等）为度量构建一颗度量标准下降最快的树，每个内部节点代表一个属性的测试，直到叶子节点处只剩下同一类别的样本。

决策树的学习包括三个重要的步骤，**特征选择**，**决策树的生成**以及**决策树的剪枝**：

- **特征选择：**特征选择方法有信息增益，信息增益比，基尼系数等。
- **生成过程：**通过计算信息增益或其它指标，选择最佳特征。从根结点开始，递归地产生决策树，不断的选取局部最优的特征，将训练集分割成能够基本正确分类的子集。（如图4.1所示）
- **剪枝过程：**有预剪枝和后剪枝两类方法。



## 4.2 划分选择

从 图4.2 的决策树算法过程可以看出：决策树学习的关键在于第8行，即如何选择**最优**划分属性，不同的划分属性得出不同的分支结构，从而影响整颗决策树的性能。一般而言，随着划分过程不断进行，我们希望决策树的分支结点所包含的样本尽可能属于同一类别，即结点的 “纯度”(purity) 越来越高。决策树最常用的量化纯度的指标有三种：信息熵，信息增益比，基尼系数，分别对应了ID3, C4.5, CART 三种决策树算法。



### 4.2.1 信息增益

ID3（Iterative Dichotomiser，迭代二分器）算法使用信息增益为准则来选择划分属性，“信息熵”(information entropy)是度量样本集合纯度（随机变量不确定度）的常用指标，假定当前样本集合 $D$ 中第 $k$ 类样本所占比例为 $p_k(k=1,2,\dots,|y|)$，则样本集合 $D$ 的信息熵定义为：
$$
\operatorname{Ent}(D)=-\sum_{k=1}^{|y|} p_{k} \log_2{p_k} \tag{4.1}
$$
$\operatorname{Ent}(D)$ 的值**越小**（最小值为0，最大值为 $\log_2{|y|}$ ），则样本集 $D$ 的**纯度越高**。其中 $|y|$ 表示样本类别数——最终分类数，如{好瓜，坏瓜}，则值为2。



> 信息论之父克劳德·香农，总结了信息熵的三条性质：
>
> - **单调性**，即发生概率越高的事件，其所携带的信息熵越低。极端案例就是“太阳从东方升起”，因为为确定事件，所以不携带任何信息量。从信息论的角度，认为这句话没有消除任何不确定性。
> - **非负性**，即信息熵不能为负。这个很好理解，因为负的信息，即你得知了某个信息后，却增加了不确定性是不合逻辑的。
> - **累加性**，即多随机事件同时发生存在的总不确定性的量度是可以表示为各事件不确定性的量度的和。写成公式就是事件 $X=A, Y=B$ 同时发生，两个事件相互独立，则 $p(X=A,Y=B)=p(X=A)\ast p(Y=B)$ ,那么信息熵为 $H(A,B)=H(A)+H(B)$ 
>
> 香农从数学上，严格证明了满足上述三个条件的随机变量不确定性度量函数具有唯一形式：
> $$
> H(X)=-C \sum\limits_{x\in \mathrm{X}} = p(x)\log p(x)
> $$
> 其中 $C$ 为常数，将其归一化之后即得到信息熵公式。
>
> 如果两个随机事件不独立，则满足 $H(A,B)=H(A)+H(B)-I(A,B)$ ，其中 $I(A,B)$ 为互信息（mutual information），代表一个随机变量包含另一个随机变量的度量。



假定离散属性 $a$ 有 $V$ 个可能的取值 $\{a^{1},a^{2},\dots,a^{V} \}$ ，通过 $a$ 属性划分样本集 $D$，则产生了 $V$ 个分支结点，用 $v$ 表示其中第 $v$ 个分支结点，则该分支结点包含了 $D$ 中所有在属性 $a$ 上取值为 $a^{v}$ 的样本，记为 $D^{v}$ 。由式4.1我们即可计算该划分下的信息熵，并且易知：分支结点包含的样本数越多，表示该分支结点的影响力越大，则对分支结点根据样本数比例赋予权重 $|D^{v}|/|D|$ ，即可计算出划分后相比原始数据集 $D$ 获得的“信息增益”（information gain）
$$
\operatorname{Gain}(D,a) = \operatorname{Ent}(D)- \sum_{v=1}^{V} \frac{|D^{v}|}{|D|} \operatorname{Ent}(D^{v})  \tag{4.2}
$$
信息增益越大，表示使用该属性划分样本集 $D$ 的效果越好，即使用该属性来进行划分所获得的纯度提升越大。因此 ID3 算法在递归过程中，每次选择最大信息增益的属性作为当前的划分属性，即在图4.2的算法流程的第8行中，选择属性 $a_* = \underset{a \in A}{\arg \max Gain(D,a)}$ 。

表4.1 西瓜数据集2.0

| 编号 | 色泽 | 根蒂 | 敲声 | 纹理 | 脐部 | 触感 | 好瓜 |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 1    | 青绿 | 蜷缩 | 浊响 | 清晰 | 凹陷 | 硬滑 | 是   |
| 2    | 乌黑 | 蜷缩 | 沉闷 | 清晰 | 凹陷 | 硬滑 | 是   |
| 3    | 乌黑 | 蜷缩 | 浊响 | 清晰 | 凹陷 | 硬滑 | 是   |
| 4    | 青绿 | 蜷缩 | 沉闷 | 清晰 | 凹陷 | 硬滑 | 是   |
| 5    | 浅白 | 蜷缩 | 浊响 | 清晰 | 凹陷 | 硬滑 | 是   |
| 6    | 青绿 | 稍蜷 | 浊响 | 清晰 | 稍凹 | 软粘 | 是   |
| 7    | 乌黑 | 稍蜷 | 浊响 | 稍糊 | 稍凹 | 软粘 | 是   |
| 8    | 乌黑 | 稍蜷 | 浊响 | 清晰 | 稍凹 | 硬滑 | 是   |
| 9    | 乌黑 | 稍蜷 | 沉闷 | 稍糊 | 稍凹 | 硬滑 | 否   |
| 10   | 青绿 | 硬挺 | 清脆 | 清晰 | 平坦 | 软粘 | 否   |
| 11   | 浅白 | 硬挺 | 清脆 | 模糊 | 平坦 | 硬滑 | 否   |
| 12   | 浅白 | 蜷缩 | 浊响 | 模糊 | 平坦 | 软粘 | 否   |
| 13   | 青绿 | 稍蜷 | 浊响 | 稍糊 | 凹陷 | 硬滑 | 否   |
| 14   | 浅白 | 稍蜷 | 沉闷 | 稍糊 | 凹陷 | 硬滑 | 否   |
| 15   | 乌黑 | 稍蜷 | 浊响 | 清晰 | 稍凹 | 软粘 | 否   |
| 16   | 浅白 | 蜷缩 | 浊响 | 模糊 | 平坦 | 硬滑 | 否   |
| 17   | 青绿 | 蜷缩 | 沉闷 | 稍糊 | 稍凹 | 硬滑 | 否   |

以表4.1中西瓜数据集2.0 为例，该数据集包含17个训练样例，显然, $|y|=2$，在决策树学习开始时，根结点包含 $D$ 中的所有样例，其中正例占 $p_1 = 8/17$，反例占 $p_2 = 9/17$。于是，根据式(4.1)可计算出根结点的信息煽为
$$
\begin{array}{cl}\operatorname{Ent}(D) &= -\sum\limits_{k=1}^{2} p_{k} \log_2{p_k}  \\&= -(8/17)* \log_2(8/17) -(9/17)\log_2(9/17) \\&= 0.9975 \approx 0.998\end{array})
$$
然后我们计算整个属性集 $A$ 中 {色泽，根蒂，敲声，纹理，脐部，触感} 每个属性的信息增益，以属性”色泽“为例，它有3个可能的取值，即 {青绿，乌黑，浅白} ，使用该属性（色泽）对数据集 $D$ 进行划分，即得到3个子集：$D^{1}$(色泽=青绿)，$D^{2}$(色泽=乌黑)，$D^{3}$(色泽=浅白) 。

子集 $D^1$ 包含编号为 {1， 4， 6， 10， 13， 17} 的6个样例，其中正例占 $p_1=3/6$，反例占 $p_2=3/6$; $D^2$ 包含编号为 {2， 3， 7， 8， 9， 15} 的6个样例，其中正、反例分别占 $p_1=4/6$， $p_2=2/6$ ;  $D^3$ 包含编号为 {5， 11， 12， 14， 16}的5个样例，其中正、反例分别占 $p_1=1/5$ ，$p_2=4/5$ 。根据 式(4.1) 可计算出用“色泽”划分之后所获得的3个分支结点的信息熵为
$$
\begin{array}{cl}\operatorname{Ent}(D^1) &= -(3/6)* \log_2(3/6) -(3/6)\log_2(3/6)=1.0  \\\operatorname{Ent}(D^2) &= -(4/6)* \log_2(4/6) -(2/6)\log_2(2/6)=0.918  \\\operatorname{Ent}(D^3) &= -(1/5)* \log_2(1/5) -(4/5)\log_2(4/5)=0.722  \\\end{array}
$$
再根据 式4.2 即可得到属性“色泽”的信息增益
$$
\begin{array}{cl}\operatorname{Gain}(D, \text{色泽})& = \operatorname{Ent}(D) - \sum\limits_{v=1}^{3} \frac{|D^{v}|}{|D|} \operatorname{Ent}(D^{v})  \\& = 0.998 - (\frac{6}{17} *1.0 + \frac{6}{17} *0.918 +\frac{5}{17} *0.722)  \\& = 0.109\end{array}
$$
类似地，我们可以计算得到其他5个属性的信息增益和它们各自属性值分支结点的信息熵
$$
\begin{array}{cl}\operatorname{Ent}(蜷缩，根蒂) &= -(5/8)* \log_2(5/8) -(3/8)\log_2(3/8) =0.954  \\\operatorname{Ent}(稍蜷，根蒂) &= -(3/7)* \log_2(3/7) -(4/7)\log_2(4/7)=0.985  \\\operatorname{Ent}(硬挺，根蒂) &= -(0/2)* \log_2(0/2) -(2/2)\log_2(2/2)=0  \\\operatorname{Ent}(浊响，敲声) &= -(6/10)* \log_2(6/10) -(4/10)\log_2(4/10)=0.971  \\\operatorname{Ent}(沉闷，敲声) &= -(2/5)* \log_2(2/5) -(3/5)\log_2(3/5)= 0.971  \\\operatorname{Ent}(清脆，敲声) &= -(0/2)* \log_2(0/2) -(2/2)\log_2(2/2)=0  \\\operatorname{Ent}(清晰，纹理) &= -(7/9)* \log_2(7/9) -(2/9)\log_2(2/9)=0.764  \\\operatorname{Ent}(模糊，纹理) &= -(0/3)* \log_2(0/3) -(3/3)\log_2(3/3)=0  \\\operatorname{Ent}(稍糊，纹理) &= -(1/5)* \log_2(1/5) -(4/5)\log_2(4/5)= 0.722  \\\operatorname{Ent}(凹陷，脐部) &= -(5/7)* \log_2(5/7) -(2/7)\log_2(2/7)=0.863  \\\operatorname{Ent}(稍凹，脐部) &= -(3/6)* \log_2(3/6) -(3/6)\log_2(3/6)=1.0  \\\operatorname{Ent}(平坦，脐部) &= -(0/4)* \log_2(0/4) -(4/4)\log_2(4/4)=0  \\\operatorname{Ent}(硬滑，触感) &= -(6/12)* \log_2(6/12) -(6/12)\log_2(6/12)=1.0  \\\operatorname{Ent}(软粘，触感) &= -(2/5)* \log_2(2/5) -(3/5)\log_2(3/5)= 0.971  \\\end{array}
$$

$$
\begin{array}{cl}\operatorname{Gain}(D, \text{根蒂}) &= 0.998 - (\frac{8}{17} *0.954 + \frac{7}{17} *0.985 +\frac{2}{17} *0) = 0.143  \\\operatorname{Gain}(D, \text{敲声}) &= 0.998 - (\frac{10}{17} *0.971 + \frac{5}{17} *0.971 +\frac{2}{17} *0) = 0.141 \\\operatorname{Gain}(D, \text{纹理}) &= 0.998 - (\frac{9}{17} *0.764 + \frac{3}{17} *0 +\frac{5}{17} *0.722) = 0.381 \\\operatorname{Gain}(D, \text{脐部}) &= 0.998 - (\frac{7}{17} *0863 + \frac{6}{17} *1.0 +\frac{4}{17} *0) = 0.289 \\\operatorname{Gain}(D, \text{触感}) &= 0.998 - (\frac{12}{17} *1.0 + \frac{5}{17} *0.971) = 0.006 \\\end{array}
$$

显然，属性“纹理”的信息增益最大，因此我们选择其作为划分属性。图4.3 给出了基于纹理对根结点进行划分的结果，各分支结点所包含的样例子集显示在结点中。

![fig4.3](../static/img/fig4.3.png)

然后，决策树学习算法将对每个分支结点进一步划分，即对应于图4.2中第11行到第15行的步骤。

以图4.3中第一个分支结点（纹理=清晰）为例，样例集为 $D^{1}=\{1,2,3,4,5,6,8,10,15\}$ ，可用属性集 {色泽，根蒂，敲声，脐部，触感} 。

表4.1.1 纹理=清晰样本子集

| 编号 | 色泽 | 根蒂 | 敲声 | 纹理 | 脐部 | 触感 | 好瓜 |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 1    | 青绿 | 蜷缩 | 浊响 | 清晰 | 凹陷 | 硬滑 | 是   |
| 2    | 乌黑 | 蜷缩 | 沉闷 | 清晰 | 凹陷 | 硬滑 | 是   |
| 3    | 乌黑 | 蜷缩 | 浊响 | 清晰 | 凹陷 | 硬滑 | 是   |
| 4    | 青绿 | 蜷缩 | 沉闷 | 清晰 | 凹陷 | 硬滑 | 是   |
| 5    | 浅白 | 蜷缩 | 浊响 | 清晰 | 凹陷 | 硬滑 | 是   |
| 6    | 青绿 | 稍蜷 | 浊响 | 清晰 | 稍凹 | 软粘 | 是   |
| 8    | 乌黑 | 稍蜷 | 浊响 | 清晰 | 稍凹 | 硬滑 | 是   |
| 10   | 青绿 | 硬挺 | 清脆 | 清晰 | 平坦 | 软粘 | 否   |
| 15   | 乌黑 | 稍蜷 | 浊响 | 清晰 | 稍凹 | 软粘 | 否   |

基于该样例集计算各属性的信息增益和它们各自属性值分支结点的信息熵
$$
\begin{array}{cl}\operatorname{Ent}(青绿，色泽) &= -(3/4)* \log_2(3/4) -(1/4)\log_2(1/4)=0.811  \\\operatorname{Ent}(乌黑，色泽) &= -(3/4)* \log_2(3/4) -(1/4)\log_2(1/4)=0.811  \\\operatorname{Ent}(浅白，色泽) &= -(1/1)* \log_2(1/1) -(0/1)\log_2(0/1)= 0  \\\operatorname{Ent}(蜷缩，根蒂) &= -(5/5)* \log_2(5/5) -(0/5)\log_2(0/5) =0  \\\operatorname{Ent}(稍蜷，根蒂) &= -(2/3)* \log_2(2/3) -(1/3)\log_2(1/3)=0.918  \\\operatorname{Ent}(硬挺，根蒂) &= -(0/1)* \log_2(0/1) -(1/1)\log_2(1/1)=0  \\\operatorname{Ent}(浊响，敲声) &= -(5/6)* \log_2(5/6) -(1/6)\log_2(1/6)=0.650  \\\operatorname{Ent}(沉闷，敲声) &= -(2/2)* \log_2(2/2) -(0/2)\log_2(0/2)= 0  \\\operatorname{Ent}(清脆，敲声) &= -(0/1)* \log_2(0/1) -(1/1)\log_2(1/1)=0  \\\operatorname{Ent}(凹陷，脐部) &= -(5/5)* \log_2(5/5) -(0/5)\log_2(0/5)=0  \\\operatorname{Ent}(稍凹，脐部) &= -(2/3)* \log_2(2/3) -(1/3)\log_2(1/3)=0.918  \\\operatorname{Ent}(平坦，脐部) &= -(0/1)* \log_2(0/1) -(1/1)\log_2(1/1)=0  \\\operatorname{Ent}(硬滑，触感) &= -(6/6)* \log_2(6/6) -(0/6)\log_2(0/6)=0  \\\operatorname{Ent}(软粘，触感) &= -(1/3)* \log_2(1/3) -(2/3)\log_2(2/3)= 0.918  \\\end{array}
$$
这里的样本集的信息熵我们在之前已经计算过，即 $Ent(D^{1})=Ent(清晰，纹理)=0.764$
$$
\begin{array}{cl}\operatorname{Gain}(D^{1}, \text{色泽}) &= 0.764 - (\frac{4}{9} *0.811 + \frac{4}{9} *0.811 +\frac{1}{9} *0) = 0.043 \\\operatorname{Gain}(D^{1}, \text{根蒂}) &= 0.764 - (\frac{5}{9} *0 + \frac{3}{9} *0.918 +\frac{1}{9} *0) = 0.458  \\\operatorname{Gain}(D^{1}, \text{敲声}) &= 0.764 - (\frac{6}{9} *0.650 + \frac{2}{9} *0 +\frac{1}{9} *0) = 0.331 \\\operatorname{Gain}(D^{1}, \text{脐部}) &= 0.764 - (\frac{5}{9} *0 + \frac{3}{9} *0.918 +\frac{1}{9} *0) = 0.458 \\\operatorname{Gain}(D^{1}, \text{触感}) &= 0.764 - (\frac{6}{9} *0 + \frac{3}{9} *0.918) = 0.458 \\\end{array}
$$
“根蒂”、“脐部”、“触感” 3个属性均取得了最大的信息增益，可任选其中之一作为纹理=清晰结点下的划分属性，类似的，对其他每个分支结点继续进行上述操作，最终得到的决策树如图4.4所示

![fig4.4](../static/img/fig4.4.png)



### 4.2.2 信息增益率

信息增益指标存在一个问题，就是偏向于取值数目较多的属性，即 V 值较大的属性，例如：对于表4.1 的西瓜数据集2.0的编号列，样本集 $D$ 将会被划分为 $|D|$ 个分支，每个分支只有一个样本，这样划分后每一个分支的信息熵为零，十分纯净，但是对分类毫无用处。

C4.5(Classifier 4.5) 算法使用“增益率”（gain ratio）来选择最优划分属性，来避免信息增益准则对可取值数目较多的属性的偏好导致的不利影响。

因为信息增益率对于可取值数目较少的属性有所偏好（与信息增益相反），因此 C4.5 算法首先计算出所有属性的信息增益，然后取其中高于平均水平的多个候选属性，计算这些候选属性的信息增益率，最后选择信息增益率最高的属性作为最优划分属性，增益率定义为：
$$
{\text { Gain ratio }(D, a)=\frac{\operatorname{Gain}(D, a)}{\operatorname{IV}(a)}}  \tag{4.3}
$$

$$
\operatorname{IV}(a)=-\sum_{v=1}^{V} \frac{\left|D^{v}\right|}{|D|} \log _{2} \frac{\left|D^{v}\right|}{|D|} \tag{4.4}
$$

其中， $\operatorname{IV}(a)$ 称为属性 $a$ 的固有值（intrinsic value），属性 $a$ 的可能取值数目越多（V越大），则通常 $\operatorname{IV}(a)$ 的值越大。

**可以发现固有值的定义与信息熵的定义是一样的！**实际上，属性的固有值就是将该属性作为目标列计算的信息熵，但是因为我们的目标列不是该属性，因此我们称为特征熵。

对于西瓜数据集2.0 我们可以得到各个属性的固有值
$$
\begin{array}{cl}\operatorname{IV}(编号) &= -17*(1/17)* \log_2(1/17)= 4.087  \\\operatorname{IV}(色泽) &= -(6/17)* \log_2(6/17) -(6/17)*\log_2(6/17)-(5/17)*\log_2(5/17) =1.580\\\operatorname{IV}(根蒂) &= -(8/17)* \log_2(8/17) -(7/17)*\log_2(7/17)-(2/17)*\log_2(2/17)=1.402 \\\operatorname{IV}(敲声) &= -(10/17)* \log_2(10/17) -(5/17)*\log_2(5/17)-(2/17)*\log_2(2/17)=1.333 \\\operatorname{IV}(纹理) &= -(9/17)* \log_2(9/17) -(3/17)*\log_2(3/17)-(5/17)*\log_2(5/17) =1.447 \\\operatorname{IV}(脐部) &= -(7/17)* \log_2(7/17) -(6/17)*\log_2(6/17)-(4/17)*\log_2(4/17) =1.549\\\operatorname{IV}(触感) &= -(12/17)* \log_2(12/17) -(5/17)*\log_2(5/17)=0.874 \\\end{array}
$$



### 4.2.3 基尼指数

CART（Classification and Regression Tree）决策树使用“基尼指数”（Gini index）来选择划分属性，基尼指数反映的是从样本集 $D$ 中随机抽取两个样本，其类别标记不一致的概率，因此 $\operatorname{Gini}(D)$ 越小越好，即数据集的纯度越高。数据集 $D$ 的基尼指数：
$$
\operatorname{Gini}(D) =\sum_{k=1}^{|y|} \sum_{k^{\prime} \neq k} p_{k} p_{k^{\prime}} =\sum_{k=1}^{|y|} p_{k}(1-p_{k})=1-\sum_{k=1}^{|y|} p_{k}^{2}  \tag{4.5}
$$
进而，使用属性 $a$ 划分后的基尼指数为：
$$
\operatorname{Gini\_index}(D, a)=\sum_{v=1}^{V} \frac{\left|D^{v}\right|}{|D|} \operatorname{Gini}\left(D^{v}\right)  \tag{4.6}
$$
于是，我们在候选属性集合 A 中，选择使得划分后基尼指数最小的属性作为最优划分属性即可，即
$$
a_* = \underset{a\in A}{\operatorname{arg min\;}} \operatorname{Gini\_index}(D,a)
$$
