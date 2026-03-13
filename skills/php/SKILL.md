---
name: php
description: "Use this skill any time a .php file is involved in any way — as input, output, or both. This includes: creating PHP scripts, reading or parsing existing PHP code, editing or modifying PHP files, or working with PHP templates. Trigger whenever the user mentions \"PHP,\" references a .php filename, or indicates they want to work with PHP code in any way. If a .php file needs to be opened, created, or touched, use this skill."
license: GPLv3
---

# PHP skill

## Single quote

Use single quote `'` rather than double quotes `"` when creating strings. This is because PHP requires additional CPU processing to parse double quote strings. This is a common best practice in PHP.

### Double quotes exception

Only use double quotes when more than 75% of the string requires interpolation. For example:

```php
"my $variable $id $message"
```

## Arrays

Use brakets `[]` to instantiate arrays instead of the `array()` function.

## Memory allocation

Memory allocation occurs when code instantiates variables, assigns string values, or converts variable data types. Make optimized in memory use. 

Regarding memory allocation, review, check, and replace:

### Variables instantiated from data already instantiated

Do not instantiate new variables from data that is already instantiated and in memory. 

#### Example

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

### Unneeded variables

Do not create a variable that is only going to be used once.

#### Example

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

### Optimal usage of data types

Use integers instead of string values for helper variables.

#### Example

```php
$step = 1;
// ....
if ($step === 1)
    $step = 2;
```

## Use statements

When coding under a specific namespace, always use `use` statements to import classes, functions, or constants from other namespaces. Do not use `\` to reference classes, functions, or constants from other namespaces without importing them with `use` statements. 

## Readability

* Variable names should be descriptive and meaningful, reflecting the purpose of the variable. Avoid using single-letter variable names except for loop counters.
* Variable names should not include their data type or data type abbreviations as a prefix or suffix. For example, use `$users` instead of `$arrayUsers` or `$arrUsers`.
* Variable names should not include their context as a prefix or suffix inside a scope that already provides the meaning. For example, if a variable is used inside a function that processes user data, the variable name should not include "user" as a prefix or suffix. Instead of `$userName`, use `$name`.

## Documentation

Unless specified with the input "NOPHPDOC", always document PHP code with docblocks using PHPDoc:
* global functions
* classes
* traits
* interfaces
* class methods (public, protected, and private)
* class variables (public, protected, and private)
* class constants (public, protected, and private)

Docblocks include:
* Description on the code being commented.
* Description of the parameters (tag `@param`).
* Description of return values (tag `@return`).
* Description of variable types (tag `@var`).
* Description of any exceptions thrown (tag `@throw`).
* When a version is available, version information (tag `@version`).
    * For class methods, variables and constants use since information instead (tag `@since`).

## Exclusions

In test cases using PHPUnit, do not include:
* Description of return values (tag `@return`).
* Description of any exceptions thrown (tag `@throw`).