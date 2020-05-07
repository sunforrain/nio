# nio
java8 nio使用的总结
## 目录
### 1. NIO_NIO 与 IO 区别
        NIO支持面向缓冲区的、基于通道的IO操作
           IO						NIO
           面向流(Stream Oriented)			        面向缓冲区(Buffer Oriented)
           阻塞IO(Blocking IO)				非阻塞IO(NonBlocking IO)
           (无)					        选择器(Selectors)
### 2. NIO_缓冲区(Buffer)的数据存取
    缓冲区（Buffer）：在 Java NIO 中负责数据的存取。缓冲区就是数组。用于存储不同数据类型的数据
### 4. NIO_直接缓冲区与非直接缓冲区
     非直接缓冲区：通过 allocate() 方法分配缓冲区，将缓冲区建立在 JVM 的内存中
     直接缓冲区：通过 allocateDirect() 方法分配直接缓冲区，将缓冲区建立在物理内存中。可以提高效率
### 5. NIO_通道(Channel)的原理与获取
    通道（Channel）：用于源节点与目标节点的连接。在 Java NIO 中负责缓冲区中数据的传输。
    Channel 本身不存储数据，因此需要配合缓冲区进行传输。
### 6. NIO_通道的数据传输与内存映射文件
    MappedByteBuffer inMappedBuf = inChannel.map(MapMode.READ_ONLY, 0, inChannel.size());
    MappedByteBuffer outMappedBuf = outChannel.map(MapMode.READ_WRITE, 0, inChannel.size());
    inChannel.transferTo(0, inChannel.size(), outChannel);
    outChannel.transferFrom(inChannel, 0, inChannel.size());
### 7. NIO_分散读取与聚集写入
    ByteBuffer[] bufs = {buf1, buf2};
    channel1.read(bufs);
     分散读取（Scattering Reads）：将通道中的数据分散到多个缓冲区中
     聚集写入（Gathering Writes）：将多个缓冲区中的数据聚集到通道中
### 8. NIO_字符集 Charset
      编码：字符串 -> 字节数组
      解码：字节数组  -> 字符串
### 9. NIO_阻塞与非阻塞
      见课件的概念解释
### 10. NIO_阻塞式
    使用 NIO 完成网络通信, 两种, 有返回值和没返回值的, 仍然会阻塞的形式
### 11. NIO_非阻塞式
    使用 NIO 完成网络通信, 这次是非阻塞的
    通过调用Selector.open() 方法创建一个Selector
    向选择器注册通道：SelectableChannel.register(Selector sel, int ops)
    可以监听的事件类型（可使用SelectionKey 的四个常量表示）
    若注册时不止监听一个事件，则可以使用“位或”操作符连接
### 12. NIO_DatagramChannel
    DatagramChannel是一个能收发UDP包的通道
### 13. NIO_Pipe 管道
    