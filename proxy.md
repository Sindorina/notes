# 动态代理

## 特点

字节码随用随创建，随用随加载

## 作用

不修改源码的基础上对方法增强

## 分类

1. 用于接口的动态代理

2. 用于子类的动态代理

### 基于接口的动态代理

   1. 涉及的类：Proxy
   2. 提供者：JDK官方

### 如何创建代理对象

   - 使用Proxy类中的newProxyInstance方法

   - newProxyInstance参数：

     1. ClassLoader：类加载器，它是用于加载代理对象字节码的，固定写法

     2. Class{}字节码数组，他是用于让代理对象和被代理对象有相同方法固定写法

     3. InvocationHandler：它是用于提供增强的代码，它是让我们写如何代理，我们一般都是一些一个该接口的实现类，通常情况下都是匿名内部类，但不是必须的，此接口的实现类都是谁用谁写

        

```JAVA
IService proxyService = Proxy.newProxyInstance(service.getClass().getClassLoader(), service.getClass().getInterfaces()
                , new InvocationHandler() {
                    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
                        return null;
                    }
                });
```



### 基于子类的动态代理

1. 涉及的类：Enhancer
2. 提供者：第三方cglib库

### 如何创建代理对象

   - 使用Enhancer类中的create方法
   - 创建代理对象的要求：被代理类不能是最终类
   - create方法参数
     1. Class：字节码，它是用于指定代理对象字节码
     2. Class{}字节码数组，他是用于让代理对象和被代理对象有相同方法固定写法
     3. InvocationHandler：它是用于提供增强的代码，它是让我们写如何代理，我们一般都是一些一个该接口的实现类，通常情况下都是匿名内部类，但不是必须的，此接口的实现类都是谁用谁写



