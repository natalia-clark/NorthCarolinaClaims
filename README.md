# Health Insurance Claims Analysis for North Carolina (2018-2020)
Daniil Kim, Natalia Clark, Antonia Murad Pim, Marnix Van der Stighelen and Philip Dias Santilhano

## Files and Descriptions 
- Final demand prediction notebook:
- Final segmentation clustering notebook:
- Dataset:
- Dictionary of grouping of healthcare specializations supporting demand analysis:
- final model pickle:
- 

## Summary

### Technical Objectives
From a technical perspective, two separate models were developed to meet the project objectives:
1. **Predictive Model**: To forecast the total number of insurance claims per provider during the next quarter (Q1 2021).
2. **Segmentation Model**: To segment the healthcare providers in North Carolina according to their descriptive characteristics.

## Data

### Data Sources
The primary data for this project was provided by the state of North Carolina and pertains to health insurance claims within the state. This dataset encompasses data from the years 2018 to 2020, including detailed records of insurance claims by type, provider information, and various health center-level variables. The dataset is structured in a long format with 85,436 rows and 117 columns, where rows are uniquely identified by provider ID, year, and quarter.

## Methodology

### CRISP-DM Framework
We used the CRISP-DM (Cross-Industry Standard Process for Data Mining) framework to guide our project, ensuring a structured approach from problem understanding to model deployment. We tailored our analysis to the business understanding, data understanding, and data preparation phases before entering the modeling phase.

## Modeling

### Predictive Analysis
For predictive analysis, we considered three different models: Linear Regression, Random Forest, and XGBoost.

- **Linear Regression**: A fundamental supervised machine learning technique used for predicting a continuous target variable based on one or more predictor variables. Linear Regression is valued for its simplicity and interpretability, making it suitable for exploration within a business context.
- **Random Forest**: Constructs multiple decision trees during training and outputs the average prediction of the individual trees for regression. Known for its high accuracy, ability to handle large datasets with higher dimensionality, and its effectiveness in capturing complex interactions between features.
- **Gradient Boosting Machines (XGBoost)**: Builds an ensemble of trees sequentially, where each new tree corrects the errors of the previous trees. GBMs are highly effective at capturing complex patterns in data and often outperform other models in predictive accuracy.

### Clustering Techniques
Clustering or segmentation aims to explore and reveal natural and meaningful groups based on multivariate input. Our goal was to develop meaningful, well-defined, and distinct clusters of healthcare providers in North Carolina based on a range of descriptive features. We experimented with three unsupervised learning algorithms:

- **K-Means**: Partitions a dataset into K distinct, non-overlapping clusters. Known for its efficiency and scalability, making it suitable for large datasets, although the choice of K and the initial centroids can significantly influence the outcome.
- **Agglomerative Clustering**: A hierarchical bottom-up method that builds clusters by repeatedly merging observations based on their distance to each other. Unlike K-Means, it does not require the number of clusters to be specified upfront and can provide an intuitive understanding of the data's structure through dendrograms.
- **DBSCAN**: Particularly effective for datasets with noise and varying density. It aims to uncover natural clusters in the data based on the density of data points, allocating outliers to a specified noise cluster.

### Final Prediction of Demand

#### Model Selection and Training

**Linear Regression**:
   - **Initial Models**: Built with different feature combinations, including Lasso regularization.
   - **Laboratories Group**: High claim values impacted error metrics. Models were compared with and without this group.
   - **Assumptions**: Lasso addressed multicollinearity; Durbin-Watson test confirmed independence. Residual analysis suggested slight violations of homoscedasticity and normality.

**Final Model Selection - Linear Regression using Lasso Regularization**:
   - **Regularization**: Alpha parameter tuned to 1.42.
   - **Performance**: No significant overfitting; linear model chosen for interpretability and performance.
   - **Feature Selection**: Included features with non-zero Lasso coefficients and logical relevance.

### Segmenting Supply

1. **Clustering Algorithms**:
   - **K-Means**: Identified as optimal for creating well-defined, meaningful clusters.

2. **K-Means Configuration**:
   - **Optimal Clusters**: Determined via elbow plot and silhouette scores; five clusters deemed optimal.
   - **Initialization**: Consistent results across multiple runs.

3. **Evaluation Metrics**:
   - **Inertia and Silhouette Score**: Evaluated within-cluster variance and separation.
   - **Random Forest Classifier**: Achieved 98.1% accuracy in predicting clusters, indicating clear characterization.
   - **Adjusted Rand Index**: High ARI (0.96) confirmed clustering robustness.

4. **Cluster Characterization**:
   - **Feature Importance**: Percentage splits of patient types, infrastructure, and business status were key.
   - **Heat Map**: Illustrated mean feature values per cluster.

## Evaluation

Models were evaluated using cross-validation and metrics such as R², MSE, and RMSE for supervised models. For unsupervised models, inertia, silhouette, the Adjusted Rand Index, and a Random Forest predictor model were examined. Error analysis was integral to our approach, evaluating model performance across different segments. We analyzed the ratio of average error to average actual values by clusters, specialization groups, and counties, and used it to adjust our predictions for the new quarter (Q1 2021).

### Project Outcomes
- **Predictive Analysis**: Enabled accurate forecasting of insurance claims, aiding in resource allocation and strategic planning.
- **Segmentation Analysis**: Provided insights into distinct groups of healthcare providers, facilitating targeted interventions and policy-making.

## References
- [CRISP-DM Framework](https://www.the-modeling-agency.com/crisp-dm.pdf)
- [Kaiser Family Foundation (KFF)](https://www.kff.org)
- [Insurance Information Institute (III)](https://www.iii.org)
- [National Association of Insurance Commissioners (NAIC)](https://www.naic.org)
- [Centers for Medicare & Medicaid Services (CMS)](https://www.cms.gov)


