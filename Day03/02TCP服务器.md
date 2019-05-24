# TCP服务器

1. ### TCP服务器

   - socket创建一个套接字

   - bin绑定套接字   IP / port

   - listen套接字

   -  accept等待客户端链接

   - recv/send接受发送数据

     

一个简单的TCP服务器

```
import socket

# 创建套接字
tcp_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# 本地信息
address = ("", 7890)

# 绑定套接字
tcp_socket.bind(address)

# 使用socket创建么人的属性使用listen将其变为被动的,就可以接受别人的链接

tcp_socket.listen(128)

# 如果有新客户端链接服务器,就创建新的套接字为其服务
# client_socket 用来服务
# tcp_socket就可以省下来等待新用户访问

client_socket,ClientAddr = tcp_socket.accept()

# 接收对方发送的数据
recv_data = client_socket.recv(1024)

print("收到数据为:",recv_data.decode("utf-8"))

# 发送数据到客户端
client_socket.send("好无聊".encode("utf-8"))

client_socket.close()
```



## TCP注意事项

1. ### <u>TCP服务器一般都是需要绑定,方便客户端寻找</u>

2. ### <u>TCP客户端一般不绑定,因为主动链接服务器,所以只要确认IP和port信息,本地客户端可以随机</u>

3. ### <u>TCP服务器通过listen可以将socket创建出来的主动套接字变为被动的,这个做TCP服务器是必须要做</u>

4. ### <u>当客户访问服务器时,就需要使用connect进行链接,udp不需要链接而直接发送,但是TCP必须连接后才能通信</u>

5. ### <u>当一个TCP客户端连接服务器时,服务器端会有一个新的套接字,这个套接字用来标记这个客户端,单独为其服务</u>

6. ### <u>listen后套接字变为被动套接字,用来接收新的客户端链接请求,而accept返回的新套接字是标记这个客户端</u>

7. ### <u>关闭listen后,被动套接字关闭,会导致新客户端不能够连接服务器,但是之前连接成功的客户端可以正常通信</u>

8. ### <u>关闭accept返回套接字意味着客户端服务完毕</u>

9. ### <u>当客户端的套接字调用close()后意味着服务器recv解堵塞,并返回长度为0,因此服务器可以通过返回的数据长度来判断客户端是否下线</u>

   

