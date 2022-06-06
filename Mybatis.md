### Mybatis 学习笔记

mybatis官网：[mybatis – MyBatis 3 | Introduction](https://mybatis.org/mybatis-3/)



### 简介

---

- MyBatis 是一款优秀的**持久层框架**

- 它支持自定义 SQL、存储过程以及高级映射。

- MyBatis 免除了几乎所有的 JDBC 代码以及设置参数和获取结果集的工作。

- MyBatis 可以通过简单的 XML 或注解来配置和映射原始类型、接口和 Java POJO（Plain Old Java Objects，普通老式 Java 对象）为数据库中的记录。
- MyBatis本是apache的一个[开源项目](https://baike.baidu.com/item/开源项目/3406069)iBatis，2010年这个[项目](https://baike.baidu.com/item/项目/477803)由apache software foundation迁移到了[google code](https://baike.baidu.com/item/google code/2346604)，并且改名为MyBatis。2013年11月迁移到[Github](https://baike.baidu.com/item/Github/10145341)。
- iBATIS一词来源于“internet”和“abatis”的组合，是一个基于Java的[持久层](https://baike.baidu.com/item/持久层/3584971)框架。iBATIS提供的持久层框架包括SQL Maps和Data Access Objects（DAOs）。

#### 获取mybatis

- Github：[mybatis-3]([mybatis/mybatis-3: MyBatis SQL mapper framework for Java (github.com)](https://github.com/mybatis/mybatis-3))

- maven仓库：[artifact/org.mybatis/mybatis]([Maven Repository: org.mybatis » mybatis (mvnrepository.com)](https://mvnrepository.com/artifact/org.mybatis/mybatis))

#### 持久化

**数据持久化**

- 持久化是指程序的数据在持久状态和瞬时状态相互转化的过程

**数据持久化方式**：

+ 数据库（JDBC）
+ IO文件持久化

#### 持久层

完成持久化工作的代码块

#### 为什么需要Mybatis？

+ 方便
+ 传统的JDBC代码太复杂了，需要简化，自动化
+ 学习成本低，更容易上手

#### Mybatis的优点

+ 简单易学
+ 灵活
+ sql语句和代码分离，提高了可维护性
+ 提供映射标签，支持对象与数据库的orm字段关系映射
+ 提供xml标签，支持写动态sql
+ 最重要的一点：使用的人多

### 第一个mybatis程序

**1、建库建表**

```sql
create database `mybatis`;
use `mybatis`;
create table `t_user`(
    `id` int(20) not null primary key,
    `name` varchar(30) default null,
    `password` varchar(30) default null
)engine = innodb default character set = utf8;
insert into `t_user`(`id`, `name`, `password`)
values (1, '张三', '123456'),
       (2, '李四', '123456'),
       (3, '王五', '123456');
select * from `t_user`;
```

**2、新建maven项目，导入mysql和mybatis依赖。**

```xml
<!--        mysql-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.21</version>
        </dependency>
<!--        mybatis-->
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>3.5.7</version>
        </dependency>
```
