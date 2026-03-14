---
name: php
description: "Use this skill any time a .php file is involved in any way — as input, output, or both. This includes: creating PHP scripts, reading or parsing existing PHP code, editing or modifying PHP files, or working with PHP templates. Trigger whenever the user mentions \"PHP,php\" references a .php filename, or indicates they want to work with PHP code in any way. If a .php file needs to be opened, created, or touched, use this skill."
license: GPLv3
---

# PHP skill

You are expert PHP developer. Follow best practices and conventions when writing PHP code.

1. **Preserve Functionality:** Never change what the code does - only how it does it. All original features, outputs, and behaviors must remain intact.
2. **Enhance Clarity:**
  * Simplify code structure by:
  * Reducing unnecessary complexity and nesting
  * Eliminating redundant code and abstractions
  * Improving readability through clear variable and function names
  * Consolidating related logic.
3. **Maintain Balance:** Avoid over-simplification that could:
  * Reduce code clarity or maintainability
  * Create overly clever solutions that are hard to understand
  * Combine too many concerns into single methods or classes
  * Remove helpful abstractions that improve code organization
  * Make the code harder to debug or extend
4. Always follow these PHP instructions:

## Single quote

Use single quote `'` rather than double quotes `"` when creating strings. Avoid the use of double quote strings.

### Double quotes exception

Only use double quotes when more than 75% of the string requires interpolation. For example:

```php
"my $variable $id $message"
```

## Arrays

Always use brakets `[]` to instantiate arrays instead of the `array()` function.

## Memory allocation

Memory allocation occurs when code instantiates variables, assigns string values, or converts variable data types. Make optimized in memory use. 

Regarding memory allocation, always review, check, and replace:

### Variables instantiated from data already instantiated

Do not instantiate new variables from data that is already instantiated and in memory. 

**Example:** see the [example reference](references/INSTANTIATED.md) to evalute wrong and correct.

### Unneeded variables

Do not create a variable that is only going to be used once.

**Example:** see the [example reference](references/UNNEEDED.md) to evalute wrong and correct.

### Optimal usage of data types

Always use integers instead of string values for helper variables.

## Use statements

* When coding under a specific namespace, always use `use` statements to import classes, functions, or constants from other namespaces.
* Do not use `\` to reference classes, functions, or constants from other namespaces without importing them with `use` statements. 

## Readability

* Always use descriptive and meaningful variable names.
* Always use variable names reflecting the purpose of the variable.
* Avoid using single-letter variable names except for loop counters.
* Never use variable names with their data type or data type abbreviations as a prefix or suffix.
* Variable names should not include their context as a prefix or suffix inside a scope that already provides the meaning.

## Documentation

Unless specified with the user input "NOPHPDOC", always add PHP code documentation with docblocks using PHPDoc.

Always add documentation for:
* global functions
* classes
* traits
* interfaces
* class methods (public, protected, and private)
* class variables (public, protected, and private)
* class constants (public, protected, and private)

Docblocks always include:
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