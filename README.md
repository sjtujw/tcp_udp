# tcp_udp
add tcp&udp coding
## 传输层中的TCP和UDP
### TCP 对应的应用层协议有：FTP,Telnet,SMTP,POP3,HTTP
### UDP 对应的应用层协议有：DNS,SNMP,TFTP
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
* 重发超时的确定（公式待补充）<br>
1. 平滑的往返时间：SRTT = alpha * SRTT +(1-alpha)*R，alpha 一般取7/8。R是这次确认花费的时间。
2. 往返时间变化：<br>
RTTVAR = beta * RTTVAR + (1-beta)|SRTT-R|，beta取3/4。<br>
重传超时值：RTO = SRTT + 4 * RTTVAR
* 以段为单位发送数据<br>
最大消息长度（MSS），以MSS的大小将数据进行分割发送。进行重发时也是以MSS为单位。MSS在三次握手时，在两端主机之间被计算得出。两端的主机在发出建立连接的请求时，会在 TCP 首部中写入 MSS 选项，告诉对方自己的接口能够适应的 MSS 的大小。然后会在两者之间选择一个较小的值投入使用。
* 利用窗口控制提高速度
    - TCP以一个段为单位，每发送一个段进行一次确认应答的处理。存在的问题是包的往返时间越长，通信性能就越低。
    - TCP引入了窗口这个概念。确认应答不再是以每个分段，而是以更大的单位进行确认，转发时间将会被大幅地缩短。<br>
![](https://github.com/sjtujw/tcp_udp/raw/master/img/window.jpg)
* 滑动窗口控制
![](https://github.com/sjtujw/tcp_udp/raw/master/img/slidewindows.jpg)
* 窗口控制中的重发控制<br>
丢包一般分为两种：
    - 确认应答未能返回的情况。
    - 某个报文段丢失的情况。
![](https://github.com/sjtujw/tcp_udp/raw/master/img/retransmit.jpg)
## 网络层中的IP协议
### IP地址(32bit)
* 网络和主机两部分标识
* IP地址四种分类（A（0-127）、B（128-191）、C（192-223）、D（224-239））
* 主机地址的部分全部设置为1，就成了广播地址；分为本地广播（本网络内）和直接广播（不同网络之间）。
* D类地址（1110）用在多播：用于将包发送给特定组内的所有主机。
* 子网掩码
### 路由
### IPV6
* IPv6（IP version 6）是为了根本解决 IPv4 地址耗尽的问题而被标准化的网际协议。IPv4 的地址长度为 4 个 8 位字节，即 32 比特。而 IPv6 的地址长度则是原来的 4 倍，即 128 比特，一般写成 8 个 16 位字节。
#### 常见状态码及原因短语<br>
HTTP请求结构：请求方式+请求URL+协议及版本<br>
HTTP响应结构：状态码+原因短语+协议及版本<br>
* 1xx：请求处理中，请求已被接受，正在处理
* 2xx：请求成功，请求被成功处理<br>
200 OK
* 3xx：重定向，要完成请求必须进行进一步处理<br>
301：永久性转移<br>
302：暂时性转移<br>
304：已缓存<br>
* 4xx：客户端错误，请求不合法<br>
400：Bad Request，请求有语法错误<br>
403：拒绝请求<br>
404：客户端所访问的页面不存在<br>
* 5xx：服务器端错误，服务器不能处理合法请求<br>
500：服务器内部错误<br>
503：服务不可用，请稍等<br>