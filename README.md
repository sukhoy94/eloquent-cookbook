# eloquent-cookbook
Eloquent cookbook


## 1. SELECT * from table users

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


## 2. LIMIT users

```
$users = User::take(5)->get();
```
