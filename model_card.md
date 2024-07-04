# Model Card

For additional information, see the [Model Card paper](https://arxiv.org/pdf/1810.03993.pdf).

## Model Details
The prediction task is to determine whether a person earns over $50K annually.
We use a GradientBoostingClassifier with optimized hyperparameters in scikit-learn 1.2.0.
Hyperparameter tuning was performed using GridSearchCV.
The optimal parameters used are:
- learning_rate: 1.0
- max_depth: 5
- min_samples_split: 100
- n_estimators: 10
The model is saved as a pickle file in the model folder. All training steps and metrics are logged in the "journal.log" file.

## Intended Use
This model is designed to predict an individual's salary level based on several attributes. It is intended for students, academics, or research purposes.

## Training Data
The Census Income Dataset was sourced from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/census+income) in CSV format.
The original dataset contains 32,561 rows and 15 columns, including the target label "salary," 8 categorical features, and 6 numerical features.
Detailed feature descriptions are available at the UCI link above.
The target label "salary" has two classes ('<=50K', '>50K') and is imbalanced, with a ratio of approximately 75% to 25%.
Basic data cleansing was performed to remove leading and trailing whitespaces. See the data_cleaning.ipynb notebook for data exploration and cleansing steps.

An 80-20 split was used to divide the dataset into training and testing sets, with stratification applied to the target label "salary."
A One Hot Encoder was used for the categorical features and a label binarizer for the target.

## Evaluation Data
20% of the dataset was reserved for model evaluation.
Transformations were applied to the categorical features and target label using the One Hot Encoder and label binarizer fitted on the training set.

## Metrics
Classification performance is evaluated using precision, recall, and fbeta metrics.
The confusion matrix is also provided.

The model achieves the following scores on the test set:
- Precision: 0.759
- Recall: 0.643
- Fbeta: 0.696
- Confusion matrix:
[[4625  320]
 [ 560 1008]]


## Ethical Considerations
This dataset should not be considered a fair representation of salary distribution and should not be used to infer salary levels for specific population categories.

## Caveats and Recommendations
The data was extracted from the 1994 Census database. As an outdated sample, it is not suitable for making accurate statistical representations of the current population. It is recommended to use this dataset for training purposes in machine learning classification or related problems.
