# Matrix-rotation
欧拉角 旋转矩阵 四元数 记录


1. 欧拉角 (Euler Angles)
正确：欧拉角确实是绕着自身坐标系（当前坐标系）的轴旋转。

例子（ZYX顺序）：

先绕自身Z轴旋转 yaw

再绕新的自身Y轴旋转 pitch

最后绕最新的自身X轴旋转 roll

2. 旋转矩阵 (Rotation Matrix)
旋转矩阵既可以表示绕固定轴旋转，也可以表示绕自身轴旋转，取决于如何使用：

绕固定坐标系旋转：
text
R_total = R_z(yaw) × R_y(pitch) × R_x(roll)
这是右乘，绕固定坐标系旋转

绕自身坐标系旋转：
text
R_total = R_x(roll) × R_y(pitch) × R_z(yaw)  
这是左乘，绕自身坐标系旋转

关键：旋转矩阵本身不指定旋转轴系，而是通过乘法顺序来区分。

3. 四元数 (Quaternions)：
   四元数既可以表示绕固定轴旋转，也可以表示绕自身轴旋转。
   四元数表示的是绕任意轴的旋转，这个轴可以在任何坐标系中定义：

python
# 绕固定坐标系的Z轴旋转45度
q_fixed = tf_transformations.quaternion_from_euler(0, 0, math.pi/4, 'rxyz')

# 绕自身坐标系的Z轴旋转45度  
q_local = tf_transformations.quaternion_from_euler(0, 0, math.pi/4, 'sxyz')
4. 总结对比
表示方法	旋转轴系	关键特点
欧拉角	自身坐标系	直观，但有万向锁问题
旋转矩阵	任意坐标系	通过乘法顺序决定旋转轴系
四元数	任意坐标系	无万向锁，计算效率高



