# Laravel Benchmark

[![Latest Version](https://img.shields.io/packagist/v/ohansyah/laravelbenchmark.svg)](https://packagist.org/packages/ohansyah/laravelbenchmark) [![Total Downloads](https://img.shields.io/packagist/dt/ohansyah/laravelbenchmark.svg)](https://packagist.org/packages/ohansyah/laravelbenchmark) [![License](https://img.shields.io/packagist/l/ohansyah/laravelbenchmark.svg)](https://packagist.org/packages/ohansyah/laravelbenchmark)

## Introduction

The Laravel Benchmark package provides a simple and convenient way to benchmark certain parts of your Laravel application. This can be useful when you need to measure the performance of specific code snippets or functions.

This package is inspired by the Laravel 9.x helper benchmarking feature, as discussed in [Laravel Documentation](https://laravel.com/docs/9.x/helpers#benchmarking) and contributed by [Nuno Maduro](https://github.com/laravel/framework/pull/44252). However, this package is specifically designed to be compatible with older PHP versions and Laravel legacy projects.

## Installation

You can install the package via Composer:
```
composer require ohansyah/laravelbenchmark
```

## Usage
```
<?php
 
use App\Models\User;
use Ohansyah\LaravelBenchmark\Benchmark;
 
Benchmark::dd(
    function () { range(1, 1000000); }
);
// 11.415ms


Benchmark::dd([
    function () { range(1, 1000000); },
    function () { User::count(); }
]);

/*
array:2 [
    0 => "10.259ms"
    1 => "111.418ms"
]
*/
```
By default, the given callbacks will be executed once (one iteration), and their duration will be displayed in the browser / console.

To invoke a callback more than once, you may specify the number of iterations that the callback should be invoked as the second argument to the method. When executing a callback more than once, the Benchmark class will return the average amount of milliseconds it took to execute the callback across all iterations

```
Benchmark::dd(
    function () { range(1, 1000000); }, 5
);
// 10.041ms

```

## License

The Laravel Benchmark package is open-sourced software licensed under the [MIT License](LICENSE.md).
