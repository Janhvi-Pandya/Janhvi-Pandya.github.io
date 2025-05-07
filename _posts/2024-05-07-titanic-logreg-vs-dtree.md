---
layout: post
title: "Titanic Dataset: Logistic Regression vs Decision Tree"
date: 2024-05-07
---

### Logistic Regression Model: Interpretation & Explanation

Logistic Regression is a binary classification model that predicts the probability of an event occurring—in our case, whether a passenger survived (1) or not (0). It outputs a probability score, and if that score is above a certain threshold (commonly 0.5), the model classifies it as "survived".

We trained a logistic regression model on the Titanic dataset and evaluated it on a validation set. The model achieved an accuracy of approximately 80%. This means the model correctly predicted survival outcomes for about 80% of passengers in the validation set.

The confusion matrix for the predictions was:

[[89 16]  
 [20 54]]

Here’s what this means:
- 89 passengers who actually died were correctly predicted as not survived (true negatives).
- 54 passengers who actually survived were correctly predicted as survived (true positives).
- 16 passengers were predicted to have survived but actually didn’t (false positives).
- 20 passengers were predicted to have died but actually survived (false negatives).

These values show us not just overall performance, but **where** the model makes mistakes. It struggles slightly more with identifying survivors (missed 20) than identifying deaths.

The classification report provides a deeper analysis:
- For class 0 (not survived), precision was 0.82 and recall was 0.85.
- For class 1 (survived), precision was 0.77 and recall was 0.73.
- F1-score for survivors was 0.75, indicating a moderate balance between precision and recall.

Precision tells us: “Out of all the times the model predicted someone would survive, how often was it right?”  
Recall tells us: “Out of all the actual survivors, how many did the model correctly identify?”

The model had higher precision than recall for survivors, meaning it was cautious about predicting survival—it only predicted it when it was confident, which means fewer false alarms, but also more missed actual survivors.

The macro and weighted average scores were both around 0.79–0.80. Macro average treats both classes equally, while weighted average accounts for class imbalance (more people died than survived in the Titanic dataset).

In summary, our logistic regression model performs quite well as a baseline. It is especially good at predicting non-survivors and moderately effective at catching true survivors. There is room for improvement, particularly in recall for the survivor class. This could potentially be addressed using more complex models (e.g., decision trees, random forests) or better feature engineering.

###  Decision Tree Classifier – Model Interpretation

We trained a Decision Tree Classifier with a maximum depth of 4 to avoid overfitting. The model was evaluated on a 20% validation set, and the results were as follows:

The model achieved an accuracy of **~79.89%**, which means it correctly predicted survival status for about 80% of passengers in the validation data. This is similar to the logistic regression model, but with different strengths.

The confusion matrix was:

[[96  9]  
 [27 47]]

This tells us:
-  **96 passengers** who died were correctly predicted as such (true negatives).
-  **47 passengers** who survived were correctly predicted (true positives).
-  **9 passengers** were wrongly predicted as survived when they died (false positives).
-  **27 passengers** were wrongly predicted as died when they actually survived (false negatives).

The classification report breaks it down further:
- For class 0 (not survived), precision = 0.78, recall = 0.91, and F1-score = 0.84. This means the model is very good at detecting people who died — it caught 91% of them.
- For class 1 (survived), precision = 0.84, recall = 0.64, and F1-score = 0.72. This means that when it predicts survival, it's usually correct (84% precision), but it **misses many actual survivors** (only 64% recall).

So, compared to logistic regression:
- The **decision tree is more confident when it predicts someone survived (higher precision)**.
- But it **misses more actual survivors than logistic regression** (lower recall).
- It’s **more aggressive in declaring deaths** (high recall for class 0).

The macro and weighted averages show balanced performance:
- Macro avg F1 = 0.78 (unweighted average across both classes)
- Weighted avg F1 = 0.79 (weighted by class size)

In summary, the decision tree performs similarly to logistic regression in terms of overall accuracy but has **different trade-offs**. It is slightly better at catching those who died and more confident in predicting survival — but less effective at identifying all survivors.

This suggests that either model is a solid baseline, and you could potentially improve performance by trying **ensemble methods** like Random Forest or Gradient Boosting.

📓 **Notebook link**: [View the code on Colab] https://colab.research.google.com/drive/1-6joDrE4xk1eAVWWKoNyep7PwVV5wPmu?usp=sharing

