# 注意

- 导入依赖后记得刷新仓库

# 问题

##  依赖字体报红

- 找包导入，包内没东西，删除后重构

## 已删除子模块，但提示子模块存在

- 删除.idea

## 依赖坐标字体变红

因为找不到jar包，要自己去下载

1. https://maven.aliyun.com/mvn/search选择gav搜索
2. mvn install:install-file -Dfile=(下载文件地址) -DgroupId=(pom.xml依赖的groupId) -DartifactId=(pom.xml依赖的artifactId) -Dversion=(pom.xml依赖的version) -Dpackaging=jar
3. 重启项目

## 静态资源无效

- maven:clean

## 导入项目maven重置

- 删除.idea文件

## plugins爆红

![img](https://img-blog.csdnimg.cn/20210317124426134.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dhb19MaWppZQ==,size_16,color_FFFFFF,t_70#pic_center)

![img](https://img-blog.csdnimg.cn/20210317124506931.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0dhb19MaWppZQ==,size_16,color_FFFFFF,t_70#pic_center)