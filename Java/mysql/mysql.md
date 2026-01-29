# MySQL数据库相关知识

## 安装方法

由于本人是Linux环境，加上安装了docker，于是我决定采用docker来安装MySQL。

```bash
# 拉取MySQL镜像，这里拉取指定版本号的8.0版本
$ docker pull mysql:8.0
# 运行Mysql容器
$ docker run -itd --name mysql-test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql:8.0
```

运行完之后，通过vscode的docker插件进行连接，在容器终端里面使用:

```bash
mysql [-h 127.0.0.1] [-P 3306] -u root -p
```

## 具体知识

### SQL

建议事项:

- MySQL数据库的SQL语句不区分大小写，关键词建议使用大写;
- SQL语句可以单行或多行书写，以分号结尾

#### DDL

数据库操作：

```text
1. 查询:
1.1 查询所有数据库: 
SHOW DATABASES;
1.2 查询当前数据库:
SELECT DATABASE();
2. 创建:
CREATE DATABASE [IF NOT EXISTS] 数据库名 [DEFAULT CHARSET 字符集] [COLLATE 排序规则];
3. 删除:
DROP DATABASE [IF EXISTS] 数据库名;
4. 使用:
USE 数据库名;
```

表操作-查询与创建：

```text
1. 查询当前数据库所有表:
SHOW TABLES;
2. 查询表结构:
DESC 表名;
3. 查询指定表的建表语句:
SHOW CREATE TABLE 表名;

4. 创建表:
CREATE TABLE 表名{
    字段1 字段1类型[COMMENT 字段1注释],
    字段2 字段2类型[COMMENT 字段2注释],
    字段3 字段3类型[COMMENT 字段3注释],
    ...
    字段n 字段n类型[COMMENT 字段n注释]
}[COMMENT 表注释];
```

数据类型:

```text
VARCHAR和CHAR的选取: 
VARCHAR是变长的，CHAR是定长的。VARCHAR的性能会弱于CHAR。一般定长的我们可以选取CHAR(比如说性别)，变长的选择VARCHAR(比如说用户名)。
```

![日期数据类型](./img/日期数据类型.png)

其中一定要非常注意`TIMESTAMP`的范围最终到2038年，尽量不要使用这个数据类型，避免系统崩溃。

![数值类型](./img/数值类型.png)

如果要使用无符号类型，就直接在后面加上`unsigned`即可。

表操作-修改:

```text
1. 添加字段: 
ALTER TABLE 表名 ADD 字段名 类型(长度) [COMMENT注释] [约束]; 
2. 修改数据类型:
ALTER TABLE 表名 MODIFY 字段名 新数据类型(长度);
3. 修改字段名和字段类型:
ALTER TABLE 表名 CHANGE 旧字段名 新字段名 类型(长度) [COMMENT 注释] [约束]
4. 删除字段: 
ALTER TABLE 表名 DROP 字段名;
5. 修改表名:
ALTER TABLE 表名 RENAME TO 新表名;
6. 删除表:
DROP TABLE [IF EXISTS] 表名;
7. 删除指定表，并重新创建表:
TRUNCATE TABLE 表名;
```
