# DSCI521 Breast Cancer Wisconsin: Data Analysis & Interpretation

## Team Members

* Mattock Callahan (mc4366@drexel.edu)
* Ifeanyi Osuchukwu (imo27@drexel.edu)
* Himanshu Vijay Rathod (hr399@drexel.edu)
* Nawaf Alhumaid (nka39@drexel.edu)

## Introduction

For our final project, we sought to analyze a dataset related to medicine, a common area of interest within our group. The dataset we selected was the Breast Cancer Wisconsin Diagnostic Data Set (link: https://bit.ly/3Kyp8ta). Available since 1995, this dataset was constructed by 3 researchers from the University of Wisconsin, and has been cited in more than 30 papers since its original release. The dataset features observations collected from "a digitized image of a fine needle aspirate (FNA) of a breast mass," and describes "the cell nuclei present in the image." The dataset was created in order to study the visual characteristics of malignant and benign tumors. We believe that this dataset will provide us with a great opportunity to develop and hone our prediction and classification skills. Our ultimate goals were to 1) determine which features are most indicative of cancerous growth and 2) construct a tool that can predict whether a mass is cancerous based on input data.

This project includes:
* notebook.ipynb: Our core notebook
* data.csv: Our dataset
* dictionary.xlsx: A data dictionary explaining the dataset features



## Key Audiences

* Medical Professionals & Institutions
* Medical Technology Firms

## Requirements

* matplotlib          3.5.1
* numpy               1.22.0
* pandas              1.3.5
* seaborn             0.11.2
* sklearn             1.0.2
* IPython             7.30.1
* jupyter_client      7.1.0
* jupyter_core        4.9.1
* jupyterlab          3.2.5
* notebook            6.4.6

## Functions 
* run_classifier: This function returns a classification and confusion matrix for a given classification model. This function accepts a classifier, training and testing datat as parameters. 
* correlated: This function returns attributes that are correlated more than a given a threshold.
* feature_importance: 
## Approach

1. Data Intake
2. Standardization
3. Visualization + EDA
4. Hypothesis Formulation
5. Classification Pre-Processing
    * Drop Correlated Features
    * Train/Test Split
    * Principal Component Analysis (PCA)
6. Classification Modeling
    * Logistic Regression
    * Random Forest
    * Gradient Boosting
    * KNeighbors
7. Measure & Compare Outcomes
    * Determine Feature Importance
    * Compare Precision, Recall, F1
    * Perform Cross-Validation
    * Compare PCA Results vs. Non-PCA Results
    
## Analysis of Results

Based on our initial exploratory data analysis, we anticipated that 1) our dataset would respond well to classification modeling and that 2) the concave_points feature group would be an important indicator. Ultimately, our intuitions were at least partially validated, but we were suprised by some of the results as well. 

Given the nature of our data, the classification performance statistic that we were most concerned with was recall. As a life-threatening disease, we did not want to overlook any possible cancer diagnoses. Although all the classification models we used produced good results, we believe that logistic regression produced the best overall results with a 98% recall score and a 98% precision score. Our cross-validation results were also promising, producing 97% accuracy with a standard deviation of ~1%, mitigating immediate concerns about over-fitting. 

We also re-ran our classification models on a dataset where we applied principal component analysis (PCA). Since PCA is a popular technique, our goal was to see how the classification results changed (if at all) with PCA applied. After discussions with our professor, we understood that PCA's effect on modeling performance may not be noticeable in all cases, and can depened on the nature of the data, as well as the hyperparameter setting. Dimensionality reduction is often required when the dataset's columns outnumber the dataset's rows. In our case, we did not notice a large difference when running our classification models on PCA and non-PCA data, and we believe this is due to the size and structure of our dataset. However, we did notice a signifcant dip in the predictive performance of our PCA classifiers when we first removed correlated features, and then subsequently applied PCA to the data. For this reason, we chose not to remove correlated features from our PCA dataset. We look forward to continuing to explore PCA in other contexts.

Our final goal was to determine which features were most important to the classification modeling. After testing various techniques, we settled on an approach where we ran each feature group (i.e. radius, concave_points) through the model by itself, and then compared the performance scores to how the model performed with all feature groups included. With this technique applied, the radius feature group lead the way, surrendering only ~7% in terms of recall. Overall, it seemed that concavity and measures of size (i.e. radius) were the most important indicators of malignancy. On the other hand, feature groups like symmetry and smoothness seemed to contribute significantly less to the model's classification performance. 

## Future Enhancements

* Add a patient "age" feature to the dataset
* Expand the number of observations
* Build towards an "unsupervised" learning model
* Utilize a data collection technique that is less invasive than FNA

## Conclusion

We believe that this particular project offered us a great opportunity to develop our data analysis and interpretation skills in a significant way. We were forced to explore new tools and techniques, while working as a team to evaluate data with real-world importance. We believe this project has given us the skills and confidence to work on similar projects in the future.
