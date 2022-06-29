# 多线程高并发web服务器

## 项目特点

1.通过多路IO复用实现多用户高并发访问；

2.使用线程池提高多线程访问性能；

3.以muduo网络库作为项目网络核心框架，以one loop per thread构成事件循环，解耦网络跟业务模块代码。

## 主从reactor多线程模式

![image](https://user-images.githubusercontent.com/53084573/176347135-449ad1be-62cd-4406-a5f9-2dd0f2e434c8.png)

1.main Reactor只有一个，只负责监听新的连接。

2.每当有新的连接请求就由Acceptor将连接请求分配给Connection

3.Connection建立socket连接到sub Reactor上。

4.每个sub Reactor是一个EventLoop，负责事件循环，sub Reactor的数量取决于工作线程的数量。

5.EventLoop监测读写事件的发生，每当有读写事件发生时，调用Connection中的读写成员函数。

6.读写操作由网络模块提供，业务逻辑完全由client负责，解耦了网络跟业务模块代码。
