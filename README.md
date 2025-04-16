# Quantacus.Ai-Case-study
# Case Description
The marketing team of an e-commerce site launched an email campaign targeting a random sample of registered users. The email introduced a new feature and included a link redirecting users to the website. A successful outcome, from the marketing perspective, is defined as a user clicking on that link.

# Workflow
Starting from a basic RandomForestClassifier, the project iteratively explores advanced modeling techniques such as XGBoost, LightGBM, SMOTE for imbalance correction, SHAP for interpretability, and custom threshold optimization to enhance model performance on imbalanced binary classification.

The final models deliver high precision and recall for the rare clicked class (~2.1%), enabling smarter audience targeting and significantly improving click-through rate (CTR) predictions.

I developed two models for future forecasting 

Model 1 : SHAP-pruned XGBoost with SMOTE

🔍 Model Summary :

This model uses XGBoost to predict whether a user will click on an email, based on both behavioral and content-based features.

The dataset is enhanced with engineered features like:
email_opened, opened_but_not_clicked (user interaction)
text_version_interaction (content personalization)

SMOTE is applied to handle severe class imbalance (very few clicked examples).
Evaluation on the held-out test set shows high accuracy and recall, especially for the minority class (clicked = 1), indicating the model is well-tuned and generalizes effectively.

📊 Performance Highlights :

Accuracy: 99%
Precision (Clicked class): 72%

Recall (Clicked class): 99% — almost all actual clicks are captured!

F1 Score (Clicked class): 83%

ROC AUC Score: 0.993 — extremely strong model discrimination ability

Model 2 : One-hot encoded XGBoost + Threshold Optimization + GridSearchCV

🔍 Model Summary :

This version uses one-hot encoded categorical features, numerical variables, and email-open behavior to predict click likelihood.

Extensive hyperparameter tuning using GridSearchCV was done, optimizing for recall of clicked emails.

The model threshold was fine-tuned (default 0.5 → optimized to 0.92) for maximum F1-score on the minority class (clicked = 1).

Evaluation was performed on a stratified test set of 20,000 samples, preserving the original class distribution.

📊 Performance Highlights :

ROC AUC Score: 0.9661 — strong discriminative performance

F1 Score (Clicked): 0.400 (best possible given severe imbalance)

Recall (Clicked): 59% — captures over half of actual clicks

Precision (Clicked): 30% — better than baseline random guess

Accuracy: 96% (on a very imbalanced set)

Optimal threshold for clicked detection: 0.92

# Key Tasks & Insights
📊 1. Campaign Performance Metrics
Email Open Rate: Calculated the percentage of users who opened the email.

Click-Through Rate (CTR): Measured the percentage of users who clicked the link inside the email.

🤖 2. Predictive Modeling
Built a machine learning model to predict the likelihood of a user clicking the link in the email based on available user and campaign data.

This model can be used to optimize recipient selection for future campaigns, potentially replacing the current random approach.

📈 3. Estimated Uplift in CTR
Using the trained model, we estimated the potential improvement in CTR if only the most likely users were targeted.

🔍 4. Segment Analysis
Conducted detailed exploration to identify user segments that responded differently to the campaign.

Discovered insightful patterns based on factors like user activity, demographics, and past interactions, enabling more targeted and personalized campaigns.
# Outcome
By leveraging data analysis and machine learning, this project demonstrates a clear path to optimize email marketing strategies, leading to higher engagement and better resource allocation.
