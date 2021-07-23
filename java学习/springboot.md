# 了解springboot

传统ssm需要解决jar包间的冲突，而springboot只需要导入starter



# 形参值

## 重定向后还带有值

```java
RedirectAttributes attributes
//带回到页面
attributes.addFlashAttribute("message", "用户名密码出错1");
    
```

# MD5加密

```java
DigestUtils.md5DigestAsHex(password.getBytes())
```



# 练习

[练习](D:\IdeaProjects\springboot)

# 遇到的问题

### spring-boot-maven-plugin爆红

- 导入版本号

### spring initializr不了

将默认地址修改为阿里的地址
https://start.aliyun.com/
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210325074625203.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzg5MTU3Mw==,size_16,color_FFFFFF,t_70#pic_center)

