# 文献阅读总结与研究方向汇报

## 序列推荐

### 1. [Dynamic Stage-aware User Interest Learning for Heterogeneous Sequential Recommendation](https://dl.acm.org/doi/pdf/10.1145/3640457.3688103)
- **作者/单位**: Shenzhen University  
- **关键词**: 序列推荐, 异质行为, 动态图, 阶段兴趣学习  
- **研究问题/目标**: 捕捉用户动态兴趣和异质性行为。
- **核心模型/方法**: 将用户的异质序列划分为若干子序列，构建阶段性用户兴趣的子图；设计动态图卷积模块以跨阶段方式学习项目表示；行为感知子图表示学习模块来表示用户在特定阶段的兴趣；通过自注意力模块提取用户的兴趣演化模式。  
- **创新点**: 动态图卷积跨阶段学习用户兴趣。

## 多模态推荐

### 1. [A Multimodal Single-Branch Embedding Network for Recommendation in Cold-Start and Missing Modality Scenarios](https://dl.acm.org/doi/pdf/10.1145/3640457.3688138)
- **作者/单位**: Johannes Kepler University Linz  
- **关键词**: 冷启动推荐, 缺失模态, 多模态单分支embedding  
- **研究问题/目标**: 解决推荐系统在冷启动和缺失模态场景中的表现。
- **核心模型/方法**: 提出Single-Branch embedding network for Recommendation (SiBraR)，通过权重共享，在不同模态上使用单一分支embedding网络。  
- **创新点**: 不同模态间共享embedding空间，提升冷启动表现。
- **不足之处**: 未考虑模态扩展性。

## 工业优化

### 1. [Embedding Optimization for Training Large-scale Deep Learning Recommendation Systems with EMBark](https://dl.acm.org/doi/pdf/10.1145/3640457.3688111)
- **作者/单位**: Nvidia  
- **关键词**: embedding优化, 大规模训练数据, 吞吐量提升  
- **研究问题/目标**: 提升大规模推荐系统模型训练中embedding部分的吞吐量。
- **核心模型/方法**: EMBark使用一个3D元组（i, j, k）表示每个分片，允许每个embedding table跨任意数量的GPU进行分片；通过自动分片规划器（一个成本驱动的贪婪搜索算法），正式训练前将不同的embedding table分类到不同的cluster。  
- **创新点**: 提前分类embedding table，优化资源利用。  
- **不足之处**: 不适用于流式数据集，复杂交互支持有限。

## 协同过滤与大语言模型

### 1. [FLIP: Fine-grained Alignment between ID-based Models and Pretrained Language Models for CTR Prediction](https://arxiv.org/html/2310.19453v4)
- **作者/单位**: Shanghai Jiaotong University  
- **关键词**: PLM, ID模型, 特征对齐  
- **研究问题/目标**: 提升CTR预测能力，融合ID和文本特征。
- **核心模型/方法**: 提出FLIP框架，利用ID模型和PLM模型进行细粒度的特征对齐；通过MLM任务（tabular data恢复masked text data）和MTM任务（cross attention模块与NCE损失函数建模tabular数据恢复）联合建模；使用InfoNCE进行实例级对比学习。  
- **创新点**: 提出通用框架，实现ID与PLM特征对齐。

## 跨域推荐

### 1. [Cross-Domain Latent Factors Sharing via Implicit Matrix Factorization](https://arxiv.org/pdf/2409.15568)
- **作者/单位**: Skolkovo Institute of Science and Technology  
- **关键词**: 跨域推荐, 协同过滤, ADMM, CDIMF  
- **研究问题/目标**: 解决跨域推荐的冷启动和暖启动问题。
- **核心模型/方法**: 使用基于ALS的矩阵分解方法，提出CDIMF，通过对重叠用户的隐含因子施加一致性约束（全局变量，局部更新与全局聚合），实现信息共享，从而捕捉不同领域之间的潜在关联。  
- **创新点**: 使用ADMM求解优化，支持分布式计算，保留数据隐私。  
- **不足之处**: 探讨了user-overlap场景，未来可探索item-overlap场景。

### 2. [A Pre-trained Zero-shot Sequential Recommendation Framework via Popularity Dynamics](https://arxiv.org/abs/2401.01497)
- **作者/单位**: UIUC  
- **关键词**: 跨域推荐, 序列推荐, zero-shot/预训练, transformer  
- **研究问题/目标**: 实现无需辅助信息的零样本跨域迁移。
- **核心模型/方法**: PrepRec，通过流行度动态生成item embedding，进行跨域迁移；不直接使用item ID或辅助信息，而是通过长短期流行度动态（即流行度变化趋势）生成item embedding；模型能够在不同领域中迁移，解决跨领域推荐中的数据不一致性问题。  
- **创新点**: 专注流行度动态，解决数据不一致问题。
- **不足之处**: 实验显示单独使用PrepRec效果有限，需要与其他模型插值优化。

### 3. [Discerning Canonical User Representation for Cross-Domain Recommendation](https://dl.acm.org/doi/fullHtml/10.1145/3640457.3688114)
- **作者/单位**: University at Albany - SUNY, USA  
- **关键词**: 跨域推荐, CCA, 协同过滤, GAN  
- **研究问题/目标**: 提升跨域推荐效果，通过区分领域间共享与特定信息。
- **核心模型/方法**: 提出DisCCA学习方法，分别对两个域的全局和共享部分进行建模；通过GCCA和GAN结合优化跨域相似性与域内差异性；增强对用户反馈分布的学习能力，提高模型泛化能力。  
- **创新点**: 提出新用户表示学习方法，提升模型泛化能力。

## 总结与提问

### 2024 Recsys热点方向总结
1. 跨域推荐的冷启动问题，尤其是如何有效建模用户共享特征。
2. 序列推荐中的异质性行为建模和动态兴趣挖掘。
3. 多模态推荐系统中的缺失模态场景与冷启动。
4. 工业优化背景下embedding表分片与吞吐量提升。
5. 协同过滤和预训练大语言模型的深度结合。

### 问题
1. 请问老师如何看待2025年推荐系统研究可能的热点方向？
2. 在跨域推荐、序列推荐、多模态、工业优化、大语言模型结合这五大方向中，您认为我们应优先深挖哪个？
3. 您对我们后续研究是否有具体建议，尤其是在选题、数据集选择或实现细节方面？