###### k8s的作用
  容器监控：实时掌握云平台资源的性能和应用运行情况
  应用调度： 保障了资源的高效利用

###### docker底层依赖的核心技术：
1. linux操作系统的命名空间（namespace）
2. 控制组（control groups）
3. 联合文件系统(union file systems)
4. linux虚拟网络支持

#### 基础架构
1. docker采用了标准的C/S架构，包括客户端和服务端两大部分。
2. 客户端和服务器端既可以运行在一个机器上，也可以通过socket或者restful API 来进行通信。

##### 服务端
1. docker daemon 一般在宿主机主机后台运行，作为服务端接受来自客户的请求，并处理一些请求（创建，运行，分发容器）。
2. docker 服务器端默认监听本地的unix:///var/run/docker.sock套接字，只允许本地的root用户访问。
