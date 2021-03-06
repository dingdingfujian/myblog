# WebSocket

### 简介
WebSocket是一种建立在TCP连接之上的全双工通信协议。2011年被IETF定为标准RFC 6455，并由RFC7936补充规范。
WebSocket使得客户端与服务器端之间的数据交换变得简单，允许服务器主动向客户端推送数据。在WebSocket API中，客户端和服务器之间只要完成一次握手就可以建立持久性连接，进行双向数据传输。
### 特点及优点
1. 建立在TCP连接之上。
2. 使用HTTP1.1进行握手。
3. 默认端口与HTTP一样，分别是80和443，分别对应ws和wss协议头。
4. 没有同源策略的限制，客户端可以直接与任何服务器通信。

1. 较少的控制开销。在连接建立后，在客户端和服务器端之间交换数据时，用于协议控制的数据头部相对较小。
2. 更强的实时性，支持服务器推送，可以双向通信。由于协议是全双工的，所以服务器可以随时主动给客户端下发数据。
3. 保持连接状态。与 HTTP 不同的是，WebSocket 需要先建立连接，这使得其成为一种有状态的协议（HTTP 为无状态协议）。之后的通信可以省略部分状态信息。
4. 更好的二进制支持。WebSocket定义了二进制帧（HTTP 2.0也有二进制帧），相对 HTTP 1.1，可以更好地处理二进制内容。
5. 可以支持扩展。WebSocket定义了扩展，用户可以扩展协议，实现自定义子协议。
6. 更好的压缩性。相对于 HTPP 压缩，WebSocket可以在适当的扩展支持下可以沿用之前内容的上下文，在传递类似数据的时候，可以显著提高压缩率。
7. 多路复用。不同的 URI 可以使用同一个WebSocket 连接。

### 原理
参见[WebSocket 是什么原理？为什么可以实现持久连接？](https://www.zhihu.com/question/20215561)简短的讲就是：通常客户端（A）发送的 HTTP请求是要经过nginx服务器（接线员B）处理然后再传给相应的处理程序（客服C）的。B 的处理速度非常快，因此A 与 B 之间的连接非常廉价。但是 C 的处理能力就比较慢了。而 WebSocket 只需要维持 A 与 B 之间的连接即可，一旦C 有消息就通知 B 而不用一直被 A 的连接占用。长轮询则需要维持 A 与 C 的连接，一旦并发量变大，C 的资源就容易耗尽。



