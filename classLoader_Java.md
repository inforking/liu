##ClassLoader##
**双亲委派机制**

类加载器收到类加载请求时，先将加载任务传递给父加载器，逐级上传，直到顶层的启动类加载器，如果该类无法加载此请求，则该类的子类尝试加载，逐级分配下来，直到能处理。

**沙箱机制**

一种JVM自我保护机制，加载类时优先加载jdk的包。（eg：用户是无法写java.lang.String类的（因为rt.jar下有同包名、同类名的类））


ref:https://blog.csdn.net/start_lie/article/details/79016312
https://blog.csdn.net/suifeng3051/article/details/52611310
