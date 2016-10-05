# MSSQL-Compat

MSSQL Compat is a small and simple drop-in library that allows your pre-7 PHP project, that uses MSSQL via mssql_* functions ( eg mssql_connect() et al ), to work transparently with PDO DBLib by providing the missing functions as wrappers around the equivalent PDO syntax - and all that with a single line!

## The story

I recently started migrating internal web applications to new servers that use PHP7.

Thus I stumbled on a couple of old applications that use MSSQL with PHP, which I dearly hoped to avoid rewriting and debugging now that PHP7 has deprecated the mssql_* family of functions.

*The result* is this single-file solution: just include it before your first mssql_* call, and it will transparently wrap them to the equivalent PDO calls.

## What it is ***not***

 - This library is *not* a security enhancement by any measure. It assumes that your program logic escapes what needs to be escaped, since you cannot benefit from PDO goodness without changing the function syntax.
   - That being said, kindly let me know if you can provide better security in the given code.
 - It is **not** meant as a means to develop new software in PHP7 using mssql_* functions - use PDO or similar!

## Requirements

MSSQL-Compat requires the bare basics for PHP7 to be able to talk to MSSQL - namely:

  - [PHP7]
  - [PDO] ( usually via the php-pdo package )
  - [PDO DBLib] installed

> *Hint*: All of the above are easily usable via repos such as [IUS] or [Remi]

## How to use

Just add an include to this library on the top of the old application `index.php` file.

```php
  <?php
     include("path/to/mssql_compat.php");

     # Insert old application logic here
```

## Under the hood: Which functions are covered

This is the list of the functions that are currently covered. They were sufficient for my needs, but, understandably, you may need more for your projects. Let me know in the issues - patches are of course very welcomed!

 - [ ] mssql_​bind
 - [x] mssql_​close
 - [x] mssql_​connect
 - [ ] mssql_​data_​seek
 - [ ] mssql_​execute
 - [x] mssql_​fetch_​array
 - [x] mssql_​fetch_​assoc
 - [ ] mssql_​fetch_​batch
 - [x] mssql_​fetch_​field
 - [x] mssql_​fetch_​object
 - [x] mssql_​fetch_​row
 - [x] mssql_​field_​length
 - [x] mssql_​field_​name
 - [x] mssql_​field_​seek
 - [ ] mssql_​field_​type
 - [x] mssql_​free_​result
 - [ ] mssql_​free_​statement
 - [x] mssql_​get_​last_​message
 - [x] mssql_​guid_​string
 - [ ] mssql_​init
 - [x] mssql_​min_​error_​severity **NOTE: Placeholder only to avoid errors!**
 - [x] mssql_​min_​message_​severity **NOTE: Placeholder only to avoid errors!**
 - [ ] mssql_​next_​result
 - [x] mssql_​num_​fields
 - [x] mssql_​num_​rows
 - [x] mssql_​pconnect
 - [x] mssql_​query
 - [ ] mssql_​result
 - [x] mssql_​rows_​affected
 - [x] mssql_​select_​db




  [PHP7]: <http://php.net/>
  [PDO]: <http://php.net/manual/en/book.pdo.php>
  [PDO DBLib]: <http://php.net/manual/en/ref.pdo-dblib.php>
  [IUS]: <https://ius.io/>
  [Remi]: <http://rpms.famillecollet.com/>
