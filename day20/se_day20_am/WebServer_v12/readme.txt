本版本改动:
HTTP协议要求，以地址栏形式传递数据时，是不能含有中文
的。(请求行，消息头中的内容都不能有中文)
为此，当我们希望从客户端传递中文时，常见办法是先将中文
以对应的字符集转换为2进制，然后在将每个字节的2进制内容
以2位16进制形式表示，前面加一个%，这样每个字节的内容
就可以以字符串"%XX"的形式表示一个字节内容。这种形式避
免了传递中文的问题。
那么在服务端接收到这样的数据后，我们还要进行一个反向的
操作，将%XX的内容还原为2进制，再按照指定字符集转换为
对应的文字。JAVA提供了API：URLDecoder，可以很方便的
解决这个问题。
     
将HttpRequest中的进一步解析URL的操作改进一下，在获取
到queryString后使用URLDecoder对内容进行转码。 
 
 
 
 
 
 
 
 
 
 
    
    
    
    