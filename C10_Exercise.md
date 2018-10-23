### Exercises

1. Draw an ANN using the original artificial neurons (like the ones in Figure 10-3) that computes A ⊕ B (where ⊕ represents the XOR operation). Hint: A ⊕ B = (A ∧ ¬ B) ∨ (¬ A ∧ B).
- 已完成

2. Why is it generally preferable to use a Logistic Regression classifier rather than a classical Perceptron (i.e., a single layer of linear threshold units trained using the Perceptron training algorithm)? How can you tweak a Perceptron to make it equivalent to a Logistic Regression classifier?
- Logistic Regression拥有更准确的算法
- Perceptron的activation function替换为logistic，可以达到与Logistic Regression相同的作用


3. Why was the logistic activation function a key ingredient in training the first MLPs?
- 使用logistic可拥有全局最优解

4. Name three popular activation functions. Can you draw them?
- ReLU, Logistic, Tanh

5. Suppose you have an MLP composed of one input layer with 10 passthrough neurons, followed by one hidden layer with 50 artificial neurons, and finally one output layer with 3 artificial neurons. All artificial neurons use the ReLU activation function.
• What is the shape of the input matrix X?
- (n, 10)

• What about the shape of the hidden layer’s weight vector Wh, and the shape of its bias vector bh?
- hidden layer's weight: (10, 50)
- bias vector: (n, 1)

• What is the shape of the output layer’s weight vector Wo, and its bias vector bo?
- output layer's weight: (51, 3)
- bias vector: (51, 1)
？？？ 上层的bias参与下层的计算？

• What is the shape of the network’s output matrix Y?
- (n, 3)

• Write the equation that computes the network’s output matrix Y as a function of X, Wh, bh, Wo and bo.
 Y = ReLU(X * Wh + bh) * Wo + bo;

6. How many neurons do you need in the output layer if you want to classify email into spam or ham? What activation function should you use in the output layer? If instead you want to tackle MNIST, how many neurons do you need in the output layer, using what activation function? Answer the same questions for getting your network to predict housing prices as in Chapter 2.

- 2 output neurons for spam classification
- softmax could be used for output layer

- 10 output neurons for MNIST classification
- softmax could be used for output layer

- 1 output neurons for Housing Price Prediction
- None Activition function


7. What is backpropagation and how does it work? What is the difference between backpropagation and reverse-mode autodiff?
...


8. Can you list all the hyperparameters you can tweak in an MLP? If the MLP overfits the training data, how could you tweak these hyperparameters to try to solve the problem?
- learning rate for each layer
- activation function
- number of layers
- number of neurons in one layer

- if overfits, reduce number of layers...
