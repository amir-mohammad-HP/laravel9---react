# barryvdh

a helpgull debagger bar that will integrate into your application:
‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍
```bash
composer require barryvdh/laravel-debugbar --dev
```
the command --dev will tell the laravel to use this package only in development mode

and in the following folder : "config/app.php"

```php
'providers' => [
    Barryvdh\Debugbar\ServiceProvider::class,
    ....,
    ],
 ```
 
 finish
