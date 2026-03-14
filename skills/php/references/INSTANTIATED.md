# Variables instantiated from data already instantiated example

❌ **WRONG** - Bad use of memory example:
```php
function logUserEmail($users) {
    $user = $users[0];
    $name = $user['name'];
    $email = $user['email'];
    if (!preg_match('/joe/', $name)) {
        echo $email;
    }
}
```

✅ **CORRECT** - Good use of memory example:
```php
function logUserEmail($users) {
    if (!preg_match('/joe/', $users[0]['name'])) {
        echo $users[0]['email'];
    }
}
```

In the example above the variables `$user`, `$name`, and `$email` are unneeded because the data they contain is already in memory, so it is more optimal to access it directly without the need to create new variables. 