
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

####  model表  Table config_model (新表)


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



####  varient表  Table config_varient (新表)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
model_code         		|	对应 config_model->code
bmw_model_code         	|	bmw 内部model 代码
bmw_package_code       	|	bmw 内部package 代码
name_en    				|	英文名
name_zh    				|	中文名
disp_order      		|	显示顺序
enabled         		|	是否启用
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人


注: 

```
唯一约束 -> bmw_model_code +  bmw_package_code
```



####  配件汇总表  Table config_unique_option (原sys_option_lib)


 字段名 | 解释 
 :-- | :-- 
id						| 主键(自增)
e_series_code       	|	小系列对应code
code    				|	bmw 系统内代码
name_trans				| 	英文名去空格专小写
name_en     			|	英文名
name_cn      			|	中文名
type		  			|	配件类型 basic/optional
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人


注: 

```
唯一约束 -> name_en + code 
索引->type
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
sop             		| 	有效开始时间
eop  					| 	有效结束时间
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
option_id    				|	配件唯一id ,对应 unique_option -> id
classify     			|	分类 
comment      			|	注释
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
唯一约束 ->library_id + option_id
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
option_id    				|	配件唯一id ,对应 unique_option -> id
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
唯一约束 ->library_id + option_id + model_code
```



#### 库可选属性表 config_library_optional_property(表名没有变化)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
library_id         		|	对应 config_library->id
option_id    				|	配件唯一id ,对应 unique_option -> id
classify     			|	分类 
comment      			|	注释
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
唯一约束 ->library_id + option_id
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
option_id    				|	配件唯一id ,对应 unique_option -> id
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
唯一约束 ->library_id + option_id + model_code
```


#### 库配件规则表 config_library_option_rule(原bmw_library_rule)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
library_id         		|	对应 config_library->id
option_id    				|	配件唯一id ,对应 unique_option -> id
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
唯一约束 ->library_id + option_id + model_code
```


#### profile基础信息表 config_profile(原 bmw_launched_profile + bmw_profile_management)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
eseries_code         	|	对应config_eseries-> code
profile_name    		|	profile 名称
profile_url    			|	profile url
import_date     		|	导入时间
based_library_version   |	对应library id
new_library_version		|	新库id
sort_date      			|	排序时间
is_responsible      	|	是否可以响应
bmw_profile_code      	|	导入时excel 表中响应的code
root_profile_id      	|	根profile id
parent_profile_id      	|	父级 profile id
content      			|	内容
profile_flag      		|	标签
status      			|	当前状态
is_launched      		|	是否启用
previous_status      	|	前状态
up_version_id           |   对应 config_profile_version_history -> id每次更新会产生一个全新的Id用来做数据关联,这块要留意
is_deleted				| 	是否删除
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
索引 ->eseries_code
索引 ->sort_date
索引 ->status
索引 ->up_verion_id
```

#### profile历史记录表 config_profile_version_history(新表)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
profile_id      		|	对应config_profile -> id
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
索引 ->profile_id
索引 ->up_version_id
```

#### profile变种车型表 config_profile_varient(原 bmw_profile_generation_information)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键( 自增)
profile_up_version_id    |	对应config_profile-> up_version_id
varient_id    			| 同profile 下 model_code_varient与package_code_varient 相同 则varient_id 相同
origin_id   			| 数据原始来源id
model_code    			|	model唯一代码 对应 config_model -> code
model_code_varient    	|	确定唯一列的标志因子,原model_code
package_code_varient    |	确定唯一列的标志因子,原package_code
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
root_price              | 根profile 中价格
column_type 			| 类型 1： root profile 中的值，2：系统运算跟新library 比对后的模板  3: 当前修改
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
索引 ->profile_up_version_id
索引 ->model_code
唯一约束 -> profile_up_version_id + model_code_varient + package_code_varient + column_type
```



#### profile单元格值设置表 config_profile_cell_setting(原 bmw_profile_basic_option + bmw_profile_flexible_option)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键( 自增)
profile_up_version_id   |	对应config_profile-> up_version_id
varient_id    			|	config_profile_varient->varient_id
option_id    			|	配件id
column_type  			| 单元格类型 1 旧profile 2 新Lib 3 用户setting
is_flexable				| 是否灵活选配
setting_content     	|	设置值
show_content   			|	显示值
cell_type				| int 单元格类型(默认null)(前端需要)
value					| "S",//值 "X","-"",'',"null","?"(前端需要)
label					| 页面显示内容 (前端需要)
rmbPrice 				| float 当前价格-系统自动计算或手动修改 (前端需要)
rmbPriceAuto			| float 当前价格-系统自动计算 (前端需要)
rmbPriceOldLib  		| float 旧库价格
rmbPriceNewLib			| float 新库价格
isChange				| 单元格选项是否改变
priceOption				| int 价格计算操作 0,默认(不处理),1,增加当前价格(配件选中,新增配件)(cellType:4,6生效),2,减去当前价格(配件取消,作废配件)(cellType:2,7,8,9生效),3,增加/减少差异价格(cellType:1,3,5生效)
ruleLabel				| 规则内容,通过每次规则表自动生成
ruleMsg					| 规则描述,,通过每次规则表自动生成
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
唯一约束 ->profile_up_version_id + varient_id + option_id + column_type + is_flexable
```


#### profile配件列表 config_profile_option(后加)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键( 自增)
profile_up_version_id    |	对应config_profile-> up_version_id
option_id    				|	配件id
classify     			|	类型
is_flexable             | 是否灵活选配
index                   | 顺序
is_in_root             	| 是否在root profile中
is_in_new_lib 			| 是否在新 library中
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
唯一约束 ->profile_up_version_id + option_id + classify
```

#### profile配件列表 config_profile_option_change(后加)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键( 自增)
profile_up_version_id    |	对应config_profile-> up_version_id
option_id    			|	配件id
classify     			|	类型
change_type				|   + / -
is_flexable 			| 是否灵活选配
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
唯一约束 ->profile_up_version_id + option_id + classify
```

#### profile配件折扣表 config_profile_option_discount(后加)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键( 自增)
profile_up_version_id    |	对应config_profile-> up_version_id
option_id    				|	配件id
price   				|	价格
root_price  			| root profile 价格
rmb_price				| 	人民币价格
discount				| 	折扣
is_flexable             | 是否灵活选配
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
唯一约束 ->profile_up_version_id + option_id + is_flexable
```






#### package 大包表 config_package_lv1(原bmw_profile_flexible_package_files)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键( 自增)
profile_id         		|	对应config_profile-> id
file_name    			|	文件名
name_cn     			|	中文名
name_en   				|	英文名
status					| 	状态
current_status			| 	当前状态
work_status				| 工作状态
is_base					|是否基础
is_check				|是否选择
sort_date				|   排序时间
up_version_id           | package_version_history -> id
is_deleted				| 	是否删除
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
索引 ->profile_id 
索引 ->is_check
索引 ->is_base
索引 -> sort_date
索引 -> status
索引 -> work_status
索引 -> up_version_id
```


#### package 大包历史记录表 config_package_version_history(新加)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键( 自增)
package_lv1_id         	|	对应config_profile-> id
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
索引 ->package_lv1_id 
```




#### package 小包表 config_package_lv2(原bmw_profile_flexible_packages_management)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键( 自增)
package_lv1_up_version_id   |	对应 config_package_lv1 -> up_version_id
package_code    		|	包代码
package_name_cn     	|	中文名
package_name_en   		|	英文名
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
索引 ->package_lv1_up_version_id 
索引 ->package_code
索引 ->package_name_cn
```




#### package 包中车信息表 config_package_varient(原bmw_profile_flexible_packages_management)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键( 自增)
package_lv2_id         	|	对应 config_package_lv2 -> id
varient_id				|  对应 config_profile_varient -> id
column_type             | 类型 1： root profile 中的值，2：系统运算跟新library 比对后的模板  3: 当前修改
package_price     		|	包价格
off_price   			|	off价格(更新中)
bv_price				| bv 价格	(更新中)
tr_forcast				| --(更新中)
eff_date				| 生效时间
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
索引 ->package_lv2_id 
索引 ->varient_id
```

#### package 包中配件列表 config_package_lv2_option(新加表)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键( 自增)
package_lv2_id         	|	对应 config_package_lv2 -> id
option_id 				|   config_unique_option ->id
price         			| 价格
discount         		| 折扣
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
唯一约束 ->package_lv2_id  + option_id
```

#### package 包中配件车变种设置表	config_package_option_varient_setting(原bmw_profile_flexible_package_option_setting)


 字段名 | 解释 
 :-- | :-- 
id 						| 主键( 自增)
package_lv2_id         	|	对应 config_package_lv2 -> id
option_id 				|   config_unique_option ->id
varient_id				|	变种车代码 config_profile_varient -> id
column_type             | 类型 1： root profile 中的值，2：系统运算跟新library 比对后的模板  3: 当前修改
setting_content			| 设置值
type_f					| --(更新中)
value					| --(更新中)
label 					| --(更新中)
rmb_price 				| --(更新中)
is_change 				| --(更新中)
rmb_price0 				| --(更新中)
price_option 			| --(更新中)
price_change_type 		| --(更新中)
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
索引 ->package_lv2_id  
索引 ->option_id  
索引 ->varient_id 
```


#### 汇率表	config_sys_exchange


 字段名 | 解释 
 :-- | :-- 
id 						| 主键( 自增)
from_date         	|	开始时间
to_date 				|   结束时间
exchange				|	汇率
created_at     			|	创建时间
updated_at     			|	更新时间
created_by     			|	创建人
updated_by     			|	更新人

注释
```
索引 ->from_date  
索引 ->to_date  
```





