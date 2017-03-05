# 梯度下降法
- 数据缩放
	- 当不同特征的取值范围差距很大时，会导致梯度下降法搜索路径长，收敛缓慢。
	- 在课程中关于房价预测的举例，以房屋面积和卧室数量为特征，建立线性回归模型，并以均方误差作为代价函数。下图便是J(theta)关于theta1和theta2的轮廓图，其中theta1为卧室数量（1-5个），theta2为房屋面积（0-1000平方英尺），由于二者取值范围差距较大，得到的图像会十分“瘦高”。
	![](https://github.com/MrTuo/Stanford-machine-learning-note/blob/master/picture/%E6%88%BF%E5%B1%8B%E5%9B%BE%E5%83%8F.PNG?raw=true)
    - 梯度下降法路径方向总是垂直于轮廓图向中心点靠近，这样一来，路径就会变得十分蜿蜒曲折，路径长，时间长。
    ![](https://github.com/MrTuo/Stanford-machine-learning-note/blob/master/picture/%E4%B8%8B%E9%99%8D%E8%B7%AF%E5%BE%84%E9%95%BF.PNG?raw=true)
    - 如果我们对两个特征做了缩放处理，结果就会好很多。下图中将每个特征出去他们的最大值，将范围缩小到0-1内。可以看出梯度下降的路径不再那么曲折了。
    ![](https://github.com/MrTuo/Stanford-machine-learning-note/blob/master/picture/%E5%A5%BD%E5%BE%88%E5%A4%9A.PNG?raw=true)
    - 较理想的情况是， 特征彼此之间范围差距不要超过100倍以上，梯度下降就能够较高时效的工作。
- 归一化处理
	- 特征的归一化处理指的是将数值特征中每一项减去特征所有取值的均值并处以范围（最大值减去最小值）。

- 步长选择
	- 随着迭代次数的增加，得到梯度下降的最终结果会减小，这反映了梯度下降在正常工作，梯度下降能否正常工作取决于学习率alpha的选择。
	- 下面是梯度下降正常工作时，迭代次数与J_theta的关系。
	![](https://github.com/MrTuo/Stanford-machine-learning-note/blob/master/picture/%E6%A2%AF%E5%BA%A6%E4%B8%8B%E9%99%8D%E6%AD%A3%E5%B8%B8%E5%B7%A5%E4%BD%9C.PNG?raw=true)
    - 下面是学习率过大时，迭代次数与J_theta的关系。
    ![](https://github.com/MrTuo/Stanford-machine-learning-note/blob/master/picture/%E4%B8%8D%E6%AD%A3%E5%B8%B8%E5%B7%A5%E4%BD%9C.PNG?raw=true)
    - 随着迭代次数增加，J_theta反而上升了，alpha太大导致每一步过长，如下图，每次迭代直接越过最优化值，J_theta逐渐上升（图中x轴应为theta）
    ![](https://github.com/MrTuo/Stanford-machine-learning-note/blob/master/picture/%E9%80%90%E6%B8%90%E4%B8%8A%E5%8D%87.PNG?raw=true)
    - 另一种情况，J_(theta)随迭代次数忽大忽小，也需要减小alpha。
    ![](https://github.com/MrTuo/Stanford-machine-learning-note/blob/master/picture/%E9%9C%87%E8%8D%A1.PNG?raw=true)
    - 总结
    	- alpha过小会导致收敛很慢。
    	- alpha过大可能会导致不收敛。
    	- 一般选取0.001,0.01,0.1,1。 
