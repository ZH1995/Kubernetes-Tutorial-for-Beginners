#### 1. 为什么使用微服务

传统大单体服务编译慢，影响多人开发的进度。

#### 2. 微服务设计模式

[微服务设计12要素](https://12factor.net/)

#### 3. 微服务的好处

微服务利于维护，降低组件间的耦合度。

#### 4. JWT（Json Web Token）

[官网](https://jwt.io/)

服务器和客户端进行安全信息传输的加密串。

**使用场景：**

（1）鉴权：单点登录后返回JWT，后续客户端的所有请求都携带JWT作为准入标记。

（2）信息交换：通过公钥/密钥对传输的信息加密。

**结构组成：**

形如xxxx.yyyy.zzzz，分别代表Header、Payload、Signature。



###### Header

```json
{
    "alg"： "HS256",
    "typ": "JWT"
}
```

然后将上面的对象进行Base64Url编码得到JWT的第一部分。

###### Payload

```json
{
    "sub": "1234567890",
    "name": "John Doe",
  	"admin": true
}
```

然后将上面的对象进行Base64Url编码得到JWT的第二部分。

###### Signature

```bash
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```

第一部分+第二部分+SK，使用加密算法得到签名。