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
