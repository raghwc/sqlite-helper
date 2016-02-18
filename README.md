# sqlite-helper
<p>sqlite bulk insertion and easy to user insert query.</p>
#How to integrate plugin
Library reference
```#
<script src="/js/sqlite-helperMini.js"></script>
```

## Sqlite bulk insertion
easy to use for sqlite bulk insertion

#Syntax
```#
sqliteh.bulkExecuteSql("<tableName>", <ArrayList>, <map column> });
```
<h1>Example</h1>
```#
 sqliteh.bulkExecuteSql("tblTest", [{ id: 1, val: "test" }, { id: 2, val: "434" }],
                function (index, item) {
                    return {
                        SystemID: item.id,
                        DisplayName: item.val
                    };
                });
                
```
