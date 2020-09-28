# 课表推送 API 接口文档

## API 接口说明

- 接口基准地址：``
- API 认证统一使用 Token 认证
- 需要授权的 API ，必须在请求头中使用 `Authorization` 字段提供 `token` 令牌
- 数据返回格式统一使用 JSON

### 支持的请求方法

- GET
- POST
### 通用返回状态说明

| *状态码* |         *含义*        |                        *说明*                       |
|----------|-----------------------|-----------------------------------------------------|
|      200 | OK                    | 请求成功                                            |
|      400 | FAILED                | 请求失败                                              |
|      401 | UNAUTHORIZED          | 未授权                                              |
|          |                       |                                                     |


---
## 注册

### 注册接口

* 请求路径：register
* 请求方法：post
* 请求参数

| 参数名   | 参数说明 | 备注     |
| -------- | -------- | -------- |
| username | 用户名称 | 不能为空 |
| password | 用户密码 | 不能为空 |
| mobile   | 手机号   | 不能为空 |
| type   | 类型   | 不能为空 |
| schoolnumber   | 校园网账号   | 不能为空 |
| college   | 学院   | 不能为空 |


* 响应参数

| 参数名   | 参数说明    | 备注 |
| -------- | ----------- | ---- |
| msg       | 返回消息     |      |
| status      | 请求状态 |      |


* 响应数据

```javascript
{
    "meta": {
        "msg": "注册成功",
        "status": 200
    }
}
```

## 登录

### 登录验证接口

* 请求路径：login
* 请求方法：post
* 请求参数

| 参数名   | 参数说明 | 备注     |
| -------- | -------- | -------- |
| username | 用户名   | 不能为空 |
| password | 密码     | 不能为空 |

* 响应参数

| 参数名   | 参数说明    | 备注            |
| -------- | ----------- | --------------- |
| id       | 用户 ID     |                 |
| username | 用户名      |                 |
| mobile   | 手机号      |                 |
| college  | 学院        |                 |
| type     | 类型        |老师为0 ,学生为1 |
| campusId | 校园网账号  |                |
| token    | 令牌        | 基于 jwt 的令牌 |
| msg       | 返回消息   |                |
| status    | 请求状态   |                |

* 响应数据

```javascript
{
    "data": {
        "id": 500,
        "username": "张三",
        "mobile": "123",
        "college": "",
        "type": "1",
        "campusId": "20183000000",
        "token": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1aWQiOjUwMCwicmlkIjowLCJpYXQiOjE1MTI1NDQyOTksImV4cCI6MTUxMjYzMDY5OX0.eGrsrvwHm-tPsO9r_pxHIQ5i5L1kX9RX444uwnRGaIM"
    },
    "meta": {
        "msg": "登录成功",
        "status": 200
    }
}
```

## 课表

### 课表数据接口
* 请求路径：timetable
* 请求方法：get
* 请求参数

| 参数名   | 参数说明 | 备注     |
| -------- | -------- | -------- |
|          |          |          |


* 响应参数

| 参数名   | 参数说明    | 备注            |
| -------- | ----------- | --------------- |
| username | 用户名      |                 |
| mobile   | 手机号      |                 |
| type     | 类型        |老师为0 ,学生为1 |
| campusId | 校园网账号  |                |
| timetable| 课表数据    |                |
| msg       | 返回消息   |                |
| status    | 请求状态   |                |

* 响应数据

```javascript
{
    "data": {
        "mobile": "123",
        "username": "张三",
        "type": "1",
        "campusId": "20183000000",
        "timetable": {}
    },
    "meta": {
        "msg": "获取成功",
        "status": 200
    }
}
```


### xls文件上传

* 请求路径：upload
* 请求方法：post
* 请求参数

| 参数名 | 参数说明 | 备注 |
| ------ | -------- | ---- |
| file   | 上传文件 |      |

* 响应参数

| 参数名 | 参数说明 | 备注 |
| ------ | -------- | ---- |
| username | 用户名      |                 |
| mobile   | 手机号      |                 |
| type     | 类型        |老师为0 ,学生为1 |
| campusId | 校园网账号  |                |
| timetable| 课表数据    |                |
| msg       | 返回消息   |                |
| status    | 请求状态   |                |
* 响应数据

```javascript
{
    "data": {
        "mobile": "123",
        "username": "张三",
        "type": "1",
        "campusId": "20183000000",
        "timetable": {}
    },
    "meta": {
        "msg": "上传成功",
        "status": 200
    }
}
```

## 推送

### 获取推送


* 请求路径：getpush
* 请求方法：get
* 请求参数

| 参数名 | 参数说明 | 备注 |
| ------ | -------- | ---- |
|        |          |      |

* 响应参数

| 参数名 | 参数说明 | 备注 |
| ------ | -------- | ---- |
| className | 课程名称   |                |
| classTime | 课程时间   |                |
| pushId    | 推送id     |                |
| pushTime  | 推送时间   |                |
| msg       | 返回消息   |                |
| status    | 请求状态   |                |
* 响应数据

```javascript
{
        "pushData": [
        {
            "className": "",
            "classTime": "",
            "pushId": "",
            "pushTime": ""
        },
        {
            "className": "",
            "classTime": "",
            "pushId": "",
            "pushTime": ""
        }
    ],
    "meta": {
        "msg": "推送添加成功",
        "status": 200
    }
}
```

### 添加推送

* 请求路径：addpush
* 请求方法：post
* 请求参数

| 参数名 | 参数说明 | 备注 |
| ------ | -------- | ---- |
| className | 课程名称   |                |
| classTime | 课程时间   |                |
| pushTime  | 推送时间   |                |

* 响应参数

| 参数名 | 参数说明 | 备注 |
| ------ | -------- | ---- |
| msg       | 返回消息   |                |
| status    | 请求状态   |                |
* 响应数据

```javascript
{
    "meta": {
        "msg": "推送添加成功",
        "status": 200
    }
}
```

### 删除推送


* 请求路径：delpush
* 请求方法：post
* 请求参数

| 参数名 | 参数说明 | 备注 |
| ------ | -------- | ---- |
| pushId    | 推送id     |                |

* 响应参数

| 参数名 | 参数说明 | 备注 |
| ------ | -------- | ---- |
| msg       | 返回消息   |                |
| status    | 请求状态   |                |
* 响应数据

```javascript
{
    "meta": {
        "msg": "推送删除成功",
        "status": 200
    }
}
```

## 管理

### 管理员登录

* 请求路径：admin/login
* 请求方法：post
* 请求参数

| 参数名   | 参数说明 | 备注     |
| -------- | -------- | -------- |
| username | 用户名   | 不能为空 |
| password | 密码     | 不能为空 |

* 响应参数

| 参数名 | 参数说明 | 备注 |
| ------ | -------- | ---- |
| pushData | 推送任务数据   |      |
| msg      | 返回消息       |      |
| status   | 请求状态       |      |

* 响应数据

```javascript
{
    "data": {
        "pushData": {}
    },
    "meta": {
        "msg": "登录成功",
        "status": 200
    }
}
```
### 添加用户

* 请求路径：register
* 请求方法：post
* 请求参数

| 参数名   | 参数说明 | 备注     |
| -------- | -------- | -------- |
| username | 用户名称 | 不能为空 |
| password | 用户密码 | 不能为空 |
| mobile   | 手机号   | 不能为空 |
| type   | 类型   | 不能为空 |
| schoolnumber   | 校园网账号   | 不能为空 |
| college   | 学院   | 不能为空 |


* 响应参数

| 参数名   | 参数说明    | 备注 |
| -------- | ----------- | ---- |
| msg       | 返回消息     |      |
| status      | 请求状态 |      |


* 响应数据

```javascript
{
    "meta": {
        "msg": "用户添加成功",
        "status": 200
    }
}
```

### 删除用户

* 请求路径：deluser
* 请求方法：post
* 请求参数

| 参数名   | 参数说明 | 备注     |
| -------- | -------- | -------- |
| username | 用户名称 |         |



* 响应参数

| 参数名   | 参数说明    | 备注 |
| -------- | ----------- | ---- |
| msg       | 返回消息     |      |
| status      | 请求状态 |      |


* 响应数据

```javascript
{
    "meta": {
        "msg": "用户删除成功",
        "status": 200
    }
}
```

