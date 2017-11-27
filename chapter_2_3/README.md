本例演示了使用JavaConfig的方式进行bean的装配。

  * 对于配置类，可以也配合`@ComponentScan`一同使用；
  * 通过为方法添加`@Bean`注解声明bean，bean的名称默认为方法名，可以通过`@Bean(name)`自定义bean的名称；
  * 对于存在依赖关系的，有两种方式（具体见`CDPlayerConfig`的两个`cdPlayer`方法）：
    * 一种是在配置方法中调用被依赖bean的配置方法（该方法由于使用`@Bean`注解，在被调用时会被拦截，保证只有一个实例）；
    * (推荐)另一种是在配置方法中将被依赖bean作为参数传递进去，相对于第一种，不需要和被依赖bean的配置方法在一个配置类中，其实甚至不限制必须由配置方法声明，通过自动扫描或XML配置文件定义的bean也可以注入进来。
  * JavaConfig功能更加强大的地方在于，产生bean实例的方法将不受任何限制，比如使用`new`和`setter`，或者更加复杂的逻辑。