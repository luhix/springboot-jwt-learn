
Simple demo with only 3 classes  

#### Please run example in *basic* folder;  
#### Then try to look at complete version in *complete* folder

#### JWT 

> header

jwt的头部承载两部分信息：

    声明类型，这里是jwt
    声明加密的算法 通常直接使用 HMAC SHA256

```
{
  'typ': 'JWT',
  'alg': 'HS256'
}
```

> playload
  
  
      载荷就是存放有效信息的地方。这个名字像是特指飞机上承载的货品，这些有效信息包含三个部分
      
      标准中注册的声明
      
      公共的声明: 公共的声明可以添加任何的信息，一般添加用户的相关信息或其他业务需要的必要信息.但不建议添加敏感信息，因为该部分在客户端可解密.
      
      私有的声明: 私有声明是提供者和消费者所共同定义的声明，一般不建议存放敏感信息，因为base64是对称解密的，意味着该部分信息可以归类为明文信息
  


>signature

    jwt的第三部分是一个签证信息，这个签证信息由三部分组成：
    
    header (base64后的)
    payload (base64后的)
    secret
    
    这个部分需要base64加密后的header和base64加密后的payload使用.连接组成的字符串，然后通过header中声明的加密方式进行加盐secret组合加密，然后就构成了jwt的第三部分


注意：secret是保存在服务器端的，jwt的签发生成也是在服务器端的，secret就是用来进行jwt的签发和jwt的验证，所以，它就是你服务端的私钥，在任何场景都不应该流露出去。一旦客户端得知这个secret, 那就意味着客户端是可以自我签发jwt了。

总的来说JWT不是为了解决内容加密问题的，JWT是解决用户会话问题的。


链接：https://www.jianshu.com/p/576dbf44b2ae
