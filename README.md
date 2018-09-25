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
