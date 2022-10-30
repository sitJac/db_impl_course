## 实验一：配置实验环境，编译并调试代码
- 需要了解：
    -   cmake项目构建工具
    -   ADB调试
- 如何编译：
    ```shell
    cd `project home`
    mkdir build
    cd build
    cmake ..
    make
    ```
- 如何运行：

    启服务端
    ```shell
        ./build/bin/observer -f ./etc/observer.ini 
    ```
    启客户端
    ```shell
        ./build/bin/obclient
    ```

## 实验二：实现 Drop Table 功能
删除表并清除表相关的资源（描述表的文件、数据文件、索引文件），能够成功执行下面语句。
```SQL
create table t(id int, age int);
show tables;
drop table t;
show tables;
drop table t;
create table t(id int, name char);
```

## 实验二：实现 DATE 字段的添加
增加数据库字段 DATE 类型，时间范围在1970年1月1日和2038年2月之间，能够成功执行以下语句。
```SQL
create table t(dmy DATE);
insert into t values('2022-3-7');
insert into t values('2022-3-8');
insert into t values('2022-3-81'); # 合法性检查
insert into t values('2022-13-1'); # 合法性检查
select  *  from t; # 日期展示检查
select  *  from t where dmy='2022-3-7'; # 日期比较检查
select  *  from t where dmy<'2022-3-7'; # 日期比较检查
select  *  from t where dmy>'2022-3-7'; # 日期比较检查
desc t;                                 # 描述表t

create table t2(c1 int, dmy DATE);
insert into t2 values(1, '2022-3-7');
select * from t2;
```