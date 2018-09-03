### Exercises

1. What are the main motivations for reducing a dataset’s dimensionality? What are the main drawbacks?
- 减低数据维度，提高训练效率，同时也可以减少训练过程中内存的使用
- 主要问题在于降维过程中，数据的准确度会受损，在一定程度上会影响最终输出模型的准确度
Adjusted: 方便数据可视化


2. What is the curse of dimensionality?
- 维度越高，数据分布越离散，不利于训练
Adjusted: 容易Overfitting


3. Once a dataset’s dimensionality has been reduced, is it possible to reverse the operation? If so, how? If not, why?
- 如果是线性映射的方法，可以通过反向操作恢复数据，但无法100%恢复。
- 如果是非线性操作，如manifold，则无法恢复数据，因为没有保留原维度坐标信息，很难恢复。


4. Can PCA be used to reduce the dimensionality of a highly nonlinear dataset?
- 不行，PCA映射对于非线性数据，无法正确保留数据拓扑信息
- 也许可以使用KernelPCA试一下...
Adjusted：PCA可适用于大多数数据的降维操作，即便是对于高度nonlinear数据，也可以去除无用的维度，
         但对于swiss roll这种每个维度都有用的数据集，降维会导致丢失关键数据


5. Suppose you perform PCA on a 1,000-dimensional dataset, setting the explained variance ratio to 95%. How many dimensions will the resulting dataset have?
- 这个并不确定，要视数据的分布而定。PCA会从映射后保留最多数据的维度开始选择，依次累加到95%，有可能几个维度就可以完成95%数据的映射


6. In what cases would you use vanilla PCA, Incremental PCA, Randomized PCA, or Kernel PCA?
- Vanilla PCA：数据量比较小的情况下使用
- Incremental PCA：需要利用并行计算，提高运行效率的情况下使用
- Randomized PCA：数据量比较大的情形下，可使用，但有可能会减低数据准确度
- Kernel PCA：非线性数据的情况下使用


7. How can you evaluate the performance of a dimensionality reduction algorithm on your dataset?
- 直接在最终测试集中验证，需要完整的数据准备->训练->预测流程。
- 通过计算原始数据与降维后再次恢复的数据误差，进行性能测试


8. Does it make any sense to chain two different dimensionality reduction algorithms?
- 感觉可以做，但是误差可能会很大，不推荐。。。
Adjusted：完全可以做，比如说像先用PCA去除掉无用的维度，然后再用LLE进一步降维。
         其实最终结果跟单独使用LLE差不多，但组合的话可以缩短时间。

