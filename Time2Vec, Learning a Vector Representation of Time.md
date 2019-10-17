### Time2Vec: Learning a Vector Representation of Time

#### Abstract

提出了$Time2Vec$，用来表示时间对模型的影响特征，该方法的拓展性较高。

#### Introduction

- 把时间考虑在内的模型都可以被认为是一个序列，因此input之间不是独立同分布的。

- e.g., 例如当预测每天的销售情况，那么一个重要的因素就是这一天是否是holiday。

  大多数的RNN模型都把input当作是同步的。当时间被认为是一个相关的特征时，它通常被作为另一个特征输入输入维度[10,14,35]。RNN并不善于去提取时间的特征。

  - 有几个学者尝试在具体应用下把时间特征作为RNN的输入，但是成本非常的高。

- 提出了一种与具体的时间无关的，通用于各大模型的方法，仿照词嵌入的方式，把time变成vetor

- 把时间向量与其他模型相结合，验证方法的有效性。

#### Related Work

- 处理与时间序列预测有关的模型：hidden Markov models，dynamic Bayesian networks, 这些模型可以被看做是RNN的特殊形式。Gaussian processes 或者support vector regression 也可以在任意的时间戳内回归预测。
- Fourier变换也被用于时间的特征提取，但是它使用的是固定频率，但本文是允许频率被学习。是从WGodfrey and Gashler 提出的神经分解得到的灵感，WGodfrey and Gashler 把一个时间信号分解为几个正弦函数和一个线性函数推断而来。

#### Time2Vec

我们创建了一个连续的基于事件的MNIST版本，方法是压平图像并记录像素的位置，像素的强度大于阈值(在我们的实验中为0.9)；

