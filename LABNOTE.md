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

## 实验三：LRU替换算法
在MiniOB中实现LRU驱逐策略算法，要求时间复杂度为O(1)。
```C++
/** 
 * 实现一个LRU链表，存储一定容量的key-value集合，最大容量是_max_size
 * 
 * - 调用exists(key)判断key是否在lru cache中
 * - 调用size() 得到lru cache的容量
 * - 调用put(key, value) 来向lru cache中插入新的key-value对，并覆盖相同key的key-value对。
 *   比如，lru cache中已经存在(10, 10)，那么put(10, 11)后，10对应的值就是11
 * - 调用get(key)得到key对应的值 
 * - 调用getVictim(&vic_key, check, ctx) 来得到满足check条件的可以被驱逐的key
 *   这个check和ctx是caller传递过来的，一般指disk_buffer_pool.cpp中的not_pinned()函数和BPManager对象指针
 * - 调用victim(vic_key, new_key) 来将vic_key-value 替换成new_key-value。
 * 
 * 每次调用put()和get()后，访问的key-value对都会移动到双向链表的头部，这样的话，双向链表的尾部
 * 就是最近最少使用的key-value对了。
 * 
 * LRU链表使用双向循环链表来实现，我们使用std::list模板类。
 * 每个key-value对作为一个元素存储在std::list中。
 * 为了提高查找效率，我们使用哈希表来存储key对应的std::list中的迭代器，这样的话，就可以根据key直接定位到std::list
 * 中的位置，而不用遍历整个链表。哈希表采用std::unordered_map模板类，哈希值计算函数采用disk_buffer_pool.h中的hash_func
 * 
 * 上层的BPManager类会使用到这个lru_cache的实现
 */
```