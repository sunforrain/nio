# nio
java8 nio使用的总结
## 目录
### 1. NIO_NIO 与 IO 区别
     *	NIO支持面向缓冲区的、基于通道的IO操作
     *  IO						        NIO
     *  面向流(Stream Oriented)			面向缓冲区(Buffer Oriented)
     *  阻塞IO(Blocking IO)				非阻塞IO(NonBlocking IO)
     *  (无)							选择器(Selectors)
### 2. NIO_缓冲区(Buffer)的数据存取
    缓冲区（Buffer）：在 Java NIO 中负责数据的存取。缓冲区就是数组。用于存储不同数据类型的数据