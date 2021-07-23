# ThymeLeaf

## 分页

- 插件 numbers ${#numbers.sequence(from,to)}生成从几到几的序列，可以each

```html
th:each="num:${#numbers.sequence(1,page.pages)}
```

## 导航条

- 传参：link URLs 中 @{/order/process(execId=${execId},execType='FAST')}，动态获取参数
- 占位符：link URLs 中 @{/order/{orderId}/details(orderId=${orderId})} ，动态获取参数
- 
- 注意：th:href="@{/delete/{id}(id=${user.id},cur=${page.current})}"参数都是在括号里的

## thymeleaf布局

*  定义fragment

```html
<!DOCTYPE html>
<html lang="en" xmlns:th="http://www.thymeleaf.org">
<!--  title标签用自己的  -->
<head th:fragment="head(title)">
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!--  title标签用自己的  -->
    <title th:replace="${title}">博客详情</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/semantic-ui/2.2.4/semantic.min.css">
    <link rel="stylesheet" href="../static/css/typo.css" th:href="@{/css/typo.css}">
</head>
<body>

</body>
</html>
```



*  使用fragment布局

```html
<head th:replace="_fragment :: head(~{::title})">
  <title>首页</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/semantic-ui/2.2.4/semantic.min.css">
  <link rel="stylesheet" href="../static/css/me.css">
</head>
```

- 指定fragment是从template下指定

## 根据是否存在来显示

```html
<div class="ui mini negative message" th:unless="${#strings.isEmpty(message)}" th:text="${message}">用户名和密码错误</div>
```

# active状态

```html
<nav th:fragment="menu(n)" class="ui inverted attached segment m-padded-tb-mini m-shadow-small" >
  <div class="ui container">
    <div class="ui inverted secondary stackable menu">
      <h2 class="ui teal header item">管理后台</h2>
      <a href="#" class="active m-item item m-mobile-hide" th:classappend="${n==1} ? 'active'"><i class="mini home icon"></i>博客</a>
```