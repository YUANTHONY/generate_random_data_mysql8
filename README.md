
### 通过存储过程随机生成员工数据
> 随机生成员工ID，员工姓名，员工性别，员工出生日期...等等。
> 通过while循环与prepare statement进行预存储提高效率。
---

#### 表设计预览
![wfbbb8.png](https://s1.ax1x.com/2020/09/18/wfbbb8.png)

---
#### 使用方法
##### mysql命令行

``` mysql
1. 进入mysql
$ mysql -uroot -p

2. 执行sys_employee.sql创建sys_employee表
$ mysql> source [文件路径]/sys_employee.sql

3. 执行generate_random_data，随机生成数据
$ mysql> soure [文件路径]/generate_random_data.sql
```
##### 第三方工具如(Navicat等)，具体请参照官方文档

---
#### 生成海量数据如(100万)
``` mysql
修改generate_random_data.sql文件中第156行数据

156: CALL generate_random_data(10000); 

> 将10000改成1000000即可

```

#### 生成数据预览
![wfLInP.png](https://s1.ax1x.com/2020/09/18/wfLInP.png)

#### 测试性能
老机子在Navicat 12 Premium下生成100万数据的测试结果：202s
![wfjo0x.png](https://s1.ax1x.com/2020/09/18/wfjo0x.png)

数据在10000时，用时3s左右，达到100万级时感觉过长，个人认为因字段数据过长，存储过程使用的函数过多等原因，导致处理时间过长。

---
#### 缺点
* 代码可能不利于观看，因为都集中在一个过程当中，排版较密
* 地址部分应该根据三大范式再进行细分
* 当随机数量达到100万级时，处理会比较缓慢，有待完善过程
  

