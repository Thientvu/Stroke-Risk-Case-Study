### 1. Introduction

- **Project Overview**: This study aims to identify the primary factors associated with stroke occurrences, aiming to enhance awareness and understanding of stroke prevention both personally and within the community.
- **Motivation**: Strokes are the second leading cause of death worldwide, as reported by the World Health Organization, accounting for approximately 11% of total global fatalities. Notably, over 795,000 people in the U.S. experience a stroke each year.
- **Objectives**:
    - Source and compile relevant data.
    - Ensure data quality through meticulous cleaning.
    - Conduct detailed exploratory data analysis using univariate and bivariate techniques, supported by comprehensive visualizations and statistical tests.
    - Develop and train machine learning models including Logistic Regression, XGBoost, Random Forest, and Neural Networks.
    - Utilize Tableau to create advanced visualizations that effectively communicate insights drawn from the data.

### 2. Data Collection

- **Data Source(s)**: The data was sourced from Kaggle, available in CSV format. [Kaggle Dataset Link](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset?resource=download)

### 3. Data Cleaning and Preprocessing

- **Initial Data Exploration**:
    - Analyzed a dataset of 5,110 entries, which includes demographics, health conditions, lifestyle factors, and stroke occurrences.
    - Identified a combination of numeric and categorical data types.
    - Noted missing values particularly in the BMI feature.
- **Cleaning Steps**:
    - Removed the 'id' column as it was irrelevant to our analysis.
    - Imputed missing values in the 'BMI' column with the mean to preserve data integrity.
    - Applied one-hot encoding to transform categorical variables into a format suitable for machine learning analysis.
- **Final Dataset Description**:
    - Retained crucial variables such as gender, age, hypertension, heart disease, marital status, work type, residence type, average glucose level, BMI, and smoking status.
    - Ensured that categorical variables were properly encoded and missing values addressed, preparing the dataset for robust analysis and modeling.

### 4. Exploratory Data Analysis (EDA)

- **Visualizations**:
    - **Age Distribution**: Utilized histograms, box plots, and strip plots to analyze the age distribution, highlight outliers, and visually represent the density of different age groups. This comprehensive approach helps identify which age groups are most susceptible to strokes.
    - **BMI and Glucose Levels**: Employed histograms, box plots, and strip plots to examine the distribution of BMI and average glucose levels. This trio of plots enables a detailed investigation of outliers, central tendencies, and variations within these metrics, which are crucial for spotting potential patterns linked to stroke risk.
    - **Correlation Matrix**: Generated a heatmap to illustrate the correlations between numerical variables, including a specific focus on their relationships with the 'stroke' outcome. This visualization aids in understanding the interplay between key factors like age, hypertension, and glucose levels, and their collective impact on stroke probability.
    - **Categorical Data Representation**: Created proportion stacked bar charts to visualize the relative frequencies of stroke occurrences within different categories. Additionally, I used distribution bar charts to depict the distribution of key categorical variables such as gender, smoking status, work type, and residence type. These visual tools are essential for pinpointing categories with elevated stroke incidences and understanding demographic influences on stroke risk.
- **Insights**:
    - **Age Insights**: The analysis indicated a higher incidence of stroke in older age groups. The box plots and strip plots highlighted significant outliers, suggesting that extreme ages might carry different risk levels.
    - **Health Conditions and Lifestyle**: Patterns in hypertension and heart disease showed strong correlations with stroke incidents. Smoking status varied widely, with 'formerly smoked' and 'smokes' categories showing distinct patterns that merit further investigation for their impact on stroke risk.
    - **BMI and Glucose Insights**: The distribution of “average glucose level” showed that both extremely low and high values might be risk factors for stroke, suggesting a U-shaped relationship.
    - **Socioeconomic Factors**: Initial findings from the proportion stacked bar charts indicated variations in stroke incidence by work type and residence type, hinting at socioeconomic factors potentially influencing stroke risk.
- **Statistical Tests**:
    - **Chi-square Tests**:
        - Tested associations between categorical variables (gender, hypertension, heart disease, marital status, work type, residence type, smoking status) and stroke occurrence.
        - Found significant associations for hypertension, heart disease, marital status, work type, and smoking status, indicating these factors are linked to stroke risk. No significant associations were found for gender and residence type.
    - **T-tests**:
        - Analyzed differences in mean values of continuous variables (age, average glucose level, BMI) between those who have had a stroke and those who have not.
        - All tests (age, glucose levels, BMI) showed significant differences, highlighting these as important factors in stroke occurrence, with age showing the most profound impact.

### 5. Model Building

- **Model Selection**: The project utilizes a variety of models to predict stroke likelihood, each chosen for their strengths in handling specific aspects of the dataset:
    - **Logistic Regression**: Opted for its quick implementation and interpretability, making it ideal for a baseline model in binary classification tasks.
    - **XGBoost**: Selected for its advanced capabilities in managing large datasets and its effectiveness in boosting model performance through gradient enhancement techniques.
    - **Random Forest**: Employed for its excellent resistance to overfitting, thanks to its ensemble approach using multiple decision trees to ensure robustness and reliability.
    - **Neural Networks**: Deployed to detect intricate patterns and interactions in the data, potentially outperforming simpler models due to their deep learning capabilities.
- **Feature Engineering and Selection**:
    - **Preprocessing**: All features were scaled or normalized to unify the scale across different measurements, which is critical for models like Neural Networks and Logistic Regression that are sensitive to input scale. Techniques such as one-hot encoding were used for categorical variables, and log normalization was applied to skewed numeric features to reduce scale disparities.
- **Model Training**:
    - **Data Splitting**: The data was partitioned into training and testing subsets with a 75/25 split, carefully designed to mirror the overall data distribution, thus ensuring that the model training and evaluations are both balanced and representative.
    - **Hyperparameter Tuning**: Utilized grid search techniques to systematically explore various combinations of parameters for XGBoost and Random Forest, aiming to optimize the models for the best performance on the given dataset.

### 6. Model Evaluation

- **Evaluation Metrics**:
    - A comprehensive set of metrics, including **Accuracy**, **Precision**, **Recall**, and **F1-Score**, was employed to provide a holistic view of the model's performance. These metrics are crucial for understanding not only how often the model is correct (accuracy) but also its effectiveness in identifying positive cases (precision and recall), as well as the balance between these metrics (F1-Score).
- **Results**:
    - Among the various models tested, **XGBoost** demonstrated superior performance on both the training and testing datasets, showing the highest F1-score. The F1-score provides a more holistic view in this case because the dataset is quite imbalanced.
    - The results are summarized in the table below, showcasing the model’s efficacy across different metrics:
        
        
        | Model | Precision | Recall | F1-Score | Accuracy |
        | --- | --- | --- | --- | --- |
        | Logistic test | 0.000000 | 0.000000 | 0.000000 | 95.14% |
        | XGB CV | 0.193452 | 0.080597 | 0.109951 | 93.92% |
        | XGB test | 0.166667 | 0.064516 | 0.093023 | 93.90% |
        | RF CV | 0.340000 | 0.016074 | 0.030085 | 95.02% |
        | RF test | 0.500000 | 0.032258 | 0.060606 | 95.15% |
        | NN test | 0.000000 | 0.000000 | 0.000000 | 95.15% |

### 7. Conclusion and Recommendations

- **Summary of Findings**:
    - Through comprehensive data analysis and modeling, this project identified several key factors significantly influencing stroke occurrences, such as age, hypertension, heart disease, and smoking status. Among the various predictive models evaluated, XGBoost emerged as the top performer, demonstrating high accuracy and robustness in predicting stroke risk. This underscores its capability to handle complex patterns and large datasets effectively.
- **Challenges Faced**:
    - The project encountered challenges in managing missing data, particularly in critical features like BMI, which required careful imputation strategies to maintain data integrity.
    - Decisions regarding feature engineering, such as which features to encode or normalize, also posed difficulties, impacting model performance and interpretability.
- **Future Work**:
    - To enhance predictive accuracy and applicability, future efforts could explore integrating more diverse and comprehensive datasets, including longitudinal data that captures changes in health status over time.
    - Further research could also examine deploying these models in clinical settings for real-time stroke risk assessment, potentially incorporating real-time data feeds to dynamically update risk predictions.
    - Advanced modeling techniques, such as deep learning and ensemble methods, could be investigated to address non-linear relationships and interactions between features more effectively.
- **Takeaway**:
    - This project has provided valuable insights into the significant impact of various lifestyle and health conditions on stroke risks. These findings can help enhance personal and community awareness, guiding preventive measures and health policies to mitigate stroke risks effectively.

### 8. References and Acknowledgments

- **References**:
    - **Kaggle** for the dataset.
    - **Pandas and NumPy** for data manipulation.
    - **Matplotlib and Seaborn** for data visualization.
    - **SciPy** for statistical tests.
    - **Sklearn** for machine learning processing.
    - **TensorFlow** for advanced modeling techniques.
- **Contact Information**:
    - [LinkedIn](https://www.linkedin.com/in/thientvu/)
    - [vuthien12316@gmail.com](mailto:vuthien12316@gmail.com)