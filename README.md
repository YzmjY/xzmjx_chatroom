## 浏览器聊天室
- 使用websocket协议，相对于http1.1，websocket可以实现主动向客户端推送消息，而不用客户端轮询来拉取聊天室其他成员的消息
- 消息协议格式如下，传输格式采用json  
//1. login协议。  
//Client: {type: "login_request", "name": "昵称"}  
//Server: {type: "login_response", result: 200, msg: "ok"}  
//  
//2. send协议。  
//Client：{type: "send_request", "msg" : "消息"}  
//Server: {type: "send_response", result: 200, msg: "ok"}  
//  
//3. user_enter 通知  
//        {type: "user_enter", msg: "xxx 加入聊天室", time:xxx}  
//  
//4. user_leave 通知  
//        {type: "user_leave", msg: "xxx 离开聊天室", time:xxx}  
//  
//5. msg 通知  
//        {type: "msg", msg: "具体聊天信息", user: "xxx", time: xxxx}    
  
- 网络框架使用xzmjx（仿照sylar项目写的），聊天室程序以动态库.so的形式被框架程序加载
