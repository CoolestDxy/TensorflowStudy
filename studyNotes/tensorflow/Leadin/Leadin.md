# Leadin
* 演示程序请参照[Leadin.py](Leadin.py)

``` py
import tensorflow as tf 
```
* 常量
``` py
import tensorflow as tf 
node0 = tf.constant(3.0,dtype=tf.float32)
node1 = tf.constant(3.0,dtype)# also tf.float32 implicitly
```
* 会话
``` py
sess = tf.Session()
print(sess.run([node0,node1]))
```
* 相加计算
``` py
node2 = tf.add(node0, node1)
print('node2', sess.run(node2))
```
* Placeholder占位符
``` py
a = tf.placeholder(tf.float32)
b = tf.placeholder(tf.float32)
adder_node = a + b  # + provides a shortcut for tf.add(a, b)
```
* feed_dict
```  py
print(sess.run(adder_node, {a:3, b:4.5}))
print(sess.run(adder_node, {a: [1,3], b: [2,4]}))
```
* 变量
``` py
W = tf.Variable([.3], dtype=tf.float32)
b = tf.Variable([-.3], dtype=tf.float32)
x = tf.placeholder(tf.float32)
linear_model = W*x + b
```
* 初始化变量
``` py
init = tf.global_variables_initializer()\
```
* 求值
``` py
print(sess.run(linear_model, {x: [1,2,3,4]}))
```
* 结束会话
``` py
sess.close()
```
* 降维求和
··· py
loss = tf.reduce_sum()
```
* 损失函数
``` py
y = tf.placeholder(tf.float32)
squared_deltas = tf.square(linear_model - y)    #损失函数(y(hat)-y)^2
loss = tf.reduce_sum(squared_deltas)            #减小Loss
print(sess.run(loss, {x: [1,2,3,4], y: [0, -1, -2, -3]}))
```
* 梯度下降
``` py
optimizer = tf.train.GradientDescentOptimizer(0.01) #梯度下降法
train = optimizer.minimize(loss)                    #设定损失函数目标
sess.run(init)# reset values to incorrect defaults. #初始化变量
for i in range(1000):
   sess.run(train, {x: [1,2,3,4], y: [0, -1, -2, -3]})#迭代优化
   #print(sess.run([W, b]))
print(sess.run([W, b]))                             #现实更新后的W,b的值
```


<img src="http://www.forkosh.com/mathtex.cgi? \Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}">

> Google's
>
> <img src="http://chart.googleapis.com/chart?cht=tx&chl=\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}" style="border:none;">
