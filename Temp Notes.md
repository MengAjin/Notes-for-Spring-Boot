小记
-
- spring.profiles.active = dev 
  spring.profiles.active = prod
  可以在.yml或命令行下设置应用执行的环境（开发或生产或测试）
- @SpringBootApplication 
   
   \= 
   @Configuration 
   
   @EnableAutoConfiguration 
   
   @ComponentScan
 
- 静态映射赋值
```$xslt
@Value("#{target.parking.post.roadSection.id}")
String getRoadSectionId();
```
- @Slf4j 用于自动添加日志
http://himichaelchu.iteye.com/blog/2124589

- FetchType
  
  LAZY  需要时加载子数据（缺点是，会话在一段时间后会被关闭）
  EAGER 在请求时立即访问并加载所有子数据
  
  eg:班级数据，班上学生的数据
  LAZY时，只取班级数据，学生数据稍后get才取到
  EAGER时，班级、学生数据一次性都取出来
  
  使用这个注解的缺点是不够灵活，可能在一个程序中要用到的取数据的方式有多种，而如果在注解中写死的话，就只能有一种
  改进策略：使用entity graph
  
- @EqualsAndHashCode
    
  参考：
  https://projectlombok.org/features/EqualsAndHashCode
  
  用于控制目标类hashCode()和equals()方法的生成
  `@EqualsAndHashCode(callSuper = false)`表示在该类生成这两个方法时不包含对应的父类的两个方法。
  当没有对父类进行扩展时，可以设置该值为true，有扩展时不能，会出现警告。
  
  
  exclude 属性用于指定生成hashcode的时候不需考虑的域

- 入口函数要放在根目录下，不能放在某个文件夹里，否则主函数将找不到 
   