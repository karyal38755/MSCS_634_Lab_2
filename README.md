# KNN and RNN Classifiers on the Wine Dataset 

## Purpose

This lab investigates the comparative behavior of two fundamental instance-based classifiers;
**K-Nearest Neighbors (KNN)** and **Radius Neighbors Classifier (RNN)** 
; applied to the classic Wine dataset from `sklearn`. 
Our objective was to understand how varying the hyperparameters 
(`k` for KNN and radius for RNN) affects classification accuracy, 
and to develop insights about when each method is preferable, especially under real data conditions.

## Key Insights

- **Accuracy Trends**:  
  - For **KNN**, accuracy improves from `k=1` (0.7778) to higher values (`k=5` through `k=21`), 
  stabilizing at 0.8056. This plateau suggests a performance ceiling tied to the dataset’s 
  intrinsic separability and feature scaling.  
  - For **RNN**, accuracy remains constant (0.8056) across all tested radius values (350 to 600). 
  This flat trend indicates the chosen radius range surpasses the dataset’s characteristic scales, 
  causing the classifier to behave almost uniformly regardless of radius.

- **Model Behavior and Tuning**:  
  - KNN shows sensitivity to small neighborhood sizes, which can cause overfitting at `k=1`. 
  Increasing `k` smooths the decision boundary, trading variance for bias.  
  - RNN’s lack of variation implies it is effectively “saturating” the neighborhood space, 
  highlighting the critical importance of radius tuning and feature scaling in RNN performance.

- **When to Prefer Which**:  
  - **KNN** is preferable for its robustness and guaranteed predictions, particularly when dataset 
  density varies or tuning simplicity is prioritized.  
  - **RNN** can be advantageous in domains with meaningful spatial thresholds but requires 
  careful radius calibration and is sensitive to feature scales.

## Challenges and Decisions

- **Feature Scale Considerations**:  
  The Wine dataset’s unscaled features, ranging widely in magnitude, affected RNN drastically, 
  necessitating careful radius selection. This highlighted the need for feature normalization in radius-based methods.

- **Visualization Nuances**:  
  Subtle accuracy differences required precise plotting techniques, including zoomed y-axis limits 
  and annotated points, especially in a Jupyter notebook environment inside PyCharm. Initial plots 
  lacked visibility of these differences, which we resolved by focused axis scaling and annotation.

- **Interpretation over Raw Scores**:  
  Despite relatively modest absolute accuracy (~80%), the lab emphasized understanding 
  **why** the models behaved as they did, focusing on hyperparameter sensitivity, model assumptions, 
  and dataset characteristics; embodying a graduate-level analytical mindset.


## Summary

This lab reinforced that **hyperparameter tuning is dataset- and model-specific**, and that 
understanding the underlying geometry and data distribution is essential before choosing or trusting
an algorithm. While KNN offered a simple, stable baseline, RNN's sensitivity to radius and scale serves 
as a cautionary tale on the perils of ignoring data preprocessing and domain context.
