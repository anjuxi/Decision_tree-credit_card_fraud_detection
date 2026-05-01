# 决策树-信用卡欺诈检测

信用卡欺诈是金融安全领域的重要问题。本项目通过机器学习中的决策树算法，构建了一个能够识别异常交易行为的分类模型。项目涵盖了完整的数据科学流程，包括数据探索、特征分析、模型训练、超参数优化和模型评估。

数据集地址：https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

## 数据集说明

项目使用经典的信用卡欺诈检测数据集（creditcard.csv），包含以下特征：

- **交易频率 (Time)**：距离第一笔交易的时间间隔
- **V1-V28**：通过PCA降维处理后的特征（保护用户隐私）
- **交易金额 (Amount)**：交易金额
- **类别标签 (Class)**：0表示正常交易，1表示欺诈交易

数据集特点：

- 总样本数：284,807 条交易记录
- 正常交易：284,315 条（99.83%）
- 欺诈交易：492 条（0.17%）
- 严重类别不平衡问题

## 项目结构

```
Decision_tree-credit_card_fraud_detection/
├── Decision_tree-credit_card_fraud_detection.ipynb   # 代码笔记本
└── creditcard.csv                                    # 信用卡交易数据集（已存到Releases）
```

## 主要功能

### 1. 数据探索与可视化

- 类别分布分析（正常交易 vs 欺诈交易）

- 交易金额分布对比

- 交易时间分布分析

- 特征相关性可视化（V1 vs V2 散点图）

### 2. 模型训练与优化

项目实现了三种决策树模型：

| 模型           | 特点                    | 适用场景       |
| -------------- | ----------------------- | -------------- |
| 基础决策树     | 无限制深度              | 基准对比       |
| 限制深度决策树 | max_depth=5             | 防止过拟合     |
| 类别平衡决策树 | class_weight='balanced' | 处理类别不平衡 |

### 3. 超参数调优

使用 GridSearchCV 进行网格搜索，优化参数包括：

- `max_depth`: 树的最大深度 [3, 5, 7, 10]
- `min_samples_split`: 内部节点再划分所需最小样本数 [10, 20, 50]
- `min_samples_leaf`: 叶子节点最小样本数 [5, 10, 20]
- `class_weight`: 类别权重 ['balanced', None]

### 4. 模型评估

- **准确率 (Accuracy)**
- **精确率 (Precision)**
- **召回率 (Recall)**
- **F1分数 (F1-Score)**
- **AUC-ROC 曲线**
- **混淆矩阵**
- **特征重要性分析**

## 安装与使用

1. 克隆或下载本项目

2. 确保数据集 `creditcard.csv` 位于项目根目录

3. 打开 Jupyter Notebook：

   ```bash
   jupyter notebook Decision_tree-credit_card_fraud_detection.ipynb
   ```

4. 按顺序运行所有代码单元格

## 模型结果

经过超参数优化后的最佳模型表现：

- **最佳参数组合**：根据网格搜索确定
- **AUC-ROC**：约 0.90+
- **Average Precision**：约 0.45+

决策树模型能够有效识别欺诈交易，同时保持较好的可解释性。

## 可视化输出

项目生成以下可视化图表：

1. **data_exploration.png**：数据分布和特征分析
2. **decision_tree_structure.png**：决策树结构可视化
3. **model_evaluation.png**：ROC曲线、混淆矩阵等评估指标

## 技术要点

### 处理类别不平衡

- 使用 `class_weight='balanced'` 自动调整类别权重
- 采用 PR-AUC 作为网格搜索的评分标准

### 防止过拟合

- 限制决策树最大深度
- 设置最小样本分割和叶子节点参数

### 可解释性

- 决策树模型具有良好的可解释性
- 可导出特征重要性，理解模型决策依据

## 许可证

本项目使用MIT协议开源

---

## 作者信息

**谙弆悕博士（Ailan Anjuxi）**

- 📧 邮箱：anjuxi.ME@outlook.com
- 📞 SIP电话：sip:anjuxi@sip.linphone.org

---

