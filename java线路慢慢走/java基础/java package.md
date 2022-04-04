## package 和jar的不同作用
1. packeage  防止两个同名的.java起冲突,打在不同包中
+ 一个.java中存在很多只有一个public class 用作对外提供接口,.java中有很多类,在java编译的中间时候一个类产生多个.class, 我们需要把这些.class 划分在同一个路径下,
2.  这个时候就是.jar的让package的文件分层的作用就得以体现了

## 如何找到一个包
+ 从系统classpath 开始找,package写出所在目录,jar,还需要在目录后面加上一个vector.jar.

## 包的本质就是文件目录
+ ccc/aaa  package .ccc package ccc.aaa一个文件目录一个包所以aaa是一个子包
+ ccc 代表一级目录 .aaa中的.代表了下一级目录
+ 我们在创建包的时候 在IDEA中 src目录下 我们创建一个包package 名称是 song.1989 ,此时src文件下出现song文件夹,song文件夹下面是1989


## 包的规范写法
![](2022-03-10-12-54-12.png)
+ 我们尽量 使用 import java.lang.Math;
+ 用到那个类就导入那个,少用import java.lang.*;

## package java.lang.Math
+ 这个语法的意义在于 我们指定某个类他在那个目录下
+ 语句必须放在最上面









