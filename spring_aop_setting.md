# spring AOP配置

## xml配置aop

1. `aop:config` 表示开始aop的配置

2. `aop:aspect` 表示配置切面

   - `id` 属性 : 给切面提供一个唯一标识
   - `ref` 属性 : 是指定通知类 bean 的 id 

3. 在 aop : aspect 标签的内部使用对应标签来配置通知的类型

   - `aop : before` 前置通知
   - `aop : after-returning` 后置通知, 在切入点方法正常执行之后执行, 它和异常通知只能执行一个
   - `aop : after-throwing`异常通知 , 在切入点方法执行产生异常之后执行, 它和后置通知只能执行一个
   - `aop : after`最终通知
   - `aop : around `环绕通知, 它是spring框架为我们提供的一种可以在代码中手动控制增强方法何时执行的方式
   - `aop : pointcut` : 用于指定切入点表达式, 该表达式的含义指的是对业务层那些方法进行加强

4. 切入点表达式的写法:

   - 关键字 : `execution`

   - 表达式 : `访问修饰符`, `返回值`,`包名.包名...类名.方法名(参数列表)`

   - 标准表达式写法

     ```java
     public T com.xxx.xxx.functionName(T t)
     ```

   - 全通配写法

     ```java
     * *..*.*(..)
     ```

   - 我们常见写法(业务层包名写出来)

     ```java
     * com.xxx.xxx.*.*(..)
     ```

     

```java
<aop:config>
    <aop:aspect id = "id" ref = "bean">
    	<aop:before method = "method"/> 
    <aop:aspect/>
</aop:config>
```

