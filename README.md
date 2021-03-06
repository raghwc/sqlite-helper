# sqlite-helper
<p>sqlite bulk insertion and easy to user insert query.</p>
<ul>
<li>Easy to Create table</li>
<li>Easy to Insert records</li>
<li>Bulk insertion</li>
<li>Convert record set into list object using .toList() extension method.</li>
<li>Convert record set into list object as an external method.</li>
<li>List to CSV string converter</li>
</ul>
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

#Create Table with sqlite-helper Syntax & Example
```#
/** Syntax **/
sqliteh.executeSql("<Table Create script>", []);
                
 /*Example*/
 sqliteh.executeSql("CREATE TABLE IF NOT EXISTS tblTest (     \
                SystemID INT NOT NULL,                        \
                DisplayName VARCHAR(50) NOT NULL,             \
                PRIMARY KEY (SystemID))", []);
```

#Insert Records with sqlite-helper Syntax & Example
```#
/** Syntax **/
sqliteh.executeSql("<Table insert script>", [<value,n+>], <success event>, <failed Event>);
                
 /*Example*/
  sqliteh.executeSql("INSERT INTO tblTest (SystemID, DisplayName)", [1, "testing"]);
```

#Sqlite Bulk Insertion with sqlite-helper Syntax & Example
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

#Select Records with sqlite-helper Syntax & Example
```#
/** Syntax **/
sqliteh.executeSql("<Table select script>", [(where value)<value,n+>], <success event>, <failed Event>);
                
 /*Example*/
 sqliteh.executeSql("SELECT * FROM tblTest", [], function (result) {
                console.log(result.toList());
            },
            function () {
                console.log("failed message");
            });
```

#Data Table to list with sqlite-helper Syntax & Example
```#
/** Syntax **/
var dataList = sqliteh.tableToList(<pass sqlite result>);
                
 /*Example*/
 sqliteh.executeSql("SELECT * FROM tblTest", [], function (result) {
				var dataList = sqliteh.tableToList(result);
            },
            function () {
                console.log("failed message");
            });
 
```

#List to CSV string with sqlite-helper Syntax & Example
```#
/** Syntax **/
var dataList = sqliteh.listToString([]);
                
 /*Example*/
 var dataList = sqliteh.listToString([3,5,6,7,8,2]);
 console.log(dataList);

 /*Output*/
 "3,5,6,7,8,2"
```
