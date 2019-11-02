# ACME Widget Failure Prediction
ACME widget failure prediction from imbalanced data

## Problem Statement

ACME, a widget manufacturer, would like to understand what causes failures of widgets and how these can be predicted or prevented in the future. They have provided some data extracted from their mainframe system. We will be developing binary classification models to predict failures of widgets and examine feature importances to identify strong predictors of failure. Our findings can help ACME accelerate quality issue investigations to develop failure prevention strategies. Through fewer warranty claims and quality recalls, ACME can benefit from reduced operating costs.

## Data
ACME has provided some data extracted from their mainframe system.

Data summary:

- **failure**: Indicate whether the widget failed (=1) or not (=0)
- **model**: Model number of the widget
- **date**: Date in yyyy-mm-dd format
- **serial_number**: Serial number of the widget
- **17 variables that begin with 'smart'**: Values extracted from the mainframe system

## Conclusion and Recommendations

### Conclusion
- Our AdaBoost classifier trained without resampling performed well in predicting widget failure with test F1 score of 0.98. We gave equal importance to precision and accuracy while tuning our model.
- Strong predictors of widget failure are *smart_5_raw*, *smart_9_raw*, *smart_18_raw* and *smart_1_raw*.

### Recommendations
- If the 17 smart values are known and collected during manufacturing, our failure prediction model can be used to augment current quality control processes and remove widgets that are likely to fail soon. During model testing, we successfully predicted 98% of failures, and 98% of all predicted failures are actual failures.
- If the 17 smart values are only known after the widgets are used, our failure prediction model can be used as an early warning system by sending user alerts if it detects that a widget may fail soon.
- Examine factors that may affect *smart_5_raw*, *smart_9_raw*, *smart_18_raw* and *smart_1_raw* values, which are strong predictors of widget failure. Develop prevention strategies that will keep these values within the norminal range for non-failures.

### Limitations
- While we believe that the smart values reported from the mainframe are comparable across widget models, ST4000DM000 is overrepresented in our dataset. It is important to test our prediction model on larger numbers of other widget models to monitor its predictive performance.
- With limited descriptions provided for the 17 explanatory variables that begin with 'smart', we did not manage to explore feature selection, feature engineering, or consider any interactions between features.
- To better understand what causes failures of widgets, it will be good to have repeated observations of functional and failed widgets over a time period. We can then examine the difference in a smart value between time T and T−1 to predict failure.
