###### k8s的作用
  容器监控：实时掌握云平台资源的性能和应用运行情况
  应用调度： 保障了资源的高效利用

### docker底层依赖的核心技术：
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

##### 客户端
1. docker 客户端则为用户提供一系列可执行命令，用户用这些命令实现与docker daemon的交互。
2. 用户使用的docker可执行命令即为客户端程序，与docker daemon 不同的是，客户端发送命令后，等待服务器返回，一旦收到返回后，客户端立即执行结束并退出。
用户执行新的命令需要再次调用客户端命令。
3. 客户端默认通过本地的unix:///var/run/docker.sock套接字向服务端发送命令。

#### 命名空间
1. 命名空间是linux内核针对实现容器虚拟化而引入的一个强大特性。每个容器都可以拥有自己单独的命名空间。
2. 在操作系统中，包括内核，文件系统，网络，PID,UID, IPC，内存，硬盘，CPU等资源，所有资源都是应用程序直接共享的。要想实现虚拟化，除了要实现对内存，CPU，网络I/O，硬盘IO，内存空间等资源的限制外，还要实现文件系统，网络，PID，UID，IPC等等的相互隔离。
##### 进程命名空间
1. linux通过命名空间管理进程号，对于同一个进程（同一个task_struct），在不同的命名空间中，看到的进程号不相同，每个进程命名空间有一套自己的进程号管理方法。进程命名空间是一个父子关系的机构，子空间中的进程对于父空间是可见的。新fork出的进程在父命名空间和子命名空间将分别有一个进程号来对应。
##### 网络命名空间
##### IPC命名空间
##### 挂载命名空间
##### UTS命名空间
##### 用户命名空间
#### 控制组（cgroup）
1. 控制组是linux内核的一个特征，主要用来对共享资源进行隔离，限制，审计等。只有能控制分配到容器的资源，docker才能避免多个容器同时运行时的系统资源竞争。
##### 资源限制
##### 优先级
##### 资源审计
##### 隔离
##### 控制

