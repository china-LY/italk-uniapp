# iTalk-社交App

## 快速预览

> 项目名称：iTalk
>
> 开发人员：熙子黒
>
> 更新日期：2021-05-16
>
> 开源协议：MTI

#### 项目介绍

> - QQ、VX的结合
> - 即时通讯技术
> - 全栈架构
> - UI规范化
>
> 
>
> 项目地址：http://italk.aoau.top
>
> 更多项目请访问：http://www.aoau.top

#### 技术栈

前端：`vue`+`uni-app`+`sass`

后端：`Nodejs(express)`+`mongoDB`

通信：`Websocket(socket.io)`

> **Why uni-app?**
>
> 1.简洁的跨平台开发框架，一次开发多平台上线（Android、ios、小程序）。
>
> 2.开发前置条件低，只需掌握`vue`即可快速上手。
>
> **Why  websocket？**
>
> 1.不同于`http`协议，详情查看官网。
>
> 2.服务端与客户端双向数据绑定。
>
> 3.封装的`socket.io`库简洁API，方便快速上手。
>
> 4.此项目为本人学习websocket项目，以准备后期开发物联网项目打基础。
>
> **Why express？**
>
> 1.`express`是基于`nodejs`标准库`http`封装的web后端框架，方便前端人员快速开发，学习成本较低。

#### Development Tool

`HBuilderX`+`WebStorm`

#### Developing HJ

`windows`+`linux`

## Project

```javascript
┌- 
├-	config/					// 配置文件
    ├-	db.js				// 连接数据库配置
    ├-  
├-	model/					// 数据模型
    ├-	
├-	middleware/				// 中间件
    ├-	err.js				// 错误处理中间件
├-	router/					// 后端路由
    ├-	index.js
├-	server/					// 
    ├-
├-	dao/					//
    ├-
├-	app.js					// 入口
├-	package.json			 // 版本控制
├-	package-lock.json		 // 版本控制
├-	README.md				// readme
└-	

```

### 1.Plugins插件

|        包        |  版本   |        备注        |
| :--------------: | :-----: | :----------------: |
|     **cors**     |  2.8.5  |      跨域处理      |
|   **express**    | 4.17.1  |      web框架       |
|   **mongoose**   | 5.12.10 |       数据库       |
| **require-all**  |  3.0.0  | 加载目录下所有文件 |
| **body-parser**  | 1.19.0  |    获取前端数据    |
|  **nodemailer**  |  6.6.0  |      邮箱插件      |
|   **bcryptjs**   |  2.4.3  |      密码加密      |
| **jsonwebtoken** |  8.5.1  |   token身份验证    |
|                  |         |                    |

> **加粗**为后端插件



### 2.前端路由

|       路由       | 参数 |  类型   |    备注    |
| :--------------: | :--: | :-----: | :--------: |
|      /index      |  /   |         |    首页    |
|     /signin      |  /   |         |   登录页   |
|     /signup      |  /   |         |   注册页   |
| /userhome?id=xxx |  id  | Num/Str | 用户唯一id |
|     /search      |  /   |         |  好友搜索  |



### 3.交互逻辑

| 标题           | 逻辑                                                         | 备注 |
| -------------- | :----------------------------------------------------------- | ---- |
| 前后端交互流程 | **前端发送请求** `→` **匹配后端路由** `→` **server处理函数** `→` **dbserver CRUD** `∞` **db** |      |
| 前后端交互验证 | 1. 登陆时，客户端发送用户名密码<br/>2. 服务端验证用户名密码是否正确，校验通过就会生成一个有时效的token串，发送给客户端<br/>3. 客户端储存token,一般都会存储在localStorage或者cookie里面<br/>4. 客户端每次请求时都带有token，可以将其放在请求头里，每次请求都携带token<br/>5. 服务端验证token，所有需要校验身份的接口都会被校验token，若token解析后的数据包含用户身份信息，则身份验证通过，返回数据<br/> |      |





## Schema

### 用户

|  字段   | 类型 |   备注   |
| :-----: | :--: | :------: |
|   _id   | str  |    id    |
|  name   | str  |  用户名  |
|  email  | str  |   邮箱   |
|   psw   | num  |   密码   |
|   sex   | str  |   性别   |
|  birth  | str  |   生日   |
|  phone  | str  |   电话   |
| explain | str  |   签名   |
| imgurl  | str  | 头像地址 |
|  time   | str  | 注册时间 |
|  grade  | str  | 用户等级 |
|         |      |          |



### 好友

|   字段   | 类型 |                     备注                      |
| :------: | :--: | :-------------------------------------------: |
|   _id    | str  |                      id                       |
|  userID  | str  |                    用户id                     |
| friendID | str  |                    好友id                     |
|   time   | str  |                   生成时间                    |
|  stete   | num  | 好友状态(0 已为好友，1 申请中，2 对方未同意 ) |
|          |      |                                               |



### 私聊消息

|   字段   | 类型 |               备注                |
| :------: | :--: | :-------------------------------: |
|   _id    | str  |                id                 |
|  userID  | str  |             发送者id              |
| friendID | str  |             接受者id              |
| message  | str  |             发送内容              |
|  types   | str  | 内容类型(0文字,1图片,2音频,3定位) |
|   time   | date |             发送日期              |
|  state   | num  |      消息状态(0已读，1未读)       |
|          |      |                                   |



### 群

|   字段   | 类型 |   备注   |
| :------: | :--: | :------: |
|   _id    | str  |    id    |
|  userID  | str  |  群主id  |
|   name   | str  |   群名   |
|  imgurl  | str  |  群封面  |
|  notice  | str  |  群说明  |
|  notice  | str  |  群公告  |
|   time   | date | 创建日期 |
| groupNum | str  |   群号   |



### 群消息

|  字段   | 类型 |   备注   |
| :-----: | :--: | :------: |
|   _id   | str  |    id    |
| groupID | str  |   群id   |
| userID  | str  | 发送者id |
| message | str  | 发送内容 |
|  time   | date | 发送时间 |
|  types  | str  | 内容类型 |
|         |      |          |

### 群成员

|  字段   | 类型 |         备注          |
| :-----: | :--: | :-------------------: |
|   _id   | str  |          id           |
| groupID | str  |         群id          |
| userID  | str  |        用户id         |
|  name   | str  |       群内昵称        |
|  time   | date |       加入日期        |
|   tip   | num  |      未读消息数       |
| shield  | num  | 免打扰(0不屏蔽,1屏蔽) |





## API DOC

> baseURL: 
>
> 
>
> 注：所有接口名对应路由调用的api



### signUp

描述：注册用户

地址：`/signup/add`

请求方式：**POST**

参数：

| 字段 | 类型 |  说明  | 必需 |
| :--: | :--: | :----: | :--: |
| name | str  | 用户名 |  是  |
| mail | str  |  邮箱  |  是  |
| pwd  | str  |  密码  |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | num  | 状态码 |  是  |

示例：

```javascript
{
    
}
```



### judgeValue

描述：查询用户是否存在

地址：`/signup/judge`

请求方式：**POST**

参数：

| 字段 | 类型 |     说明      | 必需 |
| :--: | :--: | :-----------: | :--: |
| data | str  |  用户名/邮箱  |  是  |
| type | str  | `name`/`mail` |  是  |

返回值：

|  字段  | 类型 |          说明          | 必需 |
| :----: | :--: | :--------------------: | :--: |
| status | num  |         状态码         |  是  |
| result | str  | `0`存在 或 `>0`:不存在 |  是  |

示例：

```javascript
{
    "status":200,
    "result":1
}
```



### signIn

描述：登陆

地址：`/signin/match`

请求方式：**POST**

参数：

| 字段 | 类型 |    说明     | 必需 |
| :--: | :--: | :---------: | :--: |
| data | str  | 用户名/邮箱 |  是  |
| psw  | str  |    密码     |  是  |

返回值：

|  字段  | 类型 |  说明   | 必需 |
| :----: | :--: | :-----: | :--: |
| status | num  | 状态码  |  是  |
|  name  | str  | 用户名  |  是  |
| imgurl | str  | 头像url |  是  |
| token  | str  |  token  |  是  |
|   id   | str  | 用户id  |  是  |

示例：

```javascript
{
    "status":200,
    "back":{
        "id":"60a9cb976d91641d68733adf",
        "name":"西西",
        "imgurl":"user.jpg",
        "token":"后端生成的token"
    }
}
```



### searchUser

描述：搜索用户

地址：/search/user

请求方式：**POST**

参数：

| 字段 | 类型 |  说明  | 必需 |
| :--: | :--: | :----: | :--: |
| data | str  | 搜索词 |  是  |

返回值：

|  字段  | 类型 |   说明   | 必需 |
| :----: | :--: | :------: | :--: |
| status | str  |  状态码  |  是  |
| result | str  | 用户数据 |  是  |

示例：

```javascript
{
    "status":200,
    "result":[
        {
      	 "imgurl":"user.jpg",
     	 "_id":"60a9cb976d91641d68733adf",
      	 "name":"西西",
      	 "email":"123456@qq.com"
        },
        {
          "imgurl":"user.jpg",
          "_id":"60aa4245fc3f843660404cc8",
          "name":"哥哥",
          "email":"123456789@qq.com"
        }
    ]
}
```



### isFriend

描述：是否为好友

地址：/search/isfriend

请求方式：**POST**

参数：

| 字段 | 类型 |    说明    | 必需 |
| :--: | :--: | :--------: | :--: |
| uid  | str  |   用户名   |  是  |
| fid  | str  | 搜索对象id |  是  |

返回值：

|  字段  | 类型 |     说明      | 必需 |
| :----: | :--: | :-----------: | :--: |
| status | str  | 状态码200/400 |  是  |

示例：

```javascript
{
    
}
```



### searchGroup

描述：搜索群

地址：/search/group

请求方式：**POST**

参数：

| 字段 | 类型 |  说明  | 必需 |
| :--: | :--: | :----: | :--: |
| data | str  | 搜索词 |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | str  | 状态码 |  是  |
|  name  | str  |  群名  |  是  |
|  _id   | str  |  群id  |  是  |
| imgurl | str  | 群头像 |  是  |

示例：

```javascript
{
    
}
```



### isInGroup

描述：是否在群内

地址：/search/isingroup

请求方式：**POST**

参数：

| 字段 | 类型 |  说明  | 必需 |
| :--: | :--: | :----: | :--: |
| uid  | str  | 用户id |  是  |
| gid  | str  |  群id  |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | str  | 状态码 |  是  |

示例：

```javascript
{
    
}
```





### isFriend

描述：

地址：

请求方式：**POST**

参数：

| 字段 | 类型 |  说明  | 必需 |
| :--: | :--: | :----: | :--: |
| name | str  | 用户名 |  是  |
| mail | str  |  邮箱  |  是  |
| pwd  | str  |  密码  |  是  |

返回值：

| 字段 | 类型 | 说明 | 必需 |
| :--: | :--: | :--: | :--: |
|      | str  |      |  是  |
|      | str  |      |  是  |

示例：

```javascript
{
    
}
```

### isFriend

描述：

地址：

请求方式：**POST**

参数：

| 字段 | 类型 |  说明  | 必需 |
| :--: | :--: | :----: | :--: |
| name | str  | 用户名 |  是  |
| mail | str  |  邮箱  |  是  |
| pwd  | str  |  密码  |  是  |

返回值：

| 字段 | 类型 | 说明 | 必需 |
| :--: | :--: | :--: | :--: |
|      | str  |      |  是  |
|      | str  |      |  是  |

示例：

```javascript
{
    
}
```

