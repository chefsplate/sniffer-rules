# phpcs 2.0+ Laravel 4/5 Command
[![Build Status](https://travis-ci.org/ChefsPlate/sniffer-rules.svg?branch=master)](https://travis-ci.org/ChefsPlate/sniffer-rules)
[![Latest Stable Version](https://poser.pugx.org/ChefsPlate/sniffer-rules/version.png)](https://packagist.org/packages/ChefsPlate/sniffer-rules)
[![License](https://poser.pugx.org/ChefsPlate/sniffer-rules/license.svg)](https://packagist.org/packages/ChefsPlate/sniffer-rules)

This is a [Laravel](http://laravel.com/) 4/5 package that hooks up
[SquizLabs CodeSniffer 2](https://github.com/squizlabs/PHP_CodeSniffer)
into Laravel-based apps. It can also be used manually, so read on.

Detect violations of a defined coding standard. It helps your code remain
clean and consistent. Available options are: **PSR2**, **PSR1**, **Zend**,
**PEAR**, **Squiz**, **PHPCS** and **ChefsPlate**.

### Setup

Require this package in composer:

```
$ composer require chefsplate/sniffer-rules
```

#### Laravel 4/5

In your `config/app.php` add `ChefsPlate\SnifferRules\ServiceProvider:class`
to `$providers` array:

```php
'providers' => [
    ...

    ChefsPlate\SnifferRules\ServiceProvider::class,

    ...
],
```
#### Laravel 5: Publish the configuration file

```bash
$ php artisan vendor:publish
```

#### Laravel 4: Manually create config

Copy [config](src/ChefsPlate/SnifferRules/config/config.php) to
`app/config/sniffer-rules.php`

Edit configuration file `config/sniffer-rules.php` to tweak the sniffer behavior.

#### Manual

Install our _Standard_ by configuring **PHP_CodeSniffer** to look for it.

```bash
$ php ./vendor/bin/phpcs --config-set installed_paths ./vendor/chefsplate/src/ChefsPlate/SnifferRules/Standard/
```

### Usage
#### Laravel
```bash
$ php artisan sniff
```

To run the sniffer in a CI environment, the `-n` option should be set to remove
interaction:

```
$ php artisan sniff -n
```

#### Manual

```bash
$ php ./vendor/bin/phpcs --standard=ChefsPlate path/to/code
```

It's encouraged to add a [`Makefile`](Makefile) to your project that makes it
trivial for other developers. Use `Makefile` in this directory and adjust as
needed to fit your project requirements.

## ChefsPlate Coding Standards

### Coding standards

* [PSR 2 Coding Style Guide](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md)
* [PSR 1 Coding Standards](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md)
* [PSR 0 Coding Standards](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md)

#### Addendum and Clarifications

* `namespace` should be on the same line as opening php tag. e.g.: `<?php namespace ChefsPlate\Amazing`
* Property names should be snake_case
* Test names should use underscores, not camelCase. e.g.: `test_cats_love_catnip`

## License

MIT
