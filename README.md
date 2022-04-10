# 2-layers-model操作指南

github repo链接: 

### 环境要求

```
python == 3.7.11
keras == 2.4.3
numpy == 1.18.5
```

### 模型训练

1. 数据集导入
2. 数据集预处理
3. 网络搭建

```python
NN = TwoLayerNeuralNetwork(x_train, y_train, hidden_cells=128, batch=64, lr=0.005, epochs=50, lambd=0.01, decay_rate=0) # 自定义超参数
NN.train(IS_PRINT=True) # 进行训练，并打印训练过程中的loss和acc
```

### 参数查找

隐藏层hidden_cells_num：[32, 64, 128]

学习率learning_rate：[0.05, 0.01, 0.005]

正则化强度lambda：[0, 0.001, 0.01]



### 模型测试

导入利用参数查找得到的最佳模型，并利用test函数进行测试，输出测试的accuracy：

```python
model = TwoLayerNeuralNetwork(x_train, y_train, hidden_cells=128, batch=64, lr=0.005, epochs=50, lambd=0.01, decay_rate=0)
model.load_model(filename) # 输入最佳模型的名字
model.test(x_test, y_test)
```



### 模型可视化

可视化训练和测试的 loss 曲线，测试的 accuracy 曲线，以及可视化每一层的网络参数

