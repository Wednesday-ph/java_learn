# idea连接数据库时区问题

![](https://img-blog.csdnimg.cn/20190907165021112.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0lUTWFuMjAxNw==,size_16,color_FFFFFF,t_70)

# 分页查询

- pageable中简单封装了分页的信息

```java
    public String types(@PageableDefault(size = 3, sort = "id", direction = Sort.Direction.DESC) Pageable pageable)
    {
        
    }
```

- page中封装了分页信息

```java
Page<Type> ListType(Pageable pageable);
```





# 后台验证添加数据不能为空

1. 前端

```html
<form action="#" method="post" class="ui form" th:object="${type}" >
  <input type="hidden" name="id" th:value="*{id}">
  <div class="required field">
    <div class="ui left labeled input">
      <label class="ui teal basic label">名称</label>
      <input type="text" name="name" placeholder="分类名称" th:value="*{name}">
    </div>

  </div>

  <div class="ui error message"></div>
  <!--后端校验-->
  <!--/*/
    <div class="ui negative message" th:if="${#fields.hasErrors('name')}"  >
      <i class="close icon"></i>
      <div class="header">验证失败</div>
      <p th:errors="*{name}">提交信息不符合规则</p>
    </div>
  /*/-->


</form>
```



# 注解

```java
//关联数据库的表
@Entity
//表名
@Table(name="t_blog")
public class Blog
{
    //主键
    @Id
    //自动增长
    @GeneratedValue
    private Long id;
    //推荐
    private Boolean recommend;
    //对应mysql中的timestamp
    @Temporal(TemporalType.TIMESTAMP)
    private Date createTime;
    //级联创建
    @ManyToMany(cascade = CascadeType.PERSIST)
    private List<Tag> tags = new ArrayList<>();
    @ManyToOne
    private User user;
    //blog（one）被维护
    @OneToMany(mappedBy = "blog")
    private List<Comment> comments = new ArrayList<>();
}
```



# 持久层

```java
public interface UserRepository extends JpaRepository<User,Long>
{
    //根据它的命名习惯就行了
    User findByUsernameAndPassword(String username, String password);
}

```

```

```