# 多线程高并发web服务器

## 项目内容

1.通过多路IO复用实现多用户高并发访问；

2.使用线程池提高多线程访问性能；

3.以muduo网络库作为项目网络核心框架，以one loop per thread构成事件循环，解耦网络跟业务模块代码。

### 主从reactor多线程模式

![image](https://user-images.githubusercontent.com/53084573/176342946-23d6cca1-efa1-4236-b911-70e79b136668.png)
