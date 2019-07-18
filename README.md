# tcp_udp
add tcp&udp coding
## 传输层中的TCP和UDP
### 端口号
传输层协议利用端口号识别本机中正在通信的应用程序，并准确将数据传输。<br>
![](https://github.com/sjtujw/tcp_udp/raw/master/img/duankou.jpg)
### TCP
* 三次握手<br>
![](https://github.com/sjtujw/tcp_udp/raw/master/img/shakehands3.jpg)
* 四次握手<br>
![](https://github.com/sjtujw/tcp_udp/raw/master/img/shakehands4.jpg)
* 通过序列号与确认应答提高可靠性
![](https://github.com/sjtujw/tcp_udp/raw/master/img/ack.jpg)
* 重发超时的确定（公式待补充）
* 以段为单位发送数据<br>
最大消息长度（MSS），以MSS的大小将数据进行分割发送。进行重发时也是以MSS为单位。MSS在三次握手时，在两端主机之间被计算得出。两端的主机在发出建立连接的请求时，会在 TCP 首部中写入 MSS 选项，告诉对方自己的接口能够适应的 MSS 的大小。然后会在两者之间选择一个较小的值投入使用。
* 利用窗口控制提高速度
TCP以一个段为单位，每发送一个段进行一次确认应答的处理。存在的问题是包的往返时间越长，通信性能就越低。TCP引入了窗口这个概念。确认应答不再是以每个分段，而是以更大的单位进行确认，转发时间将会被大幅地缩短。<br>
![](https://github.com/sjtujw/tcp_udp/raw/master/img/window.jpg)
* 滑动窗口控制

* 窗口控制中的重发控制
![](https://github.com/sjtujw/tcp_udp/raw/master/img/retransmit.jpg)
## 网络层中的IP协议
### IP地址
* 网络和主机两部分标识
* IP地址四种分类（A（0-127）、B（128-191）、C（192-223）、D（224-239））
* 主机地址的部分全部设置为1，就成了广播地址；分为本地广播和直接广播
* D类地址用在多播
* 子网掩码
### 路由