# 案例

### 多人无聊天器

![QQ20170930-225819@2x](D:\随笔\复习\Day05\素材\QQ20170930-225819@2x.png)

#### 说明:

- 编写一个有两个线程的程序

- 线程一用来接收数据然后显示

- 线程二用来检测键盘数据然后通过`UDP`发送数据

  

#### 参考

```
import socket, threading


def send_msg(udp_socket):
    '''获取键盘数据,并将其发送给对方'''
    while True:
        # 收集键盘数据
        msg = input("请输入要发送的数据")
        # 输入对方的IP地址
        dest_ip = input("请输入对方的IP地址:")
        # 请输入对方的port
        dest_port = input("port:")
        udp_socket.sendto(msg.encode("utf-8"), (dest_ip, dest_port))


def recv_msg(udp_socket):
    # 接收数据并显示
    while True:
        recv_msg = udp_socket.recvfrom(1024)

        recv_ip = recv_msg[1]
        recv_msg = recv_msg[0].decode("utf-8")
        recv_msg = recv_msg[0].decode("utf-8")

        print(">>>%s:%s" % (str(recv_ip), recv_msg))


def main():
    # 创建套接字
    udp_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

    udp_socket.bind(("", 1212))

    # 创建套接字子线程
    t = threading.Thread(target=recv_msg, args=(udp_socket,))
    t.start()
    send_msg(udp_socket)


if __name__ == '__main__':
    main()

```

