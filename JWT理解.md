
# JSON Web Token（JWT）
JWT是一种开放标准（RFC 7519），它定义了一种紧凑且字自包含的标准，用于将各方之间的信息地传输为JSON对象。 该信息是通过数字签名进行验证。使用HMAC算法或使用RSA的公钥/私钥对JWT进行签名，所以它的安全性非常高。

JWT由三个部分组成，分别为“.”分隔，三部分组成如下：
* 		Header（头）
* 		Payload（有效载荷）
* 		Signature（签名） 

# Header
标题通常由两部分组成：令牌的类型，即JWT，以及使用的哈希算法，如HMAC SHA256或RSA。  比如：
{
  “alg”：“HS256”，
  “typ”：“JWT”
}
将header进行Base64 编码作为JWT的第一部分。

# Payload
这是JWT的第二部分，包含了用户的一些信息和Cliam(声明、权利)，有三种类型的Cliam：保留，公开和私人声明。  一个典型的payload应该如下：
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true

}
Reserved（保留声明），它的含义就像是编程语言的保留字一样，属于JWT规范中规定好的，这类声明不是必须的，但是是建议使用的。有以下几种：
    * 		iss: JWT的签发者 
    * 		sub: 该JWT所面向的用户 
    * 		aud:JWT的接收方 
    * 		exp(expires): 过期时间，这里是一个Unix时间戳 
    * 		iat(issued at): 签发时间，这里是一个Unix时间戳 
* Public （公共声明）：这类声明需要在 IANA JSON Web Token Registry 中定义或者提供一个URI，因为要避免重名等冲突。 
* Private（私有声明）：根据业务需要自己定义的数据了 




# Signature

要创建签名部分，需要使用到用Base64编码后header和payloader，以及秘钥，将它们签名，一个典型的格式如下： 

HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)



# JWT的优缺点与适用场景
## 优点
* 无状态。Token机制在服务端不需要存储session信息，因为Token 自身包含了所有登录用户的信息，只需要在客户端的cookie或本地介质存储状态信息. 
* 去耦。不需要绑定到一个特定的身份验证方案。Token可以在任何地方生成，只要在你的API被调用的时候，你可以进行Token生成调用即可. 
* 更适用于移动应用。 当你的客户端是一个原生平台时，Cookie是不被支持的（你需要通过Cookie容器进行处理），这时采用Token认证机制就会简单得多。 
* CSRF。因为不再依赖于Cookie，所以你就不需要考虑对CSRF的防范，但需要防范XSS。 
## 缺点
* 占用太多空间。上面提到 JWT存储在Web存储中会导致XSS攻击，那就只能存储在 Cookie 里了。但是，Cookie 的存储容量是有限制的（通常为 4 KB）。而JWT 占用的空间又不是那么小，尤其是在使用无状态 JWT 时，所有的数据都被放到 JWT 里，数据大小很快就会超过 Cookie 的容量限制。 
* 无法完全掌控JWT。使用了JWT，无法实现在服务器端对用户请求进行管理——管理员没法统计多少个人登录了，一个人登录了多少次，登陆了什么设备；同时，也无法强行“踢”掉一个用户的登录——JWT一旦生成，在失效之前，总是有效的。如果实现了一个token黑名单之类的功能，就等价于实现了Session机制，无状态带来的好处就无从谈起。这个限制对于任何一个要认真做用户风险控制的网站来说都是不可能接受的。 
* 数据实效性差。 JWT 一旦被生成，就不会再和服务端有任何瓜葛，一旦服务端中的相关数据更新，JWT 中存储的数据由于得不到更新，就变成了过期的数据。 
以上这些缺点都只针对无状态 JWT。如果使用有状态 JWT（JWT 中存储认证授权信息的 ID，具体数据存储在服务端），就可以规避这些缺点。不过，有状态 JWT 基本上等同于 Session / Cookie，没有存在价值。


* 可以使用Session也可以使用Token做认证，但是总是要保证服务器端可以管理Session，通过Session是否存在来最终确定认证的有效性 
* 将认证信息存放在标记为HttpOnly，Secure，Same-Site=strict的Cookie中，从而避免XSS和CSRF 
* 如果是传统的页面网站，请使用CSRF Token机制 
* 总是使用https，只要你的网络链路经过了公网 
* 保证token/session 必须有一个有效期 
* 不要用 JWT 来做 Web 应用的会话管理，请用 Session / Cookie 

		


