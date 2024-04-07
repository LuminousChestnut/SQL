SQL Server 固定数据库角色及其权限如下： 
db_owner：具有在数据库中进行全部操作的权限，包括配置、维护数据库及删除数据库。
db_accessadmin：可以添加或删除数据库用户的权限。 
db_securityadmin：具有管理数据库角色、角色成员以及数据库中的语句和对象的权限。 
db_ddladmin：具有执行数据定义语言（DDL）的权限。 
db_backupoperator：具有备份数据库、备份日志的权限。 
db_datareader：具有查询数据库中所有用户数据的权限。 
db_datawriter：具有插入、删除和更新数据库中所有用户数据的权限。 
db_denydatareader：不允许具有查询数据库中所有用户数据的权限，等同于对所有的表和视图授予了DENY SELECT权限。 
db_denydatawriter：不允许具有INSERT、DELETE和UPDATE数据库中所有用户数据的权限。 
