

**1. 编译过程**
- 找到 *.class并加载到内存
- 字节码验证（编译阶段？）（检验**无法运行**的变量、类型、堆栈私有规则
	- 数据结构分析、
	- 内存分配、
	- 符号表连接 对另一个文件或目录的引用（import？）java.niv.Files
- 静态属性 初始化赋值静态代码块
![](http://hi.csdn.net/attachment/201009/25/0_1285420122jhjH.gif)
Java 原码编译过程
    - 分析和输入到符号表（字节码验证那一系列过程？）
    - 注解处理
    - 语义分析和生成class文件
**2. 加载过程**
## classLoader##

- 动态加载class文件到虚拟机
- 转换成java.lang.class的一个实例
	- Instances of the Class repesent classes and interfaces in a running Java application. eg:`enum`(`class`),primitive Java types(boolean、byte、int……）（represented as ` Class` objects）;`annotation`(`interface`);**sp**:every array(`class`) is reflected as a `Object` that is ** shared by all arrays with the `same element type` and` number`**.
	- Class has no public constructor. Class objects are constructed automatically when they are loaded.
		- by JVM as classes 
		- by calls to the defineClass method in class loader
- 可通过该class实例获得该类的信息，也可通过newInstance实例化一个对象

名称转换为文件名，获取类文件，采用**委托模型**搜索资源
##
##各个加载器
- Bootstrap classloader
	- native code实现（本地方法栈下？）
	- JVM 一部分 加载java.lang.* java.util.*
	- 继承自 classloader 
	- 都早Extension classloader（ExtClassLoader)、AppClassLoader
- ExtClassLoader
- AppClassLoader（继承ExtClassLoader）
	- 加载英语程序、主函数类，classpath下
- 用户自定义 继承AppClassLoader
	- getSystemClassLoader （父加载器）return AppClassLoader
![](http://hi.csdn.net/attachment/201009/25/0_1285421756PHyZ.gif)

##
ps：

##ClassLoader## 双亲委派机制

类加载器收到类加载请求时，先将加载任务传递给父加载器，逐级上传，直到顶层的启动类加载器，如果该类无法加载此请求，则该类的子类尝试加载，逐级分配下来，直到能处理。

沙箱机制

一种JVM自我保护机制，加载类时优先加载jdk的包。（eg：用户是无法写java.lang.String类的（因为rt.jar下有同包名、同类名的类））

ref:https://blog.csdn.net/start_lie/article/details/79016312 https://blog.csdn.net/suifeng3051/article/details/52611310

** 3. 执行过程 **
## JVM memory model##
![http://img.blog.csdn.net/20161210212709845?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaHlsZXh1cw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast](http://img.blog.csdn.net/20161210212709845?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaHlsZXh1cw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast "http://img.blog.csdn.net/20161210212709845?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaHlsZXh1cw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast")

- PC
- VM stack
	-编译时可知的各种基本数据类型和对象引用，所需内存空间在编译期确定。
- 本地方法栈
- 方法区 类信息、常量、静态变量(虽然共享内存区域，但不一定共享数据“我占了就是我的”）
- 堆 : 对象实例和数组
- 直接内存

方法调用至完成：栈帧从虚拟机入栈到出栈
再贴几张图：
![](http://images2015.cnblogs.com/blog/620343/201705/620343-20170513173026160-2119980188.png)
![](http://images2015.cnblogs.com/blog/620343/201705/620343-20170513174629504-1262094758.png)
![](http://images2015.cnblogs.com/blog/620343/201705/620343-20170513184007113-478361758.png)
form：https://blog.csdn.net/berylpy/article/details/72055476




