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
## 多元时间序列（MTS）
多变量时间序列具有一个以上的时间依赖变量。每个变量不仅取决于其过去的值，而且还对其他变量有一定的依赖性。这种依赖性用于预测未来的价值。
# 实验验证
