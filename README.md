# Java-Socket-Multi-Thread
Java Socket 多线程网络传输多个文件 来自 https://software.intel.com/zh-cn/blogs/2013/05/20/java-socket?language=es </br>

由于需要研究了下用 java socket 传输文件，由于需要传输多个文件，因此，采用了多线程设计。客户端每个线程创建一个 socket 连接，每个 socket 连接负责传输一个文件，服务端的ServerSocket每次 accept 一个 socket 连接，创建一个线程用于接收客户端传来的文件。</br>

除了isClosed()方法，Socket类还有一个isConnected()方法来判断Socket对象是否连接成功。看到这个名字，也许读者会产生误解。  其实isConnected()方法所判断的并不是Socket对象的当前连接状态，  而是Socket对象是否曾经连接成功过，如果成功连接过，即使现在isClosed()返回true， isConnected()仍然返回true。因此，要判断当前的Socket对象是否处于连接状态， 必须同时使用isClosed()和isConnected()方法， 即只有当isClosed()返回false，isConnected()返回true的时候Socket对象才处于连接状态。 虽然在大多数的时候可以直接使用Socket类或输入输出流的close方法关闭网络连接，但有时我们只希望关闭OutputStream或InputStream，而在关闭输入输出流的同时，并不关闭网络连接。这就需要用到Socket类的另外两个方法：shutdownInput()和shutdownOutput()，这两个方法只关闭相应的输入、输出流，而它们并没有同时关闭网络连接的功能。和isClosed()、isConnected()方法一样，Socket类也提供了两个方法来判断Socket对象的输入、输出流是否被关闭，这两个方法是isInputShutdown()和isOutputShutdown()。 shutdownInput()和shutdownOutput()并不影响Socket对象的状态。
