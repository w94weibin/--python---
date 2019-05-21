# 网络-udp

1. #### socket套接字

   socket是进程间通信的一种方式,他与其他的进程间通信的一个主要的不同:

   他能实现不同主机间的进程通信,我们网络上各种各样的服务大多是基于socket来完成通信

2. #### 创建socket

   利用socket模块中的socket函数

   ```
   import socket
   socket.socket(AddressFamily, Type)
   ```

   *说明  : socket.socket创建一个socket套接字,应该传两个参数*

   - Address Family: 可以选择AF_INET(用于INTERNET进程间通信) 或者AF_UNIX(用于同一台机器进程间通信),实际工作中常用AF_INET
   - Type:套接字类型,可以是SOCK_STREAM (流式套接字,主要用途TCP协议)或者SOCK_DGRAM(实际工作中常用AF_INET)

   ``` 
   # tcp套接字
   import socket
   s = socket.socket(socket.AF_INET,socket.SOCK_REAM)
   s.close()
   ```

   ```
   #udp套接字
   import socket
   s = socket.socket(socket.AF_INET,socket.SOCK_DGRAM)
   s.close
   ```

   

# UDP网络程序 收发数据

1. #### 发送数据

   - 创建客户端套接字

   - 收发数据

   - 关闭套接字

     ![02-就业班-02-1](D:\随笔\复习\Day01\素材\02-就业班-02-1.jpg)

#### 代码演示

```
import socket

# 1. 创建udp套接字
udp_socket = socket.socket(socket.AF_INET,socket.SOCK_DGRAM)

# 2. 准备接收方的地址
dest_addr = ('192.168.236.129', 8080)

# 3. 从键盘获取数据
send_data = input("请输入要发送的数据:")

# 4. 发送数据到指定的电脑上
udp_socket.sendto(send_data.encode('utf-8'), dest_addr)

# 5. 等待接收对方发送的数据
recv_data = udp_socket.recvfrom(1024)  # 1024表示本次接收的最大字节数

# 6. 显示对方发送的数据
# 接收到的数据recv_data是一个元组
# 第1个元素是对方发送的数据
# 第2个元素是对方的ip和端口
print(recv_data[0].decode('gbk'))
print(recv_data[1])

# 7. 关闭套接字
udp_socket.close()

```



2. #### udp网络程序收发数据

```
import socket
# 1.创建套接字
udp_socket = socket.socket(socket.AF_INET,socket.SOCK_DGRAM)
# 2. 准备接收对方地址
dest_addr = ("127.0.0.1",7890)
# 3.从键盘获取数据
send_data = input("请输入:")
# 4.发送数据到指定的电脑上
udp_socket.sendto(send_data.encode('utf-8'),desr_addr)
# 5.等待接收对方发送的数据
recv_data =udp_socket.recvfrom(1024) #1024表示接受的最大字数
# 6.显示对方发送的数据
# 接收到的数据recv_data是一个元组
# 第1个元素是对方发送的数据
# 第2个元素是对方的ip和端口
print(recv_data[0].decode('gbk')
print(recv_data[1])

# 7.关闭套接字
udp_socket.close()
```



