# str-helper

[![Latest Version on Packagist](https://img.shields.io/packagist/v/awssat/str-helper.svg?style=flat-square)](https://packagist.org/packages/awssat/str-helper)
[![StyleCI](https://styleci.io/repos/111329905/shield?branch=master)](https://styleci.io/repos/111329905)
[![Build Status](https://img.shields.io/travis/awssat/str-helper/master.svg?style=flat-square)](https://travis-ci.org/awssat/str-helper)


⚡️  A flexible, simple & yet powerful string manipulation helper for PHP. It gives you the magic of method chaining and it's easier and shorter to be included in views. It Supports most of [PHP built-in strings functions](http://php.net/manual/en/book.strings.php) (and other useful methods like: contains, equal, append, prepend ...).



```php
str('Hi World')->replace(' ', '+')->lower()
```

## Why use this instead of other string maniplulation packages ?
This is a wrapper for PHP default string functions, to provide a very poweful method chaining and conditions. 
You don't have to learn new methods names, just use PHP functions names that you know. 


## Install/Use
You can install the package via composer locally in your project folder:

```bash
$ composer require awssat/str-helper
```

After installing it, just start using `StrHelper` class, or simply the helper function `str()`: 


## Examples

```bash 
str('Hi Hello')->strReplace(' ', '-');
>> hi-hello
```


```bash
str('Hi Hello')->prepend('[')->append(']');
>> [Hi Hello]
```

In case you want an explicit string value for conditions, use "get":
```bash
if(str('Hi')->lower->get() == 'hi') {
        echo 'yes'; 
}
>> yes
```


There is a "tap" method:
```bash
str('LINK.COM')->tap(function($v){ print($v); })->lower()
>> LINK.COM
```

for callbacks use "do" method:
```bash
str('<a>link.com</a>')->do(function($string){ 
        return strip_tags($string); 
})
>> link.com
```
or: 
```bash
str('<a>link.com</a>')->do(function(){   
        $this->stripTags();
})
>> link.com/
```

you may notice using camelCase instead of snake_case for method name works too.


You can also use conditions, if(..), else(), endif()
```php
str('<html>hi</html>')
            ->ifContains('hi')
            ->upper();
>> <HTML>HI</HTML>       
```


if can take an anonymous function
```php
str('<html>hi</html>')
            ->if(function(){
                    return $this->contains('hi');
            })
            ->upper();
>> <HTML>HI</HTML>       
```

All methods are availabe to be called statically, as: 
```php
StrHelper::capitalize('life')
```
or using str() function.
```php
str()::capitalize('nomad')
```


__[UTF-8 Support] If mbstring library is installed and you call a strpos function, mb_strpos will be called instead.__


## Tests
Simply use:
```bash
$ composer test
```
## Credits
- [Abdulrahman M.](https://github.com/abdumu)
- [All Contributors](../../contributors)

## License
The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

