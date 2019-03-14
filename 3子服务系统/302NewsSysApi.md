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
 POST | /import-library | 导入library 需要显示导入进度 | response-result | 
  | | | |
 GET| /library-basic-property/{library_id}|按library_id获取所有 library-basic-property| []|
 GET| /library-basic-property/{library_id}/{item_id}|按library_id 和 item_id获取 library-basic-property| {}|
 GET| /library-basic-property/{library_id}/classify/{classify_id}|按library_id 和 classify获取 library-basic-property| []|
  | | | |
 GET| /library-basic-property-setting/{library_id}|按library_id获取所有 library-basic-property-setting| []|
 GET| /library-basic-property-setting/{library_id}/{item_id}|按library_id 和 item_id获取 library-basic-property-setting| []|
  GET| /library-basic-property-setting/{library_id}/{item_id}/{model_code}|按library_id 和 item_id和 model_code获取 library-basic-property-setting| {}|
 GET| /library-basic-property-setting/{library_id}/classify/{classify_id}|按library_id 和 classify获取 library-basic-property-setting| []|
   | | | |
 GET| /library-optional-property/{library_id}|按library_id获取所有 library-optional-property| []|
 GET| /library-optional-property/{library_id}/{item_id}|按library_id 和 item_id获取 library-optional-property| {}|
 GET| /library-optional-property/{library_id}/classify/{classify_id}|按library_id 和 classify获取 library-optional-property| []|
  | | | |
 GET| /library-optional-property-setting/{library_id}|按library_id获取所有 library-optional-property-setting| []|
 GET| /library-optional-property-setting/{library_id}/{item_id}|按library_id 和 item_id获取 library-optional-property-setting| []|
  GET| /library-optional-property-setting/{library_id}/{item_id}/{model_code}|按library_id 和 item_id和 model_code获取 library-optional-property-setting| {}|
 GET| /library-optional-property-setting/{library_id}/classify/{classify_id}|按library_id 和 classify获取 library-optional-property-setting| []|
  | | | |
 GET| /library-item-rule/{library_id}|按library_id获取所有 library-item-rule| []|
 GET| /library-item-rule/{library_id}/{item_id}|按library_id 和 item_id获取 library-item-rule| []|
 GET| /library-item-rule/{library_id}/{item_id}/{model_code}|按library_id 和 item_id和 model_code获取 library-item-rule| []|
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
 GET| /profile-varent/{profile_id}|所有 profile_id的 profile-varent| []|
 GET| /profile-varent/{profile_id}/{varent_id}|profile_id和varent_id匹配单个对象| {}|
  | | | |
 GET| /profile-item/{profile_id}|所有 profile_id的 profile-item| []|
 GET| /profile-item/{profile_id}/{item_id}|所有 profile_id和item_id 确定唯一 profile-item| {}|
  | | | |
 GET| /profile-item-change/{profile_id}|所有 profile_id的 profile-item-change| []|
 GET| /profile-item-change/{profile_id}/{item_id}|所有 profile_id和item_id 确定唯一 profile-item-change| {}|
   | | | |
 GET| /profile-cell-setting/{profile_id}|所有 profile_id的 profile-cell-setting| []|
 GET| /profile-cell-setting/{profile_id}/item/{item_id}|所有 profile_id和item_id  profile-cell-setting| []|
 GET| /profile-cell-setting/{profile_id}/varient/{varient_id}|所有 profile_id和varient_id 相关的  profile-cell-setting| []|
 GET| /profile-cell-setting/{profile_id}/{item_id}/{varient_id}| profile_id和varient_id 和 item_id 确定唯一  profile-cell-setting| {}|
 POST| /profile-cell-setting/{profile_id}/{item_id}/{varient_id}| profile_id和varient_id 和 item_id 确定唯一  profile-cell-setting,这个post 是修改| response-result|







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

