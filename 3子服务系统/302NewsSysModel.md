
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

####  库基本信息表  Table config_library (原bmw_library_management)


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




#### 库基本属性表 bmw_library_basic_property(表名没有变化)

 字段名 | 解释 
 :-- | :-- 
id 						| 主键(自增)
library_id         		|	对应 config_library->id
system_property_code    |	配件唯一id
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

注: 
> 关联标签设计格式 A方案 JSON格式
```JavaScript
[
	{
		"tagType":  "Club",
		"tagValue": "ClubID",
		"tagName":  "国安俱乐部"
	},
	{
		"tagType":  "Player",
		"tagValue": "PlayerID",
		"tagName":  "徐云龙"
	},
	{
		"tagType":  "League",
		"tagValue": "leaugeId",
		"tagName":  "中超联赛"
	}
]
```

#### 3.2.1.3 资讯评论
```SQL
Table news_comment		

id 						唯一主键
news_publish_id 		新闻Id（关联news_publish表 ID）
user_id 				用户ID
content					评论内容
praise_count			点赞数
ref_user_id				被回复用户ID
ref_comment_id			被回复评论ID
timestamp				保存点赞时间（bigint）
created_at
updated_at								
is_deleted				是否删除（用于软删除）
delete_reason			删除原因
```

#### 3.2.1.4  用户与评论的点赞关系
```SQL
Table news_comment_praise

id 						唯一主键
comment_id 				新闻评论ID（关联news_comment表 ID）
user_id 				用户ID
timestamp				保存点赞时间（bigint）
created_at
updated_at
is_deleted				是否删除（用于软删除）
```

