### Exercises

1. Draw an ANN using the original artificial neurons (like the ones in Figure 10-3) that computes A ⊕ B (where ⊕ represents the XOR operation). Hint: A ⊕ B = (A ∧ ¬ B) ∨ (¬ A ∧ B).
- 已完成

2. Why is it generally preferable to use a Logistic Regression classifier rather than a classical Perceptron (i.e., a single layer of linear threshold units trained using the Perceptron training algorithm)? How can you tweak a Perceptron to make it equivalent to a Logistic Regression classifier?
- Logistic Regression拥有更准确的算法
* 错，Logistic Regression可以处理非线性数据，可以输出概率
- Perceptron的activation function替换为logistic，可以达到与Logistic Regression相同的作用


3. Why was the logistic activation function a key ingredient in training the first MLPs?
- 使用logistic可拥有全局最优解
* 使用logistic可以支持Gradient Descent，应为函数永远有导数，可以平滑的趋近最优解。Step funciton的话没有导数，无法支持GD

4. Name three popular activation functions. Can you draw them?
- ReLU, Logistic, Tanh

5. Suppose you have an MLP composed of one input layer with 10 passthrough neurons, followed by one hidden layer with 50 artificial neurons, and finally one output layer with 3 artificial neurons. All artificial neurons use the ReLU activation function.
• What is the shape of the input matrix X?
- (n, 10)

• What about the shape of the hidden layer’s weight vector Wh, and the shape of its bias vector bh?
- hidden layer's weight: (10, 50)
- bias vector: (n, 1) 错：50，bias是直接加到矩阵运算后的结果上面的，也就是最后一行

• What is the shape of the output layer’s weight vector Wo, and its bias vector bo?
- output layer's weight: (51, 3)，错：50？？？
- bias vector: (n, 1) 错：3

• What is the shape of the network’s output matrix Y?
- (n, 3)

• Write the equation that computes the network’s output matrix Y as a function of X, Wh, bh, Wo and bo.
 Y = ReLU(X * Wh + bh) * Wo + bo;

6. How many neurons do you need in the output layer if you want to classify email into spam or ham? What activation function should you use in the output layer? If instead you want to tackle MNIST, how many neurons do you need in the output layer, using what activation function? Answer the same questions for getting your network to predict housing prices as in Chapter 2.

- 2 output neurons for spam classification
- softmax could be used for output layer
* one output layer + logistic regression

- 10 output neurons for MNIST classification
- softmax could be used for output layer

- 1 output neurons for Housing Price Prediction
- None Activition function


7. What is backpropagation and how does it work? What is the difference between backpropagation and reverse-mode autodiff?
- backpropagation算法用于训练神经网络，主要思路是通过层层递进计算整个神经网络参数对于CostFunction的Gradient
- backpropagation是reverse-mode autodiff的一种特殊形式
* 错，backpropagation代表整个神经网络的训练过程，包括先forword pass through计算cost，然后利用reverse-mode autodiff计算各个参数的gradient。
 而reverse-mode autodiff只是神经网络计算中采用的技术


8. Can you list all the hyperparameters you can tweak in an MLP? If the MLP overfits the training data, how could you tweak these hyperparameters to try to solve the problem?
- learning rate for each layer
- activation function
- number of layers
- number of neurons in one layer
- dropout

- if overfits, reduce number of layers... 
* and the number of neurons per layer
