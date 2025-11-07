## Wildcard for Laravel Cache
![Unit Tests](https://github.com/klAvAx/laravel-wildcard-cache/workflows/tests/badge.svg)
[![Packagist License](https://img.shields.io/badge/Licence-MIT-blue)](http://choosealicense.com/licenses/mit/)
[![Latest Stable Version](https://img.shields.io/packagist/v/klavax/laravel-wildcard-cache?label=Stable)](https://packagist.org/packages/klavax/laravel-wildcard-cache)
[![Total Downloads](https://img.shields.io/packagist/dt/klavax/laravel-wildcard-cache?label=Downloads)](https://packagist.org/packages/klavax/laravel-wildcard-cache)

This is a package which adds wildcard support to Laravel Cache by replacing/overriding laravel Cache stores to include wildcard support where applicable.

This package replaces/overrides these Cache Stores:
- ApcStore
- ArrayStore
- DatabaseStore
- SessionStore

This package also adds a new methods which are used behind the scenes to:
- ApcWrapper

## Installation

Require this package with composer.

```shell
composer require klavax/laravel-wildcard-cache
```

Also you will probably want to "silence" Ambiguous class resolution warnings and that can be done if you include `exclude-from-classmap` in your composer.json `autoload` section:
```json
{
    "autoload": {
        "exclude-from-classmap": [
            "vendor/laravel/framework/src/Illuminate/Cache/ApcStore.php",
            "vendor/laravel/framework/src/Illuminate/Cache/ApcWrapper.php",
            "vendor/laravel/framework/src/Illuminate/Cache/ArrayStore.php",
            "vendor/laravel/framework/src/Illuminate/Cache/DatabaseStore.php",
            "vendor/laravel/framework/src/Illuminate/Cache/SessionStore.php"
        ]
    }
}
```

## Usage

If you are using `apc`, `array`, `database` or `session` cache stores then now you can use `{any}` token in `Cache::forget` calls like so:

```php
Cache::forget("item_{any}");
Cache::forget("someOtherItem_{any}_nested_{any}");
Cache::memo()->forget("this_{any}_works")
```

## Extra Info

APCu support is experimental, documentation for it does document an APCUIterator class, but i have not been able to test it successfully...

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=klAvAx/laravel-wildcard-cache&type=Date)](https://www.star-history.com/#klAvAx/laravel-wildcard-cache&Date)
