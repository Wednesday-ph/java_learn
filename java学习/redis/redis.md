# 黑马程序员redis

# 下载

- 去github上下载.zip文件，解压即可

# 使用

- 双击 redis-server.exe
  - port: 端口
  - pid : 名称
  - 下面有时间轴的是日志
- 双击redis-cli.exe

# 基本操作

- 添加（key相同会覆盖）

```java
set key value
```

- 查询key所对的value，不存在返回空（nil）

```java
get key
```

- 清屏

```java
clear
```

- 帮助

```java
help 命令名
help @群组名    
```

- 退出

```java
quit
[esc]    
```



# 数据类型(key一直都是String)

## String

### 基本操作

```java
//添加
set key value
    
//获取
get key

//删除（操作成功为：(integer)1, 失败为： (integer)0）    
del key    
    
//添加多个
mset key1 value1 key2 value2 ...    
    
//获取多个    
mget key1 key2 ...    
```

