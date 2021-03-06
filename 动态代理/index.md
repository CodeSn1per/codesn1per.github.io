# 动态代理


### 1. 动态代理的实现

##### 1. jdk动态代理:

> * 使用java反射包中的类和接口实现动态代理的功能
> * 反射包 java.lang.reflect,里面有三个类:InvocationHandler,Method,Proxy

##### 2. cglib动态代理

> * cglib是第三方的工具库,创建代理对象.
> * cglib的原理是继承,cglib通过继承目标类,创建他的子类,在子类中重写父类中同名的方法,实现功能的修改.
> * 因为cglib是继承,重写方法,所以要求目标类不能是final的,方法也不能是final的

### 2. jdk动态代理

##### 1. 反射,Method类,表示方法,类中的方法.通过Method可以执行某个方法.

##### 2. jdk动态代理的实现

> **InvocationHandler**
>
> * 就一个方法invoke()
> * invoke():表示代理对象要执行的功能代码,你的代理类要完成的功能卸载invoke()方法中.
>
> * 方法原型:
>
>   参数: Object proxy: jdk创建的代理对象,无需赋值
>
>   Method method: 目标类中的方法,jdk提供method对象的
>
>   Object[] args: 目标类中的方法的参数,jdk提供

> **Method**
>
> * 表示方法的,确切的说是目标类中的方法
> * 通过Mehtod可以执行某一个目标类的方法,Method.invoke()

> **Proxy**
>
> * 核心的对象,创建的代理对象,之前创建对象都是用new类的构造方法(),现在使用Proxy类的方法,代替new的使用
> * 静态方法:newProxyInstance(),创建代理对象
> * 参数:
>   * classLoader loader: 类加载器,负责向内存中加载对象的.使用反射获取对象的ClassLoader
>   * Class<?>[] interfaces: 接口,目标对象实现的接口,也是反射获取的
>   * InvocationHander h: 我们自己写的,代理类要完成的功能

