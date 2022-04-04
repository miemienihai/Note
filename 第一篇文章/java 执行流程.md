## .class文件
Java class 文件是八位字节的二进制流。

---
### class文件储存信息格式

1. magic 四个字节的文件类型表示符号，用于区分是否java文件
2. minor和major _version 正如其名，这是告诉Java虚拟机的所处理的次和主版本号
3. java的常量池，final 和类名的常量


---
## jvm和jDK和JRE关系
<a href="https://blog.csdn.net/u013238512/article/details/79308282?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0.essearch_pc_relevant&spm=1001.2101.3001.4242.1">link location<a>  


<br>

---
### MAVEN是什么
<font color =black>maven项目中有一个pom.xml文件，假如你依赖了Test.jar,你就在pom文件中通过配置引入Test.jar，如果你的本地仓库没有Test.jar,就从远程仓库下载到本地仓库。别的项目再依赖Test.jar，通过pom配置依赖，就直接使用了本地仓库的jar包。</font>

<a href="https://blog.csdn.net/weixin_39918690/article/details/114114941">link location</a>
<a href="https://www.w3cschool.cn/article/72852406.html">link location </a>

---
###  IDEA 基于maven创建项目流程
<a href="https://www.cnblogs.com/wql025/p/5215570.html">link location </a>