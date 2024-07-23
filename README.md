# sparse-attention
自适应的稀疏注意力，主要方法是在第一个Transformer层近似一个低秩的注意力分数矩阵，以此为依据构造掩码矩阵

24.7.22：
### 原始的Attention效果（163M的smallGPT2，数据集为Wikitext-103，指标为困惑度）
还在跑
相同参数的论文效果：
![image](https://github.com/user-attachments/assets/13d9a690-177c-48af-86ea-f11b128ac874)

