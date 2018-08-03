# Token验证
token 验证是无状态的，服务器不记录哪些用户登录了或者哪些 JWT 被发布了，而是每个请求都带上了服务器需要验证的 token，token 放在了 Authorization header 中，形式是 Bearer { JWT }，但是也可以在 post body 里发送，甚至作为 query parameter。

## 验证流程：

1，客户端使用用户名跟密码请求登录

2，服务端收到请求，去验证用户名与密码

3，验证成功后，服务端会签发一个 Token，再把这个 Token 发送给客户端

4，客户端收到 Token 以后可以把它存储起来，比如放在 Cookie 里或者 Local Storage 里

5，客户端每次向服务端请求资源的时候需要带着服务端签发的 Token

6，服务端收到请求，然后去验证客户端请求里面带着的 Token，如果验证成功，就向客户端返回请求的数据


