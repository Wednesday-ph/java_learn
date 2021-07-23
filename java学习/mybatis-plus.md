

# Mybatis-plus

- 继承ServiceImpl

- 导入分页插件

- MapperScan("xx.mapper")

- 主键过大的问题

  ```
  mybatis-plus:
    global-config:
      db-config:
        id-type: auto
  ```

