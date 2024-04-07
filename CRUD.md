添加一列 
```
alter table 表名 add 列名 数据类型 是否为空
```
删除一列
```
alter table 表名 drop column 列名
``` 
删除一行 
```
delete from 表明 where 列名表达式
```
修改一列 
```
alter table  alter column 列名 
```
修改列名(一般慎用) 
```
exec sp_rename 'ProductInfos.ProCount','Count','column'
```
 
* * *
## 约束
主键约束   
外键约束  
unique约束  
check约束  
default约束

### 主键约束
```
alter table ProductInfos add constraint
PK_ProductInfos primary key(Id)
```
### 外键约束 
<列> <数据类型> <是否为空> foreign key references <主表中的主键>
```
Alter table ProductInfos add constraint
PK_ProductInfos foreign key(TypeId) references ProductType(TypeId)
```
### Unique约束 
<列> <数据类型>  unique <是否为空> 
```
--unique 约束 ProNo+ProName
Alter table ProductInfos add constraint
IX_ProductInfos_ProNo unique(ProNo,ProName)
```
### Check约束 
check(逻辑表达式) eg. Price decimal(18,2) check(Price<10000) default(0.00) not null,
```
--check 约束
Alter table ProductInfos add constraint CK_ProductInfos_Price check(Price<10000)
```
***
## 插入数据
一、单条数据插入
(1)
Insert (into) 表名 （列名） values（值）
```
insert into ProductType (TypeName)
values('金融类')
```

(2)
Insert into 表名（列名） select 值，值，值…
```
insert into ProductType(TypeName)
select '鞋类'
```

二、插入多条
(1)
```
Insert into ProductType(TypeName)
Values ('字符串1'),('字符串2'),('字符串3')
```
(2)
Insert 库名(变量名)
```
Select <>,<>,<> union/union all
```
其中union去除重复，union all允许重复

## 克隆数据
(1)目标表在数据库已经存在
```
Insert into Test(MName)
Select TypeName from ProductType
```

(2)目标表之前数据库中不存在，执行操作时自动创建
```
Select TypeName into Test2
From ProductType
```

更新数据（主键不可以修改）
```
update Test set MName='ssss',Age=30
where Id=5
```

## 删除数据
```
drop table --删除表
delete from table --删除表中数据（记录在日志中）
truncate table --表名 不在日志里记录
--表数据清空，恢复到初始化，标识列也恢复
--但是truncate效率高，不记录日志，不激活触发器，但是不可以rollback
--delete update insert 可以恢复
```
