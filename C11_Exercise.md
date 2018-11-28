### Exercises

说明：
- 个人答案 
* 标准答案

1. Is it okay to initialize all the weights to the same value as long as that value is selected randomly using He initialization?
- 初始化为同一个值，便无法起到He Initialization的效果
- 而且可能初始化为0，这种情况下无法进行训练
* 初始值一样时，对于同一层的每个节点，输出层的cost都是一样的。由于weight的计算需要累加输出层的Gradient，因此对于同一层，weight的变化都是一样的，无法起到拟合效果！

2. Is it okay to initialize the bias terms to 0?
- 可以，进行GD时bias还是会进行变化的

3. Name three advantages of the ELU activation function over ReLU.
- 在0处有导数，适合Gradient Descent计算
- 在小于0时有导数，可以防止Weight Vanishing 

* 在0处有导数，防止计算Gradient异常跳动
* 永远有非0导数，防止节点失效（感觉跟vanishing差不多...）


4. In which cases would you want to use each of the following activation functions: ELU, leaky ReLU (and its variants), ReLU, tanh, logistic, and softmax?
- ELU：默认情况，对性能没有高要求，而且对精确度要求高
- leaky ReLU：训练时有vanishing情况的，需要兼容性能和精确度的
- ReLU：对性能要很高的情况下，但精确度低
* tanh：？用于输出层，可以输出结果限制在[-1, 1]
* logistic：？用于输出层，可估算概率，可以作为某些算法的AF
- softmax：输出层？估算概率


5. What may happen if you set the momentum hyperparameter too close to 1 (e.g., 0.99999) when using a MomentumOptimizer?
- 历史Gradient权重变大，几乎每轮Gradient都会对后续的学习曲线造成影响，不利于收敛
* 会在由于momentum比较大，会在收敛点反复摆动，导致收敛变慢


6. Name three ways you can produce a sparse model.
- ？？？
* One way to produce a sparse model (i.e., with most weights equal to zero) is to train the model normally,
  then zero out tiny weights. For more sparsity, you can apply l1 regularization during training,
  which pushes the optimizer toward spar‐ sity. A third option is to combine l1 regularization with dual averaging, 
  using TensorFlow’s FTRLOptimizer class.


7. Does dropout slow down training? Does it slow down inference (i.e., making predictions on new instances)?
- dropout会影响节点的收敛速度，但对于整体而言，这样慢收敛反而可以防止overfitting，所以，整体上看是不会减少训练速度的 
- 预测流程不会开启dropout，因此不会有影响
* dropout会影响收敛速度！

