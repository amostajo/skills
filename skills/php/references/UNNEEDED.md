# Unneeded variables example

❌ **WRONG** - Bad use of memory example:

```php
function getUserEarnings(User $user) {
    $total = generateEarnings($user);
    $formattedTotal= formatEarnings($total);
    if (!empty($total))
        echo $formattedTotal;
}
```

✅ **CORRECT** - Good use of memory example:
```php
function getUserEarnings(User $user) {
    $total = generateEarnings($user);
    if (!empty($total))
        echo formatEarnings($total);
}
```

In the example above the variable `$formattedTotal` is removed as it was useless.