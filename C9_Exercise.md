### Exercises

1. What are the main benefits of creating a computation graph rather than directly executing the computations? What are the main drawbacks?
- 使用graph可以用于优化
- 不过缺点在于配置流程比较复杂
* 可自动计算Gradient，并行计算，跨平台，可视化
* 训练曲线抖动会变大，逐步debug变得困难


2. Is the statement a_val = a.eval(session=sess) equivalent to a_val = sess.run(a)?
- 是


3. Is the statement a_val, b_val = a.eval(session=sess), b.eval(ses sion=sess) equivalent to a_val, b_val = sess.run([a, b])?
- 前者会初始化每一个遍历，包括重复的，后者对于相同的变量只会初始化一次


4. Can you run two graphs in the same session?
- 可以
* 不行，一个session只能运行一个graph，所以必须合并两个graph


5. If you create a graph g containing a variable w, then start two threads and open a session in each thread, both using the same graph g, will each session have its own copy of the variable w or will it be shared?
- 不同session的变量相互独立
* Local Tensorflow 是相互独立的
* 但在并行运行系统下，变量会被一个集群（cluster）管理，如果session连到同一个集群，那么变量是共享的


6. When is a variable initialized? When is it destroyed?
- Session启动后需要手动初始化变量，所以是在那个地方进行初始化的，
- Session销毁时自动销毁变量
* 并行系统下，退出session并不会销毁变量，需要手动清理


7. What is the difference between a placeholder and a variable?
- placeholder主要用于传入训练数据，不需要在初始化时就赋值，同时也允许定义未知大小
- variable主要用于常量，或者参数，需要在初始化时赋值，并且shape固定
* variable其实是一个操作，只不过返回一个值而已，可以进行run操作


8. What happens when you run the graph to evaluate an operation that depends on a placeholder but you don’t feed its value? What happens if the operation does not depend on the placeholder?
- 训练时如果placeholder没有数据，会导致Exception
- 如果没用到placeholder，应该不会有问题，毕竟placeholder不强制初始化


9. When you run a graph, can you feed the output value of any operation, or just the value of placeholders?
- 只能是placeholder
* any operation


10. How can you set a variable to any value you want (during the execution phase)?
- 使用placeholder？
- placeholder直接用，variable的话可以用assign操作进行赋值


11. How many times does reverse-mode autodiff need to traverse the graph in order to compute the gradients of the cost function with regards to 10 variables? What about forward-mode autodiff? And symbolic differentiation?
- reverse-mode autodiff: 11
- forward-mode autodiff: 10
- symbolic differentiation: N/A???

* reverse-mode autodiff: 2
* forward-mode autodiff: 10
* symbolic differentiation: N/A???
这块不太懂...

