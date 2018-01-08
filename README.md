# Kaggle-Porto-Seguro

### Things I've tried for feature engineering

I started by looking at a correlation heat map of the features in the dataset. There were features that had almost no correlation with the target variable so I decided to drop those. Next, I onehot encoded categorical features because tree based methods tend to work better those than the original categories. I experimented by adding some statistical features and they seem to slightly improve results.

### Final Model

My final model uses an emsemble method called stacking. The idea is to use multiple different kind of models to predict on both the training set and the test set. In order to simulate out of sample training for the training set, I used a kfold cross validation method to train on k-1 folds and predict on the other fold. I then save the predictions on the training set to use as a feature for the stacking classifier. I did this with multiple lgbm and xgboost models trained on different features. For each model, I would create a feature for the stacking classifier. Non-linear classifiers did not seem to work as well as the simple logistic regression so I ended up using logistic regression as my final stacking classifier.
