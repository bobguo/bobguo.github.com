<htm
由于移动终端调用服务器的接口需要用的oauth认证，oauth认证中需要对url和请求参数进行签名服务端对签名进行检验（防止伪造）。

在签名及签名验证中重要的一步就是对url和参数进行拼装，然后加密。所以需要保证服务端收到的http url地址和客户端发送的url地址一致。由于客户端和后端应用服务器之间有代理服务器，所以后端服务器获取客户端使用的url时，域名以及协议和端口号需要通过proxy相关的http头来传递。

在代理服务器上需要设置的http头如下(以ngnix的配置指令为例)：
<code>
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Proto https;
</code>
