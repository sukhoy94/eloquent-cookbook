# eloquent cookbook and recipies
Eloquent cookbook


What is this ? Well, personally I'm often don't remember how to make some statements/queries via eloquent orm, that's why I'm going to make some list of useful snippets and recipies. 

Feel free to contribute too !


## 1. SELECT * from table users

Result is a collection.
```
$results = User::all();
```
or

```
$users = DB::table('users')->get();
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

## 3. SELECT certain columns

In case if you want to select certain columns, pass it as an array to all() method.

```
$users = User::all(['id', 'name', 'email',]);
```

## 4. Simple where

Let's get all users with id bigger then 2686:

```
$users = User::where('id', '>', 2686)->get();
```
## 5. Where with AND

Let's get all users with id bigger then 2686 and less then 2700
```
$users = User::where([
            ['id', '>', 2686],
            ['id', '<', 2700],
        ])->get();
```

## 6. Ordering

Let's grab 10 users with the highest id.


```
$users = DB::table('users')
            ->orderBy('id', 'desc')
            ->take(10)
            ->get();
```

## 7. LIKE

Grab all users whose name starts with A.
```
$users = User::where('name', 'like', 'A%')->get();
```

## 8. Aliasing columns

```
$users = DB::table('users')
            ->select(['id as uid', 'name as title',])
            ->orderBy('id', 'desc')
            ->take(10)
            ->get();
```

## 9. Group By

Let's add age column to users, take all users with the age > 20 and count users for each age:

```
$users = DB::table('users')
            ->select(['age', DB::raw('COUNT(id) as amount')])
            ->where('age', '>', 20)
            ->groupBy('age')
            ->get();
            
```

## 10. Enable query log

```
DB::connection()->enableQueryLog();
$queries = DB::getQueryLog();
```



