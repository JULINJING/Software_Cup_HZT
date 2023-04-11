# Outline
# 比赛内容
## 问题重述
训练集数据为不同10个风电场近一年的运行数据共30万余条，每15分钟采集一次，包括风速、风向、温度、湿度、气压和真实功率等。我们需要设计一种利用当日5:00前的数据，预测次日00:00-23:45实际功率的多变量时间序列预测方法。准确率按日统计，根据10个风电场平均准确率进行排名。
## 数据集
### 数据集字段说明
|  字段名   | 描述  |
|  ----  | ----  |
| DATATIME  | 数据采集时间 |
| WINDSPEED  | 预测风速 |
| PREPOWER |  |
| WINDDIRECTION | 风向 (0-360) 以度为单位 |
| TEMPERATURE | 温度 |
| HUMIDITY | 湿度 |
| PRESSURE |气压 以百帕为单位 (标准大气压1014百帕)|
| ROUND(A.WS,1) | 实际风速 |
| ROUND(A.POWER,0) | 预测目标，计量口径一 |
| YD15| 实际功率(预测目标，计量口径二) |
### 数据集说明
训练数据分为11个表格，其中第四个风电场数据分为两个表格。不同风电场的时间戳序列也不是一一对应的。
# 关键技术
## 数据预处理

## 多元时间序列（MTS）
多变量时间序列具有一个以上的时间依赖变量。每个变量不仅取决于其过去的值，而且还对其他变量有一定的依赖性。这种依赖性用于预测未来的价值。
![image](img/1.png "多元时间序列演示")
## MTS-Mixers
### 背景
-   MTS-Mixers是多变量时间序列预测技术，其在实践中应用广泛，包括电力和天气预测以及交通流量估计等。
-   随着计算资源和模型架构的扩展，深度学习技术，包括基于RNN和CNN的模型，已被证明在预测方面比传统的统计方法表现更好。最近，基于Transformer的模型由于其捕捉长期依赖关系的能力，在预测任务中也显示出了显著的潜力。
- 本文明确了一点transformer模型对于时间序列预测的有效性问题。之前在NLP或者CV的研究中发现用MLP层替换attention层可以得到更好的表现，此模型同样引入了相对attention来说较为简单的MLP。
### 方法
- 理论基础是利用Transformer的方法来捕捉多变量时间序列预测中的时间和通道相关性。
- 提出了一种新的方法MTS-Mixers，它使用两个分解模块来捕捉时间和通道相关性，从而提高预测准确性和效率。
### 贡献

### 结论
- 发现attention不是捕捉时间相关性的必要手段，并且时间相关性和通道相关性之间的纠缠和重叠会影响预测性能。为了克服这些挑战，提出了MTS-Mixers，它使用两个分解模块来捕捉时间和通道相关性。MTS-Mixers已经在多个公共实际多变量时间序列数据集上达到了最先进的预测性能，平均降低了15.4％的MSE(均方误差)和12.9％的MAE(平均绝对误差)。
### 官方实现
[plumprc/MTS-Mixers: MTS-Mixers: Multivariate Time Series Forecasting via Factorized Temporal and Channel Mixing (github.com)](https://github.com/plumprc/MTS-Mixers)
# 软件创新点
## 可视化
## 实时更新与滚动预测

# 实验验证
