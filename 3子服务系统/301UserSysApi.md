###  carConfiguration 接口

#### 1. 获取产品经理负责的车系列

POST http://40.73.0.200/carConfig/getCarConfigSeries

上送: BODY: { "userId" : "1"}

返回: 
```
{
    "data": [{
        "id": 2,              //  profile ID
        "series": "Series1",     // 系列
        "eSeries": [{          
            "name": "Series1",       // E系列
            "isResponsible": "true"   //  “true”表示产品经理负责的车系、
        }, {
            "name": "Series1",
            "isResponsible": "true"
        }],
        "userId": "1",
        "isResponsible": "true"
    }]
}
```

注: 该接口是用来提供当前用户（产品经理）负责的车系列


#### 2. 获取E系列配置车列表

POST http://40.73.0.200:8762/carConfig/getCarConfigProfileList

上送: BODY: { "eSeries" : "G30","userId":"1"}

返回:
```
{
    "yearLunchedList": [{
        "id": 2,
        "series": "Series1",
        "eSeries": "G30",
        "profileName": [{
            "idNumber": 2,
            "configName": "profile_name",
            "state": null,
            "createAt": "2019-01-30",
            "isResponsible": "true"
        }],
        "userId": "1",
        "sortDate": "2018",
        "updateList": null
    }],
    "yearLunchedRight": [{
        "id": 4,
        "series": "Serise7",
        "eSeries": "G30",
        "profileName": [{
            "idNumber": 4,
            "configName": "profile_name1",
            "state": null,
            "createAt": "2019-01-21",
            "isResponsible": "true"
        }]
}
```

注: 该接口用来提供小系（E系列）配置车列表

#### 3. 创建一个配件车系

POST http://40.73.0.200:8762/carConfig/updateCarConfigVariantStatus

上送: BODY: {id:"XXX",userId:"XXX",currentStatus:"XXX",updateDate:"XXX",fileName:"XXX"}

返回: 
```
{
    "code": "0", // “0” 表示成功 ，“1”表示失败
    "message": "成功！"
}
```

注: 该接口会需要传入 手机号,验证码,密码，重复密码


#### 3.1.2.3. 重置密码

POST https://api-csl.9h-sports.com/v1/user/reset-pass

上送: BODY: {phone:"18610814074",code:"xxxxxx",password:"xxxxxxx",rePassword:"xxxxxx"}

返回: {oper_code:1}

注: 该接口会需要传入 手机号,验证码,密码，重复密码

#### 3.1.2.4. 绑定手机

POST https://api-csl.9h-sports.com/v1/user/bind-phone/{user_id}

上送: BODY: {phone:"18610814074",code:"xxxxxx",password:"xxxxxxx",rePassword:"xxxxxx"}

返回: {oper_code:1}

注: 该接口会需要传入 手机号,验证码,密码，重复密码

#### 3.1.2.4. 从新绑定手机

POST https://api-csl.9h-sports.com/v1/user/re-bind-phone/{user_id}

上送: BODY: {phone:"18610814074",code:"xxxxxx",password:"xxxxxxx"}

返回: {oper_code:1}

注: 该接口会需要传入 手机号,验证码,密码 还需要token


#### 3.1.2.5. 比较密码

POST https://api-csl.9h-sports.com/v1/user/check-password

上送: BODY: {userId:"xxxx",password:"xxxxxxx"}

返回: {oper_code:1}

注: 该接口需要token

#### 3.1.2.5. 检查手机是否已经注册

GET https://api-csl.9h-sports.com/v1/user/is-phone-exist/{phone}

返回: {oper_code:1}


#### 3.1.2.6. 登录

POST https://api-csl.9h-sports.com/v1/user/logins

上送 :BODY : 账号登陆 {phone:"18610814074",password:"xxxxxxx"}, 微博登陆{weiboId:"xxxxxxx",accessToken:"xxxxxxxxxx"},微信登陆{weixinId:"xxxxxxx",accessToken:"xxxxxxxxxx"}

返回 : {oper_code:1,message:"xxxxx"}



#### 3.1.2.7. 用户登出系统

DELETE https://api-csl.9h-sports.com/v1/user/logins/{user_id}

#### 3.1.2.8. 删除某个注册的用户 (目前还未使用)

DELETE https://api-csl.9h-sports.com/v1/user/registers/{user_id}




#### 3.1.2.9. 上传设备 device_token

POST https://api-csl.9h-sports.com/v1/user/upload-device

request: {deviceToken:"xxxxxxxxxxxx",userId:"xxx",osType:"android",osVersion:"version"}

response:{oper_code:1}


注: 以上全部接口都是对user对象进行操作，以下是对user_info对象进行操作
-----------

#### 获取某个用户详细资料

GET  https://api-csl.9h-sports.com/v1/user/users/{user_id}

#### 更新某个用户详细资料

POST  https://api-csl.9h-sports.com/v1/user/users/{user_id}

request : {userId:1,nickName:"xxx",avatar:"http://xxx.png"} cookie: token

response : {oper_code:1}

#### 查询用户等级信息

POST https://api-csl.9h-sports.com/v1/user/user-level/{user_id}

#### 用户关注俱乐部

POST https://api-csl.9h-sports.com/v1/user/user-club-stars/{user_id}

request: {clubId:'xxxx'}

response: {oper_code:1,data: clubObject}

#### 用户取消关注俱乐部

DELETE https://api-csl.9h-sports.com/v1/user/user-club-stars/{user_id}/{club_id}

#### 获取用户关注的所有俱乐部

GET https://api-csl.9h-sports.com/v1/user/user-club-stars/{user_id}

response: {clubs: clubObjects}


---------------

#### 用户关注比赛

POST https://api-csl.9h-sports.com/v1/user/user-match-stars/{user_id}

request: {matchId:xxxx}

#### 用户取消关注比赛

DELETE https://api-csl.9h-sports.com/v1/user/user-match-stars/{user_id}/{match_id}

#### 用获取用户关注的所有比赛

GET https://api-csl.9h-sports.com/v1/user/user-match-stars/{user_id}


--------------------------------------------
#### 用户获取相互关注列表
GET http://user.service.9h.com/user-friends/{user_id}

返回JSON
```
{
    "desc":null,
    "oper_code":"1",
    "data":[
        {
            "nickName":"",   --> 昵称
            "fansCount":"",  --> 粉丝数量
            "avatar":"",     --> 头像
            "userId":""
        },
        Object{...},
        Object{...}
    ],
    "message":null
}
```
例：http://123.59.84.71/v1/user/user-friends/1

#### 用户获取自己的关注他人列表

GET http://user.service.9h.com/user-follows/{user_id}

返回JSON
```
{
    "desc":null,
    "oper_code":"1",
    "data":[
        {
            "nickName":"",   --> 昵称
            "fansCount":"",  --> 粉丝数量
            "avatar":"",     --> 头像
            "userId":"",
            "status":""      --> 关注关系(1:用户关注，2:互相关注)
        },
        Object{...},
        Object{...}
    ],
    "message":null
}
```
例：http://123.59.84.71/v1/user/user-follows/1

#### 用户关注其他用户

POST http://user.service.9h.com/user-follows/{user_id}

上送: BODY: {"followUserId":"××"}

返回: {oper_code:1}

#### 用户取消关注其他用户

DELETE http://user.service.9h.com/user-follows/{user_id}/{user_id}

返回: {oper_code:1,"message":"××××"}

#### 用户获取自己的被关注列表

GET http://user.service.9h.com/user-follow-bys/{user_id}

返回JSON
```
{
    "desc":null,
    "oper_code":"1",
    "data":[
        {
            "nickName":"",   --> 昵称
            "isBlocked":"",  --> 该用户是否屏蔽关注人(1:屏蔽 0:不屏蔽)
            "fansCount":"",  --> 粉丝数量
            "avatar":"",     --> 头像
            "userId":"",
            "status":""      --> 关注关系(1:用户关注，2:互相关注)
        },
        Object{...},
        Object{...}
    ],
    "message":null
}
```
例：http://123.59.84.71/v1/user/user-follow-bys/1

#### 用户从被关注列表中屏蔽关注自己的用户

PUT http://user.service.9h.com/user-follow-bys/{user_id}

上送: BODY: {"isBlocked":"0","followUserId":"××"} --> 取消屏蔽<br/>
上送: BODY: {"isBlocked":"1","followUserId":"××"} --> 屏蔽

返回: {oper_code:1,"message":"××××"}

----------------------------------------

#### 用户获取自己的每日签到记录

GET https://api-csl.9h-sports.com/v1/user/user-check-ins/{user_id}

#### 用户签到

POST https://api-csl.9h-sports.com/v1/user/user-check-ins/{user_id}

#### 获取用户今天的签到状态

GET https://api-csl.9h-sports.com/v1/user/get-user-check-ins/{user_id}

#### 获取用户签到排行

GET https://api-csl.9h-sports.com/v1/user/user-checkin-rank/{user_id}
