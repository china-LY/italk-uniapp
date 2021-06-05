# 小舍App开发文档

[TOC]



## 快速预览

> 项目名称：小舍-社交app
> 
> 开发人员：熙子黒
> 
> 更新日期：2021-05-24
> 
> 开源协议：MIT
> 
> 有任何疑问请联系邮箱：2421662954@qq.com，并注明来意。
> 
> 请勿商用！

### 功能介绍

> - QQ、VX结合的聊天社交app
> - 即时通讯技术
> - 全栈架构
> - UI规范化
>
> 项目地址：http://italk.aoau.top （建议移动设备访问）
> 
> apk自提：https://pan.baidu.com/s/14i6yiGFdAuQgSCcQbcU45w  提取码：`q29u`
>
> 更多项目请访问：http://www.aoau.top

**登陆界面**

- [x] 支持用户名/邮箱匹配登陆
- [x] 实时反馈匹配结果
- [x] 密码校验

**注册界面**

- [x] 支持用户名/邮箱已存在提示
- [x] 支持提示表单项是否填写完整
- [x] 密码复杂度反馈

**主页界面**

- [x] 好友消息提示
- [x] 好友申请提示
- [x] 最后一条消息及发送时间渲染
- [x] 最新消息排序
- [ ] 群消息提示
- [ ] 群与好友列表渲染优先级
- [ ] 大厅入口（无需创建群聊）

**搜索界面**

- [x] 正则匹配查询数据库
- [x] 搜索所有注册用户
- [x] 正则匹配渲染指定字符（串）
- [x] 添加好友功能
- [ ] 私聊窗口入口

**资料卡界面**

- [x] 好友昵称、备注、个性签名渲染
- [ ] 私聊窗口入口
- [x] 好友详情界面入口

**详情界面**

- [x] 用户详情修改（头像、签名、昵称、性别、生日、电话、邮箱）
- [ ] 用户密码修改
- [x] 修改存储数据库
- [x] 退出登录功能
- [x] 删除好友功能

**好友私聊窗口**

- [x] 发送文字消息
- [x] 发送图片消息
- [ ] 发送语音消息（兼容性）
- [x] 发送定位消息（未完善）
- [x] 发送表情消息
- [x] 拍摄照片功能
- [ ] 发送文件消息
- [ ] 发送视频消息

**好友动态**

- [ ] 动态列表渲染
- [ ] 动态详情查看
- [ ] 分享动态消息





### 技术栈

前端：`vue`+`uni-app`+`sass`

后端：`Nodejs(express)`+`mongoDB`

通信：`Websocket(socket.io)`

**Development Tool**: `HBuilderX`+`WebStorm`

**Developing env**: `Windows`开发+`Linux(Nginx)`部署

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



## Project

### 项目目录

> 暂未完善
> 
**前端**

```javascript
┌- 
├-	commons/					// 配置文件
    ├-	db.js				// 连接数据库配置
    ├-  
├-	components/					// 数据模型
    ├-	
├-	pages/				// 中间件
    ├-	err.js				// 错误处理中间件
├-	static/					// 后端路由
    ├-	index.js
├-	App.vue					// 
├-	main.js						//
├-	pages.json				// 入口
├-	manifest.json
├-	project.config.json			 // 版本控制
├-	uni.scss		 // 版本控制
├-	README.md				// readme
└-	
```

**后端**

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

### 插件

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
|    **multer**    |  1.4.2  |    文件上传插件    |
|  **socket.io**   |  2.3.0  |    后端通讯模块    |
| weapp.socket.io  |  2.0.6  |    前端通讯模块    |

> 后端插件



### 前端路由

|       路由       | 参数 |  类型   |    备注    |
| :--------------: | :--: | :-----: | :--------: |
|      /index      |  /   |         |    首页    |
|     /signin      |  /   |         |   登录页   |
|     /signup      |  /   |         |   注册页   |
| /userhome?id=xxx |  id  | Num/Str | 用户唯一id |
|     /search      |  /   |         |  好友搜索  |



### 交互逻辑

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
|   time   | date |                   生成时间                    |
|  state   | num  | 好友状态(0 已为好友，1 申请中，2 对方未同意 ) |
| lastTime | date |               最后一条消息时间                |



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

|   字段   | 类型 |         备注          |
| :------: | :--: | :-------------------: |
|   _id    | str  |          id           |
| groupID  | str  |         群id          |
|  userID  | str  |        用户id         |
|   name   | str  |       群内昵称        |
|   time   | date |       加入日期        |
|   tip    | num  |      未读消息数       |
|  shield  | num  | 免打扰(0不屏蔽,1屏蔽) |
| lastTime | date |   最后一条消息时间    |





## API DOC

> baseURL: 
>
> 注：所有接口名对应路由调用的api



### 1.signUp

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



### 2.judgeValue

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



### 3.signIn

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



### 4.searchUser

描述：搜索用户

地址：`/search/user`

请求方式：**POST**

参数：

| 字段  | 类型 |  说明  | 必需 |
| :---: | :--: | :----: | :--: |
| data  | str  | 搜索词 |  是  |
| token | str  |  验证  |  是  |

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



### 5.isFriend

描述：是否为好友

地址：`/search/isfriend`

请求方式：**POST**

参数：

| 字段  | 类型 |    说明    | 必需 |
| :---: | :--: | :--------: | :--: |
|  uid  | str  |   用户名   |  是  |
|  fid  | str  | 搜索对象id |  是  |
| token | str  |    验证    |  是  |

返回值：

|  字段  | 类型 |     说明      | 必需 |
| :----: | :--: | :-----------: | :--: |
| status | str  | 状态码200/400 |  是  |

示例：

```javascript
{
    
}
```



### 6.searchGroup

描述：搜索群

地址：/search/group

请求方式：**POST**

参数：

| 字段  | 类型 |  说明  | 必需 |
| :---: | :--: | :----: | :--: |
| data  | str  | 搜索词 |  是  |
| token | str  |  验证  |  是  |

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



### 7.isInGroup

描述：是否在群内

地址：/search/isingroup

请求方式：**POST**

参数：

| 字段  | 类型 |  说明  | 必需 |
| :---: | :--: | :----: | :--: |
|  uid  | str  | 用户id |  是  |
|  gid  | str  |  群id  |  是  |
| token | str  |  验证  |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | str  | 状态码 |  是  |

示例：

```javascript
{
    
}
```





### 8.userDetial

描述：用户详情

地址：`/user/detial`

请求方式：**POST**

参数：

| 字段  | 类型 |  说明  | 必需 |
| :---: | :--: | :----: | :--: |
|  id   | str  | 用户id |  是  |
| token | str  |  验证  |  是  |

返回值：

|  字段  | 类型 |     说明     | 必需 |
| :----: | :--: | :----------: | :--: |
| status | str  |    状态码    |  是  |
|  data  | obj  | 用户详情数据 |  是  |

示例：

```javascript
{
    data:{
        result:{
           	 createdAt:"2021-05-23T11:53:41.100Z"
			email:"242166@qq.co"
             imgurl:"user.jpg"
			name:"小花"
			sex:"asexual"
			time:"2021-05-23T11:53:41.090Z"
			updatedAt:"2021-05-25T08:20:01.765Z"
			_id:"60aa4245fc3f843660404cc8"
        }
    }
}
```

### 9.userUpdate

描述：用户信息修改

地址：`/user/update`

请求方式：**POST**

参数：

| 字段  | 类型 |   说明   | 必需 |
| :---: | :--: | :------: | :--: |
|  id   | str  |  用户id  |  是  |
| token | str  |   验证   |  是  |
| data  | str  | 修改内容 |  是  |
|  psw  | str  |   密码   |  是  |
| type  | str  | 修改类型 |  是  |

返回值：

|  字段  | 类型 |           说明            | 必需 |
| :----: | :--: | :-----------------------: | :--: |
| status | str  | 状态码200/300/400/500/201 |  是  |

示例：

```javascript
200：修改成功
300：用户名已存在，修改失败
400：失败
500：报错
201：邮箱已存在
{
    
}
```



### 10.getMarkName

描述：获取好友昵称

地址：`/user/getmarkname`

请求方式：**POST**

参数：

| 字段 | 类型 |  说明  | 必需 |
| :--: | :--: | :----: | :--: |
| uid  | str  | 用户id |  是  |
| fid  | str  | 好友id |  是  |
|      |      |        |      |

返回值：

|  字段  | 类型 |     说明      | 必需 |
| :----: | :--: | :-----------: | :--: |
| status | str  | 状态码200/500 |  是  |
| result | obj  |     昵称      |  是  |

示例：

```javascript
{
    
}
```





### 11.updateMarkName

描述：好友昵称修改

地址：`/user/updatemarkname`

请求方式：**POST**

参数：

| 字段  | 类型 |     说明     | 必需 |
| :---: | :--: | :----------: | :--: |
| token | str  |     校验     |  是  |
| data  | str  | uid/fid/name |  是  |

返回值：

|  字段  | 类型 |     说明      | 必需 |
| :----: | :--: | :-----------: | :--: |
| status | str  | 状态码200/500 |  是  |

示例：

```javascript
{
    
}
```



### 12.applyFriend

描述：*申请好友*

地址：`/friend/apply`

请求方式：**POST**

参数：

| 字段  | 类型 |    说明     | 必需 |
| :---: | :--: | :---------: | :--: |
| token | str  |    校验     |  是  |
| data  | str  | uid/fid/msg |  是  |
|  msg  | str  |   请求词    |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | str  | 状态码 |  是  |

示例：

```javascript
{
    
}
```



### 13.updateFriendState

描述：*更新好友关系（同意）*

地址：`/friend/updatefriendstate`

请求方式：**POST**

参数：

| 字段  | 类型 |  说明   | 必需 |
| :---: | :--: | :-----: | :--: |
| token | str  |  校验   |  是  |
| data  | str  | uid/fid |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | str  | 状态码 |  是  |

示例：

```javascript
{
    
}
```



### 14.deleteFriend

描述：*好友状态更新（拒绝/删除）*

地址：`/friend/deletefriend`

请求方式：**POST**

参数：

| 字段  | 类型 |  说明   | 必需 |
| :---: | :--: | :-----: | :--: |
| token | str  |  校验   |  是  |
| data  | str  | uid/fid |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | str  | 状态码 |  是  |

示例：

```javascript
{
    
}
```



### 15.*upload

描述：文件上传

地址：`/files/upload`

请求方式：**POST**

参数：

| 字段 | 类型 |              说明               | 必需 |
| :--: | :--: | :-----------------------------: | :--: |
| url  | str  | 文件保存目录（/user/group/...） |  是  |
| name | str  |             文件名              |  是  |

返回值：

| 字段 | 类型 |     说明     | 必需 |
| :--: | :--: | :----------: | :--: |
| name | str  | 保存的文件名 |  是  |

示例：

```javascript
{
    
}
```





### 16.getFriend

描述：*获取好友列表*

地址：`/index/getfriend`

请求方式：**POST**

参数：

| 字段  | 类型 |   说明   | 必需 |
| :---: | :--: | :------: | :--: |
|  uid  | str  |  用户id  |  是  |
| state | str  | 关系状态 |  是  |
| token | str  |   校验   |  是  |

返回值：

|  字段  | 类型 |       说明        | 必需 |
| :----: | :--: | :---------------: | :--: |
| status | str  |      状态码       |  是  |
| result | str  |     好友数据      |  是  |
|  type  | num  | 0：好友 / 1：群聊 |  是  |

示例：

```javascript
{
    id: ver.friendID._id,
    name: ver.friendID.name,
    markname: ver.markname,
    imgurl: ver.friendID.imgurl,
    lastTime: ver.lastTime,
}
```





### 17.getLastMsg

描述：*获取最后一条好友消息*

地址：`/index/getlastmsg`

请求方式：**POST**

参数：

| 字段  | 类型 |  说明  | 必需 |
| :---: | :--: | :----: | :--: |
| token | str  |  校验  |  是  |
|  uid  | str  | 用户id |  是  |
|  fid  | str  | 好友id |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | str  | 状态码 |  是  |
| result | str  |        |  是  |

示例：

```javascript
{
    message: ver.message,
      types: ver.types,
      time: ver.time,
}
```





### 18.unreadMsg

描述：*获取好友未读消息数*

地址：`/index/updatemsg`

请求方式：**POST**

参数：

| 字段  | 类型 |   说明   | 必需 |
| :---: | :--: | :------: | :--: |
| token | str  |   校验   |  是  |
|  uid  | str  |  用户id  |  是  |
|  fid  | str  |  好友id  |  是  |
| state | num  | 消息状态 |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | str  | 状态码 |  是  |
| result | str  | 消息数 |  是  |

示例：

```javascript
{
    
}
```





### 19.updateMsg

描述：*更新好友未读消息数*

地址：`/index/updatemsg`

请求方式：**POST**

参数：

| 字段  | 类型 |   说明   | 必需 |
| :---: | :--: | :------: | :--: |
| token | str  |   校验   |  是  |
|  uid  | str  |  用户id  |  是  |
|  fid  | str  |  好友id  |  是  |
| state | num  | 消息状态 |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | str  | 状态码 |  是  |
|        | str  |        |  是  |

示例：

```javascript
{
    
}
```





### 20.getGroup

描述：*获取群列表*

地址：`/index/getgroup`

请求方式：**POST**

参数：

| 字段  | 类型 |  说明  | 必需 |
| :---: | :--: | :----: | :--: |
| token | str  |  校验  |  是  |
|  uid  | str  | 用户id |  是  |

返回值：

|  字段  | 类型 |       说明        | 必需 |
| :----: | :--: | :---------------: | :--: |
| status | str  |      状态码       |  是  |
| result | str  |                   |  是  |
|  type  | num  | 0：好友 / 1：群聊 |  是  |

示例：

```javascript
{
    gid: ver.groupID._id,
        name: ver.groupID.name,
        markname: ver.name,
        imgurl: ver.groupID.imgurl,
        lastTime: ver.lastTime,
        tip: ver.tip
}
```





### 21.getLastMsg

描述：*获取最后一条群消息*

地址：`/index/getlastgroupmsg`

请求方式：**POST**

参数：

| 字段  | 类型 | 说明 | 必需 |
| :---: | :--: | :--: | :--: |
| token | str  | 校验 |  是  |
|  gid  | str  | 群id |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | str  | 状态码 |  是  |
| result | str  |        |  是  |

示例：

```javascript
{
    message: ver.message,
      types: ver.types,
      time: ver.time,
      name: ver.userID.name // 谁发的
}
```





### 22.updateGroupMsg

描述：*更新群未读消息数*

地址：`/index/updategroupmsg`

请求方式：**POST**

参数：

| 字段  | 类型 |  说明  | 必需 |
| :---: | :--: | :----: | :--: |
| token | str  |  校验  |  是  |
|  uid  | str  | 用户id |  是  |
|  gid  | str  |  群id  |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | str  | 状态码 |  是  |

示例：

```javascript
{
    
}
```





### 23.msg

描述：*聊天消息分页查询*

地址：`/chat/msg`

请求方式：**POST**

参数：

|   字段   | 类型 |     说明     | 必需 |
| :------: | :--: | :----------: | :--: |
|  token   | str  |     校验     |  是  |
|   uid    | str  |    用户id    |  是  |
|   fid    | str  |    好友id    |  是  |
| nowPage  | num  |   当前页数   |  是  |
| pageSize | num  | 每页消息条数 |  是  |

返回值：

|  字段  | 类型 |  说明  | 必需 |
| :----: | :--: | :----: | :--: |
| status | str  | 状态码 |  是  |
| result | str  |        |  是  |

示例：

```javascript
{
    id: ver._id,
    messagee: ver.message,
    types: ver.types,	// 消息类型
    time: ver.time,

    fromId: ver.userID._id,
    imgurl: ver.userID.imgurl,
}
```



