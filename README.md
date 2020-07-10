# eloquent-cookbook
Eloquent cookbook


## Get all data from table users

Result is a collection.
```
$results = User::all();
```

Pure sql, results is an array.

```
$results = DB::select('
            SELECT
                *
            FROM
                users
        ');
        
       
```
