# macs30100_project1_Violet Huang_April Wang_Zenthia Song

Customer Segmentation Classification project for MACS 30100

## Task:
We aim to train a multi-class classification model to divide new customers into existing segments (A, B, C, D)  for a automobile company to predict the potential groups of new customers.

## Data:
  1) Target Variable: Segmentation
        - trainng: 1867 A, 1779 B, 1896C, 2127 D
        - testing: 794 A, 523 B, 445 C, 726 D
        - Number of feature variables: 9
  2) Type of feature variables
        - Categorical: Gender, Ever_Married, Graduated, Profession, Spending_Score, Var_1
        - Numerical: Age, Work_Experience, Family_Size
  3) Preprocessing steps
        - Dropping the ID column because unique identifiers cannot function to categorize samples
  4) Dealing with missing values
        - For numerical data type: replacing missing value with mean
        - For categorical data type: dropping them
  5) Doing label encoding and one hot encoding
        - Segmentation is our ground truth; use binary 0 and 1 to represent Gender, Ever_Married, Graduated; use one hot encoding to represent 
        - Profession and Var1; use ordinal encoding to represent Spending_Score
  6) Droppping outliers based on lower/upper thresholds from boxplot calculation and magnitude comparison
  7) Normalizing numerical data
  8) Checking for Collinearity based on heatmap
 
## Model:
  1) Logistic Regression (solver='newton-cg', random_state=42) Accuracy = 32.4%
  2) Random Forest (n_estimators=200, criterion="entropy", max_depth=5, random_state=42) Accuracy = 33.9%
  3) Decision Tree (criterion='gini', random_state=42, min_samples_leaf=90, max_step=6) Accuracy = 34.5%
  4) K Neighbors (radius=1.44) Accuracy = 32.5%
  
## Result analysis:
  * The model with higher accuracy is Decision Tree because there are a large number of category features in the feature. 
  * On the whole, the accuracy of the four models are not high. Potential reasons:
     - Lack of data: the amount of data may not capture the complexity of the problem
     - Solution: acquiring more data of the characteristics of old customers
     - Non-representative data: the newly acquired customers may behave inherently different from the old customers
     -  Solution: using labeled new customer data to predict unlabeled new customer data
     - Irrelevant Features: We may selected irrelevant features. For Decision Tree model, most of our features have importances smaller than 0.1
     -  Solution: Filter out unimportant features. Add other dimension to the data set if possible
     - Algorithm Selection Issue: The choice of four algorithms may also impact the accuracy of the model. Specifically, some more complex/advanced
     algorithms may be better suited this multi-class classification problem.
     -  Solution: Deep learning, Naive Bayes
