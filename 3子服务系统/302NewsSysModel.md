
### 3.2.1. 数据模型

####  大系列表  Table config_series (原bmw_series)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
code         			|	系统唯一标示码(手动填入,这个字段将作为对外关联的外键)
name_en       			|	英文名
name_zh    				|	中文名
bmw_brand_id     		|	品牌id
disp_order      		|	显示顺序
enabled         		|	是否启用
image_url         		|	右侧显示车图片url
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人


注: 

```
唯一约束 -> code 
索引 -> disp_order
索引 -> enabled
```

####  小系列表  Table config_eseries (原bmw_eseries)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
series_code         	|	对应 config_series->code
code         			|	系统唯一标示码(手动填入,这个字段将作为对外关联的外键)
name_en       			|	英文名
name_zh    				|	中文名
disp_order      		|	显示顺序
enabled         		|	是否启用
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人


注: 

```
唯一约束 -> code 
索引 -> series_code
索引 -> disp_order
索引 -> enabled
```

####  model表  Table config_model (原bmw_eseries)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
e_series_code         	|	对应 config_eseries->code
code         			|	系统唯一标示码(手动填入,这个字段将作为对外关联的外键)
name_en       			|	英文名
name_zh    				|	中文名
disp_order      		|	显示顺序
enabled         		|	是否启用
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人


注: 

```
唯一约束 -> code 
索引 -> eseries_code
索引 -> disp_order
索引 -> enabled
```



####  配件汇总表  Table config_unique_item (原sys_option_lib)


 字段名 | 解释 
 :-- | :-- 
id						| 主键(自增)
e_series_code       	|	小系列对应code
property_code    		|	bmw 系统内代码
property_name_en     	|	英文名
property_name_cn      	|	中文名
property_type		  	|	配件类型 basic/optional
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人


注: 

```
唯一约束 -> property_name_en + property_code 
索引->property_type
```


####  导入库基本信息表  Table config_library (原bmw_library_management)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
e_series_code       	|	小系列对应code
import_date    			|	导入时间
basic_file_name     	|	基础数据导入文件名
basic_file_url      	|	基础数据文件路径
optional_file_name  	|	可选数据文件名
optional_file_url   	|	可选数据导入路径
library_output_date     |	文件导出时间
libarary_data_date      |	数据日期
version         		|	版本号
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人


注: 

```
唯一约束 -> e_series_code + version 

```




#### 库基本属性表 config_library_basic_property(表名没有变化)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
library_id         		|	对应 config_library->id
item_id    				|	配件唯一id ,对应 unique_item -> id
classify     			|	分类 
comment      			|	注释
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
唯一约束 ->library_id + item_id
索引->classify
```


注释 classify
```
1：100% option
2：Uphostory
3：Wheel
4：paint
5：trim
6: flexible package
7: flexible option
8：individule feature
9：Special cases
library里会用到前5个状态
```

#### 库基本属性内容表 config_library_basic_property_setting(表名没有变化)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
library_id         		|	对应 config_library->id
item_id    				|	配件唯一id ,对应 unique_item -> id
model_code    			|	model唯一代码 对应 config_model -> code
property_content     	|	设置内容
lhd_or_rhd      		|	左驾车右驾车 L/R/X
comment      			|	注释
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
唯一约束 ->library_id + item_id + model_code
```



#### 库可选属性表 config_library_optional_property(表名没有变化)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
library_id         		|	对应 config_library->id
item_id    				|	配件唯一id ,对应 unique_item -> id
classify     			|	分类 
comment      			|	注释
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
唯一约束 ->library_id + item_id
索引->classify
```

注释 classify
```
1：100% option
2：Uphostory
3：Wheel
4：paint
5：trim
6: flexible package
7: flexible option
8：individule feature
9：Special cases
library里会用到前5个状态
```

#### 库可选属性内容表 config_library_optional_property_setting(表名没有变化)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
library_id         		|	对应 config_library->id
item_id    				|	配件唯一id ,对应 unique_item -> id
model_code    			|	model唯一代码 对应 config_model -> code
property_content     	|	设置内容
lhd_or_rhd      		|	左驾车右驾车 L/R/X
comment      			|	注释
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
唯一约束 ->library_id + item_id + model_code
```


#### 库配件规则表 config_library_item_rule(原bmw_library_rule)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
library_id         		|	对应 config_library->id
item_id    				|	配件唯一id ,对应 unique_item -> id
model_code    			|	model唯一代码 对应 config_model -> code
property_content     	|	设置内容
relation_type      		|	关系类型
correlated_obj      	|	复杂关系内容
lhd_or_rhd      		|	左驾车右驾车 L/R/X
rrp_with_vat      		|	价格,只有combine关系的时候被设定
rrp_without_vat      	|	价格,只有combine关系的时候被设定
efp_imp      			|	价格,只有combine关系的时候被设定
efp_subs      			|	价格,只有combine关系的时候被设定
comment      			|	注释
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
唯一约束 ->library_id + item_id + model_code
```


#### profile基础信息表 config_profile(原 bmw_launched_profile + bmw_profile_management)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
eseries_code         	|	对应config_eseries-> code
profile_name    		|	profile 名称
profile_url    			|	profile url
import_date     		|	导入时间
based_library_id   		|	对应library id
new_library_id			|	新库id
sort_date      			|	排序时间
is_responsible      	|	是否可以响应
bmw_profile_code      	|	导入时excel 表中响应的code
root_profile_id      	|	根profile id
parent_profile_id      	|	父级 profile id
content      			|	内容
profile_flag      		|	标签
status      			|	当前状态
previous_status      	|	前状态
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
索引 ->eseries_code
索引 ->sort_date
索引 ->status
```

#### profile变种车型表 config_profile_varent(原 bmw_profile_generation_information)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
profile_id         		|	对应config_profile-> id
model_code    			|	model唯一代码 对应 config_model -> code
varient_id    			|	列的标志代码 model_code_varent + "-" + package_code_varent
model_code_varent    	|	确定唯一列的标志因子,原model_code
package_code_varent     |	确定唯一列的标志因子,原package_code
model_name_cn   		|	原 cn_model (model 中文显示名称)
variant_name			|	原 variant (variant 项显示内容)
variant_name_cn	     	|	原 cn_variant
line_code      			|	Line Package Code
aditional_options      	|	Aditional Options
engine_output      		|	Engine Output
volume_mix_planning     |	Volume Mix planning
dof_for_modell      	|	DOF for Modell
index      				|	顺序
sop      				|	SOP 开始时间
eop      				|	EOP 结束时间
option_code_in_ivsr     |	option code in ivsr
price_transition_result |	Detail Price transition result
price_increase_abs      |	Nominal price increase abs.
monetary_adjustment     |	Monetary adjustment
price     				|	price
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
索引 ->profile_id
索引 ->model_code
索引 ->varient_id
唯一约束 ->profile_id + varient_id
唯一约束 -> profile_id + model_code_varent + package_code_varent
```

