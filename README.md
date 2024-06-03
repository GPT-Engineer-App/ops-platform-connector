# ops-platform-connector

需要构建一个运维平台A，对接另一个运维平台B，A平台调用B平台一个接口 /getTicket ，10分钟后B平台调用A平台的接口/getStatus，返回状态数据和人员数据，A平台接口使用jwt认证，现在需要使用fastapi 构建一个服务，给出sql 表设计，及具体代码
建立用户表，用户表添加权限字段，可选字段为 admin  manager  engineer  default，并将所有表添加 自增ID 创建时间 更新时间 是否删除，且创建时间和更新时间自动填写
创建一个api验证中间层，需要验证用户名是否相等且用户密码为密钥xxxxxx+加上密码的md5加密，后查询该用户的权限是否为 admin， 方可登录
创建一个API访问中间层，创建用户访问记录表，记录所有用户的访问URL，访问参数，从访问到响应时间，访问结果，将所有返回结果统一为 {“code”: 200, "data": {}, "msg": "success"}, 访问状态解析code 是否为 200，取值为1，0
按照此逻辑，在该逻辑之前添加一个中间件，该中间件捕获异常信息，返回code 为 500，并记录到访问日志中

将上面的权限验证逻辑也同步到该中间件中，并豁免 /login /logout这两个路由
整理所有代码，分为4部分给我，一部分是模型定义文件，一部分是配置文件，一部分是具体代码，一部分是启动文件main.py

## Collaborate with GPT Engineer

This is a [gptengineer.app](https://gptengineer.app)-synced repository 🌟🤖

Changes made via gptengineer.app will be committed to this repo.

If you clone this repo and push changes, you will have them reflected in the GPT Engineer UI.

## Tech stack

This project is built with React and Chakra UI.

- Vite
- React
- Chakra UI

## Setup

```sh
git clone https://github.com/GPT-Engineer-App/ops-platform-connector.git
cd ops-platform-connector
npm i
```

```sh
npm run dev
```

This will run a dev server with auto reloading and an instant preview.

## Requirements

- Node.js & npm - [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating)
