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