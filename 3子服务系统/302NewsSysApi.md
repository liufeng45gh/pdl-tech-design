## 3.5.2. 数据服务接口

正式地址:   
Swagger:  
测试地址:  
Swagger: /swagger/index.html  

### 3.5.3.1. 所有服务接口清单

 方法 | 接口 | 用途 | 返回 | 是否走网关 
 :-- | :--  | :-- | :-- | :--
 GET | /all-series | 获取所有的系列对象 | [] |
 GET | /all-series?enabled=true | 获取所有的已上线系列对象 | [] | 
 GET | /series/{series_code} | 获取某个系列的详细资料 | {} | 
     |  |  |  |  
 GET | /series/{series_code}/eseries | 获取某个系列下的所有e系列对象 | [] |
 GET | /series/{series_code}/eseries?enabled=true | 获取某个系列下的e系列上线对象 | [] | 
 GET | /eseries/{eseries_code} | 获取单个e系列对象| {}|
 GET | /all-eseries|所有eseries| [] |
 GET | /all-eseries?enabled=true|所有上线的eseries| [] |
     |  |  |  |
 GET | /series/{series_code}/models | 获取系列下所有的model | [] |
 GET | /series/{series_code}/models?enabled=true | 获取系列下所有上线的model | [] |
 GET | /eseries/{eseries_code}/models | 获取e系列下所有的model | [] |
 GET | /eseries/{eseries_code}/models?enabled=true | 获取e系列下所有上线的model | [] |
 GET | /all-models |所有model| [] | 
 GET | /all-models?enabled=true |所有上线的model| [] | 
 GET | /models/{code} |按code 获取model| {} | 
  | | | | 
 GET | /all-options|获取所有配件(分页，默认30)| [] |
 GET | /option/{option_id}|获取某个配件| {} |
 GET | /options-by-code/{code}|按code获取配件| [] |
  | | | | 
 GET | /all-library | 所有library | []|
 GET | /all-library?status={status}   | 获取不同status 下的所有library | [] |
 GET | /eseries/eseries_code/library?status={status}   | 获取不同e系列下不同status 下的所有library | [] |
 GET | /library/{id}  | 获取一个library |{} |
 GET | /library-by-version/{version}  | 按version获取一个library| {}|
 POST | /import-library | 导入library 需要显示导入进度 | response-result | 
  | | | |
 GET| /library-basic-property/{library_id}|按library_id获取所有 library-basic-property| []|
 GET| /library-basic-property/{library_id}/{option_id}|按library_id 和 option_id获取 library-basic-property| {}|
 GET| /library-basic-property/{library_id}/classify/{classify_id}|按library_id 和 classify获取 library-basic-property| []|
  | | | |
 GET| /library-basic-property-setting/{library_id}|按library_id获取所有 library-basic-property-setting| []|
 GET| /library-basic-property-setting/{library_id}/{option_id}|按library_id 和 option_id获取 library-basic-property-setting| []|
  GET| /library-basic-property-setting/{library_id}/{option_id}/{model_code}|按library_id 和 option_id和 model_code获取 library-basic-property-setting| {}|
 GET| /library-basic-property-setting/{library_id}/classify/{classify_id}|按library_id 和 classify获取 library-basic-property-setting| []|
   | | | |
 GET| /library-optional-property/{library_id}|按library_id获取所有 library-optional-property| []|
 GET| /library-optional-property/{library_id}/{option_id}|按library_id 和 option_id获取 library-optional-property| {}|
 GET| /library-optional-property/{library_id}/classify/{classify_id}|按library_id 和 classify获取 library-optional-property| []|
  | | | |
 GET| /library-optional-property-setting/{library_id}|按library_id获取所有 library-optional-property-setting| []|
 GET| /library-optional-property-setting/{library_id}/{option_id}|按library_id 和 option_id获取 library-optional-property-setting| []|
  GET| /library-optional-property-setting/{library_id}/{option_id}/{model_code}|按library_id 和 option_id和 model_code获取 library-optional-property-setting| {}|
 GET| /library-optional-property-setting/{library_id}/classify/{classify_id}|按library_id 和 classify获取 library-optional-property-setting| []|
  | | | |
 GET| /library-option-rule/{library_id}|按library_id获取所有 library-option-rule| []|
 GET| /library-option-rule/{library_id}/{option_id}|按library_id 和 option_id获取 library-option-rule| []|
 GET| /library-option-rule/{library_id}/{option_id}/{model_code}|按library_id 和 option_id和 model_code获取 library-option-rule| []|
  | | | |
 GET| /all-profile|所有 profile| []|
 GET| /all-profile?status={status}|所有 profile中匹配status| []|
 GET| /profile/{profile_id}|按profile_id获取 profile| {}|
 GET| /profile/by-eseries/{eseries_code}|按eseries_code 获取 profile| []|
 GET| /profile/by-eseries/{eseries_code}?status={status}|按eseries_code 和 status 获取 profile| []|
 POST| /profile/{profile_id}/change-status|改变profile status| response-result|
 POST| /profile/{profile_id}/copy|复制一个profile| response-result|
 POST| /import-profile|上传profile| response-result|
   | | | |
 GET| /profile-varient/{profile_id}|所有 profile_id的 profile-varient| []|
 GET| /profile-varient/{profile_id}/{varient_id}|profile_id和varient_id匹配单个对象| {}|
 PUT| /profile-varient/{profile_id}/{varient_id}|保存 saveOrUpdate varient对象| response-result|
 DELETE| /profile-varient/{profile_id}/{varient_id}|删除 varient对象| response-result|
  | | | |
 GET| /profile-option/{profile_id}|所有 profile_id的 profile-option| []|
 GET| /profile-option/{profile_id}/{option_id}|所有 profile_id和option_id 确定唯一 profile-option| {}|
 GET| /profile-option/{profile_id}/show_diff|显示和最新library的区别| {}|
  | | | |
 GET| /profile-option-change/{profile_id}|所有 profile_id的 profile-option-change| []|
 GET| /profile-option-change/{profile_id}/{option_id}|所有 profile_id和option_id 确定唯一 profile-option-change| {}|
 POST| /profile-option-change/{profile_id}|新增 修改 删除 profile-option-change| response-result|
   | | | |
 GET| /profile-cell-setting/{profile_id}|所有 profile_id的 profile-cell-setting| []|
 GET| /profile-cell-setting/{profile_id}/option/{option_id}|所有 profile_id和option_id  profile-cell-setting| []|
 GET| /profile-cell-setting/{profile_id}/varient/{varient_id}|所有 profile_id和varient_id 相关的  profile-cell-setting| []|
 GET| /profile-cell-setting/{profile_id}/{option_id}/{varient_id}| profile_id和varient_id 和 option_id 确定唯一  profile-cell-setting| {}|
 PUT| /profile-cell-setting/{profile_id}/{option_id}/{varient_id}| 这个PUT 是saveOrUpdate| response-result|







### 3.5.3.2. 各接口的样例数据及字段解释

#### 获得所有的系列

GET /all-series

@param enabled

返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->唯一标示
        "code": "7", -> 系统系列唯一标示码
        "nameEn": "", -> 英文名
        "nameZh": "", -> 中文名
        "disp_order": "", ->显示顺序
        "enabled":"", ->是否启用
        "image_url": "", -> 大图url
    },
    {},
    {}
]

```

#### 按 series_code 获得系列对象

GET /series/{series_code}

@param enabled

返回格式:

```
HTTP Stauts Code: 200


{
    "id": "1", ->唯一标示
    "code": "7", -> 系统系列唯一标示码
    "nameEn": "", -> 英文名
    "nameZh": "", -> 中文名
    "disp_order": "", ->显示顺序
    "enabled":"", ->是否启用
    "image_url": "", -> 大图url
}

```

#### 获得所有的e系列

GET /all-eseries

@param enabled

返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->唯一标示
        "series_code": "7" 大系列的标示码
        "code": "7", -> 系统系列唯一标示码
        "nameEn": "", -> 英文名
        "nameZh": "", -> 中文名
        "disp_order": "", ->显示顺序
        "enabled":"", ->是否启用
    },
    {},
    {}
]

```


#### 按大系列code获得相关的e系列对象

GET  /series/{series_code}/eseries

@param enabled

返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->唯一标示
        "series_code": "7" 大系列的标示码
        "code": "7", -> 系统系列唯一标示码
        "nameEn": "", -> 英文名
        "nameZh": "", -> 中文名
        "disp_order": "", ->显示顺序
        "enabled":"", ->是否启用
    },
    {},
    {}
]

```


#### 获得所有的model车型

GET /all-models

@param enabled

返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->唯一标示
        "e_series_code": "7" 大系列的标示码
        "code": "7", -> 系统系列唯一标示码
        "nameEn": "", -> 英文名
        "nameZh": "", -> 中文名
        "disp_order": "", ->显示顺序
        "enabled":"", ->是否启用
    },
    {},
    {}
]

```


#### 按大系列code获得相关的model对象

GET  /series/{series_code}/models

@param enabled

返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->唯一标示
        "e_series_code": "7" 大系列的标示码
        "code": "7", -> 系统系列唯一标示码
        "nameEn": "", -> 英文名
        "nameZh": "", -> 中文名
        "disp_order": "", ->显示顺序
        "enabled":"", ->是否启用
    },
    {},
    {}
]

```

#### 按小系列code获得相关的model对象

GET  /eseries/{eseries_code}/models

@param enabled

返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->唯一标示
        "e_series_code": "7" 大系列的标示码
        "code": "7", -> 系统系列唯一标示码
        "nameEn": "", -> 英文名
        "nameZh": "", -> 中文名
        "disp_order": "", ->显示顺序
        "enabled":"", ->是否启用
    },
    {},
    {}
]

```


#### 按小系列code获得相关的model对象

GET  /models/{code}

@param enabled

返回格式:

```
HTTP Stauts Code: 200

BODY:

{
    "id": "1", ->唯一标示
    "e_series_code": "7" 大系列的标示码
    "code": "7", -> 系统系列唯一标示码
    "nameEn": "", -> 英文名
    "nameZh": "", -> 中文名
    "disp_order": "", ->显示顺序
    "enabled":"", ->是否启用
}

```


#### 所有配件对象

GET  /all-options
@param pageNo


返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "e_series_code": "G38" 小系列对应code
        "code": "300", -> bmw 系统内代码
        "nameEn": "", -> 英文名
        "nameZh": "", -> 中文名
        "type": "", -> 类型 basic| optional
        "classfy":"", ->类型 系统分类
    },
    {},
    {}
]

```

#### 获取单个配件

GET  /option/{option_id}



返回格式:

```
HTTP Stauts Code: 200

BODY:

{
    "id": "1", ->唯一标示
    "e_series_code": "G38" 小系列对应code
    "code": "300", -> bmw 系统内代码
    "nameEn": "", -> 英文名
    "nameZh": "", -> 中文名
    "type": "", -> 类型 basic| optional
    "classfy":"", ->类型 系统分类
}

```

#### 按code获取配件对象

GET  /options-by-code/{code}



返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "e_series_code": "G38" 小系列对应code
        "code": "300", -> bmw 系统内代码
        "nameEn": "", -> 英文名
        "nameZh": "", -> 中文名
        "type": "", -> 类型 basic| optional
        "classfy":"", ->类型 系统分类
    },
    {},
    {}
]

```


#### 按所有library

GET  /all-library

@RequestParam status

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "e_series_code": "G38" 小系列对应code
        "code": "300", -> bmw 系统内代码
        "import_date": "", -> 导入时间
        "basic_file_name": "", -> 文件名
        "basic_file_url": "", -> 导入文件路径
        "optional_file_name":"", ->可操作文件名
        "optional_file_url":"", ->可操作文
    },
    {},
    {}
]

```






#### 按profile_id获得基础的 profile option

GET /profile-option/{profile_id}


返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "optionId": "1", ->配件id
        "propertyCode": "7", -> 配件标示码
        "nameEn": "", -> 英文名
        "nameZh": "", -> 中文名
        "disp_order": "", ->显示顺序
        "classify":"", ->类型
        "price": "", -> 价格
        "rmbPrice": "", -> 人民币价格
        "discount": "", -> 折扣
    },
    {},
    {}
]

```


注意

```
只有root profile 才会有 prifile option
此方法需要先拿到 对应的 root prifile id,
然后按这个id 获取基础profile 对应的option list 
```

#### 按profile_id获得变化的 profile option

GET /profile-option-change/{profile_id}


返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "optionId": "1", ->配件id
        "propertyCode": "7", -> 配件标示码
        "nameEn": "", -> 英文名
        "nameZh": "", -> 中文名
        "disp_order": "", ->显示顺序
        "classify":"", ->类型
        "price": "", -> 价格
        "rmbPrice": "", -> 人民币价格
        "discount": "", -> 折扣
        "changeType": "", -> 增加还是删除 + -
    },
    {},
    {}
]

```


注意

```
此方法需按profile_id 对应的option list 
当复制的时候这些数据需要复制过去
```


#### 复制profile

POST /profile/{profile_id}/copy

@RequestParam sourceProfileId
@RequestParam newProfileName


返回格式:

```
HTTP Stauts Code: 200

BODY:

{
    optCode : "succcess" , ->操作code码
    msg : "this is reason why" , ->操作信息
    data: {} ,-> 返回数据
}


```


注意

```
需要复制 profile-option change 部分
赋值 rootId, parentId
其他原始拷贝指向新的profile id
```

#### 导入library

POST /import-library

@RequestParam version
@RequestMetadata file


返回格式:

```
HTTP Stauts Code: 200

BODY:

{
    optCode : "succcess" , ->操作code码
    msg : "this is reason why" , ->操作信息
    data: {} ,-> 返回数据
}


```


注意

```
需要维护表 config_unique_option 

```

#### 导入profile

POST /import-profile

@RequestParam libraryVersion
@RequestMetadata file


返回格式:

```
HTTP Stauts Code: 200

BODY:

{
    optCode : "succcess" , ->操作code码
    msg : "this is reason why" , ->操作信息
    data: {} ,-> 返回数据
}


```


注意

```
需要维护表 config_profile_option 
不需要维护表 config_profile_option_change
导入前 先判断数据是否可以转换成 java 对象
还需要比较 config_unique_option中是否覆盖所有相关option 对象，如果有不能识别的，需要报出那些option 不能识别,并且返回导入失败
```