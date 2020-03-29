# NumPy

```python
import numpy as np
```

## NumPy Ndarray对象

```python
numpy.array(object, dtype = None, copy = True, order = None, subok = False, ndmin = 0)
```

* object：数列或嵌套数列
* dtype：数据类型
* copy：对象是否需要复制
* order：创建数组的样式（C：行方向；F：列方向；A：任意方向（默认））
* subok：返回一个与基类类型相同的数组
* ndmin：指定最小维度

```python
# 多于一个维度  
import numpy as np 
a = np.array([[1,  2],  [3,  4]])  
print (a)
```

```python

# 最小维度  
import numpy as np 
a = np.array([1,  2,  3,4,5], ndmin =  2)  
print (a)
```

结果：[[1, 2, 3, 4, 5]]

注意：

* 下标从0开始  

