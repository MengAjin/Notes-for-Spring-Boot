How does Spring Prevent CSRF Attack?
-
参考：

https://docs.spring.io/spring-security/site/docs/current/reference/html/csrf.html

- CSRF攻击：

    即跨站请求攻击，是用户在正规网站登录之后，不小心进入了恶意网站，恶意网站通过该用户的cookie中的信息冒充用户给正规网站发送请求，盗取用户信息，可能造成经济损失。
- Spring中的防御手段：
  ```
  _csrf=<secure-random>
  ```
  通过给 _csrf 变量赋一个随机值，并加到请求之中，使得攻击者无法猜到这个值，也就无法发起攻击。
- 什么时候要使用CSRF防御手段？    
  只要是有普通用户通过浏览器向服务端发送请求这一功能，就要使用CSRF防御。
  但如果客户端不是通过浏览器发送请求，那么可以disable这一功能
  
- 取消CSRF保护的方式：
```$xslt
@EnableWebSecurity
public class WebSecurityConfig extends
WebSecurityConfigurerAdapter {

@Override
protected void configure(HttpSecurity http) throws Exception {
	http
	.csrf().disable();
}
}
```