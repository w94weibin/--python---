# TCP客户端

1. #### TCP客户端构建流程

   ```
   import socket
   # 创建socket
   tcp_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
   
   # 目的信息
   server_ip = input("请输入服务器ip:")
   server_port = int(input("请输入服务器port:"))
   
   # 链接服务器
   tcp_socket.connect((server_ip, server_port))
   
   # 提示用户输入数据
   send_data = input("请输入要发送的数据：")
   
   tcp_socket.send(send_data.encode("utf-8"))
   
   # 接收对方发送过来的数据，最大接收1024个字节
   recvData = tcp_socket.recv(1024)
   print('接收到的数据为:', recvData.decode('gbk'))
   
   # 关闭套接字
   tcp_socket.close()
   ```

   