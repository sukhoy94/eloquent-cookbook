# eloquent-cookbook
Eloquent cookbook


What is this ? Well, personally I'm often don't remember how to make some statements/queries via eloquent orm, that's why I'm going to make some list of useful snippets and recipies. 

Feel free to contribute too !


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


