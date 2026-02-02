
# Campaign Analysis

[Project URL](https://github.com/rgadicharla/MLPortfolio/blob/main/Campaign/prompt_III.ipynb)

## Business Problem
In this project, the goal is to evaluate multiple machine learning models to determine which one best predicts the target outcome. It allows the business to identify high-value or high-risk individuals early and take targeted action.

This way, the marketing team can focus their efforts on customers most likely to respond, reducing wasted outreach and improving overall campaign performance. This will reduce missed opportunities for likely engaging customers.

## Findings

### 1. SVM was the strongest overall performer
The SVM model achieved the highest AUC score (for example: 0.94), meaning it was the most effective at distinguishing between positive and negative cases. But it was significantly slow to train compared to other models.
- Example: When ranking customers by likelihood of responding, SVM placed the true responders at the top of the list more consistently than any other model.
- This allows the business to focus outreach on the customers most likely to say "yes," reducing wasted calls.

### 2. Logistic Regression performed consistently and was highly interpretable
Logistic Regression produced a strong AUC (e.g., 0.89) and similar train/test accuracy values, showing good generalization.
- Example: If the model predicted a customer had a 70% chance of responding, that probability aligned well with actual outcomes.
- Managers can understand which features increase or decrease the likelihood of a positive response, making this model useful for strategic planning.

### 3. Decision Tree showed clear signs of overfitting
The Decision Tree achieved very high training accuracy (e.g., 0.99) but much lower test accuracy (e.g., 0.78).

### 4. KNN delivered moderate performance and was sensitive to scaling
KNN produced mid-range AUC values (e.g., 0.85) and took longer to make predictions because it compares each new customer to all training examples.
KNN can work well but requires significant preprocessing and is less efficient for large datasets.

## Recommendations
Even without call duration, several features still showed strong relationships with the target:
- Whether or not the customer is employed played a big role in identifying likelihood to convert
- Month of contact: Certain months (e.g., March, June, September, December) were associated with higher success rates.
- Number of previous contacts: Customers who had been contacted before were more likely to respond.
- Days since last contact: Very recent or very old contacts tended to have lower success rates, while moderate intervals performed better.
- Previous campaign outcome: Customers who responded positively in a prior campaign were more likely to respond again.

### Recommendations when using the models
1. Use SVM for identifying the target customers
2. Use logistic regression to identify important features that affect the outcome.

