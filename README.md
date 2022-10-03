# HMM-project

## 基于隐马尔可夫模型的心梗阶段分析以及急性心梗事件预测

### 研究意义

根据《中国心血管健康与疾病报告2019》，每年约有350万人死于心血管疾病，其中心肌梗死患病人数高达250万。

临床上心血管疾病特别是心梗后病人病情的快速演变具有时效性强，不确定性因素等特点，流行病学及回归分析已经不能很好的满足实际应用的需要。

人口学信息、既往疾病史、家族疾病史等的简单样本数据已经不足以支撑对于病人病情演变的模拟。

心梗后心血管意外事件预见性差，如何能够提早从微妙的状态波动中发现识别？

### 连续时间隐马尔可夫模型与心梗发展阶段

在传统HMM模型的基础上，加入不同心梗阶段的持续时长。

![image](https://github.com/zoey-zhijing/HMM-project/blob/main/figures/VDHMM%E6%A8%A1%E5%9E%8B.png)

#### 观测空间定义

从1266条诊断记录中，根据词频统计的方法，选择出出现频率最高的“胸闷”、“狭窄”、“胸痛”、“头晕”、“中段”、“呕吐”、“不适”、“恶心”八个并发症分词。

 将8个分词描述作为自变量输入、诊断结果作为因变量输出，分为非急性心梗（陈旧性心梗）与急性心梗，建立Logistic回归模型。

 选择表现最好的“胸闷”“狭窄”“胸痛”三个分词作为观测空间。

#### 分词回归结果

![image](https://github.com/zoey-zhijing/HMM-project/blob/main/figures/%E5%88%86%E8%AF%8D%E5%9B%9E%E5%BD%92.png)

### 离散时间隐马尔科夫模型与回归模型参数

#### 模型参数

$$\lambda=(N,M,\pi,A,B)$$

#### 回归模型参数

$$ logit(P(Y_{ij}=1|s_{ij},Z_{ij}))=w_0+\sum\limits_{s=1}^N w_s \mathcal{I}(s_{ij}=s)+w^T_Z\cdot Z_{ij}$$

#### 极大似然估计方法

![image](https://github.com/zoey-zhijing/HMM-project/blob/main/figures/LR_benchmark.png)

选择状态空间元素个数为4：

回归模型结果：预测精度为71.64%

![image](https://github.com/zoey-zhijing/HMM-project/blob/main/figures/%E5%88%9D%E5%A7%8B%E5%88%86%E5%B8%834.jpeg)

![image](https://github.com/zoey-zhijing/HMM-project/blob/main/figures/%E8%BD%AC%E7%A7%BB%E6%A6%82%E7%8E%87%E7%9F%A9%E9%98%B54.jpeg)

![image](https://github.com/zoey-zhijing/HMM-project/blob/main/figures/%E8%BE%93%E5%87%BA%E6%A6%82%E7%8E%87%E7%9F%A9%E9%98%B54.jpeg)

![image](https://github.com/zoey-zhijing/HMM-project/blob/main/figures/LR_4.png)

选择状态空间元素个数为3

回归模型结果：预测精度为71.56%

![image](https://github.com/zoey-zhijing/HMM-project/blob/main/figures/LR_3.png)

![image](https://github.com/zoey-zhijing/HMM-project/blob/main/figures/%E5%88%9D%E5%A7%8B%E5%88%86%E5%B8%833.jpeg)

![image](https://github.com/zoey-zhijing/HMM-project/blob/main/figures/%E8%BD%AC%E7%A7%BB%E6%A6%82%E7%8E%87%E7%9F%A9%E9%98%B53.jpeg)

![image](https://github.com/zoey-zhijing/HMM-project/blob/main/figures/%E8%BE%93%E5%87%BA%E6%A6%82%E7%8E%87%E7%9F%A9%E9%98%B53.jpeg)

### 未来研究方向

除了并发症信息，我们计划纳入更多的危险因素信息（协变量）。

采用连续时间马氏过程分析心梗病人的心梗阶段发展。

在模型参数的估计方面，找到使似然函数本身最大化的一组参数。

