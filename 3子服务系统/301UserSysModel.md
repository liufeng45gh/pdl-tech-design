### 3.1.1. 数据模型

#### 启动的profile(bmw_launched_profile)
 字段名 | 解释 
 :-- | :-- 
id           		  	|主键ID,自增长(长整,以下所有id字段皆为该规则)
series        		  	|车系（大系）
e_series     		  	|车系（小系）
profile_name  		  	|导入的profile名称
profile_url   		  	|导入的profile路径
import_date  		  	|导入profile日期
based_library_version	|导入的profile版本号
based_profile_name      |based profile 名称
brand_id      		  	|车品牌ID（通过bmw_brand获取车系列，例如 BMW 、 MINI）
user_id  	          	|用户ID
sort_date     		  	|短日期
is_responsible     	  	|权限字段（判断是否有权限查看）
profile_id   		  	|导入的profile的ID

修改建议：
```
1.主键ID应设为 profile_id (去除现有的id字段)
2.为区分导入的profile跟生成的profile，建议新加parent_id
3.去除冗余字段（based_profile_name 跟 profile_name 取一个即可）
```

#### profile管理表(bmw_profile_management)
 字段名 | 解释 
 :-- | :-- 
id        				|主键ID
series        		  	|车系（大系）
e_series     		  	|车系（小系）
profile_name 			|拖拽的profile名称
current_status    		|状态（1：draft 2：Cancel 3：finish 4：verified(launched)）
previous_status 		|之前的状态
creater       			|创建人
create_time  			|创建时间
updater      			|更新人
update_time   			|更新时间
creater_user_id     	|创建人ID
updater_user_id     	|更新人ID
sort_date    			|短日期
profile_id   			|导入的profileID
content      			|快照内容
profile_flag 			|profile标识
new_profile_id 			|新生成的profileID
new_library_id 			|新导入的libraryID

修改建议：
```
1.主键ID应设为 new_profile_id (去除现有的id字段)|
2.profile_id 用作关联 bmw_launched_profile 中的 profile_id
```


#### 车辆基本信息表(bmw_profile_generation_information)
 字段名 | 解释 
 :-- | :-- 
id                  	|主键ID
series        			|车系（大系）
e_series     			|车系（小系）
profile_name        	|拖拽的profile名称
model               	|车型分类（740Li,730Li,750Le....）
model_code          	|车型码
package_code        	|包代码
cn_model            	|中文model
variant             	|车
cn_variant          	|中文variant
line_code           	|行代码
aditional_options   	|附加选项
engine_output       	|发动机输出功率
volume_mix_planning 	|体积混合规划
dof_for_modell      	|？？？
user_id             	|用户ID
current_status      	|状态（1：draft 2：Cancel 3：finish 4：verified(launched)）
previous_status     	|之前的状态
sort_date           	|短日期
sop                 	|开始日期
eop                 	|结束日期
option_code_in_ivsr 	|？？？？
price_transition_result |价钱（经过计算之后）
price_increase_abs  	|价格上涨
price_increase_per  	|价格上涨（欧元）
monetary_adjustment 	|货币调控
profile_id          	|导入的profileID
varient_id          	|车ID
option_code_input   	|输入的选项code
model_variant       	|车的mode + variant
price               	|车价钱

修改建议：
```
1.去除冗余字段。
2.设置关联ID/字段
```

#### 100% option 表(bmw_profile_basic_option)
 字段名 | 解释 
 :-- | :-- 
id        			|主键ID
series        		|车系（大系）
e_series     		|车系（小系）
profile_name        |拖拽的profile名称
model               |车型分类（740Li,730Li,750Le....）
model_code          |车型码
package_code        |包代码
property_code       |属性码
property_name_en    |属性英文名称
property_name_cn    |属性中文名称
setting_content     |设置内容
show_content        |展示内容
user_id             |用户ID
varient_id          |车ID
classify            |分类（1：100% option 2：Uphostory 3：Wheel 4：paint 5：trim）
option_id           |选项行ID
profile_id          |导入的profileID
rmb_price           |单元格人民币价格
option_price        |option价格
discount            |折扣
compar_flag         |比对标识（0：原有的  1：新增的）

修改建议：
```
1.去除冗余字段。
2.设置关联ID/字段
```

#### 灵活选配包表(bmw_profile_flexible_package)
 字段名 | 解释 
 :-- | :-- 
id        				|主键ID
series        			|车系（大系）
e_series     			|车系（小系）
profile_name        	|拖拽的profile名称
model               	|车型分类（740Li,730Li,750Le....）
model_code          	|车型码
package_code        	|包代码
flexible_package_code 	|灵活选配包码
classify            	|分类（6: flexible package）
package_name_en     	|包英文名
package_name_cn     	|包中文名
setting_content     	|设置内容
show_content        	|展示内容
user_id             	|用户ID
property_code       	|属性码
package_setting     	|包设置值
varient_id          	|车ID
option_id           	|选项行ID
profile_id          	|导入的profileID

修改建议：
```
1.去除冗余字段（例：classify字段）。
2.设置关联ID/字段
```

#### 灵活选配项(bmw_profile_flexible_option)
 字段名 | 解释 
 :-- | :-- 
id                  |主键ID
series        		|车系（大系）
e_series     		|车系（小系）
profile_name        |拖拽的profile名称
model               |车型分类（740Li,730Li,750Le....）
model_code          |车型码
package_code        |包代码
property_code       |属性码
classify            |分类（7）
property_name_en    |属性英文名称
property_name_cn    |属性中文名称
setting_content     |设置内容
show_content		|展示内容
user_id             |用户ID
varient_id          |车ID
option_id           |选项行ID
profile_id          |导入的profileID
rmb_price           |单元格人民币价格
option_price        |option价格
discount            |折扣

修改建议：
```
1.去除冗余字段
2.设置关联ID/字段
```

#### 其他配置项(bmw_profile_other)
 字段名 | 解释 
 :-- | :-- 
id                  |主键ID
series        		|车系（大系）
e_series     		|车系（小系）
profile_name        |拖拽的profile名称
model               |车型分类（740Li,730Li,750Le....）
model_code          |车型码
package_code        |包代码
property_code       |属性码
classify            |分类（8、9）
property_name_en    |属性英文名称
property_name_cn    |属性中文名称
setting_content     |设置内容
show_content		|展示内容
user_id             |用户ID
varient_id          |车ID
option_id           |选项行ID
profile_id          |导入的profileID
rmb_price           |单元格人民币价格
option_price        |option价格
discount            |折扣

修改建议：
```
1.去除冗余字段
2.设置关联ID/字段
```

#### Library管理表(bmw_library_management)
 字段名 | 解释 
 :-- | :-- 
id                  |主键ID
series        		|车系（大系）
e_series     		|车系（小系）
version             |版本号
import_date         |导入日期
basic_file_name     |Basic文件名
basic_file_url      |Baisc文件路径
optional_file_name  |optional文件名称
optional_file_url   |optional文件路径
library_output_date |
libarary_data_date	|
sort_date           |短日期

修改建议：
```

```

#### Library Basic属性表(bmw_library_basic_property)
 字段名 | 解释 
 :-- | :-- 
id                  |主键ID
series        		|车系（大系）
e_series     		|车系（小系）
version             |版本号
system_property_code|导入时自动生成的唯一标识
block     			|所属区块
basic_file_url      |Baisc文件路径
comment  			|注释说明
create_time   		|创建时间

修改建议：
```

```

#### Library Basic属性设置表(bmw_library_basic_property_setting)
 字段名 | 解释 
 :-- | :-- 
id                  |主键ID
series        		|车系（大系）
e_series     		|车系（小系）
version             |版本号
system_property_code|导入时自动生成的唯一标识
model     			|车模型（例如：730Li,740Le...）
property_content    |属性内容
lhd_or_rhd  		|左驾车右驾车
comment   			|注释说明
create_time   		|创建时间

修改建议：
```

```

#### Library optional属性表(bmw_library_optional_property)
 字段名 | 解释 
 :-- | :-- 
id                  |主键ID
series        		|车系（大系）
e_series     		|车系（小系）
version             |版本号
system_property_code|导入时自动生成的唯一标识
classify     		|类型（1：100% option 2：Uphostory 3：Wheel 4：paint 5：trim）
comment   			|注释说明
create_time   		|创建时间
rrp_with_vat		|价格（）
rrp_without_vat		|价格（）
efp_imp				|价格（）
efp_subs			|价格（）

修改建议：
```

```

#### Library optional Package属性设置表(bmw_library_optional_property_setting)
 字段名 | 解释 
 :-- | :-- 
id                  |主键ID
series        		|车系（大系）
e_series     		|车系（小系）
version             |版本号
system_property_code|导入时自动生成的唯一标识
model     			|车模型（例如：730Li,740Le...）
property_content    |属性内容
lhd_or_rhd  		|左驾车右驾车
rrp_with_vat		|价格（）
rrp_without_vat		|价格（）
efp_imp				|价格（）
efp_subs			|价格（）
comment   			|注释说明
create_time   		|创建时间

修改建议：
```

```

#### Library 规则表(bmw_library_rule)
 字段名 | 解释 
 :-- | :-- 
id                  |主键ID
series        		|车系（大系）
e_series     		|车系（小系）
version             |版本号
system_property_code|导入时自动生成的唯一标识
model     			|车模型（例如：730Li,740Le...）
relation_type    	|规则类型
correlated_obj		|规则内容
lhd_or_rhd  		|左驾车右驾车
rrp_with_vat		|价格（）
rrp_without_vat		|价格（）
efp_imp				|价格（）
efp_subs			|价格（）
comment   			|注释说明
create_time   		|创建时间

修改建议：
```

```

#### Library 车辆表(bmw_library_variant)
 字段名 | 解释 
 :-- | :-- 
id                  |主键ID
series        		|车系（大系）
e_series     		|车系（小系）
version             |版本号
model     			|车模型（例如：730Li,740Le...）
create_time   		|创建时间

修改建议：
```

```

#### Library option 汇总表(sys_option_lib)
 字段名 | 解释 
 :-- | :-- 
id                  |主键ID
series        		|车系（大系）
e_series     		|车系（小系）
version             |版本号
system_property_code|导入时自动生成的唯一标识
property_code       |属性码
property_name_en    |属性英文名称
property_name_cn    |属性中文名称
deletion_date		|删除时间
lib_id   			|libraryId
property_type		|属性类型
create_time   		|创建时间
sys_option_lib		|？？？

修改建议：
```
1.去除冗余字段
2.设置关联ID/字段 
```

#### 转换表(sys_convert_factor)
 字段名 | 解释 
 :-- | :-- 
id                  |主键ID
engin  				|发动机
conver_factor 		|转换因子

修改建议：
```
1.设置外键关联 engin
```
