## 说明
```
TCP数据传输实验
```

## 注意
```
本实验仅实现在【无丢包网络下】的【无拥塞控制的】
简易TCP协议栈
```

实验环境：Mininet

## 编译代码
Linux系统打开终端，执行：
```
git clone https://github.com/lizhzhuo/tcp_stack.git
cd tcp_stack
make

```

## 启用
Linux系统打开终端，执行：
```
启动mininet
sudo python2 topo/tcp_topo.py
打开xterm
mininet> xterm h1 h2
```

### 禁用tcp协议栈，并设置lib路径,需要分别在h1 h2的xterm中运行

```
./scripts/disable_arp.sh
./scripts/disable_icmp.sh
./scripts/disable_ip_forward.sh #Ubuntu中需要将-p ipv4改成-p ip
./scripts/disable_tcp_rst.sh
export LD_LIBRARY_PATH=.;
```

## 在h1,h2节点启动服务器模式
```
./tcp_stack server 10001
./tcp_stack client 10.0.0.1 10001
```


## 目录结构

带<b>*</b>号的表示需要完善的文件。

```
tcp_stack
├── client.py           # 客户端程序实现（python脚本），用于测试
├── example             # 多线程和list例子程序
├── include             # 相关头文件
├── libipstack.so       # IP查找和发送数据包相关函数实现，参见相应头文件
├── main.c
├── Makefile
├── README.md
├── scripts             # 禁止协议栈脚本
├── server.py           # 服务器程序实现（python脚本），用于测试
├── tcp_apps.c          # 基于tcp-stack的服务器和客户端程序
├── tcp.c               # TCP协议相关处理函数
├──*tcp_in.c            # TCP接收相关函数
├── tcp_out.c           # TCP发送相关函数
├──*tcp_sock.c          # tcp_sock操作相关函数
├── tcp_stack-reference # TCP协议栈参考实现
├── tcp_timer.c         # TCP定时器
└── topo                # Mininet拓扑文件夹

```