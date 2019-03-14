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
 GET | /models/code |按code 获取model| {} | 
  | | | | 
 GET | /all-items|获取所有配件(分页，默认30)| [] |
 GET | /item/{item_id}|获取某个配件| {} |
 GET | /items-by-property-code/{property_code}|按property_code获取配件| [] |
  | | | | 
 GET | /all-library | 所有library | []|
 GET | /all-library?status={status}   | 获取不同status 下的所有library | [] |
 GET | /eseries/eseries_code/library?status={status}   | 获取不同e系列下不同status 下的所有library | [] |
 GET | /library/{id}  | 获取一个library |{} |
 GET | /library-by-version/{version}  | 按version获取一个library| {}|
 POST | /import-library | 导入library | response-result | 
  | | | |
 
 POST| /
 
### 3.5.3.2. 各接口的样例数据及字段解释

#### 获得圈子所有的版块信息

GET http://group.service.9h.com/v1/sections

返回格式:

```
HTTP Stauts Code: 200

BODY:
[
    {
        "sectionId": "1", ->版块id
        "title": "中超联赛", -> 版块名称
        "logo": "", -> 版块的缩略图,为俱乐部队徽
        "clubId": "", -> 关联俱乐部id，中超联赛的版块不关联clubId
        "bgImage": "", ->背景图片
        "isHidden":"", ->是否显示
        "topics": 3456, -> 发帖数
        "bgImage": "", ->背景图
        "timestamp": "",->时间戳
    },
    {},
    {}
]

```

#### 获得某个圈子的版块信息

GET http://group.service.9h.com/v1/sections/{section_id}

@param sectionId @PathVariable("section_id") 板块id

返回格式:

```
{

                "sectionId": "1", ->版块id
                "title": "中超联赛", -> 版块名称
                "logo": "", -> 版块的缩略图,为俱乐部队徽
                "clubId": "", -> 关联俱乐部id，中超联赛的版块不关联clubId
                "bgImage": "", ->背景图片
                "isHidden":"", ->是否显示
                "topics": 3456, -> 发帖数
                "bgImage": "", ->背景图

}
```