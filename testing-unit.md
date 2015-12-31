# Unit Testing

## Setup

Before you run tests, you will need to setup a *testing database*.

By default, the testing database is called `test_timegrid`, you can change that 
and other parameters in the `phpunit.xml` file in the base directory.

## Running tests

Running `phpunit` in the base directory will execute all unit tests.

*Example Output:*

    $ phpunit 
    PHPUnit 4.8.21 by Sebastian Bergmann and contributors.
    
    ...............................................................  63 / 121 ( 52%)
    ..........................................................
    
    Time: 42.43 seconds, Memory: 97.50Mb
    
    OK (121 tests, 372 assertions)

# CodeClimate

timegrid repository is monitored by [CodeClimate](https://codeclimate.com/), an 
external service that consolidates the results from a suite of static analysis 
tools into a single, real-time report.

[![Code Climate](https://codeclimate.com/github/alariva/timegrid/badges/gpa.svg)](https://codeclimate.com/github/alariva/timegrid)
[![Test Coverage](https://codeclimate.com/github/alariva/timegrid/badges/coverage.svg)](https://codeclimate.com/github/alariva/timegrid/coverage)
[![Issue Count](https://codeclimate.com/github/alariva/timegrid/badges/issue_count.svg)](https://codeclimate.com/github/alariva/timegrid)

# Travis-CI

timegrid has continuous integration supported by 
[Travis-CI](https://travis-ci.org/).

Travis will automatically run the tests for every Pull Request, thus helping out
 to know if a code change is suitable for merge.

[![Build Status](https://travis-ci.org/alariva/timegrid.svg?branch=development)](https://travis-ci.org/alariva/timegrid)
