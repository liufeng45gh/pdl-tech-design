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

注: 该接口用作创建配件车系


#### 4. 删除配件车系

POST http://40.73.0.200:8762/carConfig/deleteCarConfigVariant

上送: BODY: {id:"XXXX"}

返回: 
```
{
    "code": "0", // “0” 表示成功 ，“1”表示失败
    "message": "成功！"
}
```
注: 该接口用作删除配件车系

#### 5. 修改状态

POST http://40.73.0.200:8762/carConfig/updateCarConfigVariantStatusById

上送: BODY: {id:"XXX",currentStatus:"XXX",updateDate:"XXX",previousStatus:"XXX"}

返回: 
```
{
    "code": "0", // “0” 表示成功 ，“1”表示失败
    "message": "成功！"
}
```
注: 该接口用作修改配置中profile的状态

#### 6. 根据系列、E系列、用户ID 获取lib版本

POST http://40.73.0.200:8762/carConfig/getLibVersion

上送: BODY: {Serise:"XXX",eSeries:"XXX",userId:"XXX"}

返回: 
```
{
    "code": 0,           // “0” 表示成功 ，“1”表示失败
    "data": [{
        "id": 454798,    //  版本ID
        "version": 1.0    //  版本名称
    }],
    "message": "成功！"
}
```

注: 该接口用作获取 library 的版本


#### 7. 根据用户ID、Profileid 获取 Profile详情

POST http://40.73.0.200:8762/carConfig/getProfileDeteils

上送: BODY: {userId:"XXX",profileId:"XXX"}

返回: 
```
{
    "code": 0,     // “0” 表示成功 ，“1”表示失败
    "data": [{
        "id": 454798,    //  版本ID
        "version": 1.0    //  版本名称
    }],
    "message": "成功！"
}
```
注: 该接口用来获取profile的详情

#### 8. 根据用户ID、Profleid获取lunchProfle详情

POST http://40.73.0.200:8762/carConfig/getLunchProfileList

上送: BODY: {userId:"XXX"}

返回: 
```
{
    "code": 0,
    "data": [{
        "id": null,
        "series": "Series12",                  //  系列
        "eSeries": "G12",                     // E系列
        "profileName": "G32_Product_profile_sample(2) - .xlsx",  // 文件名称
        "profileUrl": "/usr/local/pandora/serverAPI/temp/profile", // 文件路径
        "importDate": "2019-02-27",                          // 导入日期
        "basedLibraryVersion": null,                          // libraryVersion
        "basedProfileName": null
    }],
    "message": "成功！"
}
```
注: 该接口用来获取lunchProfile的详情

#### 9. 根据brand获取系列信息

POST http://40.73.0.200:8762/carConfig/getSeriseByBrand?brand=1

上送 :BODY：{brand:"XXX"}

返回 : 
```
{
    "data": [{
        "id": 1,             // 系列ID
        "nameEn": "1 Series", // 系列英文名称
        "nameZh": null      // 系列中文名称
    }]
}
```
注: 该接口用来获取系列详情


#### 10. 根据系列查询E系列

POST http://40.73.0.200:8762/carConfig/getESeriseBySerise?seriseid=7

上送 :BODY：{seriseid:"XXX"}

返回：
```
{
    "code": 0,
    "data": [{
        "id": null,
        "message": "成功"，
        "version": 1.0,                                             // 版本id
        "basicFileName": "7_Series_Sedan_(G11_G12)_basic(1).xlsx",      // basicFileName
        "optionalFileName":"7_Series_Sedan_(G11_G12)_optional(1).xlsx"   // optionalFileName
    }]
}
```
注：该接口是根据大系获取小系集合

#### 11. 根据车型车系获取FC数据 (目前还未使用)

POST /BmwVolumeMix/ findAllBySeriesAndEseries

上送：BODY：{Serises:"XXX",eSerises:"XXX",year:"XXX"}

返回：
```
Code说明 0-成功、1-失败

{
    "msg": "ok",
    "code": 0,
    "data": [
        {
            "id": 265301,
            "series": "7",
            "eseries": "G12",
            "variant": "730Li  MSP",
            "model_code": "7E01",
            "package_code": "ZOM ",
            "year": 2019,
            "jan_volume": 1000,
            "feb_volume": 1000,
            "mar_volume": 1000,
            "apr_volume": 1000,
            "sep_volume": 1000,
            "oct_volume": 1000,
            "jul_volume": 1000,
            "total_volume": 12000,
            "aug_volume": 1000,
            "dec_volume": 1000,
            "nov_volume": 1000,
            "may_volume": 1000,
            "jun_volume": 1000
        }
    ]
}
```
注：该接口用作获取FC数据


#### 12. 根据车型车系数据类型年份区间获取BP\BU\LRP数据

POST /BmwVolumeMix/GetVolumeBySeriesAndEseriesAndStartAndEnd

request: {Serises :"XXX",eSerises:"XXX",start:"XXX",end:"XXX",Tpye:"XXX"}

response:
```
Code说明 0-成功、1-失败、2-没有数据
{
    "code": 0,
    "data": {
        "M760Li xD \nV12 Excellence": [
            {
                "id": 265114,
                "series": "7",
                "eseries": "G12",
                "variant": "M760Li xD \nV12 Excellence",
                "model_code": "7E01",
                "package_code": "ZSL",
                "year": 2019,
                "type": "2",
                "volume": 1000
            } ],
        "750Li xDrive MSP": [
            {
                "id": 265092,
                "series": "7",
                "eseries": "G12",
                "variant": "750Li xDrive MSP",
                "model_code": "7E01",
                "package_code": "ZOM ",
                "year": 2019,
                "type": "2",
                "volume": 1000
            } ]
    }
}
```
注：该接口是根据车型车系数据类型年份区间获取BP\BU\LRP数据


#### 13. 保存volumeMix

POST  /BmwVolumeMix/SaveVolumeMix

上送：
```
saveData:
[{
            "id": "421518",
            "profileName": "test1",
            "variant": "730Li  MSP",
            "modelCode": "7E01",
            "packageCode": "ZOM ",
            "itemsList":[
                {
                    "id": 421546,
                    "year": 2020,
                    "volume": 1000,
                    "carId": 421518
                }   
            ]
            
        }]
```


#### 14. 获取单独年份的BU\BP\LRP值  

POST  /BmwVolumeMix/GetVolumeByYearAndType

上送：BODY：{Serises:"XXX",eSerises:"XXX",year:"XXX",type:"XXX"}

response : 
```
{
    "code": 0,
    "data": [
        {
            "id": 421518,
            "series": "7",
            "e_series": "G12",
            "variant": "730Li  MSP",
            "model_code": "7E01",
            "package_code": "ZOM ",
            "type": "2",
            "dataList": [
                {
                    "id": 421546,
                    "year": 2020,
                    "volume": 1000,
                    "carId": 421518
                }
            ],
            "total": 1000,
            "percentage": 0
        } 
]
}
```

#### 15.获取保存后的数据

POST /BmwVolumeMix/GetSaveVolumeDataByProfileName

上送：BODY：{profileName:"XXX"}

返回：
```
{
    "code": 0,
    "dataList": [
        {
            "id": "422490",
            "profileName": "test1",
            "variant": "730Li  MSP",
            "modelCode": "7E01",
            "packageCode": "ZOM ",
            "itemsList": [
                {
                    "id": 422491,
                    "year": 2020,
                    "volume": 1000,
                    "managementid": 422490
                }
            ]
        }
    ]
}
```
注：

#### 16. 最新版数据读取接口

POST http://40.73.0.200:8762/BmwVolumeMix/GetVolumeBySeriesAndEseriesAndStartAndEnd

request: {Serises :"XXX",eSerises:"XXX",start:"XXX",end:"XXX",Tpye:"XXX"}

response: 
```
{
    "code": 0,
    "data": [
        {
            "rowId": 422853,
            "modelLabel": null,
            "codeLabel": null,
            "totalValue": null,
            "percentageValue": null,
            "variant": "730Li  MSP",
            "model_code": "7E01",
            "package_code": "ZOM ",
            "optionsList": [
                {
                    "optionsId": 1,
                    "selectedTypeId": 1,
                    "selectedValue": 1,
                    "year": "2019",
                    "valueList": [
                        {
                            "typeId": 4,
                            "value": 1000
                        }
                    ]
                }
            ]
        }
    ]
}
```
注：

#### 17. 获取library list

GET http://40.73.0.200:8088/libDetail/getModel

request: {Serises :"XXX",eSerises:"XXX"}

返回：
```
{
    "resultMsg": "成功",
    "resultCode": 0,
    "result": [{
        "id": 252740,
        "model": "730i"
    }]}
```



#### 18. 获取车library basic blocklist

GET http://40.73.0.200:8088/libDetail/getBasicProperty

request: {Serises :"XXX",eSerises:"XXX"}

返回：
```
resultCode  返回码 0-成功1-错误编码

{
    "resultMsg": "成功",
    "resultCode": 0,
    "result": [{
        "id": 252764,
        "systemPropertyCode": "15504698223046793122",
        "block": "1. Passive safety",
        "comment": "with seat occupancy detection for driver's and passenger side"
    }]
}

```


---------------

#### 19. 获取车library basic property setting

GET http://40.73.0.200:8088/libDetail/getBasicPropertySet

request: {Serises :"XXX",eSerises:"XXX",model:"XXX",systemPropertyCode:"XXX"}

返回：
```
resultCode  返回码 0-成功1-错误编码

{
    "resultMsg": "成功",
    "resultCode": 0,
    "result": [{
        " systemPropertyCode
": 15504698223046793122,
        "propertyContent": "730i",
"lhdOrRhd": "X",

"commet": ""

    }]
}
```


#### 20. 获取车library optionnal property

GET http://40.73.0.200:8088/libDetail/getOptionalProperty

request: {Serises :"XXX",eSerises:"XXX"}

返回：
```
resultCode  返回码 0-成功1-错误编码

{
    "resultMsg": "成功",
    "resultCode": 0,
    "result": [{
        "id": 256389,
        "systemPropertyCode": "15504700767045650475",
        "comment": "note: refer to the country specific offer",
        "classify": "1"
    }]
}
```


#### 21. 通过property type获取sysOptions

GET http://40.73.0.200:8088/libDetail/getSysOption

request: {Serises :"XXX",eSerises:"XXX",propertyType:"XXX"}
```
propertyType : 必须传值 默认01
```

返回：
```

{
    "resultMsg": "成功",
    "resultCode": 0,
    "result": [{
        "systemPropertyCode": "15504698223046793122",
        "propertyCode": "",
        "propertyNameEn": "airbag for driver and front passenger"
    }]
}

```


#### 22. 获取 library rule list

GET http://40.73.0.200:8088/libDetail/getLibraryRule

request: {Serises :"XXX",eSerises:"XXX"}

返回：
```
{
    "resultMsg": "成功",
    "resultCode": 0,
    "result": [{
        "systemPropertyCode": "15505732227133293170",
        "relationType": "2",
        "correlatedObj": "only with 8AA"
    }]
}

```


#### 23. 根据LibraryE系列获取系列

GET http://40.73.0.200:8762/carConfig/getLibraryESeriseAndSerise

参数：{Serises :"XXX",eSerises:"XXX"}

返回JSON
```
{
    "code": 0,
    "data": [{
        "id": null,
"message": "成功"，
        "version": 1.0,                                          // 版本id
        "basicFileName": "7_Series_Sedan_(G11_G12)_basic(1).xlsx",      // basicFileName
        "optionalFileName":"7_Series_Sedan_(G11_G12)_optional(1).xlsx"   // optionalFileName
    }]
}

```

#### 24. FC上传

POST /Volume/improtVolumeFC

上送: BODY: {"file":"XXX",userId:"XXX"}

返回: 
```
Code    返回码 0-成功1-错误编码
```

#### 25. BP上传

POST /Volume/ improtVolumeBP

上送: BODY: {"file":"XXX",userId:"XXX"}

返回: 
```
Code    返回码 0-成功1-错误编码
```

#### 26. BU上传

POST /Volume/improtVolumeBU

上送: BODY: {"file":"XXX",userId:"XXX"}

返回: 
```
Code    返回码 0-成功1-错误编码
```

#### 27. LRP上传

POST /Volume/improtVolumeLRP

上送: BODY: {"file":"XXX",userId:"XXX"}

返回: 
```
Code    返回码 0-成功1-错误编码
```
