## 3.5.2. 数据服务接口

正式地址:   
Swagger:  
测试地址:  
Swagger: http://40.73.0.200:8888/swagger/index.html 

### 3.5.3.1. 所有服务接口清单

 方法 | 接口 | 用途 | 返回 | 调用页面|是否走网关 
 :-- | :--  | :-- | :-- | :-- | :--
 GET | /series/all-series | 获取所有的系列对象 | [] | |
 GET | /series/all-series?enabled=true | 获取所有的已上线系列对象 | [] | 车型车系一览页|
 GET | /series/{series_code} | 获取某个系列的详细资料 | {} | |
     |  |  |  |  |
 GET | /eseries/by-series/{series_code} | 获取某个系列下的所有e系列对象 | [] | |
 GET | /eseries/by-series/{series_code}?enabled=true | 获取某个系列下的e系列上线对象 | [] | |
 GET | /eseries/{eseries_code} | 获取单个e系列对象| {}| |
 GET | /eseries/all-eseries|所有eseries| [] | |
 GET | /eseries/all-eseries?enabled=true|所有上线的eseries| [] | |
     |  |  |  | |
 GET | /models/by-series/{series_code} | 获取系列下所有的model | [] | |
 GET | /models/by-series/{series_code}?enabled=true | 获取系列下所有上线的model | [] | |
 GET | /models/by-eseries/{eseries_code} | 获取e系列下所有的model | [] | |
 GET | /models/by-eseries/{eseries_code}?enabled=true | 获取e系列下所有上线的model | [] | |
 GET | /models /all-models |所有model| [] | |
 GET | /models /all-models?enabled=true |所有上线的model| [] | |
 GET | /models/{code} |按code 获取model| {} | |
  | | | | |
 GET | /option/all-options|获取所有配件(分页，默认30)| [] | |
 GET | /option/{option_id}|获取某个配件| {} | |
 GET | /options/by-code/{code}|按code获取配件| [] | |
  | | | | |
 GET | /library/all-library | 所有library | []| |
 GET | /library/all-library?status={status}   | 获取不同status 下的所有library | [] | |
 GET | /library/by-eseries/{eseries_code}?status={status}   | 获取不同e系列下不同status 下的所有library | [] | |
 GET | /library/{id}  | 获取一个library |{} | |
 GET | /library/by-version/{version}  | 按version获取一个library| {}| |
 POST | /library/import-library | 导入library 需要显示导入进度 | response-result |  |
  | | | | |
 GET| /library-basic-property/{library_id}|按library_id获取所有 library-basic-property| []| |
 GET| /library-basic-property/{library_id}/{option_id}|按library_id 和 option_id获取 library-basic-property| {}| |
 GET| /library-basic-property/{library_id}/classify/{classify_id}|按library_id 和 classify获取 library-basic-property| []| |
  | | | | |
 GET| /library-basic-property-setting/{library_id}|按library_id获取所有 library-basic-property-setting| []| |
 GET| /library-basic-property-setting/{library_id}/{option_id}|按library_id 和 option_id获取 library-basic-property-setting| []| |
  GET| /library-basic-property-setting/{library_id}/{option_id}/{model_code}|按library_id 和 option_id和 model_code获取 library-basic-property-setting| {}| |
 GET| /library-basic-property-setting/{library_id}/classify/{classify_id}|按library_id 和 classify获取 library-basic-property-setting| []| |
   | | | | |
 GET| /library-optional-property/{library_id}|按library_id获取所有 library-optional-property| []| |
 GET| /library-optional-property/{library_id}/{option_id}|按library_id 和 option_id获取 library-optional-property| {}| |
 GET| /library-optional-property/{library_id}/classify/{classify_id}|按library_id 和 classify获取 library-optional-property| []| |
  | | | | |
 GET| /library-optional-property-setting/{library_id}|按library_id获取所有 library-optional-property-setting| []| |
 GET| /library-optional-property-setting/{library_id}/{option_id}|按library_id 和 option_id获取 library-optional-property-setting| []| |
  GET| /library-optional-property-setting/{library_id}/{option_id}/{model_code}|按library_id 和 option_id和 model_code获取 library-optional-property-setting| {}| |
 GET| /library-optional-property-setting/{library_id}/classify/{classify_id}|按library_id 和 classify获取 library-optional-property-setting| []| |
  | | | | |
 GET| /library-option-rule/{library_id}|按library_id获取所有 library-option-rule| []| |
 GET| /library-option-rule/{library_id}/{option_id}|按library_id 和 option_id获取 library-option-rule| []| |
 GET| /library-option-rule/{library_id}/{option_id}/{model_code}|按library_id 和 option_id和 model_code获取 library-option-rule| []| |
  | | | | |
 GET| /profile/all-profile|所有 profile| []| |
 GET| /profile/all-profile?status={status}|所有 profile中匹配status| []| |
 GET| /profile/{profile_id}|按profile_id获取 profile| {}| 配车页面 |
 GET| /profile/by-eseries/{eseries_code}|按eseries_code 获取 profile| []| 车系 profile一览页|
 GET| /profile/by-eseries/{eseries_code}?status={status}|按eseries_code 和 status 获取 profile| []| |
 GET| /profile/by-eseries/{eseries_code}?isLaunched={isLaunched}|按eseries_code 和 isLaunched 获取 profile| []| |
 POST| /profile/{profile_id}/change-status|改变profile status| response-result| 车系 profile一览页|
 POST| /profile/{profile_id}/copy|复制一个profile| response-result|  车系 profile一览页|
 POST| /profile/import-profile|上传profile| response-result|
   | | | | |
 GET| /profile-varient/{profile_id}|所有 profile_id的 profile-varient| []|  配车页面 |
 GET| /profile-varient/{profile_id}/{varient_id}|profile_id和varient_id匹配单个对象| {}| |
 PUT| /profile-varient/{profile_id}/{varient_id}|保存 saveOrUpdate varient对象| response-result| 配车页面 |
 DELETE| /profile-varient/{profile_id}/{varient_id}|删除 varient对象| response-result| 配车页面 |
  | | | |
 GET| /profile-option/{profile_id}/show_self|所有 profile_id的 profile-option| []| |
 GET| /profile-option/{profile_id}/{option_id}|所有 profile_id和option_id 确定唯一 profile-option| {}| |
 GET| /profile-option/{profile_id}/show_diff|显示和最新library的区别| {}| |
 GET| /profile-option/{profile_id}/show_library|显示最新library的设置| []| |
 GET| /profile-option/{profile_id}/show_result|显示最后需要显示的数据 profile 中的数据 + library 中定义为标配的数据| []|  配车页面 |
  | | | | |
 GET| /profile-option-change/{profile_id}|所有 profile_id的 profile-option-change| []| 配车页面 |
 GET| /profile-option-change/{profile_id}/{option_id}|所有 profile_id和option_id 确定唯一 profile-option-change| {}| |
 POST| /profile-option-change/{profile_id}|新增 修改 删除 profile-option-change| response-result|  配车页面 |
   | | | | |
 GET| /profile-cell-setting/{profile_id}|所有 profile_id的 profile-cell-setting| []|  配车页面 |
 GET| /profile-cell-setting/{profile_id}/option/{option_id}|所有 profile_id和option_id  profile-cell-setting| []| |
 GET| /profile-cell-setting/{profile_id}/varient/{varient_id}|所有 profile_id和varient_id 相关的  profile-cell-setting| []|  配车页面 |
 GET| /profile-cell-setting/{profile_id}/{option_id}/{varient_id}| profile_id和varient_id 和 option_id 确定唯一  profile-cell-setting| {}| |
 PUT| /profile-cell-setting/{profile_id}/{option_id}/{varient_id}| 这个PUT 是saveOrUpdate| response-result|  配车页面 |
    | | | | |
 GET| /package/{e_series_code}/all-package?isLaunched={isLaunched}|package 一览页需要展示| []|  package 一览页需要展示| 	
 POST| /package/{lv1_id}/copy |复制package | []|  package一览页需要调用| 
 POST| /package/{lv1_id}/set-status |设置package状态| []|  package一览页需要调用| 
 POST| /package/{lv1_id}/set-check |设置package check状态| []|  package一览页需要调用| 
   | | | | |
 GET| /package/show-integration-data/by-profile/{profile_id}|package对应profile_id 应该返回的展示数据| []|  配车页面 ,配包页面 |
 GET| /package/show-history/by-profile/{profile_id}|package对应profile_id 对应的历史数据| []| |
 POST | /package/set-use/{profile_id}/{lv1_id}|设置profile选择历史配置包| []|  配包界面 |
 GET| /package/show-integration-data/by-lv1/{lv1_id}|package对应lv1_id 对应的 lv2 数据列表| []|   |
 POST | /package/{lv1_id}/add-package-lv2|给大包下添加小包| []|  配包界面 |
 DELETE | /package/{lv2_id}/delete|删除小包| []| 配包界面|
 GET| /package/{lv2_id}/options |package对应lv2_id 对应的 配件列表| []|   |
 DELETE | /package/{lv2_id}/{option_id}/delete|删除小包中的配件| []| 配包界面|
 POST | /package/{lv2_id}/{option_id}/add-option|给小包下添加配件| []|  配包界面 |
 PUT| /package/{lv2_id}/{option_id}/{varient_id}/setting| 这个PUT 是saveOrUpdate,设置对应格子中的值| response-result|  配包页面 |
 GET| /package/{lv2_id}/varient| 获取包下 varent 数据列表| []|  配包页面 |
 PUT| /package/{lv2_id}/{varient_id}/set-varient| 这个PUT 是saveOrUpdate,设置对应格子中的值| response-result|  配包页面 |
 DELETE| /package/{lv2_id}/{varient_id}/del-varient| 删除 varient| response-result|  配包页面 |







### 3.5.3.2. 各接口的样例数据及字段解释

#### 获得所有的系列

GET /series/all-series

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
        "dispOrder": "", ->显示顺序
        "enabled":"", ->是否启用
        "imageUrl": "", -> 大图url
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
    "dispOrder": "", ->显示顺序
    "enabled":"", ->是否启用
    "imageUrl": "", -> 大图url
}

```

#### 获得所有的e系列

GET /eseries/all-eseries

@param enabled

返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->唯一标示
        "seriesCode": "7" 大系列的标示码
        "code": "7", -> 系统系列唯一标示码
        "nameEn": "", -> 英文名
        "nameZh": "", -> 中文名
        "dispOrder": "", ->显示顺序
        "enabled":"", ->是否启用
    },
    {},
    {}
]

```


#### 按大系列code获得相关的e系列对象

GET  /eseries/by-series/{series_code}

@param enabled

返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->唯一标示
        "seriesCode": "7" 大系列的标示码
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

GET /models/all-models

@param enabled

返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->唯一标示
        "eSeriesCode": "7" 大系列的标示码
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

GET  /models/by-series/{series_code}

@param enabled

返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->唯一标示
        "eSeriesCode": "7" 大系列的标示码
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

GET  /models/by-eseries/{eseries_code}

@param enabled

返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->唯一标示
        "eSeriesCode": "7" 大系列的标示码
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
    "eSeriesCode": "7" 大系列的标示码
    "code": "7", -> 系统系列唯一标示码
    "nameEn": "", -> 英文名
    "nameZh": "", -> 中文名
    "disp_order": "", ->显示顺序
    "enabled":"", ->是否启用
}

```


#### 所有配件对象

GET  /option/all-options
@param pageNo


返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "eSeriesCode": "G38" 小系列对应code
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
    "eSeriesCode": "G38" 小系列对应code
    "code": "300", -> bmw 系统内代码
    "nameEn": "", -> 英文名
    "nameZh": "", -> 中文名
    "type": "", -> 类型 basic| optional
    "classfy":"", ->类型 系统分类
}

```

#### 按code获取配件对象

GET  /options/by-code/{code}



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

GET  /library/all-library

@RequestParam status

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "eSeriesCode": "G38" 小系列对应code
        "code": "300", -> bmw 系统内代码
        "importDate": "", -> 导入时间
        "basicFileName": "", -> 文件名
        "basicFileUrl": "", -> 导入文件路径
        "optionalFileName":"", ->可操作文件名
        "optionalFileUrl":"", ->可操作文
    },
    {},
    {}
]

```


#### 获取不同e系列下不同status 下的所有library

GET  /library/by-eseries/{eseries_code}?status={status}

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
        "importDate": "", -> 导入时间
        "basicFileName": "", -> 文件名
        "basicFileUrl": "", -> 导入文件路径
        "optionalFileName":"", ->可操作文件名
        "optionalFileUrl":"", ->可操作文
    },
    {},
    {}
]

```


#### 获取一个library

GET  /library/{id}


返回格式:

```
HTTP Stauts Code: 200

BODY:


{
	"id": "1", ->唯一标示
	"eSeriesCode": "G38" 小系列对应code
	"code": "300", -> bmw 系统内代码
	"importDate": "", -> 导入时间
	"basicFileName": "", -> 文件名
	"basicFileUrl": "", -> 导入文件路径
	"optionalFileName":"", ->可操作文件名
	"optionalFileUrl":"", ->可操作文
}

```

#### 按version获取一个library

GET  /library/by-version/{version}


返回格式:

```
HTTP Stauts Code: 200

BODY:


{
	"id": "1", ->唯一标示
	"eSeriesCode": "G38" 小系列对应code
	"code": "300", -> bmw 系统内代码
	"importDate": "", -> 导入时间
	"basicFileName": "", -> 文件名
	"basicFileUrl": "", -> 导入文件路径
	"optionalFileName":"", ->可操作文件名
	"optionalFileUrl":"", ->可操作文
}

```


#### 导入library 需要显示导入进度

POST /library/import-library

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




#### 按library_id获取所有 library-basic-property

GET /library-basic-property/{library_id}




返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "classify": "", -> 分类
        "comment": "", -> 注释
    },
    {},
    {}
]

```


#### 按library_id 和 option_id获取 library-basic-property

GET /library-basic-property/{library_id}/{option_id}




返回格式:

```
HTTP Stauts Code: 200

BODY:


{
	"id": "1", ->唯一标示
	"libraryId": "" 对应library表id
	"optionId": "", -> 配件Id
	"classify": "", -> 分类
	"comment": "", -> 注释
}

```




#### 按library_id 和 classify获取 library-basic-property

GET /library-basic-property/{library_id}/classify/{classify_id}




返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "classify": "", -> 分类
        "comment": "", -> 注释
    },
    {},
    {}
]

```




#### 按library_id获取所有 library-basic-property-setting

GET /library-basic-property-setting/{library_id}




返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "modelCode": "", -> model唯一代码
		"propertyContent": "", ->设置值
		"lhdOrRhd": "",-> 左驾车右驾车 L/R/X
        "comment": "", -> 注释
    },
    {},
    {}
]

```


#### 按library_id 和 option_id获取 library-basic-property-setting

GET /library-basic-property-setting/{library_id}/{option_id}




返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "modelCode": "", -> model唯一代码
		"propertyContent": "", ->设置值
		"lhdOrRhd": "",-> 左驾车右驾车 L/R/X
        "comment": "", -> 注释
    },
    {},
    {}
]

```


#### 按library_id 和 option_id和 model_code获取 library-basic-property-setting

GET /library-basic-property-setting/{library_id}/{option_id}/{model_code}




返回格式:

```
HTTP Stauts Code: 200

BODY:


{
	"id": "1", ->唯一标示
	"libraryId": "" 对应library表id
	"optionId": "", -> 配件Id
	"modelCode": "", -> model唯一代码
	"propertyContent": "", ->设置值
	"lhdOrRhd": "",-> 左驾车右驾车 L/R/X
	"comment": "", -> 注释
}

```


#### 按library_id 和 classify获取 library-basic-property-setting

GET /library-basic-property-setting/{library_id}/classify/{classify_id}

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "modelCode": "", -> model唯一代码
		"propertyContent": "", ->设置值
		"lhdOrRhd": "",-> 左驾车右驾车 L/R/X
        "comment": "", -> 注释
    },
    {},
    {}
]

```


#### 按library_id获取所有 library-optional-property

GET /library-optional-property/{library_id}

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
         "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "classify": "", -> 分类
        "comment": "", -> 注释
    },
    {},
    {}
]

```

#### 按library_id 和 option_id获取 library-optional-property

GET /library-optional-property/{library_id}/{option_id}

返回格式:

```
HTTP Stauts Code: 200

BODY:


{
	 "id": "1", ->唯一标示
	"libraryId": "" 对应library表id
	"optionId": "", -> 配件Id
	"classify": "", -> 分类
	"comment": "", -> 注释
}

```


#### 按library_id 和 classify获取 library-optional-property

GET /library-optional-property/{library_id}/classify/{classify_id}

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
         "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "classify": "", -> 分类
        "comment": "", -> 注释
    },
    {},
    {}
]

```



#### 按library_id获取所有 library-optional-property-setting

GET /library-optional-property-setting/{library_id}

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "modelCode": "", -> model唯一代码
		"propertyContent": "", ->设置值
		"lhdOrRhd": "",-> 左驾车右驾车 L/R/X
        "comment": "", -> 注释
    },
    {},
    {}
]

```


#### 按library_id 和 option_id获取 library-optional-property-setting

GET /library-optional-property-setting/{library_id}/{option_id}

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "modelCode": "", -> model唯一代码
		"propertyContent": "", ->设置值
		"lhdOrRhd": "",-> 左驾车右驾车 L/R/X
        "comment": "", -> 注释
    },
    {},
    {}
]

```


#### 按library_id 和 option_id和 model_code获取 library-optional-property-setting

GET /library-optional-property-setting/{library_id}/{option_id}/{model_code}

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "modelCode": "", -> model唯一代码
		"propertyContent": "", ->设置值
		"lhdOrRhd": "",-> 左驾车右驾车 L/R/X
        "comment": "", -> 注释
    },
    {},
    {}
]

```


#### 按library_id 和 option_id和 model_code获取 library-optional-property-setting

GET /library-optional-property-setting/{library_id}/{option_id}/{model_code}

返回格式:

```
HTTP Stauts Code: 200

BODY:


{
	"id": "1", ->唯一标示
	"libraryId": "" 对应library表id
	"optionId": "", -> 配件Id
	"modelCode": "", -> model唯一代码
	"propertyContent": "", ->设置值
	"lhdOrRhd": "",-> 左驾车右驾车 L/R/X
	"comment": "", -> 注释
}

```



#### 按library_id 和 classify获取 library-optional-property-setting

GET /library-optional-property-setting/{library_id}/classify/{classify_id}

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "modelCode": "", -> model唯一代码
		"propertyContent": "", ->设置值
		"lhdOrRhd": "",-> 左驾车右驾车 L/R/X
        "comment": "", -> 注释
    },
    {},
    {}
]

```


#### 按library_id获取所有 library-option-rule

GET /library-option-rule/{library_id}

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "modelCode": "", -> model唯一代码
		"propertyContent": "", ->设置值
		"relationType": "",-> 关系类型
        "correlatedObj": "", -> 复杂关系内容
		"lhdOrRhd": "", -> 复杂关系内容
		"rrpWithVat": "", -> 价格,只有combine关系的时候被设定
		"rrpWithoutVat": "", -> 价格,只有combine关系的时候被设定
		"efpImp": "", -> 价格,只有combine关系的时候被设定
		"efpSubs": "", -> 价格,只有combine关系的时候被设定
		"comment": "", -> 注释
    },
    {},
    {}
]

```

#### 按library_id 和 option_id获取 library-option-rule

GET /library-option-rule/{library_id}/{option_id}

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "modelCode": "", -> model唯一代码
		"propertyContent": "", ->设置值
		"relationType": "",-> 关系类型
        "correlatedObj": "", -> 复杂关系内容
		"lhdOrRhd": "", -> 复杂关系内容
		"rrpWithVat": "", -> 价格,只有combine关系的时候被设定
		"rrpWithoutVat": "", -> 价格,只有combine关系的时候被设定
		"efpImp": "", -> 价格,只有combine关系的时候被设定
		"efpSubs": "", -> 价格,只有combine关系的时候被设定
		"comment": "", -> 注释
    },
    {},
    {}
]

```

#### 按library_id 和 option_id获取 library-option-rule

GET /library-option-rule/{library_id}/{option_id}

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "modelCode": "", -> model唯一代码
		"propertyContent": "", ->设置值
		"relationType": "",-> 关系类型
        "correlatedObj": "", -> 复杂关系内容
		"lhdOrRhd": "", -> 复杂关系内容
		"rrpWithVat": "", -> 价格,只有combine关系的时候被设定
		"rrpWithoutVat": "", -> 价格,只有combine关系的时候被设定
		"efpImp": "", -> 价格,只有combine关系的时候被设定
		"efpSubs": "", -> 价格,只有combine关系的时候被设定
		"comment": "", -> 注释
    },
    {},
    {}
]

```


#### 按library_id 和 option_id和 model_code获取 library-option-rule

GET /library-option-rule/{library_id}/{option_id}/{model_code}

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "libraryId": "" 对应library表id
        "optionId": "", -> 配件Id
        "modelCode": "", -> model唯一代码
		"propertyContent": "", ->设置值
		"relationType": "",-> 关系类型
        "correlatedObj": "", -> 复杂关系内容
		"lhdOrRhd": "", -> 复杂关系内容
		"rrpWithVat": "", -> 价格,只有combine关系的时候被设定
		"rrpWithoutVat": "", -> 价格,只有combine关系的时候被设定
		"efpImp": "", -> 价格,只有combine关系的时候被设定
		"efpSubs": "", -> 价格,只有combine关系的时候被设定
		"comment": "", -> 注释
    },
    {},
    {}
]

```


#### 所有 profile

GET /profile/all-profile
@RequestParam status

返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "eseriesCode": "" eseries_code
        "profileName": "", -> profile 名称
        "profileUrl": "", -> 上传url
		"importDate": "", ->导入时间
		"basedLibraryId": "",-> 基于libarary id
        "newLibraryId": "", -> 新库id
		"sortDate": "", -> 排序时间
		"isResponsible": "", -> 是否可以响应
		"bmwProfileCode": "", -> 导入时excel 表中响应的code
		"rootProfileId": "", -> 根profile id
		"parentProfileId": "", -> 父级 profile id
		"content": "" , -> 内容
		"profileFlag": "" , -> 标签
		"status": "" , -> 状态
		"previousStatus": "", -> 前一个状态
    },
    {},
    {}
]

```

#### 按profile_id获取 profile

GET /profile/{profile_id}

返回格式:

```
HTTP Stauts Code: 200

BODY:


{
	"id": "1", ->唯一标示
	"eseriesCode": "" eseries_code
	"profileName": "", -> profile 名称
	"profileUrl": "", -> 上传url
	"importDate": "", ->导入时间
	"basedLibraryId": "",-> 基于libarary id
	"newLibraryId": "", -> 新库id
	"sortDate": "", -> 排序时间
	"isResponsible": "", -> 是否可以响应
	"bmwProfileCode": "", -> 导入时excel 表中响应的code
	"rootProfileId": "", -> 根profile id
	"parentProfileId": "", -> 父级 profile id
	"content": "" , -> 内容
	"profileFlag": "" , -> 标签
	"status": "" , -> 状态
	"previousStatus": "", -> 前一个状态
}

```



#### 按eseries_code 获取 profile

GET /profile/by-eseries/{eseries_code}
@RequestParam status
@RequestParam isLaunched

返回格式:

```
HTTP Stauts Code: 200

BODY:

{
	yearLunchedLeft:[
		{
			"showYearText" :"2019 profile",
			"profileVoList" : ->profiles
		},
		{}
	]
	yearUnLunchedRight: [
		{
			"showYearText" :"2019 profile",
			"profileVoList" : ->profiles
		},
		{}
	]
}



profiles: 
[
    {
        "id": "1", ->唯一标示
        "eseriesCode": "" eseries_code
        "profileName": "", -> profile 名称
        "profileUrl": "", -> 上传url
		"importDate": "", ->导入时间
		"basedLibraryId": "",-> 基于libarary id
        "newLibraryId": "", -> 新库id
		"sortDate": "", -> 排序时间
		"isResponsible": "", -> 是否可以响应
		"bmwProfileCode": "", -> 导入时excel 表中响应的code
		"rootProfileId": "", -> 根profile id
		"parentProfileId": "", -> 父级 profile id
		"content": "" , -> 内容
		"profileFlag": "" , -> 标签
		"status": "" , -> 状态
		"previousStatus": "", -> 前一个状态
    },
    {},
    {}
]

```




#### 改变profile status

POST /profile/{profile_id}/change-status



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



#### 导入profile

POST /profile/import-profile

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





#### 所有 profile_id的 profile-varient

GET /profile-varient/{profile_id}


返回格式:

```
HTTP Stauts Code: 200

BODY:

[
    {
        "id": "1", ->唯一标示
        "profileId": "" profile id
        "varientId": "", -> 车变种id
        "modelCode": "", -> model唯一代码 对应 config_model -> code
		"modelCodeVarient": "", ->确定唯一列的标志因子,原model_code
		"packageCodeVarient": "",-> 确定唯一列的标志因子,原package_code
        "modelNameCn": "", -> 原 cn_model (model 中文显示名称)
		"variantName": "", -> 变种名称
		"variantNameCn": "", -> 变种中文名称
		"lineCode": "", -> Line Package Code
		"aditionalOptions": "", -> Aditional Options
		"engineOutput": "", -> Engine Output
		"volumeMixPlanning": "" , -> Volume Mix planning
		"dofForModell": "" , -> DOF for Modell
		"index": "" , -> 顺序
		"sop": "", -> SOP 开始时间
		"eop": "", -> EOP 结束时间
		"optionCodeInIvsr": "", -> option code in ivsr
		"priceTransitionResult": "", -> Detail Price transition result
		"priceIncreaseAbs": "", -> Nominal price increase abs.
		"monetaryDdjustment": "", -> Monetary adjustment
		"price": "", -> price
    },
    {},
    {}
]

```



####  profile_id和varient_id匹配单个profile-varient对象

GET /profile-varient/{profile_id}/{varient_id}


返回格式:

```
HTTP Stauts Code: 200

BODY:


{
	"id": "1", ->唯一标示
	"profileId": "" profile id
	"varientId": "", -> 车变种id
	"modelCode": "", -> model唯一代码 对应 config_model -> code
	"modelCodeVarient": "", ->确定唯一列的标志因子,原model_code
	"packageCodeVarient": "",-> 确定唯一列的标志因子,原package_code
	"modelNameCn": "", -> 原 cn_model (model 中文显示名称)
	"variantName": "", -> 变种名称
	"variantNameCn": "", -> 变种中文名称
	"lineCode": "", -> Line Package Code
	"aditionalOptions": "", -> Aditional Options
	"engineOutput": "", -> Engine Output
	"volumeMixPlanning": "" , -> Volume Mix planning
	"dofForModell": "" , -> DOF for Modell
	"index": "" , -> 顺序
	"sop": "", -> SOP 开始时间
	"eop": "", -> EOP 结束时间
	"optionCodeInIvsr": "", -> option code in ivsr
	"priceTransitionResult": "", -> Detail Price transition result
	"priceIncreaseAbs": "", -> Nominal price increase abs.
	"monetaryDdjustment": "", -> Monetary adjustment
	"price": "", -> price
}

```


#### 保存 saveOrUpdate varient对象

PUT /profile-varient/{profile_id}/{varient_id}



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

#### 删除 varient对象

DELETE /profile-varient/{profile_id}/{varient_id}



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




#### 按profile_id获得基础的 profile option 

GET /profile-option/{profile_id}/show_self


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

#### 所有 profile_id和option_id 确定唯一 profile-option 

GET /profile-option/{profile_id}/{option_id}


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



#### 显示和最新library的区别

GET /profile-option/{profile_id}/show_diff


返回格式:

```
HTTP Stauts Code: 200

BODY:

{
	onlyInProfile: [
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
	onlyInNewLibrary: [
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
}


```



#### 显示最新library的设置 

GET /profile-option/{profile_id}/show_library


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

#### 显示最后需要显示的数据 profile 中的数据 + library 中定义为标配的数据 

GET /profile-option/{profile_id}/show_result


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
		"isInProfile": false, -> 是否在profile中存在
		"isInNewLibrary": false, -> 是否在new Library中存在
    },
    {},
    {}
]

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
用户增加或减少profile中的option 的数据，会在这个接口里体现,
此方法需按profile_id 对应的option list 
当复制的时候这些数据需要复制过去
不同的 changeType 需要显示不同的颜色
```



#### 所有 profile_id和option_id 查询相关的 profile-option-change

GET /profile-option-change/{profile_id}/{option_id}


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
用户增加或减少profile中的option 的数据，会在这个接口里体现,
此方法需按profile_id 对应的option list 
当复制的时候这些数据需要复制过去
不同的 changeType 需要显示不同的颜色
```

#### 新增 修改 删除 profile-option-change

POST /profile-option-change/{profile_id}

上送数据

{
	"optionId": "1", ->配件id
	"classify":"", ->类型
    "changeType": "", -> 增加还是删除 + -
}



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


#### 所有 profile_id的 profile-cell-setting

GET /profile-cell-setting/{profile_id}


返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->主键
        "profileId": "7", -> profile id
        "varientId": "", -> config_profile_varient-> id
        "optionId": "", -> 配件id
        "settingContent": "", ->设置值
        "showContent":"", ->显示值
    },
    {},
    {}
]

```

#### 所有 profile_id和option_id profile-cell-setting

GET /profile-cell-setting/{profile_id}/option/{option_id}


返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->主键
        "profileId": "7", -> profile id
        "varientId": "", -> config_profile_varient-> id
        "optionId": "", -> 配件id
        "settingContent": "", ->设置值
        "showContent":"", ->显示值
    },
    {},
    {}
]

```


#### 所有 profile_id和varient_id 相关的 profile-cell-setting

GET /profile-cell-setting/{profile_id}/varient/{varient_id}


返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "id": "1", ->主键
        "profileId": "7", -> profile id
        "varientId": "", -> config_profile_varient-> id
        "optionId": "", -> 配件id
        "settingContent": "", ->设置值
        "showContent":"", ->显示值
    },
    {},
    {}
]

```


#### profile_id和varient_id 和 option_id 确定唯一 profile-cell-setting

GET /profile-cell-setting/{profile_id}/{option_id}/{varient_id}


返回格式:

```
HTTP Stauts Code: 200

BODY:

{
	"id": "1", ->主键
	"profileId": "7", -> profile id
	"varientId": "", -> config_profile_varient-> id
	"optionId": "", -> 配件id
	"settingContent": "", ->设置值
	"showContent":"", ->显示值
}

```

#### 修改 cell-setting 这个PUT 是saveOrUpdate

PUT /profile-cell-setting/{profile_id}/{option_id}/{varient_id}

上送数据
{
	"settingContent": "", ->设置值
	"showContent":"", ->显示值
}



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

