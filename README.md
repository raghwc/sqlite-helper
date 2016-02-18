# sqlite-helper
<p>sqlite bulk insertion and easy to user insert query.</p>
#How to integrate plugin
Library reference
```#
<script src="/js/sqlite-helperMini.js"></script>
<script>
        $(document).ready(function () {
            try {
            sqliteh.dataBase = window.openDatabase(
	            "testDb", '1.0', 'new DataBase', (50 * 1024 * 1024),
	            function (dataBase) { });
            }
            catch (error) {
                console.log("sqllite not working please check your connection string.");
            }
        });
```
##Create table with sqlite-helper
<p>how to create table</p>
#Create Table Syntax & Example
```#
/** Syntax **/
sqliteh.executeSql("<Table Create script>", []);
                
 /*Example*/
 sqliteh.executeSql("CREATE TABLE IF NOT EXISTS tblTest (     \
                SystemID INT NOT NULL,                        \
                DisplayName VARCHAR(50) NOT NULL,             \
                PRIMARY KEY (SystemID))", []);
```
## Sqlite bulk insertion
easy to use for sqlite bulk insertion

#Sqlite Bulk Insertion Syntax & Example
```#
/** Syntax **/
sqliteh.bulkExecuteSql("<tableName>", <ArrayList>, <map column> });

/*Example*/
sqliteh.bulkExecuteSql("tblTest", [{ id: 1, val: "test" }, { id: 2, val: "434" }],
                function (index, item) {
                    return {
                        SystemID: item.id,
                        DisplayName: item.val
                    };
                });
                
```
