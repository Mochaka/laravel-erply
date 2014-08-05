# Laravel-Erply

[![Latest Stable Version](https://poser.pugx.org/mochaka/laravel-erply/v/stable.png)](https://packagist.org/packages/mochaka/laravel-erply) [![Total Downloads](https://poser.pugx.org/mochaka/laravel-erply/downloads.png)](https://packagist.org/packages/mochaka/laravel-erply) [![Latest Unstable Version](https://poser.pugx.org/mochaka/laravel-erply/v/unstable.png)](https://packagist.org/packages/mochaka/laravel-erply) [![License](https://poser.pugx.org/mochaka/laravel-erply/license.png)](https://packagist.org/packages/mochaka/laravel-erply) [![Build Status](https://travis-ci.org/Mochaka/laravel-erply.svg?branch=master)](https://travis-ci.org/Mochaka/laravel-erply)


Laravel-Erply is a simple package to interface with Erply.com's API. Read http://erply.com/api for documentation on the valid api calls and parameters.

## Requirements

1. PHP 5.4+
2. Laravel 4
3. Guzzle 3

## Installation

Add the following to your composer.json and run `composer upgrade`:

    "mochaka/laravel-erply": "*"


Add this line of code to the providers array located in your app/config/app.php file:

    'Mochaka\Erply\ErplyServiceProvider',


You don't need to add anything to your aliases array since the package does it for you.

You then need to publish the config file and fill it out with your erply credentials.

    php artisan config:publish mochaka/laravel-erply
    

## Usage

Usage is simple, you just use the API calls from the erply website as the function and enter the parameters as the array.

### Example

As shown in the PHP examples of the API [Here](http://erply.com/getting-started-with-erply-api/?lang=php), the laravel-erply package makes it even simpler.
```php
$clientGroups = Erply::getClientGroups();
```    
This call will give us the following result. A "responseStatus" tells whether the call succeeded or failed and "recordsTotal" tells how many records were returned.

```php
    Array
    (
        [status] => Array
            (
                [request] => getCustomerGroups
                [requestUnixTime] => 1370507041
                [responseStatus] => ok
                [errorCode] => 0
                [generationTime] => 0.0026431083679199
                [recordsTotal] => 3
                [recordsInResponse] => 3
            )
    
        [records] => Array
            (
                [0] => Array
                    (
                        [clientGroupID] => 17
                        [customerGroupID] => 17
                        [parentID] => 0
                        [name] => Loyal Customers
                        [pricelistID] => 0
                        [added] => 1283248838
                        [lastModified] => 1306833659
                    )
    
                [1] => Array
                    (
                        [clientGroupID] => 18
                        [customerGroupID] => 18
                        [parentID] => 0
                        [name] => One-time Customers
                        [pricelistID] => 0
                        [added] => 1283248848
                        [lastModified] => 1306833655
                    )
    
                [2] => Array
                    (
                        [clientGroupID] => 20
                        [customerGroupID] => 20
                        [parentID] => 0
                        [name] => Campaign sign-ups
                        [pricelistID] => 0
                        [added] => 1283248917
                        [lastModified] => 1306833695
                    )
    
            )
    
    )
```
The data would be accessed as a normal array:

```php
    print $clientGroups['records'][0]['clientGroupID']; // 17
 ```   
