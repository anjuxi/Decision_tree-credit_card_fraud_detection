# Credit Card Fraud Detection with Decision Trees

Credit card fraud is a major problem in financial security. This project uses decision trees to build a classifier that flags abnormal transactions. It covers the full data science workflow: data exploration, feature analysis, model training, hyperparameter tuning, and evaluation.

Dataset: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

## Dataset

The project uses the classic credit card fraud dataset (`creditcard.csv`). Features:

- **Time** — seconds elapsed since the first transaction
- **V1–V28** — features produced by PCA (anonymized to protect user privacy)
- **Amount** — transaction amount
- **Class** — label: 0 for normal, 1 for fraud

Dataset characteristics:

- Total: 284,807 transactions
- Normal: 284,315 (99.83%)
- Fraud: 492 (0.17%)
- Severe class imbalance

## Project Structure

```
Decision_tree-credit_card_fraud_detection/
├── Decision_tree-credit_card_fraud_detection.ipynb   # notebook
└── creditcard.csv                                    # dataset (stored in Releases)
```

## Main Features

### 1. Data Exploration and Visualization

- Class distribution (normal vs. fraud)
- Transaction amount distribution comparison
- Transaction time distribution
- Feature correlation visualization (V1 vs. V2 scatter plot)

### 2. Model Training and Tuning

Three decision tree models are trained:

| Model | Characteristics | Use case |
| -------------- | ----------------------- | -------------- |
| Baseline decision tree | unlimited depth | baseline comparison |
| Depth-limited decision tree | max_depth=5 | prevent overfitting |
| Class-balanced decision tree | class_weight='balanced' | handle class imbalance |

### 3. Hyperparameter Tuning

GridSearchCV is used to search over:

- `max_depth`: maximum tree depth [3, 5, 7, 10]
- `min_samples_split`: minimum samples required to split an internal node [10, 20, 50]
- `min_samples_leaf`: minimum samples per leaf [5, 10, 20]
- `class_weight`: class weights ['balanced', None]

### 4. Evaluation

- Accuracy
- Precision
- Recall
- F1 score
- AUC-ROC
- Confusion matrix
- Feature importance

## Install and Use

1. Clone or download the project.
2. Make sure `creditcard.csv` is in the project root.
3. Open the notebook:

   ```bash
   jupyter notebook Decision_tree-credit_card_fraud_detection.ipynb
   ```

4. Run all cells in order.

## Results

Performance of the tuned model:

- **Best parameters**: determined by grid search
- **AUC-ROC**: about 0.90+
- **Average Precision**: about 0.45+

The decision tree model can catch fraudulent transactions reasonably well while staying interpretable.

## Visualization Output

The project produces:

1. **data_exploration.png** — data distribution and feature analysis
2. **decision_tree_structure.png** — decision tree structure
3. **model_evaluation.png** — ROC curve, confusion matrix, and other evaluation metrics

## Technical Notes

### Handling Class Imbalance

- `class_weight='balanced'` adjusts class weights automatically
- PR-AUC is used as the scoring metric for grid search

### Preventing Overfitting

- Limit the maximum tree depth
- Set minimum samples for splits and leaves

### Interpretability

- Decision trees are interpretable
- Feature importance can be exported to understand the model's decisions

## License

MIT

---

## Author

**Dr. Ailan Anjuxi (谙弆悕)**

- Email: anjuxi.ME@outlook.com
- SIP: sip:anjuxi@sip.linphone.org

---
