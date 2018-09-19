Exercises
1. If you have trained five different models on the exact same training data, and they all achieve 95% precision, is there any chance that you can combine these models to get better results? If so, how? If not, why?
A: Use a voting classifier, like VotingClassifier, BaggingClassifier, AdaBoostClassifier, etc.

2. What is the difference between hard and soft voting classifiers?
A: Hard voting use the classification result to vote for the best output
   Soft voting use the probability of classification result to vote for the best output

3. Is it possible to speed up training of a bagging ensemble by distributing it across multiple servers? What about pasting ensembles, boosting ensembles, random forests, or stacking ensembles?
A:  bagging ensemble - YES
    pasting ensemble - YES
    boosting esembles - NO
    ramdom forests - YES
    stacking ensembles - YES

4. What is the benefit of out-of-bag evaluation?
A: - Quickly validates the model after the training finished
   - Get full usage of data


5. What makes Extra-Trees more random than regular Random Forests? How can this extra randomness help? Are Extra-Trees slower or faster than regular Random Forests?
A: - It randomly select features for split the decision tree
   - The improvement of randamization will produce high bias and low variance (regularization), which in some case will help.
   - Extra-Trees are faster


6. If your AdaBoost ensemble underfits the training data, what hyperparameters should you tweak and how?
A: - increase n_estimators
   - increase DecisionTree min_samples_leaf, max_leaf_nodes
   - slightly increase the learning rate

7. If your Gradient Boosting ensemble overfits the training set, should you increase or decrease the learning rate?
A: increase the learning rate - WRONG!!!
   应该减少learing rate，注意，层与层之间计算的是误差值，因此小的步伐可以减少激进的猜测。





