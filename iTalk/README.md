# iTalk-聊天app

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

| 主要插件 | 应用 | 备注 |
| :------: | :--: | :--: |
|          |      |      |
|          |      |      |
|          |      |      |

#### 开发工具

`HBuilderX`+`WebStorm`

#### 开发环境

`windows`+`linux`



#### 功能目录



## 开发文档

### 一、前端

#### 1. 主题定制

> uni.scss文件

- `行为相关颜色`

- `文字基本颜色`
- `背景颜色`
- `边框颜色 `
- `文字尺寸`
- `图片尺寸`
- `Border Radius`
- rpx布局

#### 2.前端路由

|       路由       | 参数 |  类型   |    备注    |
| :--------------: | :--: | :-----: | :--------: |
|      /index      |  /   |         |    首页    |
|     /signin      |  /   |         |   登录页   |
|     /signup      |  /   |         |   注册页   |
| /userhome?id=xxx |  id  | Num/Str | 用户唯一id |
|     /search      |  /   |         |  好友搜索  |





### 二、后端



### 三、联调



### 四、部署



### 五、方法函数

```js
/*
  函数：首页时间处理
  参数：
  	data 消息日期
  逻辑：
  	当天：时/分
  	前天：‘前天’ 时/分
  	大于2天：年/月/日
*/

dataTime(d) {
    let old = new Date(d)
    let now = new Date()
    // 获取old时间
    // let d = old.getTime()
    let h = old.getHours()
    let m = old.getMinutes()
    let Y = old.getFullYear()
    let M = old.getMonth()+1
    let D = old.getDate()-1
    // 获取now时间
    let nd = now.getTime()
    let nh = now.getHours()
    let n = now.getMinutes()
    let nY = now.getFullYear()
    let nM = now.getMonth()+1
    let nD = now.getDate()

    // 消息是当天，则显示:小时+分钟
    if (D===nD && M===nM && Y===nY) {
        if(h<10) h='0'+h
        if(m<10) m='0'+m
        return h+':'+m
    }
    // 消息是前天
    if (D+1===nD && M===nM && Y===nY) {
        if(h<10) h='0'+h
        if(m<10) m='0'+m
        return '前天 '+h+':'+m
    } else {
        // 消息大于两天
        return Y+'/'+M+'/'+D
    }
}
```

