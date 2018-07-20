## How it work's?
This package will resolve needed styles and pack it to the header. The rest of additional styles will be appended to the body and will be loaded after the page is ready. Warranty for google Pagespeed up to 100% and compatible with `Bootstrap`!

![google PageSpeed: Desktop](https://gitterdoc.com/GitHub/pagespeed_desktop.png) ![google PageSpeed: Mobile](https://gitterdoc.com/GitHub/pagespeed_mobile.png)

## Installation
Go to your root directory of your laravel project and install the package with composer:

```shell
$ composer require gitterdoc/critical
```

And add the configuration's file to your laravel instance:

```shell
$ php artisan vendor:publish --provider="gitterdoc\Critical\Install"
```

## Usage
Go into your `Blade` template and replace your `Stylesheets` and add the same to the end of the body by expecting the second parameter!

```html
<!DOCTYPE html>
<html lang="{{ app()->getLocale() }}">
    <head>
        <!-- OLD -->
        <!--<link href="{{ asset('css/app.css') }}" rel="stylesheet" />-->

        <!-- To your header -->
        {{ critical('css/app.css', true) }}

        <!-- //… -->
    </head>
    <body>
        <!-- //… -->

        <!-- To your footer -->
        {{ critical('css/app.css', false) }}
    </body>
</html>
```

## API

### `{{ critical($file, $type) }}`
This method will handle your stylesheets.

| **Parameter** | **Type**  | **Default**  | **Description**                                                                     |
|---------------|-----------|--------------|-------------------------------------------------------------------------------------|
| $file         | `String`  | **required** | The stylesheet, that will be handled                                                |
| $type         | `boolean` | `true`       | It's an include for your header or your footer? (header = `true`, footer = `false`) |

## Settings
You can change the settings on the `config/critical.php` file.

| **Name**         | **Type**  | **Default** | **env**                  | **Description**                                                                                                                                             |
|------------------|-----------|-------------|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **enabled**      | `boolean` | `true`      | `CRITICAL_ENABLED`       | Enable or disable the Critical module                                                                                                                       |
| **onlyprint**    | `boolean` | `true`      | `CRITICAL_ONLY_PRINT`    | Describes the handling  - `true` - Only stylesheets will be printed, no more handling  - `false` - Each site request will be parsed to find specific styles |
| **caching**      | `Array`   |             |                          |                                                                                                                                                             |
|      **enabled** | `boolean` | `true`      | `CRITICAL_CACHE_ENABLED` | Enable or disable the caching                                                                                                                               |
|      **time***   | `Integer` | `3600`      | `CRITICAL_CACHE_TIME`    | Set the maximal cache lifetime of the cache in seconds (3600 = 1 hr)                                                                                        |
| **noscript**     | `boolean` | `true`      | `CRITICAL_NOSCRIPT`      | Adding original stylesheet as `<noscript>` for browsers, that don't have JavaScript enabled                                                                 |

