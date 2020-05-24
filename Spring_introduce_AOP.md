# Spring 中的AOP

## AOP相关术语

1. `JoinPoint (连接点)` : 所谓的连接点是指那些被拦截到的点,  在 spring 中,  这些点是指方法,  因为 spring 只支持方法类型的连接点
2. `Pointcut (切入点)` : 所谓的切入点是指我们要对哪些 JoinPoint 进行拦截的定义
3. `Advice (通知/增强)` : 所谓通知是指拦截到 Joinpoint 之后所要做的事情就是通知, 分类如下
- 前置通知
   - 后置通知
   - 异常通知
   - 最终通知
   - 环绕通知
4. `Introduction (引介)` : 引介是一种特殊的通知, 在不修改源码的前提下,  Introduction 可以在运行期类动态的添加一些方法或 Field .
5. `Target (目标对象)` : 代理的目标对象
6. `Weaving (织入)` : 是指把增强应用到目标对象来创建新的对象的过程，spring 采用动态代理织入，二AspectJ采用编译期织入和类装载织入
7. `Proxy (代理)` : 一个类被 AOP 织入增强后, 就会产生一个结果代理类
8. `Aspect (切面)` : 是切入点和通知 (引介) 的结合



## spring 中 AOP要明确的事

### 开发阶段(我们做的)

编写核心业务代码(开发主线)  , 把公司代码抽取出来, 制作通知 , 在配置文件中, 生命切入点与通知的关系, 即切面

### 运行阶段( spring 框架完成)

spring 框架监控切入点方法执行. 一旦监控到切入点方法被运行, 使用代理机制, 动态创建目标对象的代理对象, 根据通知类型, 在代理对象的对应位置,  将通知对应的功能织入吗完成完整的代码逻辑运行.


