# DATATHON 2024 by RISTEK Fasilkom UI
> competition notebook, model, and results by Rizky Indrabayu

# Competition Objective
The objective of this competition is to develop a machine learning model for detecting fraud among users of a fintech platform. Any machine learning, mathematical, and statistical methods can be used to enhance the performance of the model. In addition to developing a classification model, analytical skills are also required to identify patterns among users flagged as fraudulent, in order to explain the workings of the model being used.

# What is Fraud Detection?
Fraud detection is the process of identifying whether a user's actions in a given scenario qualify as fraudulent or not. In the context of this competition, fraudulent actions are defined as users of the platform who have taken out financial products but are recorded as not having made payments by the specified deadline.

# Technical Approach
### Data Augmentation
Due to the highly imbalanced nature of our dataset, we decided to use data augmentation techniques to improve model performance. Specifically, we employed Tabular Generative Adversarial Networks (TabGANs) to generate synthetic data that mimics the distribution of our minority class.

To determine the best approach for our needs, we benchmarked two different variants of TabGAN: the OriginalGenerator and the GANGenerator. The selection of the optimal model was based on the Receiver Operating Characteristic Area Under the Curve (ROC-AUC) values, which measure the ability of the model to distinguish between classes. After evaluating both methods, the OriginalGenerator was chosen as it provided the highest ROC-AUC score, indicating better performance in balancing the dataset and improving model accuracy.
### Feature Engineering & Buillding Graph 
To effectively utilize the data from multiple files, we employed a graph-based approach for feature engineering and data preparation. Using NetworkX, a Python library for the creation, manipulation, and study of complex networks, we constructed a graph dataset that connects the different entities within our data.
### Machine Learning Model
For our analysis, we selected three machine learning approaches to evaluate their performance on our tabular dataset. These include one traditional machine learning model and two gradient boosting models:

1. Random Forest: A traditional ensemble learning method that constructs multiple decision trees during training and outputs the mode of the classes (classification) or mean prediction (regression) of the individual trees. Random Forest is known for its simplicity and effectiveness on a variety of datasets, making it a strong baseline model.

2. XGBoost (Extreme Gradient Boosting): A powerful and efficient implementation of gradient boosted decision trees designed for speed and performance. XGBoost is highly effective for a wide range of predictive modeling tasks, particularly when dealing with structured or tabular data. It provides several hyperparameters that allow fine-tuning to enhance model accuracy and performance.

3. LightGBM (Light Gradient Boosting Machine): Another gradient boosting framework that uses tree-based learning algorithms. LightGBM is optimized for faster training and lower memory usage, and it handles large-scale data efficiently. It is especially well-suited for handling categorical features and large datasets.

# Evaluation Metric
The model's performance is evaluated using the Average Precision metric with `average='macro'`. Formally, the Average Precision metric is defined as:

### AP=∑𝑖(𝑅𝑒𝑐𝑎𝑙𝑙𝑖−𝑅𝑒𝑐𝑎𝑙𝑙𝑖−1)𝑃𝑟𝑒𝑐𝑖𝑠𝑖𝑜𝑛𝑖

The implementation of this metric in Python using the Scikit-Learn library is as follows.

# Performance Results
### Leaderboard Rank: 99 of 223 teams on Kaggle
## 1. Random Forest

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.93      | 0.76   | 0.84     | 4348    |
| 1     | 0.80      | 0.94   | 0.86     | 4310    |
| **Accuracy** | **-**   | **-**   | **0.85** | **8658** |
| **Macro Avg** | **0.86** | **0.85** | **0.85** | **8658** |
| **Weighted Avg** | **0.86** | **0.85** | **0.85** | **8658** |

## 2. XGBoost

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.67      | 0.83   | 0.74     | 3516    |
| 1     | 0.86      | 0.72   | 0.79     | 5142    |
| **Accuracy** | **-**   | **-**   | **0.77** | **8658** |
| **Macro Avg** | **0.77** | **0.78** | **0.76** | **8658** |
| **Weighted Avg** | **0.78** | **0.77** | **0.77** | **8658** |

## 3. LightGBM

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.65      | 0.77   | 0.71     | 3681    |
| 1     | 0.80      | 0.70   | 0.75     | 4977    |
| **Accuracy** | **-**   | **-**   | **0.73** | **8658** |
| **Macro Avg** | **0.73** | **0.73** | **0.73** | **8658** |
| **Weighted Avg** | **0.74** | **0.73** | **0.73** | **8658** |

# References

```bibtex
@misc{djuliansah2024,
   author = {Alwin Djuliansah, Anders Willard Leo, Belati Jagad Bintang Syuhada, Darren Aldrich, Ghana Ahmada Yudistira},
   title = {RISTEK Datathon 2024},
   year = {2024},
   publisher = {Kaggle},
   url = {https://kaggle.com/competitions ristek-datathon-2024}
}

@article{huang2023,
   author = {Huang, X., Yang, Y., Wang, Y., Wang, C., Zhang, Z., Xu, J., Chen, L., & Vazirgiannis, M.},
   title = {DGraph: A Large-Scale Financial Dataset for Graph Anomaly Detection},
   year = {2023},
   journal = {arXiv},
   url = {https://arxiv.org/abs/2207.03579}
}
