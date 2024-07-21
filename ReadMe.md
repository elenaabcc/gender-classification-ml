# INSIGHT MEMO: Gender Classification by Contenct Activity

### WHAT WE WANT TO ACHIEVE
The goal of this project is to predict the gender (male/female) of a device_id based on the web contents they watch in their browser. 


### HOW WE GET THERE
1. **Data Collection and Preprocessing:**
   - Load the datasets `ground_truth_ml.csv` and `variables_ml.csv`.
   - Merge the datasets on the `id` column.
   - Aggregate the content watched by each device_id.
   - Preprocess the text data using TF-IDF Vectorizer with Spanish stop words.

2. **Addressing Class Imbalance:**
   - The dataset is highly imbalanced with 83% females and 17% males.
   - To handle this, we applied undersampling to the majority class (females) to balance the classes.

3. **Model Building and Evaluation:**
   - Train three models: Logistic Regression, XGBoost, and a simple Neural Network.
   - Evaluate the models based on accuracy, precision, recall, and F1 score.

### VARIABLES
- **id:** Unique identifier of a device_id (essentially a single person).
- **content:** The name of a single web content.
- **gender:** Ground truth gender of the device_id (male 'm' or female 'f').

### MODELS PROPOSED
1. **Logistic Regression:**
   - Simple and interpretable model.
   - Moderate performance but good as a baseline.
2. **XGBoost:**
   - Ensemble model known for its high performance.
   - More complex and requires tuning.
3. **Neural Network:**
   - Flexible and capable of modeling complex patterns.
   - Requires more data and computational resources.

### ISSUES: UNBALANCED CLASSES PROBLEM
The dataset had a significant imbalance with a majority of female samples (83%). 

To address this, we chose to use undersampling of the female class instead of oversampling the male class. This approach was selected to simplify the data preprocessing steps. Oversampling needs a deep unserstaanding syntheics data techniques.

### RESULTS
Logistic Regression and XGBoost offer balanced performance, while the Neural Network excels in recall, identifying more actual females at the cost of precision.


--> HOW TO READ THE RESULTS documentation -->  https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9

Accuracy: Measures the overall correctness of the model. For example, Logistic Regression has an accuracy of 59.73%, meaning it correctly predicts the gender 59.73% of the time.

Precision: Indicates the proportion of positive predictions (females) that are actually correct. For instance, XGBoost's precision of 0.5939 means that when it predicts a device ID as female, it is correct 59.39% of the time.

Recall: Measures the model's ability to identify all actual positive cases. The Neural Network's recall of 0.8078 shows it successfully identifies 80.78% of all actual females.

F1 Score: The harmonic mean of precision and recall. It provides a balance between precision and recall. For example, Logistic Regression's F1 score of 0.6459 indicates a balanced performance between identifying actual positives and minimizing false positives.


### WHAT WE CAN DO BETTER WITH MORE TIME AND RESOURCES
1. **Data Augmentation:** Instead of undersampling, explore oversampling techniques such as SMOTE to generate synthetic samples for the minority class.
2. **Hyperparameter Tuning:** Perform extensive hyperparameter tuning for models, especially XGBoost and Neural Networks, to improve performance.
3. **Feature Engineering:** Investigate additional features or more sophisticated text preprocessing techniques (e.g., word embeddings).
5. **Ensemble Methods:** Combine predictions from multiple models to create a more robust ensemble model.
6. **Cross-Validation:** Use cross-validation to ensure the stability and reliability of the model performance.
