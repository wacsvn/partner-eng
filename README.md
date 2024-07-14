Partner is the leading provider of engineering, environmental, construction, energy, and valuation consulting for the commercial real estate industry.

In hopes of simplifying their Property Condition Assessment (PCA) report, this project aimed to assess the associations between different structural component attributes, and to evaluate whether certain attributes imply the presence of others.

Machine Learning Model Flowchart: 
![image](https://github.com/user-attachments/assets/23b54239-205f-453a-b61b-72f0e5324eed)


In order to account for the class imbalances between frame types, we sought to experiment with additional techniques that may improve our model’s accuracy. We first attempted to implement a Balanced Random Forest Model, which essentially draws an equal number of bootstrap samples from the minority (Wood Frame) and majority (No Wood Frame) classes, and then applies the random forest model on it, ideally avoiding any overfitting caused by imbalances. Fitting this model yielded an improvement in results from the baseline; while accuracy decreased to a more realistic 71%, the F1 Score greatly increased to 0.545. Intuitively, this meant that the model was getting slightly better at predicting true positives. 

Next, in an effort to improve the accuracy of the model from that baseline, we introduced different weight values. Such changes included setting the weight parameter to be inversely proportional to class frequencies, as well as setting the parameter to be “balanced”. However, none of these tweaks to the weight introduced a significant improvement to the baseline model. 

We additionally experimented with tuning hyperparameters in order to yield the most optimal scores on our testing set. This did improve the model, with accuracy reaching a peak of 80.4% and f1-score reaching 0.643. Some of the hyperparameters here include the criterion, minimum samples split, and max features arguments. However, the three most influential hyperparameter alterations were:
Increasing the number of estimators (trees) - makes model less prone to effects of noise in individual trees
Reducing max depth - reduces complexity / chance of overfitting
Specifying criterion as ‘entropy’ - may produce more balanced trees than ‘gini’ 
