# Java-Socket-Multi-Thread
Java Socket 多线程网络传输多个文件 来自 https://software.intel.com/zh-cn/blogs/2013/05/20/java-socket?language=es </br>

由于需要研究了下用 java socket 传输文件，由于需要传输多个文件，因此，采用了多线程设计。客户端每个线程创建一个 socket 连接，每个 socket 连接负责传输一个文件，服务端的ServerSocket每次 accept 一个 socket 连接，创建一个线程用于接收客户端传来的文件。
