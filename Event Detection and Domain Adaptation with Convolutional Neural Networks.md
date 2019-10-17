### Event Detection and domain adaptation with Convolutional neural networks

complicated feature engineering for rich feature sets and error propagation from the preceding stages which generate these features.

> 什么叫产生这些特征的前一阶段的误差传导？

#### Introduction

- An example: in the sentence “A police officer was killed in New Jersey today”, an event detection system should be able to recognize the word “killed” as a trigger for the event “Die”.

#### Model

<img src="C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\1570755934512.png" alt="1570755934512" style="zoom:200%;" />

- limit the context to a fixed window size by trimming longer sentences and padding shorter sentences with a special token when necessary.  $2w+1$ be the fixed window size, $x=[x_{-w},x_{-w+1},\cdots,x_0,\cdots,x_{w-1},x_w]$ be some trigger candidate where the current token is positioned in the middle of the window.
- each token $x_i$ is transformed into a real-valued vector by looking up the following embedding tables to capture different characteristics of the token.
  - **Word Embedding Table** (initialized by some pre-trained word embeddings)
  - **Position Embedding Table**: to embed the relative distance i of the token $x_i$ to the current token $x_0$. In practice, we initialize this table randomly.
  - **Entity Type Embedding Table**: If we further know the entity mentions and their entity types in the sentence, we can also capture this information for each token by looking up the entity type embedding table (initialized randomly) using the entity type associated with each token。

#### Result

- The ACE 2005 corpus has 33 event subtypes that, along with one class “None” for the non-trigger tokens, constitutes a 34-class classification problem.

  <img src="C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\1570755979677.png" alt="1570755979677" style="zoom:150%;" />

- examine the CNNs in two scenarios: excluding the entity type embeddings (CNN1) and including the entity type embeddings (CNN2). We always use position embeddings in these two scenarios.

  ![1570756026473](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\1570756026473.png)

#### Question

> - The window size for triggers is set to 31 while the dimensionality of the position embeddings and entity type embeddings is $50^3$.
>
>   ![1570756106768](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\1570756106768.png)
>